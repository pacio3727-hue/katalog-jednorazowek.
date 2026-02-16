<!DOCTYPE html>
<html lang="pl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Katalog Jednorazówek</title>

  <!-- Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700;800&family=Orbitron:wght@600;800&display=swap" rel="stylesheet">

  <style>
    :root{
      --bg: #0b0b0d;
      --panel: #111115;
      --card: #15151b;
      --card2:#121218;
      --text: #eaeaf2;
      --muted: #a6a6b3;
      --border: rgba(255,255,255,.08);
      --shadow: 0 18px 50px rgba(0,0,0,.55);
      --shadow2: 0 10px 25px rgba(0,0,0,.55);
      --accent: #00f7ff;
      --accent2:#7c5cff;
      --radius: 16px;
    }

    *{ box-sizing:border-box; }
    html, body { height:100%; }
    body{
      margin:0;
      font-family: Inter, system-ui, -apple-system, Segoe UI, Roboto, Arial, sans-serif;
      background:
        radial-gradient(1200px 600px at 20% -10%, rgba(0,247,255,.12), transparent 55%),
        radial-gradient(900px 500px at 80% 0%, rgba(124,92,255,.12), transparent 55%),
        radial-gradient(900px 700px at 50% 115%, rgba(0,247,255,.08), transparent 55%),
        var(--bg);
      color: var(--text);
      line-height:1.45;
    }

    a{ color:inherit; text-decoration:none; }
    .wrap{
      width:min(1200px, calc(100% - 40px));
      margin:0 auto;
    }

    /* Age overlay */
    #ageOverlay{
      position:fixed;
      inset:0;
      background: rgba(0,0,0,.92);
      display:flex;
      align-items:center;
      justify-content:center;
      z-index:9999;
      padding:18px;
      backdrop-filter: blur(8px);
    }
    .ageBox{
      width:min(560px, 100%);
      background:
        radial-gradient(900px 300px at 20% 0%, rgba(0,247,255,.14), transparent 55%),
        radial-gradient(900px 300px at 80% 0%, rgba(124,92,255,.14), transparent 55%),
        rgba(15,15,20,.92);
      border:1px solid var(--border);
      border-radius: 18px;
      padding:26px;
      box-shadow: var(--shadow);
      text-align:center;
    }
    .ageBox h2{
      margin:0 0 10px;
      font-family: Orbitron, Inter, sans-serif;
      letter-spacing: 1px;
    }
    .ageBox p{
      margin:0;
      color: var(--muted);
      font-size:14px;
    }
    .ageActions{
      margin-top:16px;
      display:flex;
      gap:10px;
      justify-content:center;
      flex-wrap:wrap;
    }
    .btn{
      border:1px solid var(--border);
      background: rgba(255,255,255,.06);
      color: var(--text);
      padding:11px 16px;
      border-radius: 12px;
      cursor:pointer;
      font-weight:700;
      transition: transform .12s ease, background .12s ease, border-color .12s ease;
      user-select:none;
    }
    .btn:hover{ transform: translateY(-1px); background: rgba(255,255,255,.09); }
    .btn.primary{
      border-color: rgba(0,247,255,.35);
      background: linear-gradient(135deg, rgba(0,247,255,.18), rgba(124,92,255,.12));
    }
    .btn.primary:hover{ border-color: rgba(0,247,255,.6); }

    /* Header (sticky) */
    header{
      position: sticky;
      top: 0;
      z-index: 50;
      background: rgba(8,8,10,.72);
      border-bottom: 1px solid var(--border);
      backdrop-filter: blur(10px);
    }
    .hero{
      padding: 18px 0 14px;
    }
    .heroTop{
      display:flex;
      gap:16px;
      align-items:flex-end;
      justify-content:space-between;
      flex-wrap:wrap;
    }
    .brand{
      display:flex;
      gap:14px;
      align-items:center;
      min-width: 260px;
    }
    .logo{
      width:42px; height:42px;
      border-radius: 14px;
      background:
        radial-gradient(circle at 30% 30%, rgba(0,247,255,.9), rgba(0,247,255,0) 55%),
        radial-gradient(circle at 70% 70%, rgba(124,92,255,.9), rgba(124,92,255,0) 55%),
        rgba(255,255,255,.06);
      border: 1px solid var(--border);
      box-shadow: 0 10px 30px rgba(0,0,0,.35);
    }
    .title h1{
      margin:0;
      font-family: Orbitron, Inter, sans-serif;
      letter-spacing: 1.5px;
      font-weight: 800;
      font-size: clamp(22px, 3vw, 34px);
      line-height:1.1;
      text-transform: uppercase;
    }
    .title p{
      margin:6px 0 0;
      color: var(--muted);
      font-size: 13px;
    }

    .tools{
      display:flex;
      gap:10px;
      align-items:center;
      flex-wrap:wrap;
      justify-content:flex-end;
    }
    .input{
      display:flex;
      align-items:center;
      gap:10px;
      padding:10px 12px;
      border-radius: 14px;
      border:1px solid var(--border);
      background: rgba(255,255,255,.05);
      min-width: min(520px, 100%);
    }
    .input svg{ opacity:.8; flex:0 0 auto; }
    .input input{
      width:100%;
      border:none;
      outline:none;
      background:transparent;
      color: var(--text);
      font-size:14px;
    }
    .select{
      border:1px solid var(--border);
      background: rgba(255,255,255,.05);
      color: var(--text);
      padding:10px 12px;
      border-radius: 14px;
      font-weight:600;
      outline:none;
      cursor:pointer;
    }

    .subbar{
      margin-top:10px;
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:10px;
      flex-wrap:wrap;
      padding-bottom: 8px;
    }
    .stats{
      color: var(--muted);
      font-size: 12px;
    }
    .chips{
      display:flex;
      gap:8px;
      flex-wrap:wrap;
      justify-content:flex-end;
    }
    .chip{
      border:1px solid var(--border);
      background: rgba(255,255,255,.04);
      color: var(--muted);
      padding: 7px 10px;
      border-radius: 999px;
      font-size:12px;
      cursor:pointer;
      user-select:none;
      transition: background .12s ease, border-color .12s ease, transform .12s ease;
    }
    .chip:hover{ transform: translateY(-1px); background: rgba(255,255,255,.06); }
    .chip.active{
      color: var(--text);
      border-color: rgba(0,247,255,.35);
      background: linear-gradient(135deg, rgba(0,247,255,.12), rgba(124,92,255,.08));
    }

    /* Main */
    main{ padding: 18px 0 26px; }
    .products{
      display:grid;
      grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 16px;
    }

    .card{
      background: linear-gradient(180deg, rgba(255,255,255,.03), rgba(255,255,255,.01)), var(--card);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      overflow:hidden;
      box-shadow: 0 8px 24px rgba(0,0,0,.35);
      transition: transform .18s ease, box-shadow .18s ease, border-color .18s ease;
      display:flex;
      flex-direction:column;
      min-height: 420px;
    }
    .card:hover{
      transform: translateY(-4px);
      box-shadow: var(--shadow2);
      border-color: rgba(255,255,255,.16);
    }

    .thumb{
      position:relative;
      height: 220px;
      background: var(--card2);
      overflow:hidden;
    }
    .thumb img{
      width:100%;
      height:100%;
      object-fit:cover;
      display:block;
      filter: saturate(1.05) contrast(1.03);
      transform: scale(1.02);
    }
    .thumb::after{
      content:"";
      position:absolute;
      inset:auto 0 0 0;
      height: 60%;
      background: linear-gradient(180deg, transparent, rgba(0,0,0,.65));
      pointer-events:none;
    }

    .badgeRow{
      position:absolute;
      left: 12px;
      right: 12px;
      bottom: 12px;
      display:flex;
      gap:8px;
      flex-wrap:wrap;
      align-items:center;
    }
    .badge{
      font-size: 11px;
      font-weight: 800;
      padding: 6px 9px;
      border-radius: 999px;
      border: 1px solid var(--border);
      background: rgba(0,0,0,.35);
      color: rgba(255,255,255,.92);
      letter-spacing:.2px;
      backdrop-filter: blur(6px);
    }
    .badge.accent{
      border-color: rgba(0,247,255,.35);
      background: rgba(0,247,255,.12);
    }

    .content{
      padding: 14px 14px 12px;
      display:flex;
      flex-direction:column;
      gap: 10px;
      flex:1 1 auto;
    }
    .content h3{
      margin:0;
      font-size: 16px;
      letter-spacing:.2px;
    }
    .meta{
      margin:0;
      color: var(--muted);
      font-size: 12px;
      display:flex;
      gap:10px;
      flex-wrap:wrap;
    }
    .meta strong{ color: var(--text); font-weight:700; }

    .flavors{
      margin:0;
      padding-left: 18px;
      color: rgba(234,234,242,.84);
      font-size: 13px;
      max-height: 190px;
      overflow:auto;
      scrollbar-width: thin;
      scrollbar-color: rgba(255,255,255,.18) transparent;
    }
    .flavors li{ margin: 2px 0; }

    .footerCard{
      margin-top:auto;
      padding: 12px 14px 14px;
      border-top: 1px solid var(--border);
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:10px;
      background: rgba(0,0,0,.12);
    }
    .small{
      font-size: 12px;
      color: var(--muted);
    }
    .count{
      font-size: 12px;
      font-weight:800;
      color: var(--text);
      border:1px solid var(--border);
      background: rgba(255,255,255,.05);
      padding: 7px 10px;
      border-radius: 999px;
    }

    footer.site{
      border-top: 1px solid var(--border);
      color: rgba(255,255,255,.55);
      font-size: 12px;
      padding: 16px 0 26px;
      text-align:center;
    }

    /* helper */
    .hidden{ display:none !important; }

    /* Mobile tweaks */
    @media (max-width: 560px){
      .input{ min-width: 100%; }
      .thumb{ height: 205px; }
      .card{ min-height: 400px; }
    }
  </style>
