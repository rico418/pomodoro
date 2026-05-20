[25_00 · 番茄钟.htm](https://github.com/user-attachments/files/28061647/25_00.htm)
<!DOCTYPE html>
<!-- saved from url=(0044)file:///Users/dating/Downloads/pomodoro.html -->
<html lang="zh-CN"><head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>25:00 · 番茄钟</title>
  <link rel="stylesheet" href="./25_00 · 番茄钟_files/tabler-icons.min.css">
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    :root {
      --bg: #ffffff;
      --bg2: #f5f4f0;
      --bg3: #eeede8;
      --text: #1a1a18;
      --text2: #6b6b65;
      --text3: #a8a89f;
      --border: rgba(0,0,0,0.12);
      --border2: rgba(0,0,0,0.22);
      --radius: 10px;
      --radius-lg: 14px;
      --mono: 'Courier New', monospace;
    }
    @media (prefers-color-scheme: dark) {
      :root {
        --bg: #1c1c1a;
        --bg2: #242422;
        --bg3: #2e2e2b;
        --text: #f0efe8;
        --text2: #9a9a90;
        --text3: #6a6a62;
        --border: rgba(255,255,255,0.1);
        --border2: rgba(255,255,255,0.2);
      }
    }
    body {
      font-family: -apple-system, BlinkMacSystemFont, 'PingFang SC', 'Hiragino Sans GB', sans-serif;
      background: var(--bg);
      color: var(--text);
      min-height: 100vh;
      display: flex;
      align-items: flex-start;
      justify-content: center;
      padding: 2rem 1rem 3rem;
    }
    .wrap { width: 100%; max-width: 520px; }
    h1 { font-size: 18px; font-weight: 500; margin-bottom: 1.25rem; color: var(--text2); letter-spacing: .03em; }
    .modes {
      display: flex; gap: 6px;
      background: var(--bg2);
      border-radius: var(--radius-lg);
      padding: 4px; margin-bottom: 1.5rem;
    }
    .mode-btn {
      flex: 1; padding: 8px 0; font-size: 13px; font-weight: 500;
      border: none; background: transparent; color: var(--text2);
      border-radius: var(--radius); cursor: pointer; transition: all .2s;
    }
    .mode-btn.active {
      background: var(--bg);
      color: var(--text);
      border: 0.5px solid var(--border);
    }
    .ring-area { display: flex; justify-content: center; margin: 0.5rem 0 1.5rem; }
    .ring-track { fill: none; stroke: var(--border); stroke-width: 8; }
    .ring-prog { fill: none; stroke-width: 8; stroke-linecap: round; transition: stroke-dashoffset 1s linear, stroke .4s; }
    .time-lbl { font-size: 52px; font-weight: 500; fill: var(--text); dominant-baseline: middle; text-anchor: middle; font-family: var(--mono); }
    .phase-lbl { font-size: 13px; fill: var(--text2); dominant-baseline: middle; text-anchor: middle; }
    .controls { display: flex; align-items: center; justify-content: center; gap: 12px; margin-bottom: 1.5rem; }
    .btn {
      display: flex; align-items: center; justify-content: center;
      border: 0.5px solid var(--border2); border-radius: 50%;
      cursor: pointer; background: transparent; color: var(--text);
      transition: all .15s;
    }
    .btn:hover { background: var(--bg2); }
    .btn.main { width: 60px; height: 60px; font-size: 22px; }
    .btn.side { width: 40px; height: 40px; font-size: 18px; }
    .dots { display: flex; gap: 8px; justify-content: center; margin-bottom: 1.5rem; }
    .dot { width: 10px; height: 10px; border-radius: 50%; background: var(--border); transition: background .3s; }
    .dot.done { background: #D85A30; }
    .dot.current { background: #D85A30; opacity: .45; }
    .stats { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 8px; margin-bottom: 1.25rem; }
    .stat { background: var(--bg2); border-radius: var(--radius); padding: 10px 12px; text-align: center; }
    .stat-n { font-size: 20px; font-weight: 500; }
    .stat-l { font-size: 11px; color: var(--text2); margin-top: 2px; }
    .divider { height: 0.5px; background: var(--border); margin-bottom: 1.25rem; }
    .task-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px; }
    .task-title { font-size: 13px; font-weight: 500; color: var(--text2); letter-spacing: .04em; }
    .task-count { font-size: 11px; color: var(--text3); }
    .task-input-row { display: flex; gap: 8px; margin-bottom: 10px; }
    .task-input-row input {
      flex: 1; font-size: 14px;
      border: 0.5px solid var(--border);
      border-radius: var(--radius);
      padding: 8px 12px;
      background: var(--bg2); color: var(--text);
    }
    .task-input-row input:focus { outline: none; border-color: var(--border2); }
    .task-input-row button {
      padding: 8px 14px; font-size: 13px; font-weight: 500;
      border: 0.5px solid var(--border2);
      border-radius: var(--radius);
      background: transparent; color: var(--text); cursor: pointer;
    }
    .task-input-row button:hover { background: var(--bg2); }
    .task-list { display: flex; flex-direction: column; gap: 6px; }
    .task {
      display: flex; align-items: center; gap: 10px;
      padding: 9px 12px;
      border-radius: var(--radius);
      border: 0.5px solid var(--border);
      background: var(--bg2); cursor: pointer; transition: border-color .2s;
    }
    .task:hover { border-color: var(--border2); }
    .task.active-task { border-color: #D85A30; }
    .task-check {
      width: 16px; height: 16px; border-radius: 50%;
      border: 0.5px solid var(--border2); flex-shrink: 0;
      display: flex; align-items: center; justify-content: center;
    }
    .task.done-task .task-check { background: #D85A30; border-color: #D85A30; }
    .task.done-task .task-text { text-decoration: line-through; color: var(--text3); }
    .task-text { font-size: 14px; flex: 1; }
    .task-pomos { font-size: 11px; color: var(--text3); display: flex; align-items: center; gap: 3px; }
    .task-del { font-size: 14px; color: var(--text3); opacity: 0; transition: opacity .15s; background: none; border: none; cursor: pointer; }
    .task:hover .task-del { opacity: 1; }
  </style>
</head>
<body>
<div class="wrap">
  <h1>🍅 番茄钟</h1>
  <div class="modes">
    <button class="mode-btn active" data-mode="focus" onclick="setMode(&#39;focus&#39;)">专注 25:00</button>
    <button class="mode-btn" data-mode="short" onclick="setMode(&#39;short&#39;)">短休 5:00</button>
    <button class="mode-btn" data-mode="long" onclick="setMode(&#39;long&#39;)">长休 15:00</button>
  </div>
  <div class="ring-area">
    <svg width="220" height="220" viewBox="-10 -10 220 220" style="overflow:visible">
      <circle class="ring-track" cx="100" cy="100" r="90"></circle>
      <circle class="ring-prog" id="ring" cx="100" cy="100" r="90" stroke="#D85A30" stroke-dasharray="565.5" stroke-dashoffset="0" transform="rotate(-90 100 100)"></circle>
      <text class="time-lbl" id="timeDisp" x="100" y="97">25:00</text>
      <text class="phase-lbl" id="phaseDisp" x="100" y="124">专注时间</text>
    </svg>
  </div>
  <div class="dots" id="dotsArea"><span class="dot current"></span><span class="dot"></span><span class="dot"></span><span class="dot"></span></div>
  <div class="controls">
    <button class="btn side" onclick="resetTimer()" title="重置" aria-label="重置"><i class="ti ti-refresh"></i></button>
    <button class="btn main" id="mainBtn" onclick="toggleTimer()" aria-label="开始/暂停"><i class="ti ti-player-play" id="mainIcon"></i></button>
    <button class="btn side" onclick="skipTimer()" title="跳过" aria-label="跳过"><i class="ti ti-player-skip-forward"></i></button>
  </div>
  <div class="stats">
    <div class="stat"><div class="stat-n" id="sTomato">0</div><div class="stat-l">今日番茄</div></div>
    <div class="stat"><div class="stat-n" id="sFocus">0m</div><div class="stat-l">专注分钟</div></div>
    <div class="stat"><div class="stat-n" id="sStreak">0</div><div class="stat-l">连续专注</div></div>
  </div>
  <div class="divider"></div>
  <div class="task-header">
    <span class="task-title">任务清单</span>
    <span class="task-count" id="taskCount">0 个任务</span>
  </div>
  <div class="task-input-row">
    <input type="text" id="taskInput" placeholder="添加新任务..." maxlength="50" onkeydown="if(event.key===&#39;Enter&#39;)addTask()">
    <button onclick="addTask()">添加</button>
  </div>
  <div class="task-list" id="taskList"></div>
</div>
<script>
  const MODES = {
    focus: { secs: 25*60, label: '专注时间', color: '#D85A30' },
    short: { secs: 5*60,  label: '短暂休息', color: '#1D9E75' },
    long:  { secs: 15*60, label: '长时休息', color: '#185FA5' }
  };
  const CIRC = 2 * Math.PI * 90;
  let mode = 'focus', totalSecs = MODES.focus.secs, remaining = totalSecs;
  let running = false, timer = null;
  let tomatoes = 0, focusMins = 0, streak = 0, sessionInCycle = 0;
  let tasks = [], activeTask = null;

  const ring = document.getElementById('ring');
  const timeDisp = document.getElementById('timeDisp');
  const phaseDisp = document.getElementById('phaseDisp');
  const mainIcon = document.getElementById('mainIcon');

  function fmt(s) {
    const m = Math.floor(s / 60), sc = s % 60;
    return `${String(m).padStart(2,'0')}:${String(sc).padStart(2,'0')}`;
  }
  function updateRing() {
    const pct = remaining / totalSecs;
    ring.setAttribute('stroke-dashoffset', CIRC * (1 - pct));
    ring.setAttribute('stroke', MODES[mode].color);
    timeDisp.textContent = fmt(remaining);
    phaseDisp.textContent = MODES[mode].label;
    document.title = fmt(remaining) + ' · 番茄钟';
  }
  function renderDots() {
    const d = document.getElementById('dotsArea');
    d.innerHTML = '';
    for (let i = 0; i < 4; i++) {
      const el = document.createElement('span');
      el.className = 'dot' + (i < sessionInCycle ? ' done' : i === sessionInCycle && mode === 'focus' ? ' current' : '');
      d.appendChild(el);
    }
  }
  function setMode(m) {
    if (running) return;
    mode = m; totalSecs = MODES[m].secs; remaining = totalSecs;
    document.querySelectorAll('.mode-btn').forEach(b => b.classList.toggle('active', b.dataset.mode === m));
    updateRing(); renderDots();
  }
  function toggleTimer() {
    if (running) {
      clearInterval(timer); running = false;
      mainIcon.className = 'ti ti-player-play';
    } else {
      running = true; mainIcon.className = 'ti ti-player-pause';
      timer = setInterval(() => {
        remaining--;
        updateRing();
        if (remaining <= 0) { clearInterval(timer); running = false; mainIcon.className = 'ti ti-player-play'; onComplete(); }
      }, 1000);
    }
  }
  function resetTimer() {
    clearInterval(timer); running = false; mainIcon.className = 'ti ti-player-play';
    remaining = totalSecs; updateRing();
  }
  function skipTimer() {
    clearInterval(timer); running = false; mainIcon.className = 'ti ti-player-play';
    onComplete();
  }
  function onComplete() {
    playBeep();
    if (mode === 'focus') {
      tomatoes++; focusMins += 25; streak++;
      sessionInCycle = Math.min(sessionInCycle + 1, 4);
      if (activeTask !== null) { tasks[activeTask].pomos++; renderTasks(); }
      document.getElementById('sTomato').textContent = tomatoes;
      document.getElementById('sFocus').textContent = focusMins + 'm';
      document.getElementById('sStreak').textContent = streak;
      if (sessionInCycle >= 4) { sessionInCycle = 0; setMode('long'); }
      else { setMode('short'); }
    } else {
      streak = 0; setMode('focus');
    }
    renderDots();
  }
  function playBeep() {
    try {
      const ctx = new (window.AudioContext || window.webkitAudioContext)();
      [523, 659, 784, 1047].forEach((f, i) => {
        const o = ctx.createOscillator(), g = ctx.createGain();
        o.connect(g); g.connect(ctx.destination);
        o.frequency.value = f; o.type = 'sine';
        g.gain.setValueAtTime(0, ctx.currentTime + i * .12);
        g.gain.linearRampToValueAtTime(.18, ctx.currentTime + i * .12 + .05);
        g.gain.linearRampToValueAtTime(0, ctx.currentTime + i * .12 + .22);
        o.start(ctx.currentTime + i * .12);
        o.stop(ctx.currentTime + i * .12 + .3);
      });
    } catch(e) {}
  }
  function addTask() {
    const inp = document.getElementById('taskInput');
    const val = inp.value.trim();
    if (!val) return;
    tasks.push({ text: val, done: false, pomos: 0 });
    inp.value = '';
    renderTasks();
  }
  function renderTasks() {
    const list = document.getElementById('taskList');
    list.innerHTML = '';
    document.getElementById('taskCount').textContent = tasks.length + ' 个任务';
    tasks.forEach((t, i) => {
      const div = document.createElement('div');
      div.className = 'task' + (t.done ? ' done-task' : activeTask === i ? ' active-task' : '');
      div.innerHTML = `
        <div class="task-check">${t.done ? '<i class="ti ti-check" style="font-size:10px;color:#fff"></i>' : ''}</div>
        <span class="task-text">${t.text}</span>
        ${t.pomos > 0 ? `<span class="task-pomos"><i class="ti ti-clock" style="font-size:11px"></i> ${t.pomos}</span>` : ''}
        <button class="task-del" onclick="delTask(event,${i})" aria-label="删除"><i class="ti ti-x"></i></button>`;
      div.addEventListener('click', () => {
        if (t.done) { t.done = false; }
        else if (activeTask === i) { activeTask = null; }
        else { activeTask = i; }
        renderTasks();
      });
      list.appendChild(div);
    });
  }
  updateRing(); renderDots(); renderTasks();
</script>


</body></html>
