
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>한국어 단어장 – Học Từ Vựng Tiếng Hàn</title>
  :root {
    --bg: #0f0f13;
    --surface: #1a1a24;
    --surface2: #23232f;
    --border: #2e2e3e;
    --accent: #c084fc;
    --accent2: #818cf8;
    --accent3: #34d399;
    --danger: #f87171;
    --text: #e2e8f0;
    --text2: #94a3b8;
    --text3: #64748b;
    --korean: 'Noto Sans KR', sans-serif;
    --body: 'Be Vietnam Pro', sans-serif;
    --radius: 16px;
    --radius-sm: 8px;
  }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--body);
    min-height: 100vh;
    display: flex;
    flex-direction: column;
  }

  /* ── Header ── */
  header {
    padding: 18px 28px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    border-bottom: 1px solid var(--border);
    background: var(--surface);
    position: sticky;
    top: 0;
    z-index: 100;
  }
  .logo {
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .logo-symbol {
    font-family: var(--korean);
    font-size: 1.7rem;
    font-weight: 700;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .logo-text { font-size: .85rem; color: var(--text2); line-height: 1.3; }
  .logo-text strong { display: block; color: var(--text); font-size: 1rem; }

  .header-stats {
    display: flex;
    gap: 20px;
    font-size: .8rem;
    color: var(--text2);
  }
  .stat { text-align: center; }
  .stat span { display: block; font-size: 1.2rem; font-weight: 700; color: var(--accent); }

  /* ── Upload zone ── */
  #upload-screen {
    flex: 1;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 32px;
    padding: 40px 20px;
  }
  .upload-hero {
    text-align: center;
  }
  .upload-hero h1 {
    font-family: var(--korean);
    font-size: clamp(2rem, 5vw, 3.5rem);
    font-weight: 700;
    background: linear-gradient(135deg, var(--accent), var(--accent2), var(--accent3));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin-bottom: 8px;
  }
  .upload-hero p { color: var(--text2); font-size: 1rem; }
  .drop-zone {
    width: min(520px, 90vw);
    border: 2px dashed var(--border);
    border-radius: var(--radius);
    padding: 48px 32px;
    text-align: center;
    cursor: pointer;
    transition: all .3s;
    background: var(--surface);
  }
  .drop-zone:hover, .drop-zone.drag { border-color: var(--accent); background: #1e1a2e; }
  .drop-zone .icon { font-size: 3rem; margin-bottom: 12px; }
  .drop-zone p { color: var(--text2); margin-bottom: 16px; font-size: .9rem; }
  .btn-upload {
    display: inline-block;
    padding: 10px 24px;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    color: #fff;
    border: none;
    border-radius: 50px;
    font-family: var(--body);
    font-size: .9rem;
    font-weight: 600;
    cursor: pointer;
    transition: opacity .2s, transform .2s;
  }
  .btn-upload:hover { opacity: .85; transform: translateY(-1px); }

  .format-hint {
    width: min(520px, 90vw);
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 20px 24px;
  }
  .format-hint h3 { font-size: .85rem; color: var(--accent); margin-bottom: 10px; text-transform: uppercase; letter-spacing: .05em; }
  .format-hint code {
    display: block;
    background: var(--bg);
    border-radius: var(--radius-sm);
    padding: 12px 14px;
    font-family: monospace;
    font-size: .8rem;
    color: var(--accent3);
    white-space: pre;
    overflow-x: auto;
    margin-top: 8px;
  }
  .format-hint p { font-size: .8rem; color: var(--text2); margin-top: 8px; }

  /* ── Main App ── */
  #app-screen { display: none; flex: 1; flex-direction: column; }

  /* Tabs */
  .tabs {
    display: flex;
    gap: 4px;
    padding: 16px 24px 0;
    background: var(--surface);
    border-bottom: 1px solid var(--border);
  }
  .tab {
    padding: 10px 20px;
    border: none;
    background: transparent;
    color: var(--text2);
    font-family: var(--body);
    font-size: .9rem;
    font-weight: 600;
    cursor: pointer;
    border-radius: var(--radius-sm) var(--radius-sm) 0 0;
    transition: all .2s;
    border-bottom: 3px solid transparent;
    display: flex;
    align-items: center;
    gap: 6px;
  }
  .tab:hover { color: var(--text); background: var(--surface2); }
  .tab.active { color: var(--accent); border-bottom-color: var(--accent); background: var(--bg); }

  .panel { display: none; flex: 1; padding: 28px 24px; }
  .panel.active { display: flex; flex-direction: column; gap: 20px; }

  /* ── Flashcard ── */
  .card-controls {
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 12px;
  }
  .card-counter { color: var(--text2); font-size: .9rem; }
  .card-counter strong { color: var(--text); }
  .controls-row { display: flex; gap: 8px; flex-wrap: wrap; }

  .btn {
    padding: 9px 18px;
    border: 1px solid var(--border);
    background: var(--surface);
    color: var(--text);
    border-radius: 50px;
    font-family: var(--body);
    font-size: .85rem;
    font-weight: 600;
    cursor: pointer;
    transition: all .2s;
    display: inline-flex;
    align-items: center;
    gap: 6px;
  }
  .btn:hover { background: var(--surface2); border-color: var(--accent); }
  .btn-primary {
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    border-color: transparent;
    color: #fff;
  }
  .btn-primary:hover { opacity: .85; border-color: transparent; }
  .btn-success { background: var(--accent3); border-color: transparent; color: #0f0f13; }
  .btn-danger  { background: var(--danger);  border-color: transparent; color: #fff; }
  .btn-sm { padding: 6px 14px; font-size: .78rem; }

  /* Flip card */
  .flip-wrapper {
    perspective: 1200px;
    width: 100%;
    max-width: 620px;
    margin: 0 auto;
  }
  .flip-card {
    width: 100%;
    height: 340px;
    position: relative;
    transform-style: preserve-3d;
    transition: transform .6s cubic-bezier(.4,0,.2,1);
    cursor: pointer;
  }
  .flip-card.flipped { transform: rotateY(180deg); }
  .card-face {
    position: absolute;
    inset: 0;
    backface-visibility: hidden;
    border-radius: var(--radius);
    border: 1px solid var(--border);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 12px;
    padding: 32px;
    background: var(--surface);
  }
  .card-face.back {
    transform: rotateY(180deg);
    background: linear-gradient(135deg, #1e1a2e, #1a1a24);
    border-color: var(--accent);
  }
  .card-word {
    font-family: var(--korean);
    font-size: clamp(2.5rem, 6vw, 4rem);
    font-weight: 700;
    color: var(--text);
  }
  .card-roman { font-size: 1.1rem; color: var(--accent2); letter-spacing: .04em; }
  .card-meaning { font-size: 1.3rem; font-weight: 600; color: var(--text); }
  .card-example {
    font-size: .85rem;
    color: var(--text2);
    text-align: center;
    font-style: italic;
    line-height: 1.6;
  }
  .card-example .kor { color: var(--accent3); font-style: normal; font-family: var(--korean); }
  .card-tag {
    font-size: .72rem;
    padding: 3px 10px;
    border-radius: 50px;
    background: var(--bg);
    color: var(--accent);
    border: 1px solid var(--accent);
    position: absolute;
    top: 14px;
    left: 14px;
  }
  .card-hint {
    position: absolute;
    bottom: 14px;
    font-size: .72rem;
    color: var(--text3);
  }

  .nav-row {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 16px;
    margin-top: 4px;
  }
  .nav-row .btn { min-width: 48px; justify-content: center; }

  .progress-bar {
    width: 100%;
    max-width: 620px;
    margin: 0 auto;
    height: 4px;
    background: var(--border);
    border-radius: 4px;
    overflow: hidden;
  }
  .progress-fill {
    height: 100%;
    background: linear-gradient(90deg, var(--accent), var(--accent2));
    border-radius: 4px;
    transition: width .4s;
  }

  /* ── Stroke Panel ── */
  .stroke-search {
    display: flex;
    gap: 8px;
    flex-wrap: wrap;
    align-items: center;
  }
  .stroke-search input {
    flex: 1;
    min-width: 120px;
    padding: 9px 14px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 50px;
    color: var(--text);
    font-family: var(--korean);
    font-size: 1.1rem;
    outline: none;
    transition: border-color .2s;
  }
  .stroke-search input:focus { border-color: var(--accent); }

  .stroke-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(80px, 1fr));
    gap: 10px;
  }
  .stroke-thumb {
    border: 1px solid var(--border);
    border-radius: var(--radius-sm);
    padding: 10px 6px 6px;
    text-align: center;
    cursor: pointer;
    transition: all .2s;
    background: var(--surface);
  }
  .stroke-thumb:hover, .stroke-thumb.active { border-color: var(--accent); background: #1e1a2e; }
  .stroke-thumb .syl {
    font-family: var(--korean);
    font-size: 1.4rem;
    display: block;
  }
  .stroke-thumb .mean {
    font-size: .65rem;
    color: var(--text2);
    margin-top: 2px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  .stroke-display {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 16px;
  }
  .stroke-display h2 {
    font-family: var(--korean);
    font-size: 1.4rem;
    color: var(--text);
  }
  .stroke-canvas-wrap {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 16px;
  }
  #stroke-canvas {
    border-radius: var(--radius-sm);
    background: #fff;
  }
  .stroke-btns { display: flex; gap: 8px; flex-wrap: wrap; justify-content: center; }

  /* ── Quiz Panel ── */
  .quiz-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 12px;
  }
  .quiz-score-row {
    display: flex;
    gap: 12px;
  }
  .score-chip {
    padding: 6px 14px;
    border-radius: 50px;
    font-size: .82rem;
    font-weight: 700;
  }
  .score-correct { background: #162421; color: var(--accent3); border: 1px solid var(--accent3); }
  .score-wrong   { background: #211616; color: var(--danger);  border: 1px solid var(--danger); }

  .quiz-question-box {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 36px 28px;
    text-align: center;
  }
  .quiz-q-label { font-size: .8rem; color: var(--text3); text-transform: uppercase; letter-spacing: .08em; margin-bottom: 12px; }
  .quiz-word {
    font-family: var(--korean);
    font-size: clamp(2.5rem, 6vw, 4.5rem);
    font-weight: 700;
    color: var(--text);
  }
  .quiz-roman { font-size: 1rem; color: var(--accent2); margin-top: 4px; }
  .quiz-options {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }
  .quiz-opt {
    padding: 16px 14px;
    background: var(--surface);
    border: 2px solid var(--border);
    border-radius: var(--radius-sm);
    color: var(--text);
    font-family: var(--body);
    font-size: .95rem;
    font-weight: 600;
    cursor: pointer;
    transition: all .2s;
    text-align: left;
  }
  .quiz-opt:hover:not(:disabled) { border-color: var(--accent); background: #1e1a2e; }
  .quiz-opt.correct { border-color: var(--accent3); background: #162421; color: var(--accent3); }
  .quiz-opt.wrong   { border-color: var(--danger);  background: #211616; color: var(--danger); }
  .quiz-opt:disabled { cursor: default; }

  .quiz-feedback {
    text-align: center;
    padding: 14px;
    border-radius: var(--radius-sm);
    font-size: .95rem;
    font-weight: 600;
  }
  .quiz-feedback.correct { background: #162421; color: var(--accent3); }
  .quiz-feedback.wrong   { background: #211616; color: var(--danger); }

  .quiz-result {
    text-align: center;
    padding: 40px 20px;
  }
  .quiz-result h2 { font-size: 2rem; margin-bottom: 8px; }
  .quiz-result .big { font-size: 4rem; font-weight: 700; }
  .quiz-result p { color: var(--text2); margin: 8px 0; }

  /* ── Word List ── */
  .list-filters {
    display: flex;
    gap: 8px;
    flex-wrap: wrap;
    align-items: center;
  }
  .list-filters input {
    flex: 1;
    min-width: 160px;
    padding: 9px 14px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 50px;
    color: var(--text);
    font-family: var(--body);
    font-size: .9rem;
    outline: none;
    transition: border-color .2s;
  }
  .list-filters input:focus { border-color: var(--accent); }

  .word-table {
    border: 1px solid var(--border);
    border-radius: var(--radius);
    overflow: hidden;
  }
  .word-table table { width: 100%; border-collapse: collapse; }
  .word-table th {
    padding: 10px 16px;
    text-align: left;
    font-size: .75rem;
    color: var(--text3);
    text-transform: uppercase;
    letter-spacing: .07em;
    background: var(--surface);
    border-bottom: 1px solid var(--border);
  }
  .word-table td {
    padding: 12px 16px;
    font-size: .9rem;
    border-bottom: 1px solid var(--border);
    vertical-align: middle;
  }
  .word-table tr:last-child td { border-bottom: none; }
  .word-table tr:hover td { background: var(--surface); }
  .word-table .kor-cell { font-family: var(--korean); font-size: 1.1rem; font-weight: 700; }
  .word-table .roman-cell { color: var(--accent2); font-size: .82rem; }
  .word-table .tag-cell span {
    font-size: .7rem;
    padding: 2px 8px;
    border-radius: 50px;
    background: var(--bg);
    color: var(--accent);
    border: 1px solid var(--accent);
  }
  .play-btn {
    background: transparent;
    border: 1px solid var(--border);
    color: var(--text2);
    border-radius: 50%;
    width: 30px; height: 30px;
    display: flex; align-items: center; justify-content: center;
    cursor: pointer;
    font-size: .9rem;
    transition: all .2s;
  }
  .play-btn:hover { border-color: var(--accent3); color: var(--accent3); }

  /* ── Misc ── */
  .empty-state {
    text-align: center;
    padding: 48px 20px;
    color: var(--text3);
    font-size: .95rem;
  }
  .empty-state .big { font-size: 2.5rem; margin-bottom: 8px; }

  .toast {
    position: fixed;
    bottom: 24px;
    left: 50%;
    transform: translateX(-50%) translateY(80px);
    background: var(--surface2);
    border: 1px solid var(--border);
    color: var(--text);
    padding: 10px 20px;
    border-radius: 50px;
    font-size: .85rem;
    font-weight: 600;
    z-index: 999;
    transition: transform .3s;
    pointer-events: none;
  }
  .toast.show { transform: translateX(-50%) translateY(0); }

  select {
    padding: 9px 14px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 50px;
    color: var(--text);
    font-family: var(--body);
    font-size: .85rem;
    outline: none;
    cursor: pointer;
  }

  @media (max-width: 540px) {
    .tabs { overflow-x: auto; white-space: nowrap; gap: 0; padding: 14px 12px 0; }
    .tab { padding: 8px 12px; font-size: .8rem; }
    .panel { padding: 20px 14px; }
    .quiz-options { grid-template-columns: 1fr; }
    header { padding: 14px 16px; }
    .header-stats { gap: 12px; }
  }
</style>
</head>
<body>

<!-- ══════════ HEADER ══════════ -->
<header>
  <div class="logo">
    <div class="logo-symbol">한</div>
    <div class="logo-text">
      <strong>한국어 단어장</strong>
      Học từ vựng tiếng Hàn
    </div>
  </div>
  <div class="header-stats" id="header-stats" style="display:none">
    <div class="stat"><span id="stat-total">0</span>Từ</div>
    <div class="stat"><span id="stat-learned">0</span>Đã học</div>
  </div>
</header>

<!-- ══════════ UPLOAD SCREEN ══════════ -->
<div id="upload-screen">
  <div class="upload-hero">
    <h1>한국어 단어장</h1>
    <p>Tải lên file từ vựng để bắt đầu học</p>
  </div>

  <div class="drop-zone" id="drop-zone">
    <div class="icon">📂</div>
    <p>Kéo thả file JSON / CSV vào đây</p>
    <button class="btn-upload" onclick="document.getElementById('file-input').click()">Chọn file</button>
    <input type="file" id="file-input" accept=".json,.csv" style="display:none">
  </div>

  <div class="format-hint">
    <h3>📋 Định dạng file hỗ trợ</h3>
    <p><strong>JSON</strong> – Mảng các đối tượng từ vựng:</p>
    <code>[
  {
    "korean": "안녕하세요",
    "romanization": "annyeonghaseyo",
    "meaning": "Xin chào",
    "example_kor": "안녕하세요, 저는 민준이에요.",
    "example_viet": "Xin chào, tôi là Min-jun.",
    "tag": "Chào hỏi"
  }
]</code>
    <p><strong>CSV</strong> – Cột: korean, romanization, meaning, example_kor, example_viet, tag</p>
  </div>

  <button class="btn btn-primary" onclick="loadDemo()">🎯 Dùng dữ liệu mẫu</button>
</div>

<!-- ══════════ APP SCREEN ══════════ -->
<div id="app-screen">
  <!-- Tabs -->
  <div class="tabs">
    <button class="tab active" onclick="switchTab('flashcard')">🃏 Flashcard</button>
    <button class="tab" onclick="switchTab('quiz')">✏️ Trắc nghiệm</button>
    <button class="tab" onclick="switchTab('stroke')">✍️ Nét chữ</button>
    <button class="tab" onclick="switchTab('list')">📋 Danh sách</button>
    <button class="tab" onclick="resetApp()" style="margin-left:auto; color: var(--text3);">↩ Đổi file</button>
  </div>

  <!-- ── Flashcard Panel ── -->
  <div class="panel active" id="panel-flashcard">
    <div class="card-controls">
      <div class="card-counter">Thẻ <strong id="fc-index">1</strong> / <strong id="fc-total">0</strong></div>
      <div class="controls-row">
        <button class="btn btn-sm" onclick="shuffleCards()">🔀 Xáo trộn</button>
        <button class="btn btn-sm" onclick="speakCurrent()">🔊 Phát âm</button>
        <select id="fc-filter" onchange="applyFilter()">
          <option value="">Tất cả chủ đề</option>
        </select>
      </div>
    </div>

    <div class="progress-bar">
      <div class="progress-fill" id="fc-progress"></div>
    </div>

    <div class="flip-wrapper">
      <div class="flip-card" id="flip-card" onclick="flipCard()">
        <div class="card-face front">
          <div class="card-tag" id="fc-tag"></div>
          <div class="card-word" id="fc-word"></div>
          <div class="card-roman" id="fc-roman"></div>
          <div class="card-hint">Nhấn để lật xem nghĩa</div>
        </div>
        <div class="card-face back">
          <div class="card-tag" id="fc-tag-b"></div>
          <div class="card-meaning" id="fc-meaning"></div>
          <div class="card-example">
            <span class="kor" id="fc-ex-kor"></span>
            <span id="fc-ex-viet"></span>
          </div>
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

  <!-- ── Quiz Panel ── -->
  <div class="panel" id="panel-quiz">
    <div class="quiz-header">
      <div>
        <div style="font-size:1.1rem;font-weight:700;">Trắc nghiệm</div>
        <div style="font-size:.82rem;color:var(--text2)">Câu <span id="q-num">0</span> / <span id="q-total">0</span></div>
      </div>
      <div class="quiz-score-row">
        <div class="score-chip score-correct">✓ <span id="q-correct">0</span></div>
        <div class="score-chip score-wrong">✗ <span id="q-wrong">0</span></div>
        <button class="btn btn-sm" onclick="startQuiz()">↺ Làm lại</button>
      </div>
    </div>

    <div id="quiz-area"></div>
  </div>

  <!-- ── Stroke Panel ── -->
  <div class="panel" id="panel-stroke">
    <div class="stroke-search">
      <input type="text" id="stroke-search-inp" placeholder="Tìm từ tiếng Hàn..." oninput="filterStroke(this.value)">
      <button class="btn btn-sm" onclick="clearStrokeSearch()">✕ Xoá</button>
    </div>
    <div class="stroke-grid" id="stroke-grid"></div>
    <div class="stroke-display" id="stroke-display" style="display:none">
      <h2 id="stroke-word-title"></h2>
      <div class="stroke-canvas-wrap">
        <canvas id="stroke-canvas" width="280" height="280"></canvas>
        <div class="stroke-btns">
          <button class="btn btn-sm btn-primary" onclick="animateStrokes()">▶ Xem nét viết</button>
          <button class="btn btn-sm" onclick="stopAnimation()">⏹ Dừng</button>
          <button class="btn btn-sm" onclick="speakStroke()">🔊 Phát âm</button>
        </div>
        <div id="stroke-info" style="font-size:.82rem;color:var(--text2);text-align:center;"></div>
      </div>
    </div>
  </div>

  <!-- ── List Panel ── -->
  <div class="panel" id="panel-list">
    <div class="list-filters">
      <input type="text" id="list-search" placeholder="Tìm kiếm từ..." oninput="renderList()">
      <select id="list-tag" onchange="renderList()"><option value="">Tất cả chủ đề</option></select>
    </div>
    <div class="word-table" id="word-table"></div>
  </div>
</div>

<!-- Toast -->
<div class="toast" id="toast"></div>

<script>
// ═══════════════════════════════════════════════
//  DATA & STATE
// ═══════════════════════════════════════════════
let words = [];
let fcWords = [];
let fcIndex = 0;
let fcLearned = new Set();
let quizWords = [];
let quizIndex = 0;
let quizCorrect = 0;
let quizWrong = 0;
let strokeWord = null;
let strokeCtx = null;
let animFrame = null;

// ═══════════════════════════════════════════════
//  FILE UPLOAD
// ═══════════════════════════════════════════════
const dropZone = document.getElementById('drop-zone');
const fileInput = document.getElementById('file-input');

dropZone.addEventListener('dragover', e => { e.preventDefault(); dropZone.classList.add('drag'); });
dropZone.addEventListener('dragleave', () => dropZone.classList.remove('drag'));
dropZone.addEventListener('drop', e => {
  e.preventDefault(); dropZone.classList.remove('drag');
  const f = e.dataTransfer.files[0]; if (f) readFile(f);
});
fileInput.addEventListener('change', e => { if (e.target.files[0]) readFile(e.target.files[0]); });

function readFile(f) {
  const r = new FileReader();
  r.onload = ev => {
    try {
      const ext = f.name.split('.').pop().toLowerCase();
      if (ext === 'json') {
        words = JSON.parse(ev.target.result);
      } else {
        words = parseCSV(ev.target.result);
      }
      if (!words.length) { showToast('File rỗng hoặc sai định dạng!'); return; }
      initApp();
    } catch(e) { showToast('Lỗi đọc file: ' + e.message); }
  };
  r.readAsText(f, 'utf-8');
}

function parseCSV(text) {
  const lines = text.trim().split('\n');
  const headers = lines[0].split(',').map(h => h.trim().replace(/^"(.*)"$/, '$1'));
  return lines.slice(1).map(line => {
    const vals = line.match(/(".*?"|[^,]+|(?<=,)(?=,))/g) || [];
    const obj = {};
    headers.forEach((h, i) => {
      obj[h] = (vals[i] || '').trim().replace(/^"(.*)"$/, '$1');
    });
    return obj;
  }).filter(o => o.korean);
}

function loadDemo() {
  words = [
    { korean: "안녕하세요", romanization: "annyeonghaseyo", meaning: "Xin chào (lịch sự)", example_kor: "안녕하세요, 만나서 반가워요!", example_viet: "Xin chào, rất vui được gặp bạn!", tag: "Chào hỏi" },
    { korean: "감사합니다", romanization: "gamsahamnida", meaning: "Cảm ơn", example_kor: "도와주셔서 감사합니다.", example_viet: "Cảm ơn vì đã giúp đỡ tôi.", tag: "Chào hỏi" },
    { korean: "미안합니다", romanization: "mianhamnida", meaning: "Xin lỗi", example_kor: "늦어서 미안합니다.", example_viet: "Xin lỗi vì đến trễ.", tag: "Chào hỏi" },
    { korean: "사랑해요", romanization: "saranghaeyo", meaning: "Tôi yêu bạn", example_kor: "당신을 사랑해요.", example_viet: "Tôi yêu bạn.", tag: "Tình cảm" },
    { korean: "밥", romanization: "bap", meaning: "Cơm / Bữa ăn", example_kor: "밥 먹었어요?", example_viet: "Bạn ăn cơm chưa?", tag: "Ẩm thực" },
    { korean: "물", romanization: "mul", meaning: "Nước", example_kor: "물 한 잔 주세요.", example_viet: "Cho tôi một ly nước.", tag: "Ẩm thực" },
    { korean: "학교", romanization: "hakgyo", meaning: "Trường học", example_kor: "학교에 가요.", example_viet: "Tôi đi đến trường.", tag: "Giáo dục" },
    { korean: "친구", romanization: "chingu", meaning: "Bạn bè", example_kor: "제 친구예요.", example_viet: "Đây là bạn tôi.", tag: "Xã hội" },
    { korean: "가족", romanization: "gajok", meaning: "Gia đình", example_kor: "가족을 사랑해요.", example_viet: "Tôi yêu gia đình.", tag: "Xã hội" },
    { korean: "집", romanization: "jip", meaning: "Nhà", example_kor: "집에 가고 싶어요.", example_viet: "Tôi muốn về nhà.", tag: "Địa điểm" },
    { korean: "버스", romanization: "beoseu", meaning: "Xe buýt", example_kor: "버스 타고 가요.", example_viet: "Tôi đi bằng xe buýt.", tag: "Di chuyển" },
    { korean: "한국", romanization: "hanguk", meaning: "Hàn Quốc", example_kor: "한국에 살아요.", example_viet: "Tôi sống ở Hàn Quốc.", tag: "Địa danh" },
  ];
  initApp();
}

function resetApp() {
  if (!confirm('Quay lại màn hình tải file?')) return;
  document.getElementById('upload-screen').style.display = 'flex';
  document.getElementById('app-screen').style.display = 'none';
  document.getElementById('header-stats').style.display = 'none';
  words = []; fcWords = []; fcLearned = new Set();
  fileInput.value = '';
}

// ═══════════════════════════════════════════════
//  INIT
// ═══════════════════════════════════════════════
function initApp() {
  document.getElementById('upload-screen').style.display = 'none';
  document.getElementById('app-screen').style.display = 'flex';
  document.getElementById('header-stats').style.display = 'flex';
  document.getElementById('stat-total').textContent = words.length;

  // Tags
  const tags = [...new Set(words.map(w => w.tag).filter(Boolean))];
  const fcFilter = document.getElementById('fc-filter');
  const listTag = document.getElementById('list-tag');
  fcFilter.innerHTML = '<option value="">Tất cả chủ đề</option>';
  listTag.innerHTML = '<option value="">Tất cả chủ đề</option>';
  tags.forEach(t => {
    fcFilter.innerHTML += `<option value="${t}">${t}</option>`;
    listTag.innerHTML += `<option value="${t}">${t}</option>`;
  });

  fcLearned = new Set();
  applyFilter();
  startQuiz();
  renderStrokeGrid(words);
  renderList();
}

// ═══════════════════════════════════════════════
//  TABS
// ═══════════════════════════════════════════════
function switchTab(name) {
  document.querySelectorAll('.tab').forEach((t, i) => {
    const panels = ['flashcard','quiz','stroke','list'];
    t.classList.toggle('active', panels[i] === name);
  });
  document.querySelectorAll('.panel').forEach(p => p.classList.remove('active'));
  document.getElementById('panel-' + name).classList.add('active');
}

// ═══════════════════════════════════════════════
//  FLASHCARD
// ═══════════════════════════════════════════════
function applyFilter() {
  const tag = document.getElementById('fc-filter').value;
  fcWords = tag ? words.filter(w => w.tag === tag) : [...words];
  fcIndex = 0;
  document.getElementById('flip-card').classList.remove('flipped');
  renderCard();
}

function renderCard() {
  if (!fcWords.length) return;
  const w = fcWords[fcIndex];
  document.getElementById('fc-index').textContent = fcIndex + 1;
  document.getElementById('fc-total').textContent = fcWords.length;
  document.getElementById('fc-word').textContent = w.korean || '';
  document.getElementById('fc-roman').textContent = w.romanization || '';
  document.getElementById('fc-meaning').textContent = w.meaning || '';
  document.getElementById('fc-ex-kor').textContent = w.example_kor || '';
  document.getElementById('fc-ex-viet').textContent = w.example_viet || '';
  const tag = w.tag || '';
  document.getElementById('fc-tag').textContent = tag;
  document.getElementById('fc-tag-b').textContent = tag;
  const pct = ((fcIndex + 1) / fcWords.length * 100).toFixed(1);
  document.getElementById('fc-progress').style.width = pct + '%';
  document.getElementById('stat-learned').textContent = fcLearned.size;
}

function flipCard() {
  document.getElementById('flip-card').classList.toggle('flipped');
}

function nextCard() {
  fcIndex = (fcIndex + 1) % fcWords.length;
  document.getElementById('flip-card').classList.remove('flipped');
  renderCard();
}

function prevCard() {
  fcIndex = (fcIndex - 1 + fcWords.length) % fcWords.length;
  document.getElementById('flip-card').classList.remove('flipped');
  renderCard();
}

function shuffleCards() {
  fcWords.sort(() => Math.random() - .5);
  fcIndex = 0;
  document.getElementById('flip-card').classList.remove('flipped');
  renderCard();
  showToast('🔀 Đã xáo trộn!');
}

function markCard(known) {
  const w = fcWords[fcIndex];
  if (known) { fcLearned.add(w.korean); showToast('✓ Đánh dấu đã nhớ!'); }
  else { fcLearned.delete(w.korean); showToast('✗ Đánh dấu chưa nhớ'); }
  document.getElementById('stat-learned').textContent = fcLearned.size;
  nextCard();
}

function speakCurrent() {
  if (fcWords[fcIndex]) speak(fcWords[fcIndex].korean);
}

// ═══════════════════════════════════════════════
//  QUIZ
// ═══════════════════════════════════════════════
function startQuiz() {
  quizWords = [...words].sort(() => Math.random() - .5);
  quizIndex = 0; quizCorrect = 0; quizWrong = 0;
  updateQuizScore();
  document.getElementById('q-total').textContent = quizWords.length;
  renderQuestion();
}

function updateQuizScore() {
  document.getElementById('q-correct').textContent = quizCorrect;
  document.getElementById('q-wrong').textContent = quizWrong;
  document.getElementById('q-num').textContent = quizIndex;
}

function renderQuestion() {
  const area = document.getElementById('quiz-area');
  if (quizIndex >= quizWords.length) {
    const pct = Math.round(quizCorrect / quizWords.length * 100);
    area.innerHTML = `<div class="quiz-result">
      <div class="big">${pct}%</div>
      <h2>${pct >= 70 ? '🎉 Xuất sắc!' : '📚 Cần ôn thêm!'}</h2>
      <p>Đúng: <strong>${quizCorrect}</strong> / Sai: <strong>${quizWrong}</strong> / Tổng: <strong>${quizWords.length}</strong></p>
      <br><button class="btn btn-primary" onclick="startQuiz()">↺ Làm lại</button>
    </div>`;
    return;
  }

  const w = quizWords[quizIndex];
  // 4 options
  const opts = [w];
  const pool = words.filter(x => x.korean !== w.korean);
  while (opts.length < 4 && pool.length) {
    const i = Math.floor(Math.random() * pool.length);
    opts.push(pool.splice(i, 1)[0]);
  }
  opts.sort(() => Math.random() - .5);

  area.innerHTML = `
    <div class="quiz-question-box">
      <div class="quiz-q-label">Từ này có nghĩa là gì?</div>
      <div class="quiz-word">${w.korean}</div>
      <div class="quiz-roman">${w.romanization || ''}</div>
    </div>
    <div class="quiz-options" id="quiz-opts">
      ${opts.map((o, i) => `<button class="quiz-opt" onclick="selectOpt(this, '${o.korean}', '${w.korean}')">${o.meaning || o.korean}</button>`).join('')}
    </div>
    <div id="quiz-fb"></div>
  `;
}

function selectOpt(el, chosen, correct) {
  const btns = document.querySelectorAll('.quiz-opt');
  btns.forEach(b => b.disabled = true);
  const fb = document.getElementById('quiz-fb');
  if (chosen === correct) {
    el.classList.add('correct');
    quizCorrect++;
    fb.className = 'quiz-feedback correct';
    fb.textContent = '✓ Chính xác!';
    speak(correct);
  } else {
    el.classList.add('wrong');
    quizWrong++;
    btns.forEach(b => {
      // highlight correct
      const txt = b.textContent;
      const correctWord = words.find(w => w.korean === correct);
      if (correctWord && txt === (correctWord.meaning || correctWord.korean)) b.classList.add('correct');
    });
    fb.className = 'quiz-feedback wrong';
    fb.textContent = '✗ Sai rồi! Đáp án đúng đã được tô xanh.';
  }
  quizIndex++;
  updateQuizScore();
  setTimeout(() => renderQuestion(), 1400);
}

// ═══════════════════════════════════════════════
//  STROKE (Korean handwriting animation via Canvas)
// ═══════════════════════════════════════════════
function renderStrokeGrid(list) {
  const grid = document.getElementById('stroke-grid');
  grid.innerHTML = list.map((w, i) => `
    <div class="stroke-thumb" onclick="selectStrokeWord(${words.indexOf(w)})">
      <span class="syl">${w.korean}</span>
      <span class="mean">${w.meaning || ''}</span>
    </div>`).join('');
}

function filterStroke(q) {
  const filtered = words.filter(w =>
    w.korean.includes(q) || (w.meaning || '').toLowerCase().includes(q.toLowerCase())
  );
  renderStrokeGrid(filtered);
}

function clearStrokeSearch() {
  document.getElementById('stroke-search-inp').value = '';
  renderStrokeGrid(words);
}

function selectStrokeWord(idx) {
  strokeWord = words[idx];
  document.querySelectorAll('.stroke-thumb').forEach((el, i) => el.classList.remove('active'));
  document.getElementById('stroke-display').style.display = 'flex';
  document.getElementById('stroke-word-title').textContent = strokeWord.korean + ' – ' + (strokeWord.meaning || '');
  document.getElementById('stroke-info').textContent = strokeWord.romanization || '';

  const canvas = document.getElementById('stroke-canvas');
  strokeCtx = canvas.getContext('2d');
  drawKoreanStroke(strokeCtx, strokeWord.korean, canvas.width, canvas.height, false);
}

function animateStrokes() {
  if (!strokeWord) return;
  const canvas = document.getElementById('stroke-canvas');
  strokeCtx = canvas.getContext('2d');
  drawKoreanStroke(strokeCtx, strokeWord.korean, canvas.width, canvas.height, true);
}

function stopAnimation() {
  if (animFrame) { cancelAnimationFrame(animFrame); animFrame = null; }
  if (strokeCtx && strokeWord) {
    const canvas = document.getElementById('stroke-canvas');
    drawKoreanStroke(strokeCtx, strokeWord.korean, canvas.width, canvas.height, false);
  }
}

// Korean stroke animation using Canvas (simplified visual)
function drawKoreanStroke(ctx, text, W, H, animate) {
  if (animFrame) { cancelAnimationFrame(animFrame); animFrame = null; }
  ctx.clearRect(0, 0, W, H);

  // Background
  ctx.fillStyle = '#fff';
  ctx.fillRect(0, 0, W, H);

  // Grid lines
  ctx.strokeStyle = '#e0e0e0';
  ctx.lineWidth = 1;
  ctx.setLineDash([4, 4]);
  ctx.beginPath();
  ctx.moveTo(W/2, 0); ctx.lineTo(W/2, H);
  ctx.moveTo(0, H/2); ctx.lineTo(W, H/2);
  ctx.stroke();
  ctx.setLineDash([]);

  // Border
  ctx.strokeStyle = '#ccc';
  ctx.strokeRect(0, 0, W, H);

  if (!animate) {
    // Static draw
    ctx.fillStyle = '#1a1a2e';
    ctx.font = `bold ${Math.min(W, H) * 0.55}px 'Noto Sans KR', sans-serif`;
    ctx.textAlign = 'center';
    ctx.textBaseline = 'middle';
    ctx.fillText(text.charAt(0), W/2, H/2);
    if (text.length > 1) {
      ctx.font = `${Math.min(W,H)*0.18}px 'Noto Sans KR', sans-serif`;
      ctx.fillStyle = '#666';
      ctx.fillText(text.slice(1), W/2, H*0.82);
    }
  } else {
    // Animate: reveal stroke via clip
    let progress = 0;
    const total = 100;

    function frame() {
      ctx.clearRect(0, 0, W, H);
      ctx.fillStyle = '#fff';
      ctx.fillRect(0, 0, W, H);

      // Grid
      ctx.strokeStyle = '#e0e0e0';
      ctx.lineWidth = 1;
      ctx.setLineDash([4, 4]);
      ctx.beginPath();
      ctx.moveTo(W/2, 0); ctx.lineTo(W/2, H);
      ctx.moveTo(0, H/2); ctx.lineTo(W, H/2);
      ctx.stroke();
      ctx.setLineDash([]);
      ctx.strokeStyle = '#ccc';
      ctx.strokeRect(0, 0, W, H);

      // Sweep reveal
      const angle = (progress / total) * Math.PI * 2 - Math.PI / 2;
      ctx.save();
      ctx.beginPath();
      ctx.moveTo(W/2, H/2);
      ctx.arc(W/2, H/2, Math.max(W,H), -Math.PI/2, angle);
      ctx.closePath();
      ctx.clip();

      ctx.fillStyle = '#c084fc';
      ctx.font = `bold ${Math.min(W, H) * 0.55}px 'Noto Sans KR', sans-serif`;
      ctx.textAlign = 'center';
      ctx.textBaseline = 'middle';
      ctx.fillText(text.charAt(0), W/2, H/2);
      ctx.restore();

      // Shadow char
      ctx.fillStyle = '#ddd';
      ctx.font = `bold ${Math.min(W, H) * 0.55}px 'Noto Sans KR', sans-serif`;
      ctx.textAlign = 'center';
      ctx.textBaseline = 'middle';
      ctx.save();
      ctx.globalCompositeOperation = 'destination-over';
      ctx.fillText(text.charAt(0), W/2, H/2);
      ctx.restore();

      progress++;
      if (progress <= total) animFrame = requestAnimationFrame(frame);
      else {
        // Final static
        ctx.fillStyle = '#1a1a2e';
        ctx.font = `bold ${Math.min(W, H) * 0.55}px 'Noto Sans KR', sans-serif`;
        ctx.textAlign = 'center';
        ctx.textBaseline = 'middle';
        ctx.fillText(text.charAt(0), W/2, H/2);
        if (text.length > 1) {
          ctx.font = `${Math.min(W,H)*0.18}px 'Noto Sans KR', sans-serif`;
          ctx.fillStyle = '#666';
          ctx.fillText(text.slice(1), W/2, H*0.82);
        }
        animFrame = null;
      }
    }
    animFrame = requestAnimationFrame(frame);
  }
}

function speakStroke() {
  if (strokeWord) speak(strokeWord.korean);
}

// ═══════════════════════════════════════════════
//  WORD LIST
// ═══════════════════════════════════════════════
function renderList() {
  const q = (document.getElementById('list-search').value || '').toLowerCase();
  const tag = document.getElementById('list-tag').value;
  const filtered = words.filter(w => {
    const match = !q || w.korean.includes(q) || (w.meaning||'').toLowerCase().includes(q) || (w.romanization||'').toLowerCase().includes(q);
    const tagOk = !tag || w.tag === tag;
    return match && tagOk;
  });

  const tbl = document.getElementById('word-table');
  if (!filtered.length) {
    tbl.innerHTML = '<div class="empty-state"><div class="big">🔍</div>Không tìm thấy từ nào</div>';
    return;
  }
  tbl.innerHTML = `<table>
    <thead><tr>
      <th>Tiếng Hàn</th>
      <th>Phiên âm</th>
      <th>Nghĩa</th>
      <th>Chủ đề</th>
      <th></th>
    </tr></thead>
    <tbody>
    ${filtered.map(w => `<tr>
      <td><div class="kor-cell">${w.korean}</div></td>
      <td><div class="roman-cell">${w.romanization||''}</div></td>
      <td>${w.meaning||''}</td>
      <td class="tag-cell">${w.tag ? `<span>${w.tag}</span>` : ''}</td>
      <td><button class="play-btn" onclick="speak('${w.korean.replace(/'/g, "\\'")}')">🔊</button></td>
    </tr>`).join('')}
    </tbody>
  </table>`;
}

// ═══════════════════════════════════════════════
//  TTS (Web Speech API – Korean)
// ═══════════════════════════════════════════════
function speak(text) {
  if (!text) return;
  if ('speechSynthesis' in window) {
    window.speechSynthesis.cancel();
    const utt = new SpeechSynthesisUtterance(text);
    utt.lang = 'ko-KR';
    utt.rate = 0.85;
    // Try to find a Korean voice
    const voices = window.speechSynthesis.getVoices();
    const korVoice = voices.find(v => v.lang.startsWith('ko'));
    if (korVoice) utt.voice = korVoice;
    window.speechSynthesis.speak(utt);
  } else {
    showToast('Trình duyệt không hỗ trợ phát âm');
  }
}

// Preload voices
if ('speechSynthesis' in window) {
  window.speechSynthesis.getVoices();
  window.speechSynthesis.addEventListener('voiceschanged', () => window.speechSynthesis.getVoices());
}

// ═══════════════════════════════════════════════
//  TOAST
// ═══════════════════════════════════════════════
let toastTimer;
function showToast(msg) {
  const t = document.getElementById('toast');
  t.textContent = msg;
  t.classList.add('show');
  clearTimeout(toastTimer);
  toastTimer = setTimeout(() => t.classList.remove('show'), 2200);
}
</script>
</body>
</html>
