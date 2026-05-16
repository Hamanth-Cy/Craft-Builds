<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CraftBuilds – Minecraft Building Hub</title>
<link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&family=VT323:wght@400&family=Nunito:wght@400;600;700&display=swap" rel="stylesheet">
<style>
  :root {
    --grass: #5D9E3A;
    --dirt: #8B5E3C;
    --stone: #888;
    --diamond: #4FE0D0;
    --gold: #FFC54E;
    --wood: #A0722A;
    --sky: #87CEEB;
    --night: #0D1B2A;
    --sand: #E2C97E;
    --lava: #FF6400;
    --pixel: 4px;
    --bg: #0D1B2A;
    --card-bg: #1A2E40;
    --card-border: #2A4560;
    --text: #E8F4E8;
    --muted: #8FB3A0;
  }
 
  * { box-sizing: border-box; margin: 0; padding: 0; }
 
  body {
    font-family: 'Nunito', sans-serif;
    background: var(--bg);
    color: var(--text);
    min-height: 100vh;
    overflow-x: hidden;
  }
 
  /* Pixelated cursor */
  body { cursor: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='20' height='20'%3E%3Crect x='0' y='0' width='8' height='8' fill='%235D9E3A'/%3E%3Crect x='8' y='0' width='8' height='8' fill='%238B5E3C'/%3E%3Crect x='0' y='8' width='8' height='8' fill='%238B5E3C'/%3E%3Crect x='8' y='8' width='8' height='8' fill='%235D9E3A'/%3E%3C/svg%3E") 10 10, crosshair; }
 
  /* ===== NAV ===== */
  nav {
    background: #0a1520;
    border-bottom: 4px solid var(--grass);
    padding: 0 2rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 64px;
    position: sticky;
    top: 0;
    z-index: 100;
  }
 
  .logo {
    font-family: 'Press Start 2P', monospace;
    font-size: 14px;
    color: var(--grass);
    letter-spacing: 1px;
    text-shadow: 3px 3px 0 #2a5c1a;
  }
 
  .logo span { color: var(--diamond); }
 
  nav ul {
    list-style: none;
    display: flex;
    gap: 2rem;
  }
 
  nav ul a {
    color: var(--muted);
    text-decoration: none;
    font-size: 14px;
    font-weight: 600;
    transition: color 0.2s;
    letter-spacing: 1px;
  }
 
  nav ul a:hover { color: var(--grass); }
 
  .nav-btn {
    background: var(--grass);
    color: #fff;
    padding: 8px 18px;
    font-family: 'Press Start 2P', monospace;
    font-size: 9px;
    border: none;
    cursor: pointer;
    image-rendering: pixelated;
    box-shadow: 3px 3px 0 #2a5c1a;
    transition: transform 0.1s, box-shadow 0.1s;
  }
 
  .nav-btn:hover { transform: translate(-1px,-1px); box-shadow: 4px 4px 0 #2a5c1a; }
  .nav-btn:active { transform: translate(2px,2px); box-shadow: 1px 1px 0 #2a5c1a; }
 
  /* ===== HERO ===== */
  .hero {
    position: relative;
    min-height: 520px;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    text-align: center;
    padding: 4rem 2rem 3rem;
    overflow: hidden;
  }
 
  .hero-bg {
    position: absolute;
    inset: 0;
    background:
      linear-gradient(to bottom, #1a2e3a 0%, #0D1B2A 70%);
  }
 
  /* Pixel star field */
  .stars {
    position: absolute;
    inset: 0;
    background-image:
      radial-gradient(1px 1px at 10% 20%, #fff 100%, transparent),
      radial-gradient(1px 1px at 30% 10%, #cce 100%, transparent),
      radial-gradient(1px 1px at 60% 30%, #fff 100%, transparent),
      radial-gradient(1px 1px at 80% 15%, #eef 100%, transparent),
      radial-gradient(1px 1px at 50% 5%, #fff 100%, transparent),
      radial-gradient(1px 1px at 25% 40%, #fff 100%, transparent),
      radial-gradient(1px 1px at 90% 25%, #cce 100%, transparent),
      radial-gradient(1px 1px at 70% 50%, #fff 100%, transparent),
      radial-gradient(1px 1px at 15% 55%, #eef 100%, transparent),
      radial-gradient(1px 1px at 45% 35%, #fff 100%, transparent);
    opacity: 0.7;
  }
 
  /* Pixel terrain silhouette at hero bottom */
  .terrain {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 80px;
    background: var(--grass);
    clip-path: polygon(
      0% 60%, 3% 60%, 3% 40%, 6% 40%, 6% 20%, 9% 20%, 9% 40%, 12% 40%,
      12% 50%, 15% 50%, 15% 30%, 18% 30%, 18% 50%, 21% 50%, 21% 40%,
      24% 40%, 24% 60%, 27% 60%, 27% 45%, 30% 45%, 30% 25%, 33% 25%,
      33% 45%, 36% 45%, 36% 60%, 39% 60%, 39% 35%, 42% 35%, 42% 15%,
      45% 15%, 45% 35%, 48% 35%, 48% 55%, 51% 55%, 51% 40%, 54% 40%,
      54% 60%, 57% 60%, 57% 45%, 60% 45%, 60% 30%, 63% 30%, 63% 50%,
      66% 50%, 66% 40%, 69% 40%, 69% 60%, 72% 60%, 72% 50%, 75% 50%,
      75% 35%, 78% 35%, 78% 55%, 81% 55%, 81% 40%, 84% 40%, 84% 60%,
      87% 60%, 87% 45%, 90% 45%, 90% 25%, 93% 25%, 93% 45%, 96% 45%,
      96% 60%, 100% 60%, 100% 100%, 0% 100%
    );
  }
 
  .terrain::after {
    content: '';
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 30px;
    background: var(--dirt);
  }
 
  .hero-content { position: relative; z-index: 2; max-width: 760px; }
 
  .hero-tag {
    display: inline-block;
    background: var(--diamond);
    color: #0a2a2a;
    font-family: 'Press Start 2P', monospace;
    font-size: 8px;
    padding: 6px 14px;
    margin-bottom: 1.5rem;
    letter-spacing: 1px;
  }
 
  .hero h1 {
    font-family: 'Press Start 2P', monospace;
    font-size: clamp(22px, 4vw, 38px);
    line-height: 1.5;
    color: #fff;
    text-shadow: 4px 4px 0 #000, -1px -1px 0 rgba(93,158,58,0.3);
    margin-bottom: 1.5rem;
  }
 
  .hero h1 em {
    color: var(--grass);
    font-style: normal;
  }
 
  .hero p {
    font-size: 18px;
    color: var(--muted);
    max-width: 520px;
    margin: 0 auto 2.5rem;
    line-height: 1.7;
  }
 
  .hero-btns { display: flex; gap: 1rem; justify-content: center; flex-wrap: wrap; }
 
  .btn-primary {
    background: var(--grass);
    color: #fff;
    padding: 14px 28px;
    font-family: 'Press Start 2P', monospace;
    font-size: 11px;
    border: none;
    cursor: pointer;
    box-shadow: 4px 4px 0 #2a5c1a;
    transition: transform 0.1s, box-shadow 0.1s;
    text-decoration: none;
    display: inline-block;
  }
 
  .btn-primary:hover { transform: translate(-2px,-2px); box-shadow: 6px 6px 0 #2a5c1a; }
 
  .btn-secondary {
    background: transparent;
    color: var(--diamond);
    padding: 14px 28px;
    font-family: 'Press Start 2P', monospace;
    font-size: 11px;
    border: 3px solid var(--diamond);
    cursor: pointer;
    box-shadow: 4px 4px 0 #1a5a5a;
    transition: transform 0.1s;
    text-decoration: none;
    display: inline-block;
  }
 
  .btn-secondary:hover { transform: translate(-2px,-2px); }
 
  /* ===== STATS BAR ===== */
  .stats-bar {
    background: #111d2c;
    border-top: 3px solid var(--card-border);
    border-bottom: 3px solid var(--card-border);
    padding: 1.5rem 2rem;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
    gap: 1rem;
  }
 
  .stat {
    text-align: center;
  }
 
  .stat-num {
    font-family: 'Press Start 2P', monospace;
    font-size: 20px;
    color: var(--gold);
    display: block;
    margin-bottom: 6px;
  }
 
  .stat-label {
    font-size: 12px;
    color: var(--muted);
    letter-spacing: 1px;
    text-transform: uppercase;
  }
 
  /* ===== SECTIONS ===== */
  section { padding: 5rem 2rem; max-width: 1200px; margin: 0 auto; }
 
  .section-head {
    text-align: center;
    margin-bottom: 3rem;
  }
 
  .section-head h2 {
    font-family: 'Press Start 2P', monospace;
    font-size: clamp(16px, 3vw, 24px);
    color: #fff;
    margin-bottom: 1rem;
    text-shadow: 3px 3px 0 #000;
  }
 
  .section-head p {
    color: var(--muted);
    font-size: 16px;
    max-width: 500px;
    margin: 0 auto;
  }
 
  .pixel-divider {
    width: 80px;
    height: 6px;
    background: repeating-linear-gradient(90deg, var(--grass) 0, var(--grass) 12px, var(--diamond) 12px, var(--diamond) 24px);
    margin: 1rem auto 0;
  }
 
  /* ===== CATEGORY CHIPS ===== */
  .category-filter {
    display: flex;
    gap: 10px;
    justify-content: center;
    flex-wrap: wrap;
    margin-bottom: 3rem;
  }
 
  .chip {
    background: var(--card-bg);
    border: 2px solid var(--card-border);
    color: var(--muted);
    padding: 8px 18px;
    font-size: 13px;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.15s;
    letter-spacing: 0.5px;
  }
 
  .chip:hover, .chip.active {
    background: var(--grass);
    border-color: var(--grass);
    color: #fff;
  }
 
  /* ===== BUILD CARDS ===== */
  .builds-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 1.5rem;
  }
 
  .build-card {
    background: var(--card-bg);
    border: 2px solid var(--card-border);
    overflow: hidden;
    transition: transform 0.2s, border-color 0.2s;
    cursor: pointer;
  }
 
  .build-card:hover {
    transform: translateY(-4px);
    border-color: var(--grass);
  }
 
  .card-img {
    height: 180px;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    overflow: hidden;
  }
 
  /* Pixel art block scenes */
  .scene-castle { background: #1a2e1a; }
  .scene-modern { background: #1a1a2e; }
  .scene-village { background: #2e1a0a; }
  .scene-farm { background: #0a2e0a; }
  .scene-underwater { background: #0a1a2e; }
  .scene-nether { background: #2e0a0a; }
 
  .pixel-scene {
    width: 100%;
    height: 100%;
    display: block;
  }
 
  .card-body { padding: 1.25rem; }
 
  .card-meta {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 0.75rem;
  }
 
  .difficulty {
    font-family: 'Press Start 2P', monospace;
    font-size: 7px;
    padding: 4px 8px;
  }
 
  .diff-easy { background: #1a3a1a; color: var(--grass); border: 1px solid var(--grass); }
  .diff-medium { background: #3a2a0a; color: var(--gold); border: 1px solid var(--gold); }
  .diff-hard { background: #3a0a0a; color: var(--lava); border: 1px solid var(--lava); }
 
  .hearts {
    display: flex;
    gap: 3px;
    font-size: 12px;
  }
 
  .card-title {
    font-family: 'Press Start 2P', monospace;
    font-size: 11px;
    color: #fff;
    margin-bottom: 0.5rem;
    line-height: 1.6;
  }
 
  .card-desc {
    font-size: 13px;
    color: var(--muted);
    line-height: 1.6;
    margin-bottom: 1rem;
  }
 
  .card-footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-top: 1px solid var(--card-border);
    padding-top: 0.75rem;
  }
 
  .card-author {
    font-size: 12px;
    color: var(--muted);
  }
 
  .card-author strong { color: var(--diamond); }
 
  .card-views {
    font-size: 12px;
    color: var(--muted);
  }
 
  /* ===== TUTORIAL SECTION ===== */
  .tutorials-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(340px, 1fr));
    gap: 1.5rem;
  }
 
  .tutorial-card {
    background: var(--card-bg);
    border: 2px solid var(--card-border);
    display: flex;
    gap: 1.25rem;
    padding: 1.25rem;
    transition: border-color 0.2s;
    cursor: pointer;
  }
 
  .tutorial-card:hover { border-color: var(--diamond); }
 
  .tut-icon {
    width: 56px;
    height: 56px;
    min-width: 56px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 28px;
    background: #111d2c;
    border: 2px solid var(--card-border);
  }
 
  .tut-body h3 {
    font-family: 'Press Start 2P', monospace;
    font-size: 10px;
    color: #fff;
    margin-bottom: 6px;
    line-height: 1.6;
  }
 
  .tut-body p {
    font-size: 13px;
    color: var(--muted);
    line-height: 1.5;
    margin-bottom: 10px;
  }
 
  .tut-tag {
    font-size: 11px;
    background: #111d2c;
    color: var(--diamond);
    padding: 3px 10px;
    border: 1px solid #1a4a4a;
    display: inline-block;
  }
 
  /* ===== MATERIALS TABLE ===== */
  .material-section {
    background: #111d2c;
    border-top: 3px solid var(--card-border);
    border-bottom: 3px solid var(--card-border);
    padding: 4rem 2rem;
  }
 
  .material-inner { max-width: 1100px; margin: 0 auto; }
 
  .blocks-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(90px, 1fr));
    gap: 1rem;
    margin-top: 2rem;
  }
 
  .block-item {
    text-align: center;
    cursor: pointer;
    transition: transform 0.2s;
  }
 
  .block-item:hover { transform: scale(1.1); }
 
  .block-face {
    width: 64px;
    height: 64px;
    margin: 0 auto 8px;
    image-rendering: pixelated;
    border: 3px solid rgba(255,255,255,0.15);
    position: relative;
  }
 
  .block-name {
    font-size: 11px;
    color: var(--muted);
    font-family: 'VT323', monospace;
    font-size: 14px;
    letter-spacing: 0.5px;
  }
 
  /* ===== NEWSLETTER ===== */
  .newsletter {
    background: linear-gradient(135deg, #0a2e1a 0%, #0a1a2e 100%);
    border: 3px solid var(--grass);
    padding: 3rem 2rem;
    text-align: center;
    margin: 0 auto;
    max-width: 600px;
    position: relative;
    overflow: hidden;
  }
 
  .newsletter::before, .newsletter::after {
    content: '⛏️';
    position: absolute;
    font-size: 60px;
    opacity: 0.07;
  }
  .newsletter::before { left: -10px; top: -10px; }
  .newsletter::after { right: -10px; bottom: -10px; transform: rotate(180deg); }
 
  .newsletter h2 {
    font-family: 'Press Start 2P', monospace;
    font-size: 16px;
    color: #fff;
    margin-bottom: 1rem;
    line-height: 1.6;
  }
 
  .newsletter p { color: var(--muted); margin-bottom: 1.5rem; font-size: 15px; }
 
  .email-row {
    display: flex;
    gap: 0;
    max-width: 420px;
    margin: 0 auto;
  }
 
  .email-row input {
    flex: 1;
    background: #0a1520;
    border: 2px solid var(--card-border);
    border-right: none;
    color: var(--text);
    padding: 12px 16px;
    font-family: 'Nunito', sans-serif;
    font-size: 14px;
    outline: none;
  }
 
  .email-row input::placeholder { color: var(--muted); }
  .email-row input:focus { border-color: var(--grass); }
 
  .email-row button {
    background: var(--grass);
    color: #fff;
    border: none;
    padding: 12px 20px;
    font-family: 'Press Start 2P', monospace;
    font-size: 9px;
    cursor: pointer;
    white-space: nowrap;
    box-shadow: 3px 3px 0 #2a5c1a;
  }
 
  /* ===== FOOTER ===== */
  footer {
    background: #0a1520;
    border-top: 4px solid var(--dirt);
    padding: 3rem 2rem 1.5rem;
  }
 
  .footer-grid {
    display: grid;
    grid-template-columns: 2fr 1fr 1fr 1fr;
    gap: 2rem;
    max-width: 1100px;
    margin: 0 auto 2rem;
  }
 
  @media (max-width: 768px) {
    .footer-grid { grid-template-columns: 1fr 1fr; }
    nav ul { display: none; }
    .hero h1 { font-size: 18px; }
  }
 
  .footer-brand .logo { display: block; margin-bottom: 1rem; font-size: 12px; }
 
  .footer-brand p { font-size: 13px; color: var(--muted); line-height: 1.6; }
 
  .footer-col h4 {
    font-family: 'Press Start 2P', monospace;
    font-size: 9px;
    color: var(--grass);
    margin-bottom: 1rem;
    letter-spacing: 1px;
  }
 
  .footer-col ul { list-style: none; }
 
  .footer-col li { margin-bottom: 8px; }
 
  .footer-col a {
    color: var(--muted);
    text-decoration: none;
    font-size: 14px;
    transition: color 0.2s;
  }
 
  .footer-col a:hover { color: var(--diamond); }
 
  .footer-bottom {
    text-align: center;
    border-top: 1px solid var(--card-border);
    padding-top: 1.5rem;
    font-size: 12px;
    color: var(--muted);
    max-width: 1100px;
    margin: 0 auto;
  }
 
  /* ===== SCROLL ANIMATION ===== */
  .fade-in {
    opacity: 0;
    transform: translateY(20px);
    transition: opacity 0.6s, transform 0.6s;
  }
 
  .fade-in.visible {
    opacity: 1;
    transform: translateY(0);
  }
 
  /* Search bar */
  .search-bar {
    display: flex;
    gap: 0;
    max-width: 420px;
    margin: 0 auto 3rem;
  }
 
  .search-bar input {
    flex: 1;
    background: var(--card-bg);
    border: 2px solid var(--card-border);
    border-right: none;
    color: var(--text);
    padding: 12px 16px;
    font-family: 'Nunito', sans-serif;
    font-size: 14px;
    outline: none;
  }
 
  .search-bar input:focus { border-color: var(--grass); }
 
  .search-bar button {
    background: var(--grass);
    color: #fff;
    border: none;
    padding: 12px 18px;
    font-family: 'Press Start 2P', monospace;
    font-size: 9px;
    cursor: pointer;
    box-shadow: 2px 2px 0 #2a5c1a;
  }
 
  /* Toast notification */
  .toast {
    position: fixed;
    bottom: 2rem;
    right: 2rem;
    background: var(--grass);
    color: #fff;
    padding: 12px 20px;
    font-family: 'Press Start 2P', monospace;
    font-size: 9px;
    box-shadow: 4px 4px 0 #2a5c1a;
    z-index: 999;
    transform: translateX(200%);
    transition: transform 0.3s;
    line-height: 1.8;
  }
 
  .toast.show { transform: translateX(0); }
</style>
</head>
<body>
 
<!-- NAV -->
<nav>
  <div class="logo">Craft<span>Builds</span></div>
  <ul>
    <li><a href="#builds">Builds</a></li>
    <li><a href="#tutorials">Tutorials</a></li>
    <li><a href="#materials">Materials</a></li>
    <li><a href="#community">Community</a></li>
  </ul>
  <button class="nav-btn" onclick="showToast('Coming Soon! 🎮')">Join Discord</button>
</nav>
 
<!-- HERO -->
<div class="hero">
  <div class="hero-bg"></div>
  <div class="stars"></div>
  <div class="hero-content">
    <div class="hero-tag">⛏️ #1 Minecraft Building Resource</div>
    <h1>Build Your <em>Dream</em><br>World, Block by Block</h1>
    <p>Discover epic builds, step-by-step tutorials, and tips from the best Minecraft architects in the world.</p>
    <div class="hero-btns">
      <a href="#builds" class="btn-primary">Browse Builds →</a>
      <a href="#tutorials" class="btn-secondary">Watch Tutorials</a>
    </div>
  </div>
  <div class="terrain"></div>
</div>
 
<!-- STATS BAR -->
<div class="stats-bar">
  <div class="stat">
    <span class="stat-num">12,490</span>
    <span class="stat-label">Total Builds</span>
  </div>
  <div class="stat">
    <span class="stat-num">3,200+</span>
    <span class="stat-label">Tutorials</span>
  </div>
  <div class="stat">
    <span class="stat-num">840K</span>
    <span class="stat-label">Community Members</span>
  </div>
  <div class="stat">
    <span class="stat-num">500+</span>
    <span class="stat-label">Schematics</span>
  </div>
</div>
 
<!-- BUILDS SECTION -->
<section id="builds">
  <div class="section-head fade-in">
    <h2>⚒ Featured Builds</h2>
    <p>Hand-picked by our community — from beginner starter homes to massive mega-projects.</p>
    <div class="pixel-divider"></div>
  </div>
 
  <div class="search-bar fade-in">
    <input type="text" placeholder="Search builds, biomes, styles..." id="searchInput" />
    <button onclick="handleSearch()">Search</button>
  </div>
 
  <div class="category-filter fade-in">
    <div class="chip active" onclick="filterBuilds(this,'all')">All Builds</div>
    <div class="chip" onclick="filterBuilds(this,'medieval')">⚔️ Medieval</div>
    <div class="chip" onclick="filterBuilds(this,'modern')">🏙️ Modern</div>
    <div class="chip" onclick="filterBuilds(this,'survival')">🌲 Survival</div>
    <div class="chip" onclick="filterBuilds(this,'farm')">🌾 Farms</div>
    <div class="chip" onclick="filterBuilds(this,'fantasy')">🧙 Fantasy</div>
    <div class="chip" onclick="filterBuilds(this,'redstone')">🔴 Redstone</div>
  </div>
 
  <div class="builds-grid" id="buildsGrid">
 
    <!-- Card 1 -->
    <div class="build-card fade-in" data-cat="medieval">
      <div class="card-img scene-castle">
        <svg class="pixel-scene" viewBox="0 0 280 180" xmlns="http://www.w3.org/2000/svg">
          <rect width="280" height="180" fill="#1a2e1a"/>
          <rect x="0" y="140" width="280" height="40" fill="#3a5c3a"/>
          <rect x="0" y="130" width="280" height="10" fill="#5D9E3A"/>
          <!-- Castle towers -->
          <rect x="30" y="50" width="40" height="90" fill="#888"/>
          <rect x="150" y="50" width="40" height="90" fill="#888"/>
          <!-- Battlements -->
          <rect x="30" y="40" width="8" height="15" fill="#888"/>
          <rect x="46" y="40" width="8" height="15" fill="#888"/>
          <rect x="62" y="40" width="8" height="15" fill="#888"/>
          <rect x="150" y="40" width="8" height="15" fill="#888"/>
          <rect x="166" y="40" width="8" height="15" fill="#888"/>
          <rect x="182" y="40" width="8" height="15" fill="#888"/>
          <!-- Wall -->
          <rect x="70" y="80" width="80" height="60" fill="#777"/>
          <!-- Gate arch -->
          <rect x="95" y="100" width="30" height="40" fill="#1a2e1a"/>
          <rect x="99" y="96" width="22" height="8" fill="#1a2e1a"/>
          <!-- Windows -->
          <rect x="40" y="65" width="12" height="18" fill="#4FE0D0" opacity="0.6"/>
          <rect x="162" y="65" width="12" height="18" fill="#4FE0D0" opacity="0.6"/>
          <!-- Flag -->
          <rect x="49" y="15" width="2" height="30" fill="#ccc"/>
          <polygon points="51,15 70,22 51,29" fill="#cc3333"/>
          <rect x="169" y="15" width="2" height="30" fill="#ccc"/>
          <polygon points="171,15 190,22 171,29" fill="#cc3333"/>
          <!-- Stars -->
          <circle cx="200" cy="30" r="1.5" fill="#fff" opacity="0.8"/>
          <circle cx="230" cy="20" r="1" fill="#fff" opacity="0.6"/>
          <circle cx="20" cy="25" r="1" fill="#fff" opacity="0.7"/>
          <circle cx="250" cy="50" r="1.5" fill="#fff" opacity="0.5"/>
        </svg>
      </div>
      <div class="card-body">
        <div class="card-meta">
          <span class="difficulty diff-hard">HARD</span>
          <div class="hearts">❤️❤️❤️❤️❤️</div>
        </div>
        <h3 class="card-title">Medieval Castle<br>Stronghold</h3>
        <p class="card-desc">A full fortress with towers, dungeon, throne room and secret passages. Requires 3–5 days to complete.</p>
        <div class="card-footer">
          <span class="card-author">by <strong>SteveMaster99</strong></span>
          <span class="card-views">👁 48.2K</span>
        </div>
      </div>
    </div>
 
    <!-- Card 2 -->
    <div class="build-card fade-in" data-cat="modern">
      <div class="card-img scene-modern">
        <svg class="pixel-scene" viewBox="0 0 280 180" xmlns="http://www.w3.org/2000/svg">
          <rect width="280" height="180" fill="#1a1a2e"/>
          <rect x="0" y="140" width="280" height="40" fill="#2a2a4a"/>
          <rect x="0" y="133" width="280" height="8" fill="#555"/>
          <!-- Building 1 -->
          <rect x="40" y="40" width="60" height="100" fill="#334"/>
          <!-- Glass windows grid -->
          <rect x="47" y="50" width="14" height="10" fill="#4FE0D0" opacity="0.7"/>
          <rect x="67" y="50" width="14" height="10" fill="#4FE0D0" opacity="0.7"/>
          <rect x="87" y="50" width="7" height="10" fill="#4FE0D0" opacity="0.7"/>
          <rect x="47" y="66" width="14" height="10" fill="#4FE0D0" opacity="0.5"/>
          <rect x="67" y="66" width="14" height="10" fill="#4FE0D0" opacity="0.7"/>
          <rect x="87" y="66" width="7" height="10" fill="#fff" opacity="0.4"/>
          <rect x="47" y="82" width="14" height="10" fill="#4FE0D0" opacity="0.7"/>
          <rect x="67" y="82" width="14" height="10" fill="#FFC54E" opacity="0.6"/>
          <rect x="87" y="82" width="7" height="10" fill="#4FE0D0" opacity="0.4"/>
          <rect x="47" y="98" width="14" height="10" fill="#4FE0D0" opacity="0.3"/>
          <rect x="67" y="98" width="14" height="10" fill="#4FE0D0" opacity="0.7"/>
          <rect x="87" y="98" width="7" height="10" fill="#4FE0D0" opacity="0.6"/>
          <!-- Building 2 tall -->
          <rect x="160" y="20" width="50" height="120" fill="#2a3a4a"/>
          <rect x="168" y="30" width="10" height="8" fill="#4FE0D0" opacity="0.6"/>
          <rect x="184" y="30" width="10" height="8" fill="#FFC54E" opacity="0.7"/>
          <rect x="168" y="44" width="10" height="8" fill="#4FE0D0" opacity="0.7"/>
          <rect x="184" y="44" width="10" height="8" fill="#4FE0D0" opacity="0.5"/>
          <rect x="168" y="58" width="10" height="8" fill="#fff" opacity="0.3"/>
          <rect x="184" y="58" width="10" height="8" fill="#4FE0D0" opacity="0.7"/>
          <rect x="168" y="72" width="10" height="8" fill="#4FE0D0" opacity="0.6"/>
          <rect x="184" y="72" width="10" height="8" fill="#FFC54E" opacity="0.5"/>
          <rect x="168" y="86" width="10" height="8" fill="#4FE0D0" opacity="0.7"/>
          <rect x="184" y="86" width="10" height="8" fill="#4FE0D0" opacity="0.4"/>
          <rect x="168" y="100" width="10" height="8" fill="#fff" opacity="0.5"/>
          <rect x="184" y="100" width="10" height="8" fill="#4FE0D0" opacity="0.7"/>
          <!-- Road -->
          <rect x="110" y="133" width="50" height="8" fill="#3a3a3a"/>
          <rect x="133" y="133" width="4" height="8" fill="#fff" opacity="0.3"/>
          <!-- Moon -->
          <circle cx="240" cy="30" r="14" fill="#FFC54E" opacity="0.8"/>
          <circle cx="247" cy="26" r="11" fill="#1a1a2e"/>
        </svg>
      </div>
      <div class="card-body">
        <div class="card-meta">
          <span class="difficulty diff-medium">MEDIUM</span>
          <div class="hearts">❤️❤️❤️❤️</div>
        </div>
        <h3 class="card-title">Modern City<br>Skyline</h3>
        <p class="card-desc">Glass towers, parking structures, and a central plaza. Perfect for creative mode city builds.</p>
        <div class="card-footer">
          <span class="card-author">by <strong>PixelArchitect</strong></span>
          <span class="card-views">👁 31.7K</span>
        </div>
      </div>
    </div>
 
    <!-- Card 3 -->
    <div class="build-card fade-in" data-cat="survival">
      <div class="card-img scene-village">
        <svg class="pixel-scene" viewBox="0 0 280 180" xmlns="http://www.w3.org/2000/svg">
          <rect width="280" height="180" fill="#2e1a0a"/>
          <!-- Sky gradient -->
          <rect x="0" y="0" width="280" height="80" fill="#4a7fc1" opacity="0.4"/>
          <rect x="0" y="120" width="280" height="60" fill="#5D9E3A"/>
          <rect x="0" y="112" width="280" height="10" fill="#8B5E3C"/>
          <!-- House 1 -->
          <rect x="20" y="70" width="70" height="50" fill="#A0722A"/>
          <polygon points="20,70 55,35 90,70" fill="#cc3333"/>
          <rect x="38" y="88" width="18" height="32" fill="#1a1a0a"/>
          <rect x="62" y="82" width="16" height="14" fill="#87CEEB" opacity="0.8"/>
          <!-- Chimney -->
          <rect x="70" y="40" width="8" height="25" fill="#777"/>
          <!-- House 2 -->
          <rect x="160" y="80" width="55" height="40" fill="#c4a26a"/>
          <polygon points="160,80 187,52 215,80" fill="#8B4513"/>
          <rect x="178" y="92" width="16" height="28" fill="#1a1a0a"/>
          <rect x="164" y="85" width="12" height="10" fill="#87CEEB" opacity="0.8"/>
          <!-- Trees -->
          <rect x="110" y="90" width="6" height="30" fill="#8B5E3C"/>
          <ellipse cx="113" cy="80" rx="14" ry="16" fill="#2a7a2a"/>
          <rect x="230" y="88" width="6" height="30" fill="#8B5E3C"/>
          <ellipse cx="233" cy="78" rx="12" ry="14" fill="#2a7a2a"/>
          <!-- Path -->
          <rect x="52" y="120" width="10" height="7" fill="#d4a96a" opacity="0.5"/>
          <rect x="66" y="120" width="10" height="7" fill="#d4a96a" opacity="0.5"/>
          <rect x="80" y="120" width="10" height="7" fill="#d4a96a" opacity="0.5"/>
          <!-- Sun -->
          <circle cx="240" cy="25" r="16" fill="#FFC54E"/>
          <line x1="240" y1="5" x2="240" y2="1" stroke="#FFC54E" stroke-width="2"/>
          <line x1="256" y1="9" x2="259" y2="6" stroke="#FFC54E" stroke-width="2"/>
          <line x1="260" y1="25" x2="264" y2="25" stroke="#FFC54E" stroke-width="2"/>
        </svg>
      </div>
      <div class="card-body">
        <div class="card-meta">
          <span class="difficulty diff-easy">EASY</span>
          <div class="hearts">❤️❤️❤️</div>
        </div>
        <h3 class="card-title">Cozy Survival<br>Village</h3>
        <p class="card-desc">A charming starter village with homes, wells, gardens and paths. Ideal for first-time builders.</p>
        <div class="card-footer">
          <span class="card-author">by <strong>CraftyCreeper</strong></span>
          <span class="card-views">👁 92.4K</span>
        </div>
      </div>
    </div>
 
    <!-- Card 4 -->
    <div class="build-card fade-in" data-cat="farm">
      <div class="card-img scene-farm">
        <svg class="pixel-scene" viewBox="0 0 280 180" xmlns="http://www.w3.org/2000/svg">
          <rect width="280" height="180" fill="#0a2e0a"/>
          <rect x="0" y="110" width="280" height="70" fill="#3a6a1a"/>
          <!-- Wheat rows -->
          <rect x="20" y="98" width="8" height="16" fill="#FFC54E"/>
          <rect x="36" y="95" width="8" height="19" fill="#FFC54E"/>
          <rect x="52" y="98" width="8" height="16" fill="#E2C97E"/>
          <rect x="68" y="94" width="8" height="20" fill="#FFC54E"/>
          <rect x="84" y="97" width="8" height="17" fill="#FFC54E"/>
          <rect x="100" y="95" width="8" height="19" fill="#E2C97E"/>
          <rect x="116" y="98" width="8" height="16" fill="#FFC54E"/>
          <!-- Barn -->
          <rect x="170" y="55" width="85" height="60" fill="#8B3a1a"/>
          <polygon points="170,55 212,20 255,55" fill="#6a2a12"/>
          <rect x="197" y="80" width="30" height="35" fill="#3a1a0a"/>
          <rect x="182" y="62" width="18" height="14" fill="#FFC54E" opacity="0.6"/>
          <rect x="232" y="62" width="18" height="14" fill="#FFC54E" opacity="0.6"/>
          <!-- Windmill -->
          <rect x="60" y="40" width="8" height="60" fill="#c4a26a"/>
          <line x1="64" y1="48" x2="64" y2="10" stroke="#888" stroke-width="3"/>
          <line x1="64" y1="48" x2="90" y2="48" stroke="#888" stroke-width="3"/>
          <line x1="64" y1="48" x2="64" y2="86" stroke="#888" stroke-width="3"/>
          <line x1="64" y1="48" x2="38" y2="48" stroke="#888" stroke-width="3"/>
          <!-- Sky -->
          <rect x="0" y="0" width="280" height="40" fill="#87CEEB" opacity="0.3"/>
          <rect x="0" y="40" width="280" height="20" fill="#87CEEB" opacity="0.15"/>
          <!-- Cloud -->
          <ellipse cx="130" cy="22" rx="28" ry="10" fill="#fff" opacity="0.6"/>
          <ellipse cx="155" cy="18" rx="18" ry="9" fill="#fff" opacity="0.6"/>
          <circle cx="240" cy="18" r="12" fill="#FFC54E"/>
        </svg>
      </div>
      <div class="card-body">
        <div class="card-meta">
          <span class="difficulty diff-easy">EASY</span>
          <div class="hearts">❤️❤️❤️❤️</div>
        </div>
        <h3 class="card-title">Auto Wheat<br>Farm + Barn</h3>
        <p class="card-desc">Efficient automated wheat farm with a classic red barn. Includes basic redstone automation.</p>
        <div class="card-footer">
          <span class="card-author">by <strong>FarmerJoe_MC</strong></span>
          <span class="card-views">👁 67.1K</span>
        </div>
      </div>
    </div>
 
    <!-- Card 5 -->
    <div class="build-card fade-in" data-cat="fantasy">
      <div class="card-img scene-underwater">
        <svg class="pixel-scene" viewBox="0 0 280 180" xmlns="http://www.w3.org/2000/svg">
          <rect width="280" height="180" fill="#0a1a2e"/>
          <!-- Underwater glow -->
          <rect x="0" y="0" width="280" height="180" fill="#0066aa" opacity="0.2"/>
          <!-- Coral -->
          <rect x="20" y="130" width="6" height="30" fill="#cc4444"/>
          <ellipse cx="23" cy="128" rx="8" ry="6" fill="#ee5555"/>
          <rect x="40" y="120" width="6" height="40" fill="#cc7722"/>
          <ellipse cx="43" cy="118" rx="10" ry="7" fill="#ffaa33"/>
          <rect x="60" y="135" width="6" height="25" fill="#44cc88"/>
          <ellipse cx="63" cy="133" rx="7" ry="5" fill="#55ffaa"/>
          <!-- Crystal Palace -->
          <polygon points="120,40 140,20 160,40" fill="#4FE0D0" opacity="0.8"/>
          <polygon points="140,40 155,25 170,40" fill="#4FE0D0" opacity="0.7"/>
          <rect x="100" y="40" width="90" height="80" fill="#1a6a8a"/>
          <rect x="100" y="40" width="90" height="80" fill="url(#glass)" opacity="0.3"/>
          <!-- Windows -->
          <rect x="110" y="55" width="15" height="12" fill="#4FE0D0" opacity="0.8"/>
          <rect x="135" y="55" width="15" height="12" fill="#4FE0D0" opacity="0.8"/>
          <rect x="160" y="55" width="15" height="12" fill="#4FE0D0" opacity="0.8"/>
          <rect x="110" y="75" width="15" height="12" fill="#4FE0D0" opacity="0.6"/>
          <rect x="135" y="75" width="15" height="12" fill="#FFC54E" opacity="0.7"/>
          <rect x="160" y="75" width="15" height="12" fill="#4FE0D0" opacity="0.6"/>
          <!-- Door -->
          <rect x="130" y="95" width="30" height="25" fill="#0a3a5a"/>
          <!-- Bubbles -->
          <circle cx="50" cy="60" r="4" fill="none" stroke="#87CEEB" stroke-width="1.5" opacity="0.7"/>
          <circle cx="80" cy="40" r="3" fill="none" stroke="#87CEEB" stroke-width="1.5" opacity="0.5"/>
          <circle cx="220" cy="70" r="5" fill="none" stroke="#87CEEB" stroke-width="1.5" opacity="0.6"/>
          <circle cx="240" cy="45" r="3" fill="none" stroke="#87CEEB" stroke-width="1.5" opacity="0.4"/>
          <!-- Fish -->
          <ellipse cx="230" cy="100" rx="12" ry="6" fill="#ff6644" opacity="0.8"/>
          <polygon points="242,100 254,94 254,106" fill="#ff6644" opacity="0.8"/>
          <!-- Sandy floor -->
          <rect x="0" y="155" width="280" height="25" fill="#c4a26a" opacity="0.5"/>
        </svg>
      </div>
      <div class="card-body">
        <div class="card-meta">
          <span class="difficulty diff-hard">HARD</span>
          <div class="hearts">❤️❤️❤️❤️❤️</div>
        </div>
        <h3 class="card-title">Underwater<br>Crystal Palace</h3>
        <p class="card-desc">A stunning prismarine palace beneath the ocean surface. Requires ocean monument location and diving gear.</p>
        <div class="card-footer">
          <span class="card-author">by <strong>AquaBuilder</strong></span>
          <span class="card-views">👁 55.9K</span>
        </div>
      </div>
    </div>
 
    <!-- Card 6 -->
    <div class="build-card fade-in" data-cat="redstone">
      <div class="card-img scene-nether">
        <svg class="pixel-scene" viewBox="0 0 280 180" xmlns="http://www.w3.org/2000/svg">
          <rect width="280" height="180" fill="#2e0a0a"/>
          <!-- Lava glow -->
          <rect x="0" y="130" width="280" height="50" fill="#cc4400" opacity="0.4"/>
          <rect x="0" y="138" width="280" height="42" fill="#ff6600" opacity="0.3"/>
          <!-- Lava bubbles -->
          <circle cx="50" cy="148" r="10" fill="#ff8800" opacity="0.6"/>
          <circle cx="100" cy="155" r="8" fill="#ff6600" opacity="0.5"/>
          <circle cx="200" cy="150" r="12" fill="#ff8800" opacity="0.6"/>
          <circle cx="250" cy="148" r="9" fill="#ff6600" opacity="0.5"/>
          <!-- Machine structure -->
          <rect x="80" y="50" width="120" height="80" fill="#333"/>
          <!-- Redstone dust -->
          <rect x="40" y="110" width="40" height="4" fill="#cc0000" opacity="0.8"/>
          <rect x="200" y="110" width="40" height="4" fill="#cc0000" opacity="0.8"/>
          <rect x="78" y="90" width="4" height="24" fill="#cc0000" opacity="0.8"/>
          <rect x="198" y="90" width="4" height="24" fill="#cc0000" opacity="0.8"/>
          <!-- Pistons -->
          <rect x="85" y="60" width="16" height="20" fill="#777"/>
          <rect x="111" y="60" width="16" height="20" fill="#777"/>
          <rect x="137" y="60" width="16" height="20" fill="#777"/>
          <rect x="163" y="60" width="16" height="20" fill="#777"/>
          <!-- Redstone torches -->
          <rect x="92" y="55" width="4" height="10" fill="#555"/>
          <rect x="91" y="53" width="6" height="4" fill="#cc0000"/>
          <circle cx="94" cy="52" r="3" fill="#ff3300" opacity="0.7"/>
          <rect x="168" y="55" width="4" height="10" fill="#555"/>
          <rect x="167" y="53" width="6" height="4" fill="#cc0000"/>
          <circle cx="170" cy="52" r="3" fill="#ff3300" opacity="0.7"/>
          <!-- Repeaters -->
          <rect x="100" y="108" width="12" height="6" fill="#555"/>
          <rect x="168" y="108" width="12" height="6" fill="#555"/>
          <!-- Output beam -->
          <rect x="128" y="35" width="24" height="18" fill="#cc0000" opacity="0.3"/>
          <circle cx="140" cy="36" r="8" fill="#ff0000" opacity="0.5"/>
          <circle cx="140" cy="36" r="4" fill="#fff" opacity="0.6"/>
          <!-- Sparks -->
          <circle cx="55" cy="108" r="2" fill="#ff6600"/>
          <circle cx="220" cy="108" r="2" fill="#ff6600"/>
          <circle cx="60" cy="104" r="1.5" fill="#ff8800"/>
          <circle cx="215" cy="104" r="1.5" fill="#ff8800"/>
        </svg>
      </div>
      <div class="card-body">
        <div class="card-meta">
          <span class="difficulty diff-hard">HARD</span>
          <div class="hearts">❤️❤️❤️❤️❤️</div>
        </div>
        <h3 class="card-title">Item Sorter<br>Mega Machine</h3>
        <p class="card-desc">Fully automated redstone item sorter with 64 categories, overflow protection and display system.</p>
        <div class="card-footer">
          <span class="card-author">by <strong>RedstoneKing</strong></span>
          <span class="card-views">👁 124.3K</span>
        </div>
      </div>
    </div>
 
  </div>
</section>
 
<!-- TUTORIALS SECTION -->
<section id="tutorials">
  <div class="section-head fade-in">
    <h2>📖 Step-by-Step Tutorials</h2>
    <p>Learn from seasoned builders — from basic skills to advanced redstone engineering.</p>
    <div class="pixel-divider"></div>
  </div>
 
  <div class="tutorials-grid">
    <div class="tutorial-card fade-in">
      <div class="tut-icon">🪵</div>
      <div class="tut-body">
        <h3>How to Build a Starter Home in 10 Minutes</h3>
        <p>Perfect for new Survival Mode players. Learn room layout, lighting, and quick defensive walls.</p>
        <span class="tut-tag">Beginner · 10 min</span>
      </div>
    </div>
    <div class="tutorial-card fade-in">
      <div class="tut-icon">🔴</div>
      <div class="tut-body">
        <h3>Redstone 101: Doors, Traps & Clocks</h3>
        <p>Master basic redstone circuits, piston doors, and repeater clocks for automation beginners.</p>
        <span class="tut-tag">Beginner · 25 min</span>
      </div>
    </div>
    <div class="tutorial-card fade-in">
      <div class="tut-icon">🏰</div>
      <div class="tut-body">
        <h3>Medieval Architecture Secrets Pro Builders Use</h3>
        <p>Learn depth tricks, material mixing, and texturing techniques that make builds look truly medieval.</p>
        <span class="tut-tag">Advanced · 45 min</span>
      </div>
    </div>
    <div class="tutorial-card fade-in">
      <div class="tut-icon">🌾</div>
      <div class="tut-body">
        <h3>Build an AFK Fish Farm (Works 1.21)</h3>
        <p>Step-by-step AFK fish farm that works in the latest version. Full materials list included.</p>
        <span class="tut-tag">Intermediate · 20 min</span>
      </div>
    </div>
    <div class="tutorial-card fade-in">
      <div class="tut-icon">🎨</div>
      <div class="tut-body">
        <h3>Color Theory for Minecraft Builders</h3>
        <p>How to choose the right blocks for palettes that look great in any biome or lighting condition.</p>
        <span class="tut-tag">Intermediate · 30 min</span>
      </div>
    </div>
    <div class="tutorial-card fade-in">
      <div class="tut-icon">🗺️</div>
      <div class="tut-body">
        <h3>Planning Large Builds: Grid & Blueprint Method</h3>
        <p>Map your mega-project before placing a single block. Includes free downloadable grid template.</p>
        <span class="tut-tag">Advanced · 1 hr</span>
      </div>
    </div>
  </div>
</section>
 
<!-- MATERIALS SECTION -->
<div class="material-section" id="materials">
  <div class="material-inner">
    <div class="section-head fade-in">
      <h2>🧱 Block Library</h2>
      <p>Click a block to see build ideas and compatible pairings.</p>
      <div class="pixel-divider"></div>
    </div>
    <div class="blocks-grid" id="blockGrid">
    </div>
  </div>
</div>
 
<!-- NEWSLETTER -->
<section id="community" style="display:flex;justify-content:center;">
  <div class="newsletter fade-in">
    <h2>Get Weekly Build Drops</h2>
    <p>New builds, tutorials, and community picks — straight to your inbox every Sunday.</p>
    <div class="email-row">
      <input type="email" placeholder="your@email.com" id="emailInput"/>
      <button onclick="subscribe()">SUBSCRIBE</button>
    </div>
  </div>
</section>
 
<!-- FOOTER -->
<footer>
  <div class="footer-grid">
    <div class="footer-brand">
      <span class="logo">Craft<span>Builds</span></span>
      <p>The ultimate Minecraft building resource. Built by the community, for the community. Not affiliated with Mojang or Microsoft.</p>
    </div>
    <div class="footer-col">
      <h4>Builds</h4>
      <ul>
        <li><a href="#">Medieval</a></li>
        <li><a href="#">Modern</a></li>
        <li><a href="#">Fantasy</a></li>
        <li><a href="#">Survival</a></li>
        <li><a href="#">Redstone</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Learn</h4>
      <ul>
        <li><a href="#">Tutorials</a></li>
        <li><a href="#">Block Guide</a></li>
        <li><a href="#">Schematics</a></li>
        <li><a href="#">Seed Finder</a></li>
        <li><a href="#">Changelog</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Community</h4>
      <ul>
        <li><a href="#">Discord Server</a></li>
        <li><a href="#">Submit Build</a></li>
        <li><a href="#">Hall of Fame</a></li>
        <li><a href="#">Newsletter</a></li>
        <li><a href="#">About Us</a></li>
      </ul>
    </div>
  </div>
  <div class="footer-bottom">
    <p>⛏️ CraftBuilds 2026 — Made with ❤️ by Minecraft fans worldwide</p>
  </div>
</footer>
 
<!-- TOAST -->
<div class="toast" id="toast"></div>
 
<script>
  // Block data
  const blocks = [
    { name: 'Grass', color: '#5D9E3A', dark: '#2a5c1a' },
    { name: 'Dirt', color: '#8B5E3C', dark: '#5c3a20' },
    { name: 'Stone', color: '#888', dark: '#555' },
    { name: 'Oak Wood', color: '#A0722A', dark: '#6b4a18' },
    { name: 'Birch', color: '#E2D6B5', dark: '#a89a74' },
    { name: 'Spruce', color: '#5c3a1a', dark: '#3a2210' },
    { name: 'Dark Oak', color: '#3a2510', dark: '#200e00' },
    { name: 'Cobble', color: '#7a7a7a', dark: '#4a4a4a' },
    { name: 'Brick', color: '#a44a3a', dark: '#6a2a1a' },
    { name: 'Sand', color: '#E2C97E', dark: '#a89040' },
    { name: 'Sandstone', color: '#D4B96A', dark: '#967830' },
    { name: 'Gravel', color: '#9a9090', dark: '#6a6060' },
    { name: 'Iron', color: '#c0c0c0', dark: '#888' },
    { name: 'Gold', color: '#FFC54E', dark: '#a87a10' },
    { name: 'Diamond', color: '#4FE0D0', dark: '#1a9a8a' },
    { name: 'Emerald', color: '#2ecc71', dark: '#1a7a40' },
    { name: 'Obsidian', color: '#1a0a2e', dark: '#0a0014' },
    { name: 'Netherrack', color: '#6a1a1a', dark: '#3a0a0a' },
    { name: 'Prismarine', color: '#3a8a8a', dark: '#1a5a5a' },
    { name: 'Glowstone', color: '#ffa040', dark: '#c06000' },
  ];
 
  const blockGrid = document.getElementById('blockGrid');
  blocks.forEach(b => {
    const el = document.createElement('div');
    el.className = 'block-item';
    el.innerHTML = `
      <div class="block-face" style="background:${b.color};border-color:${b.dark};box-shadow:inset -6px -6px 0 ${b.dark}, inset 6px 6px 0 rgba(255,255,255,0.2);image-rendering:pixelated;"></div>
      <div class="block-name" style="color:#8FB3A0;">${b.name}</div>
    `;
    el.onclick = () => showToast(`${b.name} selected!\nGreat for walls & floors.`);
    blockGrid.appendChild(el);
  });
 
  // Category filter
  function filterBuilds(el, cat) {
    document.querySelectorAll('.chip').forEach(c => c.classList.remove('active'));
    el.classList.add('active');
    document.querySelectorAll('.build-card').forEach(card => {
      if (cat === 'all' || card.dataset.cat === cat) {
        card.style.display = '';
      } else {
        card.style.display = 'none';
      }
    });
  }
 
  // Search
  function handleSearch() {
    const q = document.getElementById('searchInput').value.trim();
    if (q) showToast(`Searching for "${q}"...`);
  }
 
  document.getElementById('searchInput').addEventListener('keydown', e => {
    if (e.key === 'Enter') handleSearch();
  });
 
  // Subscribe
  function subscribe() {
    const email = document.getElementById('emailInput').value;
    if (email && email.includes('@')) {
      showToast('Subscribed! ✅\nCheck your inbox soon.');
      document.getElementById('emailInput').value = '';
    } else {
      showToast('Please enter a valid\nemail address!');
    }
  }
 
  // Toast
  function showToast(msg) {
    const t = document.getElementById('toast');
    t.textContent = msg;
    t.classList.add('show');
    setTimeout(() => t.classList.remove('show'), 3000);
  }
 
  // Scroll fade-in
  const observer = new IntersectionObserver(entries => {
    entries.forEach((e, i) => {
      if (e.isIntersecting) {
        setTimeout(() => e.target.classList.add('visible'), i * 80);
        observer.unobserve(e.target);
      }
    });
  }, { threshold: 0.1 });
 
  document.querySelectorAll('.fade-in').forEach(el => observer.observe(el));
 
  // Smooth scroll for nav links
  document.querySelectorAll('a[href^="#"]').forEach(a => {
    a.addEventListener('click', e => {
      e.preventDefault();
      document.querySelector(a.getAttribute('href'))?.scrollIntoView({ behavior: 'smooth' });
    });
  });
</script>
</body>
</html>
