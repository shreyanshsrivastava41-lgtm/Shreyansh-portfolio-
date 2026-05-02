<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Shreyansh Srivastava | Recruitment Specialists</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400&family=DM+Mono:ital,wght@0,300;0,400;1,300&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --bg: #0d0d0d;
      --bg2: #141414;
      --bg3: #1c1c1c;
      --gold: #c9a84c;
      --gold-light: #e2c07a;
      --gold-dim: #7a6330;
      --white: #f0ebe0;
      --grey: #6b6b6b;
      --grey-light: #9a9a9a;
      --border: rgba(201,168,76,0.18);
      --font-display: 'Playfair Display', serif;
      --font-mono: 'DM Mono', monospace;
      --font-body: 'DM Sans', sans-serif;
      --glass-bg: rgba(20, 20, 20, 0.7);
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    html { scroll-behavior: smooth; }

    body {
      background: var(--bg);
      color: var(--white);
      font-family: var(--font-body);
      font-weight: 300;
      overflow-x: hidden;
      cursor: default;
      position: relative;
    }

    /* Grain overlay */
    body::before {
      content: '';
      position: fixed;
      inset: 0;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 512 512' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
      pointer-events: none;
      z-index: 9998;
      opacity: 0.35;
    }

    /* ── UI UPGRADE: Ambient Glows ── */
    .ambient-glow {
      position: absolute;
      width: 40vw;
      height: 40vw;
      background: radial-gradient(circle, rgba(201,168,76,0.08) 0%, transparent 70%);
      top: -10vw;
      left: -10vw;
      border-radius: 50%;
      pointer-events: none;
      z-index: 0;
    }
    .ambient-glow.right {
      top: 20%;
      left: auto;
      right: -15vw;
      background: radial-gradient(circle, rgba(201,168,76,0.05) 0%, transparent 70%);
    }

    /* ── NAV ── */
    nav {
      position: fixed;
      top: 0; left: 0; right: 0;
      z-index: 100;
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 1.2rem 4rem;
      background: var(--glass-bg);
      backdrop-filter: blur(12px);
      -webkit-backdrop-filter: blur(12px);
      border-bottom: 1px solid rgba(255,255,255,0.02);
      transition: all 0.3s ease;
    }
    nav.scrolled {
      padding: 0.8rem 4rem;
      box-shadow: 0 4px 30px rgba(0, 0, 0, 0.5);
    }
    .nav-logo {
      font-family: var(--font-display);
      font-size: 1.1rem;
      font-style: italic;
      color: var(--gold);
      letter-spacing: 0.02em;
    }
    .nav-links {
      display: flex;
      gap: 2.5rem;
      list-style: none;
    }
    .nav-links a {
      font-family: var(--font-mono);
      font-size: 0.72rem;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: var(--grey-light);
      text-decoration: none;
      transition: color 0.3s, text-shadow 0.3s;
    }
    .nav-links a:hover { 
      color: var(--gold); 
      text-shadow: 0 0 8px rgba(201,168,76,0.4);
    }

    /* ── HERO ── */
    #hero {
      min-height: 100vh;
      display: grid;
      grid-template-columns: 1fr 1fr;
      align-items: center;
      padding: 8rem 4rem 4rem;
      position: relative;
      overflow: hidden;
    }
    .hero-bg-text {
      position: absolute;
      bottom: -2rem;
      right: -1rem;
      font-family: var(--font-display);
      font-size: clamp(6rem, 15vw, 18rem);
      font-weight: 900;
      color: rgba(201,168,76,0.03);
      line-height: 1;
      pointer-events: none;
      user-select: none;
      white-space: nowrap;
    }
    .hero-left { position: relative; z-index: 1; }
    .hero-tag {
      display: inline-flex;
      align-items: center;
      gap: 0.6rem;
      font-family: var(--font-mono);
      font-size: 0.7rem;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--gold);
      margin-bottom: 1.8rem;
      opacity: 0;
      animation: fadeUp 0.8s ease 0.2s forwards;
    }
    .hero-tag::before { content: ''; width: 2rem; height: 1px; background: var(--gold); }
    .hero-name {
      font-family: var(--font-display);
      font-size: clamp(2.8rem, 6vw, 5.5rem);
      font-weight: 900;
      line-height: 1.05;
      letter-spacing: -0.01em;
      margin-bottom: 1.2rem;
      opacity: 0;
      animation: fadeUp 0.8s ease 0.4s forwards;
    }
    .hero-name em { font-style: italic; color: var(--gold); text-shadow: 0 0 20px rgba(201,168,76,0.2); }
    .hero-title {
      font-family: var(--font-mono);
      font-size: 0.85rem;
      color: var(--grey-light);
      letter-spacing: 0.08em;
      margin-bottom: 2rem;
      opacity: 0;
      animation: fadeUp 0.8s ease 0.55s forwards;
    }
    .typewriter-container {
      font-family: var(--font-mono);
      font-size: 0.9rem;
      color: var(--grey-light);
      margin-bottom: 3rem;
      min-height: 1.4em;
      opacity: 0;
      animation: fadeUp 0.8s ease 0.7s forwards;
    }
    #typewriter-text { color: var(--gold-light); }
    .cursor {
      display: inline-block;
      width: 2px; height: 1em; background: var(--gold);
      margin-left: 2px; vertical-align: middle;
      animation: blink 1s step-end infinite;
    }
    @keyframes blink { 50% { opacity: 0; } }
    .hero-ctas {
      display: flex; gap: 1rem; flex-wrap: wrap;
      opacity: 0; animation: fadeUp 0.8s ease 0.85s forwards;
    }
    .btn-primary {
      padding: 0.85rem 2rem; background: var(--gold); color: #0d0d0d;
      font-family: var(--font-mono); font-size: 0.72rem; font-weight: 600;
      letter-spacing: 0.15em; text-transform: uppercase; text-decoration: none;
      border: none; cursor: pointer; transition: all 0.3s;
      box-shadow: 0 0 15px rgba(201,168,76,0.2);
    }
    .btn-primary:hover { background: var(--gold-light); transform: translateY(-2px); box-shadow: 0 5px 20px rgba(201,168,76,0.4); }
    .btn-secondary {
      padding: 0.85rem 2rem; background: transparent; color: var(--gold);
      font-family: var(--font-mono); font-size: 0.72rem;
      letter-spacing: 0.15em; text-transform: uppercase; text-decoration: none;
      border: 1px solid var(--border); cursor: pointer; transition: all 0.3s;
    }
    .btn-secondary:hover { border-color: var(--gold); color: var(--gold-light); transform: translateY(-2px); background: rgba(201,168,76,0.05); }
    
    .hero-right {
      display: flex; flex-direction: column; align-items: flex-end;
      gap: 1.5rem; position: relative; z-index: 1;
      opacity: 0; animation: fadeIn 1s ease 1s forwards;
    }
    .stat-card {
      background: rgba(20,20,20,0.6);
      backdrop-filter: blur(5px);
      border: 1px solid var(--border);
      padding: 1.5rem 2rem; width: 16rem;
      position: relative; overflow: hidden;
      transition: transform 0.3s, border-color 0.3s;
    }
    .stat-card:hover {
      transform: translateX(-10px);
      border-color: rgba(201,168,76,0.4);
    }
    .stat-card::before { content: ''; position: absolute; top: 0; left: 0; width: 3px; height: 100%; background: var(--gold); }
    .stat-number { font-family: var(--font-display); font-size: 2.8rem; font-weight: 700; color: var(--gold); line-height: 1; }
    .stat-label { font-family: var(--font-mono); font-size: 0.65rem; letter-spacing: 0.18em; text-transform: uppercase; color: var(--grey); margin-top: 0.3rem; }

    /* ── SECTION COMMON ── */
    section { padding: 6rem 4rem; position: relative; }
    .section-header { display: flex; align-items: center; gap: 1.5rem; margin-bottom: 4rem; }
    .section-num { font-family: var(--font-mono); font-size: 0.65rem; color: var(--gold-dim); letter-spacing: 0.2em; }
    .section-title { font-family: var(--font-display); font-size: clamp(2rem, 4vw, 3.2rem); font-weight: 700; line-height: 1; }
    .section-line { flex: 1; height: 1px; background: linear-gradient(90deg, var(--border), transparent); }

    /* ── ABOUT ── */
    #about { background: var(--bg2); }
    .about-grid { display: grid; grid-template-columns: 1.2fr 1fr; gap: 5rem; align-items: start; }
    .about-bio { font-size: 1.05rem; line-height: 1.8; color: var(--grey-light); }
    .about-bio strong { color: var(--white); font-weight: 500; }
    .about-bio p + p { margin-top: 1.2rem; }
    .about-details { display: flex; flex-direction: column; gap: 1rem; }
    .detail-row { display: flex; justify-content: space-between; align-items: center; padding: 1rem 0; border-bottom: 1px solid var(--border); transition: border-color 0.3s; }
    .detail-row:hover { border-color: var(--gold-dim); }
    .detail-key { font-family: var(--font-mono); font-size: 0.65rem; letter-spacing: 0.2em; text-transform: uppercase; color: var(--grey); }
    .detail-val { font-size: 0.9rem; color: var(--white); text-align: right; }
    .badge { display: inline-block; padding: 0.25rem 0.7rem; background: rgba(201,168,76,0.12); border: 1px solid var(--border); color: var(--gold); font-family: var(--font-mono); font-size: 0.62rem; letter-spacing: 0.15em; text-transform: uppercase; }

    /* ── EXPERIENCE ── */
    #experience { background: var(--bg); }
    .exp-timeline { position: relative; padding-left: 2rem; }
    .exp-timeline::before { content: ''; position: absolute; left: 0; top: 0; bottom: 0; width: 1px; background: var(--border); }
    .exp-item { position: relative; padding: 0 0 3.5rem 2.5rem; opacity: 0; transform: translateX(-20px); transition: opacity 0.6s ease, transform 0.6s ease; }
    .exp-item.visible { opacity: 1; transform: translateX(0); }
    .exp-item::before { content: ''; position: absolute; left: -4.5px; top: 0.4rem; width: 9px; height: 9px; background: var(--gold); border-radius: 50%; box-shadow: 0 0 10px rgba(201,168,76,0.5); transition: transform 0.3s, box-shadow 0.3s; }
    .exp-item:hover::before { transform: scale(1.5); box-shadow: 0 0 15px rgba(201,168,76,0.8); }
    .exp-period { font-family: var(--font-mono); font-size: 0.65rem; letter-spacing: 0.18em; color: var(--gold-dim); text-transform: uppercase; margin-bottom: 0.5rem; }
    .exp-role { font-family: var(--font-display); font-size: 1.5rem; font-weight: 700; margin-bottom: 0.2rem; }
    .exp-company { font-family: var(--font-mono); font-size: 0.8rem; color: var(--gold); letter-spacing: 0.1em; margin-bottom: 1rem; }
    .exp-desc { font-size: 0.9rem; line-height: 1.7; color: var(--grey-light); max-width: 60rem; }
    .exp-tags { display: flex; flex-wrap: wrap; gap: 0.5rem; margin-top: 1rem; }
    .exp-tag { font-family: var(--font-mono); font-size: 0.6rem; letter-spacing: 0.15em; text-transform: uppercase; padding: 0.25rem 0.65rem; border: 1px solid var(--border); color: var(--grey); transition: all 0.3s; }
    .exp-item:hover .exp-tag { border-color: rgba(201,168,76,0.3); color: var(--white); }

    /* ── SKILLS ── */
    #skills { background: var(--bg2); }
    .skills-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 1.5rem; }
    .skill-block { background: var(--bg3); border: 1px solid var(--border); padding: 2rem; position: relative; overflow: hidden; opacity: 0; transform: translateY(20px); transition: opacity 0.5s, transform 0.5s, border-color 0.3s, box-shadow 0.3s; }
    .skill-block.visible { opacity: 1; transform: translateY(0); }
    .skill-block:hover { border-color: rgba(201,168,76,0.4); box-shadow: 0 10px 30px rgba(0,0,0,0.5); transform: translateY(-5px); }
    .skill-block-icon { font-size: 1.5rem; margin-bottom: 1rem; }
    .skill-block-title { font-family: var(--font-display); font-size: 1.1rem; font-weight: 700; margin-bottom: 0.8rem; }
    .skill-list { list-style: none; display: flex; flex-direction: column; gap: 0.4rem; }
    .skill-list li { font-family: var(--font-mono); font-size: 0.72rem; letter-spacing: 0.08em; color: var(--grey-light); display: flex; align-items: center; gap: 0.5rem; }
    .skill-list li::before { content: '▸'; color: var(--gold); font-size: 0.6rem; }

    /* ── MARKETS ── */
    #markets { background: var(--bg); }
    .markets-grid { display: grid; grid-template-columns: repeat(4, 1fr); gap: 1.5rem; }
    .market-card { border: 1px solid var(--border); padding: 2.5rem 1.5rem; text-align: center; position: relative; overflow: hidden; cursor: default; opacity: 0; transform: scale(0.95); transition: opacity 0.5s, transform 0.5s, background 0.4s, border-color 0.4s; }
    .market-card.visible { opacity: 1; transform: scale(1); }
    .market-card:hover { background: rgba(201,168,76,0.05); border-color: var(--gold); transform: scale(1.02); }
    .market-flag { font-size: 2.5rem; margin-bottom: 0.8rem; filter: grayscale(20%); transition: filter 0.3s; }
    .market-card:hover .market-flag { filter: grayscale(0%); }
    .market-name { font-family: var(--font-display); font-size: 1.3rem; font-weight: 700; margin-bottom: 0.3rem; }
    .market-sub { font-family: var(--font-mono); font-size: 0.65rem; letter-spacing: 0.15em; text-transform: uppercase; color: var(--gold-dim); }

    /* ── CONTACT ── */
    #contact { background: var(--bg2); text-align: center; }
    .contact-inner { max-width: 50rem; margin: 0 auto; }
    .contact-heading { font-family: var(--font-display); font-size: clamp(2.5rem, 5vw, 4.5rem); font-weight: 900; line-height: 1.1; margin-bottom: 1.5rem; }
    .contact-heading em { font-style: italic; color: var(--gold); }
    .contact-sub { font-size: 1rem; line-height: 1.7; color: var(--grey-light); margin-bottom: 3rem; }
    .contact-links { display: flex; justify-content: center; gap: 1.5rem; flex-wrap: wrap; margin-bottom: 3rem; }
    .contact-link { display: flex; align-items: center; gap: 0.6rem; font-family: var(--font-mono); font-size: 0.75rem; letter-spacing: 0.12em; text-transform: uppercase; color: var(--grey-light); text-decoration: none; padding: 0.8rem 1.5rem; border: 1px solid var(--border); transition: color 0.3s, border-color 0.3s, transform 0.2s; background: rgba(255,255,255,0.01); }
    .contact-link:hover { color: var(--gold); border-color: var(--gold); transform: translateY(-3px); background: rgba(201,168,76,0.05); }
    .contact-email { font-family: var(--font-display); font-size: 1.2rem; font-style: italic; color: var(--gold); }

    /* ── FOOTER ── */
    footer { padding: 2rem 4rem; border-top: 1px solid var(--border); display: flex; justify-content: space-between; align-items: center; background: var(--bg); }
    footer p { font-family: var(--font-mono); font-size: 0.65rem; letter-spacing: 0.15em; color: var(--grey); }

    /* ── SCROLL REVEAL ── */
    .reveal { opacity: 0; transform: translateY(30px); transition: opacity 0.7s ease, transform 0.7s ease; }
    .reveal.visible { opacity: 1; transform: translateY(0); }

    /* ── UI UPGRADE: AI AGENT WIDGET ── */
    .ai-widget-container {
      position: fixed;
      bottom: 2rem; right: 2rem;
      z-index: 10000;
      display: flex; flex-direction: column; align-items: flex-end; gap: 1rem;
    }
    .ai-btn {
      width: 3.5rem; height: 3.5rem;
      background: var(--gold);
      border-radius: 50%;
      display: flex; justify-content: center; align-items: center;
      cursor: pointer;
      box-shadow: 0 5px 20px rgba(201,168,76,0.4);
      border: none;
      transition: transform 0.3s, box-shadow 0.3s;
    }
    .ai-btn:hover {
      transform: scale(1.05);
      box-shadow: 0 8px 25px rgba(201,168,76,0.6);
    }
    .ai-btn svg { width: 1.5rem; height: 1.5rem; fill: var(--bg); }
    
    .ai-chat-window {
      width: 320px;
      height: 400px;
      background: rgba(20, 20, 20, 0.85);
      backdrop-filter: blur(15px);
      -webkit-backdrop-filter: blur(15px);
      border: 1px solid var(--border);
      border-radius: 12px;
      display: flex; flex-direction: column;
      overflow: hidden;
      box-shadow: 0 10px 40px rgba(0,0,0,0.8);
      opacity: 0; transform: translateY(20px) scale(0.95);
      pointer-events: none; transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
      transform-origin: bottom right;
    }
    .ai-chat-window.active {
      opacity: 1; transform: translateY(0) scale(1); pointer-events: auto;
    }
    .chat-header {
      padding: 1rem;
      background: rgba(201,168,76,0.1);
      border-bottom: 1px solid var(--border);
      display: flex; justify-content: space-between; align-items: center;
    }
    .chat-title {
      font-family: var(--font-mono); font-size: 0.75rem; letter-spacing: 0.1em;
      color: var(--gold); display: flex; align-items: center; gap: 0.5rem;
    }
    .chat-title::before {
      content: ''; width: 8px; height: 8px; background: #6ee7b7;
      border-radius: 50%; box-shadow: 0 0 5px #6ee7b7;
    }
    .close-chat { background: none; border: none; color: var(--grey-light); cursor: pointer; font-size: 1.2rem; transition: color 0.2s; }
    .close-chat:hover { color: var(--white); }
    
    .chat-body {
      flex: 1; padding: 1rem; overflow-y: auto;
      display: flex; flex-direction: column; gap: 0.8rem;
    }
    .chat-body::-webkit-scrollbar { width: 4px; }
    .chat-body::-webkit-scrollbar-thumb { background: var(--grey); border-radius: 4px; }
    
    .msg { max-width: 85%; padding: 0.7rem 1rem; font-size: 0.8rem; line-height: 1.4; border-radius: 8px; animation: fadeIn 0.3s ease; }
    .msg.bot { background: rgba(255,255,255,0.05); color: var(--white); align-self: flex-start; border-bottom-left-radius: 2px; }
    .msg.user { background: rgba(201,168,76,0.2); color: var(--white); align-self: flex-end; border-bottom-right-radius: 2px; border: 1px solid rgba(201,168,76,0.3); }
    
    .chat-input-area {
      padding: 0.8rem; border-top: 1px solid var(--border);
      display: flex; gap: 0.5rem; background: rgba(0,0,0,0.3);
    }
    .chat-input {
      flex: 1; background: none; border: none; color: var(--white);
      font-family: var(--font-body); font-size: 0.8rem; outline: none;
    }
    .chat-input::placeholder { color: var(--grey); }
    .chat-send {
      background: none; border: none; color: var(--gold);
      cursor: pointer; font-family: var(--font-mono); font-size: 0.7rem;
      text-transform: uppercase; letter-spacing: 0.1em; transition: color 0.2s;
    }
    .chat-send:hover { color: var(--gold-light); }
    .typing-indicator { font-size: 0.7rem; color: var(--grey); font-style: italic; display: none; align-self: flex-start; padding-left: 0.5rem; }

    /* ── ANIMATIONS ── */
    @keyframes fadeUp { from { opacity: 0; transform: translateY(25px); } to { opacity: 1; transform: translateY(0); } }
    @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }

    /* ── RESPONSIVE ── */
    @media (max-width: 900px) {
      nav { padding: 1.2rem 2rem; }
      #hero { grid-template-columns: 1fr; padding: 7rem 2rem 4rem; }
      .hero-right { align-items: flex-start; flex-direction: row; flex-wrap: wrap; }
      .stat-card { width: auto; flex: 1; min-width: 10rem; }
      section { padding: 4rem 2rem; }
      .about-grid { grid-template-columns: 1fr; gap: 3rem; }
      .skills-grid { grid-template-columns: 1fr 1fr; }
      .markets-grid { grid-template-columns: 1fr 1fr; }
      footer { flex-direction: column; gap: 1rem; text-align: center; }
      .ai-chat-window { bottom: 5rem; right: 1rem; width: calc(100vw - 2rem); }
    }
    @media (max-width: 560px) {
      .skills-grid { grid-template-columns: 1fr; }
      .markets-grid { grid-template-columns: 1fr 1fr; }
      .nav-links { display: none; }
    }
  </style>
