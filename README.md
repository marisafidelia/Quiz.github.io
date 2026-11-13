<!DOCTYPE html>
<html lang="id" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SainsLab IX — Portal Belajar Interaktif IPA Kelas 9 SMP/MTs</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts: Plus Jakarta Sans & Inter -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Plus+Jakarta+Sans:wght@600;700;800&display=swap" rel="stylesheet">
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                        display: ['Plus Jakarta Sans', 'sans-serif'],
                    },
                    colors: {
                        brand: {
                            blue: '#0284c7',
                            teal: '#0d9488',
                            purple: '#7c3aed',
                            dark: '#0f172a'
                        }
                    }
                }
            }
        }
    </script>
    <style>
        /* Kustomisasi Scrollbar & Animasi Halus */
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f8fafc;
            color: #1e293b;
        }
        h1, h2, h3, h4, .font-display {
            font-family: 'Plus Jakarta Sans', sans-serif;
        }
        .glass-nav {
            background: rgba(255, 255, 255, 0.9);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
        }
        .fade-in {
            animation: fadeIn 0.35s ease-out forwards;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(8px); }
            to { opacity: 1; transform: translateY(0); }
        }
        /* Custom Range Slider untuk Lab Ohm */
        input[type=range] {
            -webkit-appearance: none;
            background: transparent;
        }
        input[type=range]::-webkit-slider-thumb {
            -webkit-appearance: none;
            height: 20px;
            width: 20px;
            border-radius: 50%;
            background: #0284c7;
            cursor: pointer;
            margin-top: -6px;
            box-shadow: 0 2px 6px rgba(2, 132, 199, 0.4);
            transition: transform 0.15s ease;
        }
        input[type=range]::-webkit-slider-thumb:hover {
            transform: scale(1.15);
        }
        input[type=range]::-webkit-slider-runnable-track {
            width: 100%;
            height: 8px;
            cursor: pointer;
            background: #e2e8f0;
            border-radius: 999px;
        }
    </style>
