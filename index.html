<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Kuisioner Gadget</title>

<style>
    body {
        font-family: "Poppins", sans-serif;
        background: linear-gradient(135deg, #b388ff, #7c4dff, #651fff);
        min-height: 100vh;
        margin: 0;
        padding: 20px;
        display: flex;
        justify-content: center;
    }

    .container {
        max-width: 1100px;
        width: 100%;
        display: flex;
        flex-direction: column; /* jadikan memanjang ke bawah */
        gap: 20px;
        align-items: center;
    }

    /* --- FORM AREA --- */
    .form-box {
        width: 100%;
        background: rgba(255, 255, 255, 0.25);
        padding: 25px;
        border-radius: 20px;
        backdrop-filter: blur(12px);
        box-shadow: 0 8px 20px rgba(0,0,0,0.15);
    }

    .form-box h2 {
        margin-top: 0;
        color: #fff;
        font-weight: 600;
        font-size: 24px;
    }

    label {
        display: block;
        margin-top: 15px;
        font-weight: 600;
        color: #fff;
    }

    select, input, textarea {
        width: 100%;
        padding: 10px;
        margin-top: 6px;
        border-radius: 10px;
        border: none;
        outline: none;
        font-size: 15px;
    }

    .question {
        background: rgba(255, 255, 255, 0.45);
        padding: 15px;
        margin-top: 15px;
        border-radius: 12px;
        color: #333;
    }

    /* --- BUTTONS --- */
    button {
        margin-top: 20px;
        padding: 12px 20px;
        font-size: 16px;
        border-radius: 10px;
        border: none;
        cursor: pointer;
        font-weight: 600;
    }

    #submitBtn {
        background: #5e35b1;
        color: white;
    }

    #reset {
        background: #d1c4e9;
    }

    /* --- SUMMARY (sekarang memanjang ke bawah) --- */
    .summary {
        width: 100%;
        background: rgba(255,255,255,0.25);
        backdrop-filter: blur(10px);
        padding: 20px;
        border-radius: 20px;
        box-shadow: 0 8px 20px rgba(0,0,0,0.15);
        color: white;
        display: none; /* disembunyikan sampai ada hasil */
        text-align: left;
    }

    #donutChart {
        width: 100%;
        margin-top: 10px;
    }

    .result-box {
        margin-top: 10px;
        background: rgba(255,255,255,0.35);
        padding: 20px;
        border-radius: 15px;
        color: #333;
    }
</style>
</head>

<body>

<div class="container">

    <!-- FORM -->
    <div class="form-box">
        <h2>Kuesioner Kecanduan Gadget & Dampak Kognitif</h2>

        <form id="survey">

            <label>Nama (opsional)</label>
            <input type="text" id="nama" name="nama" placeholder="Isi bila diperlukan">

            <label>Tingkat Sekolah</label>
            <select id="kelas" required>
                <option value="" disabled selected>Pilih...</option>
                <option value="SMP">SMP / Sederajat</option>
                <option value="SMA">SMA / Sederajat</option>
            </select>

            <div id="questions"></div>

            <button id="submitBtn" type="submit">Lihat Hasil</button>
            <button id="reset" type="button">Reset</button>
        </form>

        <div id="resultArea" class="result-box"></div>
    </div>

    <!-- SUMMARY (sekarang memanjang ke bawah di bawah form) -->
    <div class="summary" id="summaryBox">
        <h3>Ringkasan</h3>
        <p id="sideScore"></p>
        <canvas id="donutChart"></canvas>
        <p id="sideLevel"></p>
    </div>

</div>

<!-- LIB: Chart.js dan jsPDF -->
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>

<script>
/* ===== PERTANYAAN (ditambah jadi 13) ===== */
const qs = [
    "Saya menggunakan gadget lebih dari 3 jam per hari.",
    "Saya kesulitan berhenti bermain gadget meskipun sudah berniat berhenti.",
    "Saya merasa cemas atau gelisah ketika tidak memegang gadget.",
    "Gadget mengganggu fokus belajar saya.",
    "Saya sering mengabaikan pekerjaan/PR karena bermain gadget.",
    "Saya tidur lebih larut karena bermain gadget.",
    "Saya sering membuka gadget tanpa alasan penting.",
    "Saya merasa marah jika penggunaan gadget saya dibatasi.",
    "Penggunaan gadget membuat nilai akademik saya menurun.",
    "Saya lebih memilih gadget daripada berinteraksi langsung.",
    "Saya menggunakan gadget saat makan atau berbicara dengan keluarga.",
    "Saya merasa waktu cepat berlalu saat menggunakan gadget.",
    "Saya sering menggunakan gadget saat mengerjakan tugas sekolah."
];

/* ===== GENERATE PERTANYAAN ===== */
const qBox = document.getElementById("questions");
qs.forEach((q, i) => {
    qBox.innerHTML += `
        <div class="question">
            <p><strong>${i+1}. ${q}</strong></p>
            <select required id="q${i}">
                <option value="" disabled selected>Pilih jawaban</option>
                <option value="1">1 - Sangat Tidak Setuju</option>
                <option value="2">2 - Tidak Setuju</option>
                <option value="3">3 - Netral</option>
                <option value="4">4 - Setuju</option>
                <option value="5">5 - Sangat Setuju</option>
            </select>
        </div>
    `;
});

