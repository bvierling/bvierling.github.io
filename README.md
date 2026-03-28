# Bradley-Vierling
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Bradley Vierling — Operations Manager</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --navy: #0a0f1e;
    --deep: #111827;
    --steel: #1e293b;
    --accent: #e8c84a;
    --accent2: #4a9aea;
    --light: #e8eaf0;
    --muted: #8899aa;
    --white: #f0f4ff;
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--navy);
    color: var(--light);
    font-family: 'DM Sans', sans-serif;
    font-weight: 300;
    overflow-x: hidden;
    cursor: none;
  }

  /* Custom cursor */
  .cursor {
    position: fixed;
    width: 12px; height: 12px;
    background: var(--accent);
    border-radius: 50%;
    pointer-events: none;
    z-index: 9999;
    transform: translate(-50%, -50%);
    transition: width 0.2s, height 0.2s, background 0.2s;
    mix-blend-mode: difference;
  }
  .cursor-ring {
    position: fixed;
    width: 36px; height: 36px;
    border: 1px solid rgba(232,200,74,0.5);
    border-radius: 50%;
    pointer-events: none;
    z-index: 9998;
    transform: translate(-50%, -50%);
    transition: all 0.12s ease;
  }
  body:hover .cursor { opacity: 1; }

  /* Noise overlay */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 100;
    opacity: 0.4;
  }

  /* ─── HERO ─── */
  .hero {
    min-height: 100vh;
    display: grid;
    grid-template-columns: 1fr 1fr;
    position: relative;
    overflow: hidden;
  }

  .hero-left {
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 80px 60px 80px 80px;
    position: relative;
    z-index: 2;
  }

  .hero-tag {
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.25em;
    color: var(--accent);
    text-transform: uppercase;
    margin-bottom: 24px;
    opacity: 0;
    animation: fadeUp 0.8s 0.2s forwards;
  }

  .hero-name {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(72px, 9vw, 140px);
    line-height: 0.88;
    color: var(--white);
    letter-spacing: 0.01em;
    opacity: 0;
    animation: fadeUp 0.9s 0.35s forwards;
  }

  .hero-name span {
    color: var(--accent);
    display: block;
  }

  .hero-title {
    font-family: 'DM Mono', monospace;
    font-size: 13px;
    letter-spacing: 0.15em;
    color: var(--muted);
    text-transform: uppercase;
    margin-top: 28px;
    opacity: 0;
    animation: fadeUp 0.8s 0.5s forwards;
  }

  .hero-divider {
    width: 60px;
    height: 2px;
    background: var(--accent);
    margin: 32px 0;
    opacity: 0;
    animation: expandWidth 0.8s 0.65s forwards;
  }

  .hero-summary {
    max-width: 420px;
    font-size: 15px;
    line-height: 1.75;
    color: rgba(232,234,240,0.75);
    opacity: 0;
    animation: fadeUp 0.8s 0.75s forwards;
  }

  .hero-contacts {
    display: flex;
    flex-direction: column;
    gap: 10px;
    margin-top: 40px;
    opacity: 0;
    animation: fadeUp 0.8s 0.9s forwards;
  }

  .contact-item {
    display: flex;
    align-items: center;
    gap: 12px;
    font-family: 'DM Mono', monospace;
    font-size: 12px;
    color: var(--muted);
    text-decoration: none;
    transition: color 0.2s;
  }
  .contact-item:hover { color: var(--accent); }
  .contact-icon {
    width: 28px; height: 28px;
    border: 1px solid var(--steel);
    border-radius: 6px;
    display: flex; align-items: center; justify-content: center;
    font-size: 12px;
    transition: border-color 0.2s, background 0.2s;
  }
  .contact-item:hover .contact-icon {
    border-color: var(--accent);
    background: rgba(232,200,74,0.08);
  }

  .hero-right {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .hero-graphic {
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, var(--deep) 0%, var(--steel) 100%);
    clip-path: polygon(8% 0%, 100% 0%, 100% 100%, 0% 100%);
    overflow: hidden;
  }

  .hero-graphic::before {
    content: '';
    position: absolute;
    width: 600px; height: 600px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(74,154,234,0.12) 0%, transparent 70%);
    top: -100px; right: -100px;
    animation: pulse 4s ease-in-out infinite;
  }

  .hero-graphic::after {
    content: '';
    position: absolute;
    inset: 0;
    background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 39px,
      rgba(255,255,255,0.02) 39px,
      rgba(255,255,255,0.02) 40px
    ),
    repeating-linear-gradient(
      90deg,
      transparent,
      transparent 39px,
      rgba(255,255,255,0.02) 39px,
      rgba(255,255,255,0.02) 40px
    );
  }

  .hero-stat-block {
    position: relative;
    z-index: 2;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
    padding: 60px 60px 60px 80px;
    opacity: 0;
    animation: fadeUp 1s 1s forwards;
  }

  .stat-card {
    background: rgba(10,15,30,0.7);
    border: 1px solid rgba(255,255,255,0.06);
    border-radius: 12px;
    padding: 28px 24px;
    backdrop-filter: blur(10px);
    transition: transform 0.3s, border-color 0.3s;
  }
  .stat-card:hover {
    transform: translateY(-4px);
    border-color: rgba(232,200,74,0.3);
  }
  .stat-number {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 52px;
    color: var(--accent);
    line-height: 1;
  }
  .stat-label {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.15em;
    color: var(--muted);
    text-transform: uppercase;
    margin-top: 8px;
    line-height: 1.5;
  }

  /* ─── NAV ─── */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 200;
    padding: 20px 80px;
    display: flex;
    justify-content: flex-end;
    gap: 32px;
    mix-blend-mode: difference;
  }
  nav a {
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.2em;
    color: var(--muted);
    text-decoration: none;
    text-transform: uppercase;
    transition: color 0.2s;
  }
  nav a:hover { color: var(--white); }

  /* ─── SECTIONS ─── */
  section {
    padding: 120px 80px;
    max-width: 1400px;
    margin: 0 auto;
  }

  .section-label {
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.3em;
    color: var(--accent);
    text-transform: uppercase;
    margin-bottom: 16px;
  }

  .section-heading {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(48px, 6vw, 80px);
    line-height: 0.9;
    color: var(--white);
    margin-bottom: 60px;
  }

  /* ─── EXPERIENCE ─── */
  #experience { background: var(--navy); }

  .exp-grid {
    display: grid;
    grid-template-columns: 280px 1fr;
    gap: 0;
  }

  .exp-timeline {
    position: relative;
    padding-right: 40px;
  }

  .exp-timeline::after {
    content: '';
    position: absolute;
    right: 0; top: 8px; bottom: 0;
    width: 1px;
    background: linear-gradient(to bottom, var(--accent), transparent);
  }

  .exp-item {
    display: contents;
    cursor: pointer;
  }

  .exp-date {
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    color: var(--muted);
    padding: 32px 40px 32px 0;
    position: relative;
    text-align: right;
    line-height: 1.5;
    cursor: pointer;
    transition: color 0.2s;
  }
  .exp-date.active { color: var(--accent); }
  .exp-date::after {
    content: '';
    position: absolute;
    right: -5px; top: 38px;
    width: 9px; height: 9px;
    border-radius: 50%;
    background: var(--steel);
    border: 2px solid var(--muted);
    transition: border-color 0.2s, background 0.2s;
  }
  .exp-date.active::after {
    border-color: var(--accent);
    background: var(--accent);
  }

  .exp-content {
    padding: 28px 0 28px 48px;
    border-bottom: 1px solid rgba(255,255,255,0.04);
  }

  .exp-company {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.2em;
    color: var(--accent2);
    text-transform: uppercase;
    margin-bottom: 8px;
  }

  .exp-role {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 28px;
    color: var(--white);
    letter-spacing: 0.03em;
    margin-bottom: 12px;
  }

  .exp-desc {
    font-size: 14px;
    line-height: 1.7;
    color: rgba(232,234,240,0.65);
    max-width: 520px;
  }

  /* ─── SKILLS ─── */
  #skills { background: var(--deep); }

  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    gap: 20px;
  }

  .skill-card {
    background: var(--navy);
    border: 1px solid rgba(255,255,255,0.05);
    border-radius: 16px;
    padding: 36px 32px;
    position: relative;
    overflow: hidden;
    transition: transform 0.3s, border-color 0.3s;
  }
  .skill-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--accent), transparent);
    transform: scaleX(0);
    transform-origin: left;
    transition: transform 0.4s;
  }
  .skill-card:hover { transform: translateY(-6px); border-color: rgba(232,200,74,0.2); }
  .skill-card:hover::before { transform: scaleX(1); }

  .skill-icon {
    font-size: 28px;
    margin-bottom: 20px;
  }

  .skill-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 22px;
    letter-spacing: 0.05em;
    color: var(--white);
    margin-bottom: 12px;
  }

  .skill-desc {
    font-size: 13px;
    line-height: 1.65;
    color: var(--muted);
  }

  /* ─── EDUCATION ─── */
  #education { background: var(--navy); }

  .edu-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 24px;
  }

  .edu-card {
    background: linear-gradient(135deg, var(--deep), var(--steel));
    border: 1px solid rgba(255,255,255,0.06);
    border-radius: 20px;
    padding: 48px 44px;
    position: relative;
    overflow: hidden;
    transition: transform 0.3s;
  }
  .edu-card:hover { transform: scale(1.02); }

  .edu-degree {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 36px;
    line-height: 1;
    color: var(--white);
    margin-bottom: 8px;
  }
  .edu-school {
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.15em;
    color: var(--accent);
    text-transform: uppercase;
    margin-bottom: 8px;
  }
  .edu-location {
    font-size: 13px;
    color: var(--muted);
  }
  .edu-badge {
    position: absolute;
    top: 28px; right: 28px;
    background: rgba(232,200,74,0.1);
    border: 1px solid rgba(232,200,74,0.3);
    border-radius: 20px;
    padding: 6px 14px;
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    color: var(--accent);
    letter-spacing: 0.1em;
  }

  /* ─── AWARDS ─── */
  .awards-strip {
    background: var(--deep);
    border-top: 1px solid rgba(255,255,255,0.05);
    border-bottom: 1px solid rgba(255,255,255,0.05);
    padding: 40px 80px;
    display: flex;
    align-items: center;
    gap: 60px;
    overflow: hidden;
  }

  .award-item {
    display: flex;
    align-items: center;
    gap: 16px;
    white-space: nowrap;
    flex-shrink: 0;
  }
  .award-star {
    color: var(--accent);
    font-size: 18px;
  }
  .award-text {
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.15em;
    color: var(--muted);
    text-transform: uppercase;
  }
  .award-divider {
    width: 1px;
    height: 24px;
    background: var(--steel);
    flex-shrink: 0;
  }

  /* ─── FOOTER ─── */
  footer {
    background: var(--navy);
    border-top: 1px solid rgba(255,255,255,0.04);
    padding: 60px 80px;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .footer-name {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 32px;
    color: var(--white);
    letter-spacing: 0.05em;
  }
  .footer-title {
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 0.15em;
    margin-top: 4px;
  }
  .footer-cta {
    display: inline-flex;
    align-items: center;
    gap: 12px;
    background: var(--accent);
    color: var(--navy);
    font-family: 'DM Mono', monospace;
    font-size: 12px;
    font-weight: 500;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    text-decoration: none;
    padding: 14px 28px;
    border-radius: 6px;
    transition: transform 0.2s, box-shadow 0.2s;
  }
  .footer-cta:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 32px rgba(232,200,74,0.3);
  }

  /* ─── ANIMATIONS ─── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to { opacity: 1; transform: translateY(0); }
  }
  @keyframes expandWidth {
    from { opacity: 0; width: 0; }
    to { opacity: 1; width: 60px; }
  }
  @keyframes pulse {
    0%, 100% { transform: scale(1); opacity: 0.6; }
    50% { transform: scale(1.15); opacity: 1; }
  }

  .reveal {
    opacity: 0;
    transform: translateY(30px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  .reveal.visible {
    opacity: 1;
    transform: none;
  }

  /* ─── RESPONSIVE ─── */
  @media (max-width: 900px) {
    .hero { grid-template-columns: 1fr; }
    .hero-right { display: none; }
    .hero-left { padding: 120px 32px 80px; }
    nav { padding: 20px 32px; }
    section { padding: 80px 32px; }
    .exp-grid { grid-template-columns: 1fr; }
    .exp-timeline { display: none; }
    .exp-content { padding: 24px 0; }
    .edu-grid { grid-template-columns: 1fr; }
    footer { flex-direction: column; gap: 32px; text-align: center; }
    .awards-strip { padding: 40px 32px; gap: 32px; }
  }
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<nav>
  <a href="#experience">Experience</a>
  <a href="#skills">Skills</a>
  <a href="#education">Education</a>
