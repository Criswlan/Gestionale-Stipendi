# Gestionale-Stipendi
<!DOCTYPE html>
<html lang="it">
<head>
  <meta charset="UTF-8">
  <title>Gestionale Stipendi</title>
  <style>
    body {
      font-family: 'Comic Sans MS', cursive;
      background: url('https://wallpapers.com/images/featured-full/estetica-sailor-moon-3z3wzc7rf9fipos2.jpg') no-repeat center center fixed;
      background-size: cover;
      text-align: center;
      padding: 20px;
      color: #333;
    }
    h1 {
      font-family: "Brush Script MT", cursive;
      font-size: 2.5em;
      color: #ff66cc;
      text-shadow: 2px 2px #fff;
    }
    h2 {
      font-family: "Brush Script MT", cursive;
      font-size: 2em;
      color: #ff66cc;
      text-shadow: 1px 1px #fff;
    }
    table {
      width: 90%;
      margin: 20px auto;
      border-collapse: collapse;
      background: rgba(255, 255, 255, 0.9);
      border-radius: 20px;
      overflow: hidden;
      box-shadow: 0 8px 25px rgba(0,0,0,0.2);
    }
    th, td {
      padding: 10px;
      text-align: center;
      border-bottom: 1px solid #ddd;
    }
    th {
      background: #ffb3e6;
      color: #fff;
    }
    tr:hover {
      background: #ffe6f7;
    }
    input, select {
      width: 90%;
      padding: 6px;
      border: 2px solid #ff99cc;
      border-radius: 10px;
      text-align: center;
    }
    button {
      background: #ff99cc;
      color: white;
      border: none;
      padding: 8px 16px;
      border-radius: 15px;
      font-size: 0.9em;
      cursor: pointer;
      margin: 5px;
      transition: 0.2s;
    }
    button:hover {
      background: #ff66b2;
      transform: scale(1.05);
    }
    .card {
      background: rgba(255, 255, 255, 0.95);
      border-radius: 20px;
      box-shadow: 0 8px 20px rgba(0,0,0,0.2);
      padding: 20px;
      max-width: 400px;
      margin: 40px auto;
    }
    .result {
      margin-top: 20px;
      font-size: 1.1em;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <h1>𝒢𝑒𝓈𝓉𝒾𝑜𝓃𝒶𝓁𝑒 𝒮𝓉𝒾𝓅𝑒𝓃𝒹𝒾</h1>

  <table id="stipendiTable">
    <thead>
      <tr>
        <th>Ruolo</th>
        <th>Dipendente</th>
        <th>Fatturato</th>
        <th>Tassazione %</th>
        <th>Fatturato Tassato</th>
        <th>% Scaglione</th>
        <th>Ore</th>
        <th>Bonus</th>
        <th>Totale</th>
        <th>Totale + Bonus</th>
        <th>❌</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>
          <select onchange="calcolaRiga(this)">
            <option value="Referente Operativo">Referente Operativo</option>
            <option value="Responsabile">Responsabile</option>
            <option value="Vice Resp">Vice Resp</option>
            <option value="Agente Sr">Agente Sr</option>
            <option value="Agente" selected>Agente</option>
            <option value="Tirocinante">Tirocinante</option>
          </select>
        </td>
        <td><input type="text" value="Luna"></td>
        <td><input type="number" value="0" onchange="calcolaRiga(this)"></td>
        <td>
          <select onchange="calcolaRiga(this)">
            <option value="0">0%</option>
            <option value="0.05">5%</option>
            <option value="0.15">15%</option>
            <option value="0.25">25%</option>
            <option value="0.35" selected>35%</option>
            <option value="0.45">45%</option>
            <option value="0.55">55%</option>
            <option value="0.60">60%</option>
            <option value="0.65">65%</option>
          </select>
        </td>
        <td></td>
        <td></td>
        <td><input type="number" value="0" onchange="calcolaRiga(this)"></td>
        <td>
          <select onchange="calcolaRiga(this)">
            <option value="">—</option>
            <option value="Fatturato">Fatturato</option>
            <option value="Ore">Ore</option>
          </select>
        </td>
        <td></td>
        <td></td>
        <td><button onclick="rimuoviRiga(this)">❌</button></td>
      </tr>
    </tbody>
  </table>

  <button onclick="aggiungiRiga()">➕ Aggiungi Dipendente</button>

  <!-- Calcolatore magico -->
  <div class="card">
    <h2>𝒯𝒶𝓈𝓈𝒶𝓏𝒾𝑜𝓃𝑒</h2>
    <input type="number" id="val1" placeholder="Valore A">
    <input type="number" id="val2" placeholder="Valore B">
    <br>
    <button onclick="calcolaScaglione()">🌟 Trasformazione 🌟</button>
    <div class="result" id="risultato"></div>
  </div>

  <script>
    function calcolaRiga(elem) {
      const row = elem.closest("tr");
      const fatturato = parseFloat(row.cells[2].children[0].value) || 0;
      const tassazione = parseFloat(row.cells[3].children[0].value) || 0;

      const fatturatoTassato = fatturato * (1 - tassazione);
      row.cells[4].innerText = "€" + fatturatoTassato.toFixed(2);

      // scaglioni %
      let perc = 0;
      if (fatturatoTassato > 2000 && fatturatoTassato <= 10000) perc = 0.025;
      else if (fatturatoTassato <= 20000) perc = 0.05;
      else if (fatturatoTassato <= 30000) perc = 0.075;
      else if (fatturatoTassato > 30000) perc = 0.1;
      row.cells[5].innerText = (perc*100).toFixed(1) + "%";

      const ore = parseInt(row.cells[6].children[0].value) || 0;
      const bonusText = row.cells[7].children[0].value || "";

      // base per ruolo
      const ruolo = row.cells[0].children[0].value;
      let base = 0;
      if (ruolo === "Referente Operativo") base = 4000;
      else if (ruolo === "Responsabile") base = 3000;
      else if (ruolo === "Vice Resp") base = 2500;
      else if (ruolo === "Agente Sr") base = 2000;
      else if (ruolo === "Agente") base = 1750;
      else if (ruolo === "Tirocinante") base = 1500;

      // totale senza bonus
      let totale = base + (fatturatoTassato * perc);
      row.cells[8].innerText = "€" + totale.toFixed(2);

      // extra
      let extra = 0;
      if (ore > 6) extra += Math.floor((ore - 6) / 3) * 10;
      if (bonusText === "Fatturato") extra += 100;
      if (bonusText === "Ore") extra += 100;

      row.cells[9].innerText = "€" + (totale + extra).toFixed(2);
    }

    function aggiungiRiga() {
      const table = document.getElementById("stipendiTable").querySelector("tbody");
      const newRow = table.rows[0].cloneNode(true);
      newRow.querySelectorAll("input").forEach(inp => inp.value = "");
      newRow.querySelectorAll("select").forEach(sel => sel.selectedIndex = 0);
      for (let i = 4; i <= 9; i++) newRow.cells[i].innerText = "";
      table.appendChild(newRow);
    }

    function rimuoviRiga(btn) {
      const row = btn.closest("tr");
      const table = document.getElementById("stipendiTable").querySelector("tbody");
      if (table.rows.length > 1) row.remove();
      else alert("Non puoi eliminare tutte le righe!");
    }

    function calcolaScaglione() {
      const v1 = parseFloat(document.getElementById("val1").value) || 0;
      const v2 = parseFloat(document.getElementById("val2").value) || 0;
      const somma = v1 + v2;

      let aliquota = 0;
      if (somma <= 25000) aliquota = 0;
      else if (somma <= 75000) aliquota = 0.05;
      else if (somma <= 125000) aliquota = 0.15;
      else if (somma <= 200000) aliquota = 0.25;
      else if (somma <= 350000) aliquota = 0.35;
      else if (somma <= 500000) aliquota = 0.45;
      else if (somma <= 750000) aliquota = 0.55;
      else if (somma <= 1000000) aliquota = 0.60;
      else aliquota = 0.65;

      const tasse = somma * aliquota;

      document.getElementById("risultato").innerHTML = `
        🌟 Somma: €${somma.toLocaleString()} <br>
        🌟 Aliquota: ${(aliquota*100).toFixed(0)}% <br>
        🌟 Totale Tassa: €${tasse.toLocaleString()}
      `;
    }
  </script>
</body>
</html>
