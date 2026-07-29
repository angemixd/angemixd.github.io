<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Para ti 🌸</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;1,400&family=Lora:ital,wght@0,400;1,400&display=swap" rel="stylesheet">
<style>
* { box-sizing: border-box; margin: 0; padding: 0; }

body {
  font-family: 'Lora', serif;
  background: #fff8f0;
  color: #5a3e4b;
  min-height: 100vh;
  overflow-x: hidden;
}

/* PETALS */
.petals-bg {
  position: fixed; inset: 0;
  pointer-events: none; z-index: 0; overflow: hidden;
}
.petal {
  position: absolute; opacity: 0;
  animation: floatPetal linear infinite;
}
@keyframes floatPetal {
  0%   { transform: translateY(-60px) rotate(0deg); opacity: 0; }
  10%  { opacity: 0.5; }
  90%  { opacity: 0.3; }
  100% { transform: translateY(110vh) rotate(360deg); opacity: 0; }
}

/* MAIN */
.wrapper {
  position: relative; z-index: 1;
  max-width: 680px; margin: 0 auto;
  padding: 60px 24px 80px;
}

/* HEADER */
.hero { text-align: center; margin-bottom: 48px; }
.hero-deco { font-size: 2.4rem; display: block; margin-bottom: 8px; }
.hero h1 {
  font-family: 'Playfair Display', serif;
  font-size: clamp(1.8rem, 6vw, 3rem);
  font-weight: 400; font-style: italic;
}
.hero p { margin-top: 12px; font-size: 0.9rem; color: #9e7b8a; }
.divider {
  margin: 24px auto 0; width: 80px; height: 2px;
  background: linear-gradient(90deg, transparent, #f4a7b9, transparent);
  border-radius: 2px;
}

/* BUTTONS */
.btn-list { display: flex; flex-direction: column; gap: 16px; }

.card-btn {
  display: block; width: 100%; text-decoration: none;
  background: linear-gradient(135deg, #fff0f5, #fdf4ff);
  border: 1.5px solid #f0c8d4;
  border-radius: 18px; padding: 20px 24px;
  cursor: pointer; text-align: left;
  transition: transform 0.2s, box-shadow 0.2s, border-color 0.2s;
  box-shadow: 0 2px 16px rgba(244,167,185,0.18);
}
.card-btn:hover {
  transform: translateY(-3px);
  box-shadow: 0 8px 28px rgba(244,167,185,0.3);
  border-color: #f4a7b9;
}
.card-btn:active { transform: scale(0.98); }
.card-btn.octo {
  background: linear-gradient(135deg, #c8e6f8, #b0d8f5);
  border-color: #5ba3d0;
}
.card-btn.octo:hover { border-color: #2a6fa8; box-shadow: 0 8px 28px rgba(91,163,208,0.3); }

.btn-inner { display: flex; align-items: center; gap: 16px; }
.btn-icon { font-size: 1.9rem; flex-shrink: 0; }
.btn-label {
  font-family: 'Playfair Display', serif;
  font-size: 1.1rem; font-style: italic; color: #5a3e4b;
}
.btn-hint { font-size: 0.75rem; color: #9e7b8a; margin-top: 2px; }
.btn-arrow { margin-left: auto; font-size: 1rem; color: #f4a7b9; flex-shrink: 0; }
.card-btn.octo .btn-arrow { color: #5ba3d0; }

/* FOOTER */
.footer { text-align: center; margin-top: 52px; font-size: 0.82rem; color: #9e7b8a; }

/* ─── MODALES CON :target ─── */
.modal {
  display: none;
  position: fixed; inset: 0;
  background: rgba(90, 62, 75, 0.5);
  backdrop-filter: blur(6px);
  z-index: 1000;
  align-items: center; justify-content: center;
  padding: 20px;
}
/* Se muestra cuando el hash de la URL coincide con el id */
.modal:target { display: flex; }

.modal.blue-modal:target { background: rgba(10, 40, 80, 0.55); }

/* CARTA */
.letter-card {
  background: #fff8f2;
  border-radius: 24px;
  max-width: 560px; width: 100%;
  max-height: 88vh; overflow-y: auto;
  padding: 44px 36px 36px;
  border: 1.5px solid #f5d5e0;
  box-shadow: 0 20px 60px rgba(90,62,75,0.25);
  position: relative;
  animation: popIn 0.35s cubic-bezier(0.34,1.56,0.64,1) both;
}
@keyframes popIn {
  from { transform: scale(0.88) translateY(28px); opacity: 0; }
  to   { transform: scale(1) translateY(0); opacity: 1; }
}
.blue-modal .letter-card {
  background: #f0f8ff;
  border-color: #90c4e8;
  box-shadow: 0 20px 60px rgba(10,40,80,0.22);
}
.letter-card::-webkit-scrollbar { width: 4px; }
.letter-card::-webkit-scrollbar-thumb { background: #f4a7b9; border-radius: 10px; }
.blue-modal .letter-card::-webkit-scrollbar-thumb { background: #5ba3d0; }

.letter-card::before {
  content: '✿'; position: absolute; top: 14px; left: 18px;
  color: #f4a7b9; opacity: 0.5; font-size: 1.2rem;
}
.letter-card::after {
  content: '✿'; position: absolute; bottom: 14px; right: 18px;
  color: #f4a7b9; opacity: 0.5; font-size: 1.2rem; transform: rotate(180deg);
}
.blue-modal .letter-card::before,
.blue-modal .letter-card::after { color: #5ba3d0; }

.letter-title {
  font-family: 'Playfair Display', serif;
  font-size: 1.6rem; font-style: italic;
  text-align: center; margin-bottom: 24px; color: #5a3e4b;
}
.letter-title::after {
  content: ''; display: block; margin: 8px auto 0;
  width: 56px; height: 2px;
  background: linear-gradient(90deg, transparent, #f4a7b9, transparent);
  border-radius: 2px;
}
.blue-modal .letter-title { color: #1a3a5c; }
.blue-modal .letter-title::after { background: linear-gradient(90deg, transparent, #5ba3d0, transparent); }

.letter-body {
  font-size: 0.97rem; line-height: 1.85;
  white-space: pre-wrap; color: #5a3e4b;
}
.blue-modal .letter-body { color: #1a3a5c; }

/* BANNER MÚSICA */
.music-banner {
  display: flex; align-items: center; gap: 14px;
  margin-top: 24px; padding: 14px 18px;
  background: rgba(91,163,208,0.12);
  border: 1.5px solid rgba(91,163,208,0.4);
  border-radius: 14px; text-decoration: none;
  transition: transform 0.2s, box-shadow 0.2s;
}
.music-banner:hover { transform: translateY(-2px); box-shadow: 0 6px 20px rgba(91,163,208,0.25); }
.music-icon { font-size: 1.7rem; animation: pulse 1.8s ease-in-out infinite; flex-shrink: 0; }
@keyframes pulse { 0%,100%{transform:scale(1)} 50%{transform:scale(1.18)} }
.music-title {
  font-family: 'Playfair Display', serif;
  font-size: 0.92rem; font-style: italic; color: #1a3a5c;
}
.music-sub { font-size: 0.72rem; color: #4a7fa5; margin-top: 2px; }
.music-arrow { margin-left: auto; color: #5ba3d0; font-size: 0.95rem; flex-shrink: 0; }

/* CERRAR */
.close-btn {
  display: block; margin: 28px auto 0;
  padding: 12px 36px;
  background: linear-gradient(135deg, #f4a7b9, #d4a0a7);
  color: #fff; border-radius: 50px; text-decoration: none;
  font-family: 'Lora', serif; font-size: 0.92rem;
  text-align: center; letter-spacing: 0.04em;
  box-shadow: 0 4px 16px rgba(244,167,185,0.4);
  transition: transform 0.2s, box-shadow 0.2s;
}
.close-btn:hover { transform: scale(1.04); box-shadow: 0 8px 24px rgba(244,167,185,0.5); }
.blue-modal .close-btn {
  background: linear-gradient(135deg, #5ba3d0, #2a6fa8);
  box-shadow: 0 4px 16px rgba(91,163,208,0.4);
}

/* OCTOPUS LAYER */
.octo-layer {
  position: fixed; inset: 0;
  pointer-events: none; z-index: 999; overflow: hidden;
  display: none;
}
.octo-layer.active { display: block; }
.octo-float { position: absolute; opacity: 0; animation: floatPetal linear infinite; }
</style>
</head>
<body>

<div class="petals-bg" id="petalsBg"></div>

<div class="wrapper">
  <header class="hero">
    <span class="hero-deco">🌸 ✦ 🌸</span>
    <h1>Para mi niña hermosa</h1>
    <p>Abre cada carta con cariño</p>
    <div class="divider"></div>
  </header>

  <div class="btn-list">

    <a class="card-btn" href="#carta0">
      <div class="btn-inner">
        <span class="btn-icon">💌</span>
        <div><div class="btn-label">Contigo</div><div class="btn-hint">Toca para leer</div></div>
        <span class="btn-arrow">→</span>
      </div>
    </a>

    <a class="card-btn" href="#carta1">
      <div class="btn-inner">
        <span class="btn-icon">🌷</span>
        <div><div class="btn-label">Tú</div><div class="btn-hint">Toca para leer</div></div>
        <span class="btn-arrow">→</span>
      </div>
    </a>

    <a class="card-btn" href="#carta2">
      <div class="btn-inner">
        <span class="btn-icon">✨</span>
        <div><div class="btn-label">El destino</div><div class="btn-hint">Toca para leer</div></div>
        <span class="btn-arrow">→</span>
      </div>
    </a>

    <a class="card-btn" href="#carta3">
      <div class="btn-inner">
        <span class="btn-icon">🌸</span>
        <div><div class="btn-label">TE AMO</div><div class="btn-hint">Toca para leer</div></div>
        <span class="btn-arrow">→</span>
      </div>
    </a>

    <a class="card-btn" href="#carta4">
      <div class="btn-inner">
        <span class="btn-icon">🦋</span>
        <div><div class="btn-label">Recuerdos</div><div class="btn-hint">Toca para leer</div></div>
        <span class="btn-arrow">→</span>
      </div>
    </a>

    <a class="card-btn octo" href="#carta5">
      <div class="btn-inner">
        <span class="btn-icon">🐙</span>
        <div><div class="btn-label">Mi pulpito azul</div><div class="btn-hint">Toca para leer</div></div>
        <span class="btn-arrow">→</span>
      </div>
    </a>

    <a class="card-btn" href="#carta6">
      <div class="btn-inner">
        <span class="btn-icon">💞</span>
        <div><div class="btn-label">ti amu</div><div class="btn-hint">Toca para leer</div></div>
        <span class="btn-arrow">→</span>
      </div>
    </a>

    <a class="card-btn" href="#carta7">
      <div class="btn-inner">
        <span class="btn-icon">🌙</span>
        <div><div class="btn-label">y contando</div><div class="btn-hint">Toca para leer</div></div>
        <span class="btn-arrow">→</span>
      </div>
    </a>

  </div>
  <p class="footer">hecho con todo el amor del mundo 🤍</p>
</div>

<!-- MODAL 0 - Contigo -->
<div class="modal" id="carta0">
  <div class="letter-card">
    <div class="letter-title">Contigo</div>
    <div class="letter-body">Mi niña hermosa, ya son 5 meses de estar juntotes y la verdad es que jamás pensé poder tener o merecer algo tan bonito como lo que tú me das.

Me salvaste. Me sacaste de un agujero muy profundo y trajiste el sol a mis días más lluviosos dejando siempre un precioso arcoíris.

No sé a quién o a qué agradecerle por haberme enviado a alguien como tú: tan hermosa, atenta, dedicada, trabajadora y lo más importante, igual de loca que yo.

Estos 5 meses solo los puedo describir como mágicos. Haces que el simple hecho de pensar en ti traiga una sonrisa a mi rostro y el hablarte provoque mariposas en mi estómago.

Gracias por haberme escogido. Y prometo escogerte hoy y siempre, por esta vida y todas las que siguen.

Te amo</div>
    <a class="close-btn" href="#">Cerrar carta 🌸</a>
  </div>
</div>

<!-- MODAL 1 - Tú -->
<div class="modal" id="carta1">
  <div class="letter-card">
    <div class="letter-title">Tú</div>
    <div class="letter-body">Sabes, siempre dije que eres todo lo bueno y bonito de este mundo, pero ¿qué es todo lo bueno y bonito de este mundo?

Pues déjame decirte todo lo que te describe y te identifica en mi mente y corazón:

Eres la chica más fokín perfecta, dulce, cálida, amable, graciosa, guapa, hermosa, linda, preciosa, habladora, bella, increíble, chistosa, sensible, carismática, inteligente, honesta, simpática, empática, divertida, encantadora, apasionada, considerada, generosa, amistosa, interesante, sencilla, talentosa, creativa, cariñosa, confiable, brillante, maravillosa, noble, romántica, chillona, auténtica, alegre, fantástica, genial, atenta, espectacular, extraordinaria, excepcional, feliz, leal, única, adorable, magnífica, fabulosa, atractiva, grandiosa, divina, perfecta.

Y por eso,

Te amo</div>
    <a class="close-btn" href="#">Cerrar carta 🌸</a>
  </div>
</div>

<!-- MODAL 2 - El destino -->
<div class="modal" id="carta2">
  <div class="letter-card">
    <div class="letter-title">El destino</div>
    <div class="letter-body">Sabes, amor, yo jamás he creído en cosas o poderes más allá, pero no hay otra forma de explicar lo que generó esta hermosa relación y conexión que tenemos, más que con el destino.

¿Quién iba a decir que un tonto intento de un tonto niño de secundaria tendría un efecto en cadena tan grande como para llevarme a lo que ahora sería mi mundo entero?

Sinceramente no siento que todo esto sea una simple coincidencia, ya que conectamos tan bien, tan rápido y de manera tan perfecta que me hacen sentir que siempre debiste ser, eres y serás tú la única en mi vida.

Y al parecer yo no soy el único que piensa así, ya que tú misma me lo dijiste un día: también piensas que todo este tiempo tu corazón me estuvo esperando.

Y por esa reacción tan hermosa,

Te amo</div>
    <a class="close-btn" href="#">Cerrar carta 🌸</a>
  </div>
</div>

<!-- MODAL 3 - TE AMO -->
<div class="modal" id="carta3">
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
    <a class="close-btn" href="#">Cerrar carta 🌸</a>
  </div>
</div>

<!-- MODAL 4 - Recuerdos -->
<div class="modal" id="carta4">
  <div class="letter-card">
    <div class="letter-title">Recuerdos</div>
    <div class="letter-body">MI NIÑA HERMOSAAAAA, ya vamos pa medio añito y la verdad es que no puedo estar más feliz de haber compartido mi vida junto a una persona tan maravillosa como tú.

Gracias por ser mi rayito de sol, mi esperanza y mi razón para seguir adelante.

Aun recuerdo la primera vez que pensamos en nuestros apodos, cuando instalamos la app, el chiste del pingüino… por más tontos o minúsculos que sean, yo realmente los atesoro, ya que tú tienes ese poder en mí de hacer cualquier momento algo memorable, algo especial, algo realmente hermoso (no tanto como tú).

Gracias por haberme elegido y seguirme eligiendo como el afortunado que puede tener el privilegio de llamarte su novia. Gracias por hacerme el hombre más feliz de este fokín mundo, y espero estar logrando el mismo efecto en ti.

Por todos estos recuerdos y la manera en la que haces de mi vida algo por lo que vale la pena continuar,

Te amo</div>
    <a class="close-btn" href="#">Cerrar carta 🌸</a>
  </div>
</div>

<!-- MODAL 5 - Mi pulpito azul -->
<div class="modal blue-modal" id="carta5">
  <div class="octo-layer" id="octoLayer"></div>
  <div class="letter-card">
    <div class="letter-title">Mi pulpito azul</div>
    <div class="letter-body">Hola mi pulpito azul, quise hacer esta carta especial porque waos, 7 meses… eso ya es más de medio año compartiendo nuestra vida, más de medio año junto a la mujer más preciosa, bella, hermosa, linda, atenta, amorosa, capaz, inteligente y carismática que jamás he conocido.

Aun lo siento todo como si fuera un sueño del cual sinceramente espero jamás despertar.

Este último mes ha sido algo difícil, ha habido muchos altibajos, problemas y depresiones, pero eso no es lo que realmente importa acá. Lo que importa es que nosotros estuvimos y estaremos juntos a través de todo eso. Logramos resolver todos y cada uno de nuestros problemitas y de paso hicimos nuestro amor aún más fuerte, y eso es algo que realmente me genera una confianza indescriptible.

En mi mente mi vida junto a ti ya está decidida y no quiero imaginarla con nadie más que no seas tú. Ver que también tienes ese mismo objetivo realmente me hace sentirme tan feliz y confiado de que entre todas las personas en este planeta de mierda pude encontrar a mi almita gemela.

Gracias por amarme tanto. Gracias por dejarme amarte tanto. Gracias por todo lo que haces por mí, y espero yo estar haciendo lo suficiente por ti.

Te dedico esta cancioncita, porque creo que recopila muy bien mi sentimiento y el cómo llegaste a mi vida dándome las energías y las ganas de continuar a tu lado.

Gracias por ser mi solecito por las mañanas.

Te amo como no tienes una idea, mi pulpito azul, y espero que este amor nos dure eternidades.</div>
    <a class="music-banner" href="https://youtu.be/tKdhg9P0ZIQ?si=RS8qxozf9V8p9Se_" target="_blank">
      <span class="music-icon">🎵</span>
      <div>
        <div class="music-title">Escucha nuestra canción</div>
        <div class="music-sub">Tú Sí Eres Real — toca para abrir</div>
      </div>
      <span class="music-arrow">→</span>
    </a>
    <a class="close-btn" href="#">Cerrar carta 🌸</a>
  </div>
</div>

<!-- MODAL 6 - ti amu -->
<div class="modal" id="carta6">
  <div class="letter-card">
    <div class="letter-title">ti amu</div>
    <div class="letter-body">Mi niña preciosota ya son 8 meses los cuales eh compartido cada segundo de mi vida junto a ti y la verdad es algo de lo cual estoy sorprendido y feliz al mismo tiempo sabes?, llegaste de la nada iluminaste mi vida y te quedaste junto a mi prometiendo continuar a mi lado durante toda la eternidad y la verdad es que lo creo.

No se porque pero simplemente me das esa seguridad y ese sentimiento de amor tan enorme que no me da miedo entregarte mi esencia de manera completa, se siente como si mi corazon fuera resguardado en una cajita de cristal para luego ser consentido con el amor de una fokin diosa y ese sentimientote es algo que jamas habia sentido, ni en lo mas minimo, todo contigo es nuevo, refrescante y hermoso y ahora solo estoy pensando en mi futuro junto a ti, en todo lo que podemos hacer y haremos y tambien en cuanto te amo y te seguire amando cada vez mas por toda la eternidad, gracias por elegir compartir tu vida conmigo, prometo no defraudarte y darte todo de mi para que tu estancia junto a mi este llena de besotes, amor y seguridad.

Ti amu con toda mi fokin alma, cuerpo y mente mi amol, gracias por seguir a mi lado</div>
    <a class="close-btn" href="#">Cerrar carta 🌸</a>
  </div>
</div>

<!-- MODAL 7 - y contando -->
<div class="modal" id="carta7">
  <div class="letter-card">
    <div class="letter-title">y contando</div>
    <div class="letter-body">Jelou mi niña preciosa, escribo esto en uno de esos dias en los que no puedo realmente dormir y solo te queria decir que gracias por darme los 9 meses mas felices de toda mi putisima vida, te amo tanto que nisiquiera yo puedo explicarlo y a veces me sorprendo a mi mismo con lo que puedo llegar a sentir y todo es gracias a ti, espero enserio poder seguir amandonos de esta manera y de mil maneras mas porque enserio creo que encontre mi almita gemela en ti.

Me siento tan feliz, seguro y amado a tu lado que simplemente no me da miedo darte mi alma entera cuando con cualquier persona hasta me da miedo demostrar algun tipo de emocion en mi cara por temor a que se aprovechen de ello. Y me estoy dando cuenta de que realmente estoy enamorado de ti, sabes... no puedo parar de pensar en "la quiero aqui" "quiero adelantar el tiempo para que ya no nos pongan trabas" "quiero despertar a su lado" "quiero hacerle el desayuno" y muchisimas cosas mas y wow, jamas habia pensado eso con nadie mas, nisiquiera sabia que podia llegar a sentir tanto.

Pero tu realmente me ayudaste a salir de mi caparazon y demostrar como soy sin reprimirme, demostrar que tambien siento y que tambien puedo amar con fokin locura.

Este mes ha sido un poco... como llamarlo?? feo?? por asi decirlo, ha habido muchisimas platicas y sabes, me alegra que las haya porque significa que realmente queremos seguir juntotes y estamos luchando por ello.

Pero como sea, tu eres y siempre seras mi almita gemela sin importar que. Gracias por estos 9 mesesotes tan magicos y contando, hermosa.

TE AMOOOOOOOOO MI PULPITO AZUUUUUL</div>
    <a class="music-banner" href="https://youtu.be/1oOoOJDbhXQ?si=0C90Tt59D6RdrLYP" target="_blank">
      <span class="music-icon">🎵</span>
      <div>
        <div class="music-title">Toma, te la dedico por preciosota ♡</div>
        <div class="music-sub">toca para abrir</div>
      </div>
      <span class="music-arrow">→</span>
    </a>
    <a class="close-btn" href="#">Cerrar carta 🌸</a>
  </div>
</div>

<script>
// Petal rain
var symbols = ['🌸','🌺','✿','❀','🌷','💮'];
var bg = document.getElementById('petalsBg');
for (var i = 0; i < 22; i++) {
  var p = document.createElement('span');
  p.className = 'petal';
  p.textContent = symbols[Math.floor(Math.random() * symbols.length)];
  p.style.left = (Math.random() * 100) + 'vw';
  p.style.fontSize = (0.8 + Math.random() * 0.9) + 'rem';
  p.style.animationDuration = (9 + Math.random() * 14) + 's';
  p.style.animationDelay = (Math.random() * 12) + 's';
  bg.appendChild(p);
}

// Octopus rain for carta5
var octoLayer = document.getElementById('octoLayer');
var octoInterval = null;

function checkHash() {
  if (window.location.hash === '#carta5') {
    startOctos();
  } else {
    stopOctos();
  }
}

window.addEventListener('hashchange', checkHash);
window.addEventListener('load', checkHash);

function startOctos() {
  stopOctos();
  octoLayer.className = 'octo-layer active';
  for (var i = 0; i < 18; i++) {
    (function(i){ setTimeout(spawnOcto, i * 300); })(i);
  }
  octoInterval = setInterval(spawnOcto, 1400);
}

function spawnOcto() {
  var o = document.createElement('span');
  o.className = 'octo-float';
  o.textContent = '🐙';
  o.style.left = (Math.random() * 100) + '%';
  o.style.fontSize = (1.4 + Math.random() * 1.6) + 'rem';
  o.style.animationDuration = (7 + Math.random() * 11) + 's';
  o.style.animationDelay = '0ms';
  octoLayer.appendChild(o);
  var ttl = parseFloat(o.style.animationDuration) * 1000 + 600;
  setTimeout(function(){ if (o.parentNode) o.remove(); }, ttl);
}

function stopOctos() {
  if (octoInterval) { clearInterval(octoInterval); octoInterval = null; }
  octoLayer.className = 'octo-layer';
  octoLayer.innerHTML = '';
}
</script>
</body>
</html>
