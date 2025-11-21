<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Intercultural Team Project Interactive</title>
<meta name="viewport" content="width=device-width, initial-scale=1" />
<style>
  :root{
    --bg:#7b0018;           /* crimson red */
    --card:#ffffff;         /* white cards */
    --border:#e5e7eb;
    --accent:#b91c1c;       /* deep red */
    --accent-soft:#fee2e2;  /* light red background */
    --text:#111827;         /* near-black text */
    --muted:#6b7280;        /* gray */
  }
  *{box-sizing:border-box;}
  body{
    margin:0;
    min-height:100vh;
    display:flex;
    align-items:center;
    justify-content:center;
    padding:16px;
    font-family:"Nunito", system-ui,-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,Helvetica,Arial,sans-serif;
    color:var(--text);
    background-color:var(--bg);
  }
  .frame{
    width:100%;
    max-width:960px;
    border-radius:18px;
    border:1px solid var(--border);
    background-color:var(--card);
    box-shadow:0 18px 40px rgba(0,0,0,.35);
    padding:20px 20px 16px;
    position:relative;
  }
  .frame-inner{
    position:relative;
    z-index:1;
  }
  header{
    display:flex;
    align-items:center;
    justify-content:space-between;
    margin-bottom:10px;
  }
  .title-wrap{
    display:flex;
    align-items:center;
    gap:10px;
  }
  .orb{
    width:18px;height:18px;border-radius:999px;
    background-color:var(--accent);
  }
  h1{
    font-size:20px;
    margin:0;
    letter-spacing:.02em;
  }
  .badge{
    font-size:11px;
    padding:4px 9px;
    border-radius:999px;
    border:1px solid var(--accent-soft);
    color:var(--accent);
    background:var(--accent-soft);
  }
  .meta{
    display:flex;
    justify-content:space-between;
    align-items:center;
    flex-wrap:wrap;
    gap:10px;
    font-size:12px;
    color:var(--muted);
    margin-bottom:10px;
  }
  .progress{
    font-size:12px;
  }
  .screen{
    border-radius:14px;
    border:1px solid var(--border);
    background-color:#f9fafb;
    padding:14px 14px 14px;
  }
  .screen-top{
    display:flex;
    justify-content:space-between;
    align-items:center;
    margin-bottom:10px;
  }
  .screen-title{
    font-size:15px;
    font-weight:700;
  }
  .screen-tag{
    font-size:11px;
    padding:3px 8px;
    border-radius:999px;
    border:1px solid var(--border);
    color:var(--accent);
    background:#fef2f2;
  }
  .screen-body{
    display:flex;
    flex-direction:column;
    gap:12px;
  }
  .panel{
    border-radius:12px;
    border:1px solid var(--border);
    background-color:#ffffff;
    padding:12px 12px 14px;
  }
  .prompt{
    font-size:15px;
    font-weight:600;
    color:#111827;
    margin-bottom:8px;
  }
  .video-wrap{
    border-radius:10px;
    border:1px solid var(--border);
    overflow:hidden;
    background:#000;
  }
  .video-wrap video{
    width:100%;
    display:block;
  }
  .choices{
    display:flex;
    flex-direction:column;
    gap:10px;
    margin-top:6px;
  }
  .choice-btn{
    appearance:none;
    border-radius:999px;
    border:1px solid var(--border);
    padding:11px 15px;
    background:#ffffff;
    color:var(--text);
    font-size:14px;
    text-align:left;
    cursor:pointer;
    display:flex;
    align-items:center;
    justify-content:space-between;
    gap:10px;
    transition:transform .08s ease, box-shadow .08s ease, border-color .12s ease, background .12s ease;
  }
  .choice-btn span.label{
    flex:1;
  }
  .choice-btn span.key{
    font-size:11px;
    padding:4px 8px;
    border-radius:999px;
    border:1px solid var(--accent-soft);
    color:var(--accent);
    background:var(--accent-soft);
    font-weight:600;
  }
  .choice-btn:hover{
    transform:translateY(-1px);
    box-shadow:0 8px 14px rgba(0,0,0,.12);
    border-color:var(--accent);
    background:#fef2f2;
  }
  .choice-btn:active{
    transform:translateY(0);
    box-shadow:none;
  }
  .choice-btn:disabled{
    opacity:.55;
    cursor:default;
    transform:none;
    box-shadow:none;
  }
  .footer{
    display:flex;
    justify-content:space-between;
    align-items:center;
    margin-top:10px;
    font-size:11px;
    color:var(--muted);
  }
  .btn{
    appearance:none;
    padding:8px 14px;
    border-radius:999px;
    border:1px solid transparent;
    cursor:pointer;
    font-size:13px;
    font-weight:700;
    background:var(--accent);
    color:#ffffff;
    box-shadow:0 8px 18px rgba(0,0,0,.25);
    transition:transform .08s ease, box-shadow .08s ease, background .12s ease, opacity .12s ease;
  }
  .btn:hover:not([disabled]){
    transform:translateY(-1px);
    box-shadow:0 12px 24px rgba(0,0,0,.3);
    background:#991b1b;
  }
  .btn:active:not([disabled]){
    transform:translateY(0);
    box-shadow:none;
  }
  .btn.secondary{
    background:#ffffff;
    color:var(--accent);
    border-color:var(--accent);
    box-shadow:none;
  }
  .btn.secondary:hover:not([disabled]){
    background:#fef2f2;
  }
  .btn[disabled]{
    opacity:.5;
    cursor:not-allowed;
    box-shadow:none;
  }
  .status-dot{
    width:8px;height:8px;border-radius:50%;
    background:#22c55e;
    margin-right:6px;
  }
  .center{
    text-align:center;
  }
  .small-note{
    font-size:12px;
    color:var(--muted);
    margin-top:6px;
  }
  .ending-text{
    font-size:13px;
    margin-top:10px;
    color:#374151;
  }
