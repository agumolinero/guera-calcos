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
      z-index: 200;
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

    .nav-links { display: flex; gap: 2.5rem; list-style: none; }

    .nav-links a {
      font-size: 0.78rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: var(--text-muted);
      text-decoration: none;
      transition: color 0.25s;
    }

    .nav-links a:hover { color: var(--gold); }

    .nav-right { display: flex; align-items: center; gap: 1rem; }

    .nav-cta {
      font-size: 0.75rem;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: var(--gold);
      border: 1px solid var(--border-hover);
      padding: 0.5rem 1.2rem;
      text-decoration: none;
      transition: background 0.25s, color 0.25s;
    }

    .nav-cta:hover { background: var(--gold); color: #0a0a0a; }

    /* ── BOTÓN CARRITO EN NAV ── */
    .cart-nav-btn {
      position: relative;
      background: transparent;
      border: 1px solid var(--border);
      color: var(--text-muted);
      cursor: pointer;
      padding: 0.45rem 0.75rem;
      display: flex;
      align-items: center;
      gap: 0.4rem;
      font-family: 'DM Sans', sans-serif;
      font-size: 0.72rem;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      transition: border-color 0.25s, color 0.25s;
    }

    .cart-nav-btn:hover { border-color: var(--border-hover); color: var(--gold); }
    .cart-nav-btn.has-items { border-color: var(--gold-dim); color: var(--gold); }

    .cart-nav-badge {
      display: none;
      background: var(--gold);
      color: #0a0a0a;
      font-size: 0.6rem;
      font-weight: 500;
      width: 16px; height: 16px;
      border-radius: 50%;
      align-items: center;
      justify-content: center;
      position: absolute;
      top: -6px; right: -6px;
    }

    .cart-nav-badge.visible { display: flex; }

    /* ── PANEL CARRITO LATERAL ── */
    .cart-overlay {
      position: fixed;
      inset: 0;
      background: rgba(0,0,0,0.6);
      z-index: 300;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.3s;
    }

    .cart-overlay.open { opacity: 1; pointer-events: all; }

    .cart-panel {
      position: fixed;
      top: 0; right: 0;
      width: 380px;
      max-width: 100vw;
      height: 100vh;
      background: #0d0d0d;
      border-left: 1px solid var(--border-hover);
      z-index: 301;
      display: flex;
      flex-direction: column;
      transform: translateX(100%);
      transition: transform 0.35s cubic-bezier(.4,0,.2,1);
    }

    .cart-panel.open { transform: translateX(0); }

    .cart-panel-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 1.5rem 1.5rem 1.2rem;
      border-bottom: 1px solid var(--border);
    }

    .cart-panel-title {
      font-family: 'Cinzel', serif;
      font-size: 1rem;
      font-weight: 700;
      color: var(--gold);
      letter-spacing: 0.1em;
    }

    .cart-close-btn {
      background: none;
      border: 1px solid var(--border);
      color: var(--text-muted);
      cursor: pointer;
      width: 32px; height: 32px;
      display: flex; align-items: center; justify-content: center;
      font-size: 1rem;
      transition: border-color 0.2s, color 0.2s;
    }

    .cart-close-btn:hover { border-color: var(--border-hover); color: var(--text); }

    .cart-items-list {
      flex: 1;
      overflow-y: auto;
      padding: 1rem 1.5rem;
    }

    .cart-items-list::-webkit-scrollbar { width: 3px; }
    .cart-items-list::-webkit-scrollbar-track { background: transparent; }
    .cart-items-list::-webkit-scrollbar-thumb { background: var(--gold-dim); }

    .cart-empty-msg {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100%;
      gap: 0.75rem;
      color: var(--text-muted);
      font-size: 0.82rem;
      letter-spacing: 0.05em;
      text-align: center;
      padding: 3rem 1rem;
    }

    .cart-empty-msg .empty-icon { font-size: 2.5rem; opacity: 0.4; }

    .cart-item {
      display: flex;
      gap: 0.85rem;
      padding: 1rem 0;
      border-bottom: 1px solid var(--border);
      animation: fadeIn 0.25s ease;
    }

    .cart-item:last-child { border-bottom: none; }

    .cart-item-thumb {
      width: 56px; height: 56px;
      background: var(--bg-card2);
      border: 1px solid var(--border);
      display: flex; align-items: center; justify-content: center;
      font-size: 1.6rem;
      flex-shrink: 0;
      overflow: hidden;
    }

    .cart-item-thumb img {
      width: 100%; height: 100%;
      object-fit: contain;
      padding: 4px;
    }

    .cart-item-details { flex: 1; min-width: 0; }

    .cart-item-name {
      font-size: 0.8rem;
      color: var(--text);
      font-weight: 400;
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
      margin-bottom: 0.2rem;
    }

    .cart-item-cat {
      font-size: 0.65rem;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: var(--gold-dim);
    }

    .cart-item-controls {
      display: flex;
      align-items: center;
      gap: 0.5rem;
      margin-top: 0.5rem;
    }

    .qty-btn {
      background: transparent;
      border: 1px solid var(--border);
      color: var(--text-muted);
      width: 22px; height: 22px;
      cursor: pointer;
      display: flex; align-items: center; justify-content: center;
      font-size: 0.9rem;
      transition: border-color 0.2s, color 0.2s;
      line-height: 1;
    }

    .qty-btn:hover { border-color: var(--gold-dim); color: var(--gold); }

    .qty-val {
      font-size: 0.82rem;
      color: var(--text-mid);
      min-width: 18px;
      text-align: center;
    }

    .cart-item-remove {
      background: none;
      border: none;
      color: var(--text-muted);
      cursor: pointer;
      font-size: 0.7rem;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      padding: 0;
      margin-left: auto;
      align-self: flex-start;
      margin-top: 2px;
      transition: color 0.2s;
    }

    .cart-item-remove:hover { color: #c0392b; }

    /* ── FOOTER CARRITO ── */
    .cart-panel-footer {
      padding: 1.2rem 1.5rem 1.5rem;
      border-top: 1px solid var(--border);
    }

    .cart-summary-line {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 0.5rem;
      font-size: 0.8rem;
      color: var(--text-muted);
    }

    .cart-total-line {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin: 1rem 0;
      padding-top: 0.75rem;
      border-top: 1px solid var(--border);
    }

    .cart-total-label {
      font-family: 'Cinzel', serif;
      font-size: 0.85rem;
      color: var(--text);
      letter-spacing: 0.08em;
    }

    .cart-total-val {
      font-family: 'Cinzel', serif;
      font-size: 1.1rem;
      color: var(--gold);
      font-weight: 700;
    }

    .cart-note {
      font-size: 0.72rem;
      color: var(--text-muted);
      line-height: 1.6;
      margin-bottom: 1rem;
      font-style: italic;
    }

    .cart-checkout-btn {
      width: 100%;
      background: var(--gold);
      border: none;
      color: #0a0a0a;
      font-family: 'DM Sans', sans-serif;
      font-size: 0.75rem;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      font-weight: 500;
      padding: 0.9rem;
      cursor: pointer;
      transition: background 0.25s;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 0.5rem;
    }

    .cart-checkout-btn:hover { background: var(--gold-light); }
    .cart-checkout-btn:disabled { opacity: 0.4; cursor: not-allowed; }

    .cart-clear-btn {
      width: 100%;
      background: transparent;
      border: 1px solid var(--border);
      color: var(--text-muted);
      font-family: 'DM Sans', sans-serif;
      font-size: 0.7rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      padding: 0.6rem;
      cursor: pointer;
      margin-top: 0.5rem;
      transition: border-color 0.2s, color 0.2s;
    }

    .cart-clear-btn:hover { border-color: var(--border-hover); color: var(--text); }

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

    .hero-bg-lines { position: absolute; inset: 0; overflow: hidden; pointer-events: none; }

    .hero-bg-lines::before, .hero-bg-lines::after {
      content: '';
      position: absolute;
      border-radius: 50%;
      border: 1px solid rgba(201,168,76,0.07);
    }

    .hero-bg-lines::before { width: 800px; height: 800px; top: 50%; left: 50%; transform: translate(-50%,-50%); }
    .hero-bg-lines::after  { width: 500px; height: 500px; top: 50%; left: 50%; transform: translate(-50%,-50%); }

    .hero-eyebrow {
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
      color: var(--text);
      opacity: 0;
      animation: fadeUp 0.9s 0.4s forwards;
    }

    .hero h1 span { display: block; color: var(--gold); font-style: italic; font-weight: 400; }

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

    section { position: relative; z-index: 1; }

    .section-header { text-align: center; padding: 5rem 2rem 3rem; }

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

    .catalog-loading {
      text-align: center;
      padding: 4rem 2rem;
      color: var(--text-muted);
      font-size: 0.85rem;
      letter-spacing: 0.1em;
    }

    .catalog-loading .spinner {
      width: 32px; height: 32px;
      border: 2px solid var(--border);
      border-top-color: var(--gold);
      border-radius: 50%;
      margin: 0 auto 1rem;
      animation: spin 0.8s linear infinite;
    }

    @keyframes spin { to { transform: rotate(360deg); } }

    .categories { padding: 0 2rem 3rem; max-width: 1100px; margin: 0 auto; }

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

    .filter-btn:hover, .filter-btn.active {
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

    .cat-card:hover { border-color: var(--border-hover); background: var(--bg-card2); transform: translateY(-3px); }
    .cat-card:hover::before { transform: scaleX(1); }

    .cat-icon { font-size: 2rem; margin-bottom: 1rem; display: block; }

    .cat-name {
      font-family: 'Cinzel', serif;
      font-size: 1rem;
      font-weight: 700;
      color: var(--gold);
      letter-spacing: 0.05em;
      margin-bottom: 0.4rem;
    }

    .cat-desc { font-size: 0.8rem; color: var(--text-muted); line-height: 1.6; }

    .cat-count {
      position: absolute;
      top: 1rem; right: 1rem;
      font-size: 0.65rem;
      letter-spacing: 0.15em;
      color: var(--gold-dim);
      text-transform: uppercase;
    }

    .stickers-section { max-width: 1100px; margin: 0 auto; padding: 0 2rem 5rem; display: none; }
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

    .stickers-title { font-family: 'Cinzel', serif; font-size: 1.8rem; color: var(--text); }

    .stickers-count {
      font-size: 0.72rem;
      letter-spacing: 0.15em;
      color: var(--gold-dim);
      text-transform: uppercase;
    }

    .stickers-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
      gap: 1rem;
    }

    /* ── STICKER CARD con botón carrito ── */
    .sticker-card {
      background: var(--bg-card);
      border: 1px solid var(--border);
      overflow: hidden;
      transition: border-color 0.25s, transform 0.25s;
      position: relative;
    }

    .sticker-card:hover { border-color: var(--border-hover); transform: translateY(-3px); }

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
      padding: 0.75rem;
      display: block;
      transition: transform 0.35s ease;
    }

    .sticker-card:hover .sticker-img { transform: scale(1.06); }

    .sticker-skeleton {
      position: absolute;
      inset: 0;
      background: linear-gradient(90deg, #161616 25%, #1e1e1e 50%, #161616 75%);
      background-size: 200% 100%;
      animation: shimmer 1.4s infinite;
    }

    @keyframes shimmer {
      0%   { background-position: 200% 0; }
      100% { background-position: -200% 0; }
    }

    .sticker-info { padding: 0.85rem 1rem 0.65rem; }

    .sticker-name { font-size: 0.82rem; color: var(--text-mid); font-weight: 400; margin-bottom: 0.35rem; }

    .sticker-badge {
      display: inline-block;
      font-size: 0.6rem;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: var(--gold-dim);
      border: 1px solid var(--border);
      padding: 0.15rem 0.5rem;
    }

    /* ── BOTÓN AGREGAR AL CARRITO ── */
    .add-to-cart-btn {
      width: calc(100% - 2rem);
      margin: 0 1rem 0.85rem;
      background: transparent;
      border: 1px solid var(--border);
      color: var(--text-muted);
      font-family: 'DM Sans', sans-serif;
      font-size: 0.68rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      padding: 0.55rem 0.5rem;
      cursor: pointer;
      transition: background 0.2s, border-color 0.2s, color 0.2s;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 0.4rem;
    }

    .add-to-cart-btn:hover {
      background: var(--gold);
      border-color: var(--gold);
      color: #0a0a0a;
    }

    .add-to-cart-btn.added {
      background: rgba(201,168,76,0.12);
      border-color: var(--gold-dim);
      color: var(--gold);
    }

    /* ── SECCIÓN PERSONALIZADA ── */
    .custom-banner { max-width: 1100px; margin: 0 auto 5rem; padding: 0 2rem; }

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

    .custom-text h3 { font-family: 'Cinzel', serif; font-size: 1.4rem; color: var(--gold); margin-bottom: 0.5rem; }
    .custom-text p  { font-size: 0.85rem; color: var(--text-muted); max-width: 420px; line-height: 1.7; }

    /* ── CONTACTO ── */
    #contacto { background: var(--bg-card); border-top: 1px solid var(--border); }

    .contact-wrap { max-width: 700px; margin: 0 auto; padding: 5rem 2rem; }

    .contact-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 3rem; margin-top: 3rem; }

    .contact-info h4 { font-family: 'Cinzel', serif; font-size: 0.9rem; color: var(--gold); letter-spacing: 0.05em; margin-bottom: 1rem; }
    .contact-info p  { font-size: 0.83rem; color: var(--text-muted); line-height: 1.8; }
    .contact-info a  { color: var(--gold-dim); text-decoration: none; transition: color 0.2s; }
    .contact-info a:hover { color: var(--gold); }

    .contact-form { display: flex; flex-direction: column; gap: 0.75rem; }

    .form-group { display: flex; flex-direction: column; gap: 0.3rem; }

    .form-group label { font-size: 0.68rem; letter-spacing: 0.12em; text-transform: uppercase; color: var(--text-muted); }

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
    .form-group select:focus { border-color: var(--gold-dim); }

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

    .wsp-btn:hover { background: rgba(37,211,102,0.1); border-color: rgba(37,211,102,0.6); }

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

    footer {
      border-top: 1px solid var(--border);
      padding: 2rem 3rem;
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 1rem;
    }

    footer .logo { font-family: 'Cinzel', serif; font-size: 0.85rem; color: var(--gold); letter-spacing: 0.15em; }
    footer p { font-size: 0.72rem; color: var(--text-muted); letter-spacing: 0.05em; }

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

    /* ── CARRITO FLOTANTE (mobile) ── */
    .cart-float-btn {
      display: none;
      position: fixed;
      bottom: 1.5rem; left: 50%; transform: translateX(-50%);
      background: var(--gold);
      color: #0a0a0a;
      border: none;
      font-family: 'DM Sans', sans-serif;
      font-size: 0.75rem;
      font-weight: 500;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      padding: 0.85rem 1.8rem;
      cursor: pointer;
      z-index: 150;
      gap: 0.5rem;
      align-items: center;
      white-space: nowrap;
      transition: background 0.25s;
    }

    .cart-float-btn.visible { display: flex; }
    .cart-float-btn:hover { background: var(--gold-light); }

    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(20px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    @keyframes fadeIn {
      from { opacity: 0; }
      to   { opacity: 1; }
    }

    @media (max-width: 768px) {
      nav { padding: 1rem 1.5rem; }
      .nav-links { display: none; }
      .contact-grid { grid-template-columns: 1fr; gap: 2rem; }
      footer { flex-direction: column; text-align: center; }
      .stickers-grid { grid-template-columns: repeat(auto-fill, minmax(150px, 1fr)); }
      .cart-panel { width: 100%; }
    }
  </style>
</head>
<body>

  <!-- OVERLAY DEL CARRITO -->
  <div class="cart-overlay" id="cartOverlay" onclick="closeCart()"></div>

  <!-- PANEL LATERAL DEL CARRITO -->
  <div class="cart-panel" id="cartPanel">
    <div class="cart-panel-header">
      <span class="cart-panel-title">✦ Mi selección</span>
      <button class="cart-close-btn" onclick="closeCart()">✕</button>
    </div>

    <div class="cart-items-list" id="cartItemsList">
      <div class="cart-empty-msg">
        <span class="empty-icon">🛒</span>
        <span>Tu carrito está vacío.<br>Agregá calcos desde el catálogo.</span>
      </div>
    </div>

    <div class="cart-panel-footer" id="cartFooter" style="display:none;">
      <div class="cart-summary-line">
        <span id="cartSummaryItems">0 productos</span>
        <span style="color:var(--gold-dim); font-size:0.7rem; letter-spacing:0.08em;">SIN PRECIO FINAL AÚN</span>
      </div>
      <p class="cart-note">Los precios se confirman por WhatsApp según el tamaño y cantidad que elijas.</p>
      <div class="cart-total-line">
        <span class="cart-total-label">Tu pedido</span>
        <span class="cart-total-val" id="cartTotalVal">— calcos</span>
      </div>
      <button class="cart-checkout-btn" id="cartCheckoutBtn" onclick="sendCartWhatsApp()">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="#0a0a0a"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
        Consultar pedido por WhatsApp
      </button>
      <button class="cart-clear-btn" onclick="clearCart()">Vaciar selección</button>
    </div>
  </div>

  <!-- NAV -->
  <nav>
    <a href="#" class="nav-logo">GUERA CALCOS</a>
    <ul class="nav-links">
      <li><a href="#catalogo">Catálogo</a></li>
      <li><a href="#personalizadas">Personalizadas</a></li>
      <li><a href="#contacto">Contacto</a></li>
    </ul>
    <div class="nav-right">
      <button class="cart-nav-btn" id="cartNavBtn" onclick="openCart()">
        🛒 Carrito
        <span class="cart-nav-badge" id="cartNavBadge">0</span>
      </button>
      <a href="#contacto" class="nav-cta">Pedir ahora</a>
    </div>
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
      <div class="filter-bar" id="filterBar">
        <button class="filter-btn active" onclick="filterCat('todos', this)">Todos</button>
      </div>

      <div class="catalog-loading" id="catalogLoading">
        <div class="spinner"></div>
        Cargando catálogo...
      </div>

      <div class="cat-grid" id="catGrid" style="display:none;"></div>
    </div>

    <div class="stickers-section" id="stickersSection">
      <button class="stickers-back" onclick="closeStickers()">← Volver al catálogo</button>
      <div class="stickers-header">
        <h3 class="stickers-title" id="stickersTitle"></h3>
        <span class="stickers-count" id="stickersCount"></span>
      </div>
      <p style="font-size:0.82rem; color:var(--text-muted); margin-bottom:1.5rem; line-height:1.8;">
        Seleccioná los diseños que te interesan con el botón <strong style="color:var(--gold-dim);">+ Agregar</strong> y luego consultá tu pedido completo por WhatsApp. 🤍
      </p>
      <div class="stickers-grid" id="stickersGrid"></div>
      <div style="margin-top:2rem; display:flex; gap:1rem; flex-wrap:wrap;">
        <button class="btn-primary" onclick="openCart()">Ver mi selección 🛒</button>
        <a href="#contacto" class="btn-secondary">Consultar diseño</a>
      </div>
    </div>
  </section>

  <!-- PERSONALIZADAS -->
  <section id="personalizadas" style="padding-bottom:3rem;">
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
            <select id="contactSelect">
              <option value="">Seleccioná...</option>
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

  <footer>
    <span class="logo">GUERA CALCOS</span>
    <p>Calcomanías únicas · Devoto, Córdoba, Argentina</p>
    <p>Hecho con 🤍 para vos</p>
  </footer>

  <div class="toast" id="toast"></div>

  <!-- BOTÓN FLOTANTE MOBILE -->
  <button class="cart-float-btn" id="cartFloatBtn" onclick="openCart()">
    🛒 Ver selección (<span id="cartFloatCount">0</span>)
  </button>

  <script>
    const SHEET_CSV_URL = 'https://docs.google.com/spreadsheets/d/e/2PACX-1vTRTL0Mpj-YsHBFn6rJlkpLmcKakFGHc1YC8liFgRriXUj5OTvlsb_4dzONJ8Bvn47LtEy-1K3irz1g/pub?gid=0&single=true&output=csv';

    const catMeta = {
      imperiales:  { icon: '🎬​' }
      torpedos:  { icon: '🎬​' },
      camioneros:  { icon: '🎬​' },
      algarrobo:  { icon: '🎬​' },
      termos:  { icon: '🎬​' },
      materas:  { icon: '🎬​' },
      bombillas:  { icon: '🎬​' },
      yerberas:  { icon: '🎬​' },
      yerbas:  { icon: '🎬​' },
     
    };

    const catLabels = {
      imperiales:  { icon: '🎬​' }
      torpedos:  { icon: '🎬​' }
      camioneros:  { icon: '🎬​' }
      algarrobo:  { icon: '🎬​' }
      termos:  { icon: '🎬​' }
      materas:  { icon: '🎬​' }
      bombillas:  { icon: '🎬​' }
      yerberas:  { icon: '🎬​' }
      yerbas:  { icon: '🎬​' }
    };

    let catalogData = {};

    // ── CARRITO ──
    let cart = []; // [{ id, nombre, categoria, imagen_id, qty }]

    function cartItemId(nombre, categoria) {
      return `${categoria}__${nombre}`;
    }

    function addToCart(nombre, categoria, imagen_id, btnEl) {
      const id = cartItemId(nombre, categoria);
      const existing = cart.find(i => i.id === id);
      if (existing) {
        existing.qty += 1;
      } else {
        cart.push({ id, nombre, categoria, imagen_id, qty: 1 });
      }
      updateCartUI();
      showToast(`✦ "${nombre}" agregado a tu selección`);
      if (btnEl) {
        btnEl.classList.add('added');
        btnEl.textContent = '✓ Agregado';
        setTimeout(() => {
          btnEl.classList.remove('added');
          const qty = (cart.find(i => i.id === id) || {}).qty || 0;
          btnEl.textContent = qty > 1 ? `+ Agregar (${qty})` : '+ Agregar al carrito';
        }, 1200);
      }
    }

    function changeQty(id, delta) {
      const item = cart.find(i => i.id === id);
      if (!item) return;
      item.qty += delta;
      if (item.qty <= 0) cart = cart.filter(i => i.id !== id);
      renderCartPanel();
      updateCartBadge();
    }

    function removeFromCart(id) {
      cart = cart.filter(i => i.id !== id);
      renderCartPanel();
      updateCartBadge();
    }

    function clearCart() {
      cart = [];
      renderCartPanel();
      updateCartBadge();
    }

    function updateCartUI() {
      renderCartPanel();
      updateCartBadge();
    }

    function updateCartBadge() {
      const total = cart.reduce((s, i) => s + i.qty, 0);
      const badge = document.getElementById('cartNavBadge');
      const btn   = document.getElementById('cartNavBtn');
      const float = document.getElementById('cartFloatBtn');
      const floatCount = document.getElementById('cartFloatCount');

      badge.textContent = total;
      badge.classList.toggle('visible', total > 0);
      btn.classList.toggle('has-items', total > 0);

      if (floatCount) floatCount.textContent = total;
      if (float) float.classList.toggle('visible', total > 0 && window.innerWidth <= 768);
    }

    function renderCartPanel() {
      const list   = document.getElementById('cartItemsList');
      const footer = document.getElementById('cartFooter');
      const sumEl  = document.getElementById('cartSummaryItems');
      const totEl  = document.getElementById('cartTotalVal');

      if (cart.length === 0) {
        list.innerHTML = `
          <div class="cart-empty-msg">
            <span class="empty-icon">🛒</span>
            <span>Tu carrito está vacío.<br>Agregá calcos desde el catálogo.</span>
          </div>`;
        footer.style.display = 'none';
        return;
      }

      const totalQty = cart.reduce((s, i) => s + i.qty, 0);

      list.innerHTML = cart.map(item => {
        const imgUrl = item.imagen_id
          ? `https://lh3.googleusercontent.com/d/${item.imagen_id}`
          : '';
        const catLabel = catLabels[item.categoria] || item.categoria;
        return `
          <div class="cart-item" id="ci_${item.id.replace(/[^a-z0-9]/gi,'_')}">
            <div class="cart-item-thumb">
              ${imgUrl
                ? `<img src="${imgUrl}" alt="${item.nombre}" onerror="this.parentElement.innerHTML='📦'" />`
                : '📦'}
            </div>
            <div class="cart-item-details">
              <div class="cart-item-name">${item.nombre}</div>
              <div class="cart-item-cat">${catLabel}</div>
              <div class="cart-item-controls">
                <button class="qty-btn" onclick="changeQty('${item.id}', -1)">−</button>
                <span class="qty-val">${item.qty}</span>
                <button class="qty-btn" onclick="changeQty('${item.id}', 1)">+</button>
                <button class="cart-item-remove" onclick="removeFromCart('${item.id}')">Quitar</button>
              </div>
            </div>
          </div>`;
      }).join('');

      sumEl.textContent = `${totalQty} calco${totalQty !== 1 ? 's' : ''} seleccionado${totalQty !== 1 ? 's' : ''}`;
      totEl.textContent = `${totalQty} calco${totalQty !== 1 ? 's' : ''}`;
      footer.style.display = 'block';
    }

    function openCart() {
      document.getElementById('cartPanel').classList.add('open');
      document.getElementById('cartOverlay').classList.add('open');
      document.body.style.overflow = 'hidden';
    }

    function closeCart() {
      document.getElementById('cartPanel').classList.remove('open');
      document.getElementById('cartOverlay').classList.remove('open');
      document.body.style.overflow = '';
    }

    function sendCartWhatsApp() {
      if (cart.length === 0) return;
      const lines = cart.map(i => {
        const catLabel = catLabels[i.categoria] || i.categoria;
        return `• ${i.nombre} (${catLabel}) × ${i.qty}`;
      });
      const msg = `Hola Guera Calcos! 👋\n\nQuiero consultar por estos calcos:\n\n${lines.join('\n')}\n\n¿Me podés confirmar precio y disponibilidad? 🔥`;
      window.open(`https://wa.me/5493564204650?text=${encodeURIComponent(msg)}`, '_blank');
    }

    // ── CSV & RENDER ──
    function parseCSV(text) {
      const lines = text.trim().split('\n');
      const headers = lines[0].split(',').map(h => h.trim().toLowerCase().replace(/\r/g, ''));
      const rows = [];
      for (let i = 1; i < lines.length; i++) {
        const cols = lines[i].split(',').map(c => c.trim().replace(/\r/g, ''));
        if (!cols[0]) continue;
        const obj = {};
        headers.forEach((h, idx) => obj[h] = cols[idx] || '');
        if (obj.categoria && obj.nombre) rows.push(obj);
      }
      return rows;
    }

    function groupByCategory(rows) {
      const grouped = {};
      rows.forEach(row => {
        const cat = row.categoria.toLowerCase().trim();
        if (!grouped[cat]) grouped[cat] = [];
        grouped[cat].push({ nombre: row.nombre, imagen_id: row.imagen_id || '' });
      });
      return grouped;
    }

    function renderCategories(filter) {
      const grid = document.getElementById('catGrid');
      const cats = Object.keys(catalogData);
      const filtered = filter === 'todos' ? cats : cats.filter(c => c === filter);

      if (filtered.length === 0) {
        grid.innerHTML = '<p style="color:var(--text-muted); font-size:0.85rem;">No hay productos en esta categoría todavía.</p>';
        return;
      }

      grid.innerHTML = filtered.map(cat => {
        const meta  = catMeta[cat]   || { icon: '📦', desc: '' };
        const label = catLabels[cat] || (cat.charAt(0).toUpperCase() + cat.slice(1));
        const count = catalogData[cat].length;
        return `
          <div class="cat-card" data-cat="${cat}" onclick="showStickers('${cat}')">
            <span class="cat-count">${count} diseño${count !== 1 ? 's' : ''}</span>
            <span class="cat-icon">${meta.icon}</span>
            <div class="cat-name">${label}</div>
            <div class="cat-desc">${meta.desc}</div>
          </div>`;
      }).join('');
    }

    function renderFilters() {
      const bar = document.getElementById('filterBar');
      bar.innerHTML = `<button class="filter-btn active" onclick="filterCat('todos', this)">Todos</button>`;
      Object.keys(catalogData).forEach(cat => {
        const label = catLabels[cat] || (cat.charAt(0).toUpperCase() + cat.slice(1));
        bar.innerHTML += `<button class="filter-btn" onclick="filterCat('${cat}', this)">${label}</button>`;
      });
    }

    function renderContactSelect() {
      const sel = document.getElementById('contactSelect');
      sel.innerHTML = '<option value="">Seleccioná...</option>';
      Object.keys(catalogData).forEach(cat => {
        const label = catLabels[cat] || (cat.charAt(0).toUpperCase() + cat.slice(1));
        sel.innerHTML += `<option value="${cat}">${label}</option>`;
      });
      sel.innerHTML += '<option value="personalizada">Personalizada</option>';
    }

    async function loadCatalog() {
      try {
        const res  = await fetch(SHEET_CSV_URL);
        const text = await res.text();
        const rows = parseCSV(text);
        catalogData = groupByCategory(rows);

        document.getElementById('catalogLoading').style.display = 'none';
        document.getElementById('catGrid').style.display = '';

        renderFilters();
        renderCategories('todos');
        renderContactSelect();

      } catch (err) {
        document.getElementById('catalogLoading').innerHTML =
          '<p style="color:var(--text-muted); font-size:0.85rem;">No se pudo cargar el catálogo. Revisá tu conexión y recargá la página.</p>';
        console.error('Error cargando el catálogo:', err);
      }
    }

    function filterCat(cat, btn) {
      document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
      btn.classList.add('active');
      renderCategories(cat);
      closeStickers();
    }

    function showStickers(cat) {
      const stickers = catalogData[cat] || [];
      const label    = catLabels[cat] || cat;

      document.getElementById('stickersTitle').textContent = label;
      document.getElementById('stickersCount').textContent =
        `${stickers.length} diseño${stickers.length !== 1 ? 's' : ''}`;

      const grid = document.getElementById('stickersGrid');
      grid.innerHTML = stickers.map((s, i) => {
        const skId   = `sk_${cat}_${i}`;
        const imgUrl = s.imagen_id
          ? `https://lh3.googleusercontent.com/d/${s.imagen_id}`
          : '';
        const itemId = cartItemId(s.nombre, cat);
        const inCart = cart.find(ci => ci.id === itemId);
        const btnLabel = inCart ? `+ Agregar (${inCart.qty})` : '+ Agregar al carrito';

        return `
          <div class="sticker-card">
            <div class="sticker-img-wrap">
              ${imgUrl
                ? `<div class="sticker-skeleton" id="${skId}"></div>
                   <img
                     class="sticker-img"
                     src="${imgUrl}"
                     alt="${s.nombre}"
                     loading="lazy"
                     style="position:absolute;inset:0;"
                     onload="var el=document.getElementById('${skId}');if(el)el.remove();this.style.position='relative';"
                     onerror="this.parentElement.innerHTML='<div style=width:100%;height:100%;display:flex;align-items:center;justify-content:center;font-size:2.5rem;>📦</div>';"
                   />`
                : `<div style="width:100%;height:100%;display:flex;align-items:center;justify-content:center;font-size:2.5rem;">📦</div>`
              }
            </div>
            <div class="sticker-info">
              <div class="sticker-name">${s.nombre}</div>
              <span class="sticker-badge">Disponible</span>
            </div>
            <button
              class="add-to-cart-btn ${inCart ? 'added' : ''}"
              id="btn_${itemId.replace(/[^a-z0-9]/gi,'_')}"
              onclick="addToCart('${s.nombre.replace(/'/g,"\\'")}', '${cat}', '${s.imagen_id}', this)"
            >${btnLabel}</button>
          </div>`;
      }).join('');

      document.getElementById('catGrid').style.display = 'none';
      document.querySelector('.filter-bar').style.display = 'none';
      const sec = document.getElementById('stickersSection');
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
      const nombre    = e.target.querySelector('input[type="text"]').value.trim();
      const categoria = e.target.querySelector('select').value;
      const consulta  = e.target.querySelector('textarea').value.trim();
      const catLabel  = catLabels[categoria] || categoria || 'No especificada';
      const mensaje   = `Hola Guera Calcos! 👋\n\n*Nombre:* ${nombre}\n*Categoría:* ${catLabel}\n*Consulta:* ${consulta}`;
      window.open(`https://wa.me/5493564204650?text=${encodeURIComponent(mensaje)}`, '_blank');
      e.target.reset();
    }

    function showToast(msg) {
      const t = document.getElementById('toast');
      t.textContent = msg;
      t.classList.add('show');
      clearTimeout(t._timer);
      t._timer = setTimeout(() => t.classList.remove('show'), 2200);
    }

    // Responsive: mostrar/ocultar float btn
    window.addEventListener('resize', updateCartBadge);

    loadCatalog();
  </script>
</body>
</html>
