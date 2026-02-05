<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Nima Ansari — Data × Film × Software</title>

  <style>
    :root{
      --bg: #07080c;
      --bg2:#0b0f18;
      --card:#0e1422cc;
      --stroke:#27324a;
      --text:#e9eefc;
      --muted:#a8b3cf;
      --muted2:#7e8bb0;
      --accent:#7c5cff;
      --accent2:#22d3ee;
      --good:#22c55e;
      --shadow: 0 18px 60px rgba(0,0,0,.55);
      --radius: 18px;
      --radius2: 26px;
      --max: 1080px;
    }

    /* Light theme (optional toggle) */
    [data-theme="light"]{
      --bg:#f6f7fb;
      --bg2:#ffffff;
      --card:#ffffffcc;
      --stroke:#e4e7f2;
      --text:#0b1020;
      --muted:#3f4b6a;
      --muted2:#60709a;
      --shadow: 0 18px 60px rgba(12,18,35,.12);
    }

    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0;
      font-family: ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, Helvetica, Arial;
      color:var(--text);
      background:
        radial-gradient(1200px 700px at 15% 10%, rgba(124,92,255,.22), transparent 60%),
        radial-gradient(1000px 600px at 85% 20%, rgba(34,211,238,.18), transparent 55%),
        radial-gradient(900px 600px at 40% 95%, rgba(124,92,255,.14), transparent 60%),
        linear-gradient(180deg, var(--bg), var(--bg2));
      overflow-x:hidden;
    }

    a{color:inherit; text-decoration:none}
    .wrap{max-width:var(--max); margin:0 auto; padding:28px 18px 80px}
    .nav{
      position:sticky; top:0; z-index:50;
      backdrop-filter: blur(12px);
      background: linear-gradient(180deg, rgba(10,12,18,.75), rgba(10,12,18,.35));
      border-bottom:1px solid rgba(255,255,255,.06);
    }
    [data-theme="light"] .nav{
      background: linear-gradient(180deg, rgba(255,255,255,.78), rgba(255,255,255,.55));
      border-bottom:1px solid rgba(0,0,0,.06);
    }

    .nav-inner{
      max-width:var(--max);
      margin:0 auto;
      padding:14px 18px;
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:14px;
    }

    .brand{
      display:flex; align-items:center; gap:10px;
      font-weight:700;
      letter-spacing:.2px;
    }
    .brand .dot{
      width:10px;height:10px;border-radius:999px;
      background: linear-gradient(135deg, var(--accent), var(--accent2));
      box-shadow:0 0 0 4px rgba(124,92,255,.12);
    }

    .nav-links{
      display:flex; gap:14px; align-items:center; flex-wrap:wrap;
      font-size:14px;
      color:var(--muted);
    }
    .nav-links a{
      padding:8px 10px;
      border:1px solid transparent;
      border-radius:999px;
      transition:.2s ease;
    }
    .nav-links a:hover{
      color:var(--text);
      border-color: rgba(124,92,255,.28);
      background: rgba(124,92,255,.10);
    }

    .btn{
      appearance:none;border:1px solid rgba(255,255,255,.10);
      background: rgba(255,255,255,.04);
      color:var(--text);
      border-radius:999px;
      padding:10px 12px;
      font-size:14px;
      display:inline-flex;
      align-items:center;
      gap:8px;
      cursor:pointer;
      transition:.2s ease;
      box-shadow: 0 10px 25px rgba(0,0,0,.18);
      user-select:none;
      white-space:nowrap;
    }
    [data-theme="light"] .btn{
      border-color: rgba(0,0,0,.08);
      background: rgba(0,0,0,.03);
      box-shadow: 0 10px 25px rgba(18,22,38,.10);
    }
    .btn:hover{
      transform: translateY(-1px);
      border-color: rgba(124,92,255,.35);
      background: rgba(124,92,255,.12);
    }
    .btn.primary{
      border-color: rgba(124,92,255,.35);
      background: linear-gradient(135deg, rgba(124,92,255,.95), rgba(34,211,238,.75));
      color:#07080c;
      font-weight:700;
    }
    .btn.primary:hover{filter:saturate(1.05) brightness(1.02)}

    .hero{
      padding:48px 0 22px;
      display:grid;
      grid-template-columns: 1.25fr .75fr;
      gap:22px;
      align-items:center;
    }
    @media (max-width: 880px){
      .hero{grid-template-columns:1fr; padding-top:28px}
    }

    .title{
      margin:0;
      font-size: clamp(38px, 5vw, 64px);
      line-height:1.04;
      letter-spacing:-.8px;
      display:flex;
      align-items:center;
      gap:14px;
      justify-content:flex-start;
    }
    /* Center option if you want it centered */
    .title.center{
      justify-content:center;
      text-align:center;
    }
    .icon{
      display:inline-grid;
      place-items:center;
      width:54px;height:54px;
      border-radius:18px;
      background: rgba(124,92,255,.14);
      border:1px solid rgba(124,92,255,.22);
      box-shadow: 0 16px 40px rgba(0,0,0,.35);
      font-size:28px;
    }
    [data-theme="light"] .icon{
      box-shadow: 0 16px 40px rgba(12,18,35,.12);
    }

    .kicker{
      margin:14px 0 0;
      color:var(--muted);
      font-size: 16px;
      line-height:1.6;
      max-width: 62ch;
    }

    .tagline{
      margin:12px 0 0;
      font-weight:700;
      font-size: 18px;
      letter-spacing:.2px;
    }
    .tagline .x{
      color:var(--muted2);
      font-weight:600;
    }
    .tagline .glow{
      background: linear-gradient(135deg, var(--accent), var(--accent2));
      -webkit-background-clip:text;
      background-clip:text;
      color:transparent;
    }

    .hero-card{
      border-radius: var(--radius2);
      background: linear-gradient(180deg, rgba(255,255,255,.06), rgba(255,255,255,.02));
      border:1px solid rgba(255,255,255,.08);
      box-shadow: var(--shadow);
      padding:18px;
      position:relative;
      overflow:hidden;
    }
    [data-theme="light"] .hero-card{
      background: linear-gradient(180deg, rgba(0,0,0,.03), rgba(0,0,0,.01));
      border-color: rgba(0,0,0,.06);
    }

    .hero-card::before{
      content:"";
      position:absolute; inset:-2px;
      background: radial-gradient(600px 180px at 30% 0%, rgba(124,92,255,.18), transparent 60%),
                  radial-gradient(460px 220px at 90% 30%, rgba(34,211,238,.14), transparent 60%);
      pointer-events:none;
    }

    .chip-row{display:flex; flex-wrap:wrap; gap:10px; margin-top:14px; position:relative}
    .chip{
      padding:8px 10px;
      border-radius:999px;
      border:1px solid rgba(255,255,255,.10);
      background: rgba(0,0,0,.18);
      color:var(--muted);
      font-size:12px;
      letter-spacing:.2px;
    }
    [data-theme="light"] .chip{
      background: rgba(255,255,255,.65);
      border-color: rgba(0,0,0,.08);
    }

    .meta{
      margin-top:14px;
      display:grid;
      gap:10px;
      position:relative;
    }
    .meta .row{
      display:flex; align-items:center; justify-content:space-between; gap:10px;
      padding:10px 12px;
      border-radius: 14px;
      border:1px solid rgba(255,255,255,.08);
      background: rgba(0,0,0,.12);
      color:var(--muted);
      font-size:13px;
    }
    [data-theme="light"] .meta .row{
      background: rgba(255,255,255,.65);
      border-color: rgba(0,0,0,.06);
    }
    .meta .row b{color:var(--text); font-weight:700}

    .section{
      margin-top:34px;
      display:grid;
      gap:14px;
    }

    .section h2{
      margin:0;
      font-size: 18px;
      letter-spacing:.3px;
      display:flex; align-items:center; gap:10px;
    }
    .section h2 .badge{
      font-size:12px;
      padding:6px 10px;
      border-radius:999px;
      background: rgba(124,92,255,.12);
      border:1px solid rgba(124,92,255,.22);
      color:var(--muted);
    }

    .grid{
      display:grid;
      grid-template-columns: repeat(12, 1fr);
      gap:14px;
    }
    .card{
      grid-column: span 6;
      border-radius: var(--radius);
      background: var(--card);
      border:1px solid rgba(255,255,255,.10);
      box-shadow: var(--shadow);
      padding:16px;
      position:relative;
      overflow:hidden;
    }
    [data-theme="light"] .card{
      border-color: rgba(0,0,0,.07);
    }
    .card h3{
      margin:0;
      font-size:16px;
      letter-spacing:.2px;
      display:flex; align-items:center; justify-content:space-between; gap:10px;
    }
    .card p{
      margin:10px 0 0;
      color:var(--muted);
      line-height:1.6;
      font-size:14px;
    }
    .card .mini{
      margin-top:10px;
      display:flex; gap:8px; flex-wrap:wrap;
    }
    .pill{
      font-size:12px;
      padding:6px 10px;
      border-radius:999px;
      border:1px solid rgba(255,255,255,.10);
      color:var(--muted);
      background: rgba(0,0,0,.12);
    }
    [data-theme="light"] .pill{
      background: rgba(255,255,255,.75);
      border-color: rgba(0,0,0,.08);
    }

    .card .topline{
      color:var(--muted2);
      font-size:12px;
      margin-top:6px;
    }

    .card .links{
      margin-top:12px;
      display:flex;
      gap:10px;
      flex-wrap:wrap;
    }
    .link{
      font-size:13px;
      color:var(--text);
      opacity:.9;
      padding:8px 10px;
      border-radius:999px;
      border:1px solid rgba(255,255,255,.10);
      background: rgba(255,255,255,.03);
      transition:.2s ease;
    }
    [data-theme="light"] .link{
      background: rgba(0,0,0,.03);
      border-color: rgba(0,0,0,.08);
    }
    .link:hover{
      transform: translateY(-1px);
      border-color: rgba(34,211,238,.30);
      background: rgba(34,211,238,.10);
    }

    @media (max-width: 880px){
      .card{grid-column: span 12;}
    }

    .timeline{
      border-radius: var(--radius2);
      border:1px solid rgba(255,255,255,.10);
      background: linear-gradient(180deg, rgba(255,255,255,.05), rgba(255,255,255,.02));
      box-shadow: var(--shadow);
      padding:16px;
    }
    [data-theme="light"] .timeline{
      border-color: rgba(0,0,0,.07);
    }

    .t-item{
      display:grid;
      grid-template-columns: 160px 1fr;
      gap:14px;
      padding:14px 10px;
      border-bottom: 1px solid rgba(255,255,255,.06);
    }
    [data-theme="light"] .t-item{
      border-bottom-color: rgba(0,0,0,.06);
    }
    .t-item:last-child{border-bottom:none}
    .t-date{
      color:var(--muted2);
      font-size:12px;
      line-height:1.3;
    }
    .t-body h3{
      margin:0;
      font-size:15px;
    }
    .t-body .role{
      margin-top:6px;
      color:var(--muted);
      font-size:13px;
    }
    .t-body ul{
      margin:10px 0 0;
      padding-left:18px;
      color:var(--muted);
      line-height:1.6;
      font-size:14px;
    }
    .t-body li{margin:6px 0}

    @media(max-width:760px){
      .t-item{grid-template-columns:1fr}
      .t-date{order:2}
    }

    .footer{
      margin-top:34px;
      border-radius: var(--radius2);
      border:1px solid rgba(255,255,255,.10);
      background: linear-gradient(135deg, rgba(124,92,255,.14), rgba(34,211,238,.10));
      box-shadow: var(--shadow);
      padding:18px;
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:12px;
      flex-wrap:wrap;
    }
    [data-theme="light"] .footer{
      border-color: rgba(0,0,0,.07);
    }

    .contact{
      display:flex;
      flex-wrap:wrap;
      gap:10px;
      align-items:center;
      color:var(--muted);
    }

    /* Reveal animations */
    .reveal{
      opacity:0;
      transform: translateY(14px);
      transition: opacity .7s ease, transform .7s ease;
    }
    .reveal.on{
      opacity:1;
      transform: translateY(0);
    }

    /* Tiny toast */
    .toast{
      position: fixed;
      left: 50%;
      bottom: 18px;
      transform: translateX(-50%);
      padding: 10px 12px;
      border-radius: 999px;
      border:1px solid rgba(255,255,255,.12);
      background: rgba(0,0,0,.65);
      backdrop-filter: blur(10px);
      color: var(--text);
      font-size: 13px;
      opacity:0;
      pointer-events:none;
      transition: opacity .2s ease, transform .2s ease;
      z-index:100;
    }
    [data-theme="light"] .toast{
      background: rgba(255,255,255,.85);
      border-color: rgba(0,0,0,.10);
    }
    .toast.show{
      opacity:1;
      transform: translateX(-50%) translateY(-2px);
    }
  </style>