</style>
</head>
<body>
  <div class="frame">
    <div class="frame-inner">
      <header>
        <div class="title-wrap">
          <div class="orb"></div>
          <div>
            <h1>Intercultural Team Project Simulator</h1>
            <div style="font-size:11px;color:var(--muted);margin-top:2px;">Choose your response style and see how your teammate reacts.</div>
          </div>
        </div>
        <span class="badge">Class demo · 4 scenes · 1 ending</span>
      </header>

      <div class="meta">
        <div class="progress" id="progressLabel">Opening · Professor announces the project</div>
        <div><span class="status-dot"></span>Interactive mode</div>
      </div>

      <section class="screen">
        <div class="screen-top">
          <div class="screen-title" id="screenTitle">Opening</div>
          <div class="screen-tag" id="screenTag">Intro</div>
        </div>
        <div class="screen-body" id="screenBody">
          <!-- dynamic content -->
        </div>
        <div class="footer">
          <div>Tip: You can press Start anytime to move on.</div>
          <button class="btn secondary" id="restartBtn" type="button">Restart</button>
        </div>
      </section>
    </div>
  </div>

<script>
let currentSceneIndex = -1; // -1 = opening
const totalScenes = 4;

const scenes = [
  {
    id: "S1",
    title: "Scene 1 — Scheduling the Meeting",
    tag: "Project logistics",
    prompt: "You and your partner need to set a time for your first team meeting. How do you respond?",
    options: [
      { key:"A", text:"I'm fine with any time. Whatever is most convenient for you.", reactionVideo:"media/S1_A.mp4" },
      { key:"B", text:"I can meet Tuesday at 3 or Thursday at 10. Which works for you?", reactionVideo:"media/S1_B.mp4" },
      { key:"C", text:"I'm flexible most afternoons. We can decide the exact time later.", reactionVideo:"media/S1_C.mp4" }
    ]
  },
  {
    id: "S2",
    title: "Scene 2 — Partner's Topic: K-Food & BTS",
    tag: "Idea discussion",
    prompt: "Your partner suggests a topic: “Korean Food and BTS: How They Improve Intercultural Communication.” How do you react?",
    options: [
      { key:"A", text:"That's interesting. Maybe we can add another perspective to make it more balanced.", reactionVideo:"media/S2_A.mp4" },
      { key:"B", text:"Yeah, but I don't think BTS and food match the assignment that well. Maybe we need something more academic.", reactionVideo:"media/S2_B.mp4" },
      { key:"C", text:"The idea is fun and creative. What if we make it bigger, like how K-pop influences global cultural identity?", reactionVideo:"media/S2_C.mp4" }
    ]
  },
  {
    id: "S3",
    title: "Scene 3 — PPT Design Conflict",
    tag: "Conflict handling",
    prompt: "Your partner sends you a PPT draft on KakaoTalk, but you don't like the design. What do you do?",
    options: [
      { key:"A", text:"This looks really good. Would it be okay if I adjust a few details later?", reactionVideo:"media/S3_A.mp4" },
      { key:"B", text:"The slides are good, but the layout is confusing. Can I redesign this section?", reactionVideo:"media/S3_B.mp4" },
      { key:"C", text:"You send a revised file back without explaining in advance.", reactionVideo:"media/S3_C.mp4" }
    ]
  },
  {
    id: "S4",
    title: "Scene 4 — Professor Rejects the Idea",
    tag: "Problem solving",
    prompt: "The professor says, “I think your topic needs to be changed.” How do you cooperate to fix the project?",
    options: [
      { key:"A", text:"Okay. I'll check past examples and adjust the idea on my own, and also see what other groups are doing.", reactionVideo:"media/S4_A.mp4" },
      { key:"B", text:"Let's ask the professor directly for clarification so we don't waste time.", reactionVideo:"media/S4_B.mp4" },
      { key:"C", text:"Let's discuss together and figure out what the professor really wants.", reactionVideo:"media/S4_C.mp4" }
    ]
  }
];

