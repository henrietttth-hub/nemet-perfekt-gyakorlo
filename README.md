# nemet-perfekt-gyakorlo
<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Perfekt – Übungsblatt</title>
<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700;800&display=swap" rel="stylesheet">
<style>
  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: 'Nunito', sans-serif;
    background: #f0f2f5;
    color: #333;
    padding-bottom: 48px;
  }

  /* ── Fejléc ── */
  .page-header {
    background: #3a86ff;
    color: white;
    text-align: center;
    padding: 38px 20px 30px;
    margin-bottom: 32px;
    box-shadow: 0 4px 18px rgba(58,134,255,0.32);
  }
  .page-header h1 {
    font-size: 2.7em;
    font-weight: 800;
    font-style: italic;
    letter-spacing: 1px;
    margin-bottom: 8px;
  }
  .page-header p {
    font-size: 1em;
    opacity: 0.9;
    font-weight: 600;
  }

  /* ── Wrapper ── */
  .card-wrap {
    max-width: 800px;
    margin: 0 auto;
    padding: 0 16px;
    display: flex;
    flex-direction: column;
    gap: 24px;
  }

  /* ── Kártya ── */
  .section {
    background: #fff;
    border-radius: 12px;
    padding: 24px 24px 28px;
    box-shadow: 0 2px 12px rgba(0,0,0,0.08);
  }
  .section h2 {
    color: #3a86ff;
    font-size: 1.05em;
    font-weight: 800;
    margin-bottom: 18px;
    border-bottom: 2px solid #e8f0ff;
    padding-bottom: 8px;
  }

  /* ── Táblázat ── */
  table { width: 100%; border-collapse: collapse; font-size: 0.95em; }
  th, td { border: 1px solid #e0e0e0; padding: 9px 14px; text-align: left; }
  th { background: #eef3ff; color: #3a86ff; font-weight: 700; }
  tr:nth-child(even) td { background: #fafbff; }
  .given { color: #555; font-style: italic; font-weight: 700; }

  td input[type="text"] {
    border: none;
    border-bottom: 2px solid #c5d3f0;
    width: 100%;
    background: transparent;
    font-family: 'Nunito', sans-serif;
    font-size: 0.95em;
    padding: 3px 4px;
    outline: none;
    color: #333;
    transition: border-color 0.2s;
  }
  td input[type="text"]:focus { border-bottom-color: #3a86ff; }

  /* ── Hat/Ist — kártyaszerű gombok ── */
  .hat-ist-list { list-style: none; display: flex; flex-direction: column; gap: 10px; }
  .hat-ist-list li { display: flex; align-items: center; gap: 12px; flex-wrap: wrap; }
  .hat-ist-list li .word { font-weight: 700; color: #444; min-width: 110px; }
  .choice-group { display: flex; gap: 8px; }
  .choice-btn {
    padding: 6px 18px;
    border-radius: 8px;
    border: 2px solid #c5d3f0;
    background: #f5f8ff;
    color: #3a86ff;
    font-family: 'Nunito', sans-serif;
    font-size: 0.95em;
    font-weight: 700;
    cursor: pointer;
    transition: background 0.15s, border-color 0.15s, color 0.15s;
    user-select: none;
  }
  .choice-btn:hover { background: #dce8ff; border-color: #3a86ff; }
  .choice-btn.selected { background: #3a86ff; border-color: #3a86ff; color: #fff; }
  .choice-btn.correct-sel { background: #d4edda !important; border-color: #28a745 !important; color: #155724 !important; }
  .choice-btn.incorrect-sel { background: #f8d7da !important; border-color: #dc3545 !important; color: #721c24 !important; }

  /* ── Partizip grid ── */
  .partizip-grid { display: flex; flex-wrap: wrap; gap: 12px; }
  .partizip-item { display: flex; flex-direction: column; gap: 4px; min-width: 130px; flex: 1; }
  .partizip-item label {
    font-size: 0.78em;
    font-weight: 800;
    color: #3a86ff;
    text-transform: uppercase;
    letter-spacing: 0.5px;
  }
  .partizip-item input {
    border: none;
    border-bottom: 2px solid #c5d3f0;
    font-family: 'Nunito', sans-serif;
    font-size: 0.95em;
    padding: 3px 4px;
    background: transparent;
    outline: none;
    color: #333;
    transition: border-color 0.2s;
  }
  .partizip-item input:focus { border-bottom-color: #3a86ff; }

  /* ── Korrigieren / Perfekt listák ── */
  .korr-list, .perfekt-list {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 14px;
  }
  .korr-list li, .perfekt-list li {
    background: #f8faff;
    border-radius: 10px;
    padding: 12px 14px;
    border: 1px solid #e4eaff;
    display: flex;
    flex-direction: column;
    gap: 6px;
  }
  .korr-list li .original {
    font-size: 0.85em;
    color: #aaa;
    text-decoration: line-through;
    font-weight: 600;
  }
  .perfekt-list li .original {
    font-size: 0.85em;
    color: #666;
    font-weight: 600;
  }
  .korr-list li input, .perfekt-list li input {
    border: none;
    border-bottom: 2px solid #c5d3f0;
    font-family: 'Nunito', sans-serif;
    font-size: 0.97em;
    padding: 3px 4px;
    background: transparent;
    outline: none;
    color: #333;
    width: 100%;
    transition: border-color 0.2s;
  }
  .korr-list li input:focus, .perfekt-list li input:focus { border-bottom-color: #3a86ff; }

  /* ── Helyes / Helytelen ── */
  .correct {
    background: #d4edda !important;
    border-bottom-color: #28a745 !important;
    color: #155724 !important;
  }
  .incorrect {
    background: #f8d7da !important;
    border-bottom-color: #dc3545 !important;
    color: #721c24 !important;
  }

  /* ── Ellenőrzés gomb ── */
  .btn-wrap {
    max-width: 800px;
    margin: 4px auto 0;
    padding: 0 16px;
  }
  .check-btn {
    display: block;
    width: 100%;
    background: #3a86ff;
    color: white;
    border: none;
    border-radius: 12px;
    padding: 16px 40px;
    font-family: 'Nunito', sans-serif;
    font-size: 1.15em;
    font-weight: 800;
    cursor: pointer;
    letter-spacing: 0.5px;
    box-shadow: 0 4px 14px rgba(58,134,255,0.35);
    transition: background 0.2s, box-shadow 0.2s, transform 0.1s;
  }
  .check-btn:hover {
    background: #1a6fef;
    box-shadow: 0 6px 22px rgba(58,134,255,0.45);
    transform: translateY(-1px);
  }
  .check-btn:active { transform: translateY(0); }

  .score {
    max-width: 800px;
    margin: 16px auto 0;
    padding: 0 16px;
    text-align: center;
    font-size: 1.25em;
    font-weight: 800;
    color: #3a86ff;
  }

  @media (max-width: 600px) {
    .page-header h1 { font-size: 1.9em; }
    .partizip-item { min-width: 100px; }
    .hat-ist-list li { flex-direction: row; align-items: center; }
  }
</style>
</head>
<body>

<div class="page-header">
  <h1>Perfekt</h1>
  <p>Löse alle Aufgaben und klicke dann auf „Ellenőrzés", um deine Antworten zu überprüfen.</p>
</div>

<div class="card-wrap">

  <!-- 1. Tabelle -->
  <div class="section">
    <h2>1. Ergänzen Sie die Tabelle (Infinitiv ↔ Partizip II)</h2>
    <table>
      <tr><th>Infinitiv</th><th>Partizip II</th></tr>
      <tr><td class="given">kochen</td><td><input type="text" id="t1" placeholder="Partizip II…"></td></tr>
      <tr><td><input type="text" id="t2" placeholder="Infinitiv…"></td><td class="given">geturnt</td></tr>
      <tr><td class="given">holen</td><td><input type="text" id="t3" placeholder="Partizip II…"></td></tr>
      <tr><td class="given">bezahlen</td><td><input type="text" id="t4" placeholder="Partizip II…"></td></tr>
      <tr><td><input type="text" id="t5" placeholder="Infinitiv…"></td><td class="given">eingekauft</td></tr>
      <tr><td class="given">trainieren</td><td><input type="text" id="t6" placeholder="Partizip II…"></td></tr>
      <tr><td class="given">zerstören</td><td><input type="text" id="t7" placeholder="Partizip II…"></td></tr>
      <tr><td><input type="text" id="t8" placeholder="Infinitiv…"></td><td class="given">bestellt</td></tr>
      <tr><td class="given">kaufen</td><td><input type="text" id="t9" placeholder="Partizip II…"></td></tr>
      <tr><td class="given">malen</td><td><input type="text" id="t10" placeholder="Partizip II…"></td></tr>
      <tr><td><input type="text" id="t11" placeholder="Infinitiv…"></td><td class="given">gerechnet</td></tr>
      <tr><td><input type="text" id="t12" placeholder="Infinitiv…"></td><td class="given">gearbeitet</td></tr>
      <tr><td class="given">suchen</td><td><input type="text" id="t13" placeholder="Partizip II…"></td></tr>
      <tr><td class="given">basteln</td><td><input type="text" id="t14" placeholder="Partizip II…"></td></tr>
      <tr><td><input type="text" id="t15" placeholder="Infinitiv…"></td><td class="given">gesurft</td></tr>
    </table>
  </div>

  <!-- 2. Hat oder Ist -->
  <div class="section">
    <h2>2. Hat oder Ist? Ergänzen Sie</h2>
    <ul class="hat-ist-list">
      <li><span class="word">eingeladen</span><div class="choice-group" data-id="hi1"><button class="choice-btn" data-val="Hat" onclick="selectChoice(this)">Hat</button><button class="choice-btn" data-val="Ist" onclick="selectChoice(this)">Ist</button></div></li>
      <li><span class="word">geschneit</span><div class="choice-group" data-id="hi2"><button class="choice-btn" data-val="Hat" onclick="selectChoice(this)">Hat</button><button class="choice-btn" data-val="Ist" onclick="selectChoice(this)">Ist</button></div></li>
      <li><span class="word">gestorben</span><div class="choice-group" data-id="hi3"><button class="choice-btn" data-val="Hat" onclick="selectChoice(this)">Hat</button><button class="choice-btn" data-val="Ist" onclick="selectChoice(this)">Ist</button></div></li>
      <li><span class="word">gesungen</span><div class="choice-group" data-id="hi4"><button class="choice-btn" data-val="Hat" onclick="selectChoice(this)">Hat</button><button class="choice-btn" data-val="Ist" onclick="selectChoice(this)">Ist</button></div></li>
      <li><span class="word">gelaufen</span><div class="choice-group" data-id="hi5"><button class="choice-btn" data-val="Hat" onclick="selectChoice(this)">Hat</button><button class="choice-btn" data-val="Ist" onclick="selectChoice(this)">Ist</button></div></li>
      <li><span class="word">gebaut</span><div class="choice-group" data-id="hi6"><button class="choice-btn" data-val="Hat" onclick="selectChoice(this)">Hat</button><button class="choice-btn" data-val="Ist" onclick="selectChoice(this)">Ist</button></div></li>
      <li><span class="word">geblieben</span><div class="choice-group" data-id="hi7"><button class="choice-btn" data-val="Hat" onclick="selectChoice(this)">Hat</button><button class="choice-btn" data-val="Ist" onclick="selectChoice(this)">Ist</button></div></li>
      <li><span class="word">gespielt</span><div class="choice-group" data-id="hi8"><button class="choice-btn" data-val="Hat" onclick="selectChoice(this)">Hat</button><button class="choice-btn" data-val="Ist" onclick="selectChoice(this)">Ist</button></div></li>
      <li><span class="word">gelernt</span><div class="choice-group" data-id="hi9"><button class="choice-btn" data-val="Hat" onclick="selectChoice(this)">Hat</button><button class="choice-btn" data-val="Ist" onclick="selectChoice(this)">Ist</button></div></li>
      <li><span class="word">umgezogen</span><div class="choice-group" data-id="hi10"><button class="choice-btn" data-val="Hat" onclick="selectChoice(this)">Hat</button><button class="choice-btn" data-val="Ist" onclick="selectChoice(this)">Ist</button></div></li>
      <li><span class="word">gesagt</span><div class="choice-group" data-id="hi11"><button class="choice-btn" data-val="Hat" onclick="selectChoice(this)">Hat</button><button class="choice-btn" data-val="Ist" onclick="selectChoice(this)">Ist</button></div></li>
    </ul>
  </div>

  <!-- 3. Partizip II -->
  <div class="section">
    <h2>3. Wie lautet das Partizip II?</h2>
    <div class="partizip-grid">
      <div class="partizip-item"><label>tauchen</label><input type="text" id="p1" placeholder="Partizip II…"></div>
      <div class="partizip-item"><label>baden</label><input type="text" id="p2" placeholder="Partizip II…"></div>
      <div class="partizip-item"><label>zerstören</label><input type="text" id="p3" placeholder="Partizip II…"></div>
      <div class="partizip-item"><label>gießen</label><input type="text" id="p4" placeholder="Partizip II…"></div>
      <div class="partizip-item"><label>einschlafen</label><input type="text" id="p5" placeholder="Partizip II…"></div>
      <div class="partizip-item"><label>fahren</label><input type="text" id="p6" placeholder="Partizip II…"></div>
      <div class="partizip-item"><label>werden</label><input type="text" id="p7" placeholder="Partizip II…"></div>
      <div class="partizip-item"><label>schlafen</label><input type="text" id="p8" placeholder="Partizip II…"></div>
      <div class="partizip-item"><label>gehen</label><input type="text" id="p9" placeholder="Partizip II…"></div>
      <div class="divizip-item partizip-item"><label>tragen</label><input type="text" id="p10" placeholder="Partizip II…"></div>
      <div class="partizip-item"><label>sein</label><input type="text" id="p11" placeholder="Partizip II…"></div>
      <div class="partizip-item"><label>essen</label><input type="text" id="p12" placeholder="Partizip II…"></div>
      <div class="partizip-item"><label>springen</label><input type="text" id="p13" placeholder="Partizip II…"></div>
      <div class="partizip-item"><label>haben</label><input type="text" id="p14" placeholder="Partizip II…"></div>
      <div class="partizip-item"><label>trinken</label><input type="text" id="p15" placeholder="Partizip II…"></div>
      <div class="partizip-item"><label>bringen</label><input type="text" id="p16" placeholder="Partizip II…"></div>
      <div class="partizip-item"><label>aufstehen</label><input type="text" id="p17" placeholder="Partizip II…"></div>
      <div class="partizip-item"><label>brechen</label><input type="text" id="p18" placeholder="Partizip II…"></div>
      <div class="partizip-item"><label>waschen</label><input type="text" id="p19" placeholder="Partizip II…"></div>
      <div class="partizip-item"><label>schwimmen</label><input type="text" id="p20" placeholder="Partizip II…"></div>
      <div class="partizip-item"><label>verstehen</label><input type="text" id="p21" placeholder="Partizip II…"></div>
      <div class="partizip-item"><label>mieten</label><input type="text" id="p22" placeholder="Partizip II…"></div>
      <div class="partizip-item"><label>genießen</label><input type="text" id="p23" placeholder="Partizip II…"></div>
      <div class="partizip-item"><label>lesen</label><input type="text" id="p24" placeholder="Partizip II…"></div>
      <div class="partizip-item"><label>schreiben</label><input type="text" id="p25" placeholder="Partizip II…"></div>
    </div>
  </div>

  <!-- 4. Korrigieren -->
  <div class="section">
    <h2>4. Korrigieren Sie (javítsd ki a hibás mondatot)</h2>
    <ul class="korr-list">
      <li><span class="original">Wohin hast du gefahren?</span><input type="text" id="k1" placeholder="Helyes mondat…"></li>
      <li><span class="original">Meine Mutter hat lange getelefoniert.</span><input type="text" id="k2" placeholder="Helyes mondat…"></li>
      <li><span class="original">Gestern ist es geregnet.</span><input type="text" id="k3" placeholder="Helyes mondat…"></li>
      <li><span class="original">Was hat hier gepassiert?</span><input type="text" id="k4" placeholder="Helyes mondat…"></li>
      <li><span class="original">Ich habe eine Suppe gebestellt.</span><input type="text" id="k5" placeholder="Helyes mondat…"></li>
      <li><span class="original">Ich habe meine Bücher mitbracht.</span><input type="text" id="k6" placeholder="Helyes mondat…"></li>
    </ul>
  </div>

  <!-- 5. Perfekt -->
  <div class="section">
    <h2>5. Schreiben Sie die Sätze im Perfekt</h2>
    <ul class="perfekt-list">
      <li><span class="original">Luise findet ihre Tasche nicht.</span><input type="text" id="pf1" placeholder="Im Perfekt…"></li>
      <li><span class="original">Meine Oma bäckt das Brot.</span><input type="text" id="pf2" placeholder="Im Perfekt…"></li>
      <li><span class="original">Nimmst du mich mit?</span><input type="text" id="pf3" placeholder="Im Perfekt…"></li>
      <li><span class="original">Warum schreit ihr?</span><input type="text" id="pf4" placeholder="Im Perfekt…"></li>
      <li><span class="original">Inge ruft Tobias an.</span><input type="text" id="pf5" placeholder="Im Perfekt…"></li>
    </ul>
  </div>

</div>

<div class="score" id="score"></div>
<div class="btn-wrap" style="margin-top:16px;">
  <button class="check-btn" onclick="checkAll()">✔ Ellenőrzés</button>
</div>

<script>
function selectChoice(btn) {
  const group = btn.parentElement;
  group.querySelectorAll('.choice-btn').forEach(b => {
    b.classList.remove('selected','correct-sel','incorrect-sel');
  });
  btn.classList.add('selected');
}

function getChoiceVal(id) {
  const group = document.querySelector(`.choice-group[data-id="${id}"]`);
  if (!group) return '';
  const sel = group.querySelector('.choice-btn.selected, .choice-btn.correct-sel, .choice-btn.incorrect-sel');
  // find actually selected (not yet checked)
  const s = group.querySelector('.choice-btn.selected');
  return s ? s.dataset.val : '';
}

function markChoiceGroup(id, ok) {
  const group = document.querySelector(`.choice-group[data-id="${id}"]`);
  if (!group) return;
  const btns = group.querySelectorAll('.choice-btn');
  btns.forEach(b => b.classList.remove('selected','correct-sel','incorrect-sel'));
  // find the selected one
  // we need to re-read — store selected value before wiping
  const sel = group.querySelector('.choice-btn.selected');
  if (sel) sel.classList.add(ok ? 'correct-sel' : 'incorrect-sel');
}

function normalize(s) {
  return s.trim().toLowerCase().replace(/\s+/g,' ');
}
function accept(inputVal, answers) {
  const v = normalize(inputVal);
  return answers.some(a => normalize(a) === v);
}
function markInput(id, ok) {
  const el = document.getElementById(id);
  el.classList.remove('correct','incorrect');
  el.classList.add(ok ? 'correct' : 'incorrect');
  return ok;
}

// Store selected values before checking
function getAndMarkChoice(id, correct) {
  const group = document.querySelector(`.choice-group[data-id="${id}"]`);
  const sel = group ? group.querySelector('.choice-btn.selected') : null;
  const val = sel ? sel.dataset.val : '';
  const ok = val === correct;
  // clear all
  group && group.querySelectorAll('.choice-btn').forEach(b =>
    b.classList.remove('selected','correct-sel','incorrect-sel')
  );
  if (sel) sel.classList.add(ok ? 'correct-sel' : 'incorrect-sel');
  return ok;
}

const tabelle = {
  t1:['gekocht'], t2:['turnen'], t3:['geholt'], t4:['bezahlt'],
  t5:['einkaufen'], t6:['trainiert'], t7:['zerstört'], t8:['bestellen'],
  t9:['gekauft'], t10:['gemalt'], t11:['rechnen'], t12:['arbeiten'],
  t13:['gesucht'], t14:['gebastelt'], t15:['surfen']
};
const hatist = {
  hi1:'Hat', hi2:'Hat', hi3:'Ist', hi4:'Hat', hi5:'Ist',
  hi6:'Hat', hi7:'Ist', hi8:'Hat', hi9:'Hat', hi10:'Ist', hi11:'Hat'
};
const partizip = {
  p1:['getaucht'], p2:['gebadet'], p3:['zerstört'], p4:['gegossen'],
  p5:['eingeschlafen'], p6:['gefahren'], p7:['geworden'], p8:['geschlafen'],
  p9:['gegangen'], p10:['getragen'], p11:['gewesen'], p12:['gegessen'],
  p13:['gesprungen'], p14:['gehabt'], p15:['getrunken'], p16:['gebracht'],
  p17:['aufgestanden'], p18:['gebrochen'], p19:['gewaschen'], p20:['geschwommen'],
  p21:['verstanden'], p22:['gemietet'], p23:['genossen'], p24:['gelesen'],
  p25:['geschrieben']
};
const korr = {
  k1:['Wohin bist du gefahren?'],
  k2:['Meine Mutter hat lange telefoniert.'],
  k3:['Gestern hat es geregnet.'],
  k4:['Was ist hier passiert?'],
  k5:['Ich habe eine Suppe bestellt.'],
  k6:['Ich habe meine Bücher mitgebracht.']
};
const perfekt = {
  pf1:['Luise hat ihre Tasche nicht gefunden.'],
  pf2:['Meine Oma hat das Brot gebacken.'],
  pf3:['Hast du mich mitgenommen?'],
  pf4:['Warum habt ihr geschrien?','Warum habt ihr geschrieen?'],
  pf5:['Inge hat Tobias angerufen.']
};

function checkAll() {
  let correct = 0, total = 0;

  for (const [id, answers] of Object.entries(tabelle)) {
    total++;
    if (markInput(id, accept(document.getElementById(id).value, answers))) correct++;
  }
  for (const [id, ans] of Object.entries(hatist)) {
    total++;
    if (getAndMarkChoice(id, ans)) correct++;
  }
  for (const [id, answers] of Object.entries(partizip)) {
    total++;
    if (markInput(id, accept(document.getElementById(id).value, answers))) correct++;
  }
  for (const [id, answers] of Object.entries(korr)) {
    total++;
    if (markInput(id, accept(document.getElementById(id).value, answers))) correct++;
  }
  for (const [id, answers] of Object.entries(perfekt)) {
    total++;
    if (markInput(id, accept(document.getElementById(id).value, answers))) correct++;
  }

  const scoreEl = document.getElementById('score');
  scoreEl.textContent = `Eredmény: ${correct} / ${total} helyes válasz`;
  scoreEl.scrollIntoView({behavior:'smooth'});
}
</script>
</body>
</html>
