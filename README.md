[elumeweb.html](https://github.com/user-attachments/files/29221699/elumeweb.html)
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Élume Hotels — Redefine Your Stay</title>
  <link
    href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=Inter:wght@300;400;500;600&display=swap"
    rel="stylesheet" />
  <script src="https://www.paypal.com/sdk/js?client-id=sb&currency=USD&intent=capture"></script>
  <style>
    *,
    *::before,
    *::after {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    :root {
      --navy: #0A1628;
      --navy2: #121F38;
      --gold: #C9A455;
      --gold2: #E8C97A;
      --ivory: #F8F4ED;
      --ivory2: #EDE8DF;
      --sage: #5C7E6B;
      --mist: #8A9BB0;
      --white: #FFFFFF;
      --shadow: rgba(10, 22, 40, 0.18);
    }

    html {
      scroll-behavior: smooth;
    }

    body {
      font-family: 'Inter', sans-serif;
      background: var(--navy);
      color: var(--ivory);
      overflow-x: hidden;
    }

    /* ─── SCROLLBAR ─── */
    ::-webkit-scrollbar {
      width: 6px;
    }

    ::-webkit-scrollbar-track {
      background: var(--navy);
    }

    ::-webkit-scrollbar-thumb {
      background: var(--gold);
      border-radius: 3px;
    }

    /* ─── LOADER ─── */
    #loader {
      position: fixed;
      inset: 0;
      z-index: 9999;
      background: var(--navy);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      transition: opacity 0.6s ease, visibility 0.6s ease;
    }

    #loader.hidden {
      opacity: 0;
      visibility: hidden;
    }

    .loader-word {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(2.5rem, 6vw, 4.5rem);
      font-weight: 300;
      color: var(--gold);
      letter-spacing: 0.35em;
      overflow: hidden;
    }

    .loader-bar {
      width: 160px;
      height: 2px;
      background: var(--navy2);
      margin-top: 20px;
      border-radius: 2px;
      overflow: hidden;
    }

    .loader-fill {
      height: 100%;
      width: 0;
      background: linear-gradient(90deg, var(--gold), var(--gold2));
      border-radius: 2px;
      animation: fillBar 1.8s ease forwards;
    }

    @keyframes fillBar {
      to {
        width: 100%;
      }
    }

    /* ─── NAV ─── */
    nav {
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      z-index: 100;
      padding: 22px 48px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      transition: background 0.4s ease, padding 0.3s ease, box-shadow 0.3s ease;
    }

    nav.scrolled {
      background: rgba(10, 22, 40, 0.95);
      backdrop-filter: blur(12px);
      padding: 14px 48px;
      box-shadow: 0 1px 30px var(--shadow);
    }

    .nav-logo {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.7rem;
      font-weight: 600;
      color: var(--gold);
      letter-spacing: 0.1em;
      text-decoration: none;
    }

    .nav-logo span {
      color: var(--ivory);
      font-weight: 300;
    }

    .nav-links {
      display: flex;
      gap: 36px;
      list-style: none;
    }

    .nav-links a {
      color: var(--mist);
      font-size: 0.82rem;
      font-weight: 500;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      text-decoration: none;
      position: relative;
      transition: color 0.3s;
    }

    .nav-links a::after {
      content: '';
      position: absolute;
      bottom: -3px;
      left: 0;
      width: 0;
      height: 1px;
      background: var(--gold);
      transition: width 0.3s ease;
    }

    .nav-links a:hover {
      color: var(--gold);
    }

    .nav-links a:hover::after {
      width: 100%;
    }

    .nav-cta {
      padding: 10px 24px;
      border: 1px solid var(--gold);
      color: var(--gold) !important;
      border-radius: 2px;
      transition: background 0.3s, color 0.3s !important;
    }

    .nav-cta::after {
      display: none !important;
    }

    .nav-cta:hover {
      background: var(--gold) !important;
      color: var(--navy) !important;
    }

    /* ─── HERO ─── */
    #hero {
      position: relative;
      height: 100vh;
      min-height: 680px;
      display: flex;
      align-items: center;
      justify-content: center;
      overflow: hidden;
    }

    .hero-bg {
      position: absolute;
      inset: 0;
      background:
        linear-gradient(to bottom, rgba(10, 22, 40, 0.55) 0%, rgba(10, 22, 40, 0.3) 50%, rgba(10, 22, 40, 0.85) 100%),
        url('https://images.unsplash.com/photo-1566073771259-6a8506099945?w=1600&q=80') center/cover no-repeat;
      transform: scale(1.08);
      transition: transform 0.1s linear;
      will-change: transform;
    }

    .hero-shimmer {
      position: absolute;
      inset: 0;
      pointer-events: none;
      background: radial-gradient(600px circle at var(--mx, 50%) var(--my, 50%),
          rgba(201, 164, 85, 0.07), transparent 60%);
      transition: background 0.15s ease;
    }

    .hero-content {
      position: relative;
      z-index: 2;
      text-align: center;
      padding: 0 24px;
      max-width: 820px;
    }

    .hero-eyebrow {
      font-size: 0.72rem;
      letter-spacing: 0.4em;
      text-transform: uppercase;
      color: var(--gold);
      margin-bottom: 20px;
      opacity: 0;
      transform: translateY(20px);
      animation: fadeUp 0.8s 1.9s ease forwards;
    }

    .hero-headline {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(3rem, 7vw, 5.8rem);
      font-weight: 300;
      line-height: 1.05;
      color: var(--ivory);
      margin-bottom: 22px;
      opacity: 0;
      transform: translateY(30px);
      animation: fadeUp 0.9s 2.1s ease forwards;
    }

    .hero-headline em {
      color: var(--gold);
      font-style: italic;
    }

    .hero-sub {
      font-size: 1rem;
      font-weight: 300;
      color: var(--mist);
      line-height: 1.7;
      margin-bottom: 40px;
      opacity: 0;
      transform: translateY(20px);
      animation: fadeUp 0.8s 2.3s ease forwards;
    }

    .hero-btns {
      display: flex;
      gap: 16px;
      justify-content: center;
      flex-wrap: wrap;
      opacity: 0;
      transform: translateY(20px);
      animation: fadeUp 0.8s 2.5s ease forwards;
    }

    .btn-primary {
      padding: 14px 36px;
      background: var(--gold);
      color: var(--navy);
      border: none;
      border-radius: 2px;
      font-family: 'Inter', sans-serif;
      font-size: 0.82rem;
      font-weight: 600;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      cursor: pointer;
      transition: background 0.3s, transform 0.2s, box-shadow 0.3s;
    }

    .btn-primary:hover {
      background: var(--gold2);
      transform: translateY(-2px);
      box-shadow: 0 8px 24px rgba(201, 164, 85, 0.35);
    }

    .btn-outline {
      padding: 14px 36px;
      background: transparent;
      border: 1px solid rgba(248, 244, 237, 0.4);
      color: var(--ivory);
      border-radius: 2px;
      font-size: 0.82rem;
      font-weight: 500;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      cursor: pointer;
      transition: border-color 0.3s, color 0.3s, transform 0.2s;
    }

    .btn-outline:hover {
      border-color: var(--gold);
      color: var(--gold);
      transform: translateY(-2px);
    }

    .hero-scroll {
      position: absolute;
      bottom: 36px;
      left: 50%;
      transform: translateX(-50%);
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 8px;
      opacity: 0;
      animation: fadeIn 1s 3s ease forwards;
    }

    .hero-scroll span {
      font-size: 0.68rem;
      letter-spacing: 0.3em;
      color: var(--mist);
      text-transform: uppercase;
    }

    .scroll-line {
      width: 1px;
      height: 40px;
      background: linear-gradient(to bottom, var(--gold), transparent);
      animation: scrollPulse 2s 3s ease-in-out infinite;
    }

    @keyframes scrollPulse {

      0%,
      100% {
        opacity: 0.4;
        transform: scaleY(1);
      }

      50% {
        opacity: 1;
        transform: scaleY(1.1);
      }
    }

    /* ─── SEARCH FORM ─── */
    #search {
      background: var(--navy2);
      padding: 56px 48px 64px;
      border-bottom: 1px solid rgba(201, 164, 85, 0.12);
    }

    .search-label {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.9rem;
      font-weight: 300;
      color: var(--ivory);
      margin-bottom: 32px;
      text-align: center;
    }

    .search-label span {
      color: var(--gold);
      font-style: italic;
    }

    .search-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
      gap: 16px;
      max-width: 960px;
      margin: 0 auto 24px;
    }

    .field-wrap {
      display: flex;
      flex-direction: column;
      gap: 7px;
    }

    .field-wrap label {
      font-size: 0.7rem;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--gold);
    }

    .field-wrap input,
    .field-wrap select {
      background: rgba(255, 255, 255, 0.05);
      border: 1px solid rgba(201, 164, 85, 0.25);
      border-radius: 2px;
      color: var(--ivory);
      padding: 12px 14px;
      font-family: 'Inter', sans-serif;
      font-size: 0.9rem;
      transition: border-color 0.3s, background 0.3s;
      outline: none;
      -webkit-appearance: none;
      appearance: none;
    }

    .field-wrap input:focus,
    .field-wrap select:focus {
      border-color: var(--gold);
      background: rgba(201, 164, 85, 0.08);
    }

    .field-wrap select option {
      background: var(--navy2);
      color: var(--ivory);
    }

    .search-btn-wrap {
      text-align: center;
    }

    .search-btn {
      padding: 14px 52px;
      background: var(--gold);
      color: var(--navy);
      border: none;
      border-radius: 2px;
      cursor: pointer;
      font-size: 0.82rem;
      font-weight: 600;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      font-family: 'Inter', sans-serif;
      transition: background 0.3s, transform 0.2s, box-shadow 0.3s;
    }

    .search-btn:hover {
      background: var(--gold2);
      transform: translateY(-2px);
      box-shadow: 0 8px 24px rgba(201, 164, 85, 0.3);
    }

    /* ─── STATS STRIP ─── */
    .stats-strip {
      background: var(--gold);
      padding: 28px 48px;
      display: flex;
      justify-content: center;
      gap: clamp(32px, 6vw, 100px);
      flex-wrap: wrap;
    }

    .stat {
      text-align: center;
    }

    .stat-num {
      font-family: 'Cormorant Garamond', serif;
      font-size: 2.4rem;
      font-weight: 600;
      color: var(--navy);
      line-height: 1;
    }

    .stat-label {
      font-size: 0.72rem;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      color: var(--navy);
      opacity: 0.7;
      margin-top: 4px;
    }

    /* ─── ROOMS SECTION ─── */
    #rooms {
      padding: 80px 48px 100px;
      max-width: 1200px;
      margin: 0 auto;
    }

    .section-header {
      text-align: center;
      margin-bottom: 56px;
    }

    .section-eyebrow {
      font-size: 0.7rem;
      letter-spacing: 0.4em;
      text-transform: uppercase;
      color: var(--gold);
      margin-bottom: 14px;
    }

    .section-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(2rem, 4.5vw, 3.2rem);
      font-weight: 300;
      color: var(--ivory);
      line-height: 1.2;
    }

    .section-title em {
      font-style: italic;
      color: var(--gold);
    }

    .section-desc {
      margin-top: 16px;
      max-width: 520px;
      margin-left: auto;
      margin-right: auto;
      font-size: 0.92rem;
      color: var(--mist);
      line-height: 1.75;
    }

    .rooms-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
      gap: 28px;
    }

    /* CARD */
    .room-card {
      background: var(--navy2);
      border: 1px solid rgba(201, 164, 85, 0.12);
      border-radius: 4px;
      overflow: hidden;
      cursor: pointer;
      opacity: 0;
      transform: translateY(40px);
      transition: transform 0.4s ease, box-shadow 0.4s ease, border-color 0.3s;
    }

    .room-card.visible {
      opacity: 1;
      transform: translateY(0);
    }

    .room-card:hover {
      transform: translateY(-6px);
      box-shadow: 0 20px 50px rgba(0, 0, 0, 0.4);
      border-color: rgba(201, 164, 85, 0.4);
    }

    .card-img-wrap {
      position: relative;
      overflow: hidden;
      height: 220px;
    }

    .card-img-wrap img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: transform 0.6s ease;
    }

    .room-card:hover .card-img-wrap img {
      transform: scale(1.06);
    }

    .card-badge {
      position: absolute;
      top: 14px;
      left: 14px;
      background: var(--gold);
      color: var(--navy);
      font-size: 0.65rem;
      font-weight: 600;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      padding: 4px 10px;
      border-radius: 2px;
    }

    .card-body {
      padding: 24px;
    }

    .card-type {
      font-size: 0.68rem;
      letter-spacing: 0.25em;
      text-transform: uppercase;
      color: var(--gold);
      margin-bottom: 8px;
    }

    .card-name {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.5rem;
      font-weight: 400;
      color: var(--ivory);
      margin-bottom: 12px;
    }

    .card-desc {
      font-size: 0.84rem;
      color: var(--mist);
      line-height: 1.65;
      margin-bottom: 18px;
    }

    .card-amenities {
      display: flex;
      gap: 10px;
      flex-wrap: wrap;
      margin-bottom: 20px;
    }

    .amenity-tag {
      font-size: 0.7rem;
      padding: 4px 10px;
      border: 1px solid rgba(201, 164, 85, 0.25);
      color: var(--mist);
      border-radius: 20px;
      letter-spacing: 0.05em;
    }

    .card-footer {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding-top: 18px;
      border-top: 1px solid rgba(201, 164, 85, 0.12);
    }

    .card-price .amount {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.7rem;
      font-weight: 600;
      color: var(--gold);
    }

    .card-price .per {
      font-size: 0.72rem;
      color: var(--mist);
      letter-spacing: 0.08em;
    }

    .card-book-btn {
      padding: 10px 22px;
      background: transparent;
      border: 1px solid var(--gold);
      color: var(--gold);
      border-radius: 2px;
      font-size: 0.78rem;
      font-weight: 500;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      cursor: pointer;
      font-family: 'Inter', sans-serif;
      transition: background 0.3s, color 0.3s, transform 0.2s;
    }

    .card-book-btn:hover {
      background: var(--gold);
      color: var(--navy);
      transform: scale(1.04);
    }

    /* ─── EXPERIENCE SECTION ─── */
    #experience {
      background: var(--navy2);
      padding: 80px 48px;
      border-top: 1px solid rgba(201, 164, 85, 0.1);
      border-bottom: 1px solid rgba(201, 164, 85, 0.1);
    }

    .exp-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 64px;
      align-items: center;
      max-width: 1100px;
      margin: 0 auto;
    }

    .exp-visual {
      position: relative;
    }

    .exp-img {
      width: 100%;
      border-radius: 4px;
      aspect-ratio: 4/3;
      object-fit: cover;
    }

    .exp-accent {
      position: absolute;
      bottom: -20px;
      right: -20px;
      width: 150px;
      height: 150px;
      border: 2px solid var(--gold);
      border-radius: 4px;
      z-index: -1;
    }

    .exp-badge {
      position: absolute;
      top: 20px;
      left: -24px;
      background: var(--gold);
      color: var(--navy);
      width: 90px;
      height: 90px;
      border-radius: 50%;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      font-family: 'Cormorant Garamond', serif;
    }

    .exp-badge .num {
      font-size: 1.8rem;
      font-weight: 600;
      line-height: 1;
    }

    .exp-badge .txt {
      font-size: 0.55rem;
      letter-spacing: 0.1em;
      text-transform: uppercase;
    }

    .exp-text .section-header {
      text-align: left;
      margin-bottom: 28px;
    }

    .exp-text .section-header .section-desc {
      margin-left: 0;
      margin-right: 0;
    }

    .exp-features {
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 16px;
      margin-bottom: 32px;
    }

    .exp-features li {
      display: flex;
      gap: 14px;
      align-items: flex-start;
      font-size: 0.9rem;
      color: var(--mist);
    }

    .exp-features li::before {
      content: '✦';
      color: var(--gold);
      font-size: 0.65rem;
      margin-top: 4px;
      flex-shrink: 0;
    }

    /* ─── TESTIMONIALS ─── */
    #reviews {
      padding: 80px 48px;
      max-width: 1100px;
      margin: 0 auto;
    }

    .reviews-track {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
      gap: 24px;
      margin-top: 48px;
    }

    .review-card {
      background: var(--navy2);
      border: 1px solid rgba(201, 164, 85, 0.1);
      border-radius: 4px;
      padding: 28px;
      opacity: 0;
      transform: translateY(30px);
      transition: opacity 0.5s ease, transform 0.5s ease;
    }

    .review-card.visible {
      opacity: 1;
      transform: translateY(0);
    }

    .stars {
      color: var(--gold);
      font-size: 0.9rem;
      margin-bottom: 14px;
    }

    .review-text {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.15rem;
      font-weight: 300;
      font-style: italic;
      color: var(--ivory);
      line-height: 1.7;
      margin-bottom: 18px;
    }

    .review-author {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .review-avatar {
      width: 40px;
      height: 40px;
      border-radius: 50%;
      background: var(--gold);
      display: flex;
      align-items: center;
      justify-content: center;
      font-weight: 600;
      color: var(--navy);
      font-size: 0.9rem;
      flex-shrink: 0;
    }

    .review-name {
      font-size: 0.85rem;
      color: var(--ivory);
      font-weight: 500;
    }

    .review-loc {
      font-size: 0.72rem;
      color: var(--mist);
      margin-top: 2px;
    }

    /* ─── MODAL OVERLAY ─── */
    .modal-overlay {
      position: fixed;
      inset: 0;
      z-index: 500;
      background: rgba(10, 22, 40, 0.88);
      backdrop-filter: blur(6px);
      display: none;
      align-items: center;
      justify-content: center;
      padding: 24px;
    }

    .modal-overlay.open {
      display: flex;
      animation: fadeIn 0.25s ease;
    }

    .modal {
      background: var(--navy2);
      border: 1px solid rgba(201, 164, 85, 0.25);
      border-radius: 6px;
      width: 100%;
      max-width: 680px;
      max-height: 92vh;
      overflow-y: auto;
      animation: slideUp 0.35s ease;
    }

    @keyframes slideUp {
      from {
        opacity: 0;
        transform: translateY(40px);
      }

      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    .modal-header {
      padding: 28px 32px 0;
      display: flex;
      align-items: flex-start;
      justify-content: space-between;
      border-bottom: 1px solid rgba(201, 164, 85, 0.1);
      padding-bottom: 20px;
    }

    .modal-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.8rem;
      font-weight: 300;
      color: var(--ivory);
    }

    .modal-subtitle {
      font-size: 0.78rem;
      letter-spacing: 0.15em;
      color: var(--gold);
      text-transform: uppercase;
      margin-bottom: 6px;
    }

    .modal-close {
      background: none;
      border: none;
      color: var(--mist);
      font-size: 1.5rem;
      cursor: pointer;
      line-height: 1;
      padding: 4px 8px;
      transition: color 0.2s;
    }

    .modal-close:hover {
      color: var(--ivory);
    }

    .modal-body {
      padding: 28px 32px;
    }

    .modal-room-img {
      width: 100%;
      height: 200px;
      object-fit: cover;
      border-radius: 3px;
      margin-bottom: 24px;
    }

    .booking-form {
      display: flex;
      flex-direction: column;
      gap: 20px;
    }

    .form-row {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 16px;
    }

    .form-group {
      display: flex;
      flex-direction: column;
      gap: 7px;
    }

    .form-group label {
      font-size: 0.7rem;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--gold);
    }

    .form-group input,
    .form-group select {
      background: rgba(255, 255, 255, 0.05);
      border: 1px solid rgba(201, 164, 85, 0.25);
      border-radius: 2px;
      color: var(--ivory);
      padding: 11px 14px;
      font-family: 'Inter', sans-serif;
      font-size: 0.9rem;
      outline: none;
      transition: border-color 0.3s, background 0.3s;
      -webkit-appearance: none;
      appearance: none;
    }

    .form-group input:focus,
    .form-group select:focus {
      border-color: var(--gold);
      background: rgba(201, 164, 85, 0.07);
    }

    .form-group select option {
      background: var(--navy2);
    }

    .price-summary {
      background: rgba(201, 164, 85, 0.07);
      border: 1px solid rgba(201, 164, 85, 0.18);
      border-radius: 3px;
      padding: 18px 20px;
    }

    .price-row {
      display: flex;
      justify-content: space-between;
      font-size: 0.88rem;
      color: var(--mist);
      margin-bottom: 8px;
    }

    .price-row.total {
      color: var(--ivory);
      font-weight: 600;
      border-top: 1px solid rgba(201, 164, 85, 0.2);
      padding-top: 10px;
      margin-bottom: 0;
      font-size: 1rem;
    }

    .price-row.total .val {
      color: var(--gold);
      font-size: 1.15rem;
    }

    #paypal-button-container {
      margin-top: 20px;
    }

    .paypal-note {
      font-size: 0.75rem;
      color: var(--mist);
      text-align: center;
      margin-top: 10px;
    }

    /* STEP INDICATOR */
    .steps {
      display: flex;
      gap: 0;
      margin-bottom: 28px;
    }

    .step {
      flex: 1;
      text-align: center;
      padding: 12px 0;
      font-size: 0.72rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: var(--mist);
      border-bottom: 2px solid rgba(201, 164, 85, 0.15);
      cursor: default;
      transition: color 0.3s, border-color 0.3s;
    }

    .step.active {
      color: var(--gold);
      border-bottom-color: var(--gold);
    }

    /* CONFIRMATION */
    #confirmation-view {
      display: none;
      text-align: center;
      padding: 40px 32px;
    }

    #confirmation-view .check-circle {
      width: 72px;
      height: 72px;
      border-radius: 50%;
      background: var(--sage);
      margin: 0 auto 20px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 2rem;
      animation: popIn 0.5s ease;
    }

    @keyframes popIn {
      0% {
        transform: scale(0);
        opacity: 0;
      }

      70% {
        transform: scale(1.15);
      }

      100% {
        transform: scale(1);
        opacity: 1;
      }
    }

    #confirmation-view h2 {
      font-family: 'Cormorant Garamond', serif;
      font-size: 2rem;
      font-weight: 300;
      color: var(--ivory);
      margin-bottom: 10px;
    }

    #confirmation-view p {
      color: var(--mist);
      font-size: 0.9rem;
      line-height: 1.7;
    }

    #confirmation-view .conf-id {
      margin: 18px auto;
      background: rgba(201, 164, 85, 0.08);
      border: 1px solid rgba(201, 164, 85, 0.25);
      border-radius: 3px;
      padding: 14px 28px;
      display: inline-block;
      font-family: monospace;
      font-size: 1.1rem;
      color: var(--gold);
      letter-spacing: 0.1em;
    }

    /* ─── FOOTER ─── */
    footer {
      background: #060E1A;
      border-top: 1px solid rgba(201, 164, 85, 0.1);
      padding: 60px 48px 32px;
    }

    .footer-grid {
      display: grid;
      grid-template-columns: 2fr 1fr 1fr 1fr;
      gap: 48px;
      max-width: 1100px;
      margin: 0 auto 48px;
    }

    .footer-brand .logo {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.6rem;
      font-weight: 600;
      color: var(--gold);
      letter-spacing: 0.1em;
      display: block;
      margin-bottom: 14px;
    }

    .footer-brand p {
      font-size: 0.84rem;
      color: var(--mist);
      line-height: 1.7;
      max-width: 240px;
    }

    .footer-col h4 {
      font-size: 0.7rem;
      letter-spacing: 0.25em;
      text-transform: uppercase;
      color: var(--gold);
      margin-bottom: 18px;
    }

    .footer-col ul {
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 10px;
    }

    .footer-col ul li a {
      font-size: 0.84rem;
      color: var(--mist);
      text-decoration: none;
      transition: color 0.2s;
    }

    .footer-col ul li a:hover {
      color: var(--ivory);
    }

    .footer-bottom {
      max-width: 1100px;
      margin: 0 auto;
      padding-top: 24px;
      border-top: 1px solid rgba(255, 255, 255, 0.05);
      display: flex;
      justify-content: space-between;
      font-size: 0.76rem;
      color: var(--mist);
    }

    .footer-bottom a {
      color: var(--gold);
      text-decoration: none;
    }

    /* ─── ANIMATIONS ─── */
    @keyframes fadeUp {
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    @keyframes fadeIn {
      from {
        opacity: 0;
      }

      to {
        opacity: 1;
      }
    }

    /* ─── TOAST ─── */
    .toast {
      position: fixed;
      bottom: 28px;
      right: 28px;
      background: var(--navy2);
      border: 1px solid var(--gold);
      border-radius: 4px;
      padding: 14px 20px;
      font-size: 0.84rem;
      color: var(--ivory);
      z-index: 999;
      max-width: 320px;
      transform: translateX(120%);
      transition: transform 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
      box-shadow: 0 8px 30px rgba(0, 0, 0, 0.3);
    }

    .toast.show {
      transform: translateX(0);
    }

    /* ─── RESPONSIVE ─── */
    @media (max-width: 768px) {
      nav {
        padding: 18px 24px;
      }

      nav.scrolled {
        padding: 12px 24px;
      }

      .nav-links {
        display: none;
      }

      #search {
        padding: 40px 24px 48px;
      }

      #rooms {
        padding: 60px 24px 80px;
      }

      .exp-grid {
        grid-template-columns: 1fr;
        gap: 40px;
      }

      .exp-accent {
        display: none;
      }

      .exp-badge {
        left: 10px;
      }

      #experience {
        padding: 60px 24px;
      }

      #reviews {
        padding: 60px 24px;
      }

      footer {
        padding: 48px 24px 28px;
      }

      .footer-grid {
        grid-template-columns: 1fr 1fr;
        gap: 32px;
      }

      .footer-bottom {
        flex-direction: column;
        gap: 8px;
      }

      .form-row {
        grid-template-columns: 1fr;
      }

      .modal-body {
        padding: 20px 24px;
      }

      .modal-header {
        padding: 20px 24px 16px;
      }

      .steps {
        display: none;
      }
    }
  </style>
