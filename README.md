<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>The Otter Outlook — Diving Beneath the Surface</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,600;0,800;1,400;1,600&family=Lora:ital,wght@0,400;0,500;1,400&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --orange: #F4A261;
    --orange-deep: #E08A4A;
    --green: #6A9C89;
    --green-deep: #527A6E;
    --green-light: #EBF2EF;
    --cream: #FAF7F2;
    --cream-dark: #F0EBE1;
    --charcoal: #2E2E2E;
    --charcoal-light: #4A4A4A;
    --mid: #8A8A8A;
    --border: rgba(106,156,137,0.2);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--cream);
    color: var(--charcoal);
    font-size: 16px;
    line-height: 1.6;
    overflow-x: hidden;
  }

  /* ── SCROLLBAR ─────────────────────────── */
  ::-webkit-scrollbar { width: 6px; }
  ::-webkit-scrollbar-track { background: var(--cream); }
  ::-webkit-scrollbar-thumb { background: var(--green); border-radius: 3px; }

  /* ── NAV ───────────────────────────────── */
  nav {
    position: sticky;
    top: 0;
    z-index: 100;
    background: var(--cream);
    border-bottom: 1.5px solid var(--border);
    backdrop-filter: blur(12px);
    -webkit-backdrop-filter: blur(12px);
  }

  .nav-inner {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 2rem;
    height: 68px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .logo {
    display: flex;
    align-items: center;
    gap: 0.6rem;
    text-decoration: none;
    color: var(--charcoal);
  }

  .logo-icon {
    width: 38px;
    height: 38px;
    background: var(--orange);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.2rem;
    box-shadow: 0 2px 8px rgba(244,162,97,0.4);
    transition: transform 0.3s ease;
  }
  .logo:hover .logo-icon { transform: rotate(-10deg) scale(1.08); }

  .logo-text {
    display: flex;
    flex-direction: column;
    line-height: 1.1;
  }
  .logo-name {
    font-family: 'Playfair Display', serif;
    font-weight: 800;
    font-size: 1.05rem;
    color: var(--charcoal);
    letter-spacing: -0.02em;
  }
  .logo-tagline {
    font-size: 0.65rem;
    color: var(--green);
    letter-spacing: 0.08em;
    text-transform: uppercase;
    font-weight: 500;
  }

  .nav-links {
    display: flex;
    align-items: center;
    gap: 0.2rem;
    list-style: none;
  }

  .nav-links a {
    text-decoration: none;
    color: var(--charcoal-light);
    font-size: 0.85rem;
    font-weight: 500;
    padding: 0.45rem 0.8rem;
    border-radius: 6px;
    transition: all 0.2s ease;
    letter-spacing: 0.01em;
  }
  .nav-links a:hover { color: var(--charcoal); background: var(--green-light); }
  .nav-links .btn-submit {
    background: var(--orange);
    color: white !important;
    padding: 0.45rem 1.1rem;
    border-radius: 20px;
    font-weight: 500;
    margin-left: 0.4rem;
    box-shadow: 0 2px 8px rgba(244,162,97,0.35);
  }
  .nav-links .btn-submit:hover { background: var(--orange-deep); transform: translateY(-1px); }

  .hamburger {
    display: none;
    flex-direction: column;
    gap: 5px;
    cursor: pointer;
    padding: 4px;
  }
  .hamburger span {
    display: block;
    width: 24px;
    height: 2px;
    background: var(--charcoal);
    border-radius: 2px;
    transition: all 0.3s;
  }

  .mobile-menu {
    display: none;
    position: fixed;
    top: 68px;
    left: 0;
    right: 0;
    background: var(--cream);
    border-bottom: 1.5px solid var(--border);
    padding: 1rem 2rem 1.5rem;
    z-index: 99;
  }
  .mobile-menu.open { display: block; }
  .mobile-menu a {
    display: block;
    padding: 0.65rem 0;
    color: var(--charcoal-light);
    text-decoration: none;
    font-weight: 500;
    border-bottom: 1px solid var(--border);
    font-size: 0.95rem;
  }
  .mobile-menu a:last-child { border-bottom: none; }

  /* ── HERO ──────────────────────────────── */
  .hero {
    background: var(--green);
    padding: 5rem 2rem 4.5rem;
    position: relative;
    overflow: hidden;
  }

  .hero::before {
    content: '';
    position: absolute;
    top: -60px; right: -60px;
    width: 320px; height: 320px;
    background: rgba(255,255,255,0.05);
    border-radius: 50%;
  }
  .hero::after {
    content: '';
    position: absolute;
    bottom: -80px; left: -40px;
    width: 250px; height: 250px;
    background: rgba(244,162,97,0.12);
    border-radius: 50%;
  }

  .hero-inner {
    max-width: 1200px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
    align-items: center;
    position: relative;
    z-index: 1;
  }

  .hero-label {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    background: rgba(244,162,97,0.2);
    color: var(--orange);
    padding: 0.3rem 0.9rem;
    border-radius: 20px;
    font-size: 0.72rem;
    font-weight: 600;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    margin-bottom: 1.2rem;
    border: 1px solid rgba(244,162,97,0.3);
  }

  .hero h1 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2rem, 4vw, 3rem);
    font-weight: 800;
    color: white;
    line-height: 1.18;
    margin-bottom: 1.2rem;
    letter-spacing: -0.02em;
  }
  .hero h1 em {
    font-style: italic;
    color: var(--orange);
  }

  .hero-summary {
    font-family: 'Lora', serif;
    color: rgba(255,255,255,0.82);
    font-size: 1.02rem;
    line-height: 1.75;
    margin-bottom: 2rem;
  }

  .hero-meta {
    display: flex;
    align-items: center;
    gap: 1rem;
    margin-bottom: 2rem;
  }
  .hero-author {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    color: rgba(255,255,255,0.75);
    font-size: 0.82rem;
    font-weight: 500;
  }
  .avatar-sm {
    width: 28px; height: 28px;
    border-radius: 50%;
    background: var(--orange);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 0.7rem;
    color: white;
    font-weight: 700;
    flex-shrink: 0;
  }
  .hero-divider {
    width: 4px; height: 4px;
    border-radius: 50%;
    background: rgba(255,255,255,0.35);
  }
  .hero-time {
    color: rgba(255,255,255,0.55);
    font-size: 0.78rem;
  }

  .btn-read {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    background: var(--orange);
    color: white;
    padding: 0.8rem 1.8rem;
    border-radius: 8px;
    text-decoration: none;
    font-weight: 600;
    font-size: 0.9rem;
    box-shadow: 0 4px 16px rgba(244,162,97,0.45);
    transition: all 0.25s ease;
    letter-spacing: 0.01em;
  }
  .btn-read:hover { transform: translateY(-2px); box-shadow: 0 8px 24px rgba(244,162,97,0.5); background: var(--orange-deep); }
  .btn-read svg { transition: transform 0.25s; }
  .btn-read:hover svg { transform: translateX(3px); }

  .hero-image {
    aspect-ratio: 4/3;
    background: rgba(255,255,255,0.08);
    border-radius: 16px;
    overflow: hidden;
    position: relative;
    border: 1px solid rgba(255,255,255,0.15);
  }

  .hero-image-placeholder {
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 1rem;
    color: rgba(255,255,255,0.4);
    font-size: 0.82rem;
    letter-spacing: 0.05em;
    text-transform: uppercase;
    position: relative;
    overflow: hidden;
  }
  .hero-image-placeholder::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, rgba(244,162,97,0.15) 0%, transparent 60%, rgba(106,156,137,0.2) 100%);
  }
  .hero-illo { font-size: 5rem; filter: drop-shadow(0 4px 12px rgba(0,0,0,0.2)); }

  .hero-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 0.4rem;
    margin-top: 1.5rem;
  }
  .tag {
    padding: 0.2rem 0.7rem;
    border-radius: 20px;
    font-size: 0.72rem;
    font-weight: 600;
    letter-spacing: 0.04em;
    cursor: pointer;
    transition: all 0.2s;
  }
  .tag-green { background: rgba(255,255,255,0.12); color: rgba(255,255,255,0.7); border: 1px solid rgba(255,255,255,0.15); }
  .tag-green:hover { background: rgba(255,255,255,0.2); }
  .tag-orange { background: rgba(244,162,97,0.15); color: var(--orange); border: 1px solid rgba(244,162,97,0.25); }
  .tag-light { background: var(--green-light); color: var(--green-deep); border: 1px solid var(--border); }
  .tag-light:hover { background: var(--green); color: white; }

  /* ── SECTION SHARED ────────────────────── */
  section { padding: 4.5rem 2rem; }
  .section-inner { max-width: 1200px; margin: 0 auto; }
  .section-header {
    display: flex;
    align-items: flex-end;
    justify-content: space-between;
    margin-bottom: 2.5rem;
    flex-wrap: wrap;
    gap: 1rem;
  }
  .section-title {
    font-family: 'Playfair Display', serif;
    font-size: 1.8rem;
    font-weight: 800;
    color: var(--charcoal);
    letter-spacing: -0.02em;
    line-height: 1.2;
  }
  .section-title span { color: var(--green); }
  .see-all {
    display: inline-flex;
    align-items: center;
    gap: 0.35rem;
    color: var(--green);
    text-decoration: none;
    font-size: 0.82rem;
    font-weight: 600;
    letter-spacing: 0.04em;
    text-transform: uppercase;
    transition: gap 0.2s;
  }
  .see-all:hover { gap: 0.6rem; }

  .section-rule {
    width: 48px;
    height: 3px;
    background: var(--orange);
    border-radius: 2px;
    margin-bottom: 0.6rem;
  }

  /* ── LATEST ARTICLES ───────────────────── */
  .articles-section { background: var(--cream); }

  .articles-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1.6rem;
  }

  .article-card {
    background: white;
    border-radius: 12px;
    overflow: hidden;
    border: 1.5px solid var(--border);
    transition: all 0.3s ease;
    cursor: pointer;
    display: flex;
    flex-direction: column;
  }
  .article-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 12px 36px rgba(46,46,46,0.10);
    border-color: var(--green);
  }

  .card-thumb {
    aspect-ratio: 16/9;
    background: var(--green-light);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 2.5rem;
    position: relative;
    overflow: hidden;
  }
  .card-thumb::after {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(to bottom, transparent 60%, rgba(106,156,137,0.15));
  }

  .card-body {
    padding: 1.3rem;
    display: flex;
    flex-direction: column;
    flex: 1;
  }
  .card-category {
    font-size: 0.68rem;
    font-weight: 700;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--green);
    margin-bottom: 0.5rem;
  }
  .card-title {
    font-family: 'Playfair Display', serif;
    font-size: 1.05rem;
    font-weight: 700;
    color: var(--charcoal);
    line-height: 1.35;
    margin-bottom: 0.6rem;
  }
  .card-preview {
    color: var(--mid);
    font-size: 0.82rem;
    line-height: 1.65;
    margin-bottom: 1rem;
    flex: 1;
  }
  .card-footer {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .card-author-row {
    display: flex;
    align-items: center;
    gap: 0.5rem;
  }
  .card-author-name { font-size: 0.78rem; font-weight: 600; color: var(--charcoal-light); }
  .card-time { font-size: 0.72rem; color: var(--mid); }

  /* ── UNDER THE SURFACE ─────────────────── */
  .surface-section {
    background: var(--charcoal);
    padding: 4.5rem 2rem;
  }

  .surface-section .section-title { color: white; }
  .surface-section .section-title span { color: var(--orange); }
  .surface-tagline {
    color: rgba(255,255,255,0.55);
    font-size: 0.88rem;
    font-family: 'Lora', serif;
    font-style: italic;
    margin-top: 0.3rem;
  }

  .surface-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1.4rem;
    margin-top: 2.5rem;
  }

  .surface-card {
    background: rgba(255,255,255,0.04);
    border: 1.5px solid rgba(255,255,255,0.08);
    border-radius: 12px;
    padding: 1.6rem;
    transition: all 0.3s;
    cursor: pointer;
  }
  .surface-card:hover {
    background: rgba(255,255,255,0.07);
    border-color: var(--orange);
    transform: translateY(-3px);
  }

  .surface-icon {
    width: 44px; height: 44px;
    border-radius: 10px;
    background: rgba(244,162,97,0.15);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.3rem;
    margin-bottom: 1rem;
    border: 1px solid rgba(244,162,97,0.25);
  }

  .surface-card h3 {
    font-family: 'Playfair Display', serif;
    font-size: 0.98rem;
    font-weight: 700;
    color: white;
    margin-bottom: 0.5rem;
    line-height: 1.3;
  }
  .surface-card p {
    color: rgba(255,255,255,0.5);
    font-size: 0.8rem;
    line-height: 1.65;
  }

  .surface-card .read-link {
    display: inline-flex;
    align-items: center;
    gap: 0.3rem;
    color: var(--orange);
    font-size: 0.75rem;
    font-weight: 600;
    letter-spacing: 0.05em;
    text-transform: uppercase;
    margin-top: 0.9rem;
    text-decoration: none;
    transition: gap 0.2s;
  }
  .surface-card .read-link:hover { gap: 0.55rem; }

  /* ── ESSAYS ────────────────────────────── */
  .essays-section { background: var(--cream-dark); }

  .essays-layout {
    display: grid;
    grid-template-columns: 2fr 1fr;
    gap: 2rem;
  }

  .essay-featured {
    background: white;
    border-radius: 14px;
    overflow: hidden;
    border: 1.5px solid var(--border);
    display: flex;
    flex-direction: column;
  }

  .essay-featured-thumb {
    aspect-ratio: 16/7;
    background: linear-gradient(135deg, var(--green-light), var(--cream));
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 4rem;
    position: relative;
    overflow: hidden;
  }
  .essay-featured-thumb::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(to bottom right, rgba(106,156,137,0.15), rgba(244,162,97,0.08));
  }

  .essay-featured-body { padding: 2rem; }
  .essay-label {
    display: inline-flex;
    align-items: center;
    gap: 0.4rem;
    background: var(--green-light);
    color: var(--green-deep);
    padding: 0.25rem 0.7rem;
    border-radius: 20px;
    font-size: 0.68rem;
    font-weight: 700;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    margin-bottom: 1rem;
    border: 1px solid var(--border);
  }
  .essay-featured-body h2 {
    font-family: 'Playfair Display', serif;
    font-size: 1.6rem;
    font-weight: 800;
    color: var(--charcoal);
    line-height: 1.25;
    margin-bottom: 0.9rem;
    letter-spacing: -0.02em;
  }
  .essay-featured-body p {
    font-family: 'Lora', serif;
    color: var(--charcoal-light);
    font-size: 0.92rem;
    line-height: 1.8;
    margin-bottom: 1.5rem;
  }
  .essay-meta {
    display: flex;
    align-items: center;
    gap: 0.8rem;
    flex-wrap: wrap;
  }
  .essay-author {
    display: flex;
    align-items: center;
    gap: 0.45rem;
    font-size: 0.78rem;
    font-weight: 600;
    color: var(--charcoal-light);
  }
  .essay-dot { color: var(--mid); }
  .essay-read-time { font-size: 0.75rem; color: var(--mid); }

  .essays-sidebar { display: flex; flex-direction: column; gap: 1rem; }
  .essay-mini {
    background: white;
    border-radius: 10px;
    padding: 1.2rem;
    border: 1.5px solid var(--border);
    cursor: pointer;
    transition: all 0.25s;
    display: flex;
    gap: 1rem;
    align-items: flex-start;
  }
  .essay-mini:hover { border-color: var(--green); transform: translateX(3px); }
  .essay-mini-num {
    font-family: 'Playfair Display', serif;
    font-size: 1.6rem;
    font-weight: 800;
    color: var(--green-light);
    line-height: 1;
    flex-shrink: 0;
    width: 32px;
  }
  .essay-mini-content {}
  .essay-mini h4 {
    font-family: 'Playfair Display', serif;
    font-size: 0.88rem;
    font-weight: 700;
    color: var(--charcoal);
    line-height: 1.35;
    margin-bottom: 0.3rem;
  }
  .essay-mini p { font-size: 0.74rem; color: var(--mid); line-height: 1.5; }

  /* ── DEBATE ────────────────────────────── */
  .debate-section { background: white; }

  .debate-box {
    border: 2px solid var(--border);
    border-radius: 16px;
    overflow: hidden;
  }

  .debate-header {
    background: var(--green);
    padding: 1.8rem 2rem;
    text-align: center;
  }
  .debate-badge {
    display: inline-flex;
    align-items: center;
    gap: 0.4rem;
    background: rgba(255,255,255,0.15);
    color: white;
    padding: 0.25rem 0.8rem;
    border-radius: 20px;
    font-size: 0.68rem;
    font-weight: 700;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    margin-bottom: 0.8rem;
  }
  .debate-question {
    font-family: 'Playfair Display', serif;
    font-size: 1.4rem;
    font-weight: 800;
    color: white;
    line-height: 1.3;
  }

  .debate-sides {
    display: grid;
    grid-template-columns: 1fr 1fr;
  }

  .debate-side {
    padding: 2rem;
  }
  .debate-side:first-child {
    border-right: 1.5px solid var(--border);
  }

  .debate-side-label {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    margin-bottom: 1rem;
  }
  .debate-badge-yes {
    background: rgba(106,156,137,0.12);
    color: var(--green-deep);
    padding: 0.2rem 0.7rem;
    border-radius: 20px;
    font-size: 0.7rem;
    font-weight: 700;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    border: 1px solid rgba(106,156,137,0.25);
  }
  .debate-badge-no {
    background: rgba(244,162,97,0.12);
    color: var(--orange-deep);
    padding: 0.2rem 0.7rem;
    border-radius: 20px;
    font-size: 0.7rem;
    font-weight: 700;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    border: 1px solid rgba(244,162,97,0.25);
  }

  .debate-side-title {
    font-family: 'Playfair Display', serif;
    font-size: 1.05rem;
    font-weight: 700;
    color: var(--charcoal);
    margin-bottom: 0.6rem;
    line-height: 1.3;
  }

  .debate-side p {
    font-family: 'Lora', serif;
    font-size: 0.85rem;
    color: var(--charcoal-light);
    line-height: 1.75;
    margin-bottom: 1rem;
  }

  .debate-author-row {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    padding-top: 1rem;
    border-top: 1px solid var(--border);
  }
  .debate-author-info { font-size: 0.76rem; }
  .debate-author-info strong { color: var(--charcoal); display: block; font-size: 0.8rem; }
  .debate-author-info span { color: var(--mid); }

  /* ── COMMUNITY VOICES ──────────────────── */
  .voices-section { background: var(--cream); }

  .voices-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 1.2rem;
  }

  .voice-card {
    background: white;
    border-radius: 12px;
    padding: 1.4rem;
    border: 1.5px solid var(--border);
    transition: all 0.25s;
    cursor: pointer;
  }
  .voice-card:hover { border-color: var(--orange); transform: translateY(-3px); box-shadow: 0 8px 24px rgba(244,162,97,0.12); }

  .voice-top {
    display: flex;
    align-items: center;
    gap: 0.7rem;
    margin-bottom: 0.9rem;
  }
  .voice-avatar {
    width: 40px; height: 40px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 700;
    font-size: 0.85rem;
    color: white;
    flex-shrink: 0;
  }
  .voice-info {}
  .voice-name { font-size: 0.82rem; font-weight: 700; color: var(--charcoal); }
  .voice-role { font-size: 0.7rem; color: var(--mid); }

  .voice-quote {
    font-family: 'Lora', serif;
    font-style: italic;
    font-size: 0.85rem;
    color: var(--charcoal-light);
    line-height: 1.65;
    margin-bottom: 0.8rem;
  }
  .voice-title {
    font-size: 0.72rem;
    font-weight: 700;
    color: var(--green);
    letter-spacing: 0.02em;
  }

  /* ── NEWSLETTER ────────────────────────── */
  .newsletter-section {
    background: linear-gradient(135deg, var(--green) 0%, var(--green-deep) 100%);
    padding: 5rem 2rem;
    position: relative;
    overflow: hidden;
  }
  .newsletter-section::before {
    content: '🦦';
    position: absolute;
    font-size: 12rem;
    opacity: 0.05;
    right: -2rem;
    top: 50%;
    transform: translateY(-50%);
  }

  .newsletter-inner {
    max-width: 600px;
    margin: 0 auto;
    text-align: center;
    position: relative;
    z-index: 1;
  }

  .newsletter-otter { font-size: 3rem; margin-bottom: 1rem; }
  .newsletter-inner h2 {
    font-family: 'Playfair Display', serif;
    font-size: 2rem;
    font-weight: 800;
    color: white;
    margin-bottom: 0.6rem;
    letter-spacing: -0.02em;
    line-height: 1.2;
  }
  .newsletter-inner p {
    color: rgba(255,255,255,0.75);
    font-family: 'Lora', serif;
    font-style: italic;
    font-size: 0.95rem;
    margin-bottom: 2rem;
  }

  .newsletter-form {
    display: flex;
    gap: 0.6rem;
    max-width: 440px;
    margin: 0 auto 1rem;
  }
  .newsletter-form input {
    flex: 1;
    padding: 0.85rem 1.2rem;
    border: none;
    border-radius: 8px;
    background: rgba(255,255,255,0.15);
    color: white;
    font-size: 0.88rem;
    outline: none;
    backdrop-filter: blur(8px);
    font-family: 'DM Sans', sans-serif;
    border: 1.5px solid rgba(255,255,255,0.2);
    transition: all 0.2s;
  }
  .newsletter-form input::placeholder { color: rgba(255,255,255,0.55); }
  .newsletter-form input:focus { border-color: rgba(255,255,255,0.5); background: rgba(255,255,255,0.22); }

  .btn-subscribe {
    padding: 0.85rem 1.5rem;
    background: var(--orange);
    color: white;
    border: none;
    border-radius: 8px;
    font-weight: 700;
    font-size: 0.88rem;
    cursor: pointer;
    transition: all 0.25s;
    font-family: 'DM Sans', sans-serif;
    box-shadow: 0 4px 12px rgba(244,162,97,0.4);
    white-space: nowrap;
  }
  .btn-subscribe:hover { background: var(--orange-deep); transform: translateY(-1px); }

  .newsletter-note {
    color: rgba(255,255,255,0.45);
    font-size: 0.73rem;
  }

  /* ── SUBMIT PAGE ───────────────────────── */
  .submit-section { background: var(--cream); display: none; }
  .submit-section.active { display: block; }

  .submit-inner {
    max-width: 700px;
    margin: 0 auto;
  }
  .submit-intro {
    font-family: 'Lora', serif;
    font-style: italic;
    color: var(--charcoal-light);
    font-size: 0.95rem;
    line-height: 1.75;
    margin-bottom: 2.5rem;
  }

  .form-group {
    margin-bottom: 1.4rem;
  }
  .form-label {
    display: block;
    font-size: 0.8rem;
    font-weight: 700;
    color: var(--charcoal);
    letter-spacing: 0.05em;
    text-transform: uppercase;
    margin-bottom: 0.5rem;
  }
  .form-input, .form-textarea, .form-select {
    width: 100%;
    padding: 0.85rem 1.1rem;
    border: 1.5px solid var(--border);
    border-radius: 8px;
    background: white;
    color: var(--charcoal);
    font-size: 0.9rem;
    font-family: 'DM Sans', sans-serif;
    outline: none;
    transition: all 0.2s;
  }
  .form-input:focus, .form-textarea:focus, .form-select:focus {
    border-color: var(--green);
    box-shadow: 0 0 0 3px rgba(106,156,137,0.12);
  }
  .form-textarea { min-height: 240px; resize: vertical; line-height: 1.7; }
  .form-hint { font-size: 0.73rem; color: var(--mid); margin-top: 0.4rem; }

  .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; }

  .btn-submit-form {
    background: var(--green);
    color: white;
    border: none;
    padding: 0.9rem 2.2rem;
    border-radius: 8px;
    font-weight: 700;
    font-size: 0.92rem;
    cursor: pointer;
    font-family: 'DM Sans', sans-serif;
    transition: all 0.25s;
    box-shadow: 0 4px 12px rgba(106,156,137,0.3);
    letter-spacing: 0.02em;
  }
  .btn-submit-form:hover { background: var(--green-deep); transform: translateY(-1px); }

  /* ── ARTICLE PAGE ──────────────────────── */
  .article-page { background: var(--cream); display: none; }
  .article-page.active { display: block; }

  .article-inner {
    max-width: 720px;
    margin: 0 auto;
    padding: 4rem 2rem 5rem;
  }

  .article-breadcrumb {
    font-size: 0.78rem;
    color: var(--mid);
    margin-bottom: 2rem;
    display: flex;
    align-items: center;
    gap: 0.4rem;
  }
  .article-breadcrumb a { color: var(--green); text-decoration: none; font-weight: 500; }
  .article-breadcrumb a:hover { text-decoration: underline; }

  .article-category-badge {
    display: inline-flex;
    align-items: center;
    background: var(--green-light);
    color: var(--green-deep);
    padding: 0.25rem 0.8rem;
    border-radius: 20px;
    font-size: 0.7rem;
    font-weight: 700;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    margin-bottom: 1.2rem;
    border: 1px solid var(--border);
  }

  .article-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(1.8rem, 4vw, 2.6rem);
    font-weight: 800;
    color: var(--charcoal);
    line-height: 1.2;
    letter-spacing: -0.025em;
    margin-bottom: 1.5rem;
  }

  .article-byline {
    display: flex;
    align-items: center;
    gap: 1rem;
    padding: 1.2rem 0;
    border-top: 1.5px solid var(--border);
    border-bottom: 1.5px solid var(--border);
    margin-bottom: 2.5rem;
    flex-wrap: wrap;
  }
  .byline-author {
    display: flex;
    align-items: center;
    gap: 0.6rem;
  }
  .byline-avatar {
    width: 42px; height: 42px;
    border-radius: 50%;
    background: var(--green);
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    font-weight: 700;
    font-size: 0.9rem;
  }
  .byline-info {}
  .byline-name { font-weight: 700; font-size: 0.88rem; color: var(--charcoal); }
  .byline-date { font-size: 0.75rem; color: var(--mid); }
  .byline-stats {
    display: flex;
    gap: 0.8rem;
    margin-left: auto;
    flex-wrap: wrap;
  }
  .byline-stat {
    display: flex;
    align-items: center;
    gap: 0.3rem;
    font-size: 0.76rem;
    color: var(--mid);
    background: var(--cream);
    padding: 0.3rem 0.7rem;
    border-radius: 20px;
    border: 1px solid var(--border);
  }

  .article-body {
    font-family: 'Lora', serif;
    font-size: 1.05rem;
    line-height: 1.9;
    color: var(--charcoal-light);
  }
  .article-body p { margin-bottom: 1.5rem; }
  .article-body h2 {
    font-family: 'Playfair Display', serif;
    font-size: 1.4rem;
    font-weight: 800;
    color: var(--charcoal);
    margin: 2.5rem 0 1rem;
    letter-spacing: -0.02em;
  }
  .article-body blockquote {
    border-left: 3px solid var(--orange);
    padding: 0.5rem 0 0.5rem 1.5rem;
    margin: 2rem 0;
    font-style: italic;
    color: var(--charcoal);
    font-size: 1.1rem;
    line-height: 1.75;
  }
  .article-body strong { color: var(--charcoal); font-weight: 600; }

  .article-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
    margin: 2.5rem 0;
    padding-top: 2rem;
    border-top: 1.5px solid var(--border);
  }

  .comments-section {
    margin-top: 3rem;
    padding-top: 2.5rem;
    border-top: 2px solid var(--border);
  }
  .comments-title {
    font-family: 'Playfair Display', serif;
    font-size: 1.3rem;
    font-weight: 800;
    color: var(--charcoal);
    margin-bottom: 1.5rem;
  }

  .comment-box {
    background: white;
    border-radius: 12px;
    padding: 1.5rem;
    border: 1.5px solid var(--border);
    margin-bottom: 1.5rem;
  }
  .comment-box textarea {
    width: 100%;
    border: 1.5px solid var(--border);
    border-radius: 8px;
    padding: 0.85rem;
    font-family: 'DM Sans', sans-serif;
    font-size: 0.88rem;
    color: var(--charcoal);
    resize: vertical;
    min-height: 100px;
    outline: none;
    background: var(--cream);
    transition: border-color 0.2s;
  }
  .comment-box textarea:focus { border-color: var(--green); }
  .comment-submit {
    margin-top: 0.8rem;
    background: var(--orange);
    color: white;
    border: none;
    padding: 0.65rem 1.5rem;
    border-radius: 6px;
    font-size: 0.85rem;
    font-weight: 700;
    cursor: pointer;
    font-family: 'DM Sans', sans-serif;
    transition: all 0.2s;
  }
  .comment-submit:hover { background: var(--orange-deep); }

  .comment {
    padding: 1.2rem 0;
    border-bottom: 1px solid var(--border);
  }
  .comment:last-child { border-bottom: none; }
  .comment-header {
    display: flex;
    align-items: center;
    gap: 0.6rem;
    margin-bottom: 0.5rem;
  }
  .comment-name { font-size: 0.82rem; font-weight: 700; color: var(--charcoal); }
  .comment-date { font-size: 0.72rem; color: var(--mid); margin-left: auto; }
  .comment p { font-size: 0.85rem; color: var(--charcoal-light); line-height: 1.65; }

  /* ── FOOTER ────────────────────────────── */
  footer {
    background: var(--charcoal);
    color: white;
    padding: 3.5rem 2rem 2rem;
  }
  .footer-inner {
    max-width: 1200px;
    margin: 0 auto;
  }
  .footer-top {
    display: grid;
    grid-template-columns: 2fr 1fr 1fr 1fr;
    gap: 3rem;
    margin-bottom: 3rem;
  }
  .footer-brand {}
  .footer-logo {
    display: flex;
    align-items: center;
    gap: 0.6rem;
    margin-bottom: 0.8rem;
  }
  .footer-logo-icon {
    width: 34px; height: 34px;
    background: var(--orange);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1rem;
  }
  .footer-logo-text {
    font-family: 'Playfair Display', serif;
    font-size: 1rem;
    font-weight: 800;
    color: white;
  }
  .footer-desc {
    color: rgba(255,255,255,0.45);
    font-size: 0.82rem;
    line-height: 1.7;
  }

  .footer-col h4 {
    font-size: 0.72rem;
    font-weight: 700;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: rgba(255,255,255,0.45);
    margin-bottom: 1rem;
  }
  .footer-col ul { list-style: none; }
  .footer-col li { margin-bottom: 0.5rem; }
  .footer-col a {
    color: rgba(255,255,255,0.6);
    text-decoration: none;
    font-size: 0.85rem;
    transition: color 0.2s;
  }
  .footer-col a:hover { color: var(--orange); }

  .footer-bottom {
    border-top: 1px solid rgba(255,255,255,0.08);
    padding-top: 1.5rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 0.5rem;
  }
  .footer-copy { font-size: 0.75rem; color: rgba(255,255,255,0.3); }
  .footer-love { font-size: 0.75rem; color: rgba(255,255,255,0.3); }
  .footer-love span { color: var(--orange); }

  /* ── PAGE VIEWS ────────────────────────── */
  .page { display: block; }
  .page.hidden { display: none; }

  /* ── ANIMATIONS ────────────────────────── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }
  .fade-up { animation: fadeUp 0.55s ease forwards; }
  .fade-up-1 { animation-delay: 0.1s; opacity: 0; }
  .fade-up-2 { animation-delay: 0.2s; opacity: 0; }
  .fade-up-3 { animation-delay: 0.3s; opacity: 0; }

  /* ── MOBILE ────────────────────────────── */
  @media (max-width: 900px) {
    .hero-inner { grid-template-columns: 1fr; gap: 2rem; }
    .hero-image { display: none; }
    .articles-grid { grid-template-columns: 1fr 1fr; }
    .surface-grid { grid-template-columns: 1fr 1fr; }
    .essays-layout { grid-template-columns: 1fr; }
    .voices-grid { grid-template-columns: 1fr 1fr; }
    .footer-top { grid-template-columns: 1fr 1fr; gap: 2rem; }
  }

  @media (max-width: 620px) {
    .nav-links { display: none; }
    .hamburger { display: flex; }
    .articles-grid { grid-template-columns: 1fr; }
    .surface-grid { grid-template-columns: 1fr; }
    .debate-sides { grid-template-columns: 1fr; }
    .debate-side:first-child { border-right: none; border-bottom: 1.5px solid var(--border); }
    .voices-grid { grid-template-columns: 1fr; }
    .newsletter-form { flex-direction: column; }
    .footer-top { grid-template-columns: 1fr; gap: 1.5rem; }
    .form-row { grid-template-columns: 1fr; }
    .byline-stats { margin-left: 0; }
    section { padding: 3rem 1.2rem; }
    .hero { padding: 3rem 1.2rem; }
  }