function setProgressLabel(){
  const label = document.getElementById("progressLabel");
  if(currentSceneIndex < 0){
    label.textContent = "Opening · Professor announces the project";
  }else if(currentSceneIndex < scenes.length){
    label.textContent = "Scene " + (currentSceneIndex+1) + " of " + totalScenes;
  }else{
    label.textContent = "Final · Completed team project";
  }
}

function showOpening(){
  currentSceneIndex = -1;
  setProgressLabel();
  const titleEl = document.getElementById("screenTitle");
  const tagEl = document.getElementById("screenTag");
  const body = document.getElementById("screenBody");
  titleEl.textContent = "Opening — The Assignment";
  tagEl.textContent = "Intro";

  body.innerHTML = `
    <div class="panel">
      <div class="prompt">
        The professor announces the final assignment: choose an intercultural communication theory and apply it to a real-world example. 
        You are paired with a Korean student for a team project.
      </div>
      <div class="video-wrap" style="margin-top:8px;">
        <video id="openingVideo" controls playsinline>
          <source src="media/opening.mp4" type="video/mp4">
        </video>
      </div>
      <div class="center" style="margin-top:10px;">
        <button class="btn" id="startBtn" type="button">Start Scenario</button>
        <div class="small-note">You can press Start anytime, even before the video ends.</div>
      </div>
    </div>
  `;

  const startBtn = document.getElementById("startBtn");
  if(startBtn){
    startBtn.addEventListener("click", () => {
      goToScene(0);
    });
  }
}

function goToScene(index){
  if(index < 0){
    showOpening();
    return;
  }
  if(index >= scenes.length){
    showEnding();
    return;
  }
  currentSceneIndex = index;
  const scene = scenes[index];
  setProgressLabel();
  const titleEl = document.getElementById("screenTitle");
  const tagEl = document.getElementById("screenTag");
  const body = document.getElementById("screenBody");
  titleEl.textContent = scene.title;
  tagEl.textContent = scene.tag;

  let choicesHtml = "";
  scene.options.forEach((opt, i)=>{
    choicesHtml += `
      <button class="choice-btn" type="button" onclick="handleChoice(${i})">
        <span class="label">${opt.text}</span>
        <span class="key">Choice ${opt.key}</span>
      </button>
    `;
  });

  body.innerHTML = `
    <div class="panel">
      <div class="prompt">${scene.prompt}</div>
      <div class="choices">
        ${choicesHtml}
      </div>
    </div>
  `;
}

function handleChoice(optionIndex){
  const scene = scenes[currentSceneIndex];
  const selected = scene.options[optionIndex];
  showReaction(selected);
}

function showReaction(option){
  const titleEl = document.getElementById("screenTitle");
  const tagEl = document.getElementById("screenTag");
  const body = document.getElementById("screenBody");
  titleEl.textContent = "Reaction — Teammate's Response";
  tagEl.textContent = "Playback";

  const nextIndex = currentSceneIndex + 1;

  body.innerHTML = `
    <div class="panel">
      <div class="prompt">You chose:</div>
      <div style="font-size:13px;color:#374151;margin-bottom:8px;">${option.text}</div>
      <div class="video-wrap">
        <video id="reactionVideo" controls autoplay playsinline>
          <source src="${option.reactionVideo}" type="video/mp4">
        </video>
      </div>
      <div class="small-note">
        When the video ends, you'll automatically move to the next scene. If it doesn't, use the button below.
      </div>
      <div class="center" style="margin-top:6px;">
        <button class="btn secondary" type="button" onclick="goToScene(${nextIndex})">Skip to Next Scene</button>
      </div>
    </div>
  `;

  const vid = document.getElementById("reactionVideo");
  if(vid){
    vid.addEventListener("ended", ()=>{
      if(nextIndex < scenes.length){
        goToScene(nextIndex);
      }else{
        showEnding();
      }
    });
  }
}

function showEnding(){
  currentSceneIndex = scenes.length;
  setProgressLabel();
  const titleEl = document.getElementById("screenTitle");
  const tagEl = document.getElementById("screenTag");
  const body = document.getElementById("screenBody");
  titleEl.textContent = "Final Ending — Completed Project";
  tagEl.textContent = "Outcome";

  body.innerHTML = `
    <div class="panel">
      <div class="prompt">
        Despite different communication styles, you and your partner adapted to each other and completed the team project.
      </div>
      <div class="video-wrap" style="margin-top:8px;">
        <video id="endingVideo" controls autoplay playsinline>
          <source src="media/ending.mp4" type="video/mp4">
        </video>
      </div>
      <div class="ending-text">
        “Different cultures. Different approaches. One successful team project.”<br/>
        “Diversity strengthens teamwork.”
      </div>
    </div>
  `;
}

document.getElementById("restartBtn").addEventListener("click", ()=>{
  showOpening();
});

showOpening();
</script>
</body>
</html>
