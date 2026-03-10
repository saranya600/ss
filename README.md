<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Happy Birthday Mama 💖</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400&family=Dancing+Script:wght@700&family=Lato:wght@300;400&display=swap" rel="stylesheet">
<style>
  :root {
    --rose: #ff6eb4;
    --lavender: #c77dff;
    --deep-purple: #7b2d8b;
    --blush: #ffd6ec;
    --gold: #ffd700;
    --white: #fff8ff;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    font-family: 'Lato', sans-serif;
    background: #1a0025;
    color: var(--white);
    overflow-x: hidden;
    min-height: 100vh;
  }

  /* ── BACKGROUND MESH ── */
  .bg-mesh {
    position: fixed; inset: 0; z-index: 0;
    background:
      radial-gradient(ellipse 80% 60% at 20% 30%, rgba(199,125,255,0.35) 0%, transparent 60%),
      radial-gradient(ellipse 70% 50% at 80% 70%, rgba(255,110,180,0.35) 0%, transparent 60%),
      radial-gradient(ellipse 60% 80% at 50% 50%, rgba(123,45,139,0.4) 0%, transparent 70%),
      #1a0025;
    animation: meshShift 8s ease-in-out infinite alternate;
  }
  @keyframes meshShift {
    0% { filter: hue-rotate(0deg) brightness(1); }
    100% { filter: hue-rotate(20deg) brightness(1.1); }
  }

  /* ── PAGES ── */
  .page {
    position: relative; z-index: 10;
    min-height: 100vh;
    display: none;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 40px 20px;
    text-align: center;
  }
  .page.active { display: flex; }

  /* ── PAGE 1: COUNTDOWN ── */
  #page-countdown { gap: 20px; }
  .countdown-number {
    font-family: 'Playfair Display', serif;
    font-size: clamp(6rem, 25vw, 14rem);
    font-weight: 700;
    background: linear-gradient(135deg, var(--lavender), var(--rose));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    animation: pulseNum 0.9s ease-in-out;
    text-shadow: none;
    filter: drop-shadow(0 0 30px rgba(199,125,255,0.8));
  }
  @keyframes pulseNum {
    0% { transform: scale(0.3); opacity: 0; }
    60% { transform: scale(1.15); opacity: 1; }
    100% { transform: scale(1); opacity: 1; }
  }
  .countdown-label {
    font-family: 'Dancing Script', cursive;
    font-size: 1.4rem;
    color: var(--blush);
    letter-spacing: 4px;
    animation: fadeSlide 0.9s ease forwards;
  }
  @keyframes fadeSlide {
    from { opacity: 0; transform: translateY(15px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* ── PAGE 2: MAIN BIRTHDAY ── */
  #page-main { gap: 30px; }

  .birthday-title {
    font-family: 'Dancing Script', cursive;
    font-size: clamp(2.2rem, 8vw, 4.5rem);
    background: linear-gradient(135deg, #fff0fb, var(--rose), var(--lavender), #fff0fb);
    background-size: 300% 300%;
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    animation: shimmer 3s ease infinite, entryDrop 1s ease forwards;
    filter: drop-shadow(0 0 20px rgba(255,110,180,0.6));
    line-height: 1.2;
  }
  @keyframes shimmer {
    0%,100% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
  }
  @keyframes entryDrop {
    from { opacity: 0; transform: translateY(-40px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* ── 3D ROTATING PHOTO ── */
  .photo-scene {
    perspective: 900px;
    width: 220px; height: 220px;
    cursor: pointer;
  }
  .photo-cube {
    width: 100%; height: 100%;
    position: relative;
    transform-style: preserve-3d;
    animation: spin3d 10s linear infinite;
    border-radius: 50%;
  }
  @keyframes spin3d {
    0% { transform: rotateY(0deg) rotateX(8deg); }
    100% { transform: rotateY(360deg) rotateX(8deg); }
  }
  .photo-face {
    position: absolute; inset: 0;
    border-radius: 50%;
    overflow: hidden;
    border: 4px solid transparent;
    background: linear-gradient(#1a0025, #1a0025) padding-box,
                linear-gradient(135deg, var(--rose), var(--lavender), var(--rose)) border-box;
    box-shadow:
      0 0 30px rgba(199,125,255,0.6),
      0 0 60px rgba(255,110,180,0.3),
      inset 0 0 20px rgba(199,125,255,0.15);
  }
  .photo-face img {
    width: 100%; height: 100%;
    object-fit: cover;
    border-radius: 50%;
  }

  /* Glow ring */
  .photo-glow {
    position: absolute;
    width: 260px; height: 260px;
    border-radius: 50%;
    top: 50%; left: 50%;
    transform: translate(-50%, -50%);
    background: radial-gradient(circle, rgba(255,110,180,0.25) 0%, transparent 70%);
    animation: glowPulse 2.5s ease-in-out infinite;
    pointer-events: none;
  }
  @keyframes glowPulse {
    0%,100% { transform: translate(-50%,-50%) scale(1); opacity: 0.7; }
    50% { transform: translate(-50%,-50%) scale(1.15); opacity: 1; }
  }

  /* ── SPECIAL MESSAGE BUTTON ── */
  .btn-spl {
    font-family: 'Dancing Script', cursive;
    font-size: 1.3rem;
    padding: 14px 36px;
    border: 2px solid var(--rose);
    border-radius: 50px;
    background: linear-gradient(135deg, rgba(255,110,180,0.2), rgba(199,125,255,0.2));
    color: var(--white);
    cursor: pointer;
    position: relative;
    overflow: hidden;
    transition: all 0.4s ease;
    backdrop-filter: blur(10px);
    letter-spacing: 1px;
    animation: buttonGlow 2s ease-in-out infinite;
  }
  @keyframes buttonGlow {
    0%,100% { box-shadow: 0 0 15px rgba(255,110,180,0.4), 0 0 30px rgba(199,125,255,0.2); }
    50% { box-shadow: 0 0 25px rgba(255,110,180,0.7), 0 0 50px rgba(199,125,255,0.4); }
  }
  .btn-spl::before {
    content: '';
    position: absolute; inset: 0;
    background: linear-gradient(135deg, var(--rose), var(--lavender));
    opacity: 0; transition: opacity 0.4s;
  }
  .btn-spl:hover::before { opacity: 1; }
  .btn-spl:hover { transform: scale(1.05) translateY(-2px); color: white; }
  .btn-spl span { position: relative; z-index: 1; }

  /* ── PAGE 3: LOVE LETTER ── */
  #page-letter { gap: 0; }

  .envelope-wrap {
    animation: letterEntry 0.8s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards;
  }
  @keyframes letterEntry {
    from { opacity: 0; transform: scale(0.3) rotate(-10deg); }
    to { opacity: 1; transform: scale(1) rotate(0deg); }
  }
  .envelope {
    width: min(380px, 90vw);
    background: linear-gradient(160deg, #fff0f8, #fde8f8);
    border-radius: 16px;
    padding: 40px 36px;
    color: #3a0050;
    box-shadow:
      0 20px 60px rgba(255,110,180,0.4),
      0 0 0 1px rgba(255,110,180,0.3);
    position: relative;
    overflow: hidden;
  }
  .envelope::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0; height: 6px;
    background: linear-gradient(90deg, var(--rose), var(--lavender), var(--rose));
  }
  .envelope-icon { font-size: 3.5rem; margin-bottom: 16px; animation: wiggle 2s ease-in-out infinite; }
  @keyframes wiggle {
    0%,100% { transform: rotate(0deg); }
    25% { transform: rotate(-8deg); }
    75% { transform: rotate(8deg); }
  }
  .letter-title {
    font-family: 'Playfair Display', serif;
    font-size: 1.5rem; font-style: italic;
    color: var(--deep-purple);
    margin-bottom: 20px;
  }
  .letter-text {
    font-family: 'Lato', sans-serif;
    font-size: 1rem; line-height: 1.85;
    color: #4a0060;
    text-align: left;
  }
  .letter-sign {
    font-family: 'Dancing Script', cursive;
    font-size: 1.6rem;
    color: var(--rose);
    margin-top: 24px;
    text-align: right;
  }
  .letter-seal {
    font-size: 2rem; margin-top: 16px;
    animation: sealPulse 1.5s ease-in-out infinite;
  }
  @keyframes sealPulse {
    0%,100% { transform: scale(1); }
    50% { transform: scale(1.2); }
  }

  /* ── PAGE 4: FUTURE QUESTION ── */
  #page-future { gap: 30px; }
  .future-q {
    font-family: 'Playfair Display', serif;
    font-size: clamp(1.4rem, 4vw, 2.2rem);
    font-style: italic;
    line-height: 1.5;
    max-width: 600px;
    background: linear-gradient(135deg, var(--blush), var(--lavender));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    filter: drop-shadow(0 0 15px rgba(199,125,255,0.5));
    animation: fadeSlide 1s ease forwards;
  }

  /* ── PAGE 5: PICTURE REVEAL ── */
  #page-reveal { gap: 28px; }

  .reveal-photo-wrap {
    position: relative;
    width: min(340px, 85vw);
  }
  .reveal-photo {
    width: 100%; border-radius: 20px;
    overflow: hidden;
    border: 3px solid transparent;
    background: linear-gradient(#1a0025,#1a0025) padding-box,
                linear-gradient(135deg, var(--rose), var(--lavender)) border-box;
    box-shadow: 0 0 40px rgba(255,110,180,0.5), 0 0 80px rgba(199,125,255,0.2);
    animation: revealIn 0.9s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards;
  }
  @keyframes revealIn {
    from { opacity: 0; transform: scale(0.5) rotate(-5deg); filter: blur(20px); }
    to { opacity: 1; transform: scale(1) rotate(0deg); filter: blur(0); }
  }
  .reveal-photo img {
    width: 100%; display: block;
    border-radius: 17px;
  }

  /* ── PAGE 6: SURPRISE ── */
  #page-surprise { gap: 24px; }
  .surprise-msg {
    max-width: 560px;
    background: linear-gradient(135deg, rgba(255,110,180,0.12), rgba(199,125,255,0.12));
    border: 1px solid rgba(255,110,180,0.4);
    border-radius: 24px;
    padding: 40px 36px;
    backdrop-filter: blur(20px);
    animation: surpriseEntry 1s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards;
    box-shadow: 0 0 50px rgba(255,110,180,0.3);
  }
  @keyframes surpriseEntry {
    from { opacity: 0; transform: translateY(60px) scale(0.8); }
    to { opacity: 1; transform: translateY(0) scale(1); }
  }
  .surprise-emoji { font-size: 3rem; margin-bottom: 16px; }
  .surprise-line {
    font-family: 'Playfair Display', serif;
    font-size: clamp(1.1rem, 3vw, 1.5rem);
    font-style: italic;
    line-height: 1.7;
    color: var(--white);
    filter: drop-shadow(0 0 10px rgba(255,110,180,0.5));
  }

  /* ── UTILITY ── */
  .divider {
    width: 80px; height: 2px;
    background: linear-gradient(90deg, transparent, var(--rose), var(--lavender), transparent);
    border-radius: 2px;
    margin: 4px auto;
  }

  .sparkle-text {
    font-family: 'Dancing Script', cursive;
    font-size: 1rem;
    color: var(--lavender);
    letter-spacing: 2px;
  }

  /* ── STARS CANVAS ── */
  #starfield { position: fixed; inset: 0; z-index: 1; pointer-events: none; }

  /* ── PETAL PARTICLES ── */
  .petal {
    position: fixed;
    font-size: 1rem;
    pointer-events: none;
    z-index: 2;
    animation: petalFall linear infinite;
    opacity: 0;
  }
  @keyframes petalFall {
    0% { transform: translateY(-20px) rotate(0deg) translateX(0); opacity: 0; }
    10% { opacity: 0.8; }
    100% { transform: translateY(110vh) rotate(720deg) translateX(80px); opacity: 0; }
  }

  /* ── RESPONSIVE ── */
  @media (max-width: 480px) {
    .envelope { padding: 28px 20px; }
    .surprise-msg { padding: 28px 20px; }
  }
</style>
</head>
<body>

<!-- Background -->
<div class="bg-mesh"></div>
<canvas id="starfield"></canvas>

<!-- ═══════════════════════════════════════════
     PAGE 1 — COUNTDOWN
════════════════════════════════════════════ -->
<div id="page-countdown" class="page active">
  <div class="sparkle-text">Get Ready For Something Special ✨</div>
  <div id="countdown-display" class="countdown-number">3</div>
  <div class="countdown-label">💖 A Birthday Surprise Awaits 💖</div>
</div>

<!-- ═══════════════════════════════════════════
     PAGE 2 — MAIN BIRTHDAY
════════════════════════════════════════════ -->
<div id="page-main" class="page">
  <div class="sparkle-text">✨ Today is Extra Special ✨</div>
  <div class="birthday-title">Happy Fabulous Birthday Mama! 🎂</div>
  <div class="divider"></div>

  <!-- 3D Rotating Photo -->
  <div style="position:relative; display:inline-block; margin: 10px 0;">
    <div class="photo-glow"></div>
    <div class="photo-scene">
      <div class="photo-cube">
        <div class="photo-face">
          <!-- Place DSC_2145.JPG in the same folder as this HTML file -->
          <img src="C:\Users\HP\OneDrive\Desktop\women's day songs\WhatsApp Image 2026-03-10 at 9.20.25 PM.jpeg" alt="Mama">
        </div>
      </div>
    </div>
  </div>

  <div class="sparkle-text">The Most Beautiful Soul 💜</div>

  <button class="btn-spl" onclick="goToLetter()">
    <span>💌 Read Your Special Message</span>
  </button>
</div>

<!-- ═══════════════════════════════════════════
     PAGE 3 — LOVE LETTER
════════════════════════════════════════════ -->
<div id="page-letter" class="page">
  <div class="envelope-wrap">
    <div class="envelope">
      <div class="envelope-icon">💌</div>
      <div class="letter-title">A Letter From The Heart</div>
      <div class="letter-text">
        Dear Mama,<br><br>
        I don't even know where to begin today. I may joke with you, tease you, and act normal, but deep inside I truly admire the man you are becoming. I see your hard work, your silent struggles, and the way you carry responsibilities without complaining.<br><br>
        Working night shifts, managing everything, and still building your future isn't easy, and I'm genuinely proud of you.<br><br>
        You have always had a special place in my heart, and no matter how much time passes or how our paths change, that care has never faded. I truly hope this year brings you success in your career, clarity in your dreams, and the stability and happiness you deserve. I want to see you win in life and reach heights that make you proud of yourself.<br><br>
        And if I'm being honest… I still miss the way we used to talk and the warmth we once shared. But even when things feel different, you are still very important to me. No matter what happens, I will always wish for your growth, your peace, and your happiness.<br><br>
        Keep chasing your dreams. I will always silently pray for your success.
      </div>
      <div class="letter-sign">Forever yours 💕</div>
      <div class="letter-seal">💖</div>
    </div>
  </div>
  <br>
  <button class="btn-spl" onclick="goToPage('page-future')" style="margin-top:20px;">
    <span>✨ Click to Continue</span>
  </button>
</div>

<!-- ═══════════════════════════════════════════
     PAGE 4 — FUTURE QUESTION
════════════════════════════════════════════ -->
<div id="page-future" class="page">
  <div class="sparkle-text">💭 A Little Question For You...</div>
  <div class="divider"></div>
  <div class="future-q">
    "Do you know how I'm going to take care of you in the future?"
  </div>
  <div class="divider"></div>
  <div class="sparkle-text" style="font-size:0.9rem; opacity:0.8;">Click below to find out 👇</div>
  <button class="btn-spl" onclick="goToPage('page-reveal')" style="margin-top:10px;">
    <span>💡 Click to Know</span>
  </button>
</div>

<!-- ═══════════════════════════════════════════
     PAGE 5 — PICTURE REVEAL
════════════════════════════════════════════ -->
<div id="page-reveal" class="page">
  <div class="sparkle-text">💖 The Answer Is...</div>
  <div class="divider"></div>

  <div class="reveal-photo-wrap">
    <div class="reveal-photo">
      <!-- Place your photo in the same folder as this HTML file -->
      <img src="C:\Users\HP\OneDrive\Desktop\women's day songs\WhatsApp Image 2026-03-10 at 9.20.24 PM.jpeg" alt="Us Together">
    </div>
  </div>

  <button class="btn-spl" onclick="goToPage('page-surprise')" style="margin-top:16px;">
    <span>🎁 Reveal My Promise</span>
  </button>
</div>

<!-- ═══════════════════════════════════════════
     PAGE 6 — SURPRISE MESSAGE
════════════════════════════════════════════ -->
<div id="page-surprise" class="page">
  <div class="sparkle-text">🌟 From Me to You, Always 🌟</div>
  <div class="divider"></div>

  <div class="surprise-msg">
    <div class="surprise-emoji">💌</div>
    <div class="surprise-line">
      "I promise to hold your hand through every storm,<br>
      be your laughter on every hard day,<br>
      and love you more fiercely<br>
      with every single sunrise —<br>
      <em>because you deserve the whole universe, Mama.</em>" 🌸
    </div>
  </div>

  <div style="font-family:'Dancing Script',cursive; font-size:2rem; color:var(--rose); margin-top:8px; animation: sealPulse 1.5s ease-in-out infinite;">
    💖 Happy Birthday Mama 💖
  </div>

  <div class="sparkle-text" style="margin-top:4px;">
    ✨ Forever &amp; Always ✨
  </div>

  <!-- Restart button -->
  <button class="btn-spl" onclick="restartShow()" style="margin-top:24px; font-size:1rem; padding:10px 28px;">
    <span>🔁 Replay from Start</span>
  </button>
</div>

<!-- ══════════════════════════════════════════════
     SCRIPTS
═══════════════════════════════════════════════ -->
<script>
/* ── STARFIELD ── */
(function(){
  const c = document.getElementById('starfield');
  const ctx = c.getContext('2d');
  let stars = [];
  function resize(){ c.width = window.innerWidth; c.height = window.innerHeight; }
  resize(); window.addEventListener('resize', resize);
  for(let i=0;i<180;i++){
    stars.push({
      x: Math.random()*window.innerWidth,
      y: Math.random()*window.innerHeight,
      r: Math.random()*1.5+0.3,
      a: Math.random(),
      s: (Math.random()*0.005)+0.002,
      d: Math.random()>0.5?1:-1
    });
  }
  function drawStars(){
    ctx.clearRect(0,0,c.width,c.height);
    stars.forEach(s=>{
      s.a += s.s*s.d;
      if(s.a>1||s.a<0) s.d*=-1;
      ctx.beginPath();
      ctx.arc(s.x,s.y,s.r,0,Math.PI*2);
      const col = Math.random()>0.5 ? `rgba(255,110,180,${s.a})` : `rgba(199,125,255,${s.a})`;
      ctx.fillStyle = col;
      ctx.fill();
    });
    requestAnimationFrame(drawStars);
  }
  drawStars();
})();

/* ── PETAL PARTICLES ── */
const petals = ['🌸','🌺','✿'];
for(let i=0;i<8;i++){
  const p = document.createElement('div');
  p.className = 'petal';
  p.textContent = petals[Math.floor(Math.random()*petals.length)];
  p.style.left = Math.random()*100+'vw';
  p.style.animationDuration = (Math.random()*8+8)+'s';
  p.style.animationDelay = Math.random()*10+'s';
  p.style.fontSize = (Math.random()*0.8+0.6)+'rem';
  document.body.appendChild(p);
}

/* ── COUNTDOWN ── */
const display = document.getElementById('countdown-display');
let count = 3;

function animateCount(n){
  display.style.animation = 'none';
  display.offsetHeight; // reflow
  display.style.animation = 'pulseNum 0.9s ease-in-out forwards';
  display.textContent = n;
}

function runCountdown(){
  animateCount(count);
  const interval = setInterval(()=>{
    count--;
    if(count > 0){
      animateCount(count);
    } else {
      clearInterval(interval);
      display.style.animation = 'none';
      display.offsetHeight;
      display.style.animation = 'pulseNum 0.9s ease-in-out forwards';
      display.textContent = '🎂';
      setTimeout(()=> goToPage('page-main'), 1200);
    }
  }, 1100);
}

/* ── PAGE NAVIGATION ── */
function goToPage(id){
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
  const target = document.getElementById(id);
  target.classList.add('active');
  target.style.animation = 'none';
  target.offsetHeight;
  target.style.animation = '';
  window.scrollTo(0,0);
}

function goToLetter(){
  goToPage('page-letter');
}

function restartShow(){
  count = 3;
  goToPage('page-countdown');
  setTimeout(runCountdown, 400);
}

/* ── START ── */
window.addEventListener('load', ()=>{
  setTimeout(runCountdown, 600);
});
</script>
</body>
</html>