</style>
</head>
<body>

<!-- ── NAV ──────────────────────────────────────────── -->
<nav>
  <div class="nav-inner">
    <a href="#" class="logo" onclick="showPage('home')">
      <div class="logo-icon">🦦</div>
      <div class="logo-text">
        <span class="logo-name">The Otter Outlook</span>
        <span class="logo-tagline">Diving beneath the surface</span>
      </div>
    </a>
    <ul class="nav-links">
      <li><a href="#" onclick="showPage('home')">Home</a></li>
      <li><a href="#articles">Articles</a></li>
      <li><a href="#essays">Essays</a></li>
      <li><a href="#debate">Debates</a></li>
      <li><a href="#" onclick="showPage('submit')" class="btn-submit">Submit</a></li>
      <li><a href="#about">About</a></li>
    </ul>
    <div class="hamburger" onclick="toggleMenu()" id="hamburger">
      <span></span><span></span><span></span>
    </div>
  </div>
</nav>

<div class="mobile-menu" id="mobileMenu">
  <a href="#" onclick="showPage('home'); toggleMenu()">Home</a>
  <a href="#articles" onclick="toggleMenu()">Articles</a>
  <a href="#essays" onclick="toggleMenu()">Essays</a>
  <a href="#debate" onclick="toggleMenu()">Debates</a>
  <a href="#" onclick="showPage('submit'); toggleMenu()">Submit an Essay</a>
  <a href="#about" onclick="toggleMenu()">About</a>
