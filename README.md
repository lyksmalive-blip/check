# check

<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1">
<title>팰파고스에 떨어진 나는 어떤 조련사?</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Noto+Serif+KR:wght@500;700;900&family=Noto+Sans+KR:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
  :root{
    --bg-deep:#111d17;
    --bg-panel:#1b2a22;
    --bg-panel-soft:#20302a;
    --ember:#e2963c;
    --ember-soft:#f0b768;
    --leaf:#8fbc6b;
    --parchment:#f3ecd8;
    --muted:#9fb09b;
    --line:#33473a;
    --shadow: 0 20px 60px rgba(0,0,0,0.45);
  }
  *{box-sizing:border-box;}
  html,body{margin:0;padding:0;}
  body{
    min-height:100vh;
    background:
      radial-gradient(560px 420px at 82% 8%, rgba(226,150,60,0.16), transparent 60%),
      radial-gradient(700px 500px at 10% 95%, rgba(143,188,107,0.10), transparent 65%),
      var(--bg-deep);
    color:var(--parchment);
    font-family:'Noto Sans KR', sans-serif;
    display:flex;
    align-items:center;
    justify-content:center;
    padding:24px 16px;
  }
  .stage{
    width:100%;
    max-width:480px;
    position:relative;
  }
  .card{
    background:var(--bg-panel);
    border:1px solid var(--line);
    border-radius:18px;
    padding:40px 28px 32px;
    box-shadow:var(--shadow);
    position:relative;
    overflow:hidden;
  }
  .card::before{
    content:"";
    position:absolute;
    top:-40%;
    right:-30%;
    width:260px;
    height:260px;
    background:radial-gradient(circle, rgba(226,150,60,0.20), transparent 70%);
    pointer-events:none;
  }

  /* ---------- Start screen ---------- */
  .eyebrow-spot{
    width:34px;height:34px;border-radius:50%;
    background:radial-gradient(circle at 35% 30%, var(--ember-soft), var(--ember) 60%, #a5601a 100%);
    box-shadow:0 0 18px rgba(226,150,60,0.55);
    margin-bottom:22px;
  }
  h1.title{
    font-family:'Noto Serif KR', serif;
    font-weight:900;
    font-size:30px;
    line-height:1.35;
    margin:0 0 18px;
    letter-spacing:-0.01em;
  }
  p.lede{
    font-size:15px;
    line-height:1.75;
    color:var(--muted);
    margin:0 0 28px;
    max-width:34ch;
  }
  .meta-line{
    font-size:13px;
    color:var(--muted);
    border-top:1px solid var(--line);
    border-bottom:1px solid var(--line);
    padding:14px 0;
    margin:0 0 30px;
    line-height:1.8;
  }
  .btn-primary{
    display:inline-flex;
    align-items:center;
    justify-content:center;
    width:100%;
    padding:16px 20px;
    background:var(--ember);
    color:#1a1206;
    font-family:'Noto Sans KR', sans-serif;
    font-weight:700;
    font-size:16px;
    border:none;
    border-radius:999px;
    cursor:pointer;
    transition:transform .15s ease, background .15s ease;
  }
  .btn-primary:hover{ background:var(--ember-soft); transform:translateY(-1px); }
  .btn-primary:active{ transform:translateY(0); }
  .btn-primary:focus-visible{ outline:3px solid var(--leaf); outline-offset:2px; }

  /* ---------- Question screen ---------- */
  .progress-wrap{
    display:flex;
    align-items:center;
    gap:12px;
    margin-bottom:26px;
  }
  .progress-track{
    flex:1;
    height:6px;
    border-radius:999px;
    background:var(--bg-panel-soft);
    overflow:hidden;
  }
  .progress-fill{
    height:100%;
    background:linear-gradient(90deg, var(--leaf), var(--ember));
    border-radius:999px;
    transition:width .3s ease;
  }
  .progress-count{
    font-size:13px;
    color:var(--muted);
    white-space:nowrap;
    font-variant-numeric:tabular-nums;
  }
  h2.question{
    font-family:'Noto Serif KR', serif;
    font-weight:700;
    font-size:22px;
    line-height:1.5;
    margin:0 0 26px;
  }
  .options{
    display:flex;
    flex-direction:column;
    gap:12px;
    margin-bottom:22px;
  }
  .option-btn{
    text-align:left;
    background:var(--bg-panel-soft);
    border:1px solid var(--line);
    border-left:4px solid var(--line);
    border-radius:12px;
    padding:16px 18px;
    color:var(--parchment);
    font-family:'Noto Sans KR', sans-serif;
    font-size:15px;
    line-height:1.6;
    cursor:pointer;
    transition:border-color .15s ease, background .15s ease, transform .1s ease;
  }
  .option-btn:hover{
    border-left-color:var(--ember);
    background:#243629;
  }
  .option-btn:active{ transform:scale(0.99); }
  .option-btn:focus-visible{ outline:3px solid var(--leaf); outline-offset:2px; }
  .nav-row{
    display:flex;
    justify-content:flex-start;
  }
  .btn-back{
    background:none;
    border:none;
    color:var(--muted);
    font-family:'Noto Sans KR', sans-serif;
    font-size:14px;
    cursor:pointer;
    padding:8px 4px;
  }
  .btn-back:disabled{
    opacity:0;
    pointer-events:none;
  }
  .btn-back:hover:not(:disabled){ color:var(--parchment); }

  /* ---------- Completed (post-quiz) screen ---------- */
  .completed-actions{
    display:flex;
    flex-direction:column;
    gap:12px;
    margin-top:6px;
  }
  .btn-secondary{
    width:100%;
    padding:14px 20px;
    background:transparent;
    color:var(--parchment);
    border:1px solid var(--line);
    border-radius:999px;
    font-family:'Noto Sans KR', sans-serif;
    font-weight:600;
    font-size:15px;
    cursor:pointer;
  }
  .btn-secondary:hover{ border-color:var(--leaf); }

  /* ---------- Result modal ---------- */
  .modal-overlay{
    position:fixed;
    inset:0;
    background:rgba(8,13,10,0.72);
    display:flex;
    align-items:center;
    justify-content:center;
    padding:20px;
    z-index:50;
  }
  .modal-overlay[hidden]{ display:none; }
  .modal-card{
    width:100%;
    max-width:440px;
    max-height:88vh;
    overflow-y:auto;
    background:var(--bg-panel);
    border:1px solid var(--line);
    border-radius:20px;
    padding:34px 26px 28px;
    position:relative;
    box-shadow:var(--shadow);
  }
  .modal-close{
    position:absolute;
    top:16px;
    right:16px;
    width:32px;
    height:32px;
    border-radius:50%;
    border:1px solid var(--line);
    background:var(--bg-panel-soft);
    color:var(--muted);
    font-size:16px;
    line-height:1;
    cursor:pointer;
  }
  .modal-close:hover{ color:var(--parchment); border-color:var(--ember); }
  .result-type-name{
    font-family:'Noto Serif KR', serif;
    font-weight:900;
    font-size:28px;
    line-height:1.4;
    margin:6px 0 8px;
    padding-right:30px;
  }
  .result-mbti{
    display:inline-block;
    font-size:12px;
    letter-spacing:0.04em;
    color:var(--bg-deep);
    background:var(--leaf);
    padding:3px 10px;
    border-radius:999px;
    font-weight:700;
    margin-bottom:20px;
  }
  .result-desc{
    font-size:15px;
    line-height:1.8;
    color:var(--parchment);
    margin:0 0 24px;
  }
  .result-sub-heading{
    font-family:'Noto Serif KR', serif;
    font-weight:700;
    font-size:16px;
    margin:0 0 12px;
  }
  .result-traits{
    list-style:none;
    margin:0 0 28px;
    padding:0;
    display:flex;
    flex-direction:column;
    gap:10px;
  }
  .result-traits li{
    display:flex;
    gap:10px;
    align-items:flex-start;
    font-size:14px;
    line-height:1.6;
    color:var(--muted);
    background:var(--bg-panel-soft);
    border:1px solid var(--line);
    border-radius:10px;
    padding:12px 14px;
  }
  .result-traits li::before{
    content:"";
    flex:0 0 6px;
    width:6px;
    height:6px;
    margin-top:7px;
    border-radius:50%;
    background:var(--ember);
  }
  .result-footnote{
    font-size:11.5px;
    line-height:1.7;
    color:var(--muted);
    border-top:1px solid var(--line);
    padding-top:16px;
    margin-top:4px;
  }

  @media (max-width:380px){
    .card{ padding:32px 20px 26px; }
    h1.title{ font-size:26px; }
    .result-type-name{ font-size:24px; }
  }

  @media (prefers-reduced-motion: reduce){
    *{ transition:none !important; }
  }
</style>
</head>
<body>

<div class="stage">

  <!-- START SCREEN -->
  <section class="card" id="screen-start">
    <div class="eyebrow-spot" aria-hidden="true"></div>
    <h1 class="title">팰파고스에 떨어진<br>나는 어떤 조련사?</h1>
    <p class="lede">낯선 섬, 새로운 팰, 그리고 나.<br>당신의 선택으로 첫 하루를 완성해 보세요.</p>
    <p class="meta-line">총 12문항 · 약 3분<br>정답은 없어요. 평소의 나와 더 가까운 쪽을 골라 주세요.</p>
    <button class="btn-primary" id="btn-start" type="button">나의 모험 시작하기</button>
  </section>

  <!-- QUESTION SCREEN -->
  <section class="card" id="screen-question" hidden>
    <div class="progress-wrap">
      <div class="progress-track">
        <div class="progress-fill" id="progress-fill"></div>
      </div>
      <span class="progress-count" id="progress-count">1 / 12</span>
    </div>
    <h2 class="question" id="question-text"></h2>
    <div class="options" id="options-wrap"></div>
    <div class="nav-row">
      <button class="btn-back" id="btn-back" type="button">← 이전 질문</button>
    </div>
  </section>

  <!-- COMPLETED SCREEN (shown behind/after modal is closed) -->
  <section class="card" id="screen-completed" hidden>
    <div class="eyebrow-spot" aria-hidden="true"></div>
    <h1 class="title">첫 하루가<br>마무리됐어요</h1>
    <p class="lede">당신의 선택으로 완성한 조련사 유형을 확인해 보세요.</p>
    <div class="completed-actions">
      <button class="btn-primary" id="btn-reopen" type="button">결과 다시 보기</button>
      <button class="btn-secondary" id="btn-retry" type="button">다시 테스트하기</button>
    </div>
  </section>

</div>

<!-- RESULT MODAL -->
<div class="modal-overlay" id="modal-overlay" hidden>
  <div class="modal-card" role="dialog" aria-modal="true" aria-labelledby="result-type-name">
    <button class="modal-close" id="modal-close" type="button" aria-label="닫기">✕</button>
    <h2 class="result-type-name" id="result-type-name"></h2>
    <span class="result-mbti" id="result-mbti"></span>
    <p class="result-desc" id="result-desc"></p>
    <h3 class="result-sub-heading">이런 모습, 나랑 닮았나요?</h3>
    <ul class="result-traits" id="result-traits"></ul>
    <button class="btn-primary" id="btn-retry-modal" type="button">다시 테스트하기</button>
    <p class="result-footnote">본 테스트는 MBTI의 선호 지표에서 착안한 오락용 콘텐츠이며, 정식 MBTI 검사가 아닙니다.</p>
  </div>
</div>

<script>
(function(){

  // ---------- Data ----------
  var questions = [
    { id:1, axis:'EI', text:'팰파고스에 도착했어요! 모닥불 주변에 조련사들이 모여 있다면?',
      options:[
        { label:'A', letter:'E', text:'"무슨 얘기 중이에요?" 다가가 이야기를 나눈다.' },
        { label:'B', letter:'I', text:'조금 떨어진 곳에 앉아 풍경을 즐기며 적응한다.' }
      ]},
    { id:2, axis:'SN', text:'탐험을 앞두고 지도 한 장을 받았어요. 먼저 눈이 가는 것은?',
      options:[
        { label:'A', letter:'N', text:'숲 너머 빈 공간. 무엇이 있을지 상상하게 된다.' },
        { label:'B', letter:'S', text:'표시된 길과 지형. 주변 모습부터 파악하게 된다.' }
      ]},
    { id:3, axis:'JP', text:'내일은 첫 장거리 탐험! 오늘 밤 무엇을 할까요?',
      options:[
        { label:'A', letter:'J', text:'출발 시각과 이동 경로를 미리 정해 둔다.' },
        { label:'B', letter:'P', text:'필요한 물건만 챙기고 경로는 내일 정한다.' }
      ]},
    { id:4, axis:'TF', text:'동료가 재료를 잘못 챙겨서 거점 공사가 멈췄어요. 먼저 할 말은?',
      options:[
        { label:'A', letter:'F', text:'"많이 당황했겠다. 같이 정리해 보자."' },
        { label:'B', letter:'T', text:'"지금 있는 재료로 만들 수 있는 것부터 보자."' }
      ]},
    { id:5, axis:'SN', text:'새로운 팰을 발견했어요! 관찰 기록에 먼저 적고 싶은 것은?',
      options:[
        { label:'A', letter:'S', text:'몸 색깔, 움직임, 발견한 장소처럼 직접 본 특징' },
        { label:'B', letter:'N', text:'어디서 왔을지, 어떤 생활을 할지 떠오르는 추측' }
      ]},
    { id:6, axis:'EI', text:'처음 보는 조련사와 잠시 쉬게 됐어요. 이야기를 나눌 때 나는?',
      options:[
        { label:'A', letter:'I', text:'혼자 생각을 정리하다가 나누고 싶은 이야기를 꺼낸다.' },
        { label:'B', letter:'E', text:'이런저런 이야기를 나누며 생각을 정리한다.' }
      ]},
    { id:7, axis:'JP', text:'탐험하다 멋진 호수를 발견했어요. 원래 목적지는 따로 있는데!',
      options:[
        { label:'A', letter:'P', text:'"오늘은 여기다!" 호수 주변부터 둘러본다.' },
        { label:'B', letter:'J', text:'"돌아오는 길에 들르자!" 예정한 목적지로 향한다.' }
      ]},
    { id:8, axis:'TF', text:'함께 얻은 베리를 나누기로 했어요. 나눌 기준을 정한다면?',
      options:[
        { label:'A', letter:'T', text:'각자 모은 양과 기여한 정도를 기준으로 나눈다.' },
        { label:'B', letter:'F', text:'각자의 배고픔과 사정을 듣고 양을 조정한다.' }
      ]},
    { id:9, axis:'SN', text:'거점에서 팰이 같은 자리를 계속 맴돌고 있어요. 먼저 드는 생각은?',
      options:[
        { label:'A', letter:'N', text:'"저곳에 특별한 이유가 있나?" 가능성을 떠올린다.' },
        { label:'B', letter:'S', text:'"언제부터 저랬지?" 주변 상태와 움직임을 살핀다.' }
      ]},
    { id:10, axis:'TF', text:'거점을 옮길 후보지가 두 곳이에요. 마지막 결정에서 더 중요한 것은?',
      options:[
        { label:'A', letter:'F', text:'함께 지낼 동료들이 편안하고 만족스럽게 느끼는지' },
        { label:'B', letter:'T', text:'이동 거리와 자원 확보 조건이 유리한지' }
      ]},
    { id:11, axis:'EI', text:'탐험을 마치고 돌아왔는데 조련사들이 저녁 모임에 초대했어요.',
      options:[
        { label:'A', letter:'I', text:'팰과 조용히 쉬면서 오늘 쓴 에너지를 채운다.' },
        { label:'B', letter:'E', text:'모임에서 오늘의 모험담을 나누며 기운을 얻는다.' }
      ]},
    { id:12, axis:'JP', text:'잠들기 전, 내일 할 일이 몇 가지 떠올랐어요.',
      options:[
        { label:'A', letter:'P', text:'내일 마음이 가는 것부터 하도록 선택지를 열어 둔다.' },
        { label:'B', letter:'J', text:'우선순위를 정해 두고 홀가분하게 잠든다.' }
      ]}
  ];

  var results = {
    ISTJ:{ title:'빈틈없는 거점 관리자', desc:'필요한 재료도, 오늘 할 일도 차근차근 챙겨요. 작은 약속을 지키며 쌓아 올린 거점은 어느새 모두가 믿고 돌아오는 곳이 되어 있죠.', traits:['자원을 정리해 두면 마음이 편해요.','한 번 맡은 일은 끝까지 챙겨요.','익숙한 방법을 꾸준히 다듬어요.']},
    ISFJ:{ title:'세심한 팰 돌보미', desc:'평소와 다른 팰의 표정도 쉽게 지나치지 않아요. 필요한 것을 조용히 챙겨 주는 당신 덕분에 거점의 하루는 한결 포근해져요.', traits:['동료의 취향을 잘 기억해요.','작은 변화도 눈에 들어와요.','편안한 일상을 함께 만들어요.']},
    INFJ:{ title:'이상적인 낙원 설계자', desc:'모두가 편히 쉬어 갈 거점을 마음속에 그려요. 당장의 편리함을 넘어, 우리가 어떤 곳에서 함께 살고 싶은지 생각하는 조련사예요.', traits:['선택에 담긴 의미를 생각해요.','동료의 마음을 깊이 이해하고 싶어요.','그려 둔 미래를 차근차근 완성해요.']},
    INTJ:{ title:'치밀한 모험 설계자', desc:'눈앞의 길 너머, 다음 모험까지 내다봐요. 혼자 생각을 정리하고 나만의 전략을 세울 때 당신의 모험은 더욱 선명해져요.', traits:['큰 목표에서 다음 할 일을 찾아요.','더 나은 방법을 고민해요.','계획에 이유가 있어야 만족해요.']},
    ISTP:{ title:'침착한 현장 해결사', desc:'예상 밖의 문제가 생겨도 우선 주변을 살펴요. 직접 만져 보고 시험하며 지금 필요한 해답을 찾아내는 조련사예요.', traits:['설명보다 직접 해 보는 게 편해요.','상황에 맞춰 방법을 바꿔요.','혼자 집중하는 시간이 소중해요.']},
    ISFP:{ title:'감각적인 거점 꾸미미', desc:'마음에 드는 풍경 하나가 오늘의 행복이 돼요. 작은 취향을 하나씩 더하다 보면 평범한 거점도 당신만의 특별한 공간이 되죠.', traits:['눈앞의 예쁜 장면에 오래 머물러요.','내 마음에 드는 선택이 중요해요.','팰과 조용히 보내는 시간이 좋아요.']},
    INFP:{ title:'낭만적인 팰 친구', desc:'처음 만난 팰과도 나만의 이야기를 쌓아 가요. 조금 돌아가는 길이라도 마음이 이끄는 곳이라면 충분히 의미 있는 모험이에요.', traits:['만남에 특별한 의미를 붙여요.','상상 속 모험이 자주 펼쳐져요.','내가 소중히 여기는 것을 지켜요.']},
    INTP:{ title:'호기심 많은 연구가', desc:'작은 현상에도 왜 그런지 궁금해져요. 혼자 관찰하고 가설을 세우다 보면 남들이 지나친 새로운 가능성이 보이곤 해요.', traits:['궁금한 것은 끝까지 파고들어요.','당연한 방법에도 질문을 던져요.','생각을 자유롭게 펼칠 때 즐거워요.']},
    ESTP:{ title:'대담한 현장 모험가', desc:'눈앞에 재미있는 기회가 보이면 움직여요. 동료들과 현장을 누비며, 예상 밖의 상황에서도 쓸 만한 방법을 빠르게 찾아내요.', traits:['직접 겪으면서 감을 잡아요.','바뀐 상황에도 유연하게 움직여요.','동료들과 행동에 나설 때 신나요.']},
    ESFP:{ title:'흥겨운 거점 분위기메이커', desc:'좋은 풍경도 맛있는 저녁도 함께라서 더 즐거워요. 오늘의 작은 재미를 발견하고 나누는 당신 곁에는 자연스레 이야기가 모여요.', traits:['재미있는 순간을 바로 나누고 싶어요.','주변 사람들의 반응을 잘 알아채요.','지금 즐길 수 있는 것을 찾아요.']},
    ENFP:{ title:'자유로운 낭만 탐험가', desc:'지도에 빈 곳이 보이면 그냥 지나칠 수 없어요. 낯선 길과 새로운 친구가 오늘의 목적지를 바꾸기도 하죠. 계획과 조금 달라도, 즐거웠다면 멋진 모험이에요!', traits:['목적지로 가다가 다른 풍경에 한눈팔아요.','새로운 팰과 함께할 이야기가 떠올라요.','재미있는 발견은 동료들에게 바로 알려요.']},
    ENTP:{ title:'기발한 모험 실험가', desc:'익숙한 방식에도 새로운 아이디어를 더해요. 동료들과 생각을 주고받다 떠오른 엉뚱한 시도가 다음 모험의 시작이 되기도 하죠.', traits:['"이렇게 하면 어떨까?"를 자주 말해요.','서로 다른 생각을 나누는 게 즐거워요.','새로운 가능성을 시험해 보고 싶어요.']},
    ESTJ:{ title:'든든한 거점 지휘관', desc:'무엇부터 해야 할지 정하고 함께 움직여요. 자원과 역할을 꼼꼼히 살피는 당신 덕분에 거점의 계획은 하나씩 현실이 돼요.', traits:['할 일을 분명하게 나눠요.','약속한 기준을 중요하게 생각해요.','함께 정한 목표를 실행에 옮겨요.']},
    ESFJ:{ title:'다정한 거점 반장', desc:'모두의 하루가 잘 흘러가고 있는지 챙겨요. 필요한 준비와 따뜻한 한마디를 더해 함께 지내는 거점에 편안함을 만들어 줘요.', traits:['함께하는 약속을 잘 챙겨요.','동료가 필요한 것을 먼저 살펴요.','모두가 어울릴 자리를 마련해요.']},
    ENFJ:{ title:'열정적인 모험 길잡이', desc:'동료의 장점을 발견하면 함께할 모험이 떠올라요. 서로의 마음을 모아 우리가 꿈꾸는 목적지로 한 걸음씩 이끌어 가요.', traits:['동료가 잘하는 것을 알아봐요.','함께 이루고 싶은 목표가 있어요.','이야기를 듣고 다음 방향을 제안해요.']},
    ENTJ:{ title:'결단력 있는 원정대장', desc:'큰 목표를 정하고 필요한 길을 만들어 가요. 동료들과 전략을 나누고 자원을 배분하며 다음 원정을 실행에 옮기는 조련사예요.', traits:['목표에 맞춰 역할을 정리해요.','더 좋은 전략이 보이면 제안해요.','결정한 일은 추진력 있게 진행해요.']}
  };

  // ---------- State ----------
  var current = 0;               // index into questions, 0-based
  var answers = new Array(questions.length).fill(null); // stores chosen letter per question
  var lastMbti = null;

  // ---------- Elements ----------
  var screenStart = document.getElementById('screen-start');
  var screenQuestion = document.getElementById('screen-question');
  var screenCompleted = document.getElementById('screen-completed');
  var modalOverlay = document.getElementById('modal-overlay');

  var progressFill = document.getElementById('progress-fill');
  var progressCount = document.getElementById('progress-count');
  var questionText = document.getElementById('question-text');
  var optionsWrap = document.getElementById('options-wrap');
  var btnBack = document.getElementById('btn-back');

  document.getElementById('btn-start').addEventListener('click', startQuiz);
  btnBack.addEventListener('click', goBack);
  document.getElementById('btn-reopen').addEventListener('click', openModal);
  document.getElementById('btn-retry').addEventListener('click', resetQuiz);
  document.getElementById('btn-retry-modal').addEventListener('click', function(){
    closeModal();
    resetQuiz();
  });
  document.getElementById('modal-close').addEventListener('click', closeModal);
  modalOverlay.addEventListener('click', function(e){
    if(e.target === modalOverlay){ closeModal(); }
  });
  document.addEventListener('keydown', function(e){
    if(e.key === 'Escape' && !modalOverlay.hidden){ closeModal(); }
  });

  function startQuiz(){
    screenStart.hidden = true;
    screenQuestion.hidden = false;
    current = 0;
    renderQuestion();
  }

  function resetQuiz(){
    answers = new Array(questions.length).fill(null);
    current = 0;
    lastMbti = null;
    screenCompleted.hidden = true;
    screenQuestion.hidden = false;
    screenStart.hidden = true;
    renderQuestion();
  }

  function renderQuestion(){
    var q = questions[current];
    var pct = Math.round(((current) / questions.length) * 100);
    progressFill.style.width = pct + '%';
    progressCount.textContent = (current + 1) + ' / ' + questions.length;
    questionText.textContent = q.text;

    optionsWrap.innerHTML = '';
    q.options.forEach(function(opt){
      var btn = document.createElement('button');
      btn.type = 'button';
      btn.className = 'option-btn';
      btn.textContent = opt.text;
      btn.addEventListener('click', function(){ selectAnswer(opt.letter); });
      optionsWrap.appendChild(btn);
    });

    btnBack.disabled = (current === 0);
  }

  function selectAnswer(letter){
    answers[current] = letter;
    if(current < questions.length - 1){
      current += 1;
      renderQuestion();
    } else {
      finishQuiz();
    }
  }

  function goBack(){
    if(current === 0) return;
    current -= 1;
    renderQuestion();
  }

  function finishQuiz(){
    var mbti = computeResult();
    lastMbti = mbti;
    screenQuestion.hidden = true;
    screenCompleted.hidden = false;
    showResult(mbti);
    openModal();
  }

  function computeResult(){
    var axisLetters = { EI: [], SN: [], TF: [], JP: [] };
    questions.forEach(function(q, idx){
      axisLetters[q.axis].push(answers[idx]);
    });

    function majority(letters){
      var counts = {};
      letters.forEach(function(l){ counts[l] = (counts[l] || 0) + 1; });
      var winner = null, best = -1;
      Object.keys(counts).forEach(function(k){
        if(counts[k] > best){ best = counts[k]; winner = k; }
      });
      return winner;
    }

    var order = ['EI', 'SN', 'TF', 'JP'];
    var mbti = order.map(function(axis){ return majority(axisLetters[axis]); }).join('');
    return mbti;
  }

  function showResult(mbti){
    var r = results[mbti];
    document.getElementById('result-type-name').textContent = r.title;
    document.getElementById('result-mbti').textContent = mbti;
    document.getElementById('result-desc').textContent = r.desc;
    var list = document.getElementById('result-traits');
    list.innerHTML = '';
    r.traits.forEach(function(t){
      var li = document.createElement('li');
      li.textContent = t;
      list.appendChild(li);
    });
  }

  function openModal(){
    if(lastMbti){ showResult(lastMbti); }
    modalOverlay.hidden = false;
  }

  function closeModal(){
    modalOverlay.hidden = true;
  }

})();
</script>

</body>
</html>
