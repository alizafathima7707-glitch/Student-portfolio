[28/10, 7:26 pm] Zehra🐦‍⬛: header id="home"><div class="wrap"><div class="bento">
  <div class="tile t-main">
    <div><h1>Zehra Jabeen A</h1></div>
    <div>
      <p>I’m a <span id="role">student developer</span></p>
      <div class="hero-btns" style="margin-top:1.2rem">
        <a class="btn" href="#projects">See my projects</a>
        <button class="btn ghost" id="resumeBtn">Download resume</button>
      </div>
    </div>
  </div>
  <div class="tile t-photo" aria-label="Photo placeholder">ZJ</div>
  <div class="tile stat"><b data-to="12">0</b><p>Projects built</p></div>
  <div class="tile stat"><b data-to="4">0</b><p>Hackathons joined</p></div>
  <div class="tile t-learn"><small>Currently learning</small><h3>TypeScript and Next.js</h3><p>Building a small blog to practice.</p></div>
  <div class="tile t-links"><a href="#">GitHub</a><a href="#">LinkedIn</a><a href="#contact">Email me</a></div>
</div></div></header>

<div class="toolbar">
    <div class="filters" role="group" aria-label="Filter projects">
      <button aria-pressed="true" data-filter="all">All</button><button aria-pressed="false" data-filter="web">Web</button>
      <button aria-pressed="false" data-filter="python">Python</button><button aria-pressed="false" data-filter="design">Design</button>
    </div>
    <input id="search" type="search" placeholder="Search projects" aria-label="Search projects">
  </div>
  <div class="grid">
    <button class="card" data-cat="web" data-title="Study Buddy" data-tech="HTML,CSS,JavaScript" data-desc="A timetable and flashcard web app used by 120 classmates." data-link="#"><div class="thumb"></div><div class="txt"><h3>Study Buddy</h3><span class="tag">Web</span></div></button>
    <!-- the other project cards follow the same pattern -->
  </div>

<dialog id="projDialog">
  <h3 id="dTitle"></h3><p id="dDesc"></p><div class="chips" id="dTech"></div>
  <a class="btn" id="dLink" href="#">View project</a> <button class="btn ghost" id="dClose">Close</button>
</dialog>

<form id="form" novalidate>
    <div><label for="name">Name</label><input id="name" autocomplete="name"><span class="err" id="eName"></span></div>
    <div><label for="email">Email</label><input id="email" type="email" autocomplete="email"><span class="err" id="eEmail"></span></div>
    <div><label for="msg">Message <span class="count" id="count">0 / 300</span></label><textarea id="msg" rows="4" maxlength="300"></textarea><span class="err" id="eMsg"></span></div>
    <button class="btn" type="submit">Send message</button>
    <p id="ok" hidden>Thanks! Your message is ready to send.</p>
  </form>
[28/10, 7:26 pm] Zehra🐦‍⬛: :root{--bg:#f2f4ff;--card:#fff;--ink:#0e1230;--muted:#555b82;--line:#dde1f6;
  --blue:#3b5bff;--lime:#c8ff3d;--mag:#ff4fa0;--cyan:#27d3ff;--dk:#0e1230;
  --head:'Syne','Trebuchet MS',sans-serif;--body:'Manrope',system-ui,sans-serif;color-scheme:light}