</div>

<!-- ── HOME PAGE ─────────────────────────────────────── -->
<div id="page-home" class="page">

  <!-- HERO -->
  <section class="hero">
    <div class="hero-inner">
      <div class="fade-up fade-up-1">
        <div class="hero-label">✦ Featured Article</div>
        <h1>Why <em>misinformation</em> spreads faster than truth online</h1>
        <p class="hero-summary">A deep look at the psychological, algorithmic, and social forces that make false stories travel six times faster than accurate ones — and what we can actually do about it.</p>
        <div class="hero-meta">
          <div class="hero-author">
            <div class="avatar-sm">OT</div>
            Otto Tanaka
          </div>
          <div class="hero-divider"></div>
          <span class="hero-time">⏱ 8 min read</span>
          <div class="hero-divider"></div>
          <span class="hero-time">March 9, 2026</span>
        </div>
        <div style="display:flex; align-items:center; gap:1rem; flex-wrap:wrap;">
          <a href="#" class="btn-read" onclick="showPage('article')">
            Read Article
            <svg width="14" height="14" viewBox="0 0 16 16" fill="none"><path d="M3 8h10M9 4l4 4-4 4" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg>
          </a>
        </div>
        <div class="hero-tags">
          <span class="tag tag-green">Media</span>
          <span class="tag tag-green">Social Platforms</span>
          <span class="tag tag-green">Psychology</span>
          <span class="tag tag-orange">Editor's Pick</span>
        </div>
      </div>
      <div class="hero-image fade-up fade-up-2">
        <div class="hero-image-placeholder">
          <div class="hero-illo">🦦</div>
          <span>Feature Illustration</span>
        </div>
      </div>
    </div>
  </section>

  <!-- LATEST ARTICLES -->
  <section class="articles-section" id="articles">
    <div class="section-inner">
      <div class="section-header">
        <div>
          <div class="section-rule"></div>
          <h2 class="section-title">Latest <span>Articles</span></h2>
        </div>
        <a href="#" class="see-all">View all →</a>
      </div>
      <div class="articles-grid">

        <div class="article-card" onclick="showPage('article')">
          <div class="card-thumb" style="background: linear-gradient(135deg, #EBF2EF, #d4e8e1);">📱</div>
          <div class="card-body">
            <div class="card-category">Media & Society</div>
            <div class="card-title">Why young people are quietly abandoning the news</div>
            <div class="card-preview">New research shows 18–34 year olds aren't just tuning out — they're actively avoiding news as a form of self-preservation. What does this mean for democracy?</div>
            <div class="card-footer">
              <div class="card-author-row">
                <div class="avatar-sm" style="background: var(--green);">OT</div>
                <span class="card-author-name">Otto Tanaka</span>
              </div>
              <span class="card-time">5 min</span>
            </div>
          </div>
        </div>

        <div class="article-card" onclick="showPage('article')">
          <div class="card-thumb" style="background: linear-gradient(135deg, #fef3ea, #fde8cc);">🤖</div>
          <div class="card-body">
            <div class="card-category">Technology & Education</div>
            <div class="card-title">Is AI changing education too fast for us to keep up?</div>
            <div class="card-preview">Students are submitting AI-written essays while teachers write AI-detection prompts. We've ended up in an arms race nobody planned for.</div>
            <div class="card-footer">
              <div class="card-author-row">
                <div class="avatar-sm" style="background: var(--orange);">GW</div>
                <span class="card-author-name">Guest Writer</span>
              </div>
              <span class="card-time">7 min</span>
            </div>
          </div>
        </div>

        <div class="article-card" onclick="showPage('article')">
          <div class="card-thumb" style="background: linear-gradient(135deg, #f0edf8, #e4dff5);">⚖️</div>
          <div class="card-body">
            <div class="card-category">Media Literacy</div>
            <div class="card-title">What media bias actually looks like — and how to spot it</div>
            <div class="card-preview">Bias isn't always political spin. It's also what stories get ignored, which voices get quoted, and the quiet assumptions baked into every headline.</div>
            <div class="card-footer">
              <div class="card-author-row">
                <div class="avatar-sm" style="background: #8B7EC8;">LC</div>
                <span class="card-author-name">L. Chen</span>
              </div>
              <span class="card-time">6 min</span>
            </div>
          </div>
        </div>

        <div class="article-card" onclick="showPage('article')">
          <div class="card-thumb" style="background: linear-gradient(135deg, #f2ebe5, #e8ddd3);">🌍</div>
          <div class="card-body">
            <div class="card-category">Climate & Policy</div>
            <div class="card-title">The climate stories that get buried under the big headlines</div>
            <div class="card-preview">While record temperatures make front pages, quieter policy shifts — the ones that actually determine outcomes — go largely unnoticed.</div>
            <div class="card-footer">
              <div class="card-author-row">
                <div class="avatar-sm" style="background: #6A9C89;">MR</div>
                <span class="card-author-name">M. Reyes</span>
              </div>
              <span class="card-time">9 min</span>
            </div>
          </div>
        </div>

        <div class="article-card" onclick="showPage('article')">
          <div class="card-thumb" style="background: linear-gradient(135deg, #eef5f0, #d5e8de);">🗳️</div>
          <div class="card-body">
            <div class="card-category">Politics</div>
            <div class="card-title">Polling is broken. Here's why we keep using it anyway</div>
            <div class="card-preview">Election polls have missed the mark badly, repeatedly. Yet they remain central to political journalism. An honest reckoning with a broken system.</div>
            <div class="card-footer">
              <div class="card-author-row">
                <div class="avatar-sm" style="background: #C4845A;">AF</div>
                <span class="card-author-name">A. Foster</span>
              </div>
              <span class="card-time">11 min</span>
            </div>
          </div>
        </div>

        <div class="article-card" onclick="showPage('article')">
          <div class="card-thumb" style="background: linear-gradient(135deg, #fef0e8, #fde5d0);">💰</div>
          <div class="card-body">
            <div class="card-category">Economics</div>
            <div class="card-title">The cost of living crisis in numbers you can actually feel</div>
            <div class="card-preview">Forget inflation percentages. Here's what the same grocery basket, rent, and commute costs in 2026 compared to five years ago.</div>
            <div class="card-footer">
              <div class="card-author-row">
                <div class="avatar-sm" style="background: var(--orange);">CB</div>
                <span class="card-author-name">Contributor</span>
              </div>
              <span class="card-time">4 min</span>
            </div>
          </div>
        </div>

      </div>
    </div>
  </section>

  <!-- UNDER THE SURFACE -->
  <section class="surface-section">
    <div class="section-inner">
      <div class="section-header">
        <div>
          <div class="section-rule"></div>
          <h2 class="section-title">Under the <span>Surface</span></h2>
          <p class="surface-tagline">What the headlines miss, and why it matters.</p>
        </div>
        <a href="#" class="see-all" style="color: var(--orange);">Explore all →</a>
      </div>
      <div class="surface-grid">
        <div class="surface-card">
          <div class="surface-icon">🔍</div>
          <h3>What the headlines miss</h3>
          <p>Every major story has a quieter companion — a policy, a precedent, a person — that never makes the front page but shapes everything else.</p>
          <a href="#" class="read-link">Dive in →</a>
        </div>
        <div class="surface-card">
          <div class="surface-icon">📊</div>
          <h3>Bias in reporting</h3>
          <p>Where a story appears, whose quotes are used, and what framing is chosen — all of these are editorial decisions, even when they don't feel like it.</p>
          <a href="#" class="read-link">Dive in →</a>
        </div>
        <div class="surface-card">
          <div class="surface-icon">🌊</div>
          <h3>Hidden implications</h3>
          <p>A new law, a trade deal, a scientific study — what do they really mean for ordinary lives? We unpack the consequences buried in the fine print.</p>
          <a href="#" class="read-link">Dive in →</a>
        </div>
        <div class="surface-card">
          <div class="surface-icon">🧭</div>
          <h3>Context the news forgot</h3>
          <p>Understanding this week's events often requires knowing what happened years ago. We connect the dots mainstream coverage skips past.</p>
          <a href="#" class="read-link">Dive in →</a>
        </div>
        <div class="surface-card">
          <div class="surface-icon">🗣️</div>
          <h3>The voices we don't hear</h3>
          <p>Whose perspectives are systematically absent from coverage? We amplify sources beyond the usual expert rolodex.</p>
          <a href="#" class="read-link">Dive in →</a>
        </div>
        <div class="surface-card">
          <div class="surface-icon">⏳</div>
          <h3>Slow news that matters</h3>
          <p>Not every important story is urgent. Some of the most significant developments unfold over months or years, away from the breaking news cycle.</p>
          <a href="#" class="read-link">Dive in →</a>
        </div>
      </div>
    </div>
  </section>

  <!-- ESSAYS -->
  <section class="essays-section" id="essays">
    <div class="section-inner">
      <div class="section-header">
        <div>
          <div class="section-rule"></div>
          <h2 class="section-title">Featured <span>Essays</span></h2>
        </div>
        <a href="#" class="see-all">All essays →</a>
      </div>
      <div class="essays-layout">
        <div class="essay-featured">
          <div class="essay-featured-thumb">📰</div>
          <div class="essay-featured-body">
            <div class="essay-label">✦ Long Read</div>
            <h2>The death of nuance: how outrage became the currency of political media</h2>
            <p>We used to read newspapers to understand events. Now, much of what we consume is designed to make us feel — afraid, angry, outraged — because those emotions drive clicks. This essay traces how we got here, who profits, and whether there's a way back.</p>
            <div class="essay-meta">
              <div class="essay-author">
                <div class="avatar-sm" style="background: var(--green);">SR</div>
                <span>Sara Roth</span>
              </div>
              <span class="essay-dot">·</span>
              <span class="essay-read-time">⏱ 14 min read</span>
              <span class="essay-dot">·</span>
              <span class="essay-read-time">March 7, 2026</span>
            </div>
          </div>
        </div>
        <div class="essays-sidebar">
          <div class="essay-mini">
            <div class="essay-mini-num">01</div>
            <div class="essay-mini-content">
              <h4>The loneliness economy and why we're all angrier online</h4>
              <p>J. Nakamura · 10 min · March 5</p>
            </div>
          </div>
          <div class="essay-mini">
            <div class="essay-mini-num">02</div>
            <div class="essay-mini-content">
              <h4>What would journalism look like if it was funded by readers, not clicks?</h4>
              <p>A. Osei · 12 min · March 2</p>
            </div>
          </div>
          <div class="essay-mini">
            <div class="essay-mini-num">03</div>
            <div class="essay-mini-content">
              <h4>How our brain assigns blame — and why it gets the story wrong</h4>
              <p>T. Vasquez · 8 min · Feb 28</p>
            </div>
          </div>
          <div class="essay-mini">
            <div class="essay-mini-num">04</div>
            <div class="essay-mini-content">
              <h4>In defence of changing your mind publicly</h4>
              <p>Otto Tanaka · 6 min · Feb 25</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- DEBATE -->
  <section class="debate-section" id="debate">
    <div class="section-inner">
      <div class="section-header">
        <div>
          <div class="section-rule"></div>
          <h2 class="section-title">The <span>Debate</span></h2>
        </div>
        <a href="#" class="see-all">Past debates →</a>
      </div>
      <div class="debate-box">
        <div class="debate-header">
          <div class="debate-badge">⚖ This Week's Debate</div>
          <div class="debate-question">Should governments regulate social media platforms more strictly?</div>
        </div>
        <div class="debate-sides">
          <div class="debate-side">
            <div class="debate-side-label">
              <span class="debate-badge-yes">Yes — For</span>
            </div>
            <div class="debate-side-title">Regulation protects the public — and democracy itself</div>
            <p>Unregulated platforms have become vectors for coordinated disinformation, election interference, and psychological manipulation at industrial scale. Governments regulate tobacco, pharmaceuticals, and financial products because the public interest demands it. The same logic applies to platforms that now shape how hundreds of millions form their views of reality.</p>
            <p>The question is no longer whether, but how thoughtfully. Done well, regulation can set minimum safety standards without silencing legitimate speech.</p>
            <div class="debate-author-row">
              <div class="avatar-sm" style="background: var(--green);">PH</div>
              <div class="debate-author-info">
                <strong>Priya Helms</strong>
                <span>Technology Policy Researcher</span>
              </div>
            </div>
          </div>
          <div class="debate-side">
            <div class="debate-side-label">
              <span class="debate-badge-no">No — Against</span>
            </div>
            <div class="debate-side-title">Government control of speech is a cure worse than the disease</div>
            <p>History shows us what happens when governments acquire power over information flows: they use it. What begins as "stopping misinformation" reliably expands to suppressing inconvenient truths. The cure — giving politicians authority over which speech is acceptable online — is more dangerous than the illness.</p>
            <p>Better solutions lie in media literacy, algorithmic transparency requirements, and market competition. Not censorship power for governments.</p>
            <div class="debate-author-row">
              <div class="avatar-sm" style="background: var(--orange);">DK</div>
              <div class="debate-author-info">
                <strong>Damien Kroger</strong>
                <span>Digital Rights Advocate</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- COMMUNITY VOICES -->
  <section class="voices-section">
    <div class="section-inner">
      <div class="section-header">
        <div>
          <div class="section-rule"></div>
          <h2 class="section-title">Community <span>Voices</span></h2>
        </div>
        <a href="#" onclick="showPage('submit')" class="see-all">Add yours →</a>
      </div>
      <div class="voices-grid">
        <div class="voice-card">
          <div class="voice-top">
            <div class="voice-avatar" style="background: #E07A5F;">MK</div>
            <div class="voice-info">
              <div class="voice-name">Maya K.</div>
              <div class="voice-role">Teacher, Bristol</div>
            </div>
          </div>
          <p class="voice-quote">"I've started teaching my students to identify the emotion a headline is trying to make them feel before they read the article. It changes everything."</p>
          <div class="voice-title">→ News literacy in the classroom</div>
        </div>
        <div class="voice-card">
          <div class="voice-top">
            <div class="voice-avatar" style="background: #81B29A;">TN</div>
            <div class="voice-info">
              <div class="voice-name">Theo N.</div>
              <div class="voice-role">Student, Glasgow</div>
            </div>
          </div>
          <p class="voice-quote">"I don't read the news because every time I do, I feel worse and know nothing more. The Otter Outlook is the first place that left me feeling informed instead of exhausted."</p>
          <div class="voice-title">→ Why my generation checks out</div>
        </div>
        <div class="voice-card">
          <div class="voice-top">
            <div class="voice-avatar" style="background: #F4A261;">CA</div>
            <div class="voice-info">
              <div class="voice-name">Carla A.</div>
              <div class="voice-role">Journalist, Lagos</div>
            </div>
          </div>
          <p class="voice-quote">"Local journalism in Nigeria is doing extraordinary work that global outlets simply never cover. The gap between what's actually happening and what gets reported is enormous."</p>
          <div class="voice-title">→ The global news blind spots</div>
        </div>
        <div class="voice-card">
          <div class="voice-top">
            <div class="voice-avatar" style="background: #7B9E87;">RS</div>
            <div class="voice-info">
              <div class="voice-name">Ravi S.</div>
              <div class="voice-role">Researcher, Toronto</div>
            </div>
          </div>
          <p class="voice-quote">"The most dangerous misinformation isn't the obviously fake stuff. It's the accurate headline that omits the context that would completely change your interpretation."</p>
          <div class="voice-title">→ Context as the missing story</div>
        </div>
      </div>
    </div>
  </section>

  <!-- NEWSLETTER -->
  <section class="newsletter-section" id="about">
    <div class="newsletter-inner">
      <div class="newsletter-otter">🦦</div>
      <h2>Stay beneath the surface.</h2>
      <p>Get thoughtful perspectives on the news every week — no outrage, no panic, just understanding.</p>
      <div class="newsletter-form">
        <input type="email" placeholder="your@email.com">
        <button class="btn-subscribe">Subscribe</button>
      </div>
      <p class="newsletter-note">Weekly. No spam. Unsubscribe anytime. 🌿</p>
    </div>
  </section>

