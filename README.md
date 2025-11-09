# stock bazzar
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Stock Bazzar - By Nischal Neupane</title>
  <style>
    /* === General Page Styling === */
    body {
      font-family: "Poppins", sans-serif;
      background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
      margin: 0;
      padding: 0;
      color: #fff;
      text-align: center;
    }

    header {
      background: rgba(0, 0, 0, 0.2);
      padding: 20px 10px;
      box-shadow: 0 2px 10px rgba(0,0,0,0.3);
    }

    header h1 {
      font-size: 2.5em;
      margin: 0;
      color: #fffa;
    }

    header p {
      font-size: 1.1em;
      margin-top: 5px;
      color: #eee;
    }

    /* === Stock Container === */
    .stock-container {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 20px;
      padding: 30px;
      max-width: 1200px;
      margin: auto;
    }

    /* === Stock Card === */
    .stock-card {
      background: rgba(255, 255, 255, 0.15);
      border-radius: 20px;
      padding: 20px;
      box-shadow: 0 8px 20px rgba(0,0,0,0.2);
      transition: transform 0.3s ease, background 0.3s ease;
    }

    .stock-card:hover {
      transform: scale(1.05);
      background: rgba(255, 255, 255, 0.25);
    }

    .stock-name {
      font-size: 1.4em;
      margin-bottom: 10px;
      font-weight: bold;
    }

    .stock-value {
      font-size: 1.2em;
      color: #fffa;
      margin: 5px 0;
    }

    .stock-change {
      font-size: 1em;
      margin-top: 5px;
      font-weight: bold;
    }

    .positive {
      color: #00ff7f;
    }

    .negative {
      color: #ff4d4d;
    }

    footer {
      background: rgba(0, 0, 0, 0.2);
      padding: 15px;
      font-size: 0.9em;
      color: #ddd;
      margin-top: 30px;
    }
  </style>
</head>
<body>

  <header>
    <h1>📈 Stock Bazzar</h1>
    <p>Designed and Developed by <strong>Nischal Neupane</strong></p>
  </header>

  <div class="stock-container" id="stockContainer">
    <!-- Stock Cards will be generated here -->
  </div>

  <footer>
    © 2025 Stock Bazzar | Powered by Nischal Neupane
  </footer>

  <script>
    // === Sample Stock Data ===
    const stocks = [
      { name: "NABIL Bank", value: 890 },
      { name: "NEPSE Index", value: 2120 },
      { name: "Hydro Power Ltd", value: 480 },
      { name: "NIC Asia", value: 1020 },
      { name: "Nepal Telecom", value: 1350 },
      { name: "Prabhu Bank", value: 560 },
      { name: "Sanima Bank", value: 700 },
      { name: "Upper Tamakoshi", value: 420 }
    ];

    // === Generate Stock Cards ===
    const container = document.getElementById('stockContainer');
    function renderStocks() {
      container.innerHTML = '';
      stocks.forEach(stock => {
        const change = (Math.random() * 4 - 2).toFixed(2); // Random change between -2 and +2
        const changeClass = change >= 0 ? 'positive' : 'negative';
        const card = `
          <div class="stock-card">
            <div class="stock-name">${stock.name}</div>
            <div class="stock-value">Rs. ${(stock.value).toFixed(2)}</div>
            <div class="stock-change ${changeClass}">
              ${change >= 0 ? '▲' : '▼'} ${change}%
            </div>
          </div>`;
        container.innerHTML += card;
      });
    }

    // === Simulate Live Updates ===
    function updatePrices() {
      stocks.forEach(stock => {
        const randomChange = Math.random() * 4 - 2; // -2% to +2%
        stock.value += stock.value * (randomChange / 100);
      });
      renderStocks();
    }

    renderStocks();
    setInterval(updatePrices, 3000); // Update every 3 seconds
  </script>

</body>
</html>
