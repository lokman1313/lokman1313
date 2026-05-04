[Uploading lokman_hossen_github_banner_v2.html…]()

<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<style>
  @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Exo+2:wght@300;400;600&display=swap');

  * { margin: 0; padding: 0; box-sizing: border-box; }
  body { background: transparent; width: 100%; }

  .banner {
    width: 100%;
    aspect-ratio: 1500 / 500;
    position: relative;
    overflow: hidden;
    background: #020b18;
    font-family: 'Exo 2', sans-serif;
  }

  canvas#bg { position: absolute; inset: 0; width: 100%; height: 100%; }

  .grid-overlay {
    position: absolute; inset: 0;
    background-image:
      linear-gradient(rgba(0,150,255,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,150,255,0.04) 1px, transparent 1px);
    background-size: 40px 40px;
  }

  .glow-left {
    position: absolute; left: -10%; top: 50%; transform: translateY(-50%);
    width: 35%; height: 80%;
    background: radial-gradient(ellipse, rgba(0,100,255,0.12) 0%, transparent 70%);
    pointer-events: none;
  }
  .glow-right {
    position: absolute; right: -5%; top: 50%; transform: translateY(-50%);
    width: 30%; height: 80%;
    background: radial-gradient(ellipse, rgba(0,200,180,0.1) 0%, transparent 70%);
    pointer-events: none;
  }

  .content {
    position: absolute; inset: 0;
    display: flex; align-items: center; justify-content: space-between;
    padding: 3% 4%;
  }

  /* LEFT */
  .left-section {
    display: flex; flex-direction: column; gap: 5%;
    width: 22%; height: 82%;
    justify-content: center; align-items: flex-start;
  }

  .code-card {
    background: rgba(0, 30, 60, 0.7);
    border: 1px solid rgba(0,150,255,0.25);
    border-radius: 6px;
    padding: 4% 6%;
    width: 100%;
    position: relative; overflow: hidden;
  }

  .code-card::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0; height: 2px;
    background: linear-gradient(90deg, transparent, rgba(0,150,255,0.8), transparent);
    animation: scanline 3s ease-in-out infinite;
  }
  .code-card:nth-child(2)::before { animation-delay: 1s; }
  .code-card:nth-child(3)::before { animation-delay: 2s; }

  @keyframes scanline {
    0%,100% { opacity: 0; transform: translateX(-100%); }
    50% { opacity: 1; transform: translateX(100%); }
  }

  .card-label {
    font-size: clamp(5px, 0.95vw, 11px);
    color: rgba(0,180,255,0.6);
    text-transform: uppercase; letter-spacing: 0.1em;
    margin-bottom: 4%;
    font-family: 'Orbitron', monospace;
  }

  .code-line {
    font-family: 'Courier New', monospace;
    font-size: clamp(5px, 0.8vw, 9.5px);
    line-height: 1.6; color: #a0c8f0;
  }
  .code-line .kw { color: #569cd6; }
  .code-line .fn { color: #dcdcaa; }
  .code-line .str { color: #ce9178; }
  .code-line .num { color: #b5cea8; }
  .code-line .cm { color: rgba(106,153,85,0.9); }

  .cursor {
    display: inline-block; width: 0.5em; height: 1em;
    background: rgba(0,180,255,0.8); vertical-align: text-bottom;
    animation: blink 1s step-end infinite;
  }
  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0} }

  /* CENTER */
  .center-section {
    display: flex; flex-direction: column; align-items: center;
    justify-content: center; flex: 1; text-align: center; padding: 0 2%;
  }

  .chevron-logo { margin-bottom: 2.5%; animation: float 4s ease-in-out infinite; }
  @keyframes float { 0%,100%{transform:translateY(0)} 50%{transform:translateY(-8px)} }

  .chevron-logo svg {
    width: clamp(20px, 3.8vw, 48px); height: auto;
    filter: drop-shadow(0 0 8px rgba(0,180,255,0.6));
  }

  .name {
    font-family: 'Orbitron', sans-serif;
    font-size: clamp(12px, 3.1vw, 42px);
    font-weight: 900; color: #ffffff;
    letter-spacing: 0.05em;
    text-shadow: 0 0 20px rgba(0,150,255,0.5), 0 0 40px rgba(0,100,200,0.3);
    animation: nameGlow 3s ease-in-out infinite alternate;
    line-height: 1.1; margin-bottom: 1%;
  }
  @keyframes nameGlow {
    from { text-shadow: 0 0 15px rgba(0,150,255,0.4), 0 0 30px rgba(0,100,200,0.2); }
    to   { text-shadow: 0 0 25px rgba(0,180,255,0.7), 0 0 50px rgba(0,130,230,0.4); }
  }

  .title {
    font-family: 'Exo 2', sans-serif;
    font-size: clamp(6px, 1.3vw, 17px);
    font-weight: 300; color: rgba(160,210,255,0.9);
    letter-spacing: 0.35em; text-transform: uppercase; margin-bottom: 2.5%;
  }

  .divider {
    width: 60%; height: 1px;
    background: linear-gradient(90deg, transparent, rgba(0,150,255,0.6), rgba(0,220,180,0.6), transparent);
    margin-bottom: 2.5%;
    animation: dividerPulse 2s ease-in-out infinite;
  }
  @keyframes dividerPulse { 0%,100%{opacity:0.6} 50%{opacity:1} }

  /* TAGS - two rows */
  .tags {
    display: flex; flex-wrap: wrap;
    justify-content: center;
    gap: 2% 1.5%;
    max-width: 90%;
  }

  .tag {
    font-size: clamp(4px, 0.78vw, 9.5px);
    color: rgba(160,210,255,0.85);
    letter-spacing: 0.1em; text-transform: uppercase; font-weight: 600;
    padding: 1.2% 2.5%;
    border: 1px solid rgba(0,150,255,0.2);
    border-radius: 3px;
    background: rgba(0,100,200,0.08);
    white-space: nowrap;
    animation: tagAppear 0.5s ease-out both;
  }
  .tag:nth-child(1){animation-delay:.1s}
  .tag:nth-child(2){animation-delay:.15s}
  .tag:nth-child(3){animation-delay:.2s}
  .tag:nth-child(4){animation-delay:.25s}
  .tag:nth-child(5){animation-delay:.3s}
  .tag:nth-child(6){animation-delay:.35s}
  .tag:nth-child(7){animation-delay:.4s}
  .tag:nth-child(8){animation-delay:.45s}

  @keyframes tagAppear {
    from{opacity:0;transform:translateY(6px)}
    to{opacity:1;transform:translateY(0)}
  }

  /* RIGHT */
  .right-section {
    width: 22%; height: 82%;
    display: flex; align-items: center; justify-content: center;
    position: relative;
  }
  .right-section canvas { width: 100%; height: 100%; }

  .top-bar, .bottom-bar {
    position: absolute; left: 0; right: 0; height: 2px;
    background: linear-gradient(90deg, transparent, rgba(0,150,255,0.5), rgba(0,220,180,0.5), transparent);
  }
  .top-bar { top: 0; } .bottom-bar { bottom: 0; }

  .side-line {
    position: absolute; top: 15%; bottom: 15%; width: 1px;
    background: linear-gradient(to bottom, transparent, rgba(0,150,255,0.3), rgba(0,220,180,0.3), transparent);
  }
  .side-line.left { left: 0; } .side-line.right { right: 0; }
</style>
</head>
<body>
<div class="banner" id="banner">
  <canvas id="bg"></canvas>
  <div class="grid-overlay"></div>
  <div class="glow-left"></div>
  <div class="glow-right"></div>
  <div class="top-bar"></div>
  <div class="bottom-bar"></div>
  <div class="side-line left"></div>
  <div class="side-line right"></div>

  <div class="content">
    <!-- LEFT: code cards -->
    <div class="left-section">
      <div class="code-card">
        <div class="card-label">Next.js</div>
        <div class="code-line"><span class="kw">export default</span></div>
        <div class="code-line">&nbsp;<span class="kw">function</span> <span class="fn">Page</span>() {</div>
        <div class="code-line">&nbsp;&nbsp;<span class="kw">return</span> &lt;<span class="fn">App</span>/&gt;}<span class="cursor"></span></div>
      </div>
      <div class="code-card">
        <div class="card-label">MongoDB</div>
        <div class="code-line"><span class="fn">db</span>.<span class="fn">collection</span>(</div>
        <div class="code-line">&nbsp;&nbsp;<span class="str">'users'</span></div>
        <div class="code-line">).<span class="fn">find</span>({})<span class="cursor"></span></div>
      </div>
      <div class="code-card">
        <div class="card-label">Git</div>
        <div class="code-line"><span class="cm">$ git commit -m</span></div>
        <div class="code-line">&nbsp;<span class="str">"feat: new ui"</span></div>
        <div class="code-line"><span class="cm">$ git push<span class="cursor"></span></span></div>
      </div>
    </div>

    <!-- CENTER -->
    <div class="center-section">
      <div class="chevron-logo">
        <svg viewBox="0 0 60 50" fill="none" xmlns="http://www.w3.org/2000/svg">
          <polyline points="5,5 30,28 55,5" stroke="rgba(180,220,255,0.9)" stroke-width="4" stroke-linecap="round" stroke-linejoin="round" fill="none"/>
          <polyline points="5,18 30,41 55,18" stroke="rgba(0,180,255,0.7)" stroke-width="4" stroke-linecap="round" stroke-linejoin="round" fill="none"/>
          <polyline points="5,31 30,54 55,31" stroke="rgba(0,220,180,0.5)" stroke-width="4" stroke-linecap="round" stroke-linejoin="round" fill="none"/>
        </svg>
      </div>
      <div class="name">LOKMAN HOSSEN</div>
      <div class="title">MERN Stack Developer</div>
      <div class="divider"></div>
      <div class="tags">
        <span class="tag">MongoDB</span>
        <span class="tag">Express.js</span>
        <span class="tag">React</span>
        <span class="tag">Node.js</span>
        <span class="tag">Next.js</span>
        <span class="tag">JavaScript</span>
        <span class="tag">Tailwind CSS</span>
        <span class="tag">Git</span>
      </div>
    </div>

    <!-- RIGHT: animated node network -->
    <div class="right-section">
      <canvas id="nodeCanvas"></canvas>
    </div>
  </div>
</div>

<script>
// Starfield
(function() {
  const canvas = document.getElementById('bg');
  const banner = document.getElementById('banner');
  let W, H, ctx, stars = [];
  function resize() {
    W = banner.offsetWidth; H = banner.offsetHeight;
    canvas.width = W; canvas.height = H;
    stars = [];
    for (let i = 0; i < 120; i++) {
      stars.push({ x: Math.random()*W, y: Math.random()*H, r: Math.random()*1.2+0.2, a: Math.random(), da: (Math.random()-0.5)*0.01 });
    }
  }
  function draw() {
    ctx = canvas.getContext('2d');
    ctx.clearRect(0,0,W,H);
    stars.forEach(s => {
      s.a += s.da;
      if (s.a < 0.1 || s.a > 1) s.da *= -1;
      ctx.beginPath(); ctx.arc(s.x, s.y, s.r, 0, Math.PI*2);
      ctx.fillStyle = `rgba(160,210,255,${s.a*0.7})`; ctx.fill();
    });
    requestAnimationFrame(draw);
  }
  resize(); window.addEventListener('resize', resize); draw();
})();

// Node network — MERN + extras
(function() {
  const c = document.getElementById('nodeCanvas');
  const parent = c.parentElement;
  let W, H, ctx, nodes = [], edges = [];

  function resize() {
    W = parent.offsetWidth; H = parent.offsetHeight;
    c.width = W; c.height = H;
    init();
  }

  function init() {
    nodes = []; edges = [];
    const labels = ['React','Node','Mongo','Express','Next.js','Git','JS','Tailwind','API'];
    const pos = [
      [0.5,0.10],[0.15,0.25],[0.82,0.25],[0.05,0.50],
      [0.50,0.48],[0.90,0.50],[0.20,0.75],[0.75,0.75],[0.50,0.88]
    ];
    pos.forEach((p,i) => {
      nodes.push({
        x: p[0]*W, y: p[1]*H,
        ox: p[0]*W, oy: p[1]*H,
        vx:(Math.random()-0.5)*0.22, vy:(Math.random()-0.5)*0.22,
        r: i===4 ? 14 : 10,
        label: labels[i], pulse: 0
      });
    });
    const pairs = [[0,1],[0,2],[1,3],[2,3],[1,4],[2,4],[3,4],[4,5],[4,6],[4,7],[4,8],[6,8],[7,8]];
    pairs.forEach(([a,b]) => edges.push({ a, b, active:false, progress:0, timer: Math.random()*160+40 }));
  }

  function draw() {
    ctx = c.getContext('2d');
    ctx.clearRect(0,0,W,H);

    edges.forEach(e => {
      const a = nodes[e.a], b = nodes[e.b];
      ctx.beginPath(); ctx.moveTo(a.x,a.y); ctx.lineTo(b.x,b.y);
      ctx.strokeStyle = 'rgba(0,120,220,0.18)'; ctx.lineWidth = 1; ctx.stroke();

      e.timer--;
      if (e.timer <= 0) { e.timer = 120+Math.random()*180; e.progress = 0; e.active = true; }
      if (e.active) {
        e.progress += 0.02;
        if (e.progress >= 1) { e.active = false; nodes[e.b].pulse = 18; }
        const px = a.x+(b.x-a.x)*e.progress, py = a.y+(b.y-a.y)*e.progress;
        const g = ctx.createRadialGradient(px,py,0,px,py,7);
        g.addColorStop(0,'rgba(0,200,255,0.95)'); g.addColorStop(1,'rgba(0,200,255,0)');
        ctx.beginPath(); ctx.arc(px,py,5,0,Math.PI*2); ctx.fillStyle=g; ctx.fill();
      }
    });

    nodes.forEach((n,i) => {
      n.x += n.vx; n.y += n.vy;
      if (n.x < n.r+4 || n.x > W-n.r-4) n.vx *= -1;
      if (n.y < n.r+4 || n.y > H-n.r-4) n.vy *= -1;

      const isCenter = i === 4;
      n.pulse = Math.max(0, n.pulse - 0.6);

      if (n.pulse > 0) {
        const gr = ctx.createRadialGradient(n.x,n.y,n.r,n.x,n.y,n.r+n.pulse*0.7+10);
        gr.addColorStop(0,`rgba(0,200,255,${n.pulse*0.04})`); gr.addColorStop(1,'rgba(0,200,255,0)');
        ctx.beginPath(); ctx.arc(n.x,n.y,n.r+n.pulse*0.7+10,0,Math.PI*2);
        ctx.fillStyle=gr; ctx.fill();
      }

      ctx.beginPath(); ctx.arc(n.x,n.y,n.r,0,Math.PI*2);
      ctx.fillStyle = isCenter ? 'rgba(0,80,180,0.92)' : 'rgba(0,40,100,0.85)';
      ctx.strokeStyle = isCenter ? 'rgba(0,200,255,0.95)' : 'rgba(0,150,255,0.55)';
      ctx.lineWidth = isCenter ? 2 : 1;
      ctx.fill(); ctx.stroke();

      ctx.fillStyle = isCenter ? 'rgba(200,240,255,1)' : 'rgba(160,210,255,0.9)';
      ctx.font = `${isCenter?600:400} ${Math.max(6,W*0.028)}px 'Exo 2',sans-serif`;
      ctx.textAlign = 'center'; ctx.textBaseline = 'middle';
      ctx.fillText(n.label, n.x, n.y);
    });

    requestAnimationFrame(draw);
  }

  resize(); window.addEventListener('resize', resize); draw();
})();
</script>
</body>
</html>


<p align="center">
  <a href="https://git.io/typing-svg">
    <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&size=25&pause=1000&color=36BCF7&center=true&vCenter=true&width=500&lines=Hello%2C+There+!;I'm+Lokman+Hossen....;Nice+to+Meet+You+😊" alt="Typing SVG" />
  </a>
</p>

<div align="center">


---

### 🚀 Full Stack Web Developer | Expert in JavaScript, React, Node.js, and Tailwind CSS | Crafting High-Performance Web Applications with MongoDB

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/lokman-hossen-dev/)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/lokman1313)
[![Gmail](https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:lokmanhossenjoy13@gmail.com)

</div>

---

<img align="right" width="320" src="https://github.com/user-attachments/assets/b275c323-d3e6-4075-bd3c-fbf96696dd51" />


### 👨‍💻 Talking about Personal Stuff:

- 🛠️ I’m currently working with **JavaScript, React, Node.js, Express, MongoDB, and Tailwind CSS.**
- 🚀 I’m currently exploring **Next.js, TypeScript, and Advanced Backend Architectures.**
- 📫 Reach me out: **lokmanhossenjoy13@email.com**

### 🌟 My Absolute Favorites:

- 💻 I love exploring new technologies and building cool, functional stuff.
- 🍕 I enjoy community meetups, tech events, and hackathons.

<br clear="right" />

---

<h1 align="center"> 🔥 Languages & Frameworks & Tools 🔥</h1

---

<div align="center">
  <img src="https://skillicons.dev/icons?i=js,react,html,css,tailwind,nodejs,express,mongodb,git,vscode,postman,github,npm" />
</div>

---

### ⌨️ My Coding Activity:

```javascript
const lokmanHossen = {
    pronouns: "he/him",
    code: ["JavaScript", "React", "HTML", "CSS", "Tailwind CSS"],
    tools: ["Node.js", "Express",  "Next", "Firebase", "Git"],
    architecture: ["MERN Stack", "REST APIs", "Frontend Design"],
    techCommunities: {
        mentor: "Web Developer",
        role: "Open Source Contributor"
    },
    challenge: "I am constantly learning and improving my development skills"
};
