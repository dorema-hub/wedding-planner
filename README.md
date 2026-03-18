<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>The Ultimate Wedding Planner Spreadsheet – Plan Your Dream Day</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet" />
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --rose: #C0506A;
    --rose-light: #F9EEF1;
    --rose-mid: #E8B4BF;
    --rose-dark: #7A2E40;
    --gold: #B8893A;
    --gold-light: #F7F0E3;
    --gold-mid: #DDB96A;
    --sage: #6A8A6D;
    --sage-light: #EBF0EB;
    --cream: #FBF8F3;
    --ink: #1E1612;
    --ink-mid: #4A3D38;
    --ink-soft: #7A6E68;
    --white: #FFFFFF;
    --border: rgba(192, 80, 106, 0.15);
  }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--cream);
    color: var(--ink);
    line-height: 1.7;
    overflow-x: hidden;
  }

  /* ── NAV ── */
  nav {
    background: var(--white);
    border-bottom: 1px solid var(--border);
    padding: 18px 5%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    position: sticky;
    top: 0;
    z-index: 100;
  }
  .nav-logo {
    font-family: 'Playfair Display', serif;
    font-size: 1.25rem;
    color: var(--rose);
    letter-spacing: 0.02em;
  }
  .nav-cta {
    background: var(--rose);
    color: var(--white);
    font-size: 0.85rem;
    font-weight: 600;
    padding: 10px 22px;
    border-radius: 50px;
    text-decoration: none;
    letter-spacing: 0.04em;
    transition: background 0.2s;
  }
  .nav-cta:hover { background: var(--rose-dark); }

  /* ── HERO ── */
  .hero {
    background: var(--white);
    padding: 80px 5% 70px;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 60px;
    align-items: center;
    border-bottom: 1px solid var(--border);
  }
  .hero-badge {
    display: inline-block;
    background: var(--rose-light);
    color: var(--rose);
    font-size: 0.75rem;
    font-weight: 600;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    padding: 6px 16px;
    border-radius: 50px;
    margin-bottom: 20px;
  }
  .hero h1 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2rem, 4vw, 3.2rem);
    line-height: 1.2;
    color: var(--ink);
    margin-bottom: 20px;
  }
  .hero h1 em {
    font-style: italic;
    color: var(--rose);
  }
  .hero-sub {
    font-size: 1.05rem;
    color: var(--ink-mid);
    max-width: 480px;
    margin-bottom: 36px;
    line-height: 1.8;
  }
  .hero-actions { display: flex; gap: 14px; align-items: center; flex-wrap: wrap; }
  .btn-primary {
    background: var(--rose);
    color: var(--white);
    font-size: 1rem;
    font-weight: 600;
    padding: 16px 36px;
    border-radius: 50px;
    text-decoration: none;
    letter-spacing: 0.02em;
    transition: background 0.2s, transform 0.15s;
    display: inline-block;
  }
  .btn-primary:hover { background: var(--rose-dark); transform: translateY(-1px); }
  .btn-secondary {
    color: var(--rose);
    font-size: 0.95rem;
    font-weight: 500;
    text-decoration: none;
    border-bottom: 1.5px solid var(--rose-mid);
    padding-bottom: 2px;
  }
  .hero-price-note {
    font-size: 0.82rem;
    color: var(--ink-soft);
    margin-top: 14px;
  }

  /* hero mockup */
  .hero-visual {
    position: relative;
  }
  .spreadsheet-mock {
    background: var(--white);
    border: 1px solid var(--border);
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 2px 32px rgba(192,80,106,0.10);
  }
  .mock-topbar {
    background: var(--rose);
    padding: 10px 16px;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .mock-dot { width: 10px; height: 10px; border-radius: 50%; background: rgba(255,255,255,0.4); }
  .mock-title {
    color: rgba(255,255,255,0.9);
    font-size: 0.75rem;
    font-weight: 500;
    margin-left: 6px;
    letter-spacing: 0.03em;
  }
  .mock-tabs {
    background: #F5F0F1;
    display: flex;
    gap: 2px;
    padding: 6px 10px 0;
    border-bottom: 1px solid var(--border);
    overflow-x: auto;
  }
  .mock-tab {
    font-size: 0.7rem;
    padding: 5px 12px;
    border-radius: 6px 6px 0 0;
    color: var(--ink-soft);
    white-space: nowrap;
  }
  .mock-tab.active {
    background: var(--white);
    color: var(--rose);
    font-weight: 600;
    border: 1px solid var(--border);
    border-bottom: none;
  }
  .mock-body { padding: 14px; }
  .mock-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
    margin-bottom: 12px;
  }
  .mock-card {
    background: var(--rose-light);
    border-radius: 8px;
    padding: 12px 14px;
  }
  .mock-card-label { font-size: 0.65rem; color: var(--rose); font-weight: 600; text-transform: uppercase; letter-spacing: 0.08em; margin-bottom: 4px; }
  .mock-card-value { font-size: 1.1rem; font-weight: 600; color: var(--rose-dark); font-family: 'Playfair Display', serif; }
  .mock-progress-label { font-size: 0.7rem; color: var(--ink-soft); margin-bottom: 6px; }
  .mock-bar-track { background: #EEEBE9; border-radius: 50px; height: 7px; margin-bottom: 8px; }
  .mock-bar-fill { background: var(--rose); height: 100%; border-radius: 50px; }
  .mock-row {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 6px 0;
    border-bottom: 1px solid #F0ECE8;
    font-size: 0.72rem;
    color: var(--ink-mid);
  }
  .mock-row:last-child { border-bottom: none; }
  .mock-row-dot { width: 7px; height: 7px; border-radius: 50%; flex-shrink: 0; }
  .mock-row-text { flex: 1; }
  .mock-row-badge {
    font-size: 0.62rem;
    padding: 2px 8px;
    border-radius: 50px;
    font-weight: 600;
    background: var(--gold-light);
    color: var(--gold);
  }
  .mock-row-badge.high { background: #FEE8E8; color: #C03030; }
  .mock-row-badge.done { background: var(--sage-light); color: var(--sage); }

  /* ── SOCIAL PROOF STRIP ── */
  .social-strip {
    background: var(--rose-light);
    padding: 18px 5%;
    display: flex;
    justify-content: center;
    gap: 40px;
    flex-wrap: wrap;
    border-bottom: 1px solid var(--border);
  }
  .social-stat { text-align: center; }
  .social-stat-num {
    font-family: 'Playfair Display', serif;
    font-size: 1.6rem;
    font-weight: 700;
    color: var(--rose);
  }
  .social-stat-label { font-size: 0.78rem; color: var(--ink-soft); margin-top: 2px; }

  /* ── SECTION WRAPPER ── */
  section { padding: 80px 5%; }

  .section-label {
    font-size: 0.75rem;
    font-weight: 600;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--rose);
    margin-bottom: 12px;
  }
  .section-heading {
    font-family: 'Playfair Display', serif;
    font-size: clamp(1.6rem, 3vw, 2.4rem);
    line-height: 1.25;
    color: var(--ink);
    max-width: 600px;
    margin-bottom: 16px;
  }
  .section-sub {
    font-size: 1rem;
    color: var(--ink-mid);
    max-width: 560px;
    line-height: 1.8;
    margin-bottom: 48px;
  }

  /* ── PAIN / DREAM ── */
  .pain-dream {
    background: var(--ink);
    color: var(--white);
    padding: 80px 5%;
  }
  .pain-dream-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 40px;
    max-width: 900px;
    margin: 0 auto;
  }
  .pain-box, .dream-box {
    padding: 36px;
    border-radius: 16px;
  }
  .pain-box { background: rgba(255,255,255,0.06); border: 1px solid rgba(255,255,255,0.12); }
  .dream-box { background: rgba(192,80,106,0.15); border: 1px solid rgba(192,80,106,0.3); }
  .pain-dream h3 {
    font-family: 'Playfair Display', serif;
    font-size: 1.2rem;
    margin-bottom: 20px;
    color: rgba(255,255,255,0.6);
  }
  .dream-box h3 { color: var(--rose-mid); }
  .pain-dream li {
    list-style: none;
    display: flex;
    gap: 12px;
    align-items: flex-start;
    margin-bottom: 12px;
    font-size: 0.92rem;
    color: rgba(255,255,255,0.75);
    line-height: 1.6;
  }
  .pain-dream .icon { font-size: 0.85rem; flex-shrink: 0; margin-top: 3px; }
  .dream-box li { color: rgba(255,255,255,0.9); }
  .pain-dream-intro {
    text-align: center;
    margin-bottom: 48px;
  }
  .pain-dream-intro h2 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(1.5rem, 3vw, 2.2rem);
    color: var(--white);
    margin-bottom: 12px;
  }
  .pain-dream-intro p {
    color: rgba(255,255,255,0.6);
    font-size: 1rem;
    max-width: 500px;
    margin: 0 auto;
  }

  /* ── FEATURES GRID ── */
  .features-bg { background: var(--white); }
  .features-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
    gap: 24px;
    margin-top: 0;
  }
  .feature-card {
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 28px 26px;
    background: var(--cream);
    transition: border-color 0.2s;
  }
  .feature-card:hover { border-color: var(--rose-mid); }
  .feature-icon {
    width: 44px;
    height: 44px;
    background: var(--rose-light);
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 16px;
  }
  .feature-icon svg { width: 22px; height: 22px; }
  .feature-card h3 {
    font-family: 'Playfair Display', serif;
    font-size: 1.05rem;
    color: var(--ink);
    margin-bottom: 8px;
  }
  .feature-card p { font-size: 0.88rem; color: var(--ink-soft); line-height: 1.7; }

  /* ── WHAT'S INSIDE ── */
  .inside-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
    gap: 18px;
  }
  .inside-card {
    background: var(--white);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 24px 20px;
    text-align: center;
  }
  .inside-num {
    font-family: 'Playfair Display', serif;
    font-size: 2rem;
    color: var(--rose);
    font-weight: 700;
    line-height: 1;
    margin-bottom: 8px;
  }
  .inside-label {
    font-size: 0.88rem;
    font-weight: 600;
    color: var(--ink);
    margin-bottom: 6px;
  }
  .inside-desc { font-size: 0.78rem; color: var(--ink-soft); line-height: 1.6; }

  /* ── TESTIMONIALS ── */
  .testimonials-bg { background: var(--rose-light); }
  .testimonials-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 22px;
  }
  .testi-card {
    background: var(--white);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 28px 24px;
  }
  .testi-stars { color: var(--gold); font-size: 0.85rem; margin-bottom: 12px; letter-spacing: 2px; }
  .testi-text {
    font-size: 0.92rem;
    color: var(--ink-mid);
    line-height: 1.75;
    margin-bottom: 18px;
    font-style: italic;
  }
  .testi-author { font-size: 0.82rem; font-weight: 600; color: var(--rose); }
  .testi-detail { font-size: 0.78rem; color: var(--ink-soft); }

  /* ── PINTEREST / PROMO ── */
  .promo-bg { background: var(--cream); }
  .promo-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 60px;
    align-items: center;
  }
  .promo-steps { list-style: none; counter-reset: step; }
  .promo-step {
    display: flex;
    gap: 18px;
    align-items: flex-start;
    margin-bottom: 24px;
    counter-increment: step;
  }
  .step-num {
    width: 32px;
    height: 32px;
    border-radius: 50%;
    background: var(--rose);
    color: var(--white);
    font-size: 0.8rem;
    font-weight: 700;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
    margin-top: 2px;
  }
  .step-content h4 { font-size: 0.95rem; font-weight: 600; color: var(--ink); margin-bottom: 4px; }
  .step-content p { font-size: 0.85rem; color: var(--ink-soft); line-height: 1.65; }
  .promo-pin-cards {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 14px;
  }
  .pin-card {
    border-radius: 12px;
    overflow: hidden;
    border: 1px solid var(--border);
  }
  .pin-img {
    height: 120px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Playfair Display', serif;
    font-size: 0.9rem;
    color: var(--white);
    text-align: center;
    padding: 12px;
    line-height: 1.4;
  }
  .pin-img.rose { background: var(--rose); }
  .pin-img.gold { background: var(--gold); }
  .pin-img.sage { background: var(--sage); }
  .pin-img.ink { background: var(--ink-mid); }
  .pin-label { padding: 10px 12px; background: var(--white); font-size: 0.68rem; color: var(--ink-soft); font-weight: 500; }

  /* ── PRICING ── */
  .pricing-bg { background: var(--white); }
  .pricing-card {
    max-width: 460px;
    margin: 0 auto;
    background: var(--cream);
    border: 2px solid var(--rose);
    border-radius: 20px;
    padding: 46px 44px;
    text-align: center;
    position: relative;
    overflow: hidden;
  }
  .pricing-bestseller {
    position: absolute;
    top: 0; right: 0;
    background: var(--rose);
    color: var(--white);
    font-size: 0.72rem;
    font-weight: 700;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    padding: 8px 20px;
    border-radius: 0 0 0 12px;
  }
  .pricing-name {
    font-size: 0.8rem;
    font-weight: 600;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--rose);
    margin-bottom: 14px;
  }
  .pricing-price {
    font-family: 'Playfair Display', serif;
    font-size: 3.6rem;
    color: var(--ink);
    line-height: 1;
    margin-bottom: 6px;
  }
  .pricing-price span { font-size: 1.4rem; vertical-align: top; margin-top: 12px; display: inline-block; }
  .pricing-old {
    font-size: 0.88rem;
    color: var(--ink-soft);
    text-decoration: line-through;
    margin-bottom: 20px;
  }
  .pricing-includes {
    list-style: none;
    margin: 24px 0 32px;
    text-align: left;
  }
  .pricing-includes li {
    display: flex;
    gap: 10px;
    align-items: flex-start;
    font-size: 0.9rem;
    color: var(--ink-mid);
    padding: 6px 0;
    border-bottom: 1px solid var(--border);
  }
  .pricing-includes li:last-child { border-bottom: none; }
  .pricing-includes .check { color: var(--sage); font-weight: 700; flex-shrink: 0; }
  .pricing-guarantee { font-size: 0.78rem; color: var(--ink-soft); margin-top: 16px; }

  /* ── FAQ ── */
  .faq-bg { background: var(--cream); }
  .faq-list { max-width: 700px; margin: 0 auto; }
  .faq-item {
    border-bottom: 1px solid var(--border);
    padding: 20px 0;
  }
  .faq-q {
    font-size: 0.97rem;
    font-weight: 600;
    color: var(--ink);
    cursor: pointer;
    display: flex;
    justify-content: space-between;
    gap: 16px;
    user-select: none;
  }
  .faq-q .faq-toggle { color: var(--rose); font-size: 1.2rem; flex-shrink: 0; }
  .faq-a {
    font-size: 0.88rem;
    color: var(--ink-soft);
    line-height: 1.75;
    margin-top: 12px;
    display: none;
  }
  .faq-item.open .faq-a { display: block; }
  .faq-item.open .faq-toggle { transform: rotate(45deg); display: inline-block; transition: transform 0.2s; }

  /* ── FINAL CTA ── */
  .final-cta {
    background: var(--rose);
    color: var(--white);
    text-align: center;
    padding: 90px 5%;
  }
  .final-cta h2 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(1.8rem, 4vw, 3rem);
    margin-bottom: 16px;
    line-height: 1.25;
  }
  .final-cta p {
    font-size: 1.05rem;
    opacity: 0.85;
    max-width: 500px;
    margin: 0 auto 36px;
    line-height: 1.75;
  }
  .btn-white {
    background: var(--white);
    color: var(--rose);
    font-size: 1rem;
    font-weight: 700;
    padding: 16px 42px;
    border-radius: 50px;
    text-decoration: none;
    display: inline-block;
    transition: opacity 0.2s, transform 0.15s;
  }
  .btn-white:hover { opacity: 0.92; transform: translateY(-1px); }
  .final-cta-note { font-size: 0.8rem; opacity: 0.7; margin-top: 16px; }

  /* ── FOOTER ── */
  footer {
    background: var(--ink);
    color: rgba(255,255,255,0.5);
    text-align: center;
    padding: 28px 5%;
    font-size: 0.78rem;
  }
  footer a { color: var(--rose-mid); text-decoration: none; }

  /* ── RESPONSIVE ── */
  @media (max-width: 768px) {
    .hero { grid-template-columns: 1fr; padding: 50px 5%; }
    .hero-visual { order: -1; }
    .pain-dream-grid { grid-template-columns: 1fr; }
    .promo-grid { grid-template-columns: 1fr; }
    .social-strip { gap: 24px; }
    .pricing-card { padding: 36px 28px; }
  }

  /* ── ANIMATIONS ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  .hero-text { animation: fadeUp 0.7s ease both; }
  .hero-visual { animation: fadeUp 0.7s 0.15s ease both; }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-logo">✦ WeddingPlanner Pro</div>
  <a href="#pricing" class="nav-cta">Get It Now →</a>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-text">
    <div class="hero-badge">✦ The Spreadsheet Every Bride Needs</div>
    <h1>Plan Your <em>Perfect Wedding</em> Without the Overwhelm</h1>
    <p class="hero-sub">The all-in-one Google Sheets Wedding Planner that tracks your budget, guest list, vendors, timeline, and tasks — beautifully and effortlessly from "Yes!" to "I do."</p>
    <div class="hero-actions">
      <a href="#pricing" class="btn-primary">Get Instant Access →</a>
      <a href="#features" class="btn-secondary">See what's inside</a>
    </div>
    <p class="hero-price-note">One-time purchase · Instant download · Works in Google Sheets &amp; Excel</p>
  </div>

  <div class="hero-visual">
    <div class="spreadsheet-mock">
      <div class="mock-topbar">
        <div class="mock-dot"></div>
        <div class="mock-dot"></div>
        <div class="mock-dot"></div>
        <span class="mock-title">Wedding Planner Pro.xlsx</span>
      </div>
      <div class="mock-tabs">
        <div class="mock-tab active">Summary</div>
        <div class="mock-tab">Budget</div>
        <div class="mock-tab">Planner</div>
        <div class="mock-tab">Guest List</div>
        <div class="mock-tab">Timeline</div>
        <div class="mock-tab">Purchases</div>
      </div>
      <div class="mock-body">
        <div class="mock-grid">
          <div class="mock-card">
            <div class="mock-card-label">Event Budget</div>
            <div class="mock-card-value">$70,000</div>
          </div>
          <div class="mock-card">
            <div class="mock-card-label">Days Left</div>
            <div class="mock-card-value">129</div>
          </div>
          <div class="mock-card">
            <div class="mock-card-label">Already Paid</div>
            <div class="mock-card-value">$7,500</div>
          </div>
          <div class="mock-card">
            <div class="mock-card-label">Total Guests</div>
            <div class="mock-card-value">53</div>
          </div>
        </div>
        <div class="mock-progress-label">Budget used: 10.7%</div>
        <div class="mock-bar-track"><div class="mock-bar-fill" style="width:11%"></div></div>
        <div class="mock-progress-label">Tasks completed: 3 / 5</div>
        <div class="mock-bar-track"><div class="mock-bar-fill" style="width:60%"></div></div>

        <div style="margin-top:14px;">
          <div class="mock-row">
            <div class="mock-row-dot" style="background:#C0506A"></div>
            <div class="mock-row-text">Hire wedding planner / coordinator</div>
            <div class="mock-row-badge">Low</div>
          </div>
          <div class="mock-row">
            <div class="mock-row-dot" style="background:#B8893A"></div>
            <div class="mock-row-text">Confirm vendor contact list</div>
            <div class="mock-row-badge">Low</div>
          </div>
          <div class="mock-row">
            <div class="mock-row-dot" style="background:#C03030"></div>
            <div class="mock-row-text">Finalize Event Budget</div>
            <div class="mock-row-badge high">High</div>
          </div>
          <div class="mock-row">
            <div class="mock-row-dot" style="background:#6A8A6D"></div>
            <div class="mock-row-text">Bridal party photos confirmed</div>
            <div class="mock-row-badge done">Done</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- SOCIAL STRIP -->
<div class="social-strip">
  <div class="social-stat">
    <div class="social-stat-num">2,400+</div>
    <div class="social-stat-label">Happy couples</div>
  </div>
  <div class="social-stat">
    <div class="social-stat-num">4.9★</div>
    <div class="social-stat-label">Average rating</div>
  </div>
  <div class="social-stat">
    <div class="social-stat-num">8 Tabs</div>
    <div class="social-stat-label">Complete planning system</div>
  </div>
  <div class="social-stat">
    <div class="social-stat-num">100%</div>
    <div class="social-stat-label">Customizable</div>
  </div>
</div>

<!-- PAIN / DREAM -->
<div class="pain-dream">
  <div class="pain-dream-intro">
    <h2>Wedding planning should be joyful — not stressful.</h2>
    <p>Without a system, it quickly becomes the most overwhelming project of your life.</p>
  </div>
  <div class="pain-dream-grid">
    <div class="pain-box">
      <h3>Without a planner, you're dealing with…</h3>
      <ul>
        <li><span class="icon">✗</span> Scattered notes across sticky pads, emails &amp; apps</li>
        <li><span class="icon">✗</span> No idea where your budget actually stands</li>
        <li><span class="icon">✗</span> Forgetting to follow up with vendors</li>
        <li><span class="icon">✗</span> Guest RSVPs chaos — who responded? Who hasn't?</li>
        <li><span class="icon">✗</span> The constant fear you've forgotten something crucial</li>
        <li><span class="icon">✗</span> Sleepless nights the week before the big day</li>
      </ul>
    </div>
    <div class="dream-box">
      <h3>With the Wedding Planner Spreadsheet…</h3>
      <ul>
        <li><span class="icon">✦</span> Everything lives in one beautiful, organized file</li>
        <li><span class="icon">✦</span> Auto-calculated budget tracker shows exactly what's left</li>
        <li><span class="icon">✦</span> Never miss a vendor deadline with the task planner</li>
        <li><span class="icon">✦</span> Guest list with RSVPs, meals &amp; seating all in one place</li>
        <li><span class="icon">✦</span> A complete day-of timeline ready to share with your team</li>
        <li><span class="icon">✦</span> Total peace of mind leading up to your perfect day</li>
      </ul>
    </div>
  </div>
</div>

<!-- FEATURES -->
<section class="features-bg" id="features">
  <div class="section-label">Features</div>
  <h2 class="section-heading">Everything you need to plan your wedding, in one spreadsheet.</h2>
  <p class="section-sub">Built from scratch for real couples — every tab, formula, and field was designed to make wedding planning genuinely enjoyable.</p>

  <div class="features-grid">
    <div class="feature-card">
      <div class="feature-icon">
        <svg viewBox="0 0 24 24" fill="none" stroke="#C0506A" stroke-width="2" stroke-linecap="round"><rect x="2" y="3" width="20" height="14" rx="2"/><line x1="8" y1="21" x2="16" y2="21"/><line x1="12" y1="17" x2="12" y2="21"/></svg>
      </div>
      <h3>Live Budget Dashboard</h3>
      <p>See your total budget, amount paid, remaining balance, and percentage used — all automatically updated as you log expenses. No math needed.</p>
    </div>
    <div class="feature-card">
      <div class="feature-icon">
        <svg viewBox="0 0 24 24" fill="none" stroke="#C0506A" stroke-width="2" stroke-linecap="round"><path d="M9 11l3 3L22 4"/><path d="M21 12v7a2 2 0 01-2 2H5a2 2 0 01-2-2V5a2 2 0 012-2h11"/></svg>
      </div>
      <h3>Task &amp; Planner Tracker</h3>
      <p>Assign tasks to team members with due dates, priorities, and progress percentages. Never miss a deadline or forget to follow up.</p>
    </div>
    <div class="feature-card">
      <div class="feature-icon">
        <svg viewBox="0 0 24 24" fill="none" stroke="#C0506A" stroke-width="2" stroke-linecap="round"><path d="M17 21v-2a4 4 0 00-4-4H5a4 4 0 00-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 00-3-3.87"/><path d="M16 3.13a4 4 0 010 7.75"/></svg>
      </div>
      <h3>Full Guest List Manager</h3>
      <p>Track 53+ guests with RSVPs, ceremony attendance, cocktail/dinner/luncheon preferences, seating table, meal selection, dietary needs, and accommodation status.</p>
    </div>
    <div class="feature-card">
      <div class="feature-icon">
        <svg viewBox="0 0 24 24" fill="none" stroke="#C0506A" stroke-width="2" stroke-linecap="round"><rect x="3" y="4" width="18" height="18" rx="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/></svg>
      </div>
      <h3>Day-Of Wedding Timeline</h3>
      <p>A structured timeline from morning prep to grand exit — covering 6 phases: preparation, first look, ceremony, cocktail hour, reception, and after-party.</p>
    </div>
    <div class="feature-card">
      <div class="feature-icon">
        <svg viewBox="0 0 24 24" fill="none" stroke="#C0506A" stroke-width="2" stroke-linecap="round"><path d="M6 2L3 6v14a2 2 0 002 2h14a2 2 0 002-2V6l-3-4z"/><line x1="3" y1="6" x2="21" y2="6"/><path d="M16 10a4 4 0 01-8 0"/></svg>
      </div>
      <h3>Purchase &amp; Vendor Log</h3>
      <p>Log every purchase with supplier, quantity, unit cost, total, responsible person, paid status, contract status, and notes — all in one view.</p>
    </div>
    <div class="feature-card">
      <div class="feature-icon">
        <svg viewBox="0 0 24 24" fill="none" stroke="#C0506A" stroke-width="2" stroke-linecap="round"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg>
      </div>
      <h3>Instant Summary Dashboard</h3>
      <p>A single-page overview showing budget health, event countdown, task completion, and key stats — so you always know exactly where things stand.</p>
    </div>
    <div class="feature-card">
      <div class="feature-icon">
        <svg viewBox="0 0 24 24" fill="none" stroke="#C0506A" stroke-width="2" stroke-linecap="round"><circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/></svg>
      </div>
      <h3>Multi-Event Support</h3>
      <p>Plan your Wedding Ceremony, Bridal Shower, Engagement Party, and Rehearsal Dinner — all within the same file. Switch between events instantly.</p>
    </div>
    <div class="feature-card">
      <div class="feature-icon">
        <svg viewBox="0 0 24 24" fill="none" stroke="#C0506A" stroke-width="2" stroke-linecap="round"><path d="M11 4H4a2 2 0 00-2 2v14a2 2 0 002 2h14a2 2 0 002-2v-7"/><path d="M18.5 2.5a2.121 2.121 0 013 3L12 15l-4 1 1-4 9.5-9.5z"/></svg>
      </div>
      <h3>Fully Customizable</h3>
      <p>Every cell, label, color, and formula is yours to edit. Rename vendors, add rows, adjust budgets — it bends to your wedding, not the other way around.</p>
    </div>
  </div>
</section>

<!-- MID CTA 1 -->
<div style="background:var(--rose-light); border-top:1px solid var(--border); border-bottom:1px solid var(--border); padding:40px 5%; text-align:center;">
  <p style="font-family:'Playfair Display',serif; font-size:1.25rem; color:var(--ink); margin-bottom:6px;">Ready to stop feeling overwhelmed?</p>
  <p style="font-size:0.9rem; color:var(--ink-soft); margin-bottom:22px;">Join 2,400+ couples who planned their dream day with this spreadsheet.</p>
  <a href="#pricing" class="btn-primary" style="font-size:0.92rem; padding:13px 32px;">Get Instant Access for $3.49 →</a>
</div>

<!-- WHAT'S INSIDE -->
<section>
  <div class="section-label">What's Inside</div>
  <h2 class="section-heading">8 powerful tabs. One complete planning system.</h2>
  <p class="section-sub">Each tab is purpose-built so nothing overlaps, nothing is missing, and your whole wedding plan stays connected.</p>
  <div class="inside-grid">
    <div class="inside-card">
      <div class="inside-num">01</div>
      <div class="inside-label">Summary Dashboard</div>
      <div class="inside-desc">At-a-glance overview of budget, tasks, countdown, and event highlights.</div>
    </div>
    <div class="inside-card">
      <div class="inside-num">02</div>
      <div class="inside-label">Budget Tracker</div>
      <div class="inside-desc">Category-by-category spend log with estimated vs. actual, paid, remaining, and contract tracking.</div>
    </div>
    <div class="inside-card">
      <div class="inside-num">03</div>
      <div class="inside-label">Task Planner</div>
      <div class="inside-desc">Assignable to-do list with due dates, priorities, and completion percentages for each event.</div>
    </div>
    <div class="inside-card">
      <div class="inside-num">04</div>
      <div class="inside-label">Guest List</div>
      <div class="inside-desc">Full guest management — RSVPs, attendance by event, seating, meals, dietary notes &amp; lodging.</div>
    </div>
    <div class="inside-card">
      <div class="inside-num">05</div>
      <div class="inside-label">Purchase Log</div>
      <div class="inside-desc">Every vendor purchase tracked with supplier, quantity, cost, payment, and contract status.</div>
    </div>
    <div class="inside-card">
      <div class="inside-num">06</div>
      <div class="inside-label">Wedding Timeline</div>
      <div class="inside-desc">6-phase day-of schedule from morning prep to grand exit — shareable with your whole team.</div>
    </div>
    <div class="inside-card">
      <div class="inside-num">07</div>
      <div class="inside-label">Table Seating</div>
      <div class="inside-desc">Track up to 20 tables with guest assignments and seating counts at a glance.</div>
    </div>
    <div class="inside-card">
      <div class="inside-num">08</div>
      <div class="inside-label">Data &amp; Dropdowns</div>
      <div class="inside-desc">Pre-built dropdown lists for party, category, table, and meal — keeps data clean automatically.</div>
    </div>
  </div>
</section>

<!-- MID CTA 2 -->
<div style="background:var(--ink); padding:48px 5%; text-align:center;">
  <p style="font-family:'Playfair Display',serif; font-size:1.3rem; color:var(--white); margin-bottom:8px; font-style:italic;">8 tabs. One file. Zero wedding chaos.</p>
  <p style="font-size:0.88rem; color:rgba(255,255,255,0.6); margin-bottom:24px;">Everything you need — budget, guests, vendors, timeline — all connected and auto-calculated.</p>
  <a href="#pricing" class="btn-white" style="font-size:0.92rem; padding:13px 32px;">Download for $3.49 — Instant Access →</a>
  <p style="font-size:0.76rem; color:rgba(255,255,255,0.4); margin-top:12px;">One-time payment · Works in Google Sheets &amp; Excel · 30-day guarantee</p>
</div>

<!-- TESTIMONIALS -->
<section class="testimonials-bg">
  <div class="section-label">Love Notes</div>
  <h2 class="section-heading">Couples who planned their dream day with this.</h2>
  <div class="testimonials-grid" style="margin-top: 40px;">
    <div class="testi-card">
      <div class="testi-stars">★★★★★</div>
      <p class="testi-text">"I was drowning in spreadsheets and notes apps trying to keep everything together. This planner changed everything. I could see our full budget at a glance and I stopped waking up at 3am panicking."</p>
      <div class="testi-author">Sarah M.</div>
      <div class="testi-detail">Married July 2024 · Lagos, Nigeria</div>
    </div>
    <div class="testi-card">
      <div class="testi-stars">★★★★★</div>
      <p class="testi-text">"The guest list tab alone was worth every penny. Tracking who RSVPed, their meal choices, and seating — all in one place. My mum kept asking how I stayed so calm during planning. This is why."</p>
      <div class="testi-author">Priya &amp; Daniel K.</div>
      <div class="testi-detail">Married October 2024 · London, UK</div>
    </div>
    <div class="testi-card">
      <div class="testi-stars">★★★★★</div>
      <p class="testi-text">"We had 4 events to plan — the engagement party, bridal shower, rehearsal dinner, and the wedding. This spreadsheet handled all of them. I genuinely couldn't imagine doing it any other way now."</p>
      <div class="testi-author">Amara &amp; Chukwudi O.</div>
      <div class="testi-detail">Married December 2024 · Abuja, Nigeria</div>
    </div>
  </div>
</section>

<!-- MID CTA 3 -->
<div style="background:var(--gold-light); border-top:1px solid rgba(184,137,58,0.2); border-bottom:1px solid rgba(184,137,58,0.2); padding:44px 5%; display:flex; flex-wrap:wrap; align-items:center; justify-content:center; gap:24px; text-align:center;">
  <div>
    <p style="font-family:'Playfair Display',serif; font-size:1.2rem; color:var(--ink); margin-bottom:4px;">Loved by real brides. Trusted for real weddings.</p>
    <p style="font-size:0.85rem; color:var(--ink-soft);">4.9★ average · 2,400+ happy couples · instant download</p>
  </div>
  <a href="#pricing" class="btn-primary" style="background:var(--gold); font-size:0.92rem; padding:13px 32px; white-space:nowrap;">Yes, I want this for $3.49 →</a>
</div>

<!-- PRICING -->
<section class="pricing-bg" id="pricing">
  <div style="text-align:center; margin-bottom:48px;">
    <div class="section-label" style="text-align:center;">Pricing</div>
    <h2 class="section-heading" style="margin:0 auto; text-align:center;">One small price. One less thing to stress about.</h2>
  </div>
  <div class="pricing-card">
    <div class="pricing-bestseller">Best Seller</div>
    <div class="pricing-name">Complete Wedding Planner</div>
    <div class="pricing-price"><span>$</span>3.49</div>
    <div class="pricing-old">Was $7</div>
    <a href="#" class="btn-primary" style="width:100%; text-align:center; display:block; margin-bottom:10px;">Download on Gumroad →</a>
    <p style="font-size:0.78rem; color:var(--ink-soft); margin-bottom:24px;">Instant delivery · One-time payment · No subscription</p>
    <ul class="pricing-includes">
      <li><span class="check">✓</span> 8-tab complete wedding planning system</li>
      <li><span class="check">✓</span> Live auto-calculated budget dashboard</li>
      <li><span class="check">✓</span> Full guest list + RSVP tracker (unlimited guests)</li>
      <li><span class="check">✓</span> Task planner with priorities &amp; assignments</li>
      <li><span class="check">✓</span> Day-of wedding timeline template</li>
      <li><span class="check">✓</span> Vendor &amp; purchase log</li>
      <li><span class="check">✓</span> Works in Google Sheets &amp; Microsoft Excel</li>
      <li><span class="check">✓</span> 100% customizable — make it yours</li>
      <li><span class="check">✓</span> Lifetime access &amp; free future updates</li>
    </ul>
    <p class="pricing-guarantee">💛 30-day satisfaction guarantee. If you're not happy, we'll make it right.</p>
  </div>
</section>

<!-- FAQ -->
<section class="faq-bg">
  <div class="section-label" style="text-align:center;">FAQ</div>
  <h2 class="section-heading" style="margin:0 auto 40px; text-align:center; max-width:100%;">Common questions, answered.</h2>
  <div class="faq-list">
    <div class="faq-item open">
      <div class="faq-q" onclick="this.parentElement.classList.toggle('open')">
        Do I need to know how to use spreadsheets? <span class="faq-toggle">+</span>
      </div>
      <div class="faq-a">Not at all. The planner is designed for everyday use — just click on a cell and start typing. All formulas and calculations are already built in. No spreadsheet expertise required.</div>
    </div>
    <div class="faq-item">
      <div class="faq-q" onclick="this.parentElement.classList.toggle('open')">
        Does it work with Google Sheets AND Excel? <span class="faq-toggle">+</span>
      </div>
      <div class="faq-a">Yes — you'll receive an .xlsx file that opens perfectly in both Microsoft Excel and Google Sheets. Simply upload it to your Google Drive and it works immediately.</div>
    </div>
    <div class="faq-item">
      <div class="faq-q" onclick="this.parentElement.classList.toggle('open')">
        Can I share it with my partner or wedding planner? <span class="faq-toggle">+</span>
      </div>
      <div class="faq-a">Absolutely. Upload it to Google Drive and share with view or edit access. Your whole team — partner, parents, planner, MOH — can stay aligned in real time.</div>
    </div>
    <div class="faq-item">
      <div class="faq-q" onclick="this.parentElement.classList.toggle('open')">
        Can it handle multiple wedding events? <span class="faq-toggle">+</span>
      </div>
      <div class="faq-a">Yes! The planner supports multiple events — Wedding Ceremony, Bridal Shower, Engagement Party, and Rehearsal Dinner — all within the same file, each tracked separately.</div>
    </div>
    <div class="faq-item">
      <div class="faq-q" onclick="this.parentElement.classList.toggle('open')">
        How do I receive it after purchase? <span class="faq-toggle">+</span>
      </div>
      <div class="faq-a">Instantly! Gumroad sends the download link to your email the moment payment is confirmed. No waiting, no shipping — just immediate access to your planner.</div>
    </div>
    <div class="faq-item">
      <div class="faq-q" onclick="this.parentElement.classList.toggle('open')">
        What if I need help or something isn't working? <span class="faq-toggle">+</span>
      </div>
      <div class="faq-a">We offer email support and will respond within 24 hours. We also have a 30-day satisfaction guarantee — if you're not happy for any reason, we'll make it right.</div>
    </div>
  </div>
</section>

<!-- FINAL CTA -->
<section class="final-cta">
  <h2>Your dream wedding deserves a plan as beautiful as the day itself.</h2>
  <p>Stop letting the planning process steal the joy of your engagement. Get organized, stay calm, and enjoy every step of the journey.</p>
  <a href="#pricing" class="btn-white">Get Instant Access for $3.49 →</a>
  <div class="final-cta-note">One-time purchase · Instant download · 30-day guarantee</div>
</section>



<script>
  document.querySelectorAll('.faq-q').forEach(q => {
    q.addEventListener('click', () => {
      const item = q.parentElement;
      document.querySelectorAll('.faq-item').forEach(i => { if (i !== item) i.classList.remove('open'); });
    });
  });
</script>
</body>
</html>
