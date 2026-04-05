<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Para ti 🌸</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,600;1,400&family=Lora:ital,wght@0,400;1,400&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --rose:    #f4a7b9;
      --blush:   #fce4ec;
      --peach:   #ffd6c0;
      --lavender:#e8d5f5;
      --cream:   #fff8f0;
      --sage:    #c8dfc8;
      --text:    #5a3e4b;
      --muted:   #9e7b8a;
      --gold:    #d4a0a7;
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    body {
      background: var(--cream);
      font-family: 'Lora', serif;
      color: var(--text);
      min-height: 100vh;
      overflow-x: hidden;
      position: relative;
    }

    /* ── Floating petals background ── */
    .petals-bg {
      position: fixed;
      inset: 0;
      pointer-events: none;
      z-index: 0;
      overflow: hidden;
    }
    .petal {
      position: absolute;
      font-size: 1.4rem;
      opacity: 0;
      animation: floatPetal linear infinite;
    }
    @keyframes floatPetal {
      0%   { transform: translateY(-60px) rotate(0deg);   opacity: 0; }
      10%  { opacity: 0.55; }
      90%  { opacity: 0.35; }
      100% { transform: translateY(110vh) rotate(360deg); opacity: 0; }
    }

    /* ── Wrapper ── */
    .wrapper {
      position: relative;
      z-index: 1;
      max-width: 680px;
      margin: 0 auto;
      padding: 60px 24px 80px;
    }

    /* ── Hero header ── */
    .hero {
      text-align: center;
      margin-bottom: 56px;
      animation: fadeDown .9s ease both;
    }
    @keyframes fadeDown {
      from { opacity: 0; transform: translateY(-24px); }
      to   { opacity: 1; transform: translateY(0); }
    }
    .hero-deco {
      font-size: 2.6rem;
      letter-spacing: .18em;
      display: block;
      margin-bottom: 8px;
      animation: fadeDown .9s .15s ease both;
    }
    .hero h1 {
      font-family: 'Playfair Display', serif;
      font-size: clamp(2rem, 6vw, 3.2rem);
      font-weight: 400;
      font-style: italic;
      color: var(--text);
      line-height: 1.15;
      animation: fadeDown .9s .25s ease both;
    }
    .hero-sub {
      margin-top: 14px;
      font-size: .95rem;
      color: var(--muted);
      letter-spacing: .06em;
      animation: fadeDown .9s .35s ease both;
    }
    .divider {
      margin: 28px auto 0;
      width: 80px;
      height: 2px;
      background: linear-gradient(90deg, transparent, var(--rose), transparent);
      border-radius: 2px;
      animation: fadeDown .9s .45s ease both;
    }

    /* ── Button list ── */
    .btn-list {
      display: flex;
      flex-direction: column;
      gap: 18px;
    }

    /* ── Each envelope button ── */
    .envelope-btn {
      position: relative;
      background: linear-gradient(135deg, #fff0f5 0%, #fdf4ff 100%);
      border: 1.5px solid #f0c8d4;
      border-radius: 18px;
      padding: 22px 28px;
      cursor: pointer;
      text-align: left;
      transition: transform .22s ease, box-shadow .22s ease, border-color .22s ease;
      box-shadow: 0 2px 16px rgba(244,167,185,.18);
      animation: fadeUp .7s ease both;
      overflow: hidden;
    }
    .envelope-btn:nth-child(1) { animation-delay: .55s; }
    .envelope-btn:nth-child(2) { animation-delay: .68s; }
    .envelope-btn:nth-child(3) { animation-delay: .81s; }
    .envelope-btn:nth-child(4) { animation-delay: .94s; }
    .envelope-btn:nth-child(5) { animation-delay:1.07s; }

    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(30px); }
      to   { opacity: 1; transform: translateY(0); }
    }
    .envelope-btn::before {
      content: '';
      position: absolute;
      inset: 0;
      background: linear-gradient(135deg, rgba(252,228,236,.5), rgba(232,213,245,.4));
      opacity: 0;
      transition: opacity .25s;
      border-radius: inherit;
    }
    .envelope-btn:hover { transform: translateY(-3px); box-shadow: 0 8px 32px rgba(244,167,185,.30); border-color: var(--rose); }
    .envelope-btn:hover::before { opacity: 1; }
    .envelope-btn:active { transform: translateY(0) scale(.98); }

    .btn-inner {
      display: flex;
      align-items: center;
      gap: 18px;
      position: relative;
      z-index: 1;
    }
    .btn-icon {
      font-size: 2rem;
      flex-shrink: 0;
      transition: transform .3s ease;
    }
    .envelope-btn:hover .btn-icon { transform: scale(1.15) rotate(-6deg); }
    .btn-label {
      font-family: 'Playfair Display', serif;
      font-size: 1.15rem;
      font-style: italic;
      color: var(--text);
    }
    .btn-hint {
      font-family: 'Lora', serif;
      font-size: .78rem;
      color: var(--muted);
      margin-top: 3px;
      font-style: normal;
    }
    .btn-arrow {
      margin-left: auto;
      font-size: 1.1rem;
      color: var(--rose);
      transition: transform .25s;
      flex-shrink: 0;
    }
    .envelope-btn:hover .btn-arrow { transform: translateX(5px); }

    /* ── Modal overlay ── */
    .overlay {
      position: fixed;
      inset: 0;
      background: rgba(90,62,75,.45);
      backdrop-filter: blur(6px);
      z-index: 100;
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 20px;
      opacity: 0;
      pointer-events: none;
      transition: opacity .35s ease;
    }
    .overlay.open {
      opacity: 1;
      pointer-events: all;
    }

    /* ── Letter card ── */
    .letter-card {
      background: #fff8f2;
      border-radius: 24px;
      max-width: 560px;
      width: 100%;
      max-height: 90vh;
      overflow-y: auto;
      box-shadow: 0 24px 80px rgba(90,62,75,.25);
      position: relative;
      transform: scale(.88) translateY(30px);
      transition: transform .4s cubic-bezier(.34,1.56,.64,1);
      padding: 48px 40px 40px;
      border: 1.5px solid #f5d5e0;
    }
    .overlay.open .letter-card {
      transform: scale(1) translateY(0);
    }

    /* scrollbar inside card */
    .letter-card::-webkit-scrollbar { width: 5px; }
    .letter-card::-webkit-scrollbar-track { background: transparent; }
    .letter-card::-webkit-scrollbar-thumb { background: var(--rose); border-radius: 10px; }

    /* corner deco */
    .letter-card::before,
    .letter-card::after {
      content: '✿';
      position: absolute;
      color: var(--rose);
      opacity: .5;
      font-size: 1.3rem;
    }
    .letter-card::before { top: 14px; left: 18px; }
    .letter-card::after  { bottom: 14px; right: 18px; transform: rotate(180deg); }

    .letter-title {
      font-family: 'Playfair Display', serif;
      font-size: 1.7rem;
      font-style: italic;
      text-align: center;
      margin-bottom: 28px;
      color: var(--text);
      position: relative;
    }
    .letter-title::after {
      content: '';
      display: block;
      margin: 10px auto 0;
      width: 60px;
      height: 2px;
      background: linear-gradient(90deg, transparent, var(--rose), transparent);
      border-radius: 2px;
    }

    .letter-body {
      font-size: 1rem;
      line-height: 1.85;
      white-space: pre-wrap;
      color: var(--text);
    }

    .letter-close {
      display: block;
      margin: 36px auto 0;
      background: linear-gradient(135deg, var(--rose), var(--gold));
      color: #fff;
      border: none;
      border-radius: 50px;
      padding: 13px 38px;
      font-family: 'Lora', serif;
      font-size: .95rem;
      cursor: pointer;
      letter-spacing: .04em;
      box-shadow: 0 4px 18px rgba(244,167,185,.4);
      transition: transform .2s, box-shadow .2s;
    }
    .letter-close:hover { transform: scale(1.04); box-shadow: 0 8px 28px rgba(244,167,185,.5); }

    /* ── Floating hearts burst on click ── */
    .burst-heart {
      position: fixed;
      pointer-events: none;
      font-size: 1.4rem;
      z-index: 200;
      animation: burstAnim .9s ease forwards;
    }
    @keyframes burstAnim {
      0%   { opacity: 1;   transform: translate(0,0) scale(.6); }
      100% { opacity: 0;   transform: translate(var(--dx), var(--dy)) scale(1.4); }
    }

    /* ── Footer ── */
    .footer {
      text-align: center;
      margin-top: 56px;
      font-size: .85rem;
      color: var(--muted);
      letter-spacing: .05em;
      animation: fadeUp .7s 1.3s ease both;
      opacity: 0;
    }
  </style>
