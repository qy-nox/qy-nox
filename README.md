<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
  <title>QY-NOX | Mahfuj · Cyber Forge</title>
  <!-- Google Fonts & Font Awesome -->
  <link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <!-- AOS Library (scroll animations) -->
  <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background: radial-gradient(circle at 20% 30%, #0a0f1e, #03050b);
      font-family: 'Space Grotesk', monospace;
      color: #e2e8ff;
      line-height: 1.5;
      scroll-behavior: smooth;
      overflow-x: hidden;
    }

    /* animated grain texture */
    body::before {
      content: "";
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 400 400' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noiseFilter'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.65' numOctaves='1' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noiseFilter)' opacity='0.04'/%3E%3C/svg%3E");
      pointer-events: none;
      z-index: 999;
      opacity: 0.2;
    }

    /* custom scrollbar */
    ::-webkit-scrollbar {
      width: 6px;
    }
    ::-webkit-scrollbar-track {
      background: #0b1120;
    }
    ::-webkit-scrollbar-thumb {
      background: #2dd4bf;
      border-radius: 8px;
    }

    .container {
      max-width: 1300px;
      margin: 0 auto;
      padding: 2rem 1.5rem;
      position: relative;
      z-index: 2;
    }

    /* GLASS CARD EFFECT */
    .glass-card {
      background: rgba(12, 20, 35, 0.45);
      backdrop-filter: blur(12px);
      border: 1px solid rgba(45, 212, 191, 0.25);
      border-radius: 2.5rem;
      box-shadow: 0 20px 35px -12px rgba(0,0,0,0.5), inset 0 1px 0 rgba(255,255,255,0.05);
      transition: all 0.3s ease;
    }

    .glass-card:hover {
      border-color: rgba(45, 212, 191, 0.6);
      box-shadow: 0 25px 40px -12px rgba(0, 255, 255, 0.15);
    }

    /* header neon pulse */
    .neon-text {
      text-shadow: 0 0 5px #2dd4bf, 0 0 12px #0f766e;
      font-weight: 600;
    }

    .badge-glow {
      background: linear-gradient(135deg, #1e293b, #0f172a);
      padding: 0.3rem 0.9rem;
      border-radius: 40px;
      font-size: 0.8rem;
      font-weight: 500;
      border-left: 2px solid #2dd4bf;
      letter-spacing: 0.5px;
    }

    /* animated grid background for sections */
    .grid-bg {
      position: relative;
    }
    .grid-bg::after {
      content: "";
      position: absolute;
      inset: 0;
      background-image: linear-gradient(#2dd4bf10 1px, transparent 1px), linear-gradient(90deg, #2dd4bf10 1px, transparent 1px);
      background-size: 40px 40px;
      pointer-events: none;
      border-radius: inherit;
    }

    /* tech badge row */
    .tech-stack i {
      font-size: 2.5rem;
      margin: 0 0.5rem;
      transition: transform 0.2s, filter 0.2s;
      filter: drop-shadow(0 0 4px #2dd4bf66);
    }
    .tech-stack i:hover {
      transform: translateY(-5px);
      filter: drop-shadow(0 0 12px #2dd4bf);
    }

    /* project cards */
    .project-card {
      background: rgba(2, 6, 23, 0.7);
      backdrop-filter: blur(4px);
      border-radius: 1.8rem;
      padding: 1.4rem;
      border: 1px solid rgba(45,212,191,0.3);
      transition: all 0.25s cubic-bezier(0.2, 0.9, 0.4, 1.1);
    }
    .project-card:hover {
      transform: translateY(-6px);
      border-color: #2dd4bf;
      background: rgba(15, 25, 45, 0.8);
      box-shadow: 0 20px 30px -15px rgba(0,255,200,0.2);
    }

    .status-badge {
      font-size: 0.7rem;
      background: #0f212e;
      padding: 0.2rem 0.7rem;
      border-radius: 30px;
      color: #7ee0d5;
    }

    /* stat grid */
    .stat-numbers {
      display: flex;
      justify-content: center;
      gap: 2rem;
      flex-wrap: wrap;
    }
    .stat-item {
      text-align: center;
      background: rgba(0,0,0,0.4);
      border-radius: 2rem;
      padding: 0.5rem 1.5rem;
      backdrop-filter: blur(4px);
    }
    .glow-button {
      background: linear-gradient(95deg, #0f172a, #0a0f1a);
      border: 1px solid #2dd4bf;
      border-radius: 40px;
      padding: 0.6rem 1.4rem;
      transition: 0.2s;
      display: inline-flex;
      align-items: center;
      gap: 8px;
      font-weight: 500;
    }
    .glow-button:hover {
      background: #2dd4bf20;
      box-shadow: 0 0 12px #2dd4bf60;
      transform: scale(1.02);
    }

    footer {
      border-top: 1px dashed #2dd4bf40;
    }

    @keyframes float {
      0% { transform: translateY(0px); }
      100% { transform: translateY(-5px); }
    }

    .floating {
      animation: float 3s ease-in-out infinite;
    }

    /* responsive */
    @media (max-width: 760px) {
      .container {
        padding: 1rem;
      }
      .tech-stack i {
        font-size: 1.8rem;
        margin: 0 0.3rem;
      }
    }
  </style>
</head>
<body>

<div class="container">
  
  <!-- header + animated signature -->
  <div class="glass-card" style="padding: 2rem 1.8rem; margin-bottom: 2rem;" data-aos="fade-up" data-aos-duration="800">
    <div style="display: flex; flex-wrap: wrap; justify-content: space-between; align-items: center;">
      <div>
        <h1 style="font-size: 3rem; letter-spacing: -1px;"><span class="neon-text">MAHFUJ</span> <span style="color:#94a3b8;">// QY-NOX</span></h1>
        <div style="display: flex; flex-wrap: wrap; gap: 12px; margin: 1rem 0 0.5rem;">
          <span class="badge-glow"><i class="fas fa-microchip"></i> Computer Technology Engineer</span>
          <span class="badge-glow"><i class="fas fa-robot"></i> AI Automation Specialist</span>
          <span class="badge-glow"><i class="fas fa-chart-line"></i> Crypto Analyst</span>
        </div>
        <p style="max-width: 550px; margin-top: 1rem; color: #b9c7d9;">
          <i class="fas fa-terminal"></i> Building autonomous agents & intelligent pipelines · 3rd Sem Diploma with a vision for next-gen automation.
        </p>
      </div>
      <div class="floating">
        <i class="fas fa-code-branch" style="font-size: 4rem; opacity: 0.7; color: #2dd4bf;"></i>
      </div>
    </div>
    <div style="margin-top: 1.8rem; display: flex; gap: 1rem; flex-wrap: wrap;">
      <div><img src="https://komarev.com/ghpvc/?username=QY-NOX&label=✧+GHOST+VIEWS+✧&color=2dd4bf&style=flat-square" alt="views"></div>
      <div><img src="https://img.shields.io/github/followers/QY-NOX?label=◈+FOLLOWERS+◈&style=flat-square&logo=github&color=2dd4bf" alt="followers"></div>
      <div><img src="https://img.shields.io/github/stars/QY-NOX?label=✦+STELLAR+STARS+✦&style=flat-square&logo=github&color=ffd966" alt="stars"></div>
    </div>
  </div>

  <!-- dynamic typing row (double impact) -->
  <div class="glass-card" style="padding: 1.5rem; margin-bottom: 2rem; text-align: center;" data-aos="fade-up" data-aos-delay="100">
    <div style="font-size: 1.6rem; font-weight: 500; letter-spacing: 1px;">
      <i class="fas fa-sync-alt" style="margin-right: 12px; color:#2dd4bf;"></i>
      <span id="dynamic-text" style="border-right: 2px solid cyan; padding-right: 6px;"></span>
    </div>
    <div style="margin-top: 0.7rem; font-size: 0.85rem; opacity: 0.7;">⚡ active quantum realm | automated mindset ⚡</div>
  </div>

  <!-- tech arsenal + specializations -->
  <div class="grid-bg glass-card" style="padding: 1.8rem; margin-bottom: 2rem;" data-aos="fade-up" data-aos-delay="150">
    <h2 style="display: flex; gap: 10px; align-items: center;"><i class="fas fa-cogs" style="color:#2dd4bf;"></i> 🔧 synaptic toolchain</h2>
    <div class="tech-stack" style="display: flex; flex-wrap: wrap; justify-content: center; gap: 1rem; margin: 1.5rem 0 0.5rem;">
      <i class="fab fa-python" title="Python"></i>
      <i class="fab fa-java" title="Java"></i>
      <i class="fab fa-js" title="JavaScript"></i>
      <i class="fab fa-html5" title="HTML5"></i>
      <i class="fab fa-css3-alt" title="CSS3"></i>
      <i class="fas fa-database" title="Pandas/SQL"></i>
      <i class="fab fa-git-alt" title="Git"></i>
      <i class="fas fa-flask" title="Flask"></i>
      <i class="fab fa-figma" title="UI/UX"></i>
    </div>
    <div style="display: flex; flex-wrap: wrap; gap: 10px; justify-content: center; margin-top: 1rem;">
      <span class="status-badge"><i class="fas fa-brain"></i> AI Agents</span>
      <span class="status-badge"><i class="fas fa-chart-simple"></i> Crypto Analytics</span>
      <span class="status-badge"><i class="fas fa-bug"></i> Bug Hunter</span>
      <span class="status-badge"><i class="fas fa-arrow-right-arrow-left"></i> Data Entry Automation</span>
    </div>
  </div>

  <!-- projects grid (sleek cards) -->
  <h2 style="margin: 2rem 0 1rem 0; display: flex; gap: 10px;"><i class="fas fa-cube" style="color:#2dd4bf;"></i> ⟡ neural projects ⟡</h2>
  <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr)); gap: 1.6rem; margin-bottom: 2.5rem;">
    <div class="project-card" data-aos="zoom-in" data-aos-delay="50">
      <i class="fas fa-robot" style="font-size: 2rem; color:#2dd4bf;"></i>
      <h3 style="margin: 0.5rem 0;">AI Auto-Data Entry Bot</h3>
      <p style="font-size: 0.85rem; opacity: 0.8;">Python · Selenium · Pandas · OCR validation</p>
      <span class="status-badge"><i class="fas fa-spinner fa-pulse"></i> Neural training</span>
      <p style="margin-top: 12px; font-size: 0.8rem;">Automated ingestion from PDF/Excel to ERP with intelligent anomaly detection.</p>
    </div>
    <div class="project-card" data-aos="zoom-in" data-aos-delay="100">
      <i class="fas fa-chart-line" style="font-size: 2rem; color:#f0b90b;"></i>
      <h3>Crypto Market Pulse</h3>
      <p>Flask · Web3 · Sentiment AI</p>
      <span class="status-badge"><i class="fas fa-chart-simple"></i> Alpha phase</span>
      <p style="margin-top: 12px; font-size: 0.8rem;">Real-time dashboard + predictive alerts using on-chain metrics.</p>
    </div>
    <div class="project-card" data-aos="zoom-in" data-aos-delay="150">
      <i class="fas fa-shield-haltered" style="font-size: 2rem; color:#f97316;"></i>
      <h3>Bug Hunter Toolkit</h3>
      <p>Java · Python · LogFalcon</p>
      <span class="status-badge"><i class="fas fa-search"></i> R&D forge</span>
      <p style="margin-top: 12px; font-size: 0.8rem;">Lightweight CLI for log forensics & CVE pattern scanning.</p>
    </div>
    <div class="project-card" data-aos="zoom-in" data-aos-delay="200">
      <i class="fas fa-cube" style="font-size: 2rem; color:#a855f7;"></i>
      <h3>Portfolio 3.0 | WebGL</h3>
      <p>Three.js · GSAP · WebGL</p>
      <span class="status-badge"><i class="fas fa-palette"></i> Designing nebula</span>
      <p style="margin-top: 12px; font-size: 0.8rem;">Immersive 3D portfolio with cosmic aesthetics & particle network.</p>
    </div>
  </div>

  <!-- GitHub Analytics + Streak (realistic live stats) -->
  <div class="glass-card" style="padding: 1.8rem; margin-bottom: 2rem;" data-aos="fade-up">
    <h2><i class="fas fa-chart-scatter"></i> 📡 GitHub telemetry</h2>
    <div style="display: flex; flex-wrap: wrap; justify-content: center; gap: 1rem; margin-top: 1.5rem;">
      <img height="170em" src="https://github-readme-stats.vercel.app/api?username=QY-NOX&show_icons=true&theme=radical&hide_border=true&bg_color=0D1117&title_color=58a6ff&icon_color=2dd4bf&text_color=c9d1d9&ring=2dd4bf" />
      <img height="170em" src="https://github-readme-stats.vercel.app/api/top-langs/?username=QY-NOX&layout=compact&theme=radical&hide_border=true&bg_color=0D1117&title_color=58a6ff&text_color=c9d1d9" />
    </div>
    <div style="margin-top: 1.2rem; text-align: center;">
      <img src="https://github-readme-streak-stats.herokuapp.com/?user=QY-NOX&theme=radical&hide_border=true&background=0D1117&stroke=2dd4bf&ring=2dd4bf&fire=ff7700&currStreakNum=c9d1d9&sideNums=c9d1d9&currStreakLabel=58a6ff" alt="streak" style="max-width: 100%;" />
    </div>
    <div class="stat-numbers" style="margin-top: 1.2rem;">
      <div class="stat-item"><i class="fas fa-code-branch"></i> 14+ repos</div>
      <div class="stat-item"><i class="fas fa-clock"></i> 600+ contributions (2025)</div>
      <div class="stat-item"><i class="fas fa-trophy"></i> 9+ dev badges</div>
    </div>
  </div>

  <!-- Achievement Trophies + Glow -->
  <div data-aos="fade-up" style="text-align: center; margin-bottom: 2rem;">
    <img src="https://github-profile-trophy.vercel.app/?username=QY-NOX&theme=radical&no-frame=true&row=1&column=7&margin-w=10" alt="trophies" style="max-width: 100%; filter: drop-shadow(0 0 5px #2dd4bf80);" />
  </div>

  <!-- Quote & Vibe section + Connect -->
  <div class="glass-card" style="padding: 1.8rem; text-align: center; margin-bottom: 2rem;" data-aos="flip-up">
    <i class="fas fa-quote-left" style="font-size: 2rem; opacity: 0.6;"></i>
    <p style="font-size: 1.25rem; font-style: italic; max-width: 80%; margin: 0.5rem auto;">"We don't just write code — we architect digital sentience. Automate everything, question everything."</p>
    <p>— Mahfuj (QY-NOX)</p>
    <div style="margin-top: 1rem;">
      <img src="https://quotes-github-readme.vercel.app/api?type=horizontal&theme=radical" alt="random quote" style="max-width: 100%; border-radius: 30px;" />
    </div>
  </div>

  <!-- connect & terminal vibe -->
  <div style="display: flex; flex-wrap: wrap; justify-content: space-between; align-items: center; gap: 1rem;" data-aos="fade-up">
    <div>
      <h3><i class="fas fa-satellite-dish"></i> quantum entanglement</h3>
      <div style="display: flex; gap: 16px; margin-top: 12px; flex-wrap: wrap;">
        <a href="https://github.com/QY-NOX" class="glow-button" style="text-decoration: none; color: #e2e8ff;"><i class="fab fa-github"></i> GitHub</a>
        <a href="#" class="glow-button" style="text-decoration: none; color: #e2e8ff;"><i class="fas fa-envelope"></i> mahfuj.crypt@pm.me</a>
        <a href="#" class="glow-button" style="text-decoration: none; color: #e2e8ff;"><i class="fab fa-linkedin"></i> /in/mahfuj</a>
        <a href="#" class="glow-button" style="text-decoration: none; color: #e2e8ff;"><i class="fab fa-twitter"></i> @QY_NOX</a>
      </div>
    </div>
    <div>
      <i class="fas fa-waveform" style="font-size: 3rem; opacity: 0.7;"></i>
    </div>
  </div>

  <!-- footer wave -->
  <footer style="margin-top: 3rem; text-align: center; padding: 1rem 0; font-size: 0.7rem;">
    <p>✦ QY-NOX · Neural signature v2.0 ✦ <i class="fas fa-bolt"></i>  AI automation frontier  </p>
    <img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&height=60&section=footer&animation=twinkling" style="width: 100%; margin-top: 1rem;" alt="wave" />
  </footer>
</div>

<script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
<script>
  AOS.init({ once: false, mirror: false, duration: 800, easing: 'ease-out-sine' });
  
  // Rotating text effect (authentic vibe)
  const phrases = [
    ">_ AI Automation Specialist", 
    ">_ Python • Java • Web Dev", 
    ">_ Building Digital Brains", 
    ">_ Crypto Market Analyst", 
    ">_ Bug Hunter | Automation Flow"
  ];
  let idx = 0;
  let charIndex = 0;
  let currentText = "";
  let isDeleting = false;
  const dynamicSpan = document.getElementById("dynamic-text");
  
  function typeEffect() {
    const fullText = phrases[idx];
    if (isDeleting) {
      currentText = fullText.substring(0, charIndex - 1);
      charIndex--;
    } else {
      currentText = fullText.substring(0, charIndex + 1);
      charIndex++;
    }
    dynamicSpan.innerHTML = currentText;
    if (!isDeleting && charIndex === fullText.length) {
      isDeleting = true;
      setTimeout(typeEffect, 1800);
      return;
    }
    if (isDeleting && charIndex === 0) {
      isDeleting = false;
      idx = (idx + 1) % phrases.length;
      setTimeout(typeEffect, 300);
      return;
    }
    let speed = isDeleting ? 50 : 100;
    setTimeout(typeEffect, speed);
  }
  typeEffect();
  
  // Additional hover particle effect for cards (optional micro-interaction)
  const cards = document.querySelectorAll('.project-card');
  cards.forEach(card => {
    card.addEventListener('mousemove', (e) => {
      const rect = card.getBoundingClientRect();
      const x = e.clientX - rect.left;
      const y = e.clientY - rect.top;
      card.style.setProperty('--x', `${x}px`);
      card.style.setProperty('--y', `${y}px`);
    });
  });
</script>
</body>
</html>
