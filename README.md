```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Petualangan Glokalisasi - Sparxie & Sparkle Edition</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@400;600;700&family=Plus+Jakarta+Sans:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #ec4899;
            --secondary: #6366f1;
            --accent: #f59e0b;
        }

        body {
            font-family: 'Plus Jakarta Sans', sans-serif;
            background-color: #070913;
            color: #f8fafc;
            overflow-x: hidden;
            user-select: none;
            -webkit-tap-highlight-color: transparent;
        }

        h1, h2, h3, .font-display {
            font-family: 'Fredoka', sans-serif;
        }

        /* Latar Belakang Tema Honkai / Astral & Kota */
        .bg-astral-map {
            background: radial-gradient(circle at 50% 15%, #3b1d5e 0%, #17153b 48%, #070913 95%);
        }

        .bg-city-vn {
            background: linear-gradient(180deg, rgba(15, 23, 42, 0.25) 0%, rgba(15, 23, 42, 0.85) 75%, #070913 100%),
                        radial-gradient(circle at 20% 25%, #be123c 0%, transparent 45%),
                        radial-gradient(circle at 85% 25%, #6366f1 0%, transparent 45%),
                        linear-gradient(135deg, #1e1b4b 0%, #2e1065 55%, #090d16 100%);
        }

        .bg-cosmic-battle {
            background: radial-gradient(circle at 50% 45%, #311042 0%, #18122b 48%, #070913 92%);
        }

        .star-grid {
            background-image: radial-gradient(#ffffff 1px, transparent 1px), radial-gradient(#f472b6 1.5px, transparent 1.5px);
            background-size: 48px 48px, 85px 85px;
            background-position: 0 0, 22px 22px;
            opacity: 0.22;
        }

        /* Animasi Karakter & Pertarungan */
        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-7px); }
        }

        @keyframes pulse-ring {
            0% { box-shadow: 0 0 0 0 rgba(236, 72, 153, 0.7); }
            70% { box-shadow: 0 0 0 12px rgba(236, 72, 153, 0); }
            100% { box-shadow: 0 0 0 0 rgba(236, 72, 153, 0); }
        }

        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            20% { transform: translateX(-10px) rotate(-3deg); }
            40% { transform: translateX(10px) rotate(3deg); }
            60% { transform: translateX(-8px); }
            80% { transform: translateX(8px); }
        }

        @keyframes attack-lunge {
            0% { transform: translateX(0) scale(1); }
            40% { transform: translateX(42px) scale(1.15); }
            100% { transform: translateX(0) scale(1); }
        }

        @keyframes pop-in {
            0% { transform: scale(0.86); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }

        @keyframes explode {
            0% { transform: scale(0.2); opacity: 1; }
            50% { transform: scale(1.45); opacity: 1; }
            100% { transform: scale(1.85); opacity: 0; }
        }

        .animate-float { animation: float 3s ease-in-out infinite; }
        .animate-float-delayed { animation: float 3.4s ease-in-out 1s infinite; }
        .animate-pulse-ring { animation: pulse-ring 2s infinite; }
        .animate-shake { animation: shake 0.45s ease-in-out; }
        .animate-lunge { animation: attack-lunge 0.45s cubic-bezier(0.22, 1, 0.36, 1); }
        .animate-pop { animation: pop-in 0.28s cubic-bezier(0.16, 1, 0.3, 1) forwards; }
        .animate-explode { animation: explode 0.65s ease-out forwards; }

        .active-speaker {
            transform: scale(1.07) translateY(-6px);
            filter: brightness(1.08) drop-shadow(0 10px 18px rgba(244, 63, 94, 0.5));
            z-index: 20;
        }

        .inactive-speaker {
            transform: scale(0.91);
            filter: brightness(0.58) grayscale(25%);
            z-index: 10;
        }

        .btn-rpg {
            transition: all 0.16s cubic-bezier(0.34, 1.56, 0.64, 1);
            box-shadow: 0 4px 0 rgba(0, 0, 0, 0.45);
        }
        .btn-rpg:active {
            transform: translateY(3px);
            box-shadow: 0 1px 0 rgba(0, 0, 0, 0.45);
        }

        ::-webkit-scrollbar { width: 5px; }
        ::-webkit-scrollbar-track { background: rgba(15, 23, 42, 0.5); }
        ::-webkit-scrollbar-thumb { background: rgba(236, 72, 153, 0.6); border-radius: 999px; }
    </style>
</head>
<body class="min-h-screen flex flex-col items-center justify-center p-0 sm:p-4">

    <!-- Container Utama Game (Mobile Portrait & Responsive Desktop Frame) -->
    <div id="app-frame" class="relative w-full max-w-md sm:max-w-2xl lg:max-w-4xl min-h-screen sm:min-h-[700px] sm:h-[90vh] bg-slate-950 sm:rounded-3xl shadow-2xl border-0 sm:border-2 border-pink-500/30 overflow-hidden flex flex-col justify-between">

        <!-- =========================================================
             TOP STEPPER HUD ALA OBEY ME! (BERURUTAN: BELAJAR -> BERLATIH -> PENILAIAN)
        ========================================================== -->
        <header id="top-hud" class="hidden z-30 px-3 sm:px-5 py-2.5 bg-slate-950/90 backdrop-blur-md border-b border-white/10 flex flex-col gap-2">
            <div class="flex items-center justify-between">
                <button onclick="navigateTo('menu')" class="btn-rpg px-2.5 py-1 rounded-xl bg-slate-800 hover:bg-slate-700 text-xs font-bold text-slate-200 flex items-center gap-1 border border-white/10">
                    <span>🗺️</span> Peta Bab
                </button>
                <div class="text-xs font-display font-bold tracking-wider uppercase text-pink-300">
                    Lesson 1: Harmoni Glokalisasi
                </div>
                <div class="flex items-center gap-1.5 bg-amber-500/20 border border-amber-400/40 px-2.5 py-0.5 rounded-xl">
                    <span class="text-xs">⭐</span>
                    <span id="hud-score" class="font-display font-bold text-amber-300 text-xs sm:text-sm">0</span>
                </div>
            </div>

            <!-- Jalur Progres Berurutan (Obey Me! Lesson Flow) -->
            <div class="grid grid-cols-3 gap-1.5 items-center text-[11px] font-bold">
                <div id="step-pill-1" class="py-1 px-2 rounded-lg text-center border transition-all bg-pink-600/30 border-pink-400 text-white">
                    1. 📖 Belajar
                </div>
                <div id="step-pill-2" class="py-1 px-2 rounded-lg text-center border transition-all bg-slate-900 border-white/10 text-slate-500">
                    2. 🎯 Berlatih
                </div>
                <div id="step-pill-3" class="py-1 px-2 rounded-lg text-center border transition-all bg-slate-900 border-white/10 text-slate-500">
                    3. ⚔️ Penilaian
                </div>
            </div>
        </header>

        <!-- =========================================================
             SCREEN 1: LOBBY & PETA LESSON BERURUTAN (OBEY ME! STYLE)
        ========================================================== -->
        <section id="screen-menu" class="flex-1 flex flex-col justify-between p-5 sm:p-8 bg-astral-map relative overflow-y-auto">
            <div class="star-grid absolute inset-0 pointer-events-none"></div>

            <!-- Header Judul -->
            <div class="relative z-10 text-center mt-2">
                <div class="inline-flex items-center gap-1.5 px-3.5 py-1 rounded-full bg-pink-500/20 border border-pink-400/40 text-[11px] font-bold text-pink-200 mb-2">
                    <span>🎭</span> Masked Fools Academy • Astral Express
                </div>
                <h1 class="text-3xl sm:text-5xl font-bold text-transparent bg-clip-text bg-gradient-to-r from-rose-300 via-amber-200 to-pink-400 leading-tight">
                    Petualangan Glokalisasi
                </h1>
                <p class="text-slate-300 text-xs sm:text-sm mt-1.5 max-w-md mx-auto">
                    Ikuti alur cerita berurutan dari <strong>Belajar</strong>, <strong>Berlatih</strong>, hingga <strong>Pertarungan Ujian</strong> bersama <strong>Sparxie</strong> & <strong>Sparkle</strong>!
                </p>
            </div>

            <!-- Showcase Duo Karakter: Sparxie & Sparkle -->
            <div class="relative z-10 flex items-center justify-center gap-4 sm:gap-8 my-3">
                <div class="animate-float text-center">
                    <div id="menu-avatar-sparxie" class="w-28 h-28 sm:w-32 sm:h-32 mx-auto"></div>
                    <span class="inline-block mt-1 px-3 py-0.5 rounded-full bg-rose-500/30 border border-rose-300/50 text-xs font-bold text-rose-100">
                        🐰 Sparxie
                    </span>
                </div>
                <div class="flex flex-col items-center">
                    <span class="text-xl sm:text-2xl font-display font-bold text-amber-300">✦</span>
                    <span class="text-[10px] uppercase tracking-widest text-pink-300 font-bold">Partner</span>
                </div>
                <div class="animate-float-delayed text-center">
                    <div id="menu-avatar-sparkle" class="w-28 h-28 sm:w-32 sm:h-32 mx-auto"></div>
                    <span class="inline-block mt-1 px-3 py-0.5 rounded-full bg-fuchsia-600/30 border border-fuchsia-400/50 text-xs font-bold text-fuchsia-100">
                        🦊 Sparkle
                    </span>
                </div>
            </div>

            <!-- Peta Node Berurutan Ala Obey Me! (Stage 1 -> Stage 2 -> Stage 3) -->
            <div class="relative z-10 max-w-md mx-auto w-full bg-slate-950/75 backdrop-blur-md border border-pink-400/30 rounded-3xl p-4 my-2">
                <div class="flex items-center justify-between mb-3">
                    <span class="text-xs font-bold uppercase tracking-wider text-amber-300">📍 Alur Lesson 1 (Berurutan)</span>
                    <span class="text-xs font-bold text-slate-300">Skor: <strong id="menu-total-score" class="text-amber-400">0</strong></span>
                </div>

                <!-- Visual Node Path -->
                <div class="relative flex items-center justify-between px-2 py-2">
                    <!-- Garis Penghubung -->
                    <div class="absolute left-8 right-8 top-1/2 -translate-y-1/2 h-1 bg-slate-800 rounded-full z-0">
                        <div id="map-progress-line" class="h-full bg-gradient-to-r from-rose-500 to-amber-400 rounded-full transition-all duration-500" style="width: 0%;"></div>
                    </div>

                    <!-- Node 1: Belajar -->
                    <div id="node-1" class="relative z-10 flex flex-col items-center gap-1">
                        <div class="w-12 h-12 rounded-2xl bg-rose-600 border-2 border-rose-300 flex items-center justify-center text-xl shadow-lg">
                            📖
                        </div>
                        <span class="text-[11px] font-bold text-white">1. Belajar</span>
                    </div>

                    <!-- Node 2: Berlatih -->
                    <div id="node-2" class="relative z-10 flex flex-col items-center gap-1">
                        <div id="node-2-icon" class="w-12 h-12 rounded-2xl bg-slate-800 border-2 border-slate-600 flex items-center justify-center text-xl shadow-lg">
                            🔒
                        </div>
                        <span class="text-[11px] font-bold text-slate-400" id="node-2-label">2. Berlatih</span>
                    </div>

                    <!-- Node 3: Penilaian -->
                    <div id="node-3" class="relative z-10 flex flex-col items-center gap-1">
                        <div id="node-3-icon" class="w-12 h-12 rounded-2xl bg-slate-800 border-2 border-slate-600 flex items-center justify-center text-xl shadow-lg">
                            🔒
                        </div>
                        <span class="text-[11px] font-bold text-slate-400" id="node-3-label">3. Penilaian</span>
                    </div>
                </div>
            </div>

            <!-- Tombol Mulai Petualangan Berurutan -->
            <div class="relative z-10 max-w-md mx-auto w-full flex flex-col gap-2.5 mt-2">
                <button id="btn-start-journey" onclick="continueSequentialJourney()" class="btn-rpg animate-pulse-ring w-full py-4 px-6 rounded-2xl bg-gradient-to-r from-rose-600 via-pink-600 to-amber-500 hover:from-rose-500 hover:to-amber-400 border border-pink-200/40 font-display font-bold text-lg text-white flex items-center justify-center gap-2 shadow-xl">
                    <span>▶</span> <span id="btn-start-text">Mulai Petualangan (Stage 1)</span>
                </button>
                <button id="btn-reset-journey" onclick="resetProgress()" class="hidden text-xs text-slate-400 hover:text-rose-300 underline py-1">
                    Ulangi dari Awal (Reset Progres)
                </button>
            </div>
        </section>

        <!-- =========================================================
             STAGE 1: BELAJAR (VISUAL NOVEL DIALOG SPARXIE & SPARKLE)
        ========================================================== -->
        <section id="screen-mode1" class="hidden flex-1 flex flex-col justify-between bg-city-vn relative overflow-hidden">
            <!-- Siluet Kota Penacony / Futuristik -->
            <div class="absolute inset-x-0 top-6 h-60 pointer-events-none opacity-35 flex items-end justify-around px-4">
                <div class="w-16 h-44 bg-rose-400/20 rounded-t-lg border-t border-x border-rose-300/30"></div>
                <div class="w-24 h-56 bg-indigo-400/20 rounded-t-lg border-t border-x border-indigo-300/30"></div>
                <div class="w-20 h-36 bg-pink-400/20 rounded-t-lg border-t border-x border-pink-300/30"></div>
                <div class="w-28 h-52 bg-amber-400/20 rounded-t-lg border-t border-x border-amber-300/30"></div>
            </div>

            <!-- Top Info Bar -->
            <div class="relative z-10 px-4 pt-3 flex justify-between items-center">
                <span id="vn-topic-badge" class="px-3 py-1 rounded-full bg-slate-950/75 border border-pink-400/40 text-xs font-semibold text-pink-200">
                    Bab 1: Apa itu Glokalisasi?
                </span>
                <span id="vn-counter" class="px-3 py-1 rounded-full bg-slate-950/75 border border-white/15 text-xs font-bold text-amber-300">
                    Dialog 1/7
                </span>
            </div>

            <!-- Panggung Karakter Chibi: Kiri (Sparxie) & Kanan (Sparkle) -->
            <div class="relative z-10 flex-1 flex items-end justify-around px-3 sm:px-10 pb-2">
                <!-- Kiri: Sparxie -->
                <div id="vn-char-left" class="transition-all duration-300 flex flex-col items-center">
                    <div id="vn-emotion-left" class="mb-1 px-2.5 py-0.5 rounded-full bg-white text-slate-900 text-xs font-bold shadow-md">
                        👍 Mantap!
                    </div>
                    <div id="vn-avatar-left" class="w-36 h-36 sm:w-44 sm:h-44"></div>
                </div>

                <!-- Kanan: Sparkle -->
                <div id="vn-char-right" class="transition-all duration-300 flex flex-col items-center">
                    <div id="vn-emotion-right" class="mb-1 px-2.5 py-0.5 rounded-full bg-white text-slate-900 text-xs font-bold shadow-md">
                        🦊 Hehe~
                    </div>
                    <div id="vn-avatar-right" class="w-36 h-36 sm:w-44 sm:h-44"></div>
                </div>
            </div>

            <!-- Kotak Dialog Hitam Visual Novel -->
            <div class="relative z-20 bg-slate-950/95 border-t-2 border-pink-500/50 p-4 sm:p-6 min-h-[205px] flex flex-col justify-between shadow-[0_-10px_30px_rgba(0,0,0,0.8)]">
                <div>
                    <div class="flex items-center gap-2 mb-2">
                        <span id="vn-speaker-name" class="px-3.5 py-0.5 rounded-lg bg-gradient-to-r from-rose-500 to-red-600 text-white font-display font-bold text-sm tracking-wide shadow">
                            Sparxie
                        </span>
                        <span id="vn-speaker-role" class="text-xs text-slate-400 font-medium">Penjelajah Budaya Global</span>
                    </div>
                    <p id="vn-dialogue-text" class="text-slate-100 text-sm sm:text-base leading-relaxed font-medium">
                        Memuat dialog...
                    </p>
                </div>

                <!-- Navigasi Dialog -->
                <div class="flex items-center justify-between gap-2 mt-4 pt-3 border-t border-white/10">
                    <button id="btn-vn-prev" onclick="prevDialogue()" class="btn-rpg px-3.5 py-2 rounded-xl bg-slate-800 hover:bg-slate-700 disabled:opacity-40 disabled:pointer-events-none text-xs sm:text-sm font-bold text-slate-200 border border-white/10">
                        ◀ Kembali
                    </button>
                    <div class="flex gap-1.5" id="vn-dots"></div>
                    <button id="btn-vn-next" onclick="nextDialogue()" class="btn-rpg px-4 py-2 rounded-xl bg-gradient-to-r from-rose-500 to-pink-600 hover:from-rose-400 hover:to-pink-500 text-xs sm:text-sm font-bold text-white shadow-lg">
                        Lanjut ▶
                    </button>
                </div>
            </div>
        </section>

        <!-- =========================================================
             STAGE 2: BERLATIH (PRACTICE QUIZ + POP-UP PEMBENARAN)
        ========================================================== -->
        <section id="screen-mode2" class="hidden flex-1 flex flex-col justify-between bg-city-vn relative overflow-y-auto p-4 sm:p-6">
            <div class="flex items-center justify-between bg-slate-950/80 backdrop-blur-md p-3 rounded-2xl border border-pink-400/30">
                <span class="text-xs sm:text-sm font-bold text-pink-300">🎯 Stage 2: Latihan Terpandu</span>
                <span id="practice-counter" class="px-3 py-1 rounded-full bg-pink-500/20 border border-pink-400/40 text-xs font-bold text-pink-200">
                    Soal 1 / 4
                </span>
            </div>

            <!-- Kartu Pertanyaan -->
            <div class="my-auto py-3 flex flex-col gap-3.5">
                <div class="bg-slate-950/90 backdrop-blur-md border-2 border-pink-500/40 rounded-3xl p-5 shadow-xl">
                    <div class="text-xs font-bold uppercase tracking-wider text-rose-400 mb-1">Uji Pemahaman Materi</div>
                    <h2 id="practice-question" class="text-base sm:text-lg font-bold text-white leading-snug">
                        Pertanyaan latihan...
                    </h2>
                </div>

                <!-- 3 Pilihan Jawaban -->
                <div id="practice-options" class="flex flex-col gap-2.5"></div>
            </div>

            <!-- Pendamping Sparxie & Sparkle di Bawah -->
            <div class="flex items-center justify-between bg-slate-950/85 rounded-2xl border border-white/10 p-3 gap-3">
                <div id="practice-helper-left" class="w-14 h-14 shrink-0"></div>
                <p class="text-xs text-slate-300 text-center">
                    "Pilih jawaban yang paling pas! Kalau salah, tenang aja, aku dan Sparkle bakal kasih tahu alasannya!"
                </p>
                <div id="practice-helper-right" class="w-14 h-14 shrink-0"></div>
            </div>
        </section>

        <!-- =========================================================
             STAGE 3: PENILAIAN (MONSTER BATTLE QUIZ)
        ==================================```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Petualangan Glokalisasi - Sparxie & Sparkle Edition</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@400;600;700&family=Plus+Jakarta+Sans:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #ec4899;
            --secondary: #6366f1;
            --accent: #f59e0b;
        }

        body {
            font-family: 'Plus Jakarta Sans', sans-serif;
            background-color: #070913;
            color: #f8fafc;
            overflow-x: hidden;
            user-select: none;
            -webkit-tap-highlight-color: transparent;
        }

        h1, h2, h3, .font-display {
            font-family: 'Fredoka', sans-serif;
        }

        /* Latar Belakang Tema Honkai / Astral & Kota */
        .bg-astral-map {
            background: radial-gradient(circle at 50% 15%, #3b1d5e 0%, #17153b 48%, #070913 95%);
        }

        .bg-city-vn {
            background: linear-gradient(180deg, rgba(15, 23, 42, 0.25) 0%, rgba(15, 23, 42, 0.85) 75%, #070913 100%),
                        radial-gradient(circle at 20% 25%, #be123c 0%, transparent 45%),
                        radial-gradient(circle at 85% 25%, #6366f1 0%, transparent 45%),
                        linear-gradient(135deg, #1e1b4b 0%, #2e1065 55%, #090d16 100%);
        }

        .bg-cosmic-battle {
            background: radial-gradient(circle at 50% 45%, #311042 0%, #18122b 48%, #070913 92%);
        }

        .star-grid {
            background-image: radial-gradient(#ffffff 1px, transparent 1px), radial-gradient(#f472b6 1.5px, transparent 1.5px);
            background-size: 48px 48px, 85px 85px;
            background-position: 0 0, 22px 22px;
            opacity: 0.22;
        }

        /* Animasi Karakter & Pertarungan */
        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-7px); }
        }

        @keyframes pulse-ring {
            0% { box-shadow: 0 0 0 0 rgba(236, 72, 153, 0.7); }
            70% { box-shadow: 0 0 0 12px rgba(236, 72, 153, 0); }
            100% { box-shadow: 0 0 0 0 rgba(236, 72, 153, 0); }
        }

        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            20% { transform: translateX(-10px) rotate(-3deg); }
            40% { transform: translateX(10px) rotate(3deg); }
            60% { transform: translateX(-8px); }
            80% { transform: translateX(8px); }
        }

        @keyframes attack-lunge {
            0% { transform: translateX(0) scale(1); }
            40% { transform: translateX(42px) scale(1.15); }
            100% { transform: translateX(0) scale(1); }
        }

        @keyframes pop-in {
            0% { transform: scale(0.86); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }

        @keyframes explode {
            0% { transform: scale(0.2); opacity: 1; }
            50% { transform: scale(1.45); opacity: 1; }
            100% { transform: scale(1.85); opacity: 0; }
        }

        .animate-float { animation: float 3s ease-in-out infinite; }
        .animate-float-delayed { animation: float 3.4s ease-in-out 1s infinite; }
        .animate-pulse-ring { animation: pulse-ring 2s infinite; }
        .animate-shake { animation: shake 0.45s ease-in-out; }
        .animate-lunge { animation: attack-lunge 0.45s cubic-bezier(0.22, 1, 0.36, 1); }
        .animate-pop { animation: pop-in 0.28s cubic-bezier(0.16, 1, 0.3, 1) forwards; }
        .animate-explode { animation: explode 0.65s ease-out forwards; }

        .active-speaker {
            transform: scale(1.07) translateY(-6px);
            filter: brightness(1.08) drop-shadow(0 10px 18px rgba(244, 63, 94, 0.5));
            z-index: 20;
        }

        .inactive-speaker {
            transform: scale(0.91);
            filter: brightness(0.58) grayscale(25%);
            z-index: 10;
        }

        .btn-rpg {
            transition: all 0.16s cubic-bezier(0.34, 1.56, 0.64, 1);
            box-shadow: 0 4px 0 rgba(0, 0, 0, 0.45);
        }
        .btn-rpg:active {
            transform: translateY(3px);
            box-shadow: 0 1px 0 rgba(0, 0, 0, 0.45);
        }

        ::-webkit-scrollbar { width: 5px; }
        ::-webkit-scrollbar-track { background: rgba(15, 23, 42, 0.5); }
        ::-webkit-scrollbar-thumb { background: rgba(236, 72, 153, 0.6); border-radius: 999px; }
    </style>
</head>
<body class="min-h-screen flex flex-col items-center justify-center p-0 sm:p-4">

    <!-- Container Utama Game (Mobile Portrait & Responsive Desktop Frame) -->
    <div id="app-frame" class="relative w-full max-w-md sm:max-w-2xl lg:max-w-4xl min-h-screen sm:min-h-[700px] sm:h-[90vh] bg-slate-950 sm:rounded-3xl shadow-2xl border-0 sm:border-2 border-pink-500/30 overflow-hidden flex flex-col justify-between">

        <!-- =========================================================
             TOP STEPPER HUD ALA OBEY ME! (BERURUTAN: BELAJAR -> BERLATIH -> PENILAIAN)
        ========================================================== -->
        <header id="top-hud" class="hidden z-30 px-3 sm:px-5 py-2.5 bg-slate-950/90 backdrop-blur-md border-b border-white/10 flex flex-col gap-2">
            <div class="flex items-center justify-between">
                <button onclick="navigateTo('menu')" class="btn-rpg px-2.5 py-1 rounded-xl bg-slate-800 hover:bg-slate-700 text-xs font-bold text-slate-200 flex items-center gap-1 border border-white/10">
                    <span>🗺️</span> Peta Bab
                </button>
                <div class="text-xs font-display font-bold tracking-wider uppercase text-pink-300">
                    Lesson 1: Harmoni Glokalisasi
                </div>
                <div class="flex items-center gap-1.5 bg-amber-500/20 border border-amber-400/40 px-2.5 py-0.5 rounded-xl">
                    <span class="text-xs">⭐</span>
                    <span id="hud-score" class="font-display font-bold text-amber-300 text-xs sm:text-sm">0</span>
                </div>
            </div>

            <!-- Jalur Progres Berurutan (Obey Me! Lesson Flow) -->
            <div class="grid grid-cols-3 gap-1.5 items-center text-[11px] font-bold">
                <div id="step-pill-1" class="py-1 px-2 rounded-lg text-center border transition-all bg-pink-600/30 border-pink-400 text-white">
                    1. 📖 Belajar
                </div>
                <div id="step-pill-2" class="py-1 px-2 rounded-lg text-center border transition-all bg-slate-900 border-white/10 text-slate-500">
                    2. 🎯 Berlatih
                </div>
                <div id="step-pill-3" class="py-1 px-2 rounded-lg text-center border transition-all bg-slate-900 border-white/10 text-slate-500">
                    3. ⚔️ Penilaian
                </div>
            </div>
        </header>

        <!-- =========================================================
             SCREEN 1: LOBBY & PETA LESSON BERURUTAN (OBEY ME! STYLE)
        ========================================================== -->
        <section id="screen-menu" class="flex-1 flex flex-col justify-between p-5 sm:p-8 bg-astral-map relative overflow-y-auto">
            <div class="star-grid absolute inset-0 pointer-events-none"></div>

            <!-- Header Judul -->
            <div class="relative z-10 text-center mt-2">
                <div class="inline-flex items-center gap-1.5 px-3.5 py-1 rounded-full bg-pink-500/20 border border-pink-400/40 text-[11px] font-bold text-pink-200 mb-2">
                    <span>🎭</span> Masked Fools Academy • Astral Express
                </div>
                <h1 class="text-3xl sm:text-5xl font-bold text-transparent bg-clip-text bg-gradient-to-r from-rose-300 via-amber-200 to-pink-400 leading-tight">
                    Petualangan Glokalisasi
                </h1>
                <p class="text-slate-300 text-xs sm:text-sm mt-1.5 max-w-md mx-auto">
                    Ikuti alur cerita berurutan dari <strong>Belajar</strong>, <strong>Berlatih</strong>, hingga <strong>Pertarungan Ujian</strong> bersama <strong>Sparxie</strong> & <strong>Sparkle</strong>!
                </p>
            </div>

            <!-- Showcase Duo Karakter: Sparxie & Sparkle -->
            <div class="relative z-10 flex items-center justify-center gap-4 sm:gap-8 my-3">
                <div class="animate-float text-center">
                    <div id="menu-avatar-sparxie" class="w-28 h-28 sm:w-32 sm:h-32 mx-auto"></div>
                    <span class="inline-block mt-1 px-3 py-0.5 rounded-full bg-rose-500/30 border border-rose-300/50 text-xs font-bold text-rose-100">
                        🐰 Sparxie
                    </span>
                </div>
                <div class="flex flex-col items-center">
                    <span class="text-xl sm:text-2xl font-display font-bold text-amber-300">✦</span>
                    <span class="text-[10px] uppercase tracking-widest text-pink-300 font-bold">Partner</span>
                </div>
                <div class="animate-float-delayed text-center">
                    <div id="menu-avatar-sparkle" class="w-28 h-28 sm:w-32 sm:h-32 mx-auto"></div>
                    <span class="inline-block mt-1 px-3 py-0.5 rounded-full bg-fuchsia-600/30 border border-fuchsia-400/50 text-xs font-bold text-fuchsia-100">
                        🦊 Sparkle
                    </span>
                </div>
            </div>

            <!-- Peta Node Berurutan Ala Obey Me! (Stage 1 -> Stage 2 -> Stage 3) -->
            <div class="relative z-10 max-w-md mx-auto w-full bg-slate-950/75 backdrop-blur-md border border-pink-400/30 rounded-3xl p-4 my-2">
                <div class="flex items-center justify-between mb-3">
                    <span class="text-xs font-bold uppercase tracking-wider text-amber-300">📍 Alur Lesson 1 (Berurutan)</span>
                    <span class="text-xs font-bold text-slate-300">Skor: <strong id="menu-total-score" class="text-amber-400">0</strong></span>
                </div>

                <!-- Visual Node Path -->
                <div class="relative flex items-center justify-between px-2 py-2">
                    <!-- Garis Penghubung -->
                    <div class="absolute left-8 right-8 top-1/2 -translate-y-1/2 h-1 bg-slate-800 rounded-full z-0">
                        <div id="map-progress-line" class="h-full bg-gradient-to-r from-rose-500 to-amber-400 rounded-full transition-all duration-500" style="width: 0%;"></div>
                    </div>

                    <!-- Node 1: Belajar -->
                    <div id="node-1" class="relative z-10 flex flex-col items-center gap-1">
                        <div class="w-12 h-12 rounded-2xl bg-rose-600 border-2 border-rose-300 flex items-center justify-center text-xl shadow-lg">
                            📖
                        </div>
                        <span class="text-[11px] font-bold text-white">1. Belajar</span>
                    </div>

                    <!-- Node 2: Berlatih -->
                    <div id="node-2" class="relative z-10 flex flex-col items-center gap-1">
                        <div id="node-2-icon" class="w-12 h-12 rounded-2xl bg-slate-800 border-2 border-slate-600 flex items-center justify-center text-xl shadow-lg">
                            🔒
                        </div>
                        <span class="text-[11px] font-bold text-slate-400" id="node-2-label">2. Berlatih</span>
                    </div>

                    <!-- Node 3: Penilaian -->
                    <div id="node-3" class="relative z-10 flex flex-col items-center gap-1">
                        <div id="node-3-icon" class="w-12 h-12 rounded-2xl bg-slate-800 border-2 border-slate-600 flex items-center justify-center text-xl shadow-lg">
                            🔒
                        </div>
                        <span class="text-[11px] font-bold text-slate-400" id="node-3-label">3. Penilaian</span>
                    </div>
                </div>
            </div>

            <!-- Tombol Mulai Petualangan Berurutan -->
            <div class="relative z-10 max-w-md mx-auto w-full flex flex-col gap-2.5 mt-2">
                <button id="btn-start-journey" onclick="continueSequentialJourney()" class="btn-rpg animate-pulse-ring w-full py-4 px-6 rounded-2xl bg-gradient-to-r from-rose-600 via-pink-600 to-amber-500 hover:from-rose-500 hover:to-amber-400 border border-pink-200/40 font-display font-bold text-lg text-white flex items-center justify-center gap-2 shadow-xl">
                    <span>▶</span> <span id="btn-start-text">Mulai Petualangan (Stage 1)</span>
                </button>
                <button id="btn-reset-journey" onclick="resetProgress()" class="hidden text-xs text-slate-400 hover:text-rose-300 underline py-1">
                    Ulangi dari Awal (Reset Progres)
                </button>
            </div>
        </section>

        <!-- =========================================================
             STAGE 1: BELAJAR (VISUAL NOVEL DIALOG SPARXIE & SPARKLE)
        ========================================================== -->
        <section id="screen-mode1" class="hidden flex-1 flex flex-col justify-between bg-city-vn relative overflow-hidden">
            <!-- Siluet Kota Penacony / Futuristik -->
            <div class="absolute inset-x-0 top-6 h-60 pointer-events-none opacity-35 flex items-end justify-around px-4">
                <div class="w-16 h-44 bg-rose-400/20 rounded-t-lg border-t border-x border-rose-300/30"></div>
                <div class="w-24 h-56 bg-indigo-400/20 rounded-t-lg border-t border-x border-indigo-300/30"></div>
                <div class="w-20 h-36 bg-pink-400/20 rounded-t-lg border-t border-x border-pink-300/30"></div>
                <div class="w-28 h-52 bg-amber-400/20 rounded-t-lg border-t border-x border-amber-300/30"></div>
            </div>

            <!-- Top Info Bar -->
            <div class="relative z-10 px-4 pt-3 flex justify-between items-center">
                <span id="vn-topic-badge" class="px-3 py-1 rounded-full bg-slate-950/75 border border-pink-400/40 text-xs font-semibold text-pink-200">
                    Bab 1: Apa itu Glokalisasi?
                </span>
                <span id="vn-counter" class="px-3 py-1 rounded-full bg-slate-950/75 border border-white/15 text-xs font-bold text-amber-300">
                    Dialog 1/7
                </span>
            </div>

            <!-- Panggung Karakter Chibi: Kiri (Sparxie) & Kanan (Sparkle) -->
            <div class="relative z-10 flex-1 flex items-end justify-around px-3 sm:px-10 pb-2">
                <!-- Kiri: Sparxie -->
                <div id="vn-char-left" class="transition-all duration-300 flex flex-col items-center">
                    <div id="vn-emotion-left" class="mb-1 px-2.5 py-0.5 rounded-full bg-white text-slate-900 text-xs font-bold shadow-md">
                        👍 Mantap!
                    </div>
                    <div id="vn-avatar-left" class="w-36 h-36 sm:w-44 sm:h-44"></div>
                </div>

                <!-- Kanan: Sparkle -->
                <div id="vn-char-right" class="transition-all duration-300 flex flex-col items-center">
                    <div id="vn-emotion-right" class="mb-1 px-2.5 py-0.5 rounded-full bg-white text-slate-900 text-xs font-bold shadow-md">
                        🦊 Hehe~
                    </div>
                    <div id="vn-avatar-right" class="w-36 h-36 sm:w-44 sm:h-44"></div>
                </div>
            </div>

            <!-- Kotak Dialog Hitam Visual Novel -->
            <div class="relative z-20 bg-slate-950/95 border-t-2 border-pink-500/50 p-4 sm:p-6 min-h-[205px] flex flex-col justify-between shadow-[0_-10px_30px_rgba(0,0,0,0.8)]">
                <div>
                    <div class="flex items-center gap-2 mb-2">
                        <span id="vn-speaker-name" class="px-3.5 py-0.5 rounded-lg bg-gradient-to-r from-rose-500 to-red-600 text-white font-display font-bold text-sm tracking-wide shadow">
                            Sparxie
                        </span>
                        <span id="vn-speaker-role" class="text-xs text-slate-400 font-medium">Penjelajah Budaya Global</span>
                    </div>
                    <p id="vn-dialogue-text" class="text-slate-100 text-sm sm:text-base leading-relaxed font-medium">
                        Memuat dialog...
                    </p>
                </div>

                <!-- Navigasi Dialog -->
                <div class="flex items-center justify-between gap-2 mt-4 pt-3 border-t border-white/10">
                    <button id="btn-vn-prev" onclick="prevDialogue()" class="btn-rpg px-3.5 py-2 rounded-xl bg-slate-800 hover:bg-slate-700 disabled:opacity-40 disabled:pointer-events-none text-xs sm:text-sm font-bold text-slate-200 border border-white/10">
                        ◀ Kembali
                    </button>
                    <div class="flex gap-1.5" id="vn-dots"></div>
                    <button id="btn-vn-next" onclick="nextDialogue()" class="btn-rpg px-4 py-2 rounded-xl bg-gradient-to-r from-rose-500 to-pink-600 hover:from-rose-400 hover:to-pink-500 text-xs sm:text-sm font-bold text-white shadow-lg">
                        Lanjut ▶
                    </button>
                </div>
            </div>
        </section>

        <!-- =========================================================
             STAGE 2: BERLATIH (PRACTICE QUIZ + POP-UP PEMBENARAN)
        ========================================================== -->
        <section id="screen-mode2" class="hidden flex-1 flex flex-col justify-between bg-city-vn relative overflow-y-auto p-4 sm:p-6">
            <div class="flex items-center justify-between bg-slate-950/80 backdrop-blur-md p-3 rounded-2xl border border-pink-400/30">
                <span class="text-xs sm:text-sm font-bold text-pink-300">🎯 Stage 2: Latihan Terpandu</span>
                <span id="practice-counter" class="px-3 py-1 rounded-full bg-pink-500/20 border border-pink-400/40 text-xs font-bold text-pink-200">
                    Soal 1 / 4
                </span>
            </div>

            <!-- Kartu Pertanyaan -->
            <div class="my-auto py-3 flex flex-col gap-3.5">
                <div class="bg-slate-950/90 backdrop-blur-md border-2 border-pink-500/40 rounded-3xl p-5 shadow-xl">
                    <div class="text-xs font-bold uppercase tracking-wider text-rose-400 mb-1">Uji Pemahaman Materi</div>
                    <h2 id="practice-question" class="text-base sm:text-lg font-bold text-white leading-snug">
                        Pertanyaan latihan...
                    </h2>
                </div>

                <!-- 3 Pilihan Jawaban -->
                <div id="practice-options" class="flex flex-col gap-2.5"></div>
            </div>

            <!-- Pendamping Sparxie & Sparkle di Bawah -->
            <div class="flex items-center justify-between bg-slate-950/85 rounded-2xl border border-white/10 p-3 gap-3">
                <div id="practice-helper-left" class="w-14 h-14 shrink-0"></div>
                <p class="text-xs text-slate-300 text-center">
                    "Pilih jawaban yang paling pas! Kalau salah, tenang aja, aku dan Sparkle bakal kasih tahu alasannya!"
                </p>
                <div id="practice-helper-right" class="w-14 h-14 shrink-0"></div>
            </div>
        </section>

        <!-- =========================================================
             STAGE 3: PENILAIAN (MONSTER BATTLE QUIZ)
        ==================================
