<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&display=swap');

    * { box-sizing: border-box; margin: 0; padding: 0; }

    body {
      background: #0d1117;
      color: #e6edf3;
      font-family: 'Inter', Arial, sans-serif;
      text-align: center;
      padding: 60px 20px 80px;
    }

    /* ── Header ── */
    .header {
      margin-bottom: 64px;
    }

    .header h1 {
      font-size: 2.4rem;
      font-weight: 700;
      letter-spacing: 6px;
      text-transform: uppercase;
      background: linear-gradient(90deg, #58a6ff, #a371f7, #f78166);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }

    .header .subtitle {
      margin-top: 10px;
      font-size: 0.85rem;
      font-weight: 300;
      letter-spacing: 3px;
      text-transform: uppercase;
      color: #8b949e;
    }

    .divider {
      width: 60px;
      height: 3px;
      background: linear-gradient(90deg, #58a6ff, #a371f7);
      border-radius: 2px;
      margin: 16px auto 0;
    }

    /* ── Section ── */
    .section {
      max-width: 720px;
      margin: 0 auto 52px;
    }

    .section-label {
      display: inline-block;
      font-size: 0.7rem;
      font-weight: 600;
      letter-spacing: 4px;
      text-transform: uppercase;
      color: #58a6ff;
      border: 1px solid #21262d;
      border-radius: 20px;
      padding: 5px 18px;
      margin-bottom: 24px;
      background: rgba(88, 166, 255, 0.05);
    }

    /* ── Icon row ── */
    .icon-row {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 14px;
      margin-bottom: 16px;
    }

    .icon-row img {
      filter: drop-shadow(0 0 6px rgba(88,166,255,0.15));
      transition: transform 0.2s;
    }

    /* ── Badge row ── */
    .badge-row {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 10px;
    }

    .badge-row img {
      border-radius: 6px;
    }

    /* ── Domain grid ── */
    .domain-grid {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 12px;
      max-width: 720px;
      margin: 0 auto;
    }

    .domain-card {
      background: #161b22;
      border: 1px solid #21262d;
      border-radius: 12px;
      padding: 14px 22px;
      font-size: 0.9rem;
      font-weight: 500;
      color: #c9d1d9;
      letter-spacing: 0.5px;
      display: flex;
      align-items: center;
      gap: 8px;
      transition: border-color 0.2s, background 0.2s;
    }

    .domain-card:hover {
      border-color: #58a6ff;
      background: rgba(88,166,255,0.06);
    }

    .domain-card .dot {
      width: 8px;
      height: 8px;
      border-radius: 50%;
      flex-shrink: 0;
    }

    /* dot colours per card */
    .dot-blue   { background: #58a6ff; }
    .dot-purple { background: #a371f7; }
    .dot-green  { background: #3fb950; }
    .dot-teal   { background: #39c5cf; }
    .dot-orange { background: #f78166; }
    .dot-yellow { background: #e3b341; }

    /* ── Footer ── */
    .footer {
      margin-top: 72px;
      font-size: 0.75rem;
      color: #30363d;
      letter-spacing: 2px;
      text-transform: uppercase;
    }
  </style>
</head>
<body>

  <!-- ── HEADER ── -->
  <div class="header">
    <h1>Expertise</h1>
    <p class="subtitle">Fahim Faisal &nbsp;·&nbsp; EEE &nbsp;·&nbsp; SUST</p>
    <div class="divider"></div>
  </div>

  <!-- ── EMBEDDED ── -->
  <div class="section">
    <div class="section-label">Embedded Systems</div>

    <div class="icon-row">
      <img src="https://skillicons.dev/icons?i=arduino"     height="52"/>
      <img src="https://skillicons.dev/icons?i=raspberrypi" height="52"/>
      <img src="https://skillicons.dev/icons?i=c"           height="52"/>
      <img src="https://skillicons.dev/icons?i=cpp"         height="52"/>
      <img src="https://skillicons.dev/icons?i=python"      height="52"/>
      <img src="https://cdn.simpleicons.org/stmicroelectronics" height="52"/>
    </div>

    <div class="badge-row">
      <img src="https://img.shields.io/badge/STM32-03234B?style=for-the-badge&logo=stmicroelectronics&logoColor=white"/>
      <img src="https://img.shields.io/badge/CubeIDE-0A66C2?style=for-the-badge&logoColor=white"/>
      <img src="https://img.shields.io/badge/HAL-1E1E1E?style=for-the-badge&logoColor=white"/>
    </div>
  </div>

  <!-- ── PCB & HARDWARE ── -->
  <div class="section">
    <div class="section-label">PCB &amp; Hardware Design</div>

    <div class="badge-row">
      <img src="https://img.shields.io/badge/EasyEDA-FF6C37?style=for-the-badge&logo=easyeda&logoColor=white"/>
      <img src="https://img.shields.io/badge/Eagle-FF9E0F?style=for-the-badge&logo=autodesk&logoColor=white"/>
      <img src="https://img.shields.io/badge/Altium-0A66C2?style=for-the-badge&logo=altiumdesigner&logoColor=white"/>
      <img src="https://img.shields.io/badge/Proteus-1E1E1E?style=for-the-badge&logoColor=white"/>
      <img src="https://img.shields.io/badge/Cadence-EE0000?style=for-the-badge&logo=cadence&logoColor=white"/>
    </div>
  </div>

  <!-- ── TOOLS ── -->
  <div class="section">
    <div class="section-label">Tools &amp; Software</div>

    <div class="icon-row">
      <img src="https://skillicons.dev/icons?i=vscode"  height="52"/>
      <img src="https://skillicons.dev/icons?i=matlab"  height="52"/>
      <img src="https://skillicons.dev/icons?i=git"     height="52"/>
      <img src="https://skillicons.dev/icons?i=github"  height="52"/>
    </div>

    <div class="badge-row">
      <img src="https://img.shields.io/badge/Fusion%20360-FF6C00?style=for-the-badge&logo=autodesk&logoColor=white"/>
    </div>
  </div>

  <!-- ── DOMAINS ── -->
  <div class="section">
    <div class="section-label">Areas of Expertise</div>

    <div class="domain-grid">
      <div class="domain-card"><span class="dot dot-blue"></span>   Robotics</div>
      <div class="domain-card"><span class="dot dot-purple"></span> Embedded Systems</div>
      <div class="domain-card"><span class="dot dot-green"></span>  PCB Design</div>
      <div class="domain-card"><span class="dot dot-teal"></span>   IoT</div>
      <div class="domain-card"><span class="dot dot-orange"></span> Machine Learning</div>
      <div class="domain-card"><span class="dot dot-yellow"></span> 3D Modeling</div>
    </div>
  </div>

  <div class="footer">Shahjalal University of Science &amp; Technology &nbsp;·&nbsp; Sylhet</div>

</body>
</html>
