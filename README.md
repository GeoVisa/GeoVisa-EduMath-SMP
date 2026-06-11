<!doctype html>
<html lang="id">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>EduMath SMP: GeoVisa 🎮🔥</title>
    <script src="https://www.geogebra.org/apps/deployggb.js"></script>

    <style>
      @import url("https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;800;900&display=swap");
      
      .logo-header{
          display:flex;
          justify-content:center;
          align-items:center;
          gap:80px;
          margin-bottom:25px;
        }

        .logo-header img{
          width:120px;
          height:120px;
          object-fit:contain;
          filter:drop-shadow(0 0 10px rgba(255,255,255,.3));
        }

        .logo-center{
          text-align:center;
        }

      :root {
        --primary: #00d2ff;
        --primary-hover: #3a7bd5;
        --secondary: #22c55e;
        --wrong: #ef4444;
        --gold: #facc15;
        --bg-dark: #0f172a;
        --bg-light: #1e293b;
        --glass: rgba(255, 255, 255, 0.08);
        --glass-border: rgba(255, 255, 255, 0.2);
      }

      body {
        font-family: "Poppins", sans-serif;
        margin: 0;
        background: radial-gradient(
          circle at 50% 0%,
          var(--bg-light),
          var(--bg-dark)
        );
        color: white;
        text-align: center;
        min-height: 100vh;
        overflow-x: hidden;
      }

      /* TYPOGRAPHY & GLOWS */
      h1 {
        font-size: 4em;
        margin-bottom: 0;
        text-transform: uppercase;
        letter-spacing: 2px;
        text-shadow: 0 0 20px rgba(0, 210, 255, 0.5);
      }
      .text-primary {
        color: var(--primary);
      }
      .rank-text {
        color: var(--gold);
        font-weight: 900;
        text-shadow: 0 0 15px rgba(250, 204, 21, 0.6);
      }

      /* CONTAINERS */
      .container {
        max-width: 900px;
        margin: 30px auto;
        padding: 30px;
        background: var(--glass);
        border-radius: 24px;
        backdrop-filter: blur(20px);
        -webkit-backdrop-filter: blur(20px);
        border: 1px solid var(--glass-border);
        box-shadow:
          0 25px 50px rgba(0, 0, 0, 0.5),
          inset 0 0 20px rgba(255, 255, 255, 0.02);
      }

      .header-info {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 15px 25px;
        background: rgba(0, 0, 0, 0.4);
        border-radius: 18px;
        margin-bottom: 25px;
        border: 1px solid var(--primary);
        box-shadow: 0 0 15px rgba(0, 210, 255, 0.2);
        font-size: 1.1em;
        font-weight: 600;
      }

      /* BUTTONS */
      .btn {
        padding: 16px 40px;
        border: none;
        border-radius: 14px;
        font-family: "Poppins", sans-serif;
        font-weight: 800;
        font-size: 1.1em;
        cursor: pointer;
        background: linear-gradient(
          135deg,
          var(--primary),
          var(--primary-hover)
        );
        color: white;
        transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        text-transform: uppercase;
        letter-spacing: 1.5px;
        box-shadow: 0 10px 20px rgba(0, 210, 255, 0.3);
      }
      .btn:hover {
        transform: translateY(-3px) scale(1.05);
        box-shadow: 0 15px 30px rgba(0, 210, 255, 0.5);
      }
      .btn:active {
        transform: translateY(2px) scale(0.98);
      }

      .btn-secondary {
        background: rgba(0, 0, 0, 0.5);
        border: 2px solid var(--gold);
        box-shadow: 0 10px 20px rgba(250, 204, 21, 0.15);
        color: var(--gold);
        margin-top: 20px;
      }
      .btn-secondary:hover {
        background: rgba(250, 204, 21, 0.1);
        box-shadow: 0 15px 30px rgba(250, 204, 21, 0.3);
      }

      /* GEOGEBRA WRAPPERS */
      .ggb-box {
        width: 100%;
        background: #f7efe5;
        border-radius: 20px;
        margin: 20px 0;
        overflow: hidden;
        border: 4px solid var(--glass-border);
        box-shadow: 0 15px 30px rgba(0, 0, 0, 0.3);
        transition: border-color 0.3s ease;
      }
      .ggb-box:hover {
        border-color: var(--primary);
      }
      .mini-ggb {
        height: 260px !important;
        margin: 10px 0;
      }

      /* INPUT FIELD */
      input {
        padding: 18px;
        width: 160px;
        border-radius: 14px;
        border: 2px solid var(--glass-border);
        background: rgba(0, 0, 0, 0.6);
        color: var(--primary);
        font-family: "Poppins", sans-serif;
        font-size: 24px;
        font-weight: bold;
        text-align: center;
        outline: none;
        transition: all 0.3s ease;
        box-shadow: inset 0 5px 10px rgba(0, 0, 0, 0.5);
      }
      input:focus {
        border-color: var(--primary);
        box-shadow:
          0 0 15px rgba(0, 210, 255, 0.4),
          inset 0 5px 10px rgba(0, 0, 0, 0.5);
        transform: translateY(-2px);
      }

      /* MODAL (LAB PEMBUKTIAN) */
      .modal {
        display: none;
        position: fixed;
        z-index: 2000;
        left: 0;
        top: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(15, 23, 42, 0.95);
        backdrop-filter: blur(10px);
        overflow-y: auto;
        animation: fadeIn 0.4s ease;
      }

      .modal-content {
        background: var(--bg-light);
        margin: 3% auto;
        padding: 40px;
        border: 1px solid var(--primary);
        width: 90%;
        max-width: 1100px;
        border-radius: 24px;
        text-align: left;
        box-shadow:
          0 20px 60px rgba(0, 0, 0, 0.8),
          0 0 30px rgba(0, 210, 255, 0.2);
      }

      .bukti-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        gap: 25px;
        margin-top: 30px;
      }

      .bukti-card {
        background: rgba(0, 0, 0, 0.4);
        padding: 20px;
        border-radius: 20px;
        border-top: 5px solid var(--primary);
        transition:
          transform 0.3s ease,
          box-shadow 0.3s ease;
      }
      .bukti-card:hover {
        transform: translateY(-10px);
        box-shadow: 0 15px 30px rgba(0, 0, 0, 0.5);
      }
      .bukti-card h3 {
        margin-top: 0;
        color: white;
        display: flex;
        align-items: center;
        gap: 10px;
      }
      .bukti-card p {
        font-size: 14px;
        line-height: 1.6;
        color: #cbd5e1;
      }
      .rumus-badge {
        display: inline-block;
        background: rgba(250, 204, 21, 0.15);
        color: var(--gold);
        padding: 8px 15px;
        border-radius: 8px;
        font-weight: bold;
        border: 1px solid var(--gold);
        font-size: 1.1em;
        margin-top: 10px;
      }

      .close-modal {
        float: right;
        font-size: 36px;
        font-weight: bold;
        cursor: pointer;
        color: var(--wrong);
        transition: 0.2s;
      }
      .close-modal:hover {
        transform: scale(1.2);
        text-shadow: 0 0 10px var(--wrong);
      }

      /* ANIMATIONS & EFFECTS */
      .correct-anim {
        animation: flashGreen 0.6s ease;
      }
      .wrong-anim {
        animation: shake 0.5s ease;
      }
      @keyframes flashGreen {
        0%,
        100% {
          background-color: var(--bg-dark);
        }
        50% {
          background-color: #064e3b;
        }
      }
      @keyframes shake {
        0%,
        100% {
          transform: translateX(0);
        }
        20%,
        60% {
          transform: translateX(-15px);
        }
        40%,
        80% {
          transform: translateX(15px);
        }
      }
      @keyframes fadeIn {
        from {
          opacity: 0;
        }
        to {
          opacity: 1;
        }
      }

      #music-toggle {
        position: fixed;
        bottom: 25px;
        left: 25px;
        cursor: pointer;
        background: rgba(0, 0, 0, 0.5);
        padding: 15px;
        border-radius: 50%;
        font-size: 24px;
        z-index: 3000;
        border: 1px solid var(--glass-border);
        transition: 0.3s;
      }
      #music-toggle:hover {
        background: var(--primary);
        border-color: white;
        transform: scale(1.1) rotate(10deg);
      }
    </style>
  </head>

  <body>
    <div id="music-toggle" onclick="toggleBGM()">🎵</div>

    <!-- AUDIO ASSETS -->
    <audio
      id="snd-correct"
      src="https://assets.mixkit.co/active_storage/sfx/2000/2000-preview.mp3"
    ></audio>
    <audio
      id="snd-wrong"
      src="https://assets.mixkit.co/active_storage/sfx/2013/2013-preview.mp3"
    ></audio>
    <audio
      id="snd-start"
      src="https://assets.mixkit.co/active_storage/sfx/2004/2004-preview.mp3"
    ></audio>
    <audio
      id="snd-rankup"
      src="https://assets.mixkit.co/active_storage/sfx/1435/1435-preview.mp3"
    ></audio>
    <audio
      id="snd-victory"
      src="https://assets.mixkit.co/active_storage/sfx/1434/1434-preview.mp3"
    ></audio>
    <audio
      id="bgm"
      loop
      src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-17.mp3"
    ></audio>

    <!-- MENU -->
    <div id="menu" style="margin-top: 6vh">
      <div class="logo-header">

  <img src="https://d13i5xhouzkrd.cloudfront.net/assets/publisher-logos/Unmul_logo_low.png" alt="UNMUL">

  <div class="logo-center">

    <h1>
      📐 MATH <span class="text-primary">CHAMPION</span>
    </h1>

    <p style="font-size: 2em; color: #94a3b8; margin-bottom: 40px">
      Geometri Ruang dan Hubungan Antar Sudut SMP
    </p>

  </div>

  <img src="https://1.bp.blogspot.com/-CTvH4ISeUOo/Vcpbbe8-J2I/AAAAAAAAABQ/vy9HQQCHO1g/s320/Untitled-1.png" alt="HIMAPTIKA">

