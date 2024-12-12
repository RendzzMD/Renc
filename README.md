<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ngetest HTML Req</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        label {
            display: block;
            margin-bottom: 10px;
        }
        input, select, button {
            width: 100%;
            margin-bottom: 15px;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            background-color: #4CAF50;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background-color: #45a049;
        }
    </style>
</head>
<body>
    <h2>Test Request Web</h2>
    <form id="requestForm">
        <label for="url">URL:</label>
        <input type="text" id="url" name="url" placeholder="Masukkan URL" required>

        <label for="method">Metode Request:</label>
        <select id="method" name="method">
            <option value="GET">GET</option>
            <option value="Bypass">Bypass</option>
            <option value="POST">POST</option>
        </select>

        <label for="jumlah">Jumlah Permintaan:</label>
        <input type="number" id="jumlah" name="jumlah" placeholder="Masukkan jumlah permintaan" required>

        <button type="button" onclick="kirimPermintaan()">Kirim Banyak Permintaan</button>
    </form>

    <p id="status"></p>

    <script>
        function kirimPermintaan() {
            const url = document.getElementById("url").value;
            const method = document.getElementById("method").value;
            const jumlah = document.getElementById("jumlah").value;

            if (!url || !jumlah) {
                alert("Harap isi semua kolom!");
                return;
            }

            document.getElementById("status").textContent = "Mengirim permintaan...";
            
            for (let i = 0; i < jumlah; i++) {
                fetch(url, { method })
                    .then(response => console.log(`Response ${i + 1}:`, response.status))
                    .catch(error => console.error(`Error ${i + 1}:`, error));
            }

            document.getElementById("status").textContent = "Permintaan terkirim!";
        }
    </script>
</body>
</html>
