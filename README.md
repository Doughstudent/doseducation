<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>DOS Education - Digital Online Studies</title>
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
  body { background: var(--bg); color: var(--text); font-family: 'Rajdhani', sans-serif; min-height: 100vh; overflow-x: hidden; }
  body::before { content: ''; position: fixed; inset: 0; background: repeating-linear-gradient(0deg, transparent, transparent 2px, rgba(0,255,224,0.015) 2px, rgba(0,255,224,0.015) 4px); pointer-events: none; z-index: 9999; }
  body::after { content: ''; position: fixed; inset: 0; background-image: linear-gradient(rgba(0,255,224,0.03) 1px, transparent 1px), linear-gradient(90deg, rgba(0,255,224,0.03) 1px, transparent 1px); background-size: 40px 40px; pointer-events: none; z-index: 0; }
  header { position: sticky; top: 0; z-index: 100; background: rgba(10,10,15,0.92); backdrop-filter: blur(12px); border-bottom: 1px solid var(--border); padding: 14px 32px; display: flex; align-items: center; justify-content: space-between; }
  .logo { font-family: 'Orbitron', monospace; font-size: 1.4rem; font-weight: 900; letter-spacing: 2px; color: var(--accent); text-shadow: var(--glow); }
  .logo span { color: var(--text); }
  .tagline { font-size: 0.75rem; letter-spacing: 4px; color: var(--muted); text-transform: uppercase; margin-top: 2px; }
  .nav-right { display: flex; gap: 20px; font-size: 0.85rem; letter-spacing: 1px; color: var(--muted); align-items: center; }
  .nav-right > span { cursor: pointer; transition: color 0.2s; }
  .nav-right > span:hover { color: var(--accent); }

  /* Resources dropdown */
  .nav-resources { position: relative; }
  .nav-resources > span { cursor: pointer; transition: color 0.2s; }
  .nav-resources > span:hover, .nav-resources:hover > span { color: var(--accent); }
  .resources-dropdown { display: none; position: absolute; top: calc(100% + 14px); right: 0; background: rgba(10,10,15,0.97); border: 1px solid var(--border); border-radius: 8px; min-width: 230px; z-index: 200; box-shadow: 0 12px 40px rgba(0,0,0,0.7); overflow: hidden; animation: dropIn 0.15s ease; }
  @keyframes dropIn { from { opacity: 0; transform: translateY(-6px); } to { opacity: 1; transform: translateY(0); } }
  .nav-resources:hover .resources-dropdown { display: block; }
  .dropdown-label { font-family: 'Orbitron', monospace; font-size: 0.6rem; letter-spacing: 3px; color: var(--muted); padding: 12px 16px 8px; text-transform: uppercase; border-bottom: 1px solid var(--border); }
  .dropdown-item { display: flex; align-items: center; gap: 10px; padding: 11px 16px; color: var(--text); font-size: 0.83rem; letter-spacing: 0.5px; cursor: pointer; transition: background 0.15s, color 0.15s; text-decoration: none; border-bottom: 1px solid var(--border); }
  .dropdown-item:last-child { border-bottom: none; }
  .dropdown-item:hover { background: rgba(0,255,224,0.07); color: var(--accent); }
  .di-icon { font-size: 1rem; flex-shrink: 0; }
  .di-text { display: flex; flex-direction: column; }
  .di-name { font-weight: 600; }
  .di-sub { font-size: 0.7rem; color: var(--muted); margin-top: 1px; }

  .scroll-target { scroll-margin-top: 74px; }
  .hero { position: relative; z-index: 1; padding: 48px 32px 24px; text-align: center; }
  .hero h1 { font-family: 'Orbitron', monospace; font-size: clamp(1.5rem, 4vw, 3rem); font-weight: 900; letter-spacing: 3px; color: var(--text); margin-bottom: 10px; }
  .hero h1 em { font-style: normal; color: var(--accent); text-shadow: var(--glow); }
  .hero p { color: var(--muted); font-size: 1rem; letter-spacing: 2px; text-transform: uppercase; margin-bottom: 28px; }
  .controls { position: relative; z-index: 1; display: flex; gap: 12px; justify-content: center; flex-wrap: wrap; padding: 0 32px 28px; }
  .search-box { background: var(--card); border: 1px solid var(--border); border-radius: 4px; padding: 10px 20px; color: var(--text); font-family: 'Rajdhani', sans-serif; font-size: 1rem; letter-spacing: 1px; width: 280px; outline: none; transition: border-color 0.2s, box-shadow 0.2s; }
  .search-box:focus { border-color: var(--accent); box-shadow: var(--glow); }
  .filter-btn { background: var(--card); border: 1px solid var(--border); border-radius: 4px; padding: 10px 18px; color: var(--muted); font-family: 'Rajdhani', sans-serif; font-size: 0.9rem; letter-spacing: 1px; cursor: pointer; transition: all 0.2s; text-transform: uppercase; }
  .filter-btn:hover, .filter-btn.active { border-color: var(--accent); color: var(--accent); box-shadow: var(--glow); }
  .section { position: relative; z-index: 1; padding: 0 32px 48px; }
  .section-title { font-family: 'Orbitron', monospace; font-size: 0.85rem; letter-spacing: 4px; color: var(--muted); text-transform: uppercase; margin-bottom: 20px; padding-bottom: 10px; border-bottom: 1px solid var(--border); display: flex; align-items: center; gap: 12px; }
  .section-title::before { content: ''; display: block; width: 4px; height: 16px; background: var(--accent); box-shadow: var(--glow); }
  .game-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(200px, 1fr)); gap: 16px; }
  .game-card { background: var(--card); border: 1px solid var(--border); border-radius: 6px; overflow: hidden; cursor: pointer; transition: all 0.25s; text-decoration: none; display: block; position: relative; }
  .game-card:hover { border-color: var(--accent); transform: translateY(-4px); box-shadow: 0 8px 32px rgba(0,255,224,0.12); }
  .game-thumb-placeholder { width: 100%; height: 120px; display: flex; align-items: center; justify-content: center; font-size: 3rem; background: linear-gradient(135deg, #0d0d1a 0%, #12121e 100%); }
  .game-info { padding: 12px 14px; }
  .game-name { font-family: 'Orbitron', monospace; font-size: 0.75rem; font-weight: 700; letter-spacing: 1px; color: var(--text); margin-bottom: 4px; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
  .game-desc { font-size: 0.8rem; color: var(--muted); line-height: 1.4; }
  .game-tag { position: absolute; top: 8px; right: 8px; background: rgba(0,0,0,0.75); backdrop-filter: blur(6px); border-radius: 3px; padding: 2px 7px; font-size: 0.65rem; font-family: 'Orbitron', monospace; letter-spacing: 1px; text-transform: uppercase; }
  .tag-all { color: var(--accent); border: 1px solid #00ffe044; }
  .tag-13 { color: var(--accent2); border: 1px solid #ff3e6c44; }
  .tag-hot { color: var(--accent3); border: 1px solid #ffe10044; }
  .overlay { display: none; position: fixed; inset: 0; z-index: 9998; background: rgba(0,0,0,0.92); flex-direction: column; align-items: center; justify-content: center; backdrop-filter: blur(8px); }
  .overlay.open { display: flex; }
  .launch-box { background: var(--card); border: 1px solid var(--accent); border-radius: 10px; padding: 48px 56px; text-align: center; max-width: 420px; width: 90%; box-shadow: 0 0 60px rgba(0,255,224,0.15); animation: popIn 0.2s ease; }
  @keyframes popIn { from { transform: scale(0.9); opacity: 0; } to { transform: scale(1); opacity: 1; } }
  .launch-emoji { font-size: 4rem; margin-bottom: 16px; }
  .overlay-title { font-family: 'Orbitron', monospace; font-size: 1rem; color: var(--accent); letter-spacing: 2px; margin-bottom: 10px; }
  .launch-desc { color: var(--muted); font-size: 0.85rem; letter-spacing: 1px; margin-bottom: 28px; line-height: 1.6; }
  .btn-play { background: var(--accent); color: #000; border: none; border-radius: 5px; padding: 12px 32px; font-family: 'Orbitron', monospace; font-size: 0.85rem; font-weight: 700; letter-spacing: 2px; cursor: pointer; transition: opacity 0.2s, transform 0.15s; display: block; width: 100%; margin-bottom: 12px; }
  .btn-play:hover { opacity: 0.85; transform: scale(1.02); }
  .overlay-close { background: transparent; color: var(--muted); border: 1px solid var(--border); border-radius: 5px; padding: 10px 32px; font-family: 'Orbitron', monospace; font-size: 0.75rem; letter-spacing: 1px; cursor: pointer; transition: all 0.2s; display: block; width: 100%; }
  .overlay-close:hover { border-color: var(--accent2); color: var(--accent2); }
  .ticker { background: var(--accent); color: #000; padding: 6px 0; overflow: hidden; position: relative; z-index: 1; margin-bottom: 32px; }
  .ticker-inner { display: flex; gap: 60px; animation: ticker 30s linear infinite; white-space: nowrap; font-family: 'Orbitron', monospace; font-size: 0.7rem; font-weight: 700; letter-spacing: 2px; }
  @keyframes ticker { from { transform: translateX(0); } to { transform: translateX(-50%); } }
  @keyframes pulse { 0%, 100% { opacity: 1; transform: scale(1); } 50% { opacity: 0.4; transform: scale(0.85); } }
  .proxy-card { display: flex; gap: 16px; background: var(--card); border: 1px solid var(--border); border-radius: 8px; padding: 18px; text-decoration: none; transition: all 0.25s; align-items: flex-start; }
  .proxy-card:hover { border-color: #5865F2; transform: translateY(-3px); box-shadow: 0 8px 28px rgba(88,101,242,0.15); }
  .proxy-icon { font-size: 2rem; flex-shrink: 0; margin-top: 2px; }
  .proxy-name { font-family: 'Orbitron', monospace; font-size: 0.78rem; font-weight: 700; letter-spacing: 1px; color: var(--text); margin-bottom: 6px; }
  .proxy-desc { font-size: 0.82rem; color: var(--muted); line-height: 1.5; margin-bottom: 10px; }
  .proxy-tags { display: flex; flex-wrap: wrap; gap: 6px; }
  .ptag { background: rgba(88,101,242,0.12); border: 1px solid rgba(88,101,242,0.3); color: #9aa0f5; border-radius: 3px; padding: 2px 8px; font-size: 0.7rem; font-family: 'Orbitron', monospace; }
  .app-card { display: flex; align-items: center; gap: 14px; background: var(--card); border: 1px solid var(--border); border-radius: 8px; padding: 14px 16px; text-decoration: none; transition: all 0.22s; }
  .app-card:hover { border-color: var(--c, var(--accent)); transform: translateY(-2px); box-shadow: 0 6px 20px rgba(0,0,0,0.3); }
  .app-icon { font-size: 1.8rem; flex-shrink: 0; }
  .app-name { font-family: 'Orbitron', monospace; font-size: 0.72rem; font-weight: 700; letter-spacing: 1px; color: var(--text); margin-bottom: 3px; }
  .app-desc { font-size: 0.78rem; color: var(--muted); }
  @media(max-width: 600px) { header { padding: 12px 16px; } .section { padding: 0 16px 32px; } .controls { padding: 0 16px 20px; } .hero { padding: 32px 16px 16px; } .game-grid { grid-template-columns: repeat(auto-fill, minmax(150px, 1fr)); gap: 12px; } }
</style>
</head>
<body>

<header>
  <div>
    <div class="logo">DOS<span>education</span></div>
    <div class="tagline">Digital Online Studies — Interactive Learning Portal</div>
  </div>
  <div class="nav-right">
    <span onclick="document.getElementById('games-section').scrollIntoView({behavior:'smooth'})">Curriculum</span>

    <div class="nav-resources">
      <span>Resources &#9662;</span>
      <div class="resources-dropdown">
        <div class="dropdown-label">Jump to section</div>
        <a class="dropdown-item" onclick="goTo('resources-music')">
          <span class="di-icon">&#127925;</span>
          <span class="di-text"><span class="di-name">Music</span><span class="di-sub">Spotify, SoundCloud, YouTube Music</span></span>
        </a>
        <a class="dropdown-item" onclick="goTo('resources-chat')">
          <span class="di-icon">&#128172;</span>
          <span class="di-text"><span class="di-name">Chat</span><span class="di-sub">Discord, Telegram, Guilded</span></span>
        </a>
        <a class="dropdown-item" onclick="goTo('resources-video')">
          <span class="di-icon">&#127916;</span>
          <span class="di-text"><span class="di-name">Video &amp; Anime</span><span class="di-sub">YouTube, Crunchyroll, Twitch</span></span>
        </a>
        <a class="dropdown-item" onclick="goTo('resources-social')">
          <span class="di-icon">&#128241;</span>
          <span class="di-text"><span class="di-name">Social Media</span><span class="di-sub">Instagram, TikTok, Reddit</span></span>
        </a>
        <a class="dropdown-item" onclick="goTo('resources-tools')">
          <span class="di-icon">&#128296;</span>
          <span class="di-text"><span class="di-name">Tools &amp; Utilities</span><span class="di-sub">Canva, Figma, Notion, Replit</span></span>
        </a>
      </div>
    </div>

    <a href="https://discord.com/users/xuaoxiaolingy" target="_blank" style="text-decoration:none; display:flex; align-items:center; gap:8px; background:#5865F222; border:1px solid #5865F255; border-radius:5px; padding:7px 14px; color:#fff; font-family:'Rajdhani',sans-serif; font-size:0.85rem; letter-spacing:1px; transition:all 0.2s;" onmouseover="this.style.background='#5865F244';this.style.borderColor='#5865F2'" onmouseout="this.style.background='#5865F222';this.style.borderColor='#5865F255'">
      <svg width="18" height="18" viewBox="0 0 24 24" fill="#5865F2"><path d="M20.317 4.37a19.791 19.791 0 0 0-4.885-1.515.074.074 0 0 0-.079.037c-.21.375-.444.864-.608 1.25a18.27 18.27 0 0 0-5.487 0 12.64 12.64 0 0 0-.617-1.25.077.077 0 0 0-.079-.037A19.736 19.736 0 0 0 3.677 4.37a.07.07 0 0 0-.032.027C.533 9.046-.32 13.58.099 18.057c.002.022.015.043.032.053a19.9 19.9 0 0 0 5.993 3.03.077.077 0 0 0 .084-.028 14.09 14.09 0 0 0 1.226-1.994.076.076 0 0 0-.041-.106 13.107 13.107 0 0 1-1.872-.892.077.077 0 0 1-.008-.128 10.2 10.2 0 0 0 .372-.292.074.074 0 0 1 .077-.01c3.928 1.793 8.18 1.793 12.062 0a.074.074 0 0 1 .078.01c.12.098.246.198.373.292a.077.077 0 0 1-.006.127 12.299 12.299 0 0 1-1.873.892.077.077 0 0 0-.041.107c.36.698.772 1.362 1.225 1.993a.076.076 0 0 0 .084.028 19.839 19.839 0 0 0 6.002-3.03.077.077 0 0 0 .032-.054c.5-5.177-.838-9.674-3.549-13.66a.061.061 0 0 0-.031-.03zM8.02 15.33c-1.183 0-2.157-1.085-2.157-2.419 0-1.333.956-2.419 2.157-2.419 1.21 0 2.176 1.096 2.157 2.42 0 1.333-.956 2.418-2.157 2.418zm7.975 0c-1.183 0-2.157-1.085-2.157-2.419 0-1.333.955-2.419 2.157-2.419 1.21 0 2.176 1.096 2.157 2.42 0 1.333-.946 2.418-2.157 2.418z"/></svg>
      <span style="color:#5865F2; font-weight:600;">xuaoxiaolingy</span>
    </a>
  </div>
</header>

<div class="ticker">
  <div class="ticker-inner">
    KRUNKER.IO &nbsp;&#183;&nbsp; SHELL SHOCKERS &nbsp;&#183;&nbsp; 1V1.LOL &nbsp;&#183;&nbsp; SLITHER.IO &nbsp;&#183;&nbsp; AGAR.IO &nbsp;&#183;&nbsp; DIEP.IO &nbsp;&#183;&nbsp; PAPER.IO &nbsp;&#183;&nbsp; ZOMBS.IO &nbsp;&#183;&nbsp; MINESWEEPER &nbsp;&#183;&nbsp; 2048 &nbsp;&#183;&nbsp; TETRIS &nbsp;&#183;&nbsp; SNAKE &nbsp;&#183;&nbsp; DRIFT BOSS &nbsp;&#183;&nbsp; VENGE.IO &nbsp;&#183;&nbsp; LORDZ.IO &nbsp;&#183;&nbsp; NOW LOADING... KRUNKER.IO &nbsp;&#183;&nbsp; SHELL SHOCKERS &nbsp;&#183;&nbsp; 1V1.LOL &nbsp;&#183;&nbsp; SLITHER.IO &nbsp;&#183;&nbsp; AGAR.IO &nbsp;&#183;&nbsp; DIEP.IO &nbsp;&#183;&nbsp; PAPER.IO &nbsp;&#183;&nbsp; ZOMBS.IO &nbsp;&#183;&nbsp; MINESWEEPER &nbsp;&#183;&nbsp; 2048 &nbsp;&#183;&nbsp; TETRIS &nbsp;&#183;&nbsp; SNAKE &nbsp;&#183;&nbsp; DRIFT BOSS &nbsp;&#183;&nbsp; VENGE.IO &nbsp;&#183;&nbsp; LORDZ.IO &nbsp;&#183;&nbsp; NOW LOADING...
  </div>
</div>

<div class="hero">
  <h1>INTERACTIVE <em>STUDY</em> MODULES</h1>
  <p>Engage your brain &#8212; all platforms, all speeds</p>
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

<div class="section" id="games-section">
  <div class="section-title">&#128293; HOT RIGHT NOW</div>
  <div class="game-grid" id="gameGrid"></div>
</div>

<!-- ROBLOX -->
<div class="section" style="margin-top:8px;">
  <div class="section-title">&#127EB5; ROBLOX &#8212; PLAY ON CHROMEBOOK</div>
  <p style="color:var(--muted); font-size:0.85rem; letter-spacing:1px; margin-bottom:20px; line-height:1.7;">Roblox normally needs an app &#8212; but these cloud &amp; browser options let you play straight from Chrome with no downloads!</p>
  <a href="https://now.gg/apps/roblox-corporation/5349/roblox.html" target="_blank" style="display:flex; gap:20px; background: linear-gradient(135deg, #1a1a0f 0%, #2a2200 100%); border:2px solid #ffe10066; border-radius:10px; padding:24px; text-decoration:none; margin-bottom:20px; align-items:center; transition: all 0.25s;" onmouseover="this.style.borderColor='#ffe100';this.style.boxShadow='0 8px 32px rgba(255,225,0,0.2)'" onmouseout="this.style.borderColor='#ffe10066';this.style.boxShadow='none'">
    <div style="font-size:4rem; flex-shrink:0;">&#127918;</div>
    <div>
      <div style="font-family:'Orbitron',monospace; font-size:1rem; font-weight:900; color:#ffe100; letter-spacing:2px; margin-bottom:8px;">NOW.GG &#8212; CLOUD ROBLOX &#11088; BEST OPTION</div>
      <div style="color:#aaa; font-size:0.88rem; line-height:1.7; margin-bottom:12px;">Play Roblox <strong style="color:#fff">directly in your browser</strong> &#8212; no download, no install. Works on Chromebooks and school computers!</div>
      <div style="display:flex; gap:8px; flex-wrap:wrap;">
        <span style="background:#ffe10022; border:1px solid #ffe10055; color:#ffe100; border-radius:3px; padding:3px 10px; font-size:0.7rem; font-family:'Orbitron',monospace;">&#9989; NO DOWNLOAD</span>
        <span style="background:#ffe10022; border:1px solid #ffe10055; color:#ffe100; border-radius:3px; padding:3px 10px; font-size:0.7rem; font-family:'Orbitron',monospace;">&#9989; CHROMEBOOK</span>
        <span style="background:#ffe10022; border:1px solid #ffe10055; color:#ffe100; border-radius:3px; padding:3px 10px; font-size:0.7rem; font-family:'Orbitron',monospace;">&#9989; FREE</span>
      </div>
    </div>
  </a>
  <div style="display:grid; grid-template-columns: repeat(auto-fill, minmax(200px, 1fr)); gap:14px;">
    <a href="https://www.crazygames.com/game/build-and-crush" target="_blank" class="proxy-card" style="flex-direction:column; gap:10px;"><div style="font-size:2.2rem;">&#127959;</div><div><div class="proxy-name">Build &amp; Crush</div><div class="proxy-desc">Build structures then destroy others &#8212; pure Roblox energy in the browser.</div></div></a>
    <a href="https://www.crazygames.com/game/voxiom-io" target="_blank" class="proxy-card" style="flex-direction:column; gap:10px;"><div style="font-size:2.2rem;">&#9935;</div><div><div class="proxy-name">Voxiom.io</div><div class="proxy-desc">Minecraft + Fortnite vibes. Build, mine and battle in a voxel world.</div></div></a>
    <a href="https://www.crazygames.com/game/kogama-city" target="_blank" class="proxy-card" style="flex-direction:column; gap:10px;"><div style="font-size:2.2rem;">&#127961;</div><div><div class="proxy-name">KoGaMa City</div><div class="proxy-desc">User-made worlds you can explore &#8212; literally Roblox in the browser.</div></div></a>
    <a href="https://www.crazygames.com/game/eggy-party" target="_blank" class="proxy-card" style="flex-direction:column; gap:10px;"><div style="font-size:2.2rem;">&#129370;</div><div><div class="proxy-name">Eggy Party</div><div class="proxy-desc">Fall Guys-style party game. Multiplayer chaos!</div></div></a>
  </div>
</div>

<!-- PROXIES -->
<div class="section" style="margin-top:8px; padding-bottom:60px;">
  <div class="section-title">&#127760; WEB PROXIES &#8212; BYPASS FILTERS</div>
  <p style="color:var(--muted); font-size:0.85rem; letter-spacing:1px; margin-bottom:20px; line-height:1.7;">These proxies let you access Roblox, YouTube, and other blocked sites through your browser.</p>
  <div style="display:grid; grid-template-columns: repeat(auto-fill, minmax(260px, 1fr)); gap:16px;">
    <a href="https://titaniumnetwork.org" target="_blank" class="proxy-card"><div class="proxy-icon">&#128311;</div><div class="proxy-info"><div class="proxy-name">Titanium Network</div><div class="proxy-desc">Ultraviolet proxy &#8212; supports Roblox, YouTube and most sites.</div><div class="proxy-tags"><span class="ptag">Roblox</span><span class="ptag">YouTube</span><span class="ptag">UV Proxy</span></div></div></a>
    <a href="https://holyubofficial.net" target="_blank" class="proxy-card"><div class="proxy-icon">&#128519;</div><div class="proxy-info"><div class="proxy-name">Holy Unblocker</div><div class="proxy-desc">Popular school bypass with built-in games and proxy tabs.</div><div class="proxy-tags"><span class="ptag">Games</span><span class="ptag">Sites</span><span class="ptag">Stealth</span></div></div></a>
    <a href="https://interstellarnetwork.pages.dev" target="_blank" class="proxy-card"><div class="proxy-icon">&#128640;</div><div class="proxy-info"><div class="proxy-name">Interstellar</div><div class="proxy-desc">Fast Cloudflare-hosted proxy with Ultraviolet backend.</div><div class="proxy-tags"><span class="ptag">Fast</span><span class="ptag">Cloudflare</span><span class="ptag">Games</span></div></div></a>
    <a href="https://3kh0.github.io" target="_blank" class="proxy-card"><div class="proxy-icon">&#127918;</div><div class="proxy-info"><div class="proxy-name">3kh0 Games + Proxy</div><div class="proxy-desc">GitHub-hosted unblocked games + web proxy. Tons of games included.</div><div class="proxy-tags"><span class="ptag">GitHub</span><span class="ptag">Games</span><span class="ptag">Proxy</span></div></div></a>
    <a href="https://hypertabs.cc" target="_blank" class="proxy-card"><div class="proxy-icon">&#128209;</div><div class="proxy-info"><div class="proxy-name">HyperTabs</div><div class="proxy-desc">Disguises browsing as Google Classroom. Perfect if teachers walk by.</div><div class="proxy-tags"><span class="ptag">Stealth</span><span class="ptag">&#128293; Smart</span></div></div></a>
    <a href="https://nebulaproxy.io" target="_blank" class="proxy-card"><div class="proxy-icon">&#127756;</div><div class="proxy-info"><div class="proxy-name">Nebula Proxy</div><div class="proxy-desc">Clean dark proxy. Good for social media and games at school.</div><div class="proxy-tags"><span class="ptag">Social</span><span class="ptag">Games</span></div></div></a>
  </div>
  <div style="margin-top:24px; background:var(--card); border:1px solid var(--border); border-left:3px solid var(--accent3); border-radius:6px; padding:16px 20px;">
    <div style="font-family:'Orbitron',monospace; font-size:0.75rem; color:var(--accent3); letter-spacing:2px; margin-bottom:8px;">&#128161; PRO TIPS</div>
    <div style="color:var(--muted); font-size:0.85rem; line-height:1.8;">
      &#8226; <strong style="color:var(--text)">Cloudflare Pages (.pages.dev)</strong> and <strong style="color:var(--text)">GitHub Pages (.github.io)</strong> are hardest to block<br>
      &#8226; Use <strong style="color:var(--text)">HyperTabs</strong> if teachers walk by &#8212; it looks like Google Classroom<br>
      &#8226; For Roblox specifically, <strong style="color:var(--text)">Ultraviolet proxy</strong> (Titanium/Interstellar) works best
    </div>
  </div>
</div>

<!-- RESOURCES / APPS SECTION -->
<div class="section scroll-target" id="resources" style="margin-top:8px;">
  <div class="section-title">&#128241; UNBLOCKED APPS &amp; RESOURCES</div>
  <p style="color:var(--muted); font-size:0.85rem; letter-spacing:1px; margin-bottom:24px; line-height:1.7;">All browser-based &#8212; no downloads needed. Works on Chromebook &amp; school computers.</p>

  <div id="resources-music" class="scroll-target" style="font-family:'Orbitron',monospace; font-size:0.72rem; color:var(--muted); letter-spacing:3px; margin-bottom:12px;">&#127925; MUSIC</div>
  <div style="display:grid; grid-template-columns:repeat(auto-fill,minmax(200px,1fr)); gap:12px; margin-bottom:28px;">
    <a href="https://open.spotify.com" target="_blank" class="app-card" style="--c:#1DB954"><span class="app-icon">&#127911;</span><div><div class="app-name">Spotify Web</div><div class="app-desc">Stream any song free in browser</div></div></a>
    <a href="https://soundcloud.com" target="_blank" class="app-card" style="--c:#ff5500"><span class="app-icon">&#9729;</span><div><div class="app-name">SoundCloud</div><div class="app-desc">Free music &amp; underground tracks</div></div></a>
    <a href="https://music.youtube.com" target="_blank" class="app-card" style="--c:#ff0000"><span class="app-icon">&#9654;</span><div><div class="app-name">YouTube Music</div><div class="app-desc">Free YouTube Music web player</div></div></a>
    <a href="https://www.pandora.com" target="_blank" class="app-card" style="--c:#005483"><span class="app-icon">&#128251;</span><div><div class="app-name">Pandora</div><div class="app-desc">Free radio &amp; music stations</div></div></a>
  </div>

  <div id="resources-chat" class="scroll-target" style="font-family:'Orbitron',monospace; font-size:0.72rem; color:var(--muted); letter-spacing:3px; margin-bottom:12px;">&#128172; CHAT</div>
  <div style="display:grid; grid-template-columns:repeat(auto-fill,minmax(200px,1fr)); gap:12px; margin-bottom:28px;">
    <a href="https://discord.com/app" target="_blank" class="app-card" style="--c:#5865F2"><span class="app-icon">&#127918;</span><div><div class="app-name">Discord Web</div><div class="app-desc">Chat with friends in browser</div></div></a>
    <a href="https://web.telegram.org" target="_blank" class="app-card" style="--c:#2AABEE"><span class="app-icon">&#9992;</span><div><div class="app-name">Telegram Web</div><div class="app-desc">Instant messaging, no app needed</div></div></a>
    <a href="https://app.guilded.gg" target="_blank" class="app-card" style="--c:#F5C518"><span class="app-icon">&#128737;</span><div><div class="app-name">Guilded</div><div class="app-desc">Discord alternative &#8212; less blocked</div></div></a>
    <a href="https://groupme.com" target="_blank" class="app-card" style="--c:#00b5e2"><span class="app-icon">&#128172;</span><div><div class="app-name">GroupMe</div><div class="app-desc">Group chat for free in browser</div></div></a>
  </div>

  <div id="resources-video" class="scroll-target" style="font-family:'Orbitron',monospace; font-size:0.72rem; color:var(--muted); letter-spacing:3px; margin-bottom:12px;">&#127916; VIDEO &amp; ANIME</div>
  <div style="display:grid; grid-template-columns:repeat(auto-fill,minmax(200px,1fr)); gap:12px; margin-bottom:28px;">
    <a href="https://www.youtube.com" target="_blank" class="app-card" style="--c:#ff0000"><span class="app-icon">&#128250;</span><div><div class="app-name">YouTube</div><div class="app-desc">Watch videos free</div></div></a>
    <a href="https://www.crunchyroll.com" target="_blank" class="app-card" style="--c:#f47521"><span class="app-icon">&#127845;</span><div><div class="app-name">Crunchyroll</div><div class="app-desc">Free anime streaming (ads)</div></div></a>
    <a href="https://www4.gogoanimes.fi" target="_blank" class="app-card" style="--c:#00ffe0"><span class="app-icon">&#9961;</span><div><div class="app-name">GogoAnime</div><div class="app-desc">Free anime &#8212; huge library</div></div></a>
    <a href="https://9animetv.to" target="_blank" class="app-card" style="--c:#9b59b6"><span class="app-icon">&#127800;</span><div><div class="app-name">9AnimeTV</div><div class="app-desc">Watch anime free, no login</div></div></a>
    <a href="https://www.twitch.tv" target="_blank" class="app-card" style="--c:#9146FF"><span class="app-icon">&#128995;</span><div><div class="app-name">Twitch</div><div class="app-desc">Watch live game streams</div></div></a>
    <a href="https://animesuge.to" target="_blank" class="app-card" style="--c:#e74c3c"><span class="app-icon">&#127884;</span><div><div class="app-name">AnimeSuge</div><div class="app-desc">Dubbed &amp; subbed anime free</div></div></a>
  </div>

  <div id="resources-social" class="scroll-target" style="font-family:'Orbitron',monospace; font-size:0.72rem; color:var(--muted); letter-spacing:3px; margin-bottom:12px;">&#128241; SOCIAL MEDIA</div>
  <div style="display:grid; grid-template-columns:repeat(auto-fill,minmax(200px,1fr)); gap:12px; margin-bottom:28px;">
    <a href="https://www.instagram.com" target="_blank" class="app-card" style="--c:#e1306c"><span class="app-icon">&#128248;</span><div><div class="app-name">Instagram</div><div class="app-desc">Browse IG in browser</div></div></a>
    <a href="https://twitter.com" target="_blank" class="app-card" style="--c:#1DA1F2"><span class="app-icon">&#128038;</span><div><div class="app-name">Twitter / X</div><div class="app-desc">Browse X without the app</div></div></a>
    <a href="https://www.tiktok.com" target="_blank" class="app-card" style="--c:#ff0050"><span class="app-icon">&#127925;</span><div><div class="app-name">TikTok Web</div><div class="app-desc">Scroll TikTok in Chrome</div></div></a>
    <a href="https://www.reddit.com" target="_blank" class="app-card" style="--c:#ff4500"><span class="app-icon">&#128125;</span><div><div class="app-name">Reddit</div><div class="app-desc">Browse memes &amp; communities</div></div></a>
    <a href="https://www.pinterest.com" target="_blank" class="app-card" style="--c:#e60023"><span class="app-icon">&#128204;</span><div><div class="app-name">Pinterest</div><div class="app-desc">Browse aesthetic content</div></div></a>
    <a href="https://www.snapchat.com/web" target="_blank" class="app-card" style="--c:#FFFC00"><span class="app-icon">&#128123;</span><div><div class="app-name">Snapchat Web</div><div class="app-desc">Send snaps from browser</div></div></a>
  </div>

  <div id="resources-tools" class="scroll-target" style="font-family:'Orbitron',monospace; font-size:0.72rem; color:var(--muted); letter-spacing:3px; margin-bottom:12px;">&#128296; TOOLS &amp; UTILITIES</div>
  <div style="display:grid; grid-template-columns:repeat(auto-fill,minmax(200px,1fr)); gap:12px; margin-bottom:8px;">
    <a href="https://docs.google.com" target="_blank" class="app-card" style="--c:#4285F4"><span class="app-icon">&#128196;</span><div><div class="app-name">Google Docs</div><div class="app-desc">Free word processing online</div></div></a>
    <a href="https://www.canva.com" target="_blank" class="app-card" style="--c:#00c4cc"><span class="app-icon">&#127912;</span><div><div class="app-name">Canva</div><div class="app-desc">Design graphics &amp; posters free</div></div></a>
    <a href="https://www.figma.com" target="_blank" class="app-card" style="--c:#f24e1e"><span class="app-icon">&#9999;</span><div><div class="app-name">Figma</div><div class="app-desc">UI design tool &#8212; browser based</div></div></a>
    <a href="https://replit.com" target="_blank" class="app-card" style="--c:#f26207"><span class="app-icon">&#128187;</span><div><div class="app-name">Replit</div><div class="app-desc">Code anything in browser</div></div></a>
    <a href="https://www.photopea.com" target="_blank" class="app-card" style="--c:#1b73e8"><span class="app-icon">&#128444;</span><div><div class="app-name">Photopea</div><div class="app-desc">Free Photoshop in browser</div></div></a>
    <a href="https://www.notion.so" target="_blank" class="app-card" style="--c:#ffffff"><span class="app-icon">&#128221;</span><div><div class="app-name">Notion</div><div class="app-desc">Notes, todos &amp; planning</div></div></a>
  </div>
</div>

<!-- LIVE CHAT -->
<div class="section" style="margin-top:8px; padding-bottom:60px;">
  <div class="section-title">&#128172; LIVE CHAT &#8212; TALK TO VISITORS</div>
  <p style="color:var(--muted); font-size:0.85rem; letter-spacing:1px; margin-bottom:20px; line-height:1.7;">Chat live with everyone visiting the site right now! Messages are real &#8212; anyone on the site sees them. &#128293;</p>
  <div style="background:var(--card); border:1px solid var(--border); border-radius:10px; overflow:hidden; max-width:720px;">
    <div style="padding:12px 18px; background:var(--surface); border-bottom:1px solid var(--border); display:flex; align-items:center; justify-content:space-between;">
      <div style="display:flex; align-items:center; gap:10px;">
        <span style="display:inline-block; width:9px; height:9px; background:#00ffe0; border-radius:50%; box-shadow:0 0 8px #00ffe0; animation: pulse 1.5s infinite;"></span>
        <span style="font-family:'Orbitron',monospace; font-size:0.72rem; color:var(--accent); letter-spacing:2px;">DOSEDUCATION LIVE CHAT</span>
      </div>
      <span style="font-size:0.75rem; color:var(--muted);">powered by tlk.io</span>
    </div>
    <iframe src="https://tlk.io/doseducation?skin=dark" style="width:100%; height:500px; border:none; display:block;" allow="microphone"></iframe>
  </div>
</div>

<!-- Launch Overlay -->
<div class="overlay" id="overlay">
  <div class="launch-box">
    <div class="launch-emoji" id="launchEmoji">&#127918;</div>
    <div class="overlay-title" id="overlayTitle">GAME NAME</div>
    <div class="launch-desc">Click the button below to launch this game.<br>It will open in a new tab.</div>
    <button class="btn-play" onclick="launchGame()">&#9654; &nbsp; PLAY NOW</button>
    <button class="overlay-close" onclick="closeGame()">&#10005; &nbsp; CANCEL</button>
  </div>
</div>

<script>
function goTo(id) {
  const el = document.getElementById(id);
  if (el) el.scrollIntoView({ behavior: 'smooth' });
}

const games = [
  { name: "Krunker.io", desc: "Pixel FPS battle royale", emoji: "&#127919;", url: "https://krunker.io", cat: "shooter", age: "13+", hot: true },
  { name: "Slither.io", desc: "Grow your snake, eat others", emoji: "&#128013;", url: "https://slither.io", cat: "io", age: "all", hot: true },
  { name: "Agar.io", desc: "Classic cell munching", emoji: "&#128309;", url: "https://agar.io", cat: "io", age: "all", hot: true },
  { name: "Paper.io 2", desc: "Claim territory, defeat rivals", emoji: "&#128196;", url: "https://paper-io.com", cat: "io", age: "all", hot: true },
  { name: "Shell Shockers", desc: "Egg FPS multiplayer", emoji: "&#129370;", url: "https://shellshock.io", cat: "shooter", age: "13+", hot: true },
  { name: "1v1.lol", desc: "Build and shoot battle royale", emoji: "&#127959;", url: "https://1v1.lol", cat: "shooter", age: "13+", hot: true },
  { name: "Venge.io", desc: "3D tactical FPS", emoji: "&#128299;", url: "https://venge.io", cat: "shooter", age: "13+", hot: true },
  { name: "Diep.io", desc: "Tank upgrade shooter", emoji: "&#128640;", url: "https://diep.io", cat: "shooter", age: "all", hot: false },
  { name: "Zombs.io", desc: "Survive zombie waves", emoji: "&#129503;", url: "https://zombs.io", cat: "action", age: "13+", hot: false },
  { name: "Wormate.io", desc: "Candy snake mayhem", emoji: "&#127853;", url: "https://wormate.io", cat: "io", age: "all", hot: false },
  { name: "Hexar.io", desc: "Hex grid domination", emoji: "&#128311;", url: "https://hexar.io", cat: "io", age: "all", hot: false },
  { name: "Brutal.io", desc: "Flail weapon battle royale", emoji: "&#9939;", url: "https://brutal.io", cat: "action", age: "13+", hot: true },
  { name: "2048", desc: "Merge tiles to win", emoji: "&#128290;", url: "https://play2048.co", cat: "puzzle", age: "all", hot: false },
  { name: "Minesweeper", desc: "Classic bomb defuser", emoji: "&#128163;", url: "https://minesweeper.online", cat: "puzzle", age: "all", hot: false },
  { name: "Chess.com", desc: "Play chess online", emoji: "&#9823;", url: "https://www.chess.com/play/online", cat: "puzzle", age: "all", hot: true },
  { name: "Tetris", desc: "The classic block stacker", emoji: "&#129138;", url: "https://tetris.com/play-tetris", cat: "puzzle", age: "all", hot: false },
  { name: "Drift Boss", desc: "Drift around corners endlessly", emoji: "&#127950;", url: "https://www.crazygames.com/game/drift-boss", cat: "racing", age: "all", hot: true },
  { name: "Moto X3M", desc: "Insane bike stunts", emoji: "&#127949;", url: "https://www.crazygames.com/game/moto-x3m", cat: "racing", age: "all", hot: true },
  { name: "Slope", desc: "Speed ball on slope", emoji: "&#9917;", url: "https://slope-game.github.io", cat: "racing", age: "all", hot: true },
  { name: "Minecraft Classic", desc: "Build in the original MC", emoji: "&#9935;", url: "https://classic.minecraft.net", cat: "action", age: "all", hot: true },
  { name: "Friday Night Funkin", desc: "Rhythm battle game", emoji: "&#127925;", url: "https://www.crazygames.com/game/friday-night-funkin", cat: "action", age: "13+", hot: true },
  { name: "Among Us Online", desc: "Find the impostor", emoji: "&#128308;", url: "https://www.crazygames.com/game/among-us-online-edition", cat: "action", age: "all", hot: true },
  { name: "Smash Karts", desc: "Go-kart battle arena", emoji: "&#128168;", url: "https://smashkarts.io", cat: "action", age: "all", hot: true },
  { name: "Skribbl.io", desc: "Draw and guess with friends", emoji: "&#9999;", url: "https://skribbl.io", cat: "puzzle", age: "all", hot: true },
  { name: "Surviv.io", desc: "2D battle royale shooter", emoji: "&#129686;", url: "https://surviv.io", cat: "shooter", age: "13+", hot: true },
  { name: "Ev.io", desc: "Sci-fi FPS arena shooter", emoji: "&#128126;", url: "https://ev.io", cat: "shooter", age: "13+", hot: true },
  { name: "Narrow.one", desc: "Medieval castle archery", emoji: "&#127985;", url: "https://narrow.one", cat: "action", age: "all", hot: true },
  { name: "Getaway Shootout", desc: "Chaotic escape battles", emoji: "&#128680;", url: "https://www.crazygames.com/game/getaway-shootout", cat: "action", age: "13+", hot: true },
  { name: "Only Up Parkour", desc: "Endless upward parkour", emoji: "&#11014;", url: "https://www.crazygames.com/game/only-up-parkour", cat: "action", age: "all", hot: true },
  { name: "Cookie Clicker", desc: "Bake infinite cookies", emoji: "&#127850;", url: "https://orteil.dashnet.org/cookieclicker/", cat: "puzzle", age: "all", hot: true },
  { name: "Fireboy and Watergirl", desc: "Co-op elemental puzzles", emoji: "&#128293;", url: "https://www.crazygames.com/game/fireboy-and-watergirl-1-forest-temple", cat: "puzzle", age: "all", hot: true },
  { name: "Bloons TD", desc: "Tower defense balloon pop", emoji: "&#127880;", url: "https://www.crazygames.com/game/bloons-tower-defense-5", cat: "puzzle", age: "all", hot: true },
  { name: "Happy Wheels", desc: "Gory physics ragdoll", emoji: "&#129657;", url: "https://www.crazygames.com/game/happy-wheels", cat: "action", age: "13+", hot: true },
  { name: "Super Smash Flash 2", desc: "Fan-made Smash Bros", emoji: "&#128074;", url: "https://www.crazygames.com/game/super-smash-flash-2", cat: "action", age: "all", hot: true },
  { name: "Rocket Bot Royale", desc: "Tank battle royale", emoji: "&#128640;", url: "https://rocketbotroyale.winterpixel.io", cat: "shooter", age: "13+", hot: true },
  { name: "Kirka.io", desc: "Stylized FPS multiplayer", emoji: "&#127918;", url: "https://kirka.io", cat: "shooter", age: "13+", hot: true },
  { name: "Territorial.io", desc: "Conquer the world map", emoji: "&#128506;", url: "https://territorial.io", cat: "io", age: "all", hot: true },
  { name: "Hole.io", desc: "Black hole eating city", emoji: "&#128371;", url: "https://hole-io.com", cat: "io", age: "all", hot: true },
  { name: "Geometry Dash Lite", desc: "Rhythm platformer challenge", emoji: "&#128314;", url: "https://www.crazygames.com/game/geometry-dash-lite", cat: "action", age: "all", hot: true },
  { name: "Drift Hunters", desc: "Car drifting simulator", emoji: "&#127783;", url: "https://www.crazygames.com/game/drift-hunters", cat: "racing", age: "all", hot: true },
  { name: "MiniRoyale 2", desc: "Fast FPS battle royale", emoji: "&#127919;", url: "https://miniroyale.io", cat: "shooter", age: "13+", hot: true },
  { name: "Strike Force Heroes", desc: "Mercenary team battles", emoji: "&#128170;", url: "https://www.crazygames.com/game/strike-force-heroes", cat: "action", age: "13+", hot: true },
  { name: "Fleeing the Complex", desc: "Henry Stickmin breakout", emoji: "&#127939;", url: "https://www.crazygames.com/game/fleeing-the-complex", cat: "action", age: "13+", hot: true },
  { name: "Kingdom Rush", desc: "Epic tower defense", emoji: "&#127984;", url: "https://www.crazygames.com/game/kingdom-rush", cat: "puzzle", age: "all", hot: true },
  { name: "Plants vs Zombies", desc: "Classic garden defense", emoji: "&#127819;", url: "https://www.crazygames.com/game/plants-vs-zombies", cat: "puzzle", age: "all", hot: true },
  { name: "Mope.io", desc: "Animal food chain survival", emoji: "&#129409;", url: "https://mope.io", cat: "io", age: "all", hot: false },
  { name: "Starve.io", desc: "Craft and survive multiplayer", emoji: "&#129683;", url: "https://starve.io", cat: "action", age: "13+", hot: false },
  { name: "Defly.io", desc: "Helicopter territory war", emoji: "&#128641;", url: "https://defly.io", cat: "action", age: "all", hot: false },
  { name: "Wordle", desc: "5-letter word guessing", emoji: "&#129002;", url: "https://wordplay.com", cat: "puzzle", age: "all", hot: false },
  { name: "Run 3", desc: "Endless runner in space", emoji: "&#127939;", url: "https://www.crazygames.com/game/run-3-game", cat: "racing", age: "all", hot: false },
  { name: "Tunnel Rush", desc: "Neon speed tunnel", emoji: "&#127752;", url: "https://www.crazygames.com/game/tunnel-rush", cat: "racing", age: "all", hot: false },
  { name: "Dino Game", desc: "Chrome offline dinosaur", emoji: "&#129429;", url: "https://chromedino.com", cat: "action", age: "all", hot: false },
  { name: "Basketball Stars", desc: "1v1 basketball skills", emoji: "&#127936;", url: "https://www.crazygames.com/game/basketball-stars", cat: "action", age: "all", hot: false },
  { name: "Bonk.io", desc: "Physics ball battles", emoji: "&#127921;", url: "https://bonk.io", cat: "io", age: "all", hot: false },
  { name: "Snowball.io", desc: "Snowball fight arena", emoji: "&#10052;", url: "https://snowball.io", cat: "io", age: "all", hot: false },
  { name: "Tanki Online", desc: "Multiplayer tank battles", emoji: "&#128737;", url: "https://tankionline.com", cat: "shooter", age: "13+", hot: false },
  { name: "Splix.io", desc: "Claim land, cut off enemies", emoji: "&#127815;", url: "https://splix.io", cat: "io", age: "all", hot: false },
  { name: "Wings.io", desc: "Aerial dogfight battle", emoji: "&#9992;", url: "https://wings.io", cat: "io", age: "all", hot: false },
  { name: "Bob the Robber", desc: "Stealth thief adventure", emoji: "&#128373;", url: "https://www.crazygames.com/game/bob-the-robber", cat: "puzzle", age: "all", hot: false },
  { name: "Papa Freezeria", desc: "Ice cream shop sim", emoji: "&#127846;", url: "https://www.crazygames.com/game/papas-freezeria", cat: "puzzle", age: "all", hot: false },
  { name: "Duck Life 4", desc: "Train your racing duck", emoji: "&#129414;", url: "https://www.crazygames.com/game/duck-life-4", cat: "puzzle", age: "all", hot: false },
  { name: "Earn to Die 2", desc: "Drive through zombies", emoji: "&#128663;", url: "https://www.crazygames.com/game/earn-to-die-2", cat: "racing", age: "13+", hot: false },
  { name: "Mutilate-a-Doll 2", desc: "Physics sandbox ragdoll", emoji: "&#129414;", url: "https://www.crazygames.com/game/mutilate-a-doll-2", cat: "action", age: "13+", hot: false },
  { name: "Age of War", desc: "Evolving strategy war", emoji: "&#9876;", url: "https://www.crazygames.com/game/age-of-war", cat: "action", age: "13+", hot: false },
  { name: "Fancy Pants", desc: "Smooth stickman platformer", emoji: "&#128310;", url: "https://www.crazygames.com/game/fancy-pants-adventures", cat: "action", age: "all", hot: false },
  { name: "Temple Run 2", desc: "Endless jungle escape run", emoji: "&#127939;", url: "https://www.crazygames.com/game/temple-run-2", cat: "racing", age: "all", hot: false },
];

let currentFilter = 'all';

function renderGames(list) {
  const grid = document.getElementById('gameGrid');
  grid.innerHTML = '';
  list.forEach(game => {
    const card = document.createElement('div');
    card.className = 'game-card';
    card.onclick = () => openGame(game.url, game.name, game.emoji);
    card.innerHTML = '<div class="game-thumb-placeholder">' + game.emoji + '</div>' +
      '<span class="game-tag ' + (game.age === '13+' ? 'tag-13' : game.hot ? 'tag-hot' : 'tag-all') + '">' + (game.age === '13+' ? '13+' : game.hot ? 'HOT' : 'FREE') + '</span>' +
      '<div class="game-info"><div class="game-name">' + game.name + '</div><div class="game-desc">' + game.desc + '</div></div>';
    grid.appendChild(card);
  });
}

function filterGames() {
  const query = document.getElementById('searchInput').value.toLowerCase();
  let filtered = games;
  if (currentFilter !== 'all') filtered = filtered.filter(g => g.cat === currentFilter || g.age === currentFilter);
  if (query) filtered = filtered.filter(g => g.name.toLowerCase().includes(query) || g.desc.toLowerCase().includes(query));
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
  document.getElementById('launchEmoji').innerHTML = emoji;
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

document.addEventListener('keydown', e => { if (e.key === 'Escape') closeGame(); });
renderGames(games);

// ===================== DOUGH CURSOR =====================
(function() {
  const style = document.createElement('style');
  style.textContent = `
    * { cursor: none !important; }
    #dough-cursor {
      position: fixed;
      pointer-events: none;
      z-index: 999999;
      width: 64px;
      height: 64px;
      transform: translate(-50%, -50%);
      transition: transform 0.08s ease;
      user-select: none;
    }
    #dough-cursor.clicking {
      transform: translate(-50%, -50%) scale(0.8) rotate(-12deg) translateX(-6px);
      animation: flinch 0.25s ease;
    }
    @keyframes flinch {
      0%   { transform: translate(-50%, -50%) scale(1) rotate(0deg); }
      30%  { transform: translate(calc(-50% - 8px), calc(-50% - 6px)) scale(0.78) rotate(-15deg); }
      60%  { transform: translate(calc(-50% + 4px), calc(-50% - 2px)) scale(0.82) rotate(8deg); }
      100% { transform: translate(-50%, -50%) scale(0.8) rotate(-10deg); }
    }
  `;
  document.head.appendChild(style);

  const HAPPY_SVG = `<svg width="64" height="64" viewBox="0 0 64 64" xmlns="http://www.w3.org/2000/svg">
    <!-- Shadow -->
    <ellipse cx="32" cy="61" rx="22" ry="3" fill="rgba(0,0,0,0.10)"/>
    <!-- Outer stroke / sticker border -->
    <circle cx="32" cy="31" r="27" fill="white" stroke="white" stroke-width="4"/>
    <!-- Main body - golden biscuit -->
    <circle cx="32" cy="31" r="25" fill="#f0c060"/>
    <!-- Texture bumps -->
    <circle cx="20" cy="20" r="3.5" fill="#e8b84a" opacity="0.6"/>
    <circle cx="42" cy="18" r="2.8" fill="#e8b84a" opacity="0.6"/>
    <circle cx="14" cy="35" r="2.5" fill="#e8b84a" opacity="0.5"/>
    <circle cx="48" cy="38" r="3" fill="#e8b84a" opacity="0.5"/>
    <circle cx="35" cy="48" r="2.2" fill="#e8b84a" opacity="0.5"/>
    <circle cx="22" cy="46" r="2" fill="#e8b84a" opacity="0.4"/>
    <circle cx="44" cy="26" r="1.8" fill="#e8b84a" opacity="0.4"/>
    <!-- Highlight top -->
    <ellipse cx="26" cy="16" rx="9" ry="5" fill="white" opacity="0.35" transform="rotate(-20,26,16)"/>
    <!-- Dark outline ring -->
    <circle cx="32" cy="31" r="25" fill="none" stroke="#5a3010" stroke-width="2.5"/>
    <!-- Left eye -->
    <circle cx="22" cy="29" r="4.5" fill="#1a1a1a"/>
    <circle cx="23.5" cy="27.5" r="1.5" fill="white" opacity="0.9"/>
    <!-- Right eye -->
    <circle cx="42" cy="29" r="4.5" fill="#1a1a1a"/>
    <circle cx="43.5" cy="27.5" r="1.5" fill="white" opacity="0.9"/>
    <!-- Blush left -->
    <ellipse cx="16" cy="36" rx="5.5" ry="3.5" fill="#f08080" opacity="0.65"/>
    <!-- Blush right -->
    <ellipse cx="48" cy="36" rx="5.5" ry="3.5" fill="#f08080" opacity="0.65"/>
    <!-- Happy open mouth -->
    <path d="M23 38 Q32 46 41 38" stroke="#5a3010" stroke-width="2" fill="#c85050" stroke-linecap="round"/>
    <path d="M23 38 Q32 46 41 38" fill="#c85050"/>
    <!-- Teeth -->
    <path d="M26 38 Q32 42 38 38" fill="white" stroke="none"/>
  </svg>`;

  const SAD_SVG = `<svg width="64" height="64" viewBox="0 0 64 64" xmlns="http://www.w3.org/2000/svg">
    <!-- Shadow -->
    <ellipse cx="32" cy="61" rx="22" ry="3" fill="rgba(0,0,0,0.10)"/>
    <!-- Outer stroke / sticker border -->
    <circle cx="32" cy="31" r="27" fill="white" stroke="white" stroke-width="4"/>
    <!-- Main body -->
    <circle cx="32" cy="31" r="25" fill="#e8b84a"/>
    <!-- Texture bumps (slightly darker when sad) -->
    <circle cx="20" cy="20" r="3.5" fill="#d4a030" opacity="0.6"/>
    <circle cx="42" cy="18" r="2.8" fill="#d4a030" opacity="0.6"/>
    <circle cx="14" cy="35" r="2.5" fill="#d4a030" opacity="0.5"/>
    <circle cx="48" cy="38" r="3" fill="#d4a030" opacity="0.5"/>
    <circle cx="35" cy="48" r="2.2" fill="#d4a030" opacity="0.5"/>
    <!-- Highlight top -->
    <ellipse cx="26" cy="16" rx="9" ry="5" fill="white" opacity="0.25" transform="rotate(-20,26,16)"/>
    <!-- Dark outline ring -->
    <circle cx="32" cy="31" r="25" fill="none" stroke="#5a3010" stroke-width="2.5"/>
    <!-- Left eye - scared/squinting X -->
    <line x1="19" y1="26" x2="25" y2="32" stroke="#1a1a1a" stroke-width="2.5" stroke-linecap="round"/>
    <line x1="25" y1="26" x2="19" y2="32" stroke="#1a1a1a" stroke-width="2.5" stroke-linecap="round"/>
    <!-- Right eye - scared/squinting X -->
    <line x1="39" y1="26" x2="45" y2="32" stroke="#1a1a1a" stroke-width="2.5" stroke-linecap="round"/>
    <line x1="45" y1="26" x2="39" y2="32" stroke="#1a1a1a" stroke-width="2.5" stroke-linecap="round"/>
    <!-- Blush left (bigger when scared) -->
    <ellipse cx="16" cy="36" rx="6" ry="4" fill="#f08080" opacity="0.75"/>
    <!-- Blush right -->
    <ellipse cx="48" cy="36" rx="6" ry="4" fill="#f08080" opacity="0.75"/>
    <!-- Frown mouth -->
    <path d="M23 44 Q32 37 41 44" stroke="#5a3010" stroke-width="2.2" fill="none" stroke-linecap="round"/>
    <!-- Sweat drop -->
    <ellipse cx="50" cy="20" rx="3" ry="4.5" fill="#7ac8f0" opacity="0.9"/>
    <ellipse cx="50" cy="16" rx="2" ry="2" fill="#7ac8f0" opacity="0.9"/>
  </svg>`;

  const cursor = document.createElement('div');
  cursor.id = 'dough-cursor';
  cursor.innerHTML = HAPPY_SVG;
  document.body.appendChild(cursor);

  // Particle pool
  const particles = [];
  const PARTICLE_COUNT = 20;
  const EMOJIS = ['✨','💫','⭐','🌟','·','˚'];

  class Particle {
    constructor() {
      this.el = document.createElement('div');
      this.el.style.cssText = 'position:fixed;pointer-events:none;z-index:999998;user-select:none;opacity:0;';
      document.body.appendChild(this.el);
      this.active = false;
    }
    spawn(x, y) {
      this.x = x; this.y = y;
      this.vx = (Math.random() - 0.5) * 4;
      this.vy = (Math.random() - 0.5) * 4 - 1.5;
      this.life = 1;
      this.decay = 0.04 + Math.random() * 0.04;
      this.size = 10 + Math.random() * 10;
      this.el.textContent = EMOJIS[Math.floor(Math.random() * EMOJIS.length)];
      this.el.style.fontSize = this.size + 'px';
      this.active = true;
    }
    update() {
      if (!this.active) return;
      this.life -= this.decay;
      if (this.life <= 0) { this.active = false; this.el.style.opacity = 0; return; }
      this.x += this.vx; this.y += this.vy; this.vy += 0.1;
      this.el.style.opacity = this.life;
      this.el.style.left = (this.x - this.size/2) + 'px';
      this.el.style.top = (this.y - this.size/2) + 'px';
    }
  }

  for (let i = 0; i < PARTICLE_COUNT; i++) particles.push(new Particle());

  let mouseX = -200, mouseY = -200, lastSpawn = 0;

  document.addEventListener('mousemove', e => {
    mouseX = e.clientX; mouseY = e.clientY;
    cursor.style.left = mouseX + 'px';
    cursor.style.top = mouseY + 'px';
    const now = Date.now();
    if (now - lastSpawn > 40) {
      lastSpawn = now;
      const p = particles.find(p => !p.active);
      if (p) p.spawn(mouseX, mouseY);
    }
  });

  document.addEventListener('mousedown', () => {
    cursor.innerHTML = SAD_SVG;
    cursor.classList.add('clicking');
  });

  document.addEventListener('mouseup', () => {
    cursor.innerHTML = HAPPY_SVG;
    cursor.classList.remove('clicking');
    for (let i = 0; i < 7; i++) {
      const p = particles.find(p => !p.active);
      if (p) p.spawn(mouseX, mouseY);
    }
  });

  function animate() {
    particles.forEach(p => p.update());
    requestAnimationFrame(animate);
  }
  animate();
})();
</script>
</body>
</html>
