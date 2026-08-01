<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Meine Zeit auf der AIDAsol</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,400;9..144,500;9..144,600;9..144,700&family=Nunito+Sans:opsz,wght@6..12,400;6..12,600;6..12,700;6..12,800&family=IBM+Plex+Mono:wght@500&display=swap" rel="stylesheet">
<style>
  /* ---------- Tokens ---------- */
  :root{
    --bg:#FAF1E2;
    --bg-card:#FFFAF0;
    --ink:#2A2420;
    --ink-soft:#6B5D4F;
    --anchor:#1E4A4B;
    --anchor-deep:#123334;
    --anchor-tint:#DCE9E8;
    --accent:#C85A2A;
    --accent-bright:#F0975B;
    --accent-soft:#F3D9BE;
    --gold:#C79232;
    --line:rgba(42,36,32,0.14);
    --hero-bg-1:#163C3D;
    --hero-bg-2:#0F2A2B;
    --hero-ink:#FBF1DD;
    --radius-lg:28px;
    --radius-md:18px;
    --radius-sm:10px;
    --shadow-card:0 14px 34px -18px rgba(20,16,12,0.35);
    --font-display:'Fraunces', serif;
    --font-body:'Nunito Sans', sans-serif;
    --font-mono:'IBM Plex Mono', monospace;
    --wrap:1080px;
  }

  *{ box-sizing:border-box; }
  html{ scroll-behavior:smooth; }
  body{
    margin:0;
    background:var(--bg);
    color:var(--ink);
    font-family:var(--font-body);
    font-size:17px;
    line-height:1.6;
    -webkit-font-smoothing:antialiased;
  }
  h1,h2,h3{ font-family:var(--font-display); font-weight:600; margin:0; }
  p{ margin:0; }
  a{ color:inherit; }
  ul,ol{ margin:0; padding:0; list-style:none; }
  img,svg{ display:block; max-width:100%; }

  .wrap{ max-width:var(--wrap); margin:0 auto; padding:0 28px; }

  a:focus-visible, button:focus-visible{
    outline:3px solid var(--gold);
    outline-offset:3px;
  }

  /* ---------- Hero ---------- */
  .hero{
    background:linear-gradient(160deg, var(--hero-bg-1), var(--hero-bg-2));
    color:var(--hero-ink);
    padding:64px 0 0;
    position:relative;
    overflow:hidden;
  }
  .hero-inner{
    position:relative;
    z-index:2;
    padding-bottom:56px;
  }
  .eyebrow{
    display:inline-flex;
    align-items:center;
    gap:8px;
    font-family:var(--font-mono);
    font-size:12.5px;
    letter-spacing:.08em;
    text-transform:uppercase;
    color:var(--accent-bright);
    background:rgba(255,255,255,0.06);
    border:1px solid rgba(251,241,221,0.18);
    padding:7px 14px;
    border-radius:999px;
  }
  .hero h1{
    margin-top:22px;
    font-size:clamp(2.4rem, 5.4vw, 4.1rem);
    line-height:1.04;
    max-width:14ch;
  }
  .hero h1 em{
    font-style:italic;
    color:var(--accent-bright);
  }
  .hero-dates{
    margin-top:18px;
    font-family:var(--font-mono);
    font-size:clamp(.95rem, 1.6vw, 1.1rem);
    color:var(--hero-ink);
    opacity:.85;
    letter-spacing:.02em;
  }
  .hero-intro{
    margin-top:22px;
    max-width:52ch;
    font-size:1.06rem;
    color:var(--hero-ink);
    opacity:.92;
  }

  .chipnav{
    margin-top:32px;
    display:flex;
    flex-wrap:wrap;
    gap:10px;
  }
  .chip{
    font-family:var(--font-body);
    font-weight:700;
    font-size:.88rem;
    text-decoration:none;
    color:var(--hero-ink);
    border:1px solid rgba(251,241,221,0.35);
    padding:9px 16px;
    border-radius:999px;
    transition:background .2s ease, color .2s ease, border-color .2s ease;
  }
  .chip:hover{
    background:var(--accent-bright);
    border-color:var(--accent-bright);
    color:var(--anchor-deep);
  }

  /* ---------- Horizon / Countdown widget ---------- */
  .horizon-card{
    margin-top:44px;
    background:rgba(251,241,221,0.06);
    border:1px solid rgba(251,241,221,0.16);
    border-radius:var(--radius-lg);
    padding:28px 30px 24px;
    backdrop-filter:blur(2px);
  }
  .horizon-status{
    font-family:var(--font-display);
    font-size:clamp(1.15rem,2.4vw,1.5rem);
    color:var(--hero-ink);
  }
  .horizon-status strong{ color:var(--accent-bright); font-weight:700; }

  .horizon-track{
    position:relative;
    height:6px;
    background:rgba(251,241,221,0.2);
    border-radius:999px;
    margin:34px 4px 10px;
  }
  .horizon-fill{
    position:absolute; inset:0 auto 0 0;
    width:0%;
    background:linear-gradient(90deg, var(--gold), var(--accent-bright));
    border-radius:999px;
    transition:width 1s ease;
  }
  .horizon-marker{
    position:absolute;
    top:50%;
    left:0%;
    transform:translate(-50%,-50%);
    font-size:1.5rem;
    line-height:1;
    transition:left 1s ease;
    filter:drop-shadow(0 3px 6px rgba(0,0,0,0.45));
  }
  .horizon-tick{
    position:absolute;
    top:-7px;
    width:2px;
    height:20px;
    background:rgba(251,241,221,0.5);
    transform:translateX(-50%);
  }
  .horizon-tick span{
    position:absolute;
    top:26px;
    left:50%;
    transform:translateX(-50%);
    font-family:var(--font-mono);
    font-size:.68rem;
    color:rgba(251,241,221,0.65);
    white-space:nowrap;
  }
  .horizon-tick.tick-start span{ left:0; transform:none; text-align:left; }
  .horizon-tick.tick-end span{ left:auto; right:0; transform:none; text-align:right; }
  .horizon-endpoints{
    display:flex;
    justify-content:space-between;
    margin-top:30px;
    font-family:var(--font-mono);
    font-size:.78rem;
    color:rgba(251,241,221,0.75);
  }
  .horizon-endpoints small{ display:block; opacity:.7; font-size:.72rem; margin-top:2px; }

  .wave-divider{
    display:block;
    width:100%;
    height:auto;
    position:relative;
    z-index:1;
    margin-top:-2px;
  }

  /* ---------- Sections ---------- */
  .section{ padding:84px 0; }
  .section + .section{ border-top:1px solid var(--line); }
  .section-head{ max-width:60ch; margin-bottom:44px; }
  .kicker{
    font-family:var(--font-mono);
    font-size:.78rem;
    letter-spacing:.08em;
    text-transform:uppercase;
    color:var(--accent);
  }
  .section h2{
    margin-top:10px;
    font-size:clamp(1.7rem, 3.4vw, 2.4rem);
    color:var(--anchor-deep);
  }
  .section-lede{
    margin-top:14px;
    color:var(--ink-soft);
    font-size:1.04rem;
  }

  /* ---------- Ship stats ---------- */
  .stat-grid{
    display:grid;
    grid-template-columns:repeat(auto-fit, minmax(150px,1fr));
    gap:2px;
    background:var(--line);
    border:1px solid var(--line);
    border-radius:var(--radius-md);
    overflow:hidden;
  }
  .stat-cell{
    background:var(--bg-card);
    padding:22px 20px;
  }
  .stat-cell .val{
    font-family:var(--font-display);
    font-size:1.5rem;
    color:var(--anchor-deep);
    font-weight:600;
  }
  .stat-cell .lab{
    margin-top:4px;
    font-size:.82rem;
    color:var(--ink-soft);
  }

  .tracker-row{
    margin-top:28px;
    display:flex;
    flex-wrap:wrap;
    align-items:center;
    gap:18px;
  }
  .btn{
    display:inline-flex;
    align-items:center;
    gap:8px;
    font-family:var(--font-body);
    font-weight:800;
    font-size:.94rem;
    text-decoration:none;
    color:var(--ink);
    background:var(--accent-bright);
    padding:13px 22px;
    border-radius:999px;
    box-shadow:var(--shadow-card);
    transition:transform .15s ease, box-shadow .15s ease;
  }
  .btn:hover{ transform:translateY(-2px); }
  .fineprint{
    font-family:var(--font-mono);
    font-size:.76rem;
    color:var(--ink-soft);
  }

  /* ---------- Route timeline ---------- */
  .stat-strip{
    display:flex;
    flex-wrap:wrap;
    gap:28px;
    margin-top:28px;
    padding:22px 26px;
    background:var(--anchor-tint);
    border-radius:var(--radius-md);
  }
  .stat-strip div{ min-width:110px; }
  .stat-strip .val{
    font-family:var(--font-display);
    font-size:1.5rem;
    color:var(--anchor-deep);
    font-weight:700;
  }
  .stat-strip .lab{ font-size:.78rem; color:var(--ink-soft); margin-top:2px; }

  .timeline{
    margin-top:40px;
    display:flex;
    flex-direction:column;
  }
  .stage{
    display:grid;
    grid-template-columns:56px 1fr;
    gap:20px;
    padding:26px 0;
    border-top:1px solid var(--line);
  }
  .stage:last-child{ padding-bottom:0; }
  .stage-num{
    font-family:var(--font-mono);
    font-size:.85rem;
    color:var(--bg-card);
    background:var(--anchor);
    width:38px; height:38px;
    border-radius:50%;
    display:flex; align-items:center; justify-content:center;
  }
  .stage.is-main .stage-num{ background:var(--accent); }
  .stage-body{ display:flex; flex-direction:column; gap:6px; }
  .stage-head{
    display:flex;
    flex-wrap:wrap;
    align-items:baseline;
    gap:10px;
  }
  .stage-title{ font-family:var(--font-display); font-size:1.22rem; color:var(--anchor-deep); font-weight:600; }
  .stage-dates{ font-family:var(--font-mono); font-size:.8rem; color:var(--ink-soft); }
  .stage-days{
    font-family:var(--font-mono);
    font-size:.72rem;
    color:var(--accent);
    background:var(--accent-soft);
    padding:3px 9px;
    border-radius:999px;
  }
  .stage-desc{ color:var(--ink-soft); font-size:.98rem; max-width:62ch; }

  .route-note{
    margin-top:32px;
    font-size:.92rem;
    color:var(--ink-soft);
    border-left:3px solid var(--accent-soft);
    padding-left:16px;
  }

  /* ---------- Diary ---------- */
  .diary-grid{
    margin-top:36px;
    display:grid;
    grid-template-columns:repeat(auto-fit, minmax(220px,1fr));
    gap:22px;
  }
  .diary-card{
    background:var(--bg-card);
    border:1px solid var(--line);
    border-radius:var(--radius-md);
    padding:18px;
    box-shadow:var(--shadow-card);
  }
  .diary-photo{
    aspect-ratio:4/3;
    border-radius:var(--radius-sm);
    border:1.5px dashed var(--line);
    background:repeating-linear-gradient(135deg, rgba(30,74,75,0.04) 0 10px, transparent 10px 20px);
    display:flex;
    flex-direction:column;
    align-items:center;
    justify-content:center;
    gap:6px;
    color:var(--ink-soft);
    text-align:center;
  }
  .diary-photo .icon{ font-size:1.6rem; opacity:.7; }
  .diary-photo span{ font-size:.74rem; font-family:var(--font-mono); }
  .diary-date{
    margin-top:14px;
    font-family:var(--font-mono);
    font-size:.72rem;
    color:var(--accent);
    text-transform:uppercase;
    letter-spacing:.04em;
  }
  .diary-title{
    margin-top:4px;
    font-family:var(--font-display);
    font-size:1.08rem;
    color:var(--anchor-deep);
  }
  .diary-caption{
    margin-top:6px;
    font-size:.86rem;
    font-style:italic;
    color:var(--ink-soft);
  }

  /* ---------- Footer ---------- */
  .footer{
    padding:56px 0 64px;
    text-align:center;
  }
  .footer p{ color:var(--ink-soft); }
  .footer .sign{
    font-family:var(--font-display);
    font-size:1.3rem;
    color:var(--anchor-deep);
    margin-bottom:10px;
  }
  .footer .meta{
    margin-top:18px;
    font-family:var(--font-mono);
    font-size:.72rem;
    color:var(--ink-soft);
    opacity:.75;
  }

  @media (max-width:640px){
    .section{ padding:60px 0; }
    .hero{ padding-top:48px; }
    .hero-inner{ padding-bottom:44px; }
    .stage{ grid-template-columns:40px 1fr; }
  }

  @media (prefers-reduced-motion: reduce){
    html{ scroll-behavior:auto; }
    .horizon-fill, .horizon-marker, .btn{ transition:none; }
  }
