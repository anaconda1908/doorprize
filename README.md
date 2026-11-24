<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Selamat! Klaim Hadiah Doorprize Rp 100.000</title>
    <!-- Tailwind CSS untuk styling responsif dan modern -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Canvas Confetti untuk efek selebrasi -->
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.9.3/dist/confetti.browser.min.js"></script>
    <!-- Google Fonts: Plus Jakarta Sans -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap" rel="stylesheet">

    <style>
        body {
            font-family: 'Plus Jakarta Sans', sans-serif;
            background: radial-gradient(circle at top, #1e1b4b 0%, #0f172a 100%);
            min-height: 100vh;
            overflow-x: hidden;
        }

        /* Animasi melayang untuk kotak kado */
        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-12px) rotate(2deg); }
        }

        /* Animasi bergetar saat kotak kado diklik */
        @keyframes shake {
            0%, 100% { transform: rotate(0deg) scale(1); }
            20% { transform: rotate(-10deg) scale(1.08); }
            40% { transform: rotate(10deg) scale(1.08); }
            60% { transform: rotate(-10deg) scale(1.1); }
            80% { transform: rotate(10deg) scale(1.1); }
        }

        /* Animasi kilau cahaya di belakang kado */
        @keyframes pulseGlow {
            0%, 100% { opacity: 0.4; transform: scale(0.95); }
            50% { opacity: 0.85; transform: scale(1.1); }
        }

        .gift-float {
            animation: float 3s ease-in-out infinite;
        }

        .gift-shake {
            animation: shake 0.6s ease-in-out;
        }

        .glow-effect {
            animation: pulseGlow 2.5s ease-in-out infinite;
        }

        /* Efek kartu kaca (Glassmorphism) */
        .glass-card {
            background: rgba(255, 255, 255, 0.96);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
        }
    </style>
