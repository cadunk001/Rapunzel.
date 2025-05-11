<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Para minha Rapunzel</title>
  <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Poppins:wght@400;600&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, #ffccd5, #f8e1e1);
      color: #333;
      text-align: center;
      overflow-x: hidden;
      position: relative;
      min-height: 100vh;
    }
    /* Efeitos de corações flutuantes (gerais e no pedido) */
    .heart {
      position: absolute;
      width: 20px;
      height: 20px;
      background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="%23ff4d4d"><path d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z"/></svg>') no-repeat center;
      background-size: contain;
      animation: float 6s ease-in-out infinite;
    }
    @keyframes float {
      0% { transform: translateY(0) rotate(0deg); opacity: 0.8; }
      50% { transform: translateY(-50vh) rotate(180deg); opacity: 0.4; }
      100% { transform: translateY(-100vh) rotate(360deg); opacity: 0; }
    }
    header {
      padding: 20px 20px 40px;
      color: #fff;
      text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);
    }
    h1 {
      font-family: 'Great Vibes', cursive;
      font-size: 4em;
      margin: 0;
      color: #ff4d4d;
    }
    p {
      font-size: 1.3em;
      margin: 10px auto;
      max-width: 700px;
      line-height: 1.6;
    }
    .audio-section {
      margin: 20px auto;
      padding: 10px;
    }
    .upload-section {
      margin: 30px auto;
      padding: 20px;
      background: rgba(255, 255, 255, 0.9);
      border-radius: 15px;
      max-width: 600px;
      box-shadow: 0 8px 16px rgba(0, 0, 0, 0.1);
    }
    input[type="file"] {
      margin: 10px;
      padding: 10px;
      font-size: 1em;
      border: 1px solid #ddd;
      border-radius: 5px;
    }
    button {
      padding: 12px 25px;
      font-size: 1.1em;
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(45deg, #ff4d4d, #ff6b6b);
      color: white;
      border: none;
      border-radius: 25px;
      cursor: pointer;
      transition: transform 0.3s, box-shadow 0.3s;
    }
    button:hover {
      transform: scale(1.05);
      box-shadow: 0 6px 12px rgba(255, 77, 77, 0.3);
    }
    .gallery {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 20px;
      padding: 20px;
    }
    .gallery img {
      max-width: 250px;
      border-radius: 10px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
      transition: transform 0.3s;
    }
    .gallery img:hover {
      transform: scale(1.1);
    }
    .proposal {
      margin: 40px auto;
      padding: 20px;
      background: rgba(255, 255, 255, 0.9);
      border-radius: 15px;
      max-width: 600px;
      box-shadow: 0 8px 16px rgba(0, 0, 0, 0.1);
    }
    #proposal-text {
      display: none;
      font-size: 2em;
      color: #ff4d4d;
      margin-top: 20px;
      animation: fadeIn 1.5s;
    }
    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }
    @media (max-width: 600px) {
      h1 { font-size: 2.5em; }
      p { font-size: 1.1em; }
      .gallery img { max-width: 100%; }
    }
  </style>
</head>
<body>
  <!-- Efeitos de corações gerais -->
  <script>
    function createHeart() {
      const heart = document.createElement('div');
      heart.className = 'heart';
      heart.style.left = Math.random() * 100 + 'vw';
      heart.style.animationDuration = Math.random() * 4 + 5 + 's';
      heart.style.opacity = Math.random() * 0.5 + 0.5;
      document.body.appendChild(heart);
      setTimeout(() => heart.remove(), 6000);
    }
    setInterval(createHeart, 500);
  </script>

  <header>
    <div class="audio-section">
      <audio id="audioPlayer" controls>
        <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mp3">
        Seu navegador não suporta áudio.
      </audio>
      <p>Clique para ouvir nossa música enquanto lê!</p>
    </div>
    <h1>Para minha Rapunzel</h1>
    <p>Você transformou meus dias em algo mágico, e quero te mostrar o quanto você é especial para mim.</p>
  </header>

  <section class="upload-section">
    <h2>Adicione Nossas Fotos</h2>
    <input type="file" id="photoInput" accept="image/*" multiple>
    <button onclick="uploadPhotos()">Enviar Fotos</button>
  </section>

  <section class="gallery" id="gallery"></section>

  <section class="proposal">
    <p>Você é o motivo do meu sorriso. Cada momento com você é um presente.</p>
    <button onclick="showProposal()">Quero te fazer uma pergunta...</button>
    <div id="proposal-text">Quer ser minha namorada?</div>
  </section>

  <script>
    // Efeito do pedido com corações
    function showProposal() {
      const proposalText = document.getElementById('proposal-text');
      proposalText.style.display = 'block';

      // Adicionar corações ao clicar
      for (let i = 0; i < 10; i++) {
        const heart = document.createElement('div');
        heart.className = 'heart';
        heart.style.left = Math.random() * 80 + 10 + 'vw';
        heart.style.animationDuration = Math.random() * 3 + 3 + 's';
        document.body.appendChild(heart);
        setTimeout(() => heart.remove(), 4000);
      }
    }

    // Carregar fotos do LocalStorage
    function loadPhotos() {
      const gallery = document.getElementById('gallery');
      const savedPhotos = JSON.parse(localStorage.getItem('photos')) || [];
      gallery.innerHTML = '';
      savedPhotos.forEach(photo => {
        const img = document.createElement('img');
        img.src = photo;
        gallery.appendChild(img);
      });
    }

    // Fazer upload de fotos
    function uploadPhotos() {
      const photoInput = document.getElementById('photoInput');
      const files = photoInput.files;
      const savedPhotos = JSON.parse(localStorage.getItem('photos')) || [];

      for (let i = 0; i < files.length; i++) {
        const file = files[i];
        if (file.type.startsWith('image/')) {
          const reader = new FileReader();
          reader.onload = function(e) {
            savedPhotos.push(e.target.result);
            localStorage.setItem('photos', JSON.stringify(savedPhotos));
            loadPhotos();
          };
          reader.readAsDataURL(file);
        }
      }
    }

    // Carregar fotos ao abrir o site
    window.onload = loadPhotos;
  </script>
</body>
</html>
