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
  transition: background 0.6s;
}

/* PETALS */
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
  0%   { transform: translateY(-60px) rotate(0deg); opacity: 0; }
  10%  { opacity: 0.5; }
  90%  { opacity: 0.3; }
  100% { transform: translateY(110vh) rotate(360deg); opacity: 0; }
}

/* MAIN CONTENT */
.wrapper {
  position: relative;
  z-index: 1;
  max-width: 680px;
  margin: 0 auto;
  padding: 60px 24px 80px;
}

/* HEADER */
.hero {
  text-align: center;
  margin-bottom: 48px;
}
.hero-deco {
  font-size: 2.4rem;
  display: block;
  margin-bottom: 8px;
}
.hero h1 {
  font-family: 'Playfair Display', serif;
  font-size: clamp(1.8rem, 6vw, 3rem);
  font-weight: 400;
  font-style: italic;
}
.hero p {
  margin-top: 12px;
  font-size: 0.9rem;
  color: #9e7b8a;
}
.divider {
  margin: 24px auto 0;
  width: 80px;
  height: 2px;
  background: linear-gradient(90deg, transparent, #f4a7b9, transparent);
  border-radius: 2px;
}

/* BUTTONS */
.btn-list {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.card-btn {
  display: block;
  width: 100%;
  background: linear-gradient(135deg, #fff0f5, #fdf4ff);
  border: 1.5px solid #f0c8d4;
  border-radius: 18px;
  padding: 20px 24px;
  cursor: pointer;
  text-align: left;
  transition: transform 0.2s, box-shadow 0.2s, border-color 0.2s;
  box-shadow: 0 2px 16px rgba(244,167,185,0.18);
}
.card-btn:hover {
  transform: translateY(-3px);
  box-shadow: 0 8px 28px rgba(244,167,185,0.3);
  border-color: #f4a7b9;
}
.card-btn:active {
  transform: scale(0.98);
}
.card-btn.octo {
  background: linear-gradient(135deg, #c8e6f8, #b0d8f5);
  border-color: #5ba3d0;
}
.card-btn.octo:hover {
  border-color: #2a6fa8;
  box-shadow: 0 8px 28px rgba(91,163,208,0.3);
}

.btn-inner {
  display: flex;
  align-items: center;
  gap: 16px;
}
.btn-icon {
  font-size: 1.9rem;
  flex-shrink: 0;
}
.btn-label {
  font-family: 'Playfair Display', serif;
  font-size: 1.1rem;
  font-style: italic;
  color: #5a3e4b;
}
.btn-hint {
  font-size: 0.75rem;
  color: #9e7b8a;
  margin-top: 2px;
}
.btn-arrow {
  margin-left: auto;
  font-size: 1rem;
  color: #f4a7b9;
  flex-shrink: 0;
}
.card-btn.octo .btn-arrow { color: #5ba3d0; }

/* FOOTER */
.footer {
  text-align: center;
  margin-top: 52px;
  font-size: 0.82rem;
  color: #9e7b8a;
}

/* OVERLAY */
.overlay {
  display: none;
  position: fixed;
  inset: 0;
  background: rgba(90, 62, 75, 0.5);
  backdrop-filter: blur(6px);
  z-index: 1000;
  align-items: center;
  justify-content: center;
  padding: 20px;
}
.overlay.active {
  display: flex;
}
.overlay.blue {
  background: rgba(10, 40, 80, 0.55);
}

/* LETTER CARD */
.letter-card {
  background: #fff8f2;
  border-radius: 24px;
  max-width: 560px;
  width: 100%;
  max-height: 88vh;
  overflow-y: auto;
  padding: 44px 36px 36px;
  border: 1.5px solid #f5d5e0;
  box-shadow: 0 20px 60px rgba(90,62,75,0.25);
  position: relative;
  z-index: 1001;
  animation: popIn 0.4s cubic-bezier(0.34, 1.56, 0.64, 1) both;
}
@keyframes popIn {
  from { transform: scale(0.85) translateY(30px); opacity: 0; }
  to   { transform: scale(1) translateY(0); opacity: 1; }
}
.letter-card.blue {
  background: #f0f8ff;
  border-color: #90c4e8;
}

.letter-card::-webkit-scrollbar { width: 4px; }
.letter-card::-webkit-scrollbar-thumb { background: #f4a7b9; border-radius: 10px; }
.letter-card.blue::-webkit-scrollbar-thumb { background: #5ba3d0; }

.letter-card::before {
  content: '✿';
  position: absolute;
  top: 14px; left: 18px;
  color: #f4a7b9;
  opacity: 0.5;
  font-size: 1.2rem;
}
.letter-card::after {
  content: '✿';
  position: absolute;
  bottom: 14px; right: 18px;
  color: #f4a7b9;
  opacity: 0.5;
  font-size: 1.2rem;
  transform: rotate(180deg);
}
.letter-card.blue::before,
.letter-card.blue::after { color: #5ba3d0; }

.letter-title {
  font-family: 'Playfair Display', serif;
  font-size: 1.6rem;
  font-style: italic;
  text-align: center;
  margin-bottom: 24px;
  color: #5a3e4b;
}
.letter-title::after {
  content: '';
  display: block;
  margin: 8px auto 0;
  width: 56px; height: 2px;
  background: linear-gradient(90deg, transparent, #f4a7b9, transparent);
  border-radius: 2px;
}
.letter-card.blue .letter-title { color: #1a3a5c; }
.letter-card.blue .letter-title::after { background: linear-gradient(90deg, transparent, #5ba3d0, transparent); }

.letter-body {
  font-size: 0.97rem;
  line-height: 1.85;
  white-space: pre-wrap;
  color: #5a3e4b;
}
.letter-card.blue .letter-body { color: #1a3a5c; }

/* MUSIC BANNER */
.music-banner {
  display: flex;
  align-items: center;
  gap: 14px;
  margin-top: 24px;
  padding: 14px 18px;
  background: rgba(91,163,208,0.12);
  border: 1.5px solid rgba(91,163,208,0.4);
  border-radius: 14px;
  text-decoration: none;
  transition: transform 0.2s, box-shadow 0.2s;
}
.music-banner:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(91,163,208,0.25);
}
.music-icon {
  font-size: 1.7rem;
  animation: pulse 1.8s ease-in-out infinite;
  flex-shrink: 0;
}
@keyframes pulse {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.18); }
}
.music-title {
  font-family: 'Playfair Display', serif;
  font-size: 0.92rem;
  font-style: italic;
  color: #1a3a5c;
}
.music-sub {
  font-size: 0.72rem;
  color: #4a7fa5;
  margin-top: 2px;
}
.music-arrow {
  margin-left: auto;
  color: #5ba3d0;
  font-size: 0.95rem;
}

/* CLOSE BUTTON */
.close-btn {
  display: block;
  margin: 28px auto 0;
  padding: 12px 36px;
  background: linear-gradient(135deg, #f4a7b9, #d4a0a7);
  color: #fff;
  border: none;
  border-radius: 50px;
  font-family: 'Lora', serif;
  font-size: 0.92rem;
  cursor: pointer;
  letter-spacing: 0.04em;
  box-shadow: 0 4px 16px rgba(244,167,185,0.4);
  transition: transform 0.2s, box-shadow 0.2s;
}
.close-btn:hover {
  transform: scale(1.04);
  box-shadow: 0 8px 24px rgba(244,167,185,0.5);
}
.letter-card.blue .close-btn {
  background: linear-gradient(135deg, #5ba3d0, #2a6fa8);
  box-shadow: 0 4px 16px rgba(91,163,208,0.4);
}

/* OCTOPUS LAYER */
.octo-layer {
  position: fixed;
  inset: 0;
  pointer-events: none;
  z-index: 999;
  overflow: hidden;
  display: none;
}
.octo-layer.active { display: block; }
.octo-float {
  position: absolute;
  opacity: 0;
  animation: floatPetal linear infinite;
}
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
    <button class="card-btn" onclick="openCard(0)">
      <div class="btn-inner">
        <span class="btn-icon">💌</span>
        <div><div class="btn-label">Contigo</div><div class="btn-hint">Toca para leer</div></div>
        <span class="btn-arrow">→</span>
      </div>
    </button>
    <button class="card-btn" onclick="openCard(1)">
      <div class="btn-inner">
        <span class="btn-icon">🌷</span>
        <div><div class="btn-label">Tú</div><div class="btn-hint">Toca para leer</div></div>
        <span class="btn-arrow">→</span>
      </div>
    </button>
    <button class="card-btn" onclick="openCard(2)">
      <div class="btn-inner">
        <span class="btn-icon">✨</span>
        <div><div class="btn-label">El destino</div><div class="btn-hint">Toca para leer</div></div>
        <span class="btn-arrow">→</span>
      </div>
    </button>
    <button class="card-btn" onclick="openCard(3)">
      <div class="btn-inner">
        <span class="btn-icon">🌸</span>
        <div><div class="btn-label">TE AMO</div><div class="btn-hint">Toca para leer</div></div>
        <span class="btn-arrow">→</span>
      </div>
    </button>
    <button class="card-btn" onclick="openCard(4)">
      <div class="btn-inner">
        <span class="btn-icon">🦋</span>
        <div><div class="btn-label">Recuerdos</div><div class="btn-hint">Toca para leer</div></div>
        <span class="btn-arrow">→</span>
      </div>
    </button>
    <button class="card-btn octo" onclick="openCard(5)">
      <div class="btn-inner">
        <span class="btn-icon">🐙</span>
        <div><div class="btn-label">Mi pulpito azul</div><div class="btn-hint">Toca para leer</div></div>
        <span class="btn-arrow">→</span>
      </div>
    </button>
  </div>

  <p class="footer">hecho con todo el amor del mundo 🤍</p>
</div>

<!-- MODAL -->
<div class="overlay" id="overlay" onclick="handleOverlayClick(event)">
  <div class="letter-card" id="letterCard">
    <div class="letter-title" id="cardTitle"></div>
    <div class="letter-body" id="cardBody"></div>
    <a class="music-banner" id="musicBanner" href="https://youtu.be/tKdhg9P0ZIQ?si=RS8qxozf9V8p9Se_" target="_blank">
      <span class="music-icon">🎵</span>
      <div>
        <div class="music-title">Escucha nuestra canción</div>
        <div class="music-sub">Tú Sí Eres Real — toca para abrir</div>
      </div>
      <span class="music-arrow">→</span>
    </a>
    <button class="close-btn" onclick="closeCard()">Cerrar carta 🌸</button>
  </div>
</div>

<!-- OCTOPUS LAYER -->
<div class="octo-layer" id="octoLayer"></div>

<script>
var cards = [
  {
    title: "Contigo",
    body: "Mi niña hermosa, ya son 5 meses de estar juntotes y la verdad es que jamás pensé poder tener o merecer algo tan bonito como lo que tú me das.\n\nMe salvaste. Me sacaste de un agujero muy profundo y trajiste el sol a mis días más lluviosos dejando siempre un precioso arcoíris.\n\nNo sé a quién o a qué agradecerle por haberme enviado a alguien como tú: tan hermosa, atenta, dedicada, trabajadora y lo más importante, igual de loca que yo.\n\nEstos 5 meses solo los puedo describir como mágicos. Haces que el simple hecho de pensar en ti traiga una sonrisa a mi rostro y el hablarte provoque mariposas en mi estómago.\n\nGracias por haberme escogido. Y prometo escogerte hoy y siempre, por esta vida y todas las que siguen.\n\nTe amo"
  },
  {
    title: "Tú",
    body: "Sabes, siempre dije que eres todo lo bueno y bonito de este mundo, pero ¿qué es todo lo bueno y bonito de este mundo?\n\nPues déjame decirte todo lo que te describe y te identifica en mi mente y corazón:\n\nEres la chica más fokín perfecta, dulce, cálida, amable, graciosa, guapa, hermosa, linda, preciosa, habladora, bella, increíble, chistosa, sensible, carismática, inteligente, honesta, simpática, empática, divertida, encantadora, apasionada, considerada, generosa, amistosa, interesante, sencilla, talentosa, creativa, cariñosa, confiable, brillante, maravillosa, noble, romántica, chillona, auténtica, alegre, fantástica, genial, atenta, espectacular, extraordinaria, excepcional, feliz, leal, única, adorable, magnífica, fabulosa, atractiva, grandiosa, divina, perfecta.\n\nY por eso,\n\nTe amo"
  },
  {
    title: "El destino",
    body: "Sabes, amor, yo jamás he creído en cosas o poderes más allá, pero no hay otra forma de explicar lo que generó esta hermosa relación y conexión que tenemos, más que con el destino.\n\n¿Quién iba a decir que un tonto intento de un tonto niño de secundaria tendría un efecto en cadena tan grande como para llevarme a lo que ahora sería mi mundo entero?\n\nSinceramente no siento que todo esto sea una simple coincidencia, ya que conectamos tan bien, tan rápido y de manera tan perfecta que me hacen sentir que siempre debiste ser, eres y serás tú la única en mi vida.\n\nY al parecer yo no soy el único que piensa así, ya que tú misma me lo dijiste un día: también piensas que todo este tiempo tu corazón me estuvo esperando.\n\nY por esa reacción tan hermosa,\n\nTe amo"
  },
  {
    title: "TE AMO",
    body: "No sé cuánto tiempo me tomé hacer todo esto, pero espero tenerlo listo para cuando ya hayamos cumplido los 5 mesesotes, y si no pues te pido perdón de rodillas y te lo compensaré con unos abrazotes y unos besotes.\n\nPero creo que con esto ya te he dicho la mayoría de cosas que mi corazón y mente siempre repasan, así que ya lo sabes, mi niña hermosa:\n\nTe amo de una manera que preocuparía a un psiquiatra.\n\nTe amo de una manera que un matemático jamás podría cuantificar.\n\nTe amo de una manera que un filósofo jamás podría imaginar.\n\nTe amo de una manera que un poeta jamás podría plasmar.\n\nTe amo más que la inmensidad del universo observable.\n\nTe amé ayer, te amo hoy y te amaré mañana.\n\nSimplemente,\n\nTe amo"
  },
  {
    title: "Recuerdos",
    body: "MI NIÑA HERMOSAAAAA, ya vamos pa medio añito y la verdad es que no puedo estar más feliz de haber compartido mi vida junto a una persona tan maravillosa como tú.\n\nGracias por ser mi rayito de sol, mi esperanza y mi razón para seguir adelante.\n\nAun recuerdo la primera vez que pensamos en nuestros apodos, cuando instalamos la app, el chiste del pingüino… por más tontos o minúsculos que sean, yo realmente los atesoro, ya que tú tienes ese poder en mí de hacer cualquier momento algo memorable, algo especial, algo realmente hermoso (no tanto como tú).\n\nGracias por haberme elegido y seguirme eligiendo como el afortunado que puede tener el privilegio de llamarte su novia. Gracias por hacerme el hombre más feliz de este fokín mundo, y espero estar logrando el mismo efecto en ti.\n\nPor todos estos recuerdos y la manera en la que haces de mi vida algo por lo que vale la pena continuar,\n\nTe amo"
  },
  {
    title: "Mi pulpito azul",
    blue: true,
    body: "Hola mi pulpito azul, quise hacer esta carta especial porque waos, 7 meses… eso ya es más de medio año compartiendo nuestra vida, más de medio año junto a la mujer más preciosa, bella, hermosa, linda, atenta, amorosa, capaz, inteligente y carismática que jamás he conocido.\n\nAun lo siento todo como si fuera un sueño del cual sinceramente espero jamás despertar.\n\nEste último mes ha sido algo difícil, ha habido muchos altibajos, problemas y depresiones, pero eso no es lo que realmente importa acá. Lo que importa es que nosotros estuvimos y estaremos juntos a través de todo eso. Logramos resolver todos y cada uno de nuestros problemitas y de paso hicimos nuestro amor aún más fuerte, y eso es algo que realmente me genera una confianza indescriptible.\n\nEn mi mente mi vida junto a ti ya está decidida y no quiero imaginarla con nadie más que no seas tú. Ver que también tienes ese mismo objetivo realmente me hace sentirme tan feliz y confiado de que entre todas las personas en este planeta de mierda pude encontrar a mi almita gemela.\n\nGracias por amarme tanto. Gracias por dejarme amarte tanto. Gracias por todo lo que haces por mí, y espero yo estar haciendo lo suficiente por ti.\n\nTe dedico esta cancioncita, porque creo que recopila muy bien mi sentimiento y el cómo llegaste a mi vida dándome las energías y las ganas de continuar a tu lado.\n\nGracias por ser mi solecito por las mañanas.\n\nTe amo como no tienes una idea, mi pulpito azul, y espero que este amor nos dure eternidades."
  }
];

var overlay = document.getElementById('overlay');
var letterCard = document.getElementById('letterCard');
var cardTitle = document.getElementById('cardTitle');
var cardBody = document.getElementById('cardBody');
var musicBanner = document.getElementById('musicBanner');
var octoLayer = document.getElementById('octoLayer');
var octoInterval = null;

function openCard(index) {
  var card = cards[index];
  cardTitle.textContent = card.title;
  cardBody.textContent = card.body;
  letterCard.scrollTop = 0;

  if (card.blue) {
    overlay.className = 'overlay active blue';
    letterCard.className = 'letter-card blue';
    musicBanner.style.display = 'flex';
    document.body.style.background = '#e8f4fd';
    startOctos();
  } else {
    overlay.className = 'overlay active';
    letterCard.className = 'letter-card';
    musicBanner.style.display = 'none';
    document.body.style.background = '#fff8f0';
    stopOctos();
  }
}

function closeCard() {
  overlay.className = 'overlay';
  document.body.style.background = '#fff8f0';
  stopOctos();
}

function handleOverlayClick(e) {
  if (e.target === overlay) closeCard();
}

// Petal rain
var symbols = ['🌸','🌺','✿','❀','🌷','💮'];
var petalsBg = document.getElementById('petalsBg');
for (var i = 0; i < 22; i++) {
  (function(i) {
    var p = document.createElement('span');
    p.className = 'petal';
    p.textContent = symbols[Math.floor(Math.random() * symbols.length)];
    p.style.left = (Math.random() * 100) + 'vw';
    p.style.fontSize = (0.8 + Math.random() * 0.9) + 'rem';
    p.style.animationDuration = (9 + Math.random() * 14) + 's';
    p.style.animationDelay = (Math.random() * 12) + 's';
    petalsBg.appendChild(p);
  })(i);
}

// Octopus rain
function startOctos() {
  stopOctos();
  octoLayer.className = 'octo-layer active';
  for (var i = 0; i < 18; i++) {
    (function(i) { setTimeout(function() { spawnOcto(); }, i * 300); })(i);
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
  setTimeout(function() { if (o.parentNode) o.remove(); }, ttl);
}

function stopOctos() {
  if (octoInterval) { clearInterval(octoInterval); octoInterval = null; }
  octoLayer.className = 'octo-layer';
  octoLayer.innerHTML = '';
}
</script>
</body>
</html>