</style>
</head>
<body>

<header class="hero">
  <div class="wrap hero-inner">
    <span class="eyebrow">⚓ nur für Mama &amp; Papa</span>
    <h1>Meine Zeit auf der <em>AIDAsol</em></h1>
    <p class="hero-dates">02.10.2026&nbsp;&nbsp;→&nbsp;&nbsp;02.03.2027</p>
    <p class="hero-intro">Damit ihr immer wisst, wo ich gerade unterwegs bin und was als Nächstes ansteht, habe ich euch diese kleine Seite gebaut. Schaut jederzeit vorbei — sie zeigt euch automatisch den aktuellen Stand, ganz ohne dass ich etwas tun muss.</p>

    <nav class="chipnav">
      <a class="chip" href="#schiff">Das Schiff</a>
      <a class="chip" href="#route">Die Route</a>
      <a class="chip" href="#tagebuch">Foto-Tagebuch</a>
    </nav>

    <div class="horizon-card" role="group" aria-label="Fortschritt meiner Zeit an Bord">
      <p class="horizon-status" id="horizonStatus">Lädt …</p>
      <div class="horizon-track">
        <div class="horizon-fill" id="horizonFill"></div>
        <div class="horizon-tick tick-start" style="left:10.6%"><span>18.10. Start Weltreise</span></div>
        <div class="horizon-tick tick-end" style="left:94%"><span>21.02. Rückkehr</span></div>
        <div class="horizon-marker" id="shipMarker">🚢</div>
      </div>
      <div class="horizon-endpoints">
        <span>02.10.2026<small>Einschiffung</small></span>
        <span>02.03.2027<small>Ausschiffung</small></span>
      </div>
    </div>
  </div>

  <svg class="wave-divider" viewBox="0 0 1440 90" preserveAspectRatio="none" aria-hidden="true">
    <path d="M0,40 C240,90 480,0 720,40 C960,80 1200,10 1440,50 L1440,90 L0,90 Z" fill="#FAF1E2"></path>
  </svg>