@media(prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#090c1a;--card:#121730;--ink:#eef0ff;--muted:#9aa1c8;--line:#252c52;color-scheme:dark}}
:root[data-theme="dark"]{--bg:#090c1a;--card:#121730;--ink:#eef0ff;--muted:#9aa1c8;--line:#252c52;color-scheme:dark}

.bento{display:grid;grid-template-columns:repeat(4,1fr);grid-auto-rows:minmax(150px,auto);gap:14px}
.tile{padding:1.4rem}
.t-main{grid-column:span 2;grid-row:span 2;background:var(--blue);color:#fff;border:0;display:flex;flex-direction:column;justify-content:space-between;gap:1.5rem}
.t-main h1{font-size:clamp(2.6rem,7vw,4.6rem);letter-spacing:-.03em}
.t-main p{color:#e4e8ff;font-size:1.15rem}
#role{color:var(--lime);font-weight:700}
#role::after{content:"|";animation:blink 1s steps(2) infinite}
@keyframes blink{50%{opacity:0}}
.hero-btns{display:flex;gap:.8rem;flex-wrap:wrap}
.t-photo{grid-row:span 2;background:linear-gradient(160deg,var(--mag),var(--blue));border:0;display:grid;place-items:center;font:800 4.5rem var(--head);color:#fff}
.stat b{display:block;font:800 clamp(2.2rem,5vw,3.2rem) var(--head);color:var(--blue)}
.t-learn{background:var(--lime);border:0;color:var(--dk);grid-column:span 2}
.t-learn p,.t-learn small{color:#2c3320}
.t-learn h3{margin:.3rem 0}
.t-links{display:flex;flex-direction:column;justify-content:center;gap:.5rem;grid-column:span 2}
.t-links a{font-weight:700;text-decoration:none}
.t-links a:hover{color:var(--blue)}
@media(max-width:900px){.bento{grid-template-columns:repeat(2,1fr)}.t-main{grid-column:span 2}.t-photo{grid-row:span 1;min-height:150px}}

.grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(240px,1fr));gap:14px}
.card{overflow:hidden;text-align:left;cursor:pointer;font:inherit;color:var(--ink);padding:0;transition:transform .2s,box-shadow .2s}
.card:hover{transform:translateY(-5px);box-shadow:0 18px 40px -20px var(--blue)}
[28/10, 7:26 pm] Zehra🐦‍⬛: /* Theme toggle: remembers choice, falls back to the system setting */
let saved=null;try{saved=localStorage.getItem('theme')}catch(e){}
root.dataset.theme=saved||(matchMedia('(prefers-color-scheme:dark)').matches?'dark':'light');
$('#theme').onclick=()=>{const t=root.dataset.theme==='dark'?'light':'dark';root.dataset.theme=t;try{localStorage.setItem('theme',t)}catch(e){}};

/* Count-up stats and skill bars: run once when visible */
const io=new IntersectionObserver(es=>es.forEach(e=>{
  if(!e.isIntersecting)return;io.unobserve(e.target);
  const el=e.target;
  if(el.dataset.to){const to=+el.dataset.to,t0=performance.now();
    (function f(t){const p=Math.min((t-t0)/1200,1);el.textContent=Math.round(to*p);if(p<1)requestAnimationFrame(f)})(t0)}
  else el.style.width=el.dataset.level+'%';
}),{threshold:.4});
$$('[data-to],.bar i').forEach(el=>io.observe(el));

/* Project filter + search */
let cat='all';const cards=$$('.card');
function apply(){
  const q=$('#search').value.trim().toLowerCase();let n=0;
  cards.forEach(c=>{
    const ok=(cat==='all'||c.dataset.cat.split(' ').includes(cat))&&(c.dataset.title+' '+c.dataset.tech).toLowerCase().includes(q);
    c.hidden=!ok;if(ok)n++;
  });
  $('#none').style.display=n?'none':'block';
}
$$('.filters button').forEach(b=>b.onclick=()=>{cat=b.dataset.filter;$$('.filters button').forEach(x=>x.setAttribute('aria-pressed',x===b));apply()});
$('#search').oninput=apply;

$('#form').onsubmit=e=>{
  e.preventDefault();$('#ok').hidden=true;
  const okMail=/^[^\s@]+@[^\s@]+\.[^\s@]{2,}$/.test($('#email').value.trim());
  $('#eName').textContent=$('#name').value.trim().length<2?'Enter your name.':'';
  $('#eEmail').textContent=okMail?'':'Enter an email like name@example.com.';
  $('#eMsg').textContent=$('#msg').value.trim().length<10?'Write at least 10 characters.':'';
  if(!$('#eName').textContent&&!$('#eEmail').textContent&&!$('#eMsg').textContent){$('#ok').hidden=false;e.target.reset();$('#count').textContent='0 / 300'}
};
