# NexusDigital
Confection et modernisation de sites web.
<!DOCTYPE html>

<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>NEXUS DIGITAL — Architecte du Web</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Cormorant+Garamond:ital,wght@0,300;0,400;1,300&family=DM+Mono:wght@300;400&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

:root {
–black: #060608;
–white: #f4f0e8;
–cream: #ede8dc;
–gold: #c9a84c;
–gold-light: #e8c96a;
–accent: #d4541a;
–grey: #2a2830;
–muted: #7a7570;
}

html { scroll-behavior: smooth; }

body {
background: var(–black);
color: var(–white);
font-family: ‘Cormorant Garamond’, Georgia, serif;
overflow-x: hidden;
cursor: none;
}

/* CURSOR */
.cursor {
width: 12px; height: 12px;
background: var(–gold);
border-radius: 50%;
position: fixed;
top: 0; left: 0;
pointer-events: none;
z-index: 10000;
transform: translate(-50%, -50%);
transition: width .2s, height .2s, background .2s;
mix-blend-mode: difference;
}
.cursor-ring {
width: 40px; height: 40px;
border: 1px solid rgba(201,168,76,0.5);
border-radius: 50%;
position: fixed;
top: 0; left: 0;
pointer-events: none;
z-index: 9999;
transform: translate(-50%, -50%);
transition: all .12s ease-out;
}
body:hover .cursor { opacity: 1; }