</head>
<body>

  <div class="ambient-glow"></div>
  <div class="ambient-glow right"></div>

  <nav id="navbar">
    <div class="nav-logo">S. Srivastava</div>
    <ul class="nav-links">
      <li><a href="#about">About</a></li>
      <li><a href="#experience">Experience</a></li>
      <li><a href="#skills">Skills</a></li>
      <li><a href="#markets">Markets</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
  </nav>

  <section id="hero">
    <div class="hero-bg-text">Recruit</div>
    <div class="hero-left">
      <div class="hero-tag">Recruitment specialist · Workday Certified</div>
      <h1 class="hero-name">Shreyansh<br><em>Srivastava</em></h1>
      <p class="hero-title">// Full-Cycle Technical Recruitment · Global Markets</p>
      <div class="typewriter-container">
        &gt; <span id="typewriter-text"></span><span class="cursor"></span>
      </div>
      <div class="hero-ctas">
        <a href="#contact" class="btn-primary">Get in Touch</a>
        <a href="#experience" class="btn-secondary">View Experience</a>
      </div>
    </div>
    <div class="hero-right">
      <div class="stat-card">
        <div class="stat-number">4+</div>
        <div class="stat-label">Years of Experience</div>
      </div>
      <div class="stat-card">
        <div class="stat-number">F500</div>
        <div class="stat-label">Client Portfolio</div>
      </div>
      <div class="stat-card">
        <div class="stat-number">4</div>
        <div class="stat-label">Global Markets</div>
      </div>
    </div>
  </section>

  <section id="about">
    <div class="section-header reveal">
      <span class="section-num">01</span>
      <h2 class="section-title">About</h2>
      <div class="section-line"></div>
    </div>
    <div class="about-grid">
      <div class="about-bio reveal">
        <p>Results-driven <strong>Recruitment specialist</strong> with 4+ years of specialized experience in IT talent acquisition across <strong>global markets</strong> — UK, EU, US, and India.</p>
        <p>Proven track record delivering high-quality candidates for <strong>Fortune 500 clients</strong> in Investment Banking, Wealth Management, and Commercial Banking sectors. Expert in full-cycle recruitment, ATS/VMS platforms, and strategic sourcing methodologies.</p>
        <p><strong>Workday Certified</strong> with demonstrated success in building high-performing technical teams and maintaining exceptional client satisfaction rates. My approach blends sharp technical intuition with a deep understanding of people — matching not just skills, but potential.</p>
      </div>
      <div class="about-details reveal">
        <div class="detail-row"><span class="detail-key">Location</span><span class="detail-val">Noida, UP, India</span></div>
        <div class="detail-row"><span class="detail-key">Current Role</span><span class="detail-val">Sr. IT Recruiter @ iXceed Solutions</span></div>
        <div class="detail-row"><span class="detail-key">Email</span><span class="detail-val">Shreyanshcareer41@gmail.com</span></div>
        <div class="detail-row"><span class="detail-key">Phone</span><span class="detail-val">+91 7007997580</span></div>
        <div class="detail-row"><span class="detail-key">Certification</span><span class="detail-val"><span class="badge">Workday Certified</span></span></div>
        <div class="detail-row"><span class="detail-key">Education</span><span class="detail-val">BSc, PRSU Prayagraj</span></div>
        <div class="detail-row"><span class="detail-key">Availability</span><span class="detail-val"><span class="badge" style="color:#6ee7b7;border-color:rgba(110,231,183,0.3);background:rgba(110,231,183,0.08)">Open to Opportunities</span></span></div>
      </div>
    </div>
  </section>

  <section id="experience">
    <div class="section-header reveal">
      <span class="section-num">02</span>
      <h2 class="section-title">Experience</h2>
      <div class="section-line"></div>
    </div>
    <div class="exp-timeline">
      <div class="exp-item">
        <div class="exp-period">Aug 2025 – Present · 9 months</div>
        <div class="exp-role">Sr. IT Recruiter</div>
        <div class="exp-company">iXceed Solutions · London Area, UK</div>
        <div class="exp-desc">Leading end-to-end technical recruitment across the UK market, managing client relationships and delivering high-quality IT talent for enterprise-level mandates. Specializing in financial services technology roles with a focus on Investment Banking and FinTech.</div>
        <div class="exp-tags"><span class="exp-tag">UK Market</span><span class="exp-tag">FinTech</span><span class="exp-tag">Full-Cycle Recruitment</span><span class="exp-tag">Client Management</span></div>
      </div>
      <div class="exp-item">
        <div class="exp-period">Aug 2023 – Jun 2025 · 1 yr 11 mos</div>
        <div class="exp-role">Sr. Technical Recruiter</div>
        <div class="exp-company">The Crox Group · Illinois, US</div>
        <div class="exp-desc">Full life-cycle recruitment virtuoso deciphering diverse job descriptions for esteemed clients. Expertise across Investment Banking, Wealth Management, and Commercial Banks. Leveraged ATS and VMS tools to source, screen, and place top-tier IT professionals across contract and permanent roles.</div>
        <div class="exp-tags"><span class="exp-tag">US Market</span><span class="exp-tag">Investment Banking</span><span class="exp-tag">Wealth Management</span><span class="exp-tag">ATS / VMS</span><span class="exp-tag">Direct Clients</span></div>
      </div>
      <div class="exp-item">
        <div class="exp-period">Jun 2022 – Aug 2023 · 1 yr 3 mos</div>
        <div class="exp-role">Technical Recruiter</div>
        <div class="exp-company">The Crox Group</div>
        <div class="exp-desc">Shortlisted candidates, conducted phone and email outreach, and facilitated hiring for both contract and permanent IT positions. Worked with Direct Clients and Preferred Vendors. Scouted talent on Monster, Naukri, and LinkedIn using advanced Boolean search techniques.</div>
        <div class="exp-tags"><span class="exp-tag">Boolean Search</span><span class="exp-tag">LinkedIn Sourcing</span><span class="exp-tag">Contract & Perm</span><span class="exp-tag">Candidate Engagement</span></div>
      </div>
      <div class="exp-item">
        <div class="exp-period">Feb 2022 – Jun 2022 · 5 mos</div>
        <div class="exp-role">Talent Acquisition Trainee</div>
        <div class="exp-company">QUALTECH RPO · Noida, India</div>
        <div class="exp-desc">Utilized various sourcing strategies including job boards, social media, networking events, and referrals to engage both passive and active candidates. Built healthy talent pipelines for current and future client roles.</div>
        <div class="exp-tags"><span class="exp-tag">Sourcing Strategy</span><span class="exp-tag">Pipeline Building</span><span class="exp-tag">Passive Candidates</span></div>
      </div>
    </div>
  </section>

  <section id="skills">
    <div class="section-header reveal">
      <span class="section-num">03</span>
      <h2 class="section-title">Expertise</h2>
      <div class="section-line"></div>
    </div>
    <div class="skills-grid">
      <div class="skill-block">
        <div class="skill-block-icon">🎯</div>
        <div class="skill-block-title">Recruitment</div>
        <ul class="skill-list"><li>Full-Cycle Recruitment</li><li>Technical Screening</li><li>Candidate Negotiation</li><li>Offer Management</li><li>Dispute Resolution</li></ul>
      </div>
      <div class="skill-block">
        <div class="skill-block-icon">🛠️</div>
        <div class="skill-block-title">Tools & Platforms</div>
        <ul class="skill-list"><li>Workday (Certified)</li><li>ATS / VMS Platforms</li><li>LinkedIn Recruiter</li><li>Monster / Naukri</li><li>Boolean Search</li></ul>
      </div>
      <div class="skill-block">
        <div class="skill-block-icon">🏦</div>
        <div class="skill-block-title">Industry Focus</div>
        <ul class="skill-list"><li>Investment Banking</li><li>Wealth Management</li><li>Commercial Banking</li><li>FinTech</li><li>IT / Engineering</li></ul>
      </div>
      <div class="skill-block">
        <div class="skill-block-icon">🤖</div>
        <div class="skill-block-title">AI in HR</div>
        <ul class="skill-list"><li>Generative AI (Certified)</li><li>ChatGPT for HR</li><li>AI-Driven Sourcing</li><li>Human Capital Mgmt</li><li>AI Skills (Outskill)</li></ul>
      </div>
      <div class="skill-block">
        <div class="skill-block-icon">🤝</div>
        <div class="skill-block-title">Client Relations</div>
        <ul class="skill-list"><li>Fortune 500 Clients</li><li>Direct Client Mgmt</li><li>Preferred Vendor Lists</li><li>Stakeholder Alignment</li><li>SLA Management</li></ul>
      </div>
      <div class="skill-block">
        <div class="skill-block-icon">🌍</div>
        <div class="skill-block-title">Global Operations</div>
        <ul class="skill-list"><li>UK / EU Markets</li><li>US Market (Illinois)</li><li>India Operations</li><li>Cross-timezone Hiring</li><li>Compliance Awareness</li></ul>
      </div>
    </div>
  </section>

  <section id="markets">
    <div class="section-header reveal">
      <span class="section-num">04</span>
      <h2 class="section-title">Global Markets</h2>
      <div class="section-line"></div>
    </div>
    <div class="markets-grid">
      <div class="market-card"><div class="market-flag">🇬🇧</div><div class="market-name">United Kingdom</div><div class="market-sub">London · Active</div></div>
      <div class="market-card"><div class="market-flag">🇪🇺</div><div class="market-name">European Union</div><div class="market-sub">EU-wide · Experienced</div></div>
      <div class="market-card"><div class="market-flag">🇺🇸</div><div class="market-name">United States</div><div class="market-sub">Illinois · Experienced</div></div>
      <div class="market-card"><div class="market-flag">🇮🇳</div><div class="market-name">India</div><div class="market-sub">Noida · Based Here</div></div>
    </div>
  </section>

  <section id="contact">
    <div class="contact-inner reveal">
      <h2 class="contact-heading">Let's find<br>the <em>right fit.</em></h2>
      <p class="contact-sub">Whether you're a hiring manager looking for elite IT talent, or a professional exploring your next career move — I'm here to make the match. Let's talk.</p>
      <div class="contact-links">
        <a href="tel:+917007997580" class="contact-link">📞 +91 7007997580</a>
        <a href="mailto:Shreyanshcareer41@gmail.com" class="contact-link">✉ Email Me</a>
        <a href="https://www.linkedin.com/in/shreyansh-srivastava-47b2881aa" target="_blank" class="contact-link">🔗 LinkedIn</a>
      </div>
      <div class="contact-email">Shreyanshcareer41@gmail.com</div>
    </div>
  </section>

  <footer>
    <p>© 2026 Shreyansh Srivastava · Recruitment Specialist</p>
    <p>Noida, Uttar Pradesh, India</p>
  </footer>

  <div class="ai-widget-container">
    <div class="ai-chat-window" id="aiChatWindow">
      <div class="chat-header">
        <div class="chat-title">Shreyansh AI Agent</div>
        <button class="close-chat" id="closeChatBtn">×</button>
      </div>
      <div class="chat-body" id="chatBody">
        <div class="msg bot">Hello! I'm Shreyansh's AI assistant. Do you have any questions about his recruitment experience, skills, or how to get in touch?</div>
        <div class="typing-indicator" id="typingIndicator">Typing...</div>
      </div>
      <div class="chat-input-area">
        <input type="text" id="chatInput" class="chat-input" placeholder="Ask a question..." autocomplete="off">
        <button class="chat-send" id="chatSendBtn">Send</button>
      </div>
    </div>
    
    <button class="ai-btn" id="aiToggleBtn" aria-label="Open AI Assistant">
      <svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
        <path d="M12 2C6.48 2 2 6.48 2 12C2 17.52 6.48 22 12 22C17.52 22 22 17.52 22 12C22 6.48 17.52 2 12 2ZM13 17H11V15H13V17ZM13 13H11V7H13V13Z"/>
      </svg>
    </button>
  </div>

  <script>
    // ── NAVBAR SCROLL EFFECT ──
    window.addEventListener('scroll', () => {
      const nav = document.getElementById('navbar');
      if (window.scrollY > 50) {
        nav.classList.add('scrolled');
      } else {
        nav.classList.remove('scrolled');
      }
    });

    // ── TYPEWRITER ──
    const phrases = [
      "Connecting talent with opportunity.",
      "Fortune 500 recruitment specialist.",
      "4+ years · UK · EU · US · India.",
      "Workday Certified recruiter.",
      "Your next hire is one call away.",
    ];
    let pIdx = 0, cIdx = 0, deleting = false;
    const el = document.getElementById('typewriter-text');
    function type() {
      const current = phrases[pIdx];
      if (!deleting) {
        el.textContent = current.substring(0, cIdx + 1);
        cIdx++;
        if (cIdx === current.length) { deleting = true; setTimeout(type, 2000); return; }
      } else {
        el.textContent = current.substring(0, cIdx - 1);
        cIdx--;
        if (cIdx === 0) { deleting = false; pIdx = (pIdx + 1) % phrases.length; }
      }
      setTimeout(type, deleting ? 40 : 60);
    }
    setTimeout(type, 1500);

    // ── SCROLL REVEAL ──
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('visible'); } });
    }, { threshold: 0.12 });
    document.querySelectorAll('.reveal, .exp-item, .skill-block, .market-card').forEach(el => observer.observe(el));
    
    document.querySelectorAll('.skill-block').forEach((el, i) => el.style.transitionDelay = `${i * 0.08}s`);
    document.querySelectorAll('.market-card').forEach((el, i) => el.style.transitionDelay = `${i * 0.1}s`);
    document.querySelectorAll('.exp-item').forEach((el, i) => el.style.transitionDelay = `${i * 0.12}s`);

    // ── AI AGENT LOGIC ──
    const aiToggleBtn = document.getElementById('aiToggleBtn');
    const aiChatWindow = document.getElementById('aiChatWindow');
    const closeChatBtn = document.getElementById('closeChatBtn');
    const chatInput = document.getElementById('chatInput');
    const chatSendBtn = document.getElementById('chatSendBtn');
    const chatBody = document.getElementById('chatBody');
    const typingIndicator = document.getElementById('typingIndicator');

    // Toggle Window
    function toggleChat() { aiChatWindow.classList.toggle('active'); }
    aiToggleBtn.addEventListener('click', toggleChat);
    closeChatBtn.addEventListener('click', () => aiChatWindow.classList.remove('active'));

    // Chat Logic
    function addMessage(text, sender) {
      const msgDiv = document.createElement('div');
      msgDiv.classList.add('msg', sender);
      msgDiv.textContent = text;
      // Insert before typing indicator
      chatBody.insertBefore(msgDiv, typingIndicator);
      chatBody.scrollTop = chatBody.scrollHeight;
    }

    function getBotResponse(input) {
      const lowerInput = input.toLowerCase();
      if (lowerInput.includes('experience') || lowerInput.includes('work')) {
        return "Shreyansh has 4+ years of experience as a Sr. IT Recruiter, currently working at iXceed Solutions handling the UK market. Previously, he managed US markets for The Crox Group.";
      } else if (lowerInput.includes('skill') || lowerInput.includes('tool')) {
        return "He is Workday Certified, an expert in ATS/VMS platforms, Boolean Search, and specializes in placing IT professionals in Investment Banking and FinTech.";
      } else if (lowerInput.includes('contact') || lowerInput.includes('email') || lowerInput.includes('phone')) {
        return "You can reach Shreyansh at Shreyanshcareer41@gmail.com or call him at +91 7007997580.";
      } else if (lowerInput.includes('location') || lowerInput.includes('where')) {
        return "He is based in Noida, UP, India, but he handles global markets including the UK, EU, and US.";
      } else if (lowerInput.includes('hi') || lowerInput.includes('hello')) {
        return "Hello there! How can I help you learn more about Shreyansh's professional background?";
      } else {
        return "Thanks for reaching out! I'm still learning, but you can find all of Shreyansh's detailed experience in the portfolio sections above, or email him directly for specifics!";
      }
    }

    function handleSend() {
      const text = chatInput.value.trim();
      if (!text) return;
      
      addMessage(text, 'user');
      chatInput.value = '';
      
      // Show typing indicator
      typingIndicator.style.display = 'block';
      chatBody.scrollTop = chatBody.scrollHeight;

      // Simulate network delay
      setTimeout(() => {
        typingIndicator.style.display = 'none';
        const response = getBotResponse(text);
        addMessage(response, 'bot');
      }, 1000 + Math.random() * 1000);
    }

    chatSendBtn.addEventListener('click', handleSend);
    chatInput.addEventListener('keypress', (e) => {
      if (e.key === 'Enter') handleSend();
    });
  </script>
</body>
</html>
