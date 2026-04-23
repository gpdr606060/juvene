<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Rejuvenese — Clínica Estética</title>
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400&family=Jost:wght@300;400;500&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --cream:    #f7f3ee;
      --ivory:    #ede8df;
      --gold:     #b89660;
      --gold-lt:  #d4b483;
      --sage:     #3d5247;
      --charcoal: #1e1e1e;
      --warm-gray:#7a7068;
    }
 
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
 
    html { scroll-behavior: smooth; }
 
    body {
      font-family: 'Jost', sans-serif;
      background: var(--cream);
      color: var(--charcoal);
      overflow-x: hidden;
    }
 
    /* ── CURSOR ── */
    * { cursor: none; }
    .cursor {
      position: fixed; top: 0; left: 0; z-index: 9999;
      pointer-events: none;
      width: 10px; height: 10px;
      background: var(--gold);
      border-radius: 50%;
      transform: translate(-50%, -50%);
      transition: transform .15s ease, width .25s ease, height .25s ease, opacity .25s ease;
    }
    .cursor-ring {
      position: fixed; top: 0; left: 0; z-index: 9998;
      pointer-events: none;
      width: 38px; height: 38px;
      border: 1px solid var(--gold);
      border-radius: 50%;
      transform: translate(-50%, -50%);
      transition: transform .35s cubic-bezier(.2,.8,.2,1), opacity .3s;
      opacity: .5;
    }
 
    /* ── NAV ── */
    nav {
      position: fixed; top: 0; width: 100%; z-index: 100;
      display: flex; align-items: center; justify-content: space-between;
      padding: 28px 60px;
      transition: background .5s, padding .5s;
    }
    nav.scrolled {
      background: rgba(247,243,238,.95);
      backdrop-filter: blur(12px);
      padding: 18px 60px;
      box-shadow: 0 1px 0 rgba(184,150,96,.2);
    }
    .nav-logo {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.7rem; font-weight: 300; letter-spacing: .12em;
      color: var(--sage); text-decoration: none;
    }
    .nav-logo span { color: var(--gold); }
    .nav-links { display: flex; gap: 36px; list-style: none; }
    .nav-links a {
      font-size: .78rem; letter-spacing: .18em; text-transform: uppercase;
      color: var(--charcoal); text-decoration: none; font-weight: 400;
      position: relative;
    }
    .nav-links a::after {
      content: ''; position: absolute; bottom: -3px; left: 0;
      width: 0; height: 1px; background: var(--gold);
      transition: width .35s ease;
    }
    .nav-links a:hover::after { width: 100%; }
    .nav-cta {
      font-size: .78rem; letter-spacing: .18em; text-transform: uppercase;
      background: var(--sage); color: var(--cream) !important;
      padding: 12px 26px; text-decoration: none;
      transition: background .3s;
    }
    .nav-cta:hover { background: var(--gold) !important; }
    .nav-cta::after { display: none !important; }
 
    /* ── HERO ── */
    .hero {
      min-height: 100vh;
      display: grid; grid-template-columns: 1fr 1fr;
      position: relative; overflow: hidden;
    }
    .hero-left {
      background: var(--sage);
      display: flex; flex-direction: column;
      justify-content: flex-end; padding: 80px 70px;
      position: relative; z-index: 2;
    }
    .hero-eyebrow {
      font-size: .72rem; letter-spacing: .3em; text-transform: uppercase;
      color: var(--gold-lt); margin-bottom: 32px;
      animation: fadeUp .9s .2s both;
    }
    .hero-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(3.5rem, 5.5vw, 6.5rem);
      font-weight: 300; line-height: 1.05;
      color: var(--cream); letter-spacing: -.01em;
      animation: fadeUp 1s .4s both;
    }
    .hero-title em { font-style: italic; color: var(--gold-lt); }
    .hero-sub {
      margin-top: 32px; max-width: 360px;
      font-size: .9rem; line-height: 1.8; font-weight: 300;
      color: rgba(237,232,223,.7);
      animation: fadeUp 1s .6s both;
    }
    .hero-buttons {
      margin-top: 48px; display: flex; gap: 16px;
      animation: fadeUp 1s .8s both;
    }
    .btn-primary {
      padding: 16px 38px;
      background: var(--gold); color: var(--charcoal);
      font-size: .78rem; letter-spacing: .18em; text-transform: uppercase;
      text-decoration: none;
      transition: background .3s, transform .3s;
    }
    .btn-primary:hover { background: var(--gold-lt); transform: translateY(-2px); }
    .btn-outline {
      padding: 16px 38px;
      border: 1px solid rgba(237,232,223,.4); color: var(--cream);
      font-size: .78rem; letter-spacing: .18em; text-transform: uppercase;
      text-decoration: none;
      transition: border-color .3s, transform .3s;
    }
    .btn-outline:hover { border-color: var(--gold-lt); transform: translateY(-2px); }
    .hero-numbers {
      margin-top: 72px; display: flex; gap: 48px;
      animation: fadeUp 1s 1s both;
    }
    .hero-num-item { display: flex; flex-direction: column; }
    .hero-num-value {
      font-family: 'Cormorant Garamond', serif;
      font-size: 2.6rem; font-weight: 300; color: var(--gold-lt);
      line-height: 1;
    }
    .hero-num-label {
      font-size: .68rem; letter-spacing: .2em; text-transform: uppercase;
      color: rgba(237,232,223,.5); margin-top: 6px;
    }
 
    .hero-right {
      position: relative; overflow: hidden;
    }
    .hero-img-bg {
      position: absolute; inset: 0;
      background:
        radial-gradient(ellipse at 60% 30%, rgba(184,150,96,.18) 0%, transparent 60%),
        linear-gradient(135deg, #c5b8a8 0%, #a89880 40%, #8c7a68 100%);
    }
    .hero-decorative {
      position: absolute; bottom: 60px; left: 60px;
      font-family: 'Cormorant Garamond', serif;
      font-size: 11rem; font-weight: 300; letter-spacing: -.05em;
      color: rgba(255,255,255,.07); line-height: 1;
      user-select: none;
      animation: fadeUp 1.2s .5s both;
    }
    .hero-badge {
      position: absolute; top: 50%; right: 60px; transform: translateY(-50%);
      width: 140px; height: 140px;
      border: 1px solid rgba(255,255,255,.3); border-radius: 50%;
      display: flex; align-items: center; justify-content: center;
      animation: spin 20s linear infinite;
    }
    .hero-badge-inner {
      font-size: .58rem; letter-spacing: .35em; text-transform: uppercase;
      color: rgba(255,255,255,.7);
      writing-mode: vertical-rl;
    }
    .hero-line {
      position: absolute; bottom: 0; left: 0; right: 0;
      height: 1px; background: linear-gradient(90deg, transparent, var(--gold), transparent);
    }
 
    /* ── MARQUEE ── */
    .marquee-wrap {
      overflow: hidden; background: var(--gold);
      padding: 14px 0; white-space: nowrap;
    }
    .marquee-inner {
      display: inline-block;
      animation: marquee 22s linear infinite;
    }
    .marquee-inner span {
      font-size: .72rem; letter-spacing: .28em; text-transform: uppercase;
      color: var(--charcoal); margin: 0 40px;
    }
    .marquee-inner span::before { content: '✦  '; color: var(--sage); }
 
    /* ── INTRO ── */
    .intro {
      display: grid; grid-template-columns: 1fr 1fr;
      gap: 0; padding: 120px 80px;
      align-items: center;
    }
    .intro-left {
      padding-right: 80px; border-right: 1px solid var(--ivory);
    }
    .section-tag {
      font-size: .68rem; letter-spacing: .3em; text-transform: uppercase;
      color: var(--gold); margin-bottom: 20px; display: block;
    }
    .intro-heading {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(2.2rem, 3.5vw, 3.8rem);
      font-weight: 300; line-height: 1.2;
      color: var(--charcoal);
    }
    .intro-heading em { font-style: italic; color: var(--sage); }
    .intro-right { padding-left: 80px; }
    .intro-p {
      font-size: .92rem; line-height: 1.95; font-weight: 300;
      color: var(--warm-gray); margin-bottom: 24px;
    }
    .intro-divider {
      width: 48px; height: 1px; background: var(--gold); margin: 36px 0;
    }
    .intro-quote {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.35rem; font-style: italic; font-weight: 300;
      color: var(--sage); line-height: 1.6;
    }
 
    /* ── SERVICES ── */
    .services { padding: 80px 80px 120px; background: var(--charcoal); }
    .services-header {
      display: flex; justify-content: space-between; align-items: flex-end;
      margin-bottom: 72px;
    }
    .services-heading {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(2.5rem, 4vw, 4.5rem);
      font-weight: 300; color: var(--cream); line-height: 1.1;
    }
    .services-heading em { font-style: italic; color: var(--gold-lt); }
    .services-desc {
      max-width: 320px; font-size: .88rem; line-height: 1.8;
      color: rgba(247,243,238,.5); font-weight: 300; text-align: right;
    }
    .services-grid {
      display: grid; grid-template-columns: repeat(3, 1fr); gap: 2px;
    }
    .service-card {
      background: rgba(247,243,238,.03);
      border: 1px solid rgba(184,150,96,.12);
      padding: 52px 42px;
      position: relative; overflow: hidden;
      transition: background .4s, border-color .4s, transform .4s;
    }
    .service-card:hover {
      background: rgba(184,150,96,.08);
      border-color: rgba(184,150,96,.35);
      transform: translateY(-4px);
    }
    .service-card::before {
      content: '';
      position: absolute; top: 0; left: 0; right: 0;
      height: 2px; background: linear-gradient(90deg, var(--gold), transparent);
      transform: scaleX(0); transform-origin: left;
      transition: transform .4s ease;
    }
    .service-card:hover::before { transform: scaleX(1); }
    .service-num {
      font-family: 'Cormorant Garamond', serif;
      font-size: 4rem; font-weight: 300;
      color: rgba(184,150,96,.15); line-height: 1;
      position: absolute; top: 24px; right: 32px;
    }
    .service-icon {
      font-size: 1.6rem; margin-bottom: 28px; display: block;
    }
    .service-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.6rem; font-weight: 400;
      color: var(--cream); margin-bottom: 16px;
    }
    .service-text {
      font-size: .83rem; line-height: 1.85; font-weight: 300;
      color: rgba(247,243,238,.55);
    }
    .service-link {
      display: inline-flex; align-items: center; gap: 8px;
      margin-top: 32px; font-size: .72rem; letter-spacing: .2em;
      text-transform: uppercase; color: var(--gold);
      text-decoration: none; transition: gap .3s;
    }
    .service-link:hover { gap: 14px; }
 
    /* ── PROCESS ── */
    .process {
      padding: 120px 80px;
      background: var(--ivory);
    }
    .process-inner {
      max-width: 900px; margin: 0 auto; text-align: center;
    }
    .process-heading {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(2rem, 3.5vw, 3.5rem);
      font-weight: 300; color: var(--charcoal);
      margin-bottom: 72px; line-height: 1.2;
    }
    .process-heading em { font-style: italic; color: var(--sage); }
    .process-steps {
      display: grid; grid-template-columns: repeat(4, 1fr);
      gap: 0; position: relative;
    }
    .process-steps::before {
      content: '';
      position: absolute; top: 40px; left: 12.5%; right: 12.5%;
      height: 1px; background: linear-gradient(90deg, transparent, var(--gold), transparent);
    }
    .process-step {
      display: flex; flex-direction: column; align-items: center;
      padding: 0 20px;
    }
    .step-circle {
      width: 80px; height: 80px;
      border: 1px solid var(--gold); border-radius: 50%;
      display: flex; align-items: center; justify-content: center;
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.6rem; font-weight: 300; color: var(--gold);
      background: var(--ivory); margin-bottom: 28px;
      position: relative; z-index: 1;
      transition: background .3s, color .3s;
    }
    .process-step:hover .step-circle {
      background: var(--gold); color: var(--cream);
    }
    .step-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.1rem; font-weight: 500;
      color: var(--charcoal); margin-bottom: 12px;
    }
    .step-desc {
      font-size: .8rem; line-height: 1.8; color: var(--warm-gray); font-weight: 300;
    }
 
    /* ── TESTIMONIALS ── */
    .testimonials { padding: 120px 80px; }
    .testimonials-header { text-align: center; margin-bottom: 80px; }
    .test-heading {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(2rem, 3.5vw, 3.5rem);
      font-weight: 300; color: var(--charcoal);
    }
    .test-heading em { font-style: italic; color: var(--gold); }
    .test-grid {
      display: grid; grid-template-columns: repeat(3, 1fr); gap: 28px;
    }
    .test-card {
      background: var(--ivory);
      padding: 52px 42px;
      border-bottom: 3px solid transparent;
      transition: border-color .3s, transform .3s;
    }
    .test-card:hover {
      border-color: var(--gold);
      transform: translateY(-5px);
    }
    .test-stars {
      display: flex; gap: 4px; margin-bottom: 28px;
    }
    .test-stars span { color: var(--gold); font-size: .85rem; }
    .test-text {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.25rem; font-style: italic; font-weight: 300;
      color: var(--charcoal); line-height: 1.7; margin-bottom: 32px;
    }
    .test-author { display: flex; align-items: center; gap: 16px; }
    .test-avatar {
      width: 46px; height: 46px; border-radius: 50%;
      display: flex; align-items: center; justify-content: center;
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.2rem; font-weight: 400;
      color: var(--cream); background: var(--sage);
      flex-shrink: 0;
    }
    .test-author-name {
      font-size: .82rem; font-weight: 500; color: var(--charcoal);
      letter-spacing: .05em;
    }
    .test-author-role {
      font-size: .72rem; color: var(--warm-gray); margin-top: 2px;
      font-weight: 300;
    }
 
    /* ── CTA BAND ── */
    .cta-band {
      background: var(--sage);
      padding: 100px 80px;
      display: grid; grid-template-columns: 1fr auto;
      align-items: center; gap: 80px;
    }
    .cta-headline {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(2.4rem, 4vw, 4.2rem);
      font-weight: 300; color: var(--cream); line-height: 1.1;
    }
    .cta-headline em { font-style: italic; color: var(--gold-lt); }
    .cta-sub {
      margin-top: 16px; font-size: .88rem; font-weight: 300;
      color: rgba(247,243,238,.6); line-height: 1.7;
    }
    .cta-form { display: flex; gap: 0; min-width: 360px; }
    .cta-input {
      flex: 1; padding: 18px 24px;
      background: rgba(255,255,255,.1);
      border: 1px solid rgba(255,255,255,.2); border-right: none;
      color: var(--cream); font-family: 'Jost', sans-serif;
      font-size: .85rem; outline: none;
    }
    .cta-input::placeholder { color: rgba(247,243,238,.4); }
    .cta-btn {
      padding: 18px 32px;
      background: var(--gold); color: var(--charcoal);
      border: none; font-family: 'Jost', sans-serif;
      font-size: .75rem; letter-spacing: .2em; text-transform: uppercase;
      font-weight: 500; cursor: none;
      transition: background .3s;
    }
    .cta-btn:hover { background: var(--gold-lt); }
 
    /* ── FOOTER ── */
    footer {
      background: var(--charcoal);
      padding: 80px 80px 40px;
    }
    .footer-top {
      display: grid; grid-template-columns: 2fr 1fr 1fr 1fr;
      gap: 60px; padding-bottom: 60px;
      border-bottom: 1px solid rgba(255,255,255,.08);
    }
    .footer-brand {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.9rem; font-weight: 300; letter-spacing: .12em;
      color: var(--cream); margin-bottom: 20px;
    }
    .footer-brand span { color: var(--gold); }
    .footer-tagline {
      font-size: .82rem; line-height: 1.8; font-weight: 300;
      color: rgba(247,243,238,.4); max-width: 260px;
    }
    .footer-col h4 {
      font-size: .7rem; letter-spacing: .25em; text-transform: uppercase;
      color: var(--gold); margin-bottom: 24px; font-weight: 400;
    }
    .footer-col ul { list-style: none; }
    .footer-col li { margin-bottom: 12px; }
    .footer-col a {
      font-size: .83rem; font-weight: 300;
      color: rgba(247,243,238,.5); text-decoration: none;
      transition: color .3s;
    }
    .footer-col a:hover { color: var(--cream); }
    .footer-bottom {
      padding-top: 36px; display: flex; justify-content: space-between;
      align-items: center;
    }
    .footer-copy {
      font-size: .75rem; font-weight: 300;
      color: rgba(247,243,238,.3);
    }
    .footer-socials { display: flex; gap: 20px; }
    .footer-social {
      width: 38px; height: 38px;
      border: 1px solid rgba(255,255,255,.15); border-radius: 50%;
      display: flex; align-items: center; justify-content: center;
      color: rgba(247,243,238,.4); font-size: .75rem;
      text-decoration: none; transition: border-color .3s, color .3s;
    }
    .footer-social:hover { border-color: var(--gold); color: var(--gold); }
 
    /* ── ANIMATIONS ── */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(30px); }
      to   { opacity: 1; transform: translateY(0); }
    }
    @keyframes marquee {
      from { transform: translateX(0); }
      to   { transform: translateX(-50%); }
    }
    @keyframes spin {
      from { transform: translateY(-50%) rotate(0deg); }
      to   { transform: translateY(-50%) rotate(360deg); }
    }
    .reveal {
      opacity: 0; transform: translateY(40px);
      transition: opacity .8s ease, transform .8s ease;
    }
    .reveal.visible {
      opacity: 1; transform: translateY(0);
    }
 
    /* ── MOBILE ── */
    @media (max-width: 900px) {
      .hero { grid-template-columns: 1fr; }
      .hero-right { height: 300px; }
      .hero-left { padding: 100px 32px 60px; }
      nav { padding: 20px 32px; }
      .nav-links { display: none; }
      .intro { grid-template-columns: 1fr; padding: 60px 32px; }
      .intro-left { padding-right: 0; border-right: none; padding-bottom: 40px; }
      .intro-right { padding-left: 0; }
      .services { padding: 60px 32px; }
      .services-grid { grid-template-columns: 1fr; }
      .services-header { flex-direction: column; gap: 24px; }
      .services-desc { text-align: left; max-width: 100%; }
      .process { padding: 60px 32px; }
      .process-steps { grid-template-columns: 1fr 1fr; gap: 40px; }
      .process-steps::before { display: none; }
      .testimonials { padding: 60px 32px; }
      .test-grid { grid-template-columns: 1fr; }
      .cta-band { grid-template-columns: 1fr; padding: 60px 32px; }
      .cta-form { flex-direction: column; }
      .cta-input { border-right: 1px solid rgba(255,255,255,.2); border-bottom: none; }
      footer { padding: 60px 32px 32px; }
      .footer-top { grid-template-columns: 1fr 1fr; }
      .footer-bottom { flex-direction: column; gap: 20px; }
    }
  </style>
