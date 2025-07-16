<!DOCTYPE html>
<html lang="de">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Karlopolis</title>
  <!-- Google Fonts: Quicksand + Manrope für moderne Optik -->
  <link href="https://fonts.googleapis.com/css?family=Quicksand:400,500,700|Manrope:400,600,800&display=swap" rel="stylesheet">
  <style>
    :root {
      --creme-bg: #f7f4ef;
      --accent: #2563eb;
      --accent-dark: #1e40af;
      --text: #2563eb;
      --header-bg: #fff;
      --shadow: 0 2px 12px #2563eb10;
      --card-bg: #fff;
      --border-radius: 12px;
      --transition-fast: 0.18s cubic-bezier(.4,0,.2,1);
      --nav-height: 54px;
      --nav-blur: 18px;
      --info-gap: 18px;
      --menu-width: 220px;
    }
    html { scroll-behavior: smooth; }
    body {
      margin: 0;
      font-family: 'Manrope', 'Quicksand', Arial, sans-serif;
      background: var(--creme-bg);
      color: var(--text);
      min-height: 100vh;
    }
    header {
      background: var(--header-bg);
      box-shadow: var(--shadow);
      padding: 38px 0 14px 0;
      text-align: center;
      font-size: 2.15rem;
      font-weight: 800;
      letter-spacing: 1.5px;
      color: var(--accent);
      font-family: 'Manrope', Arial, sans-serif;
      cursor: pointer;
      user-select: none;
      transition: color var(--transition-fast);
      position: relative;
      z-index: 102;
    }
    header:hover { color: var(--accent-dark); }

    nav {
      position: sticky;
      top: 0;
      z-index: 100;
      background: rgba(255,255,255,0.87);
      -webkit-backdrop-filter: blur(var(--nav-blur));
      backdrop-filter: blur(var(--nav-blur));
      border-bottom: 1px solid #e5e7eb;
      font-family: 'Manrope', Arial, sans-serif;
      box-shadow: 0 1px 8px #2563eb09;
      height: var(--nav-height);
      width: 100%;
    }
    .hamburger {
      position: absolute;
      top: 7px;
      right: 18px;
      width: 44px;
      height: 44px;
      background: none;
      border: none;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      outline: none;
      z-index: 201;
    }
    .hamburger span {
      display: block;
      width: 27px;
      height: 3.5px;
      background: var(--accent-dark);
      border-radius: 3px;
      margin: 4px 0;
      transition: all 0.26s cubic-bezier(.4,0,.2,1);
    }
    .nav-dropdown-menu {
      display: none;
      position: absolute;
      top: 56px;
      right: 18px;
      min-width: var(--menu-width);
      background: rgba(255,255,255,0.97);
      border-radius: var(--border-radius);
      box-shadow: 0 8px 32px #2563eb1c;
      border: 1px solid #e5e7eb;
      padding: 16px 0;
      z-index: 200;
      animation: dropdownFadeIn 0.22s;
      font-family: 'Manrope', Arial, sans-serif;
      overflow: hidden;
    }
    .nav-dropdown-menu.open { display: block; }
    .nav-dropdown-menu a {
      display: block;
      color: var(--accent-dark);
      padding: 14px 32px;
      font-size: 1.08rem;
      text-decoration: none;
      white-space: nowrap;
      font-weight: 600;
      transition: background 0.13s, color 0.13s;
      border-left: 3px solid transparent;
    }
    .nav-dropdown-menu a:hover,
    .nav-dropdown-menu a:focus {
      background: #f3f8ff;
      color: var(--accent);
      border-left: 3px solid var(--accent);
    }
    @keyframes dropdownFadeIn {
      from { opacity: 0; transform: translateY(12px);}
      to { opacity: 1; transform: translateY(0);}
    }
    main { min-height: 60vh; color: var(--text); }
    @media (max-width: 600px) {
      .nav-dropdown-menu {
        right: 10px;
        min-width: 80vw;
      }
      .hamburger {
        right: 6px;
        top: 6px;
        width: 38px;
        height: 38px;
      }
    }
    .hero {
      max-width: 1100px;
      margin: 60px auto 0 auto;
      text-align: center;
      padding: 0 1.5rem;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 20px;
      color: var(--text);
    }
    .hero-image {
      width: 100%;
      max-width: 880px;
      display: block;
      margin: 0 auto 32px auto;
      border-radius: var(--border-radius);
      box-shadow: 0 8px 50px #2563eb12;
      object-fit: cover;
      height: 350px;
    }
    .hero-title {
      font-size: 2.45rem;
      font-weight: 800;
      margin: 0 0 10px 0;
      color: var(--accent);
      letter-spacing: 1.4px;
      font-family: 'Manrope', Arial, sans-serif;
      line-height: 1.13;
    }
    .hero-desc {
      font-size: 1.26rem;
      color: var(--text);
      margin-bottom: 32px;
      line-height: 1.7;
      max-width: 640px;
      margin-left: auto;
      margin-right: auto;
      font-family: 'Quicksand', Arial, sans-serif;
    }
    .hero-btn {
      display: inline-block;
      margin-top: 14px;
      background: var(--accent);
      color: #fff;
      font-size: 1.13rem;
      font-weight: 700;
      padding: 14px 38px;
      border-radius: 9px;
      border: none;
      cursor: pointer;
      box-shadow: 0 4px 18px #2563eb21;
      text-decoration: none;
      transition: background var(--transition-fast), transform var(--transition-fast);
      font-family: 'Manrope', Arial, sans-serif;
      letter-spacing: 0.7px;
    }
    .hero-btn:hover {
      background: var(--accent-dark);
      transform: translateY(-2px) scale(1.04);
    }
    .image-row {
      max-width: 1100px;
      margin: 64px auto 0 auto;
      display: flex;
      gap: 2.5rem;
      justify-content: center;
      padding: 0 1.5rem;
      flex-wrap: wrap;
      color: var(--text);
    }
    .image-card {
      background: var(--card-bg);
      border-radius: var(--border-radius);
      box-shadow: 0 8px 38px #2563eb1a;
      flex: 1 1 340px;
      max-width: 440px;
      min-width: 260px;
      display: flex;
      flex-direction: column;
      align-items: center;
      margin-bottom: 28px;
      font-family: 'Quicksand', Arial, sans-serif;
      transition: transform 0.14s, box-shadow 0.14s;
      color: var(--text);
    }
    .image-card:hover {
      transform: translateY(-4px) scale(1.03);
      box-shadow: 0 12px 48px #2563eb22;
    }
    .image-card img {
      width: 100%;
      height: 210px;
      object-fit: cover;
      border-top-left-radius: var(--border-radius);
      border-top-right-radius: var(--border-radius);
      margin-bottom: 0;
      display: block;
    }
    .image-card .caption {
      padding: 24px 22px 20px 22px;
      color: var(--text);
      font-size: 1.12rem;
      text-align: center;
      font-family: 'Quicksand', Arial, sans-serif;
    }
    .staat-info,
    .staat-ankuendigungen {
      max-width: 700px;
      margin: 0 auto;
      background: var(--card-bg);
      border-radius: var(--border-radius);
      box-shadow: 0 4px 24px #2563eb12;
      color: var(--text);
      font-family: 'Quicksand', Arial, sans-serif;
      transition: box-shadow var(--transition-fast);
    }
    .staat-info {
      padding: 38px 32px;
      font-size: 1.16rem;
      line-height: 1.95;
      margin-top: 70px;
      margin-bottom: var(--info-gap);
    }
    .staat-info:hover {
      box-shadow: 0 12px 40px #2563eb21;
    }
    .staat-info h2 {
      color: var(--accent);
      font-size: 1.45rem;
      margin-bottom: 1.2rem;
      font-weight: 800;
      letter-spacing: 0.5px;
      font-family: 'Manrope', Arial, sans-serif;
    }
    .staat-info ul {
      list-style: none;
      padding: 0;
      margin: 0;
    }
    .staat-info li {
      margin-bottom: 7px;
      color: var(--text);
    }
    .staat-info .label {
      color: var(--accent);
      font-weight: 700;
      margin-right: 8px;
      font-family: 'Quicksand', Arial, sans-serif;
    }
    .staat-ankuendigungen {
      padding: 32px 28px;
      font-size: 1.13rem;
      line-height: 1.9;
      margin-bottom: var(--info-gap);
    }
    .staat-ankuendigungen:hover {
      box-shadow: 0 12px 40px #2563eb21;
    }
    .staat-ankuendigungen h2 {
      color: var(--accent);
      font-size: 1.29rem;
      margin-bottom: 1.2rem;
      font-weight: 800;
      letter-spacing: 0.4px;
      font-family: 'Manrope', Arial, sans-serif;
    }
    .staat-ankuendigungen ul {
      list-style: none;
      padding: 0;
      margin: 0;
    }
    .staat-ankuendigungen li {
      margin-bottom: 6px;
      color: var(--text);
    }
    .staat-ankuendigungen .label {
      color: var(--accent);
      font-weight: 700;
      margin-right: 8px;
      font-family: 'Quicksand', Arial, sans-serif;
    }
    .page {
      max-width: 1000px;
      margin: 52px auto;
      background: var(--card-bg);
      border-radius: var(--border-radius);
      box-shadow: 0 4px 28px #2563eb1a;
      padding: 44px 36px;
      color: var(--text);
      font-size: 1.18rem;
      display: none;
      animation: fadeIn 0.44s;
      font-family: 'Quicksand', Arial, sans-serif;
    }
    .page.active {
      display: block;
    }
    .page h2 {
      color: var(--accent);
      margin-top: 0;
      font-size: 2.1rem;
      margin-bottom: 24px;
      letter-spacing: 0.8px;
      font-family: 'Manrope', Arial, sans-serif;
      font-weight: 800;
    }
    .betrieb-cards {
      display: flex;
      gap: 2.5rem;
      flex-wrap: wrap;
      justify-content: center;
      margin-top: 38px;
      color: var(--text);
    }
    .betrieb-card {
      background: #f8fafc;
      border-radius: 20px;
      box-shadow: 0 2px 16px #2563eb1a;
      padding: 28px 24px 24px 24px;
      max-width: 340px;
      min-width: 220px;
      flex: 1 1 260px;
      margin-bottom: 18px;
      text-align: center;
      font-family: 'Quicksand', Arial, sans-serif;
      display: flex;
      flex-direction: column;
      align-items: center;
      position: relative;
      transition: transform 0.14s, box-shadow 0.14s;
      color: var(--text);
    }
    .betrieb-card:hover {
      transform: translateY(-4px) scale(1.03);
      box-shadow: 0 8px 38px #2563eb26;
    }
    .betrieb-card-placeholder-img {
      width: 110px;
      height: 110px;
      background: var(--betrieb-placeholder);
      border-radius: 50%;
      margin-bottom: 18px;
      display: flex;
      align-items: center;
      justify-content: center;
      color: var(--betrieb-placeholder-icon);
      font-size: 2.8rem;
      font-weight: 700;
      font-family: 'Manrope', Arial, sans-serif;
      border: 2.5px dashed #cbd5e1;
      user-select: none;
      margin-top: -48px;
      box-shadow: 0 2px 12px #2563eb16;
      object-fit: cover;
    }
    .betrieb-card h3 {
      color: var(--accent);
      margin: 18px 0 8px 0;
      font-size: 1.28rem;
      letter-spacing: 0.2px;
      font-family: 'Manrope', Arial, sans-serif;
      font-weight: 700;
      cursor: pointer;
      transition: color 0.15s;
    }
    .betrieb-card h3:hover {
      color: var(--accent-dark);
      text-decoration: underline;
    }
    .betrieb-card p {
      color: var(--text);
      font-size: 1.07rem;
      margin: 0;
      font-family: 'Quicksand', Arial, sans-serif;
    }
    .betrieb-card .img-label {
      color: #b5a37c;
      font-size: 0.97rem;
      margin-top: 4px;
      margin-bottom: 8px;
      font-family: 'Quicksand', Arial, sans-serif;
      letter-spacing: 0.1px;
    }
    .betrieb-card-placeholder-img svg {
      width: 48px;
      height: 48px;
      opacity: 0.5;
    }
    /* Detailseiten für Betriebe */
    .betrieb-detail {
      max-width: 700px;
      margin: 52px auto;
      background: var(--card-bg);
      border-radius: var(--border-radius);
      box-shadow: 0 4px 28px #2563eb24;
      padding: 44px 36px;
      color: var(--text);
      font-size: 1.17rem;
      font-family: 'Quicksand', Arial, sans-serif;
      display: none;
      animation: fadeIn 0.44s;
    }
    .betrieb-detail.active {
      display: block;
    }
    .betrieb-detail h2 {
      color: var(--accent);
      font-size: 2rem;
      font-weight: 800;
      margin-top: 0;
      margin-bottom: 24px;
      letter-spacing: 0.7px;
      font-family: 'Manrope', Arial, sans-serif;
    }
    .betrieb-detail .back-link {
      display: inline-block;
      margin-bottom: 18px;
      color: var(--accent-dark);
      font-size: 1rem;
      text-decoration: underline;
      cursor: pointer;
      transition: color 0.13s;
    }
    .betrieb-detail .back-link:hover {
      color: var(--accent);
    }
    @media (max-width: 600px) {
      .betrieb-detail { padding: 18px 8px; }
    }
  </style>