</head>
<body class="text-slate-800 flex flex-col items-center justify-center p-4 sm:p-6 selection:bg-amber-400 selection:text-slate-900">

    <!-- Notifikasi Toast Custom (Pengganti alert) -->
    <div id="toast-box" class="fixed top-5 left-1/2 -translate-x-1/2 z-50 transition-all duration-300 opacity-0 pointer-events-none transform -translate-y-4 w-[90%] max-w-sm">
        <div id="toast-content" class="bg-slate-900 text-white px-4 py-3 rounded-2xl shadow-2xl border border-slate-700 flex items-center gap-3 text-sm font-medium">
            <span id="toast-icon" class="text-lg">ℹ️</span>
            <span id="toast-message">Pesan notifikasi</span>
        </div>
    </div>

    <!-- Container Utama -->
    <main class="w-full max-w-md mx-auto my-auto">
        
        <!-- Header Brand / Event -->
        <header class="text-center mb-5">
            <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-white/10 border border-white/15 text-amber-300 text-xs font-semibold tracking-wider uppercase mb-2 backdrop-blur-sm">
                <span>✨</span> E-Voucher Doorprize Resmi
            </div>
            <h1 id="event-title" class="text-white text-xl sm:text-2xl font-extrabold tracking-tight">
                SPECIAL DOORPRIZE EVENT
            </h1>
        </header>

        <!-- STATE 1: KOTAK KADO (BELUM DIBUKA) -->
        <section id="view-unopened" class="glass-card rounded-3xl p-6 sm:p-8 shadow-2xl border border-white/40 text-center transition-all duration-500">
            <h2 class="text-2xl sm:text-3xl font-extrabold text-slate-900 mb-2">
                Anda Mendapatkan Kejutan!
            </h2>
            <p class="text-slate-500 text-sm sm:text-base mb-8 leading-relaxed">
                Ketuk kotak hadiah di bawah ini untuk membuka doorprize spesial Anda.
            </p>

            <!-- Area Interaktif Kotak Kado -->
            <div class="relative flex items-center justify-center my-6">
                <!-- Cahaya Belakang -->
                <div class="absolute w-44 h-44 bg-gradient-to-tr from-amber-400 to-pink-500 rounded-full blur-2xl glow-effect"></div>
                
                <!-- Tombol Kado SVG -->
                <button id="btn-open-gift" type="button" aria-label="Buka Kotak Hadiah" class="relative z-10 group focus:outline-none cursor-pointer p-4 rounded-3xl transition-transform active:scale-95">
                    <div id="gift-box-wrapper" class="gift-float">
                        <svg class="w-40 h-40 sm:w-44 sm:h-44 drop-shadow-2xl" viewBox="0 0 200 200" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <!-- Bayangan Bawah -->
                            <ellipse cx="100" cy="182" rx="65" ry="10" fill="#0F172A" fill-opacity="0.18"/>
                            <!-- Badan Kotak -->
                            <rect x="35" y="85" width="130" height="90" rx="14" fill="url(#boxGrad)"/>
                            <rect x="35" y="85" width="130" height="16" fill="#000000" fill-opacity="0.12"/>
                            <!-- Pita Vertikal Badan -->
                            <rect x="86" y="85" width="28" height="90" fill="url(#ribbonGrad)"/>
                            <!-- Tutup Kotak -->
                            <rect x="25" y="60" width="150" height="30" rx="10" fill="url(#lidGrad)"/>
                            <!-- Pita Vertikal Tutup -->
                            <rect x="86" y="60" width="28" height="30" fill="url(#ribbonGrad)"/>
                            <!-- Pita Kupu-kupu Atas -->
                            <path d="M100 60C100 60 65 20 48 38C31 56 75 60 100 60Z" fill="#FBBF24"/>
                            <path d="M100 60C100 60 135 20 152 38C169 56 125 60 100 60Z" fill="#F59E0B"/>
                            <circle cx="100" cy="58" r="10" fill="#FEF08A"/>
                            <defs>
                                <linearGradient id="boxGrad" x1="35" y1="85" x2="165" y2="175" gradientUnits="userSpaceOnUse">
                                    <stop stop-color="#4F46E5"/>
                                    <stop offset="1" stop-color="#312E81"/>
                                </linearGradient>
                                <linearGradient id="lidGrad" x1="25" y1="60" x2="175" y2="90" gradientUnits="userSpaceOnUse">
                                    <stop stop-color="#6366F1"/>
                                    <stop offset="1" stop-color="#4338CA"/>
                                </linearGradient>
                                <linearGradient id="ribbonGrad" x1="86" y1="60" x2="114" y2="175" gradientUnits="userSpaceOnUse">
                                    <stop stop-color="#FDE047"/>
                                    <stop offset="1" stop-color="#F59E0B"/>
                                </linearGradient>
                            </defs>
                        </svg>
                    </div>
                </button>
            </div>

            <button id="btn-trigger-text" type="button" class="w-full py-4 px-6 rounded-2xl bg-gradient-to-r from-amber-400 via-amber-500 to-orange-500 hover:from-amber-500 hover:to-orange-600 text-slate-950 font-extrabold text-base sm:text-lg shadow-lg shadow-amber-500/30 transition-all transform hover:-translate-y-0.5 active:translate-y-0 cursor-pointer">
                🎁 BUKA HADIAH SEKARANG
            </button>

            <p class="text-xs text-slate-400 mt-4">
                *Pastikan klaim dilakukan langsung pada perangkat pemenang.
            </p>
        </section>

        <!-- STATE 2: PENGUMUMAN HADIAH TERBUKA -->
        <section id="view-opened" class="hidden glass-card rounded-3xl p-6 sm:p-8 shadow-2xl border border-white/40 text-center transition-all duration-500">
            
            <!-- Banner Status Sudah Dibuka (Muncul jika halaman di-refresh) -->
            <div id="already-claimed-banner" class="hidden mb-5 p-3.5 rounded-2xl bg-amber-50 border border-amber-200 text-amber-800 text-xs sm:text-sm flex items-start gap-2.5 text-left">
                <span class="text-base mt-0.5">🔒</span>
                <div>
                    <p class="font-bold">Hadiah Sudah Terbuka di Perangkat Ini</p>
                    <p class="text-amber-700 mt-0.5">Silakan tekan tombol konfirmasi di bawah jika belum menghubungi panitia.</p>
                </div>
            </div>

            <!-- Header Pemenang -->
            <div class="inline-flex items-center justify-center w-14 h-14 rounded-2xl bg-emerald-100 text-emerald-600 text-3xl mb-3 shadow-inner">
                🎉
            </div>
            <p class="text-xs font-bold uppercase tracking-widest text-emerald-600 mb-1">
                Selamat! Anda Memenangkan
            </p>
            
            <!-- Kotak Nominal Hadiah -->
            <div class="my-4 py-5 px-4 rounded-2xl bg-gradient-to-br from-slate-900 via-indigo-950 to-slate-900 text-white border border-amber-400/40 shadow-lg relative overflow-hidden">
                <div class="absolute -right-6 -top-6 w-24 h-24 bg-amber-400/20 rounded-full blur-xl"></div>
                <p class="text-xs text-amber-300 font-medium mb-1">Hadiah Doorprize Resmi</p>
                <div id="prize-amount-display" class="text-3xl sm:text-4xl font-extrabold text-transparent bg-clip-text bg-gradient-to-r from-amber-200 via-yellow-400 to-amber-300 tracking-tight">
                    Rp 100.000
                </div>
            </div>

            <!-- Instruksi Singkat -->
            <p id="claim-instruction" class="text-slate-600 text-sm mb-6 leading-relaxed">
                Tunjukkan layar ini atau klik tombol di bawah untuk mengonfirmasi hadiah Anda kepada panitia.
            </p>

            <!-- Tombol Aksi Cepat -->
            <div class="space-y-3">
                <button id="btn-confirm-wa" type="button" class="w-full py-4 px-5 rounded-2xl bg-[#25D366] hover:bg-[#1ebe5d] text-white font-extrabold text-sm sm:text-base shadow-lg shadow-emerald-500/25 flex items-center justify-center gap-2.5 transition-all transform hover:-translate-y-0.5 active:translate-y-0 cursor-pointer">
                    <!-- Ikon WhatsApp SVG -->
                    <svg class="w-5 h-5 fill-current" viewBox="0 0 24 24">
                        <path d="M12.031 6.172c-3.181 0-5.767 2.586-5.768 5.766-.001 1.298.38 2.27 1.019 3.287l-.582 2.128 2.182-.573c.978.58 1.911.928 3.145.929 3.178 0 5.767-2.587 5.768-5.766.001-3.187-2.575-5.77-5.764-5.771zm3.392 8.244c-.144.405-.837.774-1.17.824-.299.045-.677.063-1.092-.069-.252-.08-.575-.187-.988-.365-1.739-.751-2.874-2.502-2.961-2.617-.087-.116-.708-.94-.708-1.793s.448-1.273.607-1.446c.159-.173.346-.217.462-.217l.332.006c.106.005.249-.04.39.298.144.347.491 1.2.534 1.287.043.087.072.188.014.304-.058.116-.087.188-.173.289l-.26.304c-.087.086-.177.18-.076.354.101.174.449.741.964 1.201.662.591 1.221.774 1.394.86s.274.072.376-.043c.101-.116.433-.506.549-.68.116-.173.231-.145.39-.087s1.011.477 1.184.564.289.13.332.202c.045.072.045.419-.1.824z"/>
                    </svg>
                    <span>KONFIRMASI KE WHATSAPP PANITIA</span>
                </button>

                <button id="btn-copy-link" type="button" class="w-full py-3 px-4 rounded-2xl bg-slate-100 hover:bg-slate-200 text-slate-700 font-bold text-xs sm:text-sm transition cursor-pointer">
                    📋 Salin Bukti Tautan Hadiah
                </button>
            </div>
        </section>

        <!-- Footer & Tombol Reset Admin Tersembunyi -->
        <footer class="mt-6 text-center text-slate-400 text-xs space-y-2">
            <p>&copy; <span id="year-now">2026</span> Panitia Doorprize Resmi. Hak Cipta Dilindungi.</p>
            <div>
                <!-- Klik 3x pada teks ini untuk membuka mode reset testing -->
                <button type="button" id="secret-admin-trigger" class="text-slate-600 hover:text-slate-400 transition text-[11px] select-none cursor-pointer">
                    Status Sesi: <span id="session-id-footer">AKTIF</span>
                </button>
            </div>
        </footer>
    </main>

    <!-- Modal Admin Reset (Untuk Testing) -->
    <div id="admin-modal" class="fixed inset-0 z-50 hidden bg-slate-950/80 backdrop-blur-sm flex items-center justify-center p-4">
        <div class="bg-white rounded-2xl max-w-xs w-full p-5 shadow-2xl text-center">
            <div class="w-10 h-10 rounded-full bg-rose-100 text-rose-600 flex items-center justify-center mx-auto mb-3 text-lg">
                🛠️
            </div>
            <h4 class="font-bold text-slate-900 text-base">Mode Testing Admin</h4>
            <p class="text-xs text-slate-500 mt-1 mb-4">
                Reset status pembukaan kado di browser ini agar bisa menguji animasi dari awal lagi?
            </p>
            <div class="flex gap-2">
                <button type="button" id="btn-close-admin" class="flex-1 py-2.5 px-3 rounded-xl bg-slate-100 hover:bg-slate-200 text-slate-700 font-semibold text-xs cursor-pointer">
                    Batal
                </button>
                <button type="button" id="btn-reset-claim" class="flex-1 py-2.5 px-3 rounded-xl bg-rose-600 hover:bg-rose-700 text-white font-semibold text-xs cursor-pointer">
                    Reset Kado
                </button>
            </div>
        </div>
    </div>

    <script>
        /**
         * ============================================================================
         * KONFIGURASI UTAMA (SILAKAN UBAH SESUAI KEBUTUHAN CLIENT)
         * ============================================================================
         */
        const CONFIG = {
            // Nomor WhatsApp Panitia/Admin (Gunakan kode negara 62 tanpa tanda + atau spasi)
            adminWhatsApp: "6281234567890",

            // Judul Event di bagian atas halaman
            eventName: "SPECIAL DOORPRIZE EVENT",

            // Nominal hadiah yang ditampilkan
            prizeNominal: "Rp 100.000",

            // Pesan singkat pada tampilan setelah kado terbuka
            instructionText: "Tunjukkan layar ini atau klik tombol di bawah untuk mengonfirmasi hadiah Anda kepada panitia.",

            // Key penyimpanan lokal browser untuk mencegah animasi terbuka ulang di perangkat yang sama
            storageKey: "doorprize_100k_opened_v2"
        };

        /**
         * ============================================================================
         * INISIALISASI STATE & ELEMEN DOM
         * ============================================================================
         */
        const viewUnopened = document.getElementById('view-unopened');
        const viewOpened = document.getElementById('view-opened');
        const btnOpenGift = document.getElementById('btn-open-gift');
        const btnTriggerText = document.getElementById('btn-trigger-text');
        const giftBoxWrapper = document.getElementById('gift-box-wrapper');
        const alreadyClaimedBanner = document.getElementById('already-claimed-banner');
        const btnConfirmWa = document.getElementById('btn-confirm-wa');
        const btnCopyLink = document.getElementById('btn-copy-link');

        // Set teks dinamis awal
        document.getElementById('event-title').textContent = CONFIG.eventName;
        document.getElementById('prize-amount-display').textContent = CONFIG.prizeNominal;
        document.getElementById('claim-instruction').textContent = CONFIG.instructionText;
        document.getElementById('year-now').textContent = new Date().getFullYear();

        /**
         * Fungsi Menampilkan Notifikasi Toast Ringan
         */
        function showToast(message, icon = "ℹ️") {
            const toastBox = document.getElementById('toast-box');
            document.getElementById('toast-message').textContent = message;
            document.getElementById('toast-icon').textContent = icon;
            
            toastBox.classList.remove('opacity-0', '-translate-y-4', 'pointer-events-none');
            toastBox.classList.add('opacity-100', 'translate-y-0');

            setTimeout(() => {
                toastBox.classList.add('opacity-0', '-translate-y-4', 'pointer-events-none');
                toastBox.classList.remove('opacity-100', 'translate-y-0');
            }, 3000);
        }

        /**
         * Efek Ledakan Konfeti Meriah
         */
        function launchConfetti() {
            if (typeof confetti !== 'function') return;
            
            const duration = 2200;
            const end = Date.now() + duration;

            (function frame() {
                confetti({
                    particleCount: 5,
                    angle: 60,
                    spread: 55,
                    origin: { x: 0 },
                    colors: ['#fbbf24', '#f59e0b', '#4f46e5', '#10b981']
                });
                confetti({
                    particleCount: 5,
                    angle: 120,
                    spread: 55,
                    origin: { x: 1 },
                    colors: ['#fbbf24', '#f59e0b', '#ec4899', '#10b981']
                });

                if (Date.now() < end) {
                    requestAnimationFrame(frame);
                }
            }());
        }

        /**
         * Menampilkan Tampilan Hadiah Terbuka
         */
        function revealPrizeView(isReloaded = false) {
            viewUnopened.classList.add('hidden');
            viewOpened.classList.remove('hidden');
            document.getElementById('session-id-footer').textContent = "TERBUKA";

            if (isReloaded) {
                alreadyClaimedBanner.classList.remove('hidden');
            }
        }

        /**
         * Handler Saat Kotak Kado Dibuka Pertama Kali
         */
        function handleOpenGift() {
            btnOpenGift.disabled = true;
            btnTriggerText.disabled = true;

            giftBoxWrapper.classList.remove('gift-float');
            giftBoxWrapper.classList.add('gift-shake');
            btnTriggerText.textContent = "Membuka Kejutan...";

            setTimeout(() => {
                try {
                    localStorage.setItem(CONFIG.storageKey, JSON.stringify({
                        prize: CONFIG.prizeNominal,
                        openedAt: new Date().toISOString()
                    }));
                } catch (e) {
                    console.warn("LocalStorage tidak tersedia:", e);
                }

                launchConfetti();
                revealPrizeView(false);
            }, 650);
        }

        /**
         * Cek Status Pembukaan Kado Saat Halaman Dimuat
         */
        function checkExistingOpen() {
            try {
                const existingRaw = localStorage.getItem(CONFIG.storageKey);
                if (existingRaw) {
                    revealPrizeView(true);
                }
            } catch (e) {
                console.warn("Gagal membaca status pembukaan kado:", e);
            }
        }

        /**
         * Event Listeners
         */
        btnOpenGift.addEventListener('click', handleOpenGift);
        btnTriggerText.addEventListener('click', handleOpenGift);

        // Salin tautan halaman ke clipboard
        btnCopyLink.addEventListener('click', () => {
            const tempInput = document.createElement('input');
            tempInput.value = window.location.href;
            document.body.appendChild(tempInput);
            tempInput.select();
            document.execCommand('copy');
            document.body.removeChild(tempInput);
            showToast("Tautan hadiah berhasil disalin!", "✅");
        });

        // Konfirmasi singkat ke WhatsApp Panitia tanpa form input panjang
        btnConfirmWa.addEventListener('click', () => {
            const message =
`Halo Panitia *${CONFIG.eventName}*,
Saya baru saja membuka kado doorprize dan mendapatkan hadiah *${CONFIG.prizeNominal}*.

Mohon informasi langkah selanjutnya ya. Terima kasih! 🙏`;

            const waUrl = `https://wa.me/${CONFIG.adminWhatsApp}?text=${encodeURIComponent(message)}`;

            showToast("Membuka WhatsApp Panitia...", "📲");
            setTimeout(() => {
                window.open(waUrl, '_blank');
            }, 350);
        });

        // Fitur Tersembunyi Admin: Klik 3x pada teks footer untuk Reset Testing
        let secretClicks = 0;
        let secretTimer = null;
        document.getElementById('secret-admin-trigger').addEventListener('click', () => {
            secretClicks++;
            clearTimeout(secretTimer);
            secretTimer = setTimeout(() => { secretClicks = 0; }, 1000);

            if (secretClicks >= 3) {
                secretClicks = 0;
                document.getElementById('admin-modal').classList.remove('hidden');
            }
        });

        document.getElementById('btn-close-admin').addEventListener('click', () => {
            document.getElementById('admin-modal').classList.add('hidden');
        });

        document.getElementById('btn-reset-claim').addEventListener('click', () => {
            try {
                localStorage.removeItem(CONFIG.storageKey);
            } catch (e) {}
            window.location.reload();
        });

        // Jalankan pengecekan saat halaman dibuka
        window.addEventListener('DOMContentLoaded', checkExistingOpen);
    </script>
</body>
</html>