/* NOISE OVERLAY */
body::before {
content: ‘’;
position: fixed;
inset: 0;
background-image: url(“data:image/svg+xml,%3Csvg viewBox=‘0 0 256 256’ xmlns=‘http://www.w3.org/2000/svg’%3E%3Cfilter id=‘noise’%3E%3CfeTurbulence type=‘fractalNoise’ baseFrequency=‘0.9’ numOctaves=‘4’ stitchTiles=‘stitch’/%3E%3C/filter%3E%3Crect width=‘100%25’ height=‘100%25’ filter=‘url(%23noise)’ opacity=‘0.04’/%3E%3C/svg%3E”);
opacity: 0.35;
pointer-events: none;
z-index: 9998;
}

/* NAV */
nav {
position: fixed;
top: 0; left: 0; right: 0;
z-index: 1000;
display: flex;
justify-content: space-between;
align-items: center;
padding: 28px 60px;
background: linear-gradient(to bottom, rgba(6,6,8,0.95), transparent);
backdrop-filter: blur(2px);
}
.nav-logo {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 1.6rem;
letter-spacing: 0.2em;
color: var(–gold);
text-decoration: none;
}
.nav-logo span { color: var(–white); }
nav ul { list-style: none; display: flex; gap: 48px; }
nav ul a {
font-family: ‘DM Mono’, monospace;
font-size: 0.68rem;
letter-spacing: 0.18em;
text-transform: uppercase;
color: var(–muted);
text-decoration: none;
transition: color 0.3s;
}
nav ul a:hover { color: var(–gold); }

/* HERO */
.hero {
min-height: 100vh;
display: flex;
flex-direction: column;
justify-content: flex-end;
padding: 0 60px 80px;
position: relative;
overflow: hidden;
}

.hero-bg {
position: absolute;
inset: 0;
background:
radial-gradient(ellipse 70% 60% at 80% 30%, rgba(201,168,76,0.06) 0%, transparent 60%),
radial-gradient(ellipse 50% 70% at 10% 80%, rgba(212,84,26,0.04) 0%, transparent 50%),
var(–black);
z-index: 0;
}

.hero-grid {
position: absolute;
inset: 0;
background-image:
linear-gradient(rgba(201,168,76,0.04) 1px, transparent 1px),
linear-gradient(90deg, rgba(201,168,76,0.04) 1px, transparent 1px);
background-size: 80px 80px;
z-index: 1;
mask-image: linear-gradient(to bottom, transparent 0%, rgba(0,0,0,0.4) 40%, transparent 100%);
}

.hero-number {
position: absolute;
top: 120px;
right: 60px;
font-family: ‘Bebas Neue’, sans-serif;
font-size: 22vw;
color: transparent;
-webkit-text-stroke: 1px rgba(201,168,76,0.08);
letter-spacing: -0.02em;
line-height: 1;
z-index: 1;
user-select: none;
}

.hero-content { position: relative; z-index: 2; max-width: 900px; }

.hero-eyebrow {
font-family: ‘DM Mono’, monospace;
font-size: 0.7rem;
letter-spacing: 0.3em;
color: var(–gold);
text-transform: uppercase;
margin-bottom: 32px;
display: flex;
align-items: center;
gap: 16px;
}
.hero-eyebrow::before {
content: ‘’;
display: block;
width: 40px;
height: 1px;
background: var(–gold);
}

.hero h1 {
font-family: ‘Bebas Neue’, sans-serif;
font-size: clamp(5rem, 11vw, 13rem);
line-height: 0.88;
letter-spacing: -0.01em;
margin-bottom: 40px;
}
.hero h1 em {
font-family: ‘Cormorant Garamond’, Georgia, serif;
font-style: italic;
font-weight: 300;
color: var(–gold);
font-size: 0.75em;
}

.hero-sub {
font-size: 1.2rem;
font-weight: 300;
color: var(–muted);
line-height: 1.7;
max-width: 480px;
margin-bottom: 56px;
}

.hero-cta {
display: flex;
gap: 20px;
align-items: center;
}

.btn-primary {
background: var(–gold);
color: var(–black);
font-family: ‘DM Mono’, monospace;
font-size: 0.72rem;
letter-spacing: 0.2em;
text-transform: uppercase;
text-decoration: none;
padding: 18px 40px;
display: inline-block;
transition: all 0.3s;
position: relative;
overflow: hidden;
}
.btn-primary::after {
content: ‘’;
position: absolute;
inset: 0;
background: var(–accent);
transform: scaleX(0);
transform-origin: left;
transition: transform 0.4s ease;
z-index: -1;
}
.btn-primary:hover { color: var(–white); }
.btn-primary:hover::after { transform: scaleX(1); }

.btn-ghost {
font-family: ‘DM Mono’, monospace;
font-size: 0.72rem;
letter-spacing: 0.2em;
text-transform: uppercase;
color: var(–muted);
text-decoration: none;
display: flex;
align-items: center;
gap: 12px;
transition: color 0.3s;
}
.btn-ghost::after {
content: ‘→’;
font-size: 1rem;
transition: transform 0.3s;
}
.btn-ghost:hover { color: var(–white); }
.btn-ghost:hover::after { transform: translateX(6px); }

.hero-scroll {
position: absolute;
right: 60px;
bottom: 80px;
display: flex;
flex-direction: column;
align-items: center;
gap: 12px;
z-index: 2;
}
.scroll-line {
width: 1px;
height: 60px;
background: linear-gradient(to bottom, var(–gold), transparent);
animation: scrollLine 1.8s ease infinite;
}
@keyframes scrollLine {
0% { transform: scaleY(0); transform-origin: top; opacity: 0; }
50% { transform: scaleY(1); opacity: 1; }
100% { transform: scaleY(0); transform-origin: bottom; opacity: 0; }
}
.scroll-label {
font-family: ‘DM Mono’, monospace;
font-size: 0.55rem;
letter-spacing: 0.3em;
color: var(–muted);
writing-mode: vertical-rl;
}

/* MARQUEE */
.marquee-wrap {
overflow: hidden;
border-top: 1px solid rgba(201,168,76,0.15);
border-bottom: 1px solid rgba(201,168,76,0.15);
padding: 20px 0;
background: rgba(201,168,76,0.03);
}
.marquee-track {
display: flex;
gap: 0;
animation: marquee 20s linear infinite;
white-space: nowrap;
}
.marquee-item {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 1rem;
letter-spacing: 0.3em;
color: var(–muted);
padding: 0 40px;
display: flex;
align-items: center;
gap: 20px;
}
.marquee-item span { color: var(–gold); font-size: 0.6rem; }
@keyframes marquee {
0% { transform: translateX(0); }
100% { transform: translateX(-50%); }
}

/* SECTIONS */
section { position: relative; }

/* ABOUT */
.about {
padding: 160px 60px;
display: grid;
grid-template-columns: 1fr 1.2fr;
gap: 120px;
align-items: center;
}

.section-label {
font-family: ‘DM Mono’, monospace;
font-size: 0.65rem;
letter-spacing: 0.3em;
color: var(–gold);
text-transform: uppercase;
margin-bottom: 24px;
}

.about-left h2 {
font-family: ‘Bebas Neue’, sans-serif;
font-size: clamp(3rem, 5vw, 6rem);
line-height: 0.95;
margin-bottom: 32px;
}
.about-left h2 em {
font-family: ‘Cormorant Garamond’, serif;
font-style: italic;
color: var(–gold);
font-size: 0.9em;
}

.about-right p {
font-size: 1.15rem;
font-weight: 300;
line-height: 1.85;
color: #9a958e;
margin-bottom: 24px;
}
.about-right p strong { color: var(–white); font-weight: 400; }

.stat-row {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 1px;
margin-top: 60px;
border: 1px solid rgba(201,168,76,0.1);
background: rgba(201,168,76,0.1);
}
.stat {
background: var(–black);
padding: 32px 24px;
text-align: center;
}
.stat-num {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 3rem;
color: var(–gold);
line-height: 1;
display: block;
}
.stat-desc {
font-family: ‘DM Mono’, monospace;
font-size: 0.6rem;
letter-spacing: 0.2em;
color: var(–muted);
text-transform: uppercase;
margin-top: 8px;
display: block;
}

/* SERVICES */
.services { padding: 160px 60px; }
.services-header {
display: flex;
justify-content: space-between;
align-items: flex-end;
margin-bottom: 80px;
border-bottom: 1px solid rgba(255,255,255,0.06);
padding-bottom: 40px;
}
.services-header h2 {
font-family: ‘Bebas Neue’, sans-serif;
font-size: clamp(3rem, 5vw, 6rem);
line-height: 0.95;
}
.services-header h2 em {
font-family: ‘Cormorant Garamond’, serif;
font-style: italic;
color: var(–gold);
font-size: 0.85em;
}
.services-intro {
max-width: 300px;
font-size: 0.95rem;
color: var(–muted);
line-height: 1.7;
text-align: right;
}

.services-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 1px; background: rgba(201,168,76,0.08); }
.service-card {
background: var(–black);
padding: 80px 64px;
position: relative;
overflow: hidden;
transition: background 0.4s;
cursor: pointer;
}
.service-card::before {
content: ‘’;
position: absolute;
top: 0; left: 0; right: 0;
height: 2px;
background: linear-gradient(90deg, var(–gold), transparent);
transform: scaleX(0);
transform-origin: left;
transition: transform 0.4s;
}
.service-card:hover { background: rgba(201,168,76,0.03); }
.service-card:hover::before { transform: scaleX(1); }

