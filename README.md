
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no" />
  <title>Carta de Amor - 21/07/25</title>

  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Playfair+Display:wght@700&family=Poppins:wght@400;500&display=swap" rel="stylesheet">

  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, #fff8fd, #fdf2f8, #fce5f0);
      color: #444;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      padding: 20px;
      overflow-x: hidden;
      position: relative;
    }

    /* Animación de borde brillante RGB */
    @keyframes rainbowGlow {
      0% { box-shadow: 0 0 15px rgba(255, 105, 180, 0.6); }
      25% { box-shadow: 0 0 15px rgba(140, 100, 255, 0.6); }
      50% { box-shadow: 0 0 15px rgba(0, 200, 255, 0.6); }
      75% { box-shadow: 0 0 15px rgba(255, 190, 100, 0.6); }
      100% { box-shadow: 0 0 15px rgba(255, 105, 180, 0.6); }
    }

    /* Marco brillante general */
    .glow-frame {
      position: relative;
      display: inline-block;
      border-radius: 20px;
      margin: 1rem 0;
      animation: rainbowGlow 3s ease-in-out infinite alternate;
      background: linear-gradient(45deg, #ff80ab, #ba68c8, #4fc3f7, #ffcc80);
      padding: 4px;
    }

    .glow-frame img {
      border-radius: 18px;
      display: block;
      width: 100%;
      height: auto;
      border: 4px solid #fff;
      filter: brightness(1) blur(0.5px);
      transition: transform 0.3s ease;
    }

    .glow-frame img:hover {
      transform: scale(1.03);
    }

    /* Pantalla de bloqueo */
    .lock-screen {
      text-align: center;
      padding: 1.8rem 2rem;
      max-width: 440px;
      background: rgba(255, 255, 255, 0.98);
      border-radius: 32px;
      box-shadow: 0 16px 45px rgba(255, 105, 180, 0.25);
      border: 3px solid transparent;
      background-clip: padding-box;
      position: relative;
      z-index: 1;
    }

    .lock-screen::before {
      content: '';
      position: absolute;
      inset: -3px;
      background: linear-gradient(45deg, #ff80ab, #ba68c8, #ffcc80);
      border-radius: 35px;
      z-index: -1;
      opacity: 0.7;
      animation: backgroundShift 6s ease-in-out infinite;
    }

    @keyframes backgroundShift {
      0%, 100% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
    }

    .lock-screen h2 {
      font-family: 'Playfair Display', serif;
      font-size: 2.1rem;
      background: linear-gradient(45deg, #e91e63, #ba68c8, #ff8f00);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      margin: 1rem 0;
      animation: backgroundShift 6s ease-in-out infinite;
    }

    .lock-screen p {
      color: #d81b60;
      font-size: 1.15rem;
      margin-bottom: 1.3rem;
      font-weight: 500;
    }

    /* Display de clave */
    .key-display {
      font-family: 'Poppins', monospace;
      font-size: 1.8rem;
      color: #e91e63;
      background: linear-gradient(135deg, #fff0f5, #ffe6f0);
      padding: 0.9rem 1.3rem;
      border-radius: 16px;
      margin: 1.1rem auto;
      width: 90%;
      border: 3px solid #ff80ab;
      letter-spacing: 4px;
      box-shadow: 0 6px 15px rgba(255, 105, 180, 0.2);
    }

    /* Teclado */
    .keypad {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 12px;
      margin: 1.3rem 0;
    }

    .key {
      font-size: 1.45rem;
      font-weight: 600;
      padding: 1rem 0;
      background: linear-gradient(135deg, #fff5f8, #ffe6f0);
      color: #e91e63;
      border: 3px solid #ff80ab;
      border-radius: 14px;
      cursor: pointer;
      transition: all 0.25s cubic-bezier(0.25, 0.8, 0.25, 1);
      box-shadow: 0 4px 10px rgba(255, 105, 180, 0.2);
    }

    .key:hover {
      background: linear-gradient(135deg, #ffe6f0, #f8dafa);
      transform: translateY(-4px);
      box-shadow: 0 8px 18px rgba(255, 105, 180, 0.35);
    }

    .key:active {
      transform: scale(0.95);
      box-shadow: 0 3px 8px rgba(233, 30, 99, 0.3);
    }

    /* Botón Iniciar */
    .btn-iniciar {
      margin-top: 1.4rem;
      padding: 0.9rem 2rem;
      font-size: 1.25rem;
      font-weight: 600;
      background: linear-gradient(45deg, #e91e63, #ba68c8, #8e24aa);
      color: white;
      border: none;
      border-radius: 32px;
      cursor: pointer;
      box-shadow: 0 8px 20px rgba(233, 30, 99, 0.4);
      transition: all 0.3s ease;
      animation: float 3s ease-in-out infinite;
    }

    @keyframes float {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-6px); }
    }

    .btn-iniciar:hover {
      transform: scale(1.08) translateY(-3px);
      box-shadow: 0 10px 25px rgba(233, 30, 99, 0.5);
    }

    .btn-iniciar:active {
      transform: scale(1.03);
    }

    /* Contenedor principal - Carta */
    .main-container {
      display: none;
      text-align: center;
      max-width: 95%;
      padding: 1.8rem 1.4rem;
    }

    .letter-frame {
      background: rgba(255, 255, 255, 0.95);
      border-radius: 30px;
      padding: 1.8rem 1.6rem;
      box-shadow: 0 15px 40px rgba(255, 105, 180, 0.25);
      border: 4px solid transparent;
      background-clip: padding-box;
      position: relative;
      margin-bottom: 1.6rem;
    }

    .letter-frame::before {
      content: '';
      position: absolute;
      inset: 0;
      border-radius: 30px;
      padding: 4px;
      background: linear-gradient(45deg, #ff80ab, #ba68c8);
      -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
      -webkit-mask-composite: destination-out;
      mask-composite: subtract;
      pointer-events: none;
    }

    h1 {
      font-family: 'Playfair Display', serif;
      font-size: 2.3rem;
      background: linear-gradient(45deg, #e91e63, #ba68c8);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      margin-bottom: 1.4rem;
    }

    /* Letra de la carta: más compacta */
    .letter {
      font-family: 'Dancing Script', cursive;
      font-size: 1.55rem;
      line-height: 1.65;
      color: #d81b60;
      text-align: left;
      white-space: pre-line;
      letter-spacing: 0.8px;
      margin: 0;
      opacity: 1;
      font-weight: 500;
    }

    /* Botón de galería */
    .btn-gallery {
      display: inline-block;
      margin: 1.4rem auto 1rem;
      padding: 0.9rem 2rem;
      font-family: 'Poppins', sans-serif;
      font-size: 1.15rem;
      font-weight: 600;
      color: white;
      background: linear-gradient(45deg, #e91e63, #ba68c8);
      border: none;
      border-radius: 30px;
      cursor: pointer;
      box-shadow: 0 8px 20px rgba(233, 30, 99, 0.4);
      transition: all 0.3s ease;
      animation: pulse 2s infinite, rainbowGlow 3s ease-in-out infinite alternate;
    }

    .btn-gallery:hover {
      transform: scale(1.12);
      box-shadow: 0 10px 25px rgba(233, 30, 99, 0.6);
    }

    .btn-gallery:active {
      transform: scale(1.08);
    }

    footer {
      margin-top: 1.4rem;
      font-style: italic;
      color: #ba68c8;
      font-size: 1.1rem;
    }

    /* Pantalla de Galería */
    .gallery-screen {
      display: none;
      flex-direction: column;
      align-items: center;
      width: 100%;
      max-width: 900px;
      padding: 2rem 1.4rem;
      text-align: center;
    }

    .gallery-title {
      font-family: 'Playfair Display', serif;
      font-size: 2.5rem;
      background: linear-gradient(45deg, #e91e63, #ba68c8, #ff8f00);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      margin-bottom: 1.6rem;
      animation: rainbowGlow 3s ease-in-out infinite alternate;
    }

    .gallery-main-img {
      width: 100%;
      max-width: 480px;
      margin-bottom: 1.8rem;
    }

    .gallery-thumbnails {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(110px, 1fr));
      gap: 10px;
      width: 100%;
      max-width: 580px;
    }

    /* Modal de zoom */
    .modal-zoom {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.9);
      z-index: 2000;
      justify-content: center;
      align-items: center;
      cursor: zoom-out;
    }

    .modal-zoom img {
      max-width: 90%;
      max-height: 90%;
      border-radius: 15px;
      border: 5px solid #e91e63;
      box-shadow: 0 0 30px rgba(255, 105, 180, 0.8);
      animation: fadeIn 0.3s;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: scale(0.9); }
      to { opacity: 1; transform: scale(1); }
    }

    /* Cuadro de error */
    .error-modal {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.5);
      display: flex;
      justify-content: center;
      align-items: center;
      z-index: 200;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.3s;
    }

    .error-modal.active {
      opacity: 1;
      pointer-events: all;
    }

    .error-content {
      background: white;
      border-radius: 20px;
      width: 90%;
      max-width: 360px;
      padding: 1.6rem;
      position: relative;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
      border: 3px solid #ffb6c1;
      animation: popIn 0.3s;
      font-family: 'Poppins', sans-serif;
    }

    @keyframes popIn {
      from { transform: scale(0.8); opacity: 0; }
      to { transform: scale(1); opacity: 1; }
    }

    .close-error {
      position: absolute;
      top: 10px;
      right: 10px;
      font-size: 1.4rem;
      color: #e91e63;
      cursor: pointer;
      width: 26px;
      height: 26px;
      display: flex;
      justify-content: center;
      align-items: center;
      border-radius: 50%;
      background: #fff0f5;
      transition: all 0.2s;
    }

    .close-error:hover {
      background: #ffe6f0;
      transform: rotate(90deg);
    }

    .error-content h3 {
      color: #e91e63;
      margin-bottom: 0.9rem;
      font-size: 1.25rem;
      text-align: center;
    }

    .error-content p {
      color: #555;
      line-height: 1.55;
      margin-bottom: 1.3rem;
      font-size: 1.02rem;
    }

    /* Corazones flotantes */
    .floating-heart {
      position: fixed;
      font-size: 18px;
      pointer-events: none;
      opacity: 0;
      z-index: 1000;
      user-select: none;
      animation: floatUp 18s ease-out forwards, fadeHeart 4s ease-in-out infinite;
    }

    @keyframes floatUp {
      0% {
        transform: translateY(100vh) rotate(0deg);
        opacity: 0;
      }
      10% { opacity: 0.8; }
      90% { opacity: 0.8; }
      100% {
        transform: translateY(-20vh) rotate(360deg);
        opacity: 0;
      }
    }

    @keyframes fadeHeart {
      0%, 100% { opacity: 0.6; }
      50% { opacity: 1; }
    }

    /* By AnthZz Berrocal */
    .credit {
      margin-top: 1.3rem;
      font-size: 0.7rem;
      color: #ccc;
      font-style: italic;
      text-align: center;
    }

    @media (max-width: 480px) {
      .lock-screen, .main-container, .gallery-screen {
        padding: 1.4rem;
        max-width: 98%;
      }

      h1 {
        font-size: 2rem;
      }

      .letter {
        font-size: 1.4rem;
        line-height: 1.6;
      }

      .btn-iniciar {
        font-size: 1.15rem;
        padding: 0.8rem 1.8rem;
      }

      .gallery-thumbnails {
        grid-template-columns: repeat(2, 1fr);
      }
    }
  </style>
</head>
<body>

  <!-- Corazones flotantes -->
  <script>
    function createHearts() {
      const hearts = ['❤️', '💖', '💕', '💓', '💗', '💞', '💘', '💝', '💟'];
      setInterval(() => {
        const heart = document.createElement('div');
        heart.className = 'floating-heart';
        heart.textContent = hearts[Math.floor(Math.random() * hearts.length)];
        heart.style.left = Math.random() * 90 + 5 + 'vw';
        heart.style.bottom = '0';
        document.body.appendChild(heart);

        setTimeout(() => {
          heart.remove();
        }, 18000);
      }, 2500);
    }
    createHearts();
  </script>

  <!-- Pantalla de bloqueo -->
  <div id="lockScreen" class="lock-screen">
    <h2>🔐 Tu Carta Mi Amor</h2>
    <p>👇INGRESA EL CÓDIGO DE ACCESO 👇</p>

    <div class="glow-frame">
      <img src="https://media2.giphy.com/media/v1.Y2lkPTZjMDliOTUyZTAxbHV0Mm1rYmI2emc3ZmdvcGdka2szMGMzMHl4ZXlhcmEzN3A4cCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/Y62ofc4S1Vst2/giphy.gif" alt="Corazones flotando" />
    </div>

    <div id="display" class="key-display"></div>

    <div class="keypad">
      <div class="key" onclick="addDigit('1')">1</div>
      <div class="key" onclick="addDigit('2')">2</div>
      <div class="key" onclick="addDigit('3')">3</div>
      <div class="key" onclick="addDigit('4')">4</div>
      <div class="key" onclick="addDigit('5')">5</div>
      <div class="key" onclick="addDigit('6')">6</div>
      <div class="key" onclick="addDigit('7')">7</div>
      <div class="key" onclick="addDigit('8')">8</div>
      <div class="key" onclick="addDigit('9')">9</div>
      <div class="key" onclick="addDigit('0')">0</div>
      <div class="key" onclick="addDigit('/')">/</div>
      <div class="key" onclick="clearInput()">⌫</div>
    </div>

    <button class="btn-iniciar" onclick="submitKey()">Iniciar</button>

    <div class="glow-frame">
      <img src="https://media0.giphy.com/media/v1.Y2lkPTZjMDliOTUyMzl0NTh2ZHhmOHF1Nm45NHNqcmN1bTVrdHNtbDgwbjZpZTFqMno3diZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/11TyfGbDbBv4be/giphy.gif" alt="Bailarina de amor" />
    </div>
  </div>

  <!-- Carta principal -->
  <div id="mainContainer" class="main-container">
    <div class="letter-frame">
      <h1>Para Ti Amorcita Hermosa💖</h1>
      <div id="letter" class="letter"></div>

      <!-- Foto principal centrada -->
      <div class="glow-frame" style="margin: 1.4rem auto; max-width: 400px; display: flex; justify-content: center;">
        <img src="https://i.postimg.cc/RFcd9YQW/IMG-20250901-WA0112.jpg" alt="Foto principal de Paul y Yanina" />
      </div>

      <button class="btn-gallery" onclick="openGallery()">Ver nuestras fotos 📸</button>
      <footer>Con todo mi corazón, Te dedico ésto para usted.</footer>
    </div>

    <p class="credit">By AnthZz Berrocal</p>
  </div>

  <!-- Tercera pantalla: Galería -->
  <div id="galleryScreen" class="gallery-screen">
    <h2 class="gallery-title">✨ Nuestra Galería Mi Reina💖</h2>

    <div class="glow-frame gallery-main-img">
      <img src="https://i.postimg.cc/RFcd9YQW/IMG-20250901-WA0112.jpg" alt="Foto grande" style="width: 100%; border-radius: 18px;" onclick="zoomImage(this)" />
    </div>

    <div class="gallery-thumbnails">
      <div class="glow-frame"><img src="https://i.postimg.cc/DyVhx4m5/IMG-20250901-WA0109.jpg" class="gallery-img" onclick="zoomImage(this)" /></div>
      <div class="glow-frame"><img src="https://i.postimg.cc/brc59bLt/IMG-20250901-WA0110.jpg" class="gallery-img" onclick="zoomImage(this)" /></div>
      <div class="glow-frame"><img src="https://i.postimg.cc/NMTJFFYf/IMG-20250901-WA0111.jpg" class="gallery-img" onclick="zoomImage(this)" /></div>
      <div class="glow-frame"><img src="https://i.postimg.cc/xTj5Dtkd/IMG-20250901-WA0107.jpg" class="gallery-img" onclick="zoomImage(this)" /></div>
    </div>

    <button class="btn-iniciar" style="margin-top: 1.8rem;" onclick="closeGallery()">Volver a la carta</button>
    <p class="credit">By AnthZz Berrocal</p>
  </div>

  <!-- Modal de zoom -->
  <div id="zoomModal" class="modal-zoom" onclick="closeZoom()">
    <img id="zoomedImage" src="" />
  </div>

  <!-- Cuadro de error -->
  <div id="errorModal" class="error-modal">
    <div class="error-content">
      <div class="close-error" onclick="cerrarError()">×</div>
      <h3>⚠️ Código Incorrecto</h3>
      <p>El código que ingresaste es incorrecto. Por favor, inténtalo de nuevo.</p>
    </div>
  </div>

  <script>
    let input = '';
    const correctKey = '21/07/25';
    const nombreYo = 'Paul';
    const nombreElla = 'Yanina';

    function addDigit(digit) {
      if (input.length < 8) {
        input += digit;
        updateDisplay();
      }
    }

    function clearInput() {
      input = '';
      updateDisplay();
    }

    function updateDisplay() {
      document.getElementById('display').textContent = input;
    }

    function submitKey() {
      if (input === correctKey) {
        document.getElementById('lockScreen').style.display = 'none';
        document.getElementById('mainContainer').style.display = 'block';
        typeWriter();
      } else {
        document.getElementById('errorModal').classList.add('active');
        clearInput();
      }
    }

    function cerrarError() {
      document.getElementById('errorModal').classList.remove('active');
    }

    function typeWriter() {
      const letterElement = document.getElementById('letter');
      letterElement.textContent = '';
      letterElement.style.opacity = 1;
      
      let i = 0;
      const message = getMessage();
      const speed = 35;

      function type() {
        if (i < message.length) {
          letterElement.textContent += message.charAt(i);
          i++;
          setTimeout(type, speed);
        }
      }

      setTimeout(type, 300);
    }

    function getMessage() {
      return `Mi amor ${nombreElla},

Hoy quiero que sepas, con cada latido de mi corazón,
que eres la persona más hermosa, dulce y especial
que he tenido la fortuna de conocer.

Desde que llegaste a mi vida, todo tiene más color,
más sentido, más magia. Tus risas son mi melodía favorita,
tu mirada, mi refugio, y tu amor, mi mayor bendición.

Cada día contigo es un regalo que agradezco profundamente.
No hay palabras suficientes para describir lo que siento,
pero si pudiera dibujarlo, sería un cielo lleno de estrellas,
un jardín lleno de tulipanes, con cada color representa los 
sentimientos que tenemos el uno por el otro.

Gracias por ser tú, por amarme como soy,
por entenderme sin necesidad de palabras,
por abrazarme incluso cuando no lo merezco.

Te amo más de lo que las palabras pueden decir,
más de lo que el tiempo puede medir,
más de lo que el universo puede contener.

Siempre serás mi hogar, mi sueño, mi razón.

Con todo mi amor y cariño,
Atte:
${nombreYo} 💖`;
    }

    function openGallery() {
      document.getElementById('mainContainer').style.display = 'none';
      document.getElementById('galleryScreen').style.display = 'flex';
    }

    function closeGallery() {
      document.getElementById('galleryScreen').style.display = 'none';
      document.getElementById('mainContainer').style.display = 'block';
    }

    function zoomImage(img) {
      const modal = document.getElementById('zoomModal');
      const zoomImg = document.getElementById('zoomedImage');
      zoomImg.src = img.src;
      modal.style.display = 'flex';
    }

    function closeZoom() {
      document.getElementById('zoomModal').style.display = 'none';
    }
  </script>
</body>
</html>
