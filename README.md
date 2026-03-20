<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>📋 Edukasi Nyeri — Skala VAS</title>
  <style>
    /* ===== RESET & BASE ===== */
    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(135deg, #e0f7fa 0%, #ffffff 50%, #fce4ec 100%);
      color: #333;
      line-height: 1.6;
      padding-bottom: 40px;
    }

    /* ===== HEADER ===== */
    .header {
      background: linear-gradient(135deg, #0d47a1, #1976d2, #42a5f5);
      color: #fff;
      text-align: center;
      padding: 28px 20px 22px;
      border-radius: 0 0 30px 30px;
      box-shadow: 0 4px 20px rgba(13,71,161,0.3);
    }
    .header h1 { font-size: 1.5rem; margin-bottom: 4px; }
    .header p  { font-size: 0.9rem; opacity: 0.9; }
    .header .icon-big { font-size: 2.5rem; margin-bottom: 6px; }

    /* ===== CONTAINER ===== */
    .container { max-width: 480px; margin: 0 auto; padding: 0 16px; }

    /* ===== SECTION TITLE ===== */
    .section-title {
      display: flex; align-items: center; gap: 8px;
      margin: 26px 0 12px; font-size: 1.1rem; font-weight: 700; color: #0d47a1;
    }

    /* ===== INFO BOX ===== */
    .info-box {
      background: #fff;
      border-left: 5px solid #1976d2;
      border-radius: 12px;
      padding: 16px;
      margin-bottom: 16px;
      box-shadow: 0 2px 10px rgba(0,0,0,0.06);
      font-size: 0.92rem;
    }

    /* ===== VAS VISUAL BAR ===== */
    .vas-bar-wrapper { margin: 20px 0 10px; }
    .vas-bar {
      height: 22px;
      border-radius: 12px;
      background: linear-gradient(90deg, #4caf50 0%, #8bc34a 25%, #ffeb3b 45%, #ff9800 70%, #f44336 90%, #b71c1c 100%);
      position: relative;
    }
    .vas-labels {
      display: flex; justify-content: space-between;
      font-size: 0.75rem; font-weight: 600; margin-top: 4px; color: #555;
    }

    /* ===== PAIN CARDS ===== */
    .pain-card {
      border-radius: 16px;
      padding: 18px;
      margin-bottom: 14px;
      box-shadow: 0 3px 12px rgba(0,0,0,0.07);
      display: flex;
      gap: 14px;
      align-items: flex-start;
    }
    .pain-card .emoji {
      font-size: 2.4rem;
      flex-shrink: 0;
      width: 50px; text-align: center;
    }
    .pain-card .content h3 { font-size: 1rem; margin-bottom: 2px; }
    .pain-card .content .score { font-size: 0.8rem; font-weight: 700; margin-bottom: 6px; }
    .pain-card .content p  { font-size: 0.85rem; margin-bottom: 4px; }
    .pain-card .content .examples {
      font-size: 0.8rem; color: #555;
      background: rgba(255,255,255,0.6);
      padding: 8px 10px; border-radius: 8px; margin-top: 6px;
    }

    /* Card colors */
    .card-none    { background: linear-gradient(135deg, #e8f5e9, #f1f8e9); border-left: 5px solid #4caf50; }
    .card-mild    { background: linear-gradient(135deg, #f1f8e9, #fffde7); border-left: 5px solid #8bc34a; }
    .card-moderate{ background: linear-gradient(135deg, #fff8e1, #fff3e0); border-left: 5px solid #ff9800; }
    .card-severe  { background: linear-gradient(135deg, #fbe9e7, #ffebee); border-left: 5px solid #f44336; }
    .card-worst   { background: linear-gradient(135deg, #ffebee, #fce4ec); border-left: 5px solid #b71c1c; }

    .card-none .score    { color: #2e7d32; }
    .card-mild .score    { color: #558b2f; }
    .card-moderate .score{ color: #e65100; }
    .card-severe .score  { color: #c62828; }
    .card-worst .score   { color: #b71c1c; }

    /* ===== HOW-TO STEPS ===== */
    .steps { counter-reset: step; }
    .step-item {
      background: #fff;
      border-radius: 12px;
      padding: 14px 14px 14px 52px;
      margin-bottom: 10px;
      position: relative;
      box-shadow: 0 2px 8px rgba(0,0,0,0.05);
      font-size: 0.9rem;
    }
    .step-item::before {
      counter-increment: step;
      content: counter(step);
      position: absolute; left: 14px; top: 14px;
      background: #1976d2; color: #fff;
      width: 28px; height: 28px;
      border-radius: 50%;
      display: flex; align-items: center; justify-content: center;
      font-weight: 700; font-size: 0.85rem;
    }

    /* ===== TIPS BOX ===== */
    .tips-box {
      background: linear-gradient(135deg, #e3f2fd, #e8eaf6);
      border-radius: 16px;
      padding: 18px;
      margin-bottom: 14px;
      box-shadow: 0 2px 10px rgba(0,0,0,0.06);
    }
    .tips-box h3 { color: #1565c0; font-size: 1rem; margin-bottom: 10px; }
    .tips-box ul { padding-left: 20px; font-size: 0.88rem; }
    .tips-box li { margin-bottom: 8px; }

    /* ===== INTERACTIVE SLIDER ===== */
    .interactive-section {
      background: #fff;
      border-radius: 16px;
      padding: 20px;
      text-align: center;
      box-shadow: 0 3px 15px rgba(0,0,0,0.08);
      margin-bottom: 16px;
    }
    .interactive-section h3 { color: #0d47a1; margin-bottom: 14px; font-size: 1rem; }
    .slider-container { margin: 16px 0; }
    input[type="range"] {
      -webkit-appearance: none; appearance: none;
      width: 100%; height: 14px;
      border-radius: 8px;
      background: linear-gradient(90deg, #4caf50, #8bc34a, #ffeb3b, #ff9800, #f44336, #b71c1c);
      outline: none;
    }
    input[type="range"]::-webkit-slider-thumb {
      -webkit-appearance: none; appearance: none;
      width: 30px; height: 30px;
      border-radius: 50%;
      background: #fff;
      border: 3px solid #0d47a1;
      cursor: pointer;
      box-shadow: 0 2px 8px rgba(0,0,0,0.2);
    }
    input[type="range"]::-moz-range-thumb {
      width: 30px; height: 30px;
      border-radius: 50%;
      background: #fff;
      border: 3px solid #0d47a1;
      cursor: pointer;
    }
    .slider-labels { display: flex; justify-content: space-between; font-size: 0.75rem; color: #777; margin-top: 4px; }
    .result-display {
      margin-top: 16px;
      padding: 14px;
      border-radius: 12px;
      font-size: 1rem;
      font-weight: 600;
      transition: all 0.3s ease;
    }

    /* ===== FOOTER ===== */
    .footer {
      text-align: center;
      margin-top: 30px;
      padding: 18px;
      font-size: 0.78rem;
      color: #888;
    }
    .footer a { color: #1976d2; text-decoration: none; }

    /* ===== ACCORDION (FAQ) ===== */
    details {
      background: #fff;
      border-radius: 12px;
      margin-bottom: 10px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.05);
      overflow: hidden;
    }
    summary {
      padding: 14px 16px;
      font-weight: 600;
      font-size: 0.92rem;
      cursor: pointer;
      list-style: none;
      display: flex; align-items: center; gap: 8px;
    }
    summary::-webkit-details-marker { display: none; }
    summary::before { content: "▸"; transition: transform 0.2s; }
    details[open] summary::before { transform: rotate(90deg); }
    details .detail-content { padding: 0 16px 14px; font-size: 0.88rem; color: #555; }
  </style>
</head>
<body>

  <!-- ===== HEADER ===== -->
  <div class="header">
    <div class="icon-big">🩺</div>
    <h1>Kenali Nyeri Anda</h1>
    <p>Panduan Memahami Skala Nyeri VAS<br/>(Visual Analog Scale)</p>
  </div>

  <div class="container">

    <!-- ===== APA ITU VAS ===== -->
    <div class="section-title">📖 Apa Itu Skala VAS?</div>
    <div class="info-box">
      <strong>Visual Analog Scale (VAS)</strong> adalah alat ukur nyeri berupa
      <strong>garis lurus sepanjang 10 cm</strong>, dengan ujung kiri menandakan
      <em>"Tidak Ada Nyeri" (0)</em> dan ujung kanan menandakan
      <em>"Nyeri Paling Hebat" (10)</em>.<br/><br/>
      Anda cukup <strong>menunjuk atau menandai</strong> satu titik pada garis
      yang paling menggambarkan rasa nyeri Anda saat ini.
    </div>

    <!-- ===== VISUAL BAR ===== -->
    <div class="vas-bar-wrapper">
      <div class="vas-bar"></div>
      <div class="vas-labels">
        <span>0</span><span>1</span><span>2</span><span>3</span><span>4</span>
        <span>5</span><span>6</span><span>7</span><span>8</span><span>9</span><span>10</span>
      </div>
    </div>

    <!-- ===== CARA MENGGUNAKAN ===== -->
    <div class="section-title">📝 Cara Menggunakan</div>
    <div class="steps">
      <div class="step-item">Perawat memberikan garis skala VAS kepada Anda.</div>
      <div class="step-item">Perhatikan garis dari kiri (0 = tidak nyeri) sampai kanan (10 = paling nyeri).</div>
      <div class="step-item">Tunjuk atau tandai satu titik yang sesuai dengan rasa nyeri Anda <strong>saat ini</strong>.</div>
      <div class="step-item">Perawat akan mengukur posisi tanda Anda untuk menentukan skor nyeri.</div>
    </div>

    <!-- ===== KATEGORI NYERI ===== -->
    <div class="section-title">🎯 Arti Skor Nyeri Anda</div>

    <!-- Tidak Nyeri -->
    <div class="pain-card card-none">
      <div class="emoji">😊</div>
      <div class="content">
        <h3>Tidak Ada Nyeri</h3>
        <div class="score">Skor VAS: 0</div>
        <p>Anda tidak merasakan sakit sama sekali.</p>
        <div class="examples">
          ✅ Kondisi normal tanpa keluhan<br/>
          ✅ Merasa nyaman sepenuhnya
        </div>
      </div>
    </div>

    <!-- Nyeri Ringan -->
    <div class="pain-card card-mild">
      <div class="emoji">🙂</div>
      <div class="content">
        <h3>Nyeri Ringan</h3>
        <div class="score">Skor VAS: 1 – 3</div>
        <p>Nyeri terasa tapi <strong>masih bisa diabaikan</strong>. Aktivitas sehari-hari tidak terganggu.</p>
        <div class="examples">
          📌 Luka gores kecil / lecet<br/>
          📌 Sakit kepala ringan<br/>
          📌 Pegal otot setelah olahraga<br/>
          📌 Nyeri bekas suntikan
        </div>
      </div>
    </div>

    <!-- Nyeri Sedang -->
    <div class="pain-card card-moderate">
      <div class="emoji">😣</div>
      <div class="content">
        <h3>Nyeri Sedang</h3>
        <div class="score">Skor VAS: 4 – 6</div>
        <p>Nyeri <strong>cukup mengganggu</strong>, sulit diabaikan. Mulai mempengaruhi konsentrasi & aktivitas.</p>
        <div class="examples">
          📌 Sakit gigi berlubang<br/>
          📌 Nyeri haid / kram perut<br/>
          📌 Keseleo pergelangan kaki<br/>
          📌 Migrain / sakit kepala berat
        </div>
      </div>
    </div>

    <!-- Nyeri Berat -->
    <div class="pain-card card-severe">
      <div class="emoji">😫</div>
      <div class="content">
        <h3>Nyeri Berat</h3>
        <div class="score">Skor VAS: 7 – 9</div>
        <p>Nyeri <strong>sangat mengganggu</strong>, sangat sulit beraktivitas. Membutuhkan obat pereda nyeri.</p>
        <div class="examples">
          📌 Nyeri pasca operasi<br/>
          📌 Kolik ginjal / batu ginjal<br/>
          📌 Patah tulang<br/>
          📌 Nyeri persalinan
        </div>
      </div>
    </div>

    <!-- Nyeri Sangat Berat -->
    <div class="pain-card card-worst">
      <div class="emoji">😭</div>
      <div class="content">
        <h3>Nyeri Sangat Berat</h3>
        <div class="score">Skor VAS: 10</div>
        <p>Nyeri <strong>paling hebat yang bisa dibayangkan</strong>. Tidak tertahankan & butuh penanganan darurat.</p>
        <div class="examples">
          📌 Luka bakar luas / berat<br/>
          📌 Trauma / kecelakaan berat<br/>
          📌 Nyeri kanker tanpa obat<br/>
          📌 Nyeri tak terkontrol
        </div>
      </div>
    </div>

    <!-- ===== INTERACTIVE SLIDER ===== -->
    <div class="section-title">🎮 Coba Sendiri!</div>
    <div class="interactive-section">
      <h3>Geser untuk menentukan skor nyeri Anda</h3>
      <div class="slider-container">
        <input type="range" id="painSlider" min="0" max="10" value="0" step="1" />
        <div class="slider-labels">
          <span>0</span><span>5</span><span>10</span>
        </div>
      </div>
      <div class="result-display" id="resultDisplay">
        😊 Skor: <strong>0</strong> — Tidak Ada Nyeri
      </div>
    </div>

    <!-- ===== TIPS ===== -->
    <div class="section-title">💡 Tips Penting</div>
    <div class="tips-box">
      <h3>🔑 Yang Perlu Anda Ketahui</h3>
      <ul>
        <li><strong>Nyeri bersifat subjektif</strong> — Hanya Anda yang bisa menilai rasa sakit Anda sendiri. Tidak ada jawaban salah!</li>
        <li><strong>Jujurlah</strong> — Penilaian yang akurat membantu dokter/perawat memberikan penanganan terbaik.</li>
        <li><strong>Laporkan perubahan</strong> — Jika nyeri bertambah atau tidak membaik setelah diberi obat, segera informasikan.</li>
        <li><strong>Nyeri bisa ditangani</strong> — Selain obat, teknik relaksasi, napas dalam, kompres, dan aromaterapi juga bisa membantu.</li>
      </ul>
    </div>

    <!-- ===== FAQ ACCORDION ===== -->
    <div class="section-title">❓ Pertanyaan Umum</div>

    <details>
      <summary>Apakah skor VAS bisa berubah-ubah?</summary>
      <div class="detail-content">
        Ya! Nyeri bisa berubah seiring waktu, aktivitas, atau setelah mendapat pengobatan.
        Perawat akan meminta Anda menilai ulang secara berkala untuk memantau perkembangan.
      </div>
    </details>

    <details>
      <summary>Bagaimana jika saya bingung menentukan skor?</summary>
      <div class="detail-content">
        Tidak perlu khawatir. Cukup pilih angka yang paling mendekati rasa nyeri Anda.
        Anda juga bisa minta perawat membantu menjelaskan.
      </div>
    </details>

    <details>
      <summary>Kapan harus segera melapor ke perawat?</summary>
      <div class="detail-content">
        Segera laporkan jika:<br/>
        • Nyeri tiba-tiba meningkat drastis<br/>
        • Skor VAS ≥ 4 dan tidak membaik<br/>
        • Nyeri disertai gejala baru (mual, pusing, sesak, dll.)<br/>
        • Obat nyeri yang diberikan tidak terasa efeknya
      </div>
    </details>

    <details>
      <summary>Apakah VAS bisa digunakan untuk anak-anak?</summary>
      <div class="detail-content">
        VAS lebih cocok untuk pasien usia <strong>≥ 8 tahun</strong> yang bisa memahami konsep garis.
        Untuk anak-anak yang lebih kecil, biasanya digunakan skala wajah (Wong-Baker FACES).
      </div>
    </details>

    <!-- ===== EMERGENCY NOTE ===== -->
    <div class="section-title">🚨 Penting!</div>
    <div class="info-box" style="border-left-color: #f44336; background: #fff5f5;">
      Jika Anda merasakan nyeri <strong>skor 7 ke atas</strong> atau nyeri yang tiba-tiba sangat hebat,
      <strong>segera hubungi perawat atau tekan bel darurat</strong>. Jangan menahan nyeri sendirian — 
      kami siap membantu Anda! 🤝
    </div>

    <!-- ===== FOOTER ===== -->
    <div class="footer">
      📋 Materi Edukasi Pasien — Skala Nyeri VAS<br/>
      © 2026 | Tim Keperawatan<br/>
      <em>Kesehatan Anda, Prioritas Kami</em> 💙
    </div>

  </div>

  <!-- ===== JAVASCRIPT — INTERACTIVE SLIDER ===== -->
  <script>
    const slider = document.getElementById('painSlider');
    const display = document.getElementById('resultDisplay');

    const painData = [
      { emoji: '😊', label: 'Tidak Ada Nyeri',   color: '#e8f5e9', text: '#2e7d32' },
      { emoji: '😊', label: 'Nyeri Sangat Ringan',color: '#f1f8e9', text: '#33691e' },
      { emoji: '🙂', label: 'Nyeri Ringan',       color: '#f1f8e9', text: '#558b2f' },
      { emoji: '🙂', label: 'Nyeri Ringan',       color: '#fffde7', text: '#827717' },
      { emoji: '😐', label: 'Nyeri Sedang',       color: '#fff8e1', text: '#f57f17' },
      { emoji: '😣', label: 'Nyeri Sedang',       color: '#fff3e0', text: '#e65100' },
      { emoji: '😣', label: 'Nyeri Sedang-Berat', color: '#fbe9e7', text: '#bf360c' },
      { emoji: '😫', label: 'Nyeri Berat',        color: '#ffebee', text: '#c62828' },
      { emoji: '😫', label: 'Nyeri Berat',        color: '#ffebee', text: '#b71c1c' },
      { emoji: '😫', label: 'Nyeri Sangat Berat', color: '#fce4ec', text: '#880e4f' },
      { emoji: '😭', label: 'Nyeri Tak Tertahankan', color: '#f8d7da', text: '#b71c1c' }
    ];

    slider.addEventListener('input', function () {
      const val = parseInt(this.value);
      const data = painData[val];
      display.style.background = data.color;
      display.style.color = data.text;
      display.innerHTML = `${data.emoji} Skor: <strong>${val}</strong> — ${data.label}`;
    });
  </script>

</body>
</html>
