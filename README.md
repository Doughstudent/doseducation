# doseducation
unblock gqmes
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>DOS Education – Digital Online Studies</title>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Rajdhani:wght@300;400;600&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0a0a0f;
    --surface: #111118;
    --card: #16161f;
    --border: #1e1e2e;
    --accent: #00ffe0;
    --accent2: #ff3e6c;
    --accent3: #ffe100;
    --text: #e0e0f0;
    --muted: #555577;
    --glow: 0 0 12px #00ffe055;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Rajdhani', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Scanline overlay */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background: repeating-linear-gradient(0deg, transparent, transparent 2px, rgba(0,255,224,0.015) 2px, rgba(0,255,224,0.015) 4px);
    pointer-events: none;
    z-index: 9999;
  }

  /* Grid bg */
  body::after {
    content: '';
    position: fixed;
    inset: 0;
    background-image: linear-gradient(rgba(0,255,224,0.03) 1px, transparent 1px),
                      linear-gradient(90deg, rgba(0,255,224,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  header {
    position: sticky;
    top: 0;
    z-index: 100;
    background: rgba(10,10,15,0.92);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid var(--border);
    padding: 14px 32px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .logo {
    font-family: 'Orbitron', monospace;
    font-size: 1.4rem;
    font-weight: 900;
    letter-spacing: 2px;
    color: var(--accent);
    text-shadow: var(--glow);
  }

  .logo span { color: var(--text); }

  .tagline {
    font-size: 0.75rem;
    letter-spacing: 4px;
    color: var(--muted);
    text-transform: uppercase;
    margin-top: 2px;
  }

  .nav-right {
    display: flex;
    gap: 20px;
    font-size: 0.85rem;
    letter-spacing: 1px;
    color: var(--muted);
  }

  .nav-right span {
    cursor: pointer;
    transition: color 0.2s;
  }

  .nav-right span:hover { color: var(--accent); }

  /* Hero */
  .hero {
    position: relative;
    z-index: 1;
    padding: 48px 32px 24px;
    text-align: center;
  }

  .hero h1 {
    font-family: 'Orbitron', monospace;
    font-size: clamp(1.5rem, 4vw, 3rem);
    font-weight: 900;
    letter-spacing: 3px;
    color: var(--text);
    margin-bottom: 10px;
  }

  .hero h1 em {
    font-style: normal;
    color: var(--accent);
    text-shadow: var(--glow);
  }

  .hero p {
    color: var(--muted);
    font-size: 1rem;
    letter-spacing: 2px;
    text-transform: uppercase;
    margin-bottom: 28px;
  }

  /* Search & filter */
  .controls {
    position: relative;
    z-index: 1;
    display: flex;
    gap: 12px;
    justify-content: center;
    flex-wrap: wrap;
    padding: 0 32px 28px;
  }

  .search-box {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 10px 20px;
    color: var(--text);
    font-family: 'Rajdhani', sans-serif;
    font-size: 1rem;
    letter-spacing: 1px;
    width: 280px;
    outline: none;
    transition: border-color 0.2s, box-shadow 0.2s;
  }

  .search-box:focus {
    border-color: var(--accent);
    box-shadow: var(--glow);
  }

  .filter-btn {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 10px 18px;
    color: var(--muted);
    font-family: 'Rajdhani', sans-serif;
    font-size: 0.9rem;
    letter-spacing: 1px;
    cursor: pointer;
    transition: all 0.2s;
    text-transform: uppercase;
  }

  .filter-btn:hover,
  .filter-btn.active {
    border-color: var(--accent);
    color: var(--accent);
    box-shadow: var(--glow);
  }

  /* Section */
  .section {
    position: relative;
    z-index: 1;
    padding: 0 32px 48px;
  }

  .section-title {
    font-family: 'Orbitron', monospace;
    font-size: 0.85rem;
    letter-spacing: 4px;
    color: var(--muted);
    text-transform: uppercase;
    margin-bottom: 20px;
    padding-bottom: 10px;
    border-bottom: 1px solid var(--border);
    display: flex;
    align-items: center;
    gap: 12px;
  }

  .section-title::before {
    content: '';
    display: block;
    width: 4px;
    height: 16px;
    background: var(--accent);
    box-shadow: var(--glow);
  }

  /* Game grid */
  .game-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 16px;
  }

  .game-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 6px;
    overflow: hidden;
    cursor: pointer;
    transition: all 0.25s;
    text-decoration: none;
    display: block;
    position: relative;
  }

  .game-card:hover {
    border-color: var(--accent);
    transform: translateY(-4px);
    box-shadow: 0 8px 32px rgba(0,255,224,0.12);
  }

  .game-card:hover .game-thumb { filter: brightness(1.1) saturate(1.3); }

  .game-thumb {
    width: 100%;
    height: 120px;
    object-fit: cover;
    display: block;
    transition: filter 0.25s;
    background: #0d0d1a;
  }

  .game-thumb-placeholder {
    width: 100%;
    height: 120px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 3rem;
    background: linear-gradient(135deg, #0d0d1a 0%, #12121e 100%);
    transition: filter 0.25s;
  }

  .game-info {
    padding: 12px 14px;
  }

  .game-name {
    font-family: 'Orbitron', monospace;
    font-size: 0.75rem;
    font-weight: 700;
    letter-spacing: 1px;
    color: var(--text);
    margin-bottom: 4px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  .game-desc {
    font-size: 0.8rem;
    color: var(--muted);
    line-height: 1.4;
    letter-spacing: 0.5px;
  }

  .game-tag {
    position: absolute;
    top: 8px;
    right: 8px;
    background: rgba(0,0,0,0.75);
    backdrop-filter: blur(6px);
    border-radius: 3px;
    padding: 2px 7px;
    font-size: 0.65rem;
    font-family: 'Orbitron', monospace;
    letter-spacing: 1px;
    text-transform: uppercase;
  }

  .tag-all { color: var(--accent); border: 1px solid var(--accent)44; }
  .tag-13 { color: var(--accent2); border: 1px solid var(--accent2)44; }
  .tag-hot { color: var(--accent3); border: 1px solid var(--accent3)44; }

  /* Launch overlay */
  .overlay {
    display: none;
    position: fixed;
    inset: 0;
    z-index: 9998;
    background: rgba(0,0,0,0.92);
    flex-direction: column;
    align-items: center;
    justify-content: center;
    backdrop-filter: blur(8px);
  }

  .overlay.open { display: flex; }

  .launch-box {
    background: var(--card);
    border: 1px solid var(--accent);
    border-radius: 10px;
    padding: 48px 56px;
    text-align: center;
    max-width: 420px;
    width: 90%;
    box-shadow: 0 0 60px rgba(0,255,224,0.15);
    animation: popIn 0.2s ease;
  }

  @keyframes popIn {
    from { transform: scale(0.9); opacity: 0; }
    to { transform: scale(1); opacity: 1; }
  }

  .launch-emoji { font-size: 4rem; margin-bottom: 16px; }

  .overlay-title {
    font-family: 'Orbitron', monospace;
    font-size: 1rem;
    color: var(--accent);
    letter-spacing: 2px;
    margin-bottom: 10px;
  }

  .launch-desc {
    color: var(--muted);
    font-size: 0.85rem;
    letter-spacing: 1px;
    margin-bottom: 28px;
    line-height: 1.6;
  }

  .btn-play {
    background: var(--accent);
    color: #000;
    border: none;
    border-radius: 5px;
    padding: 12px 32px;
    font-family: 'Orbitron', monospace;
    font-size: 0.85rem;
    font-weight: 700;
    letter-spacing: 2px;
    cursor: pointer;
    transition: opacity 0.2s, transform 0.15s;
    display: block;
    width: 100%;
    margin-bottom: 12px;
  }

  .btn-play:hover { opacity: 0.85; transform: scale(1.02); }

  .overlay-close {
    background: transparent;
    color: var(--muted);
    border: 1px solid var(--border);
    border-radius: 5px;
    padding: 10px 32px;
    font-family: 'Orbitron', monospace;
    font-size: 0.75rem;
    letter-spacing: 1px;
    cursor: pointer;
    transition: all 0.2s;
    display: block;
    width: 100%;
  }

  .overlay-close:hover { border-color: var(--accent2); color: var(--accent2); }

  /* Marquee ticker */
  .ticker {
    background: var(--accent);
    color: #000;
    padding: 6px 0;
    overflow: hidden;
    position: relative;
    z-index: 1;
    margin-bottom: 32px;
  }

  .ticker-inner {
    display: flex;
    gap: 60px;
    animation: ticker 30s linear infinite;
    white-space: nowrap;
    font-family: 'Orbitron', monospace;
    font-size: 0.7rem;
    font-weight: 700;
    letter-spacing: 2px;
  }

  @keyframes ticker {
    from { transform: translateX(0); }
    to { transform: translateX(-50%); }
  }

  .hidden { display: none !important; }

  .proxy-card {
    display: flex;
    gap: 16px;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 18px;
    text-decoration: none;
    transition: all 0.25s;
    align-items: flex-start;
  }

  .proxy-card:hover {
    border-color: #5865F2;
    transform: translateY(-3px);
    box-shadow: 0 8px 28px rgba(88,101,242,0.15);
  }

  .proxy-icon {
    font-size: 2rem;
    flex-shrink: 0;
    margin-top: 2px;
  }

  .proxy-name {
    font-family: 'Orbitron', monospace;
    font-size: 0.78rem;
    font-weight: 700;
    letter-spacing: 1px;
    color: var(--text);
    margin-bottom: 6px;
  }

  .proxy-desc {
    font-size: 0.82rem;
    color: var(--muted);
    line-height: 1.5;
    margin-bottom: 10px;
  }

  .proxy-tags { display: flex; flex-wrap: wrap; gap: 6px; }

  .ptag {
    background: rgba(88,101,242,0.12);
    border: 1px solid rgba(88,101,242,0.3);
    color: #9aa0f5;
    border-radius: 3px;
    padding: 2px 8px;
    font-size: 0.7rem;
    font-family: 'Orbitron', monospace;
    letter-spacing: 0.5px;
  }

  /* Responsive */
  @media(max-width: 600px) {
    header { padding: 12px 16px; }
    .section { padding: 0 16px 32px; }
    .controls { padding: 0 16px 20px; }
    .hero { padding: 32px 16px 16px; }
    .game-grid { grid-template-columns: repeat(auto-fill, minmax(150px, 1fr)); gap: 12px; }
  }
</style>
</head>
<body>

<header>
  <div>
    <div class="logo">DOS<span>education</span></div>
    <div class="tagline">Digital Online Studies — Interactive Learning Portal</div>
  </div>
  <div class="nav-right">
    <span>Curriculum</span>
    <span>Resources</span>
    <a href="https://discord.com/users/xuaoxiaolingy" target="_blank" style="text-decoration:none; display:flex; align-items:center; gap:8px; background:#5865F222; border:1px solid #5865F255; border-radius:5px; padding:7px 14px; color:#fff; font-family:'Rajdhani',sans-serif; font-size:0.85rem; letter-spacing:1px; transition:all 0.2s;" onmouseover="this.style.background='#5865F244';this.style.borderColor='#5865F2'" onmouseout="this.style.background='#5865F222';this.style.borderColor='#5865F255'">
      <svg width="18" height="18" viewBox="0 0 24 24" fill="#5865F2"><path d="M20.317 4.37a19.791 19.791 0 0 0-4.885-1.515.074.074 0 0 0-.079.037c-.21.375-.444.864-.608 1.25a18.27 18.27 0 0 0-5.487 0 12.64 12.64 0 0 0-.617-1.25.077.077 0 0 0-.079-.037A19.736 19.736 0 0 0 3.677 4.37a.07.07 0 0 0-.032.027C.533 9.046-.32 13.58.099 18.057c.002.022.015.043.032.053a19.9 19.9 0 0 0 5.993 3.03.077.077 0 0 0 .084-.028 14.09 14.09 0 0 0 1.226-1.994.076.076 0 0 0-.041-.106 13.107 13.107 0 0 1-1.872-.892.077.077 0 0 1-.008-.128 10.2 10.2 0 0 0 .372-.292.074.074 0 0 1 .077-.01c3.928 1.793 8.18 1.793 12.062 0a.074.074 0 0 1 .078.01c.12.098.246.198.373.292a.077.077 0 0 1-.006.127 12.299 12.299 0 0 1-1.873.892.077.077 0 0 0-.041.107c.36.698.772 1.362 1.225 1.993a.076.076 0 0 0 .084.028 19.839 19.839 0 0 0 6.002-3.03.077.077 0 0 0 .032-.054c.5-5.177-.838-9.674-3.549-13.66a.061.061 0 0 0-.031-.03zM8.02 15.33c-1.183 0-2.157-1.085-2.157-2.419 0-1.333.956-2.419 2.157-2.419 1.21 0 2.176 1.096 2.157 2.42 0 1.333-.956 2.418-2.157 2.418zm7.975 0c-1.183 0-2.157-1.085-2.157-2.419 0-1.333.955-2.419 2.157-2.419 1.21 0 2.176 1.096 2.157 2.42 0 1.333-.946 2.418-2.157 2.418z"/></svg>
      <span style="color:#5865F2; font-weight:600;">xuaoxiaolingy</span>
    </a>
  </div>
</header>

<!-- Ticker -->
<div class="ticker">
  <div class="ticker-inner" id="ticker">
    🎮 KRUNKER.IO &nbsp;·&nbsp; SHELL SHOCKERS &nbsp;·&nbsp; 1V1.LOL &nbsp;·&nbsp; SLITHER.IO &nbsp;·&nbsp; AGAR.IO &nbsp;·&nbsp; DIEP.IO &nbsp;·&nbsp; PAPER.IO &nbsp;·&nbsp; ZOMBS.IO &nbsp;·&nbsp; MINESWEEPER &nbsp;·&nbsp; 2048 &nbsp;·&nbsp; TETRIS &nbsp;·&nbsp; SNAKE &nbsp;·&nbsp; DRIFT BOSS &nbsp;·&nbsp; VENGE.IO &nbsp;·&nbsp; LORDZ.IO &nbsp;·&nbsp; WORMATE.IO &nbsp;·&nbsp; TANK ROYALE &nbsp;·&nbsp; HEXAR.IO &nbsp;·&nbsp; NOW LOADING... 🎮 KRUNKER.IO &nbsp;·&nbsp; SHELL SHOCKERS &nbsp;·&nbsp; 1V1.LOL &nbsp;·&nbsp; SLITHER.IO &nbsp;·&nbsp; AGAR.IO &nbsp;·&nbsp; DIEP.IO &nbsp;·&nbsp; PAPER.IO &nbsp;·&nbsp; ZOMBS.IO &nbsp;·&nbsp; MINESWEEPER &nbsp;·&nbsp; 2048 &nbsp;·&nbsp; TETRIS &nbsp;·&nbsp; SNAKE &nbsp;·&nbsp; DRIFT BOSS &nbsp;·&nbsp; VENGE.IO &nbsp;·&nbsp; LORDZ.IO &nbsp;·&nbsp; WORMATE.IO &nbsp;·&nbsp; TANK ROYALE &nbsp;·&nbsp; HEXAR.IO &nbsp;·&nbsp; NOW LOADING...
  </div>
</div>

<div class="hero">
  <h1>INTERACTIVE <em>STUDY</em> MODULES</h1>
  <p>Engage your brain — all platforms, all speeds</p>
</div>

<div class="controls">
  <input class="search-box" type="text" placeholder="Search modules..." id="searchInput" oninput="filterGames()">
  <button class="filter-btn active" onclick="setFilter('all', this)">All</button>
  <button class="filter-btn" onclick="setFilter('action', this)">Action</button>
  <button class="filter-btn" onclick="setFilter('io', this)">IO Games</button>
  <button class="filter-btn" onclick="setFilter('puzzle', this)">Puzzle</button>
  <button class="filter-btn" onclick="setFilter('racing', this)">Racing</button>
  <button class="filter-btn" onclick="setFilter('shooter', this)">Shooter</button>
  <button class="filter-btn" onclick="setFilter('13+', this)">13+</button>
</div>

<div class="section">
  <div class="section-title">🔥 HOT RIGHT NOW</div>
  <div class="game-grid" id="gameGrid"></div>
</div>

<!-- PROXIES SECTION -->
<div class="section" style="margin-top:8px; padding-bottom: 60px;">
  <div class="section-title">🌐 WEB PROXIES — BYPASS FILTERS</div>
  <p style="color:var(--muted); font-size:0.85rem; letter-spacing:1px; margin-bottom:20px; line-height:1.7;">These proxies let you access Roblox, YouTube, and other blocked sites through your browser. If one is down, try another — they rotate frequently.</p>
  <div style="display:grid; grid-template-columns: repeat(auto-fill, minmax(260px, 1fr)); gap:16px;" id="proxyGrid">

    <!-- Ultraviolet / Titanium -->
    <a href="https://titaniumnetwork.org" target="_blank" class="proxy-card">
      <div class="proxy-icon">🔷</div>
      <div class="proxy-info">
        <div class="proxy-name">Titanium Network</div>
        <div class="proxy-desc">Hosts Ultraviolet proxy — one of the most powerful. Supports Roblox, YouTube, and most sites.</div>
        <div class="proxy-tags"><span class="ptag">Roblox</span><span class="ptag">YouTube</span><span class="ptag">UV Proxy</span></div>
      </div>
    </a>

    <!-- Holy Unblocker -->
    <a href="https://holyubofficial.net" target="_blank" class="proxy-card">
      <div class="proxy-icon">😇</div>
      <div class="proxy-info">
        <div class="proxy-name">Holy Unblocker</div>
        <div class="proxy-desc">Popular school bypass with built-in games and proxy tabs. Very well maintained.</div>
        <div class="proxy-tags"><span class="ptag">Games</span><span class="ptag">Sites</span><span class="ptag">Stealth</span></div>
      </div>
    </a>

    <!-- Interstellar -->
    <a href="https://interstellarnetwork.pages.dev" target="_blank" class="proxy-card">
      <div class="proxy-icon">🚀</div>
      <div class="proxy-info">
        <div class="proxy-name">Interstellar</div>
        <div class="proxy-desc">Fast Cloudflare-hosted proxy with Ultraviolet backend. Great for gaming sites.</div>
        <div class="proxy-tags"><span class="ptag">Fast</span><span class="ptag">Cloudflare</span><span class="ptag">Games</span></div>
      </div>
    </a>

    <!-- Rammerhead -->
    <a href="https://rammerhead.org" target="_blank" class="proxy-card">
      <div class="proxy-icon">🐏</div>
      <div class="proxy-info">
        <div class="proxy-name">Rammerhead</div>
        <div class="proxy-desc">Browser-based proxy that rewrites traffic. Works on most school networks.</div>
        <div class="proxy-tags"><span class="ptag">Browser Proxy</span><span class="ptag">Roblox</span></div>
      </div>
    </a>

    <!-- Corrosion -->
    <a href="https://corrosion.party" target="_blank" class="proxy-card">
      <div class="proxy-icon">⚗️</div>
      <div class="proxy-info">
        <div class="proxy-name">Corrosion Party</div>
        <div class="proxy-desc">Web proxy with multiple backends. Clean UI and regularly updated mirrors.</div>
        <div class="proxy-tags"><span class="ptag">Multi-backend</span><span class="ptag">Sites</span></div>
      </div>
    </a>

    <!-- Nebula Proxy -->
    <a href="https://nebulaproxy.io" target="_blank" class="proxy-card">
      <div class="proxy-icon">🌌</div>
      <div class="proxy-info">
        <div class="proxy-name">Nebula Proxy</div>
        <div class="proxy-desc">Clean dark-themed proxy site. Good for unblocking social media and games at school.</div>
        <div class="proxy-tags"><span class="ptag">Social</span><span class="ptag">Games</span><span class="ptag">Dark Mode</span></div>
      </div>
    </a>

    <!-- Incognito Proxy -->
    <a href="https://incognitosite.pages.dev" target="_blank" class="proxy-card">
      <div class="proxy-icon">🕵️</div>
      <div class="proxy-info">
        <div class="proxy-name">Incognito Unblocker</div>
        <div class="proxy-desc">Lightweight pages.dev hosted proxy. Harder for school filters to detect.</div>
        <div class="proxy-tags"><span class="ptag">Stealth</span><span class="ptag">Lightweight</span></div>
      </div>
    </a>

    <!-- 3kh0 -->
    <a href="https://3kh0.github.io" target="_blank" class="proxy-card">
      <div class="proxy-icon">🎮</div>
      <div class="proxy-info">
        <div class="proxy-name">3kh0 Games + Proxy</div>
        <div class="proxy-desc">GitHub-hosted unblocked games site with built-in web proxy. Tons of games included too.</div>
        <div class="proxy-tags"><span class="ptag">GitHub</span><span class="ptag">Games</span><span class="ptag">Proxy</span></div>
      </div>
    </a>

    <!-- Hypertabs -->
    <a href="https://hypertabs.cc" target="_blank" class="proxy-card">
      <div class="proxy-icon">📑</div>
      <div class="proxy-info">
        <div class="proxy-name">HyperTabs</div>
        <div class="proxy-desc">Disguises browsing as a fake school tab. Hides games/sites behind a Google Classroom look.</div>
        <div class="proxy-tags"><span class="ptag">Stealth</span><span class="ptag">Disguised</span><span class="ptag">🔥 Smart</span></div>
      </div>
    </a>

    <!-- Sussy Proxy -->
    <a href="https://sassyproxy.pages.dev" target="_blank" class="proxy-card">
      <div class="proxy-icon">📡</div>
      <div class="proxy-info">
        <div class="proxy-name">Sassy Proxy</div>
        <div class="proxy-desc">Reliable Cloudflare Pages proxy. One of the harder ones for school blocks to catch.</div>
        <div class="proxy-tags"><span class="ptag">Cloudflare</span><span class="ptag">Reliable</span></div>
      </div>
    </a>

  </div>

  <div style="margin-top:24px; background:var(--card); border:1px solid var(--border); border-left: 3px solid var(--accent3); border-radius:6px; padding:16px 20px;">
    <div style="font-family:'Orbitron',monospace; font-size:0.75rem; color:var(--accent3); letter-spacing:2px; margin-bottom:8px;">💡 PRO TIPS</div>
    <div style="color:var(--muted); font-size:0.85rem; line-height:1.8; letter-spacing:0.5px;">
      • If a proxy is blocked, try it on your <strong style="color:var(--text)">phone's data</strong> to confirm it works, then access from school<br>
      • <strong style="color:var(--text)">Cloudflare Pages (.pages.dev)</strong> and <strong style="color:var(--text)">GitHub Pages (.github.io)</strong> are the hardest for schools to block<br>
      • Use <strong style="color:var(--text)">HyperTabs</strong> if teachers walk by — it looks like Google Classroom<br>
      • For Roblox specifically, <strong style="color:var(--text)">Ultraviolet proxy</strong> (Titanium/Interstellar) gives the best results
    </div>
  </div>
</div>

<!-- Launch Overlay -->
<div class="overlay" id="overlay">
  <div class="launch-box">
    <div class="launch-emoji" id="launchEmoji">🎮</div>
    <div class="overlay-title" id="overlayTitle">GAME NAME</div>
    <div class="launch-desc">Click the button below to launch this game.<br>It will open in a new tab.</div>
    <button class="btn-play" id="playBtn" onclick="launchGame()">▶ &nbsp; PLAY NOW</button>
    <button class="overlay-close" onclick="closeGame()">✕ &nbsp; CANCEL</button>
  </div>
</div>

<script>
const games = [
  // IO GAMES
  { name: "Krunker.io", desc: "Pixel FPS battle royale", emoji: "🎯", url: "https://krunker.io", cat: "shooter", age: "13+", hot: true },
  { name: "Slither.io", desc: "Grow your snake, eat others", emoji: "🐍", url: "https://slither.io", cat: "io", age: "all", hot: true },
  { name: "Agar.io", desc: "Classic cell munching", emoji: "🔵", url: "https://agar.io", cat: "io", age: "all", hot: true },
  { name: "Diep.io", desc: "Tank upgrade shooter", emoji: "🚀", url: "https://diep.io", cat: "shooter", age: "all", hot: false },
  { name: "Paper.io 2", desc: "Claim territory, defeat rivals", emoji: "📄", url: "https://paper-io.com", cat: "io", age: "all", hot: true },
  { name: "Zombs.io", desc: "Survive zombie waves", emoji: "🧟", url: "https://zombs.io", cat: "action", age: "13+", hot: false },
  { name: "Wormate.io", desc: "Candy snake mayhem", emoji: "🍭", url: "https://wormate.io", cat: "io", age: "all", hot: false },
  { name: "Lordz.io", desc: "Medieval real-time strategy", emoji: "⚔️", url: "https://lordz.io", cat: "action", age: "all", hot: false },
  { name: "Hexar.io", desc: "Hex grid domination", emoji: "🔷", url: "https://hexar.io", cat: "io", age: "all", hot: false },
  { name: "Mope.io", desc: "Animal food chain survival", emoji: "🦁", url: "https://mope.io", cat: "io", age: "all", hot: false },
  { name: "Starve.io", desc: "Craft & survive multiplayer", emoji: "🪓", url: "https://starve.io", cat: "action", age: "13+", hot: false },
  { name: "Defly.io", desc: "Helicopter territory war", emoji: "🚁", url: "https://defly.io", cat: "action", age: "all", hot: false },
  { name: "Brutal.io", desc: "Flail weapon battle royale", emoji: "⛓️", url: "https://brutal.io", cat: "action", age: "13+", hot: true },
  { name: "Spinz.io", desc: "Fidget spinner battles", emoji: "🌀", url: "https://spinz.io", cat: "io", age: "all", hot: false },
  { name: "Wilds.io", desc: "RPG battle arena", emoji: "🗡️", url: "https://wilds.io", cat: "action", age: "13+", hot: false },

  // SHOOTERS & ACTION
  { name: "Shell Shockers", desc: "Egg FPS multiplayer", emoji: "🥚", url: "https://shellshock.io", cat: "shooter", age: "13+", hot: true },
  { name: "1v1.lol", desc: "Build & shoot battle royale", emoji: "🏗️", url: "https://1v1.lol", cat: "shooter", age: "13+", hot: true },
  { name: "Venge.io", desc: "3D tactical FPS", emoji: "🔫", url: "https://venge.io", cat: "shooter", age: "13+", hot: true },
  { name: "War Brokers", desc: "Voxel multiplayer FPS", emoji: "🪖", url: "https://warbrokers.io", cat: "shooter", age: "13+", hot: false },
  { name: "Bullet Force", desc: "Realistic online FPS", emoji: "💥", url: "https://www.crazygames.com/game/bullet-force-multiplayer", cat: "shooter", age: "13+", hot: false },
  { name: "Combat Online", desc: "3D shooter action", emoji: "🎖️", url: "https://www.crazygames.com/game/combat-online", cat: "shooter", age: "13+", hot: false },

  // PUZZLE & CLASSICS
  { name: "2048", desc: "Merge tiles to win", emoji: "🔢", url: "https://play2048.co", cat: "puzzle", age: "all", hot: false },
  { name: "Minesweeper", desc: "Classic bomb defuser", emoji: "💣", url: "https://minesweeper.online", cat: "puzzle", age: "all", hot: false },
  { name: "Sudoku.com", desc: "Number logic puzzles", emoji: "🔲", url: "https://sudoku.com", cat: "puzzle", age: "all", hot: false },
  { name: "Chess.com", desc: "Play chess online", emoji: "♟️", url: "https://www.chess.com/play/online", cat: "puzzle", age: "all", hot: true },
  { name: "Wordle", desc: "5-letter word guessing", emoji: "🟩", url: "https://wordplay.com", cat: "puzzle", age: "all", hot: false },
  { name: "Tetris", desc: "The classic block stacker", emoji: "🟦", url: "https://tetris.com/play-tetris", cat: "puzzle", age: "all", hot: false },
  { name: "Mahjong", desc: "Tile matching strategy", emoji: "🀄", url: "https://www.crazygames.com/game/mahjong-classic", cat: "puzzle", age: "all", hot: false },

  // RACING
  { name: "Drift Boss", desc: "Drift around corners endlessly", emoji: "🏎️", url: "https://www.crazygames.com/game/drift-boss", cat: "racing", age: "all", hot: true },
  { name: "Moto X3M", desc: "Insane bike stunts", emoji: "🏍️", url: "https://www.crazygames.com/game/moto-x3m", cat: "racing", age: "all", hot: true },
  { name: "Slope", desc: "Speed ball on slope", emoji: "⚽", url: "https://slope-game.github.io", cat: "racing", age: "all", hot: true },
  { name: "Run 3", desc: "Endless runner in space", emoji: "🏃", url: "https://www.crazygames.com/game/run-3-game", cat: "racing", age: "all", hot: false },
  { name: "Tunnel Rush", desc: "Neon speed tunnel", emoji: "🌈", url: "https://www.crazygames.com/game/tunnel-rush", cat: "racing", age: "all", hot: false },
  { name: "Drive Mad", desc: "Physics car challenges", emoji: "🚙", url: "https://www.crazygames.com/game/drive-mad", cat: "racing", age: "all", hot: false },
  { name: "Road Fury", desc: "Highway survival shooter", emoji: "🛣️", url: "https://www.crazygames.com/game/road-fury", cat: "racing", age: "13+", hot: false },

  // MORE ACTION
  { name: "Stickman Hook", desc: "Web-slinging stickman", emoji: "🕷️", url: "https://www.crazygames.com/game/stickman-hook", cat: "action", age: "all", hot: false },
  { name: "Minecraft Classic", desc: "Build in the original MC", emoji: "⛏️", url: "https://classic.minecraft.net", cat: "action", age: "all", hot: true },
  { name: "Friday Night Funkin", desc: "Rhythm battle game", emoji: "🎵", url: "https://www.crazygames.com/game/friday-night-funkin", cat: "action", age: "13+", hot: true },
  { name: "Among Us Online", desc: "Find the impostor", emoji: "🔴", url: "https://www.crazygames.com/game/among-us-online-edition", cat: "action", age: "all", hot: true },
  { name: "Dino Game", desc: "Chrome offline dinosaur", emoji: "🦕", url: "https://chromedino.com", cat: "action", age: "all", hot: false },
  { name: "Stick Duel", desc: "Battle stickman fighting", emoji: "🥊", url: "https://www.crazygames.com/game/stick-duel-battle", cat: "action", age: "13+", hot: false },
  { name: "Rooftop Snipers", desc: "2-player rooftop duels", emoji: "🎯", url: "https://www.crazygames.com/game/rooftop-snipers", cat: "shooter", age: "13+", hot: false },
  { name: "Basketball Stars", desc: "1v1 basketball skills", emoji: "🏀", url: "https://www.crazygames.com/game/basketball-stars", cat: "action", age: "all", hot: false },
  { name: "Rocket Soccer", desc: "Cars + soccer madness", emoji: "🚗", url: "https://www.crazygames.com/game/rocket-soccer-derby", cat: "action", age: "all", hot: false },
  { name: "Smash Karts", desc: "Go-kart battle arena", emoji: "💨", url: "https://smashkarts.io", cat: "action", age: "all", hot: true },
  { name: "Bonk.io", desc: "Physics ball battles", emoji: "🎱", url: "https://bonk.io", cat: "io", age: "all", hot: false },
  { name: "Skribbl.io", desc: "Draw & guess with friends", emoji: "✏️", url: "https://skribbl.io", cat: "puzzle", age: "all", hot: true },
  { name: "GarticPhone", desc: "Telephone drawing chaos", emoji: "📞", url: "https://garticphone.com", cat: "puzzle", age: "13+", hot: false },

  // MORE IO
  { name: "Surviv.io", desc: "2D battle royale shooter", emoji: "🪖", url: "https://surviv.io", cat: "shooter", age: "13+", hot: true },
  { name: "Yohoho.io", desc: "Pirate battle royale", emoji: "🏴‍☠️", url: "https://yohoho.io", cat: "io", age: "all", hot: false },
  { name: "Stabfish.io", desc: "Fish stab multiplayer", emoji: "🐟", url: "https://stabfish.io", cat: "io", age: "all", hot: false },
  { name: "Snowball.io", desc: "Snowball fight arena", emoji: "❄️", url: "https://snowball.io", cat: "io", age: "all", hot: false },
  { name: "Skate Hooligans", desc: "Endless skate runner", emoji: "🛹", url: "https://www.crazygames.com/game/skate-hooligans", cat: "racing", age: "all", hot: false },
  { name: "Ev.io", desc: "Sci-fi FPS arena shooter", emoji: "👾", url: "https://ev.io", cat: "shooter", age: "13+", hot: true },
  { name: "Narrow.one", desc: "Medieval castle archery", emoji: "🏹", url: "https://narrow.one", cat: "action", age: "all", hot: true },
  { name: "Blumgi Slime", desc: "Slime jumping platformer", emoji: "🟢", url: "https://www.crazygames.com/game/blumgi-slime", cat: "action", age: "all", hot: false },
  { name: "Getaway Shootout", desc: "Chaotic escape battles", emoji: "🚨", url: "https://www.crazygames.com/game/getaway-shootout", cat: "action", age: "13+", hot: true },
  { name: "Ragdoll Archers", desc: "Floppy archer battles", emoji: "🏹", url: "https://www.crazygames.com/game/ragdoll-archers", cat: "action", age: "13+", hot: false },
  { name: "Stickman Climb", desc: "Sticky climbing walls", emoji: "🧗", url: "https://www.crazygames.com/game/stickman-climb-2", cat: "action", age: "all", hot: false },
  { name: "Only Up Parkour", desc: "Endless upward parkour", emoji: "⬆️", url: "https://www.crazygames.com/game/only-up-parkour", cat: "action", age: "all", hot: true },
  { name: "Monkey Mart", desc: "Run a jungle supermarket", emoji: "🐒", url: "https://www.crazygames.com/game/monkey-mart", cat: "action", age: "all", hot: false },
  { name: "Zombie Tsunami", desc: "Grow your zombie horde", emoji: "🧟", url: "https://www.crazygames.com/game/zombie-tsunami", cat: "action", age: "13+", hot: false },
  { name: "Spacebar Clicker", desc: "How fast can you click?", emoji: "⌨️", url: "https://spacebar-clicker.com", cat: "puzzle", age: "all", hot: false },
  { name: "Cookie Clicker", desc: "Bake infinite cookies", emoji: "🍪", url: "https://orteil.dashnet.org/cookieclicker/", cat: "puzzle", age: "all", hot: true },
  { name: "Crossy Road", desc: "Hop across the road", emoji: "🐔", url: "https://www.crazygames.com/game/crossy-road-online", cat: "action", age: "all", hot: false },
  { name: "Stack Bounce", desc: "Break through stack tiles", emoji: "🔴", url: "https://www.crazygames.com/game/stack-bounce", cat: "action", age: "all", hot: false },
  { name: "Soccer Physics", desc: "Floppy soccer 2-player", emoji: "⚽", url: "https://www.crazygames.com/game/soccer-physics", cat: "action", age: "all", hot: false },
  { name: "Fireboy & Watergirl", desc: "Co-op elemental puzzles", emoji: "🔥", url: "https://www.crazygames.com/game/fireboy-and-watergirl-1-forest-temple", cat: "puzzle", age: "all", hot: true },
  { name: "Jacksmith", desc: "Forge weapons for warriors", emoji: "⚒️", url: "https://www.crazygames.com/game/jacksmith", cat: "puzzle", age: "all", hot: false },
  { name: "Bloons TD", desc: "Tower defense balloon pop", emoji: "🎈", url: "https://www.crazygames.com/game/bloons-tower-defense-5", cat: "puzzle", age: "all", hot: true },
  { name: "Happy Wheels", desc: "Gory physics ragdoll", emoji: "🩸", url: "https://www.crazygames.com/game/happy-wheels", cat: "action", age: "13+", hot: true },
  { name: "Super Smash Flash 2", desc: "Fan-made Smash Bros", emoji: "👊", url: "https://www.crazygames.com/game/super-smash-flash-2", cat: "action", age: "all", hot: true },
  { name: "Tanki Online", desc: "Multiplayer tank battles", emoji: "🛡️", url: "https://tankionline.com", cat: "shooter", age: "13+", hot: false },
  { name: "Warscrap.io", desc: "Tank arena io game", emoji: "💣", url: "https://warscrap.io", cat: "shooter", age: "13+", hot: false },
  { name: "Smash Karts 2", desc: "Kart battle arena sequel", emoji: "🏁", url: "https://www.crazygames.com/game/smash-karts", cat: "racing", age: "all", hot: false },
  { name: "Rocket Bot Royale", desc: "Tank battle royale", emoji: "🚀", url: "https://rocketbotroyale.winterpixel.io", cat: "shooter", age: "13+", hot: true },
  { name: "Powerline.io", desc: "Neon snake power grid", emoji: "⚡", url: "https://powerline.io", cat: "io", age: "all", hot: false },
  { name: "Kirka.io", desc: "Stylized FPS multiplayer", emoji: "🎮", url: "https://kirka.io", cat: "shooter", age: "13+", hot: true },
  { name: "Swordz.io", desc: "Sword arena battles", emoji: "🗡️", url: "https://swordz.io", cat: "io", age: "13+", hot: false },
  { name: "Superhex.io", desc: "Hex territory capture", emoji: "🔶", url: "https://superhex.io", cat: "io", age: "all", hot: false },
  { name: "Little Big Snake", desc: "Snake RPG adventure", emoji: "🐉", url: "https://littlebigsnake.com", cat: "io", age: "all", hot: false },
  { name: "Zombotron", desc: "Metal slug-style shooter", emoji: "🤖", url: "https://www.crazygames.com/game/zombotron", cat: "action", age: "13+", hot: false },
  { name: "Duck Life 4", desc: "Train your racing duck", emoji: "🦆", url: "https://www.crazygames.com/game/duck-life-4", cat: "puzzle", age: "all", hot: false },
  { name: "Fancy Pants", desc: "Smooth stickman platformer", emoji: "👖", url: "https://www.crazygames.com/game/fancy-pants-adventures", cat: "action", age: "all", hot: false },
  { name: "Age of War", desc: "Evolving strategy war", emoji: "⚔️", url: "https://www.crazygames.com/game/age-of-war", cat: "action", age: "13+", hot: false },
  { name: "Swords & Souls", desc: "Train a gladiator fighter", emoji: "🛡️", url: "https://www.crazygames.com/game/swords-and-souls", cat: "action", age: "13+", hot: false },
  { name: "Papa's Freezeria", desc: "Ice cream shop sim", emoji: "🍦", url: "https://www.crazygames.com/game/papas-freezeria", cat: "puzzle", age: "all", hot: false },
  { name: "Doodle Jump", desc: "Bounce to the top", emoji: "🐸", url: "https://www.crazygames.com/game/doodle-jump", cat: "action", age: "all", hot: false },
  { name: "Geometry Dash Lite", desc: "Rhythm platformer hell", emoji: "🔺", url: "https://www.crazygames.com/game/geometry-dash-lite", cat: "action", age: "all", hot: true },
  { name: "Temple Run 2", desc: "Endless jungle escape run", emoji: "🏃", url: "https://www.crazygames.com/game/temple-run-2", cat: "racing", age: "all", hot: false },
  { name: "Death Run 3D", desc: "Dodge deadly obstacles", emoji: "💀", url: "https://www.crazygames.com/game/death-run-3d", cat: "racing", age: "13+", hot: false },
  { name: "Drift Hunters", desc: "Car drifting simulator", emoji: "🌫️", url: "https://www.crazygames.com/game/drift-hunters", cat: "racing", age: "all", hot: true },
  { name: "Parking Fury 3D", desc: "Realistic parking sim", emoji: "🅿️", url: "https://www.crazygames.com/game/parking-fury-3d", cat: "racing", age: "all", hot: false },
  { name: "Stunt Simulator", desc: "Insane vehicle stunts", emoji: "🎪", url: "https://www.crazygames.com/game/stunt-simulator-multiplayer", cat: "racing", age: "all", hot: false },
  { name: "MiniRoyale 2", desc: "Fast FPS battle royale", emoji: "🎯", url: "https://miniroyale.io", cat: "shooter", age: "13+", hot: true },
  { name: "Forward Assault", desc: "CS-style team shooter", emoji: "💥", url: "https://www.crazygames.com/game/forward-assault-remix", cat: "shooter", age: "13+", hot: false },
  { name: "Pixel Gun Apocalypse", desc: "Pixel multiplayer FPS", emoji: "🔫", url: "https://www.crazygames.com/game/pixel-gun-apocalypse-7", cat: "shooter", age: "13+", hot: false },
  { name: "Tanked.io", desc: "Multiplayer tank wars", emoji: "🚜", url: "https://tanked.io", cat: "shooter", age: "all", hot: false },

  // 40 MORE GAMES
  { name: "Repuls.io", desc: "Zero gravity FPS shooter", emoji: "🌙", url: "https://repuls.io", cat: "shooter", age: "13+", hot: false },
  { name: "Territorial.io", desc: "Conquer the world map", emoji: "🗺️", url: "https://territorial.io", cat: "io", age: "all", hot: true },
  { name: "Battlefields.io", desc: "Top-down squad shooter", emoji: "🪖", url: "https://battlefields.io", cat: "shooter", age: "13+", hot: false },
  { name: "Fightz.io", desc: "Brawl arena multiplayer", emoji: "🥋", url: "https://fightz.io", cat: "io", age: "13+", hot: false },
  { name: "Splix.io", desc: "Claim land, cut off enemies", emoji: "🟧", url: "https://splix.io", cat: "io", age: "all", hot: false },
  { name: "Gats.io", desc: "Top-down pixel shooter", emoji: "🔧", url: "https://gats.io", cat: "shooter", age: "13+", hot: false },
  { name: "Foes.io", desc: "Battle royale island survival", emoji: "🏝️", url: "https://foes.io", cat: "io", age: "13+", hot: false },
  { name: "Zlap.io", desc: "Flail weapon multiplayer", emoji: "🔨", url: "https://zlap.io", cat: "io", age: "all", hot: false },
  { name: "Chompers.io", desc: "Chomp and grow bigger", emoji: "😬", url: "https://chompers.io", cat: "io", age: "all", hot: false },
  { name: "Hole.io", desc: "Black hole eating city", emoji: "🕳️", url: "https://hole-io.com", cat: "io", age: "all", hot: true },
  { name: "Wings.io", desc: "Aerial dogfight battle", emoji: "✈️", url: "https://wings.io", cat: "io", age: "all", hot: false },
  { name: "Oceanar.io", desc: "Ocean creature survival", emoji: "🦈", url: "https://oceanar.io", cat: "io", age: "all", hot: false },
  { name: "Stickman Supreme Duelist", desc: "Epic stickman 1v1 fights", emoji: "🥷", url: "https://www.crazygames.com/game/stickman-supreme-duelist-2", cat: "action", age: "13+", hot: false },
  { name: "Combat Reloaded 2", desc: "CS-style online FPS", emoji: "🎖️", url: "https://www.crazygames.com/game/combat-reloaded-2", cat: "shooter", age: "13+", hot: true },
  { name: "Dead Zed", desc: "Survive zombie apocalypse", emoji: "🧟", url: "https://www.crazygames.com/game/dead-zed", cat: "shooter", age: "13+", hot: false },
  { name: "Boxhead 2Play", desc: "Co-op zombie shooter rooms", emoji: "📦", url: "https://www.crazygames.com/game/boxhead-2play-rooms", cat: "shooter", age: "13+", hot: false },
  { name: "Strike Force Heroes", desc: "Mercenary team battles", emoji: "💪", url: "https://www.crazygames.com/game/strike-force-heroes", cat: "action", age: "13+", hot: true },
  { name: "Sniper Assassin", desc: "Take out targets silently", emoji: "🎯", url: "https://www.crazygames.com/game/sniper-assassin", cat: "shooter", age: "13+", hot: false },
  { name: "Fleeing the Complex", desc: "Henry Stickmin breakout", emoji: "🏃", url: "https://www.crazygames.com/game/fleeing-the-complex", cat: "action", age: "13+", hot: true },
  { name: "Escaping the Prison", desc: "Henry Stickmin escape", emoji: "⛓️", url: "https://www.crazygames.com/game/escaping-the-prison", cat: "action", age: "all", hot: false },
  { name: "Infiltrating the Airship", desc: "Henry Stickmin heist", emoji: "🛸", url: "https://www.crazygames.com/game/infiltrating-the-airship", cat: "action", age: "all", hot: false },
  { name: "Electric Man 2", desc: "Electrified stick fighter", emoji: "⚡", url: "https://www.crazygames.com/game/electric-man-2", cat: "action", age: "13+", hot: false },
  { name: "Raze 2", desc: "Sci-fi arena shooter", emoji: "👽", url: "https://www.crazygames.com/game/raze-2", cat: "action", age: "13+", hot: false },
  { name: "Achilles 2", desc: "Epic warrior battle", emoji: "🛡️", url: "https://www.crazygames.com/game/achilles-2-origin-of-a-legend", cat: "action", age: "13+", hot: false },
  { name: "Feudalism 3", desc: "Medieval conquest RPG", emoji: "⚔️", url: "https://www.crazygames.com/game/feudalism-3", cat: "action", age: "13+", hot: false },
  { name: "Mutilate-a-Doll 2", desc: "Physics sandbox ragdoll", emoji: "🪆", url: "https://www.crazygames.com/game/mutilate-a-doll-2", cat: "action", age: "13+", hot: true },
  { name: "Earn to Die 2", desc: "Drive through zombies", emoji: "🚗", url: "https://www.crazygames.com/game/earn-to-die-2", cat: "racing", age: "13+", hot: false },
  { name: "Road of Fury 2", desc: "Mad Max highway madness", emoji: "🛣️", url: "https://www.crazygames.com/game/road-of-fury-2", cat: "racing", age: "13+", hot: false },
  { name: "Turbo Dismount", desc: "Crash test physics chaos", emoji: "💥", url: "https://www.crazygames.com/game/turbo-dismount", cat: "racing", age: "13+", hot: false },
  { name: "Shopping Cart Hero", desc: "Launch your shopping cart", emoji: "🛒", url: "https://www.crazygames.com/game/shopping-cart-hero-hd", cat: "action", age: "all", hot: false },
  { name: "Learn to Fly 3", desc: "Launch a penguin to space", emoji: "🐧", url: "https://www.crazygames.com/game/learn-to-fly-3", cat: "action", age: "all", hot: false },
  { name: "Burrito Bison Launcha Libre", desc: "Gummy bear launcher mayhem", emoji: "🌯", url: "https://www.crazygames.com/game/burrito-bison-launcha-libre", cat: "action", age: "all", hot: false },
  { name: "Potty Racers 3", desc: "Build a flying porta-potty", emoji: "🚽", url: "https://www.crazygames.com/game/potty-racers-3", cat: "racing", age: "all", hot: false },
  { name: "Cat Ninja", desc: "Sneaky ninja cat platformer", emoji: "🐱", url: "https://www.crazygames.com/game/cat-ninja", cat: "action", age: "all", hot: false },
  { name: "Bob the Robber", desc: "Stealth thief adventure", emoji: "🕵️", url: "https://www.crazygames.com/game/bob-the-robber", cat: "puzzle", age: "all", hot: false },
  { name: "Papa's Burgeria", desc: "Burger restaurant sim", emoji: "🍔", url: "https://www.crazygames.com/game/papas-burgeria", cat: "puzzle", age: "all", hot: false },
  { name: "Papa's Pancakeria", desc: "Pancake breakfast rush", emoji: "🥞", url: "https://www.crazygames.com/game/papas-pancakeria", cat: "puzzle", age: "all", hot: false },
  { name: "Kingdom Rush", desc: "Epic tower defense", emoji: "🏰", url: "https://www.crazygames.com/game/kingdom-rush", cat: "puzzle", age: "all", hot: true },
  { name: "Plants vs Zombies", desc: "Classic garden defense", emoji: "🌻", url: "https://www.crazygames.com/game/plants-vs-zombies", cat: "puzzle", age: "all", hot: true },
  { name: "Diggy", desc: "Dig deep underground", emoji: "⛏️", url: "https://www.crazygames.com/game/diggy", cat: "puzzle", age: "all", hot: false },
];

let currentFilter = 'all';

function renderGames(list) {
  const grid = document.getElementById('gameGrid');
  grid.innerHTML = '';
  list.forEach(game => {
    const card = document.createElement('div');
    card.className = 'game-card';
    card.setAttribute('data-cat', game.cat);
    card.setAttribute('data-age', game.age);
    card.onclick = () => openGame(game.url, game.name, game.emoji);
    card.innerHTML = `
      <div class="game-thumb-placeholder">${game.emoji}</div>
      <span class="game-tag ${game.age === '13+' ? 'tag-13' : game.hot ? 'tag-hot' : 'tag-all'}">${game.age === '13+' ? '13+' : game.hot ? 'HOT' : 'FREE'}</span>
      <div class="game-info">
        <div class="game-name">${game.name}</div>
        <div class="game-desc">${game.desc}</div>
      </div>
    `;
    grid.appendChild(card);
  });
}

function filterGames() {
  const query = document.getElementById('searchInput').value.toLowerCase();
  let filtered = games;
  if (currentFilter !== 'all') {
    filtered = filtered.filter(g => g.cat === currentFilter || g.age === currentFilter);
  }
  if (query) {
    filtered = filtered.filter(g => g.name.toLowerCase().includes(query) || g.desc.toLowerCase().includes(query));
  }
  renderGames(filtered);
}

function setFilter(cat, btn) {
  currentFilter = cat;
  document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
  btn.classList.add('active');
  filterGames();
}

let currentGameUrl = '';

function openGame(url, name, emoji) {
  currentGameUrl = url;
  document.getElementById('overlayTitle').textContent = name.toUpperCase();
  document.getElementById('launchEmoji').textContent = emoji;
  document.getElementById('overlay').classList.add('open');
  document.body.style.overflow = 'hidden';
}

function launchGame() {
  if (currentGameUrl) window.open(currentGameUrl, '_blank');
  closeGame();
}

function closeGame() {
  document.getElementById('overlay').classList.remove('open');
  currentGameUrl = '';
  document.body.style.overflow = '';
}

// ESC closes overlay
document.addEventListener('keydown', e => { if (e.key === 'Escape') closeGame(); });

renderGames(games);
</script>
</body>
</html>
