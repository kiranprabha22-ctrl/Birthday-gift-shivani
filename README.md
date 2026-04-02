<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Happy Birthday Shiva Priya 🎂</title>

  <style>
    body {
      margin: 0;
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, #ff758c, #ff7eb3);
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      overflow: hidden;
      text-align: center;
    }

    .card {
      background: white;
      padding: 25px;
      border-radius: 20px;
      box-shadow: 0 10px 25px rgba(0,0,0,0.2);
      max-width: 90%;
      width: 350px;
      animation: pop 1.2s ease;
    }

    h1 {
      color: #ff4081;
      font-size: 26px;
      margin-bottom: 10px;
    }

    h2 {
      color: #333;
      font-size: 20px;
      margin-bottom: 15px;
    }

    p {
      color: #555;
      font-size: 15px;
      margin-bottom: 20px;
    }

    button {
      background: #ff4081;
      color: white;
      border: none;
      padding: 12px 20px;
      border-radius: 25px;
      font-size: 16px;
      cursor: pointer;
    }

    button:hover {
      background: #e91e63;
    }

    @keyframes pop {
      from { transform: scale(0.7); opacity: 0; }
      to { transform: scale(1); opacity: 1; }
    }

    canvas {
      position: fixed;
      top: 0;
      left: 0;
      pointer-events: none;
    }

    @media (max-width: 480px) {
      h1 { font-size: 22px; }
      h2 { font-size: 18px; }
      p { font-size: 14px; }
    }
  </style>
</head>

<body>

<canvas id="confetti"></canvas>

<div class="card">
  <h1>🎂 Happy Birthday</h1>
  <h2>Shiva Priya 💖</h2>
  <p>May your day be filled with happiness, love, and endless smiles! 🌸✨</p>
  <button onclick="startConfetti()">Celebrate 🎉</button>
</div>

<script>
  const canvas = document.getElementById('confetti');
  const ctx = canvas.getContext('2d');

  function resizeCanvas() {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
  }
  resizeCanvas();
  window.addEventListener('resize', resizeCanvas);

  let confetti = [];

  function randomColor() {
    return `hsl(${Math.random() * 360}, 100%, 50%)`;
  }

  function createConfetti() {
    return {
      x: Math.random() * canvas.width,
      y: Math.random() * canvas.height - canvas.height,
      size: Math.random() * 6 + 3,
      speed: Math.random() * 3 + 2,
      color: randomColor()
    };
  }

  function drawConfetti() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    confetti.forEach(c => {
      ctx.fillStyle = c.color;
      ctx.fillRect(c.x, c.y, c.size, c.size);
    });
    updateConfetti();
  }

  function updateConfetti() {
    confetti.forEach((c, i) => {
      c.y += c.speed;
      c.x += Math.sin(c.y * 0.01);

      if (c.y > canvas.height) {
        confetti[i] = createConfetti();
        confetti[i].y = 0;
      }
    });
  }

  function animate() {
    drawConfetti();
    requestAnimationFrame(animate);
  }

  function startConfetti() {
    confetti = [];
    for (let i = 0; i < 180; i++) {
      confetti.push(createConfetti());
    }
    animate();
  }

  // Auto start confetti on load
  startConfetti();
</script>

</body>
</html>