</header>

<main class="wrap">

  <!-- SCHIFF -->
  <section class="section" id="schiff">
    <div class="section-head">
      <span class="kicker">Mein Zuhause auf Zeit</span>
      <h2>Die AIDAsol im Überblick</h2>
      <p class="section-lede">Ein paar Eckdaten zum Schiff, auf dem ich die nächsten Monate lebe und arbeite — falls ihr euch schon immer gefragt habt, wie groß so ein "kleines Zuhause auf dem Wasser" eigentlich ist.</p>
    </div>

    <div class="stat-grid">
      <div class="stat-cell"><div class="val">253&nbsp;m</div><div class="lab">Länge</div></div>
      <div class="stat-cell"><div class="val">32&nbsp;m</div><div class="lab">Breite</div></div>
      <div class="stat-cell"><div class="val">71.300</div><div class="lab">BRZ (Tonnage)</div></div>
      <div class="stat-cell"><div class="val">~22&nbsp;kn</div><div class="lab">Reisegeschwindigkeit</div></div>
      <div class="stat-cell"><div class="val">14</div><div class="lab">Decks</div></div>
      <div class="stat-cell"><div class="val">1.097</div><div class="lab">Kabinen</div></div>
      <div class="stat-cell"><div class="val">bis 2.194</div><div class="lab">Gäste</div></div>
      <div class="stat-cell"><div class="val">~609</div><div class="lab">Crew an Bord</div></div>
      <div class="stat-cell"><div class="val">2011</div><div class="lab">Baujahr, Meyer Werft</div></div>
    </div>

    <div class="tracker-row">
      <a class="btn" href="https://www.vesselfinder.com/de/vessels/details/9490040" target="_blank" rel="noopener">Live-Position ansehen ↗</a>
      <p class="fineprint">Auf VesselFinder seht ihr per Funksignal (AIS), wo das Schiff sich gerade befindet.<br>IMO 9490040 · MMSI 247302900</p>
    </div>
  </section>

  <!-- ROUTE -->
  <section class="section" id="route">
    <div class="section-head">
      <span class="kicker">Wohin es geht</span>
      <h2>Die große Reise</h2>
      <p class="section-lede">Herzstück meiner Zeit an Bord ist die achte Weltreise der AIDAsol: 126 Tage rund um den Globus, vom 18. Oktober 2026 bis zum 21. Februar 2027. Davor und danach bin ich zur Vorbereitung bzw. zum Ausklang mit an Bord — insgesamt ergibt das meinen ganzen Einsatzzeitraum.</p>
    </div>

    <div class="stat-strip">
      <div><div class="val">126</div><div class="lab">Tage Weltreise</div></div>
      <div><div class="val">4</div><div class="lab">Kontinente</div></div>
      <div><div class="val">20</div><div class="lab">Länder</div></div>
      <div><div class="val">43</div><div class="lab">Häfen</div></div>
      <div><div class="val">2×</div><div class="lab">Äquator­überquerung</div></div>
    </div>

    <ol class="timeline">
      <li class="stage">
        <span class="stage-num">0</span>
        <div class="stage-body">
          <div class="stage-head">
            <span class="stage-title">Einschiffung &amp; Vorbereitung</span>
            <span class="stage-dates">02.10. – 18.10.2026</span>
            <span class="stage-days">16 Tage</span>
          </div>
          <p class="stage-desc">Ich schiffe in Hamburg ein, lerne Schiff und Crew kennen und bereite alles für die große Reise vor.</p>
        </div>
      </li>
      <li class="stage is-main">
        <span class="stage-num">1</span>
        <div class="stage-body">
          <div class="stage-head">
            <span class="stage-title">Hamburg → San Antonio (Chile)</span>
            <span class="stage-dates">18.10. – 01.12.2026</span>
            <span class="stage-days">44 Tage</span>
          </div>
          <p class="stage-desc">Über den Atlantik, vorbei an den Kanaren, tief in den Amazonas (u. a. Santarém und Boca da Valeria) und um das berühmte Kap Hoorn an der Südspitze Südamerikas.</p>
        </div>
      </li>
      <li class="stage is-main">
        <span class="stage-num">2</span>
        <div class="stage-body">
          <div class="stage-head">
            <span class="stage-title">San Antonio → Mauritius</span>
            <span class="stage-dates">01.12.2026 – 19.01.2027</span>
            <span class="stage-days">49 Tage</span>
          </div>
          <p class="stage-desc">Über den Pazifik zur Osterinsel und durch die Südsee (Französisch-Polynesien, u. a. Tahiti), dann sechs Häfen in Australien — inklusive Silvester-Feuerwerk in Sydney am 31.12.</p>
        </div>
      </li>
      <li class="stage is-main">
        <span class="stage-num">3</span>
        <div class="stage-body">
          <div class="stage-head">
            <span class="stage-title">Mauritius → Hamburg</span>
            <span class="stage-dates">19.01. – 21.02.2027</span>
            <span class="stage-days">33 Tage</span>
          </div>
          <p class="stage-desc">Über den Indischen Ozean (La Réunion), am Kap der Guten Hoffnung vorbei nach Kapstadt und Namibia, dann über die Kanaren zurück nach Hamburg.</p>
        </div>
      </li>
      <li class="stage">
        <span class="stage-num">4</span>
        <div class="stage-body">
          <div class="stage-head">
            <span class="stage-title">Ausklang &amp; Ausschiffung</span>
            <span class="stage-dates">21.02. – 02.03.2027</span>
            <span class="stage-days">9 Tage</span>
          </div>
          <p class="stage-desc">Direkt im Anschluss startet laut Fahrplan eine kurze Nordland-Kreuzfahrt ab Hamburg — ich bin voraussichtlich bis zu meinem letzten Arbeitstag mit an Bord, bevor es nach Hause geht.</p>
        </div>
      </li>
    </ol>

    <p class="route-note">Kleiner Hinweis: Die Route basiert auf dem öffentlichen AIDA-Fahrplan und kann sich noch ändern. Mein genauer persönlicher Einsatz an Bord kann außerdem leicht abweichen — diese Übersicht dient euch vor allem zur groben Orientierung, wo das Schiff wann etwa unterwegs ist.</p>
  </section>

  <!-- TAGEBUCH -->
  <section class="section" id="tagebuch">
    <div class="section-head">
      <span class="kicker">Von unterwegs</span>
      <h2>Foto-Tagebuch</h2>
      <p class="section-lede">Hier sammle ich Fotos und kurze Updates von den schönsten Momenten der Reise. Die Seite ist fest, ich aktualisiere die Karten also von Hand, sobald ich an Land Internet habe — schaut also gerne ab und zu wieder vorbei.</p>
    </div>

    <div class="diary-grid">
      <article class="diary-card">
        <div class="diary-photo"><span class="icon">📷</span><span>Foto folgt</span></div>
        <p class="diary-date">02.10.2026</p>
        <h3 class="diary-title">Einschiffung in Hamburg</h3>
        <p class="diary-caption">Update folgt, sobald es losgeht.</p>
      </article>
      <article class="diary-card">
        <div class="diary-photo"><span class="icon">📷</span><span>Foto folgt</span></div>
        <p class="diary-date">November 2026</p>
        <h3 class="diary-title">Amazonas-Erlebnis</h3>
        <p class="diary-caption">Vier Tage auf dem Fluss, u. a. Santarém.</p>
      </article>
      <article class="diary-card">
        <div class="diary-photo"><span class="icon">📷</span><span>Foto folgt</span></div>
        <p class="diary-date">Ende November 2026</p>
        <h3 class="diary-title">Kap Hoorn</h3>
        <p class="diary-caption">Die Südspitze Südamerikas.</p>
      </article>
      <article class="diary-card">
        <div class="diary-photo"><span class="icon">📷</span><span>Foto folgt</span></div>
        <p class="diary-date">24.–25.12.2026</p>
        <h3 class="diary-title">Weihnachten auf See</h3>
        <p class="diary-caption">Update folgt.</p>
      </article>
      <article class="diary-card">
        <div class="diary-photo"><span class="icon">📷</span><span>Foto folgt</span></div>
        <p class="diary-date">31.12.2026</p>
        <h3 class="diary-title">Silvester in Sydney</h3>
        <p class="diary-caption">Feuerwerk über dem Hafen.</p>
      </article>
      <article class="diary-card">
        <div class="diary-photo"><span class="icon">📷</span><span>Foto folgt</span></div>
        <p class="diary-date">Februar 2027</p>
        <h3 class="diary-title">Kapstadt</h3>
        <p class="diary-caption">Update folgt.</p>
      </article>
      <article class="diary-card">
        <div class="diary-photo"><span class="icon">📷</span><span>Foto folgt</span></div>
        <p class="diary-date">02.03.2027</p>
        <h3 class="diary-title">Zurück in Hamburg</h3>
        <p class="diary-caption">Ich freu mich schon auf euch!</p>
      </article>
    </div>
  </section>