</div><!-- end #page-home -->

<!-- ── SUBMIT PAGE ────────────────────────────────────── -->
<div id="page-submit" class="page hidden">
  <section style="padding: 4rem 2rem; background: var(--cream); min-height: 80vh;">
    <div class="submit-inner section-inner" style="max-width:700px;">
      <div style="margin-bottom:2rem;">
        <div class="section-rule"></div>
        <h1 class="section-title">Submit an <span>Essay</span></h1>
      </div>
      <p class="submit-intro">The Otter Outlook publishes thoughtful, well-reasoned essays on current events, media, and society. We're not looking for hot takes — we're looking for depth, curiosity, and clarity. All submissions are reviewed by our editors before publishing.</p>

      <div class="form-group">
        <div class="form-row">
          <div>
            <label class="form-label">Your Name</label>
            <input type="text" class="form-input" placeholder="Full name or pen name">
          </div>
          <div>
            <label class="form-label">Email Address</label>
            <input type="email" class="form-input" placeholder="we'll respond here">
          </div>
        </div>
      </div>

      <div class="form-group">
        <label class="form-label">Article Title</label>
        <input type="text" class="form-input" placeholder="A clear, specific headline">
        <div class="form-hint">Tip: avoid vague titles. 'Why X matters' is weaker than 'How X is quietly changing Y.'</div>
      </div>

      <div class="form-group">
        <label class="form-label">Section</label>
        <select class="form-select">
          <option value="">Choose a section…</option>
          <option>Media & Journalism</option>
          <option>Technology & Society</option>
          <option>Politics & Policy</option>
          <option>Climate & Environment</option>
          <option>Economics & Work</option>
          <option>Under the Surface (Explainer)</option>
          <option>Community Voices (Short Opinion)</option>
          <option>Other</option>
        </select>
      </div>

      <div class="form-group">
        <label class="form-label">Your Essay</label>
        <textarea class="form-textarea" placeholder="Paste your essay here. We recommend 600–1,500 words for essays, and 200–400 words for Community Voices. Write as if you're explaining to a smart friend who doesn't follow this topic closely."></textarea>
        <div class="form-hint">Minimum 400 words. We reserve the right to lightly edit for clarity and length.</div>
      </div>

      <div class="form-group">
        <label class="form-label">Sources & Links <span style="color:var(--mid); font-weight:400; text-transform:none; letter-spacing:0;">(optional)</span></label>
        <textarea class="form-textarea" style="min-height:80px;" placeholder="List any sources, studies, or links you've referenced. One per line."></textarea>
      </div>

      <div style="display:flex; align-items:center; justify-content:space-between; flex-wrap:wrap; gap:1rem;">
        <button class="btn-submit-form">Send for Review 🦦</button>
        <p style="font-size:0.75rem; color:var(--mid); max-width:260px;">We aim to respond within 5–7 days. We read everything.</p>
      </div>
    </div>
  </section>
