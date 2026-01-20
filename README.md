<!DOCTYPE html>
<html lang="ms">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kokurikulum Ceria SK Kita</title>
    <link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@400;600&family=Nunito:wght@400;700&display=swap" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
    
    <style>
        :root {
            --primary: #FF9F1C; /* Oren Ceria */
            --secondary: #2EC4B6; /* Hijau Laut */
            --accent: #FFBF69; /* Kuning Lembut */
            --bg: #CBF3F0; /* Biru Muda Background */
            --text: #2D3436;
        }

        body {
            font-family: 'Nunito', sans-serif;
            background-color: var(--bg);
            background-image: url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='none' fill-rule='evenodd'%3E%3Cg fill='%23ffffff' fill-opacity='0.4'%3E%3Cpath d='M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E");
            margin: 0;
            padding: 20px;
            color: var(--text);
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }

        .container {
            background: white;
            width: 100%;
            max-width: 500px;
            border-radius: 25px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
            overflow: hidden;
            border: 5px solid white;
        }

        .header {
            background-color: var(--secondary);
            padding: 30px 20px;
            text-align: center;
            color: white;
            border-bottom-left-radius: 25px;
            border-bottom-right-radius: 25px;
        }

        .header h1 {
            font-family: 'Fredoka', sans-serif;
            margin: 0;
            font-size: 28px;
            letter-spacing: 1px;
        }

        .header p {
            margin: 5px 0 0;
            font-size: 16px;
            opacity: 0.9;
        }

        .tabs {
            display: flex;
            justify-content: center;
            margin-top: 20px;
            gap: 10px;
            padding: 0 20px;
        }

        .tab-btn {
            background: #eee;
            border: none;
            padding: 12px 20px;
            border-radius: 50px;
            font-family: 'Fredoka', sans-serif;
            font-size: 16px;
            cursor: pointer;
            transition: all 0.3s ease;
            flex: 1;
            color: #777;
        }

        .tab-btn.active {
            background: var(--primary);
            color: white;
            transform: scale(1.05);
            box-shadow: 0 4px 10px rgba(255, 159, 28, 0.4);
        }

        .form-section {
            padding: 25px;
            display: none;
            animation: fadeIn 0.5s;
        }

        .form-section.active {
            display: block;
        }

        .input-group {
            margin-bottom: 15px;
        }

        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 700;
            color: var(--text);
        }

        input, select {
            width: 100%;
            padding: 12px;
            border: 2px solid #ddd;
            border-radius: 12px;
            font-size: 16px;
            font-family: 'Nunito', sans-serif;
            box-sizing: border-box; /* Fix padding issues */
            transition: border-color 0.3s;
        }

        input:focus, select:focus {
            outline: none;
            border-color: var(--secondary);
        }

        .submit-btn {
            width: 100%;
            background: var(--secondary);
            color: white;
            border: none;
            padding: 15px;
            border-radius: 12px;
            font-size: 18px;
            font-family: 'Fredoka', sans-serif;
            cursor: pointer;
            margin-top: 10px;
            box-shadow: 0 4px 0 #209a8e; /* 3D effect */
            transition: transform 0.1s;
        }

        .submit-btn:active {
            transform: translateY(4px);
            box-shadow: none;
        }

        .footer {
            text-align: center;
            padding: 15px;
            font-size: 12px;
            color: #888;
        }

        /* Loading Spinner */
        .loader {
            display: none;
            border: 4px solid #f3f3f3;
            border-top: 4px solid var(--primary);
            border-radius: 50%;
            width: 20px;
            height: 20px;
            animation: spin 1s linear infinite;
            margin: 0 auto;
        }

        @keyframes spin { 0% { transform: rotate(0deg); } 100% { transform: rotate(360deg); } }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }

    </style>
</head>
<body>

