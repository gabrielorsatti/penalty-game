<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>⚽ Economist FC — Penalty Shootout</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Oswald:wght@400;600;700&family=Bebas+Neue&family=Space+Mono:wght@400;700&display=swap');

  :root {
    --gold: #F5C518;
    --dark: #0a0a0f;
    --card-bg: #12121a;
    --green: #1a7a1a;
    --green-light: #2db52d;
    --white: #f0f0f0;
    --red: #e03030;
    --blue: #1e3a8a;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--dark);
    color: var(--white);
    font-family: 'Oswald', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* STADIUM BACKGROUND */
  .stadium-bg {
    position: fixed;
    inset: 0;
    background:
      radial-gradient(ellipse at 50% 110%, #1a4a1a 0%, transparent 60%),
      radial-gradient(ellipse at 50% -10%, #1e3a8a22 0%, transparent 50%),
      linear-gradient(180deg, #060610 0%, #0a0a0f 100%);
    z-index: 0;
  }

  .stars {
    position: fixed;
    inset: 0;
    background-image:
      radial-gradient(1px 1px at 20% 30%, white, transparent),
      radial-gradient(1px 1px at 80% 10%, white, transparent),
      radial-gradient(1px 1px at 40% 60%, white, transparent),
      radial-gradient(1px 1px at 70% 80%, white, transparent),
      radial-gradient(1px 1px at 10% 70%, rgba(255,255,255,0.5), transparent),
      radial-gradient(1px 1px at 90% 40%, rgba(255,255,255,0.5), transparent);
    z-index: 0;
    opacity: 0.3;
  }

  .container {
    position: relative;
    z-index: 1;
    max-width: 900px;
    margin: 0 auto;
    padding: 20px;
  }

  /* HEADER */
  .header {
    text-align: center;
    padding: 30px 0 20px;
    animation: slideDown 0.6s ease;
  }

  .header h1 {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(2.5rem, 8vw, 5rem);
    color: var(--gold);
    letter-spacing: 4px;
    text-shadow: 0 0 40px rgba(245,197,24,0.5), 0 4px 0 #8a6d00;
    line-height: 1;
  }

  .header .subtitle {
    font-size: 1rem;
    color: #888;
    letter-spacing: 3px;
    text-transform: uppercase;
    margin-top: 8px;
  }

  @keyframes slideDown {
    from { transform: translateY(-40px); opacity: 0; }
    to { transform: translateY(0); opacity: 1; }
  }

  /* SCORE BOARD */
  .scoreboard {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 20px;
    margin: 20px 0;
    background: linear-gradient(135deg, #1a1a2e, #16213e);
    border: 2px solid var(--gold);
    border-radius: 12px;
    padding: 16px 30px;
    box-shadow: 0 0 30px rgba(245,197,24,0.2);
  }

  .score-team {
    text-align: center;
    min-width: 120px;
  }

  .score-team .name {
    font-size: 0.75rem;
    letter-spacing: 2px;
    color: #aaa;
    text-transform: uppercase;
  }

  .score-team .score {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 3.5rem;
    color: var(--gold);
    line-height: 1;
  }

  .score-divider {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 2rem;
    color: #444;
  }

  .shots-remaining {
    font-size: 0.85rem;
    color: #666;
    letter-spacing: 1px;
  }

  /* PENALTY INDICATORS */
  .penalty-dots {
    display: flex;
    gap: 8px;
    justify-content: center;
    margin: 4px 0;
  }

  .dot {
    width: 16px;
    height: 16px;
    border-radius: 50%;
    border: 2px solid #444;
    background: transparent;
    transition: all 0.3s ease;
  }

  .dot.goal { background: var(--green-light); border-color: var(--green-light); box-shadow: 0 0 8px var(--green-light); }
  .dot.miss { background: var(--red); border-color: var(--red); }

  /* PITCH */
  .pitch-wrapper {
    position: relative;
    margin: 20px auto;
    max-width: 600px;
  }

  .pitch {
    background: linear-gradient(180deg,
      #1d5c1d 0%, #236b23 8%, #1d5c1d 16%, #236b23 24%,
      #1d5c1d 32%, #236b23 40%, #1d5c1d 48%, #236b23 56%,
      #1d5c1d 64%, #236b23 72%, #1d5c1d 80%, #236b23 88%,
      #1d5c1d 96%, #236b23 100%
    );
    border: 3px solid rgba(255,255,255,0.1);
    border-radius: 8px;
    position: relative;
    aspect-ratio: 4/3;
    overflow: hidden;
    cursor: crosshair;
    box-shadow: 0 20px 60px rgba(0,0,0,0.8), inset 0 0 40px rgba(0,0,0,0.3);
  }

  /* GOAL */
  .goal {
    position: absolute;
    top: 8%;
    left: 50%;
    transform: translateX(-50%);
    width: 55%;
    height: 28%;
    border: 3px solid rgba(255,255,255,0.9);
    background: rgba(255,255,255,0.05);
    z-index: 3;
  }

  /* Goal net lines */
  .goal::before {
    content: '';
    position: absolute;
    inset: 0;
    background-image:
      repeating-linear-gradient(0deg, transparent, transparent 14px, rgba(255,255,255,0.15) 14px, rgba(255,255,255,0.15) 15px),
      repeating-linear-gradient(90deg, transparent, transparent 14px, rgba(255,255,255,0.15) 14px, rgba(255,255,255,0.15) 15px);
  }

  /* Goal zones (click targets) */
  .goal-zone {
    position: absolute;
    cursor: crosshair;
    z-index: 5;
    transition: background 0.15s ease;
  }

  .goal-zone:hover { background: rgba(255,255,255,0.1) !important; }

  /* Penalty spot */
  .penalty-spot {
    position: absolute;
    bottom: 28%;
    left: 50%;
    transform: translateX(-50%);
    width: 8px;
    height: 8px;
    border-radius: 50%;
    background: white;
    opacity: 0.8;
    z-index: 4;
  }

  /* Penalty arc */
  .penalty-arc {
    position: absolute;
    bottom: 24%;
    left: 50%;
    transform: translateX(-50%);
    width: 28%;
    height: 14%;
    border: 2px solid rgba(255,255,255,0.5);
    border-top: none;
    border-radius: 0 0 100px 100px;
    z-index: 3;
  }

  /* Penalty area */
  .penalty-area {
    position: absolute;
    top: 36%;
    left: 50%;
    transform: translateX(-50%);
    width: 68%;
    height: 46%;
    border: 2px solid rgba(255,255,255,0.5);
    z-index: 3;
  }

  /* 6 yard box */
  .six-yard {
    position: absolute;
    top: 36%;
    left: 50%;
    transform: translateX(-50%);
    width: 38%;
    height: 22%;
    border: 2px solid rgba(255,255,255,0.5);
    z-index: 3;
  }

  /* GOALKEEPER */
  .goalkeeper {
    position: absolute;
    font-size: clamp(1.5rem, 4vw, 2.5rem);
    z-index: 6;
    transition: left 0.3s cubic-bezier(0.25, 0.46, 0.45, 0.94);
    filter: drop-shadow(0 2px 4px rgba(0,0,0,0.8));
    user-select: none;
    pointer-events: none;
  }

  /* BALL */
  .ball {
    position: absolute;
    font-size: clamp(1rem, 3vw, 1.8rem);
    z-index: 7;
    bottom: 30%;
    left: 50%;
    transform: translateX(-50%);
    transition: all 0.5s cubic-bezier(0.25, 0.46, 0.45, 0.94);
    filter: drop-shadow(0 2px 4px rgba(0,0,0,0.8));
    pointer-events: none;
  }

  .ball.shooting {
    transition: all 0.4s cubic-bezier(0.17, 0.67, 0.83, 0.67);
  }

  /* RESULT FLASH */
  .result-flash {
    position: absolute;
    inset: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 20;
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.2s;
  }

  .result-flash.visible { opacity: 1; }

  .result-flash .result-text {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(3rem, 10vw, 6rem);
    letter-spacing: 4px;
    text-shadow: 0 4px 20px rgba(0,0,0,0.8);
    animation: popIn 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
  }

  .result-flash.goal-result { background: rgba(29, 92, 29, 0.7); }
  .result-flash.miss-result { background: rgba(180, 20, 20, 0.6); }
  .result-flash.saved-result { background: rgba(20, 40, 120, 0.7); }

  @keyframes popIn {
    from { transform: scale(0.5); opacity: 0; }
    to { transform: scale(1); opacity: 1; }
  }

  /* CROWD NOISE INDICATOR */
  .crowd {
    text-align: center;
    font-size: 0.8rem;
    letter-spacing: 1px;
    color: #555;
    height: 20px;
    margin: 4px 0;
    transition: all 0.3s;
  }

  /* SHOT BUTTON */
  .shoot-btn {
    display: block;
    width: 100%;
    max-width: 300px;
    margin: 15px auto;
    padding: 14px 40px;
    background: linear-gradient(135deg, var(--gold), #c9a000);
    color: #000;
    border: none;
    border-radius: 8px;
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.4rem;
    letter-spacing: 3px;
    cursor: pointer;
    transition: all 0.2s ease;
    box-shadow: 0 4px 20px rgba(245,197,24,0.4);
  }

  .shoot-btn:hover:not(:disabled) {
    transform: translateY(-2px);
    box-shadow: 0 6px 30px rgba(245,197,24,0.6);
  }

  .shoot-btn:active:not(:disabled) { transform: translateY(0); }
  .shoot-btn:disabled { opacity: 0.4; cursor: not-allowed; }

  /* INSTRUCTIONS */
  .instructions {
    text-align: center;
    font-size: 0.85rem;
    color: #666;
    letter-spacing: 1px;
    margin: 8px 0;
  }

  /* STATS CARD */
  .stats-section {
    margin-top: 40px;
    animation: fadeIn 0.8s ease 0.3s both;
  }

  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .section-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 2rem;
    color: var(--gold);
    letter-spacing: 4px;
    text-align: center;
    margin-bottom: 20px;
    position: relative;
  }

  .section-title::after {
    content: '';
    display: block;
    width: 60px;
    height: 3px;
    background: var(--gold);
    margin: 8px auto 0;
  }

  /* FIFA PLAYER CARD */
  .fifa-card {
    background: linear-gradient(135deg, #b8860b 0%, #f5c518 25%, #ffd700 50%, #f5c518 75%, #b8860b 100%);
    border-radius: 16px;
    padding: 3px;
    max-width: 340px;
    margin: 0 auto 30px;
    box-shadow: 0 20px 60px rgba(245,197,24,0.4), 0 0 0 1px rgba(255,255,255,0.1);
  }

  .fifa-card-inner {
    background: linear-gradient(160deg, #1a1a2e 0%, #16213e 40%, #0f3460 100%);
    border-radius: 13px;
    padding: 20px;
    display: grid;
    grid-template-columns: auto 1fr;
    gap: 16px;
    align-items: start;
  }

  .card-left {
    text-align: center;
  }

  .card-rating {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 3rem;
    color: var(--gold);
    line-height: 1;
  }

  .card-position {
    font-size: 0.7rem;
    color: var(--gold);
    letter-spacing: 2px;
    font-weight: 700;
  }

  .card-flag {
    font-size: 1.5rem;
    margin-top: 8px;
  }

  .card-avatar {
    font-size: 4rem;
    margin: 8px 0;
    filter: drop-shadow(0 4px 8px rgba(0,0,0,0.6));
  }

  .card-right {
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  .card-name {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.6rem;
    color: var(--white);
    letter-spacing: 2px;
    border-bottom: 1px solid rgba(245,197,24,0.3);
    padding-bottom: 8px;
    margin-bottom: 10px;
  }

  .card-stats-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 6px;
  }

  .card-stat {
    display: flex;
    align-items: center;
    gap: 6px;
  }

  .stat-val {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.2rem;
    color: var(--gold);
    min-width: 28px;
  }

  .stat-name {
    font-size: 0.65rem;
    color: #aaa;
    letter-spacing: 1px;
    text-transform: uppercase;
  }

  /* XP BARS */
  .xp-bars {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
    margin-top: 20px;
  }

  .xp-bar-item {
    background: rgba(255,255,255,0.03);
    border: 1px solid rgba(245,197,24,0.15);
    border-radius: 8px;
    padding: 12px;
  }

  .xp-label {
    display: flex;
    justify-content: space-between;
    font-size: 0.75rem;
    color: #888;
    letter-spacing: 1px;
    margin-bottom: 6px;
    text-transform: uppercase;
  }

  .xp-label span:last-child {
    color: var(--gold);
    font-weight: 700;
  }

  .xp-track {
    height: 6px;
    background: rgba(255,255,255,0.08);
    border-radius: 3px;
    overflow: hidden;
  }

  .xp-fill {
    height: 100%;
    border-radius: 3px;
    background: linear-gradient(90deg, var(--gold), #ff9f0a);
    transform-origin: left;
    animation: fillBar 1.5s cubic-bezier(0.22, 1, 0.36, 1) forwards;
    transform: scaleX(0);
  }

  @keyframes fillBar {
    to { transform: scaleX(1); }
  }

  /* CAREER TIMELINE */
  .career-timeline {
    margin-top: 30px;
    position: relative;
  }

  .career-timeline::before {
    content: '';
    position: absolute;
    left: 28px;
    top: 0;
    bottom: 0;
    width: 2px;
    background: linear-gradient(180deg, var(--gold), transparent);
  }

  .career-item {
    display: flex;
    gap: 20px;
    align-items: flex-start;
    margin-bottom: 20px;
    padding-left: 60px;
    position: relative;
    animation: slideRight 0.5s ease both;
  }

  .career-item:nth-child(1) { animation-delay: 0.1s; }
  .career-item:nth-child(2) { animation-delay: 0.2s; }
  .career-item:nth-child(3) { animation-delay: 0.3s; }
  .career-item:nth-child(4) { animation-delay: 0.4s; }

  @keyframes slideRight {
    from { transform: translateX(-20px); opacity: 0; }
    to { transform: translateX(0); opacity: 1; }
  }

  .career-icon {
    position: absolute;
    left: 14px;
    top: 4px;
    width: 28px;
    height: 28px;
    border-radius: 50%;
    background: var(--gold);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 0.9rem;
    box-shadow: 0 0 15px rgba(245,197,24,0.5);
    flex-shrink: 0;
  }

  .career-body {
    background: rgba(255,255,255,0.03);
    border: 1px solid rgba(245,197,24,0.15);
    border-radius: 10px;
    padding: 12px 16px;
    flex: 1;
  }

  .career-club {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.1rem;
    color: var(--gold);
    letter-spacing: 2px;
  }

  .career-role {
    font-size: 0.75rem;
    color: #888;
    letter-spacing: 1px;
    margin-top: 2px;
    text-transform: uppercase;
  }

  .career-desc {
    font-size: 0.8rem;
    color: #ccc;
    margin-top: 6px;
    line-height: 1.5;
    font-family: 'Space Mono', monospace;
  }

  .career-badge {
    display: inline-block;
    background: rgba(245,197,24,0.15);
    border: 1px solid rgba(245,197,24,0.3);
    color: var(--gold);
    font-size: 0.65rem;
    padding: 2px 8px;
    border-radius: 4px;
    letter-spacing: 1px;
    margin-top: 8px;
  }

  /* GAME OVER MODAL */
  .modal {
    display: none;
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,0.85);
    z-index: 100;
    align-items: center;
    justify-content: center;
    animation: fadeInBg 0.3s ease;
  }

  .modal.open { display: flex; }

  @keyframes fadeInBg {
    from { opacity: 0; }
    to { opacity: 1; }
  }

  .modal-box {
    background: linear-gradient(135deg, #1a1a2e, #16213e);
    border: 2px solid var(--gold);
    border-radius: 16px;
    padding: 40px;
    text-align: center;
    max-width: 380px;
    width: 90%;
    animation: popIn 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
    box-shadow: 0 30px 80px rgba(0,0,0,0.9), 0 0 40px rgba(245,197,24,0.3);
  }

  .modal-trophy { font-size: 4rem; margin-bottom: 10px; }

  .modal-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 2.5rem;
    color: var(--gold);
    letter-spacing: 4px;
    margin-bottom: 8px;
  }

  .modal-score {
    font-size: 3rem;
    font-family: 'Bebas Neue', sans-serif;
    color: white;
    margin: 10px 0;
  }

  .modal-message {
    font-size: 0.9rem;
    color: #888;
    letter-spacing: 1px;
    margin-bottom: 20px;
    font-family: 'Space Mono', monospace;
  }

  .restart-btn {
    background: var(--gold);
    color: #000;
    border: none;
    border-radius: 8px;
    padding: 12px 30px;
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.2rem;
    letter-spacing: 2px;
    cursor: pointer;
    transition: all 0.2s;
  }

  .restart-btn:hover { transform: scale(1.05); }

  /* TARGET CURSOR EFFECT */
  .aim-indicator {
    position: absolute;
    width: 20px;
    height: 20px;
    pointer-events: none;
    z-index: 10;
    transform: translate(-50%, -50%);
    opacity: 0;
    transition: opacity 0.2s;
  }

  .aim-indicator::before,
  .aim-indicator::after {
    content: '';
    position: absolute;
    background: rgba(255,255,255,0.8);
  }

  .aim-indicator::before {
    width: 100%;
    height: 1px;
    top: 50%;
    left: 0;
  }

  .aim-indicator::after {
    width: 1px;
    height: 100%;
    left: 50%;
    top: 0;
  }

  @media (max-width: 600px) {
    .xp-bars { grid-template-columns: 1fr; }
    .fifa-card-inner { grid-template-columns: 1fr; text-align: center; }
    .card-stats-grid { grid-template-columns: repeat(3, 1fr); }
    .career-item { padding-left: 50px; }
  }
</style>
</head>
<body>

<div class="stadium-bg"></div>
<div class="stars"></div>

<div class="container">

  <!-- HEADER -->
  <div class="header">
    <h1>⚽ ECONOMIST FC</h1>
    <p class="subtitle">Where Regression Meets The Beautiful Game</p>
  </div>

  <!-- SCOREBOARD -->
  <div class="scoreboard">
    <div class="score-team">
      <div class="name">🧑 VOUS</div>
      <div class="score" id="player-score">0</div>
      <div class="penalty-dots" id="player-dots"></div>
    </div>
    <div style="text-align:center">
      <div class="score-divider">VS</div>
      <div class="shots-remaining" id="shots-left">5 tirs restants</div>
    </div>
    <div class="score-team">
      <div class="name">🥅 GARDIEN</div>
      <div class="score" id="keeper-score">0</div>
      <div class="penalty-dots" id="keeper-dots"></div>
    </div>
  </div>

  <!-- CROWD STATUS -->
  <div class="crowd" id="crowd-text">🏟️ Cliquez sur le but pour viser votre tir !</div>

  <!-- PITCH -->
  <div class="pitch-wrapper">
    <div class="pitch" id="pitch">
      <!-- Markings -->
      <div class="penalty-area"></div>
      <div class="six-yard"></div>
      <div class="goal" id="goal">
        <!-- 9 click zones: 3x3 grid -->
        <div class="goal-zone" id="zone-TL" style="top:0;left:0;width:33.3%;height:50%" data-zone="top-left"></div>
        <div class="goal-zone" id="zone-TC" style="top:0;left:33.3%;width:33.3%;height:50%" data-zone="top-center"></div>
        <div class="goal-zone" id="zone-TR" style="top:0;left:66.6%;width:33.4%;height:50%" data-zone="top-right"></div>
        <div class="goal-zone" id="zone-ML" style="top:50%;left:0;width:33.3%;height:50%" data-zone="mid-left"></div>
        <div class="goal-zone" id="zone-MC" style="top:50%;left:33.3%;width:33.3%;height:50%" data-zone="mid-center"></div>
        <div class="goal-zone" id="zone-MR" style="top:50%;left:66.6%;width:33.4%;height:50%" data-zone="mid-right"></div>
      </div>
      <div class="penalty-arc"></div>
      <div class="penalty-spot"></div>

      <!-- Goalkeeper -->
      <div class="goalkeeper" id="goalkeeper">🧤</div>

      <!-- Ball -->
      <div class="ball" id="ball">⚽</div>

      <!-- Aim indicator -->
      <div class="aim-indicator" id="aim"></div>

      <!-- Result flash -->
      <div class="result-flash" id="result-flash">
        <div class="result-text" id="result-text"></div>
      </div>
    </div>
  </div>

  <!-- SHOOT BUTTON -->
  <button class="shoot-btn" id="shoot-btn" disabled>⚽ CHOISISSEZ UNE ZONE</button>
  <p class="instructions" id="instructions">👆 Cliquez sur le cadre du but pour viser</p>

  <!-- GAME OVER MODAL -->
  <div class="modal" id="modal">
    <div class="modal-box">
      <div class="modal-trophy" id="modal-trophy">🏆</div>
      <div class="modal-title" id="modal-title">GAME OVER</div>
      <div class="modal-score" id="modal-score-display">0 / 5</div>
      <div class="modal-message" id="modal-message">Série terminée</div>
      <button class="restart-btn" onclick="restartGame()">🔁 NOUVELLE SÉRIE</button>
    </div>
  </div>

  <!-- STATS SECTION -->
  <div class="stats-section">
    <div class="section-title">🏆 CHAMPION STATS CARD</div>

    <!-- FIFA CARD -->
    <div class="fifa-card">
      <div class="fifa-card-inner">
        <div class="card-left">
          <div class="card-rating">94</div>
          <div class="card-position">ECO</div>
          <div class="card-avatar">🧑‍💼</div>
          <div class="card-flag">🇫🇷</div>
        </div>
        <div class="card-right">
          <div class="card-name">ECONOMIST</div>
          <div class="card-stats-grid">
            <div class="card-stat"><span class="stat-val">97</span><span class="stat-name">Macro</span></div>
            <div class="card-stat"><span class="stat-val">95</span><span class="stat-name">R²</span></div>
            <div class="card-stat"><span class="stat-val">93</span><span class="stat-name">Policy</span></div>
            <div class="card-stat"><span class="stat-val">91</span><span class="stat-name">IV</span></div>
            <div class="card-stat"><span class="stat-val">94</span><span class="stat-name">Data</span></div>
            <div class="card-stat"><span class="stat-val">96</span><span class="stat-name">Pres.</span></div>
          </div>
        </div>
      </div>
    </div>

    <!-- XP BARS -->
    <div class="xp-bars">
      <div class="xp-bar-item">
        <div class="xp-label"><span>⚽ Buts (papers publiés)</span><span>8</span></div>
        <div class="xp-track"><div class="xp-fill" style="width:80%;animation-delay:0.1s"></div></div>
      </div>
      <div class="xp-bar-item">
        <div class="xp-label"><span>🎯 Passes déc. (collaborations)</span><span>14</span></div>
        <div class="xp-track"><div class="xp-fill" style="width:70%;animation-delay:0.2s"></div></div>
      </div>
      <div class="xp-bar-item">
        <div class="xp-label"><span>📐 xG (régressions scorées)</span><span>312</span></div>
        <div class="xp-track"><div class="xp-fill" style="width:97%;animation-delay:0.3s"></div></div>
      </div>
      <div class="xp-bar-item">
        <div class="xp-label"><span>🛡️ Clean sheets (R² > 0.9)</span><span>89%</span></div>
        <div class="xp-track"><div class="xp-fill" style="width:89%;animation-delay:0.4s"></div></div>
      </div>
      <div class="xp-bar-item">
        <div class="xp-label"><span>🔑 Interceptions (IV instruments)</span><span>47</span></div>
        <div class="xp-track"><div class="xp-fill" style="width:94%;animation-delay:0.5s"></div></div>
      </div>
      <div class="xp-bar-item">
        <div class="xp-label"><span>🔢 DiD designs</span><span>23</span></div>
        <div class="xp-track"><div class="xp-fill" style="width:92%;animation-delay:0.6s"></div></div>
      </div>
      <div class="xp-bar-item">
        <div class="xp-label"><span>📊 p-values < 0.05</span><span>96%</span></div>
        <div class="xp-track"><div class="xp-fill" style="width:96%;animation-delay:0.7s"></div></div>
      </div>
      <div class="xp-bar-item">
        <div class="xp-label"><span>🏹 Tirs cadrés (talks conférences)</span><span>31</span></div>
        <div class="xp-track"><div class="xp-fill" style="width:78%;animation-delay:0.8s"></div></div>
      </div>
    </div>

    <!-- CAREER TIMELINE -->
    <div class="section-title" style="margin-top:40px">📋 PARCOURS — TRANSFER HISTORY</div>
    <div class="career-timeline">

      <div class="career-item">
        <div class="career-icon">📚</div>
        <div class="career-body">
          <div class="career-club">ÉCOLE D'ÉCONOMIE DE PARIS</div>
          <div class="career-role">Académie d'élite • Formation avancée</div>
          <div class="career-desc">Entraînement tactique intensif en micro, macro et économétrie. Formation au pressing haut niveau — style de jeu : théorie des jeux + causalité.</div>
          <span class="career-badge">⭐ ACADÉMIE PREMIUM</span>
        </div>
      </div>

      <div class="career-item">
        <div class="career-icon">🌍</div>
        <div class="career-body">
          <div class="career-club">BANQUE MONDIALE — ROME</div>
          <div class="career-role">Prêt international • Bureau Italie</div>
          <div class="career-desc">Déplacement sur le terrain international. Analyses de politiques publiques mondiales, évaluation d'impact en contexte développement. Expérience UEFA Champions League.</div>
          <span class="career-badge">🌍 INTERNATIONAL CAP</span>
        </div>
      </div>

      <div class="career-item">
        <div class="career-icon">📋</div>
        <div class="career-body">
          <div class="career-club">INSTITUT DES POLITIQUES PUBLIQUES</div>
          <div class="career-role">Milieu créatif • Design de politiques</div>
          <div class="career-desc">Rôle pivot entre recherche académique et décision publique. Maîtrise des évaluations de politiques éducatives et sociales. Schéma de jeu : RDD + DiD.</div>
          <span class="career-badge">🧠 THINK-TANK CLUB</span>
        </div>
      </div>

      <div class="career-item">
        <div class="career-icon">🏦</div>
        <div class="career-body">
          <div class="career-club">BANQUE DE FRANCE</div>
          <div class="career-role">Attaquant macro • Analyse monétaire</div>
          <div class="career-desc">Le club le plus prestigieux de la Ligue française. Modélisation macro-financière, conjoncture économique, prévision. VAR (Vector AutoRegression) comme arme de prédilection.</div>
          <span class="career-badge">🏆 LIGUE 1 PRESTIGE</span>
        </div>
      </div>

    </div>

  </div><!-- end stats-section -->

  <div style="text-align:center; padding: 40px 0 20px; color: #333; font-size: 0.75rem; letter-spacing: 2px; font-family: 'Space Mono', monospace;">
    ⚽ "IN GOD WE TRUST. ALL OTHERS MUST BRING DATA." ⚽
  </div>

</div><!-- end container -->

<script>
// ═══════════════════════════════════════
//  PENALTY GAME ENGINE
// ═══════════════════════════════════════

const TOTAL_SHOTS = 5;
let playerGoals = 0;
let keeperSaves = 0;
let shotsRemaining = TOTAL_SHOTS;
let selectedZone = null;
let isAnimating = false;

// Zone positions relative to pitch (for ball animation)
const zoneCoords = {
  'top-left':    { x: 22, y: 12 },
  'top-center':  { x: 50, y: 12 },
  'top-right':   { x: 78, y: 12 },
  'mid-left':    { x: 22, y: 25 },
  'mid-center':  { x: 50, y: 25 },
  'mid-right':   { x: 78, y: 25 },
};

// Keeper behavior per zone
const keeperSaveProbability = {
  'top-left': 0.15,
  'top-center': 0.35,
  'top-right': 0.15,
  'mid-left': 0.25,
  'mid-center': 0.45,
  'mid-right': 0.25,
};

const keeperPositions = {
  'top-left': 20, 'mid-left': 20,
  'top-center': 45, 'mid-center': 45,
  'top-right': 72, 'mid-right': 72,
};

const crowdReactions = {
  goal: ["⚽ BUUUUT ! 🎉", "🔥 QUEL COUP DE PIED !", "🏟️ INCROYABLE ! THE NET IS SHAKING !", "💥 GOOOAL ! LA FOULE EST EN DÉLIRE !"],
  saved: ["🧤 ARRÊT ! Le gardien économise tout !", "🚫 SAUVÉ ! Le gardien fait son RDD !", "😱 Le modèle logit prédit... l'arrêt !"],
  miss: ["❌ RATÉ ! La balle sort du cadre !", "🌬️ À côté ! L'erreur standard était trop grande !", "📉 Hors cadre — R² = 0.00 ce tir-là..."]
};

function initDots() {
  const pDots = document.getElementById('player-dots');
  const kDots = document.getElementById('keeper-dots');
  pDots.innerHTML = '';
  kDots.innerHTML = '';
  for (let i = 0; i < TOTAL_SHOTS; i++) {
    pDots.innerHTML += `<div class="dot" id="pdot-${i}"></div>`;
    kDots.innerHTML += `<div class="dot" id="kdot-${i}"></div>`;
  }
}

function setupZoneListeners() {
  document.querySelectorAll('.goal-zone').forEach(zone => {
    zone.addEventListener('click', () => {
      if (isAnimating) return;
      selectedZone = zone.dataset.zone;
      document.querySelectorAll('.goal-zone').forEach(z => z.style.background = '');
      zone.style.background = 'rgba(245,197,24,0.2)';
      document.getElementById('shoot-btn').disabled = false;
      document.getElementById('instructions').textContent = `🎯 Zone visée : ${zoneLabel(selectedZone)} — Cliquez SHOOT !`;
      document.getElementById('crowd-text').textContent = '🎯 Zone sélectionnée ! Le gardien se prépare...';
    });
  });
}

function zoneLabel(zone) {
  const labels = {
    'top-left':'Haut gauche','top-center':'Haut centre','top-right':'Haut droite',
    'mid-left':'Milieu gauche','mid-center':'Centre','mid-right':'Milieu droite'
  };
  return labels[zone] || zone;
}

document.getElementById('shoot-btn').addEventListener('click', () => {
  if (!selectedZone || isAnimating || shotsRemaining <= 0) return;
  shoot();
});

function shoot() {
  isAnimating = true;
  document.getElementById('shoot-btn').disabled = true;

  const zone = selectedZone;
  const saveProbability = keeperSaveProbability[zone];
  const isSaved = Math.random() < saveProbability;
  const coords = zoneCoords[zone];

  // Move goalkeeper
  const keeperPos = keeperPositions[zone];
  const gk = document.getElementById('goalkeeper');
  const pitchW = document.getElementById('pitch').offsetWidth;
  const pitchH = document.getElementById('pitch').offsetHeight;
  gk.style.left = `${keeperPos}%`;
  gk.style.top = `${pitchH * 0.08}px`;
  gk.style.transform = 'translateX(-50%)';

  // Animate ball
  const ball = document.getElementById('ball');
  ball.classList.add('shooting');

  if (isSaved) {
    // Ball goes toward goal but keeper gets there
    ball.style.left = `${coords.x}%`;
    ball.style.bottom = `${100 - coords.y}%`;
    ball.style.transform = 'translateX(-50%) scale(0.6)';
  } else {
    // Ball goes into net
    ball.style.left = `${coords.x}%`;
    ball.style.bottom = `${100 - coords.y}%`;
    ball.style.transform = 'translateX(-50%) scale(0.5)';
  }

  setTimeout(() => {
    showResult(isSaved, zone);
  }, 500);
}

function showResult(isSaved, zone) {
  const shotIndex = TOTAL_SHOTS - shotsRemaining;
  const flash = document.getElementById('result-flash');
  const resultText = document.getElementById('result-text');

  if (isSaved) {
    keeperSaves++;
    document.getElementById('keeper-score').textContent = keeperSaves;
    flash.className = 'result-flash saved-result visible';
    resultText.textContent = '🧤 ARRÊT !';
    resultText.style.color = '#7eb8ff';
    document.getElementById(`kdot-${shotIndex}`).classList.add('goal');
    document.getElementById(`pdot-${shotIndex}`).classList.add('miss');
    const r = crowdReactions.saved;
    document.getElementById('crowd-text').textContent = r[Math.floor(Math.random()*r.length)];
  } else {
    playerGoals++;
    document.getElementById('player-score').textContent = playerGoals;
    flash.className = 'result-flash goal-result visible';
    resultText.textContent = '⚽ BUUUT !';
    resultText.style.color = '#7eff9a';
    document.getElementById(`pdot-${shotIndex}`).classList.add('goal');
    document.getElementById(`kdot-${shotIndex}`).classList.add('miss');
    const r = crowdReactions.goal;
    document.getElementById('crowd-text').textContent = r[Math.floor(Math.random()*r.length)];
  }

  shotsRemaining--;
  const sl = document.getElementById('shots-left');
  sl.textContent = shotsRemaining > 0 ? `${shotsRemaining} tir${shotsRemaining>1?'s':''} restant${shotsRemaining>1?'s':''}` : 'Série terminée';

  setTimeout(() => {
    flash.className = 'result-flash';
    resetBall();
    if (shotsRemaining <= 0) {
      setTimeout(showGameOver, 400);
    } else {
      isAnimating = false;
      selectedZone = null;
      document.querySelectorAll('.goal-zone').forEach(z => z.style.background = '');
      document.getElementById('instructions').textContent = '👆 Cliquez sur le cadre du but pour viser';
      document.getElementById('crowd-text').textContent = '🏟️ Prochain tir — choisissez votre zone !';
    }
  }, 1200);
}

function resetBall() {
  const ball = document.getElementById('ball');
  ball.classList.remove('shooting');
  ball.style.left = '50%';
  ball.style.bottom = '30%';
  ball.style.transform = 'translateX(-50%)';
  ball.style.transition = 'none';
  setTimeout(() => { ball.style.transition = ''; }, 50);

  // Reset keeper to center
  const pitchH = document.getElementById('pitch').offsetHeight;
  const gk = document.getElementById('goalkeeper');
  gk.style.left = '47%';
  gk.style.top = `${pitchH * 0.08}px`;
}

function showGameOver() {
  const modal = document.getElementById('modal');
  const trophy = document.getElementById('modal-trophy');
  const title = document.getElementById('modal-title');
  const scoreDisp = document.getElementById('modal-score-display');
  const msg = document.getElementById('modal-message');

  scoreDisp.textContent = `${playerGoals} / ${TOTAL_SHOTS}`;

  if (playerGoals >= 5) {
    trophy.textContent = '🏆'; title.textContent = 'PARFAIT !';
    msg.textContent = '100% de précision — Digne d\'un économètre !';
  } else if (playerGoals >= 4) {
    trophy.textContent = '🥇'; title.textContent = 'EXCELLENT !';
    msg.textContent = 'R² = 0.98 — Régression quasi-parfaite !';
  } else if (playerGoals >= 3) {
    trophy.textContent = '🥈'; title.textContent = 'BIEN JOUÉ !';
    msg.textContent = 'xG atteint — La loi des grands nombres approuve.';
  } else if (playerGoals >= 2) {
    trophy.textContent = '🥉'; title.textContent = 'PAS MAL';
    msg.textContent = 'Significatif à 5% mais la variance reste haute...';
  } else {
    trophy.textContent = '📉'; title.textContent = 'PLUS DE DONNÉES';
    msg.textContent = 'Résultat non significatif. Recommencer l\'échantillon.';
  }

  modal.classList.add('open');
}

function restartGame() {
  playerGoals = 0;
  keeperSaves = 0;
  shotsRemaining = TOTAL_SHOTS;
  selectedZone = null;
  isAnimating = false;

  document.getElementById('player-score').textContent = '0';
  document.getElementById('keeper-score').textContent = '0';
  document.getElementById('shots-left').textContent = `${TOTAL_SHOTS} tirs restants`;
  document.getElementById('shoot-btn').disabled = true;
  document.getElementById('instructions').textContent = '👆 Cliquez sur le cadre du but pour viser';
  document.getElementById('crowd-text').textContent = '🏟️ Cliquez sur le but pour viser votre tir !';
  document.getElementById('modal').classList.remove('open');
  document.querySelectorAll('.goal-zone').forEach(z => z.style.background = '');
  resetBall();
  initDots();
}

// INIT
initDots();
setupZoneListeners();

// Position goalkeeper
window.addEventListener('load', () => {
  const pitch = document.getElementById('pitch');
  const pitchH = pitch.offsetHeight;
  const gk = document.getElementById('goalkeeper');
  gk.style.left = '47%';
  gk.style.top = `${pitchH * 0.08}px`;
});
</script>

</body>
</html>