</div>

<!-- ── ARTICLE PAGE ─────────────────────────────────── -->
<div id="page-article" class="page hidden">
  <div class="article-inner">
    <div class="article-breadcrumb">
      <a href="#" onclick="showPage('home')">Home</a>
      <span>›</span>
      <a href="#">Articles</a>
      <span>›</span>
      <span>Misinformation</span>
    </div>

    <div class="article-category-badge">Media & Society</div>

    <h1 class="article-title">Why misinformation spreads faster than truth online</h1>

    <div class="article-byline">
      <div class="byline-author">
        <div class="byline-avatar">OT</div>
        <div class="byline-info">
          <div class="byline-name">Otto Tanaka</div>
          <div class="byline-date">March 9, 2026</div>
        </div>
      </div>
      <div class="byline-stats">
        <div class="byline-stat">⏱ 8 min read</div>
        <div class="byline-stat">👁 4.2k views</div>
        <div class="byline-stat" style="color:var(--green); border-color:var(--border);">💬 23 comments</div>
      </div>
    </div>

    <div class="article-body">
      <p>In 2018, a study from MIT's Media Lab published a finding so stark it reshaped how researchers talk about the internet: false stories on Twitter spread six times faster than true ones, reached deeper into social networks, and were seventy percent more likely to be retweeted. And the culprit wasn't bots. It was us.</p>

      <p>We like to imagine that misinformation is something that happens to other people — the less educated, the more credulous, the more partisan. But the MIT research, and a decade of follow-up studies, tells a more uncomfortable story: the tendency to share false information appears to be a remarkably consistent feature of human behaviour online, cutting across demographics and political affiliations.</p>

      <blockquote>"False news is more novel than true news, and humans are more likely to share novel information." — Soroush Vosoughi, MIT Media Lab, 2018</blockquote>

      <h2>The novelty problem</h2>

      <p>The core mechanism is surprisingly simple. False stories, particularly those spreading on social media, tend to be <strong>more emotionally surprising and novel</strong> than true ones. Real news — trade negotiations, regulatory decisions, gradual policy shifts — is usually slow, complex, and difficult to summarise. False news is often vivid, outrageous, and perfectly designed for a six-second emotional reaction.</p>

      <p>Our brains evolved to pay attention to the surprising and the threatening. In a prehistoric context, this was adaptive. A startling rustle in the undergrowth was worth passing on. In an information environment flooded with content competing for attention, these same instincts make us reliably unreliable sharers of accurate information.</p>

      <h2>What platforms get wrong about moderation</h2>

      <p>The standard response from platforms has been to focus on individual pieces of false content: label it, downrank it, remove it. This approach treats misinformation like a weed — something to be pulled out once identified. But the evidence suggests the problem is more like soil composition. The information environment itself is structured in ways that give false claims a systematic advantage.</p>

      <p>Recommendation algorithms optimise for engagement. Engagement is generated by emotional arousal. Emotional arousal is reliably produced by content that surprises, angers, or frightens. The result is an architecture that, even without any intent to spread misinformation, consistently rewards it.</p>

      <h2>Is there a way back?</h2>

      <p>The honest answer is: probably not a complete one. The novelty advantage of false information appears to be deeply tied to human psychology in ways that can't simply be designed away. But there are approaches that seem to help at the margins.</p>

      <p><strong>Accuracy nudges</strong> — prompting people to think about whether something is accurate before they share it — have shown modest but real effects in research settings. <strong>Lateral reading</strong>, the technique used by professional fact-checkers of immediately checking multiple sources rather than reading deeply from a single one, can be taught and appears to work for non-experts.</p>

      <p>The deeper challenge is structural. A media ecosystem funded by attention will continue to reward the content that captures it. Until the economic incentives change, the problem won't.</p>
    </div>

    <div class="article-tags">
      <span class="tag tag-light">Misinformation</span>
      <span class="tag tag-light">Social Media</span>
      <span class="tag tag-light">Media Literacy</span>
      <span class="tag tag-light">Psychology</span>
      <span class="tag tag-light">Algorithms</span>
    </div>

    <!-- COMMENTS -->
    <div class="comments-section">
      <div class="comments-title">Discussion (23)</div>

      <div class="comment-box">
        <p style="font-size:0.8rem; color:var(--charcoal-light); margin-bottom:0.7rem; font-weight:500;">Join the discussion — please keep it thoughtful. 🦦</p>
        <textarea placeholder="Share your perspective..."></textarea>
        <button class="comment-submit">Post Comment</button>
      </div>

      <div class="comment">
        <div class="comment-header">
          <div class="avatar-sm" style="background:#81B29A; width:32px; height:32px; font-size:0.7rem;">LM</div>
          <span class="comment-name">Leila M.</span>
          <span class="comment-date">Mar 9</span>
        </div>
        <p>The point about recommendation algorithms is the one that doesn't get enough attention. People blame individuals for sharing misinformation, but we've built systems that make it structurally likely. Individual blame without systemic change is just moralising.</p>
      </div>

      <div class="comment">
        <div class="comment-header">
          <div class="avatar-sm" style="background:#E07A5F; width:32px; height:32px; font-size:0.7rem;">DW</div>
          <span class="comment-name">Dan W.</span>
          <span class="comment-date">Mar 10</span>
        </div>
        <p>I found the accuracy nudge research genuinely encouraging. Small prompts toward reflection can shift behaviour. It suggests the problem isn't hopeless — it's just that we haven't taken low-cost interventions seriously enough.</p>
      </div>

      <div class="comment">
        <div class="comment-header">
          <div class="avatar-sm" style="background:#6A9C89; width:32px; height:32px; font-size:0.7rem;">OT</div>
          <span class="comment-name">Otto Tanaka</span>
          <span class="comment-date" style="color:var(--green);">Author · Mar 10</span>
        </div>
        <p>Dan — agreed on the nudges. What I found interesting in the follow-up research is that the effect persists even when people know they're being nudged. There's something genuinely promising in that. The challenge is scaling interventions that platforms have little financial incentive to implement.</p>
      </div>
    </div>
  </div>
