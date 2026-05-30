<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Para ti 🌸</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,600;1,400&family=Lora:ital,wght@0,400;1,400&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --rose:  #f4a7b9;
      --cream: #fff8f0;
      --text:  #5a3e4b;
      --muted: #9e7b8a;
      --gold:  #d4a0a7;
    }
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    body {
      background: var(--cream);
      font-family: 'Lora', serif;
      color: var(--text);
      min-height: 100vh;
      overflow-x: hidden;
      transition: background .6s;
    }
    body.blue-mode { background: #e8f4fd; }

    /* Petals */
    .petals-bg { position: fixed; inset: 0; pointer-events: none; z-index: 0; overflow: hidden; }
    .petal { position: absolute; opacity: 0; animation: floatPetal linear infinite; }
    @keyframes floatPetal {
      0%   { transform: translateY(-60px) rotate(0deg); opacity: 0; }
      10%  { opacity: 0.5; }
      90%  { opacity: 0.3; }
      100% { transform: translateY(110vh) rotate(360deg); opacity: 0; }
    }

    /* Wrapper */
    .wrapper { position: relative; z-index: 1; max-width: 680px; margin: 0 auto; padding: 60px 24px 80px; }

    /* Hero */
    .hero { text-align: center; margin-bottom: 56px; }
    .hero-deco { font-size: 2.4rem; letter-spacing: .18em; display: block; margin-bottom: 8px; }
    .hero h1 { font-family: 'Playfair Display', serif; font-size: clamp(2rem,6vw,3.2rem); font-weight: 400; font-style: italic; line-height: 1.15; }
    .hero-sub { margin-top: 14px; font-size: .95rem; color: var(--muted); letter-spacing: .06em; }
    .divider { margin: 28px auto 0; width: 80px; height: 2px; background: linear-gradient(90deg,transparent,var(--rose),transparent); border-radius: 2px; }

    /* Button list */
    .btn-list { display: flex; flex-direction: column; gap: 18px; }

    /* Card button */
    .card-btn {
      width: 100%;
      background: linear-gradient(135deg, #fff0f5, #fdf4ff);
      border: 1.5px solid #f0c8d4;
      border-radius: 18px;
      padding: 22px 28px;
      cursor: pointer;
      text-align: left;
      transition: transform .22s, box-shadow .22s, border-color .22s;
      box-shadow: 0 2px 16px rgba(244,167,185,.18);
    }
    .card-btn:hover { transform: translateY(-3px); box-shadow: 0 8px 32px rgba(244,167,185,.3); border-color: var(--rose); }
    .card-btn:active { transform: scale(.98); }
    .card-btn.octo { background: linear-gradient(135deg,#c8e6f8,#b0d8f5); border-color: #5ba3d0; }
    .card-btn.octo:hover { border-color: #2a6fa8; box-shadow: 0 8px 32px rgba(91,163,208,.3); }

    .btn-inner { display: flex; align-items: center; gap: 18px; }
    .btn-icon { font-size: 2rem; flex-shrink: 0; transition: transform .3s; }
    .card-btn:hover .btn-icon { transform: scale(1.15) rotate(-6deg); }
    .btn-label { font-family: 'Playfair Display', serif; font-size: 1.15rem; font-style: italic; color: var(--text); }
    .btn-hint { font-size: .78rem; color: var(--muted); margin-top: 3px; }
    .btn-arrow { margin-left: auto; font-size: 1.1rem; color: var(--rose); transition: transform .25s; flex-shrink: 0; }
    .card-btn:hover .btn-arrow { transform: translateX(5px); }
    .card-btn.octo .btn-arrow { color: #5ba3d0; }

    /* Overlay */
    .overlay {
      position: fixed; inset: 0;
      background: rgba(90,62,75,.45);
      backdrop-filter: blur(6px);
      z-index: 200;
      display: flex; align-items: center; justify-content: center;
      padding: 20px;
      opacity: 0; pointer-events: none;
      transition: opacity .35s;
    }
    .overlay.open { opacity: 1; pointer-events: all; }
    .overlay.blue-overlay { background: rgba(10,40,80,.55); }

    /* Octo layer */
    .octo-layer { position: fixed; inset: 0; pointer-events: none; z-index: 201; overflow: hidden; }
    .octo-float { position: absolute; opacity: 0; animation: floatPetal linear infinite; pointer-events: none; }

    /* Letter card */
    .letter-card {
      background: #fff8f2;
      border-radius: 24px;
      max-width: 560px; width: 100%;
      max-height: 90vh; overflow-y: auto;
      box-shadow: 0 24px 80px rgba(90,62,75,.25);
      position: relative; z-index: 202;
      transform: scale(.88) translateY(30px);
      transition: transform .4s cubic-bezier(.34,1.56,.64,1);
      padding: 48px 40px 40px;
      border: 1.5px solid #f5d5e0;
    }
    .overlay.open .letter-card { transform: scale(1) translateY(0); }
    .letter-card.blue { background: #f0f8ff; border-color: #90c4e8; }

    .letter-card::-webkit-scrollbar { width: 5px; }
    .letter-card::-webkit-scrollbar-thumb { background: var(--rose); border-radius: 10px; }
    .letter-card.blue::-webkit-scrollbar-thumb { background: #5ba3d0; }

    .letter-card::before, .letter-card::after { content: '✿'; position: absolute; color: var(--rose); opacity: .5; font-size: 1.3rem; }
    .letter-card::before { top: 14px; left: 18px; }
    .letter-card::after  { bottom: 14px; right: 18px; transform: rotate(180deg); }
    .letter-card.blue::before, .letter-card.blue::after { color: #5ba3d0; }

    .letter-title { font-family: 'Playfair Display', serif; font-size: 1.7rem; font-style: italic; text-align: center; margin-bottom: 28px; color: var(--text); }
    .letter-title::after { content: ''; display: block; margin: 10px auto 0; width: 60px; height: 2px; background: linear-gradient(90deg,transparent,var(--rose),transparent); border-radius: 2px; }
    .letter-card.blue .letter-title { color: #1a3a5c; }
    .letter-card.blue .letter-title::after { background: linear-gradient(90deg,transparent,#5ba3d0,transparent); }

    .letter-body { font-size: 1rem; line-height: 1.85; white-space: pre-wrap; color: var(--text); }
    .letter-card.blue .letter-body { color: #1a3a5c; }

    /* Music banner */
    .music-banner {
      display: flex; margin-top: 28px; text-decoration: none;
      background: linear-gradient(135deg,rgba(91,163,208,.15),rgba(42,111,168,.2));
      border: 1.5px solid rgba(91,163,208,.45);
      border-radius: 14px; padding: 14px 20px;
      align-items: center; gap: 14px;
      transition: transform .2s, box-shadow .2s, background .2s;
    }
    .music-banner:hover { transform: translateY(-2px); box-shadow: 0 6px 24px rgba(91,163,208,.3); background: linear-gradient(135deg,rgba(91,163,208,.25),rgba(42,111,168,.3)); }
    .music-banner-icon { font-size: 1.8rem; flex-shrink: 0; animation: pulse 1.8s ease-in-out infinite; }
    @keyframes pulse { 0%,100%{transform:scale(1)} 50%{transform:scale(1.18)} }
    .music-banner-title { font-family: 'Playfair Display', serif; font-size: .95rem; font-style: italic; color: #1a3a5c; }
    .music-banner-sub { font-size: .75rem; color: #4a7fa5; margin-top: 3px; }
    .music-banner-arrow { font-size: 1rem; color: #5ba3d0; margin-left: auto; transition: transform .2s; }
    .music-banner:hover .music-banner-arrow { transform: translateX(4px); }

    /* Close button */
    .letter-close {
      display: block; margin: 32px auto 0;
      background: linear-gradient(135deg,var(--rose),var(--gold));
      color: #fff; border: none; border-radius: 50px;
      padding: 13px 38px; font-family: 'Lora', serif; font-size: .95rem;
      cursor: pointer; letter-spacing: .04em;
      box-shadow: 0 4px 18px rgba(244,167,185,.4);
      transition: transform .2s, box-shadow .2s;
    }
    .letter-close:hover { transform: scale(1.04); box-shadow: 0 8px 28px rgba(244,167,185,.5); }
    .letter-card.blue .letter-close { background: linear-gradient(135deg,#5ba3d0,#2a6fa8); }

    /* Footer */
    .footer { text-align: center; margin-top: 56px; font-size: .85rem; color: var(--muted); letter-spacing: .05em; }

    /* Animations */
    @keyframes fadeDown { from{opacity:0;transform:translateY(-24px)} to{opacity:1;transform:translateY(0)} }
    @keyframes fadeUp   { from{opacity:0;transform:translateY(30px)}  to{opacity:1;transform:translateY(0)} }
    .hero { animation: fadeDown .9s ease both; }
  </style>
</head>
<body>

<div class="petals-bg" id="petalsBg"></div>

<div class="wrapper">
  <header class="hero">
    <span class="hero-deco">🌸 ✦ 🌸</span>
    <h1>Para mi niña hermosa</h1>
    <p class="hero-sub">Abre cada carta con cariño</p>
    <div class="divider"></div>
  </header>

  <div class="btn-list" id="btnList">
    <button class="card-btn" data-card="0">
      <div class="btn-inner">
        <span class="btn-icon">💌</span>
        <div><div class="btn-label">Contigo</div><div class="btn-hint">Toca para leer</div></div>
        <span class="btn-arrow">→</span>
      </div>
    </button>
    <button class="card-btn" data-card="1">
      <div class="btn-inner">
        <span class="btn-icon">🌷</span>
        <div><div class="btn-label">Tú</div><div class="btn-hint">Toca para leer</div></div>
        <span class="btn-arrow">→</span>
      </div>
    </button>
    <button class="card-btn" data-card="2">
      <div class="btn-inner">
        <span class="btn-icon">✨</span>
        <div><div class="btn-label">El destino</div><div class="btn-hint">Toca para leer</div></div>
        <span class="btn-arrow">→</span>
      </div>
    </button>
    <button class="card-btn" data-card="3">
      <div class="btn-inner">
        <span class="btn-icon">🌸</span>
        <div><div class="btn-label">TE AMO</div><div class="btn-hint">Toca para leer</div></div>
        <span class="btn-arrow">→</span>
      </div>
    </button>
    <button class="card-btn" data-card="4">
      <div class="btn-inner">
        <span class="btn-icon">🦋</span>
        <div><div class="btn-label">Recuerdos</div><div class="btn-hint">Toca para leer</div></div>
        <span class="btn-arrow">→</span>
      </div>
    </button>
    <button class="card-btn octo" data-card="5">
      <div class="btn-inner">
        <span class="btn-icon">🐙</span>
        <div><div class="btn-label">Mi pulpito azul</div><div class="btn-hint">Toca para leer</div></div>
        <span class="btn-arrow">→</span>
      </div>
    </button>
  </div>

  <p class="footer">hecho con todo el amor del mundo </p>
</div>

<!-- Single reusable overlay -->
<div class="overlay" id="overlay">
  <div class="letter-card" id="letterCard">
    <div class="letter-title" id="cardTitle"></div>
    <div class="letter-body"  id="cardBody"></div>
    <a class="music-banner" id="musicBanner" href="https://youtu.be/tKdhg9P0ZIQ?si=RS8qxozf9V8p9Se_" target="_blank" rel="noopener">
      <span class="music-banner-icon">🎵</span>
      <div>
        <div class="music-banner-title">Escucha nuestra canción</div>
        <div class="music-banner-sub">Tú Sí Eres Real — toca para abrir</div>
      </div>
      <span class="music-banner-arrow">→</span>
    </a>
    <button class="letter-close" id="closeBtn">Cerrar carta 🌸</button>
  </div>
</div>

<!-- Octopus layer (outside overlay, fixed) -->
<div class="octo-layer" id="octoLayer"></div>

<script>
document.addEventListener("DOMContentLoaded", function() {

  const cards = [
    {
      title: "Contigo",
      body: `Mi niña hermosa, ya son 5 meses de estar juntotes y la verdad es que jamás pensé poder tener o merecer algo tan bonito como lo que tú me das.

Me salvaste. Me sacaste de un agujero muy profundo y trajiste el sol a mis días más lluviosos dejando siempre un precioso arcoíris.

No sé a quién o a qué agradecerle por haberme enviado a alguien como tú: tan hermosa, atenta, dedicada, trabajadora y lo más importante, igual de loca que yo.

Estos 5 meses solo los puedo describir como mágicos. Haces que el simple hecho de pensar en ti traiga una sonrisa a mi rostro y el hablarte provoque mariposas en mi estómago.

Gracias por haberme escogido. Y prometo escogerte hoy y siempre, por esta vida y todas las que siguen.

Te amo`
    },
    {
      title: "Tú",
      body: `Sabes, siempre dije que eres todo lo bueno y bonito de este mundo, pero ¿qué es todo lo bueno y bonito de este mundo?

Pues déjame decirte todo lo que te describe y te identifica en mi mente y corazón:

Eres la chica más fokín perfecta, dulce, cálida, amable, graciosa, guapa, hermosa, linda, preciosa, habladora, bella, increíble, chistosa, sensible, carismática, inteligente, honesta, simpática, empática, divertida, encantadora, apasionada, considerada, generosa, amistosa, interesante, sencilla, talentosa, creativa, cariñosa, confiable, brillante, maravillosa, noble, romántica, chillona, auténtica, alegre, fantástica, genial, atenta, espectacular, extraordinaria, excepcional, feliz, leal, única, adorable, magnífica, fabulosa, atractiva, grandiosa, divina, perfecta.

Y por eso,

Te amo`
    },
    {
      title: "El destino",
      body: `Sabes, amor, yo jamás he creído en cosas o poderes más allá, pero no hay otra forma de explicar lo que generó esta hermosa relación y conexión que tenemos, más que con el destino.

¿Quién iba a decir que un tonto intento de un tonto niño de secundaria tendría un efecto en cadena tan grande como para llevarme a lo que ahora sería mi mundo entero?

Sinceramente no siento que todo esto sea una simple coincidencia, ya que conectamos tan bien, tan rápido y de manera tan perfecta que me hacen sentir que siempre debiste ser, eres y serás tú la única en mi vida.

Y al parecer yo no soy el único que piensa así, ya que tú misma me lo dijiste un día: también piensas que todo este tiempo tu corazón me estuvo esperando.

Y por esa reacción tan hermosa,

Te amo`
    },
    {
      title: "TE AMO",
      body: `No sé cuánto tiempo me tomé hacer todo esto, pero espero tenerlo listo para cuando ya hayamos cumplido los 5 mesesotes, y si no pues te pido perdón de rodillas y te lo compensaré con unos abrazotes y unos besotes.

Pero creo que con esto ya te he dicho la mayoría de cosas que mi corazón y mente siempre repasan, así que ya lo sabes, mi niña hermosa:

Te amo de una manera que preocuparía a un psiquiatra.

Te amo de una manera que un matemático jamás podría cuantificar.

Te amo de una manera que un filósofo jamás podría imaginar.

Te amo de una manera que un poeta jamás podría plasmar.

Te amo más que la inmensidad del universo observable.

Te amé ayer, te amo hoy y te amaré mañana.

Simplemente,

Te amo`
    },
    {
      title: "Recuerdos",
      body: `MI NIÑA HERMOSAAAAA, ya vamos pa medio añito y la verdad es que no puedo estar más feliz de haber compartido mi vida junto a una persona tan maravillosa como tú.

Gracias por ser mi rayito de sol, mi esperanza y mi razón para seguir adelante.

Aun recuerdo la primera vez que pensamos en nuestros apodos, cuando instalamos la app, el chiste del pingüino… por más tontos o minúsculos que sean, yo realmente los atesoro, ya que tú tienes ese poder en mí de hacer cualquier momento algo memorable, algo especial, algo realmente hermoso (no tanto como tú).

Gracias por haberme elegido y seguirme eligiendo como el afortunado que puede tener el privilegio de llamarte su novia. Gracias por hacerme el hombre más feliz de este fokín mundo, y espero estar logrando el mismo efecto en ti.

Por todos estos recuerdos y la manera en la que haces de mi vida algo por lo que vale la pena continuar,

Te amo`
    },
    {
      title: "Mi pulpito azul",
      blue: true,
      body: `Hola mi pulpito azul, quise hacer esta carta especial porque waos, 7 meses… eso ya es más de medio año compartiendo nuestra vida, más de medio año junto a la mujer más preciosa, bella, hermosa, linda, atenta, amorosa, capaz, inteligente y carismática que jamás he conocido.

Aun lo siento todo como si fuera un sueño del cual sinceramente espero jamás despertar.

Este último mes ha sido algo difícil, ha habido muchos altibajos, problemas y depresiones, pero eso no es lo que realmente importa acá. Lo que importa es que nosotros estuvimos y estaremos juntos a través de todo eso. Logramos resolver todos y cada uno de nuestros problemitas y de paso hicimos nuestro amor aún más fuerte, y eso es algo que realmente me genera una confianza indescriptible.

En mi mente mi vida junto a ti ya está decidida y no quiero imaginarla con nadie más que no seas tú. Ver que también tienes ese mismo objetivo realmente me hace sentirme tan feliz y confiado de que entre todas las personas en este planeta de mierda pude encontrar a mi almita gemela.

Gracias por amarme tanto. Gracias por dejarme amarte tanto. Gracias por todo lo que haces por mí, y espero yo estar haciendo lo suficiente por ti.

Te dedico esta cancioncita, porque creo que recopila muy bien mi sentimiento y el cómo llegaste a mi vida dándome las energías y las ganas de continuar a tu lado.

Gracias por ser mi solecito por las mañanas.

Te amo como no tienes una idea, mi pulpito azul, y espero que este amor nos dure eternidades.`
    }
  ];

  // Elements
  const overlay    = document.getElementById('overlay');
  const letterCard = document.getElementById('letterCard');
  const cardTitle  = document.getElementById('cardTitle');
  const cardBody   = document.getElementById('cardBody');
  const musicBanner = document.getElementById('musicBanner');
  const closeBtn   = document.getElementById('closeBtn');
  const octoLayer  = document.getElementById('octoLayer');
  let octoInterval = null;

  // Open card
  function openCard(index) {
    const card = cards[index];
    cardTitle.textContent = card.title;
    cardBody.textContent  = card.body;
    letterCard.scrollTop  = 0;

    if (card.blue) {
      overlay.classList.add('blue-overlay');
      letterCard.classList.add('blue');
      musicBanner.style.display = 'flex';
      document.body.classList.add('blue-mode');
      startOctos();
    } else {
      overlay.classList.remove('blue-overlay');
      letterCard.classList.remove('blue');
      musicBanner.style.display = 'none';
      document.body.classList.remove('blue-mode');
      stopOctos();
    }

    overlay.classList.add('open');
  }

  // Close card
  function closeCard() {
    overlay.classList.remove('open');
    overlay.classList.remove('blue-overlay');
    letterCard.classList.remove('blue');
    document.body.classList.remove('blue-mode');
    stopOctos();
  }

  // Wire buttons
  document.querySelectorAll('.card-btn').forEach(function(btn) {
    btn.addEventListener('click', function() {
      openCard(parseInt(this.dataset.card));
    });
  });

  // Close button
  closeBtn.addEventListener('click', closeCard);

  // Click outside card to close
  overlay.addEventListener('click', function(e) {
    if (e.target === overlay) closeCard();
  });

  // Petal rain
  const symbols = ['🌸','🌺','✿','❀','🌷','💮'];
  const petalsBg = document.getElementById('petalsBg');
  for (let i = 0; i < 22; i++) {
    const p = document.createElement('span');
    p.className = 'petal';
    p.textContent = symbols[Math.floor(Math.random() * symbols.length)];
    p.style.left = Math.random() * 100 + 'vw';
    p.style.fontSize = (.8 + Math.random() * .9) + 'rem';
    p.style.animationDuration = (9 + Math.random() * 14) + 's';
    p.style.animationDelay = (Math.random() * 12) + 's';
    petalsBg.appendChild(p);
  }

  // Button entrance animations
  document.querySelectorAll('.card-btn').forEach(function(btn, i) {
    btn.style.opacity = '0';
    btn.style.animation = 'fadeUp .7s ' + (.55 + i * .13) + 's ease both';
  });

  // Octopus rain
  function startOctos() {
    stopOctos();
    for (let i = 0; i < 18; i++) spawnOcto(i * 300);
    octoInterval = setInterval(function() { spawnOcto(0); }, 1400);
  }

  function spawnOcto(delay) {
    const o = document.createElement('span');
    o.className = 'octo-float';
    o.textContent = '🐙';
    o.style.left = Math.random() * 100 + '%';
    o.style.fontSize = (1.4 + Math.random() * 1.6) + 'rem';
    o.style.animationDuration = (7 + Math.random() * 11) + 's';
    o.style.animationDelay = delay + 'ms';
    octoLayer.appendChild(o);
    const ttl = parseFloat(o.style.animationDuration) * 1000 + delay +
