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
      --cream:   #fff8f0;
      --text:    #5a3e4b;
      --muted:   #9e7b8a;
      --gold:    #d4a0a7;
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    /* Hide all checkboxes */
    input[type="checkbox"] { display: none; }

    body {
      background: var(--cream);
      font-family: 'Lora', serif;
      color: var(--text);
      min-height: 100vh;
      overflow-x: hidden;
      position: relative;
      transition: background .6s ease;
    }

    /* Blue mode triggered by last checkbox */
    #card5:checked ~ * body,
    body.blue { background: #e8f4fd; }

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
      opacity: 0;
      animation: floatPetal linear infinite;
    }
    @keyframes floatPetal {
      0%   { transform: translateY(-60px) rotate(0deg);   opacity: 0; }
      10%  { opacity: 0.5; }
      90%  { opacity: 0.3; }
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

    /* ── Hero ── */
    .hero { text-align: center; margin-bottom: 56px; }
    .hero-deco { font-size: 2.4rem; letter-spacing: .18em; display: block; margin-bottom: 8px; }
    .hero h1 {
      font-family: 'Playfair Display', serif;
      font-size: clamp(2rem, 6vw, 3.2rem);
      font-weight: 400; font-style: italic;
      color: var(--text); line-height: 1.15;
    }
    .hero-sub { margin-top: 14px; font-size: .95rem; color: var(--muted); letter-spacing: .06em; }
    .divider {
      margin: 28px auto 0; width: 80px; height: 2px;
      background: linear-gradient(90deg, transparent, var(--rose), transparent);
      border-radius: 2px;
    }

    /* ── Button list ── */
    .btn-list { display: flex; flex-direction: column; gap: 18px; }

    /* ── Envelope label (acts as button) ── */
    .envelope-label {
      position: relative;
      display: block;
      background: linear-gradient(135deg, #fff0f5 0%, #fdf4ff 100%);
      border: 1.5px solid #f0c8d4;
      border-radius: 18px;
      padding: 22px 28px;
      cursor: pointer;
      transition: transform .22s ease, box-shadow .22s ease, border-color .22s ease;
      box-shadow: 0 2px 16px rgba(244,167,185,.18);
      overflow: hidden;
    }
    .envelope-label:hover {
      transform: translateY(-3px);
      box-shadow: 0 8px 32px rgba(244,167,185,.30);
      border-color: var(--rose);
    }
    .envelope-label:active { transform: translateY(0) scale(.98); }

    .btn-inner { display: flex; align-items: center; gap: 18px; }
    .btn-icon { font-size: 2rem; flex-shrink: 0; transition: transform .3s ease; }
    .envelope-label:hover .btn-icon { transform: scale(1.15) rotate(-6deg); }
    .btn-label {
      font-family: 'Playfair Display', serif;
      font-size: 1.15rem; font-style: italic; color: var(--text);
    }
    .btn-hint { font-size: .78rem; color: var(--muted); margin-top: 3px; }
    .btn-arrow {
      margin-left: auto; font-size: 1.1rem; color: var(--rose);
      transition: transform .25s; flex-shrink: 0;
    }
    .envelope-label:hover .btn-arrow { transform: translateX(5px); }

    /* Octopus button style */
    .octopus-label {
      background: linear-gradient(135deg, #c8e6f8 0%, #b0d8f5 100%);
      border-color: #5ba3d0;
    }
    .octopus-label:hover { border-color: #2a6fa8; box-shadow: 0 8px 32px rgba(91,163,208,.3); }
    .octopus-label .btn-arrow { color: #5ba3d0; }

    /* ── Overlay (shown when checkbox is checked) ── */
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

    /* Show overlay when its checkbox is checked */
    #card0:checked ~ .overlay-0,
    #card1:checked ~ .overlay-1,
    #card2:checked ~ .overlay-2,
    #card3:checked ~ .overlay-3,
    #card4:checked ~ .overlay-4,
    #card5:checked ~ .overlay-5 {
      opacity: 1;
      pointer-events: all;
    }

    /* Blue overlay for card 5 */
    #card5:checked ~ .overlay-5 {
      background: rgba(10,40,80,.55);
    }

    /* ── Octopus rain inside overlay-5 ── */
    .octo-layer {
      position: absolute;
      inset: 0;
      pointer-events: none;
      overflow: hidden;
      z-index: 0;
    }
    .octo-float {
      position: absolute;
      opacity: 0;
      animation: floatPetal linear infinite;
      pointer-events: none;
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
      z-index: 1;
      transform: scale(.88) translateY(30px);
      transition: transform .4s cubic-bezier(.34,1.56,.64,1), background .5s, border-color .5s;
      padding: 48px 40px 40px;
      border: 1.5px solid #f5d5e0;
    }
    .overlay-5 .letter-card {
      background: #f0f8ff;
      border-color: #90c4e8;
      box-shadow: 0 24px 80px rgba(10,40,80,.22);
    }

    #card0:checked ~ .overlay-0 .letter-card,
    #card1:checked ~ .overlay-1 .letter-card,
    #card2:checked ~ .overlay-2 .letter-card,
    #card3:checked ~ .overlay-3 .letter-card,
    #card4:checked ~ .overlay-4 .letter-card,
    #card5:checked ~ .overlay-5 .letter-card {
      transform: scale(1) translateY(0);
    }

    .letter-card::-webkit-scrollbar { width: 5px; }
    .letter-card::-webkit-scrollbar-track { background: transparent; }
    .letter-card::-webkit-scrollbar-thumb { background: var(--rose); border-radius: 10px; }
    .overlay-5 .letter-card::-webkit-scrollbar-thumb { background: #5ba3d0; }

    .letter-card::before, .letter-card::after {
      content: '✿'; position: absolute; color: var(--rose); opacity: .5; font-size: 1.3rem;
    }
    .letter-card::before { top: 14px; left: 18px; }
    .letter-card::after  { bottom: 14px; right: 18px; transform: rotate(180deg); }
    .overlay-5 .letter-card::before,
    .overlay-5 .letter-card::after { color: #5ba3d0; }

    .letter-title {
      font-family: 'Playfair Display', serif;
      font-size: 1.7rem; font-style: italic;
      text-align: center; margin-bottom: 28px; color: var(--text);
      position: relative;
    }
    .letter-title::after {
      content: ''; display: block; margin: 10px auto 0;
      width: 60px; height: 2px;
      background: linear-gradient(90deg, transparent, var(--rose), transparent);
      border-radius: 2px;
    }
    .overlay-5 .letter-title { color: #1a3a5c; }
    .overlay-5 .letter-title::after { background: linear-gradient(90deg, transparent, #5ba3d0, transparent); }

    .letter-body {
      font-size: 1rem; line-height: 1.85;
      white-space: pre-wrap; color: var(--text);
    }
    .overlay-5 .letter-body { color: #1a3a5c; }

    /* ── Music banner ── */
    .music-banner {
      display: flex;
      margin-top: 28px;
      text-decoration: none;
      background: linear-gradient(135deg, rgba(91,163,208,.15), rgba(42,111,168,.2));
      border: 1.5px solid rgba(91,163,208,.45);
      border-radius: 14px;
      padding: 14px 20px;
      align-items: center;
      gap: 14px;
      transition: transform .2s, box-shadow .2s, background .2s;
      cursor: pointer;
    }
    .music-banner:hover {
      transform: translateY(-2px);
      box-shadow: 0 6px 24px rgba(91,163,208,.3);
      background: linear-gradient(135deg, rgba(91,163,208,.25), rgba(42,111,168,.3));
    }
    .music-banner-icon {
      font-size: 1.8rem; flex-shrink: 0;
      animation: pulse 1.8s ease-in-out infinite;
    }
    @keyframes pulse {
      0%, 100% { transform: scale(1); }
      50%       { transform: scale(1.18); }
    }
    .music-banner-text { flex: 1; }
    .music-banner-title {
      font-family: 'Playfair Display', serif;
      font-size: .95rem; font-style: italic; color: #1a3a5c;
    }
    .music-banner-sub { font-size: .75rem; color: #4a7fa5; margin-top: 3px; }
    .music-banner-arrow { font-size: 1rem; color: #5ba3d0; transition: transform .2s; flex-shrink: 0; }
    .music-banner:hover .music-banner-arrow { transform: translateX(4px); }

    /* ── Close button (label unchecks the checkbox) ── */
    .letter-close {
      display: block;
      margin: 32px auto 0;
      background: linear-gradient(135deg, var(--rose), var(--gold));
      color: #fff; border: none; border-radius: 50px;
      padding: 13px 38px;
      font-family: 'Lora', serif; font-size: .95rem;
      cursor: pointer; letter-spacing: .04em;
      box-shadow: 0 4px 18px rgba(244,167,185,.4);
      transition: transform .2s, box-shadow .2s;
    }
    .letter-close:hover { transform: scale(1.04); box-shadow: 0 8px 28px rgba(244,167,185,.5); }
    .overlay-5 .letter-close {
      background: linear-gradient(135deg, #5ba3d0, #2a6fa8);
      box-shadow: 0 4px 18px rgba(91,163,208,.45);
    }

    /* ── Footer ── */
    .footer {
      text-align: center; margin-top: 56px;
      font-size: .85rem; color: var(--muted); letter-spacing: .05em;
    }

    /* ── Animations ── */
    @keyframes fadeDown {
      from { opacity: 0; transform: translateY(-24px); }
      to   { opacity: 1; transform: translateY(0); }
    }
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(30px); }
      to   { opacity: 1; transform: translateY(0); }
    }
    .hero  { animation: fadeDown .9s ease both; }
    .btn-list > *:nth-child(1) { animation: fadeUp .7s .55s ease both; opacity: 0; animation-fill-mode: both; }
    .btn-list > *:nth-child(2) { animation: fadeUp .7s .68s ease both; opacity: 0; animation-fill-mode: both; }
    .btn-list > *:nth-child(3) { animation: fadeUp .7s .81s ease both; opacity: 0; animation-fill-mode: both; }
    .btn-list > *:nth-child(4) { animation: fadeUp .7s .94s ease both; opacity: 0; animation-fill-mode: both; }
    .btn-list > *:nth-child(5) { animation: fadeUp .7s 1.07s ease both; opacity: 0; animation-fill-mode: both; }
    .btn-list > *:nth-child(6) { animation: fadeUp .7s 1.20s ease both; opacity: 0; animation-fill-mode: both; }
    .footer { animation: fadeUp .7s 1.35s ease both; opacity: 0; animation-fill-mode: both; }
  </style>
</head>
<body>

<!-- Checkboxes controlling each modal -->
<input type="checkbox" id="card0">
<input type="checkbox" id="card1">
<input type="checkbox" id="card2">
<input type="checkbox" id="card3">
<input type="checkbox" id="card4">
<input type="checkbox" id="card5">

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

    <label class="envelope-label" for="card0">
      <div class="btn-inner">
        <span class="btn-icon">💌</span>
        <div>
          <div class="btn-label">Contigo</div>
          <div class="btn-hint">Toca para leer</div>
        </div>
        <span class="btn-arrow">→</span>
      </div>
    </label>

    <label class="envelope-label" for="card1">
      <div class="btn-inner">
        <span class="btn-icon">🌷</span>
        <div>
          <div class="btn-label">Tú</div>
          <div class="btn-hint">Toca para leer</div>
        </div>
        <span class="btn-arrow">→</span>
      </div>
    </label>

    <label class="envelope-label" for="card2">
      <div class="btn-inner">
        <span class="btn-icon">✨</span>
        <div>
          <div class="btn-label">El destino</div>
          <div class="btn-hint">Toca para leer</div>
        </div>
        <span class="btn-arrow">→</span>
      </div>
    </label>

    <label class="envelope-label" for="card3">
      <div class="btn-inner">
        <span class="btn-icon">🌸</span>
        <div>
          <div class="btn-label">TE AMO</div>
          <div class="btn-hint">Toca para leer</div>
        </div>
        <span class="btn-arrow">→</span>
      </div>
    </label>

    <label class="envelope-label" for="card4">
      <div class="btn-inner">
        <span class="btn-icon">🦋</span>
        <div>
          <div class="btn-label">Recuerdos</div>
          <div class="btn-hint">Toca para leer</div>
        </div>
        <span class="btn-arrow">→</span>
      </div>
    </label>

    <label class="envelope-label octopus-label" for="card5">
      <div class="btn-inner">
        <span class="btn-icon">🐙</span>
        <div>
          <div class="btn-label">Mi pulpito azul</div>
          <div class="btn-hint">Toca para leer</div>
        </div>
        <span class="btn-arrow">→</span>
      </div>
    </label>

  </div>
  <p class="footer">hecho con todo el amor del mundo 🤍</p>
</div>

<!-- Modal 0 - Contigo -->
<div class="overlay overlay-0">
  <div class="letter-card">
    <div class="letter-title">Contigo</div>
    <div class="letter-body">Mi niña hermosa, ya son 5 meses de estar juntotes y la verdad es que jamás pensé poder tener o merecer algo tan bonito como lo que tú me das.

Me salvaste. Me sacaste de un agujero muy profundo y trajiste el sol a mis días más lluviosos dejando siempre un precioso arcoíris.

No sé a quién o a qué agradecerle por haberme enviado a alguien como tú: tan hermosa, atenta, dedicada, trabajadora y lo más importante, igual de loca que yo.

Estos 5 meses solo los puedo describir como mágicos. Haces que el simple hecho de pensar en ti traiga una sonrisa a mi rostro y el hablarte provoque mariposas en mi estómago.

Gracias por haberme escogido. Y prometo escogerte hoy y siempre, por esta vida y todas las que siguen.

Te amo</div>
    <label class="letter-close" for="card0">Cerrar carta 🌸</label>
  </div>
</div>

<!-- Modal 1 - Tú -->
<div class="overlay overlay-1">
  <div class="letter-card">
    <div class="letter-title">Tú</div>
    <div class="letter-body">Sabes, siempre dije que eres todo lo bueno y bonito de este mundo, pero ¿qué es todo lo bueno y bonito de este mundo?

Pues déjame decirte todo lo que te describe y te identifica en mi mente y corazón:

Eres la chica más fokín perfecta, dulce, cálida, amable, graciosa, guapa, hermosa, linda, preciosa, habladora, bella, increíble, chistosa, sensible, carismática, inteligente, honesta, simpática, empática, divertida, encantadora, apasionada, considerada, generosa, amistosa, interesante, sencilla, talentosa, creativa, cariñosa, confiable, brillante, maravillosa, noble, romántica, chillona, auténtica, alegre, fantástica, genial, atenta, espectacular, extraordinaria, excepcional, feliz, leal, única, adorable, magnífica, fabulosa, atractiva, grandiosa, divina, perfecta.

Y por eso,

Te amo</div>
    <label class="letter-close" for="card1">Cerrar carta 🌸</label>
  </div>
</div>

<!-- Modal 2 - El destino -->
<div class="overlay overlay-2">
  <div class="letter-card">
    <div class="letter-title">El destino</div>
    <div class="letter-body">Sabes, amor, yo jamás he creído en cosas o poderes más allá, pero no hay otra forma de explicar lo que generó esta hermosa relación y conexión que tenemos, más que con el destino.

¿Quién iba a decir que un tonto intento de un tonto niño de secundaria tendría un efecto en cadena tan grande como para llevarme a lo que ahora sería mi mundo entero?

Sinceramente no siento que todo esto sea una simple coincidencia, ya que conectamos tan bien, tan rápido y de manera tan perfecta que me hacen sentir que siempre debiste ser, eres y serás tú la única en mi vida.

Y al parecer yo no soy el único que piensa así, ya que tú misma me lo dijiste un día: también piensas que todo este tiempo tu corazón me estuvo esperando.

Y por esa reacción tan hermosa,

Te amo</div>
    <label class="letter-close" for="card2">Cerrar carta 🌸</label>
  </div>
</div>

<!-- Modal 3 - TE AMO -->
<div class="overlay overlay-3">
  <div class="letter-card">
    <div class="letter-title">TE AMO</div>
    <div class="letter-body">No sé cuánto tiempo me tomé hacer todo esto, pero espero tenerlo listo para cuando ya hayamos cumplido los 5 mesesotes, y si no pues te pido perdón de rodillas y te lo compensaré con unos abrazotes y unos besotes.

Pero creo que con esto ya te he dicho la mayoría de cosas que mi corazón y mente siempre repasan, así que ya lo sabes, mi niña hermosa:

Te amo de una manera que preocuparía a un psiquiatra.

Te amo de una manera que un matemático jamás podría cuantificar.

Te amo de una manera que un filósofo jamás podría imaginar.

Te amo de una manera que un poeta jamás podría plasmar.

Te amo más que la inmensidad del universo observable.

Te amé ayer, te amo hoy y te amaré mañana.

Simplemente,

Te amo</div>
    <label class="letter-close" for="card3">Cerrar carta 🌸</label>
  </div>
</div>

<!-- Modal 4 - Recuerdos -->
<div class="overlay overlay-4">
  <div class="letter-card">
    <div class="letter-title">Recuerdos</div>
    <div class="letter-body">MI NIÑA HERMOSAAAAA, ya vamos pa medio añito y la verdad es que no puedo estar más feliz de haber compartido mi vida junto a una persona tan maravillosa como tú.

Gracias por ser mi rayito de sol, mi esperanza y mi razón para seguir adelante.

Aun recuerdo la primera vez que pensamos en nuestros apodos, cuando instalamos la app, el chiste del pingüino… por más tontos o minúsculos que sean, yo realmente los atesoro, ya que tú tienes ese poder en mí de hacer cualquier momento algo memorable, algo especial, algo realmente hermoso (no tanto como tú).

Gracias por haberme elegido y seguirme eligiendo como el afortunado que puede tener el privilegio de llamarte su novia. Gracias por hacerme el hombre más feliz de este fokín mundo, y espero estar logrando el mismo efecto en ti.

Por todos estos recuerdos y la manera en la que haces de mi vida algo por lo que vale la pena continuar,

Te amo</div>
    <label class="letter-close" for="card4">Cerrar carta 🌸</label>
  </div>
</div>

<!-- Modal 5 - Mi pulpito azul -->
<div class="overlay overlay-5">
  <div class="octo-layer" id="octoLayer"></div>
  <div class="letter-card">
    <div class="letter-title">Mi pulpito azul</div>
    <div class="letter-body">Hola mi pulpito azul, quise hacer esta carta especial porque waos, 7 meses… eso ya es más de medio año compartiendo nuestra vida, más de medio año junto a la mujer más preciosa, bella, hermosa, linda, atenta, amorosa, capaz, inteligente y carismática que jamás he conocido.

Aun lo siento todo como si fuera un sueño del cual sinceramente espero jamás despertar.

Este último mes ha sido algo difícil, ha habido muchos altibajos, problemas y depresiones, pero eso no es lo que realmente importa acá. Lo que importa es que nosotros estuvimos y estaremos juntos a través de todo eso. Logramos resolver todos y cada uno de nuestros problemitas y de paso hicimos nuestro amor aún más fuerte, y eso es algo que realmente me genera una confianza indescriptible.

En mi mente mi vida junto a ti ya está decidida y no quiero imaginarla con nadie más que no seas tú. Ver que también tienes ese mismo objetivo realmente me hace sentirme tan feliz y confiado de que entre todas las personas en este planeta de mierda pude encontrar a mi almita gemela.

Gracias por amarme tanto. Gracias por dejarme amarte tanto. 