.service-num {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 6rem;
color: transparent;
-webkit-text-stroke: 1px rgba(201,168,76,0.15);
line-height: 1;
margin-bottom: 28px;
}
.service-card h3 {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 2.4rem;
letter-spacing: 0.05em;
margin-bottom: 20px;
color: var(–white);
}
.service-card p {
font-size: 1.05rem;
color: var(–muted);
line-height: 1.85;
font-weight: 300;
}
.service-tag {
display: inline-block;
margin-top: 28px;
font-family: ‘DM Mono’, monospace;
font-size: 0.6rem;
letter-spacing: 0.2em;
color: var(–gold);
border: 1px solid rgba(201,168,76,0.3);
padding: 6px 14px;
text-transform: uppercase;
}

/* PROCESS */
.process { padding: 160px 60px; background: var(–grey); }
.process h2 {
font-family: ‘Bebas Neue’, sans-serif;
font-size: clamp(3rem, 5vw, 6rem);
line-height: 0.95;
margin-bottom: 80px;
text-align: center;
}
.process h2 em {
font-family: ‘Cormorant Garamond’, serif;
font-style: italic;
color: var(–gold);
font-size: 0.85em;
}
.steps {
display: grid;
grid-template-columns: repeat(4, 1fr);
gap: 0;
position: relative;
}
.steps::before {
content: ‘’;
position: absolute;
top: 30px; left: 12.5%; right: 12.5%;
height: 1px;
background: linear-gradient(90deg, transparent, var(–gold), transparent);
}
.step { padding: 0 32px; text-align: center; }
.step-dot {
width: 60px; height: 60px;
border: 1px solid rgba(201,168,76,0.4);
border-radius: 50%;
display: flex; align-items: center; justify-content: center;
margin: 0 auto 32px;
font-family: ‘Bebas Neue’, sans-serif;
font-size: 1.2rem;
color: var(–gold);
background: var(–grey);
position: relative;
z-index: 1;
}
.step h4 {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 1.3rem;
letter-spacing: 0.05em;
margin-bottom: 12px;
}
.step p {
font-size: 0.88rem;
color: var(–muted);
line-height: 1.7;
}