</div>
      <button class="btn btn-secondary" onclick="openModal()">
        🔬 LAB VISUALISASI RUMUS (3D)
      </button>
      <br /><br />
      <button
        class="btn"
        style="font-size: 22px; padding: 20px 50px"
        onclick="startGame()"
      >
        MASUK ARENA 🚀
      </button>
      <br /><br />
      <button class="btn" onclick="openSudut()">📏 HUBUNGAN ANTAR SUDUT</button>
      <br /><br />
      <button class="btn" onclick="openQuizSudut()">🧠 QUIZ SUDUT</button>
      <br /><br />
      <button class="btn" onclick="openGabunganQuiz()">
        🧊 QUIZ BANGUN GABUNGAN
      </button>
      <div
    style="
    margin-top:40px;
    text-align:right;
    font-size:13px;
    color:#94a3b8;
    "
    >
    Copyright © 2026 Al, Vel, Fin, Mal.
    All rights reserved.
    </div>
    </div>

    <!-- MODAL LAB PEMBUKTIAN -->
    <div id="modalBukti" class="modal">
      <div class="modal-content">
        <span class="close-modal" onclick="closeModal()">&times;</span>
        <h2
          style="
            color: var(--primary);
            text-align: center;
            font-size: 2.5em;
            margin-top: 0;
            text-transform: uppercase;
          "
        >
          🔬 Lab Visualisasi Pembuktian
        </h2>
        <p style="text-align: center; color: #94a3b8; font-size: 1.1em">
          Geser dan putar bangun 3D di bawah ini untuk melihat darimana asal
          rumus didapatkan!
        </p>

        <div class="bukti-grid">
          <!-- BALOK -->
          <div class="bukti-card">
            <h3>🧊 1. Konsep Balok</h3>
            <div id="ggb-bukti-balok" class="mini-ggb ggb-box"></div>
            <p>
              <b>Visualisasi:</b> Volume adalah susunan kubus satuan. Panjang
              (p), Lebar (l), dan Tinggi (t) mewakili dimensi ruang yang diisi
              penuh.
            </p>
            <div class="rumus-badge">V = p × l × t</div>
          </div>

          <!-- PRISMA -->
          <div class="bukti-card" style="border-top-color: var(--secondary)">
            <h3>⛺ 2. Konsep Prisma Segitiga</h3>
            <div id="ggb-bukti-prisma" class="mini-ggb ggb-box"></div>
            <p>
              <b>Visualisasi:</b> Prisma segitiga terbentuk dari alas segitiga
              yang "ditarik" lurus ke atas setinggi <i>t</i>. Isinya adalah Luas
              Alas yang ditumpuk-tumpuk.
            </p>
            <div
              class="rumus-badge"
              style="
                color: var(--secondary);
                border-color: var(--secondary);
                background: rgba(34, 197, 94, 0.15);
              "
            >
              V = Luas Alas × t
            </div>
          </div>

          <!-- LIMAS -->
          <div class="bukti-card" style="border-top-color: var(--wrong)">
            <h3>🔺 3. Bukti Limas</h3>
            <div id="ggb-bukti-limas" class="mini-ggb ggb-box"></div>
            <p>
              <b>Visualisasi:</b> Lihat bangun di atas! Limas (kuning) berada
              tepat di dalam Prisma (biru transparan) dengan alas & tinggi yang
              sama. Volume limas persis mengisi <b>sepertiga</b> dari prisma
              tersebut.
            </p>
            <div
              class="rumus-badge"
              style="
                color: var(--wrong);
                border-color: var(--wrong);
                background: rgba(239, 68, 68, 0.15);
              "
            >
              V = 1/3 × L_alas × t
            </div>
          </div>
        </div>

        <div style="text-align: center; margin-top: 40px">
          <button class="btn" style="padding: 15px 60px" onclick="closeModal()">
            SAYA PAHAM, GAS MAIN!
          </button>
        </div>
      </div>
    </div>

    <!-- HUBUNGAN ANTAR SUDUT -->
    <div id="sudutPage" style="display: none">
      <button class="btn" style="margin-top: 20px" onclick="backMenu()">
        ⬅ KEMBALI KE MENU
      </button>

      <div class="container">
        <h2
          style="
            font-size: 2.5em;
            margin-bottom: 10px;
            color: #00d2ff;
            text-align: center;
          "
        >
          📏 Hubungan Antar Sudut
        </h2>

        <p
          style="
            text-align: center;
            color: #cbd5e1;
            margin-bottom: 25px;
            font-size: 18px;
          "
        >
          Eksplorasi hubungan antar sudut interaktif GeoGebra.
        </p>

        <iframe
          src="https://www.geogebra.org/calculator/ye9hndaw?embed"
          width="100%"
          height="700"
          style="
            border: none;
            border-radius: 20px;
            background: white;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
          "
        >
        </iframe>
      </div>
    </div>
    <!-- QUIZ SUDUT -->
    <div id="quizSudutPage" style="display: none">
      <button
        class="btn btn-secondary"
        style="margin-top: 20px"
        onclick="backMenu()"
      >
        ⬅ KEMBALI MENU
      </button>

      <div class="container">
        <div class="header-info">
          <div>
            🏆 Skor:
            <span id="sudut-skor" class="text-primary">0</span>
          </div>

          <div>
            Soal:
            <span id="sudut-no" style="color: var(--secondary)"> 1 </span>/5
          </div>
        </div>

        <h2 id="sudut-pertanyaan" style="font-size: 1.8em">Loading Quiz...</h2>

        <div id="ggb-sudut" class="ggb-box" style="height: 450px"></div>

        <div
          style="
            margin: 30px 0;
            display: flex;
            justify-content: center;
            gap: 15px;
            align-items: center;
          "
        >
          <input
            type="number"
            id="jawaban-sudut"
            placeholder="Sudut?"
            onkeypress="handleSudutEnter(event)"
          />

          <button class="btn" onclick="cekSudut()">JAWAB 🎯</button>
        </div>

        <div
          id="sudut-feedback"
          style="font-weight: 900; font-size: 1.5em; min-height: 40px"
        ></div>

        <div
          id="sudut-bahas"
          style="
            display: none;
            background: rgba(0, 0, 0, 0.6);
            padding: 20px;
            border-radius: 15px;
            margin-top: 15px;
            border-left: 5px solid var(--wrong);
            text-align: left;
          "
        ></div>
      </div>
    </div>

    <!-- QUIZ BANGUN GABUNGAN -->
    <div id="quizGabunganPage" style="display: none">
      <button
        class="btn btn-secondary"
        style="margin-top: 20px"
        onclick="backMenu()"
      >
        ⬅ KEMBALI MENU
      </button>

      <div class="container">
        <div class="header-info">
          <div>
            🏆 Skor:
            <span id="gabungan-skor" class="text-primary">0</span>
          </div>

          <div>
            Soal:
            <span id="gabungan-no" style="color: var(--secondary)">1</span>/5
          </div>
        </div>

        <h2 id="gabungan-pertanyaan" style="font-size: 1.8em">
          Loading Quiz...
        </h2>

        <div id="ggb-gabungan" class="ggb-box" style="height: 450px"></div>

        <div
          style="
            margin: 30px 0;
            display: flex;
            justify-content: center;
            gap: 15px;
            align-items: center;
          "
        >
          <input
            type="number"
            id="jawaban-gabungan"
            placeholder="Volume?"
            onkeypress="handleGabunganEnter(event)"
          />

          <button class="btn" onclick="cekGabungan()">JAWAB 🎯</button>
        </div>

        <div
          id="gabungan-feedback"
          style="font-weight: 900; font-size: 1.5em; min-height: 40px"
        ></div>

        <div
          id="gabungan-bahas"
          style="
            display: none;
            background: rgba(0, 0, 0, 0.6);
            padding: 20px;
            border-radius: 15px;
            margin-top: 15px;
            border-left: 5px solid var(--wrong);
            text-align: left;
          "
        ></div>
      </div>
    </div>

    <!-- GAME AREA -->
    <div id="game" class="container" style="display: none">
      <button
        class="btn btn-secondary"
        style="margin-bottom: 20px"
        onclick="backMenu()"
      >
        ⬅ KEMBALI MENU
      </button>
      <div class="header-info">
        <div>🏆 Skor: <span id="skor" class="text-primary">0</span></div>
        <div><span id="rank" class="rank-text">PEMULA</span></div>
        <div>
          Quest: <span id="no" style="color: var(--secondary)">1</span> / 10
        </div>
      </div>

      <h2 id="pertanyaan" style="font-size: 1.8em; margin: 10px 0">
        Loading Quest...
      </h2>

      <div id="ggb-main" class="ggb-box" style="height: 450px"></div>

      <div
        style="
          margin: 30px 0 10px 0;
          display: flex;
          justify-content: center;
          gap: 15px;
          align-items: center;
        "
      >
        <input
          type="number"
          id="jawaban-user"
          placeholder="Hasil Volume?"
          onkeypress="handleEnter(event)"
        />
        <button class="btn" onclick="cekJawaban()">SAYA YAKIN! 🎯</button>
      </div>

      <div
        id="feedback"
        style="
          font-weight: 900;
          font-size: 1.5em;
          min-height: 40px;
          margin-top: 10px;
        "
      ></div>

      <div
        id="bahas"
        style="
          display: none;
          background: rgba(0, 0, 0, 0.6);
          padding: 20px;
          border-radius: 15px;
          margin-top: 15px;
          border-left: 5px solid var(--wrong);
          text-align: left;
          font-size: 1.1em;
        "
      ></div>
    </div>

    <script>
      let score = 0,
        currentNo = 1,
        correctAnswer = 0,
        currentData = {},
        lastRank = "PEMULA";
      let ggbMainApi;
      let ggbSudutApi;

      let sudutJenis = 1;
      let sudutScore = 0;
      let sudutNo = 1;
      let sudutData = {};

      let ggbGabunganApi;
      let gabunganScore = 0;
      let gabunganNo = 1;
      let gabunganData = {};

      /* FUNGSI INJEKSI GEOGEBRA */
      function injectGGB(id, type) {
        const p = {
          appName: "3d",
          width: id === "ggb-main" ? 850 : 350,
          height: id === "ggb-main" ? 450 : 260,
          showToolBar: true,
          showMenuBar: false,
          showAlgebraInput: false,
          enableRightClick: false,
          appletOnLoad: function (api) {
            setupView(api);

            if (type === "main") {
              ggbMainApi = api;
              nextQuestion();
            }

            if (type === "sudut") {
              ggbSudutApi = api;
              nextSudutQuestion();
            }

            // VISUALISASI BUKTI BALOK
            if (type === "balok") {
              api.evalCommand("A=(0,0,0)");
              api.evalCommand("B=(4,0,0)");
              api.evalCommand("C=(4,3,0)");
              api.evalCommand("D=(0,3,0)");
              api.evalCommand("base=Polygon(A,B,C,D)");
              api.evalCommand("b=Prism(base, 3)");
              api.evalCommand("SetColor(b, 0, 210, 255)");
            }

            // VISUALISASI BUKTI PRISMA
            if (type === "prisma") {
              api.evalCommand("A=(0,0,0)");
              api.evalCommand("B=(4,0,0)");
              api.evalCommand("C=(0,4,0)");
              api.evalCommand("base=Polygon(A,B,C)");
              api.evalCommand("p=Prism(base, 5)");

              // warna prisma segitiga
              api.evalCommand("SetColor(p, 170, 0, 255)");
              api.setFilling("p", 0.7);

              // garis lebih tebal
              api.setLineThickness("p", 5);

              // tampilkan objek
              api.setVisible("p", true);
            }

            // VISUALISASI BUKTI LIMAS (Limas dalam Prisma)
            if (type === "limas") {
              api.evalCommand("A=(0,0,0)");
              api.evalCommand("B=(4,0,0)");
              api.evalCommand("C=(4,4,0)");
              api.evalCommand("D=(0,4,0)");

              api.evalCommand("base=Polygon(A,B,C,D)");

              // =========================
              // PRISMA LUAR (BIRU)
              // =========================
              api.evalCommand("pr=Prism(base,4)");

              api.evalCommand("SetColor(pr,0,210,255)");

              api.setFilling("pr", 0.15);

              api.setLineThickness("pr", 4);

              // =========================
              // LIMAS DALAM (KUNING)
              // =========================
              api.evalCommand("T=(2,2,4)");

              api.evalCommand("py=Pyramid(base,T)");

              // warna kuning emas
              api.evalCommand("SetColor(py,255,215,0)");

              // isi penuh
              api.setFilling("py", 1);

              // garis limas
              api.setLineThickness("py", 5);

              // tampilkan objek
              api.setVisible("py", true);

              // supaya tidak transparan
              api.setFixed("py", true, false);

              // titik puncak merah biar jelas
              api.evalCommand("SetColor(T,255,0,0)");
              api.setPointSize("T", 7);
            }
          },
        };
        new GGBApplet(p, true).inject(id);
      }

      function injectSudut() {
        const p = {
          appName: "classic",
          width: 850,
          height: 450,

          showToolBar: false,
          showMenuBar: false,
          showAlgebraInput: false,
          enableRightClick: false,

          appletOnLoad: function (api) {
            ggbSudutApi = api;

            api.evalCommand("ShowAxes(false)");
            api.evalCommand("ShowGrid(false)");

            nextSudutQuestion();
          },
        };

        new GGBApplet(p, true).inject("ggb-sudut");
      }

      function injectGabungan() {
        const p = {
          appName: "3d",
          width: 850,
          height: 450,

          showToolBar: false,
          showMenuBar: false,
          showAlgebraInput: false,
          enableRightClick: true,
          enableShiftDragZoom: true,
          enableLabelDrags: false,
          capturingThreshold: 3,
          enableShiftDragZoom: true,

          appletOnLoad: function (api) {
            ggbGabunganApi = api;

            setupView(api);

            api.setPerspective("T");

            nextGabunganQuestion();
          },
        };

        new GGBApplet(p, true).inject("ggb-gabungan");
      }

      function cekGabungan() {
        document.getElementById("jawaban-gabungan").disabled = true;

        let user = parseInt(document.getElementById("jawaban-gabungan").value);

        if (isNaN(user)) {
          document.getElementById("jawaban-gabungan").disabled = false;
          return;
        }

        if (user === gabunganData.answer) {
          gabunganScore += 10;

          document.getElementById("snd-correct").play();
          document.body.classList.add("correct-anim");

          setTimeout(()=>{
          document.body.classList.remove("correct-anim");
          },600);

          document.getElementById("gabungan-feedback").innerHTML =
            "<span style='color:lime'>BENAR 🔥</span>";
        } else {
          document.getElementById("snd-wrong").play();
          document.body.classList.add("wrong-anim");

           setTimeout(() => {
           document.body.classList.remove("wrong-anim");
           },500);

          document.getElementById("gabungan-feedback").innerHTML =
            "<span style='color:red'>SALAH ❌</span>";

          document.getElementById("gabungan-bahas").style.display = "block";

          document.getElementById("gabungan-bahas").innerHTML =
          `
          <b>📋 LOG SISTEM (PEMBAHASAN):</b>
          <hr style="border:1px solid #ef4444;">
          ${gabunganData.bahas}
          `;
        }

        document.getElementById("gabungan-skor").innerText = gabunganScore;

        setTimeout(() => {
          document.getElementById("jawaban-gabungan").disabled = false;

          gabunganNo++;

          nextGabunganQuestion();
        }, 5000);
      }

      function setupView(api) {
        api.evalCommand("ShowAxes(false)");
        api.evalCommand("ShowGrid(false)");

        // background aqua
        api.setGraphicsOptions(1, {
          bgColor: "#bffcff",
        });

        api.enableShiftDragZoom(false);
      }

      /* LOGIKA MODAL */
      let modalLoaded = false;
      function openModal() {
        document.getElementById("snd-start").play();
        document.getElementById("modalBukti").style.display = "block";
        document.body.style.overflow = "hidden"; // Mencegah background scroll

        // Lazy load GeoGebra di modal agar tidak berat di awal
        if (!modalLoaded) {
          injectGGB("ggb-bukti-balok", "balok");
          injectGGB("ggb-bukti-prisma", "prisma");
          injectGGB("ggb-bukti-limas", "limas");
          modalLoaded = true;
        }
      }

      function closeModal() {
        document.getElementById("modalBukti").style.display = "none";
        document.body.style.overflow = "auto";
      }

      /* LOGIKA GAME */
      function toggleBGM() {
        const bgm = document.getElementById("bgm");
        if (bgm.paused) {
          bgm.play();
          document.getElementById("music-toggle").innerText = "🎵";
        } else {
          bgm.pause();
          document.getElementById("music-toggle").innerText = "🔇";
        }
      }

      function startGame() {
        document.getElementById("snd-start").play();
        document.getElementById("bgm").volume = 0.3;
        document.getElementById("bgm").play();
        document.getElementById("menu").style.display = "none";
        document.getElementById("game").style.display = "block";
        injectGGB("ggb-main", "main");
      }

      function rand(min, max) {
        return Math.floor(Math.random() * (max - min + 1)) + min;
      }

      // Enter otomatis tekan HIT
      function handleEnter(e) {
        if (e.key === "Enter") cekJawaban();
      }

      function nextQuestion() {
        if (currentNo > 10) {
          finish();
          return;
        }

        ggbMainApi.newConstruction();
        setupView(ggbMainApi);

        document.getElementById("jawaban-user").value = "";
        document.getElementById("jawaban-user").focus();
        document.getElementById("bahas").style.display = "none";
        document.getElementById("feedback").innerText = "";
        document.getElementById("no").innerText = currentNo;

        let tipe = rand(1, 3);

        if (tipe === 1) {
          // BALOK
          let p = rand(4, 8),
            l = rand(3, 5),
            t = rand(3, 6);
          correctAnswer = p * l * t;
          currentData = {
            text: `Sebuah <b>Balok</b> memiliki:<br> Panjang = ${p}, Lebar = ${l}, Tinggi = ${t}`,
            rumus: `<b>Volume Balok = p × l × t</b><br>V = ${p} × ${l} × ${t} = <span style="color:var(--primary)">${correctAnswer}</span>`,
          };

          ggbMainApi.evalCommand(`
          balok = Prism(Polygon((0,0,0),(${p},0,0),(${p},${l},0),(0,${l},0)),${t})`);

          let r = rand(50, 255);
          let g = rand(50, 255);
          let b = rand(50, 255);

          ggbMainApi.setColor("balok", r, g, b);
          ggbMainApi.setFilling("balok", 1);
          ggbMainApi.setLineThickness("balok", 5);
          ggbMainApi.setVisible("balok", true);
        } else if (tipe === 2) {
          // PRISMA
          let alas = rand(12, 24),
            t = rand(5, 10);
          correctAnswer = alas * t;
          currentData = {
            text: `Sebuah <b>Prisma Segitiga</b> memiliki:<br> Luas Alas = ${alas}, Tinggi = ${t}`,
            rumus: `<b>Volume Prisma = Luas Alas × t</b><br>V = ${alas} × ${t} = <span style="color:var(--secondary)">${correctAnswer}</span>`,
          };

          ggbMainApi.evalCommand(`alas = Polygon((0,0,0),(4,0,0),(0,3,0))`);
          ggbMainApi.evalCommand(`prisma = Prism(alas, ${t})`);

          let r = rand(50, 255);
          let g = rand(50, 255);
          let b = rand(50, 255);

          ggbMainApi.setColor("prisma", r, g, b);
          ggbMainApi.setFilling("prisma", 1);
          ggbMainApi.setLineThickness("prisma", 5);
          ggbMainApi.setVisible("prisma", true);
        } else {
          // LIMAS
          let p = rand(4, 8);
          let l = rand(4, 8);
          let t = rand(4, 9);

          let la = p * l;

          correctAnswer = (la * t) / 3;

          currentData = {
            text: `
            Sebuah <b>Limas Segiempat</b> memiliki:<br>
            Panjang Alas = ${p}<br>
            Lebar Alas = ${l}<br>
            Tinggi = ${t}
            `,

            rumus: `
            <b>Volume Limas = 1/3 × Luas Alas × t</b><br><br>

            Luas Alas = p × l<br>
            = ${p} × ${l}<br>
            = ${la}<br><br>

            V = 1/3 × ${la} × ${t}<br>
            = ${correctAnswer}
            `,
          };

          ggbMainApi.evalCommand(
          `alasLimas=Polygon((0,0,0),(${p},0,0),(${p},${l},0),(0,${l},0))`
          );

          ggbMainApi.evalCommand(
           `limas=Pyramid(alasLimas,(${p/2},${l/2},${t}))`
          );

          let r = rand(50, 255);
          let g = rand(50, 255);
          let b = rand(50, 255);

          ggbMainApi.setColor("limas", r, g, b);
          ggbMainApi.setFilling("limas", 1);
          ggbMainApi.setLineThickness("limas", 5);
          ggbMainApi.setVisible("limas", true);
        }

        document.getElementById("pertanyaan").innerHTML = currentData.text;
      }

      function cekJawaban() {
        const userInp = parseInt(document.getElementById("jawaban-user").value);
        if (isNaN(userInp)) return;

        if (userInp === correctAnswer) {
          score += 10;
          document.getElementById("snd-correct").play();
          document.getElementById("feedback").innerHTML =
            "<span style='color:var(--secondary); text-shadow: 0 0 10px var(--secondary);'>⚡ CRITICAL HIT! +10 XP ⚡</span>";
          document.body.classList.add("correct-anim");
        } else {
          document.getElementById("snd-wrong").play();
          document.getElementById("feedback").innerHTML =
            "<span style='color:var(--wrong); text-shadow: 0 0 10px var(--wrong);'>❌ SALAH ❌</span>";
          document.body.classList.add("wrong-anim");
          document.getElementById("bahas").style.display = "block";
          document.getElementById("bahas").innerHTML =
            `<b>LOG SISTEM (PEMBAHASAN):</b><br>${currentData.rumus}`;
        }

        document.getElementById("skor").innerText = score;
        updateRank();

        // Disable input sementara
        document.getElementById("jawaban-user").disabled = true;

        setTimeout(() => {
          document.body.classList.remove("correct-anim", "wrong-anim");
          document.getElementById("jawaban-user").disabled = false;
          currentNo++;
          nextQuestion();
        }, 7000);
      }

      function updateRank() {
        let r = "PEMULA";
        let color = "#cbd5e1";

        if (score >= 90) {
          r = "JENIUS BRO 👑";
          color = "#facc15";
        } else if (score >= 60) {
          r = "AYO PASTI BISA 💎";
          color = "#00d2ff";
        } else if (score >= 30) {
          r = "BELAJAR LAGI YAAA 🏆";
          color = "#fbbf24";
        }

        if (r !== lastRank) {
          document.getElementById("snd-rankup").play();
          lastRank = r;
        }

        const rankEl = document.getElementById("rank");
        rankEl.innerText = r;
        rankEl.style.color = color;
      }

      function finish() {
        document.getElementById("bgm").pause();
        document.getElementById("snd-victory").play();
        document.getElementById("game").innerHTML = `
        <h1 style="color:var(--gold); font-size: 4em; margin-bottom: 0;">VICTORY!</h1>
        <p style="font-size: 1.5em; color: #cbd5e1;">Arena Diselesaikan</p>
        <div style="font-size: 6em; font-weight: 900; margin: 20px 0; color: var(--primary); text-shadow: 0 0 30px var(--primary);">${score}</div>
        <h2 style="font-size: 2.5em; color: white;">RANK FINAL:<br><span class="rank-text">${lastRank}</span></h2>
        <button class="btn" onclick="location.reload()" style="margin-top:30px; font-size: 1.5em; padding: 20px 50px;">MAIN LAGI 🔄</button>
    `;
      }
      function openSudut() {
        document.getElementById("menu").style.display = "none";
        document.getElementById("sudutPage").style.display = "block";
      }

      function openQuizSudut() {
        document.getElementById("menu").style.display = "none";
        document.getElementById("quizSudutPage").style.display = "block";
        injectSudut();
      }

      function openGabunganQuiz() {
        document.getElementById("menu").style.display = "none";
        document.getElementById("quizGabunganPage").style.display = "block";
        injectGabungan();
      }

      function backMenu() {
        document.getElementById("sudutPage").style.display = "none";
        document.getElementById("quizSudutPage").style.display = "none";
        document.getElementById("quizGabunganPage").style.display = "none";
        document.getElementById("game").style.display = "none";

        document.getElementById("menu").style.display = "block";
      }

      function handleGabunganEnter(e) {
        if (e.key === "Enter") {
          cekGabungan();
        }
      }

      function handleSudutEnter(e) {
        if (e.key === "Enter") cekSudut();
      }

      function nextSudutQuestion() {
        if (!ggbSudutApi) return;

        if (sudutNo > 5) {
          finishSudut();
          return;
        }

        ggbSudutApi.newConstruction();
        setupView(ggbSudutApi);

        document.getElementById("jawaban-sudut").value = "";
        document.getElementById("sudut-feedback").innerHTML = "";
        document.getElementById("sudut-bahas").style.display = "none";
        document.getElementById("sudut-no").innerText = sudutNo;

        let jenis = rand(1, 3); // ❗ 3 tipe soal
        let x = rand(30, 75);

        sudutData = { x: x, answer: 0, bahas: "" };

        // =========================
        // 1. PELURUS
        // =========================
        if (jenis === 1) {
          sudutData.answer = 180 - x;
          sudutData.bahas = `Sudut pelurus = 180° - ${x}° = ${sudutData.answer}°`;

          document.getElementById("sudut-pertanyaan").innerHTML =
            `Jika α = ${x}°, berapakah sudut pelurusnya?`;

          ggbSudutApi.evalCommand("A=(-6,0)");
          ggbSudutApi.evalCommand("B=(0,0)");
          ggbSudutApi.evalCommand("C=(6,0)");

          let rad = (x * Math.PI) / 180;
          ggbSudutApi.evalCommand(
            `D=(${4 * Math.cos(rad)},${4 * Math.sin(rad)})`,
          );

          ggbSudutApi.evalCommand("Line(A,C)");
          ggbSudutApi.evalCommand("Segment(B,D)");
          ggbSudutApi.evalCommand("s=Angle(C,B,D)");
          ggbSudutApi.setLabelVisible("s", false);

          ggbSudutApi.evalCommand(`Text("α = ${x}°", (1.5, 0.5))`);

          let currentSudutBahas = "";
          currentSudutBahas = `Sudut pelurus = 180° - α = 180° - ${x}° = ${sudutAnswer}°`;
        }

        // =========================
        // 2. SEHADAP
        // =========================
        else if (jenis === 2) {
          sudutData.answer = x;
          sudutData.bahas = `Sudut sehadap sama besar = ${x}°`;

          document.getElementById("sudut-pertanyaan").innerHTML =
            `Jika α = ${x}°, berapakah sudut sehadapnya?`;

          ggbSudutApi.evalCommand("Line((-5,2),(5,2))");
          ggbSudutApi.evalCommand("Line((-5,-1),(5,-1))");
          ggbSudutApi.evalCommand("Line((-2,-3),(3,4))");

          ggbSudutApi.evalCommand(`Text("α = ${x}°", (1.5, 2.3))`);
          ggbSudutApi.evalCommand(`Text("?", (-0.5, -0.7))`);

          sudutData.bahas = `<b>Pembahasan:</b><br>
    Sudut-sudut <b>sehadap</b> memiliki posisi yang sama sehingga besarnya sama.<br><br>

    Jadi:<br>${x}° = ${sudutData.answer}°`;
        }

        // =========================
        // 3. DALAM BERSEBERANGAN
        // =========================
        else {
          sudutData.answer = x;
          sudutData.bahas = `Sudut dalam berseberangan sama besar = ${x}°`;

          document.getElementById("sudut-pertanyaan").innerHTML =
            `Jika α = ${x}°, berapakah sudut dalam berseberangannya?`;

          ggbSudutApi.evalCommand("Line((-5,2),(5,2))");
          ggbSudutApi.evalCommand("Line((-5,-1),(5,-1))");
          ggbSudutApi.evalCommand("Line((-2,-3),(3,4))");

          ggbSudutApi.evalCommand(`Text("α = ${x}°", (1.5, 1.5))`);
          ggbSudutApi.evalCommand(`Text("?", (1.5, -0.7))`);

          sudutData.bahas = `<b>Pembahasan:</b><br>
    Sudut <b>dalam berseberangan</b> selalu sama besar.<br><br>

    Jadi:<br>${x}° = ${sudutData.answer}°`;
        }
      }

      function cekSudut() {
        document.getElementById("jawaban-sudut").disabled = true;
        let user = parseInt(document.getElementById("jawaban-sudut").value);

        if (isNaN(user)) return;

        if (user === sudutData.answer) {
          sudutScore += 10;

          document.getElementById("snd-correct").play();
          document.body.classList.add("correct-anim");

          setTimeout(()=>{
          document.body.classList.remove("correct-anim");
          },600);
          document.getElementById("sudut-feedback").innerHTML =
            "<span style='color:lime'>BENAR 🔥</span>";
        } else {
          document.getElementById("snd-wrong").play();
          document.body.classList.add("wrong-anim");

          setTimeout(() => {
          document.body.classList.remove("wrong-anim");
          },500);

          document.getElementById("sudut-feedback").innerHTML =
            "<span style='color:red'>SALAH ❌</span>";

          document.getElementById("sudut-bahas").style.display = "block";

          // PEMBAHASAN DINAMIS
          document.getElementById("sudut-bahas").innerHTML =
          `
          <b>📋 LOG SISTEM (PEMBAHASAN):</b>
          <hr style="border:1px solid #ef4444;">
          ${sudutData.bahas}
          `;
        }

        document.getElementById("sudut-skor").innerText = sudutScore;

        setTimeout(() => {
          document.getElementById("jawaban-sudut").disabled = false;
          sudutNo++;

          nextSudutQuestion();
        }, 5000);
      }

      function nextGabunganQuestion() {
        if (!ggbGabunganApi) return;

        if (gabunganNo > 5) {
          finishGabungan();
          return;
        }

        document.getElementById("jawaban-gabungan").value = "";
        document.getElementById("gabungan-feedback").innerHTML = "";
        document.getElementById("gabungan-bahas").style.display = "none";
        document.getElementById("gabungan-no").innerText = gabunganNo;

        const models = [
          {
            nama: "Balok + Limas",

            link: "https://www.geogebra.org/calculator/qhsy5tgn",

            soal:
              "Hitung volume gabungan balok dan limas berikut!<br><br>" +
              "Balok: p=6, l=4, t=5<br>" +
              "Limas memiliki tinggi 6",

            answer: 168,

            bahas: `
  Volume Balok = 6 × 4 × 5 = 120<br><br>

  Volume Limas = 1/3 × (6 × 4) × 6<br>
  = 48<br><br>

  Volume Gabungan = 120 + 48<br>
  = <b>168</b>
  `,
          },

          {
            nama: "Bangun Gabungan 2",

            link: "https://www.geogebra.org/calculator/y8sgktvy?embed",

            soal:
              "Hitung volume bangun gabungan berikut!<br><br>" +
              "Balok: p = 12 cm, l = 5 cm, t = 6 cm<br>" +
              "Prisma di atas memiliki tinggi 5 cm",

            answer: 510,

            bahas: `
  Volume Balok = 12 × 5 × 6
  = 360 cm³<br><br>

  Volume Prisma Atas =
  1/2 × 12 × 5 × 5
  = 150 cm³<br><br>

  Volume Total =
  360 + 150
  = <b>510 cm³</b>
  `,
          },

          {
            nama: "Bangun Gabungan 3",

            link: "https://www.geogebra.org/calculator/yqn5jg2r",

            soal:
              "Hitung volume bangun gabungan berikut!<br><br>" +
              "Balok: p = 15 cm, l = 12 cm, t = 10 cm<br>" +
              "Prisma di atas memiliki tinggi 8 cm",

            answer: 2520,

            bahas: `
  Volume Balok = 15 × 12 × 10
  = 1.800 cm³<br><br>

  Volume Prisma Atas =
  1/2 × 12 × 8 × 15
  = 720 cm³<br><br>

  Volume Total =
  1800 + 720
  = <b>2520 cm³</b>
  `,
          },
        ];

        let model = models[(gabunganNo - 1) % models.length];

        gabunganData.answer = model.answer;
        gabunganData.bahas = model.bahas;

        document.getElementById("gabungan-pertanyaan").innerHTML = model.soal;

        document.getElementById("ggb-gabungan").innerHTML = `
<iframe
src="${model.link}"
width="100%"
height="450"
style="
border:none;
border-radius:20px;
background:white;
overflow:hidden;
">
</iframe>
`;

        // warna balok
        ggbGabunganApi.setColor("balok", 0, 210, 255);
        ggbGabunganApi.setFilling("balok", 0.7);

        // LIMAS DI ATAS BALOK
        ggbGabunganApi.evalCommand(`
alasL = Polygon(
(0,0,5),
(6,0,5),
(6,4,5),
(0,4,5)
)
`);

        ggbGabunganApi.evalCommand(`
limas = Pyramid(alasL,(3,2,11))
`);

        // warna limas
        ggbGabunganApi.setColor("limas", 255, 215, 0);
        ggbGabunganApi.setFilling("limas", 0.8);
      }

      function finishGabungan() {
        document.getElementById("quizGabunganPage").innerHTML = `

  <div class="container">

    <h1>🧊 QUIZ GABUNGAN SELESAI</h1>

    <h2>Skor Akhir:</h2>

    <div style="
    font-size:70px;
    color:#00d2ff;
    font-weight:900;
    ">
      ${gabunganScore}
    </div>

    <button class="btn"
    onclick="location.reload()">

      MAIN LAGI 🔄

    </button>

  </div>
  `;
      }

      function finishSudut() {
        document.getElementById("quizSudutPage").innerHTML = `

    <div class="container">

    <h1>🎉 QUIZ SELESAI</h1>

    <h2>Skor Akhir:</h2>

    <div style="
    font-size:70px;
    color:#00d2ff;
    font-weight:900;
    ">
    ${sudutScore}
    </div>

    <button class="btn"
    onclick="location.reload()">
    MAIN LAGI 🔄
    </button>

    </div>
    `;
      }
    </script>
  </body>
</html>
