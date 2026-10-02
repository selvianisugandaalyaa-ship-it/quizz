```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kuis Pendidikan Agama Islam</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Plus Jakarta Sans', sans-serif;
        }
    </style>
</head>
<body class="bg-emerald-950 text-slate-100 min-h-screen flex flex-col justify-between selection:bg-emerald-500 selection:text-white">

    <!-- Header Navigation -->
    <header class="border-b border-emerald-800/50 bg-emerald-900/40 backdrop-blur sticky top-0 z-50">
        <div class="max-w-4xl mx-auto px-4 py-3 flex items-center justify-between">
            <div class="flex items-center gap-3">
                <div class="w-10 h-10 rounded-xl bg-gradient-to-br from-emerald-400 to-teal-600 flex items-center justify-center font-bold text-slate-900 text-lg shadow-lg shadow-emerald-900/50">
                    📖
                </div>
                <div>
                    <h1 class="font-bold text-lg leading-tight text-emerald-100">Kuis Agama Islam</h1>
                    <p class="text-xs text-emerald-300/70">Uji Pemahaman Dasar Keislaman</p>
                </div>
            </div>
            <div id="quiz-badge" class="hidden text-xs bg-emerald-800/60 border border-emerald-700/50 text-emerald-200 px-3 py-1.5 rounded-full font-medium">
                15 Soal Pilihan Ganda
            </div>
        </div>
    </header>

    <!-- Main Container -->
    <main class="max-w-3xl w-full mx-auto px-4 py-8 flex-grow flex flex-col justify-center">

        <!-- SCREEN 1: START SCREEN -->
        <div id="start-screen" class="bg-emerald-900/30 border border-emerald-800/60 rounded-3xl p-6 md:p-10 text-center shadow-2xl backdrop-blur-sm">
            <div class="inline-flex items-center justify-center w-20 h-20 bg-emerald-800/50 rounded-full mb-6 text-4xl border border-emerald-700/50">
                ✨
            </div>
            <h2 class="text-2xl md:text-3xl font-bold text-emerald-50 mb-3">Selamat Datang di Kuis Agama Islam</h2>
            <p class="text-emerald-200/80 mb-8 max-w-lg mx-auto leading-relaxed">
                Uji dan perdalam pengetahuan Islam Anda meliputi Al-Qur'an, Rukun Islam, Rukun Iman, Kisah Nabi, dan Fiqih Dasar.
            </p>

            <div class="grid grid-cols-2 md:grid-cols-3 gap-3 mb-8 max-w-md mx-auto text-left text-sm">
                <div class="bg-emerald-950/60 p-3 rounded-xl border border-emerald-800/40">
                    <span class="text-xs text-emerald-400 block mb-0.5">Jumlah Soal</span>
                    <span class="font-semibold text-emerald-100">15 Pertanyaan</span>
                </div>
                <div class="bg-emerald-950/60 p-3 rounded-xl border border-emerald-800/40">
                    <span class="text-xs text-emerald-400 block mb-0.5">Format</span>
                    <span class="font-semibold text-emerald-100">Pilihan Ganda</span>
                </div>
                <div class="bg-emerald-950/60 p-3 rounded-xl border border-emerald-800/40 col-span-2 md:col-span-1">
                    <span class="text-xs text-emerald-400 block mb-0.5">Pembahasan</span>
                    <span class="font-semibold text-emerald-100">Tersedia LENGKAP</span>
                </div>
            </div>

            <button onclick="startQuiz()" class="w-full sm:w-auto px-8 py-3.5 bg-gradient-to-r from-emerald-500 to-teal-500 hover:from-emerald-400 hover:to-teal-400 text-slate-950 font-bold rounded-2xl shadow-lg shadow-emerald-500/20 transition-all hover:scale-[1.02] active:scale-[0.98]">
                Mulai Kuis Sekarang
            </button>
        </div>

        <!-- SCREEN 2: QUIZ SCREEN -->
        <div id="quiz-screen" class="hidden space-y-6">
            <!-- Progress Bar & Counter -->
            <div class="bg-emerald-900/30 border border-emerald-800/50 p-4 rounded-2xl">
                <div class="flex justify-between items-center text-sm font-semibold mb-2 text-emerald-200">
                    <span>Soal <span id="current-question-num" class="text-emerald-400">1</span> dari 15</span>
                    <span id="score-counter" class="text-xs bg-emerald-800/50 border border-emerald-700/50 px-2.5 py-1 rounded-lg">Skor: 0</span>
                </div>
                <div class="w-full bg-emerald-950 rounded-full h-2.5 overflow-hidden border border-emerald-800/40">
                    <div id="progress-bar" class="bg-gradient-to-r from-emerald-400 to-teal-400 h-2.5 rounded-full transition-all duration-300" style="width: 6.66%"></div>
                </div>
            </div>

            <!-- Question Card -->
            <div class="bg-emerald-900/30 border border-emerald-800/60 rounded-3xl p-6 md:p-8 shadow-xl backdrop-blur-sm">
                <h3 id="question-text" class="text-lg md:text-xl font-bold text-emerald-50 leading-relaxed mb-6">
                    <!-- Text Soal -->
                </h3>

                <!-- Options -->
                <div id="options-container" class="space-y-3">
                    <!-- Opsi Jawaban akan dirender JS -->
                </div>

                <!-- Feedback & Explanation Box -->
                <div id="explanation-box" class="hidden mt-6 p-4 rounded-2xl border bg-emerald-950/80 border-emerald-700/60 transition-all">
                    <div class="flex items-center gap-2 font-bold mb-1" id="feedback-header">
                        <!-- Header umpan balik -->
                    </div>
                    <p id="explanation-text" class="text-sm text-emerald-200/90 leading-relaxed">
                        <!-- Penjelasan -->
                    </p>
                </div>

                <!-- Navigation Action -->
                <div class="mt-8 flex justify-end">
                    <button id="next-btn" onclick="nextQuestion()" disabled class="px-6 py-3 bg-slate-800 text-slate-500 font-bold rounded-xl transition-all cursor-not-allowed">
                        Lanjut Ke Soal Berikutnya →
                    </button>
                </div>
            </div>
        </div>

        <!-- SCREEN 3: RESULT SCREEN -->
        <div id="result-screen" class="hidden bg-emerald-900/30 border border-emerald-800/60 rounded-3xl p-6 md:p-10 text-center shadow-2xl backdrop-blur-sm">
            <div id="result-icon" class="text-6xl mb-4">🎉</div>
            <h2 class="text-2xl md:text-3xl font-bold text-emerald-50 mb-2">Hasil Kuis Anda</h2>
            <p id="result-message" class="text-emerald-200/80 mb-6 text-sm">Kerja bagus! Berikut adalah ringkasan performa Anda.</p>

            <!-- Score Circle -->
            <div class="inline-flex flex-col items-center justify-center w-36 h-36 rounded-full bg-gradient-to-b from-emerald-800/60 to-emerald-950 border-4 border-emerald-500/50 shadow-inner mb-8">
                <span id="final-score" class="text-4xl font-extrabold text-emerald-300">0</span>
                <span class="text-xs text-emerald-400 font-medium uppercase tracking-wider mt-1">Nilai Akhir</span>
            </div>

            <!-- Stats Grid -->
            <div class="grid grid-cols-2 gap-4 max-w-sm mx-auto mb-8 text-left">
                <div class="bg-emerald-950/60 p-4 rounded-2xl border border-emerald-800/40 flex items-center gap-3">
                    <div class="w-10 h-10 rounded-xl bg-emerald-500/20 text-emerald-400 flex items-center justify-center font-bold text-lg">✓</div>
                    <div>
                        <span class="text-xs text-emerald-400 block">Benar</span>
                        <span id="correct-count" class="font-bold text-emerald-100 text-lg">0</span>
                    </div>
                </div>
                <div class="bg-emerald-950/60 p-4 rounded-2xl border border-emerald-800/40 flex items-center gap-3">
                    <div class="w-10 h-10 rounded-xl bg-rose-500/20 text-rose-400 flex items-center justify-center font-bold text-lg">✕</div>
                    <div>
                        <span class="text-xs text-rose-300 block">Salah</span>
                        <span id="wrong-count" class="font-bold text-emerald-100 text-lg">0</span>
                    </div>
                </div>
            </div>

            <div class="flex flex-col sm:flex-row gap-3 justify-center">
                <button onclick="restartQuiz()" class="px-6 py-3 bg-emerald-500 hover:bg-emerald-400 text-slate-950 font-bold rounded-xl transition-all shadow-lg shadow-emerald-500/20">
                    🔄 Ulangi Kuis
                </button>
                <button onclick="showReview()" class="px-6 py-3 bg-emerald-950 border border-emerald-700/60 hover:bg-emerald-800/40 text-emerald-200 font-bold rounded-xl transition-all">
                    📋 Lihat Pembahasan
                </button>
            </div>
        </div>

        <!-- SCREEN 4: REVIEW SCREEN -->
        <div id="review-screen" class="hidden space-y-6">
            <div class="flex items-center justify-between">
                <h2 class="text-xl font-bold text-emerald-100">Pembahasan Soal</h2>
                <button onclick="backToResult()" class="text-xs px-3 py-1.5 bg-emerald-800/60 border border-emerald-700/50 hover:bg-emerald-800 rounded-lg text-emerald-200">
                    ← Kembali ke Hasil
                </button>
            </div>
            
            <div id="review-container" class="space-y-4">
                <!-- Daftar pembahasan dirender oleh JS -->
            </div>
        </div>

    </main>

    <!-- Footer -->
    <footer class="border-t border-emerald-800/40 py-4 text-center text-xs text-emerald-400/60">
        <p>© Kuis Agama Islam Interaktif - Pembelajaran Pendidikan Agama Islam</p>
    </footer>

    <!-- Quiz Logic JavaScript -->
    <script>
        const questions = [
            {
                id: 1,
                question: "Kitab suci Al-Qur'an diturunkan kepada Nabi Muhammad SAW melalui perantara malaikat...",
                options: [
                    { key: "A", text: "Malaikat Jibril" },
                    { key: "B", text: "Malaikat Mikail" },
                    { key: "C", text: "Malaikat Israfil" },
                    { key: "D", text: "Malaikat Izrail" }
                ],
                correct: "A",
                explanation: "Malaikat Jibril bertugas menyampaikan wahyu Allah SWT kepada para Nabi dan Rasul."
            },
            {
                id: 2,
                question: "Surah pertama yang diturunkan kepada Nabi Muhammad SAW di Gua Hira adalah...",
                options: [
                    { key: "A", text: "Surah Al-Baqarah ayat 1-5" },
                    { key: "B", text: "Surah Al-Fatihah ayat 1-7" },
                    { key: "C", text: "Surah Al-'Alaq ayat 1-5" },
                    { key: "D", text: "Surah Al-Ikhlas ayat 1-4" }
                ],
                correct: "C",
                explanation: "Surah Al-'Alaq ayat 1-5 adalah wahyu pertama yang diturunkan di Gua Hira melalui Malaikat Jibril."
            },
            {
                id: 3,
                question: "Urutan Rukun Islam yang ketiga adalah...",
                options: [
                    { key: "A", text: "Menunaikan zakat" },
                    { key: "B", text: "Mendirikan sholat" },
                    { key: "C", text: "Berpuasa di bulan Ramadhan" },
                    { key: "D", text: "Menunaikan haji bagi yang mampu" }
                ],
                correct: "A",
                explanation: "Urutan Rukun Islam: 1) Syahadat, 2) Sholat, 3) Zakat, 4) Puasa Ramadhan, 5) Naik Haji bagi yang mampu."
            },
            {
                id: 4,
                question: "Nabi yang mendapat julukan Khatamul Anbiya (Penutup para nabi) adalah...",
                options: [
                    { key: "A", text: "Nabi Ibrahim AS" },
                    { key: "B", text: "Nabi Muhammad SAW" },
                    { key: "C", text: "Nabi Isa AS" },
                    { key: "D", text: "Nabi Musa AS" }
                ],
                correct: "B",
                explanation: "Gelar 'Khatamul Anbiya' artinya penutup para nabi dan rasul, yang dianugerahkan kepada Nabi Muhammad SAW."
            },
            {
                id: 5,
                question: "Sholat wajib lima waktu yang memiliki jumlah rakaat paling sedikit adalah...",
                options: [
                    { key: "A", text: "Sholat Zuhur" },
                    { key: "B", text: "Sholat Isya" },
                    { key: "C", text: "Sholat Subuh" },
                    { key: "D", text: "Sholat Maghrib" }
                ],
                correct: "C",
                explanation: "Sholat Subuh hanya memiliki 2 rakaat, terbilang paling sedikit di antara sholat fardhu 5 waktu."
            },
            {
                id: 6,
                question: "Peristiwa perjalanan malam hari Nabi Muhammad SAW dari Masjidil Haram ke Masjidil Aqsha lalu naik ke Sidratul Muntaha disebut...",
                options: [
                    { key: "A", text: "Isra Mi'raj" },
                    { key: "B", text: "Fathu Makkah" },
                    { key: "C", text: "Perjanjian Hudaibiyah" },
                    { key: "D", text: "Peristiwa Hijrah" }
                ],
                correct: "A",
                explanation: "Isra Mi'raj adalah mukjizat perjalanan agung Nabi Muhammad SAW tempat diperintahkannya sholat 5 waktu."
            },
            {
                id: 7,
                question: "Malaikat yang bertugas mencatat amal buruk manusia adalah...",
                options: [
                    { key: "A", text: "Malaikat Munkar" },
                    { key: "B", text: "Malaikat Nakir" },
                    { key: "C", text: "Malaikat 'Atid" },
                    { key: "D", text: "Malaikat Raqib" }
                ],
                correct: "C",
                explanation: "Malaikat Raqib mencatat amal kebaikan, sedangkan Malaikat 'Atid mencatat amal keburukan."
            },
            {
                id: 8,
                question: "Jumlah juz yang terdapat di dalam Al-Qur'an secara keseluruhan adalah...",
                options: [
                    { key: "A", text: "20 juz" },
                    { key: "B", text: "30 juz" },
                    { key: "C", text: "25 juz" },
                    { key: "D", text: "40 juz" }
                ],
                correct: "B",
                explanation: "Al-Qur'an secara utuh terbagi menjadi 30 juz dan 114 surah."
            },
            {
                id: 9,
                question: "Khalifah pertama dari Khulafaur Rasyidin yang menggantikan kepemimpinan setelah Nabi Muhammad SAW wafat adalah...",
                options: [
                    { key: "A", text: "Ali bin Abi Thalib" },
                    { key: "B", text: "Abu Bakar Ash-Shiddiq" },
                    { key: "C", text: "Umar bin Khattab" },
                    { key: "D", text: "Usman bin Affan" }
                ],
                correct: "B",
                explanation: "Abu Bakar Ash-Shiddiq RA adalah khalifah pertama dari empat Khulafaur Rasyidin."
            },
            {
                id: 10,
                question: "Bersuci menggunakan debu atau tanah yang bersih sebagai pengganti wudhu dinamakan...",
                options: [
                    { key: "A", text: "Mandi wajib" },
                    { key: "B", text: "Istinja" },
                    { key: "C", text: "Tayamum" },
                    { key: "D", text: "Tazkiyah" }
                ],
                correct: "C",
                explanation: "Tayamum dilakukan menggunakan debu suci apabila tidak ditemukan air atau ada halangan medis."
            },
            {
                id: 11,
                question: "Puasa yang hukumnya wajib dilakukan oleh setiap umat Islam yang memenuhi syarat selama satu bulan penuh adalah...",
                options: [
                    { key: "A", text: "Puasa Syawal" },
                    { key: "B", text: "Puasa Arafah" },
                    { key: "C", text: "Puasa Ramadhan" },
                    { key: "D", text: "Puasa Senin-Kamis" }
                ],
                correct: "C",
                explanation: "Puasa Ramadhan hukumnya Fardhu 'Ain bagi setiap muslim yang baligh dan berakal selama bulan Ramadhan."
            },
            {
                id: 12,
                question: "Rukun Iman yang kelima menurut ajaran Islam adalah percaya kepada...",
                options: [
                    { key: "A", text: "Malaikat-malaikat Allah" },
                    { key: "B", text: "Hari Kiamat" },
                    { key: "C", text: "Kitab-kitab Allah" },
                    { key: "D", text: "Qada dan Qadar" }
                ],
                correct: "B",
                explanation: "Rukun Iman ke-5 adalah meyakini dan percaya akan datangnya Hari Kiamat (Hari Akhir)."
            },
            {
                id: 13,
                question: "Kitab suci Injil diturunkan oleh Allah SWT kepada Nabi...",
                options: [
                    { key: "A", text: "Nabi Daud AS" },
                    { key: "B", text: "Nabi Ibrahim AS" },
                    { key: "C", text: "Nabi Isa AS" },
                    { key: "D", text: "Nabi Musa AS" }
                ],
                correct: "C",
                explanation: "Kitab Taurat (Nabi Musa AS), Kitab Zabur (Nabi Daud AS), Kitab Injil (Nabi Isa AS), dan Al-Qur'an (Nabi Muhammad SAW)."
            },
            {
                id: 14,
                question: "Gelar Al-Amin yang diberikan masyarakat Makkah kepada Nabi Muhammad SAW berarti...",
                options: [
                    { key: "A", text: "Orang yang penyebar" },
                    { key: "B", text: "Orang yang cerdas" },
                    { key: "C", text: "Orang yang pemurah" },
                    { key: "D", text: "Orang yang dapat dipercaya" }
                ],
                correct: "D",
                explanation: "Gelar Al-Amin diberikan karena kejujuran, keluhuran budi, dan sifat terpercaya Nabi Muhammad SAW."
            },
            {
                id: 15,
                question: "Jumlah Rukun Iman ada...",
                options: [
                    { key: "A", text: "Lima" },
                    { key: "B", text: "Enam" },
                    { key: "C", text: "Tiga" },
                    { key: "D", text: "Dua" }
                ],
                correct: "B",
                explanation: "Rukun Iman berjumlah 6 perkara (Iman kepada Allah, Malaikat, Kitab, Rasul, Hari Kiamat, serta Qada & Qadar)."
            }
        ];

        let currentQuestionIndex = 0;
        let score = 0;
        let userAnswers = [];

        // Elements
        const startScreen = document.getElementById('start-screen');
        const quizScreen = document.getElementById('quiz-screen');
        const resultScreen = document.getElementById('result-screen');
        const reviewScreen = document.getElementById('review-screen');
        const quizBadge = document.getElementById('quiz-badge');

        const currentQuestionNumEl = document.getElementById('current-question-num');
        const scoreCounterEl = document.getElementById('score-counter');
        const progressBarEl = document.getElementById('progress-bar');
        const questionTextEl = document.getElementById('question-text');
        const optionsContainerEl = document.getElementById('options-container');
        const explanationBoxEl = document.getElementById('explanation-box');
        const feedbackHeaderEl = document.getElementById('feedback-header');
        const explanationTextEl = document.getElementById('explanation-text');
        const nextBtnEl = document.getElementById('next-btn');

        function startQuiz() {
            startScreen.classList.add('hidden');
            quizScreen.classList.remove('hidden');
            quizBadge.classList.remove('hidden');
            
            currentQuestionIndex = 0;
            score = 0;
            userAnswers = [];
            
            loadQuestion();
        }

        function loadQuestion() {
            const q = questions[currentQuestionIndex];
            
            // Reset state UI
            explanationBoxEl.classList.add('hidden');
            nextBtnEl.disabled = true;
            nextBtnEl.className = "px-6 py-3 bg-slate-800 text-slate-500 font-bold rounded-xl transition-all cursor-not-allowed";
            nextBtnEl.textContent = (currentQuestionIndex === questions.length - 1) ? "Lihat Hasil Akhir ✨" : "Lanjut Ke Soal Berikutnya →";

            // Update Progress
            currentQuestionNumEl.textContent = currentQuestionIndex + 1;
            scoreCounterEl.textContent = `Skor: ${score}`;
            const progressPercent = ((currentQuestionIndex + 1) / questions.length) * 100;
            progressBarEl.style.width = `${progressPercent}%`;

            // Set Question Text
            questionTextEl.textContent = `${q.id}. ${q.question}`;

            // Clear and Render Options
            optionsContainerEl.innerHTML = '';
            q.options.forEach(opt => {
                const button = document.createElement('button');
                button.type = 'button';
                button.className = "w-full text-left p-4 rounded-2xl border border-emerald-800/60 bg-emerald-950/40 hover:bg-emerald-900/60 hover:border-emerald-600/60 transition-all flex items-start gap-3.5 group";
                button.onclick = () => selectOption(opt.key);
                
                button.innerHTML = `
                    <span class="w-7 h-7 rounded-lg bg-emerald-900/80 border border-emerald-700/60 text-emerald-300 flex items-center justify-center font-semibold text-xs shrink-0 group-hover:bg-emerald-700 group-hover:text-white transition-all">
                        ${opt.key}
                    </span>
                    <span class="text-sm md:text-base text-emerald-100/90 font-medium pt-0.5 leading-snug">
                        ${opt.text}
                    </span>
                `;
                optionsContainerEl.appendChild(button);
            });
        }

        function selectOption(selectedKey) {
            const q = questions[currentQuestionIndex];
            const isCorrect = (selectedKey === q.correct);

            userAnswers.push({
                questionId: q.id,
                selected: selectedKey,
                isCorrect: isCorrect
            });

            if (isCorrect) {
                score += 10;
            }

            // Update Score Counter
            scoreCounterEl.textContent = `Skor: ${score}`;

            // Highlight Options
            const optionButtons = optionsContainerEl.children;
            q.options.forEach((opt, idx) => {
                const btn = optionButtons[idx];
                btn.disabled = true;
                btn.classList.remove('hover:bg-emerald-900/60', 'hover:border-emerald-600/60');

                if (opt.key === q.correct) {
                    btn.className = "w-full text-left p-4 rounded-2xl border-2 border-emerald-400 bg-emerald-900/90 flex items-start gap-3.5 shadow-lg shadow-emerald-900/40";
                } else if (opt.key === selectedKey && !isCorrect) {
                    btn.className = "w-full text-left p-4 rounded-2xl border-2 border-rose-500/80 bg-rose-950/50 flex items-start gap-3.5 opacity-90";
                } else {
                    btn.className += " opacity-40";
                }
            });

            // Show Feedback & Explanation
            explanationBoxEl.classList.remove('hidden');
            if (isCorrect) {
                feedbackHeaderEl.className = "flex items-center gap-2 font-bold text-emerald-400 mb-1";
                feedbackHeaderEl.innerHTML = "<span>✓</span> Jawaban Anda Benar!";
            } else {
                feedbackHeaderEl.className = "flex items-center gap-2 font-bold text-rose-400 mb-1";
                feedbackHeaderEl.innerHTML = `<span>✕</span> Jawaban Kurang Tepat (Jawaban Benar: ${q.correct})`;
            }
            explanationTextEl.textContent = q.explanation;

            // Enable Next Button
            nextBtnEl.disabled = false;
            nextBtnEl.className = "px-6 py-3 bg-gradient-to-r from-emerald-500 to-teal-500 hover:from-emerald-400 hover:to-teal-400 text-slate-950 font-bold rounded-xl transition-all shadow-md shadow-emerald-500/20 active:scale-95 cursor-pointer";
        }

        function nextQuestion() {
            if (currentQuestionIndex < questions.length - 1) {
                currentQuestionIndex++;
                loadQuestion();
            } else {
                showResults();
            }
        }

        function showResults() {
            quizScreen.classList.add('hidden');
            resultScreen.classList.remove('hidden');

            const totalQuestions = questions.length;
            const correctCount = userAnswers.filter(a => a.isCorrect).length;
            const wrongCount = totalQuestions - correctCount;
            const finalScoreVal = Math.round((correctCount / totalQuestions) * 100);

            document.getElementById('final-score').textContent = finalScoreVal;
            document.getElementById('correct-count').textContent = correctCount;
            document.getElementById('wrong-count').textContent = wrongCount;

            const resultIcon = document.getElementById('result-icon');
            const resultMsg = document.getElementById('result-message');

            if (finalScoreVal === 100) {
                resultIcon.textContent = "🏆";
                resultMsg.textContent = "Mumtaz! Sempurna! Anda menguasai seluruh materi dengan sangat baik.";
            } else if (finalScoreVal >= 75) {
                resultIcon.textContent = "🌟";
                resultMsg.textContent = "Sangat Baik! Pemahaman pemahaman dasar agama Islam Anda sudah mantap.";
            } else if (finalScoreVal >= 50) {
                resultIcon.textContent = "👍";
                resultMsg.textContent = "Cukup Baik! Anda bisa meninjau ulang pembahasan untuk meningkatkan nilai.";
            } else {
                resultIcon.textContent = "📚";
                resultMsg.textContent = "Jangan berkecil hati! Mari pelajari kembali pembahasan di bawah ini.";
            }
        }

        function restartQuiz() {
            resultScreen.classList.add('hidden');
            reviewScreen.classList.add('hidden');
            startQuiz();
        }

        function showReview() {
            resultScreen.classList.add('hidden');
            reviewScreen.classList.remove('hidden');

            const container = document.getElementById('review-container');
            container.innerHTML = '';

            questions.forEach((q, index) => {
                const userAns = userAnswers[index];
                const isCorrect = userAns ? userAns.isCorrect : false;
                const userChoiceKey = userAns ? userAns.selected : '-';

                const card = document.createElement('div');
                card.className = `p-5 rounded-2xl border ${isCorrect ? 'border-emerald-800/60 bg-emerald-900/20' : 'border-rose-900/60 bg-rose-950/20'} space-y-3`;

                let optionsHtml = '';
                q.options.forEach(opt => {
                    let optStyle = "text-emerald-200/70";
                    let badge = "";

                    if (opt.key === q.correct) {
                        optStyle = "text-emerald-300 font-bold";
                        badge = `<span class="ml-2 text-xs bg-emerald-500/20 text-emerald-300 border border-emerald-500/40 px-2 py-0.5 rounded">Jawaban Benar</span>`;
                    }
                    if (opt.key === userChoiceKey && !isCorrect) {
                        optStyle = "text-rose-400 font-semibold line-through";
                        badge = `<span class="ml-2 text-xs bg-rose-500/20 text-rose-300 border border-rose-500/40 px-2 py-0.5 rounded">Pilihan Anda</span>`;
                    }

                    optionsHtml += `
                        <div class="text-sm flex items-center ${optStyle}">
                            <span class="w-6 font-mono text-xs opacity-75">${opt.key}.</span>
                            <span>${opt.text}</span>
                            ${badge}
                        </div>
                    `;
                });

                card.innerHTML = `
                    <div class="flex items-start justify-between gap-3">
                        <h4 class="font-bold text-emerald-100 text-base leading-snug">
                            ${q.id}. ${q.question}
                        </h4>
                        <span class="shrink-0 px-2.5 py-1 rounded-lg text-xs font-bold ${isCorrect ? 'bg-emerald-500/20 text-emerald-300 border border-emerald-500/30' : 'bg-rose-500/20 text-rose-300 border border-rose-500/30'}">
                            ${isCorrect ? '✓ Benar' : '✕ Salah'}
                        </span>
                    </div>
                    <div class="pl-2 border-l-2 ${isCorrect ? 'border-emerald-600/40' : 'border-rose-600/40'} space-y-1.5 pt-1">
                        ${optionsHtml}
                    </div>
                    <div class="bg-emerald-950/80 p-3 rounded-xl border border-emerald-800/40 text-xs text-emerald-200/80">
                        <span class="font-bold text-emerald-400 block mb-0.5">Penjelasan:</span>
                        ${q.explanation}
                    </div>
                `;

                container.appendChild(card);
            });
        }

        function backToResult() {
            reviewScreen.classList.add('hidden');
            resultScreen.classList.remove('hidden');
        }
    </script>
</body>
</html>
```