/* PORTFOLIO - SITES LINKS */
.portfolio { padding: 160px 60px; }
.portfolio-header { margin-bottom: 80px; }
.portfolio-header h2 {
font-family: ‘Bebas Neue’, sans-serif;
font-size: clamp(3rem, 5vw, 6rem);
line-height: 0.95;
}
.portfolio-header h2 em {
font-family: ‘Cormorant Garamond’, serif;
font-style: italic;
color: var(–gold);
font-size: 0.85em;
}

.portfolio-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 2px; }

.portfolio-item {
position: relative;
overflow: hidden;
background: var(–grey);
aspect-ratio: 16/10;
display: flex;
flex-direction: column;
justify-content: flex-end;
padding: 40px;
text-decoration: none;
color: var(–white);
transition: all 0.5s;
}
.portfolio-item::before {
content: ‘’;
position: absolute;
inset: 0;
background: linear-gradient(to top, rgba(6,6,8,0.9) 0%, rgba(6,6,8,0.2) 50%, transparent 100%);
z-index: 1;
}
.portfolio-item:hover { transform: scale(1.01); }

.portfolio-bg {
position: absolute;
inset: 0;
z-index: 0;
transition: transform 0.6s ease;
}
.portfolio-item:hover .portfolio-bg { transform: scale(1.05); }