</head>
<body class="min-h-screen flex flex-col selection:bg-teal-500 selection:text-white">

    <!-- ==================== HEADER / NAVBAR ==================== -->
    <header class="sticky top-0 z-40 glass-nav border-b border-slate-200/80 shadow-sm">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-16 md:h-20">
                <!-- Logo & Judul -->
                <div class="flex items-center gap-3 cursor-pointer" onclick="switchTab('materi')">
                    <div class="w-10 h-10 md:w-11 md:h-11 rounded-xl bg-gradient-to-br from-sky-600 via-teal-500 to-purple-600 flex items-center justify-center text-white shadow-md">
                        <!-- Ikon Atom SVG -->
                        <svg class="w-6 h-6 animate-spin" style="animation-duration: 14s;" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
                            <circle cx="12" cy="12" r="2.5" fill="currentColor"/>
                            <ellipse cx="12" cy="12" rx="10" ry="4" transform="rotate(30 12 12)"/>
                            <ellipse cx="12" cy="12" rx="10" ry="4" transform="rotate(90 12 12)"/>
                            <ellipse cx="12" cy="12" rx="10" ry="4" transform="rotate(150 12 12)"/>
                        </svg>
                    </div>
                    <div>
                        <div class="flex items-center gap-2">
                            <span class="font-display font-extrabold text-xl md:text-2xl bg-gradient-to-r from-sky-700 via-teal-600 to-purple-700 bg-clip-text text-transparent">
                                SainsLab IX
                            </span>
                            <span class="hidden sm:inline-block text-[11px] font-bold uppercase tracking-wider px-2 py-0.5 rounded-full bg-teal-100 text-teal-800 border border-teal-200">
                                SMP / MTs
                            </span>
                        </div>
                        <p class="text-xs text-slate-500 hidden sm:block">Portal Belajar IPA Kelas 9 • Kurikulum Merdeka & K13</p>
                    </div>
                </div>

                <!-- Navigasi Desktop -->
                <nav class="hidden md:flex items-center gap-1.5 bg-slate-100/90 p-1.5 rounded-2xl border border-slate-200/70">
                    <button onclick="switchTab('materi')" id="nav-materi" class="nav-btn px-4 py-2 rounded-xl text-sm font-semibold transition-all flex items-center gap-2 bg-white text-sky-700 shadow-sm">
                        <span>📚</span> Materi Bab
                    </button>
                    <button onclick="switchTab('lab')" id="nav-lab" class="nav-btn px-4 py-2 rounded-xl text-sm font-semibold text-slate-600 hover:text-slate-900 transition-all flex items-center gap-2">
                        <span>🔬</span> Lab Virtual
                    </button>
                    <button onclick="switchTab('kuis')" id="nav-kuis" class="nav-btn px-4 py-2 rounded-xl text-sm font-semibold text-slate-600 hover:text-slate-900 transition-all flex items-center gap-2">
                        <span>🎯</span> Kuis Interaktif
                    </button>
                    <button onclick="switchTab('glosarium')" id="nav-glosarium" class="nav-btn px-4 py-2 rounded-xl text-sm font-semibold text-slate-600 hover:text-slate-900 transition-all flex items-center gap-2">
                        <span>📖</span> Glosarium
                    </button>
                </nav>

                <!-- Indikator Progres Belajar -->
                <div class="flex items-center gap-3">
                    <div class="text-right hidden lg:block">
                        <div class="text-xs font-medium text-slate-500">Bab Dipelajari</div>
                        <div class="text-sm font-bold text-teal-700"><span id="progress-count">0</span> / 10 Bab</div>
                    </div>
                    <div class="w-10 h-10 rounded-full bg-sky-50 border border-sky-200 flex items-center justify-center text-sky-700 font-bold text-xs shadow-inner" title="Progres Membaca Materi">
                        <span id="progress-percent">0%</span>
                    </div>
                </div>
            </div>

            <!-- Navigasi Mobile (Bottom/Sub-header Scrollable) -->
            <div class="flex md:hidden items-center gap-1.5 pb-3 overflow-x-auto no-scrollbar">
                <button onclick="switchTab('materi')" id="mob-materi" class="mob-btn flex-1 whitespace-nowrap px-3 py-2 rounded-xl text-xs font-bold bg-sky-600 text-white shadow-sm">
                    📚 Materi (10)
                </button>
                <button onclick="switchTab('lab')" id="mob-lab" class="mob-btn flex-1 whitespace-nowrap px-3 py-2 rounded-xl text-xs font-bold bg-slate-100 text-slate-600">
                    🔬 Lab Virtual
                </button>
                <button onclick="switchTab('kuis')" id="mob-kuis" class="mob-btn flex-1 whitespace-nowrap px-3 py-2 rounded-xl text-xs font-bold bg-slate-100 text-slate-600">
                    🎯 Kuis
                </button>
                <button onclick="switchTab('glosarium')" id="mob-glosarium" class="mob-btn flex-1 whitespace-nowrap px-3 py-2 rounded-xl text-xs font-bold bg-slate-100 text-slate-600">
                    📖 Glosarium
                </button>
            </div>
        </div>
    </header>

    <!-- ==================== KONTEN UTAMA ==================== -->
    <main class="flex-grow max-w-7xl w-full mx-auto px-4 sm:px-6 lg:px-8 py-6 md:py-8">

        <!-- ==================== TAB 1: BERANDA & MATERI ==================== -->
        <section id="tab-materi" class="tab-content fade-in">
            <!-- Hero Banner Ringkas -->
            <div class="relative overflow-hidden rounded-3xl bg-gradient-to-r from-sky-700 via-teal-600 to-purple-700 text-white p-6 sm:p-8 md:p-10 mb-8 shadow-lg">
                <div class="relative z-10 max-w-3xl">
                    <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-white/15 backdrop-blur-md text-xs font-semibold tracking-wide mb-3 border border-white/20">
                        <span>✨</span> Semester 1 & Semester 2 Lengkap
                    </div>
                    <h1 class="text-2xl sm:text-3xl md:text-4xl font-extrabold tracking-tight mb-3 leading-tight">
                        Eksplorasi Ilmu Pengetahuan Alam Kelas IX
                    </h1>
                    <p class="text-sky-100 text-sm sm:text-base leading-relaxed mb-6">
                        Pelajari 10 bab utama IPA SMP mulai dari Biologi sel & genetika, Fisika listrik & kemagnetan, hingga Kimia partikel & teknologi ramah lingkungan dengan ringkasan interaktif.
                    </p>
                    <div class="flex flex-wrap gap-3">
                        <button onclick="switchTab('lab')" class="px-5 py-2.5 rounded-xl bg-white text-sky-800 font-bold text-sm shadow-md hover:bg-sky-50 transition flex items-center gap-2">
                            <span>🧪</span> Coba Simulasi Lab Virtual
                        </button>
                        <button onclick="switchTab('kuis')" class="px-5 py-2.5 rounded-xl bg-purple-900/40 hover:bg-purple-900/60 text-white border border-white/30 font-semibold text-sm transition flex items-center gap-2">
                            <span>⚡</span> Uji Kemampuan (Kuis)
                        </button>
                    </div>
                </div>
                <!-- Dekorasi Latar Sains -->
                <div class="hidden lg:block absolute right-8 top-1/2 -translate-y-1/2 opacity-20 pointer-events-none">
                    <svg class="w-56 h-56" viewBox="0 0 200 200" fill="none" stroke="currentColor" stroke-width="3">
                        <path d="M70 30 H130 M85 30 V75 L45 155 C40 165 47 175 58 175 H142 C153 175 160 165 155 155 L115 75 V30" stroke-linecap="round" stroke-linejoin="round"/>
                        <path d="M62 125 Q100 110 138 125" stroke-linecap="round"/>
                        <circle cx="90" cy="148" r="6" fill="currentColor"/>
                        <circle cx="114" cy="140" r="4" fill="currentColor"/>
                        <circle cx="102" cy="158" r="5" fill="currentColor"/>
                    </svg>
                </div>
            </div>

            <!-- Filter Semester & Pencarian Cepat Materi -->
            <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-4 mb-6">
                <div class="flex items-center gap-2 flex-wrap">
                    <button onclick="filterSemester('all')" id="sem-all" class="sem-btn px-4 py-2 rounded-xl text-xs sm:text-sm font-bold bg-slate-800 text-white shadow-sm transition">
                        Semua Bab (10)
                    </button>
                    <button onclick="filterSemester(1)" id="sem-1" class="sem-btn px-4 py-2 rounded-xl text-xs sm:text-sm font-semibold bg-white text-slate-600 border border-slate-200 hover:bg-slate-50 transition">
                        Semester 1 (Bab 1–5)
                    </button>
                    <button onclick="filterSemester(2)" id="sem-2" class="sem-btn px-4 py-2 rounded-xl text-xs sm:text-sm font-semibold bg-white text-slate-600 border border-slate-200 hover:bg-slate-50 transition">
                        Semester 2 (Bab 6–10)
                    </button>
                </div>

                <div class="relative w-full sm:w-72">
                    <input type="text" id="search-materi" oninput="renderChapters()" placeholder="Cari topik bab (misal: Mendel, Listrik)..." 
                        class="w-full pl-9 pr-4 py-2 rounded-xl bg-white border border-slate-200 text-sm focus:outline-none focus:ring-2 focus:ring-sky-500 focus:border-transparent">
                    <svg class="w-4 h-4 text-slate-400 absolute left-3 top-1/2 -translate-y-1/2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"/>
                    </svg>
                </div>
            </div>

            <!-- Grid Kartu 10 Bab Materi -->
            <div id="chapters-grid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-5">
                <!-- Diisi dinamis oleh JavaScript -->
            </div>
        </section>

        <!-- ==================== TAB 2: LAB VIRTUAL MINI ==================== -->
        <section id="tab-lab" class="tab-content hidden fade-in">
            <div class="mb-6">
                <span class="text-xs font-bold uppercase tracking-wider text-purple-600 bg-purple-100 px-3 py-1 rounded-full">Praktikum Digital</span>
                <h2 class="text-2xl sm:text-3xl font-extrabold text-slate-900 mt-2">Laboratorium Virtual IPA Kelas IX</h2>
                <p class="text-slate-600 text-sm sm:text-base mt-1">Ubah variabel di bawah ini dan amati hasil percobaan secara langsung!</p>
            </div>

            <!-- Sub-Tab Pemilih Simulasi -->
            <div class="flex flex-wrap gap-3 mb-6">
                <button onclick="switchSim('mendel')" id="btn-sim-mendel" class="px-5 py-3 rounded-2xl font-bold text-sm flex items-center gap-2.5 bg-gradient-to-r from-teal-600 to-emerald-600 text-white shadow-md transition">
                    <span class="text-lg">🧬</span> Simulasi 1: Persilangan Monohibrid (Mendel)
                </button>
                <button onclick="switchSim('ohm')" id="btn-sim-ohm" class="px-5 py-3 rounded-2xl font-bold text-sm flex items-center gap-2.5 bg-white text-slate-700 border border-slate-200 hover:bg-slate-50 transition">
                    <span class="text-lg">⚡</span> Simulasi 2: Hukum Ohm & Daya Listrik
                </button>
            </div>

            <!-- SIMULASI 1: PERSILANGAN MONOHIBRID -->
            <div id="sim-mendel" class="bg-white rounded-3xl border border-slate-200/90 shadow-sm p-5 sm:p-8">
                <div class="flex flex-col lg:flex-row justify-between gap-6 border-b border-slate-100 pb-6 mb-6">
                    <div>
                        <h3 class="text-xl font-bold text-slate-900 flex items-center gap-2">
                            <span>🌱</span> Simulator Papan Punnett (Persilangan Monohibrid)
                        </h3>
                        <p class="text-sm text-slate-600 mt-1">
                            Pelajari Hukum I Mendel (Segregasi Bebas) dengan menyilangkan dua induk tanaman kacang kapri (<i>Pisum sativum</i>).
                        </p>
                    </div>
                    <!-- Pilihan Sifat Beda -->
                    <div class="flex flex-col sm:flex-row items-start sm:items-center gap-2 bg-slate-50 p-3 rounded-2xl border border-slate-200/70">
                        <label for="trait-select" class="text-xs font-bold text-slate-600 uppercase tracking-wide">Pilih Sifat Beda:</label>
                        <select id="trait-select" onchange="updatePunnett()" class="bg-white border border-slate-300 text-slate-800 text-sm font-semibold rounded-xl px-3 py-1.5 focus:ring-2 focus:ring-teal-500 outline-none">
                            <option value="tinggi">Tinggi Batang (T = Tinggi, t = Pendek)</option>
                            <option value="biji">Bentuk Biji (B = Bulat, b = Kisut)</option>
                            <option value="warna">Warna Bunga (M = Merah, m = Putih)</option>
                        </select>
                    </div>
                </div>

                <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 items-start">
                    <!-- Panel Kontrol Induk (Parental) -->
                    <div class="lg:col-span-5 space-y-5 bg-slate-50/80 p-5 rounded-2xl border border-slate-200/70">
                        <h4 class="font-bold text-slate-800 text-sm uppercase tracking-wider flex items-center gap-2">
                            <span>⚙️</span> Atur Genotipe Induk (Parental / P)
                        </h4>

                        <!-- Induk 1 -->
                        <div class="bg-white p-4 rounded-xl border border-slate-200 shadow-xs">
                            <label class="block text-xs font-bold text-sky-700 uppercase mb-1.5">Induk 1 (Jantan ♂)</label>
                            <select id="parent1" onchange="updatePunnett()" class="w-full bg-slate-50 border border-slate-300 rounded-xl px-3.5 py-2.5 text-sm font-bold text-slate-800 focus:ring-2 focus:ring-sky-500 outline-none">
                                <!-- Diisi JS -->
                            </select>
                            <p id="parent1-desc" class="text-xs text-slate-500 mt-2 font-medium"></p>
                        </div>

                        <!-- Tanda Silang -->
                        <div class="text-center font-extrabold text-slate-400 text-lg">✕ (Disilangkan dengan)</div>

                        <!-- Induk 2 -->
                        <div class="bg-white p-4 rounded-xl border border-slate-200 shadow-xs">
                            <label class="block text-xs font-bold text-purple-700 uppercase mb-1.5">Induk 2 (Betina ♀)</label>
                            <select id="parent2" onchange="updatePunnett()" class="w-full bg-slate-50 border border-slate-300 rounded-xl px-3.5 py-2.5 text-sm font-bold text-slate-800 focus:ring-2 focus:ring-purple-500 outline-none">
                                <!-- Diisi JS -->
                            </select>
                            <p id="parent2-desc" class="text-xs text-slate-500 mt-2 font-medium"></p>
                        </div>

                        <!-- Info Gamet -->
                        <div class="bg-teal-50 border border-teal-200 rounded-xl p-3.5 text-xs text-teal-900">
                            <span class="font-bold block mb-1">💡 Pembentukan Gamet (Meiosis):</span>
                            <span id="gamete-info">Gamet Induk 1: T, T | Gamet Induk 2: t, t</span>
                        </div>
                    </div>

                    <!-- Hasil Papan Punnett & Rasio -->
                    <div class="lg:col-span-7 space-y-6">
                        <!-- Tabel Punnett Square -->
                        <div>
                            <h4 class="font-bold text-slate-800 text-sm uppercase tracking-wider mb-3">📊 Papan Punnett (Keturunan F1)</h4>
                            <div class="overflow-hidden rounded-2xl border-2 border-slate-200 shadow-xs">
                                <table class="w-full text-center border-collapse">
                                    <thead>
                                        <tr class="bg-slate-100 text-slate-700 font-bold text-sm">
                                            <th class="p-3 border-b border-r border-slate-200 bg-slate-200/70 w-1/5">Gamet ♂ \ ♀</th>
                                            <th id="p2-g1" class="p-3 border-b border-r border-slate-200 text-purple-700 text-base w-2/5">t</th>
                                            <th id="p2-g2" class="p-3 border-b border-slate-200 text-purple-700 text-base w-2/5">t</th>
                                        </tr>
                                    </thead>
                                    <tbody class="divide-y divide-slate-200 text-sm sm:text-base">
                                        <tr>
                                            <th id="p1-g1" class="p-4 border-r border-slate-200 bg-slate-100 text-sky-700 font-bold text-base">T</th>
                                            <td id="cell-00" class="p-4 border-r border-slate-200 transition-colors"></td>
                                            <td id="cell-01" class="p-4 transition-colors"></td>
                                        </tr>
                                        <tr>
                                            <th id="p1-g2" class="p-4 border-r border-slate-200 bg-slate-100 text-sky-700 font-bold text-base">T</th>
                                            <td id="cell-10" class="p-4 border-r border-slate-200 transition-colors"></td>
                                            <td id="cell-11" class="p-4 transition-colors"></td>
                                        </tr>
                                    </tbody>
                                </table>
                            </div>
                        </div>

                        <!-- Hasil Perbandingan Rasio -->
                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                            <div class="bg-sky-50/80 border border-sky-200 rounded-2xl p-4">
                                <div class="text-xs font-bold uppercase tracking-wider text-sky-800 mb-2">🧬 Perbandingan Genotipe</div>
                                <div id="genotype-ratio" class="space-y-1.5 text-sm font-semibold text-slate-800">
                                    <!-- Diisi JS -->
                                </div>
                            </div>
                            <div class="bg-purple-50/80 border border-purple-200 rounded-2xl p-4">
                                <div class="text-xs font-bold uppercase tracking-wider text-purple-800 mb-2">🌿 Perbandingan Fenotipe</div>
                                <div id="phenotype-ratio" class="space-y-1.5 text-sm font-semibold text-slate-800">
                                    <!-- Diisi JS -->
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- SIMULASI 2: HUKUM OHM & DAYA LISTRIK -->
            <div id="sim-ohm" class="hidden bg-white rounded-3xl border border-slate-200/90 shadow-sm p-5 sm:p-8">
                <div class="border-b border-slate-100 pb-5 mb-6">
                    <h3 class="text-xl font-bold text-slate-900 flex items-center gap-2">
                        <span>🔌</span> Simulator Rangkaian Listrik DC (Hukum Ohm & Daya)
                    </h3>
                    <p class="text-sm text-slate-600 mt-1">
                        Geser pengaturan <b>Tegangan (V)</b> dan <b>Hambatan (R)</b> untuk mengamati perubahan kecepatan aliran arus listrik (I) serta nyala lampu.
                    </p>
                </div>

                <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 items-center">
                    <!-- Kontrol Slider -->
                    <div class="lg:col-span-5 space-y-6 bg-slate-50 p-5 rounded-2xl border border-slate-200/80">
                        <!-- Slider Tegangan (V) -->
                        <div>
                            <div class="flex justify-between items-center mb-2">
                                <label for="slider-v" class="text-sm font-bold text-slate-800">Tegangan Sumber (V)</label>
                                <span class="px-3 py-1 rounded-lg bg-sky-100 text-sky-800 font-extrabold text-sm"><span id="val-v">12</span> Volt</span>
                            </div>
                            <input type="range" id="slider-v" min="1" max="24" step="1" value="12" oninput="updateOhmLab()" class="w-full">
                            <div class="flex justify-between text-[11px] text-slate-400 mt-1">
                                <span>1 V (Kecil)</span>
                                <span>12 V (Aki)</span>
                                <span>24 V (Besar)</span>
                            </div>
                        </div>

                        <!-- Slider Hambatan (R) -->
                        <div>
                            <div class="flex justify-between items-center mb-2">
                                <label for="slider-r" class="text-sm font-bold text-slate-800">Hambatan Lampu (R)</label>
                                <span class="px-3 py-1 rounded-lg bg-purple-100 text-purple-800 font-extrabold text-sm"><span id="val-r">6</span> Ohm (Ω)</span>
                            </div>
                            <input type="range" id="slider-r" min="2" max="20" step="1" value="6" oninput="updateOhmLab()" class="w-full">
                            <div class="flex justify-between text-[11px] text-slate-400 mt-1">
                                <span>2 Ω (Rendah)</span>
                                <span>10 Ω</span>
                                <span>20 Ω (Tinggi)</span>
                            </div>
                        </div>

                        <!-- Kartu Hasil Rumus -->
                        <div class="grid grid-cols-2 gap-3 pt-2">
                            <div class="bg-white p-3.5 rounded-xl border border-teal-200 shadow-xs">
                                <div class="text-[11px] font-bold text-slate-500 uppercase">Kuat Arus (I = V / R)</div>
                                <div class="text-xl sm:text-2xl font-extrabold text-teal-600 mt-0.5"><span id="res-i">2.00</span> <span class="text-sm font-bold">A</span></div>
                            </div>
                            <div class="bg-white p-3.5 rounded-xl border border-amber-200 shadow-xs">
                                <div class="text-[11px] font-bold text-slate-500 uppercase">Daya Listrik (P = V × I)</div>
                                <div class="text-xl sm:text-2xl font-extrabold text-amber-600 mt-0.5"><span id="res-p">24.0</span> <span class="text-sm font-bold">Watt</span></div>
                            </div>
                        </div>

                        <div class="bg-sky-50 border border-sky-200 rounded-xl p-3.5 text-xs text-sky-900 leading-relaxed">
                            <b>Kesimpulan Hukum Ohm:</b> Kuat arus listrik (<i>I</i>) berbanding lurus dengan tegangan (<i>V</i>) dan berbanding terbalik dengan hambatan (<i>R</i>).
                        </div>
                    </div>

                    <!-- Kanvas Animasi Rangkaian Listrik -->
                    <div class="lg:col-span-7 flex flex-col items-center">
                        <div class="w-full bg-slate-900 rounded-2xl p-4 shadow-inner border border-slate-700 relative">
                            <div class="flex justify-between items-center text-xs text-slate-400 mb-2 px-1">
                                <span class="flex items-center gap-1.5"><span class="w-2.5 h-2.5 rounded-full bg-sky-400 inline-block"></span> Aliran Elektron / Muatan</span>
                                <span id="lamp-status" class="font-bold text-amber-400">Nyala Lampu: Sedang</span>
                            </div>
                            <canvas id="ohm-canvas" class="w-full h-64 sm:h-72 rounded-xl bg-slate-950 block"></canvas>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- ==================== TAB 3: KUIS INTERAKTIF ==================== -->
        <section id="tab-kuis" class="tab-content hidden fade-in">
            <div class="max-w-3xl mx-auto">
                <div class="mb-6 text-center">
                    <span class="text-xs font-bold uppercase tracking-wider text-teal-700 bg-teal-100 px-3 py-1 rounded-full">Evaluasi Mandiri</span>
                    <h2 class="text-2xl sm:text-3xl font-extrabold text-slate-900 mt-2">Kuis Latihan IPA Kelas IX</h2>
                    <p class="text-slate-600 text-sm sm:text-base mt-1">Uji pemahamanmu pada 10 soal pilihan ganda lengkap dengan pembahasan instan!</p>
                </div>

                <!-- Kontainer Kuis Aktif -->
                <div id="quiz-container" class="bg-white rounded-3xl border border-slate-200 shadow-sm p-6 sm:p-8">
                    <!-- Header Progress Kuis -->
                    <div class="flex items-center justify-between text-xs sm:text-sm font-bold text-slate-600 mb-2">
                        <span>Soal <span id="quiz-current-num" class="text-sky-700">1</span> dari <span id="quiz-total-num">10</span></span>
                        <span class="px-3 py-1 rounded-full bg-purple-100 text-purple-800" id="quiz-topic-badge">Bab 1: Reproduksi</span>
                        <span>Skor: <span id="quiz-live-score" class="text-teal-600">0</span></span>
                    </div>
                    <div class="w-full h-2.5 bg-slate-100 rounded-full overflow-hidden mb-6">
                        <div id="quiz-progress-bar" class="h-full bg-gradient-to-r from-sky-500 via-teal-500 to-purple-600 transition-all duration-300" style="width: 10%;"></div>
                    </div>

                    <!-- Pertanyaan -->
                    <h3 id="quiz-question" class="text-base sm:text-lg font-bold text-slate-900 leading-relaxed mb-5">
                        Memuat pertanyaan...
                    </h3>

                    <!-- Pilihan Jawaban -->
                    <div id="quiz-options" class="space-y-3 mb-6">
                        <!-- Diisi dinamis oleh JS -->
                    </div>

                    <!-- Kotak Umpan Balik & Pembahasan -->
                    <div id="quiz-feedback" class="hidden rounded-2xl p-4 mb-6 text-sm leading-relaxed border">
                        <div id="quiz-feedback-title" class="font-extrabold mb-1"></div>
                        <p id="quiz-feedback-text"></p>
                    </div>

                    <!-- Tombol Navigasi Soal -->
                    <div class="flex justify-end">
                        <button id="quiz-next-btn" onclick="nextQuestion()" class="hidden px-6 py-3 rounded-xl bg-sky-600 hover:bg-sky-700 text-white font-bold text-sm shadow-md transition flex items-center gap-2">
                            <span>Soal Berikutnya</span>
                            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"/></svg>
                        </button>
                    </div>
                </div>

                <!-- Kontainer Hasil Akhir Kuis -->
                <div id="quiz-result" class="hidden bg-white rounded-3xl border border-slate-200 shadow-sm p-8 text-center">
                    <div id="result-emoji" class="text-6xl mb-4">🏆</div>
                    <h3 class="text-2xl sm:text-3xl font-extrabold text-slate-900 mb-2">Kuis Selesai!</h3>
                    <p id="result-predicate" class="text-base font-bold text-teal-600 mb-6">Predikat: Sangat Baik</p>

                    <div class="inline-flex items-center justify-center w-32 h-32 rounded-full bg-gradient-to-br from-sky-50 to-teal-50 border-4 border-teal-500 mb-6 shadow-inner">
                        <div>
                            <div class="text-3xl font-extrabold text-slate-900" id="result-score">80</div>
                            <div class="text-xs font-bold text-slate-500 uppercase">Nilai Akhir</div>
                        </div>
                    </div>

                    <p id="result-summary" class="text-slate-600 text-sm sm:text-base max-w-md mx-auto mb-8">
                        Kamu berhasil menjawab 8 dari 10 soal dengan benar.
                    </p>

                    <div class="flex flex-wrap justify-center gap-3">
                        <button onclick="restartQuiz()" class="px-6 py-3 rounded-xl bg-gradient-to-r from-sky-600 to-teal-600 hover:opacity-95 text-white font-bold text-sm shadow-md transition">
                            🔄 Ulangi Kuis
                        </button>
                        <button onclick="switchTab('materi')" class="px-6 py-3 rounded-xl bg-slate-100 hover:bg-slate-200 text-slate-800 font-bold text-sm transition">
                            📚 Pelajari Materi Lagi
                        </button>
                    </div>
                </div>
            </div>
        </section>

        <!-- ==================== TAB 4: GLOSARIUM IPA ==================== -->
        <section id="tab-glosarium" class="tab-content hidden fade-in">
            <div class="max-w-4xl mx-auto">
                <div class="mb-6">
                    <span class="text-xs font-bold uppercase tracking-wider text-sky-700 bg-sky-100 px-3 py-1 rounded-full">Kamus Sains</span>
                    <h2 class="text-2xl sm:text-3xl font-extrabold text-slate-900 mt-2">Glosarium Istilah IPA Kelas IX</h2>
                    <p class="text-slate-600 text-sm sm:text-base mt-1">Cari definisi istilah-istilah penting Biologi, Fisika, dan Kimia kelas 9 secara cepat.</p>
                </div>

                <!-- Kotak Pencarian Glosarium -->
                <div class="relative mb-6">
                    <input type="text" id="search-glossary" oninput="renderGlossary()" placeholder="Ketik istilah yang dicari (contoh: Mitosis, Alel, Coulomb, Transgenik, Ion)..." 
                        class="w-full pl-11 pr-4 py-3.5 rounded-2xl bg-white border border-slate-200 shadow-xs text-sm sm:text-base focus:outline-none focus:ring-2 focus:ring-teal-500">
                    <svg class="w-5 h-5 text-slate-400 absolute left-4 top-1/2 -translate-y-1/2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"/>
                    </svg>
                </div>

                <!-- Daftar Kartu Istilah -->
                <div id="glossary-list" class="grid grid-cols-1 md:grid-cols-2 gap-4">
                    <!-- Diisi dinamis oleh JS -->
                </div>
            </div>
        </section>

    </main>

    <!-- ==================== MODAL DETAIL MODUL MATERI ==================== -->
    <div id="chapter-modal" class="fixed inset-0 z-50 hidden bg-slate-900/60 backdrop-blur-xs flex items-center justify-center p-4 overflow-y-auto">
        <div class="bg-white rounded-3xl max-w-3xl w-full max-h-[90vh] flex flex-col shadow-2xl border border-slate-200 overflow-hidden fade-in">
            <!-- Header Modal -->
            <div id="modal-header" class="p-5 sm:p-6 bg-gradient-to-r from-sky-700 to-teal-600 text-white flex justify-between items-start gap-4">
                <div>
                    <span id="modal-badge" class="inline-block text-xs font-bold uppercase tracking-wider bg-white/20 px-2.5 py-0.5 rounded-full mb-2">Semester 1 • Bab 1</span>
                    <h3 id="modal-title" class="text-xl sm:text-2xl font-extrabold leading-snug">Judul Bab</h3>
                </div>
                <button onclick="closeModal()" class="p-2 rounded-xl bg-white/15 hover:bg-white/25 text-white transition" aria-label="Tutup">
                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M6 18L18 6M6 6l12 12"/></svg>
                </button>
            </div>

            <!-- Isi Modal Scrollable -->
            <div class="p-5 sm:p-7 overflow-y-auto space-y-6 text-slate-700 text-sm sm:text-base leading-relaxed">
                <!-- Ringkasan Konsep -->
                <div>
                    <h4 class="font-bold text-slate-900 text-base flex items-center gap-2 mb-2">
                        <span class="w-7 h-7 rounded-lg bg-sky-100 text-sky-700 flex items-center justify-center text-sm">📌</span>
                        Konsep Inti & Ringkasan Materi
                    </h4>
                    <p id="modal-summary" class="text-slate-600"></p>
                </div>

                <!-- Poin-Poin Penting -->
                <div class="bg-slate-50 rounded-2xl p-4 sm:p-5 border border-slate-200/80">
                    <h4 class="font-bold text-slate-900 text-base flex items-center gap-2 mb-3">
                        <span class="w-7 h-7 rounded-lg bg-teal-100 text-teal-700 flex items-center justify-center text-sm">✅</span>
                        Poin Kunci yang Wajib Diingat
                    </h4>
                    <ul id="modal-points" class="space-y-2 text-sm text-slate-700 list-disc pl-5">
                        <!-- Diisi JS -->
                    </ul>
                </div>

                <!-- Rumus Utama (Jika Ada) -->
                <div id="modal-formula-box" class="bg-purple-50/80 rounded-2xl p-4 sm:p-5 border border-purple-200">
                    <h4 class="font-bold text-purple-950 text-base flex items-center gap-2 mb-2">
                        <span class="w-7 h-7 rounded-lg bg-purple-200 text-purple-800 flex items-center justify-center text-sm">📐</span>
                        Rumus & Persamaan Penting
                    </h4>
                    <div id="modal-formula" class="font-mono text-sm sm:text-base font-bold text-purple-900 bg-white px-4 py-3 rounded-xl border border-purple-100 shadow-2xs"></div>
                </div>

                <!-- Contoh Soal & Pembahasan -->
                <div class="bg-amber-50/70 rounded-2xl p-4 sm:p-5 border border-amber-200">
                    <h4 class="font-bold text-amber-950 text-base flex items-center gap-2 mb-2">
                        <span class="w-7 h-7 rounded-lg bg-amber-200 text-amber-800 flex items-center justify-center text-sm">💡</span>
                        Contoh Soal & Pembahasan Singkat
                    </h4>
                    <p id="modal-example-q" class="font-semibold text-slate-900 text-sm mb-2"></p>
                    <div class="text-sm text-slate-700 bg-white/90 p-3.5 rounded-xl border border-amber-200/70">
                        <span class="font-bold text-teal-700">Pembahasan: </span>
                        <span id="modal-example-a"></span>
                    </div>
                </div>
            </div>

            <!-- Footer Modal -->
            <div class="p-4 sm:px-6 bg-slate-50 border-t border-slate-200 flex flex-wrap justify-between items-center gap-3">
                <button id="modal-sim-link" onclick="" class="hidden px-4 py-2 rounded-xl bg-purple-600 hover:bg-purple-700 text-white font-bold text-xs sm:text-sm transition">
                    🔬 Buka Simulasi Terkait
                </button>
                <div class="flex items-center gap-2 ml-auto">
                    <button id="btn-mark-done" onclick="toggleChapterDone()" class="px-4 py-2 rounded-xl bg-teal-600 hover:bg-teal-700 text-white font-bold text-xs sm:text-sm transition">
                        ✓ Tandai Sudah Dipelajari
                    </button>
                    <button onclick="closeModal()" class="px-4 py-2 rounded-xl bg-slate-200 hover:bg-slate-300 text-slate-800 font-bold text-xs sm:text-sm transition">
                        Tutup
                    </button>
                </div>
            </div>
        </div>
    </div>

    <!-- ==================== FOOTER ==================== -->
    <footer class="bg-white border-t border-slate-200 mt-12 py-6">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex flex-col sm:flex-row justify-between items-center gap-4 text-xs sm:text-sm text-slate-500">
            <div class="flex items-center gap-2 font-semibold text-slate-700">
                <span>🧪 SainsLab IX</span>
                <span>•</span>
                <span>Media Pembelajaran Interaktif IPA SMP Kelas 9</span>
            </div>
            <div>Dirancang untuk mendukung belajar mandiri siswa Indonesia 🇮🇩</div>
        </div>
    </footer>

    <!-- ==================== JAVASCRIPT LOGIKA & DATA ==================== -->
    <script>
        // ==================== 1. DATA 10 BAB MATERI IPA KELAS IX ====================
        const chaptersData = [
            {
                id: 1,
                semester: 1,
                icon: "🧬",
                color: "from-sky-600 to-blue-700",
                badgeColor: "bg-sky-100 text-sky-800",
                title: "Sistem Reproduksi pada Manusia",
                shortDesc: "Pembelahan sel (mitosis & meiosis), struktur organ reproduksi, spermatogenesis, oogenesis, menstruasi, serta kesehatan reproduksi.",
                summary: "Setiap makhluk hidup bereproduksi untuk melestarikan jenisnya. Pada manusia, proses ini diawali dengan pembelahan sel tubuh (mitosis) untuk pertumbuhan dan pembelahan sel kelamin (meiosis) yang menghasilkan sel gamet haploid (n).",
                points: [
                    "Mitosis menghasilkan 2 sel anakan yang identik secara genetik dengan induknya (diploid / 2n), terjadi pada sel tubuh.",
                    "Meiosis menghasilkan 4 sel anakan dengan jumlah kromosom setengah dari induknya (haploid / n), terjadi pada pembentukan sel kelamin.",
                    "Organ reproduksi pria meliputi testis (penghasil sperma & hormon testosteron), epididimis, vas deferens, dan penis.",
                    "Organ reproduksi wanita meliputi ovarium (penghasil ovum, estrogen, progesteron), tuba fallopi (tempat fertilisasi), uterus (rahim), dan vagina.",
                    "Menstruasi terjadi apabila sel telur tidak dibuahi sehingga dinding rahim (endometrium) luruh bersama darah."
                ],
                formula: "Sel Induk (2n) ──[Meiosis]──▶ 4 Sel Gamet (n)  |  Sperma (n) + Ovum (n) ──[Fertilisasi]──▶ Zigot (2n)",
                exampleQ: "Di bagian organ reproduksi wanita manakah peristiwa fertilisasi (pembuahan sel telur oleh sperma) umumnya terjadi?",
                exampleA: "Fertilisasi terjadi di Tuba Fallopi (oviduk / saluran telur). Setelah terbentuk zigot, zigot akan membelah sambil bergerak menuju uterus (rahim) untuk tertanam (implantasi)."
            },
            {
                id: 2,
                semester: 1,
                icon: "🌱",
                color: "from-teal-600 to-emerald-700",
                badgeColor: "bg-teal-100 text-teal-800",
                title: "Sistem Perkembangbiakan Tumbuhan & Hewan",
                shortDesc: "Reproduksi vegetatif & generatif pada Angiospermae, penyerbukan, pembuahan ganda, serta metamorfosis dan teknologi reproduksi hewan.",
                summary: "Tumbuhan dan hewan memiliki strategi perkembangbiakan vegetatif (aseksual, tanpa peleburan gamet) dan generatif (seksual, melalui peleburan gamet jantan dan betina) untuk beradaptasi terhadap lingkungannya.",
                points: [
                    "Vegetatif alami tumbuhan: rizoma (jahe), stolon/geragih (stroberi), umbi lapis (bawang merah), umbi batang (kentang), tunas adventif (cocor bebek).",
                    "Vegetatif buatan tumbuhan: mencangkok, menyambung (enten), menempel (okulasi), setek, dan merunduk.",
                    "Pembuahan ganda pada Angiospermae: Inti generatif 1 + ovum → zigot (2n); Inti generatif 2 + inti kandung lembaga sekunder → endosperma (3n).",
                    "Perkembangbiakan hewan: Ovipar (bertelur), Vivipar (melahirkan), dan Ovovivipar (bertelur-melahirkan, misal: hiu, kadal).",
                    "Metamorfosis sempurna melewati tahap pupa/kepompong (telur → larva → pupa → imago), sedangkan tidak sempurna tidak melewati fase pupa."
                ],
                formula: "Inti Generatif 1 (n) + Ovum (n) = Zigot (2n)   |   Inti Generatif 2 (n) + IKLS (2n) = Endosperma (3n)",
                exampleQ: "Mengapa pembuahan pada tumbuhan berbiji tertutup (Angiospermae) disebut sebagai pembuahan ganda?",
                exampleA: "Karena terjadi dua kali peleburan inti sel: pertama menghasilkan zigot (calon individu baru), dan kedua menghasilkan endosperma (cadangan makanan bagi embrio)."
            },
            {
                id: 3,
                semester: 1,
                icon: "🧪",
                color: "from-purple-600 to-indigo-700",
                badgeColor: "bg-purple-100 text-purple-800",
                title: "Pewarisan Sifat pada Makhluk Hidup",
                shortDesc: "Materi genetik (DNA, gen, kromosom), Hukum I & II Mendel, persilangan monohibrid & dihibrid, serta kelainan genetik.",
                summary: "Sifat-sifat orang tua diwariskan kepada keturunannya melalui materi genetik (DNA) yang tersusun dalam kromosom. Gregor Mendel merumuskan hukum pewarisan sifat melalui percobaan kacang kapri.",
                points: [
                    "Genotipe adalah susunan gen yang tidak tampak dari luar (contoh: BB, Bb, bb), sedangkan Fenotipe adalah sifat yang tampak (contoh: Biji Bulat).",
                    "Alel dominan (huruf kapital) menutupi ekspresi alel resesif (huruf kecil) pada keadaan heterozigot (Bb).",
                    "Hukum I Mendel (Segregasi): Pada pembentukan gamet, pasangan alel memisah secara bebas. Rasio fenotipe F2 monohibrid dominan penuh = 3 : 1.",
                    "Hukum II Mendel (Asortasi Bebas): Alel dari gen yang berbeda mengelompok secara bebas. Rasio fenotipe F2 dihibrid = 9 : 3 : 3 : 1.",
                    "Kelainan genetik terpaut kromosom X antara lain buta warna dan hemofilia, sedangkan albino terpaut autosom resesif."
                ],
                formula: "Rasio Fenotipe F2 Monohibrid = 3 Dominan : 1 Resesif   |   Rasio Fenotipe F2 Dihibrid = 9 : 3 : 3 : 1",
                exampleQ: "Persilangan kacang kapri berbiji bulat heterozigot (Bb) dengan sesamanya (Bb) menghasilkan 400 tanaman. Berapa perkiraan tanaman berbiji kisut (bb)?",
                exampleA: "Dari persilangan Bb × Bb diperoleh genotipe BB (1), Bb (2), dan bb (1). Peluang biji kisut (bb) adalah 1/4 × 400 = 100 tanaman.",
                simAction: "mendel"
            },
            {
                id: 4,
                semester: 1,
                icon: "⚡",
                color: "from-amber-500 to-orange-600",
                badgeColor: "bg-amber-100 text-amber-800",
                title: "Listrik Statis dalam Kehidupan Sehari-hari",
                shortDesc: "Muatan listrik, interaksi antarmuatan, Hukum Coulomb, medan listrik, potensial listrik, dan kelistrikan pada sel saraf.",
                summary: "Listrik statis mempelajari kumpulan muatan listrik dalam keadaan diam. Benda bermuatan positif jika kekurangan elektron, dan bermuatan negatif jika kelebihan elektron.",
                points: [
                    "Muatan sejenis tolak-menolak (+ dengan + atau - dengan -), sedangkan muatan berlawanan jenis tarik-menarik (+ dengan -).",
                    "Menggosok penggaris plastik dengan kain wol membuat elektron pindah dari wol ke plastik sehingga plastik bermuatan negatif.",
                    "Hukum Coulomb: Besar gaya tarik/tolak sebanding dengan perkalian kedua muatan dan berbanding terbalik dengan kuadrat jaraknya.",
                    "Sel saraf (neuron) menghantarkan impuls listrik melalui perubahan beda potensial ion Na+ dan K+ di sepanjang akson.",
                    "Hewan penghasil listrik statis/tegangan tinggi antara lain belut listrik, ikan pari listrik, dan hiu kepala martil."
                ],
                formula: "F = k · (q₁ · q₂) / r²    (k = 9 × 10⁹ N·m²/C²)",
                exampleQ: "Dua benda bermuatan masing-masing +4 μC dan -6 μC terpisah sejauh 2 cm. Jika jaraknya diperbesar menjadi 4 cm (2 kali semula), bagaimana gaya Coulomb-nya?",
                exampleA: "Karena F berbanding terbalik dengan r², jika jarak menjadi 2 kali lipat, maka gaya Coulomb berkurang menjadi (1/2)² = 1/4 kali gaya semula."
            },
            {
                id: 5,
                semester: 1,
                icon: "🔌",
                color: "from-cyan-600 to-sky-700",
                badgeColor: "bg-cyan-100 text-cyan-800",
                title: "Listrik Dinamis dalam Kehidupan Sehari-hari",
                shortDesc: "Arus listrik, Hukum Ohm, hambatan kawat, rangkaian seri & paralel, Hukum Kirchhoff, serta energi dan daya listrik.",
                summary: "Listrik dinamis membahas muatan listrik yang mengalir dalam rangkaian tertutup. Arus listrik konvensional mengalir dari potensial tinggi (+) ke rendah (-), berlawanan dengan arah aliran elektron.",
                points: [
                    "Hukum Ohm menyatakan kuat arus (I) sebanding dengan tegangan (V) dan berbanding terbalik dengan hambatan (R).",
                    "Rangkaian Seri: Arus sama di semua titik (I_total = I₁ = I₂), tegangan terbagi, hambatan pengganti R_s = R₁ + R₂.",
                    "Rangkaian Paralel: Tegangan sama di setiap cabang (V_total = V₁ = V₂), arus terbagi, hambatan pengganti 1/R_p = 1/R₁ + 1/R₂.",
                    "Hukum I Kirchhoff: Jumlah arus yang masuk ke titik percabangan sama dengan jumlah arus yang keluar (∑I_masuk = ∑I_keluar).",
                    "Penggunaan energi listrik di rumah diukur dalam satuan kWh (kilowatt-jam)."
                ],
                formula: "I = V / R   |   P = V · I = I² · R   |   W = P · t = V · I · t",
                exampleQ: "Sebuah setrika listrik memiliki hambatan 44 Ω dipasang pada tegangan 220 V. Berapa kuat arus dan daya listrik setrika tersebut?",
                exampleA: "Kuat arus I = V / R = 220 / 44 = 5 Ampere. Daya listrik P = V × I = 220 × 5 = 1.100 Watt.",
                simAction: "ohm"
            },
            {
                id: 6,
                semester: 2,
                icon: "🧲",
                color: "from-rose-600 to-red-700",
                badgeColor: "bg-rose-100 text-rose-800",
                title: "Kemagnetan dan Pemanfaatannya",
                shortDesc: "Sifat kutub magnet, feromagnetik/paramagnetik/diamagnetik, elektromagnet, Gaya Lorentz, induksi elektromagnetik, dan transformator.",
                summary: "Magnet memiliki dua kutub (Utara dan Selatan). Selain bahan magnetik alami, arus listrik dapat menghasilkan medan magnet (elektromagnet) dan sebaliknya perubahan medan magnet dapat menghasilkan listrik.",
                points: [
                    "Bahan magnetik: Feromagnetik (ditarik kuat, misal besi, baja, nikel, kobalt), Paramagnetik (ditarik lemah, misal aluminium), Diamagnetik (ditolak lemah, misal emas, bismut).",
                    "Cara membuat magnet: Menggosok searah, induksi magnet, dan mengalirkan arus listrik DC (elektromagnet).",
                    "Gaya Lorentz bekerja pada kawat berarus di dalam medan magnet (F = B · I · L), diterapkan pada motor listrik.",
                    "Induksi elektromagnetik (Faraday) menghasilkan GGL induksi akibat perubahan fluks magnet, diterapkan pada generator dan dinamo.",
                    "Transformator (Trafo): Step-Up menaikkan tegangan (Ns > Np), sedangkan Step-Down menurunkan tegangan (Ns < Np)."
                ],
                formula: "F = B · I · L    |    Vp / Vs = Np / Ns = Is / Ip",
                exampleQ: "Sebuah transformator memiliki 200 lilitan primer dan 1.000 lilitan sekunder. Jika tegangan input 22 V, berapa tegangan keluarannya?",
                exampleA: "Vs = (Ns / Np) × Vp = (1.000 / 200) × 22 V = 5 × 22 V = 110 Volt (Trafo Step-Up)."
            },
            {
                id: 7,
                semester: 2,
                icon: "🧫",
                color: "from-emerald-600 to-green-700",
                badgeColor: "bg-emerald-100 text-emerald-800",
                title: "Bioteknologi",
                shortDesc: "Perbedaan bioteknologi konvensional (fermentasi) dan modern (rekayasa genetika, kultur jaringan, kloning, bayi tabung).",
                summary: "Bioteknologi memanfaatkan makhluk hidup (bakteri, jamur, virus) atau bagian-bagiannya untuk menghasilkan produk dan jasa yang bermanfaat bagi kesejahteraan manusia.",
                points: [
                    "Bioteknologi Konvensional menggunakan mikroorganisme secara langsung melalui fermentasi dengan peralatan sederhana (tempe, tapai, yoghurt, keju, kecap).",
                    "Mikroorganisme penting: Rhizopus oryzae (tempe), Saccharomyces cerevisiae (tapai & roti), Lactobacillus bulgaricus (yoghurt), Neurospora crassa (oncom).",
                    "Bioteknologi Modern melibatkan rekayasa genetika (DNA rekombinan), kultur jaringan tumbuhan, kloning, dan antibodi monoklonal.",
                    "Contoh produk transgenik: Tanaman kapas Bt tahan hama, padi Golden Rice kaya vitamin A, dan bakteri penghasil hormon insulin manusia.",
                    "Dampak bioteknologi perlu diwaspadai terkait potensi alergi, berkurangnya keanekaragaman hayati, dan pencemaran biologis."
                ],
                formula: "Glukosa (C₆H₁₂O₆) ──[Saccharomyces]──▶ 2 Etanol (C₂H₅OH) + 2 CO₂ + Energi",
                exampleQ: "Jamur apa yang berperan penting dalam proses fermentasi kedelai menjadi tempe, dan apa fungsinya?",
                exampleA: "Jamur Rhizopus oryzae. Hifa jamur ini mengikat butir-butir kedelai menjadi padat serta menghasilkan enzim protease yang memecah protein kompleks menjadi asam amino yang mudah dicerna."
            },
            {
                id: 8,
                semester: 2,
                icon: "⚛️",
                color: "from-indigo-600 to-violet-700",
                badgeColor: "bg-indigo-100 text-indigo-800",
                title: "Partikel Penyusun Benda dan Makhluk Hidup",
                shortDesc: "Atom (proton, neutron, elektron), nomor atom & nomor massa, konfigurasi elektron, ion, molekul unsur & senyawa, serta sifat bahan.",
                summary: "Semua materi di alam semesta tersusun atas partikel-partikel sangat kecil berupa atom, ion, dan molekul. Susunan partikel menentukan sifat fisika dan kimia suatu benda.",
                points: [
                    "Atom terdiri atas inti atom (proton bermuatan + dan neutron netral) yang dikelilingi elektron bermuatan negatif (-) pada kulit atom.",
                    "Nomor Atom (Z) = jumlah proton = jumlah elektron (pada atom netral). Nomor Massa (A) = jumlah proton + neutron.",
                    "Ion adalah atom bermuatan listrik: Kation (ion positif, melepas elektron, misal Na+) dan Anion (ion negatif, menangkap elektron, misal Cl-).",
                    "Molekul unsur tersusun dari atom sejenis (O₂, H₂, N₂), sedangkan molekul senyawa tersusun dari atom berbeda jenis (H₂O, CO₂).",
                    "Intan dan grafit sama-sama tersusun atas atom karbon (C), namun berbeda sifat karena perbedaan ikatan dan struktur kristalnya."
                ],
                formula: "Jumlah Proton = Z   |   Jumlah Neutron = A - Z   |   Konfigurasi Kulit: K(2), L(8), M(18), N(32)",
                exampleQ: "Suatu atom Natrium dilambangkan dengan ²³₁₁Na. Tentukan jumlah proton, elektron, dan neutron pada atom netral tersebut!",
                exampleA: "Nomor atom Z = 11 (Proton = 11, Elektron = 11). Nomor massa A = 23, maka Neutron = A - Z = 23 - 11 = 12 neutron."
            },
            {
                id: 9,
                semester: 2,
                icon: "🌍",
                color: "from-amber-700 to-yellow-800",
                badgeColor: "bg-yellow-100 text-yellow-900",
                title: "Tanah dan Keberlangsungan Kehidupan",
                shortDesc: "Peran tanah, organisme tanah, proses pembentukan tanah, lapisan horizon tanah, serta upaya menjaga kelestarian tanah.",
                summary: "Tanah merupakan komponen abiotik vital yang menyediakan nutrisi bagi tumbuhan, menjadi habitat miliaran mikroorganisme pengurai, serta menyaring dan menyimpan air tanah.",
                points: [
                    "Pelapukan batuan menjadi tanah terjadi melalui 3 cara: Pelapukan fisika (suhu/angin), kimiawi (air hujan asam), dan biologis (lumut kerak/akar).",
                    "Lapisan tanah dari atas ke bawah: Horizon O (humus organik), Horizon A (topsoil kaya mineral & humus), Horizon B (subsoil), Horizon C (batuan lapuk), Horizon R (batuan induk).",
                    "Organisme tanah (cacing tanah, bakteri, jamur) berperan menguraikan bahan organik, menggemburkan tanah (aerasi), dan mengikat nitrogen.",
                    "Erosi tanah dapat dicegah dengan reboisasi, pembuatan terasering di lahan miring, dan rotasi tanaman (crop rotation)."
                ],
                formula: "Urutan Lapisan Tanah: Horizon O (Atas) ➔ A (Topsoil) ➔ B (Subsoil) ➔ C ➔ R (Batuan Induk)",
                exampleQ: "Mengapa pembuatan terasering (sengkedan) sangat dianjurkan pada lahan pertanian di daerah pegunungan yang miring?",
                exampleA: "Terasering mengurangi kemiringan lereng sehingga memperlambat aliran air hujan di permukaan, meningkatkan resapan air, dan mencegah erosi lapisan topsoil yang subur."
            },
            {
                id: 10,
                semester: 2,
                icon: "♻️",
                color: "from-teal-500 to-cyan-700",
                badgeColor: "bg-teal-100 text-teal-900",
                title: "Teknologi Ramah Lingkungan",
                shortDesc: "Prinsip green technology, energi terbarukan (surya, angin, air, biogas, biofuel), kendaraan listrik, dan biopori.",
                summary: "Teknologi ramah lingkungan adalah bentuk penerapan teknologi yang memperhatikan prinsip pelestarian lingkungan, efisiensi sumber daya, dan meminimalkan limbah serta emisi karbon.",
                points: [
                    "Prinsip teknologi ramah lingkungan: Refine (bahan ramah lingkungan), Reduce (kurangi limbah), Reuse (guna ulang), Recycle (daur ulang), Recovery (perolehan kembali).",
                    "Sumber energi terbarukan: Panel surya (sel fotovoltaik), PLTB (turbin angin), PLTA (air), Geotermal (panas bumi), Biofuel (biodiesel & bioetanol), dan Biogas (gas metana dari limbah kotoran).",
                    "Teknologi transportasi ramah lingkungan meliputi mobil listrik (EV), mobil hidrogen (fuel cell), dan kereta maglev.",
                    "Lubang resapan biopori dan fitoremediasi (tanaman penyerap polutan seperti eceng gondok) membantu menjaga kualitas air dan tanah."
                ],
                formula: "Prinsip 5R: Refine • Reduce • Reuse • Recycle • Recovery",
                exampleQ: "Bagaimana cara kerja biogas sebagai salah satu contoh teknologi ramah lingkungan di bidang energi?",
                exampleA: "Biogas dihasilkan dari fermentasi anaerob (tanpa oksigen) limbah organik atau kotoran ternak oleh bakteri metanogen yang menghasilkan gas metana (CH₄) sebagai bahan bakar pengganti LPG."
            }
        ];

        // ==================== 2. DATA KUIS INTERAKTIF (10 SOAL) ====================
        const quizQuestions = [
            {
                topic: "Bab 1: Sistem Reproduksi",
                question: "Perhatikan pernyataan berikut! (1) Menghasilkan 2 sel anakan, (2) Terjadi pada sel tubuh, (3) Jumlah kromosom sel anakan setengah dari induknya, (4) Bertujuan untuk menghasilkan sel kelamin. Ciri pembelahan MEIOSIS ditunjukkan oleh nomor...",
                options: [
                    "A. (1) dan (2)",
                    "B. (1) dan (3)",
                    "C. (2) dan (4)",
                    "D. (3) dan (4)"
                ],
                correct: 3,
                explanation: "Pembelahan meiosis terjadi pada pembentukan sel kelamin (gamet) dan mereduksi jumlah kromosom dari diploid (2n) menjadi haploid (n) atau setengah dari induknya."
            },
            {
                topic: "Bab 2: Reproduksi Tumbuhan",
                question: "Pada proses pembuahan ganda tumbuhan berbiji tertutup (Angiospermae), peleburan antara inti sel generatif 2 dengan inti kandung lembaga sekunder akan menghasilkan...",
                options: [
                    "A. Zigot yang bersifat diploid (2n)",
                    "B. Endosperma yang bersifat triploid (3n)",
                    "C. Bakal biji yang bersifat haploid (n)",
                    "D. Kulit biji pelindung embrio"
                ],
                correct: 1,
                explanation: "Inti generatif 1 (n) + ovum (n) → zigot (2n). Sedangkan inti generatif 2 (n) + inti kandung lembaga sekunder (2n) → endosperma (3n) sebagai cadangan makanan."
            },
            {
                topic: "Bab 3: Pewarisan Sifat",
                question: "Tanaman mangga berbuah besar rasa asam (BBmm) disilangkan dengan tanaman mangga berbuah kecil rasa manis (bbMM). Jika keturunan F1 (BbMm) disilangkan sesamanya, berapakah rasio fenotipe buah besar rasa manis pada F2?",
                options: [
                    "A. 9 / 16",
                    "B. 3 / 16",
                    "C. 1 / 16",
                    "D. 12 / 16"
                ],
                correct: 0,
                explanation: "Berdasarkan Hukum II Mendel pada persilangan dihibrid heterozigot (BbMm × BbMm), rasio fenotipe F2 adalah 9 (B_M_ : Besar Manis) : 3 (B_mm) : 3 (bbM_) : 1 (bbmm)."
            },
            {
                topic: "Bab 4: Listrik Statis",
                question: "Sebuah penggaris plastik digosok-gosokkan pada rambut yang kering, kemudian didekatkan pada potongan kertas kecil sehingga kertas tertarik. Peristiwa ini terjadi karena...",
                options: [
                    "A. Elektron berpindah dari penggaris ke rambut sehingga penggaris bermuatan positif",
                    "B. Proton berpindah dari rambut ke penggaris sehingga penggaris bermuatan positif",
                    "C. Elektron berpindah dari rambut ke penggaris sehingga penggaris bermuatan negatif",
                    "D. Proton berpindah dari penggaris ke rambut sehingga penggaris bermuatan negatif"
                ],
                correct: 2,
                explanation: "Proton tidak dapat berpindah. Saat digosok, elektron berpindah dari rambut ke penggaris plastik sehingga penggaris kelebihan elektron (bermuatan negatif)."
            },
            {
                topic: "Bab 5: Listrik Dinamis",
                question: "Sebuah lampu memiliki hambatan 15 Ω dihubungkan dengan sumber tegangan 30 Volt. Besar kuat arus listrik yang mengalir dan daya lampu tersebut berturut-turut adalah...",
                options: [
                    "A. 0,5 A dan 15 Watt",
                    "B. 2 A dan 60 Watt",
                    "C. 2 A dan 30 Watt",
                    "D. 450 A dan 15 Watt"
                ],
                correct: 1,
                explanation: "Menurut Hukum Ohm: I = V / R = 30 V / 15 Ω = 2 Ampere. Daya listrik: P = V × I = 30 V × 2 A = 60 Watt."
            },
            {
                topic: "Bab 6: Kemagnetan",
                question: "Sebuah transformator step-down memiliki jumlah lilitan primer 1.000 lilitan dan lilitan sekunder 250 lilitan. Jika tegangan primernya 220 Volt, maka tegangan keluarannya adalah...",
                options: [
                    "A. 880 Volt",
                    "B. 110 Volt",
                    "C. 55 Volt",
                    "D. 22 Volt"
                ],
                correct: 2,
                explanation: "Menggunakan persamaan trafo: Vs = (Ns / Np) × Vp = (250 / 1.000) × 220 V = (1/4) × 220 V = 55 Volt."
            },
            {
                topic: "Bab 7: Bioteknologi",
                question: "Pasangan produk bioteknologi konvensional dan mikroorganisme yang berperan dalam pembuatannya yang paling tepat adalah...",
                options: [
                    "A. Tapai ketan — Rhizopus oryzae",
                    "B. Yoghurt — Lactobacillus bulgaricus",
                    "C. Tempe — Saccharomyces cerevisiae",
                    "D. Kecap — Acetobacter xylinum"
                ],
                correct: 1,
                explanation: "Yoghurt dibuat dari fermentasi susu oleh bakteri Lactobacillus bulgaricus atau Streptococcus thermophilus. Tempe menggunakan Rhizopus oryzae, dan tapai menggunakan Saccharomyces cerevisiae."
            },
            {
                topic: "Bab 8: Partikel Materi",
                question: "Diketahui lambang unsur Aluminium adalah ²⁷₁₃Al. Apabila atom Aluminium melepaskan 3 elektron membentuk ion Al³⁺, maka jumlah elektron pada ion tersebut adalah...",
                options: [
                    "A. 10 elektron",
                    "B. 13 elektron",
                    "C. 14 elektron",
                    "D. 16 elektron"
                ],
                correct: 0,
                explanation: "Atom netral ²⁷₁₃Al memiliki 13 proton dan 13 elektron. Karena melepaskan 3 elektron menjadi Al³⁺, sisa elektronnya adalah 13 - 3 = 10 elektron."
            },
            {
                topic: "Bab 9: Tanah & Kehidupan",
                question: "Lapisan tanah paling atas yang berwarna gelap, kaya akan bahan organik (humus), serta menjadi tempat utama tumbuhnya akar tanaman disebut...",
                options: [
                    "A. Horizon R (Batuan Induk)",
                    "B. Horizon C (Batuan Lapuk)",
                    "C. Horizon B (Subsoil)",
                    "D. Horizon O dan A (Topsoil)"
                ],
                correct: 3,
                explanation: "Horizon O dan A (topsoil) merupakan lapisan teratas yang paling subur karena mengandung banyak humus dan aktivitas mikroorganisme pengurai."
            },
            {
                topic: "Bab 10: Teknologi Ramah Lingkungan",
                question: "Pemanfaatan kotoran ternak untuk menghasilkan gas metana (CH₄) sebagai bahan bakar memasak di pedesaan merupakan penerapan teknologi ramah lingkungan berupa...",
                options: [
                    "A. Sel Fotovoltaik",
                    "B. Biogas",
                    "C. Geotermal",
                    "D. Biopori"
                ],
                correct: 1,
                explanation: "Biogas adalah gas yang dihasilkan oleh aktivitas anaerobik (fermentasi tanpa oksigen) bahan-bahan organik seperti kotoran hewan dengan hasil utama gas metana (CH₄)."
            }
        ];

        // ==================== 3. DATA GLOSARIUM IPA KELAS IX ====================
        const glossaryData = [
            { term: "Alel", category: "Genetika", def: "Pasangan gen yang terletak pada lokus yang sama pada kromosom homolog dan menentukan sifat alternatif (misal: T dan t)." },
            { term: "Anion", category: "Partikel Materi", def: "Ion bermuatan negatif yang terbentuk karena suatu atom menangkap atau menerima satu atau lebih elektron (contoh: Cl⁻)." },
            { term: "Bioteknologi", category: "Bioteknologi", def: "Pemanfaatan prinsip-prinsip ilmiah dan makhluk hidup (mikroorganisme) untuk menghasilkan produk dan jasa bagi manusia." },
            { term: "Elektromagnet", category: "Kemagnetan", def: "Magnet sementara yang dibuat dengan cara mengalirkan arus listrik searah melalui kumparan kawat yang dililitkan pada inti besi." },
            { term: "Endosperma", category: "Reproduksi Tumbuhan", def: "Jaringan triploid (3n) pada biji tumbuhan berbunga yang berfungsi sebagai cadangan makanan bagi embrio selama perkecambahan." },
            { term: "Fenotipe", category: "Genetika", def: "Sifat fisik atau karakteristik yang tampak dan dapat diamati pada suatu organisme hasil interaksi genotipe dengan lingkungan." },
            { term: "Fertilisasi", category: "Reproduksi", def: "Proses peleburan inti sel sperma (haploid) dengan inti sel telur/ovum (haploid) membentuk zigot (diploid)." },
            { term: "Feromagnetik", category: "Kemagnetan", def: "Bahan yang ditarik sangat kuat oleh magnet dan dapat dibuat menjadi magnet permanen, seperti besi, baja, nikel, dan kobalt." },
            { term: "Genotipe", category: "Genetika", def: "Susunan genetik suatu individu yang tidak tampak secara langsung dan biasanya disimbolkan dengan pasangan huruf (misal: BB, Bb, bb)." },
            { term: "Hukum Coulomb", category: "Listrik Statis", def: "Hukum yang menyatakan gaya listrik antara dua muatan sebanding dengan besar kedua muatan dan berbanding terbalik dengan kuadrat jaraknya." },
            { term: "Hukum Ohm", category: "Listrik Dinamis", def: "Hukum yang menyatakan kuat arus listrik yang mengalir dalam penghantar sebanding dengan beda potensial (tegangan) dan berbanding terbalik dengan hambatannya." },
            { term: "Induksi Elektromagnetik", category: "Kemagnetan", def: "Peristiwa timbulnya gaya gerak listrik (GGL) dan arus listrik pada penghantar akibat perubahan jumlah garis gaya magnet yang memotong kumparan." },
            { term: "Kation", category: "Partikel Materi", def: "Ion bermuatan positif yang terbentuk karena suatu atom netral melepaskan satu atau lebih elektron (contoh: Na⁺, Ca²⁺)." },
            { term: "Kultur Jaringan", category: "Bioteknologi", def: "Teknik perbanyakan tumbuhan secara vegetatif dengan menumbuhkan sel/jaringan tanaman dalam media nutrisi steril berdasarkan sifat totipotensi." },
            { term: "Meiosis", category: "Reproduksi", def: "Pembelahan sel yang menghasilkan 4 sel anakan dengan jumlah kromosom setengah dari sel induk (reduksi kromosom), terjadi pada pembentukan gamet." },
            { term: "Mitosis", category: "Reproduksi", def: "Pembelahan sel tubuh yang menghasilkan 2 sel anakan dengan jumlah dan susunan kromosom identik dengan sel induknya." },
            { term: "Oogenesis", category: "Reproduksi", def: "Proses pembentukan dan pematangan sel telur (ovum) di dalam ovarium wanita." },
            { term: "Sel Fotovoltaik", category: "Teknologi Lingkungan", def: "Komponen utama pada panel surya yang mengubah energi cahaya matahari secara langsung menjadi energi listrik." },
            { term: "Spermatogenesis", category: "Reproduksi", def: "Proses pembentukan dan pematangan sel sperma di dalam tubulus seminiferus pada testis pria." },
            { term: "Transgenik", category: "Bioteknologi", def: "Organisme yang susunan genetiknya telah dimodifikasi dengan menyisipkan gen dari organisme lain untuk memperoleh sifat unggul." }
        ];

        // ==================== STATE APLIKASI ====================
        let currentSemesterFilter = 'all';
        let completedChapters = JSON.parse(localStorage.getItem('sainslab9_done') || '[]');
        let activeModalChapterId = null;

        // State Kuis
        let currentQuizIdx = 0;
        let quizScore = 0;
        let quizAnswered = false;

        // State Animasi Ohm
        let ohmAnimId = null;
        let electrons = [];

        // ==================== FUNGSI NAVIGASI TAB ====================
        function switchTab(tabName) {
            // Sembunyikan semua tab
            document.querySelectorAll('.tab-content').forEach(el => el.classList.add('hidden'));
            // Tampilkan tab yang dipilih
            document.getElementById(`tab-${tabName}`).classList.remove('hidden');

            // Update style tombol desktop
            document.querySelectorAll('.nav-btn').forEach(btn => {
                btn.classList.remove('bg-white', 'text-sky-700', 'shadow-sm');
                btn.classList.add('text-slate-600');
            });
            const activeNav = document.getElementById(`nav-${tabName}`);
            if (activeNav) {
                activeNav.classList.add('bg-white', 'text-sky-700', 'shadow-sm');
                activeNav.classList.remove('text-slate-600');
            }

            // Update style tombol mobile
            document.querySelectorAll('.mob-btn').forEach(btn => {
                btn.classList.remove('bg-sky-600', 'text-white', 'shadow-sm');
                btn.classList.add('bg-slate-100', 'text-slate-600');
            });
            const activeMob = document.getElementById(`mob-${tabName}`);
            if (activeMob) {
                activeMob.classList.add('bg-sky-600', 'text-white', 'shadow-sm');
                activeMob.classList.remove('bg-slate-100', 'text-slate-600');
            }

            // Inisialisasi khusus jika masuk tab Lab
            if (tabName === 'lab') {
                initPunnettOptions();
                resizeOhmCanvas();
            }
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        // ==================== FUNGSI MATERI & MODAL ====================
        function updateProgressUI() {
            const count = completedChapters.length;
            const percent = Math.round((count / chaptersData.length) * 100);
            document.getElementById('progress-count').textContent = count;
            document.getElementById('progress-percent').textContent = `${percent}%`;
        }

        function filterSemester(sem) {
            currentSemesterFilter = sem;
            document.querySelectorAll('.sem-btn').forEach(btn => {
                btn.classList.remove('bg-slate-800', 'text-white', 'shadow-sm');
                btn.classList.add('bg-white', 'text-slate-600', 'border', 'border-slate-200');
            });
            const activeBtn = document.getElementById(`sem-${sem}`);
            activeBtn.classList.add('bg-slate-800', 'text-white', 'shadow-sm');
            activeBtn.classList.remove('bg-white', 'text-slate-600', 'border', 'border-slate-200');
            renderChapters();
        }

        function renderChapters() {
            const grid = document.getElementById('chapters-grid');
            const query = document.getElementById('search-materi').value.toLowerCase().trim();

            const filtered = chaptersData.filter(ch => {
                const matchSem = currentSemesterFilter === 'all' || ch.semester === currentSemesterFilter;
                const matchQuery = ch.title.toLowerCase().includes(query) || ch.shortDesc.toLowerCase().includes(query);
                return matchSem && matchQuery;
            });

            if (filtered.length === 0) {
                grid.innerHTML = `
                    <div class="col-span-full text-center py-12 bg-white rounded-3xl border border-slate-200">
                        <div class="text-4xl mb-2">🔍</div>
                        <p class="font-bold text-slate-700">Materi tidak ditemukan</p>
                        <p class="text-sm text-slate-500">Coba gunakan kata kunci lain.</p>
                    </div>`;
                return;
            }

            grid.innerHTML = filtered.map(ch => {
                const isDone = completedChapters.includes(ch.id);
                return `
                <article onclick="openChapterModal(${ch.id})" class="group bg-white rounded-3xl border ${isDone ? 'border-teal-300 ring-1 ring-teal-200' : 'border-slate-200/90'} p-5 sm:p-6 shadow-xs hover:shadow-lg hover:-translate-y-1 transition-all duration-200 cursor-pointer flex flex-col justify-between">
                    <div>
                        <div class="flex items-center justify-between gap-2 mb-4">
                            <span class="text-xs font-bold px-3 py-1 rounded-full ${ch.badgeColor}">
                                Semester ${ch.semester} • Bab ${ch.id}
                            </span>
                            ${isDone 
                                ? `<span class="text-xs font-bold text-teal-700 bg-teal-50 border border-teal-200 px-2.5 py-0.5 rounded-full">✓ Dipelajari</span>` 
                                : `<span class="text-xs font-medium text-slate-400 group-hover:text-sky-600 transition">Baca Modul →</span>`
                            }
                        </div>
                        <div class="flex items-start gap-3.5 mb-3">
                            <div class="w-12 h-12 rounded-2xl bg-gradient-to-br ${ch.color} text-white flex items-center justify-center text-2xl shrink-0 shadow-sm group-hover:scale-105 transition-transform">
                                ${ch.icon}
                            </div>
                            <h3 class="font-bold text-slate-900 text-base sm:text-lg leading-snug group-hover:text-sky-700 transition-colors">
                                ${ch.title}
                            </h3>
                        </div>
                        <p class="text-xs sm:text-sm text-slate-600 leading-relaxed line-clamp-3">
                            ${ch.shortDesc}
                        </p>
                    </div>

                    <div class="mt-5 pt-3.5 border-t border-slate-100 flex items-center justify-between text-xs font-bold text-sky-700">
                        <span>Buka Ringkasan & Contoh Soal</span>
                        <span class="w-7 h-7 rounded-full bg-sky-50 group-hover:bg-sky-600 group-hover:text-white flex items-center justify-center transition-colors">
                            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"/></svg>
                        </span>
                    </div>
                </article>`;
            }).join('');
        }

        function openChapterModal(id) {
            const ch = chaptersData.find(item => item.id === id);
            if (!ch) return;

            activeModalChapterId = id;
            document.getElementById('modal-header').className = `p-5 sm:p-6 bg-gradient-to-r ${ch.color} text-white flex justify-between items-start gap-4`;
            document.getElementById('modal-badge').textContent = `Semester ${ch.semester} • Bab ${ch.id}`;
            document.getElementById('modal-title').textContent = `${ch.icon} ${ch.title}`;
            document.getElementById('modal-summary').textContent = ch.summary;

            document.getElementById('modal-points').innerHTML = ch.points.map(pt => `<li>${pt}</li>`).join('');
            document.getElementById('modal-formula').textContent = ch.formula;
            document.getElementById('modal-example-q').textContent = ch.exampleQ;
            document.getElementById('modal-example-a').textContent = ch.exampleA;

            // Tombol simulasi terkait jika ada
            const simBtn = document.getElementById('modal-sim-link');
            if (ch.simAction) {
                simBtn.classList.remove('hidden');
                simBtn.onclick = () => {
                    closeModal();
                    switchTab('lab');
                    switchSim(ch.simAction);
                };
            } else {
                simBtn.classList.add('hidden');
            }

            updateModalDoneButton();
            document.getElementById('chapter-modal').classList.remove('hidden');
            document.body.style.overflow = 'hidden';
        }

        function closeModal() {
            document.getElementById('chapter-modal').classList.add('hidden');
            document.body.style.overflow = '';
        }

        function updateModalDoneButton() {
            const btn = document.getElementById('btn-mark-done');
            const isDone = completedChapters.includes(activeModalChapterId);
            if (isDone) {
                btn.textContent = "✓ Sudah Dipelajari (Batalkan)";
                btn.className = "px-4 py-2 rounded-xl bg-teal-100 text-teal-800 border border-teal-300 font-bold text-xs sm:text-sm transition";
            } else {
                btn.textContent = "✓ Tandai Sudah Dipelajari";
                btn.className = "px-4 py-2 rounded-xl bg-teal-600 hover:bg-teal-700 text-white font-bold text-xs sm:text-sm transition";
            }
        }

        function toggleChapterDone() {
            if (!activeModalChapterId) return;
            const idx = completedChapters.indexOf(activeModalChapterId);
            if (idx === -1) {
                completedChapters.push(activeModalChapterId);
            } else {
                completedChapters.splice(idx, 1);
            }
            localStorage.setItem('sainslab9_done', JSON.stringify(completedChapters));
            updateModalDoneButton();
            updateProgressUI();
            renderChapters();
        }

        // ==================== FUNGSI LAB VIRTUAL ====================
        function switchSim(simType) {
            const mendelDiv = document.getElementById('sim-mendel');
            const ohmDiv = document.getElementById('sim-ohm');
            const btnMendel = document.getElementById('btn-sim-mendel');
            const btnOhm = document.getElementById('btn-sim-ohm');

            if (simType === 'mendel') {
                mendelDiv.classList.remove('hidden');
                ohmDiv.classList.add('hidden');
                btnMendel.className = "px-5 py-3 rounded-2xl font-bold text-sm flex items-center gap-2.5 bg-gradient-to-r from-teal-600 to-emerald-600 text-white shadow-md transition";
                btnOhm.className = "px-5 py-3 rounded-2xl font-bold text-sm flex items-center gap-2.5 bg-white text-slate-700 border border-slate-200 hover:bg-slate-50 transition";
            } else {
                mendelDiv.classList.add('hidden');
                ohmDiv.classList.remove('hidden');
                btnOhm.className = "px-5 py-3 rounded-2xl font-bold text-sm flex items-center gap-2.5 bg-gradient-to-r from-sky-600 to-purple-600 text-white shadow-md transition";
                btnMendel.className = "px-5 py-3 rounded-2xl font-bold text-sm flex items-center gap-2.5 bg-white text-slate-700 border border-slate-200 hover:bg-slate-50 transition";
                resizeOhmCanvas();
            }
        }

        // --- Simulasi 1: Papan Punnett Mendel ---
        const traitsConfig = {
            tinggi: { domChar: 'T', recChar: 't', domName: 'Batang Tinggi', recName: 'Batang Pendek', emojiDom: '🌲', emojiRec: '🌱' },
            biji:   { domChar: 'B', recChar: 'b', domName: 'Biji Bulat', recName: 'Biji Kisut', emojiDom: '🟡', emojiRec: '🫘' },
            warna:  { domChar: 'M', recChar: 'm', domName: 'Bunga Merah', recName: 'Bunga Putih', emojiDom: '🌺', emojiRec: '🤍' }
        };

        function initPunnettOptions() {
            const traitKey = document.getElementById('trait-select').value;
            const cfg = traitsConfig[traitKey];
            const D = cfg.domChar;
            const r = cfg.recChar;

            const optionsHTML = `
                <option value="${D}${D}">${D}${D} — Homozigot Dominan (${cfg.domName})</option>
                <option value="${D}${r}" selected>${D}${r} — Heterozigot (${cfg.domName})</option>
                <option value="${r}${r}">${r}${r} — Homozigot Resesif (${cfg.recName})</option>
            `;

            const p1 = document.getElementById('parent1');
            const p2 = document.getElementById('parent2');
            const prev1 = p1.selectedIndex >= 0 ? p1.selectedIndex : 1;
            const prev2 = p2.selectedIndex >= 0 ? p2.selectedIndex : 1;

            p1.innerHTML = optionsHTML;
            p2.innerHTML = optionsHTML;
            p1.selectedIndex = prev1;
            p2.selectedIndex = prev2;

            updatePunnett();
        }

        function updatePunnett() {
            const traitKey = document.getElementById('trait-select').value;
            const cfg = traitsConfig[traitKey];
            const D = cfg.domChar;
            const r = cfg.recChar;

            const p1Select = document.getElementById('parent1');
            const p2Select = document.getElementById('parent2');

            // Jika karakter alel berubah akibat ganti sifat beda, perbarui opsi
            if (!p1Select.value.includes(D) && !p1Select.value.includes(r)) {
                initPunnettOptions();
                return;
            }

            const g1 = p1Select.value; // misal "Tt"
            const g2 = p2Select.value; // misal "Tt"

            const p1Gametes = [g1[0], g1[1]];
            const p2Gametes = [g2[0], g2[1]];

            document.getElementById('p1-g1').textContent = p1Gametes[0];
            document.getElementById('p1-g2').textContent = p1Gametes[1];
            document.getElementById('p2-g1').textContent = p2Gametes[0];
            document.getElementById('p2-g2').textContent = p2Gametes[1];

            document.getElementById('parent1-desc').textContent = `Fenotipe: ${g1.includes(D) ? cfg.domName : cfg.recName}`;
            document.getElementById('parent2-desc').textContent = `Fenotipe: ${g2.includes(D) ? cfg.domName : cfg.recName}`;
            document.getElementById('gamete-info').textContent = `Gamet Induk 1: (${p1Gametes[0]}) dan (${p1Gametes[1]})  |  Gamet Induk 2: (${p2Gametes[0]}) dan (${p2Gametes[1]})`;

            const genotypeCounts = {};
            let domPhenoCount = 0;
            let recPhenoCount = 0;

            for (let row = 0; row < 2; row++) {
                for (let col = 0; col < 2; col++) {
                    // Urutkan huruf kapital di depan (misal t + T -> Tt)
                    const pair = [p1Gametes[row], p2Gametes[col]].sort((a, b) => {
                        if (a === a.toUpperCase() && b === b.toLowerCase()) return -1;
                        if (a === a.toLowerCase() && b === b.toUpperCase()) return 1;
                        return 0;
                    }).join('');

                    genotypeCounts[pair] = (genotypeCounts[pair] || 0) + 1;
                    const isDominant = pair.includes(D);
                    if (isDominant) domPhenoCount++; else recPhenoCount++;

                    const cell = document.getElementById(`cell-${row}${col}`);
                    cell.className = `p-3 sm:p-4 border-slate-200 ${col === 0 ? 'border-r' : ''} ${isDominant ? 'bg-teal-50/70' : 'bg-amber-50/70'}`;
                    cell.innerHTML = `
                        <div class="text-lg sm:text-xl font-extrabold ${isDominant ? 'text-teal-800' : 'text-amber-800'}">${pair}</div>
                        <div class="text-xs font-medium text-slate-600 mt-0.5">${isDominant ? cfg.emojiDom + ' ' + cfg.domName : cfg.emojiRec + ' ' + cfg.recName}</div>
                    `;
                }
            }

            // Render Rasio Genotipe
            const genoHTML = Object.entries(genotypeCounts).map(([geno, count]) => {
                const pct = (count / 4) * 100;
                return `<div class="flex justify-between items-center bg-white px-3 py-1.5 rounded-lg border border-sky-100">
                    <span class="font-bold text-sky-900">${geno}</span>
                    <span class="text-xs font-bold text-slate-600">${count}/4 (${pct}%)</span>
                </div>`;
            }).join('');
            document.getElementById('genotype-ratio').innerHTML = genoHTML;

            // Render Rasio Fenotipe
            let phenoHTML = '';
            if (domPhenoCount > 0) {
                phenoHTML += `<div class="flex justify-between items-center bg-white px-3 py-1.5 rounded-lg border border-purple-100">
                    <span class="font-bold text-teal-800">${cfg.emojiDom} ${cfg.domName}</span>
                    <span class="text-xs font-bold text-slate-600">${domPhenoCount}/4 (${(domPhenoCount/4)*100}%)</span>
                </div>`;
            }
            if (recPhenoCount > 0) {
                phenoHTML += `<div class="flex justify-between items-center bg-white px-3 py-1.5 rounded-lg border border-purple-100">
                    <span class="font-bold text-amber-800">${cfg.emojiRec} ${cfg.recName}</span>
                    <span class="text-xs font-bold text-slate-600">${recPhenoCount}/4 (${(recPhenoCount/4)*100}%)</span>
                </div>`;
            }
            document.getElementById('phenotype-ratio').innerHTML = phenoHTML;
        }

        // --- Simulasi 2: Hukum Ohm & Animasi Rangkaian ---
        function updateOhmLab() {
            const V = parseFloat(document.getElementById('slider-v').value);
            const R = parseFloat(document.getElementById('slider-r').value);
            const I = V / R;
            const P = V * I;

            document.getElementById('val-v').textContent = V;
            document.getElementById('val-r').textContent = R;
            document.getElementById('res-i').textContent = I.toFixed(2);
            document.getElementById('res-p').textContent = P.toFixed(1);

            const statusEl = document.getElementById('lamp-status');
            if (P < 10) {
                statusEl.textContent = "Nyala Lampu: Redup";
                statusEl.className = "font-bold text-slate-400";
            } else if (P < 45) {
                statusEl.textContent = "Nyala Lampu: Terang Normal";
                statusEl.className = "font-bold text-amber-400";
            } else {
                statusEl.textContent = "Nyala Lampu: Sangat Terang!";
                statusEl.className = "font-bold text-yellow-300";
            }
        }

        function resizeOhmCanvas() {
            const canvas = document.getElementById('ohm-canvas');
            if (!canvas || canvas.offsetParent === null) return;
            const rect = canvas.getBoundingClientRect();
            canvas.width = rect.width;
            canvas.height = rect.height;
            initElectrons();
            if (!ohmAnimId) animateOhmCircuit();
        }

        function initElectrons() {
            electrons = [];
            const numParticles = 16;
            for (let i = 0; i < numParticles; i++) {
                electrons.push({ progress: i / numParticles });
            }
        }

        function animateOhmCircuit() {
            const canvas = document.getElementById('ohm-canvas');
            if (!canvas) return;
            const ctx = canvas.getContext('2d');
            const w = canvas.width;
            const h = canvas.height;

            const V = parseFloat(document.getElementById('slider-v').value);
            const R = parseFloat(document.getElementById('slider-r').value);
            const I = V / R;
            const P = V * I;

            ctx.clearRect(0, 0, w, h);

            // Koordinat kotak rangkaian kabel
            const padX = Math.max(45, w * 0.14);
            const padY = Math.max(42, h * 0.18);
            const left = padX, right = w - padX, top = padY, bottom = h - padY;
            const boxW = right - left;
            const boxH = bottom - top;
            const perimeter = 2 * (boxW + boxH);

            // Gambar Kabel Rangkaian
            ctx.strokeStyle = '#334155';
            ctx.lineWidth = 6;
            ctx.lineJoin = 'round';
            ctx.strokeRect(left, top, boxW, boxH);

            // Gerakkan & Gambar Titik Elektron sesuai kuat arus I
            const speed = Math.min(0.018, I * 0.0014);
            electrons.forEach(p => {
                p.progress = (p.progress + speed) % 1;
                const dist = p.progress * perimeter;
                let px = left, py = top;

                if (dist < boxW) {
                    px = left + dist; py = top;
                } else if (dist < boxW + boxH) {
                    px = right; py = top + (dist - boxW);
                } else if (dist < 2 * boxW + boxH) {
                    px = right - (dist - (boxW + boxH)); py = bottom;
                } else {
                    px = left; py = bottom - (dist - (2 * boxW + boxH));
                }

                ctx.beginPath();
                ctx.arc(px, py, 4.5, 0, Math.PI * 2);
                ctx.fillStyle = '#38bdf8';
                ctx.shadowColor = '#0284c7';
                ctx.shadowBlur = 8;
                ctx.fill();
                ctx.shadowBlur = 0;
            });

            // Gambar Baterai di Sisi Kiri
            const midY = (top + bottom) / 2;
            ctx.fillStyle = '#0f172a';
            ctx.fillRect(left - 18, midY - 22, 36, 44);
            // Kutub Panjang (+)
            ctx.strokeStyle = '#ef4444';
            ctx.lineWidth = 4;
            ctx.beginPath(); ctx.moveTo(left - 14, midY - 8); ctx.lineTo(left + 14, midY - 8); ctx.stroke();
            // Kutub Pendek (-)
            ctx.strokeStyle = '#94a3b8';
            ctx.lineWidth = 4;
            ctx.beginPath(); ctx.moveTo(left - 8, midY + 8); ctx.lineTo(left + 8, midY + 8); ctx.stroke();
            // Label Baterai
            ctx.fillStyle = '#f8fafc';
            ctx.font = 'bold 12px Inter, sans-serif';
            ctx.textAlign = 'right';
            ctx.fillText(`${V} V`, left - 22, midY + 4);

            // Gambar Lampu di Sisi Kanan
            const brightness = Math.min(1, P / 65);
            if (brightness > 0.05) {
                const grad = ctx.createRadialGradient(right, midY, 5, right, midY, 28 + brightness * 38);
                grad.addColorStop(0, `rgba(253, 224, 71, ${0.4 + brightness * 0.6})`);
                grad.addColorStop(1, 'rgba(253, 224, 71, 0)');
                ctx.fillStyle = grad;
                ctx.beginPath();
                ctx.arc(right, midY, 28 + brightness * 38, 0, Math.PI * 2);
                ctx.fill();
            }

            // Bola Lampu
            ctx.beginPath();
            ctx.arc(right, midY, 18, 0, Math.PI * 2);
            ctx.fillStyle = brightness > 0.15 ? '#fde047' : '#1e293b';
            ctx.fill();
            ctx.lineWidth = 2.5;
            ctx.strokeStyle = '#eab308';
            ctx.stroke();

            // Label Hambatan Lampu
            ctx.fillStyle = '#f8fafc';
            ctx.font = 'bold 12px Inter, sans-serif';
            ctx.textAlign = 'left';
            ctx.fillText(`R = ${R} Ω`, right + 24, midY + 4);

            // Label Amperemeter di Atas
            const midX = (left + right) / 2;
            ctx.beginPath();
            ctx.arc(midX, top, 16, 0, Math.PI * 2);
            ctx.fillStyle = '#0d9488';
            ctx.fill();
            ctx.strokeStyle = '#ccfbf1';
            ctx.lineWidth = 2;
            ctx.stroke();
            ctx.fillStyle = '#ffffff';
            ctx.font = 'bold 12px Inter, sans-serif';
            ctx.textAlign = 'center';
            ctx.fillText('A', midX, top + 4);
            ctx.fillStyle = '#5eead4';
            ctx.fillText(`I = ${I.toFixed(2)} A`, midX, top - 22);

            ohmAnimId = requestAnimationFrame(animateOhmCircuit);
        }

        // ==================== FUNGSI KUIS INTERAKTIF ====================
        function loadQuizQuestion() {
            quizAnswered = false;
            const q = quizQuestions[currentQuizIdx];

            document.getElementById('quiz-current-num').textContent = currentQuizIdx + 1;
            document.getElementById('quiz-total-num').textContent = quizQuestions.length;
            document.getElementById('quiz-topic-badge').textContent = q.topic;
            document.getElementById('quiz-live-score').textContent = quizScore;
            document.getElementById('quiz-progress-bar').style.width = `${((currentQuizIdx + 1) / quizQuestions.length) * 100}%`;
            document.getElementById('quiz-question').textContent = q.question;

            const optionsEl = document.getElementById('quiz-options');
            optionsEl.innerHTML = q.options.map((opt, idx) => `
                <button onclick="selectAnswer(${idx})" id="opt-btn-${idx}" class="w-full text-left p-4 rounded-2xl border-2 border-slate-200 hover:border-sky-400 hover:bg-sky-50/50 font-semibold text-sm sm:text-base text-slate-800 transition-all flex items-center justify-between gap-3">
                    <span>${opt}</span>
                    <span id="opt-icon-${idx}" class="text-lg"></span>
                </button>
            `).join('');

            document.getElementById('quiz-feedback').classList.add('hidden');
            document.getElementById('quiz-next-btn').classList.add('hidden');
        }

        function selectAnswer(selectedIdx) {
            if (quizAnswered) return;
            quizAnswered = true;

            const q = quizQuestions[currentQuizIdx];
            const isCorrect = selectedIdx === q.correct;

            if (isCorrect) {
                quizScore += 10;
                document.getElementById('quiz-live-score').textContent = quizScore;
            }

            // Warnai semua tombol pilihan
            q.options.forEach((_, idx) => {
                const btn = document.getElementById(`opt-btn-${idx}`);
                const icon = document.getElementById(`opt-icon-${idx}`);
                btn.disabled = true;
                btn.classList.remove('hover:border-sky-400', 'hover:bg-sky-50/50');

                if (idx === q.correct) {
                    btn.classList.remove('border-slate-200');
                    btn.classList.add('border-teal-500', 'bg-teal-50', 'text-teal-950');
                    icon.textContent = '✅';
                } else if (idx === selectedIdx && !isCorrect) {
                    btn.classList.remove('border-slate-200');
                    btn.classList.add('border-rose-500', 'bg-rose-50', 'text-rose-950');
                    icon.textContent = '❌';
                } else {
                    btn.classList.add('opacity-60');
                }
            });

            // Tampilkan pembahasan
            const fbBox = document.getElementById('quiz-feedback');
            const fbTitle = document.getElementById('quiz-feedback-title');
            const fbText = document.getElementById('quiz-feedback-text');

            fbBox.classList.remove('hidden', 'bg-teal-50', 'border-teal-200', 'text-teal-900', 'bg-rose-50', 'border-rose-200', 'text-rose-900');
            if (isCorrect) {
                fbBox.classList.add('bg-teal-50', 'border-teal-200', 'text-teal-900');
                fbTitle.textContent = "🎉 Jawabanmu Benar!";
            } else {
                fbBox.classList.add('bg-rose-50', 'border-rose-200', 'text-rose-900');
                fbTitle.textContent = "💡 Kurang Tepat, Yuk Simak Pembahasannya:";
            }
            fbText.textContent = q.explanation;

            const nextBtn = document.getElementById('quiz-next-btn');
            nextBtn.classList.remove('hidden');
            nextBtn.querySelector('span').textContent = currentQuizIdx === quizQuestions.length - 1 ? "Lihat Nilai Akhir" : "Soal Berikutnya";
        }

        function nextQuestion() {
            if (currentQuizIdx < quizQuestions.length - 1) {
                currentQuizIdx++;
                loadQuizQuestion();
            } else {
                showQuizResult();
            }
        }

        function showQuizResult() {
            document.getElementById('quiz-container').classList.add('hidden');
            const resBox = document.getElementById('quiz-result');
            resBox.classList.remove('hidden');

            document.getElementById('result-score').textContent = quizScore;
            const correctCount = quizScore / 10;
            document.getElementById('result-summary').textContent = `Kamu berhasil menjawab ${correctCount} dari ${quizQuestions.length} soal dengan tepat.`;

            let emoji = "🏆", pred = "Predikat: Sangat Kompeten (Luar Biasa!)";
            if (quizScore < 60) {
                emoji = "📚";
                pred = "Predikat: Perlu Berlatih Lagi (Jangan Menyerah!)";
            } else if (quizScore < 80) {
                emoji = "🌟";
                pred = "Predikat: Cukup Baik (Terus Tingkatkan!)";
            }
            document.getElementById('result-emoji').textContent = emoji;
            document.getElementById('result-predicate').textContent = pred;
        }

        function restartQuiz() {
            currentQuizIdx = 0;
            quizScore = 0;
            document.getElementById('quiz-result').classList.add('hidden');
            document.getElementById('quiz-container').classList.remove('hidden');
            loadQuizQuestion();
        }

        // ==================== FUNGSI GLOSARIUM ====================
        function renderGlossary() {
            const list = document.getElementById('glossary-list');
            const query = document.getElementById('search-glossary').value.toLowerCase().trim();

            const filtered = glossaryData.filter(item =>
                item.term.toLowerCase().includes(query) ||
                item.def.toLowerCase().includes(query) ||
                item.category.toLowerCase().includes(query)
            );

            if (filtered.length === 0) {
                list.innerHTML = `<div class="col-span-full text-center py-10 bg-white rounded-2xl border border-slate-200 text-slate-500 text-sm">Istilah "<b>${query}</b>" tidak ditemukan di glosarium.</div>`;
                return;
            }

            list.innerHTML = filtered.map(item => `
                <div class="bg-white rounded-2xl border border-slate-200/90 p-5 shadow-2xs hover:border-teal-300 transition">
                    <div class="flex items-center justify-between gap-2 mb-2">
                        <h4 class="font-bold text-slate-900 text-base">${item.term}</h4>
                        <span class="text-[11px] font-bold px-2.5 py-0.5 rounded-full bg-slate-100 text-slate-600">${item.category}</span>
                    </div>
                    <p class="text-xs sm:text-sm text-slate-600 leading-relaxed">${item.def}</p>
                </div>
            `).join('');
        }

        // ==================== INISIALISASI SAAT HALAMAN DIMUAT ====================
        window.addEventListener('DOMContentLoaded', () => {
            updateProgressUI();
            renderChapters();
            initPunnettOptions();
            updateOhmLab();
            loadQuizQuestion();
            renderGlossary();
        });

        window.addEventListener('resize', () => {
            resizeOhmCanvas();
        });

        // Tutup modal jika klik area gelap di luar kotak
        document.getElementById('chapter-modal').addEventListener('click', (e) => {
            if (e.target.id === 'chapter-modal') closeModal();
        });
    </script>
</body>
</html>