</nav>

<!-- ─── HERO ─── -->
<section class="hero" id="home" style="max-width:none; padding:0; margin:0;">
  <div class="hero-left">
    <div class="hero-tag">Operations Leader · Cincinnati, OH</div>
    <h1 class="hero-name">
      Bradley<br>
      <span>Vierling</span>
    </h1>
    <div class="hero-title">Operations Manager</div>
    <div class="hero-divider"></div>
    <p class="hero-summary">
      Aligning people, processes, and strategy to drive measurable business results. Specializing in high-performing teams, lean systems, and scalable operational excellence.
    </p>
    <div class="hero-contacts">
      <a class="contact-item" href="tel:5133350499">
        <div class="contact-icon">📞</div>
        513-335-0499
      </a>
      <a class="contact-item" href="mailto:bvierling@gmail.com">
        <div class="contact-icon">✉️</div>
        bvierling@gmail.com
      </a>
      <a class="contact-item" href="https://www.linkedin.com/in/bradley-vierling" target="_blank">
        <div class="contact-icon">🔗</div>
        linkedin.com/in/bradley-vierling
      </a>
      <a class="contact-item" href="#">
        <div class="contact-icon">📍</div>
        1575 Gelhot Dr, Fairfield OH 45014
      </a>
    </div>
  </div>

  <div class="hero-right">
    <div class="hero-graphic"></div>
    <div class="hero-stat-block">
      <div class="stat-card">
        <div class="stat-number">14+</div>
        <div class="stat-label">Years in Operations & Logistics</div>
      </div>
      <div class="stat-card">
        <div class="stat-number">MBA</div>
        <div class="stat-label">Bowling Green State University</div>
      </div>
      <div class="stat-card">
        <div class="stat-number">5</div>
        <div class="stat-label">Companies Led or Supported</div>
      </div>
      <div class="stat-card">
        <div class="stat-number">3×</div>
        <div class="stat-label">Dean's List — Consecutive Semesters</div>
      </div>
    </div>
  </div>