</main>

<footer class="footer">
  <div class="wrap">
    <p class="sign">Bis bald, ich hab euch lieb ♥</p>
    <p>Diese Seite läuft ganz von selbst — kommt einfach jederzeit wieder vorbei.</p>
    <p class="meta">Meine Zeit auf der AIDAsol · 02.10.2026 – 02.03.2027</p>
  </div>
</footer>

<script>
(function(){
  var START = new Date('2026-10-02T00:00:00');
  var END   = new Date('2027-03-02T23:59:59');
  var now   = new Date();

  function daysBetween(a,b){ return Math.round((b - a) / 86400000); }

  var totalDays = daysBetween(START, END);
  var statusEl  = document.getElementById('horizonStatus');
  var fillEl    = document.getElementById('horizonFill');
  var markerEl  = document.getElementById('shipMarker');
  var percent, statusHTML;

  if (now < START) {
    var toStart = daysBetween(now, START);
    statusHTML = 'Noch <strong>' + toStart + ' Tage</strong> bis zur Einschiffung ⚓';
    percent = 0;
  } else if (now > END) {
    var since = daysBetween(END, now);
    statusHTML = since <= 0
      ? 'Heute geht es nach Hause 🏡'
      : 'Schon <strong>' + since + ' Tage</strong> wieder zuhause 🏡';
    percent = 100;
  } else {
    var elapsed = daysBetween(START, now);
    var remaining = totalDays - elapsed;
    statusHTML = 'Tag <strong>' + elapsed + '</strong> von ' + totalDays + ' an Bord ⛴️ — noch ' + remaining + ' Tage';
    percent = Math.min(100, Math.max(0, (elapsed / totalDays) * 100));
  }

  statusEl.innerHTML = statusHTML;
  fillEl.style.width = percent + '%';
  markerEl.style.left = percent + '%';
})();
</script>

</body>
</html>