<div class="container">
    <div class="header">
        <h1>🌟 Unit Beruniform 🌟</h1>
        <p>SK Taman Anggerik, Johor Bahru</p>
    </div>

    <div class="tabs">
        <button class="tab-btn active" onclick="switchTab('daftar')">📝 Pendaftaran</button>
        <button class="tab-btn" onclick="switchTab('hadir')">🙋‍♂️ Kehadiran</button>
    </div>

    <div id="daftar" class="form-section active">
        <form id="formPendaftaran">
            <div class="input-group">
                <label>Nama Penuh Murid</label>
                <input type="text" name="nama" placeholder="Contoh: Ali bin Abu" required>
            </div>
            <div class="input-group">
                <label>Kelas</label>
                <select name="kelas" required>
                    <option value="">Pilih Kelas...</option>
                    <option value="4 Alamanda">4 Alamanda</option>
                    <option value="4 Akasia">4 Akasia</option>
                    <option value="5 Alamanda">5 Alamanda</option>
                    <option value="5 Akasia">5 Akasia</option>
                    <option value="6 Alamanda">6 Alamanda</option>
                    <option value="6 Akasia">6 Akasia</option>
                </select>
            </div>
            <div class="input-group">
                <label>Pilih Unit Beruniform</label>
                <select name="unit" required>
                    <option value="">Pilih Unit...</option>
                    <option value="Pengakap">⚜️ Pengakap</option>
                    <option value="TKRS">👮 Tunas Kadet Remaja</option>
                    <option value="BSMM">🚑 Bulan Sabit Merah</option>
                    <option value="Puteri Islam">🧕 Puteri Islam</option>
                </select>
            </div>
            <div class="input-group">
                <label>No. Telefon Penjaga</label>
                <input type="tel" name="phone" placeholder="Contoh: 0123456789" required>
            </div>
            
            <button type="submit" class="submit-btn">Hantar Pendaftaran 🚀</button>
            <div class="loader" id="loader1"></div>
        </form>
    </div>

    <div id="hadir" class="form-section">
        <form id="formKehadiran">
            <div class="input-group">
                <label>Nama Murid</label>
                <input type="text" name="nama" placeholder="Nama Penuh" required>
            </div>
            <div class="input-group">
                <label>Unit</label>
                <select name="unit" required>
                    <option value="">Pilih Unit...</option>
                    <option value="Pengakap">⚜️ Pengakap</option>
                    <option value="TKRS">👮 Tunas Kadet Remaja</option>
                    <option value="BSMM">🚑 Bulan Sabit Merah</option>
                    <option value="Puteri Islam">🧕 Puteri Islam</option>
                </select>
            </div>
            <div class="input-group">
                <label>Tarikh Aktiviti</label>
                <input type="date" name="tarikh" required>
            </div>
            <div class="input-group">
                <label>Catatan (Jika ada)</label>
                <input type="text" name="catatan" placeholder="Cth: Datang lewat sikit">
            </div>

            <button type="submit" class="submit-btn" style="background-color: var(--primary);">Sahkan Kehadiran ✅</button>
            <div class="loader" id="loader2"></div>
        </form>
    </div>

    <div class="footer">
        Dibuat dengan ❤️ untuk murid-murid.
    </div>
</div>

<script>
    // https://script.google.com/macros/s/AKfycbyq9FoxbxPa9m1D4jGwoR2QvPforwn3H3z9-DJ_2XkwvU9lzPyDv-jNSz4SVe6QO893Bg/exec
    const SCRIPT_URL = 'https://script.google.com/macros/s/AKfycbyq9FoxbxPa9m1D4jGwoR2QvPforwn3H3z9-DJ_2XkwvU9lzPyDv-jNSz4SVe6QO893Bg/exec';

    function switchTab(tabName) {
        // Hide all forms
        document.querySelectorAll('.form-section').forEach(el => el.classList.remove('active'));
        // Show selected form
        document.getElementById(tabName).classList.add('active');
        
        // Update button styles
        document.querySelectorAll('.tab-btn').forEach(btn => btn.classList.remove('active'));
        event.target.classList.add('active');
    }

    // Fungsi Hantar Pendaftaran
    document.getElementById('formPendaftaran').addEventListener('submit', function(e) {
        e.preventDefault();
        submitData(this, 'daftar', 'loader1');
    });

    // Fungsi Hantar Kehadiran
    document.getElementById('formKehadiran').addEventListener('submit', function(e) {
        e.preventDefault();
        submitData(this, 'hadir', 'loader2');
    });

    function submitData(form, type, loaderId) {
        const btn = form.querySelector('button');
        const loader = document.getElementById(loaderId);
        
        // UI Loading State
        btn.style.display = 'none';
        loader.style.display = 'block';

        // Ambil data form
        const formData = new FormData(form);
        const data = Object.fromEntries(formData);
        data.jenis = type; // Tambah tag jenis data

        fetch(SCRIPT_URL, {
            method: 'POST',
            body: JSON.stringify(data),
            mode: 'no-cors' // Penting untuk bypass isu CORS Google
        })
        .then(() => {
            // Success Alert (SweetAlert2)
            Swal.fire({
                title: 'Berjaya!',
                text: type === 'daftar' ? 'Pendaftaran diterima!' : 'Kehadiran direkodkan!',
                icon: 'success',
                confirmButtonText: 'Hebat!',
                confirmButtonColor: '#2EC4B6'
            });
            form.reset();
        })
        .catch(error => {
            Swal.fire({
                title: 'Alamak!',
                text: 'Ada masalah internet mungkin?',
                icon: 'error',
                confirmButtonText: 'Cuba lagi'
            });
            console.error('Error:', error);
        })
        .finally(() => {
            btn.style.display = 'block';
            loader.style.display = 'none';
        });
    }
</script>

</body>
</html>