</head>

<body>
  <!-- Top nav -->
  <header class="nav">
    <div class="nav-inner">
      <div class="brand">
        <span class="dot"></span>
        <span>Nima Ansari</span>
      </div>

      <nav class="nav-links">
        <a href="#work">Selected Works</a>
        <a href="#experience">Experience</a>
        <a href="#toolkit">Toolkit</a>
        <a href="#contact">Contact</a>
      </nav>

      <div style="display:flex; gap:10px; align-items:center;">
        <button class="btn" id="themeBtn" aria-label="Toggle theme">🌗 Theme</button>
        <a class="btn primary" href="#contact">🎬 Let’s build</a>
      </div>
    </div>
  </header>

  <main class="wrap">
    <!-- HERO -->
    <section class="hero">
      <div class="reveal">
        <!-- Add class="center" if you want the title centered -->
        <h1 class="title" id="top">
          <span class="icon">🎬</span>
          Nima Ansari
        </h1>

        <div class="tagline">
          <span class="x">Data × Film × Software —</span>
          <span class="glow">building tools that tell stories.</span>
        </div>

        <p class="kicker">
          I build systems the way films are made: with intention, structure, and audience in mind.
          My work sits at the intersection of <b>machine learning</b>, <b>data engineering</b>, and <b>visual storytelling</b> —
          turning complexity into narrative and decision into action. :contentReference[oaicite:1]{index=1}
        </p>

        <div class="chip-row">
          <span class="chip">Austin, TX</span>
          <span class="chip">B.S. Data Science (UT Austin)</span>
          <span class="chip">ML · Backend · Data</span>
          <span class="chip">Film / Creative Systems</span>
        </div>

        <div style="margin-top:16px; display:flex; gap:10px; flex-wrap:wrap;">
          <button class="btn" id="copyEmailBtn">📧 Copy email</button>
          <a class="btn" href="#work">🎞 View work</a>
          <a class="btn" href="https://www.linkedin.com/in/nima-ansari" target="_blank" rel="noreferrer">💼 LinkedIn</a>
          <!-- Replace with your real GitHub -->
          <a class="btn" href="#" id="githubLink" target="_blank" rel="noreferrer">🐙 GitHub</a>
        </div>
      </div>

      <aside class="hero-card reveal">
        <div style="position:relative">
          <img
            src="https://media3.giphy.com/media/z2YiftHRaPbWw/giphy.gif"
            alt="Film vibe gif"
            style="width:100%; border-radius:18px; border:1px solid rgba(255,255,255,.10); display:block;"
          />
          <div class="meta">
            <div class="row">
              <span>Focus</span>
              <b>ML + Data Systems</b>
            </div>
            <div class="row">
              <span>Current</span>
              <b>Research + Engineering</b>
            </div>
            <div class="row">
              <span>Style</span>
              <b>Story-first builds</b>
            </div>
          </div>

          <div style="margin-top:12px; color:var(--muted); font-size:13px; line-height:1.6;">
            “Code becomes a medium. Data becomes narrative.”
          </div>
        </div>
      </aside>
    </section>

    <!-- Director's Statement -->
    <section class="section reveal" id="statement">
      <h2>🎥 Director’s Statement <span class="badge">how I build</span></h2>
      <div class="card" style="grid-column: span 12;">
        <p style="margin-top:0">
          I build software with the same discipline that makes great films work:
          a clear problem, a deliberate structure, and a tight feedback loop with real users.
          I’ve shipped backend systems for multi-user collaboration, built analytics dashboards for research,
          and applied ML pipelines to real datasets — from <b>124+ multimodal audio sessions</b>
          to <b>1,500+ semiconductor signals</b>. :contentReference[oaicite:2]{index=2}
        </p>
        <p>
          I’m especially interested in projects where engineering meets storytelling:
          developer tools that feel cinematic, data products that explain themselves, and AI systems
          that reduce complexity instead of adding it.
        </p>
      </div>
    </section>

    <!-- Selected Works -->
    <section class="section" id="work">
      <h2 class="reveal">🎞 Selected Works <span class="badge">projects</span></h2>

      <div class="grid">
        <article class="card reveal">
          <h3>
            H-E-B Shared Shopping Lists + Split-Bill Backend
            <span style="color:var(--muted2); font-size:12px;">(Intern)</span>
          </h3>
          <div class="topline">Real-time collaboration · multi-user billing · backend services</div>
          <p>
            Built backend services for real-time shared shopping lists with a split-bill system supporting
            <b>4+ users</b>. Queried and analyzed <b>500+ user interaction records</b> to inform implementation strategy
            for a <b>10+ developer</b> team. :contentReference[oaicite:3]{index=3}
          </p>
          <div class="mini">
            <span class="pill">Python</span><span class="pill">React</span><span class="pill">SQL</span><span class="pill">Backend</span>
          </div>
          <div class="links">
            <!-- Replace # with real links if/when you have them -->
            <a class="link" href="#" target="_blank" rel="noreferrer">Repo</a>
            <a class="link" href="#" target="_blank" rel="noreferrer">Case Study</a>
          </div>
        </article>

        <article class="card reveal">
          <h3>
            Matchmaker AI (Retrieval + Ranking)
            <span style="color:var(--muted2); font-size:12px;">(Project)</span>
          </h3>
          <div class="topline">Vector search + metadata + multi-stage ranking</div>
          <p>
            Evaluated a multi-stage retrieval and ranking workflow combining vector similarity
            (Pinecone embeddings) with structured metadata to improve match relevance. :contentReference[oaicite:4]{index=4}
          </p>
          <div class="mini">
            <span class="pill">React</span><span class="pill">Node.js</span><span class="pill">Firestore</span><span class="pill">Pinecone</span>
          </div>
          <div class="links">
            <a class="link" href="#" target="_blank" rel="noreferrer">Repo</a>
            <a class="link" href="#" target="_blank" rel="noreferrer">Demo</a>
          </div>
        </article>

        <article class="card reveal">
          <h3>
            UT Austin Infant-Parent Interaction Analytics
            <span style="color:var(--muted2); font-size:12px;">(Research)</span>
          </h3>
          <div class="topline">EDA + dashboards + vocal-feature KPIs</div>
          <p>
            Analyzed <b>124+ multimodal audio datasets</b> with Pandas/NumPy to identify behavioral and acoustic patterns.
            Built a Tableau dashboard visualizing session volume, vocal-feature KPIs, and time-series trends. :contentReference[oaicite:5]{index=5}
          </p>
          <div class="mini">
            <span class="pill">Python</span><span class="pill">Pandas</span><span class="pill">NumPy</span><span class="pill">Tableau</span>
          </div>
          <div class="links">
            <a class="link" href="#" target="_blank" rel="noreferrer">Write-up</a>
          </div>
        </article>

        <article class="card reveal">
          <h3>
            Semiconductor Defect Detection Pipelines
            <span style="color:var(--muted2); font-size:12px;">(Research)</span>
          </h3>
          <div class="topline">Rare-event detection · feature extraction · automation</div>
          <p>
            Analyzed <b>1,500+ chip-level EDS signals</b> with statistical analysis and ML pipelines to identify defect patterns.
            Automated preprocessing + feature extraction, cutting defect identification time by <b>~23%</b>. :contentReference[oaicite:6]{index=6}
          </p>
          <div class="mini">
            <span class="pill">ML Pipelines</span><span class="pill">Statistical Analysis</span><span class="pill">Automation</span>
          </div>
          <div class="links">
            <a class="link" href="#" target="_blank" rel="noreferrer">Summary</a>
          </div>
        </article>

        <article class="card reveal" style="grid-column: span 12;">
          <h3>
            DarkBrickProductions — Film as a System
            <span style="color:var(--muted2); font-size:12px;">(Creative)</span>
          </h3>
          <div class="topline">Long-form storytelling · production pipelines · audience building</div>
          <p>
            Built an end-to-end creative production pipeline over years of LEGO stop-motion filmmaking:
            writing, shooting, editing, and iterating with an audience. This is where my “story-first engineering”
            mindset was born — the habit of designing for pacing, clarity, and impact.
          </p>
          <div class="mini">
            <span class="pill">Storytelling</span><span class="pill">Creative Tooling</span><span class="pill">Production</span>
          </div>
          <div class="links">
            <a class="link" href="#" target="_blank" rel="noreferrer">Watch</a>
            <a class="link" href="#" target="_blank" rel="noreferrer">Behind the Scenes</a>
          </div>
        </article>
      </div>
    </section>

    <!-- Experience Timeline -->
    <section class="section" id="experience">
      <h2 class="reveal">🧭 Experience <span class="badge">timeline</span></h2>

      <div class="timeline reveal">
        <div class="t-item">
          <div class="t-date">Aug 2025 — Dec 2025<br/>Austin, TX</div>
          <div class="t-body">
            <h3>H-E-B — Software Engineering Intern (Backend & Data Analytics)</h3>
            <div class="role">Built multi-user, real-time backend systems + user behavior analysis. :contentReference[oaicite:7]{index=7}</div>
            <ul>
              <li>Backend services for shared shopping lists + split-bill across <b>4+ users</b> (Python & React).</li>
              <li>SQL analysis on <b>500+ interaction records</b> to guide implementation strategy for <b>10+ devs</b>.</li>
            </ul>
          </div>
        </div>

        <div class="t-item">
          <div class="t-date">Aug 2025 — Dec 2025<br/>Austin, TX</div>
          <div class="t-body">
            <h3>UT Austin — AI & ML Research Assistant (Infant-Parent Interactions)</h3>
            <div class="role">EDA + dashboards for multimodal behavioral research. :contentReference[oaicite:8]{index=8}</div>
            <ul>
              <li>Analyzed <b>124+ audio datasets</b> with Pandas/NumPy to identify behavioral/acoustic patterns.</li>
              <li>Built Tableau dashboards for session volume, vocal KPIs, and time-series interaction trends.</li>
            </ul>
          </div>
        </div>

        <div class="t-item">
          <div class="t-date">May 2025 — Aug 2025<br/>Dallas, TX</div>
          <div class="t-body">
            <h3>Lone Star Neurology — Data Engineering Intern</h3>
            <div class="role">Dashboards + RESTful APIs for commerce-like healthcare flows. :contentReference[oaicite:9]{index=9}</div>
            <ul>
              <li>Power BI dashboard integrating patient/prescription/transaction systems for KPI + YoY analysis.</li>
              <li>Designed REST APIs + data models supporting cart + checkout across <b>20,000 use cases</b>.</li>
            </ul>
          </div>
        </div>

        <div class="t-item">
          <div class="t-date">Aug 2024 — Dec 2024<br/>Seoul, KR</div>
          <div class="t-body">
            <h3>Samsung Semiconductor × Hanyang University — Undergraduate Research Intern</h3>
            <div class="role">Stat + ML pipelines for defect pattern detection. :contentReference[oaicite:10]{index=10}</div>
            <ul>
              <li>Analyzed <b>1,500+ EDS signals</b> to identify defect patterns and support rare-event detection.</li>
              <li>Automated preprocessing + feature extraction, improving cycle time by <b>~23%</b>.</li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <!-- Toolkit -->
    <section class="section" id="toolkit">
      <h2 class="reveal">🛠 Production Toolkit <span class="badge">skills</span></h2>

      <div class="grid">
        <div class="card reveal">
          <h3>Languages</h3>
          <p>Python · Java · C++ · JavaScript · HTML · CSS · R · Kotlin · SQL · Bash :contentReference[oaicite:11]{index=11}</p>
        </div>
        <div class="card reveal">
          <h3>Technologies</h3>
          <p>PostgreSQL · React · Django · Linux :contentReference[oaicite:12]{index=12}</p>
        </div>
      </div>
    </section>

    <!-- Contact -->
    <section class="section" id="contact">
      <h2 class="reveal">📬 Contact <span class="badge">reach me</span></h2>

      <div class="footer reveal">
        <div class="contact">
          <span>📧 <b id="emailText">nima.ansari.4448@utexas.edu</b></span>
          <span>•</span>
          <span>📱 (469) 536-7236</span>
          <span>•</span>
          <span>📍 Austin, TX</span>
        </div>

        <div style="display:flex; gap:10px; flex-wrap:wrap;">
          <button class="btn" id="copyEmailBtn2">Copy email</button>
          <a class="btn" href="https://www.linkedin.com/in/nima-ansari" target="_blank" rel="noreferrer">LinkedIn</a>
          <!-- Replace with your real GitHub + portfolio -->
          <a class="btn" href="#" id="portfolioLink" target="_blank" rel="noreferrer">Portfolio</a>
          <a class="btn" href="#" id="githubLink2" target="_blank" rel="noreferrer">GitHub</a>
        </div>
      </div>
    </section>

    <div style="margin-top:22px; color:var(--muted2); font-size:12px;">
      Built with intention. Shot on code. 🎬
    </div>
  </main>

  <div class="toast" id="toast">Copied.</div>

  <script>
    // ====== CONFIG (replace these links) ======
    const LINKS = {
      github: "https://github.com/your-username",    // <-- change
      portfolio: "https://yourusername.github.io"    // <-- change
    };

    // Apply link placeholders
    document.getElementById("githubLink").href = LINKS.github;
    document.getElementById("githubLink2").href = LINKS.github;
    document.getElementById("portfolioLink").href = LINKS.portfolio;

    // ====== Smooth scroll for internal anchors ======
    document.querySelectorAll('a[href^="#"]').forEach(a => {
      a.addEventListener("click", (e) => {
        const id = a.getAttribute("href");
        const el = document.querySelector(id);
        if (!el) return;
        e.preventDefault();
        el.scrollIntoView({ behavior: "smooth", block: "start" });
      });
    });

    // ====== Reveal on scroll ======
    const io = new IntersectionObserver((entries) => {
      entries.forEach(ent => {
        if(ent.isIntersecting) ent.target.classList.add("on");
      });
    }, { threshold: 0.12 });

    document.querySelectorAll(".reveal").forEach(el => io.observe(el));

    // ====== Theme toggle ======
    const themeBtn = document.getElementById("themeBtn");
    const root = document.documentElement;

    const savedTheme = localStorage.getItem("theme");
    if (savedTheme) root.setAttribute("data-theme", savedTheme);

    themeBtn.addEventListener("click", () => {
      const current = root.getAttribute("data-theme");
      const next = current === "light" ? "" : "light";
      if (next) root.setAttribute("data-theme", next);
      else root.removeAttribute("data-theme");
      localStorage.setItem("theme", next || "");
      toast(next ? "Light mode" : "Dark mode");
    });

    // ====== Copy email buttons ======
    const email = "nima.ansari.4448@utexas.edu";
    const copy = async () => {
      try{
        await navigator.clipboard.writeText(email);
        toast("Email copied");
      }catch{
        // fallback
        const ta = document.createElement("textarea");
        ta.value = email;
        document.body.appendChild(ta);
        ta.select();
        document.execCommand("copy");
        document.body.removeChild(ta);
        toast("Email copied");
      }
    };

    document.getElementById("copyEmailBtn").addEventListener("click", copy);
    document.getElementById("copyEmailBtn2").addEventListener("click", copy);

    // ====== Toast helper ======
    let toastTimer;
    function toast(msg){
      const el = document.getElementById("toast");
      el.textContent = msg;
      el.classList.add("show");
      clearTimeout(toastTimer);
      toastTimer = setTimeout(()=> el.classList.remove("show"), 1400);
    }
  </script>
</body>
</html>