</div>

<!-- ── FOOTER ─────────────────────────────────────────── -->
<footer>
  <div class="footer-inner">
    <div class="footer-top">
      <div class="footer-brand">
        <div class="footer-logo">
          <div class="footer-logo-icon">🦦</div>
          <span class="footer-logo-text">The Otter Outlook</span>
        </div>
        <p class="footer-desc">A calm café for ideas about the news. Independent, reader-supported, and committed to understanding over outrage. Diving beneath the surface since 2025.</p>
      </div>
      <div class="footer-col">
        <h4>Read</h4>
        <ul>
          <li><a href="#">Latest Articles</a></li>
          <li><a href="#">Essays</a></li>
          <li><a href="#">Debates</a></li>
          <li><a href="#">Under the Surface</a></li>
          <li><a href="#">Community Voices</a></li>
        </ul>
      </div>
      <div class="footer-col">
        <h4>Topics</h4>
        <ul>
          <li><a href="#">Media & Journalism</a></li>
          <li><a href="#">Technology</a></li>
          <li><a href="#">Politics</a></li>
          <li><a href="#">Climate</a></li>
          <li><a href="#">Economics</a></li>
        </ul>
      </div>
      <div class="footer-col">
        <h4>About</h4>
        <ul>
          <li><a href="#">Our Mission</a></li>
          <li><a href="#" onclick="showPage('submit')">Submit an Essay</a></li>
          <li><a href="#">Editorial Standards</a></li>
          <li><a href="#">Contact</a></li>
          <li><a href="#">Privacy Policy</a></li>
        </ul>
      </div>
    </div>
    <div class="footer-bottom">
      <p class="footer-copy">© 2026 The Otter Outlook. All rights reserved.</p>
      <p class="footer-love">Made with <span>♥</span> for curious minds</p>
    </div>
  </div>