</head>

<body>

  <!-- LOADER -->
  <div id="loader">
    <div class="loader-word">ÉLUME</div>
    <div class="loader-bar">
      <div class="loader-fill"></div>
    </div>
  </div>

  <!-- NAV -->
  <nav id="navbar">
    <a href="#" class="nav-logo">Élume<span>Hotels</span></a>
    <ul class="nav-links">
      <li><a href="#rooms">Rooms</a></li>
      <li><a href="#experience">Experience</a></li>
      <li><a href="#reviews">Reviews</a></li>
      <li><a href="#rooms" class="nav-cta">Book Now</a></li>
    </ul>
  </nav>

  <!-- HERO -->
  <section id="hero">
    <div class="hero-bg" id="heroBg"></div>
    <div class="hero-shimmer" id="heroShimmer"></div>
    <div class="hero-content">
      <p class="hero-eyebrow">A New Standard of Luxury</p>
      <h1 class="hero-headline">Where <em>Comfort</em><br>Becomes Art</h1>
      <p class="hero-sub">Curated stays, timeless interiors, and service that remembers<br>your name before you arrive.
      </p>
      <div class="hero-btns">
        <button class="btn-primary" onclick="scrollTo('#rooms')">Explore Rooms</button>
        <button class="btn-outline" onclick="scrollTo('#experience')">Our Story</button>
      </div>
    </div>
    <div class="hero-scroll">
      <span>Discover</span>
      <div class="scroll-line"></div>
    </div>
  </section>

  <!-- SEARCH -->
  <section id="search">
    <h2 class="search-label">Find Your <span>Perfect Stay</span></h2>
    <div class="search-grid">
      <div class="field-wrap">
        <label>Check-In</label>
        <input type="date" id="checkIn" />
      </div>
      <div class="field-wrap">
        <label>Check-Out</label>
        <input type="date" id="checkOut" />
      </div>
      <div class="field-wrap">
        <label>Guests</label>
        <select id="guests">
          <option>1 Guest</option>
          <option>2 Guests</option>
          <option>3 Guests</option>
          <option>4 Guests</option>
        </select>
      </div>
      <div class="field-wrap">
        <label>Room Type</label>
        <select id="roomTypeFilter">
          <option value="all">All Rooms</option>
          <option value="deluxe">Deluxe</option>
          <option value="suite">Suite</option>
          <option value="penthouse">Penthouse</option>
        </select>
      </div>
    </div>
    <div class="search-btn-wrap">
      <button class="search-btn" onclick="filterRooms()">Search Availability</button>
    </div>
  </section>

  <!-- STATS -->
  <div class="stats-strip">
    <div class="stat">
      <div class="stat-num" data-count="42">0</div>
      <div class="stat-label">Luxury Rooms</div>
    </div>
    <div class="stat">
      <div class="stat-num" data-count="98">0</div>
      <div class="stat-label">Guest Satisfaction %</div>
    </div>
    <div class="stat">
      <div class="stat-num" data-count="15">0</div>
      <div class="stat-label">Years of Excellence</div>
    </div>
    <div class="stat">
      <div class="stat-num" data-count="8">0</div>
      <div class="stat-label">Award Wins</div>
    </div>
  </div>

  <!-- ROOMS -->
  <section id="rooms">
    <div class="section-header">
      <p class="section-eyebrow">Our Collection</p>
      <h2 class="section-title">Rooms &amp; <em>Suites</em></h2>
      <p class="section-desc">Every space is a considered composition of material, light, and craft — designed to feel
        like a home you never want to leave.</p>
    </div>
    <div class="rooms-grid" id="roomsGrid">
      <!-- Cards injected by JS -->
    </div>
  </section>

  <!-- EXPERIENCE -->
  <section id="experience">
    <div class="exp-grid">
      <div class="exp-visual">
        <img src="https://images.unsplash.com/photo-1584132967334-10e028bd69f7?w=900&q=80" alt="Hotel experience"
          class="exp-img" />
        <div class="exp-accent"></div>
        <div class="exp-badge">
          <div class="num">★5</div>
          <div class="txt">Star</div>
        </div>
      </div>
      <div class="exp-text">
        <div class="section-header">
          <p class="section-eyebrow">Beyond a Stay</p>
          <h2 class="section-title">An <em>Experience</em><br>Crafted for You</h2>
          <p class="section-desc">From the moment you arrive, every detail has been considered. Élume is not simply a
            hotel — it is a philosophy of hospitality.</p>
        </div>
        <ul class="exp-features">
          <li>Personal concierge available around the clock, seven days a week</li>
          <li>Chef-curated dining from seasonal, locally-sourced ingredients</li>
          <li>Rooftop infinity pool with panoramic skyline views</li>
          <li>Signature spa treatments designed by world-class therapists</li>
          <li>Complimentary airport transfers in our fleet of luxury vehicles</li>
        </ul>
        <button class="btn-primary" onclick="scrollTo('#rooms')">View Our Rooms</button>
      </div>
    </div>
  </section>

  <!-- REVIEWS -->
  <section id="reviews">
    <div class="section-header">
      <p class="section-eyebrow">Guest Voices</p>
      <h2 class="section-title">What They <em>Remember</em></h2>
    </div>
    <div class="reviews-track">
      <div class="review-card">
        <div class="stars">★★★★★</div>
        <p class="review-text">"The penthouse suite was unlike anything I've experienced. Every detail spoke of
          intention and artistry."</p>
        <div class="review-author">
          <div class="review-avatar">S</div>
          <div>
            <div class="review-name">Sophia Laurent</div>
            <div class="review-loc">Paris, France</div>
          </div>
        </div>
      </div>
      <div class="review-card">
        <div class="stars">★★★★★</div>
        <p class="review-text">"We celebrated our anniversary here. The staff remembered everything — our wine
          preferences, our allergies, even our names."</p>
        <div class="review-author">
          <div class="review-avatar">J</div>
          <div>
            <div class="review-name">James & Elena Voss</div>
            <div class="review-loc">London, UK</div>
          </div>
        </div>
      </div>
      <div class="review-card">
        <div class="stars">★★★★★</div>
        <p class="review-text">"The rooftop pool at sunset is something I will spend the rest of my life trying to
          replicate elsewhere — and failing."</p>
        <div class="review-author">
          <div class="review-avatar">A</div>
          <div>
            <div class="review-name">Aiko Nakamura</div>
            <div class="review-loc">Tokyo, Japan</div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <div class="footer-grid">
      <div class="footer-brand">
        <span class="logo">ÉlumeHotels</span>
        <p>A sanctuary of quiet luxury, tucked into the heart of the city. Every stay is a story worth telling.</p>
      </div>
      <div class="footer-col">
        <h4>Explore</h4>
        <ul>
          <li><a href="#rooms">Rooms &amp; Suites</a></li>
          <li><a href="#experience">Dining</a></li>
          <li><a href="#">Spa &amp; Wellness</a></li>
          <li><a href="#">Events</a></li>
        </ul>
      </div>
      <div class="footer-col">
        <h4>Stay</h4>
        <ul>
          <li><a href="#">Book Direct</a></li>
          <li><a href="#">Special Offers</a></li>
          <li><a href="#">Loyalty Program</a></li>
          <li><a href="#">Gift Cards</a></li>
        </ul>
      </div>
      <div class="footer-col">
        <h4>Contact</h4>
        <ul>
          <li><a href="#">+1 (800) 358-6332</a></li>
          <li><a href="#">stay@elumehotels.com</a></li>
          <li><a href="#">12 Grand Promenade, NYC</a></li>
          <li><a href="#">Directions</a></li>
        </ul>
      </div>
    </div>
    <div class="footer-bottom">
      <span>© 2026 Élume Hotels. All rights reserved.</span>
      <span>Powered by <a href="#">PayPal Payments</a> · <a href="#">Privacy</a> · <a href="#">Terms</a></span>
    </div>
  </footer>

  <!-- BOOKING MODAL -->
  <div class="modal-overlay" id="bookingModal">
    <div class="modal" id="modalBox">
      <div id="booking-view">
        <div class="modal-header">
          <div>
            <p class="modal-subtitle" id="modalRoomType">Suite</p>
            <h2 class="modal-title" id="modalRoomName">Oceanic Suite</h2>
          </div>
          <button class="modal-close" onclick="closeModal()">✕</button>
        </div>
        <div class="modal-body">
          <div class="steps">
            <div class="step active">Details</div>
            <div class="step">Payment</div>
            <div class="step">Confirm</div>
          </div>
          <img id="modalRoomImg" src="" alt="Room" class="modal-room-img" />
          <div class="booking-form">
            <div class="form-row">
              <div class="form-group">
                <label>First Name</label>
                <input type="text" id="guestFirstName" placeholder="Enter first name" />
              </div>
              <div class="form-group">
                <label>Last Name</label>
                <input type="text" id="guestLastName" placeholder="Enter last name" />
              </div>
            </div>
            <div class="form-group">
              <label>Email Address</label>
              <input type="email" id="guestEmail" placeholder="your@email.com" />
            </div>
            <div class="form-row">
              <div class="form-group">
                <label>Check-In Date</label>
                <input type="date" id="modalCheckIn" />
              </div>
              <div class="form-group">
                <label>Check-Out Date</label>
                <input type="date" id="modalCheckOut" />
              </div>
            </div>
            <div class="form-row">
              <div class="form-group">
                <label>Guests</label>
                <select id="modalGuests">
                  <option>1 Guest</option>
                  <option>2 Guests</option>
                  <option>3 Guests</option>
                  <option>4 Guests</option>
                </select>
              </div>
              <div class="form-group">
                <label>Special Requests</label>
                <input type="text" id="specialReq" placeholder="Optional" />
              </div>
            </div>

            <!-- Price summary -->
            <div class="price-summary" id="priceSummary">
              <div class="price-row"><span>Room Rate</span><span id="summNightly">$0 / night</span></div>
              <div class="price-row"><span>Duration</span><span id="summNights">0 nights</span></div>
              <div class="price-row"><span>Taxes &amp; Fees (12%)</span><span id="summTax">$0</span></div>
              <div class="price-row total"><span>Total</span><span class="val" id="summTotal">$0</span></div>
            </div>

            <!-- PayPal -->
            <div id="paypal-button-container"></div>
            <p class="paypal-note">🔒 Secured by PayPal · Your data is encrypted and never stored on our servers.</p>
          </div>
        </div>
      </div>

      <!-- Confirmation view -->
      <div id="confirmation-view">
        <div class="check-circle">✓</div>
        <h2>Booking Confirmed!</h2>
        <p>Thank you for choosing Élume Hotels. A confirmation has been sent to your email.</p>
        <div class="conf-id" id="confIdDisplay">ÉLUME-000000</div>
        <p id="confDetails" style="font-size:0.84rem;color:var(--mist);margin-top:8px;"></p>
        <br />
        <button class="btn-primary" onclick="closeModal()" style="margin-top:12px;">Done</button>
      </div>
    </div>
  </div>

  <!-- TOAST -->
  <div class="toast" id="toast"></div>

  <script>
    /* ─────────────────────────────────────────
       DATA
    ───────────────────────────────────────── */
    const rooms = [
      {
        id: 1, type: 'deluxe', category: 'Deluxe Room',
        name: 'Garden Deluxe', badge: 'Most Popular',
        price: 220, maxGuests: 2,
        desc: 'Overlooking our private courtyard gardens, this sun-drenched room pairs warm walnut tones with cream linen for an understated calm.',
        amenities: ['King Bed', 'Garden View', 'Free Wi-Fi', 'Mini Bar'],
        img: 'https://images.unsplash.com/photo-1631049307264-da0ec9d70304?w=700&q=80'
      },
      {
        id: 2, type: 'suite', category: 'Suite',
        name: 'Oceanic Suite', badge: 'Sea View',
        price: 380, maxGuests: 3,
        desc: 'A suite defined by light — floor-to-ceiling ocean-facing windows, a freestanding soaking tub, and bespoke hand-stitched furnishings throughout.',
        amenities: ['King Bed', 'Ocean View', 'Soaking Tub', 'Butler Service'],
        img: 'https://images.unsplash.com/photo-1582719478250-c89cae4dc85b?w=700&q=80'
      },
      {
        id: 3, type: 'suite', category: 'Suite',
        name: 'Skyline Suite', badge: 'City Views',
        price: 450, maxGuests: 4,
        desc: 'The city unfolds below you through panoramic glass. A living room, dining space, and master suite create a private urban sanctuary.',
        amenities: ['2 Bedrooms', 'Panoramic View', 'Full Kitchen', 'Private Bar'],
        img: 'https://images.unsplash.com/photo-1560347876-aeef00ee58a1?w=700&q=80'
      },
      {
        id: 4, type: 'deluxe', category: 'Deluxe Room',
        name: 'Heritage Room', badge: null,
        price: 195, maxGuests: 2,
        desc: 'Restored original architecture meets modern amenity — exposed oak beams above a cocooning bed dressed in 600-thread Egyptian cotton.',
        amenities: ['Queen Bed', 'Heritage Design', 'Rain Shower', 'Lounge Chair'],
        img: 'https://images.unsplash.com/photo-1618773928121-c32242e63f39?w=700&q=80'
      },
      {
        id: 5, type: 'penthouse', category: 'Penthouse',
        name: 'The Penthouse', badge: 'Pinnacle',
        price: 1200, maxGuests: 6,
        desc: 'The entire top floor. A private rooftop terrace, home theatre, chef\'s kitchen, and three bedrooms — reserved for those who accept nothing less.',
        amenities: ['3 Bedrooms', 'Private Terrace', 'Home Cinema', 'Personal Chef'],
        img: 'https://images.unsplash.com/photo-1595526114035-0d45ed16cfbf?w=700&q=80'
      },
      {
        id: 6, type: 'deluxe', category: 'Deluxe Room',
        name: 'Spa Retreat', badge: 'Wellness',
        price: 260, maxGuests: 2,
        desc: 'An in-room infrared sauna, aromatherapy diffuser, and plunge bath make this the city\'s most restorative night\'s sleep.',
        amenities: ['King Bed', 'In-Room Sauna', 'Plunge Bath', 'Wellness Kit'],
        img: 'https://images.unsplash.com/photo-1578683010236-d716f9a3f461?w=700&q=80'
      },
    ];

    let currentRoom = null;
    let paypalRendered = false;

    /* ─────────────────────────────────────────
       LOADER
    ───────────────────────────────────────── */
    window.addEventListener('load', () => {
      setTimeout(() => {
        document.getElementById('loader').classList.add('hidden');
        initAnimations();
      }, 2200);
    });

    /* ─────────────────────────────────────────
       RENDER ROOMS
    ───────────────────────────────────────── */
    function renderRooms(list) {
      const grid = document.getElementById('roomsGrid');
      grid.innerHTML = '';
      if (!list.length) {
        grid.innerHTML = `<p style="color:var(--mist);grid-column:1/-1;text-align:center;padding:40px 0;">No rooms match your search. Please adjust your filters.</p>`;
        return;
      }
      list.forEach((r, i) => {
        const card = document.createElement('div');
        card.className = 'room-card';
        card.style.transitionDelay = `${i * 0.08}s`;
        card.innerHTML = `
      <div class="card-img-wrap">
        <img src="${r.img}" alt="${r.name}" loading="lazy" />
        ${r.badge ? `<span class="card-badge">${r.badge}</span>` : ''}
      </div>
      <div class="card-body">
        <p class="card-type">${r.category}</p>
        <h3 class="card-name">${r.name}</h3>
        <p class="card-desc">${r.desc}</p>
        <div class="card-amenities">${r.amenities.map(a => `<span class="amenity-tag">${a}</span>`).join('')}</div>
        <div class="card-footer">
          <div class="card-price">
            <span class="amount">$${r.price}</span>
            <span class="per"> / night</span>
          </div>
          <button class="card-book-btn" onclick="openModal(${r.id})">Book Now</button>
        </div>
      </div>`;
        grid.appendChild(card);
      });
      observeCards();
    }

    renderRooms(rooms);

    /* ─────────────────────────────────────────
       FILTER
    ───────────────────────────────────────── */
    function filterRooms() {
      const type = document.getElementById('roomTypeFilter').value;
      const filtered = type === 'all' ? rooms : rooms.filter(r => r.type === type);
      renderRooms(filtered);
      document.getElementById('rooms').scrollIntoView({ behavior: 'smooth', block: 'start' });
      showToast(`Showing ${filtered.length} room${filtered.length !== 1 ? 's' : ''}`);
    }

    /* ─────────────────────────────────────────
       SCROLL ANIMATIONS
    ───────────────────────────────────────── */
    function observeCards() {
      const io = new IntersectionObserver((entries) => {
        entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
      }, { threshold: 0.12 });
      document.querySelectorAll('.room-card, .review-card').forEach(el => io.observe(el));
    }

    function initAnimations() {
      observeCards();

      // Stat counters
      const statObserver = new IntersectionObserver((entries) => {
        entries.forEach(e => {
          if (e.isIntersecting) {
            animateCount(e.target);
            statObserver.unobserve(e.target);
          }
        });
      }, { threshold: 0.5 });
      document.querySelectorAll('[data-count]').forEach(el => statObserver.observe(el));
    }

    function animateCount(el) {
      const target = +el.dataset.count;
      const suffix = el.textContent.includes('%') ? '%' : '';
      let start = 0;
      const dur = 1800;
      const step = timestamp => {
        if (!start) start = timestamp;
        const progress = Math.min((timestamp - start) / dur, 1);
        const ease = 1 - Math.pow(1 - progress, 3);
        el.textContent = Math.floor(ease * target) + suffix;
        if (progress < 1) requestAnimationFrame(step);
      };
      requestAnimationFrame(step);
    }

    /* ─────────────────────────────────────────
       PARALLAX + SHIMMER
    ───────────────────────────────────────── */
    const heroBg = document.getElementById('heroBg');
    const heroShimmer = document.getElementById('heroShimmer');

    window.addEventListener('scroll', () => {
      const y = window.scrollY;
      heroBg.style.transform = `scale(1.08) translateY(${y * 0.25}px)`;

      // Navbar
      const nav = document.getElementById('navbar');
      nav.classList.toggle('scrolled', y > 60);
    });

    document.getElementById('hero').addEventListener('mousemove', e => {
      const rect = e.currentTarget.getBoundingClientRect();
      const x = ((e.clientX - rect.left) / rect.width * 100).toFixed(1);
      const y = ((e.clientY - rect.top) / rect.height * 100).toFixed(1);
      heroShimmer.style.setProperty('--mx', x + '%');
      heroShimmer.style.setProperty('--my', y + '%');
    });

    /* ─────────────────────────────────────────
       MODAL
    ───────────────────────────────────────── */
    function openModal(roomId) {
      currentRoom = rooms.find(r => r.id === roomId);
      if (!currentRoom) return;

      document.getElementById('modalRoomType').textContent = currentRoom.category;
      document.getElementById('modalRoomName').textContent = currentRoom.name;
      document.getElementById('modalRoomImg').src = currentRoom.img;

      // Pre-fill dates from search form
      const ci = document.getElementById('checkIn').value;
      const co = document.getElementById('checkOut').value;
      if (ci) document.getElementById('modalCheckIn').value = ci;
      if (co) document.getElementById('modalCheckOut').value = co;

      // Default dates if not set
      if (!document.getElementById('modalCheckIn').value) {
        const today = new Date(); today.setDate(today.getDate() + 1);
        document.getElementById('modalCheckIn').value = today.toISOString().split('T')[0];
      }
      if (!document.getElementById('modalCheckOut').value) {
        const d = new Date(document.getElementById('modalCheckIn').value);
        d.setDate(d.getDate() + 2);
        document.getElementById('modalCheckOut').value = d.toISOString().split('T')[0];
      }

      updatePrice();

      document.getElementById('booking-view').style.display = 'block';
      document.getElementById('confirmation-view').style.display = 'none';
      document.getElementById('bookingModal').classList.add('open');
      document.body.style.overflow = 'hidden';

      renderPayPalButton();
    }

    function closeModal() {
      document.getElementById('bookingModal').classList.remove('open');
      document.body.style.overflow = '';
      paypalRendered = false;
      document.getElementById('paypal-button-container').innerHTML = '';
    }

    // Close on overlay click
    document.getElementById('bookingModal').addEventListener('click', function (e) {
      if (e.target === this) closeModal();
    });

    // Update price on date change
    ['modalCheckIn', 'modalCheckOut'].forEach(id => {
      document.getElementById(id).addEventListener('change', updatePrice);
    });

    function updatePrice() {
      if (!currentRoom) return;
      const ci = new Date(document.getElementById('modalCheckIn').value);
      const co = new Date(document.getElementById('modalCheckOut').value);
      const nights = Math.max(1, Math.round((co - ci) / 86400000));
      const subtotal = currentRoom.price * nights;
      const tax = +(subtotal * 0.12).toFixed(2);
      const total = +(subtotal + tax).toFixed(2);

      document.getElementById('summNightly').textContent = `$${currentRoom.price} / night`;
      document.getElementById('summNights').textContent = `${nights} night${nights !== 1 ? 's' : ''}`;
      document.getElementById('summTax').textContent = `$${tax}`;
      document.getElementById('summTotal').textContent = `$${total}`;

      return { nights, subtotal, tax, total };
    }

    /* ─────────────────────────────────────────
       PAYPAL
    ───────────────────────────────────────── */
    function renderPayPalButton() {
      if (paypalRendered) return;
      paypalRendered = true;

      const container = document.getElementById('paypal-button-container');
      container.innerHTML = '';

      paypal.Buttons({
        style: {
          color: 'gold',
          shape: 'rect',
          label: 'pay',
          height: 44,
          tagline: false
        },

        onClick(data, actions) {
          if (!validateForm()) {
            return actions.reject();
          }
          return actions.resolve();
        },

        createOrder(data, actions) {
          const { total } = updatePrice();
          return actions.order.create({
            purchase_units: [{
              amount: {
                value: String(total),
                currency_code: 'USD'
              },
              description: `${currentRoom.name} — Élume Hotels`
            }]
          });
        },

        onApprove(data, actions) {
          return actions.order.capture().then(details => {
            const confId = 'ÉLUME-' + Math.random().toString(36).slice(2, 8).toUpperCase();
            const ci = document.getElementById('modalCheckIn').value;
            const co = document.getElementById('modalCheckOut').value;
            const fn = document.getElementById('guestFirstName').value;

            document.getElementById('booking-view').style.display = 'none';
            document.getElementById('confirmation-view').style.display = 'block';
            document.getElementById('confIdDisplay').textContent = confId;
            document.getElementById('confDetails').textContent =
              `${fn ? fn + ', your ' : 'Your '}${currentRoom.name} is reserved · Check-in ${ci} → ${co}`;
            showToast('🎉 Booking confirmed! Check your email.');
          });
        },

        onError(err) {
          showToast('Payment could not be processed. Please try again.');
          console.error('PayPal error:', err);
        },

        onCancel() {
          showToast('Payment cancelled. Your details are still saved.');
        }

      }).render('#paypal-button-container');
    }

    function validateForm() {
      const firstName = document.getElementById('guestFirstName').value.trim();
      const lastName = document.getElementById('guestLastName').value.trim();
      const email = document.getElementById('guestEmail').value.trim();
      const ci = document.getElementById('modalCheckIn').value;
      const co = document.getElementById('modalCheckOut').value;

      if (!firstName || !lastName) { showToast('Please enter your full name.'); return false; }
      if (!email || !email.includes('@')) { showToast('Please enter a valid email address.'); return false; }
      if (!ci || !co) { showToast('Please select check-in and check-out dates.'); return false; }
      if (new Date(co) <= new Date(ci)) { showToast('Check-out must be after check-in.'); return false; }
      return true;
    }

    /* ─────────────────────────────────────────
       UTILITIES
    ───────────────────────────────────────── */
    function scrollTo(selector) {
      document.querySelector(selector)?.scrollIntoView({ behavior: 'smooth', block: 'start' });
    }

    let toastTimer;
    function showToast(msg) {
      const t = document.getElementById('toast');
      t.textContent = msg;
      t.classList.add('show');
      clearTimeout(toastTimer);
      toastTimer = setTimeout(() => t.classList.remove('show'), 3500);
    }

    // Set min dates
    const today = new Date().toISOString().split('T')[0];
    ['checkIn', 'checkOut', 'modalCheckIn', 'modalCheckOut'].forEach(id => {
      const el = document.getElementById(id);
      if (el) el.min = today;
    });
  </script>
</body>

</html>
