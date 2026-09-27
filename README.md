<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>حروف الهجاء مع الحركات والمدود</title>
<style>
  :root{
    --bg:#0f172a; --surface:#1e293b; --surface2:#334155; --line:#334155;
    --text:#f8fafc; --muted:#94a3b8;
    --gold:#bf953f; --gold-light:#fcf6ba; --gold-dark:#aa771c;
    --fatha:#ef4444; --damma:#3b82f6; --kasra:#22c55e; --sukun:#9ca3af;
    --madA:#f97316; --madW:#06b6d4; --madY:#10b981;
  }
  *{box-sizing:border-box;}
  body{
    font-family:'Tajawal','Segoe UI',Tahoma,Arial,sans-serif;
    background:radial-gradient(circle at 50% 0%, #1b2740 0%, var(--bg) 60%);
    color:var(--text); margin:0; padding:20px 16px 60px;
    display:flex; flex-direction:column; align-items:center; min-height:100vh;
  }
  .lux-font{font-family:'Amiri','Traditional Arabic','Times New Roman',serif;}

  header{text-align:center; margin-bottom:24px; width:100%; max-width:1000px;}
  h1{font-size:2.1rem; margin:0 0 8px; font-weight:900;}
  .gold-gradient{
    background:linear-gradient(to right,var(--gold),var(--gold-light),var(--gold),var(--gold-light),var(--gold-dark));
    -webkit-background-clip:text; background-clip:text; color:transparent;
  }
  p.subtitle{color:var(--muted); font-size:1rem; margin:0; line-height:1.7;}

  main{width:100%; max-width:1000px; display:flex; flex-direction:column; gap:18px;}

  .panel{
    background:var(--surface); padding:18px; border-radius:18px;
    border:1px solid var(--line); box-shadow:0 8px 24px rgba(0,0,0,.25);
  }
  .panel h2{font-size:1.05rem; margin:0 0 14px; color:#cbd5e1; font-weight:700;}

  /* ====== أزرار الحركات ====== */
  .modes-grid{display:grid; grid-template-columns:repeat(7,1fr); gap:8px;}
  .mode-tab{
    background:var(--surface2); border:2px solid transparent; border-radius:14px;
    padding:10px 4px; display:flex; flex-direction:column; align-items:center; gap:4px;
    color:var(--text); transition:.2s;
  }
  .mode-tab .mode-sample{font-size:1.7rem; font-weight:bold; line-height:1.2; color:var(--c);}
  .mode-tab .mode-name{font-size:.72rem; color:var(--muted);}
  .mode-tab:hover{background:#3e4c63;}
  .mode-tab.active{
    border-color:var(--c); background:color-mix(in srgb, var(--c) 18%, var(--surface2));
    box-shadow:0 0 16px color-mix(in srgb, var(--c) 55%, transparent);
  }
  .mode-tab.active .mode-name{color:#fff;}

  /* ====== شاشة العرض والأزرار ====== */
  .display-row{display:flex; gap:18px; flex-wrap:wrap;}
  .display-card{
    flex:0 0 250px; aspect-ratio:1; border-radius:24px;
    background:var(--surface); border:2px solid var(--gold);
    display:flex; align-items:center; justify-content:center;
    box-shadow:0 0 20px rgba(191,149,63,.2); position:relative; overflow:hidden;
  }
  #mainLetter{font-size:7rem; font-weight:bold; text-shadow:0 0 24px rgba(255,255,255,.25); line-height:1;}
  .display-side{flex:1; min-width:250px; display:flex; flex-direction:column; gap:10px; justify-content:center;}

  button{font-family:inherit; cursor:pointer; border:none; outline:none; transition:.2s;}
  button:active{transform:scale(.97);}
  .btn-action{
    width:100%; padding:14px; border-radius:12px; font-weight:bold; font-size:1rem;
    display:flex; align-items:center; justify-content:center; gap:8px;
  }
  .btn-autoplay{background:var(--surface2); color:#fff; border:2px solid #475569;}
  .btn-autoplay:hover{background:#475569;}
  .btn-autoplay.active-play{background:#10b981; border-color:#059669; animation:pulse 1.8s infinite;}
  .btn-full{background:#3b2f6b; color:#e9d5ff; border:2px solid #6d28d9;}
  .btn-full:hover{background:#4c3d85;}
  .btn-full.active-play{background:#8b5cf6; border-color:#a78bfa; animation:pulse 1.8s infinite;}
  .btn-download{
    background:linear-gradient(to right,var(--gold),var(--gold-light),var(--gold));
    color:#000; box-shadow:0 0 15px rgba(191,149,63,.4);
  }
  .btn-download:hover{opacity:.9;}
  .hint{font-size:.8rem; color:var(--muted); text-align:center; line-height:1.6;}

  /* ====== شبكة الحروف ====== */
  .letters-grid{display:grid; grid-template-columns:repeat(7,1fr); gap:8px;}
  .letter-btn{
    padding:12px 4px; font-size:1.7rem; font-weight:bold; line-height:1.3;
    background:transparent; color:#e2e8f0; border:1px solid #475569; border-radius:10px;
  }
  .letter-btn:hover{background:var(--surface2); border-color:var(--gold-light);}
  .letter-btn.active{
    background:var(--gold); color:#000; border-color:var(--gold-light);
    box-shadow:0 0 14px rgba(191,149,63,.6);
  }

  /* ====== الجدول الشامل ====== */
  .table-wrap{overflow:auto; max-height:460px; border-radius:12px; border:1px solid var(--line);}
  table{border-collapse:collapse; width:100%; min-width:720px;}
  thead th{
    position:sticky; top:0; background:#243146; color:#cbd5e1; font-size:.82rem;
    padding:9px 6px; border-bottom:2px solid var(--gold-dark); z-index:2;
  }
  tbody th{
    background:#243146; color:var(--gold-light); font-size:1.4rem;
    padding:6px 10px; border-bottom:1px solid #2c3a52; position:sticky; right:0;
  }
  td{
    text-align:center; padding:6px 4px; font-size:1.35rem; cursor:pointer;
    border-bottom:1px solid #26334a; border-right:1px solid #26334a;
    transition:background .15s;
  }
  td:hover{background:#334155;}
  td.cell-active{background:rgba(191,149,63,.35); color:#fff; box-shadow:inset 0 0 0 1px var(--gold-light);}

  /* ====== وميض العرض ====== */
  .flash-animation{animation:flash .65s ease-out;}
  @keyframes flash{
    0%{box-shadow:0 0 0 transparent; background-color:var(--surface); border-color:var(--gold);}
    40%{box-shadow:0 0 50px var(--flash-color); background-color:var(--flash-light); border-color:var(--flash-color);}
    100%{box-shadow:0 0 20px rgba(191,149,63,.2); background-color:var(--surface); border-color:var(--gold);}
  }
  @keyframes pulse{
    0%{box-shadow:0 0 0 0 rgba(255,255,255,.5);}
    70%{box-shadow:0 0 0 12px rgba(255,255,255,0);}
    100%{box-shadow:0 0 0 0 rgba(255,255,255,0);}
  }

  /* ====== توست ====== */
  .toast{
    position:fixed; top:20px; left:50%; transform:translateX(-50%);
    background:#10b981; color:#fff; padding:14px 26px; border-radius:12px;
    z-index:9999; font-weight:bold; box-shadow:0 12px 30px rgba(0,0,0,.4);
    animation:fadeIn .3s ease-out;
  }
  @keyframes fadeIn{from{opacity:0; transform:translate(-50%,-12px);} to{opacity:1; transform:translate(-50%,0);}}

  @media (max-width:760px){
    .modes-grid{grid-template-columns:repeat(4,1fr);}
    .letters-grid{grid-template-columns:repeat(5,1fr);}
    #mainLetter{font-size:5.5rem;}
    .display-card{flex:0 0 100%; max-width:250px; margin:0 auto;}
    h1{font-size:1.6rem;}
  }
</style>
</head>
<body>

<header>
  <h1 class="gold-gradient">حروف الهجاء مع الحركات والمدود</h1>
  <p class="subtitle">
    الفتحة • الضمة • الكسرة • السكون • مد الألف • مد الواو • مد الياء<br>
    تطبيق تفاعلي بنطق صوتي ووميض ملوّن — يعمل بدون إنترنت
  </p>
</header>

<main>

  <!-- 1) اختيار الحركة -->
  <section class="panel">
    <h2>١ — اختر الحركة أو المد</h2>
    <div class="modes-grid" id="modesGrid"></div>
  </section>

  <!-- 2) شاشة العرض + الأزرار -->
  <section class="display-row">
    <div class="display-card" id="displayCard" style="--flash-color:#ef4444; --flash-light:rgba(239,68,68,.25);">
      <span id="mainLetter" class="lux-font">أَ</span>
    </div>

    <div class="display-side">
      <button id="autoPlayBtn" class="btn-action btn-autoplay" onclick="toggleAuto(false)">
        ▶ تشغيل تلقائي (الحروف بالحركة الحالية)
      </button>
      <button id="autoFullBtn" class="btn-action btn-full" onclick="toggleAuto(true)">
        🎬 تشغيل شامل (كل الحروف × كل الحركات)
      </button>
      <button class="btn-action btn-download" onclick="downloadOfflineApp()">
        ⬇ تنزيل التطبيق (للعمل بدون إنترنت)
      </button>
      <div class="hint">اضغط على أي حرف أو أي خانة في الجدول لسماع النطق</div>
    </div>
  </section>

  <!-- 3) شبكة الحروف -->
  <section class="panel">
    <h2>٢ — اختر الحرف</h2>
    <div id="lettersGrid" class="letters-grid"></div>
  </section>

  <!-- 4) الجدول الشامل -->
  <section class="panel">
    <h2>٣ — الجدول الشامل: جميع الحروف مرتّبة مع كل الحركات والمدود</h2>
    <div class="table-wrap">
      <table id="fullTable"></table>
    </div>
  </section>

</main>

<script>
/* ============================================================
   البيانات الأساسية
   ============================================================ */
const ALPHABET = ['أ','ب','ت','ث','ج','ح','خ','د','ذ','ر','ز','س','ش',
                  'ص','ض','ط','ظ','ع','غ','ف','ق','ك','ل','م','ن','ه','و','ي'];

const HARAKAT = [
  {key:'fatha', name:'الفتحة',  sample:'بَ',  char:'َ', suffix:'', color:'#ef4444', light:'rgba(239,68,68,.25)',  rate:0.85},
  {key:'damma', name:'الضمة',   sample:'بُ',  char:'ُ', suffix:'', color:'#3b82f6', light:'rgba(59,130,246,.25)', rate:0.85},
  {key:'kasra', name:'الكسرة',  sample:'بِ',  char:'ِ', suffix:'', color:'#22c55e', light:'rgba(34,197,94,.25)',  rate:0.85},
  {key:'sukun', name:'السكون',  sample:'بْ',  char:'ْ', suffix:'', color:'#9ca3af', light:'rgba(156,163,175,.25)',rate:0.85},
  {key:'madA',  name:'مد الألف',sample:'بَا', char:'َ', suffix:'ا',color:'#f97316', light:'rgba(249,115,22,.25)', rate:0.60},
  {key:'madW',  name:'مد الواو',sample:'بُو', char:'ُ', suffix:'و',color:'#06b6d4', light:'rgba(6,182,212,.25)',  rate:0.60},
  {key:'madY',  name:'مد الياء',sample:'بِي', char:'ِ', suffix:'ي',color:'#10b981', light:'rgba(16,185,129,.25)', rate:0.60}
];
const HMAP = Object.fromEntries(HARAKAT.map(h => [h.key, h]));

/* ============================================================
   الحالة
   ============================================================ */
let currentLetter  = 'أ';
let currentHarakah = 'fatha';
let autoTimer      = null;
let autoIsFull     = false;
let autoLetterIdx  = 0;
let autoHarakahIdx = 0;

const gridEl        = document.getElementById('lettersGrid');
const tableEl       = document.getElementById('fullTable');
const modesGridEl   = document.getElementById('modesGrid');
const mainLetterEl  = document.getElementById('mainLetter');
const displayCardEl = document.getElementById('displayCard');
const autoPlayBtn   = document.getElementById('autoPlayBtn');
const autoFullBtn   = document.getElementById('autoFullBtn');

/* ============================================================
   تركيب الحرف مع الحركة (مع معالجة خاصة للألف والواو والياء)
   ============================================================ */
function compose(letter, key){
  if (letter === 'أ'){
    return { fatha:'أَ', damma:'أُ', kasra:'إِ', sukun:'أْ',
             madA:'آ',  madW:'أُو', madY:'إِي' }[key];
  }
  if (letter === 'و' && key === 'madW') return 'وُو';
  if (letter === 'ي' && key === 'madY') return 'يِي';
  const h = HMAP[key];
  return letter + h.char + h.suffix;
}

/* ============================================================
   البناء الأولي
   ============================================================ */
function init(){
  renderModes();
  renderGrid();
  renderTable();
  updateDisplay(false);   // بدون نطق عند التحميل (سياسة المتصفح)
}

/* --- أزرار الحركات --- */
function renderModes(){
  modesGridEl.innerHTML = '';
  HARAKAT.forEach(h => {
    const btn = document.createElement('button');
    btn.className = 'mode-tab' + (h.key === currentHarakah ? ' active' : '');
    btn.dataset.key = h.key;
    btn.style.setProperty('--c', h.color);
    btn.innerHTML = `<span class="mode-sample lux-font">${h.sample}</span>
                     <span class="mode-name">${h.name}</span>`;
    btn.onclick = () => { stopAuto(); setHarakah(h.key, true); };
    modesGridEl.appendChild(btn);
  });
}

/* --- شبكة الحروف --- */
function renderGrid(){
  gridEl.innerHTML = '';
  ALPHABET.forEach((letter, i) => {
    const btn = document.createElement('button');
    btn.className = 'letter-btn lux-font' + (letter === currentLetter ? ' active' : '');
    btn.textContent = compose(letter, currentHarakah);
    btn.onclick = () => { stopAuto(); setLetter(letter, true); };
    gridEl.appendChild(btn);
  });
}

/* --- الجدول الشامل --- */
function renderTable(){
  let html = '<thead><tr><th>الحرف</th>';
  HARAKAT.forEach(h => { html += `<th style="color:${h.color}">${h.name}</th>`; });
  html += '</tr></thead><tbody>';

  ALPHABET.forEach(letter => {
    html += `<tr><th class="lux-font">${letter}</th>`;
    HARAKAT.forEach(h => {
      html += `<td class="lux-font" data-letter="${letter}" data-key="${h.key}">${compose(letter, h.key)}</td>`;
    });
    html += '</tr>';
  });
  html += '</tbody>';
  tableEl.innerHTML = html;

  tableEl.querySelectorAll('td').forEach(td => {
    td.onclick = () => {
      stopAuto();
      currentLetter  = td.dataset.letter;
      currentHarakah = td.dataset.key;
      renderModes();
      renderGrid();
      updateDisplay(true);
    };
  });
}

/* ============================================================
   التحديث والعرض
   ============================================================ */
function setLetter(letter, speak){
  currentLetter = letter;
  autoLetterIdx = ALPHABET.indexOf(letter);
  markActiveLetter();
  updateDisplay(speak);
}

function setHarakah(key, speak){
  currentHarakah = key;
  autoHarakahIdx = HARAKAT.findIndex(h => h.key === key);
  renderModes();
  renderGrid();
  updateDisplay(speak);
}

function markActiveLetter(){
  const idx = ALPHABET.indexOf(currentLetter);
  Array.from(gridEl.children).forEach((b, i) => b.classList.toggle('active', i === idx));
}

function updateDisplay(speak = true){
  const h = HMAP[currentHarakah];
  const text = compose(currentLetter, currentHarakah);

  mainLetterEl.textContent = text;

  /* وميض بلون الحركة */
  displayCardEl.style.setProperty('--flash-color', h.color);
  displayCardEl.style.setProperty('--flash-light', h.light);
  displayCardEl.classList.remove('flash-animation');
  void displayCardEl.offsetWidth;      // إعادة تفعيل الأنيميشن
  displayCardEl.classList.add('flash-animation');

  /* تمييز الخانة في الجدول */
  tableEl.querySelectorAll('td.cell-active').forEach(td => td.classList.remove('cell-active'));
  const cell = tableEl.querySelector(`td[data-letter="${currentLetter}"][data-key="${currentHarakah}"]`);
  if (cell) cell.classList.add('cell-active');

  if (speak) playAudio(text, h.rate);
}

/* ============================================================
   النطق الصوتي (سحابي للجودة + بديل آلي بدون إنترنت)
   ============================================================ */
let currentOnlineAudio = null;
let audioToken = 0;

function playAudio(text, rate){
  const token = ++audioToken;

  if ('speechSynthesis' in window) window.speechSynthesis.cancel();
  if (currentOnlineAudio){
    try { currentOnlineAudio.pause(); } catch(e){}
    currentOnlineAudio = null;
  }

  if (navigator.onLine){
    try{
      const url = 'https://translate.google.com/translate_tts?ie=UTF-8&tl=ar&client=tw-ob&q='
                  + encodeURIComponent(text);
      const audio = new Audio(url);
      currentOnlineAudio = audio;
      audio.playbackRate = rate < 0.8 ? 0.75 : 1.0;   // إبطاء بسيط لإبراز المد
      audio.play().catch(() => { if (token === audioToken) playOfflineAudio(text, rate); });
      return;
    }catch(e){ /* المتابعة للبديل */ }
  }
  playOfflineAudio(text, rate);
}

function playOfflineAudio(text, rate){
  if (!('speechSynthesis' in window)) return;
  const u = new SpeechSynthesisUtterance(text);
  u.lang  = 'ar-SA';
  u.rate  = rate;
  u.pitch = 1.0;
  const voices = window.speechSynthesis.getVoices() || [];
  const arVoice = voices.find(v => v.lang && v.lang.toLowerCase().startsWith('ar'));
  if (arVoice) u.voice = arVoice;
  window.speechSynthesis.speak(u);
}

if ('speechSynthesis' in window) {
  window.speechSynthesis.onvoiceschanged = () => {};
}

/* ============================================================
   التشغيل التلقائي
   ============================================================ */
function toggleAuto(full){
  if (autoTimer){
    // إن كان يعمل بالفعل بنفس النمط → إيقاف
    if (autoIsFull === full){ stopAuto(); return; }
    stopAuto();
  }
  startAuto(full);
}

function startAuto(full){
  autoIsFull = full;

  autoLetterIdx  = Math.max(0, ALPHABET.indexOf(currentLetter));
  autoHarakahIdx = Math.max(0, HARAKAT.findIndex(h => h.key === currentHarakah));

  const btn = full ? autoFullBtn : autoPlayBtn;
  btn.classList.add('active-play');
  btn.innerHTML = full ? '⏸ إيقاف التشغيل الشامل' : '⏸ إيقاف التلقائي';

  /* نطق العنصر الحالي فوراً ثم المتابعة */
  updateDisplay(true);

  autoTimer = setInterval(() => {
    autoLetterIdx++;

    if (autoLetterIdx >= ALPHABET.length){
      autoLetterIdx = 0;
      if (autoIsFull){
        autoHarakahIdx = (autoHarakahIdx + 1) % HARAKAT.length;
        currentHarakah = HARAKAT[autoHarakahIdx].key;
        renderModes();
        renderGrid();
      }
    }

    currentLetter = ALPHABET[autoLetterIdx];
    markActiveLetter();
    updateDisplay(true);
  }, 2300);
}

function stopAuto(){
  if (autoTimer){
    clearInterval(autoTimer);
    autoTimer = null;
  }
  autoPlayBtn.classList.remove('active-play');
  autoFullBtn.classList.remove('active-play');
  autoPlayBtn.innerHTML = '▶ تشغيل تلقائي (الحروف بالحركة الحالية)';
  autoFullBtn.innerHTML = '🎬 تشغيل شامل (كل الحروف × كل الحركات)';
}

/* ============================================================
   تنزيل التطبيق للعمل بدون إنترنت
   ============================================================ */
function downloadOfflineApp(){
  const htmlContent = '<!DOCTYPE html>\n' + document.documentElement.outerHTML;
  const blob = new Blob([htmlContent], {type:'text/html;charset=utf-8'});
  const url  = URL.createObjectURL(blob);

  const a = document.createElement('a');
  a.href = url;
  a.download = 'Learn_Arabic_Offline.html';
  document.body.appendChild(a);
  a.click();
  document.body.removeChild(a);
  URL.revokeObjectURL(url);

  const msg = document.createElement('div');
  msg.className = 'toast';
  msg.textContent = '✅ تم تنزيل التطبيق! افتح الملف المحمّل ليعمل بدون إنترنت.';
  document.body.appendChild(msg);
  setTimeout(() => msg.remove(), 5000);
}

/* ============================================================
   الإقلاع
   ============================================================ */
window.addEventListener('load', init);
</script>

</body>
</html>
