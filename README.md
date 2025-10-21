# ramalan-dts
ini adalah ramalan tentang percintaan dan karir dari dede tri sapana
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ramalan DTS: Takdir di Tanganmu</title>
    
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap');
        
        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%); /* Latar Biru Tua Gradasi */
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            padding: 20px;
        }
        .container {
            background-color: #ffffff;
            padding: 40px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            max-width: 550px;
            width: 100%;
        }
        h1 {
            text-align: center;
            color: #1e3c72;
            margin-bottom: 10px;
            font-size: 2em;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.1);
        }
        h3 {
            text-align: center;
            color: #666;
            margin-bottom: 25px;
            font-weight: 400;
        }
        label {
            display: block;
            margin-bottom: 5px;
            font-weight: 600;
            color: #333;
        }
        input[type="text"], input[type="number"], select {
            width: 100%;
            padding: 12px;
            margin-bottom: 20px;
            border: 1px solid #ddd;
            border-radius: 8px;
            box-sizing: border-box;
            font-size: 16px;
            transition: border-color 0.3s;
        }
        input:focus, select:focus {
            border-color: #2a5298;
            outline: none;
        }
        button {
            width: 100%;
            padding: 15px;
            background-color: #ff6b6b; /* Warna Tombol Merah Muda */
            color: white;
            border: none;
            border-radius: 8px;
            font-size: 1.1em;
            font-weight: 700;
            cursor: pointer;
            transition: background-color 0.3s ease, transform 0.1s;
        }
        button:hover {
            background-color: #e64a4a;
            transform: translateY(-2px);
        }
        #hasilRamalan {
            margin-top: 30px;
            padding: 25px;
            border: 3px solid #1e3c72;
            border-radius: 10px;
            background-color: #f0f8ff; /* Latar hasil yang lebih cerah */
            min-height: 150px;
            display: none;
            white-space: pre-wrap;
            box-shadow: inset 0 0 8px rgba(0, 0, 0, 0.05);
            line-height: 1.6;
        }
        .judul-hasil {
            color: #1e3c72;
            font-size: 1.5em;
            font-weight: 700;
            text-align: center;
            margin-bottom: 15px;
            border-bottom: 2px dashed #ccc;
            padding-bottom: 10px;
        }
        .peringatan-ramalan {
            margin-top: 20px;
            font-size: 0.9em;
            padding: 10px;
            border-left: 5px solid #ff6b6b;
            background-color: #fff0f0;
            color: #555;
            font-style: italic;
            border-radius: 5px;
        }
    </style>
</head>
<body>

<div class="container">
    <h1>🔮 Ramalan DTS 🌟</h1>
    <h3>Takdir di Tanganmu: Ramalan Hanya Pemanis</h3>
    
    <form id="formRamalan">
        <label for="nama">1. Nama Anda:</label>
        <input type="text" id="nama" required placeholder="Cth: Lintang">

        <label for="umur">2. Umur (tahun):</label>
        <input type="number" id="umur" required min="1" max="120" placeholder="Cth: 28">

        <label for="kota">3. Kota Tempat Tinggal:</label>
        <input type="text" id="kota" required placeholder="Cth: Yogyakarta">

        <label for="zodiak">4. Zodiak Anda:</label>
        <select id="zodiak" required>
            <option value="">-- Pilih Zodiak --</option>
            <option value="Aries">Aries (21 Mar - 19 Apr)</option>
            <option value="Taurus">Taurus (20 Apr - 20 Mei)</option>
            <option value="Gemini">Gemini (21 Mei - 20 Jun)</option>
            <option value="Cancer">Cancer (21 Jun - 22 Jul)</option>
            <option value="Leo">Leo (23 Jul - 22 Agu)</option>
            <option value="Virgo">Virgo (23 Agu - 22 Sep)</option>
            <option value="Libra">Libra (23 Sep - 22 Okt)</option>
            <option value="Scorpio">Scorpio (23 Okt - 21 Nov)</option>
            <option value="Sagitarius">Sagitarius (22 Nov - 21 Des)</option>
            <option value="Capricorn">Capricorn (22 Des - 19 Jan)</option>
            <option value="Aquarius">Aquarius (20 Jan - 18 Feb)</option>
            <option value="Pisces">Pisces (19 Feb - 20 Mar)</option>
        </select>

        <label for="fokus">5. Fokus Ramalan:</label>
        <select id="fokus" required>
            <option value="">-- Pilih Fokus --</option>
            <option value="Karir">Karir & Keuangan</option>
            <option value="Cinta">Cinta & Hubungan</option>
        </select>

        <button type="submit" id="tombolRamal">RAMAL TAKDIRKU!</button>
    </form>

    <div id="hasilRamalan">
        </div>
</div>