</footer>

<script>
  // ── PAGE ROUTING
  function showPage(name) {
    document.querySelectorAll('.page').forEach(p => p.classList.add('hidden'));
    const target = document.getElementById('page-' + name);
    if (target) {
      target.classList.remove('hidden');
      window.scrollTo({ top: 0, behavior: 'smooth' });
    }
  }

  // ── MOBILE MENU
  function toggleMenu() {
    const menu = document.getElementById('mobileMenu');
    menu.classList.toggle('open');
  }

  // ── NEWSLETTER SUBSCRIBE
  document.querySelector('.btn-subscribe').addEventListener('click', function() {
    const input = this.previousElementSibling;
    if (input.value && input.value.includes('@')) {
      this.textContent = '✓ You\'re in!';
      this.style.background = 'var(--green-deep)';
      input.value = '';
      input.placeholder = 'See you in your inbox 🦦';
      input.disabled = true;
    } else {
      input.style.borderColor = 'rgba(244,162,97,0.8)';
      input.placeholder = 'Enter a valid email…';
      setTimeout(() => { input.style.borderColor = ''; }, 2000);
    }
  });

  // ── COMMENT SUBMIT
  document.querySelector('.comment-submit').addEventListener('click', function() {
    const ta = this.previousElementSibling;
    if (ta.value.trim().length > 10) {
      const toast = document.createElement('div');
      toast.textContent = '🦦 Comment submitted for moderation!';
      toast.style.cssText = `
        position:fixed; bottom:1.5rem; right:1.5rem; z-index:999;
        background:var(--green); color:white; padding:0.9rem 1.4rem;
        border-radius:10px; font-size:0.85rem; font-weight:600;
        box-shadow: 0 4px 20px rgba(106,156,137,0.4);
        animation: fadeUp 0.3s ease;
      `;
      document.body.appendChild(toast);
      ta.value = '';
      setTimeout(() => toast.remove(), 3000);
    }
  });

  // ── SUBMIT FORM
  document.querySelector('.btn-submit-form').addEventListener('click', function() {
    const name = document.querySelectorAll('.form-input')[0];
    const essay = document.querySelector('.form-textarea');
    if (name.value && essay.value.length > 50) {
      this.textContent = '✓ Submitted! We\'ll be in touch.';
      this.style.background = 'var(--orange)';
      this.disabled = true;
    } else {
      this.textContent = 'Please fill in name and essay ↑';
      setTimeout(() => { this.textContent = 'Send for Review 🦦'; }, 2500);
    }
  });

  // ── SCROLL ANIMATIONS
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.style.opacity = '1';
        entry.target.style.transform = 'translateY(0)';
      }
    });
  }, { threshold: 0.1 });

  document.querySelectorAll('.article-card, .surface-card, .voice-card, .essay-mini').forEach(el => {
    el.style.transition = 'opacity 0.5s ease, transform 0.5s ease';
    el.style.opacity = '0';
    el.style.transform = 'translateY(16px)';
    observer.observe(el);
  });
</script>

</body>
</html>