</head>
<body>

<!-- Petal rain -->
<div class="petals-bg" id="petalsBg"></div>

<div class="wrapper">
  <header class="hero">
    <span class="hero-deco">🌸 ✦ 🌸</span>
    <h1>Para mi niña hermosa</h1>
    <p class="hero-sub">Abre cada carta con cariño</p>
    <div class="divider"></div>
  </header>

  <div class="btn-list">

    <button class="envelope-btn" onclick="openCard(0, event)">
      <div class="btn-inner">
        <span class="btn-icon">💌</span>
        <div>
          <div class="btn-label">Contigo</div>
          <div class="btn-hint">Toca para leer</div>
        </div>
        <span class="btn-arrow">→</span>
      </div>
    </button>

    <button class="envelope-btn" onclick="openCard(1, event)">
      <div class="btn-inner">
        <span class="btn-icon">🌷</span>
        <div>
          <div class="btn-label">Tú</div>
          <div class="btn-hint">Toca para leer</div>
        </div>
        <span class="btn-arrow">→</span>
      </div>
    </button>

    <button class="envelope-btn" onclick="openCard(2, event)">
      <div class="btn-inner">
        <span class="btn-icon">✨</span>
        <div>
          <div class="btn-label">El destino</div>
          <div class="btn-hint">Toca para leer</div>
        </div>
        <span class="btn-arrow">→</span>
      </div>
    </button>

    <button class="envelope-btn" onclick="openCard(3, event)">
      <div class="btn-inner">
        <span class="btn-icon">🌸</span>
        <div>
          <div class="btn-label">TE AMO</div>
          <div class="btn-hint">Toca para leer</div>
        </div>
        <span class="btn-arrow">→</span>
      </div>
    </button>

  </div>

  <p class="footer">hecho con todo el amor del mundo</p>
