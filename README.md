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
      transition: background 1s ease, color 1s ease;
    }

    /* ── Blue mode ── */
    body.blue-mode {
      background: #0d1b2e;
      color: #cce4ff;
    }
    body.blue-mode .hero h1,
    body.blue-mode .btn-label { color: #a8d4ff; }
    body.blue-mode .hero-sub,
    body.blue-mode .btn-hint,
    body.blue-mode .footer  { color: #6aaed6; }
    body.blue-mode .divider { background: linear-gradient(90deg, transparent, #5baee0, transparent); }
    body.blue-mode .envelope-btn {
      background: linear-gradient(135deg, #0f2a45 0%, #162e50 100%);
      border-color: #2a6496;
      box-shadow: 0 2px 16px rgba(91,174,224,.18);
    }
    body.blue-mode .envelope-btn:hover {
      border-color: #5baee0;
      box-shadow: 0 8px 32px rgba(91,174,224,.35);
    }
    body.blue-mode .btn-arrow { color: #5baee0; }
    body.blue-mode .overlay  { background: rgba(5,18,35,.6); }
    body.blue-mode .letter-card {
      background: #0e2038;
      border-color: #2a5f8a;
      box-shadow: 0 24px 80px rgba(0,80,160,.4);
      color: #cce4ff;
    }
    body.blue-mode .letter-title { color: #a8d4ff; }
    body.blue-mode .letter-body  { color: #cce4ff; }
    body.blue-mode .letter-title::after { background: linear-gradient(90deg, transparent, #5baee0, transparent); }
    body.blue-mode .letter-card::before,
    body.blue-mode .letter-card::after  { color: #5baee0; }
    body.blue-mode .letter-close {
      background: linear-gradient(135deg, #1a6fad, #2a9bd4);
      box-shadow: 0 4px 18px rgba(42,155,212,.4);
    }
    body.blue-mode .petals-bg { display: none; }

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

    /* ── Octopus border rain ── */
    .octo-container {
      position: fixed;
      inset: 0;
      pointer-events: none;
      z-index: 101;
      overflow: hidden;
      display: none;
    }
    .octo-container.active { display: block; }
    .octo {
      position: absolute;
      font-size: 1.6rem;
      opacity: 0;
      animation: octoFall linear infinite;
    }
    @keyframes octoFall {
      0%   { opacity: 0; transform: translateY(-80px) rotate(0deg) scale(.7); }
      10%  { opacity: .85; }
      90%  { opacity: .6; }
      100% { opacity: 0; transform: translateY(110vh) rotate(400deg) scale(1.1); }
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
      transition: color 1s;
    }
    .hero-sub {
      margin-top: 14px;
      font-size: .95rem;
      color: var(--muted);
      letter-spacing: .06em;
      animation: fadeDown .9s .35s ease both;
      transition: color 1s;
    }
    .divider {
      margin: 28px auto 0;
      width: 80px;
      height: 2px;
      background: linear-gradient(90deg, transparent, var(--rose), transparent);
      border-radius: 2px;
      animation: fadeDown .9s .45s ease both;
      transition: background 1s;
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
      transition: transform .22s ease, box-shadow .22s ease, border-color .22s ease, background 1s, color 1s;
      box-shadow: 0 2px 16px rgba(244,167,185,.18);
      animation: fadeUp .7s ease both;
      overflow: hidden;
    }
    .envelope-btn:nth-child(1) { animation-delay: .55s; }
    .envelope-btn:nth-child(2) { animation-delay: .68s; }
    .envelope-btn:nth-child(3) { animation-delay: .81s; }
    .envelope-btn:nth-child(4) { animation-delay: .94s; }
    .envelope-btn:nth-child(5) { animation-delay:1.07s; }
    .envelope-btn:nth-child(6) { animation-delay:1.20s; }

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
      transition: color 1s;
    }
    .btn-hint {
      font-family: 'Lora', serif;
      font-size: .78rem;
      color: var(--muted);
      margin-top: 3px;
      font-style: normal;
      transition: color 1s;
    }
    .btn-arrow {
      margin-left: auto;
      font-size: 1.1rem;
      color: var(--rose);
      transition: transform .25s, color 1s;
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
      transition: opacity .35s ease, background 1s;
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
      transition: transform .4s cubic-bezier(.34,1.56,.64,1), background 1s, border-color 1s, color 1s, box-shadow 1s;
      padding: 48px 40px 40px;
      border: 1.5px solid #f5d5e0;
    }
    .overlay.open .letter-card {
      transform: scale(1) translateY(0);
    }

    .letter-card::-webkit-scrollbar { width: 5px; }
    .letter-card::-webkit-scrollbar-track { background: transparent; }
    .letter-card::-webkit-scrollbar-thumb { background: var(--rose); border-radius: 10px; }

    .letter-card::before,
    .letter-card::after {
      content: '✿';
      position: absolute;
      color: var(--rose);
      opacity: .5;
      font-size: 1.3rem;
      transition: color 1s;
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
      transition: color 1s;
    }
    .letter-title::after {
      content: '';
      display: block;
      margin: 10px auto 0;
      width: 60px;
      height: 2px;
      background: linear-gradient(90deg, transparent, var(--rose), transparent);
      border-radius: 2px;
      transition: background 1s;
    }

    .letter-body {
      font-size: 1rem;
      line-height: 1.85;
      white-space: pre-wrap;
      color: var(--text);
      transition: color 1s;
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
      transition: transform .2s, box-shadow .2s, background 1s;
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
      transition: color 1s;
    }
  </style>
</head>
<body>

<!-- Petal rain -->
<div class="petals-bg" id="petalsBg"></div>

<!-- Octopus border rain (blue card only) -->
<div class="octo-container" id="octoContainer"></div>

<!-- Hidden audio -->
<audio id="bgMusic" loop>
  <source src="data:audio/mpeg;base64,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
