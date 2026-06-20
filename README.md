<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Korean Vocabulary App</title>
<style>
body{font-family:Arial,sans-serif;margin:0;background:#f4f6fb;color:#222}
header{background:#2563eb;color:#fff;padding:12px;text-align:center}
nav{display:flex;gap:8px;flex-wrap:wrap;justify-content:center;padding:10px}
button{padding:8px 12px;border:none;border-radius:8px;cursor:pointer}
section{display:none;padding:15px}.active{display:block}
.card{max-width:500px;margin:auto;background:#fff;padding:20px;border-radius:12px;text-align:center;box-shadow:0 2px 8px #0002}
.dark{background:#111;color:#eee}.dark .card{background:#222;color:#eee}
input,select{padding:8px;margin:4px}
table{width:100%;border-collapse:collapse}td,th{border:1px solid #ccc;padding:6px}
canvas{max-width:400px}
</style>
</head>
<body>
<header><h2>한국어 단어장</h2></header>
<nav>
<button onclick="showTab('flash')">Flashcard</button>
<button onclick="showTab('quiz')">Quiz</button>
<button onclick="showTab('write')">Nét viết</button>
<button onclick="showTab('manage')">Quản lý</button>
<button onclick="showTab('stats')">Thống kê</button>
<button onclick="toggleDark()">Dark Mode</button>
</nav>

<section id="flash" class="active">
<div class="card" onclick="flipCard()">
<h2 id="word"></h2>
<p id="meaning">Nhấn để lật</p>
</div>
<div style="text-align:center;margin-top:10px">
<button onclick="prevWord()">◀</button>
<button onclick="speak()">🔊</button>
<button onclick="nextWord()">▶</button>
</div>
</section>

<section id="quiz">
<div class="card">
<h3 id="q"></h3>
<div id="opts"></div>
<p id="result"></p>
</div>
</section>

<section id="write">
<div class="card">
<input id="hangulInput" value="한">
<button onclick="animateHangul()">Animate</button>
<svg id="svg" width="220" height="220" viewBox="0 0 220 220">
<rect width="220" height="220" fill="white" stroke="gray"/>
<line x1="110" y1="0" x2="110" y2="220" stroke="#ddd"/>
<line x1="0" y1="110" x2="220" y2="110" stroke="#ddd"/>
</svg>
</div>
</section>

<section id="manage">
<div>
<input id="k" placeholder="한국어">
<input id="v" placeholder="Tiếng Việt">
<button onclick="addWord()">Thêm</button>
</div>
<table id="tbl"></table>
</section>

<section id="stats">
<div class="card">
<p id="stat"></p>
<canvas id="chart" width="300" height="300"></canvas>
</div>
</section>

<script>
let words=JSON.parse(localStorage.getItem("kv_words")||'null')||[
{k:"안녕하세요",v:"Xin chào"},
{k:"감사합니다",v:"Cảm ơn"},
{k:"학교",v:"Trường học"},
{k:"친구",v:"Bạn bè"},
{k:"사랑",v:"Tình yêu"},
{k:"가족",v:"Gia đình"},
{k:"음식",v:"Món ăn"},
{k:"물",v:"Nước"},
{k:"책",v:"Sách"},
{k:"학생",v:"Học sinh"},
{k:"선생님",v:"Giáo viên"},
{k:"의사",v:"Bác sĩ"},
{k:"병원",v:"Bệnh viện"},
{k:"시간",v:"Thời gian"},
{k:"오늘",v:"Hôm nay"},
{k:"내일",v:"Ngày mai"},
{k:"한국",v:"Hàn Quốc"},
{k:"베트남",v:"Việt Nam"},
{k:"컴퓨터",v:"Máy tính"},
{k:"전화",v:"Điện thoại"}
];
let idx=0,flipped=false,score=0;
function save(){localStorage.setItem("kv_words",JSON.stringify(words));renderTable();drawStats();}
function showTab(id){document.querySelectorAll("section").forEach(s=>s.classList.remove("active"));document.getElementById(id).classList.add("active");}
function renderCard(){word.textContent=words[idx].k;meaning.textContent=flipped?words[idx].v:"Nhấn để lật";}
function flipCard(){flipped=!flipped;renderCard();}
function nextWord(){idx=(idx+1)%words.length;flipped=false;renderCard();}
function prevWord(){idx=(idx-1+words.length)%words.length;flipped=false;renderCard();}
function speak(){
let u=new SpeechSynthesisUtterance(words[idx].k);
u.lang="ko-KR"; speechSynthesis.speak(u);
}
function makeQuiz(){
let a=words[Math.floor(Math.random()*words.length)];
q.textContent=a.k+" = ?";
let arr=[a.v];
while(arr.length<4){let x=words[Math.floor(Math.random()*words.length)].v;if(!arr.includes(x))arr.push(x);}
arr.sort(()=>Math.random()-0.5);
opts.innerHTML="";
arr.forEach(o=>{
let b=document.createElement("button");
b.textContent=o;
b.onclick=()=>{result.textContent=o===a.v?"Đúng":"Sai"; if(o===a.v)score++; setTimeout(makeQuiz,800); drawStats();};
opts.appendChild(b);
});
}
function addWord(){
words.push({k:k.value,v:v.value});save();
}
function renderTable(){
tbl.innerHTML="<tr><th>Hàn</th><th>Việt</th></tr>"+words.map(w=>`<tr><td>${w.k}</td><td>${w.v}</td></tr>`).join("");
}
function drawStats(){
stat.textContent="Tổng số từ: "+words.length+" | Điểm quiz: "+score;
let c=document.getElementById("chart"),x=c.getContext("2d");
x.clearRect(0,0,300,300);
x.beginPath();x.arc(150,150,100,0,Math.PI*2);x.stroke();
x.fillText("Words:"+words.length,110,145);
x.fillText("Score:"+score,110,165);
}
function animateHangul(){
let svg=document.getElementById("svg");
svg.innerHTML='<rect width="220" height="220" fill="white" stroke="gray"/><path d="M60 40 L60 180 M60 110 L140 110 M160 40 L160 180" stroke="black" stroke-width="8" fill="none"><animate attributeName="stroke-dashoffset" from="300" to="0" dur="2s"/></path>';
}
function toggleDark(){document.body.classList.toggle("dark");}
renderCard(); renderTable(); makeQuiz(); drawStats();
</script>
</body>
</html>
