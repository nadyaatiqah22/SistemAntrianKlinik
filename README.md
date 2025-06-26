<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>Sistem Antrian Klinik - Tema Daun</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      margin: 0;
      padding: 0;
      background: linear-gradient(to right, #16441a, #a5d6a7);
      color: #2e7d32;
    }

    .container {
      max-width: 600px;
      margin: 40px auto;
      background: #ffffff;
      border-radius: 15px;
      box-shadow: 0 8px 16px rgba(0,0,0,0.2);
      padding: 30px;
    }

    h2, h3 {
      text-align: center;
      color: #1b5e20;
    }

    label, input, button {
      display: block;
      width: 100%;
      margin: 10px 0;
    }

    input {
      padding: 10px;
      border-radius: 8px;
      border: 1px solid #81c784;
      outline: none;
    }

    button {
      padding: 10px;
      border: none;
      border-radius: 8px;
      background-color: #66bb6a;
      color: white;
      font-weight: bold;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }

    button:hover {
      background-color: #388e3c;
    }

    ul {
      list-style-type: none;
      padding: 0;
    }

    li {
      background-color: #c8e6c9;
      margin: 5px 0;
      padding: 10px;
      border-radius: 8px;
      box-shadow: 0 2px 4px rgba(0,0,0,0.1);
    }

    #currentPatient {
      text-align: center;
      margin-top: 20px;
      font-size: 1.2em;
      color: #2e7d32;
    }
  </style>
</head>
<body>

  <div class="container">
    <h2>🌿 Sistem Antrian Klinik</h2>

    <label for="patientName">Nama Pasien:</label>
    <input type="text" id="patientName" placeholder="Masukkan nama pasien">

    <button onclick="addToQueue()">Tambah ke Antrian</button>
    <button onclick="callNext()">Panggil Antrian Berikutnya</button>

    <h3>Antrian Saat Ini:</h3>
    <ul id="queueList"></ul>

    <h3 id="currentPatient">Pasien yang Dipanggil: -</h3>
  </div>

  <script>
    const queue = [];

    function addToQueue() {
      const nameInput = document.getElementById("patientName");
      const name = nameInput.value.trim();

      if (name === "") {
        alert("Nama pasien tidak boleh kosong.");
        return;
      }

      queue.push(name);
      nameInput.value = "";
      updateQueueDisplay();
    }

    function callNext() {
      if (queue.length === 0) {
        document.getElementById("currentPatient").innerText = "Pasien yang Dipanggil: Tidak ada antrian.";
        return;
      }

      const next = queue.shift();
      document.getElementById("currentPatient").innerText = "Pasien yang Dipanggil: " + next;
      updateQueueDisplay();
    }

    function updateQueueDisplay() {
      const list = document.getElementById("queueList");
      list.innerHTML = "";

      queue.forEach((name, index) => {
        const item = document.createElement("li");
        item.innerText = `${index + 1}. ${name}`;
        list.appendChild(item);
      });
    }
  </script>

</body>
</html>