</section>

<!-- ─── EXPERIENCE ─── -->
<section id="experience">
  <div class="section-label reveal">Track Record</div>
  <h2 class="section-heading reveal">Experience</h2>
  <div class="exp-grid">
    <div class="exp-timeline">
      <div class="exp-date active" data-index="0">Feb 2023<br>— Present</div>
      <div class="exp-date" data-index="1">Jan 2021<br>— Jan 2023</div>
      <div class="exp-date" data-index="2">Aug 2017<br>— Jan 2021</div>
      <div class="exp-date" data-index="3">Aug 2016<br>— Aug 2017</div>
      <div class="exp-date" data-index="4">Jul 2012<br>— Jul 2016</div>
    </div>
    <div>
      <div class="exp-content reveal" data-index="0">
        <div class="exp-company">Republic Services</div>
        <div class="exp-role">Operations Manager</div>
        <p class="exp-desc">Leading operational strategy across people, process, and performance. Building high-performing teams through accountability, succession planning, and continuous leadership development. Implementing lean strategies to improve efficiency, reduce waste, and scale measurable business results.</p>
      </div>
      <div class="exp-content reveal" data-index="1">
        <div class="exp-company">Butler County Clerk of Courts</div>
        <div class="exp-role">Assistant Manager — Title Division</div>
        <p class="exp-desc">Managed day-to-day operations in the Title Division, supporting compliance, workflow optimization, and staff coordination within a government services environment.</p>
      </div>
      <div class="exp-content reveal" data-index="2">
        <div class="exp-company">Republic Services</div>
        <div class="exp-role">Lead Driver</div>
        <p class="exp-desc">Served in a frontline operational leadership capacity, developing deep knowledge of waste management logistics and setting performance standards for field operations teams.</p>
      </div>
      <div class="exp-content reveal" data-index="3">
        <div class="exp-company">Ernst Concrete</div>
        <div class="exp-role">Ready Mix Driver</div>
        <p class="exp-desc">Delivered ready-mix concrete safely and efficiently, building strong customer relationships and maintaining high standards for on-time delivery performance.</p>
      </div>
      <div class="exp-content reveal" data-index="4">
        <div class="exp-company">Rumpke Waste & Recycling</div>
        <div class="exp-role">Relief Driver / Market Safety Trainer</div>
        <p class="exp-desc">Combined operational driving responsibilities with a formal safety training role. Developed and delivered market safety programs, reducing incident rates and building a culture of safety compliance across the team.</p>
      </div>
    </div>
  </div>
