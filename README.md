<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Perfil de José - Precision Agriculture & Research</title>
  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css?family=Roboto:400,700&display=swap" rel="stylesheet" />
  <!-- Leaflet CSS para el mapa -->
  <link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css" />
  <style>
    /* Reset y estilos base */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body {
      font-family: 'Roboto', sans-serif;
      background-color: #f5f5f5;
      color: #333;
      line-height: 1.6;
      transition: background-color 0.3s, color 0.3s;
    }
    .dark-mode {
      background-color: #121212;
      color: #ddd;
    }
    a {
      color: inherit;
      text-decoration: none;
    }
    /* Header */
    header {
      padding: 20px;
      background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
      color: #fff;
      text-align: center;
      position: relative;
    }
    header h2 {
      font-size: 2em;
      margin-bottom: 10px;
    }
    header p {
      font-size: 1.2em;
    }
    .toggle-dark {
      position: absolute;
      top: 20px;
      right: 20px;
      background: rgba(255, 255, 255, 0.3);
      border: none;
      padding: 10px 15px;
      border-radius: 5px;
      cursor: pointer;
      color: #fff;
      transition: background 0.3s;
    }
    .toggle-dark:hover {
      background: rgba(255, 255, 255, 0.5);
    }
    .social-links img {
      margin: 0 5px;
      transition: transform 0.3s;
    }
    .social-links img:hover {
      transform: scale(1.1);
    }
    /* Secciones */
    section {
      padding: 40px 20px;
    }
    h3 {
      margin-bottom: 20px;
      text-align: center;
    }
    /* Tarjetas de Investigación */
    .cards-container {
      display: flex;
      flex-wrap: wrap;
      gap: 20px;
      justify-content: center;
    }
    .card {
      background-color: #fff;
      border-radius: 10px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
      overflow: hidden;
      transition: transform 0.3s, box-shadow 0.3s;
      width: 300px;
      cursor: pointer;
    }
    .card:hover {
      transform: translateY(-5px);
      box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
    }
    .card-content {
      padding: 20px;
    }
    .card-content h4 {
      margin-bottom: 10px;
    }
    .card-content p {
      font-size: 0.9em;
      color: #555;
    }
    /* Mapa */
    #map {
      height: 300px;
      border-radius: 10px;
      margin: 20px auto;
      max-width: 600px;
    }
    /* Gráfico */
    #chartContainer {
      max-width: 600px;
      margin: 40px auto;
    }
    /* Blog */
    .blog-posts {
      display: flex;
      flex-direction: column;
      gap: 20px;
      max-width: 800px;
      margin: 0 auto;
    }
    .blog-post {
      background: #fff;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    }
    .blog-post h4 {
      margin-bottom: 10px;
    }
    .blog-post a {
      color: #0077B5;
      font-weight: bold;
    }
    /* Proyectos GitHub */
    .projects {
      display: flex;
      flex-wrap: wrap;
      gap: 20px;
      justify-content: center;
      max-width: 800px;
      margin: 0 auto;
    }
    .project-card {
      background: #fff;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
      transition: transform 0.3s;
      width: 300px;
      text-align: center;
      cursor: pointer;
    }
    .project-card:hover {
      transform: translateY(-5px);
    }
    /* Testimonios */
    .testimonials {
      max-width: 800px;
      margin: 40px auto;
      text-align: center;
    }
    .testimonial {
      background: #fff;
      padding: 20px;
      margin: 20px;
      border-radius: 10px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    }
    /* Adaptación en modo oscuro */
    .dark-mode header {
      background: linear-gradient(135deg, #222, #444);
    }
    .dark-mode .card,
    .dark-mode .blog-post,
    .dark-mode .project-card,
    .dark-mode .testimonial {
      background: #1e1e1e;
      color: #ddd;
    }
  </style>
</head>
<body>
  <!-- Header con toggle de modo oscuro -->
  <header>
    <button class="toggle-dark" id="toggleDark">Modo Oscuro</button>
    <h2>
      Hey 👋, I'm <a href="https://www.linkedin.com/in/jlhm98/" target="_blank">José</a>
    </h2>
    <p>
      Agriculture Engineer | Precision Agriculture Enthusiast | Master's in Water Resources
    </p>
    <div class="social-links">
      <a href="https://www.linkedin.com/in/jlhm98/" target="_blank">
        <img src="https://img.shields.io/badge/-@jlhm98-0077B5?style=flat-square&amp;logo=LinkedIn" alt="LinkedIn" />
      </a>
      <a href="https://x.com/Joselhm98" target="_blank">
        <img src="https://img.shields.io/badge/-@Joselhm98-1DA1F2?style=flat-square&amp;logo=X" alt="X" />
      </a>
      <a href="https://www.instagram.com/jlhm98/" target="_blank">
        <img src="https://img.shields.io/badge/-@jlhm98-E4405F?style=flat-square&amp;logo=Instagram" alt="Instagram" />
      </a>
      <a href="https://open.spotify.com/user/12169733138?si=868c6a92e4a8451f" target="_blank">
        <img src="https://img.shields.io/badge/-@jlhm98-1DB954?style=flat-square&amp;logo=Spotify" alt="Spotify" />
      </a>
      <a href="mailto:joluhumu98@gmail.com">
        <img src="https://img.shields.io/badge/-joluhumu98@gmail.com-c14438?style=flat-square&amp;logo=Gmail&amp;logoColor=white" alt="Gmail" />
      </a>
    </div>
  </header>

  <!-- Sección de Investigación con tarjetas interactivas -->
  <section id="research">
    <h3>Research Work</h3>
    <p style="text-align:center;">
      I'm actively involved in research related to precision agriculture. Here are some of the papers I have collaborated on:
    </p>
    <div class="cards-container">
      <div class="card" onclick="window.open('https://www.mdpi.com/2072-4292/17/4/632', '_blank')">
        <div class="card-content">
          <h4>Paper 1</h4>
          <p>"Rice Yield Prediction Using Spectral and Textural Indices Derived from UAV Imagery and Machine Learning Models in Lambayeque, Peru"</p>
        </div>
      </div>
      <div class="card" onclick="window.open('https://www.mdpi.com/2072-4292/16/20/3882', '_blank')">
        <div class="card-content">
          <h4>Paper 2</h4>
          <p>"Water Use Efficiency in Rice Under Alternative Wetting and Drying Technique Using Energy Balance Model with UAV Information and AquaCrop in Lambayeque, Peru"</p>
        </div>
      </div>
      <div class="card" onclick="window.open('https://www.mdpi.com/2072-4292/16/5/796', '_blank')">
        <div class="card-content">
          <h4>Paper 3</h4>
          <p>"Water Stress Index and Stomatal Conductance under Different Irrigation Regimes with Thermal Sensors in Rice Fields on the Northern Coast of Peru"</p>
        </div>
      </div>
    </div>
  </section>

  <!-- Sección de Mapa Interactivo -->
  <section id="mapSection">
    <h3>Locations of Work</h3>
    <div id="map"></div>
  </section>

  <!-- Sección de Gráfico Dinámico -->
  <section id="chartSection">
    <h3>Research Overview</h3>
    <div id="chartContainer">
      <canvas id="researchChart"></canvas>
    </div>
  </section>

  <!-- Sección de GitHub Stats -->
  <section id="githubStats" style="text-align:center; padding:40px 20px;">
    <h3>GitHub Stats</h3>
    <img src="https://github-readme-stats.vercel.app/api?username=JLHM1998&show_icons=true&count_private=true" alt="JLHM1998 GitHub Stats" />
  </section>

  <!-- Scripts -->
  <!-- Leaflet JS para el mapa -->
  <script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>
  <!-- Chart.js para el gráfico -->
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <script>
    // Toggle de modo oscuro
    const toggleButton = document.getElementById('toggleDark');
    toggleButton.addEventListener('click', () => {
      document.body.classList.toggle('dark-mode');
      toggleButton.textContent = document.body.classList.contains('dark-mode') ? 'Modo Claro' : 'Modo Oscuro';
    });

    // Inicializar mapa con Leaflet
    var map = L.map('map').setView([-6.712, -79.835], 7); // Centro aproximado en Perú
    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
      maxZoom: 18
    }).addTo(map);
    // Marcadores de ejemplo
    L.marker([-6.712, -79.835]).addTo(map).bindPopup('Lambayeque, Peru');
    L.marker([-12.0464, -77.0428]).addTo(map).bindPopup('Lima, Peru');

    // Inicializar gráfico con Chart.js
    const ctx = document.getElementById('researchChart').getContext('2d');
    const researchChart = new Chart(ctx, {
      type: 'bar',
      data: {
        labels: ['Paper 1', 'Paper 2', 'Paper 3'],
        datasets: [{
          label: 'Citations',
          data: [50, 75, 30],
          backgroundColor: [
            'rgba(75, 192, 192, 0.2)',
            'rgba(153, 102, 255, 0.2)',
            'rgba(255, 159, 64, 0.2)'
          ],
          borderColor: [
            'rgba(75, 192, 192, 1)',
            'rgba(153, 102, 255, 1)',
            'rgba(255, 159, 64, 1)'
          ],
          borderWidth: 1
        }]
      },
      options: {
        scales: {
          y: {
            beginAtZero: true
          }
        }
      }
    });
  </script>
</body>
</html>
