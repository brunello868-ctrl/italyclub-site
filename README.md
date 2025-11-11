# italyclub-site <!DOCTYPE html>
<html lang="it">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ItalyClub - Server Minecraft</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=MedievalSharp&display=swap');

    body {
      margin: 0;
      font-family: 'MedievalSharp', cursive;
      background: url('https://i.imgur.com/x1GOfIu.jpeg') no-repeat center center fixed;
      background-size: cover;
      color: #f1e2b6;
      text-align: center;
    }

    header {
      background: rgba(0, 0, 0, 0.7);
      padding: 30px;
      border-bottom: 3px solid #a87b2f;
    }

    h1 {
      font-size: 3em;
      color: #d4af37;
      text-shadow: 2px 2px 6px #000;
    }

    .ip-box {
      background: rgba(0, 0, 0, 0.6);
      border: 2px solid #a87b2f;
      border-radius: 10px;
      display: inline-block;
      padding: 15px 25px;
      margin-top: 10px;
      font-size: 1.2em;
    }

    #player-count {
      color: #85e085;
      font-weight: bold;
    }

    section {
      background: rgba(0, 0, 0, 0.5);
      margin: 40px auto;
      padding: 20px;
      width: 80%;
      border: 2px solid #a87b2f;
      border-radius: 10px;
      box-shadow: 0 0 15px #000;
    }

    footer {
      background: rgba(0, 0, 0, 0.8);
      padding: 20px;
      border-top: 3px solid #a87b2f;
      color: #ccc;
      font-size: 0.9em;
    }

    button {
      background: #a87b2f;
      color: #000;
      border: none;
      padding: 10px 20px;
      border-radius: 5px;
      font-size: 1.1em;
      cursor: pointer;
      transition: 0.3s;
    }

    button:hover {
      background: #d4af37;
    }
  </style>
</head>
<body>
  <header>
    <h1>⚔️ ItalyClub ⚔️</h1>
    <div class="ip-box">
      IP Server: <span id="server-ip">italyclub.gamesrv.top</span><br>
      Giocatori online: <span id="player-count">Caricamento...</span>
    </div>
  </header>

  <section>
    <h2>Benvenuto nel regno di ItalyClub</h2>
    <p>
      Entra in un mondo medievale pieno di avventure, castelli e battaglie!<br>
      Unisciti ai nostri eroi e conquista la gloria nel regno di <strong>ItalyClub</strong>.
    </p>
    <button onclick="copyIP()">Copia IP</button>
  </section>

  <footer>
    © 2025 ItalyClub - Tutti i diritti riservati
  </footer>

  <script>
    // Funzione per copiare l'IP
    function copyIP() {
      navigator.clipboard.writeText("italyclub.gamesrv.top");
      alert("IP copiato: italyclub.gamesrv.top");
    }

    // Mostra numero giocatori online
    async function getPlayerCount() {
      const response = await fetch("https://api.mcsrvstat.us/2/italyclub.gamesrv.top");
      const data = await response.json();
      const countEl = document.getElementById("player-count");

      if (data && data.online) {
        countEl.textContent = data.players.online + " / " + data.players.max;
      } else {
        countEl.textContent = "Offline";
        countEl.style.color = "#ff6b6b";
      }
    }

    getPlayerCount();
    setInterval(getPlayerCount, 60000); // aggiorna ogni minuto
  </script>
</body>
</html>


