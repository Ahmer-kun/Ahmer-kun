
<style>
  @import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Orbitron:wght@400;700;900&display=swap');

  :root {
    --bg: #020c18;
    --panel: #040f1e;
    --border: #0e2a44;
    --accent: #00b4d8;
    --accent2: #0077a8;
    --dim: #1a3a52;
    --text: #c8e8f5;
    --muted: #4a7a96;
    --bright: #e0f4ff;
    --red: #ff3c5a;
    --green: #00e5a0;
    --gold: #f0a500;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body, .wrap {
    background: var(--bg);
    color: var(--text);
    font-family: 'Share Tech Mono', monospace;
    font-size: 13px;
    line-height: 1.6;
  }

  .wrap {
    padding: 20px 16px 40px;
    max-width: 900px;
    margin: 0 auto;
  }

  /* SCAN LINE OVERLAY */
  .scanlines {
    position: fixed; top: 0; left: 0; width: 100%; height: 100%;
    background: repeating-linear-gradient(0deg, transparent, transparent 2px, rgba(0,180,216,0.012) 2px, rgba(0,180,216,0.012) 4px);
    pointer-events: none; z-index: 999;
  }

  /* HEADER */
  .hdr {
    border: 1px solid var(--border);
    border-top: 3px solid var(--accent);
    background: var(--panel);
    padding: 24px 28px 20px;
    position: relative;
    margin-bottom: 2px;
  }

  .hdr::before {
    content: 'IDENTITY_MANIFEST.exe';
    position: absolute; top: -1px; right: 20px;
    background: var(--accent); color: #000;
    font-size: 10px; font-weight: 700;
    padding: 2px 10px; letter-spacing: 2px;
    font-family: 'Share Tech Mono', monospace;
  }

  .hdr-grid {
    display: grid;
    grid-template-columns: auto 1fr auto;
    gap: 24px;
    align-items: start;
  }

  .avatar {
    width: 72px; height: 72px;
    border: 2px solid var(--accent);
    border-radius: 4px;
    background: var(--dim);
    display: flex; align-items: center; justify-content: center;
    font-family: 'Orbitron', sans-serif;
    font-size: 22px; font-weight: 900;
    color: var(--accent);
    position: relative;
    flex-shrink: 0;
  }

  .avatar::after {
    content: '';
    position: absolute; bottom: -6px; left: 50%; transform: translateX(-50%);
    width: 2px; height: 6px;
    background: var(--accent);
  }

  .name-block {}

  .codename {
    font-family: 'Orbitron', sans-serif;
    font-size: 26px; font-weight: 900;
    color: var(--bright);
    letter-spacing: 3px;
    line-height: 1;
    margin-bottom: 4px;
  }

  .subtitle {
    color: var(--accent);
    font-size: 11px;
    letter-spacing: 2px;
    margin-bottom: 12px;
  }

  .meta-row {
    display: flex; gap: 16px; flex-wrap: wrap;
  }

  .meta-item {
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 1px;
  }

  .meta-item span {
    color: var(--text);
  }

  .status-block {
    display: flex; flex-direction: column; gap: 6px; align-items: flex-end;
  }

  .status-pill {
    display: flex; align-items: center; gap: 6px;
    border: 1px solid var(--border);
    padding: 4px 10px;
    font-size: 10px; letter-spacing: 2px;
    color: var(--muted);
  }

  .dot {
    width: 6px; height: 6px; border-radius: 50%;
    background: var(--green);
    animation: blink 1.8s infinite;
  }

  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0.3} }

  .typing-line {
    margin-top: 16px;
    font-size: 12px; color: var(--muted);
    border-top: 1px solid var(--border);
    padding-top: 12px;
    overflow: hidden;
    white-space: nowrap;
  }

  .cursor {
    display: inline-block;
    width: 8px; height: 13px;
    background: var(--accent);
    animation: blink 0.8s infinite;
    vertical-align: middle;
    margin-left: 2px;
  }

  /* GRID LAYOUT */
  .main-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2px;
    margin-bottom: 2px;
  }

  .panel {
    background: var(--panel);
    border: 1px solid var(--border);
    padding: 18px 20px;
    position: relative;
  }

  .panel-title {
    font-family: 'Orbitron', sans-serif;
    font-size: 9px;
    letter-spacing: 3px;
    color: var(--accent);
    margin-bottom: 14px;
    padding-bottom: 8px;
    border-bottom: 1px solid var(--border);
    display: flex; align-items: center; gap: 8px;
  }

  .panel-title::before {
    content: '//';
    color: var(--dim);
    font-family: 'Share Tech Mono', monospace;
    font-size: 11px;
  }

  /* STACK ROWS */
  .stack-row {
    display: flex; align-items: center;
    justify-content: space-between;
    padding: 5px 0;
    border-bottom: 1px solid rgba(14,42,68,0.5);
    font-size: 12px;
  }

  .stack-row:last-child { border-bottom: none; }

  .stack-label { color: var(--muted); }
  .stack-val { color: var(--text); text-align: right; font-size: 11px; }

  .tag {
    display: inline-block;
    padding: 1px 7px;
    border: 1px solid;
    font-size: 10px;
    letter-spacing: 1px;
    margin: 2px;
  }

  .tag-blue { border-color: var(--accent2); color: var(--accent); }
  .tag-green { border-color: #00664a; color: var(--green); }
  .tag-gold { border-color: #8a5c00; color: var(--gold); }
  .tag-red { border-color: #7a1020; color: var(--red); }

  /* PROJECTS */
  .proj-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2px;
    margin-bottom: 2px;
  }

  .proj-card {
    background: var(--panel);
    border: 1px solid var(--border);
    padding: 16px 18px;
    position: relative;
    cursor: pointer;
    transition: border-color 0.2s;
  }

  .proj-card:hover { border-color: var(--accent); }

  .proj-card::before {
    content: attr(data-num);
    position: absolute; top: 10px; right: 14px;
    font-family: 'Orbitron', sans-serif;
    font-size: 20px; font-weight: 900;
    color: var(--dim);
    line-height: 1;
  }

  .proj-name {
    font-family: 'Orbitron', sans-serif;
    font-size: 11px; font-weight: 700;
    color: var(--bright);
    letter-spacing: 1px;
    margin-bottom: 4px;
  }

  .proj-desc {
    font-size: 11px; color: var(--muted);
    margin-bottom: 10px;
    line-height: 1.5;
  }

  .proj-bar {
    height: 2px;
    background: var(--border);
    margin-bottom: 8px;
    position: relative;
    overflow: hidden;
  }

  .proj-bar-fill {
    height: 100%;
    background: var(--accent);
    position: relative;
  }

  .proj-bar-fill::after {
    content: '';
    position: absolute; right: 0; top: 0;
    width: 4px; height: 100%;
    background: var(--bright);
    animation: scan 2s linear infinite;
  }

  @keyframes scan { 0%{opacity:1} 50%{opacity:0} 100%{opacity:1} }

  .proj-stack {
    font-size: 10px; color: var(--accent2);
    letter-spacing: 1px;
  }

  /* CERTS */
  .cert-row {
    display: flex; align-items: center;
    gap: 12px;
    padding: 9px 0;
    border-bottom: 1px solid rgba(14,42,68,0.6);
  }

  .cert-row:last-child { border-bottom: none; }

  .cert-level {
    font-family: 'Orbitron', sans-serif;
    font-size: 8px; font-weight: 700;
    color: var(--gold);
    letter-spacing: 1px;
    width: 32px;
    flex-shrink: 0;
    text-align: center;
  }

  .cert-name { color: var(--bright); font-size: 12px; flex: 1; }
  .cert-issuer { color: var(--muted); font-size: 10px; letter-spacing: 1px; }

  .verified-badge {
    background: rgba(0,229,160,0.08);
    border: 1px solid rgba(0,229,160,0.25);
    color: var(--green);
    font-size: 9px;
    padding: 2px 6px;
    letter-spacing: 1px;
    flex-shrink: 0;
  }

  /* STATS */
  .stat-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2px;
    margin-bottom: 2px;
  }

  .stat-card {
    background: var(--panel);
    border: 1px solid var(--border);
    padding: 14px 16px;
    text-align: center;
  }

  .stat-num {
    font-family: 'Orbitron', sans-serif;
    font-size: 22px; font-weight: 900;
    color: var(--accent);
    line-height: 1;
    margin-bottom: 4px;
  }

  .stat-label {
    font-size: 9px; color: var(--muted);
    letter-spacing: 2px;
    text-transform: uppercase;
  }

  /* GOALS */
  .goal-row {
    display: flex; gap: 10px;
    align-items: flex-start;
    padding: 6px 0;
    font-size: 12px;
    color: var(--text);
    border-bottom: 1px solid rgba(14,42,68,0.5);
  }

  .goal-row:last-child { border-bottom: none; }

  .goal-icon { color: var(--accent); flex-shrink: 0; width: 16px; }

  /* FOOTER */
  .footer-panel {
    background: var(--panel);
    border: 1px solid var(--border);
    border-bottom: 3px solid var(--accent);
    padding: 18px 20px;
    display: grid;
    grid-template-columns: 1fr auto;
    align-items: center;
    gap: 20px;
  }

  .connect-links {
    display: flex; gap: 8px; flex-wrap: wrap;
  }

  .link-btn {
    display: inline-flex; align-items: center; gap: 6px;
    border: 1px solid var(--border);
    padding: 7px 14px;
    font-family: 'Share Tech Mono', monospace;
    font-size: 11px;
    color: var(--muted);
    text-decoration: none;
    letter-spacing: 1px;
    transition: all 0.2s;
    cursor: pointer;
  }

  .link-btn:hover {
    border-color: var(--accent);
    color: var(--accent);
    background: rgba(0,180,216,0.05);
  }

  .terminal-line {
    font-size: 11px;
    color: var(--muted);
    line-height: 2;
  }

  .terminal-line .cmd { color: var(--accent); }
  .terminal-line .out { color: var(--green); }

  /* CORNER MARKS */
  .corner-tl, .corner-br {
    position: absolute;
    width: 10px; height: 10px;
  }

  .corner-tl { top: -1px; left: -1px; border-top: 2px solid var(--accent); border-left: 2px solid var(--accent); }
  .corner-br { bottom: -1px; right: -1px; border-bottom: 2px solid var(--accent); border-right: 2px solid var(--accent); }

  /* FULL WIDTH PANELS */
  .full { grid-column: 1 / -1; }

  @media (max-width: 600px) {
    .hdr-grid { grid-template-columns: auto 1fr; }
    .status-block { display: none; }
    .main-grid, .proj-grid, .stat-grid { grid-template-columns: 1fr; }
  }
</style>

<div class="scanlines"></div>

<div class="wrap">

  <!-- HEADER -->
  <div class="hdr">
    <div class="corner-tl"></div>
    <div class="corner-br"></div>
    <div class="hdr-grid">
      <div class="avatar">AA</div>
      <div class="name-block">
        <div class="codename">AHMER AMIR</div>
        <div class="subtitle">FULL STACK DEVELOPER &nbsp;·&nbsp; CYBERSECURITY ANALYST &nbsp;·&nbsp; CS UNDERGRADUATE</div>
        <div class="meta-row">
          <div class="meta-item">BASE: <span>KARACHI, PK 🇵🇰</span></div>
          <div class="meta-item">CLASS: <span>UNDERGRADUATE</span></div>
          <div class="meta-item">YEAR: <span>2026</span></div>
        </div>
      </div>
      <div class="status-block">
        <div class="status-pill"><div class="dot"></div>SYSTEM ONLINE</div>
        <div class="status-pill" style="color:var(--gold); border-color:var(--dim);">⬡ OPEN TO HIRE</div>
        <div class="status-pill" style="color:var(--green); border-color:var(--dim);">✓ CERTS VERIFIED</div>
      </div>
    </div>
    <div class="typing-line">
      &gt; directive: <span style="color:var(--bright)">"Build it. Understand it. Break it. Secure it."</span>
      <div class="cursor"></div>
    </div>
  </div>

  <!-- STATS ROW -->
  <div class="stat-grid">
    <div class="stat-card">
      <div class="stat-num">4</div>
      <div class="stat-label">Certifications</div>
    </div>
    <div class="stat-card">
      <div class="stat-num">266</div>
      <div class="stat-label">Contributions</div>
    </div>
    <div class="stat-card">
      <div class="stat-num">2020</div>
      <div class="stat-label">Active Since</div>
    </div>
  </div>

  <!-- MAIN 2-COL -->
  <div class="main-grid">

    <!-- STACK -->
    <div class="panel">
      <div class="panel-title">TECHNOLOGY STACK</div>
      <div class="stack-row">
        <span class="stack-label">FRONTEND</span>
        <span class="stack-val">
          <span class="tag tag-blue">REACT</span>
          <span class="tag tag-blue">JS</span>
          <span class="tag tag-blue">HTML5</span>
          <span class="tag tag-blue">CSS3</span>
        </span>
      </div>
      <div class="stack-row">
        <span class="stack-label">BACKEND</span>
        <span class="stack-val">
          <span class="tag tag-green">NODE.JS</span>
          <span class="tag tag-green">EXPRESS</span>
          <span class="tag tag-green">MONGODB</span>
        </span>
      </div>
      <div class="stack-row">
        <span class="stack-label">SECURITY</span>
        <span class="stack-val">
          <span class="tag tag-red">NMAP</span>
          <span class="tag tag-red">METASPLOIT</span>
          <span class="tag tag-red">BURP</span>
        </span>
      </div>
      <div class="stack-row">
        <span class="stack-label">SCRIPTING</span>
        <span class="stack-val">
          <span class="tag tag-gold">PYTHON</span>
          <span class="tag tag-gold">BASH</span>
          <span class="tag tag-gold">POWERSHELL</span>
        </span>
      </div>
      <div class="stack-row">
        <span class="stack-label">WEB3</span>
        <span class="stack-val">
          <span class="tag tag-blue">SOLIDITY</span>
          <span class="tag tag-blue">ETHEREUM</span>
        </span>
      </div>
      <div class="stack-row">
        <span class="stack-label">TOOLS</span>
        <span class="stack-val">
          <span class="tag tag-green">GIT</span>
          <span class="tag tag-green">LINUX</span>
          <span class="tag tag-green">VSCODE</span>
          <span class="tag tag-green">KALI</span>
        </span>
      </div>
    </div>

    <!-- OBJECTIVE MATRIX -->
    <div class="panel">
      <div class="panel-title">OBJECTIVE MATRIX — 2026</div>
      <div class="goal-row">
        <span class="goal-icon">▸</span>
        Master backend architecture & system design
      </div>
      <div class="goal-row">
        <span class="goal-icon">▸</span>
        Advance penetration testing — CTFs & home lab
      </div>
      <div class="goal-row">
        <span class="goal-icon">▸</span>
        Explore machine learning fundamentals
      </div>
      <div class="goal-row">
        <span class="goal-icon">▸</span>
        AWS cloud & infrastructure basics
      </div>
      <div class="goal-row">
        <span class="goal-icon">▸</span>
        Ship 3 production-grade projects
      </div>
      <div class="goal-row">
        <span class="goal-icon">▸</span>
        Contribute to open source security tooling
      </div>

      <div style="margin-top: 14px; padding-top: 10px; border-top: 1px solid var(--border);">
        <div style="font-size: 10px; color: var(--muted); letter-spacing: 1px; margin-bottom: 6px;">OPEN TO</div>
        <span class="tag tag-blue">WEB DEV</span>
        <span class="tag tag-red">CYBERSECURITY</span>
        <span class="tag tag-gold">IT SUPPORT</span>
        <span class="tag tag-green">COLLABS</span>
      </div>
    </div>

  </div>

  <!-- PROJECTS -->
  <div class="proj-grid">
    <div class="proj-card" data-num="01">
      <div class="proj-name">PORTFOLIO PRIME</div>
      <div class="proj-desc">Dark, animated personal portfolio. Built to feel like a product, not a template.</div>
      <div class="proj-bar"><div class="proj-bar-fill" style="width:100%"></div></div>
      <div class="proj-stack">HTML &nbsp;·&nbsp; CSS &nbsp;·&nbsp; JAVASCRIPT &nbsp;·&nbsp; STATUS: LIVE</div>
    </div>
    <div class="proj-card" data-num="02">
      <div class="proj-name">COMMERCE NEXUS</div>
      <div class="proj-desc">Full stack e-commerce. JWT auth, cart system, product pipeline, order tracking.</div>
      <div class="proj-bar"><div class="proj-bar-fill" style="width:100%"></div></div>
      <div class="proj-stack">REACT &nbsp;·&nbsp; NODE &nbsp;·&nbsp; MONGODB &nbsp;·&nbsp; STATUS: LIVE</div>
    </div>
    <div class="proj-card" data-num="03">
      <div class="proj-name">GHOST SCANNER [SEC]</div>
      <div class="proj-desc">CLI recon tool — host discovery, port scanning, vulnerability enumeration + reports.</div>
      <div class="proj-bar"><div class="proj-bar-fill" style="width:82%"></div></div>
      <div class="proj-stack">PYTHON &nbsp;·&nbsp; NMAP &nbsp;·&nbsp; BASH &nbsp;·&nbsp; STATUS: v0.8 BETA</div>
    </div>
    <div class="proj-card" data-num="04">
      <div class="proj-name">SIGNAL — CHAT PROTOCOL</div>
      <div class="proj-desc">Real-time multi-room messaging. WebSocket architecture + live user presence.</div>
      <div class="proj-bar"><div class="proj-bar-fill" style="width:100%"></div></div>
      <div class="proj-stack">NODE &nbsp;·&nbsp; SOCKET.IO &nbsp;·&nbsp; EXPRESS &nbsp;·&nbsp; STATUS: LIVE</div>
    </div>
  </div>

  <!-- CERTS FULL WIDTH -->
  <div class="panel" style="margin-bottom:2px; position:relative;">
    <div class="corner-tl"></div>
    <div class="panel-title">CLEARANCE REGISTRY — VERIFIED CREDENTIALS</div>
    <div class="cert-row">
      <div class="cert-level">★★★★</div>
      <div>
        <div class="cert-name">CC — Certified in Cybersecurity (SCCP)</div>
        <div class="cert-issuer">ISC²</div>
      </div>
      <div class="verified-badge">VERIFIED</div>
    </div>
    <div class="cert-row">
      <div class="cert-level">★★★★</div>
      <div>
        <div class="cert-name">Cybersecurity Analyst Professional Certificate</div>
        <div class="cert-issuer">IBM</div>
      </div>
      <div class="verified-badge">VERIFIED</div>
    </div>
    <div class="cert-row">
      <div class="cert-level">★★★★</div>
      <div>
        <div class="cert-name">Full Stack JavaScript Developer</div>
        <div class="cert-issuer">IBM</div>
      </div>
      <div class="verified-badge">VERIFIED</div>
    </div>
    <div class="cert-row">
      <div class="cert-level">★★★</div>
      <div>
        <div class="cert-name">IT Support Specialist</div>
        <div class="cert-issuer">GOOGLE</div>
      </div>
      <div class="verified-badge">VERIFIED</div>
    </div>
  </div>

  <!-- GITHUB STATS FULL WIDTH -->
  <div class="panel" style="margin-bottom:2px;">
    <div class="panel-title">GITHUB TELEMETRY</div>
    <div style="display:grid; grid-template-columns:1fr 1fr; gap:12px; flex-wrap:wrap;">
      <img src="https://github-readme-stats-sigma-five.vercel.app/api?username=Ahmer-kun&show_icons=true&hide_border=true&bg_color=040f1e&title_color=00b4d8&icon_color=00b4d8&text_color=c8e8f5&ring_color=0e2a44" style="width:100%; border:1px solid var(--border);" loading="lazy"/>
      <img src="https://streak-stats.demolab.com/?user=Ahmer-kun&hide_border=true&background=040f1e&ring=00b4d8&fire=00b4d8&currStreakLabel=00b4d8&sideLabels=4a7a96&dates=4a7a96&sideNums=e0f4ff&currStreakNum=e0f4ff" style="width:100%; border:1px solid var(--border);" loading="lazy"/>
    </div>
    <div style="margin-top:12px;">
      <img src="https://github-readme-activity-graph.vercel.app/graph?username=Ahmer-kun&bg_color=040f1e&color=00b4d8&line=0e2a44&point=00b4d8&area=true&area_color=0e2a44&hide_border=true" style="width:100%; border:1px solid var(--border);" loading="lazy"/>
    </div>
  </div>

  <!-- OPERATOR PROFILE -->
  <div class="panel" style="margin-bottom:2px;">
    <div class="panel-title">OPERATOR PROFILE</div>
    <div style="display:grid; grid-template-columns:1fr 1fr; gap:0;">
      <div>
        <div class="stack-row"><span class="stack-label">PEAK HOURS</span><span class="stack-val" style="color:var(--gold)">22:00 — 03:00 PKT</span></div>
        <div class="stack-row"><span class="stack-label">COFFEE/DAY</span><span class="stack-val">3 cups minimum</span></div>
        <div class="stack-row"><span class="stack-label">EDITOR</span><span class="stack-val">VS Code</span></div>
        <div class="stack-row"><span class="stack-label">TABS/SPACES</span><span class="stack-val" style="color:var(--red)">SPACES. NON-NEGOTIABLE.</span></div>
      </div>
      <div style="padding-left:20px; border-left:1px solid var(--border);">
        <div class="stack-row"><span class="stack-label">OBSESSION</span><span class="stack-val">CTF challenges</span></div>
        <div class="stack-row"><span class="stack-label">SOUNDTRACK</span><span class="stack-val">Synthwave + Lo-fi</span></div>
        <div class="stack-row"><span class="stack-label">PHILOSOPHY</span><span class="stack-val" style="color:var(--accent)">Understand to protect</span></div>
        <div class="stack-row"><span class="stack-label">CONTACT</span><span class="stack-val" style="color:var(--green)">OPEN</span></div>
      </div>
    </div>
  </div>

  <!-- FOOTER -->
  <div class="footer-panel">
    <div>
      <div style="font-size:9px; color:var(--muted); letter-spacing:2px; margin-bottom:8px;">// ESTABLISH UPLINK</div>
      <div class="connect-links">
        <a class="link-btn" href="https://www.linkedin.com/in/muhammad-ahmer-b88485283" target="_blank">⬡ LINKEDIN</a>
        <a class="link-btn" href="https://github.com/Ahmer-kun" target="_blank">⬡ GITHUB</a>
        <a class="link-btn" href="https://ahmer-kun.github.io/myportfolio/" target="_blank">⬡ PORTFOLIO</a>
      </div>
    </div>
    <div class="terminal-line" style="text-align:right;">
      <div><span class="cmd">&gt; </span><span class="out">uplink established.</span></div>
      <div><span class="cmd">&gt; </span>السَّلاَمُ عَلَيْكُمْ</div>
      <div><span class="cmd">&gt; </span><span class="out">EOF</span><div class="cursor" style="display:inline-block;"></div></div>
    </div>
  </div>

</div>