/* ===== HITUNG SKOR ===== */
function getScore() {
    let total = 0;
    let answered = 0;

    qs.forEach((_, i) => {
        const el = document.getElementById("q" + i);
        const v = el ? el.value : "";
        if (v !== "") {
            answered++;
            total += Number(v);
        }
    });

    return { total, answered };
}

/* ===== INTERPRETASI ===== */
function interpret(score) {
    if (score <= 20)
        return { level: "Rendah", advice: "Penggunaan gadget masih tergolong sehat." };
    else if (score <= 35)
        return { level: "Sedang", advice: "Perlu pengaturan waktu penggunaan gadget." };
    else
        return { level: "Tinggi", advice: "Harus segera mengurangi intensitas penggunaan gadget." };
}

/* ===== DONUT CHART ===== */
let chart;

function renderChart(score, max) {
    const ctx = document.getElementById("donutChart");

    if (chart) chart.destroy();

    chart = new Chart(ctx, {
        type: 'doughnut',
        data: {
            labels: ["Skor", "Sisa Nilai"],
            datasets: [{
                data: [score, Math.max(0, max - score)],
                backgroundColor: ['#5e35b1', '#e0e0e0']
            }]
        },
        options: {
            responsive: true,
            cutout: "70%"
        }
    });
}

/* ===== KENDALI SUMMARY ===== */
const summaryBox = document.getElementById('summaryBox');
summaryBox.style.display = "none";

/* ===== PDF GENERATOR ===== */
function generatePDF(data) {
    const { nama, kelas, total, max, out } = data;
    const { jsPDF } = window.jspdf;
    const doc = new jsPDF();

    const title = "Hasil Kuisioner Kecanduan Gadget";
    const date = new Date().toLocaleString();

    doc.setFontSize(16);
    doc.text(title, 14, 20);
    doc.setFontSize(11);
    doc.text(`Tanggal: ${date}`, 14, 30);
    doc.text(`Nama: ${nama || '-'}`, 14, 38);
    doc.text(`Tingkat Sekolah: ${kelas}`, 14, 46);
    doc.text(`Skor: ${total} / ${max}`, 14, 54);
    doc.text(`Kategori: ${out.level}`, 14, 62);
    doc.text(`Saran:`, 14, 70);

    // wrap advice text if long
    const splitText = doc.splitTextToSize(out.advice, 180);
    doc.text(splitText, 14, 78);

    doc.save('kuisioner-result.pdf');
}

/* ===== SUBMIT ===== */
document.getElementById("survey").addEventListener("submit", (e) => {
    e.preventDefault();

    const { total, answered } = getScore();
    const max = qs.length * 5;

    if (answered < qs.length) {
        alert("Semua pertanyaan wajib dijawab.");
        return;
    }

    const out = interpret(total);

    /* --- tampilkan ringkasan di area bawah --- */
    summaryBox.style.display = "block";
    document.getElementById("sideScore").innerHTML = `<strong>Skor:</strong> ${total}/${max}`;
    document.getElementById("sideLevel").innerHTML = `<strong>Kategori:</strong> ${out.level}`;

    renderChart(total, max);

    /* --- tampilkan hasil lengkap di bawah form --- */
    const nama = document.getElementById("nama").value;
    const kelas = document.getElementById("kelas").value;

    document.getElementById("resultArea").innerHTML = `
        <h3>Hasil Kuisioner</h3>
        <p><strong>Nama:</strong> ${nama || '-'}</p>
        <p><strong>Tingkat Sekolah:</strong> ${kelas}</p>
        <p><strong>Skor Akhir:</strong> ${total} dari ${max}</p>
        <p><strong>Tingkat Risiko:</strong> ${out.level}</p>
        <p><strong>Saran:</strong> ${out.advice}</p>
        <div style="display:flex;gap:10px;flex-wrap:wrap">
          <button id="saveSend" type="button" style="background:#25D366;color:#fff">Simpan & Kirim ke WhatsApp</button>
          <button id="downloadPdf" type="button" style="background:#4caf50;color:#fff">Simpan PDF</button>
        </div>
        <p style="font-size:12px;margin-top:8px;color:#444">Setelah menyimpan PDF, klik tombol WhatsApp untuk membuka percakapan (wa.link/2xi7e5). File perlu dilampirkan secara manual di WhatsApp jika diperlukan.</p>
    `;

    // attach listeners to dynamic buttons
    document.getElementById("downloadPdf").addEventListener("click", () => {
        generatePDF({ nama, kelas, total, max, out });
    });

    document.getElementById("saveSend").addEventListener("click", () => {
        // generate dan unduh PDF terlebih dahulu
        generatePDF({ nama, kelas, total, max, out });

        // buka wa.link di tab baru
        // membuka wa.link sesuai permintaan, user dapat mengirim file secara manual di chat tersebut
        window.open('https://wa.link/erv0so', '_blank');
    });
});

/* ===== RESET ===== */
document.getElementById("reset").addEventListener("click", () => {
    document.getElementById("survey").reset();
    document.getElementById("resultArea").innerHTML = "";
    summaryBox.style.display = "none";
    if (chart) {
        chart.destroy();
        chart = null;
    }
});
</script>

</body>
</html>
