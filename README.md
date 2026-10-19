[reading-buddy.html](https://github.com/user-attachments/files/33652783/reading-buddy.html)
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Dongyoon's Reading Buddy - 그래픽 노블 학습 메이트</title>
    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
    <style>
        .tap-word { cursor: pointer; border-bottom: 1px dotted #818cf8; border-radius: 2px; transition: background .15s; }
        .tap-word:hover, .tap-word.hit { background: #e0e7ff; }
        .speaking { background: #fef3c7 !important; border-color: #fbbf24 !important; }
    </style>
</head>
<body class="bg-slate-50 text-slate-800 font-sans antialiased min-h-screen pb-16">
    <div class="max-w-5xl mx-auto px-4 py-6">
        
        <!-- Header & Nav Tabs -->
        <header class="flex flex-col sm:flex-row items-center justify-between border-b border-slate-200 pb-5 mb-6 gap-4">
            <div>
                <div class="flex items-center gap-2">
                    <span class="bg-indigo-100 text-indigo-700 text-xs font-semibold px-3 py-1 rounded-full uppercase">AR 2.5 ~ 3.2</span>
                    <span class="bg-amber-100 text-amber-700 text-xs font-semibold px-3 py-1 rounded-full">🔥 Dongyoon's Daily Goal</span>
                </div>
                <h1 class="text-2xl font-bold mt-1 text-slate-900">📖 동윤이의 그래픽 노블 리딩 버디</h1>
            </div>

            <!-- Page Navigation Tabs -->
            <nav class="flex bg-slate-200/70 p-1 rounded-xl text-sm font-medium">
                <button data-tab="today" class="tab-btn px-4 py-2 rounded-lg bg-white text-indigo-600 shadow-sm transition cursor-pointer">📚 오늘의 학습</button>
                <button data-tab="history" class="tab-btn px-4 py-2 rounded-lg text-slate-600 hover:text-slate-900 transition cursor-pointer">📈 누적 기록</button>
                <button data-tab="wrong" class="tab-btn px-4 py-2 rounded-lg text-slate-600 hover:text-slate-900 transition flex items-center gap-1.5 cursor-pointer">
                    <span>🔁 오답</span><span class="bg-rose-500 text-white text-xs px-2 py-0.5 rounded-full font-bold">3</span>
                </button>
            </nav>
        </header>

        <div id="viewToday">
        <!-- Daily Chapter Progress & Upload Banner -->
        <section class="bg-gradient-to-r from-indigo-900 to-indigo-700 text-white p-5 rounded-2xl mb-8 shadow-md">
            <div class="flex flex-col md:flex-row items-start md:items-center justify-between gap-4">
                <div class="space-y-1">
                    <div class="text-indigo-200 text-xs font-semibold uppercase tracking-wider">Dongyoon's Today Mission</div>
                    <h2 class="text-xl font-bold">Chapter 3. The Secret Entrance (pp. 24~35)</h2>
                    <p class="text-indigo-100 text-sm">오늘 정해진 분량: 총 3페이지 중 2페이지 완료!</p>
                </div>
                <div class="w-full md:w-auto flex flex-col sm:flex-row items-center gap-3">
                    <div class="w-full sm:w-36 bg-indigo-950/50 rounded-full h-3 p-0.5 border border-indigo-400/30">
                        <div class="bg-emerald-400 h-2 rounded-full w-2/3"></div>
                    </div>
                    <span class="text-xs text-indigo-200 font-mono">66% 완료</span>
                    
                    <!-- 사진 업로드 버튼 -->
                    <label class="w-full sm:w-auto bg-white hover:bg-indigo-50 text-indigo-900 font-bold px-4 py-2 rounded-xl text-sm transition shadow-sm flex items-center justify-center gap-1.5 cursor-pointer">
                        <span>📸</span> 다음 페이지 올리기
                        <input type="file" id="imageUpload" class="hidden" accept="image/*">
                    </label>
                </div>
            </div>
        </section>

        <!-- 이번 주 학습 (주 2회) -->
        <section class="bg-white border border-slate-200 rounded-2xl p-4 mb-6 shadow-sm flex flex-col sm:flex-row sm:items-center justify-between gap-3">
            <div class="flex items-center gap-3">
                <div id="weekDots" class="flex gap-1.5"></div>
                <div>
                    <div class="text-sm font-bold text-slate-900">이번 주 학습 <span id="weekCount" class="text-indigo-600"></span></div>
                    <div id="weekText" class="text-xs text-slate-500"></div>
                </div>
            </div>
            <button id="recordBtn" class="px-4 py-2.5 rounded-xl text-sm font-bold transition cursor-pointer"></button>
        </section>

        <!-- Main Workspace: 태블릿/모바일 최적화 그리드 -->
        <div class="grid grid-cols-1 lg:grid-cols-3 gap-6 items-start">
            
            <!-- Left Panel: OCR & Panel Text -->
            <div class="space-y-6">
                <!-- Page Preview Card -->
                <div class="bg-white p-5 rounded-2xl shadow-sm border border-slate-200">
                    <div class="flex items-center justify-between mb-3">
                        <h3 class="font-bold text-slate-900 flex items-center gap-2 text-sm">
                            <span>🖼️</span> 업로드된 페이지 미리보기
                        </h3>
                        <span id="uploadStatus" class="text-xs text-slate-400">사진을 올려주세요</span>
                    </div>
                    <div id="previewContainer" class="w-full h-64 sm:h-80 bg-slate-100 rounded-xl border-2 border-dashed border-slate-300 flex flex-col items-center justify-center p-2 text-center overflow-hidden relative">
                        <div id="placeholderContent" class="flex flex-col items-center justify-center">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-10 w-10 text-slate-400 mb-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M4 16l4.586-4.586a2 2 0 012.828 0L16 16m-2-2l1.586-1.586a2 2 0 012.828 0L20 14m-6-6h.01M6 20h12a2 2 0 002-2V6a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z" />
                            </svg>
                            <p class="text-xs text-slate-500 font-medium">Graphic Novel Page Photo</p>
                        </div>
                        <img id="previewImage" class="hidden w-full h-full object-contain rounded-lg" alt="Uploaded Page">
                    </div>
                </div>

                <!-- Panel Text OCR List with Audio Reader Button -->
                <div class="bg-white p-5 rounded-2xl shadow-sm border border-slate-200">
                    <div class="flex items-center justify-between mb-3">
                        <h3 class="font-bold text-slate-900 flex items-center gap-2 text-sm">
                            <span>💬</span> 추출된 텍스트 <span class="text-[10px] font-normal text-slate-400">(단어를 누르면 발음!)</span>
                        </h3>
                        <button id="readAllBtn" class="flex items-center gap-1 bg-indigo-50 hover:bg-indigo-100 text-indigo-700 text-xs font-semibold px-2.5 py-1.5 rounded-lg transition cursor-pointer">
                            <span>🔊</span> 전체 지문 읽기
                        </button>
                    </div>
                    <!-- 내용이 길어져도 내부 스크롤되도록 max-h 지정 -->
                    <div class="bg-slate-50 rounded-xl p-3 text-xs text-slate-700 space-y-2.5 font-mono max-h-60 overflow-y-auto border border-slate-100">
                        <div class="p-2 bg-white rounded border border-slate-200 flex items-start justify-between gap-2">
                            <div class="ocr-text leading-relaxed">
                                <span class="text-indigo-600 font-bold">[Panel 1]</span> "Watch out!" yelled Max, ducking behind the bushes.
                            </div>
                            <button class="speak-btn text-indigo-500 hover:text-indigo-700 p-1 shrink-0 cursor-pointer" title="문장 듣기">🔊</button>
                        </div>
                        <div class="p-2 bg-white rounded border border-slate-200 flex items-start justify-between gap-2">
                            <div class="ocr-text leading-relaxed">
                                <span class="text-indigo-600 font-bold">[Panel 2]</span> The mysterious glowing box began to shake violently.
                            </div>
                            <button class="speak-btn text-indigo-500 hover:text-indigo-700 p-1 shrink-0 cursor-pointer" title="문장 듣기">🔊</button>
                        </div>
                        <div class="p-2 bg-white rounded border border-slate-200 flex items-start justify-between gap-2">
                            <div class="ocr-text leading-relaxed">
                                <span class="text-indigo-600 font-bold">[Panel 3]</span> "Do you think we should open it?" asked Lily with a nervous smile.
                            </div>
                            <button class="speak-btn text-indigo-500 hover:text-indigo-700 p-1 shrink-0 cursor-pointer" title="문장 듣기">🔊</button>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Right Panel: Vocabulary & Quizzes -->
            <div class="lg:col-span-2 space-y-6">

                <!-- Vocabulary Cards with Audio Buttons -->
                <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200">
                    <div class="flex items-center justify-between mb-4">
                        <h3 class="font-bold text-slate-900 flex items-center gap-2">
                            <span>💡</span> AR 2.5~3.2 핵심 단어장
                        </h3>
                        <div class="flex items-center gap-2">
                            <button id="readWordsBtn" class="flex items-center gap-1 bg-indigo-50 hover:bg-indigo-100 text-indigo-700 text-xs font-semibold px-2.5 py-1.5 rounded-lg transition cursor-pointer"><span>🔊</span> 단어 전체 듣기</button>
                            <span class="text-xs bg-indigo-50 text-indigo-700 px-2.5 py-1 rounded-md font-medium">4 Words</span>
                        </div>
                    </div>
                    
                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
                        <div class="p-3.5 rounded-xl border border-slate-200 bg-slate-50/50 flex flex-col justify-between">
                            <div class="flex justify-between items-start">
                                <div>
                                    <span class="word-text font-bold text-indigo-950 text-base">mysterious</span>
                                    <span class="text-xs text-slate-400 block">/mɪˈstɪəriəs/</span>
                                </div>
                                <button class="speak-word-btn w-8 h-8 bg-indigo-100 hover:bg-indigo-200 text-indigo-700 rounded-full flex items-center justify-center transition cursor-pointer" title="발음 듣기">
                                    🔊
                                </button>
                            </div>
                            <p class="text-sm text-slate-700 mt-2">신비로운, 알 수 없는</p>
                        </div>

                        <div class="p-3.5 rounded-xl border border-slate-200 bg-slate-50/50 flex flex-col justify-between">
                            <div class="flex justify-between items-start">
                                <div>
                                    <span class="word-text font-bold text-indigo-950 text-base">violently</span>
                                    <span class="text-xs text-slate-400 block">/ˈvaɪələntli/</span>
                                </div>
                                <button class="speak-word-btn w-8 h-8 bg-indigo-100 hover:bg-indigo-200 text-indigo-700 rounded-full flex items-center justify-center transition cursor-pointer" title="발음 듣기">
                                    🔊
                                </button>
                            </div>
                            <p class="text-sm text-slate-700 mt-2">격렬하게, 심하게</p>
                        </div>

                        <div class="p-3.5 rounded-xl border border-slate-200 bg-slate-50/50 flex flex-col justify-between">
                            <div class="flex justify-between items-start">
                                <div>
                                    <span class="word-text font-bold text-indigo-950 text-base">nervous</span>
                                    <span class="text-xs text-slate-400 block">/ˈnɜːrvəs/</span>
                                </div>
                                <button class="speak-word-btn w-8 h-8 bg-indigo-100 hover:bg-indigo-200 text-indigo-700 rounded-full flex items-center justify-center transition cursor-pointer" title="발음 듣기">
                                    🔊
                                </button>
                            </div>
                            <p class="text-sm text-slate-700 mt-2">초조한, 긴장한</p>
                        </div>

                        <div class="p-3.5 rounded-xl border border-slate-200 bg-slate-50/50 flex flex-col justify-between">
                            <div class="flex justify-between items-start">
                                <div>
                                    <span class="word-text font-bold text-indigo-950 text-base">duck</span>
                                    <span class="text-xs text-slate-400 block">/dʌk/</span>
                                </div>
                                <button class="speak-word-btn w-8 h-8 bg-indigo-100 hover:bg-indigo-200 text-indigo-700 rounded-full flex items-center justify-center transition cursor-pointer" title="발음 듣기">
                                    🔊
                                </button>
                            </div>
                            <p class="text-sm text-slate-700 mt-2">(몸을) 푹 숙이다</p>
                        </div>
                    </div>
                </div>

                <!-- Quiz Section -->
                <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200">
                    <div class="flex items-center justify-between border-b border-slate-100 pb-3 mb-5">
                        <h3 class="font-bold text-slate-900 flex items-center gap-2">
                            <span>✏️</span> 오늘 페이지 학습 퀴즈
                        </h3>
                        <div class="flex gap-2">
                            <button class="px-3 py-1 text-xs font-semibold rounded-lg bg-indigo-600 text-white cursor-pointer">1. 단어 문제</button>
                            <button class="px-3 py-1 text-xs font-semibold rounded-lg bg-slate-100 text-slate-600 hover:bg-slate-200 cursor-pointer">2. 내용 이해</button>
                        </div>
                    </div>

                    <div class="space-y-4">
                        <div class="bg-slate-50 border border-slate-200 p-4 rounded-xl">
                            <div class="flex justify-between items-center mb-2">
                                <span class="text-xs font-bold text-indigo-600">Vocabulary Quiz Q1</span>
                                <span class="text-xs text-slate-400">뜻에 알맞은 단어를 선택하세요</span>
                            </div>
                            <p class="font-semibold text-sm text-slate-900 mb-3">"가슴이 콩닥거리고 불안하거나 긴장된 상태"를 의미하는 단어는?</p>
                            
                            <div class="grid grid-cols-1 sm:grid-cols-3 gap-2 text-sm">
                                <button class="p-2.5 rounded-lg border border-slate-200 bg-white hover:border-indigo-500 hover:text-indigo-600 text-left font-medium transition cursor-pointer">
                                    A) Mysterious
                                </button>
                                <button class="p-2.5 rounded-lg border border-indigo-500 bg-indigo-50/50 text-indigo-700 text-left font-medium transition cursor-pointer flex justify-between items-center">
                                    <span>B) Nervous</span>
                                    <span class="text-xs">✔️</span>
                                </button>
                                <button class="p-2.5 rounded-lg border border-slate-200 bg-white hover:border-indigo-500 hover:text-indigo-600 text-left font-medium transition cursor-pointer">
                                    C) Violently
                                </button>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Review / Wrong Answer Note -->
                <div id="wrongSection" class="bg-rose-50/60 border border-rose-200 p-5 rounded-2xl">
                    <div class="flex items-center justify-between mb-3">
                        <div class="flex items-center gap-2">
                            <span class="text-lg">🚨</span>
                            <h3 class="font-bold text-rose-900 text-sm">지난 오답 다시보기 (복습 필요 3개)</h3>
                        </div>
                        <span class="text-xs text-rose-600 font-medium underline cursor-pointer">전체 오답노트 이동 →</span>
                    </div>

                    <div class="bg-white rounded-xl p-3 border border-rose-100 space-y-2 text-xs">
                        <div class="flex justify-between items-center pb-2 border-b border-slate-100">
                            <div>
                                <span class="font-bold text-slate-800">[Ch 2. p.18]</span>
                                <span class="text-slate-600 ml-1">"shiver"의 뜻으로 올바른 것은?</span>
                            </div>
                            <span class="bg-rose-100 text-rose-700 font-bold px-2 py-0.5 rounded">2회 틀림</span>
                        </div>
                        <p class="text-slate-500">내가 쓴 답: <span class="line-through text-rose-500">소리치다</span> ➔ 정답: <span class="text-emerald-600 font-bold">(추워서) 떨다</span></p>
                    </div>
                </div>

            </div>
        </div>
        </div><!-- /viewToday -->

        <!-- 누적 기록 -->
        <div id="viewHistory" class="hidden space-y-6">
            <div id="histStats" class="grid grid-cols-3 gap-3"></div>

            <div class="bg-white p-5 rounded-2xl shadow-sm border border-slate-200">
                <h3 class="font-bold text-slate-900 text-sm mb-3">🗓️ 주간 달성 현황 <span class="text-xs font-normal text-slate-400">(주 2회 목표)</span></h3>
                <div id="histWeeks" class="space-y-2"></div>
            </div>

            <div class="grid grid-cols-1 lg:grid-cols-2 gap-6 items-start">
                <div class="bg-white p-5 rounded-2xl shadow-sm border border-slate-200">
                    <h3 class="font-bold text-slate-900 text-sm mb-3">📒 학습 일지</h3>
                    <div id="histSessions" class="space-y-2 max-h-96 overflow-y-auto"></div>
                </div>
                <div class="bg-white p-5 rounded-2xl shadow-sm border border-slate-200">
                    <h3 class="font-bold text-slate-900 text-sm mb-3">💡 누적 단어장</h3>
                    <div id="histWords" class="space-y-2 max-h-96 overflow-y-auto"></div>
                </div>
            </div>
            <p class="text-xs text-slate-400 text-center">기록은 이 기기의 이 브라우저에 저장돼요. 다른 기기에서는 따로 쌓입니다.</p>
        </div>
    </div>

    <!-- 속도 조절 버튼 -->
    <button id="rateBtn" class="fixed bottom-4 right-4 z-50 bg-indigo-600 hover:bg-indigo-700 text-white text-sm font-semibold px-4 py-2.5 rounded-full shadow-lg cursor-pointer">🙂 보통 속도</button>

    <!-- 기능 구현 자바스크립트 -->
    <script>
        // ---------- 사진 업로드 ----------
        const imageUpload = document.getElementById('imageUpload');
        const previewImage = document.getElementById('previewImage');
        const placeholderContent = document.getElementById('placeholderContent');
        const uploadStatus = document.getElementById('uploadStatus');
        imageUpload.addEventListener('change', e => {
            const file = e.target.files[0];
            if (!file) return;
            const reader = new FileReader();
            reader.onload = ev => {
                previewImage.src = ev.target.result;
                previewImage.classList.remove('hidden');
                placeholderContent.classList.add('hidden');
                uploadStatus.textContent = '업로드 완료!';
                uploadStatus.className = 'text-xs text-emerald-600 font-semibold';
            };
            reader.readAsDataURL(file);
        });

        // ---------- 음성 읽기 (TTS) ----------
        const hasTTS = 'speechSynthesis' in window;
        let voice = null, session = 0;
        const RATES = [
            { v: 0.6,  label: '🐢 느리게' },
            { v: 0.85, label: '🙂 보통' },
            { v: 1.0,  label: '🐇 빠르게' }
        ];
        let rateIdx = 1;

        function pickVoice() {
            const en = speechSynthesis.getVoices().filter(v => v.lang.replace('_', '-').startsWith('en'));
            voice = en.find(v => v.lang.replace('_', '-') === 'en-US' && /Google|Samantha|Aaron|Natural|Enhanced/i.test(v.name))
                 || en.find(v => v.lang.replace('_', '-') === 'en-US') || en[0] || null;
        }
        if (hasTTS) { pickVoice(); speechSynthesis.onvoiceschanged = pickVoice; }

        function speakRaw(text, onDone) {
            const u = new SpeechSynthesisUtterance(text);
            u.lang = 'en-US';
            if (voice) u.voice = voice;
            u.rate = RATES[rateIdx].v;
            let done = false;
            const finish = () => { if (!done) { done = true; onDone && onDone(); } };
            u.onend = finish; u.onerror = finish;
            speechSynthesis.speak(u);
        }

        function speakText(text) {               // 한 번 읽기 (진행 중인 읽기는 중단)
            if (!hasTTS) return alert('현재 브라우저가 음성 재생을 지원하지 않습니다.');
            stopAll();
            speakRaw(text);
        }

        function clearHighlight() { document.querySelectorAll('.speaking').forEach(el => el.classList.remove('speaking')); }

        const readAllBtn = document.getElementById('readAllBtn');
        const readWordsBtn = document.getElementById('readWordsBtn');
        const btnDefault = { readAll: readAllBtn.innerHTML, readWords: readWordsBtn.innerHTML };
        const STOP_HTML = '<span>⏹️</span> 멈추기';

        function resetButtons() {
            readAllBtn.innerHTML = btnDefault.readAll;
            readWordsBtn.innerHTML = btnDefault.readWords;
        }
        function stopAll() {
            session++;
            if (hasTTS) speechSynthesis.cancel();
            clearHighlight();
            resetButtons();
        }

        // 여러 항목을 차례대로 읽으며 하이라이트
        function readQueue(items, btn) {
            if (!hasTTS) return alert('현재 브라우저가 음성 재생을 지원하지 않습니다.');
            stopAll();
            const my = session;
            btn.innerHTML = STOP_HTML;
            let i = 0;
            const next = () => {
                if (my !== session) return;
                clearHighlight();
                if (i >= items.length) { resetButtons(); return; }
                const it = items[i++];
                it.row.classList.add('speaking');
                speakRaw(it.text, () => setTimeout(next, 250));
            };
            next();
        }
        function isReading(btn) { return btn.innerHTML === STOP_HTML; }

        // ---------- 문장(OCR) ----------
        const sentenceOf = el => el.textContent.replace(/\[Panel \d+\]/g, '').trim();

        // 문장 속 단어를 눌러 발음 듣기
        document.querySelectorAll('.ocr-text').forEach(el => {
            [...el.childNodes].forEach(node => {
                if (node.nodeType !== 3) return;
                const frag = document.createDocumentFragment();
                node.textContent.split(/([A-Za-z']+)/).forEach(part => {
                    if (/^[A-Za-z']+$/.test(part)) {
                        const s = document.createElement('span');
                        s.className = 'tap-word';
                        s.textContent = part;
                        frag.appendChild(s);
                    } else frag.appendChild(document.createTextNode(part));
                });
                node.replaceWith(frag);
            });
            el.addEventListener('click', e => {
                const w = e.target.closest('.tap-word');
                if (!w) return;
                w.classList.add('hit');
                setTimeout(() => w.classList.remove('hit'), 600);
                speakText(w.textContent);
            });
        });

        // 문장별 🔊
        document.querySelectorAll('.speak-btn').forEach(btn => {
            btn.addEventListener('click', () => {
                const row = btn.closest('.flex');
                const el = row.querySelector('.ocr-text');
                stopAll();
                row.classList.add('speaking');
                speakRaw(sentenceOf(el), () => row.classList.remove('speaking'));
            });
        });

        // 전체 지문 읽기 / 멈추기
        readAllBtn.addEventListener('click', () => {
            if (isReading(readAllBtn)) return stopAll();
            const items = [...document.querySelectorAll('.ocr-text')].map(el => ({ text: sentenceOf(el), row: el.closest('.flex') }));
            readQueue(items, readAllBtn);
        });

        // ---------- 단어장 ----------
        const wordCards = [...document.querySelectorAll('.word-text')].map(w => ({ text: w.textContent.trim(), row: w.closest('.rounded-xl') }));
        document.querySelectorAll('.speak-word-btn').forEach(btn => {
            btn.addEventListener('click', () => {
                const card = btn.closest('.rounded-xl');
                const word = card.querySelector('.word-text').textContent.trim();
                stopAll();
                card.classList.add('speaking');
                speakRaw(word, () => card.classList.remove('speaking'));
            });
        });
        readWordsBtn.addEventListener('click', () => {
            if (isReading(readWordsBtn)) return stopAll();
            readQueue(wordCards, readWordsBtn);
        });

        // ---------- 속도 조절 ----------
        document.getElementById('rateBtn').addEventListener('click', function () {
            rateIdx = (rateIdx + 1) % RATES.length;
            this.textContent = RATES[rateIdx].label + ' 속도';
            if (hasTTS) speakRaw('Ready');   // 바뀐 속도 미리 듣기
        });

        // ---------- 학습 기록 (주 2회 · 누적) ----------
        const CHILD_ID = 'dongyoon';            // 둘째 아이 프로필 추가 시 다른 id를 사용
        const GOAL = 2;                         // 주당 학습 횟수
        const STORE_KEY = 'readingBuddy:' + CHILD_ID;
        let memData = null;
        function loadData() {
            try { const r = localStorage.getItem(STORE_KEY); if (r) return JSON.parse(r); } catch (e) {}
            return memData || { sessions: [] };
        }
        function saveData() {
            memData = data;
            try { localStorage.setItem(STORE_KEY, JSON.stringify(data)); } catch (e) {}
        }
        let data = loadData();
        if (!data || !Array.isArray(data.sessions)) data = { sessions: [] };

        const pad = n => String(n).padStart(2, '0');
        const ymd = d => d.getFullYear() + '-' + pad(d.getMonth() + 1) + '-' + pad(d.getDate());
        const parseYmd = t => { const [y, m, d] = t.split('-').map(Number); return new Date(y, m - 1, d); };
        const mondayOf = d => { const x = new Date(d.getFullYear(), d.getMonth(), d.getDate()); x.setDate(x.getDate() - (x.getDay() + 6) % 7); return x; };
        const weekKey = d => ymd(mondayOf(d));
        const md = t => { const d = parseYmd(t); return (d.getMonth() + 1) + '/' + d.getDate(); };
        const esc = t => String(t).replace(/[&<>"']/g, c => ({ '&': '&amp;', '<': '&lt;', '>': '&gt;', '"': '&quot;', "'": '&#39;' }[c]));
        const weekCount = wk => data.sessions.filter(x => x.week === wk).length;

        const recordBtn = document.getElementById('recordBtn');

        function renderWeek() {
            const now = new Date(), wk = weekKey(now), today = ymd(now);
            const n = weekCount(wk), done = data.sessions.some(x => x.date === today);
            let dots = '';
            for (let i = 0; i < Math.max(GOAL, n); i++)
                dots += i < n
                    ? '<span class="w-8 h-8 rounded-full bg-emerald-500 text-white flex items-center justify-center text-sm font-bold">✓</span>'
                    : '<span class="w-8 h-8 rounded-full border-2 border-dashed border-slate-300"></span>';
            document.getElementById('weekDots').innerHTML = dots;
            document.getElementById('weekCount').textContent = n + ' / ' + GOAL + '회';
            document.getElementById('weekText').textContent =
                n >= GOAL ? '🎉 이번 주 목표 달성! 수고했어요' : '목표까지 ' + (GOAL - n) + '회 남았어요';
            if (done) {
                recordBtn.textContent = '✅ 오늘 학습 기록됨 (누르면 취소)';
                recordBtn.className = 'px-4 py-2.5 rounded-xl text-sm font-bold transition cursor-pointer bg-emerald-50 text-emerald-700 border border-emerald-200';
            } else {
                recordBtn.textContent = n >= GOAL ? '➕ 추가 학습 기록하기' : '✅ 오늘 학습 완료 기록하기';
                recordBtn.className = 'px-4 py-2.5 rounded-xl text-sm font-bold transition cursor-pointer bg-indigo-600 hover:bg-indigo-700 text-white shadow-sm';
            }
        }

        recordBtn.addEventListener('click', () => {
            const now = new Date(), today = ymd(now);
            const idx = data.sessions.findIndex(x => x.date === today);
            if (idx >= 0) {
                if (!confirm('오늘 학습 기록을 취소할까요?')) return;
                data.sessions.splice(idx, 1);
            } else {
                data.sessions.push({
                    date: today,
                    week: weekKey(now),
                    chapter: document.querySelector('section h2').textContent.trim(),
                    words: wordCards.map(c => ({
                        w: c.text,
                        meaning: c.row.querySelector('p').textContent.trim(),
                        ipa: c.row.querySelector('span.block').textContent.trim()
                    })),
                    sentences: [...document.querySelectorAll('.ocr-text')].map(sentenceOf)
                });
            }
            saveData();
            renderAll();
        });

        function renderHistory() {
            const list = [...data.sessions].sort((a, b) => b.date.localeCompare(a.date));

            // 누적 단어
            const wmap = new Map();
            [...data.sessions].sort((a, b) => a.date.localeCompare(b.date)).forEach(x =>
                x.words.forEach(w => {
                    const k = w.w.toLowerCase();
                    if (!wmap.has(k)) wmap.set(k, { ...w, first: x.date, count: 0 });
                    wmap.get(k).count++;
                }));

            // 연속 달성 주
            const byWeek = {};
            data.sessions.forEach(x => byWeek[x.week] = (byWeek[x.week] || 0) + 1);
            let cur = mondayOf(new Date()), streak = 0;
            if ((byWeek[ymd(cur)] || 0) < GOAL) cur.setDate(cur.getDate() - 7);
            while ((byWeek[ymd(cur)] || 0) >= GOAL) { streak++; cur.setDate(cur.getDate() - 7); }

            const stat = (icon, num, label) =>
                '<div class="bg-white border border-slate-200 rounded-2xl p-4 text-center shadow-sm"><div class="text-2xl">' + icon +
                '</div><div class="text-2xl font-bold text-slate-900 mt-1">' + num + '</div><div class="text-xs text-slate-500">' + label + '</div></div>';
            document.getElementById('histStats').innerHTML =
                stat('📚', data.sessions.length, '총 학습 횟수') + stat('💡', wmap.size, '누적 단어') + stat('🔥', streak, '연속 목표 달성(주)');

            // 주간 현황 (이번 주 포함 최근 8주)
            const weeks = [];
            let m = mondayOf(new Date());
            for (let i = 0; i < 8; i++) { weeks.push(ymd(m)); m = new Date(m); m.setDate(m.getDate() - 7); }
            document.getElementById('histWeeks').innerHTML = weeks.map((wk, i) => {
                const n = byWeek[wk] || 0, end = parseYmd(wk); end.setDate(end.getDate() + 6);
                const ok = n >= GOAL;
                return '<div class="flex items-center justify-between text-sm"><span class="text-slate-600 w-28">' + md(wk) + ' ~ ' + md(ymd(end)) + (i === 0 ? ' <span class="text-indigo-600 text-xs font-semibold">이번 주</span>' : '') +
                    '</span><div class="flex-1 mx-3 h-2 bg-slate-100 rounded-full overflow-hidden"><div class="h-2 rounded-full ' + (ok ? 'bg-emerald-500' : 'bg-indigo-400') + '" style="width:' + Math.min(100, n / GOAL * 100) + '%"></div></div>' +
                    '<span class="text-xs font-bold ' + (ok ? 'text-emerald-600' : 'text-slate-500') + '">' + n + '/' + GOAL + (ok ? ' ✓' : '') + '</span></div>';
            }).join('');

            // 학습 일지
            document.getElementById('histSessions').innerHTML = list.length ? list.map(x =>
                '<details class="border border-slate-200 rounded-xl p-3 text-sm"><summary class="cursor-pointer flex justify-between items-center gap-2">' +
                '<span><span class="font-bold text-slate-900">' + md(x.date) + '</span> <span class="text-slate-600">' + esc(x.chapter) + '</span></span>' +
                '<span class="text-xs text-slate-400 shrink-0">단어 ' + x.words.length + '개</span></summary>' +
                '<div class="mt-2 text-xs text-slate-600 space-y-1">' + x.sentences.map(t => '<p class="flex gap-1.5"><button class="hist-speak text-indigo-500 cursor-pointer" data-text="' + esc(t) + '">🔊</button><span>' + esc(t) + '</span></p>').join('') +
                '<button class="hist-del text-rose-500 underline mt-2 cursor-pointer" data-date="' + x.date + '">이 기록 삭제</button></div></details>'
            ).join('') : '<p class="text-sm text-slate-400 text-center py-6">아직 기록이 없어요.<br>학습 후 “오늘 학습 완료 기록하기”를 눌러보세요.</p>';

            // 누적 단어장
            document.getElementById('histWords').innerHTML = wmap.size ? [...wmap.values()].map(w =>
                '<div class="flex items-center justify-between border border-slate-200 rounded-xl p-2.5 bg-slate-50/50"><div><span class="font-bold text-indigo-950">' + esc(w.w) +
                '</span> <span class="text-xs text-slate-400">' + esc(w.ipa) + '</span><div class="text-xs text-slate-600">' + esc(w.meaning) +
                ' <span class="text-slate-400">· ' + md(w.first) + ' 첫 학습' + (w.count > 1 ? ' · ' + w.count + '회 등장' : '') + '</span></div></div>' +
                '<button class="hist-speak w-8 h-8 bg-indigo-100 hover:bg-indigo-200 rounded-full cursor-pointer" data-text="' + esc(w.w) + '">🔊</button></div>'
            ).join('') : '<p class="text-sm text-slate-400 text-center py-6">학습을 기록하면 단어가 여기에 쌓여요.</p>';
        }

        document.getElementById('viewHistory').addEventListener('click', e => {
            const sp = e.target.closest('.hist-speak');
            if (sp) return speakText(sp.dataset.text);
            const del = e.target.closest('.hist-del');
            if (del && confirm('이 학습 기록을 삭제할까요?')) {
                data.sessions = data.sessions.filter(x => x.date !== del.dataset.date);
                saveData(); renderAll();
            }
        });

        // ---------- 탭 전환 ----------
        function showTab(tab) {
            stopAll();
            document.getElementById('viewToday').classList.toggle('hidden', tab === 'history');
            document.getElementById('viewHistory').classList.toggle('hidden', tab !== 'history');
            document.querySelectorAll('.tab-btn').forEach(b => {
                const on = b.dataset.tab === (tab === 'wrong' ? 'wrong' : tab);
                b.classList.toggle('bg-white', on); b.classList.toggle('text-indigo-600', on); b.classList.toggle('shadow-sm', on);
                b.classList.toggle('text-slate-600', !on);
            });
            if (tab === 'wrong') document.getElementById('wrongSection').scrollIntoView({ behavior: 'smooth', block: 'center' });
            else window.scrollTo({ top: 0 });
        }
        document.querySelectorAll('.tab-btn').forEach(b => b.addEventListener('click', () => showTab(b.dataset.tab)));

        function renderAll() { renderWeek(); renderHistory(); }
        renderAll();
    </script>
</body>
</html>