</head>
<body>
 
  <!-- CURSOR -->
  <div class="cursor" id="cursor"></div>
  <div class="cursor-ring" id="cursorRing"></div>
 
  <!-- NAV -->
  <nav id="nav">
    <a href="#" class="nav-logo">Re<span>juven</span>ese</a>
    <ul class="nav-links">
      <li><a href="#servicios">Servicios</a></li>
      <li><a href="#nosotros">Nosotros</a></li>
      <li><a href="#proceso">Proceso</a></li>
      <li><a href="#testimonios">Testimonios</a></li>
      <li><a href="#contacto" class="nav-cta">Reservar cita</a></li>
    </ul>
  </nav>
 
  <!-- HERO -->
  <section class="hero">
    <div class="hero-left">
      <p class="hero-eyebrow">Clínica Estética Premium · Est. 2015</p>
      <h1 class="hero-title">Tu belleza,<br><em>redefinida.</em></h1>
      <p class="hero-sub">Tratamientos de vanguardia con tecnología de última generación y el más alto estándar de cuidado personalizado.</p>
      <div class="hero-buttons">
        <a href="#contacto" class="btn-primary">Agenda tu consulta</a>
        <a href="#servicios" class="btn-outline">Ver servicios</a>
      </div>
      <div class="hero-numbers">
        <div class="hero-num-item">
          <span class="hero-num-value">10+</span>
          <span class="hero-num-label">Años de experiencia</span>
        </div>
        <div class="hero-num-item">
          <span class="hero-num-value">8K+</span>
          <span class="hero-num-label">Pacientes felices</span>
        </div>
        <div class="hero-num-item">
          <span class="hero-num-value">30+</span>
          <span class="hero-num-label">Tratamientos</span>
        </div>
      </div>
    </div>
    <div class="hero-right">
      <div class="hero-img-bg"></div>
      <div class="hero-decorative">✦</div>
      <div class="hero-badge">
        <div class="hero-badge-inner">Expertos en belleza · Rejuvenese</div>
      </div>
      <div class="hero-line"></div>
    </div>
  </section>
 
  <!-- MARQUEE -->
  <div class="marquee-wrap">
    <div class="marquee-inner">
      <span>Medicina Estética</span><span>Rejuvenecimiento Facial</span>
      <span>Botox & Fillers</span><span>Láser Corporal</span>
      <span>Peeling Químico</span><span>Tratamiento Capilar</span>
      <span>Hidratación Profunda</span><span>Nutrición Estética</span>
      <span>Medicina Estética</span><span>Rejuvenecimiento Facial</span>
      <span>Botox & Fillers</span><span>Láser Corporal</span>
      <span>Peeling Químico</span><span>Tratamiento Capilar</span>
      <span>Hidratación Profunda</span><span>Nutrición Estética</span>
    </div>
  </div>
 
  <!-- INTRO -->
  <section class="intro" id="nosotros">
    <div class="intro-left reveal">
      <span class="section-tag">Sobre Rejuvenese</span>
      <h2 class="intro-heading">Ciencia y arte al<br>servicio de tu<br><em>bienestar</em></h2>
    </div>
    <div class="intro-right reveal">
      <p class="intro-p">En Rejuvenese combinamos la más avanzada tecnología médico-estética con un enfoque completamente personalizado. Nuestro equipo de especialistas certificados diseña cada tratamiento según tu anatomía única y objetivos.</p>
      <p class="intro-p">Creemos que la belleza auténtica surge del equilibrio entre salud y confianza. Por eso cada visita es una experiencia holística, desde la consulta inicial hasta los cuidados postratamiento.</p>
      <div class="intro-divider"></div>
      <p class="intro-quote">"Cada rostro cuenta su propia historia. Nosotros la hacemos brillar."</p>
    </div>
  </section>
 
  <!-- SERVICES -->
  <section class="services" id="servicios">
    <div class="services-header reveal">
      <h2 class="services-heading">Nuestros<br><em>tratamientos</em></h2>
      <p class="services-desc">Soluciones estéticas integrales diseñadas para resultados naturales y duraderos.</p>
    </div>
    <div class="services-grid">
 
      <div class="service-card reveal">
        <span class="service-num">01</span>
        <span class="service-icon">💉</span>
        <h3 class="service-title">Botox & Fillers</h3>
        <p class="service-text">Suaviza líneas de expresión y restaura el volumen perdido con toxina botulínica y ácido hialurónico de alta calidad. Resultados naturales y sutiles.</p>
        <a href="#contacto" class="service-link">Conocer más →</a>
      </div>
 
      <div class="service-card reveal">
        <span class="service-num">02</span>
        <span class="service-icon">✨</span>
        <h3 class="service-title">Láser & Tecnología</h3>
        <p class="service-text">Desde depilación láser hasta rejuvenecimiento con radiofrecuencia y ultrasónico. Tecnología de vanguardia para una piel más firme y radiante.</p>
        <a href="#contacto" class="service-link">Conocer más →</a>
      </div>
 
      <div class="service-card reveal">
        <span class="service-num">03</span>
        <span class="service-icon">🌿</span>
        <h3 class="service-title">Peeling & Hidratación</h3>
        <p class="service-text">Renovación celular profunda con peelings químicos y tratamientos de hidratación intensiva. Luminosidad y textura excepcional desde la primera sesión.</p>
        <a href="#contacto" class="service-link">Conocer más →</a>
      </div>
 
      <div class="service-card reveal">
        <span class="service-num">04</span>
        <span class="service-icon">🔬</span>
        <h3 class="service-title">Plasma Rico en Plaquetas</h3>
        <p class="service-text">Aprovecha el poder regenerativo de tu propio organismo. El tratamiento PRP estimula la producción de colágeno y acelera la renovación cutánea.</p>
        <a href="#contacto" class="service-link">Conocer más →</a>
      </div>
 
      <div class="service-card reveal">
        <span class="service-num">05</span>
        <span class="service-icon">💆</span>
        <h3 class="service-title">Tratamientos Corporales</h3>
        <p class="service-text">Reductores, modeladores y anticelulíticos con tecnología de última generación. Transforma y redefine tu silueta de forma segura y efectiva.</p>
        <a href="#contacto" class="service-link">Conocer más →</a>
      </div>
 
      <div class="service-card reveal">
        <span class="service-num">06</span>
        <span class="service-icon">💊</span>
        <h3 class="service-title">Nutrición Estética</h3>
        <p class="service-text">La belleza empieza desde adentro. Vitaminas, sueros y nutrientes específicos administrados para potenciar tus resultados y revitalizar tu energía.</p>
        <a href="#contacto" class="service-link">Conocer más →</a>
      </div>
 
    </div>
  </section>
 
  <!-- PROCESS -->
  <section class="process" id="proceso">
    <div class="process-inner">
      <span class="section-tag" style="color:var(--gold)">Nuestro proceso</span>
      <h2 class="process-heading reveal">Tu camino hacia la mejor<br>versión de ti <em>misma</em></h2>
      <div class="process-steps">
        <div class="process-step reveal">
          <div class="step-circle">1</div>
          <h4 class="step-title">Consulta Inicial</h4>
          <p class="step-desc">Evaluación completa de tu piel y objetivos con nuestros especialistas.</p>
        </div>
        <div class="process-step reveal">
          <div class="step-circle">2</div>
          <h4 class="step-title">Plan Personalizado</h4>
          <p class="step-desc">Diseñamos un protocolo de tratamiento único para ti y tus necesidades.</p>
        </div>
        <div class="process-step reveal">
          <div class="step-circle">3</div>
          <h4 class="step-title">Tratamiento</h4>
          <p class="step-desc">Aplicación con las técnicas más avanzadas en un ambiente de confort total.</p>
        </div>
        <div class="process-step reveal">
          <div class="step-circle">4</div>
          <h4 class="step-title">Seguimiento</h4>
          <p class="step-desc">Acompañamiento continuo para asegurar y potenciar tus resultados.</p>
        </div>
      </div>
    </div>
  </section>
 
  <!-- TESTIMONIALS -->
  <section class="testimonials" id="testimonios">
    <div class="testimonials-header reveal">
      <span class="section-tag">Lo que dicen de nosotros</span>
      <h2 class="test-heading">Historias de <em>transformación</em></h2>
    </div>
    <div class="test-grid">
 
      <div class="test-card reveal">
        <div class="test-stars">
          <span>★</span><span>★</span><span>★</span><span>★</span><span>★</span>
        </div>
        <p class="test-text">"Llevo tres años viniendo a Rejuvenese y los resultados siguen superando mis expectativas. El equipo es increíblemente profesional y siempre me hace sentir especial."</p>
        <div class="test-author">
          <div class="test-avatar">M</div>
          <div>
            <p class="test-author-name">María Valentina C.</p>
            <p class="test-author-role">Tratamiento facial · Bogotá</p>
          </div>
        </div>
      </div>
 
      <div class="test-card reveal">
        <div class="test-stars">
          <span>★</span><span>★</span><span>★</span><span>★</span><span>★</span>
        </div>
        <p class="test-text">"El cambio fue gradual y natural, exactamente lo que quería. Nadie sospecha que me hice algo, solo sé que me dicen que me veo 10 años más joven. ¡Maravilloso!"</p>
        <div class="test-author">
          <div class="test-avatar">L</div>
          <div>
            <p class="test-author-name">Laura Esperanza M.</p>
            <p class="test-author-role">Botox & Fillers · Medellín</p>
          </div>
        </div>
      </div>
 
      <div class="test-card reveal">
        <div class="test-stars">
          <span>★</span><span>★</span><span>★</span><span>★</span><span>★</span>
        </div>
        <p class="test-text">"Vine por la depilación láser y me quedé por todos los demás tratamientos. La tecnología que tienen es de primer nivel y los resultados son permanentes. ¡100% recomendada!"</p>
        <div class="test-author">
          <div class="test-avatar">S</div>
          <div>
            <p class="test-author-name">Sofía Alejandra R.</p>
            <p class="test-author-role">Láser corporal · Cali</p>
          </div>
        </div>
      </div>
 
    </div>
  </section>
 
  <!-- CTA BAND -->
  <section class="cta-band" id="contacto">
    <div class="reveal">
      <h2 class="cta-headline">Comienza tu<br><em>transformación</em><br>hoy</h2>
      <p class="cta-sub">Déjanos tu correo y te contactamos para agendar<br>tu consulta inicial completamente gratuita.</p>
    </div>
    <div class="reveal">
      <div class="cta-form">
        <input class="cta-input" type="email" placeholder="tu@correo.com"/>
        <button class="cta-btn">Reservar</button>
      </div>
      <p style="margin-top:14px; font-size:.72rem; color:rgba(247,243,238,.35); font-weight:300;">
        También puedes llamarnos al <strong style="color:rgba(247,243,238,.6)">+57 (1) 800 REJUV</strong>
      </p>
    </div>
  </section>
 
  <!-- FOOTER -->
  <footer>
    <div class="footer-top">
      <div>
        <div class="footer-brand">Re<span>juven</span>ese</div>
        <p class="footer-tagline">Tu clínica estética de confianza. Ciencia, arte y pasión por la belleza en cada tratamiento.</p>
      </div>
      <div class="footer-col">
        <h4>Servicios</h4>
        <ul>
          <li><a href="#">Botox & Fillers</a></li>
          <li><a href="#">Láser Facial</a></li>
          <li><a href="#">Corporales</a></li>
          <li><a href="#">PRP</a></li>
          <li><a href="#">Nutrición</a></li>
        </ul>
      </div>
      <div class="footer-col">
        <h4>Clínica</h4>
        <ul>
          <li><a href="#">Sobre nosotros</a></li>
          <li><a href="#">Nuestro equipo</a></li>
          <li><a href="#">Blog</a></li>
          <li><a href="#">Promociones</a></li>
        </ul>
      </div>
      <div class="footer-col">
        <h4>Contacto</h4>
        <ul>
          <li><a href="#">Cra 15 # 93 – 47, Bogotá</a></li>
          <li><a href="#">info@rejuvenese.co</a></li>
          <li><a href="#">Lun–Sáb: 8am – 7pm</a></li>
          <li><a href="#">Agendar cita</a></li>
        </ul>
      </div>
    </div>
    <div class="footer-bottom">
      <p class="footer-copy">© 2025 Rejuvenese · Todos los derechos reservados</p>
      <div class="footer-socials">
        <a href="#" class="footer-social">ig</a>
        <a href="#" class="footer-social">fb</a>
        <a href="#" class="footer-social">yt</a>
        <a href="#" class="footer-social">tk</a>
      </div>
    </div>
  </footer>
 
  <script>
    // CURSOR
    const cursor = document.getElementById('cursor');
    const ring   = document.getElementById('cursorRing');
    document.addEventListener('mousemove', e => {
      cursor.style.left = e.clientX + 'px';
      cursor.style.top  = e.clientY + 'px';
      ring.style.left   = e.clientX + 'px';
      ring.style.top    = e.clientY + 'px';
    });
    document.querySelectorAll('a, button, .service-card, .test-card').forEach(el => {
      el.addEventListener('mouseenter', () => {
        cursor.style.width  = '20px';
        cursor.style.height = '20px';
        ring.style.opacity  = '1';
        ring.style.width    = '60px';
        ring.style.height   = '60px';
      });
      el.addEventListener('mouseleave', () => {
        cursor.style.width  = '10px';
        cursor.style.height = '10px';
        ring.style.opacity  = '.5';
        ring.style.width    = '38px';
        ring.style.height   = '38px';
      });
    });
 
    // NAV SCROLL
    const nav = document.getElementById('nav');
    window.addEventListener('scroll', () => {
      nav.classList.toggle('scrolled', window.scrollY > 60);
    });
 
    // REVEAL ON SCROLL
    const reveals = document.querySelectorAll('.reveal');
    const observer = new IntersectionObserver(entries => {
      entries.forEach((e, i) => {
        if (e.isIntersecting) {
          setTimeout(() => e.target.classList.add('visible'), i * 80);
          observer.unobserve(e.target);
        }
      });
    }, { threshold: 0.12 });
    reveals.forEach(r => observer.observe(r));
  </script>
</body>
</html>