</section>

<!-- ─── SKILLS ─── -->
<section id="skills" style="background:var(--deep); max-width:none; padding:120px 80px;">
<div style="max-width:1400px; margin:0 auto;">
  <div class="section-label reveal">Capabilities</div>
  <h2 class="section-heading reveal">Core Skills</h2>
  <div class="skills-grid">
    <div class="skill-card reveal">
      <div class="skill-icon">🏛️</div>
      <div class="skill-title">Organizational Leadership</div>
      <p class="skill-desc">Building, mentoring, and scaling high-performing leadership teams through accountability structures, succession planning, and continuous development programs.</p>
    </div>
    <div class="skill-card reveal">
      <div class="skill-icon">📊</div>
      <div class="skill-title">Strategic Lean Analysis</div>
      <p class="skill-desc">Applying lean methodologies to identify inefficiencies, reduce waste, and drive data-driven improvements across operational workflows and financial processes.</p>
    </div>
    <div class="skill-card reveal">
      <div class="skill-icon">🚀</div>
      <div class="skill-title">Business Growth & Scale</div>
      <p class="skill-desc">Designing operational systems and business foundations that support sustainable, scalable growth — from process documentation to performance measurement.</p>
    </div>
    <div class="skill-card reveal">
      <div class="skill-icon">🔄</div>
      <div class="skill-title">Change Management</div>
      <p class="skill-desc">Leading organizations through transformation by aligning stakeholders, communicating strategy clearly, and sustaining momentum across complex change initiatives.</p>
    </div>
    <div class="skill-card reveal">
      <div class="skill-icon">💬</div>
      <div class="skill-title">Communication</div>
      <p class="skill-desc">Fostering open, inclusive environments that encourage feedback, innovation, and cross-functional collaboration at every level of the organization.</p>
    </div>
    <div class="skill-card reveal">
      <div class="skill-icon">🛡️</div>
      <div class="skill-title">Safety & Compliance</div>
      <p class="skill-desc">Formal safety training background with experience developing market-wide safety programs that build culture, reduce incidents, and meet regulatory requirements.</p>
    </div>
  </div>