<script>
    document.getElementById('formRamalan').addEventListener('submit', function(e) {
        e.preventDefault(); 

        // 1. Ambil Data Input
        const nama = document.getElementById('nama').value.trim();
        const umur = parseInt(document.getElementById('umur').value);
        const kota = document.getElementById('kota').value.trim();
        const zodiak = document.getElementById('zodiak').value;
        const fokus = document.getElementById('fokus').value;
        const hasilDiv = document.getElementById('hasilRamalan');
        
        // Cek jika ada input yang kosong
        if (!nama || isNaN(umur) || !kota || !zodiak || !fokus) {
            hasilDiv.style.display = 'block';
            hasilDiv.innerHTML = "<div class='judul-hasil'>⚠️ Kesalahan Input</div><p style='color:red; text-align:center;'>Harap isi semua kolom dengan benar sebelum meminta ramalan, ${nama}!</p>";
            return;
        }

        // 2. Data Acak untuk Ramalan Panjang
        const elemen = ['Api', 'Air', 'Tanah', 'Udara'];
        const kartu = ['Bintang Keberanian', 'Matahari Kebijaksanaan', 'Bulan Perenungan', 'Menara Perubahan'];
        const elemenAcak = elemen[Math.floor(Math.random() * elemen.length)];
        const kartuAcak = kartu[Math.floor(Math.random() * kartu.length)];
        const energiUmur = (umur % 5 === 0) ? "kuat dan stabil" : "penuh dinamika";

        let judulInti = "";
        let ramalanInti = "";

        // 3. Logika Ramalan Berdasarkan Fokus
        if (fokus === "Cinta") {
            judulInti = "Pusat Energi: ROMANSA & RELASI";
            const statusCinta = [
                `Anda sedang berada di bawah pengaruh 'Cahaya ${kartuAcak}'. Bagi yang lajang, semesta akan mempertemukan Anda dengan seseorang yang memiliki energi ${elemenAcak} di kota **${kota}**. Perkenalan akan terjadi di tempat yang berhubungan dengan hobi atau kegiatan intelektual.`,
                `Ramalan menunjukkan periode 'Harmoni dan Kompromi'. Bagi yang sudah berpasangan, hubungan Anda akan memasuki fase pendalaman emosional. Tantangannya adalah komunikasi. Pastikan Anda dan pasangan tidak hanya mendengar, tapi benar-benar *menyelami* perasaan satu sama lain. Kehidupan romantis akan cemerlang di bawah **Bulan Agustus** ini.`,
                `Kartu 'Pencarian Jati Diri' muncul. Sebelum menemukan belahan jiwa, Anda dianjurkan untuk fokus pada diri sendiri. Cinta yang datang mungkin membawa pelajaran berat, tetapi sangat berharga. Orang dengan usia ${Math.floor(umur / 2) + 10} tahun mungkin memainkan peran penting dalam babak kisah Anda.`
            ];
            ramalanInti = statusCinta[Math.floor(Math.random() * statusCinta.length)];
            
        } else if (fokus === "Karir") {
            judulInti = "Pusat Energi: KARIR & PENCAPAIAN";
            const statusKarir = [
                `Anda dilingkupi aura 'Terobosan dan Promosi'. Zodiak ${zodiak} Anda menunjukkan energi yang **${energiUmur}**. Ini adalah waktu ideal untuk meminta kenaikan jabatan atau memulai usaha baru. Sebuah ide brilian yang terkait dengan **${kota}** akan menjadi kunci kesuksesan finansial.`,
                `Ramalan 'Perjalanan dan Ekspansi' muncul. Anda mungkin akan mendapat peluang kerja yang mengharuskan Anda berpindah ke luar kota, atau terlibat dalam proyek berskala internasional. Keuangan akan stabil, tetapi diperlukan investasi kecil pada keterampilan (skill) baru. Mentor yang tepat akan muncul dari bidang ${elemenAcak}.`,
                `Kartu 'Ujian Ketekunan' muncul. Jangan menyerah jika ada hambatan di awal. Energi tahun ini menuntut Anda untuk menguasai detail. Kesuksesan finansial bukan datang dari keberuntungan, melainkan dari **disiplin** yang Anda bangun dalam 60 hari ke depan.`
            ];
            ramalanInti = statusKarir[Math.floor(Math.random() * statusKarir.length)];
        }
        
        // 4. Catatan Kaki Peringatan
        const catatanPeringatan = `
        <div class="peringatan-ramalan">
            <p><strong>PENTING, ${nama.toUpperCase()}!</strong></p>
            <p>Ramalan DTS ini adalah simulasi hiburan. Prediksi yang muncul **TIDAK 100% AKURAT ATAU BENAR**.</p>
            <p>Ini hanyalah pemanis. Takdir Anda bisa terjadi atau tidak, tergantung pada **kemauan, usaha keras, dan keberanian** Anda untuk meraihnya. Semangat!</p>
        </div>
        `;
        
        // 5. Gabungkan Hasil
        const hasilInti = `
        <div class="judul-hasil">HASIL RAMALAN DTS ${nama.toUpperCase()}</div>

        <p><strong>Data Dasar Energi:</strong></p>
        <p>Nama: ${nama} (${umur} tahun) | Zodiak: ${zodiak} | Kota Utama: ${kota}</p>
        <hr>

        <p><strong>${judulInti}</strong></p>
        <p>${ramalanInti}</p>
        <p><strong>Tarot Panduan:</strong> ${kartuAcak}</p>
        
        <br>
        
        `;

        // Tampilkan hasil
        hasilDiv.style.display = 'block';
        hasilDiv.innerHTML = hasilInti + catatanPeringatan;
        
        // Scroll ke hasil
        hasilDiv.scrollIntoView({ behavior: 'smooth' });
    });
</script>

</body>
</html>
