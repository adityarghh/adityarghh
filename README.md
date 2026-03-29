<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1"/>
<title>adi — github profile</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
*{margin:0;padding:0;box-sizing:border-box}
:root{--bg:#080b12;--bg2:#0e1420;--coral:#ff6b6b;--amber:#ffcc44;--teal:#4ecdc4;--blue:#45b7d1;--text:#e8eaf0;--muted:#8892a4;--border:rgba(255,255,255,0.07)}
html{scroll-behavior:smooth}
body{background:var(--bg);color:var(--text);font-family:'Syne',sans-serif;overflow-x:hidden;min-height:100vh}
#bg-canvas{position:fixed;inset:0;z-index:0;pointer-events:none}
.page{position:relative;z-index:1;max-width:760px;margin:0 auto;padding:0 24px 80px}
.hero{min-height:100vh;display:flex;flex-direction:column;justify-content:center;padding-top:60px;position:relative}
.hero-tag{font-family:'JetBrains Mono',monospace;font-size:13px;color:var(--teal);letter-spacing:2px;text-transform:uppercase;margin-bottom:20px;opacity:0;animation:fadeUp 0.6s ease 0.2s forwards}
.hero-name{font-size:clamp(52px,10vw,88px);font-weight:800;line-height:1;letter-spacing:-2px;margin-bottom:16px;opacity:0;animation:fadeUp 0.7s ease 0.35s forwards}
.hero-name .grad{background:linear-gradient(135deg,var(--coral),var(--amber),var(--teal));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text}
.hero-desc{font-size:18px;color:var(--muted);font-weight:400;max-width:460px;line-height:1.7;margin-bottom:36px;opacity:0;animation:fadeUp 0.7s ease 0.5s forwards}
.hero-desc b{color:var(--text);font-weight:600}
.typewriter-wrap{font-family:'JetBrains Mono',monospace;font-size:14px;color:var(--coral);margin-bottom:40px;opacity:0;animation:fadeUp 0.7s ease 0.65s forwards;min-height:22px}
.typewriter-wrap::after{content:'|';animation:blink 0.8s infinite;margin-left:2px}
@keyframes blink{0%,100%{opacity:1}50%{opacity:0}}
.hero-pills{display:flex;flex-wrap:wrap;gap:10px;opacity:0;animation:fadeUp 0.7s ease 0.8s forwards}
.pill{padding:7px 16px;border-radius:100px;font-size:12.5px;font-family:'JetBrains Mono',monospace;border:1px solid var(--border);background:rgba(255,255,255,0.04);color:var(--muted);transition:all 0.2s;cursor:default}
.pill:hover{border-color:var(--teal);color:var(--teal);background:rgba(78,205,196,0.08)}
.pill.hot{border-color:rgba(255,107,107,0.4);color:var(--coral);background:rgba(255,107,107,0.07)}
.scroll-hint{position:absolute;bottom:32px;left:50%;transform:translateX(-50%);display:flex;flex-direction:column;align-items:center;gap:8px;opacity:0;animation:fadeUp 0.7s ease 1.2s forwards;color:var(--muted);font-size:11px;font-family:'JetBrains Mono',monospace;letter-spacing:1px}
.scroll-dot{width:6px;height:6px;border-radius:50%;background:var(--teal);animation:scrollBounce 1.6s ease infinite}
@keyframes scrollBounce{0%,100%{transform:translateY(0)}50%{transform:translateY(8px)}}
section{margin-bottom:80px}
.sec-label{font-family:'JetBrains Mono',monospace;font-size:11px;letter-spacing:3px;text-transform:uppercase;color:var(--teal);margin-bottom:28px;display:flex;align-items:center;gap:12px}
.sec-label::after{content:'';flex:1;height:1px;background:linear-gradient(90deg,rgba(78,205,196,0.3),transparent)}
.code-card{background:var(--bg2);border:1px solid var(--border);border-radius:16px;padding:24px 28px;font-family:'JetBrains Mono',monospace;font-size:13.5px;line-height:2;position:relative;overflow:hidden}
.code-card::before{content:'';position:absolute;top:0;left:0;right:0;height:1px;background:linear-gradient(90deg,var(--coral),var(--amber),var(--teal))}
.dot-row{display:flex;gap:6px;margin-bottom:18px}
.dot{width:11px;height:11px;border-radius:50%}
.dot.r{background:#ff5f57}.dot.y{background:#febc2e}.dot.g{background:#28c840}
.kw{color:#ff7b9c}.str{color:#98d4a3}.key{color:#79c0ff}.val{color:var(--amber)}.cm{color:#4a5568;font-style:italic}
.proj-grid{display:flex;flex-direction:column;gap:14px}
.proj-card{background:var(--bg2);border:1px solid var(--border);border-radius:14px;padding:20px 24px;display:flex;align-items:center;gap:20px;transition:all 0.25s;cursor:default;position:relative;overflow:hidden}
.proj-card::after{content:'';position:absolute;inset:0;background:linear-gradient(135deg,rgba(255,107,107,0.04),transparent);opacity:0;transition:opacity 0.25s}
.proj-card:hover{border-color:rgba(255,107,107,0.25);transform:translateX(4px)}
.proj-card:hover::after{opacity:1}
.proj-emoji{font-size:28px;flex-shrink:0;width:44px;text-align:center}
.proj-info{flex:1}
.proj-name{font-size:15px;font-weight:700;color:var(--text);margin-bottom:4px}
.proj-desc{font-size:13px;color:var(--muted);line-height:1.5}
.proj-tags{display:flex;gap:6px;flex-wrap:wrap;margin-top:10px}
.tag{font-family:'JetBrains Mono',monospace;font-size:10.5px;padding:3px 10px;border-radius:6px;background:rgba(255,255,255,0.05);border:1px solid var(--border);color:var(--muted)}
.proj-live{font-family:'JetBrains Mono',monospace;font-size:10px;color:var(--coral);border:1px solid rgba(255,107,107,0.35);padding:4px 10px;border-radius:100px;display:flex;align-items:center;gap:5px;flex-shrink:0;background:rgba(255,107,107,0.07)}
.live-dot{width:5px;height:5px;border-radius:50%;background:var(--coral);animation:pulse-dot 1.5s infinite}
@keyframes pulse-dot{0%,100%{box-shadow:0 0 0 0 rgba(255,107,107,0.5)}50%{box-shadow:0 0 0 5px rgba(255,107,107,0)}}
.stack-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(100px,1fr));gap:10px}
.stack-item{background:var(--bg2);border:1px solid var(--border);border-radius:12px;padding:14px 10px;text-align:center;font-family:'JetBrains Mono',monospace;font-size:12px;color:var(--muted);transition:all 0.2s;cursor:default}
.stack-item:hover{border-color:rgba(78,205,196,0.3);color:var(--teal);background:rgba(78,205,196,0.05);transform:translateY(-3px)}
.stack-icon{font-size:22px;display:block;margin-bottom:6px}
.stats-row{display:flex;gap:14px;flex-wrap:wrap}
.stats-row img{border-radius:12px;flex:1;min-width:240px}
.connect-row{display:flex;gap:12px;flex-wrap:wrap}
.conn-btn{padding:12px 22px;border-radius:12px;font-family:'JetBrains Mono',monospace;font-size:13px;font-weight:500;text-decoration:none;border:1px solid var(--border);color:var(--muted);background:var(--bg2);transition:all 0.2s;display:flex;align-items:center;gap:8px}
.conn-btn:hover{color:var(--text);border-color:rgba(255,255,255,0.2);transform:translateY(-2px)}
.conn-btn.primary{background:linear-gradient(135deg,rgba(255,107,107,0.15),rgba(255,204,68,0.1));border-color:rgba(255,107,107,0.35);color:var(--coral)}
.conn-btn.primary:hover{background:rgba(255,107,107,0.2)}
.footer{text-align:center;font-family:'JetBrains Mono',monospace;font-size:12px;color:var(--muted);padding-top:40px;border-top:1px solid var(--border)}
.footer span{color:var(--coral)}
@keyframes fadeUp{from{opacity:0;transform:translateY(20px)}to{opacity:1;transform:translateY(0)}}
.reveal{opacity:0;transform:translateY(24px);transition:opacity 0.6s ease,transform 0.6s ease}
.reveal.visible{opacity:1;transform:none}
</style>
</head>
<body>
<canvas id="bg-canvas"></canvas>
<div class="page">
  <div class="hero">
    <div class="hero-tag">// building cool stuff since 2025</div>
    <h1 class="hero-name">hey, i'm<br/><span class="grad">Aditya.</span></h1>
    <p class="hero-desc"><b>AI engineer & full-stack dev</b> based at VIT Bhopal.<br/>I build things that actually ship — not just sit in repos.</p>
    <div class="typewriter-wrap" id="typer"></div>
    <div class="hero-pills">
      <span class="pill hot">🚀 shipped to prod</span>
      <span class="pill">BTech AI @ VIT</span>
      <span class="pill">LLM integration</span>
      <span class="pill">open to collabs</span>
      <span class="pill">he/him</span>
    </div>
    <div class="scroll-hint"><span>scroll</span><div class="scroll-dot"></div></div>
  </div>

  <section class="reveal">
    <div class="sec-label">01 — about</div>
    <div class="code-card">
      <div class="dot-row"><div class="dot r"></div><div class="dot y"></div><div class="dot g"></div></div>
      <span class="kw">const</span> <span class="key">adi</span> = {<br/>
      &nbsp;&nbsp;<span class="key">building</span>  : <span class="str">"AI-powered web stuff"</span>,<br/>
      &nbsp;&nbsp;<span class="key">learning</span>  : <span class="str">"LLMs · NLP · distributed systems"</span>,<br/>
      &nbsp;&nbsp;<span class="key">ask_me</span>    : <span class="str">"LLM APIs · UI/UX · building products"</span>,<br/>
      &nbsp;&nbsp;<span class="key">fun_fact</span>  : <span class="str">"shipped a live AI app in first year 🤯"</span>,<br/>
      &nbsp;&nbsp;<span class="key">currently</span> : <span class="str">"Core member @ Bit by Bit Club, VIT"</span><br/>
      }
    </div>
  </section>

  <section class="reveal">
    <div class="sec-label">02 — what i've shipped</div>
    <div class="proj-grid">
      <div class="proj-card">
        <div class="proj-emoji">🎤</div>
        <div class="proj-info">
          <div class="proj-name">Baby Steps to the Mic</div>
          <div class="proj-desc">AI public speaking coach — real-time speech transcription & Claude API feedback</div>
          <div class="proj-tags"><span class="tag">Vanilla JS</span><span class="tag">Claude API</span><span class="tag">Web Speech API</span><span class="tag">Vercel</span></div>
        </div>
        <div class="proj-live"><div class="live-dot"></div>live</div>
      </div>
      <div class="proj-card">
        <div class="proj-emoji">💬</div>
        <div class="proj-info">
          <div class="proj-name">Distributed Chat System</div>
          <div class="proj-desc">Multi-client TCP socket server with thread-per-connection & synchronized state</div>
          <div class="proj-tags"><span class="tag">Java</span><span class="tag">TCP/IP</span><span class="tag">Concurrency</span></div>
        </div>
      </div>
      <div class="proj-card">
        <div class="proj-emoji">📄</div>
        <div class="proj-info">
          <div class="proj-name">DocuQuery</div>
          <div class="proj-desc">NLP document retrieval with relevance-ranked results across formats</div>
          <div class="proj-tags"><span class="tag">Python</span><span class="tag">NLP</span><span class="tag">IR</span></div>
        </div>
      </div>
      <div class="proj-card">
        <div class="proj-emoji">🏷️</div>
        <div class="proj-info">
          <div class="proj-name">Offroad-Semantic</div>
          <div class="proj-desc">ML semantic classification — TF-IDF, vectorization, Scikit-learn inference</div>
          <div class="proj-tags"><span class="tag">Python</span><span class="tag">Scikit-learn</span><span class="tag">NLP</span></div>
        </div>
      </div>
    </div>
  </section>

  <section class="reveal">
    <div class="sec-label">03 — tools & stack</div>
    <div class="stack-grid">
      <div class="stack-item"><span class="stack-icon">🐍</span>Python</div>
      <div class="stack-item"><span class="stack-icon">☕</span>Java</div>
      <div class="stack-item"><span class="stack-icon">🌐</span>JavaScript</div>
      <div class="stack-item"><span class="stack-icon">⚛️</span>React</div>
      <div class="stack-item"><span class="stack-icon">💨</span>Tailwind</div>
      <div class="stack-item"><span class="stack-icon">🧪</span>Flask</div>
      <div class="stack-item"><span class="stack-icon">▲</span>Vercel</div>
      <div class="stack-item"><span class="stack-icon">🎨</span>Figma</div>
      <div class="stack-item"><span class="stack-icon">🤖</span>Sklearn</div>
      <div class="stack-item"><span class="stack-icon">🔢</span>NumPy</div>
      <div class="stack-item"><span class="stack-icon">🐼</span>Pandas</div>
      <div class="stack-item"><span class="stack-icon">🐙</span>Git</div>
    </div>
  </section>

  <section class="reveal">
    <div class="sec-label">04 — github stats</div>
    <div class="stats-row">
      <img src="https://github-readme-streak-stats.herokuapp.com/?user=adityarghh&theme=radical&border=30363d&background=0e1420&ring=ff6b6b&fire=ffcc44&currStreakLabel=4ecdc4&sideLabels=8892a4&dates=8892a4" alt="streak"/>
      <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=adityarghh&layout=compact&theme=radical&bg_color=0e1420&border_color=30363d&title_color=ffcc44&text_color=8892a4&langs_count=5" alt="langs"/>
    </div>
  </section>

  <section class="reveal">
    <div class="sec-label">05 — find me</div>
    <div class="connect-row">
      <a href="https://linkedin.com/in/aditya-raj-79a53b314" class="conn-btn primary" target="_blank">
        <svg width="14" height="14" fill="currentColor" viewBox="0 0 24 24"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
        LinkedIn
      </a>
      <a href="https://portfolio-aditya-seven-rho.vercel.app" class="conn-btn" target="_blank">🌐 Portfolio</a>
      <a href="mailto:adiwildinn@gmail.com" class="conn-btn">📧 Email</a>
    </div>
  </section>

  <div class="footer">made with <span>♥</span> and too much caffeine &nbsp;·&nbsp; adityarghh</div>
</div>

<script>
const canvas=document.getElementById('bg-canvas'),ctx=canvas.getContext('2d');
let W,H;
function resize(){W=canvas.width=window.innerWidth;H=canvas.height=window.innerHeight}
resize();window.addEventListener('resize',resize);
const COLORS=['#ff6b6b','#ffcc44','#4ecdc4','#45b7d1','#ff8e53'];
class P{
  constructor(){this.reset(true)}
  reset(init=false){
    this.x=Math.random()*W;this.y=init?Math.random()*H:H+10;
    this.r=Math.random()*1.8+0.4;this.color=COLORS[Math.floor(Math.random()*COLORS.length)];
    this.vx=(Math.random()-.5)*0.3;this.vy=-(Math.random()*0.4+0.15);
    this.alpha=Math.random()*0.5+0.1;this.life=0;this.maxLife=Math.random()*300+200;
  }
  update(){this.x+=this.vx;this.y+=this.vy;this.life++;if(this.y<-10||this.life>this.maxLife)this.reset()}
  draw(){
    ctx.save();ctx.globalAlpha=this.alpha*Math.sin((this.life/this.maxLife)*Math.PI);
    ctx.fillStyle=this.color;ctx.shadowBlur=8;ctx.shadowColor=this.color;
    ctx.beginPath();ctx.arc(this.x,this.y,this.r,0,Math.PI*2);ctx.fill();ctx.restore();
  }
}
const particles=Array.from({length:90},()=>new P());
let mx=300,my=300;
document.addEventListener('mousemove',e=>{mx=e.clientX;my=e.clientY});
function draw(){
  ctx.clearRect(0,0,W,H);
  ctx.save();ctx.strokeStyle='rgba(255,255,255,0.025)';ctx.lineWidth=0.5;
  for(let x=0;x<W;x+=60){ctx.beginPath();ctx.moveTo(x,0);ctx.lineTo(x,H);ctx.stroke()}
  for(let y=0;y<H;y+=60){ctx.beginPath();ctx.moveTo(0,y);ctx.lineTo(W,y);ctx.stroke()}
  ctx.restore();
  const g=ctx.createRadialGradient(mx,my,0,mx,my,300);
  g.addColorStop(0,'rgba(78,205,196,0.045)');g.addColorStop(1,'transparent');
  ctx.fillStyle=g;ctx.fillRect(0,0,W,H);
  particles.forEach(p=>{p.update();p.draw()});
  requestAnimationFrame(draw);
}
draw();
const lines=['building AI-powered web apps 🔨','shipped to prod in year 1 🚀','LLMs · NLP · full-stack dev','open to collabs & hackathons 🤝'];
let li=0,ci=0,del=false;
const el=document.getElementById('typer');
function type(){
  const line=lines[li];
  el.textContent=del?line.slice(0,--ci):line.slice(0,++ci);
  if(!del&&ci===line.length){del=true;setTimeout(type,1800);return}
  if(del&&ci===0){del=false;li=(li+1)%lines.length}
  setTimeout(type,del?35:75);
}
setTimeout(type,1400);
const obs=new IntersectionObserver(entries=>entries.forEach(e=>{if(e.isIntersecting)e.target.classList.add('visible')}),{threshold:0.12});
document.querySelectorAll('.reveal').forEach(el=>obs.observe(el));
</script>
</body>
</html>