</div>
</section>

<!-- ─── AWARDS ─── -->
<div class="awards-strip">
  <div class="award-item">
    <span class="award-star">★</span>
    <span class="award-text">Dean's List — 3 Consecutive Semesters</span>
  </div>
  <div class="award-divider"></div>
  <div class="award-item">
    <span class="award-star">★</span>
    <span class="award-text">National Youth Leadership Forum Alumni</span>
  </div>
  <div class="award-divider"></div>
  <div class="award-item">
    <span class="award-star">★</span>
    <span class="award-text">Defense, Intelligence & Diplomacy Program</span>
  </div>
</div>

<!-- ─── EDUCATION ─── -->
<section id="education">
  <div class="section-label reveal">Credentials</div>
  <h2 class="section-heading reveal">Education</h2>
  <div class="edu-grid">
    <div class="edu-card reveal">
      <div class="edu-badge">Graduate</div>
      <div class="edu-degree">Master of Business Administration</div>
      <div class="edu-school">Bowling Green State University</div>
      <div class="edu-location">Bowling Green, Ohio</div>
    </div>
    <div class="edu-card reveal">
      <div class="edu-badge">Undergraduate</div>
      <div class="edu-degree">BS of Commerce in Business Management</div>
      <div class="edu-school">Miami University</div>
      <div class="edu-location">Oxford, Ohio · Minor in English Studies</div>
    </div>
  </div>