</head>

<body>
  <!-- Age Gate -->
  <div id="ageOverlay" aria-modal="true" role="dialog" aria-label="Weryfikacja wieku">
    <div class="ageBox">
      <h2>🔞 Ostrzeżenie</h2>
      <p>
        Strona zawiera informacje o produktach nikotynowych.<br>
        Tylko dla osób pełnoletnich (18+).<br>
        Nikotyna jest substancją silnie uzależniającą.
      </p>
      <div class="ageActions">
        <button class="btn primary" onclick="acceptAge()">Mam ukończone 18 lat</button>
        <button class="btn" onclick="declineAge()">Nie mam 18 lat</button>
      </div>
    </div>
  </div>

  <!-- Header -->
  <header>
    <div class="wrap hero">
      <div class="heroTop">
        <div class="brand">
          <div class="logo" aria-hidden="true"></div>
          <div class="title">
            <h1>Jednorazowe e-papierosy</h1>
            <p>Katalog modeli i dostępnych smaków</p>
          </div>
        </div>

        <div class="tools" role="search">
          <div class="input" title="Wyszukaj po modelu lub smaku">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none" aria-hidden="true">
              <path d="M10.5 18a7.5 7.5 0 1 1 0-15 7.5 7.5 0 0 1 0 15Z" stroke="currentColor" stroke-width="2"/>
              <path d="M21 21l-4.2-4.2" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
            </svg>
            <input id="searchInput" type="search" placeholder="Szukaj: np. 'Vimto', 'Mint', 'Tornado'..." autocomplete="off" />
          </div>

          <select id="modelFilter" class="select" aria-label="Filtruj po modelu">
            <option value="all">Wszystkie modele</option>
          </select>
        </div>
      </div>

      <div class="subbar">
        <div class="stats">
          Widoczne: <strong id="visibleCount">0</strong> / <strong id="totalCount">0</strong>
          &nbsp;•&nbsp; Kliknij chip, by szybko filtrować.
        </div>
        <div class="chips" aria-label="Szybkie filtry">
          <div class="chip" data-chip="mint">Mint</div>
          <div class="chip" data-chip="ice">Ice</div>
          <div class="chip" data-chip="lemon">Lemon</div>
          <div class="chip" data-chip="berry">Berry</div>
          <div class="chip" data-chip="watermelon">Watermelon</div>
          <div class="chip" data-chip="apple">Apple</div>
        </div>
      </div>
    </div>
  </header>

  <!-- Main -->
  <main class="wrap">
    <section class="products" id="products">

      <!-- MODEL 1 -->
      <article class="card" data-model="Merryblade" data-meta="30000 puff • 5% • regulacja mocy 10–26W" data-tags="strawberry kiwi aloe blackcurrant ice peach raspberry cherry mixed berries energy dragon fruit lime honey apple grape fizzy blueberry grapefruit aperol candy vimto lemon mojito jager orange melon dr pepper forest">
        <div class="thumb">
          <img src="https://bestevape.com/wp-content/uploads/2025/10/2-merry-mi-blade-30000-vape-diposable-wegwerp-vape-e-cigarette-puff-jetable-france-nederland-belgie-goedkoop.jpg" alt="Merryblade" loading="lazy">
          <div class="badgeRow">
            <span class="badge accent">30000 puff</span>
            <span class="badge">5%</span>
            <span class="badge">10–26W</span>
          </div>
        </div>
        <div class="content">
          <h3>Merryblade</h3>
          <p class="meta"><strong>Spec:</strong> 30000 puff • 5% • regulacja mocy 10–26W</p>
          <ul class="flavors">
            <li>Prime Strawberry</li><li>Kiwi Passion Fruit Guava</li><li>Aloe Blackcurrant</li>
            <li>Lush Ice</li><li>Peach Lemonade</li><li>Strawberry Raspberry Cherry Ice</li>
            <li>Mixed Berries</li><li>Red Energy Ice</li><li>Dragon Fruit Ice</li>
            <li>Sunset Lime</li><li>Honey Peach</li><li>Green Apple</li>
            <li>Frozen Grape</li><li>Fizzy Cherry</li><li>Crazy Blueberry</li>
            <li>Grapefruit Refresher</li><li>Aperol</li><li>Desert Candy</li>
            <li>Vimto</li><li>Breezy Lemon Berry</li><li>Summer Blaze</li>
            <li>Tropical Citrus Fizz</li><li>Mr. Blue</li><li>Fanta</li>
            <li>Love 66</li><li>Lemon Mojito</li><li>Jager Red Energy</li>
            <li>Orange Dragon</li><li>Iced Peach Melon</li><li>Dr Pepper</li>
            <li>Grape Berry</li><li>Peach Guava</li><li>Forest Berries</li>
            <li>Wicks</li><li>Wilderness Forest</li><li>Grape Slush</li>
          </ul>
        </div>
        <div class="footerCard">
          <span class="small">Model: Merryblade</span>
          <span class="count"></span>
        </div>
      </article>

      <!-- MODEL 2 -->
      <article class="card" data-model="ETS Dual Galaxy" data-meta="30000 puff • 5% • dual flavor" data-tags="peach apple mint blueberry raspberry strawberry watermelon passion cherry lemon lime aloe grape black mr razz cola skittles guava">
        <div class="thumb">
          <img src="https://wapujemy.com/wp-content/uploads/2025/04/wersja-2.png" alt="ETS Dual Galaxy" loading="lazy">
          <div class="badgeRow">
            <span class="badge accent">30000 puff</span>
            <span class="badge">5%</span>
            <span class="badge">Dual</span>
          </div>
        </div>
        <div class="content">
          <h3>ETS Dual Galaxy</h3>
          <p class="meta"><strong>Spec:</strong> 30000 puff • 5% • dual flavor</p>
          <ul class="flavors">
            <li>Juicy Peach / Double Apple</li>
            <li>Blackberry Gum / Fresh Mint Gum</li>
            <li>Blueberry Raspberry / Strawberry Ice</li>
            <li>Watermelon Ice / Triple Melon</li>
            <li>Passion Berry / Cherry Ice</li>
            <li>Lemon Lime / Pink Lemon</li>
            <li>Blueberry Sour Raspberry / Blackberry Ice</li>
            <li>Summer Dream / Aloe Grape</li>
            <li>Mr Black / Blue Razz Ice</li>
            <li>Apple Peach / Mango Peach</li>
            <li>Cherry Cola Ice / Watermelon Cherry</li>
            <li>Strawberry Pomegranate / Strawberry Kiwi Pomegranate</li>
            <li>Skittles / Orange Melon</li>
            <li>Kiwi Guava / Strawberry Kiwi</li>
            <li>Blueberry cherry cranberry / Strawberry Raspberry Cherry Ice</li>
          </ul>
        </div>
        <div class="footerCard">
          <span class="small">Model: ETS Dual Galaxy</span>
          <span class="count"></span>
        </div>
      </article>

      <!-- MODEL 3 -->
      <article class="card" data-model="MerryMi M-Mecha" data-meta="16000 puff • 3%" data-tags="watermelon strawberry kiwi peach cherry cactus lychee razz apple grape cola dragon fruit berries energy orange pineapple mojito mint blueberry vimto fanta lemon needle cranberry">
        <div class="thumb">
          <img src="https://vape444.com/cdn/shop/files/Merry-Mi-M-Mecha-16K-black-mint_022b8826-2473-47f8-a56b-e49df07b8579.jpg?v=1766859429" alt="MerryMi M-Mecha" loading="lazy">
          <div class="badgeRow">
            <span class="badge accent">16000 puff</span>
            <span class="badge">3%</span>
          </div>
        </div>
        <div class="content">
          <h3>MerryMi M-Mecha</h3>
          <p class="meta"><strong>Spec:</strong> 16000 puff • 3%</p>
          <ul class="flavors">
            <li>Watermelon Ice</li><li>Strawberry Kiwi</li><li>Pink Peach</li>
            <li>Black Cherry Lime</li><li>Cactus Candy</li><li>Lychee Ice</li>
            <li>Blue Razz Ice</li><li>Sour Apple</li><li>Grape Ice</li>
            <li>Cherry Cola</li><li>Dragon Fruit Ice</li><li>Mix Berries</li>
            <li>Red Energy Ice</li><li>Orange Ice Kiwi</li><li>Pineapple Orange Soda</li>
            <li>Kiwi Passion Fruit Guava</li><li>Pink Lemonade</li><li>Jagermeister Red Bull</li>
            <li>Miami Mint</li><li>Blueberry Watermelon</li><li>Mr Blue</li>
            <li>Prime Strawberry</li><li>Love66</li><li>Vimto</li>
            <li>Fanta</li><li>Sour Lemon Mojito</li><li>Pine Needle Berry</li>
            <li>Cranberry Lime</li><li>White Peach Berries</li><li>Sour Strawberry Daiquiri</li>
            <li>Dr. Pepper</li><li>Wicks</li><li>Peach Guava</li>
            <li>Grapefruit Refresher</li><li>Grape Berry</li>
          </ul>
        </div>
        <div class="footerCard">
          <span class="small">Model: MerryMi M-Mecha</span>
          <span class="count"></span>
        </div>
      </article>

      <!-- MODEL 5 -->
      <article class="card" data-model="MerryMi Mecha Pro" data-meta="35000 puff • 5%" data-tags="cactus peach berries summer watermelon razz energy blueberry cherry cranberry fanta vimto">
        <div class="thumb">
          <img src="https://vapemvps.com/cdn/shop/files/merry-mi-mecha-pro-20k-puffs-fanta-vapemvps.jpg?v=1763392696" alt="MerryMi Mecha Pro" loading="lazy">
          <div class="badgeRow">
            <span class="badge accent">35000 puff</span>
            <span class="badge">5%</span>
          </div>
        </div>
        <div class="content">
          <h3>MerryMi Mecha Pro</h3>
          <p class="meta"><strong>Spec:</strong> 35000 puff • 5%</p>
          <ul class="flavors">
            <li>Cactus Candy</li>
            <li>White Peach Berries</li>
            <li>Summer Blaze</li>
            <li>Watermelon Ice</li>
            <li>Blue Razz Ice</li>
            <li>Jager Red Energy</li>
            <li>Blueberry Cherry Cranberry</li>
            <li>Fanta</li>
            <li>Vimto</li>
          </ul>
        </div>
        <div class="footerCard">
          <span class="small">Model: MerryMi Mecha Pro</span>
          <span class="count"></span>
        </div>
      </article>

      <!-- MODEL 6 -->
      <article class="card" data-model="Airmez Fox 4in1" data-meta="120000 puff • 2% • 4 smaki" data-tags="strawberry raspberry kiwi ice peach mango watermelon pink lemonade passion mixed berries triple love cherry blueberry guava tropical lemon mojito grape dragonfruit energy">
        <div class="thumb">
          <img src="https://www.vapeandoando.com/cdn/shop/files/Airmez-Fox-3.jpg?v=1764637798" alt="Airmez Fox 4in1" loading="lazy">
          <div class="badgeRow">
            <span class="badge accent">120000 puff</span>
            <span class="badge">2%</span>
            <span class="badge">4in1</span>
          </div>
        </div>
        <div class="content">
          <h3>Airmez Fox 4in1</h3>
          <p class="meta"><strong>Spec:</strong> 120000 puff • 2% • 4 smaki</p>
          <ul class="flavors">
            <li>Strawberry Raspberry / Strawberry Kiwi / Strawberry Ice / Peach Mango Watermelon</li>
            <li>Pink Lemonade / Passion Kiss / Mixed Berries / Triple Berry</li>
            <li>Love 66 / Cherry / Blueberry On Ice / Kiwi Passion Fruit Guava</li>
            <li>Mango Peach / Tropical Fruit / Peach Ice / Sour Mango Pineapple</li>
            <li>Watermelon Ice / Raspberry Watermelon / Blueberry Raspberry / Strawberry Watermelon</li>
            <li>Peach Mango Watermelon / Blueberry Cherry / Watermelon Dragon Fruit / Passion Kiss</li>
            <li>Peach Ice / Pink Lemonade / Watermelon Ice / Dr Blue</li>
            <li>Grape Ice / Love 66 / Blueberry On Ice / Dragonfruit Ice</li>
            <li>Red Mojito / Love 66 / Mixed Berries / Strawberry Watermelon</li>
            <li>Cherry / Love 66 / Berry Lemonade / Grape Ice</li>
          </ul>
        </div>
        <div class="footerCard">
          <span class="small">Model: Airmez Fox 4in1</span>
          <span class="count"></span>
        </div>
      </article>

      <!-- MODEL 7 -->
      <article class="card" data-model="Tornado" data-meta="15000 puff • 5% / 2%" data-tags="kiwi passion fruit guava grape ice blueberry dragon mixed berry razz lemonade">
        <div class="thumb">
          <img src="https://www.randmvape-shop.net/cdn/shop/files/RandMTornado15000.png?v=1748017766&width=1080" alt="Tornado" loading="lazy">
          <div class="badgeRow">
            <span class="badge accent">15000 puff</span>
            <span class="badge">5% / 2%</span>
          </div>
        </div>
        <div class="content">
          <h3>Tornado</h3>
          <p class="meta"><strong>Spec:</strong> 15000 puff • 5% / 2%</p>
          <ul class="flavors">
            <li>Kiwi Passion Fruit Guava</li>
            <li>Grape Ice</li>
            <li>Blueberry On Ice</li>
            <li>Dragon Fruit</li>
            <li>Mixed Berry</li>
            <li>Blue Razz Lemonade</li>
          </ul>
        </div>
        <div class="footerCard">
          <span class="small">Model: Tornado</span>
          <span class="count"></span>
        </div>
      </article>

      <!-- MODEL 8 -->
      <article class="card" data-model="Fumot Tornado" data-meta="20000 puff • 5%" data-tags="blueberry raspberry hard candy strawberry kiwi peach pineapple orange skittles pear cotton jelly beans huckleberry watermelon mixed berry lychee melon cherry apple gummy bear mint cactus grape cola lemon blackcurrant mango grapefruit">
        <div class="thumb">
          <img src="https://static.24hvape.com/wp-content/uploads/2025/06/13121252/24h-vape-fumot-tornado-20000-20k-puffs-mixed-berry-654x690.jpg.webp" alt="Fumot Tornado" loading="lazy">
          <div class="badgeRow">
            <span class="badge accent">20000 puff</span>
            <span class="badge">5%</span>
          </div>
        </div>
        <div class="content">
          <h3>Fumot Tornado</h3>
          <p class="meta"><strong>Spec:</strong> 20000 puff • 5%</p>
          <ul class="flavors">
            <li>Blueberry Raspberry Hard Candy</li>
            <li>Strawberry Kiwi</li>
            <li>Peach Pineapple Orange</li>
            <li>Skittles</li>
            <li>Pear Ice</li>
            <li>Cotton Candy</li>
            <li>Jelly Beans</li>
            <li>Huckleberry</li>
            <li>Watermelon Ice</li>
            <li>Strawberry Watermelon</li>
            <li>Mixed Berry</li>
            <li>Lychee Hami Melon</li>
            <li>Cherry Lime</li>
            <li>Pineapple Lemon Green Apple</li>
            <li>Banana Cake</li>
            <li>Mr Blue</li>
            <li>Blueberry Raspberry</li>
            <li>Cherry Cola</li>
            <li>Kiwi Passion Fruit Guava</li>
            <li>Strawberry Raspberry Cherry Ice</li>
            <li>Cherry Berry</li>
            <li>Blueberry Sour Raspberry</li>
            <li>Peach Berry</li>
            <li>Blue Razz Gummy Bear</li>
            <li>Cool Mint</li>
            <li>Cactus Ice</li>
            <li>Red Grape Lime</li>
            <li>Cola Lemon</li>
            <li>Blackcurrant Apple</li>
            <li>Cactus Kiwi</li>
            <li>Cola Ice</li>
            <li>Mango Grape Ice</li>
            <li>Blueberry Cactus Ice</li>
            <li>Grape Kiwi</li>
            <li>Apple Grapefruit</li>
          </ul>
        </div>
        <div class="footerCard">
          <span class="small">Model: Fumot Tornado</span>
          <span class="count"></span>
        </div>
      </article>

      <!-- MODEL 9 -->
      <article class="card" data-model="Fumot Digital Monkey" data-meta="40000 puff • 5%" data-tags="banana strawberry watermelon blueberry raspberry black gummy ice peach pink lemonade mango grape lemon tropical rainbow cherry apple mint">
        <div class="thumb">
          <img src="https://wezbucha.org/wp-content/uploads/2025/09/mon3.jpeg" alt="Fumot Digital Monkey" loading="lazy">
          <div class="badgeRow">
            <span class="badge accent">40000 puff</span>
            <span class="badge">5%</span>
          </div>
        </div>
        <div class="content">
          <h3>Fumot Digital Monkey</h3>
          <p class="meta"><strong>Spec:</strong> 40000 puff • 5%</p>
          <ul class="flavors">
            <li>Banana Ice</li>
            <li>Strawberry Watermelon</li>
            <li>Blueberry Raspberry</li>
            <li>Black Ice</li>
            <li>White Gummy Ice</li>
            <li>Watermelon Ice</li>
            <li>Juicy Peach Ice</li>
            <li>Pink Lemonade</li>
            <li>Strawberry Mango</li>
            <li>Peach Mango Watermelon</li>
            <li>Grape Lemon</li>
            <li>Tropical Rainbow Blast</li>
            <li>Cherry Bomb</li>
            <li>Strawberry Mint Candy</li>
            <li>Double Apple</li>
          </ul>
        </div>
        <div class="footerCard">
          <span class="small">Model: Fumot Digital Monkey</span>
          <span class="count"></span>
        </div>
      </article>

      <!-- MODEL 10 -->
      <article class="card" data-model="Movkin Tycoon" data-meta="40000 puff • 5% • 3 tryby ICE & 3 tryby nikotyny" data-tags="watermelon strawberry blueberry blackberry mint raspberry peach lime mango pineapple razz apple cherry banana orange grape lemon">
        <div class="thumb">
          <img src="https://szfumotvape.com/wp-content/uploads/2025/10/fumot-vape-heating-cores.webp" alt="Movkin Tycoon" loading="lazy">
          <div class="badgeRow">
            <span class="badge accent">40000 puff</span>
            <span class="badge">5%</span>
            <span class="badge">Tryby ICE</span>
          </div>
        </div>
        <div class="content">
          <h3>Movkin Tycoon</h3>
          <p class="meta"><strong>Spec:</strong> 40000 puff • 5% • 3 tryby ICE &amp; 3 tryby nikotyny</p>
          <ul class="flavors">
            <li>Watermelon Strawberry</li>
            <li>Blueberry Blackberry</li>
            <li>Miami Mint</li>
            <li>Raspberry Peach Lime</li>
            <li>Sour Mango Pineapple</li>
            <li>Blue Razz Ice</li>
            <li>Sour Apple</li>
            <li>Berry Cherry Lime</li>
            <li>Watermelon Ice</li>
            <li>Blackcurrant Strawberry</li>
            <li>Banana Taffy Freze</li>
            <li>Orange Fucking Fab</li>
            <li>Grape Lemon</li>
            <li>Peachy Mango Watermelon</li>
            <li>Strawberry B-Pop</li>
            <li>Juicy Peach</li>
          </ul>
        </div>
        <div class="footerCard">
          <span class="small">Model: Movkin Tycoon</span>
          <span class="count"></span>
        </div>
      </article>

      <!-- MODEL 11 -->
      <article class="card" data-model="RandM Tornado 60k 3in1" data-meta="60000 puff • 5% • 3 smaki" data-tags="watermelon strawberry energy kiwi lemon mixed berries peach apple lady killer mango banana razz grape cherry sour">
        <div class="thumb">
          <img src="https://www.deeppouch.com/wp-content/uploads/2026/01/RahdM-Tornado-3in1-60000-Puffs.webp" alt="RandM Tornado 60k 3in1" loading="lazy">
          <div class="badgeRow">
            <span class="badge accent">60000 puff</span>
            <span class="badge">5%</span>
            <span class="badge">3in1</span>
          </div>
        </div>
        <div class="content">
          <h3>RandM Tornado 60k 3in1</h3>
          <p class="meta"><strong>Spec:</strong> 60000 puff • 5% • 3 smaki</p>
          <ul class="flavors">
            <li>Watermelon Ice / Strawberry Red Bull / Strawberry Kiwi</li>
            <li>Strawberry Watermelon / Blueberry on Ice / Kiwi Lemon</li>
            <li>Mixed Berries / Peach Apple Ice / Lady Killer</li>
            <li>Mango Ice / Banana Ice / Blue Razz Lemonade</li>
            <li>Peach Mango Pineapple / Strawberry Raspberry Ice / Triple Mango</li>
            <li>Strawberry Grape / Peach Mango / Ice Pop</li>
            <li>Strawberry Ice / Sour Apple / Blueberry Raspberry</li>
            <li>Grape Ice / Cherry Ice / Blue Sour Raspberry</li>
            <li>Peach Ice / Red Apple / Blueberry Cherry Cranberry</li>
            <li>Kiwi Passion Fruit Guava / Green Apple / Juicy Peach</li>
          </ul>
        </div>
        <div class="footerCard">
          <span class="small">Model: RandM Tornado 60k 3in1</span>
          <span class="count"></span>
        </div>
      </article>

      <!-- MODEL 12 -->
      <article class="card" data-model="WGA Crystal Plus" data-meta="20000 puff • 5% • 2 smaki" data-tags="blue razz gummy raspberry strawberry ice blueberry cherry cranberry lemon lime sherbet cola heisenberg pinkman watermelon mr pink ice cream banana orange">
        <div class="thumb">
          <img src="https://wezbucha.org/wp-content/uploads/2024/08/wga-crystal-plus-20000-vape_web-11_1024x1024.webp" alt="WGA Crystal Plus" loading="lazy">
          <div class="badgeRow">
            <span class="badge accent">20000 puff</span>
            <span class="badge">5%</span>
            <span class="badge">2 smaki</span>
          </div>
        </div>
        <div class="content">
          <h3>WGA Crystal Plus</h3>
          <p class="meta"><strong>Spec:</strong> 20000 puff • 5% • 2 smaki</p>
          <ul class="flavors">
            <li>Blue Razz Gummy / Blue Raspberry</li>
            <li>Strawberry Raspberry Ice / Blueberry Cherry Cranberry</li>
            <li>Lemon Lime / Lemonade Sherbet Ice</li>
            <li>Blueberry Ice / Strawberry Ice</li>
            <li>Blue Razz Lemonade / Cola Lemon</li>
            <li>Heisenberg / Pinkman</li>
            <li>Watermelon Cherry / Mr Pink</li>
            <li>Strawberry Ice Cream / Strawberry Banana</li>
            <li>Blueberry Ice Pop / Strawberry Ice Pop</li>
            <li>Cherry Ice / Orange Ice</li>
          </ul>
        </div>
        <div class="footerCard">
          <span class="small">Model: WGA Crystal Plus</span>
          <span class="count"></span>
        </div>
      </article>

    </section>
  </main>

  <footer class="site">
    © 2026 • Katalog jednorazowych e-papierosów • 18+
  </footer>

  <script>
    // Age gate
    function acceptAge(){
      localStorage.setItem("ageAccepted","yes");
      document.getElementById("ageOverlay").classList.add("hidden");
    }
    function declineAge(){
      // prosto i czytelnie: wróć na pustą stronę / zamknij (przeglądarka i tak ogranicza)
      window.location.href = "about:blank";
    }
    if(localStorage.getItem("ageAccepted") === "yes"){
      document.getElementById("ageOverlay").classList.add("hidden");
    }

    // Filtering / search
    const cards = Array.from(document.querySelectorAll(".card"));
    const searchInput = document.getElementById("searchInput");
    const modelFilter = document.getElementById("modelFilter");
    const visibleCount = document.getElementById("visibleCount");
    const totalCount = document.getElementById("totalCount");
    const chips = Array.from(document.querySelectorAll(".chip"));

    // Fill model dropdown
    const models = [...new Set(cards.map(c => c.dataset.model))].sort((a,b)=>a.localeCompare(b,'pl'));
    models.forEach(m=>{
      const opt = document.createElement("option");
      opt.value = m;
      opt.textContent = m;
      modelFilter.appendChild(opt);
    });

    // Flavor count badges
    cards.forEach(card=>{
      const countEl = card.querySelector(".count");
      const list = card.querySelectorAll(".flavors li").length;
      countEl.textContent = `${list} smaków`;
    });

    totalCount.textContent = cards.length;

    let activeChip = null;

    function normalize(s){
      return (s || "").toLowerCase().trim();
    }

    function applyFilters(){
      const q = normalize(searchInput.value);
      const model = modelFilter.value;
      const chip = activeChip;

      let shown = 0;

      cards.forEach(card=>{
        const modelName = normalize(card.dataset.model);
        const meta = normalize(card.dataset.meta);
        const tags = normalize(card.dataset.tags);
        const flavorsText = normalize(card.querySelector(".flavors")?.innerText);

        const inModel = (model === "all") || (card.dataset.model === model);
        const inSearch = !q || (
          modelName.includes(q) ||
          meta.includes(q) ||
          tags.includes(q) ||
          flavorsText.includes(q)
        );

        const inChip = !chip || (tags.includes(chip) || flavorsText.includes(chip));

        const ok = inModel && inSearch && inChip;
        card.classList.toggle("hidden", !ok);
        if(ok) shown++;
      });

      visibleCount.textContent = shown;
    }

    // Chip toggle (single-active)
    chips.forEach(ch=>{
      ch.addEventListener("click", ()=>{
        const value = ch.dataset.chip;
        const isActive = ch.classList.contains("active");
        chips.forEach(x=>x.classList.remove("active"));

        if(isActive){
          activeChip = null;
        }else{
          ch.classList.add("active");
          activeChip = value;
        }
        applyFilters();
      });
    });

    searchInput.addEventListener("input", applyFilters);
    modelFilter.addEventListener("change", applyFilters);

    // initial
    applyFilters();
  </script>
</body>
</html>
