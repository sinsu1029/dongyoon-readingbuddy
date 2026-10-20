[reading-buddy (5).html](https://github.com/user-attachments/files/33707277/reading-buddy.5.html)
<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
<meta name="color-scheme" content="light">
<title>동윤이의 리딩 버디 · 그래픽 노블 학습</title>
<style>
  /* ── 토큰 ─────────────────────────────────────────── */
  :root{
    --ink:#191934; --ink-2:#3d3d5c; --muted:#71718f;
    --paper:#f6f6fb; --card:#ffffff; --line:#e4e4f0;
    --indigo:#4338ca; --indigo-d:#312e81; --indigo-soft:#eef2ff;
    --amber:#f59e0b; --amber-soft:#fffbeb;
    --ok:#059669; --ok-soft:#ecfdf5; --bad:#e11d48; --bad-soft:#fff1f2;
  }
  *,*::before,*::after{box-sizing:border-box}
  html{-webkit-text-size-adjust:100%}
  body{
    margin:0;background:var(--paper);color:var(--ink);padding-bottom:32px;min-height:100vh;
    font-family:-apple-system,BlinkMacSystemFont,"Apple SD Gothic Neo","Pretendard","Malgun Gothic","Segoe UI",Roboto,sans-serif;
    line-height:1.55;-webkit-font-smoothing:antialiased;
  }
  button,input,select,textarea{font:inherit;color:inherit}
  button{border:0;background:none}
  .hidden{display:none!important}
  .wrap{max-width:860px;margin:0 auto;padding:16px 16px 8px}
  .serif{font-family:Georgia,"Iowan Old Style","Times New Roman",serif}

  /* ── 공통 컨트롤 ──────────────────────────────────── */
  .btn{
    display:inline-flex;align-items:center;justify-content:center;gap:8px;min-height:52px;padding:0 18px;
    border-radius:16px;background:#ececf6;color:var(--ink);font-weight:700;font-size:15.5px;cursor:pointer;
    touch-action:manipulation;-webkit-tap-highlight-color:transparent;transition:transform .08s,filter .15s;
  }
  .btn:active{transform:scale(.97)}
  .btn.primary{background:var(--indigo);color:#fff;box-shadow:0 2px 0 #312e81}
  .btn.soft{background:var(--indigo-soft);color:var(--indigo-d)}
  .btn.ghost{background:#ececf6;color:var(--ink-2)}
  .btn.danger{background:var(--bad-soft);color:#be123c}
  .btn.ok{background:var(--ok-soft);color:#047857}
  .btn.block{display:flex;width:100%}
  .btn.sm{min-height:46px;font-size:14px;padding:0 14px;border-radius:14px}
  .btn.tiny{min-height:44px;font-size:13px;padding:0 12px;border-radius:12px}
  .btn.round{width:52px;height:52px;min-height:52px;padding:0;border-radius:50%;font-size:20px;flex:none}
  .btn:focus-visible,.tab:focus-visible,.opt:focus-visible,.chip:focus-visible{outline:3px solid #818cf8;outline-offset:2px}

  /* ── 헤더 ─────────────────────────────────────────── */
  .top{display:flex;align-items:flex-start;justify-content:space-between;gap:12px;margin-bottom:14px}
  .app-title{margin:0;font-size:20px;font-weight:800;letter-spacing:-.02em}
  .sub{margin:3px 0 0;font-size:12.5px;color:var(--muted)}

  /* ── 탭 ───────────────────────────────────────────── */
  .tabs{display:flex;gap:4px;background:#e6e6f2;padding:5px;border-radius:18px;overflow-x:auto;scrollbar-width:none}
  .tabs::-webkit-scrollbar{display:none}
  .tab{
    flex:1 1 0;min-width:0;display:inline-flex;align-items:center;justify-content:center;gap:5px;
    min-height:50px;padding:0 10px;border-radius:14px;background:transparent;color:#55557a;
    font-weight:700;font-size:14.5px;white-space:nowrap;cursor:pointer;-webkit-tap-highlight-color:transparent;
  }
  .tab.on{background:#fff;color:var(--indigo);box-shadow:0 1px 3px rgba(25,25,52,.12)}
  .badge{display:inline-flex;align-items:center;justify-content:center;min-width:21px;height:21px;padding:0 6px;border-radius:999px;background:var(--bad);color:#fff;font-size:11.5px;font-weight:800}

  /* ── 히어로 ───────────────────────────────────────── */
  .hero{
    background:linear-gradient(135deg,#312e81 0%,#4338ca 60%,#4f46e5 100%);
    color:#fff;border-radius:24px;padding:20px;margin-bottom:14px;box-shadow:0 12px 30px -12px rgba(49,46,129,.55);
  }
  .hero .eyebrow{font-size:11px;letter-spacing:.12em;text-transform:uppercase;color:#c7d2fe;font-weight:700}
  .hero h2{margin:6px 0 2px;font-size:21px;font-weight:800;letter-spacing:-.02em;line-height:1.3}
  .hero p{margin:0;color:#dfe4ff;font-size:13px}
  .hero-row{display:flex;align-items:center;justify-content:space-between;gap:12px;flex-wrap:wrap}
  .chip-level{display:inline-flex;align-items:center;gap:6px;background:rgba(255,255,255,.14);border:1px solid rgba(255,255,255,.25);color:#fff;font-size:11.5px;font-weight:700;padding:6px 11px;border-radius:999px}
  .seg{display:flex;gap:4px;background:rgba(0,0,0,.22);padding:4px;border-radius:12px}
  .seg button{min-height:40px;padding:0 11px;border-radius:9px;color:#c7d2fe;font-size:13px;font-weight:700;cursor:pointer}
  .seg button.on{background:#fff;color:var(--indigo-d)}

  /* ── 카드 ─────────────────────────────────────────── */
  .card{background:var(--card);border:1px solid var(--line);border-radius:22px;padding:18px;margin-bottom:12px}
  .card-head{display:flex;align-items:center;justify-content:space-between;gap:10px;margin-bottom:12px;flex-wrap:wrap}
  .card-title{margin:0;font-size:15.5px;font-weight:800;display:flex;align-items:center;gap:7px}
  .hint{margin:6px 0 0;font-size:12.5px;color:var(--muted);line-height:1.6}
  .hint b{color:var(--ink-2)}
  .stack{display:flex;flex-direction:column;gap:10px}
  .row{display:flex;align-items:center;gap:10px}
  .row.wrap{flex-wrap:wrap}
  .row.between{justify-content:space-between}
  .grow{flex:1;min-width:0}
  .empty{padding:44px 14px;text-align:center;color:#9a9ab8;font-size:15px;font-weight:600;line-height:1.75}

  /* ── 입력 ─────────────────────────────────────────── */
  input:not([type=checkbox]):not([type=radio]):not([type=file]),textarea,select{
    width:100%;border:1px solid #d4d4e4;border-radius:14px;background:#fff;padding:13px 15px;font-size:16px;outline:none;
    transition:border-color .15s,box-shadow .15s;
  }
  input:focus,textarea:focus,select:focus{border-color:var(--indigo);box-shadow:0 0 0 3px rgba(67,56,202,.14)}
  textarea{resize:none;line-height:1.7;min-height:70px}
  select{appearance:none;background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='13' height='8' viewBox='0 0 14 9'%3E%3Cpath d='M1 1l6 6 6-6' fill='none' stroke='%2371718f' stroke-width='2' stroke-linecap='round'/%3E%3C/svg%3E");background-repeat:no-repeat;background-position:right 14px center;padding-right:38px;font-weight:600}
  label.fld{display:block;font-size:12px;font-weight:800;color:var(--muted);margin-bottom:5px;letter-spacing:.02em}

  /* ── 지문 (책 페이지 느낌) ─────────────────────────── */
  .passage{display:flex;flex-direction:column;gap:12px}
  .panel{display:flex;gap:12px;align-items:flex-start;padding:12px 14px 12px 0;border-left:3px solid #e0e7ff;padding-left:14px}
  .panel .no{flex:none;width:24px;font-size:11.5px;font-weight:800;color:#a5b4fc;padding-top:5px;letter-spacing:.04em}
  .panel .txt{flex:1;font-size:18px;line-height:1.65;color:#232342}
  .panel.speaking{border-left-color:var(--amber);background:var(--amber-soft);border-radius:0 12px 12px 0}
  .passage.reading .panel{border-left-color:#c7d2fe}
  .passage.reading .panel.speaking{border-left-color:var(--amber)}
  .tap-word{cursor:pointer;border-bottom:1px dotted #a5b4fc;border-radius:3px;transition:background .15s}
  .tap-word:hover,.tap-word.hit{background:#e0e7ff}
  .say{flex:none}

  /* ── 단어 카드 ────────────────────────────────────── */
  .wgrid{display:grid;grid-template-columns:1fr;gap:10px}
  @media(min-width:560px){.wgrid{grid-template-columns:1fr 1fr}}
  .wcard{border:1px solid var(--line);border-radius:18px;padding:14px;background:#fbfbfe;display:flex;justify-content:space-between;gap:10px}
  .wcard .word{font-size:20px;font-weight:800;letter-spacing:-.01em;color:#1e1b4b}
  .wcard .ipa{font-size:12px;color:#9a9ab8;margin-top:1px}
  .wcard .ko{font-size:14.5px;color:var(--ink-2);margin-top:6px}

  /* ── 퀴즈 ─────────────────────────────────────────── */
  .subnav{display:flex;gap:6px;margin-bottom:14px}
  .subnav button{min-height:44px;padding:0 14px;border-radius:12px;background:#eff0f8;color:#55557a;font-size:13.5px;font-weight:700;cursor:pointer}
  .subnav button.on{background:var(--indigo);color:#fff}
  .qcard{background:#fbfbfe;border:1px solid var(--line);border-radius:16px;padding:14px;margin-bottom:10px}
  .qhead{display:flex;justify-content:space-between;align-items:center;margin-bottom:8px}
  .qlabel{font-size:11px;font-weight:800;color:var(--indigo);letter-spacing:.06em;text-transform:uppercase}
  .qtext{font-size:15.5px;font-weight:700;margin:0 0 10px;line-height:1.55}
  .opts{display:grid;grid-template-columns:1fr;gap:8px}
  @media(min-width:560px){.opts{grid-template-columns:1fr 1fr 1fr}}
  .opt{display:flex;align-items:center;min-height:56px;padding:10px 13px;border:2px solid var(--line);border-radius:13px;background:#fff;font-size:14.5px;font-weight:600;text-align:left;cursor:pointer;transition:.15s}
  .opt:active{transform:scale(.99)}
  .opt.good{border-color:#10b981;background:var(--ok-soft)}
  .opt.bad{border-color:#f43f5e;background:var(--bad-soft)}
  .opt:disabled{opacity:.75;cursor:default}
  .fb{font-size:12.5px;margin-top:9px;line-height:1.6}
  .fb.ok{color:#047857}.fb.bad{color:#be123c}

  /* ── 어휘 목록 ────────────────────────────────────── */
  .vrow{display:flex;align-items:center;justify-content:space-between;gap:12px;background:#fff;border:1px solid var(--line);border-radius:16px;padding:12px 14px}
  .vrow .w{font-size:18px;font-weight:800;color:#1e1b4b}
  .vrow .m{font-size:13.5px;color:var(--ink-2);margin-top:1px}
  .vrow .meta{font-size:11.5px;color:#9a9ab8;margin-top:3px}
  .pill{font-size:11px;font-weight:800;padding:3px 8px;border-radius:999px;white-space:nowrap}
  .pill.new{background:#eef2ff;color:#4338ca}
  .pill.learn{background:var(--amber-soft);color:#b45309}
  .pill.master{background:var(--ok-soft);color:#047857}
  .filters{display:flex;gap:6px;overflow-x:auto;padding-bottom:2px;scrollbar-width:none}
  .filters::-webkit-scrollbar{display:none}
  .chip{min-height:44px;padding:0 14px;border-radius:999px;border:1px solid #d4d4e4;background:#fff;font-size:13.5px;font-weight:700;color:#55557a;white-space:nowrap;cursor:pointer}
  .chip.on{background:var(--indigo);border-color:var(--indigo);color:#fff}

  /* ── 기록 ─────────────────────────────────────────── */
  .stats{display:grid;grid-template-columns:1fr 1fr 1fr;gap:9px;margin-bottom:12px}
  .stat{background:#fff;border:1px solid var(--line);border-radius:18px;padding:14px 10px;text-align:center}
  .stat .n{font-size:21px;font-weight:800;margin-top:2px}
  .stat .l{font-size:11.5px;color:var(--muted);font-weight:600}
  .dots{display:flex;gap:6px}
  .dot{width:32px;height:32px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:13px;font-weight:800}
  .dot.done{background:var(--ok);color:#fff}
  .dot.todo{border:2px dashed #cfcfe0}
  .wk{display:flex;align-items:center;gap:10px;font-size:13px}
  .wk .track{flex:1;height:8px;background:#ececf6;border-radius:999px;overflow:hidden}
  .wk .fill{height:100%;border-radius:999px;background:var(--indigo)}
  .wk .fill.ok{background:var(--ok)}
  .sess{border:1px solid var(--line);border-radius:14px;padding:11px 13px;font-size:13.5px}
  .sess summary{display:flex;justify-content:space-between;gap:8px;cursor:pointer;font-weight:700}
  .sess .body{margin-top:9px;font-size:12.5px;color:var(--ink-2);line-height:1.7}

  /* ── 부모 모드 ────────────────────────────────────── */
  .pnav{display:flex;flex-wrap:wrap;gap:6px;margin-bottom:14px}
  .pnav::-webkit-scrollbar{display:none}
  .pnav button{min-height:44px;padding:0 14px;border-radius:12px;background:#ececf6;color:#55557a;font-size:13.5px;font-weight:700;white-space:nowrap;cursor:pointer}
  .pnav button.on{background:var(--indigo);color:#fff}
  .box{border:1px dashed #cfcfe0;border-radius:16px;padding:14px;background:#fbfbfe}
  .prow{display:flex;align-items:center;justify-content:space-between;gap:10px;border:1px solid var(--line);border-radius:14px;padding:11px 13px;font-size:13.5px;background:#fff}
  .prow .bad{color:#be123c;font-weight:700}
  .draft{display:flex;align-items:center;justify-content:space-between;gap:10px;border:1px solid var(--line);border-radius:16px;padding:12px 13px;background:#fff}
  .draft .thumb{width:54px;height:54px;border-radius:10px;object-fit:cover;background:#ececf6;flex:none}
  .draft .t{font-size:13.5px;font-weight:700}
  .draft .s{font-size:12px;color:var(--muted);margin-top:2px}
  .rev-panel{display:flex;gap:8px;align-items:flex-start;border:1px solid var(--line);border-radius:14px;padding:10px;background:#fff}
  .rev-panel .n{font-size:11px;font-weight:800;color:#a5b4fc;padding-top:12px;flex:none}
  .rev-panel textarea{min-height:64px;font-size:14.5px}
  .rev-word{display:grid;grid-template-columns:1.4fr 1fr 1.6fr auto;gap:6px;align-items:center}
  .rev-word input{padding:10px 12px;font-size:14.5px;border-radius:11px}
  .rev-q{border:1px solid var(--line);border-radius:16px;padding:12px;background:#fff}
  .rev-q input{padding:10px 12px;font-size:14px;border-radius:11px}
  .rev-opt{display:flex;align-items:center;gap:8px;margin-top:6px}
  .rev-opt input[type=radio]{width:20px;height:20px;accent-color:var(--indigo);flex:none}
  .rev-opt input[type=text]{flex:1}
  .zoom{position:fixed;inset:0;background:rgba(15,15,35,.92);z-index:95;display:flex;align-items:center;justify-content:center;padding:16px}
  .zoom img{max-width:100%;max-height:100%;object-fit:contain;border-radius:12px}

  /* ── 모달 ─────────────────────────────────────────── */
  .modal{position:fixed;inset:0;z-index:90;display:flex;align-items:center;justify-content:center;padding:20px;background:rgba(15,15,35,.5)}
  .sheet{width:100%;max-width:420px;background:#fff;border-radius:24px;padding:22px;box-shadow:0 24px 60px rgba(15,15,35,.35);max-height:88vh;overflow-y:auto}
  .gate-q{font-size:30px;font-weight:800;text-align:center;margin:18px 0;letter-spacing:.04em}
  .gate-in{height:62px;font-size:24px;font-weight:800;text-align:center}

  /* ── 토스트 · 속도 ────────────────────────────────── */
  .toast{position:fixed;left:50%;bottom:86px;transform:translateX(-50%) translateY(10px);z-index:99;max-width:88%;padding:12px 18px;border-radius:14px;background:#191934;color:#fff;font-size:14px;font-weight:600;opacity:0;pointer-events:none;transition:.25s}
  .toast.on{opacity:1;transform:translateX(-50%) translateY(0)}
  .rate{display:none}
  .bar{height:8px;border-radius:999px;background:#ececf6;overflow:hidden;margin-top:8px}
  .bar>i{display:block;height:100%;background:var(--indigo);border-radius:999px;transition:width .3s}
  .status{font-size:12.5px;color:var(--muted);margin-top:8px;line-height:1.6}

  @media (max-width:400px){
    .panel .txt{font-size:17px}
    .hero h2{font-size:19px}
    .tab{font-size:13.5px;padding:0 6px}
    .rev-word{grid-template-columns:1fr 1fr;gap:6px}
  }
  @media (prefers-reduced-motion:reduce){*{transition:none!important;animation:none!important}}
</style>
</head>
<body>
<div class="wrap">

  <header class="top">
    <div>
      <h1 class="app-title">📖 동윤이의 리딩 버디</h1>
      <p class="sub">노블 한 권을 읽고, 어휘를 쌓고, 내용을 확인해요</p>
    </div>
    <button id="parentBtn" class="btn tiny ghost">⚙ 부모</button>
  </header>

  <!-- ══ 아이 화면 ══ -->
  <div id="kidWrap">
    <nav class="tabs" role="tablist">
      <button class="tab on" data-tab="today" role="tab">📚 오늘</button>
      <button class="tab" data-tab="vocab" role="tab">💡 어휘</button>
      <button class="tab" data-tab="wrong" role="tab">🔁 오답 <span id="wrongN" class="badge">0</span></button>
      <button class="tab" data-tab="history" role="tab">📈 기록</button>
    </nav>

    <!-- 오늘 -->
    <section id="v-today" class="pg" style="margin-top:14px">
      <div class="hero">
        <div class="hero-row">
          <div style="min-width:0">
            <div class="eyebrow">Today's reading</div>
            <h2 id="heroTitle">아직 책이 없어요</h2>
            <p id="heroSub">부모님께 ⚙ 부모에서 책과 페이지를 등록해 달라고 해요.</p>
          </div>
          <span class="chip-level" id="heroLevel">AR 2.5~3.5</span>
        </div>
        <div class="hero-row" style="margin-top:14px">
          <div class="seg" id="pagePicker"></div>
          <div style="font-size:12px;color:#c7d2fe" id="pageInfo"></div>
        </div>
        <div class="bar" style="background:rgba(255,255,255,.18)"><i id="heroBar" style="background:#a5f3d0;width:0%"></i></div>
      </div>

      <div class="card">
        <div class="card-head">
          <h3 class="card-title"><span>🖼️</span> 이 페이지 지문</h3>
          <div class="row" style="gap:6px"><button id="rateBtn" class="btn sm ghost">🙂 보통</button><button id="readAllBtn" class="btn sm soft">🔊 페이지 읽기</button></div>
        </div>
        <div id="passage" class="passage"></div>
      </div>

      <div class="card">
        <div class="card-head">
          <h3 class="card-title"><span>💡</span> 이 페이지 단어 <span id="wordCount" class="hint" style="margin:0"></span></h3>
          <button id="readWordsBtn" class="btn sm soft">🔊 단어 듣기</button>
        </div>
        <div id="vocabGrid" class="wgrid"></div>
      </div>

      <div class="card">
        <div class="card-head" style="margin-bottom:6px">
          <h3 class="card-title"><span>✏️</span> 확인 퀴즈</h3>
        </div>
        <div class="subnav">
          <button id="qTabWord" class="on">1. 단어</button>
          <button id="qTabRead">2. 내용 이해</button>
        </div>
        <div id="quizBody"></div>
      </div>

      <button id="recordBtn" class="btn primary block" style="margin-bottom:16px">✅ 오늘 학습 완료 기록하기</button>
    </section>

    <!-- 어휘 -->
    <section id="v-vocab" class="pg hidden" style="margin-top:14px">
      <div class="card">
        <div class="card-head">
          <h3 class="card-title"><span>💡</span> <span id="vocabBookName">이 책의 어휘</span></h3>
          <span class="hint" id="vocabTotal" style="margin:0"></span>
        </div>
        <div class="filters" id="vocabFilters" style="margin-bottom:12px">
          <button class="chip on" data-f="all">전체</button>
          <button class="chip" data-f="new">새 단어</button>
          <button class="chip" data-f="learn">학습 중</button>
          <button class="chip" data-f="master">익힌 단어</button>
        </div>
        <div id="vocabList" class="stack"></div>
      </div>
      <p class="hint" style="text-align:center">한 페이지에서 다시 나온 단어는 <b>등장 횟수</b>가 쌓여요. 많이 나올수록 꼭 외워야 하는 단어예요.</p>
    </section>

    <!-- 오답 -->
    <section id="v-wrong" class="pg hidden" style="margin-top:14px">
      <div class="card">
        <div class="card-head">
          <h3 class="card-title"><span>🔁</span> 다시 볼 문제</h3>
          <span class="hint" id="wrongCount" style="margin:0"></span>
        </div>
        <p class="hint" style="margin:-4px 0 12px">틀린 문제를 다시 맞히면 목록에서 사라져요.</p>
        <div id="wrongList" class="stack"></div>
      </div>
    </section>

    <!-- 기록 -->
    <section id="v-history" class="pg hidden" style="margin-top:14px">
      <div class="stats" id="histStats"></div>
      <div class="card">
        <div class="card-head">
          <h3 class="card-title"><span>🗓️</span> 이번 주 <span class="hint" id="weekCount" style="margin:0"></span></h3>
        </div>
        <div class="row between">
          <div class="dots" id="weekDots"></div>
          <span class="hint" id="weekText" style="margin:0"></span>
        </div>
      </div>
      <div class="card">
        <div class="card-head"><h3 class="card-title"><span>📒</span> 학습 일지</h3></div>
        <div id="histSessions" class="stack"></div>
      </div>
      <p class="hint" style="text-align:center">기록은 이 브라우저에만 저장돼요. ⚙ 부모 → 백업에서 파일로 보관할 수 있어요.</p>
    </section>
  </div>

  <!-- ══ 부모 화면 ══ -->
  <section id="parentWrap" class="hidden">
    <div class="row between" style="margin-bottom:12px">
      <h2 style="margin:0;font-size:20px;font-weight:800">⚙ 부모 설정</h2>
      <button id="parentBack" class="btn tiny ghost">← 학습으로</button>
    </div>

    <div class="pnav" id="pnav">
      <button data-p="book" class="on">책 · 챕터</button>
      <button data-p="upload">사진 → 분석</button>
      <button data-p="review">승인 대기</button>
      <button data-p="pages">페이지 관리</button>
      <button data-p="ai">AI 설정</button>
      <button data-p="backup">백업</button>
    </div>

    <!-- 책 · 챕터 -->
    <div id="pp-book" class="pp">
      <div class="card">
        <h3 class="card-title" style="margin-bottom:10px"><span>📚</span> 현재 책</h3>
        <select id="bookSel" style="margin-bottom:6px"></select>
        <p class="hint" id="bookMeta" style="margin:0 0 10px"></p>
        <div class="row wrap">
          <button id="bookAddBtn" class="btn sm soft">➕ 새 책</button>
          <button id="chapterAddBtn" class="btn sm soft">➕ 새 챕터</button>
          <button id="bookDelBtn" class="btn sm danger">책 삭제</button>
        </div>
        <div id="bookForm" class="box hidden" style="margin-top:12px">
          <label class="fld">책 제목</label>
          <input id="bookTitle" placeholder="예: The Secret Garden (Graphic Novel)">
          <label class="fld" style="margin-top:10px">AR 레벨</label>
          <input id="bookAr" value="2.5~3.5">
          <div class="row end" style="margin-top:10px">
            <button id="bookCancel" class="btn sm ghost">취소</button>
            <button id="bookSave" class="btn sm primary">저장</button>
          </div>
        </div>
        <div id="chapterForm" class="box hidden" style="margin-top:12px">
          <label class="fld">챕터 이름</label>
          <input id="chapterTitle" placeholder="예: Chapter 1. The New House">
          <div class="row end" style="margin-top:10px">
            <button id="chapterCancel" class="btn sm ghost">취소</button>
            <button id="chapterSave" class="btn sm primary">저장</button>
          </div>
        </div>
      </div>
      <div class="card">
        <h3 class="card-title" style="margin-bottom:10px"><span>🗂️</span> 챕터</h3>
        <div id="chapterList" class="stack"></div>
      </div>
    </div>

    <!-- 업로드 -->
    <div id="pp-upload" class="pp hidden">
      <div class="card">
        <h3 class="card-title" style="margin-bottom:8px"><span>📸</span> 페이지 사진 올리기</h3>
        <p class="hint">노블 페이지를 찍어 올리면 AI가 <b>지문 · 필수 어휘 · 내용 이해 문제</b>를 뽑아요. 결과는 바로 아이 화면에 가지 않고 <b>승인 대기</b>에 쌓입니다.<br>사진은 <b>인터넷 연결</b>이 필요하고, 1장당 10~30초 걸려요. 분석 결과는 새로고침하면 사라지니 승인까지 마쳐주세요.</p>
        <label class="btn primary block" for="imgInput" style="margin-top:12px">📷 사진 선택 (여러 장 가능)</label>
        <input id="imgInput" type="file" accept="image/*" multiple class="hidden">
        <p id="upStatus" class="status"></p>
        <div id="draftList" class="stack" style="margin-top:12px"></div>
      </div>
      <div class="card">
        <h3 class="card-title" style="margin-bottom:8px"><span>🎯</span> 분석 기준</h3>
        <p class="hint">현재 설정: <b id="critLevel">AR 2.5~3.5</b> · 페이지당 단어 6~8개 · 문제 4~5개<br>책을 바꾸면 그 책의 AR 레벨로 분석해요.</p>
      </div>
    </div>

    <!-- 승인 대기 -->
    <div id="pp-review" class="pp hidden">
      <div class="card">
        <div class="card-head">
          <h3 class="card-title"><span>📝</span> 승인 대기</h3>
          <span class="hint" id="draftCount" style="margin:0"></span>
        </div>
        <p class="hint" style="margin:-4px 0 12px">AI가 뽑은 내용을 확인하고, 틀린 부분을 고친 뒤 승인해 주세요. 승인해야 아이 화면에 들어갑니다.</p>
        <div id="draftQueue" class="stack"></div>
      </div>
    </div>

    <!-- 페이지 관리 -->
    <div id="pp-pages" class="pp hidden">
      <div class="card">
        <div class="card-head">
          <h3 class="card-title"><span>📄</span> 승인된 페이지</h3>
          <span class="hint" id="pagesCount" style="margin:0"></span>
        </div>
        <div id="pagesList" class="stack"></div>
      </div>
    </div>

    <!-- AI 설정 -->
    <div id="pp-ai" class="pp hidden">
      <div class="card">
        <h3 class="card-title" style="margin-bottom:8px"><span>🔑</span> AI 연결</h3>
        <p class="hint">제공사를 고르고 키를 넣으면 사진 분석을 쓸 수 있어요. 키는 이 브라우저에만 저장되고 파일에는 들어가지 않습니다.</p>
        <label class="fld" style="margin-top:12px">제공사</label>
        <select id="provSel">
          <option value="gemini">Google Gemini</option>
          <option value="anthropic">Anthropic (Claude)</option>
        </select>
        <label class="fld" style="margin-top:10px">API 키</label>
        <input id="apiKey" type="password" autocomplete="off" placeholder="AIza…">
        <label class="fld" style="margin-top:10px">모델</label>
        <input id="modelIn" placeholder="gemini-3.8-flash">
        <div class="row wrap" style="margin-top:10px">
          <button id="aiSave" class="btn sm primary">저장</button>
          <button id="aiCheck" class="btn sm ghost">연결 확인</button>
          <button id="aiDel" class="btn sm danger">키 삭제</button>
        </div>
        <p id="aiStatus" class="status"></p>
        <div id="modelList" class="row wrap" style="margin-top:8px"></div>
      </div>
      <div class="card">
        <h3 class="card-title" style="margin-bottom:8px"><span>🎚️</span> 아이 레벨</h3>
        <div class="row">
          <input id="childAr" class="grow" placeholder="2.5~3.5">
          <button id="childArSave" class="btn sm soft">저장</button>
        </div>
        <p class="hint">책마다 다른 AR을 쓰면 그 책 값이 우선 적용돼요.</p>
      </div>
    </div>

    <!-- 백업 -->
    <div id="pp-backup" class="pp hidden">
      <div class="card">
        <h3 class="card-title" style="margin-bottom:8px"><span>💾</span> 데이터 백업</h3>
        <p class="hint">책 · 페이지 · 어휘 · 학습 기록이 모두 들어 있어요. 기기를 바꾸거나 브라우저 기록을 지울 때 사용하세요.</p>
        <div class="row wrap" style="margin-top:12px">
          <button id="expBtn" class="btn soft" style="flex:1">⬇️ 내보내기</button>
          <button id="impBtn" class="btn ghost" style="flex:1">⬆️ 불러오기</button>
          <input id="impFile" type="file" accept=".json,application/json" class="hidden">
        </div>
        <p id="impSt" class="status"></p>
      </div>
      <div class="card">
        <h3 class="card-title" style="margin-bottom:8px"><span>🧹</span> 정리</h3>
        <p class="hint">어휘 학습 기록만 초기화하고 책과 페이지는 남겨요.</p>
        <button id="resetVocab" class="btn sm danger" style="margin-top:10px">어휘 기록 초기화</button>
      </div>
    </div>

    <!-- 검수 편집기 -->
    <div id="pp-editor" class="pp hidden">
      <div class="card">
        <div class="card-head">
          <h3 class="card-title"><span>🔍</span> 페이지 검수</h3>
          <button id="edBack" class="btn tiny ghost">← 목록으로</button>
        </div>
        <img id="edThumb" class="hidden" style="width:100%;max-height:210px;object-fit:contain;border-radius:12px;background:#f1f1f8;margin-bottom:12px" alt="페이지 사진">
        <div class="box" style="margin-bottom:12px">
          <p class="hint" style="margin:0">사진과 지문을 비교하며 고쳐주세요. 고친 내용은 <b>승인</b>을 눌러야 저장됩니다.</p>
        </div>

        <h4 class="card-title" style="margin-bottom:8px">지문</h4>
        <div id="edPanels" class="stack"></div>
        <button id="edAddPanel" class="btn sm ghost" style="margin-top:8px">➕ 문장 추가</button>

        <h4 class="card-title" style="margin:18px 0 8px">어휘</h4>
        <div id="edWords" class="stack"></div>
        <button id="edAddWord" class="btn sm ghost" style="margin-top:8px">➕ 단어 추가</button>

        <h4 class="card-title" style="margin:18px 0 8px">내용 이해 문제</h4>
        <div id="edQs" class="stack"></div>
        <button id="edAddQ" class="btn sm ghost" style="margin-top:8px">➕ 문제 추가</button>

        <div class="row" style="margin-top:18px">
          <button id="edApprove" class="btn primary grow">✅ 승인하고 저장</button>
          <button id="edDrop" class="btn danger">삭제</button>
        </div>
        <p class="hint" style="text-align:center">승인하면 <b id="edTarget">이 챕터</b>의 마지막 페이지로 들어가요.</p>
      </div>
    </div>
  </section>
</div>


<!-- 부모 확인 -->
<div id="gate" class="modal hidden" role="dialog" aria-modal="true">
  <div class="sheet">
    <h2 style="margin:0;font-size:19px;font-weight:800">부모님 확인</h2>
    <p class="hint">아이가 실수로 설정을 바꾸지 않도록 확인해요.</p>
    <p class="gate-q" id="gateQ">7 × 8 = ?</p>
    <input id="gateIn" class="gate-in" type="text" inputmode="numeric" autocomplete="off" aria-label="정답">
    <div class="row" style="justify-content:flex-end;margin-top:14px">
      <button id="gateCancel" class="btn ghost">취소</button>
      <button id="gateOk" class="btn primary">확인</button>
    </div>
  </div>
</div>

<!-- 이미지 확대 -->
<div id="zoom" class="zoom hidden"><img id="zoomImg" alt="확대"></div>

<!-- 불러오기 -->
<div id="impModal" class="modal hidden" role="dialog" aria-modal="true">
  <div class="sheet">
    <h2 style="margin:0;font-size:19px;font-weight:800">백업 불러오기</h2>
    <p class="hint" id="impInfo"></p>
    <div class="stack" style="margin-top:16px">
      <button id="impMerge" class="btn primary block">합치기</button>
      <button id="impReplace" class="btn danger block">덮어쓰기</button>
      <button id="impCancel" class="btn ghost block">취소</button>
    </div>
  </div>
</div>

<div id="toast" class="toast" role="status" aria-live="polite"></div>
<script>
/* ═══════════ 공통 ═══════════ */
const $ = id => document.getElementById(id);
const KEY = 'readingBuddy:dongyoon';
const KEY_API = 'readingBuddy:apiKey';
const esc = t => String(t == null ? '' : t).replace(/[&<>"']/g, c => ({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]));
const norm = s => String(s || '').toLowerCase().replace(/[^a-z' ]/g, '').replace(/\s+/g, ' ').trim();
const uid = p => p + Date.now().toString(36) + Math.random().toString(36).slice(2, 6);
const shuf = a => a.map(x => [Math.random(), x]).sort((a, b) => a[0] - b[0]).map(x => x[1]);
const pad2 = n => String(n).padStart(2, '0');
const ymd = d => d.getFullYear() + '-' + pad2(d.getMonth() + 1) + '-' + pad2(d.getDate());
const md = t => { const d = new Date(t + 'T00:00:00'); return (d.getMonth() + 1) + '/' + d.getDate(); };
const parseYmd = t => new Date(t + 'T00:00:00');
const mondayOf = d => { const x = new Date(d.getFullYear(), d.getMonth(), d.getDate()); x.setDate(x.getDate() - ((x.getDay() + 6) % 7)); return x; };
const weekKey = d => ymd(mondayOf(d));
let toastT;
function toast(m) { const t = $('toast'); t.textContent = m; t.classList.add('on'); clearTimeout(toastT); toastT = setTimeout(() => t.classList.remove('on'), 2400); }

/* ═══════════ 상태 ═══════════ */
const EMPTY = () => ({
  v: 2, name: '동윤', ar: '2.5~3.5', books: [], vocab: {}, sessions: [], wrong: [],
  ai: { provider: 'gemini', models: { gemini: 'gemini-3.8-flash', anthropic: 'claude-sonnet-5-5' } },
  active: { book: '', chapter: '', page: 0 }
});
let S = EMPTY();

const AI_DEFAULT = { provider: 'gemini', models: { gemini: 'gemini-3.8-flash', anthropic: 'claude-sonnet-5-5' } };
function normalizeAI(a) {
  a = a && typeof a === 'object' ? a : {};
  const out = { provider: a.provider === 'anthropic' ? 'anthropic' : 'gemini', models: Object.assign({}, AI_DEFAULT.models, a.models || {}) };
  if (a.model && typeof a.model === 'string') out.models[out.provider] = a.model;
  return out;
}

function normalizeState(o) {
  const base = EMPTY();
  if (!o || typeof o !== 'object') return base;
  const out = Object.assign(base, {
    name: typeof o.name === 'string' ? o.name : '동윤',
    ar: typeof o.ar === 'string' ? o.ar : '2.5~3.5',
    books: Array.isArray(o.books) ? o.books : [],
    vocab: (o.vocab && typeof o.vocab === 'object') ? o.vocab : {},
    sessions: Array.isArray(o.sessions) ? o.sessions : [],
    wrong: Array.isArray(o.wrong) ? o.wrong : [],
    ai: normalizeAI(o.ai),
    active: Object.assign({ book: '', chapter: '', page: 0 }, o.active || {})
  });
  out.books = out.books.filter(b => b && typeof b.id === 'string').map(b => ({
    id: b.id, title: b.title || '제목 없음', ar: b.ar || out.ar,
    chapters: (Array.isArray(b.chapters) ? b.chapters : []).filter(c => c && c.id).map(c => ({
      id: c.id, title: c.title || 'Chapter',
      pages: (Array.isArray(c.pages) ? c.pages : []).filter(p => p && Array.isArray(p.panels)).map(p => ({
        id: p.id || uid('p'), n: p.n || 1, date: p.date || ymd(new Date()), done: !!p.done,
        panels: (p.panels || []).filter(x => x && x.text).map((x, i) => ({ n: x.n || i + 1, text: x.text })),
        words: (p.words || []).filter(x => x && x.w).map(x => ({ w: x.w, ipa: x.ipa || '', ko: x.ko || '' })),
        questions: (p.questions || []).filter(x => x && x.q).map(x => ({ q: x.q, ko: x.ko || '', a: x.a || '', o: Array.isArray(x.o) ? x.o : [], ex: x.ex || '' }))
      }))
    }))
  }));
  if (!out.books.length) out.books.push({ id: uid('b'), title: '우리 책', ar: out.ar, chapters: [{ id: uid('c'), title: 'Chapter 1', pages: [] }] });
  out.books.forEach(b => { if (!b.chapters.length) b.chapters.push({ id: uid('c'), title: 'Chapter 1', pages: [] }); });
  const b0 = out.books.find(b => b.id === out.active.book) || out.books[0];
  out.active.book = b0.id;
  const c0 = b0.chapters.find(c => c.id === out.active.chapter) || b0.chapters[0];
  out.active.chapter = c0.id;
  out.active.page = Math.max(0, Math.min(out.active.page || 0, Math.max(0, c0.pages.length - 1)));
  return out;
}

function load() {
  let raw = null;
  try { raw = JSON.parse(localStorage.getItem(KEY) || 'null'); } catch (e) {}
  if (raw && typeof raw === 'object') {
    if (!Array.isArray(raw.books) && Array.isArray(raw.sessions)) {
      /* v1 파일에서 넘어오기: 마지막 페이지 한 장을 첫 페이지로 */
      const book = { id: uid('b'), title: '우리 책', ar: '2.5~3.5', chapters: [{ id: uid('c'), title: 'Chapter 1', pages: [] }] };
      if (raw.page && Array.isArray(raw.page.panels) && raw.page.panels.length) {
        book.chapters[0].pages.push({
          id: uid('p'), n: 1, date: ymd(new Date()), done: false,
          panels: raw.page.panels, words: raw.page.words || [], questions: raw.page.questions || []
        });
      }
      raw.books = [book];
      raw.vocab = {};
      raw.active = { book: book.id, chapter: book.chapters[0].id, page: 0 };
    }
    S = normalizeState(raw);
  } else {
    S = normalizeState(null);
  }
}
function save() {
  try { localStorage.setItem(KEY, JSON.stringify(S)); }
  catch (e) { toast('저장 공간이 부족해요. 백업 후 사진 분석 결과를 정리해 주세요.'); }
}
const book = () => S.books.find(b => b.id === S.active.book) || S.books[0];
const chapter = () => { const b = book(); return b.chapters.find(c => c.id === S.active.chapter) || b.chapters[0]; };
const page = () => { const c = chapter(); return c.pages[S.active.page] || null; };
const bank = () => { const b = book(); if (!S.vocab[b.id]) S.vocab[b.id] = {}; return S.vocab[b.id]; };
const bookWordCount = () => Object.keys(bank()).length;

/* ═══════════ 음성 ═══════════ */
let voice = null, tok = 0, ri = 1;
const RATES = [[.6, '🐢 느리게'], [.85, '🙂 보통'], [1, '🐇 빠르게']];
const pickVoice = () => {
  try {
    const en = speechSynthesis.getVoices().filter(v => /^en/i.test(v.lang.replace('_', '-')));
    voice = en.find(v => /^en-US/i.test(v.lang) && /Google|Samantha|Aaron|Natural|Enhanced/i.test(v.name)) || en.find(v => /^en-US/i.test(v.lang)) || en[0] || null;
  } catch (e) {}
};
if ('speechSynthesis' in window) { pickVoice(); speechSynthesis.onvoiceschanged = pickVoice; }
function say(text, done, rate) {
  if (!('speechSynthesis' in window)) { if (done) done(); return; }
  const u = new SpeechSynthesisUtterance(text);
  u.lang = 'en-US'; if (voice) u.voice = voice; u.rate = rate || RATES[ri][0];
  let d = 0; u.onend = u.onerror = () => { if (!d) { d = 1; if (done) done(); } };
  try { speechSynthesis.speak(u); } catch (e) { if (done) done(); }
}
function stopAll() {
  tok++; try { speechSynthesis.cancel(); } catch (e) {}
  clearInterval(readTimer); readTimer = null;
  document.querySelectorAll('.panel.speaking, .wcard.speaking').forEach(e => e.classList.remove('speaking'));
  const pgs = $('passage'); if (pgs) pgs.classList.remove('reading');
  if ($('readAllBtn')) $('readAllBtn').textContent = '🔊 페이지 읽기';
  if ($('readWordsBtn')) $('readWordsBtn').textContent = '🔊 단어 듣기';
}
const speak = t => { stopAll(); say(t); };
const speakLetters = w => { stopAll(); say(String(w).replace(/[^A-Za-z ]/g, '').split('').join(', '), null, .7); };
$('rateBtn').onclick = function () {
  ri = (ri + 1) % 3; this.textContent = RATES[ri][1]; speak('Ready');
};
let unlocked = false;
document.addEventListener('pointerdown', () => {
  if (unlocked || !('speechSynthesis' in window)) return;
  unlocked = true;
  try { const u = new SpeechSynthesisUtterance(' '); u.volume = 0; speechSynthesis.speak(u); } catch (e) {}
}, { once: true });

/* ═══════════ 지문 단어 탭 ═══════════ */
function wrapWords(el) {
  [...el.childNodes].forEach(node => {
    if (node.nodeType !== 3) return;
    const frag = document.createDocumentFragment();
    node.textContent.split(/([A-Za-z']+)/).forEach(part => {
      if (/^[A-Za-z']+$/.test(part)) {
        const s = document.createElement('span');
        s.className = 'tap-word'; s.textContent = part; frag.appendChild(s);
      } else frag.appendChild(document.createTextNode(part));
    });
    node.replaceWith(frag);
  });
}

/* ═══════════ 탭 이동 ═══════════ */
let curTab = 'today';
function goTab(t) {
  curTab = t; stopAll();
  document.querySelectorAll('.tab').forEach(b => b.classList.toggle('on', b.dataset.tab === t));
  ['today', 'vocab', 'wrong', 'history'].forEach(k => $('v-' + k).classList.toggle('hidden', k !== t));
  if (t === 'today') renderToday();
  if (t === 'vocab') renderVocab();
  if (t === 'wrong') renderWrong();
  if (t === 'history') renderHistory();
  window.scrollTo({ top: 0 });
}
document.querySelectorAll('.tab').forEach(b => b.onclick = () => goTab(b.dataset.tab));

/* ═══════════ 오늘 ═══════════ */
let qMode = 'word', qData = [], qPick = {};
function renderToday() {
  const b = book(), c = chapter(), p = page();
  $('heroTitle').textContent = b.title;
  $('heroLevel').textContent = 'AR ' + (b.ar || S.ar);
  $('heroSub').textContent = c.title + (p ? ' · p.' + p.n : ' · 페이지 없음');
  const pages = c.pages;
  $('pagePicker').innerHTML = pages.length
    ? pages.map((x, i) => '<button data-i="' + i + '" class="' + (i === S.active.page ? 'on' : '') + '">' + (x.n || i + 1) + '</button>').join('')
    : '';
  $('pageInfo').textContent = pages.length ? (S.active.page + 1) + ' / ' + pages.length + ' 페이지' : '';
  const done = pages.filter(x => x.done).length;
  $('heroBar').style.width = pages.length ? Math.round(done / pages.length * 100) + '%' : '0%';

  if (!p) {
    $('passage').innerHTML = '<div class="empty">이 챕터에는 아직 페이지가 없어요.<br><span style="font-size:13px;font-weight:500">부모님이 ⚙ 부모 → 사진 → 분석에서 페이지를 올려 주세요.</span></div>';
    $('vocabGrid').innerHTML = '';
    $('wordCount').textContent = '';
    $('quizBody').innerHTML = '<p class="empty">페이지를 올리면 퀴즈가 생겨요.</p>';
    $('recordBtn').textContent = '✅ 오늘 학습 완료 기록하기';
    return;
  }
  renderPassage(p);
  renderPageWords(p);
  renderQuiz(p);
  const today = ymd(new Date());
  $('recordBtn').textContent = S.sessions.some(s => s.date === today) ? '✅ 오늘 기록 완료 (누르면 취소)' : '✅ 오늘 학습 완료 기록하기';
}

function renderPassage(p) {
  $('passage').innerHTML = p.panels.map((x, i) =>
    '<div class="panel" data-i="' + i + '"><div class="no">' + (x.n || i + 1) + '</div><div class="txt"></div></div>').join('');
  p.panels.forEach((x, i) => {
    const el = $('passage').querySelector('.panel[data-i="' + i + '"] .txt');
    el.textContent = x.text;
    wrapWords(el);
  });
}
$('passage').onclick = e => {
  const w = e.target.closest('.tap-word');
  if (!w) return;
  w.classList.add('hit'); setTimeout(() => w.classList.remove('hit'), 600);
  speak(w.textContent);
};
$('pagePicker').onclick = e => {
  const b = e.target.closest('button[data-i]');
  if (!b) return;
  S.active.page = +b.dataset.i; save(); stopAll(); renderToday();
  window.scrollTo({ top: 0, behavior: 'smooth' });
};
let readTimer = null;
const CHROME_DESKTOP = /Chrome/.test(navigator.userAgent) && !/Mobile|Android|iPhone|iPad/.test(navigator.userAgent);
function passageText(p) {
  return p.panels.map(x => {
    const t = String(x.text || '').trim().replace(/\s+/g, ' ');
    return /[.!?"'’”]$/.test(t) ? t : t + '.';
  }).join(' ').trim();
}
$('readAllBtn').onclick = () => {
  if ($('passage').classList.contains('reading')) return stopAll();
  const p = page(); if (!p || !p.panels.length) return;
  stopAll();
  const my = tok;
  $('readAllBtn').textContent = '⏹️ 멈추기';
  $('passage').classList.add('reading');
  if (!('speechSynthesis' in window)) return stopAll();

  const full = passageText(p);
  const starts = [];
  let pos = 0;
  p.panels.forEach(x => { starts.push(pos); pos += String(x.text || '').trim().length + 1; });

  const u = new SpeechSynthesisUtterance(full);
  u.lang = 'en-US';
  if (voice) u.voice = voice;
  u.rate = RATES[ri][0];
  let last = -1;
  u.onboundary = ev => {
    if (my !== tok) return;
    const ci = ev.charIndex || 0;
    let k = 0;
    for (let i = 0; i < starts.length; i++) if (ci >= starts[i]) k = i;
    if (k === last) return;
    last = k;
    document.querySelectorAll('.panel.speaking').forEach(e => e.classList.remove('speaking'));
    const el = $('passage').querySelector('.panel[data-i="' + k + '"]');
    if (el) { el.classList.add('speaking'); el.scrollIntoView({ block: 'center', behavior: 'smooth' }); }
  };
  u.onend = u.onerror = () => { if (my === tok) stopAll(); };
  /* Chrome 데스크톱은 긴 문장을 15초쯤에서 끊는 버그가 있어 살짝 깨워준다 */
  if (CHROME_DESKTOP) {
    readTimer = setInterval(() => {
      if (my !== tok) { clearInterval(readTimer); return; }
      try { speechSynthesis.pause(); speechSynthesis.resume(); } catch (e) {}
    }, 9000);
  }
  try { speechSynthesis.speak(u); } catch (e) { stopAll(); }
};

function renderPageWords(p) {
  $('wordCount').textContent = p.words.length + '개';
  $('vocabGrid').innerHTML = p.words.length
    ? p.words.map((w, i) =>
      '<div class="wcard" data-i="' + i + '"><div><div class="word">' + esc(w.w) + '</div>' +
      '<div class="ipa">' + esc(w.ipa || '') + '</div><div class="ko">' + esc(w.ko || '') + '</div></div>' +
      '<button class="btn round soft" data-say="' + i + '" aria-label="발음">🔊</button></div>').join('')
    : '<p class="hint">이 페이지에는 단어가 없어요.</p>';
}
$('vocabGrid').onclick = e => {
  const b = e.target.closest('[data-say]');
  if (!b) return;
  const p = page(); if (!p) return;
  speak(p.words[+b.dataset.say].w);
};
$('readWordsBtn').onclick = () => {
  if ($('readWordsBtn').textContent.indexOf('멈추기') > -1) return stopAll();
  const p = page(); if (!p || !p.words.length) return;
  stopAll();
  const my = tok;
  $('readWordsBtn').textContent = '⏹️ 멈추기';
  let i = 0;
  const next = () => {
    if (my !== tok) return;
    document.querySelectorAll('.wcard.speaking').forEach(e => e.classList.remove('speaking'));
    if (i >= p.words.length) { stopAll(); return; }
    const el = $('vocabGrid').querySelector('.wcard[data-i="' + i + '"]');
    if (el) el.classList.add('speaking');
    say(p.words[i++].w, () => setTimeout(next, 450));
  };
  next();
};

/* ═══════════ 퀴즈 ═══════════ */
function buildQuiz(mode, p) {
  if (mode === 'read') {
    return p.questions.map((q, i) => ({
      id: 'r:' + p.id + ':' + i, kind: '내용', q: q.q, ko: q.ko, a: q.a,
      o: shuf(q.o.slice()), ex: q.ex, speak: ''
    })).filter(q => q.a && q.o.length >= 2);
  }
  const words = p.words.filter(w => w.w && w.ko);
  const all = Object.values(bank()).filter(x => x.ko);
  return words.map((x, i) => {
    const toWord = i % 2 === 0;
    const others = shuf(all.filter(y => norm(y.w) !== norm(x.w))).slice(0, 2);
    const opts = toWord ? [x.w, ...others.map(y => y.w)] : [x.ko, ...others.map(y => y.ko)];
    return {
      id: 'w:' + norm(x.w), kind: '단어',
      q: toWord ? '「' + x.ko + '」을 뜻하는 단어는?' : '「' + x.w + '」의 뜻으로 알맞은 것은?',
      ko: '', a: toWord ? x.w : x.ko, o: shuf(opts), ex: x.w + ' = ' + x.ko,
      speak: toWord ? '' : x.w
    };
  }).filter(q => new Set(q.o).size === q.o.length);
}
function renderQuiz(p) {
  $('qTabWord').className = qMode === 'word' ? 'on' : '';
  $('qTabRead').className = qMode === 'read' ? 'on' : '';
  qData = buildQuiz(qMode, p);
  if (!qData.length) {
    $('quizBody').innerHTML = '<p class="empty">' + (qMode === 'word'
      ? '이 페이지에는 풀 단어가 없어요.'
      : '이 페이지에는 내용 문제가 없어요. 부모님이 검수할 때 문제를 추가할 수 있어요.') + '</p>';
    return;
  }
  qData.forEach(q => { if (qPick[q.id] === undefined) qPick[q.id] = null; });
  let done = 0, ok = 0;
  const cards = qData.map((q, i) => {
    const picked = qPick[q.id], answered = picked !== null && picked !== undefined;
    if (answered) { done++; if (q.o[picked] === q.a) ok++; }
    const opts = q.o.map((t, j) => {
      let cls = 'opt';
      if (answered) {
        if (t === q.a) cls += ' good';
        else if (j === picked) cls += ' bad';
      }
      return '<button class="' + cls + '" data-i="' + i + '" data-j="' + j + '"' + (answered ? ' disabled' : '') + '>' + 'ABC'[j] + ') ' + esc(t) + '</button>';
    }).join('');
    const fb = !answered ? '' : (q.o[picked] === q.a)
      ? '<p class="fb ok">🎉 정답! ' + esc(q.ex) + '</p>'
      : '<p class="fb bad">정답은 <b>' + esc(q.a) + '</b> 이에요. ' + esc(q.ex) + '</p>';
    return '<div class="qcard"><div class="qhead"><span class="qlabel">' + (qMode === 'word' ? 'Vocabulary' : 'Reading') + ' Q' + (i + 1) + '</span>' +
      '<span class="hint" style="margin:0">' + (qMode === 'word' ? '알맞은 답을 고르세요' : '지문을 보고 고르세요') + '</span></div>' +
      '<p class="qtext">' + esc(q.q) + (q.speak ? ' <button class="btn tiny soft" data-say="' + esc(q.speak) + '">🔊</button>' : '') + '</p>' +
      '<div class="opts">' + opts + '</div>' + fb + '</div>';
  }).join('');
  const label = done === qData.length
    ? ((ok === qData.length ? '🏆 모두 맞혔어요! ' : '결과 ') + ok + '/' + qData.length + ' 정답')
    : ('진행 ' + done + '/' + qData.length + ' · 정답 ' + ok);
  $('quizBody').innerHTML = cards +
    '<div class="row between" style="background:var(--indigo-soft);border-radius:14px;padding:12px"><b style="font-size:14px;color:#312e81">' + label +
    '</b><button id="qRetry" class="btn tiny ghost">🔄 다시 풀기</button></div>';
}
$('qTabWord').onclick = () => { qMode = 'word'; qPick = {}; stopAll(); renderQuiz(page()); };
$('qTabRead').onclick = () => { qMode = 'read'; qPick = {}; stopAll(); renderQuiz(page()); };
$('quizBody').onclick = e => {
  const sp = e.target.closest('[data-say]');
  if (sp) return speak(sp.dataset.say);
  if (e.target.closest('#qRetry')) { qPick = {}; renderQuiz(page()); return; }
  const b = e.target.closest('.opt');
  if (!b) return;
  const i = +b.dataset.i, j = +b.dataset.j, q = qData[i];
  if (qPick[q.id] !== null && qPick[q.id] !== undefined) return;
  qPick[q.id] = j;
  const ok = q.o[j] === q.a;
  recordAnswer(q, ok, q.o[j]);
  refreshWordStats(q, ok);
  renderQuiz(page());
};
function recordAnswer(q, ok, mine) {
  const today = ymd(new Date());
  const i = S.wrong.findIndex(x => x.id === q.id);
  if (ok) { if (i >= 0) S.wrong.splice(i, 1); }
  else if (i >= 0) { S.wrong[i].n++; S.wrong[i].mine = mine; S.wrong[i].date = today; }
  else S.wrong.push({ id: q.id, kind: q.kind, q: q.q, mine, ans: q.a, n: 1, date: today });
  save(); refreshBadges();
}
function refreshWordStats(q, ok) {
  if (q.kind !== '단어') return;
  const b = bank();
  const key = Object.keys(b).find(k => norm(b[k].w) === norm(q.a) || norm(b[k].w) === norm(q.ex.split('=')[0]));
  if (!key) return;
  const z = b[key];
  if (ok) { z.ok = (z.ok || 0) + 1; z.streak = (z.streak || 0) + 1; }
  else { z.bad = (z.bad || 0) + 1; z.streak = 0; }
  save();
}
function refreshBadges() {
  $('wrongN').textContent = S.wrong.length;
  $('wrongCount').textContent = S.wrong.length ? S.wrong.length + '개' : '';
}

/* ═══════════ 어휘 ═══════════ */
let vocabFilter = 'all';
const wordStatus = z => (z.streak >= 2 ? 'master' : (z.bad > 0 || z.ok > 0) ? 'learn' : 'new');
function renderVocab() {
  const b = book();
  $('vocabBookName').textContent = b.title;
  const list = Object.values(bank());
  $('vocabTotal').textContent = list.length + '개';
  document.querySelectorAll('#vocabFilters .chip').forEach(c => c.classList.toggle('on', c.dataset.f === vocabFilter));
  const filtered = list.filter(x => vocabFilter === 'all' || wordStatus(x) === vocabFilter)
    .sort((x, y) => (y.count || 1) - (x.count || 1) || x.w.localeCompare(y.w));
  $('vocabList').innerHTML = filtered.length
    ? filtered.map((x, i) => {
        const st = wordStatus(x);
        const label = st === 'master' ? '익힘' : st === 'learn' ? '학습 중' : '새 단어';
        return '<div class="vrow"><div style="min-width:0"><div class="w">' + esc(x.w) + ' <span class="hint" style="margin:0">' + esc(x.ipa || '') + '</span></div>' +
          '<div class="m">' + esc(x.ko || '') + '</div>' +
          '<div class="meta">' + (x.count || 1) + '회 등장' + (x.bad ? ' · ' + x.bad + '번 틀림' : '') + '</div></div>' +
          '<div class="row" style="gap:8px;flex:none"><span class="pill ' + st + '">' + label + '</span>' +
          '<button class="btn round soft" data-say="' + esc(x.w) + '">🔊</button></div></div>';
      }).join('')
    : '<p class="empty">' + (list.length ? '이 상태의 단어가 없어요.' : '아직 단어가 없어요. 페이지를 승인하면 단어가 쌓여요.') + '</p>';
}
$('vocabFilters').onclick = e => {
  const c = e.target.closest('.chip'); if (!c) return;
  vocabFilter = c.dataset.f; renderVocab();
};
$('vocabList').onclick = e => {
  const b = e.target.closest('[data-say]'); if (b) speak(b.dataset.say);
};

/* ═══════════ 오답 ═══════════ */
function renderWrong() {
  refreshBadges();
  $('wrongList').innerHTML = S.wrong.length
    ? [...S.wrong].reverse().map(x =>
      '<div class="vrow" style="align-items:flex-start"><div style="min-width:0">' +
      '<div class="meta" style="margin:0 0 3px">[' + esc(x.kind) + ' · ' + md(x.date) + '] · ' + x.n + '회 틀림</div>' +
      '<div style="font-size:14px;font-weight:700;line-height:1.5">' + esc(x.q) + '</div>' +
      '<div class="m" style="margin-top:4px;font-size:13px">내 답 <s style="color:#be123c">' + esc(x.mine) + '</s> → 정답 <b style="color:#047857">' + esc(x.ans) + '</b></div></div></div>').join('')
    : '<p class="empty">복습할 오답이 없어요 👏 퀴즈를 풀면 여기에 쌓여요.</p>';
}

/* ═══════════ 기록 ═══════════ */
function renderHistory() {
  const wmap = bank();
  const byWeek = {};
  S.sessions.forEach(x => byWeek[x.week] = (byWeek[x.week] || 0) + 1);
  let cur = mondayOf(new Date()), streak = 0;
  if ((byWeek[ymd(cur)] || 0) < 2) cur.setDate(cur.getDate() - 7);
  while ((byWeek[ymd(cur)] || 0) >= 2) { streak++; cur.setDate(cur.getDate() - 7); }
  $('histStats').innerHTML =
    '<div class="stat"><div style="font-size:18px">📚</div><div class="n">' + S.sessions.length + '</div><div class="l">학습 횟수</div></div>' +
    '<div class="stat"><div style="font-size:18px">💡</div><div class="n">' + Object.keys(wmap).length + '</div><div class="l">누적 단어</div></div>' +
    '<div class="stat"><div style="font-size:18px">🔥</div><div class="n">' + streak + '</div><div class="l">연속 목표(주)</div></div>';

  const now = new Date(), wk = weekKey(now), today = ymd(now);
  const n = byWeek[wk] || 0;
  let dots = '';
  for (let i = 0; i < Math.max(2, n); i++)
    dots += '<span class="dot ' + (i < n ? 'done' : 'todo') + '">' + (i < n ? '✓' : '') + '</span>';
  $('weekDots').innerHTML = dots;
  $('weekCount').textContent = n + ' / 2회';
  $('weekText').textContent = n >= 2 ? '🎉 목표 달성!' : '목표까지 ' + (2 - n) + '회';

  const sessions = [...S.sessions].sort((a, b) => b.date.localeCompare(a.date));
  $('histSessions').innerHTML = sessions.length
    ? sessions.map(s => {
        const pgs = (s.pages || []).map(pid => {
          for (const b of S.books) for (const c of b.chapters) { const p = c.pages.find(x => x.id === pid); if (p) return c.title + ' p.' + p.n; }
          return null;
        }).filter(Boolean);
        return '<details class="sess"><summary><span>' + md(s.date) + ' · ' + esc(s.chapter || '') + '</span>' +
          '<span class="hint" style="margin:0">단어 ' + (s.words || []).length + '개</span></summary>' +
          '<div class="body">' + (pgs.length ? '<p style="margin:0 0 6px">📄 ' + esc(pgs.join(' · ')) + '</p>' : '') +
          ((s.words || []).slice(0, 12).map(w => '<span style="display:inline-block;margin:0 6px 4px 0">' + esc(w.w) + '</span>').join('')) +
          '<button class="btn tiny danger" data-del="' + s.id + '" style="margin-top:8px">기록 삭제</button></div></details>';
      }).join('')
    : '<p class="empty">아직 기록이 없어요.<br>학습을 마치고 기록 버튼을 눌러보세요.</p>';
}
$('histSessions').onclick = e => {
  const b = e.target.closest('[data-del]'); if (!b) return;
  if (!confirm('이 기록을 삭제할까요? (페이지와 단어는 남아요)')) return;
  S.sessions = S.sessions.filter(x => x.id !== b.dataset.del);
  save(); renderHistory();
};

$('recordBtn').onclick = () => {
  const p = page(), c = chapter(), b = book();
  if (!p) return;
  const today = ymd(new Date());
  const i = S.sessions.findIndex(s => s.date === today);
  if (i >= 0) {
    if (!confirm('오늘 학습 기록을 취소할까요?')) return;
    S.sessions.splice(i, 1); save(); renderToday(); renderHistory(); toast('오늘 기록을 취소했어요'); return;
  }
  p.done = true;
  S.sessions.push({
    id: uid('s'), date: today, week: weekKey(new Date()),
    chapter: b.title + ' · ' + c.title, pages: [p.id],
    words: p.words.map(w => ({ w: w.w, ko: w.ko }))
  });
  save(); renderToday(); refreshBadges(); toast('오늘 학습을 기록했어요');
};

/* ═══════════ 부모 모드 ═══════════ */
let gateAns = 0;
function openGate() {
  const a = 3 + Math.floor(Math.random() * 7), b = 3 + Math.floor(Math.random() * 7);
  gateAns = a * b;
  $('gateQ').textContent = a + ' × ' + b + ' = ?';
  $('gateIn').value = '';
  $('gate').classList.remove('hidden');
  setTimeout(() => $('gateIn').focus(), 60);
}
const closeGate = () => $('gate').classList.add('hidden');
$('parentBtn').onclick = openGate;
$('gateCancel').onclick = closeGate;
$('gateIn').onkeydown = e => { if (e.key === 'Enter') $('gateOk').click(); };
$('gateOk').onclick = () => {
  if (String(parseInt($('gateIn').value, 10)) === String(gateAns)) { closeGate(); openParent(); }
  else { toast('정답이 아니에요. 다시 계산해 보세요.'); $('gateIn').value = ''; $('gateIn').focus(); }
};
$('gate').onclick = e => { if (e.target === $('gate')) closeGate(); };

function openParent() {
  stopAll();
  $('kidWrap').classList.add('hidden');
  $('parentWrap').classList.remove('hidden');
  $('rateBtn').classList.add('hidden');
  $('parentBtn').classList.add('hidden');
  renderBooks(); renderDrafts(); renderPages(); renderAI(); renderBackupHint();
  showPP('book');
  window.scrollTo({ top: 0 });
}
$('parentBack').onclick = () => {
  $('parentWrap').classList.add('hidden');
  $('kidWrap').classList.remove('hidden');
  $('rateBtn').classList.remove('hidden');
  $('parentBtn').classList.remove('hidden');
  renderToday(); refreshBadges();
  window.scrollTo({ top: 0 });
};
function showPP(id) {
  document.querySelectorAll('.pp').forEach(e => e.classList.toggle('hidden', e.id !== 'pp-' + id));
  document.querySelectorAll('#pnav button').forEach(b => b.classList.toggle('on', b.dataset.p === id));
  if (id === 'review') renderDrafts();
  if (id === 'pages') renderPages();
  window.scrollTo({ top: 0 });
}
$('pnav').onclick = e => {
  const b = e.target.closest('button[data-p]');
  if (b) showPP(b.dataset.p);
};

/* ── 책 · 챕터 ── */
function renderBooks() {
  const b = book();
  $('bookSel').innerHTML = S.books.map(x => '<option value="' + x.id + '"' + (x.id === b.id ? ' selected' : '') + '>' + esc(x.title) + '</option>').join('');
  $('bookMeta').textContent = 'AR ' + (b.ar || S.ar) + ' · 챕터 ' + b.chapters.length + '개 · 페이지 ' + b.chapters.reduce((n, c) => n + c.pages.length, 0) + '장';
  $('chapterList').innerHTML = b.chapters.map(c =>
    '<button class="prow" data-ch="' + c.id + '" style="text-align:left;width:100%">' +
    '<span><b>' + esc(c.title) + '</b> <span class="hint" style="margin:0">· ' + c.pages.length + '페이지</span></span>' +
    '<span class="' + (c.id === b.chapters.find(x => x.id === S.active.chapter)?.id ? 'hint' : 'hint') + '" style="margin:0">' + (c.id === S.active.chapter ? '✅ 선택됨' : '선택') + '</span></button>').join('');
  $('critLevel').textContent = 'AR ' + (b.ar || S.ar);
}
$('bookSel').onchange = e => {
  S.active.book = e.target.value;
  const b = book(); S.active.chapter = b.chapters[0].id; S.active.page = 0;
  save(); renderBooks(); renderDrafts(); renderPages();
};
$('chapterList').onclick = e => {
  const b = e.target.closest('[data-ch]'); if (!b) return;
  S.active.chapter = b.dataset.ch; S.active.page = 0;
  save(); renderBooks(); renderPages();
};
$('bookAddBtn').onclick = () => { $('bookForm').classList.remove('hidden'); $('bookTitle').value = ''; $('bookAr').value = S.ar; $('bookTitle').focus(); };
$('bookCancel').onclick = () => $('bookForm').classList.add('hidden');
$('bookSave').onclick = () => {
  const t = $('bookTitle').value.trim();
  if (!t) return toast('책 제목을 입력해 주세요.');
  const b = { id: uid('b'), title: t, ar: $('bookAr').value.trim() || S.ar, chapters: [{ id: uid('c'), title: 'Chapter 1', pages: [] }] };
  S.books.push(b);
  S.active = { book: b.id, chapter: b.chapters[0].id, page: 0 };
  save(); $('bookForm').classList.add('hidden');
  renderBooks(); renderPages(); renderDrafts(); toast('책을 추가했어요');
};
$('chapterAddBtn').onclick = () => { $('chapterForm').classList.remove('hidden'); $('chapterTitle').value = ''; $('chapterTitle').focus(); };
$('chapterCancel').onclick = () => $('chapterForm').classList.add('hidden');
$('chapterSave').onclick = () => {
  const t = $('chapterTitle').value.trim();
  if (!t) return toast('챕터 이름을 입력해 주세요.');
  const b = book();
  const c = { id: uid('c'), title: t, pages: [] };
  b.chapters.push(c);
  S.active.chapter = c.id; S.active.page = 0;
  save(); $('chapterForm').classList.add('hidden');
  renderBooks(); renderPages(); toast('챕터를 추가했어요');
};
$('bookDelBtn').onclick = () => {
  if (S.books.length < 2) return toast('책이 하나뿐이라 삭제할 수 없어요.');
  const b = book();
  if (!confirm('"' + b.title + '" 책과 그 안의 페이지·어휘를 모두 삭제할까요?')) return;
  S.books = S.books.filter(x => x.id !== b.id);
  delete S.vocab[b.id];
  S.active = { book: S.books[0].id, chapter: S.books[0].chapters[0].id, page: 0 };
  save(); normalizeAfterDelete(); renderBooks(); renderPages(); renderDrafts();
};

/* ── 페이지 목록 ── */
function renderPages() {
  const c = chapter();
  $('pagesCount').textContent = c.pages.length ? c.pages.length + '페이지' : '';
  $('pagesList').innerHTML = c.pages.length
    ? c.pages.map((p, i) =>
      '<div class="prow"><span style="min-width:0"><b>p.' + p.n + '</b> <span class="hint" style="margin:0">지문 ' + p.panels.length + ' · 단어 ' + p.words.length + ' · 문제 ' + p.questions.length + '</span>' +
      (p.done ? ' <span class="pill master">학습함</span>' : '') + '</span>' +
      '<span class="row" style="gap:6px;flex:none"><button class="btn tiny soft" data-open="' + i + '">열기</button>' +
      '<button class="btn tiny danger" data-delpage="' + i + '">삭제</button></span></div>').join('')
    : '<p class="hint">아직 승인된 페이지가 없어요. 사진을 분석하고 승인하면 여기에 쌓여요.</p>';
}
$('pagesList').onclick = e => {
  const o = e.target.closest('[data-open]');
  if (o) {
    S.active.page = +o.dataset.open; save();
    $('parentWrap').classList.add('hidden'); $('kidWrap').classList.remove('hidden');
    $('rateBtn').classList.remove('hidden'); $('parentBtn').classList.remove('hidden');
    goTab('today'); return;
  }
  const d = e.target.closest('[data-delpage]');
  if (!d) return;
  const c = chapter(), i = +d.dataset.delpage, p = c.pages[i];
  if (!confirm('p.' + p.n + ' 페이지를 삭제할까요? 어휘 목록은 남아요.')) return;
  c.pages.splice(i, 1);
  c.pages.forEach((x, k) => x.n = k + 1);
  S.active.page = Math.min(S.active.page, Math.max(0, c.pages.length - 1));
  save(); renderPages(); renderToday();
};

/* ── AI 설정 ── */
const PROVIDERS = {
  gemini: { label: 'Google Gemini', def: 'gemini-3.8-flash', ph: 'AIza…', keys: 'https://aistudio.google.com/apikey' },
  anthropic: { label: 'Anthropic', def: 'claude-sonnet-5-5', ph: 'sk-ant-…', keys: 'https://console.anthropic.com' }
};
const keyName = p => 'readingBuddy:key:' + p;
function getKey(prov) {
  const p = prov || S.ai.provider;
  try {
    const k = localStorage.getItem(keyName(p));
    if (k) return k;
    /* 이전 버전(단일 키) → Anthropic 키로 이어받기 */
    if (p === 'anthropic') return localStorage.getItem(KEY_API) || '';
    return '';
  } catch (e) { return ''; }
}
const getModel = () => S.ai.models[S.ai.provider] || AI_DEFAULT.models[S.ai.provider];
function renderAI() {
  const p = S.ai.provider, k = getKey(p), P = PROVIDERS[p];
  $('provSel').value = p;
  $('apiKey').placeholder = P.ph;
  $('modelIn').value = getModel();
  $('modelIn').placeholder = P.def;
  $('aiStatus').textContent = k
    ? '✅ ' + P.label + ' 키 저장됨 (끝 4자리 ' + k.slice(-4) + ')'
    : P.label + ' 키가 아직 없어요. ' + P.keys + ' 에서 발급할 수 있어요.';
  $('childAr').value = S.ar;
  $('critLevel').textContent = 'AR ' + (book().ar || S.ar) + ' · ' + P.label + ' ' + getModel();
}
$('provSel').onchange = e => {
  S.ai.provider = e.target.value === 'anthropic' ? 'anthropic' : 'gemini';
  save(); $('modelList').innerHTML = ''; renderAI();
};
$('aiSave').onclick = () => {
  const v = $('apiKey').value.trim();
  if (v) {
    if (v.length < 20) return toast('키가 너무 짧아요. 다시 확인해 주세요.');
    try { localStorage.setItem(keyName(S.ai.provider), v); } catch (e) { return toast('이 브라우저에서는 키를 저장할 수 없어요.'); }
    $('apiKey').value = '';
  }
  const m = $('modelIn').value.trim();
  if (m) S.ai.models[S.ai.provider] = m;
  save(); renderAI(); toast(PROVIDERS[S.ai.provider].label + ' 설정을 저장했어요');
};
$('aiDel').onclick = () => {
  try { localStorage.removeItem(keyName(S.ai.provider)); localStorage.removeItem(KEY_API); } catch (e) {}
  renderAI(); toast('키를 삭제했어요');
};
$('aiCheck').onclick = async () => {
  const p = S.ai.provider, k = getKey(p), P = PROVIDERS[p];
  if (!k) return toast('먼저 API 키를 저장해 주세요.');
  $('aiStatus').textContent = P.label + ' 모델 목록을 확인하는 중…';
  try {
    let ids = [];
    if (p === 'gemini') {
      const r = await fetch('https://generativelanguage.googleapis.com/v1beta/models?pageSize=100', { headers: { 'x-goog-api-key': k } });
      if (!r.ok) { const e = new Error('HTTP ' + r.status); e.status = r.status; throw e; }
      const j = await r.json();
      ids = (j.models || []).filter(m => (m.supportedGenerationMethods || []).includes('generateContent'))
        .map(m => m.name.replace('models/', ''));
    } else {
      const r = await fetch('https://api.anthropic.com/v1/models?limit=30', {
        headers: { 'x-api-key': k, 'anthropic-version': '2023-06-01', 'anthropic-dangerous-direct-browser-access': 'true' }
      });
      if (!r.ok) { const e = new Error('HTTP ' + r.status); e.status = r.status; throw e; }
      const j = await r.json();
      ids = (j.data || []).map(x => x.id);
    }
    $('aiStatus').textContent = ids.length ? '✅ 사용 가능한 모델 ' + ids.length + '개 · 눌러서 선택하세요' : '모델 목록이 비어 있어요.';
    $('modelList').innerHTML = ids.map(id => '<button class="chip" data-model="' + esc(id) + '" style="font-size:12px;min-height:38px">' + esc(id) + '</button>').join('');
  } catch (e) {
    $('aiStatus').textContent = '❌ 확인 실패 (' + (e.status ? 'HTTP ' + e.status : e.message) + ') · 키와 인터넷 연결을 확인해주세요.';
  }
};
$('modelList').onclick = e => {
  const b = e.target.closest('[data-model]'); if (!b) return;
  S.ai.models[S.ai.provider] = b.dataset.model;
  $('modelIn').value = b.dataset.model; save(); renderAI();
  toast('모델을 바꿨어요: ' + b.dataset.model);
};
$('childArSave').onclick = () => {
  const v = $('childAr').value.trim();
  if (!v) return toast('레벨을 입력해 주세요.');
  S.ar = v; save(); renderAI(); toast('아이 레벨을 ' + v + '(으)로 저장했어요');
};

/* ── 사진 분석 ── */
let drafts = [];
const AI_PROMPT = (b, c, ar, known) => `You are preparing study material for a Korean elementary student reading an English graphic novel at AR level ${ar}.
Book: "${b}" / ${c}.
Read the page image and reply with ONLY valid JSON (no markdown fences, no commentary) in exactly this shape:
{"panels":[{"n":1,"text":"..."}],"words":[{"w":"...","ipa":"/.../","ko":"..."}],"questions":[{"q":"...","ko":"...","a":"...","o":["...","...","..."],"ex":"..."}]}
Rules:
- panels: transcribe the English text on the page in reading order, split into sentences or speech bubbles (max 14). Copy exactly. Never invent text. Skip sound effects without words.
- words: choose 6-8 essential vocabulary words for an AR ${ar} reader. Prioritise words that (1) are useful general English, (2) appear near or above that level, (3) the student is likely not to know yet. EXCLUDE character names, place names, and any word in this known list: ${known || '(none)'}.
- ipa: IPA in slashes. ko: short natural Korean meaning, no more than 8 words.
- questions: 4-5 multiple-choice comprehension questions about THIS page. Mix: factual detail, inference, order of events, and word meaning in context. q is simple English. ko is the Korean translation of q. o has exactly 3 short English options and a is exactly one of them. Wrong options must be clearly wrong according to the page. ex is one short English sentence of evidence that starts with [Panel N] referring to the panel that proves it.
- If the page is only a title page or word list with no story, return "questions":[].
- Output JSON only.`;


async function toJpegB64(file) {
  const u = URL.createObjectURL(file), im = new Image();
  await new Promise((ok, no) => { im.onload = ok; im.onerror = no; im.src = u; });
  const sc = Math.min(1, 1600 / Math.max(im.naturalWidth, im.naturalHeight));
  const c = document.createElement('canvas');
  c.width = Math.round(im.naturalWidth * sc); c.height = Math.round(im.naturalHeight * sc);
  c.getContext('2d').drawImage(im, 0, 0, c.width, c.height);
  URL.revokeObjectURL(u);
  return c.toDataURL('image/jpeg', 0.85).split(',')[1];
}
function cleanPage(o) {
  const t = v => typeof v === 'string' ? v.trim() : '';
  const arr = v => Array.isArray(v) ? v : [];
  return {
    panels: arr(o.panels).map((p, i) => ({ n: +p.n || i + 1, text: t(p.text) })).filter(p => p.text).slice(0, 16),
    words: arr(o.words).map(w => ({ w: t(w.w), ipa: t(w.ipa), ko: t(w.ko) })).filter(w => /^[A-Za-z][A-Za-z' -]*$/.test(w.w) && w.ko).slice(0, 10),
    questions: arr(o.questions).map(q => {
      const a = t(q.a); if (!t(q.q) || !a) return null;
      const opts = [...new Set(arr(q.o).map(t).filter(Boolean))].slice(0, 4);
      if (!opts.includes(a)) opts.unshift(a);
      return { q: t(q.q), ko: t(q.ko), a, o: opts.slice(0, 3), ex: t(q.ex) };
    }).filter(q => q && q.o.length >= 2).slice(0, 6)
  };
}
const friendly = err => {
  if (err.status === 401 || err.status === 403) return 'API 키가 올바르지 않거나 권한이 없어요. ⚙ AI 설정에서 확인해 주세요.';
  if (err.status === 404) return '모델 이름을 찾을 수 없어요. AI 설정 → 연결 확인에서 모델을 골라주세요.';
  if (err.status === 429) return '요청이 너무 많아요. 잠시 뒤 다시 시도해 주세요.';
  if (err.status === 400 && /credit|billing/i.test(err.message || '')) return 'API 크레딧이 부족해요.';
  if (err.status >= 500) return 'AI 서버가 잠시 바빠요.';
  return err.message || '알 수 없는 오류';
};
async function callAI(b64, prompt) {
  const p = S.ai.provider, key = getKey(p), model = getModel();
  if (!key) throw new Error(PROVIDERS[p].label + ' API 키가 없어요. ⚙ AI 설정에서 저장해 주세요.');
  if (p === 'gemini') {
    const r = await fetch('https://generativelanguage.googleapis.com/v1beta/openai/chat/completions', {
      method: 'POST',
      headers: { 'content-type': 'application/json', 'authorization': 'Bearer ' + key, 'x-goog-api-key': key },
      body: JSON.stringify({
        model, temperature: 0.2, max_tokens: 4000,
        messages: [{ role: 'user', content: [
          { type: 'text', text: prompt },
          { type: 'image_url', image_url: { url: 'data:image/jpeg;base64,' + b64 } }
        ] }]
      })
    });
    if (!r.ok) { const e = new Error((await r.text()).slice(0, 300)); e.status = r.status; throw e; }
    const j = await r.json();
    return (((j.choices || [])[0] || {}).message || {}).content || '';
  }
  const r = await fetch('https://api.anthropic.com/v1/messages', {
    method: 'POST',
    headers: { 'content-type': 'application/json', 'x-api-key': key, 'anthropic-version': '2023-06-01', 'anthropic-dangerous-direct-browser-access': 'true' },
    body: JSON.stringify({
      model, max_tokens: 4000,
      messages: [{ role: 'user', content: [
        { type: 'image', source: { type: 'base64', media_type: 'image/jpeg', data: b64 } },
        { type: 'text', text: prompt }
      ] }]
    })
  });
  if (!r.ok) { const e = new Error((await r.text()).slice(0, 300)); e.status = r.status; throw e; }
  const j = await r.json();
  return (j.content || []).filter(x => x.type === 'text').map(x => x.text).join('');
}
async function analyzePage(file) {
  const b = book(), c = chapter();
  const known = Object.values(bank()).slice(0, 120).map(x => x.w).join(', ');
  const b64 = await toJpegB64(file);
  const txt = await callAI(b64, AI_PROMPT(b.title, c.title, b.ar || S.ar, known));
  const raw = txt.slice(txt.indexOf('{'), txt.lastIndexOf('}') + 1);
  const page = cleanPage(JSON.parse(raw));
  if (!page.panels.length) throw new Error('페이지에서 지문을 찾지 못했어요. 더 선명한 사진으로 다시 올려주세요.');
  return { id: uid('d'), img: 'data:image/jpeg;base64,' + b64, name: file.name, panels: page.panels, words: page.words, questions: page.questions };
}
$('imgInput').onchange = async e => {
  const files = [...e.target.files];
  e.target.value = '';
  if (!files.length) return;
  if (!getKey()) { $('upStatus').textContent = '먼저 AI 설정에서 ' + PROVIDERS[S.ai.provider].label + ' 키를 저장해 주세요.'; showPP('ai'); return; }
  if (!confirm('사진 ' + files.length + '장을 분석합니다.\n장당 API 호출 1회, 10~30초 걸려요. 시작할까요?')) return;
  let n = 0;
  for (const f of files) {
    n++;
    $('upStatus').textContent = '🤖 ' + n + ' / ' + files.length + ' 분석 중… (' + f.name + ')';
    try {
      const d = await analyzePage(f);
      drafts.push(d); renderDrafts();
      $('upStatus').textContent = '✅ ' + n + ' / ' + files.length + ' 완료 · 승인 대기에 ' + drafts.length + '개';
    } catch (err) {
      $('upStatus').textContent = '❌ ' + f.name + ' · ' + friendly(err);
      if (err.status === 401 || err.status === 404) break;
    }
  }
};
function draftCard(d, i) {
  return '<div class="draft"><img class="thumb" src="' + d.img + '" alt=""><div style="min-width:0;flex:1">' +
    '<div class="t">' + esc(d.name || '페이지') + '</div>' +
    '<div class="s">지문 ' + d.panels.length + ' · 단어 ' + d.words.length + ' · 문제 ' + d.questions.length + '</div></div>' +
    '<button class="btn sm primary" data-edit="' + i + '">검수</button></div>';
}
function renderDrafts() {
  const box1 = $('draftList'), box2 = $('draftQueue');
  $('draftCount').textContent = drafts.length ? drafts.length + '개 대기' : '';
  const html = drafts.length ? drafts.map((d, i) => draftCard(d, i)).join('') : '<p class="hint">승인을 기다리는 페이지가 없어요. 사진을 올리면 여기에 쌓여요.</p>';
  if (box1) box1.innerHTML = html;
  if (box2) box2.innerHTML = html;
}
document.addEventListener('click', e => {
  const b = e.target.closest('[data-edit]');
  if (!b) return;
  openEditor(+b.dataset.edit);
});

/* ── 검수 편집기 ── */
let editing = null, editingIndex = -1;
function openEditor(i) {
  editingIndex = i;
  editing = JSON.parse(JSON.stringify(drafts[i]));
  showPP('editor');
  $('edThumb').src = editing.img;
  $('edThumb').classList.remove('hidden');
  $('edTarget').textContent = book().title + ' · ' + chapter().title;
  renderEditor();
}
$('edBack').onclick = () => { editing = null; showPP('review'); };

function renderEditor() {
  const d = editing;
  $('edPanels').innerHTML = d.panels.map((p, i) =>
    '<div class="rev-panel" data-i="' + i + '"><div class="n">' + (i + 1) + '</div>' +
    '<textarea data-k="text" aria-label="지문 ' + (i + 1) + '">' + esc(p.text) + '</textarea>' +
    '<button class="btn tiny danger" data-delpanel="' + i + '">✕</button></div>').join('');

  $('edWords').innerHTML = d.words.map((w, i) =>
    '<div class="rev-word" data-i="' + i + '">' +
    '<input data-k="w" value="' + esc(w.w) + '" placeholder="word" aria-label="단어">' +
    '<input data-k="ipa" value="' + esc(w.ipa) + '" placeholder="/ipa/" aria-label="발음기호">' +
    '<input data-k="ko" value="' + esc(w.ko) + '" placeholder="뜻" aria-label="뜻">' +
    '<button class="btn tiny danger" data-delword="' + i + '">✕</button></div>').join('')
    || '<p class="hint">단어가 없어요. 필요하면 추가하세요.</p>';

  $('edQs').innerHTML = d.questions.map((q, i) => {
    const opts = (q.o && q.o.length ? q.o : ['', '', '']).slice(0, 3);
    while (opts.length < 3) opts.push('');
    return '<div class="rev-q" data-i="' + i + '">' +
      '<label class="fld">문제 (English)</label><input data-k="q" value="' + esc(q.q) + '">' +
      '<label class="fld" style="margin-top:8px">한국어 번역</label><input data-k="ko" value="' + esc(q.ko) + '">' +
      '<label class="fld" style="margin-top:8px">보기 3개 · 정답에 표시</label>' +
      opts.map((o, j) =>
        '<div class="rev-opt"><input type="radio" name="qa' + i + '" data-j="' + j + '"' + (q.a && q.a === o ? ' checked' : '') + ' aria-label="정답">' +
        '<input type="text" data-k="opt" data-j="' + j + '" value="' + esc(o) + '" placeholder="보기 ' + 'ABC'[j] + '"></div>').join('') +
      '<label class="fld" style="margin-top:8px">근거 (예: [Panel 2] He ran to the door.)</label><input data-k="ex" value="' + esc(q.ex) + '">' +
      '<button class="btn tiny danger" data-delq="' + i + '" style="margin-top:8px">문제 삭제</button></div>';
  }).join('') || '<p class="hint">문제가 없어요. 페이지에 문제를 추가하면 아이가 내용 이해를 확인할 수 있어요.</p>';
}

$('edPanels').addEventListener('input', e => {
  const box = e.target.closest('.rev-panel'); if (!box) return;
  editing.panels[+box.dataset.i].text = e.target.value;
});
$('edPanels').addEventListener('click', e => {
  const b = e.target.closest('[data-delpanel]'); if (!b) return;
  editing.panels.splice(+b.dataset.delpanel, 1); renderEditor();
});
$('edWords').addEventListener('input', e => {
  const box = e.target.closest('.rev-word'); if (!box) return;
  editing.words[+box.dataset.i][e.target.dataset.k] = e.target.value;
});
$('edWords').addEventListener('click', e => {
  const b = e.target.closest('[data-delword]'); if (!b) return;
  editing.words.splice(+b.dataset.delword, 1); renderEditor();
});
$('edQs').addEventListener('input', e => {
  const box = e.target.closest('.rev-q'); if (!box) return;
  const q = editing.questions[+box.dataset.i], k = e.target.dataset.k;
  if (k === 'opt') {
    const j = +e.target.dataset.j, prev = q.o[j];
    q.o[j] = e.target.value;
    if (q.a === prev) q.a = e.target.value;
  } else if (k) q[k] = e.target.value;
});
$('edQs').addEventListener('change', e => {
  if (e.target.type !== 'radio') return;
  const box = e.target.closest('.rev-q');
  const q = editing.questions[+box.dataset.i];
  q.a = q.o[+e.target.dataset.j];
});
$('edQs').addEventListener('click', e => {
  const b = e.target.closest('[data-delq]'); if (!b) return;
  editing.questions.splice(+b.dataset.delq, 1); renderEditor();
});
$('edAddPanel').onclick = () => { editing.panels.push({ n: editing.panels.length + 1, text: '' }); renderEditor(); };
$('edAddWord').onclick = () => { editing.words.push({ w: '', ipa: '', ko: '' }); renderEditor(); };
$('edAddQ').onclick = () => { editing.questions.push({ q: '', ko: '', a: '', o: ['', '', ''], ex: '' }); renderEditor(); };
$('edDrop').onclick = () => {
  if (!confirm('이 분석 결과를 버릴까요?')) return;
  drafts.splice(editingIndex, 1); editing = null; renderDrafts(); showPP('review');
};
$('edApprove').onclick = () => {
  const d = editing;
  const panels = d.panels.filter(p => p.text.trim());
  const words = d.words.filter(w => w.w.trim() && w.ko.trim()).map(w => ({ w: w.w.trim(), ipa: w.ipa.trim(), ko: w.ko.trim() }));
  const questions = d.questions.map(q => {
    const o = (q.o || []).map(x => (x || '').trim()).filter(Boolean);
    let a = (q.a || '').trim();
    if (!o.length || !q.q.trim()) return null;
    if (!o.includes(a)) a = o[0];
    return { q: q.q.trim(), ko: q.ko.trim(), a, o: o.slice(0, 3), ex: q.ex.trim() };
  }).filter(Boolean);
  if (!panels.length) return toast('지문이 비어 있어요. 한 줄이라도 채워주세요.');
  const c = chapter(), b = book();
  const pg = { id: uid('p'), n: c.pages.length + 1, date: ymd(new Date()), done: false, panels, words, questions };
  c.pages.push(pg);
  words.forEach(w => {
    const bk = S.vocab[b.id] || (S.vocab[b.id] = {});
    const k = norm(w.w); if (!k) return;
    const z = bk[k] || (bk[k] = { w: w.w, ipa: w.ipa, ko: w.ko, count: 0, first: ymd(new Date()), ok: 0, bad: 0, streak: 0 });
    z.count = (z.count || 0) + 1;
    if (!z.ko && w.ko) z.ko = w.ko;
    if (!z.ipa && w.ipa) z.ipa = w.ipa;
  });
  S.active.page = c.pages.length - 1;
  drafts.splice(editingIndex, 1); editing = null;
  save(); renderDrafts(); renderPages(); renderBooks(); renderToday(); refreshBadges();
  showPP('review');
  toast('p.' + pg.n + ' 승인 완료 · 단어 ' + words.length + '개');
};

/* ── 백업 ── */
function renderBackupHint() { $('impSt').textContent = '책 ' + S.books.length + '권 · 학습 ' + S.sessions.length + '회 · 오답 ' + S.wrong.length + '개'; }
$('expBtn').onclick = () => {
  const d = new Date();
  const name = 'reading-buddy-' + d.getFullYear() + pad2(d.getMonth() + 1) + pad2(d.getDate()) + '.json';
  const blob = new Blob([JSON.stringify(S, null, 2)], { type: 'application/json' });
  const a = document.createElement('a');
  a.href = URL.createObjectURL(blob); a.download = name;
  document.body.appendChild(a); a.click(); a.remove();
  setTimeout(() => URL.revokeObjectURL(a.href), 2000);
  $('impSt').textContent = '백업 파일을 내려받았어요.';
};
let pendingImport = null;
$('impBtn').onclick = () => $('impFile').click();
$('impFile').onchange = e => {
  const f = e.target.files[0]; if (!f) return;
  const r = new FileReader();
  r.onload = () => {
    try {
      const d = JSON.parse(r.result);
      if (!d || !Array.isArray(d.books)) throw new Error('bad');
      pendingImport = d;
      $('impInfo').textContent = '책 ' + d.books.length + '권 · 학습 ' + (d.sessions || []).length + '회를 찾았어요. 어떻게 넣을까요?';
      $('impModal').classList.remove('hidden');
    } catch (err) { toast('백업 파일을 읽을 수 없어요.'); }
    $('impFile').value = '';
  };
  r.readAsText(f);
};
const closeImport = () => { $('impModal').classList.add('hidden'); pendingImport = null; };
$('impCancel').onclick = closeImport;
$('impReplace').onclick = () => doImport('replace');
$('impMerge').onclick = () => doImport('merge');
function doImport(mode) {
  const d = pendingImport; if (!d) return;
  if (mode === 'replace') {
    S = normalizeState(d);
  } else {
    const have = new Set(S.books.map(b => b.id));
    (d.books || []).forEach(b => { if (!have.has(b.id)) S.books.push(b); });
    const sid = new Set(S.sessions.map(x => x.id || x.date));
    (d.sessions || []).forEach(x => { if (!sid.has(x.id || x.date)) S.sessions.push(x); });
    const wid = new Set(S.wrong.map(x => x.id));
    (d.wrong || []).forEach(x => { if (!wid.has(x.id)) S.wrong.push(x); });
    Object.keys(d.vocab || {}).forEach(bid => {
      const dst = S.vocab[bid] || (S.vocab[bid] = {});
      Object.keys(d.vocab[bid]).forEach(k => {
        const a = dst[k], b = d.vocab[bid][k];
        if (!a) dst[k] = b;
        else { a.count = (a.count || 0) + (b.count || 0); a.ok = (a.ok || 0) + (b.ok || 0); a.bad = (a.bad || 0) + (b.bad || 0); a.streak = Math.max(a.streak || 0, b.streak || 0); }
      });
    });
    S.books.forEach(b => { if (!b.chapters.length) b.chapters.push({ id: uid('c'), title: 'Chapter 1', pages: [] }); });
  }
  S = normalizeState(S);
  save(); closeImport();
  renderBooks(); renderPages(); renderDrafts(); renderAI(); renderBackupHint(); renderToday(); refreshBadges();
  toast(mode === 'replace' ? '백업으로 덮어썼어요' : '백업을 합쳤어요');
}
$('resetVocab').onclick = () => {
  if (!confirm('이 책의 어휘 학습 기록(정답/오답 횟수)을 초기화할까요? 단어 목록은 남아요.')) return;
  const b = book();
  Object.values(S.vocab[b.id] || {}).forEach(z => { z.ok = 0; z.bad = 0; z.streak = 0; });
  save(); toast('어휘 기록을 초기화했어요');
};

/* ── 초기화 ── */
function normalizeAfterDelete() {
  const b = book();
  const c = b.chapters.find(x => x.id === S.active.chapter) || b.chapters[0];
  S.active.book = b.id; S.active.chapter = c.id;
  S.active.page = Math.min(S.active.page, Math.max(0, c.pages.length - 1));
  save();
}
load();
normalizeAfterDelete();
refreshBadges();
goTab('today');
renderDrafts();
</script>
<script type="module" src="https://static.cloudflareinsights.com/beacon.min.js/vce701823e78c4301a35b7e07294d87301792088814092" integrity="sha512-UKNk8GbxkABxKcXYuLkO16EleLGUkcvJWtpSNmExE0Too3ZaFAxTscNWEc1OdAv5/BikHawapSCaiD2XCmp+Bw==" data-cf-beacon='{"version":"2024.11.0","token":"4edd5f8ec12a48cfa682ab8261b80a79","spa":2}' crossorigin="anonymous"></script>
</body>
</html>
