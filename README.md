# guera-calcos
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Guera Calcos – Calcomanías únicas</title>
  <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;700;900&family=Cormorant+Garamond:ital,wght@0,300;0,400;1,300&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet" />
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --gold: #c9a84c;
      --gold-light: #e8c97a;
      --gold-dim: #8a6d2f;
      --bg: #0a0a0a;
      --bg-card: #111111;
      --bg-card2: #161616;
      --border: rgba(201,168,76,0.18);
      --border-hover: rgba(201,168,76,0.5);
      --text: #f0ead8;
      --text-muted: #7a7060;
      --text-mid: #b0a080;
    }

    html { scroll-behavior: smooth; }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: 'DM Sans', sans-serif;
      font-weight: 300;
      min-height: 100vh;
      overflow-x: hidden;
    }

    /* ── NOISE OVERLAY ── */
    body::before {
      content: '';
      position: fixed;
      inset: 0;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='1'/%3E%3C/svg%3E");
      opacity: 0.03;
      pointer-events: none;
      z-index: 0;
    }

    /* ── NAV ── */
    nav {
      position: fixed;
      top: 0; left: 0; right: 0;
      z-index: 100;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 1.2rem 3rem;
      background: rgba(10,10,10,0.85);
      backdrop-filter: blur(12px);
      border-bottom: 1px solid var(--border);
    }

    .nav-logo {
      font-family: 'Cinzel', serif;
      font-size: 1.1rem;
      font-weight: 700;
      letter-spacing: 0.15em;
      color: var(--gold);
      text-decoration: none;
    }

    .nav-links {
      display: flex;
      gap: 2.5rem;
      list-style: none;
    }

    .nav-links a {
      font-family: 'DM Sans', sans-serif;
      font-size: 0.78rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: var(--text-muted);
      text-decoration: none;
      transition: color 0.25s;
    }

    .nav-links a:hover { color: var(--gold); }

    .nav-cta {
      font-family: 'DM Sans', sans-serif;
      font-size: 0.75rem;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: var(--gold);
      border: 1px solid var(--border-hover);
      padding: 0.5rem 1.2rem;
      text-decoration: none;
      transition: background 0.25s, color 0.25s;
    }

    .nav-cta:hover {
      background: var(--gold);
      color: #0a0a0a;
    }

    /* ── HERO ── */
    .hero {
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      text-align: center;
      padding: 8rem 2rem 4rem;
      position: relative;
    }

    .hero-bg-lines {
      position: absolute;
      inset: 0;
      overflow: hidden;
      pointer-events: none;
    }

    .hero-bg-lines::before,
    .hero-bg-lines::after {
      content: '';
      position: absolute;
      border-radius: 50%;
      border: 1px solid rgba(201,168,76,0.07);
    }

    .hero-bg-lines::before {
      width: 800px; height: 800px;
      top: 50%; left: 50%;
      transform: translate(-50%, -50%);
    }

    .hero-bg-lines::after {
      width: 500px; height: 500px;
      top: 50%; left: 50%;
      transform: translate(-50%, -50%);
    }

    .hero-eyebrow {
      font-family: 'DM Sans', sans-serif;
      font-size: 0.7rem;
      letter-spacing: 0.35em;
      text-transform: uppercase;
      color: var(--gold);
      margin-bottom: 1.8rem;
      opacity: 0;
      animation: fadeUp 0.8s 0.2s forwards;
    }

    .hero h1 {
      font-family: 'Cinzel', serif;
      font-size: clamp(3.5rem, 10vw, 8rem);
      font-weight: 900;
      line-height: 0.95;
      letter-spacing: -0.01em;
      color: var(--text);
      opacity: 0;
      animation: fadeUp 0.9s 0.4s forwards;
    }

    .hero h1 span {
      display: block;
      color: var(--gold);
      font-style: italic;
      font-weight: 400;
    }

    .hero-sub {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(1rem, 2vw, 1.3rem);
      color: var(--text-mid);
      margin-top: 1.5rem;
      max-width: 440px;
      line-height: 1.7;
      font-style: italic;
      opacity: 0;
      animation: fadeUp 0.9s 0.6s forwards;
    }

    .hero-actions {
      display: flex;
      gap: 1rem;
      margin-top: 2.5rem;
      opacity: 0;
      animation: fadeUp 0.9s 0.8s forwards;
    }

    .btn-primary {
      font-family: 'DM Sans', sans-serif;
      font-size: 0.78rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      background: var(--gold);
      color: #0a0a0a;
      border: none;
      padding: 0.85rem 2rem;
      cursor: pointer;
      text-decoration: none;
      transition: background 0.25s, transform 0.2s;
      font-weight: 500;
    }

    .btn-primary:hover { background: var(--gold-light); transform: translateY(-1px); }

    .btn-secondary {
      font-family: 'DM Sans', sans-serif;
      font-size: 0.78rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      background: transparent;
      color: var(--text-muted);
      border: 1px solid var(--border);
      padding: 0.85rem 2rem;
      cursor: pointer;
      text-decoration: none;
      transition: border-color 0.25s, color 0.25s;
    }

    .btn-secondary:hover { border-color: var(--border-hover); color: var(--text); }

    .hero-divider {
      width: 60px; height: 1px;
      background: var(--gold-dim);
      margin: 3rem auto 0;
      opacity: 0;
      animation: fadeIn 1s 1s forwards;
    }

    /* ── SECTION ── */
    section {
      position: relative;
      z-index: 1;
    }

    .section-header {
      text-align: center;
      padding: 5rem 2rem 3rem;
    }

    .section-label {
      font-size: 0.65rem;
      letter-spacing: 0.4em;
      text-transform: uppercase;
      color: var(--gold-dim);
      margin-bottom: 0.8rem;
    }

    .section-title {
      font-family: 'Cinzel', serif;
      font-size: clamp(1.6rem, 4vw, 2.4rem);
      font-weight: 700;
      color: var(--text);
    }

    /* ── CATEGORIES GRID ── */
    .categories {
      padding: 0 2rem 3rem;
      max-width: 1100px;
      margin: 0 auto;
    }

    .filter-bar {
      display: flex;
      gap: 0.5rem;
      flex-wrap: wrap;
      justify-content: center;
      margin-bottom: 3rem;
    }

    .filter-btn {
      font-family: 'DM Sans', sans-serif;
      font-size: 0.72rem;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      background: transparent;
      color: var(--text-muted);
      border: 1px solid var(--border);
      padding: 0.45rem 1rem;
      cursor: pointer;
      transition: all 0.2s;
    }

    .filter-btn:hover,
    .filter-btn.active {
      background: var(--gold);
      color: #0a0a0a;
      border-color: var(--gold);
    }

    .cat-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
      gap: 1.5rem;
    }

    .cat-card {
      background: var(--bg-card);
      border: 1px solid var(--border);
      padding: 2rem 1.5rem;
      cursor: pointer;
      transition: border-color 0.3s, transform 0.3s, background 0.3s;
      position: relative;
      overflow: hidden;
    }

    .cat-card::before {
      content: '';
      position: absolute;
      bottom: 0; left: 0; right: 0;
      height: 2px;
      background: linear-gradient(90deg, transparent, var(--gold), transparent);
      transform: scaleX(0);
      transition: transform 0.3s;
    }

    .cat-card:hover {
      border-color: var(--border-hover);
      background: var(--bg-card2);
      transform: translateY(-3px);
    }

    .cat-card:hover::before { transform: scaleX(1); }

    .cat-icon {
      font-size: 2rem;
      margin-bottom: 1rem;
      display: block;
    }

    .cat-name {
      font-family: 'Cinzel', serif;
      font-size: 1rem;
      font-weight: 700;
      color: var(--gold);
      letter-spacing: 0.05em;
      margin-bottom: 0.4rem;
    }

    .cat-desc {
      font-size: 0.8rem;
      color: var(--text-muted);
      line-height: 1.6;
    }

    .cat-count {
      position: absolute;
      top: 1rem; right: 1rem;
      font-size: 0.65rem;
      letter-spacing: 0.15em;
      color: var(--gold-dim);
      text-transform: uppercase;
    }

    /* ── STICKERS GRID ── */
    .stickers-section {
      max-width: 1100px;
      margin: 0 auto;
      padding: 0 2rem 5rem;
      display: none;
    }

    .stickers-section.visible { display: block; }

    .stickers-back {
      display: flex;
      align-items: center;
      gap: 0.5rem;
      font-size: 0.75rem;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: var(--text-muted);
      cursor: pointer;
      background: none;
      border: none;
      margin-bottom: 2rem;
      transition: color 0.2s;
    }

    .stickers-back:hover { color: var(--gold); }

    .stickers-header {
      display: flex;
      align-items: baseline;
      gap: 1rem;
      margin-bottom: 2rem;
      border-bottom: 1px solid var(--border);
      padding-bottom: 1.5rem;
    }

    .stickers-title {
      font-family: 'Cinzel', serif;
      font-size: 1.8rem;
      color: var(--text);
    }

    /* ── STICKER CARDS CON IMAGEN ── */
    .stickers-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
      gap: 1rem;
    }

    .sticker-card {
      background: var(--bg-card);
      border: 1px solid var(--border);
      overflow: hidden;
      transition: border-color 0.25s, transform 0.25s;
      cursor: pointer;
    }

    .sticker-card:hover {
      border-color: var(--border-hover);
      transform: translateY(-3px);
    }

    /* Imagen real desde Google Drive */
    .sticker-img-wrap {
      width: 100%;
      aspect-ratio: 1 / 1;
      background: #161616;
      overflow: hidden;
      position: relative;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .sticker-img {
      width: 100%;
      height: 100%;
      object-fit: contain;
      display: block;
      transition: transform 0.35s ease;
      padding: 0.5rem;
    }

    .sticker-card:hover .sticker-img {
      transform: scale(1.06);
    }

    /* Fallback emoji cuando no hay imagen */
    .sticker-img-placeholder {
      width: 100%;
      aspect-ratio: 1 / 1;
      background: #161616;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 3rem;
    }

    /* Spinner de carga */
    .sticker-img-wrap .loader {
      position: absolute;
      inset: 0;
      display: flex;
      align-items: center;
      justify-content: center;
      background: #161616;
      font-size: 1.5rem;
      pointer-events: none;
      transition: opacity 0.3s;
    }

    .sticker-img-wrap .loader.hidden { opacity: 0; }

    .sticker-info {
      padding: 0.85rem 1rem;
    }

    .sticker-name {
      font-size: 0.82rem;
      color: var(--text-mid);
      font-weight: 400;
      margin-bottom: 0.35rem;
    }

    .sticker-badge {
      display: inline-block;
      font-size: 0.6rem;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: var(--gold-dim);
      border: 1px solid var(--border);
      padding: 0.15rem 0.5rem;
    }

    /* ── PERSONALIZADA HIGHLIGHT ── */
    .custom-banner {
      max-width: 1100px;
      margin: 0 auto 5rem;
      padding: 0 2rem;
    }

    .custom-inner {
      border: 1px solid var(--border-hover);
      padding: 3rem 2.5rem;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 2rem;
      flex-wrap: wrap;
      background: linear-gradient(135deg, #0f0e09 0%, #111008 100%);
      position: relative;
      overflow: hidden;
    }

    .custom-inner::after {
      content: '✦';
      position: absolute;
      right: 2rem; top: 50%;
      transform: translateY(-50%);
      font-size: 6rem;
      color: var(--gold);
      opacity: 0.05;
      pointer-events: none;
    }

    .custom-text h3 {
      font-family: 'Cinzel', serif;
      font-size: 1.4rem;
      color: var(--gold);
      margin-bottom: 0.5rem;
    }

    .custom-text p {
      font-size: 0.85rem;
      color: var(--text-muted);
      max-width: 420px;
      line-height: 1.7;
    }

    /* ── CONTACTO ── */
    #contacto {
      background: var(--bg-card);
      border-top: 1px solid var(--border);
    }

    .contact-wrap {
      max-width: 700px;
      margin: 0 auto;
      padding: 5rem 2rem;
    }

    .contact-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 3rem;
      margin-top: 3rem;
    }

    .contact-info h4 {
      font-family: 'Cinzel', serif;
      font-size: 0.9rem;
      color: var(--gold);
      letter-spacing: 0.05em;
      margin-bottom: 1rem;
    }

    .contact-info p {
      font-size: 0.83rem;
      color: var(--text-muted);
      line-height: 1.8;
    }

    .contact-info a {
      color: var(--gold-dim);
      text-decoration: none;
      transition: color 0.2s;
    }

    .contact-info a:hover { color: var(--gold); }

    .contact-form {
      display: flex;
      flex-direction: column;
      gap: 0.75rem;
    }

    .form-group {
      display: flex;
      flex-direction: column;
      gap: 0.3rem;
    }

    .form-group label {
      font-size: 0.68rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: var(--text-muted);
    }

    .form-group input,
    .form-group textarea,
    .form-group select {
      background: var(--bg);
      border: 1px solid var(--border);
      color: var(--text);
      padding: 0.65rem 0.85rem;
      font-family: 'DM Sans', sans-serif;
      font-size: 0.85rem;
      font-weight: 300;
      outline: none;
      transition: border-color 0.2s;
      width: 100%;
      appearance: none;
    }

    .form-group input:focus,
    .form-group textarea:focus,
    .form-group select:focus {
      border-color: var(--gold-dim);
    }

    .form-group textarea { resize: vertical; min-height: 100px; }
    .form-group select option { background: #111; }

    .wsp-btn {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 0.6rem;
      background: #1a1a0a;
      border: 1px solid rgba(37,211,102,0.3);
      color: #25d366;
      font-family: 'DM Sans', sans-serif;
      font-size: 0.75rem;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      padding: 0.7rem 1.2rem;
      cursor: pointer;
      text-decoration: none;
      margin-top: 0.5rem;
      transition: background 0.25s, border-color 0.25s;
    }

    .wsp-btn:hover {
      background: rgba(37,211,102,0.1);
      border-color: rgba(37,211,102,0.6);
    }

    .submit-btn {
      background: var(--gold);
      border: none;
      color: #0a0a0a;
      font-family: 'DM Sans', sans-serif;
      font-size: 0.75rem;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      font-weight: 500;
      padding: 0.85rem;
      cursor: pointer;
      margin-top: 0.25rem;
      transition: background 0.25s;
    }

    .submit-btn:hover { background: var(--gold-light); }

    /* ── FOOTER ── */
    footer {
      border-top: 1px solid var(--border);
      padding: 2rem 3rem;
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 1rem;
    }

    footer .logo {
      font-family: 'Cinzel', serif;
      font-size: 0.85rem;
      color: var(--gold);
      letter-spacing: 0.15em;
    }

    footer p {
      font-size: 0.72rem;
      color: var(--text-muted);
      letter-spacing: 0.05em;
    }

    /* ── TOAST ── */
    .toast {
      position: fixed;
      bottom: 2rem; right: 2rem;
      background: var(--gold);
      color: #0a0a0a;
      font-family: 'DM Sans', sans-serif;
      font-size: 0.8rem;
      font-weight: 500;
      padding: 0.85rem 1.5rem;
      z-index: 999;
      transform: translateY(100px);
      opacity: 0;
      transition: all 0.4s;
    }

    .toast.show { transform: translateY(0); opacity: 1; }

    /* ── ANIMATIONS ── */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(20px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    @keyframes fadeIn {
      from { opacity: 0; }
      to   { opacity: 1; }
    }

    /* ── MOBILE ── */
    @media (max-width: 768px) {
      nav { padding: 1rem 1.5rem; }
      .nav-links { display: none; }
      .contact-grid { grid-template-columns: 1fr; gap: 2rem; }
      footer { flex-direction: column; text-align: center; }
      .stickers-grid { grid-template-columns: repeat(auto-fill, minmax(150px, 1fr)); }
    }
  </style>
</head>
<body>

  <!-- NAV -->
  <nav>
    <a href="#" class="nav-logo">GUERA CALCOS</a>
    <ul class="nav-links">
      <li><a href="#catalogo">Catálogo</a></li>
      <li><a href="#personalizadas">Personalizadas</a></li>
      <li><a href="#contacto">Contacto</a></li>
    </ul>
    <a href="#contacto" class="nav-cta">Pedir ahora</a>
  </nav>

  <!-- HERO -->
  <section class="hero">
    <div class="hero-bg-lines"></div>
    <p class="hero-eyebrow">Calcomanías artesanales · Córdoba, Argentina</p>
    <h1>GUERA<span>Calcos</span></h1>
    <p class="hero-sub">Tu estilo en cada superficie. Calcomanías de alta calidad para termos, autos, motos, notebooks y más.</p>
    <div class="hero-actions">
      <a href="#catalogo" class="btn-primary">Ver catálogo</a>
      <a href="#contacto" class="btn-secondary">Contacto</a>
    </div>
    <div class="hero-divider"></div>
  </section>

  <!-- CATÁLOGO -->
  <section id="catalogo">
    <div class="section-header">
      <p class="section-label">Todo el stock disponible</p>
      <h2 class="section-title">Catálogo</h2>
    </div>

    <div class="categories">
      <div class="filter-bar">
        <button class="filter-btn active" onclick="filterCat('todos', this)">Todos</button>
        <button class="filter-btn" onclick="filterCat('animados', this)">Animados</button>
        <button class="filter-btn" onclick="filterCat('argentina', this)">Argentina</button>
        <button class="filter-btn" onclick="filterCat('basquet', this)">Básquet</button>
        <button class="filter-btn" onclick="filterCat('f1', this)">F1</button>
        <button class="filter-btn" onclick="filterCat('futbol', this)">Fútbol</button>
        <button class="filter-btn" onclick="filterCat('girls', this)">Girls</button>
        <button class="filter-btn" onclick="filterCat('marcas', this)">Marcas</button>
        <button class="filter-btn" onclick="filterCat('motors', this)">Motors</button>
        <button class="filter-btn" onclick="filterCat('vintage', this)">Vintage</button>
      </div>

      <div class="cat-grid" id="catGrid">
        <div class="cat-card" data-cat="animados" onclick="showStickers('animados')">
          <span class="cat-count">Stock disponible</span>
          <span class="cat-icon">🎌</span>
          <div class="cat-name">Animados</div>
          <div class="cat-desc">Anime, cartoons y personajes animados de todos los estilos.</div>
        </div>
        <div class="cat-card" data-cat="argentina" onclick="showStickers('argentina')">
          <span class="cat-count">Stock disponible</span>
          <span class="cat-icon">🇦🇷</span>
          <div class="cat-name">Argentina General</div>
          <div class="cat-desc">Escudos, frases y símbolos patrios. Orgullo argentino en cada calco.</div>
        </div>
        <div class="cat-card" data-cat="basquet" onclick="showStickers('basquet')">
          <span class="cat-count">Stock disponible</span>
          <span class="cat-icon">🏀</span>
          <div class="cat-name">Básquet</div>
          <div class="cat-desc">NBA, básquet argentino, equipos y jugadores icónicos.</div>
        </div>
        <div class="cat-card" data-cat="f1" onclick="showStickers('f1')">
          <span class="cat-count">Stock disponible</span>
          <span class="cat-icon">🏎️</span>
          <div class="cat-name">Fórmula 1</div>
          <div class="cat-desc">Escuderías, cascos y leyendas de la Fórmula 1.</div>
        </div>
        <div class="cat-card" data-cat="futbol" onclick="showStickers('futbol')">
          <span class="cat-count">Stock disponible</span>
          <span class="cat-icon">⚽</span>
          <div class="cat-name">Fútbol</div>
          <div class="cat-desc">Clubes, selecciones y jugadores del fútbol local e internacional.</div>
        </div>
        <div class="cat-card" data-cat="girls" onclick="showStickers('girls')">
          <span class="cat-count">Stock disponible</span>
          <span class="cat-icon">🌸</span>
          <div class="cat-name">Girls</div>
          <div class="cat-desc">Diseños femeninos, floreados, ilustraciones y frases para ellas.</div>
        </div>
        <div class="cat-card" data-cat="marcas" onclick="showStickers('marcas')">
          <span class="cat-count">Stock disponible</span>
          <span class="cat-icon">⚡</span>
          <div class="cat-name">Marcas</div>
          <div class="cat-desc">Logos y diseños de marcas icónicas del streetwear y lifestyle.</div>
        </div>
        <div class="cat-card" data-cat="motors" onclick="showStickers('motors')">
          <span class="cat-count">Stock disponible</span>
          <span class="cat-icon">🏍️</span>
          <div class="cat-name">Motors</div>
          <div class="cat-desc">Autos clásicos, motos, cultura del asfalto y velocidad.</div>
        </div>
        <div class="cat-card" data-cat="vintage" onclick="showStickers('vintage')">
          <span class="cat-count">Stock disponible</span>
          <span class="cat-icon">📻</span>
          <div class="cat-name">Vintage General</div>
          <div class="cat-desc">Estética retro, colores vibrantes y diseños que no envejecen.</div>
        </div>
      </div>
    </div>

    <!-- Vista de stickers expandida -->
    <div class="stickers-section" id="stickersSection">
      <button class="stickers-back" onclick="closeStickers()">← Volver al catálogo</button>
      <div class="stickers-header">
        <h3 class="stickers-title" id="stickersTitle"></h3>
      </div>

      <p style="font-size:0.82rem; color:var(--text-muted); margin-bottom:1.5rem; line-height:1.8;">
        ¿Te interesa algún diseño? Contactame por WhatsApp o completá el formulario abajo y te cuento precio y disponibilidad. 🤍
      </p>

      <div class="stickers-grid" id="stickersGrid"></div>

      <div style="margin-top: 2rem; display:flex; gap:1rem; flex-wrap:wrap;">
        <a href="#contacto" class="btn-primary">Consultar por este diseño</a>
      </div>
    </div>
  </section>

  <!-- PERSONALIZADAS -->
  <section id="personalizadas" style="padding-bottom: 3rem;">
    <div class="custom-banner">
      <div class="custom-inner">
        <div class="custom-text">
          <h3>✦ Personalizadas</h3>
          <p>¿Tenés una idea en mente? Hacemos calcomanías a medida: tu nombre, tu diseño, tu marca. Consultanos sin compromiso y te armamos un presupuesto.</p>
        </div>
        <a href="#contacto" class="btn-primary" style="white-space:nowrap; flex-shrink:0;">Solicitar diseño</a>
      </div>
    </div>
  </section>

  <!-- CONTACTO -->
  <section id="contacto">
    <div class="contact-wrap">
      <div class="section-header" style="padding-top:0;">
        <p class="section-label">Estamos para vos</p>
        <h2 class="section-title">Contacto & Pedidos</h2>
      </div>

      <div class="contact-grid">
        <div class="contact-info">
          <h4>Guera Calcos</h4>
          <p>
            📍 Devoto, Córdoba, Argentina<br><br>
            Respondemos rápido por WhatsApp.<br><br>
            <a href="https://wa.me/3564204650" target="_blank" style="color:var(--gold);">→ Escribinos al WhatsApp</a><br>
            <a href="https://instagram.com/guera_calcos" target="_blank" style="color:var(--gold);">→ Seguinos en Instagram</a>
          </p>
          <a href="https://wa.me/3564204650?text=Hola%20Guera%20Calcos%2C%20vi%20el%20cat%C3%A1logo%20y%20quiero%20consultar%20un%20pedido%20%F0%9F%94%A5" target="_blank" class="wsp-btn" style="margin-top:1.5rem; text-decoration:none;">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="#25d366"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
            Escribir por WhatsApp
          </a>
        </div>

        <form class="contact-form" onsubmit="handleForm(event)">
          <div class="form-group">
            <label>Tu nombre</label>
            <input type="text" placeholder="Ej: Valentina" required />
          </div>
          <div class="form-group">
            <label>Categoría que te interesa</label>
            <select>
              <option value="">Seleccioná...</option>
              <option>Animados</option>
              <option>Argentina General</option>
              <option>Básquet</option>
              <option>Fórmula 1</option>
              <option>Fútbol</option>
              <option>Girls</option>
              <option>Marcas</option>
              <option>Motors</option>
              <option>Vintage General</option>
              <option>Personalizada</option>
            </select>
          </div>
          <div class="form-group">
            <label>Tu consulta o pedido</label>
            <textarea placeholder="Contame qué diseño buscás, en qué superficie la vas a poner, si querés personalizarla..."></textarea>
          </div>
          <button type="submit" class="submit-btn">Enviar consulta</button>
        </form>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <span class="logo">GUERA CALCOS</span>
    <p>Calcomanías únicas · Córdoba, Argentina</p>
    <p>Hecho con 🤍 para vos</p>
  </footer>

  <div class="toast" id="toast">¡Consulta enviada! Te respondo pronto 🤍</div>

  <script>
    // ─────────────────────────────────────────────
    //  DATOS DE STICKERS
    //
    //  Para agregar imagen de Google Drive:
    //  1. Compartí el archivo como "Cualquier persona con el enlace"
    //  2. Copiá el ID del link (la parte larga)
    //     Ej: https://drive.google.com/file/d/  →ESTE_ES_EL_ID←  /view
    //  3. Pegalo en el campo img así:
    //     img: 'https://drive.google.com/uc?export=view&id=ESTE_ES_EL_ID'
    //
    //  Si un sticker no tiene imagen todavía, dejá img: '' y se mostrará el emoji.
    // ─────────────────────────────────────────────

    const data = {
      animados: [
        { name: 'Dragon Ball',  e: '🐉', img: '' },
        { name: 'Naruto',       e: '🍃', img: '' },
        { name: 'Rick & Morty', e: '🛸', img: '' },
        { name: 'Simpsons',     e: '🍩', img: '' },
        { name: 'Pokémon',      e: '⚡', img: '' },
      ],
      argentina: [
        { name: 'Mapa Argentina', e: '🗺️', img: '' },
        { name: 'Frase Criolla',  e: '🧉', img: '' },
        { name: 'Mate',           e: '🧉', img: '' },
        { name: 'Gaucho',         e: '🐎', img: '' },
        { name: 'Provincias',     e: '🌆', img: '' },
        { name: 'Bandera',        e: '🇦🇷', img: '' },
      ],
      basquet: [
        { name: 'NBA Logo',          e: '🏀', img: '' },
        { name: 'NBA Jugadores',     e: '⛹🏼‍♂️', img: '' },
        { name: 'Básquet Argentino', e: '🇦🇷', img: '' },
        { name: 'Cancha',            e: '🏀', img: '' },
      ],
      motors: [
        { name: 'Marcas', e: '🏁', img: 'https://drive.google.com/open?id=1-Hky-ExbsNdOo1mGpUY6GGeYJPT-NcS-&usp=drive_copy' },
        { name: 'Autos',  e: '🚗', img: '' },
        { name: 'Motos',  e: '🏍️', img: '' },
      ],
      futbol: [
        { name: 'Boca Juniors',       e: '💙', img: '' },
        { name: 'River Plate',        e: '❤️', img: '' },
        { name: 'Selección Argentina',e: '🇦🇷', img: '' },
        { name: 'Fútbol argentino',   e: '⚽', img: '' },
      ],
      girls: [
        { name: 'Flores',     e: '🌸', img: '' },
        { name: 'Mariposas',  e: '🦋', img: '' },
        { name: 'Good vibes', e: '💫', img: '' },
        { name: 'Corazones',  e: '💕', img: '' },
        { name: 'Coqueta',    e: '💅', img: '' },
        { name: 'Horóscopo',  e: '♌', img: '' },
      ],
      marcas: [
        { name: 'Snacks',     e: '🥤', img: '' },
        { name: 'Vestimenta', e: '🏷️', img: '' },
        { name: 'Redes',      e: '🌐', img: '' },
      ],
      f1: [
        { name: 'Circuitos',   e: '🔥', img: '' },
        { name: 'Monoplazas',  e: '🏎️', img: '' },
        { name: 'Corredores',  e: '⚡', img: '' },
      ],
      vintage: [
        { name: 'Cassette',      e: '📼', img: '' },
        { name: 'Polaroid',      e: '📷', img: '' },
        { name: 'Música Retro',  e: '🎵', img: '' },
        { name: 'Neon 80s',      e: '💜', img: '' },
        { name: 'VHS',           e: '📹', img: '' },
        { name: 'Estrellas Retro', e: '⭐', img: '' },
        { name: 'Vintage Pin',   e: '📌', img: '' },
        { name: 'Old School',    e: '🖤', img: '' },
      ],
    };

    const catNames = {
      animados: 'Animados',
      argentina: 'Argentina General',
      basquet: 'Básquet',
      f1: 'Fórmula 1',
      futbol: 'Fútbol',
      girls: 'Girls',
      marcas: 'Marcas',
      motors: 'Motors',
      vintage: 'Vintage General',
    };

    function filterCat(cat, btn) {
      document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
      btn.classList.add('active');
      document.querySelectorAll('.cat-card').forEach(card => {
        card.style.display = (cat === 'todos' || card.dataset.cat === cat) ? '' : 'none';
      });
      closeStickers();
    }

    function buildStickerCard(s) {
      if (s.img) {
        // ── Con imagen de Google Drive ──
        return `
          <div class="sticker-card">
            <div class="sticker-img-wrap">
              <div class="loader" id="loader-${s.name.replace(/\s/g,'')}">⏳</div>
              <img
                class="sticker-img"
                src="${s.img}"
                alt="${s.name}"
                loading="lazy"
                onload="this.previousElementSibling.classList.add('hidden')"
                onerror="this.parentElement.innerHTML='<div class=\\'sticker-img-placeholder\\'>${s.e}</div>'"
              />
            </div>
            <div class="sticker-info">
              <div class="sticker-name">${s.name}</div>
              <span class="sticker-badge">Disponible</span>
            </div>
          </div>`;
      } else {
        // ── Sin imagen: muestra emoji ──
        return `
          <div class="sticker-card">
            <div class="sticker-img-placeholder">${s.e}</div>
            <div class="sticker-info">
              <div class="sticker-name">${s.name}</div>
              <span class="sticker-badge">Disponible</span>
            </div>
          </div>`;
      }
    }

    function showStickers(cat) {
      const grid  = document.getElementById('stickersGrid');
      const title = document.getElementById('stickersTitle');
      const sec   = document.getElementById('stickersSection');
      const catGrid = document.getElementById('catGrid');

      title.textContent = catNames[cat] || cat;
      grid.innerHTML = (data[cat] || []).map(buildStickerCard).join('');

      catGrid.style.display = 'none';
      document.querySelector('.filter-bar').style.display = 'none';
      sec.classList.add('visible');
      sec.scrollIntoView({ behavior: 'smooth', block: 'start' });
    }

    function closeStickers() {
      document.getElementById('stickersSection').classList.remove('visible');
      document.getElementById('catGrid').style.display = '';
      document.querySelector('.filter-bar').style.display = '';
    }

    function handleForm(e) {
      e.preventDefault();
      const toast = document.getElementById('toast');
      toast.classList.add('show');
      setTimeout(() => toast.classList.remove('show'), 3500);
      e.target.reset();
    }
  </script>
</body>
</html>