</section>

<!-- ─── FOOTER ─── -->
<footer>
  <div>
    <div class="footer-name">Bradley Vierling</div>
    <div class="footer-title">Operations Manager · Fairfield, OH</div>
  </div>
  <a class="footer-cta" href="mailto:bvierling@gmail.com">
    Get in Touch →
  </a>
</footer>

<script>
  // Custom cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;

  document.addEventListener('mousemove', e => {
    mx = e.clientX; my = e.clientY;
    cursor.style.left = mx + 'px';
    cursor.style.top = my + 'px';
  });

  function animateRing() {
    rx += (mx - rx) * 0.12;
    ry += (my - ry) * 0.12;
    ring.style.left = rx + 'px';
    ring.style.top = ry + 'px';
    requestAnimationFrame(animateRing);
  }
  animateRing();

  document.querySelectorAll('a, button, .skill-card, .stat-card').forEach(el => {
    el.addEventListener('mouseenter', () => {
      cursor.style.width = '20px';
      cursor.style.height = '20px';
    });
    el.addEventListener('mouseleave', () => {
      cursor.style.width = '12px';
      cursor.style.height = '12px';
    });
  });

  // Scroll reveal
  const observer = new IntersectionObserver(entries => {
    entries.forEach((entry, i) => {
      if (entry.isIntersecting) {
        setTimeout(() => entry.target.classList.add('visible'), i * 80);
      }
    });
  }, { threshold: 0.1 });

  document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

  // Timeline interaction
  document.querySelectorAll('.exp-date').forEach(date => {
    date.addEventListener('click', () => {
      document.querySelectorAll('.exp-date').forEach(d => d.classList.remove('active'));
      date.classList.add('active');
    });
  });

  // Counter animation for stats
  function animateValue(el, start, end, duration, suffix = '') {
    let startTime = null;
    const step = timestamp => {
      if (!startTime) startTime = timestamp;
      const progress = Math.min((timestamp - startTime) / duration, 1);
      const val = Math.floor(progress * (end - start) + start);
      el.textContent = val + suffix;
      if (progress < 1) requestAnimationFrame(step);
    };
    requestAnimationFrame(step);
  }

  const statObs = new IntersectionObserver(entries => {
    if (entries[0].isIntersecting) {
      const nums = document.querySelectorAll('.stat-number');
      animateValue(nums[0], 0, 14, 1200, '+');
      setTimeout(() => statObs.disconnect(), 100);
    }
  }, { threshold: 0.5 });

  const statBlock = document.querySelector('.hero-stat-block');
  if (statBlock) statObs.observe(statBlock);
</script>
</body>
</html>
