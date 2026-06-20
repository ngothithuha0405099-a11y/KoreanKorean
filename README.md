<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>한국어 단어장</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@300;400;700&family=Be+Vietnam+Pro:wght@300;400;600;700&display=swap');
  *,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
  :root{
    --bg:#0f0f13;--surface:#1a1a24;--surface2:#23232f;--border:#2e2e3e;
    --accent:#c084fc;--accent2:#818cf8;--accent3:#34d399;--danger:#f87171;
    --warn:#fbbf24;--text:#e2e8f0;--text2:#94a3b8;--text3:#64748b;
    --korean:'Noto Sans KR',sans-serif;--body:'Be Vietnam Pro',sans-serif;
    --radius:16px;--radius-sm:8px;
  }
  body{background:var(--bg);color:var(--text);font-family:var(--body);min-height:100vh;display:flex;flex-direction:column;}
  header{padding:14px 24px;display:flex;align-items:center;justify-content:space-between;border-bottom:1px solid var(--border);background:var(--surface);position:sticky;top:0;z-index:100;}
  .logo{display:flex;align-items:center;gap:10px;}
  .logo-symbol{font-family:var(--korean);font-size:1.6rem;font-weight:700;background:linear-gradient(135deg,var(--accent),var(--accent2));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;}
  .logo-text{font-size:.82rem;color:var(--text2);line-height:1.3;}
  .logo-text strong{display:block;color:var(--text);font-size:.95rem;}
  .header-stats{display:flex;gap:16px;font-size:.78rem;color:var(--text2);}
  .stat{text-align:center;}.stat span{display:block;font-size:1.1rem;font-weight:700;color:var(--accent);}
  .tabs{display:flex;gap:2px;padding:14px 20px 0;background:var(--surface);border-bottom:1px solid var(--border);overflow-x:auto;}
  .tab{padding:9px 16px;border:none;background:transparent;color:var(--text2);font-family:var(--body);font-size:.85rem;font-weight:600;cursor:pointer;border-radius:var(--radius-sm) var(--radius-sm) 0 0;transition:all .2s;border-bottom:3px solid transparent;white-space:nowrap;display:flex;align-items:center;gap:5px;}
  .tab:hover{color:var(--text);background:var(--surface2);}
  .tab.active{color:var(--accent);border-bottom-color:var(--accent);background:var(--bg);}
  .panel{display:none;flex:1;padding:24px 20px;overflow-y:auto;}
  .panel.active{display:flex;flex-direction:column;gap:18px;}
  .btn{padding:8px 16px;border:1px solid var(--border);background:var(--surface);color:var(--text);border-radius:50px;font-family:var(--body);font-size:.82rem;font-weight:600;cursor:pointer;transition:all .2s;display:inline-flex;align-items:center;gap:5px;}
  .btn:hover{background:var(--surface2);border-color:var(--accent);}
  .btn-primary{background:linear-gradient(135deg,var(--accent),var(--accent2));border-color:transparent;color:#fff;}
  .btn-primary:hover{opacity:.85;border-color:transparent;}
  .btn-success{background:var(--accent3);border-color:transparent;color:#0f0f13;}
  .btn-danger{background:var(--danger);border-color:transparent;color:#fff;}
  .btn-warn{background:var(--warn);border-color:transparent;color:#0f0f13;}
  .btn-sm{padding:5px 12px;font-size:.75rem;}
  select{padding:7px 12px;background:var(--surface);border:1px solid var(--border);border-radius:50px;color:var(--text);font-family:var(--body);font-size:.82rem;outline:none;cursor:pointer;}

  /* ── Flashcard ── */
  .card-controls{display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:10px;}
  .card-counter{color:var(--text2);font-size:.88rem;}.card-counter strong{color:var(--text);}
  .controls-row{display:flex;gap:7px;flex-wrap:wrap;}
  .progress-bar{width:100%;max-width:600px;margin:0 auto;height:4px;background:var(--border);border-radius:4px;overflow:hidden;}
  .progress-fill{height:100%;background:linear-gradient(90deg,var(--accent),var(--accent2));border-radius:4px;transition:width .4s;}
  .flip-wrapper{perspective:1200px;width:100%;max-width:600px;margin:0 auto;}
  .flip-card{width:100%;height:320px;position:relative;transform-style:preserve-3d;transition:transform .6s cubic-bezier(.4,0,.2,1);cursor:pointer;}
  .flip-card.flipped{transform:rotateY(180deg);}
  .card-face{position:absolute;inset:0;backface-visibility:hidden;border-radius:var(--radius);border:1px solid var(--border);display:flex;flex-direction:column;align-items:center;justify-content:center;gap:10px;padding:28px;background:var(--surface);}
  .card-face.back{transform:rotateY(180deg);background:linear-gradient(135deg,#1e1a2e,#1a1a24);border-color:var(--accent);}
  .card-word{font-family:var(--korean);font-size:clamp(2.2rem,5.5vw,3.8rem);font-weight:700;color:var(--text);}
  .card-roman{font-size:1rem;color:var(--accent2);letter-spacing:.04em;}
  .card-meaning{font-size:1.2rem;font-weight:600;color:var(--text);}
  .card-example{font-size:.82rem;color:var(--text2);text-align:center;line-height:1.7;}
  .card-example .kor{color:var(--accent3);font-family:var(--korean);display:block;margin-bottom:2px;}
  .card-grammar{font-size:.75rem;color:var(--warn);background:#1f1a0a;border:1px solid #3d3010;border-radius:var(--radius-sm);padding:6px 10px;text-align:center;max-width:100%;}
  .card-tag{font-size:.68rem;padding:2px 8px;border-radius:50px;background:var(--bg);color:var(--accent);border:1px solid var(--accent);position:absolute;top:12px;left:12px;}
  .card-level{font-size:.68rem;padding:2px 8px;border-radius:50px;position:absolute;top:12px;right:12px;}
  .lv-1{background:#0d2011;color:var(--accent3);border:1px solid var(--accent3);}
  .lv-2{background:#0d1620;color:var(--accent2);border:1px solid var(--accent2);}
  .lv-3{background:#1e1a2e;color:var(--accent);border:1px solid var(--accent);}
  .lv-4{background:#211616;color:var(--danger);border:1px solid var(--danger);}
  .card-hint{position:absolute;bottom:12px;font-size:.68rem;color:var(--text3);}
  .nav-row{display:flex;align-items:center;justify-content:center;gap:12px;margin-top:2px;}

  /* ── Level filter pills ── */
  .level-pills{display:flex;gap:7px;flex-wrap:wrap;}
  .pill{padding:5px 14px;border-radius:50px;border:1px solid var(--border);background:var(--surface);color:var(--text2);font-size:.78rem;font-weight:600;cursor:pointer;transition:all .2s;}
  .pill:hover{border-color:var(--accent);}
  .pill.active{background:var(--accent);border-color:var(--accent);color:#fff;}
  .pill.lp-1.active{background:var(--accent3);border-color:var(--accent3);color:#0f0f13;}
  .pill.lp-2.active{background:var(--accent2);border-color:var(--accent2);color:#fff;}
  .pill.lp-3.active{background:var(--accent);border-color:var(--accent);color:#fff;}
  .pill.lp-4.active{background:var(--danger);border-color:var(--danger);color:#fff;}

  /* ── Quiz ── */
  .quiz-header{display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:10px;}
  .quiz-score-row{display:flex;gap:10px;}
  .score-chip{padding:5px 12px;border-radius:50px;font-size:.78rem;font-weight:700;}
  .score-correct{background:#162421;color:var(--accent3);border:1px solid var(--accent3);}
  .score-wrong{background:#211616;color:var(--danger);border:1px solid var(--danger);}
  .quiz-question-box{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius);padding:30px 24px;text-align:center;}
  .quiz-q-label{font-size:.76rem;color:var(--text3);text-transform:uppercase;letter-spacing:.08em;margin-bottom:10px;}
  .quiz-word{font-family:var(--korean);font-size:clamp(2.2rem,5.5vw,4rem);font-weight:700;color:var(--text);}
  .quiz-roman{font-size:.95rem;color:var(--accent2);margin-top:3px;}
  .quiz-options{display:grid;grid-template-columns:1fr 1fr;gap:10px;}
  .quiz-opt{padding:14px 12px;background:var(--surface);border:2px solid var(--border);border-radius:var(--radius-sm);color:var(--text);font-family:var(--body);font-size:.9rem;font-weight:600;cursor:pointer;transition:all .2s;text-align:left;}
  .quiz-opt:hover:not(:disabled){border-color:var(--accent);background:#1e1a2e;}
  .quiz-opt.correct{border-color:var(--accent3);background:#162421;color:var(--accent3);}
  .quiz-opt.wrong{border-color:var(--danger);background:#211616;color:var(--danger);}
  .quiz-opt:disabled{cursor:default;}
  .quiz-feedback{text-align:center;padding:12px;border-radius:var(--radius-sm);font-size:.9rem;font-weight:600;}
  .quiz-feedback.correct{background:#162421;color:var(--accent3);}
  .quiz-feedback.wrong{background:#211616;color:var(--danger);}
  .quiz-result{text-align:center;padding:36px 20px;}
  .quiz-result .big{font-size:3.5rem;font-weight:700;}.quiz-result h2{font-size:1.8rem;margin-bottom:6px;}.quiz-result p{color:var(--text2);margin:6px 0;}

  /* ── Stroke ── */
  .stroke-search{display:flex;gap:7px;flex-wrap:wrap;align-items:center;}
  .stroke-search input{flex:1;min-width:120px;padding:8px 13px;background:var(--surface);border:1px solid var(--border);border-radius:50px;color:var(--text);font-family:var(--korean);font-size:1rem;outline:none;transition:border-color .2s;}
  .stroke-search input:focus{border-color:var(--accent);}
  .stroke-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(75px,1fr));gap:8px;}
  .stroke-thumb{border:1px solid var(--border);border-radius:var(--radius-sm);padding:9px 5px 5px;text-align:center;cursor:pointer;transition:all .2s;background:var(--surface);}
  .stroke-thumb:hover,.stroke-thumb.active{border-color:var(--accent);background:#1e1a2e;}
  .stroke-thumb .syl{font-family:var(--korean);font-size:1.3rem;display:block;}
  .stroke-thumb .mean{font-size:.62rem;color:var(--text2);margin-top:2px;white-space:nowrap;overflow:hidden;text-overflow:ellipsis;}
  .stroke-has-data{border-color:#3a2e4e;}

  .stroke-viewer{display:flex;flex-direction:column;align-items:center;gap:14px;margin-top:4px;}
  .stroke-viewer h2{font-family:var(--korean);font-size:1.3rem;color:var(--text);}
  .stroke-box{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius);padding:18px;display:flex;flex-direction:column;align-items:center;gap:14px;width:100%;max-width:420px;}
  .stroke-svg-wrap{position:relative;background:#fff;border-radius:var(--radius-sm);width:260px;height:260px;}
  .stroke-svg-wrap svg{position:absolute;inset:0;width:100%;height:100%;}
  .stroke-btns{display:flex;gap:7px;flex-wrap:wrap;justify-content:center;}
  .stroke-info{font-size:.78rem;color:var(--text2);text-align:center;line-height:1.6;}
  .stroke-counter{font-size:.78rem;color:var(--accent);font-weight:600;}
  .stroke-note{font-size:.72rem;color:var(--text3);font-style:italic;text-align:center;}

  /* ── List ── */
  .list-filters{display:flex;gap:7px;flex-wrap:wrap;align-items:center;}
  .list-filters input{flex:1;min-width:150px;padding:8px 13px;background:var(--surface);border:1px solid var(--border);border-radius:50px;color:var(--text);font-family:var(--body);font-size:.88rem;outline:none;transition:border-color .2s;}
  .list-filters input:focus{border-color:var(--accent);}
  .word-table{border:1px solid var(--border);border-radius:var(--radius);overflow:hidden;}
  .word-table table{width:100%;border-collapse:collapse;}
  .word-table th{padding:9px 14px;text-align:left;font-size:.72rem;color:var(--text3);text-transform:uppercase;letter-spacing:.07em;background:var(--surface);border-bottom:1px solid var(--border);}
  .word-table td{padding:11px 14px;font-size:.88rem;border-bottom:1px solid var(--border);vertical-align:middle;}
  .word-table tr:last-child td{border-bottom:none;}
  .word-table tr:hover td{background:var(--surface);}
  .kor-cell{font-family:var(--korean);font-size:1.05rem;font-weight:700;}
  .roman-cell{color:var(--accent2);font-size:.78rem;}
  .tag-cell span{font-size:.68rem;padding:2px 7px;border-radius:50px;background:var(--bg);color:var(--accent);border:1px solid var(--accent);}
  .play-btn{background:transparent;border:1px solid var(--border);color:var(--text2);border-radius:50%;width:28px;height:28px;display:flex;align-items:center;justify-content:center;cursor:pointer;font-size:.85rem;transition:all .2s;}
  .play-btn:hover{border-color:var(--accent3);color:var(--accent3);}
  .lv-badge{font-size:.65rem;padding:2px 6px;border-radius:50px;}

  .empty-state{text-align:center;padding:40px 20px;color:var(--text3);font-size:.9rem;}
  .empty-state .big{font-size:2.2rem;margin-bottom:6px;}
  .toast{position:fixed;bottom:20px;left:50%;transform:translateX(-50%) translateY(80px);background:var(--surface2);border:1px solid var(--border);color:var(--text);padding:9px 18px;border-radius:50px;font-size:.82rem;font-weight:600;z-index:999;transition:transform .3s;pointer-events:none;}
  .toast.show{transform:translateX(-50%) translateY(0);}
  @media(max-width:540px){
    .tabs{padding:12px 10px 0;gap:0;}
    .tab{padding:7px 10px;font-size:.78rem;}
    .panel{padding:16px 12px;}
    .quiz-options{grid-template-columns:1fr;}
    header{padding:12px 14px;}
  }
</style>
</head>
<body>
<header>
  <div class="logo">
    <div class="logo-symbol">한</div>
    <div class="logo-text"><strong>한국어 단어장</strong>Học từ vựng tiếng Hàn</div>
  </div>
  <div class="header-stats">
    <div class="stat"><span id="stat-total">0</span>Từ</div>
    <div class="stat"><span id="stat-learned">0</span>Đã học</div>
    <div class="stat"><span id="stat-level">-</span>Cấp độ</div>
  </div>
</header>

<div id="app-screen" style="display:flex;flex:1;flex-direction:column;">
  <div class="tabs">
    <button class="tab active" onclick="switchTab('flashcard')">🃏 Flashcard</button>
    <button class="tab" onclick="switchTab('quiz')">✏️ Trắc nghiệm</button>
    <button class="tab" onclick="switchTab('stroke')">✍️ Nét chữ</button>
    <button class="tab" onclick="switchTab('list')">📋 Danh sách</button>
  </div>

  <!-- FLASHCARD -->
  <div class="panel active" id="panel-flashcard">
    <div class="card-controls">
      <div class="card-counter">Thẻ <strong id="fc-index">1</strong> / <strong id="fc-total">0</strong></div>
      <div class="controls-row">
        <button class="btn btn-sm" onclick="shuffleCards()">🔀 Xáo</button>
        <button class="btn btn-sm" onclick="speakCurrent()">🔊 Phát âm</button>
        <select id="fc-tag" onchange="applyFilter()"><option value="">Tất cả chủ đề</option></select>
      </div>
    </div>
    <div class="level-pills">
      <div class="pill active" onclick="setPillLevel(this,'')" data-lv="">Tất cả</div>
      <div class="pill lp-1" onclick="setPillLevel(this,'1')" data-lv="1">🟢 Sơ cấp</div>
      <div class="pill lp-2" onclick="setPillLevel(this,'2')" data-lv="2">🔵 Trung cấp</div>
      <div class="pill lp-3" onclick="setPillLevel(this,'3')" data-lv="3">🟣 Cao cấp</div>
      <div class="pill lp-4" onclick="setPillLevel(this,'4')" data-lv="4">🔴 TOPIK</div>
    </div>
    <div class="progress-bar"><div class="progress-fill" id="fc-progress"></div></div>
    <div class="flip-wrapper">
      <div class="flip-card" id="flip-card" onclick="flipCard()">
        <div class="card-face front">
          <div class="card-tag" id="fc-tag-label"></div>
          <div class="card-level" id="fc-level-label"></div>
          <div class="card-word" id="fc-word"></div>
          <div class="card-roman" id="fc-roman"></div>
          <div class="card-hint">Nhấn để xem nghĩa</div>
        </div>
        <div class="card-face back">
          <div class="card-tag" id="fc-tag-b"></div>
          <div class="card-level" id="fc-level-b"></div>
          <div class="card-meaning" id="fc-meaning"></div>
          <div class="card-example">
            <span class="kor" id="fc-ex-kor"></span>
            <span id="fc-ex-viet"></span>
          </div>
          <div class="card-grammar" id="fc-grammar"></div>
          <div class="card-hint">Nhấn để lật lại</div>
        </div>
      </div>
    </div>
    <div class="nav-row">
      <button class="btn btn-sm" onclick="prevCard()">← Trước</button>
      <button class="btn btn-danger btn-sm" onclick="markCard(false)">✗ Chưa nhớ</button>
      <button class="btn btn-success btn-sm" onclick="markCard(true)">✓ Đã nhớ</button>
      <button class="btn btn-sm" onclick="nextCard()">Tiếp →</button>
    </div>
  </div>

  <!-- QUIZ -->
  <div class="panel" id="panel-quiz">
    <div class="quiz-header">
      <div>
        <div style="font-size:1.05rem;font-weight:700;">Trắc nghiệm</div>
        <div style="font-size:.78rem;color:var(--text2)">Câu <span id="q-num">0</span> / <span id="q-total">0</span></div>
      </div>
      <div class="quiz-score-row">
        <div class="score-chip score-correct">✓ <span id="q-correct">0</span></div>
        <div class="score-chip score-wrong">✗ <span id="q-wrong">0</span></div>
        <select id="quiz-level" onchange="startQuiz()" style="font-size:.75rem;padding:5px 10px;">
          <option value="">Tất cả cấp độ</option>
          <option value="1">🟢 Sơ cấp</option>
          <option value="2">🔵 Trung cấp</option>
          <option value="3">🟣 Cao cấp</option>
          <option value="4">🔴 TOPIK</option>
        </select>
        <button class="btn btn-sm" onclick="startQuiz()">↺ Làm lại</button>
      </div>
    </div>
    <div id="quiz-area"></div>
  </div>

  <!-- STROKE -->
  <div class="panel" id="panel-stroke">
    <div class="stroke-search">
      <input type="text" id="stroke-search-inp" placeholder="Tìm từ..." oninput="filterStroke(this.value)">
      <button class="btn btn-sm" onclick="clearStrokeSearch()">✕</button>
    </div>
    <p style="font-size:.75rem;color:var(--text3);">💜 Viền tím = có dữ liệu nét viết SVG thật. Còn lại hiển thị tĩnh.</p>
    <div class="stroke-grid" id="stroke-grid"></div>
    <div class="stroke-viewer" id="stroke-viewer" style="display:none">
      <h2 id="sv-title"></h2>
      <div class="stroke-box">
        <div class="stroke-svg-wrap" id="svg-wrap"></div>
        <div class="stroke-counter" id="sv-counter"></div>
        <div class="stroke-btns">
          <button class="btn btn-sm btn-primary" id="btn-play" onclick="playStrokes()">▶ Xem nét</button>
          <button class="btn btn-sm" onclick="resetStrokes()">↺ Reset</button>
          <button class="btn btn-sm" onclick="prevStroke()">‹ Nét trước</button>
          <button class="btn btn-sm" onclick="nextStroke()">Nét sau ›</button>
          <button class="btn btn-sm" onclick="speakStroke()">🔊 Phát âm</button>
        </div>
        <div class="stroke-info" id="sv-info"></div>
        <div class="stroke-note" id="sv-note"></div>
      </div>
    </div>
  </div>

  <!-- LIST -->
  <div class="panel" id="panel-list">
    <div class="list-filters">
      <input type="text" id="list-search" placeholder="Tìm kiếm từ..." oninput="renderList()">
      <select id="list-tag" onchange="renderList()"><option value="">Tất cả chủ đề</option></select>
      <select id="list-level" onchange="renderList()">
        <option value="">Tất cả cấp</option>
        <option value="1">🟢 Sơ cấp</option>
        <option value="2">🔵 Trung cấp</option>
        <option value="3">🟣 Cao cấp</option>
        <option value="4">🔴 TOPIK</option>
      </select>
    </div>
    <div class="word-table" id="word-table"></div>
  </div>
</div>

<div class="toast" id="toast"></div>

<script>
// ══════════════════════════════════════════════════════════════
//  SVG STROKE DATA — thứ tự nét thật sự cho các 자모 (자음+모음)
//  Mỗi nét là mảng [x1,y1, cx1,cy1, cx2,cy2, x2,y2] (cubic bezier)
//  hoặc [x1,y1, x2,y2] (đường thẳng), trong không gian 100×100
// ══════════════════════════════════════════════════════════════

// Bộ nét viết cho từng 자모 — thứ tự nét chuẩn theo KS X 1026
// Mỗi segment: ['L', x1,y1, x2,y2] hoặc ['C', x1,y1, cx1,cy1, cx2,cy2, x2,y2]
const JAMO_STROKES = {
  // ─── 자음 ───
  'ㄱ': {
    name:'기역 (giyeok)', order:'trái→phải, trên→dưới',
    strokes:[
      ['L',18,25, 75,25],      // nét 1: ngang trên
      ['L',75,25, 75,78],      // nét 2: dọc xuống
    ]
  },
  'ㄴ': {
    name:'니은 (nieun)', order:'trên→dưới, trái→phải',
    strokes:[
      ['L',28,22, 28,75],      // nét 1: dọc xuống
      ['L',28,75, 75,75],      // nét 2: ngang phải
    ]
  },
  'ㄷ': {
    name:'디귿 (digeut)', order:'trái→phải, trên→dưới, trái→phải',
    strokes:[
      ['L',18,22, 78,22],      // nét 1: ngang trên
      ['L',22,50, 78,50],      // nét 2: ngang giữa
      ['L',22,78, 78,78],      // nét 3: ngang dưới
    ]
  },
  'ㄹ': {
    name:'리을 (rieul)', order:'nhiều nét tạo hình zigzag',
    strokes:[
      ['L',20,22, 75,22],      // nét 1
      ['L',75,22, 75,48],      // nét 2
      ['L',75,48, 20,48],      // nét 3
      ['L',20,48, 20,55],      // nét 4
      ['L',20,55, 75,55],      // nét 5 (thực tế ㄹ có 5 nét)
    ]
  },
  'ㅁ': {
    name:'미음 (mieum)', order:'trái→phải theo hình vuông',
    strokes:[
      ['L',20,22, 78,22],      // trên
      ['L',78,22, 78,78],      // phải
      ['L',78,78, 20,78],      // dưới
      ['L',20,78, 20,22],      // trái
    ]
  },
  'ㅂ': {
    name:'비읍 (bieup)', order:'2 dọc rồi 3 ngang',
    strokes:[
      ['L',22,22, 22,78],      // dọc trái
      ['L',76,22, 76,78],      // dọc phải
      ['L',22,22, 76,22],      // ngang trên
      ['L',22,50, 76,50],      // ngang giữa
      ['L',22,78, 76,78],      // ngang dưới
    ]
  },
  'ㅅ': {
    name:'시옷 (siot)', order:'trái xuống, phải xuống',
    strokes:[
      ['C',48,20, 30,35, 18,55, 15,78],  // nét 1: cong trái
      ['C',48,20, 65,35, 80,55, 83,78],  // nét 2: cong phải
    ]
  },
  'ㅇ': {
    name:'이응 (ieung)', order:'vòng tròn ngược chiều kim đồng hồ',
    strokes:[
      ['C',50,18, 78,18, 82,50, 82,50],  // vòng tròn phần 1
      ['C',82,50, 82,82, 50,82, 50,82],  // phần 2
      ['C',50,82, 18,82, 18,50, 18,50],  // phần 3
      ['C',18,50, 18,18, 50,18, 50,18],  // phần 4
    ]
  },
  'ㅈ': {
    name:'지읒 (jieut)', order:'ngang trên rồi 2 nét chéo',
    strokes:[
      ['L',18,28, 80,28],      // nét 1: ngang
      ['C',48,28, 30,50, 18,75, 15,80],  // nét 2: chéo trái
      ['C',48,28, 65,50, 80,75, 83,80],  // nét 3: chéo phải
    ]
  },
  'ㅊ': {
    name:'치읓 (chieut)', order:'dấu trên, ngang, 2 chéo',
    strokes:[
      ['L',43,10, 55,10],      // dấu nhỏ trên
      ['L',18,28, 80,28],
      ['C',48,28, 30,50, 18,75, 15,80],
      ['C',48,28, 65,50, 80,75, 83,80],
    ]
  },
  'ㅋ': {
    name:'키읔 (kieuk)', order:'như ㄱ thêm nét ngang giữa',
    strokes:[
      ['L',18,25, 75,25],
      ['L',75,25, 75,78],
      ['L',30,51, 65,51],
    ]
  },
  'ㅌ': {
    name:'티읕 (tieut)', order:'như ㄷ thêm nét ngang giữa',
    strokes:[
      ['L',18,22, 78,22],
      ['L',22,50, 78,50],
      ['L',22,78, 78,78],
      ['L',22,35, 78,35],
    ]
  },
  'ㅍ': {
    name:'피읖 (pieup)', order:'ngang trên, 2 dọc, ngang dưới',
    strokes:[
      ['L',18,28, 80,28],
      ['L',32,28, 32,72],
      ['L',66,28, 66,72],
      ['L',18,72, 80,72],
    ]
  },
  'ㅎ': {
    name:'히읗 (hieut)', order:'dấu nhỏ, vòng, dọc, vòng tròn',
    strokes:[
      ['L',43,10, 55,10],
      ['L',30,25, 68,25],
      ['C',50,32, 78,32, 82,55, 82,55],
      ['C',82,55, 82,80, 50,80, 50,80],
      ['C',50,80, 18,80, 18,55, 18,55],
      ['C',18,55, 18,32, 50,32, 50,32],
    ]
  },
  // ─── 모음 ───
  'ㅏ': {
    name:'아 (a)', order:'dọc, ngang phải',
    strokes:[
      ['L',48,15, 48,85],     // dọc
      ['L',48,38, 75,38],     // ngang phải
    ]
  },
  'ㅓ': {
    name:'어 (eo)', order:'dọc, ngang trái',
    strokes:[
      ['L',50,15, 50,85],
      ['L',50,38, 23,38],
    ]
  },
  'ㅗ': {
    name:'오 (o)', order:'ngang trên, dọc xuống',
    strokes:[
      ['L',18,42, 80,42],
      ['L',48,42, 48,82],
    ]
  },
  'ㅜ': {
    name:'우 (u)', order:'ngang dưới, dọc lên',
    strokes:[
      ['L',18,55, 80,55],
      ['L',48,55, 48,15],
    ]
  },
  'ㅡ': {
    name:'으 (eu)', order:'một nét ngang',
    strokes:[
      ['L',15,50, 83,50],
    ]
  },
  'ㅣ': {
    name:'이 (i)', order:'một nét dọc',
    strokes:[
      ['L',50,12, 50,87],
    ]
  },
  'ㅐ': {
    name:'애 (ae)', order:'2 dọc, ngang phải nét 1',
    strokes:[
      ['L',35,15, 35,85],
      ['L',35,38, 60,38],
      ['L',65,15, 65,85],
    ]
  },
  'ㅔ': {
    name:'에 (e)', order:'dọc, ngang trái, dọc 2',
    strokes:[
      ['L',32,15, 32,85],
      ['L',32,38, 58,38],
      ['L',62,15, 62,85],
    ]
  },
  'ㅛ': {
    name:'요 (yo)', order:'2 dọc ngắn, ngang dài',
    strokes:[
      ['L',33,25, 33,48],
      ['L',65,25, 65,48],
      ['L',18,48, 80,48],
      ['L',48,48, 48,82],
    ]
  },
  'ㅠ': {
    name:'유 (yu)', order:'ngang, 2 dọc xuống',
    strokes:[
      ['L',18,40, 80,40],
      ['L',33,40, 33,80],
      ['L',65,40, 65,80],
    ]
  },
};

// Map âm tiết Hangul → jamo components
// Hangul Unicode: U+AC00 + (초성×21 + 중성)×28 + 종성
const CHOSUNG  = ['ㄱ','ㄲ','ㄴ','ㄷ','ㄸ','ㄹ','ㅁ','ㅂ','ㅃ','ㅅ','ㅆ','ㅇ','ㅈ','ㅉ','ㅊ','ㅋ','ㅌ','ㅍ','ㅎ'];
const JUNGSUNG = ['ㅏ','ㅐ','ㅑ','ㅒ','ㅓ','ㅔ','ㅕ','ㅖ','ㅗ','ㅘ','ㅙ','ㅚ','ㅛ','ㅜ','ㅝ','ㅞ','ㅟ','ㅠ','ㅡ','ㅢ','ㅣ'];
const JONGSUNG = ['','ㄱ','ㄲ','ㄳ','ㄴ','ㄵ','ㄶ','ㄷ','ㄹ','ㄺ','ㄻ','ㄼ','ㄽ','ㄾ','ㄿ','ㅀ','ㅁ','ㅂ','ㅄ','ㅅ','ㅆ','ㅇ','ㅈ','ㅊ','ㅋ','ㅌ','ㅍ','ㅎ'];

function decomposeHangul(char) {
  const code = char.charCodeAt(0) - 0xAC00;
  if (code < 0 || code > 11171) return null;
  const cho = Math.floor(code / 28 / 21);
  const jung = Math.floor((code / 28) % 21);
  const jong = code % 28;
  return { cho: CHOSUNG[cho], jung: JUNGSUNG[jung], jong: JONGSUNG[jong] };
}

// ── Tạo SVG path string từ stroke data ──
function strokeToPath(seg) {
  if (seg[0] === 'L') {
    return `M ${seg[1]} ${seg[2]} L ${seg[3]} ${seg[4]}`;
  } else if (seg[0] === 'C') {
    return `M ${seg[1]} ${seg[2]} C ${seg[3]} ${seg[4]}, ${seg[5]} ${seg[6]}, ${seg[7]} ${seg[8]}`;
  }
  return '';
}

// ── Ghép tất cả nét của một âm tiết ──
function getSyllableStrokes(char) {
  const jamo = decomposeHangul(char);
  if (!jamo) return null;

  const result = [];
  const components = [jamo.cho, jamo.jung];
  if (jamo.jong) components.push(jamo.jong);

  // Xác định vùng vẽ cho từng thành phần trong ô 100×100
  // Layout: có / không có 종성, 모음 dọc hay ngang
  const hasJong = !!jamo.jong;
  const isVerticalVowel = ['ㅏ','ㅐ','ㅑ','ㅒ','ㅓ','ㅔ','ㅕ','ㅖ','ㅣ'].includes(jamo.jung);
  const isHorizontalVowel = ['ㅗ','ㅛ','ㅜ','ㅠ','ㅡ'].includes(jamo.jung);

  // Vùng cho 초성
  let choBox, jungBox, jongBox;
  if (isVerticalVowel && !hasJong) {
    choBox  = {x:5,  y:5,  w:52, h:90};
    jungBox = {x:57, y:5,  w:38, h:90};
  } else if (isVerticalVowel && hasJong) {
    choBox  = {x:5,  y:5,  w:50, h:55};
    jungBox = {x:55, y:5,  w:38, h:55};
    jongBox = {x:5,  y:60, w:90, h:35};
  } else if (isHorizontalVowel && !hasJong) {
    choBox  = {x:10, y:5,  w:80, h:50};
    jungBox = {x:10, y:55, w:80, h:40};
  } else {
    choBox  = {x:10, y:5,  w:80, h:38};
    jungBox = {x:10, y:43, w:80, h:28};
    jongBox = {x:10, y:70, w:80, h:26};
  }

  // Hàm transform nét từ không gian 100×100 vào box
  function transformSeg(seg, box) {
    const tx = v => box.x + (v / 100) * box.w;
    const ty = v => box.y + (v / 100) * box.h;
    const s = [...seg];
    if (s[0]==='L') { s[1]=tx(s[1]);s[2]=ty(s[2]);s[3]=tx(s[3]);s[4]=ty(s[4]); }
    else if (s[0]==='C') {
      s[1]=tx(s[1]);s[2]=ty(s[2]);
      s[3]=tx(s[3]);s[4]=ty(s[4]);
      s[5]=tx(s[5]);s[6]=ty(s[6]);
      s[7]=tx(s[7]);s[8]=ty(s[8]);
    }
    return s;
  }

  const pairs = [[jamo.cho, choBox], [jamo.jung, jungBox]];
  if (hasJong) pairs.push([jamo.jong, jongBox]);

  let strokeIdx = 0;
  for (const [jm, box] of pairs) {
    const data = JAMO_STROKES[jm];
    if (!data) {
      // không có data → vẽ placeholder
      result.push({ jamo: jm, idx: strokeIdx++, seg: null, box, label: `${jm} (chưa có data nét)` });
      continue;
    }
    for (const seg of data.strokes) {
      result.push({ jamo: jm, idx: strokeIdx, seg: transformSeg(seg, box), label: `${data.name} — nét ${result.filter(r=>r.jamo===jm).length+1}/${data.strokes.length}` });
      strokeIdx++;
    }
  }
  return result;
}

// ══════════════════════════════════════════════════════════════
//  DỮ LIỆU TỪ VỰNG 100 TỪ
// ══════════════════════════════════════════════════════════════
const words = [
  // ── Cấp 1: Sơ cấp ──
  {korean:"안녕하세요",romanization:"annyeonghaseyo",meaning:"Xin chào (lịch sự)",example_kor:"안녕하세요, 저는 민준이에요.",example_viet:"Xin chào, tôi là Min-jun.",grammar:"안녕하세요 = 안녕(bình an) + 하다(làm) + 세요(kính ngữ). Dùng với người lớn hơn hoặc người không thân quen.",tag:"Chào hỏi",level:"1"},
  {korean:"감사합니다",romanization:"gamsahamnida",meaning:"Cảm ơn (trang trọng)",example_kor:"도와주셔서 감사합니다.",example_viet:"Cảm ơn vì đã giúp đỡ tôi.",grammar:"감사(cảm tạ) + 합니다(kính ngữ lịch sự). 해요체: 감사해요. Trả lời: 천만에요 (không có gì).",tag:"Chào hỏi",level:"1"},
  {korean:"미안합니다",romanization:"mianhamnida",meaning:"Xin lỗi (trang trọng)",example_kor:"늦어서 미안합니다.",example_viet:"Xin lỗi vì đến trễ.",grammar:"미안(미안하다=xin lỗi) + 합니다. Thân mật hơn: 미안해요, 미안해. 죄송합니다 lịch sự hơn.",tag:"Chào hỏi",level:"1"},
  {korean:"안녕히 가세요",romanization:"annyeonghi gaseyo",meaning:"Tạm biệt (người ra về)",example_kor:"내일 봬요! 안녕히 가세요.",example_viet:"Hẹn gặp ngày mai! Tạm biệt.",grammar:"안녕히 가세요 (nói với người đi). 안녕히 계세요 (nói với người ở lại). Phân biệt 2 cách chào tạm biệt.",tag:"Chào hỏi",level:"1"},
  {korean:"이름",romanization:"ireum",meaning:"Tên",example_kor:"이름이 뭐예요?",example_viet:"Bạn tên là gì?",grammar:"이름이 뭐예요? = Tên + 이(trợ từ chủ ngữ) + 뭐(cái gì) + 예요(là). 이/가 là trợ từ chủ ngữ.",tag:"Giới thiệu",level:"1"},
  {korean:"나라",romanization:"nara",meaning:"Đất nước / Quốc gia",example_kor:"어느 나라 사람이에요?",example_viet:"Bạn là người nước nào?",grammar:"어느(nào) + 나라(nước) + 사람(người) + 이에요(là). Cấu trúc hỏi nguồn gốc.",tag:"Giới thiệu",level:"1"},
  {korean:"밥",romanization:"bap",meaning:"Cơm / Bữa ăn",example_kor:"밥 먹었어요?",example_viet:"Bạn ăn cơm chưa?",grammar:"먹었어요 = 먹다(ăn) + 었(quá khứ) + 어요(kính ngữ). Người Hàn dùng câu này như lời chào.",tag:"Ẩm thực",level:"1"},
  {korean:"물",romanization:"mul",meaning:"Nước",example_kor:"물 한 잔 주세요.",example_viet:"Cho tôi một ly nước.",grammar:"한(một) + 잔(chén/ly) + 주세요(xin hãy cho). 주세요 = 주다(cho) + 세요(kính ngữ mệnh lệnh).",tag:"Ẩm thực",level:"1"},
  {korean:"집",romanization:"jip",meaning:"Nhà",example_kor:"집에 가고 싶어요.",example_viet:"Tôi muốn về nhà.",grammar:"에 가다 = đi đến. 고 싶다 = muốn làm gì. 집에 가고 싶어요 = muốn về nhà.",tag:"Địa điểm",level:"1"},
  {korean:"학교",romanization:"hakgyo",meaning:"Trường học",example_kor:"학교에서 한국어를 배워요.",example_viet:"Tôi học tiếng Hàn ở trường.",grammar:"에서 = trợ từ chỉ nơi thực hiện hành động. 배우다 = học. 를 = trợ từ tân ngữ.",tag:"Giáo dục",level:"1"},
  {korean:"친구",romanization:"chingu",meaning:"Bạn bè",example_kor:"제 친구예요.",example_viet:"Đây là bạn tôi.",grammar:"제 = 저의 (của tôi, rút gọn). 예요 = là (sau nguyên âm). 이에요 (sau phụ âm).",tag:"Xã hội",level:"1"},
  {korean:"가족",romanization:"gajok",meaning:"Gia đình",example_kor:"가족이 몇 명이에요?",example_viet:"Gia đình bạn có mấy người?",grammar:"몇(bao nhiêu) + 명(đếm người) + 이에요(là). 명 là đơn vị đếm người trong tiếng Hàn.",tag:"Gia đình",level:"1"},
  {korean:"엄마",romanization:"eomma",meaning:"Mẹ",example_kor:"엄마가 요리를 해요.",example_viet:"Mẹ đang nấu ăn.",grammar:"가 = trợ từ chủ ngữ (sau nguyên âm). 을/를 = trợ từ tân ngữ. 요리하다 = nấu ăn.",tag:"Gia đình",level:"1"},
  {korean:"아빠",romanization:"appa",meaning:"Bố / Ba",example_kor:"아빠는 회사에 가요.",example_viet:"Bố đi làm.",grammar:"는/은 = trợ từ chủ đề (topic). Khác với 이/가 (chủ ngữ). 회사 = công ty.",tag:"Gia đình",level:"1"},
  {korean:"오빠",romanization:"oppa",meaning:"Anh trai (gọi bởi nữ)",example_kor:"오빠, 밥 먹었어?",example_viet:"Anh ơi, anh ăn cơm chưa?",grammar:"오빠 = anh trai/bạn trai lớn tuổi hơn, chỉ nữ dùng. 형 = nam gọi anh trai. 언니 = nữ gọi chị.",tag:"Gia đình",level:"1"},
  {korean:"하나",romanization:"hana",meaning:"Một (số đếm thuần Hàn)",example_kor:"사과 하나 주세요.",example_viet:"Cho tôi một quả táo.",grammar:"Số thuần Hàn: 하나(1), 둘(2), 셋(3), 넷(4), 다섯(5). Dùng với đơn vị đếm bản địa.",tag:"Số đếm",level:"1"},
  {korean:"오늘",romanization:"oneul",meaning:"Hôm nay",example_kor:"오늘 날씨가 좋아요.",example_viet:"Hôm nay thời tiết đẹp.",grammar:"날씨가 좋아요 = thời tiết(날씨) + chủ ngữ(가) + tốt(좋다)+요. 좋다 → 좋아요 (thể hiện tại).",tag:"Thời gian",level:"1"},
  {korean:"내일",romanization:"naeil",meaning:"Ngày mai",example_kor:"내일 뭐 해요?",example_viet:"Ngày mai bạn làm gì?",grammar:"뭐(cái gì) + 해요(làm). Câu hỏi đơn giản không cần trợ từ câu hỏi, chỉ thay ngữ điệu.",tag:"Thời gian",level:"1"},
  {korean:"어제",romanization:"eoje",meaning:"Hôm qua",example_kor:"어제 뭐 했어요?",example_viet:"Hôm qua bạn làm gì?",grammar:"했어요 = 하다(làm) + 았/었(quá khứ) + 어요. Quá khứ của 하다 là 했다.",tag:"Thời gian",level:"1"},
  {korean:"지금",romanization:"jigeum",meaning:"Bây giờ",example_kor:"지금 어디에 있어요?",example_viet:"Bạn đang ở đâu bây giờ?",grammar:"어디(ở đâu) + 에(trợ từ vị trí) + 있어요(ở/có). 있다 = ở, tồn tại. 없다 = không có.",tag:"Thời gian",level:"1"},
  {korean:"사랑해요",romanization:"saranghaeyo",meaning:"Tôi yêu bạn",example_kor:"당신을 사랑해요.",example_viet:"Tôi yêu bạn.",grammar:"사랑하다(yêu) → 사랑해요(thể 해요). 당신 = bạn (trang trọng). 너를 사랑해 = thân mật hơn.",tag:"Tình cảm",level:"1"},
  {korean:"좋아요",romanization:"joayo",meaning:"Tôi thích / Tốt",example_kor:"한국 음식이 너무 좋아요.",example_viet:"Tôi rất thích đồ ăn Hàn.",grammar:"좋다(tốt/thích) → 좋아요. 너무 = quá, rất. 음식이 좋아요 = thích đồ ăn (chủ thể là người nói).",tag:"Cảm xúc",level:"1"},
  {korean:"싫어요",romanization:"sireoyo",meaning:"Tôi không thích",example_kor:"매운 음식이 싫어요.",example_viet:"Tôi không thích đồ ăn cay.",grammar:"싫다(ghét/không thích) → 싫어요. 매운 = cay (tính từ đứng trước danh từ, bỏ 다 thêm ㄴ/은).",tag:"Cảm xúc",level:"1"},
  {korean:"맛있어요",romanization:"masisseoyo",meaning:"Ngon",example_kor:"이 음식이 정말 맛있어요.",example_viet:"Món ăn này thực sự rất ngon.",grammar:"맛있다 = ngon (맛=vị+있다=có). 이 = này (chỉ thị từ gần). 정말 = thực sự.",tag:"Ẩm thực",level:"1"},
  {korean:"예뻐요",romanization:"yeppeoyo",meaning:"Đẹp (ngoại hình)",example_kor:"꽃이 정말 예뻐요.",example_viet:"Bông hoa thực sự rất đẹp.",grammar:"예쁘다(đẹp) → 예뻐요 (불규칙: bỏ ㅡ + 어요). Biến tắc ㅡ탈락.",tag:"Tính từ",level:"1"},
  {korean:"크다",romanization:"keuda",meaning:"To lớn",example_kor:"한국은 산이 많고 크지 않아요.",example_viet:"Hàn Quốc có nhiều núi nhưng không lớn.",grammar:"크다 → 커요 (bỏ 으 thêm 어요). 많다 = nhiều → 많아요. 지 않아요 = phủ định.",tag:"Tính từ",level:"1"},

  // ── Cấp 2: Trung cấp ──
  {korean:"버스",romanization:"beoseu",meaning:"Xe buýt",example_kor:"버스를 타고 학교에 가요.",example_viet:"Tôi đi xe buýt đến trường.",grammar:"을/를 타다 = đi (phương tiện). 타고 = 타다+고 (nối 2 mệnh đề: đi... và...). 에 가다 = đến.",tag:"Di chuyển",level:"1"},
  {korean:"지하철",romanization:"jihacheol",meaning:"Tàu điện ngầm",example_kor:"지하철 몇 호선이에요?",example_viet:"Đây là tuyến tàu số mấy?",grammar:"몇(bao nhiêu) + 호선(số tuyến) + 이에요. 호선 = số hiệu tuyến metro.",tag:"Di chuyển",level:"2"},
  {korean:"병원",romanization:"byeongwon",meaning:"Bệnh viện",example_kor:"병원에 가야 해요.",example_viet:"Tôi phải đi bệnh viện.",grammar:"아/어야 하다 = phải làm gì. 가야 해요 = phải đi. Cấu trúc bổn phận quan trọng.",tag:"Sức khỏe",level:"2"},
  {korean:"약",romanization:"yak",meaning:"Thuốc",example_kor:"약을 먹어야 해요.",example_viet:"Bạn phải uống thuốc.",grammar:"약을 먹다 = uống thuốc (먹다=ăn, dùng cho cả thuốc). 마시다=uống nước. Phân biệt 먹다 vs 마시다.",tag:"Sức khỏe",level:"2"},
  {korean:"날씨",romanization:"nalssyi",meaning:"Thời tiết",example_kor:"오늘 날씨가 어때요?",example_viet:"Hôm nay thời tiết thế nào?",grammar:"어때요? = thế nào? (hỏi cảm nhận/tình trạng). 어떻다 → 어때요. Câu hỏi tình trạng phổ biến.",tag:"Thiên nhiên",level:"2"},
  {korean:"비가 오다",romanization:"biga oda",meaning:"Trời mưa",example_kor:"비가 와서 우산을 챙겼어요.",example_viet:"Vì trời mưa nên tôi mang ô.",grammar:"아/어서 = vì... nên (nguyên nhân-kết quả). 비가 오다 = mưa rơi. 우산을 챙기다 = mang ô.",tag:"Thiên nhiên",level:"2"},
  {korean:"음식",romanization:"eumsik",meaning:"Đồ ăn / Thức ăn",example_kor:"한국 음식 중에 뭘 제일 좋아해요?",example_viet:"Bạn thích món ăn Hàn nào nhất?",grammar:"중에(trong số) + 뭘(cái gì-rút gọn của 무엇을) + 제일(nhất) + 좋아하다(thích).",tag:"Ẩm thực",level:"2"},
  {korean:"김치",romanization:"gimchi",meaning:"Kim chi",example_kor:"김치를 담가 본 적 있어요?",example_viet:"Bạn đã thử làm kim chi chưa?",grammar:"아/어 본 적 있다 = đã từng làm gì chưa. 담그다(muối kim chi) + 아 본 적 있다.",tag:"Ẩm thực",level:"2"},
  {korean:"쇼핑",romanization:"syoping",meaning:"Mua sắm",example_kor:"주말에 쇼핑하러 가요.",example_viet:"Cuối tuần tôi đi mua sắm.",grammar:"(으)러 가다 = đi để làm gì (mục đích di chuyển). 쇼핑하러 가다 = đi để mua sắm.",tag:"Mua sắm",level:"2"},
  {korean:"얼마예요",romanization:"eolmayeyo",meaning:"Bao nhiêu tiền?",example_kor:"이거 얼마예요?",example_viet:"Cái này bao nhiêu tiền?",grammar:"이거 = 이것(cái này, rút gọn). 얼마 = bao nhiêu tiền. 예요/이에요 = là. Câu hỏi giá cơ bản.",tag:"Mua sắm",level:"2"},
  {korean:"회사",romanization:"hoesa",meaning:"Công ty",example_kor:"어느 회사에서 일해요?",example_viet:"Bạn làm việc ở công ty nào?",grammar:"에서 = tại (nơi làm hành động). 일하다 = làm việc. 어느 = nào (hỏi về sự lựa chọn cụ thể).",tag:"Công việc",level:"2"},
  {korean:"일",romanization:"il",meaning:"Công việc / Việc làm",example_kor:"요즘 일이 너무 많아요.",example_viet:"Dạo này công việc nhiều quá.",grammar:"요즘(dạo này) + 너무(quá) + 많아요(nhiều). 너무 trong khẩu ngữ dùng để nhấn mạnh.",tag:"Công việc",level:"2"},
  {korean:"돈",romanization:"don",meaning:"Tiền",example_kor:"돈을 모으고 있어요.",example_viet:"Tôi đang tiết kiệm tiền.",grammar:"고 있다 = đang làm (thể tiến hành). 모으다(tiết kiệm/gom góp) + 고 있어요 = đang tiết kiệm.",tag:"Công việc",level:"2"},
  {korean:"여행",romanization:"yeohaeng",meaning:"Du lịch",example_kor:"방학에 여행을 가고 싶어요.",example_viet:"Tôi muốn đi du lịch dịp nghỉ hè.",grammar:"방학(nghỉ hè/xuân) + 에(vào dịp) + 여행을 가다(đi du lịch) + 고 싶다(muốn).",tag:"Du lịch",level:"2"},
  {korean:"호텔",romanization:"hotel",meaning:"Khách sạn",example_kor:"호텔을 예약했어요.",example_viet:"Tôi đã đặt khách sạn rồi.",grammar:"예약하다(đặt trước/reserve) + 았어요(quá khứ). 았/었 + 어요 = thì quá khứ.",tag:"Du lịch",level:"2"},
  {korean:"지도",romanization:"jido",meaning:"Bản đồ",example_kor:"지도 앱으로 찾았어요.",example_viet:"Tôi tìm bằng app bản đồ.",grammar:"으로 = bằng (công cụ/phương tiện). 앱으로 = bằng app. 찾다(tìm) → 찾았어요(đã tìm).",tag:"Du lịch",level:"2"},
  {korean:"문화",romanization:"munhwa",meaning:"Văn hóa",example_kor:"한국 문화에 관심이 있어요.",example_viet:"Tôi có hứng thú với văn hóa Hàn.",grammar:"에 관심이 있다 = có hứng thú với. 있다 vs 없다. 관심 = sự quan tâm/hứng thú.",tag:"Văn hóa",level:"2"},
  {korean:"음악",romanization:"eumak",meaning:"Âm nhạc",example_kor:"음악을 들으면서 공부해요.",example_viet:"Tôi vừa học vừa nghe nhạc.",grammar:"면서 = vừa...vừa (2 hành động đồng thời). 들으면서 = vừa nghe. 들다(nghe) bất quy tắc.",tag:"Văn hóa",level:"2"},
  {korean:"영화",romanization:"yeonghwa",meaning:"Phim / Điện ảnh",example_kor:"같이 영화 보러 갈까요?",example_viet:"Chúng ta cùng đi xem phim nhé?",grammar:"같이 = cùng nhau. (으)러 가다 = đi để làm gì. 갈까요? = đi không? (đề nghị/gợi ý).",tag:"Giải trí",level:"2"},
  {korean:"운동",romanization:"undong",meaning:"Thể dục / Thể thao",example_kor:"매일 운동하는 편이에요.",example_viet:"Tôi có xu hướng tập thể dục mỗi ngày.",grammar:"는 편이다 = có xu hướng, thiên về. 매일(mỗi ngày) + 운동하다 + 는 편이에요.",tag:"Sức khỏe",level:"2"},
  {korean:"건강",romanization:"geongang",meaning:"Sức khỏe",example_kor:"건강이 최고예요.",example_viet:"Sức khỏe là quan trọng nhất.",grammar:"최고(tốt nhất) + 예요(là). 최고 = 最高. Câu khẳng định A가/이 B예요 = A là B.",tag:"Sức khỏe",level:"2"},
  {korean:"사진",romanization:"sajin",meaning:"Ảnh / Chụp ảnh",example_kor:"사진 찍어도 돼요?",example_viet:"Tôi có thể chụp ảnh không?",grammar:"아/어도 되다 = có thể/được phép làm. 찍다(chụp) + 어도 돼요? = có được chụp không?",tag:"Sinh hoạt",level:"2"},
  {korean:"시간",romanization:"sigan",meaning:"Thời gian / Giờ",example_kor:"시간이 있으면 같이 가요.",example_viet:"Nếu có thời gian thì cùng đi nhé.",grammar:"(으)면 = nếu (điều kiện). 있으면 = nếu có. 같이 가요 = cùng đi nhé (lời mời).",tag:"Thời gian",level:"2"},
  {korean:"주말",romanization:"jumal",meaning:"Cuối tuần",example_kor:"주말에 보통 뭐 해요?",example_viet:"Cuối tuần bạn thường làm gì?",grammar:"보통(thường thường/thường xuyên) + 뭐 해요(làm gì). Hỏi thói quen sinh hoạt.",tag:"Thời gian",level:"2"},
  {korean:"약속",romanization:"yakssok",meaning:"Hẹn / Lời hứa",example_kor:"내일 약속이 있어요.",example_viet:"Ngày mai tôi có hẹn.",grammar:"있어요 = có (tồn tại/sở hữu). 약속이 있다 = có hẹn. Dùng 있다/없다 để nói có/không.",tag:"Sinh hoạt",level:"2"},
  {korean:"피곤하다",romanization:"pigonhada",meaning:"Mệt mỏi",example_kor:"요즘 너무 피곤해요.",example_viet:"Dạo này tôi mệt quá.",grammar:"피곤하다 → 피곤해요. 하다 động từ: bỏ 다 thêm 여요→해요. 너무 = quá (nhấn mạnh).",tag:"Cảm xúc",level:"2"},
  {korean:"힘들다",romanization:"himdeurda",meaning:"Vất vả / Khó khăn",example_kor:"한국어가 힘들지만 재미있어요.",example_viet:"Tiếng Hàn vất vả nhưng thú vị.",grammar:"지만 = nhưng (tương phản). 힘들다(vất vả) + 지만 + 재미있다(thú vị). Cấu trúc đối lập quan trọng.",tag:"Cảm xúc",level:"2"},

  // ── Cấp 3: Cao cấp ──
  {korean:"경험",romanization:"gyeongheom",meaning:"Kinh nghiệm / Trải nghiệm",example_kor:"다양한 경험을 쌓는 것이 중요해요.",example_viet:"Tích lũy nhiều trải nghiệm đa dạng là quan trọng.",grammar:"는 것 = danh hóa động từ (việc làm gì). 쌓는 것이 중요하다 = việc tích lũy quan trọng.",tag:"Giáo dục",level:"3"},
  {korean:"노력",romanization:"noryeok",meaning:"Nỗ lực / Cố gắng",example_kor:"노력하면 반드시 성공할 수 있어요.",example_viet:"Nếu nỗ lực thì chắc chắn có thể thành công.",grammar:"(으)면 = nếu. 반드시(chắc chắn) + 수 있다(có thể). 을/ㄹ 수 있다 = có thể làm.",tag:"Giáo dục",level:"3"},
  {korean:"목표",romanization:"mokpyo",meaning:"Mục tiêu",example_kor:"올해 목표가 한국어 능숙하게 말하는 거예요.",example_viet:"Mục tiêu năm nay là nói tiếng Hàn thành thạo.",grammar:"는 거예요 = cái việc... (danh hóa+는 것의 구어체). 능숙하게 = thành thạo (부사형).",tag:"Phát triển",level:"3"},
  {korean:"습관",romanization:"seupkwan",meaning:"Thói quen",example_kor:"좋은 습관을 만드는 데 시간이 걸려요.",example_viet:"Cần thời gian để tạo thói quen tốt.",grammar:"는 데 시간이 걸리다 = mất thời gian để làm gì. 걸리다 = mất (thời gian/công sức).",tag:"Phát triển",level:"3"},
  {korean:"관계",romanization:"gwangye",meaning:"Mối quan hệ",example_kor:"인간관계가 복잡해요.",example_viet:"Mối quan hệ giữa người với người phức tạp.",grammar:"인간관계 = quan hệ con người (từ ghép: 인간+관계). 복잡하다 = phức tạp → 복잡해요.",tag:"Xã hội",level:"3"},
  {korean:"의견",romanization:"uigyeon",meaning:"Ý kiến",example_kor:"당신의 의견을 말씀해 주세요.",example_viet:"Hãy cho biết ý kiến của bạn.",grammar:"말씀해 주세요 = (kính ngữ) xin hãy nói. 주세요 sau động từ = xin hãy làm gì cho tôi.",tag:"Giao tiếp",level:"3"},
  {korean:"문제",romanization:"munje",meaning:"Vấn đề / Bài toán",example_kor:"이 문제를 어떻게 해결할까요?",example_viet:"Làm thế nào để giải quyết vấn đề này?",grammar:"어떻게(như thế nào) + 해결하다(giải quyết) + ㄹ까요(chúng ta nên/sẽ). Câu hỏi bàn luận.",tag:"Giao tiếp",level:"3"},
  {korean:"비교",romanization:"bigyo",meaning:"So sánh",example_kor:"두 제품을 비교해 봤어요.",example_viet:"Tôi đã thử so sánh hai sản phẩm.",grammar:"아/어 보다 = thử làm gì. 비교해 봤어요 = đã thử so sánh. 봤어요 = 보았어요 (quá khứ).",tag:"Học thuật",level:"3"},
  {korean:"이유",romanization:"iyu",meaning:"Lý do / Nguyên nhân",example_kor:"한국어를 배우는 이유가 뭐예요?",example_viet:"Lý do bạn học tiếng Hàn là gì?",grammar:"배우는(đang học/việc học) + 이유(lý do) + 가(chủ ngữ) + 뭐예요(là gì). Hỏi lý do.",tag:"Học thuật",level:"3"},
  {korean:"결정",romanization:"gyeoljeong",meaning:"Quyết định",example_kor:"혼자 결정하기 어려워요.",example_viet:"Khó mà quyết định một mình.",grammar:"기 어렵다 = khó để làm gì. 기 쉽다 = dễ để làm gì. 혼자 = một mình.",tag:"Phát triển",level:"3"},
  {korean:"연락",romanization:"yeollak",meaning:"Liên lạc",example_kor:"연락 주시면 감사하겠습니다.",example_viet:"Nếu bạn liên lạc thì tôi rất biết ơn.",grammar:"감사하겠습니다 = (kính ngữ trang trọng) tôi sẽ biết ơn. 겠 = dự đoán/ý chí tương lai.",tag:"Giao tiếp",level:"3"},
  {korean:"기억",romanization:"giieok",meaning:"Ký ức / Nhớ",example_kor:"어릴 때 기억이 흐릿해요.",example_viet:"Ký ức hồi nhỏ mờ nhạt rồi.",grammar:"어릴 때 = khi còn nhỏ. 을/ㄹ 때 = khi (thời gian). 흐릿하다 = mờ nhạt, không rõ ràng.",tag:"Cảm xúc",level:"3"},
  {korean:"발전",romanization:"baljeon",meaning:"Phát triển / Tiến bộ",example_kor:"한국은 빠른 속도로 발전했어요.",example_viet:"Hàn Quốc đã phát triển với tốc độ nhanh.",grammar:"빠른(nhanh-tính từ) + 속도(tốc độ) + 로(bằng/với). 발전하다 = phát triển → 발전했어요.",tag:"Xã hội",level:"3"},
  {korean:"환경",romanization:"hwangyeong",meaning:"Môi trường",example_kor:"환경 보호에 더 관심을 가져야 해요.",example_viet:"Chúng ta cần quan tâm hơn đến bảo vệ môi trường.",grammar:"더(hơn nữa) + 관심을 가지다(quan tâm) + 아야 하다(phải). 보호(bảo vệ) = 保護.",tag:"Xã hội",level:"3"},
  {korean:"성격",romanization:"seonggyeok",meaning:"Tính cách",example_kor:"성격이 좋은 사람이 좋아요.",example_viet:"Tôi thích người có tính cách tốt.",grammar:"성격이 좋은(tính cách tốt-mệnh đề quan hệ) + 사람(người). Tính từ đứng trước danh từ.",tag:"Con người",level:"3"},
  {korean:"인생",romanization:"insaeng",meaning:"Cuộc đời / Cuộc sống",example_kor:"인생은 짧으니까 즐겁게 살아요.",example_viet:"Cuộc đời ngắn nên hãy sống vui vẻ.",grammar:"으니까 = vì, do đó (nguyên nhân chủ quan). 짧다(ngắn)+으니까. 즐겁게 = vui vẻ (부사).",tag:"Con người",level:"3"},
  {korean:"행복",romanization:"haengbok",meaning:"Hạnh phúc",example_kor:"행복은 가까운 곳에 있어요.",example_viet:"Hạnh phúc ở gần thôi.",grammar:"가까운(gần-tính từ đứng trước) + 곳(nơi) + 에 있다(ở tại). 가깝다 → 가까운 (불규칙ㅂ).",tag:"Con người",level:"3"},
  {korean:"기회",romanization:"gihoe",meaning:"Cơ hội",example_kor:"기회가 오면 놓치지 마세요.",example_viet:"Khi cơ hội đến, đừng để lỡ.",grammar:"지 마세요 = đừng làm (cấm đoán lịch sự). 놓치다(để lỡ) + 지 마세요. Rất thông dụng.",tag:"Phát triển",level:"3"},
  {korean:"준비",romanization:"junbi",meaning:"Chuẩn bị",example_kor:"미리 준비하는 것이 중요해요.",example_viet:"Chuẩn bị trước là điều quan trọng.",grammar:"미리(trước) + 준비하다(chuẩn bị) + 는 것이(việc...) + 중요하다(quan trọng).",tag:"Phát triển",level:"3"},
  {korean:"선택",romanization:"seontaek",meaning:"Lựa chọn",example_kor:"좋은 선택을 했어요.",example_viet:"Bạn đã có một lựa chọn tốt.",grammar:"좋은(tốt) + 선택(lựa chọn) + 을(tân ngữ) + 하다(làm) → 했어요(đã làm). V+했어요=quá khứ.",tag:"Phát triển",level:"3"},
  {korean:"부탁",romanization:"butak",meaning:"Nhờ vả / Yêu cầu",example_kor:"한 가지 부탁이 있어요.",example_viet:"Tôi có một việc muốn nhờ bạn.",grammar:"한 가지(một điều) + 부탁이 있다(có điều muốn nhờ). Mở đầu lịch sự khi cần nhờ người khác.",tag:"Giao tiếp",level:"3"},

  // ── Cấp 4: TOPIK ──
  {korean:"가능성",romanization:"ganeungseong",meaning:"Khả năng / Tiềm năng",example_kor:"이 계획이 실현될 가능성이 얼마나 돼요?",example_viet:"Khả năng kế hoạch này được thực hiện là bao nhiêu?",grammar:"이/가 될 가능성 = khả năng trở thành. 얼마나 = bao nhiêu. 실현되다 = được thực hiện (피동).",tag:"Học thuật",level:"4"},
  {korean:"논리",romanization:"nolli",meaning:"Logic / Lý luận",example_kor:"논리적인 사고가 필요해요.",example_viet:"Cần tư duy logic.",grammar:"논리적인(có tính logic-tính từ) = 논리+적(접미사)+인(관형형). 필요하다 = cần thiết.",tag:"Học thuật",level:"4"},
  {korean:"복잡하다",romanization:"bokjaphada",meaning:"Phức tạp",example_kor:"상황이 생각보다 복잡했어요.",example_viet:"Tình huống phức tạp hơn tôi nghĩ.",grammar:"보다 = hơn (so sánh). 생각보다 = hơn những gì nghĩ. 었어요 = quá khứ. Cấu trúc so sánh A보다.",tag:"Học thuật",level:"4"},
  {korean:"영향",romanization:"yeonghyang",meaning:"Ảnh hưởng",example_kor:"SNS가 젊은이들에게 큰 영향을 미쳐요.",example_viet:"MXH có ảnh hưởng lớn đến giới trẻ.",grammar:"에게 = với/cho (người nhận). 영향을 미치다 = tạo ra ảnh hưởng. 미치다 = vươn tới/tác động.",tag:"Xã hội",level:"4"},
  {korean:"과정",romanization:"gwajeong",meaning:"Quá trình",example_kor:"결과보다 과정이 중요할 수 있어요.",example_viet:"Quá trình có thể quan trọng hơn kết quả.",grammar:"보다 = hơn. 결과(kết quả)보다 과정이(quá trình) = quá trình hơn kết quả. 수 있다 = có thể.",tag:"Học thuật",level:"4"},
  {korean:"제도",romanization:"jedo",meaning:"Chế độ / Hệ thống",example_kor:"사회 제도를 개선해야 한다.",example_viet:"Cần phải cải thiện chế độ xã hội.",grammar:"아야/어야 한다 = phải (ngữ pháp cần thiết). 개선하다 = cải thiện. 한다 = văn viết trang trọng.",tag:"Xã hội",level:"4"},
  {korean:"현상",romanization:"hyeonsang",meaning:"Hiện tượng",example_kor:"이 현상의 원인을 분석해야 해요.",example_viet:"Cần phân tích nguyên nhân của hiện tượng này.",grammar:"의 = trợ từ sở hữu (của). 현상의 원인 = nguyên nhân của hiện tượng. 분석하다 = phân tích.",tag:"Học thuật",level:"4"},
  {korean:"해결책",romanization:"haegyeolchaek",meaning:"Giải pháp",example_kor:"근본적인 해결책을 찾아야 해요.",example_viet:"Cần tìm giải pháp căn bản.",grammar:"근본적인(căn bản) = 근본+적+인. 찾아야 해요 = phải tìm. 근본적 = có tính căn bản, gốc rễ.",tag:"Học thuật",level:"4"},
  {korean:"의식",romanization:"uisik",meaning:"Ý thức / Nhận thức",example_kor:"환경 보호 의식을 높여야 해요.",example_viet:"Cần nâng cao ý thức bảo vệ môi trường.",grammar:"높이다 = nâng cao (사동사: 높다→높이다). 아야 해요 = phải. 을 높이다 = nâng cao cái gì.",tag:"Xã hội",level:"4"},
  {korean:"갈등",romanization:"galdeung",meaning:"Mâu thuẫn / Xung đột",example_kor:"세대 간 갈등을 줄이려면 대화가 필요해요.",example_viet:"Để giảm mâu thuẫn giữa các thế hệ cần có đối thoại.",grammar:"으려면 = để có thể/nếu muốn (목적+조건). 줄이다 = giảm bớt (사동). 세대 간 = giữa các thế hệ.",tag:"Xã hội",level:"4"},
  {korean:"반면",romanization:"banmyeon",meaning:"Mặt khác / Trong khi đó",example_kor:"도시는 편리한 반면 복잡해요.",example_viet:"Thành phố tiện lợi nhưng mặt khác lại phức tạp.",grammar:"는 반면(에) = trong khi đó, mặt khác (đối lập). Liên từ nối 2 mệnh đề đối lập, dùng nhiều văn viết.",tag:"Học thuật",level:"4"},
  {korean:"경쟁",romanization:"gyeongjaeng",meaning:"Cạnh tranh",example_kor:"치열한 경쟁 속에서 살아남으려면 실력이 있어야 해요.",example_viet:"Để sống sót trong cuộc cạnh tranh khốc liệt cần có thực lực.",grammar:"속에서 = trong (không gian/hoàn cảnh). 살아남다 = sống sót. 으려면 = nếu muốn/để.",tag:"Xã hội",level:"4"},
];

// ══════════════════════════════════════════════════════════════
//  STATE
// ══════════════════════════════════════════════════════════════
let fcWords=[], fcIndex=0, fcLearned=new Set(), activePillLevel='', activePillTag='';
let quizWords=[], quizIndex=0, quizCorrect=0, quizWrong=0;
let strokeWord=null, strokeStrokes=[], strokeCurrent=0, strokePlaying=false, strokeTimer=null;

// ══════════════════════════════════════════════════════════════
//  INIT
// ══════════════════════════════════════════════════════════════
function initApp(){
  document.getElementById('stat-total').textContent=words.length;
  const tags=[...new Set(words.map(w=>w.tag).filter(Boolean))];
  ['fc-tag','list-tag'].forEach(id=>{
    const el=document.getElementById(id);
    el.innerHTML='<option value="">Tất cả chủ đề</option>';
    tags.forEach(t=>el.innerHTML+=`<option value="${t}">${t}</option>`);
  });
  applyFilter(); startQuiz(); renderStrokeGrid(words); renderList();
}

// ── Tabs ──
function switchTab(name){
  document.querySelectorAll('.tab').forEach((t,i)=>{
    const panels=['flashcard','quiz','stroke','list'];
    t.classList.toggle('active',panels[i]===name);
  });
  document.querySelectorAll('.panel').forEach(p=>p.classList.remove('active'));
  document.getElementById('panel-'+name).classList.add('active');
}

// ══════════════════════════════════════════════════════════════
//  FLASHCARD
// ══════════════════════════════════════════════════════════════
function setPillLevel(el,lv){
  document.querySelectorAll('.pill').forEach(p=>p.classList.remove('active'));
  el.classList.add('active');
  activePillLevel=lv;
  applyFilter();
}
function applyFilter(){
  const tag=document.getElementById('fc-tag').value;
  fcWords=words.filter(w=>{
    const lvOk=!activePillLevel||w.level===activePillLevel;
    const tagOk=!tag||w.tag===tag;
    return lvOk&&tagOk;
  });
  fcIndex=0;
  document.getElementById('flip-card').classList.remove('flipped');
  renderCard();
  const lvNames={'':"Tất cả",'1':"Sơ cấp",'2':"Trung cấp",'3':"Cao cấp",'4':"TOPIK"};
  document.getElementById('stat-level').textContent=lvNames[activePillLevel]||'-';
}
const LEVEL_CLASS={1:'lv-1',2:'lv-2',3:'lv-3',4:'lv-4'};
const LEVEL_NAME={1:'🟢 Sơ cấp',2:'🔵 Trung cấp',3:'🟣 Cao cấp',4:'🔴 TOPIK'};
function renderCard(){
  if(!fcWords.length){
    document.getElementById('fc-word').textContent='Không có từ';
    document.getElementById('fc-roman').textContent='';
    document.getElementById('fc-meaning').textContent='';
    document.getElementById('fc-ex-kor').textContent='';
    document.getElementById('fc-ex-viet').textContent='';
    document.getElementById('fc-grammar').textContent='';
    return;
  }
  const w=fcWords[fcIndex];
  document.getElementById('fc-index').textContent=fcIndex+1;
  document.getElementById('fc-total').textContent=fcWords.length;
  document.getElementById('fc-word').textContent=w.korean||'';
  document.getElementById('fc-roman').textContent=w.romanization||'';
  document.getElementById('fc-meaning').textContent=w.meaning||'';
  document.getElementById('fc-ex-kor').textContent=w.example_kor||'';
  document.getElementById('fc-ex-viet').textContent=w.example_viet||'';
  document.getElementById('fc-grammar').textContent=w.grammar||'';
  ['fc-tag-label','fc-tag-b'].forEach(id=>document.getElementById(id).textContent=w.tag||'');
  const lc=LEVEL_CLASS[w.level]||'lv-1';
  const ln=LEVEL_NAME[w.level]||'';
  ['fc-level-label','fc-level-b'].forEach(id=>{
    const el=document.getElementById(id);
    el.textContent=ln; el.className='card-level '+lc;
  });
  document.getElementById('fc-progress').style.width=((fcIndex+1)/fcWords.length*100).toFixed(1)+'%';
  document.getElementById('stat-learned').textContent=fcLearned.size;
}
function flipCard(){document.getElementById('flip-card').classList.toggle('flipped');}
function nextCard(){fcIndex=(fcIndex+1)%fcWords.length;document.getElementById('flip-card').classList.remove('flipped');renderCard();}
function prevCard(){fcIndex=(fcIndex-1+fcWords.length)%fcWords.length;document.getElementById('flip-card').classList.remove('flipped');renderCard();}
function shuffleCards(){fcWords.sort(()=>Math.random()-.5);fcIndex=0;document.getElementById('flip-card').classList.remove('flipped');renderCard();showToast('🔀 Đã xáo trộn!');}
function markCard(known){
  const w=fcWords[fcIndex];
  if(known){fcLearned.add(w.korean);showToast('✓ Đã nhớ!');}
  else{fcLearned.delete(w.korean);showToast('✗ Chưa nhớ');}
  document.getElementById('stat-learned').textContent=fcLearned.size;
  nextCard();
}
function speakCurrent(){if(fcWords[fcIndex])speak(fcWords[fcIndex].korean);}

// ══════════════════════════════════════════════════════════════
//  QUIZ
// ══════════════════════════════════════════════════════════════
function startQuiz(){
  const lv=document.getElementById('quiz-level').value;
  quizWords=(lv?words.filter(w=>w.level===lv):[...words]).sort(()=>Math.random()-.5);
  quizIndex=0;quizCorrect=0;quizWrong=0;
  updateQuizScore();
  document.getElementById('q-total').textContent=quizWords.length;
  renderQuestion();
}
function updateQuizScore(){
  document.getElementById('q-correct').textContent=quizCorrect;
  document.getElementById('q-wrong').textContent=quizWrong;
  document.getElementById('q-num').textContent=quizIndex;
}
function renderQuestion(){
  const area=document.getElementById('quiz-area');
  if(quizIndex>=quizWords.length){
    const pct=Math.round(quizCorrect/quizWords.length*100);
    area.innerHTML=`<div class="quiz-result">
      <div class="big">${pct}%</div>
      <h2>${pct>=80?'🎉 Xuất sắc!':pct>=60?'👏 Khá tốt!':'📚 Cần ôn thêm!'}</h2>
      <p>Đúng: <strong>${quizCorrect}</strong> / Sai: <strong>${quizWrong}</strong> / Tổng: <strong>${quizWords.length}</strong></p>
      <br><button class="btn btn-primary" onclick="startQuiz()">↺ Làm lại</button>
    </div>`;
    return;
  }
  const w=quizWords[quizIndex];
  const opts=[w];
  const pool=words.filter(x=>x.korean!==w.korean);
  while(opts.length<4&&pool.length){const i=Math.floor(Math.random()*pool.length);opts.push(pool.splice(i,1)[0]);}
  opts.sort(()=>Math.random()-.5);
  area.innerHTML=`
    <div class="quiz-question-box">
      <div class="quiz-q-label">Từ này có nghĩa là gì?</div>
      <div class="quiz-word">${w.korean}</div>
      <div class="quiz-roman">${w.romanization||''}</div>
    </div>
    <div class="quiz-options">
      ${opts.map(o=>`<button class="quiz-opt" onclick="selectOpt(this,'${o.korean.replace(/'/g,"\\'")}','${w.korean.replace(/'/g,"\\'")}')">${o.meaning}</button>`).join('')}
    </div>
    <div id="quiz-fb"></div>`;
}
function selectOpt(el,chosen,correct){
  document.querySelectorAll('.quiz-opt').forEach(b=>b.disabled=true);
  const fb=docu