</div>

<!-- Modal -->
<div class="overlay" id="overlay" onclick="closeOnBg(event)">
  <div class="letter-card" id="letterCard">
    <div class="letter-title" id="cardTitle"></div>
    <div class="letter-body"  id="cardBody"></div>
    <button class="letter-close" onclick="closeCard()">Cerrar carta 🌸</button>
  </div>
</div>

<script>
  /* ── Letter data ── */
  const cards = [
    {
      title: "Contigo",
      body: `Mi niña hermosa ya son 5 meses de estar juntotes y la verdad es que jamas pense poder tener o merecer algo tan bonito como lo que tu me das, me salvaste, me sacaste de un agujero muy profundo y trajiste el sol a mis dias mas lluviosos dejando siempre un precioso arcoiris, no se a quien o a que agradecerle por haberme enviado a alguien como tu, tan hermosa, atenta, dedicada, trabajadora y lo mas importante igual de loca que yo, estos 5 meses solo los puedo describir como magicos, haces que el simple hecho de pensar en ti traiga una sonrisa a mi rostro y el hablarte provoque mariposas en mi estomago gracias por haberme escogido y prometo escogerte hoy y siempre por esta vida y todas las que siguen


Te amo`
    },
    {
      title: "Tú",
      body: `Sabes siempre dije que eres todo lo bueno y bonito de este mundo pero ¿que es todo lo bueno y bonito de este mundo? Pues dejame decirte todo lo que te describe y identifica en mi mente y corazon

Eres la chica más fokin 
perfecta, dulce, cálida, amable, graciosa, guapa, hermosa, linda, preciosa, habladora, bella, increible, chistosa, sensible, carismática, inteligente, honesta, simpática, empatica, divertida, encantadora, apasionada, considerada, generosa, amistosa, interesante, sencilla, talentosa, creativa, cariñosa, confiable, graciosa, brillante, maravillosa, noble, romántica, chillona, auténtica, alegre, fantástica, increíble, genial, atenta, encantadora, espectacular, extraordinaria, excepcional, feliz, leal, única, apasionada, adorable, magnífica, fabulosa, atractiva, grandiosa, divina, perfecta y por eso

Te amo`
    },
    {
      title: "El destino",
      body: `Sabes amor yo jamas eh creido en cosas o poderes mas alla pero no hay otra forma de explicar lo que genero esta hermosa relacion y conexion que tenemos mas que con el destino, quien iba a decir que un tonto intento de un tonto niño de secundaria tendría un efecto en cadena tan grande como para llevarme a lo que ahora seria mi mundo entero, sinceramente no siento que todo esto sea una simple coincidencia ya que conectamos tan bien, tan rapido y de manera tan perfecta que me hacen sentir que siempre debiste ser, eres y seras tu la unica en mi vida y al parecer yo no soy el unico que piensa asi ya que tu misma me lo dijiste un dia, tambien piensas que todo este tiempo tu corazon me estuvo esperando y por esa reaccion tan hermosa

Te amo`
    },
    {
      title: "TE AMO",
      body: `No se cuánto tiempo me tome hacer todo esto pero espero tenerlo listo para cuando ya hayamos cumplido los 5 mesesotes y si no pues te pido perdon de rodillas y te lo compensare con unos abrazotes y unos besotes pero creo que con esto ya te eh dicho la mayoria de cosas que mi corazon y mente siempre repasan, asi que ya lo sabes mi niña hermosa, te amo de una manera que preocuparia a un psiquiatra, te amo de una manera que un matematico jamas podria cuantificar, te amo de una manera que un filosofo jamas podria imaginar, te amo de una manera que un poeta jamas podria plasmar, te amo mas que la inmensidad del univero observable, te ame ayer, te amo hoy y te amare mañana, simplemente 

Te amo`
    },

  ];

  /* ── Petal rain ── */
  const symbols = ['🌸','🌺','✿','❀','🌷','💮'];
  const bg = document.getElementById('petalsBg');
  for (let i = 0; i < 22; i++) {
    const p = document.createElement('span');
    p.classList.add('petal');
    p.textContent = symbols[Math.floor(Math.random() * symbols.length)];
    p.style.left      = Math.random() * 100 + 'vw';
    p.style.fontSize  = (.8 + Math.random() * .9) + 'rem';
    p.style.animationDuration  = (9 + Math.random() * 14) + 's';
    p.style.animationDelay     = (Math.random() * 12) + 's';
    bg.appendChild(p);
  }

  /* ── Open / close modal ── */
  const overlay    = document.getElementById('overlay');
  const cardTitle  = document.getElementById('cardTitle');
  const cardBody   = document.getElementById('cardBody');
  const letterCard = document.getElementById('letterCard');

  function openCard(index, e) {
    spawnHearts(e.clientX, e.clientY);
    cardTitle.textContent = cards[index].title;
    cardBody.textContent  = cards[index].body;
    letterCard.scrollTop  = 0;
    overlay.classList.add('open');
  }

  function closeCard() { overlay.classList.remove('open'); }
  function closeOnBg(e) { if (e.target === overlay) closeCard(); }

  /* ── Heart burst ── */
  function spawnHearts(cx, cy) {
    const hearts = ['💕','💖','🌸','✨','💗'];
    for (let i = 0; i < 10; i++) {
      const h = document.createElement('span');
      h.classList.add('burst-heart');
      h.textContent = hearts[Math.floor(Math.random() * hearts.length)];
      const angle = Math.random() * 2 * Math.PI;
      const dist  = 60 + Math.random() * 90;
      h.style.left = cx + 'px';
      h.style.top  = cy + 'px';
      h.style.setProperty('--dx', Math.cos(angle) * dist + 'px');
      h.style.setProperty('--dy', Math.sin(angle) * dist + 'px');
      h.style.animationDelay = Math.random() * .15 + 's';
      document.body.appendChild(h);
      setTimeout(() => h.remove(), 1100);
    }
  }
</script>
</body>
</html>