</head>
<body>
  <header onclick="showPage('')">
    Karlopolis
  </header>
  <nav>
    <!-- Hamburger-Menü-Symbol oben rechts -->
    <button class="hamburger" id="hamburger-menu" aria-label="Menü öffnen" aria-expanded="false">
      <span></span>
      <span></span>
      <span></span>
    </button>
    <!-- Dropdown-Menü -->
    <div class="nav-dropdown-menu" id="main-dropdown-menu">
      <a href="#" onclick="showPage('');closeMenu();return false;">Start</a>
      <a href="#" onclick="showPage('agentur');closeMenu();return false;">BB Agency</a>
      <a href="#" onclick="showPage('betriebe');closeMenu();return false;">Betriebe</a>
    </div>
  </nav>
  <main>
    <!-- Startseite -->
    <section class="hero" id="home">
      <img src="image1.jpg" alt="Staatliches Gebäude" class="hero-image">
      <div class="hero-title">Willkommen in Karloplis</div>
      <div class="hero-desc">
        Dem Demokratischen Staat am Karlsgymnasium<br>
        Entdecke unsere großartigen Betriebe und vieles mehr
      </div>
      <a class="hero-btn" href="#staat">Mehr erfahren</a>
    </section>

    <section class="image-row" id="imagerow">
      <div class="image-card">
        <img src="image3.jpg" alt="Innenansicht Treppenhaus">
        <div class="caption">
          Repräsentatives Treppenhaus – verbindet Tradition und Moderne im Staatsgebäude.
        </div>
      </div>
      <div class="image-card">
        <img src="image2.jpg" alt="Foyer im Staatsgebäude">
        <div class="caption">
          Das großzügige Foyer als Ort der Begegnung und Verwaltung.
        </div>
      </div>
    </section>

    <section class="staat-info" id="staat">
      <h2>Informationen zum Staat</h2>
      <ul>
        <li><span class="label">Name:</span> Karlopolis</li>
        <li><span class="label">Bürger:</span> 500</li>
        <li><span class="label">Regierungsform:</span> Demokratie</li>
        <li><span class="label">Landessprache:</span> Deutsch</li>
        <li><span class="label">Heutige Öffnungszeit:</span> 8-13 Uhr</li>
      </ul>
    </section>

    <section class="staat-ankuendigungen">
      <h2>Staatsankündigungen</h2>
      <ul>
        <li><span class="label">16. Juli:</span> Sommerfest im Staat ab 12 Uhr – alle Bürger sind herzlich eingeladen!</li>
        <li><span class="label">18. Juli:</span> xxx</li>
        <li><span class="label">20. Juli:</span> xxx</li>
      </ul>
    </section>

    <!-- Unterseite: Betriebe -->
    <section class="page" id="betriebe-page">
      <h2>Unsere Betriebe</h2>
      <div class="betrieb-cards">
        <!-- Blumenstudio Flora -->
        <div class="betrieb-card">
          <div class="betrieb-card-placeholder-img">
            <svg viewBox="0 0 24 24" fill="none">
              <path d="M4 7.5A2.5 2.5 0 0 1 6.5 5h2.086a1 1 0 0 0 .707-.293l.914-.914A2 2 0 0 1 12.828 3h2.343a2 2 0 0 1 1.414.586l.914.914a1 1 0 0 0 .707.293H17.5A2.5 2.5 0 0 1 20 7.5v9a2.5 2.5 0 0 1-2.5 2.5h-11A2.5 2.5 0 0 1 4 16.5v-9Z" stroke="currentColor" stroke-width="1.3"/>
              <circle cx="12" cy="13" r="3.2" stroke="currentColor" stroke-width="1.3"/>
            </svg>
          </div>
          <div class="img-label">Platzhalter – Bild einfügen</div>
          <h3 onclick="showBetriebDetail('flora')">Blumenstudio Flora</h3>
          <p>Kreative Floristik für jeden Anlass – ob Hochzeit, Event oder einfach nur ein schöner Strauß für Zuhause.</p>
        </div>
        <!-- Fitnesszentrum Aktiv -->
        <div class="betrieb-card">
          <div class="betrieb-card-placeholder-img">
            <svg viewBox="0 0 24 24" fill="none">
              <path d="M4 7.5A2.5 2.5 0 0 1 6.5 5h2.086a1 1 0 0 0 .707-.293l.914-.914A2 2 0 0 1 12.828 3h2.343a2 2 0 0 1 1.414.586l.914.914a1 1 0 0 0 .707.293H17.5A2.5 2.5 0 0 1 20 7.5v9a2.5 2.5 0 0 1-2.5 2.5h-11A2.5 2.5 0 0 1 4 16.5v-9Z" stroke="currentColor" stroke-width="1.3"/>
              <circle cx="12" cy="13" r="3.2" stroke="currentColor" stroke-width="1.3"/>
            </svg>
          </div>
          <div class="img-label">Platzhalter – Bild einfügen</div>
          <h3 onclick="showBetriebDetail('aktiv')">Fitnesszentrum Aktiv</h3>
          <p>Modern ausgestattetes Fitnessstudio mit vielfältigen Kursangeboten und individueller Betreuung durch erfahrene Trainer.</p>
        </div>
        <!-- Autohaus Schnell -->
        <div class="betrieb-card">
          <div class="betrieb-card-placeholder-img">
            <svg viewBox="0 0 24 24" fill="none">
              <path d="M4 7.5A2.5 2.5 0 0 1 6.5 5h2.086a1 1 0 0 0 .707-.293l.914-.914A2 2 0 0 1 12.828 3h2.343a2 2 0 0 1 1.414.586l.914.914a1 1 0 0 0 .707.293H17.5A2.5 2.5 0 0 1 20 7.5v9a2.5 2.5 0 0 1-2.5 2.5h-11A2.5 2.5 0 0 1 4 16.5v-9Z" stroke="currentColor" stroke-width="1.3"/>
              <circle cx="12" cy="13" r="3.2" stroke="currentColor" stroke-width="1.3"/>
            </svg>
          </div>
          <div class="img-label">Platzhalter – Bild einfügen</div>
          <h3 onclick="showBetriebDetail('schnell')">Autohaus Schnell</h3>
          <p>Ihr zuverlässiger Partner für Neu- und Gebrauchtwagen, Werkstattservice und Mobilitätslösungen. Modernste Technik trifft auf persönliche Beratung.</p>
        </div>
        <!-- Karls-Gymnasium -->
        <div class="betrieb-card">
          <img class="betrieb-card-placeholder-img" src="123.jpg" alt="Karls-Gymnasium">
          <div class="img-label">Karls-Gymnasium</div>
          <h3 onclick="showBetriebDetail('karls')">Karls-Gymnasium</h3>
          <p>Traditionsreiches Gymnasium mit exzellentem Bildungsangebot und moderner Ausstattung.</p>
        </div>
      </div>
    </section>

    <!-- Detailseiten für Betriebe -->
    <section class="betrieb-detail" id="detail-flora">
      <span class="back-link" onclick="showPage('betriebe')">&larr; Zurück zu Betriebe</span>
      <h2>Blumenstudio Flora</h2>
      <p>
        Das <b>Blumenstudio Flora</b> bietet kreative Floristik für jeden Anlass. Ob Hochzeit, Event, Trauerfeier oder einfach ein schöner Strauß für Zuhause – unser Team aus erfahrenen Floristen berät Sie gerne und gestaltet individuelle Blumenarrangements nach Ihren Wünschen.
      </p>
      <ul>
        <li>Öffnungszeiten: Mo–Fr 8 – 16 Uhr</li>
        <li>Kontakt: flora@karlopolis.de</li>
        <li>Preise: Sträuße ab 50 Karlonen</li>
      </ul>
    </section>
    <section class="betrieb-detail" id="detail-aktiv">
      <span class="back-link" onclick="showPage('betriebe')">&larr; Zurück zu Betriebe</span>
      <h2>Fitnesszentrum Aktiv</h2>
      <p>
        Das <b>Fitnesszentrum Aktiv</b> ist das modernste Fitnessstudio in Karlopolis. Wir bieten Ihnen modernste Geräte, ein vielfältiges Kursangebot und individuelle Betreuung durch erfahrene Trainer. Ob Muskelaufbau, Ausdauertraining oder Entspannung – bei uns finden Sie das richtige Programm.
      </p>
      <ul>
        <li>Öffnungszeiten: Mo–Sa 7 – 20 Uhr</li>
        <li>Kontakt: aktiv@karlopolis.de</li>
        <li>Mitgliedschaft: ab 200 Karlonen/Monat</li>
      </ul>
    </section>
    <section class="betrieb-detail" id="detail-schnell">
      <span class="back-link" onclick="showPage('betriebe')">&larr; Zurück zu Betriebe</span>
      <h2>Autohaus Schnell</h2>
      <p>
        Das <b>Autohaus Schnell</b> ist Ihr zuverlässiger Partner für Neu- und Gebrauchtwagen. Neben dem Fahrzeugverkauf bieten wir Werkstattservice, Inspektionen und Mobilitätslösungen. Unser Team berät Sie kompetent und persönlich.
      </p>
      <ul>
        <li>Öffnungszeiten: Mo–Fr 9 – 17 Uhr, Sa 10 – 14 Uhr</li>
        <li>Kontakt: schnell@karlopolis.de</li>
        <li>Service: Inspektion ab 120 Karlonen</li>
      </ul>
    </section>
    <section class="betrieb-detail" id="detail-karls">
      <span class="back-link" onclick="showPage('betriebe')">&larr; Zurück zu Betriebe</span>
      <h2>Karls-Gymnasium</h2>
      <p>
        Das <b>Karls-Gymnasium</b> ist ein traditionsreiches Gymnasium mit exzellentem Bildungsangebot, engagierten Lehrkräften und moderner Ausstattung. Wir fördern Talente und bieten eine Vielzahl von AGs, Projekten und Austauschprogrammen.
      </p>
      <ul>
        <li>Schulzeiten: Mo–Fr 8 – 16 Uhr</li>
        <li>Kontakt: schule@karlopolis.de</li>
        <li>Besonderheiten: Austausch mit Partnerstädten, Musik- und Sport-AGs</li>
      </ul>
    </section>

    <!-- Unterseite: Agentur -->
    <section class="page" id="agentur-page">
      <h2>BB Agency – Kreativagentur</h2>
      <p>
        Die BB Agency ist eine moderne Agentur, die sich auf innovative digitale und kreative Lösungen spezialisiert hat.
      </p>
      <ul>
        <li> <b>Webdesign & Entwicklung:</b> Individueller Auftritt für Betriebe auf der Website des Staats ab 500 Karlonen.</li>
        <li> <b>Branding & Grafikdesign:</b> Entwicklung von Logos und Werbematerialien wie Plakaten ab 100 Karlonen.</li>
        <li> <b>Marketing & Social Media:</b> Strategien für Reichweite wie z.B. Marktschreier ab 100 Karlonen.</li>        
      </ul>
      <p style="margin-top:22px;">Unser junges, kreatives Team begleitet Sie von der Idee bis zur Umsetzung – persönlich, flexibel und kompetent.</p>
    </section>
  </main>
  <script>
    // Hamburger Menü: Öffnen/Schließen
    const hamburger = document.getElementById('hamburger-menu');
    const dropdownMenu = document.getElementById('main-dropdown-menu');
    hamburger.addEventListener('click', function(e) {
      e.stopPropagation();
      const isOpen = dropdownMenu.classList.contains('open');
      dropdownMenu.classList.toggle('open', !isOpen);
      hamburger.classList.toggle('active', !isOpen);
      hamburger.setAttribute('aria-expanded', !isOpen ? 'true' : 'false');
    });
    function closeMenu() {
      dropdownMenu.classList.remove('open');
      hamburger.classList.remove('active');
      hamburger.setAttribute('aria-expanded', 'false');
    }
    document.addEventListener('click', function(e) {
      if (!e.target.closest('.nav-dropdown-menu') &&
          !e.target.closest('.hamburger')) {
        closeMenu();
      }
    });

    // Seitenwechsel wie gehabt
    function showPage(page) {
      // Verstecke alle Hauptseiten und alle Detailseiten
      document.getElementById('home').style.display = page ? 'none' : '';
      document.getElementById('imagerow').style.display = page ? 'none' : '';
      document.getElementById('staat').style.display = page ? 'none' : '';
      document.querySelector('.staat-ankuendigungen').style.display = page ? 'none' : '';
      document.getElementById('betriebe-page').classList.remove('active');
      document.getElementById('agentur-page').classList.remove('active');
      // Verstecke alle Betrieb-Detailseiten
      hideAllBetriebDetails();

      closeMenu();
      if (page === 'betriebe') {
        document.getElementById('betriebe-page').classList.add('active');
      } else if (page === 'agentur') {
        document.getElementById('agentur-page').classList.add('active');
      } else {
        document.getElementById('home').style.display = '';
        document.getElementById('imagerow').style.display = '';
        document.getElementById('staat').style.display = '';
        document.querySelector('.staat-ankuendigungen').style.display = '';
      }
      window.scrollTo({top: 0, behavior: "smooth"});
    }

    function hideAllBetriebDetails() {
      document.getElementById('detail-flora').classList.remove('active');
      document.getElementById('detail-aktiv').classList.remove('active');
      document.getElementById('detail-schnell').classList.remove('active');
      document.getElementById('detail-karls').classList.remove('active');
    }

    function showBetriebDetail(which) {
      // Verstecke alle Hauptseiten und alle Detailseiten
      document.getElementById('home').style.display = 'none';
      document.getElementById('imagerow').style.display = 'none';
      document.getElementById('staat').style.display = 'none';
      document.querySelector('.staat-ankuendigungen').style.display = 'none';
      document.getElementById('betriebe-page').classList.remove('active');
      document.getElementById('agentur-page').classList.remove('active');
      hideAllBetriebDetails();

      // Zeige die richtige Detailseite
      document.getElementById('detail-' + which).classList.add('active');
      window.scrollTo({top: 0, behavior: "smooth"});
    }

    showPage();
    document.querySelector('header').addEventListener('click', function() {
      showPage('');
    });
  </script>
</body>
</html>
