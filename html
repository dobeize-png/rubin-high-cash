<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Rubin High Cash - Simulador Automático</title>
  <style>
    body { font-family: Arial, sans-serif; background: #121212; color: #fff; display: flex; flex-direction: column; align-items: center; padding: 10px; }
    h1 { color: #00ff99; margin-bottom: 10px; }
    #chart { width: 100%; max-width: 500px; height: 200px; background: #222; margin-bottom: 10px; display: flex; align-items: flex-end; justify-content: flex-start; }
    .bar { width: 10px; margin-right: 2px; }
    .call { background: #0f0; }
    .put { background: #f00; }
    .info { margin: 5px 0; font-size: 16px; }
  </style>
</head>
<body>
  <h1>Rubin High Cash</h1>
  <div id="chart"></div>
  <div class="info" id="price">Preço atual: --</div>
  <div class="info" id="time">Tempo para fechamento da vela: --</div>
  <div class="info" id="signal">Sinal: --</div>

  <script>
    // CONFIGURAÇÃO
    const TIMEFRAME = 120; // 2 minutos em segundos
    const TRIGGER_BEFORE_CLOSE = 77; // segundos antes do fechamento
    const MAX_CANDLES = 30;

    let candles = [];

    async function fetchPrice() {
      try {
        const response = await fetch('https://api.exchangerate.host/latest?base=EUR&symbols=USD');
        const data = await response.json();
        return parseFloat(data.rates.USD.toFixed(5));
      } catch (e) {
        console.error('Erro ao buscar preço:', e);
        return null;
      }
    }

    function updateChart() {
      const chartDiv = document.getElementById('chart');
      chartDiv.innerHTML = '';
      candles.forEach(c => {
        const bar = document.createElement('div');
        bar.classList.add('bar');
        bar.classList.add(c.signal === 'CALL' ? 'call' : 'put');
        bar.style.height = Math.min(200, c.price * 20) + 'px';
        chartDiv.appendChild(bar);
      });
    }

    function triggerSignal(candle) {
      if (candles.length < 1) return;
      const lastPrice = candles[candles.length - 1].price;
      candle.signal = candle.price > lastPrice ? 'CALL' : 'PUT';
      document.getElementById('signal').innerText = 'Sinal: ' + candle.signal;
    }

    async function tick() {
      const price = await fetchPrice();
      if (price === null) return;

      const now = new Date();
      const seconds = now.getSeconds() + now.getMinutes() * 60;
      const timeToClose = TIMEFRAME - (seconds % TIMEFRAME);

      document.getElementById('price').innerText = 'Preço atual: ' + price;
      document.getElementById('time').innerText = 'Tempo para fechamento da vela: ' + timeToClose + 's';

      let candle = { price, time: now, signal: null };

      if (timeToClose === TRIGGER_BEFORE_CLOSE) {
        triggerSignal(candle);
      }

      if (timeToClose === TIMEFRAME) {
        candles.push(candle);
        if (candles.length > MAX_CANDLES) candles.shift();
        updateChart();
      }
    }

    setInterval(tick, 1000);
  </script>
</body>
</html>