.portfolio-bg-1 {
background:
radial-gradient(ellipse at 30% 60%, rgba(180,40,20,0.4), transparent 60%),
radial-gradient(ellipse at 80% 20%, rgba(201,120,40,0.3), transparent 50%),
linear-gradient(135deg, #1a0a06 0%, #2d1208 100%);
}
.portfolio-bg-2 {
background:
radial-gradient(ellipse at 70% 40%, rgba(20,80,40,0.5), transparent 60%),
radial-gradient(ellipse at 20% 80%, rgba(60,120,80,0.3), transparent 50%),
linear-gradient(135deg, #060f08 0%, #0a1a0e 100%);
}

.portfolio-item-content { position: relative; z-index: 2; }
.portfolio-label {
font-family: ‘DM Mono’, monospace;
font-size: 0.6rem;
letter-spacing: 0.3em;
color: var(–gold);
text-transform: uppercase;
margin-bottom: 8px;
display: block;
}
.portfolio-item h3 {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 2.2rem;
letter-spacing: 0.05em;
margin-bottom: 8px;
}
.portfolio-item p {
font-size: 0.88rem;
color: rgba(244,240,232,0.7);
font-weight: 300;
margin-bottom: 20px;
}
.portfolio-link {
font-family: ‘DM Mono’, monospace;
font-size: 0.65rem;
letter-spacing: 0.2em;
text-transform: uppercase;
color: var(–gold);
display: flex;
align-items: center;
gap: 8px;
border: 1px solid rgba(201,168,76,0.4);
padding: 10px 20px;
width: fit-content;
transition: all 0.3s;
}
.portfolio-item:hover .portfolio-link {
background: var(–gold);
color: var(–black);
}

/* PRICING */
.pricing { padding: 160px 60px; background: linear-gradient(180deg, var(–black) 0%, rgba(42,40,48,0.3) 100%); }
.pricing h2 {
font-family: ‘Bebas Neue’, sans-serif;
font-size: clamp(3rem, 5vw, 6rem);
line-height: 0.95;
text-align: center;
margin-bottom: 80px;
}
.pricing h2 em {
font-family: ‘Cormorant Garamond’, serif;
font-style: italic;
color: var(–gold);
font-size: 0.85em;
}

.pricing-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 2px; background: rgba(201,168,76,0.08); }
.price-card {
background: var(–black);
padding: 60px 40px;
position: relative;
transition: background 0.3s;
}
.price-card.featured {
background: rgba(201,168,76,0.06);
border-top: 2px solid var(–gold);
}
.price-card:hover { background: rgba(201,168,76,0.04); }

.price-badge {
font-family: ‘DM Mono’, monospace;
font-size: 0.6rem;
letter-spacing: 0.3em;
background: var(–gold);
color: var(–black);
padding: 4px 12px;
text-transform: uppercase;
position: absolute;
top: 24px; right: 24px;
}
.price-tier {
font-family: ‘DM Mono’, monospace;
font-size: 0.65rem;
letter-spacing: 0.3em;
color: var(–muted);
text-transform: uppercase;
margin-bottom: 20px;
}
.price-name {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 2.2rem;
letter-spacing: 0.03em;
margin-bottom: 8px;
}
.price-amount {
font-family: ‘Cormorant Garamond’, serif;
font-size: 3.5rem;
font-weight: 300;
color: var(–gold);
line-height: 1;
margin: 20px 0;
}
.price-amount sup { font-size: 1.5rem; vertical-align: super; }
.price-from { font-family: ‘DM Mono’, monospace; font-size: 0.6rem; color: var(–muted); letter-spacing: 0.1em; }
.price-divider { height: 1px; background: rgba(255,255,255,0.06); margin: 28px 0; }
.price-features { list-style: none; }
.price-features li {
font-size: 0.9rem;
color: var(–muted);
padding: 10px 0;
border-bottom: 1px solid rgba(255,255,255,0.04);
display: flex;
align-items: center;
gap: 10px;
}
.price-features li::before {
content: ‘◆’;
color: var(–gold);
font-size: 0.4rem;
flex-shrink: 0;
}
.price-cta {
display: block;
text-align: center;
margin-top: 36px;
padding: 16px;
font-family: ‘DM Mono’, monospace;
font-size: 0.68rem;
letter-spacing: 0.2em;
text-transform: uppercase;
text-decoration: none;
border: 1px solid rgba(201,168,76,0.3);
color: var(–gold);
transition: all 0.3s;
}
.price-cta:hover { background: var(–gold); color: var(–black); }
.price-card.featured .price-cta { background: var(–gold); color: var(–black); }
.price-card.featured .price-cta:hover { background: var(–accent); border-color: var(–accent); color: var(–white); }

/* CONTACT */
.contact { padding: 160px 60px; position: relative; overflow: hidden; }
.contact-bg {
position: absolute;
inset: 0;
background: radial-gradient(ellipse 80% 80% at 50% 50%, rgba(201,168,76,0.04) 0%, transparent 70%);
z-index: 0;
}
.contact-inner { position: relative; z-index: 1; max-width: 800px; margin: 0 auto; text-align: center; }
.contact h2 {
font-family: ‘Bebas Neue’, sans-serif;
font-size: clamp(3rem, 7vw, 9rem);
line-height: 0.88;
margin-bottom: 32px;
}
.contact h2 em {
font-family: ‘Cormorant Garamond’, serif;
font-style: italic;
color: var(–gold);
font-size: 0.85em;
}
.contact p {
font-size: 1.1rem;
color: var(–muted);
line-height: 1.8;
margin-bottom: 56px;
font-weight: 300;
}
.contact-email {
display: block;
font-family: ‘Bebas Neue’, sans-serif;
font-size: clamp(1.5rem, 3vw, 3rem);
color: var(–gold);
text-decoration: none;
letter-spacing: 0.05em;
margin-bottom: 56px;
transition: color 0.3s;
}
.contact-email:hover { color: var(–white); }

/* FOOTER */
footer {
border-top: 1px solid rgba(255,255,255,0.06);
padding: 40px 60px;
display: flex;
justify-content: space-between;
align-items: center;
}
.footer-logo {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 1.2rem;
letter-spacing: 0.15em;
color: var(–gold);
}
.footer-copy {
font-family: ‘DM Mono’, monospace;
font-size: 0.6rem;
letter-spacing: 0.15em;
color: var(–muted);
}
.footer-links { display: flex; gap: 32px; }
.footer-links a {
font-family: ‘DM Mono’, monospace;
font-size: 0.6rem;
letter-spacing: 0.15em;
color: var(–muted);
text-decoration: none;
text-transform: uppercase;
transition: color 0.3s;
}
.footer-links a:hover { color: var(–gold); }

/* ANIMATIONS */
.reveal {
opacity: 0;
transform: translateY(30px);
transition: opacity 0.8s ease, transform 0.8s ease;
}
.reveal.visible {
opacity: 1;
transform: translateY(0);
}

@media (max-width: 900px) {
nav { padding: 20px 24px; }
nav ul { display: none; }
.hero { padding: 0 24px 60px; }
.about { grid-template-columns: 1fr; padding: 80px 24px; gap: 48px; }
.services { padding: 80px 24px; }
.services-grid { grid-template-columns: 1fr; }
.steps { grid-template-columns: 1fr 1fr; gap: 48px; }
.steps::before { display: none; }
.portfolio-grid { grid-template-columns: 1fr; }
.pricing-grid { grid-template-columns: 1fr; }
.pricing { padding: 80px 24px; }
.contact { padding: 80px 24px; }
footer { flex-direction: column; gap: 20px; text-align: center; }
.hero-number { font-size: 40vw; top: 80px; right: 0; }
}
</style>

</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- NAV -->

<nav>
  <a href="#" class="nav-logo">NEXUS<span>DIGITAL</span></a>
  <ul>
    <li><a href="#services">Services</a></li>
    <li><a href="#processus">Processus</a></li>
    <li><a href="#portfolio">Portfolio</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<!-- HERO -->

<section class="hero">
  <div class="hero-bg"></div>
  <div class="hero-grid"></div>
  <div class="hero-number">WEB</div>

  <div class="hero-content">
    <div class="hero-eyebrow">Architecte du Web Premium</div>
    <h1>
      Votre Présence<br>
      <em>Réinventée.</em>
    </h1>
    <p class="hero-sub">
      Nous créons et reconstruisons les sites web d'entreprise avec une exigence absolue — alliant esthétique de haute couture et performances techniques d'élite.
    </p>
    <div class="hero-cta">
      <a href="#contact" class="btn-primary">Démarrer un projet</a>
      <a href="#portfolio" class="btn-ghost">Voir les réalisations</a>
    </div>
  </div>

  <div class="hero-scroll">
    <div class="scroll-line"></div>
    <span class="scroll-label">DÉFILER</span>
  </div>
</section>

<!-- MARQUEE -->

<div class="marquee-wrap">
  <div class="marquee-track">
    <div class="marquee-item">Création de sites <span>✦</span></div>
    <div class="marquee-item">Reconstruction digitale <span>✦</span></div>
    <div class="marquee-item">Design d'excellence <span>✦</span></div>
    <div class="marquee-item">Performance & SEO <span>✦</span></div>
    <div class="marquee-item">Expérience utilisateur <span>✦</span></div>
    <div class="marquee-item">Identité web <span>✦</span></div>
    <div class="marquee-item">Création de sites <span>✦</span></div>
    <div class="marquee-item">Reconstruction digitale <span>✦</span></div>
    <div class="marquee-item">Design d'excellence <span>✦</span></div>
    <div class="marquee-item">Performance & SEO <span>✦</span></div>
    <div class="marquee-item">Expérience utilisateur <span>✦</span></div>
    <div class="marquee-item">Identité web <span>✦</span></div>
  </div>
</div>

<!-- ABOUT -->

<section class="about" id="about">
  <div class="about-left reveal">
    <div class="section-label">À propos</div>
    <h2>L'Art du<br>Web <em>Maîtrisé.</em></h2>
    <div class="stat-row">
      <div class="stat"><span class="stat-num">87+</span><span class="stat-desc">Sites créés</span></div>
      <div class="stat"><span class="stat-num">100%</span><span class="stat-desc">Satisfaction</span></div>
      <div class="stat"><span class="stat-num">5★</span><span class="stat-desc">Note moyenne</span></div>
    </div>
  </div>
  <div class="about-right reveal">
    <p>Dans un monde où la première impression est <strong>digitale</strong>, votre site web n'est pas une simple vitrine — c'est votre ambassadeur, votre commercial, votre image de marque fusionnés en une expérience unique.</p>
    <p>Chez <strong>NEXUS DIGITAL</strong>, nous ne nous contentons pas de construire des sites. Nous <strong>architecturons des présences digitales</strong> qui convertissent, fidélisent et distinguent les entreprises qui osent l'excellence.</p>
    <p>Que vous partiez de zéro ou que vous souhaitiez <strong>reconstruire intégralement</strong> un site obsolète, notre approche sur-mesure garantit un résultat à la hauteur de vos ambitions.</p>
  </div>
</section>

<!-- SERVICES -->

<section class="services" id="services">
  <div class="services-header reveal">
    <div>
      <div class="section-label">Ce que nous faisons</div>
      <h2>Nos <em>Services</em><br>Clés en Main</h2>
    </div>
    <p class="services-intro">Chaque projet est traité avec la même rigueur : zéro compromis sur la qualité, zéro délai non respecté.</p>
  </div>

  <div class="services-grid">
    <div class="service-card reveal">
      <div class="service-num">01</div>
      <h3>Création de Site Web</h3>
      <p>Votre entreprise mérite une présence digitale pensée de A à Z. Nous concevons votre site depuis la stratégie jusqu'au lancement : design exclusif, code sur-mesure, performances optimales et expérience utilisateur pensée pour convertir vos visiteurs en clients.</p>
      <span class="service-tag">Sur mesure · Clé en main</span>
    </div>
    <div class="service-card reveal">
      <div class="service-num">02</div>
      <h3>Rénovation de Site Web</h3>
      <p>Votre site actuel ne vous représente plus ? Nous prenons en charge la refonte intégrale de votre présence digitale — nouveau design, nouvelle architecture, migration de contenu, SEO optimisé — pour un résultat qui vous ressemble enfin.</p>
      <span class="service-tag">Refonte totale · Migration incluse</span>
    </div>
  </div>
</section>

<!-- PROCESS -->

<section class="process" id="processus">
  <h2 class="reveal">Notre <em>Processus</em></h2>
  <div class="steps">
    <div class="step reveal">
      <div class="step-dot">01</div>
      <h4>Découverte</h4>
      <p>Audit complet de vos besoins, de votre secteur et de votre concurrence pour définir une stratégie gagnante.</p>
    </div>
    <div class="step reveal">
      <div class="step-dot">02</div>
      <h4>Conception</h4>
      <p>Maquettes interactives et design system unique créés selon votre identité de marque et vos objectifs.</p>
    </div>
    <div class="step reveal">
      <div class="step-dot">03</div>
      <h4>Développement</h4>
      <p>Code de haute qualité, optimisé pour la performance, la sécurité et la compatibilité multi-appareils.</p>
    </div>
    <div class="step reveal">
      <div class="step-dot">04</div>
      <h4>Lancement</h4>
      <p>Déploiement accompagné, formation à la gestion du site et suivi post-lancement pendant 30 jours.</p>
    </div>
  </div>
</section>

<!-- PORTFOLIO -->

<section class="portfolio" id="portfolio">
  <div class="portfolio-header reveal">
    <div class="section-label">Réalisations</div>
    <h2>Des Sites qui<br><em>Impressionnent.</em></h2>
  </div>
  <div class="portfolio-grid">
    <a href="brasa.html" class="portfolio-item reveal">
      <div class="portfolio-bg portfolio-bg-1"></div>
      <div class="portfolio-item-content">
        <span class="portfolio-label">Restauration / Brésilien</span>
        <h3>BRASA & FOGO</h3>
        <p>Restaurant de grillades brésiliennes — Ambiance feu & passion</p>
        <div class="portfolio-link">Voir le site →</div>
      </div>
    </a>
    <a href="jardin.html" class="portfolio-item reveal">
      <div class="portfolio-bg portfolio-bg-2"></div>
      <div class="portfolio-item-content">
        <span class="portfolio-label">Restauration / Gastronomique</span>
        <h3>LE JARDIN SECRET</h3>
        <p>Restaurant gastronomique végétal — Élégance naturelle</p>
        <div class="portfolio-link">Voir le site →</div>
      </div>
    </a>
  </div>
</section>

<!-- CONTACT -->

<section class="contact" id="contact">
  <div class="contact-bg"></div>
  <div class="contact-inner">
    <div class="section-label reveal">Parlons-en</div>
    <h2 class="reveal">Prêt à<br><em>Transformer</em><br>Votre Web ?</h2>
    <p class="reveal">Un projet, une question, une simple envie d'explorer les possibilités ? Chaque grande collaboration commence par une conversation.</p>
    <a href="mailto:contact@nexusdigital.fr" class="contact-email reveal">contact@nexusdigital.fr</a>
    <a href="mailto:contact@nexusdigital.fr" class="btn-primary reveal">Envoyer un message</a>
  </div>
</section>

<!-- FOOTER -->

<footer>
  <div class="footer-logo">NEXUS DIGITAL</div>
  <div class="footer-links">
    <a href="brasa.html">Brasa & Fogo</a>
    <a href="jardin.html">Le Jardin Secret</a>
    <a href="#contact">Contact</a>
  </div>
  <div class="footer-copy">© 2025 NEXUS DIGITAL — Tous droits réservés</div>
</footer>

<script>
  // Custom cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;
  document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; cursor.style.left = mx + 'px'; cursor.style.top = my + 'px'; });
  function animRing() { rx += (mx - rx) * 0.12; ry += (my - ry) * 0.12; ring.style.left = rx + 'px'; ring.style.top = ry + 'px'; requestAnimationFrame(animRing); }
  animRing();

  // Hover effects on interactive elements
  document.querySelectorAll('a, button, .service-card, .portfolio-item').forEach(el => {
    el.addEventListener('mouseenter', () => { cursor.style.width = '20px'; cursor.style.height = '20px'; ring.style.width = '60px'; ring.style.height = '60px'; });
    el.addEventListener('mouseleave', () => { cursor.style.width = '12px'; cursor.style.height = '12px'; ring.style.width = '40px'; ring.style.height = '40px'; });
  });

  // Reveal on scroll
  const reveals = document.querySelectorAll('.reveal');
  const obs = new IntersectionObserver((entries) => {
    entries.forEach((e, i) => {
      if (e.isIntersecting) {
        setTimeout(() => e.target.classList.add('visible'), i * 80);
      }
    });
  }, { threshold: 0.1, rootMargin: '0px 0px -50px 0px' });
  reveals.forEach(r => obs.observe(r));
</script>

</body>
</html>