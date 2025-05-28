# for-you
open this
<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Untuk Kamu</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;700&family=Sacramento&display=swap');

  body {
    margin: 0;
    background: linear-gradient(135deg, #fceabb, #f8b500);
    font-family: 'Montserrat', sans-serif;
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    color: #441c1d;
    overflow: hidden;
    text-align: center;
    padding: 2rem;
  }

  h1 {
    font-family: 'Sacramento', cursive;
    font-size: 4.5rem;
    margin: 0 0 0.2em 0;
    letter-spacing: 0.1em;
    text-shadow: 2px 2px #aa6700cc;
  }

  p {
    font-size: 1.4rem;
    max-width: 450px;
    margin: 0 0 2em 0;
    font-weight: 600;
    line-height: 1.5;
    user-select: none;
    color: #5c2f00;
  }

  button {
    background: #b85b12;
    border: none;
    padding: 1em 3em;
    border-radius: 30px;
    font-size: 1.3rem;
    font-weight: 700;
    color: #fceabb;
    box-shadow: 0 4px 15px #c5952aaa;
    cursor: pointer;
    transition: background 0.3s ease, box-shadow 0.3s ease;
    user-select: none;
  }

  button:hover {
    background: #ac4200;
    box-shadow: 0 6px 20px #c5a445cc;
  }

  /* Floating hearts */
  .hearts-container {
    pointer-events: none;
    position: fixed;
    top: 0; left: 0; width: 100vw; height: 100vh;
    overflow: visible;
  }

  .heart {
    position: absolute;
    bottom: -40px;
    width: 22px;
    height: 22px;
    background: #b85b12;
    transform: rotate(-45deg);
    animation: floatUp linear forwards;
    opacity: 0.85;
    filter: drop-shadow(0 0 2px #8c3e00);
    border-radius: 3px;
  }
  .heart::before, .heart::after {
    content: "";
    position: absolute;
    width: 22px;
    height: 22px;
    background: #b85b12;
    border-radius: 50%;
  }
  .heart::before {
    top: -11px;
    left: 0;
  }
  .heart::after {
    left: 11px;
    top: 0;
  }

  @keyframes floatUp {
    0% {
      transform: translateY(0) rotate(-45deg);
      opacity: 0.85;
    }
    100% {
      transform: translateY(-550px) rotate(-45deg);
      opacity: 0;
    }
  }

  .hidden-message {
    margin-top: 1.5em;
    font-size: 1.3rem;
    font-style: italic;
    color: #6a3f00;
    opacity: 0;
    transition: opacity 1s ease;
    max-width: 400px;
    pointer-events: none;
    user-select: text;
  }

  .hidden-message.visible {
    opacity: 1;
    pointer-events: auto;
  }

</style>
</head>
<body>
  <h1>Untuk Kamu</h1>
  <p>Kehadiranmu mengisi hari-hariku dengan kebahagiaan dan warna yang indah.</p>
  <button id="revealBtn" aria-labelledby="btnLabel" aria-expanded="false">Klik di sini</button>
  <div id="hiddenMsg" class="hidden-message" role="region" aria-live="polite">
    Aku sangat berterima kasih atas kehadiranmu, dan aku selalu berharap yang terbaik untuk kita berdua ❤️
  </div>

  <div class="hearts-container" id="heartsContainer"></div>

<script>
  const btn = document.getElementById('revealBtn');
  const hiddenMsg = document.getElementById('hiddenMsg');
  const heartsContainer = document.getElementById('heartsContainer');

  btn.addEventListener('click', () => {
    if (hiddenMsg.classList.contains('visible')) {
      hiddenMsg.classList.remove('visible');
      btn.setAttribute('aria-expanded', 'false');
    } else {
      hiddenMsg.classList.add('visible');
      btn.setAttribute('aria-expanded', 'true');
      startHearts();
    }
  });

  function createHeart() {
    const heart = document.createElement('div');
    heart.classList.add('heart');
    heart.style.left = Math.random() * 100 + 'vw';
    heart.style.animationDuration = (3 + Math.random() * 3) + 's';
    heart.style.width = heart.style.height = (15 + Math.random() * 20) + 'px';

    heartsContainer.appendChild(heart);

    setTimeout(() => {
      heart.remove();
    }, 7000);
  }

  function startHearts() {
    const interval = setInterval(createHeart, 350);
    setTimeout(() => clearInterval(interval), 4500);
  }
</script>
</body>
</html>
