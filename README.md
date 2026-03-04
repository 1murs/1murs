<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>1murs — GitHub Profile Preview</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;1,300;1,400&family=JetBrains+Mono:wght@300&display=swap');

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: #020209;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    overflow: hidden;
    font-family: 'Cormorant Garamond', serif;
  }

  /* Stars */
  .stars {
    position: fixed;
    inset: 0;
    z-index: 0;
  }

  .star {
    position: absolute;
    background: white;
    border-radius: 50%;
    animation: twinkle var(--duration) ease-in-out infinite alternate;
    opacity: 0;
  }

  @keyframes twinkle {
    0%   { opacity: 0; transform: scale(0.8); }
    100% { opacity: var(--max-opacity); transform: scale(1.2); }
  }

  /* Nebula */
  .nebula {
    position: fixed;
    inset: 0;
    z-index: 0;
    background:
      radial-gradient(ellipse 80% 60% at 20% 30%, rgba(80, 40, 160, 0.25) 0%, transparent 60%),
      radial-gradient(ellipse 60% 80% at 80% 70%, rgba(20, 10, 80, 0.35) 0%, transparent 60%),
      radial-gradient(ellipse 100% 50% at 50% 50%, rgba(10, 5, 40, 0.5) 0%, transparent 70%);
  }

  /* Content */
  .content {
    position: relative;
    z-index: 10;
    text-align: center;
    padding: 60px 40px;
    animation: appear 2.5s ease forwards;
    opacity: 0;
  }

  @keyframes appear {
    0%   { opacity: 0; transform: translateY(20px); }
    100% { opacity: 1; transform: translateY(0); }
  }

  .nickname {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(60px, 12vw, 120px);
    font-weight: 300;
    letter-spacing: 0.3em;
    color: #e2d9f3;
    text-shadow:
      0 0 40px rgba(180, 140, 255, 0.4),
      0 0 80px rgba(120, 80, 200, 0.2);
    margin-bottom: 70px;
  }

  .divider {
    width: 1px;
    height: 60px;
    background: linear-gradient(to bottom, transparent, rgba(180,140,255,0.4), transparent);
    margin: 0 auto 60px;
  }

  .quote {
    font-size: clamp(16px, 2.5vw, 22px);
    font-weight: 300;
    font-style: italic;
    color: #b8a8d9;
    line-height: 1.8;
    max-width: 640px;
    letter-spacing: 0.03em;
    margin-bottom: 30px;
    text-shadow: 0 0 30px rgba(150, 100, 230, 0.2);
  }

  .author {
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    font-weight: 300;
    letter-spacing: 0.25em;
    color: rgba(160, 130, 210, 0.5);
    text-transform: uppercase;
  }

  /* Shooting star */
  .shoot {
    position: fixed;
    width: 2px;
    height: 80px;
    background: linear-gradient(to bottom, transparent, rgba(220,200,255,0.8), transparent);
    border-radius: 50%;
    animation: shoot 6s ease-in-out infinite;
    opacity: 0;
    transform: rotate(-45deg);
  }

  @keyframes shoot {
    0%   { opacity: 0; top: -10%; left: 80%; }
    5%   { opacity: 1; }
    20%  { opacity: 0; top: 30%; left: 50%; }
    100% { opacity: 0; top: 30%; left: 50%; }
  }

  .shoot:nth-child(2) { animation-delay: 3.5s; left: 60%; }
</style>
</head>
<body>

<div class="nebula"></div>
<canvas class="stars" id="stars"></canvas>

<div class="shoot"></div>
<div class="shoot"></div>

<div class="content">
  <div class="nickname">1murs</div>
  <div class="divider"></div>
  <div class="quote">
    "If you want to live a happy life,<br/>
    tie it to a goal,<br/>
    not to people or objects."
  </div>
  <div class="author">— Albert Einstein</div>
</div>

<script>
  const canvas = document.getElementById('stars');
  const ctx = canvas.getContext('2d');
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;

  for (let i = 0; i < 220; i++) {
    const x = Math.random() * canvas.width;
    const y = Math.random() * canvas.height;
    const r = Math.random() * 1.2;
    const opacity = Math.random() * 0.7 + 0.1;
    ctx.beginPath();
    ctx.arc(x, y, r, 0, Math.PI * 2);
    ctx.fillStyle = `rgba(255,255,255,${opacity})`;
    ctx.fill();
  }

  window.addEventListener('resize', () => {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
  });
</script>
</body>
</html>
