# Yousef - Rubik Training

<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>تعلّم حل مكعب روبيك</title>
<style>
:root{box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px);--bg:#eef2f7;--card:#fff;--ink:#14213d;--mute:#5b6577;--line:#d5dbe6;--acc:#b71234;--acc-ink:#fff}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#0e1424;--card:#171f35;--ink:#eef1f8;--mute:#9aa5bd;--line:#2a3555;--acc:#ff5a4f;--acc-ink:#1a0a08}}
:root[data-theme="dark"]{--bg:#0e1424;--card:#171f35;--ink:#eef1f8;--mute:#9aa5bd;--line:#2a3555;--acc:#ff5a4f;--acc-ink:#1a0a08}
*,*::before,*::after{box-sizing:inherit}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
body{margin:0;background:var(--bg);color:var(--ink);font-family:"Segoe UI",Tahoma,"Noto Naskh Arabic",Arial,sans-serif;line-height:1.7}
main{max-width:640px;margin:0 auto;padding:16px}
h1{font-size:1.5rem;margin:4px 0 2px}
.sub{color:var(--mute);margin:0 0 12px;font-size:.95rem}
.scene{perspective:800px;height:270px;display:flex;align-items:center;justify-content:center;touch-action:none;cursor:grab;background:var(--card);border:1px solid var(--line);border-radius:16px;position:relative;overflow:hidden}
#cur{position:absolute;top:10px;inset-inline-start:14px;font:700 1.6rem/1 ui-monospace,Menlo,monospace;color:var(--acc);direction:ltr}
.hint{position:absolute;bottom:8px;inset-inline:0;text-align:center;font-size:.75rem;color:var(--mute)}
.fsb{position:absolute;top:8px;inset-inline-end:10px;width:44px;height:44px;border-radius:12px;border:1px solid var(--line);background:var(--bg);color:var(--ink);font-size:1.3rem;cursor:pointer;z-index:2}
.scene.full{position:fixed;inset:0;z-index:50;height:auto;border-radius:0;border:0}
.scene.full .fsb{top:calc(8px + env(safe-area-inset-top,0px))}
#rig{width:0;height:0;position:relative;transform-style:preserve-3d;transform:rotateX(-28deg) rotateY(-38deg)}
.cubie{position:absolute;width:56px;height:56px;left:-28px;top:-28px;transform-style:preserve-3d}
.f{position:absolute;inset:0;background:#10131c;border:2px solid #0a0c12;border-radius:7px;backface-visibility:hidden}
.F{transform:translateZ(28px)}.B{transform:rotateY(180deg) translateZ(28px)}
.R{transform:rotateY(90deg) translateZ(28px)}.L{transform:rotateY(-90deg) translateZ(28px)}
.U{transform:rotateX(90deg) translateZ(28px)}.D{transform:rotateX(-90deg) translateZ(28px)}
.steps{display:flex;gap:8px;overflow-x:auto;padding:12px 0 6px}
.steps button{flex:0 0 auto;min-width:44px;height:44px;border-radius:12px;border:1px solid var(--line);background:var(--card);color:var(--ink);font:700 1rem inherit;cursor:pointer}
.steps button[aria-current="true"]{background:var(--acc);color:var(--acc-ink);border-color:var(--acc)}
button:focus-visible{outline:3px solid var(--acc);outline-offset:2px}
.lesson{background:var(--card);border:1px solid var(--line);border-radius:16px;padding:16px}
.lesson h2{margin:0 0 6px;font-size:1.2rem}
.lesson p{margin:0 0 12px}
.alg{border-top:1px dashed var(--line);padding:10px 0}
.alg b{display:block;font-size:.9rem;color:var(--mute);font-weight:600}
.alg code{display:block;direction:ltr;text-align:left;font:600 1.05rem/1.6 ui-monospace,Menlo,monospace;margin:2px 0 8px;word-spacing:.35em}
.btn{border:0;border-radius:10px;padding:10px 16px;font:700 .95rem inherit;cursor:pointer;background:var(--acc);color:var(--acc-ink)}
.btn.alt{background:transparent;color:var(--ink);border:1px solid var(--line)}
.row{display:flex;gap:8px;flex-wrap:wrap;margin-top:12px}
.moves{display:grid;grid-template-columns:repeat(6,1fr);gap:6px;margin-top:10px;direction:ltr}
.moves button{height:44px;border-radius:10px;border:1px solid var(--line);background:var(--bg);color:var(--ink);font:700 1rem ui-monospace,Menlo,monospace;cursor:pointer}
.legend{font-size:.85rem;color:var(--mute);margin:12px 0 0}
.mem{display:flex;align-items:center;gap:10px;padding:6px 0}.mem span{flex:1}.mem meter{width:90px}.mem b{direction:ltr;min-width:34px;text-align:left}
</style>
</head>
<body>
<main>
<h1>تعلّم حل مكعب روبيك</h1>
<p class="sub">سبع خطوات للمبتدئين. امسك أي وجه في المكعب واسحبه لتدوير الطبقة بنفسك، أو اضغط على الحركات لتشاهدها بالتفصيل.</p>
<div class="scene" id="scene"><button class="fsb" id="fs" aria-label="ملء الشاشة">⛶</button><div id="cur"></div><div id="rig"></div><div class="hint">اسحب على وجه المكعب لتدوير طبقة، أو اسحب خارجه لتدوير المكعب كله</div></div>
<div class="steps" id="steps" role="tablist" aria-label="الخطوات"></div>
<section class="lesson" id="lesson"></section>
<div class="row"><button class="btn alt" id="reset">إعادة المكعب</button><button class="btn alt" id="mix">اخلط المكعب</button></div>
<p class="legend">جرّب الحركات بنفسك (حرف = مع عقارب الساعة، ’ = عكسها):</p>
<div class="moves" id="moves"></div>
</main>
<script>
const S=56,COL={U:'#ffffff',D:'#ffd500',F:'#009b48',B:'#0046ad',R:'#b71234',L:'#ff5800'};
const rig=document.getElementById('rig'),cur=document.getElementById('cur');
let cubies=[];
const I=[1,0,0,0,1,0,0,0,1];
const mul=(a,b)=>{const r=[];for(let i=0;i<3;i++)for(let j=0;j<3;j++)r.push(a[3*i]*b[j]+a[3*i+1]*b[3+j]+a[3*i+2]*b[6+j]);return r};
const mv=(a,v)=>[0,1,2].map(i=>a[3*i]*v[0]+a[3*i+1]*v[1]+a[3*i+2]*v[2]);
const rotM=(ax,t)=>{const c=Math.cos(t),s=Math.sin(t);return ax==='x'?[1,0,0,0,c,-s,0,s,c]:ax==='y'?[c,0,-s,0,1,0,s,0,c]:[c,-s,0,s,c,0,0,0,1]};
const MV={R:['x',1,c=>c.p[0]===1],L:['x',-1,c=>c.p[0]===-1],U:['y',1,c=>c.p[1]===-1],D:['y',-1,c=>c.p[1]===1],F:['z',1,c=>c.p[2]===1],B:['z',-1,c=>c.p[2]===-1]};
function draw(c,m){m=m||I;const r=mul(m,c.R),p=mv(m,c.p).map(v=>v*S);
c.el.style.transform=`matrix3d(${r[0]},${r[3]},${r[6]},0,${r[1]},${r[4]},${r[7]},0,${r[2]},${r[5]},${r[8]},0,${p[0]},${p[1]},${p[2]},1)`}
function build(){rig.innerHTML='';cubies=[];
for(let x=-1;x<=1;x++)for(let y=-1;y<=1;y++)for(let z=-1;z<=1;z++){
const el=document.createElement('div');el.className='cubie';
const f={F:z===1,B:z===-1,R:x===1,L:x===-1,U:y===-1,D:y===1};
for(const k in f){const d=document.createElement('i');d.className='f '+k;if(f[k])d.style.background=COL[k];el.appendChild(d)}
rig.appendChild(el);const c={el,p:[x,y,z],R:I};cubies.push(c);draw(c)}}
let dur=380;
function turn(tok){return new Promise(res=>{
const f=tok[0],n=tok[1]==='2'?2:1,d=(tok[1]==="'"||tok[1]==='’')?-1:1,[ax,sg,sel]=MV[f];
const L=cubies.filter(sel),A=sg*d*n*Math.PI/2,t0=performance.now(),T=dur*(n===2?1.5:1);
(function tick(now){let k=Math.min(1,(now-t0)/T);const e=k<.5?2*k*k:1-Math.pow(-2*k+2,2)/2,m=rotM(ax,A*e);
L.forEach(c=>draw(c,m));
if(k<1)return requestAnimationFrame(tick);
const mm=rotM(ax,A);L.forEach(c=>{c.p=mv(mm,c.p).map(Math.round);c.R=mul(mm,c.R).map(v=>Math.round(v));draw(c)});res()})(t0)})}
function spin(i,idx,sg){return new Promise(res=>{const ax='xyz'[i],L=cubies.filter(c=>c.p[i]===idx),A=sg*Math.PI/2,t0=performance.now();
(function tick(now){const k=Math.min(1,(now-t0)/260),e=k<.5?2*k*k:1-Math.pow(-2*k+2,2)/2,m=rotM(ax,A*e);L.forEach(c=>draw(c,m));
if(k<1)return requestAnimationFrame(tick);
const mm=rotM(ax,A);L.forEach(c=>{c.p=mv(mm,c.p).map(Math.round);c.R=mul(mm,c.R).map(Math.round);draw(c)});res()})(t0)})}
let q=Promise.resolve();
const enq=fn=>{q=q.then(fn);return q};
const disp=t=>t.replace(/'/g,'’');
const run=(s,fast)=>enq(async()=>{dur=fast?110:380;for(const t of s.split(' ')){cur.textContent=disp(t);await turn(t)}cur.textContent=''});
const STEPS=[
{t:'تعرّف على المكعب والرموز',d:'لكل وجه حرف: U أعلى، D أسفل، R يمين، L يسار، F أمام، B خلف. الحرف وحده يعني ربع لفّة مع عقارب الساعة، والحرف مع ’ يعني عكس العقارب، والرقم 2 يعني لفّتين. المراكز لا تتحرك أبدًا، وهي التي تحدد لون كل وجه.',a:[{l:'شاهد تسلسل بسيط',s:"R U R' U'"}]},
{t:'الصليب الأبيض',d:'ضع المركز الأبيض لأعلى، ثم كوّن علامة + بيضاء حوله، بحيث يطابق لون الحافة الجانبية لون مركز الوجه المجاور. هذه الخطوة تُحلّ بالتفكير وليس بخوارزمية: جرّب الحركات بنفسك من الأزرار بالأسفل.',a:[]},
{t:'زوايا الطبقة الأولى',d:'ضع الزاوية البيضاء فوق مكانها مباشرة (في الطبقة السفلية)، وكرّر الحركات التالية حتى يصير الأبيض لأعلى. قد تحتاج إلى التكرار من مرة إلى خمس مرات.',a:[{l:'أدخل الزاوية',s:"R' D' R D"},{l:'تكرار مرتين',s:"R' D' R D R' D' R D"}]},
{t:'الطبقة الثانية',d:'اقلب المكعب بحيث يكون الأبيض لأسفل. ابحث عن حافة في الطبقة العليا لا تحمل اللون الأصفر، وضعها فوق مركز لونها، ثم أدخلها لليمين أو لليسار.',a:[{l:'إدخال لليمين',s:"U R U' R' U' F' U F"},{l:'إدخال لليسار',s:"U' L' U L U F U' F'"}]},
{t:'الصليب الأصفر',d:'الهدف تكوين علامة + صفراء على الوجه العلوي. إذا رأيت نقطة فقط، أو خطًا، أو شكل حرف L، كرّر الحركات حتى يكتمل الصليب.',a:[{l:'ارسم الصليب',s:"F R U R' U' F'"}]},
{t:'ترتيب الزوايا الصفراء',d:'أولًا اجعل الأصفر لأعلى في كل الزوايا بتكرار الحركة الأولى، ثم بدّل الزوايا الأربع في أماكنها الصحيحة بالحركة الثانية.',a:[{l:'توجيه الأصفر لأعلى',s:"R U R' U R U2 R'"},{l:'تبديل الزوايا',s:"U R U' L' U R' U' L"}]},
{t:'اللمسة الأخيرة',d:'بقي ترتيب الحواف الصفراء. ثبّت وجهين متجاورين مناسبين وكرّر خوارزمية التبديل حتى تتطابق كل الحواف مع المراكز. أحسنت، المكعب انحلّ.',a:[{l:'تبديل الحواف',s:"R U' R U R U R U' R' U' R2"}]}
];
const stEl=document.getElementById('steps'),ls=document.getElementById('lesson');
function show(i){
[...stEl.children].forEach((b,j)=>b.setAttribute('aria-current',j===i));
const s=STEPS[i];ls.innerHTML='<h2></h2><p></p>';ls.firstChild.textContent=(i+1)+'. '+s.t;ls.lastChild.textContent=s.d;
s.a.forEach(a=>{const w=document.createElement('div');w.className='alg';
w.innerHTML='<b></b><code></code><button class="btn">شغّل الحركات</button>';
w.children[0].textContent=a.l;w.children[1].textContent=disp(a.s);
w.children[2].onclick=()=>run(a.s);ls.appendChild(w)})}
STEPS.forEach((s,i)=>{const b=document.createElement('button');b.textContent=i+1;b.setAttribute('role','tab');b.setAttribute('aria-label','الخطوة '+(i+1));b.onclick=()=>show(i);stEl.appendChild(b)});
const mvEl=document.getElementById('moves');
["U","U'","D","D'","R","R'","L","L'","F","F'","B","B'"].forEach(t=>{const b=document.createElement('button');b.textContent=disp(t);b.onclick=()=>run(t);mvEl.appendChild(b)});
document.getElementById('reset').onclick=()=>enq(()=>{build();cur.textContent=''});
document.getElementById('mix').onclick=()=>{const f='UDRLFB',a=[];let l='';for(let i=0;i<16;i++){let x;do{x=f[Math.random()*6|0]}while(x===l);l=x;a.push(x+(Math.random()<.5?"'":''))}run(a.join(' '),true)};
let rx=-28,ry=-38,dn=false,lx=0,ly=0;const sc=document.getElementById('scene');
let full=false,zm=1;const view=()=>rig.style.transform=`scale(${zm}) rotateX(${rx}deg) rotateY(${ry}deg)`;
const N0={F:[0,0,1],B:[0,0,-1],R:[1,0,0],L:[-1,0,0],U:[0,-1,0],D:[0,1,0]};
const D2=Math.PI/180,scr=v=>{const a=ry*D2,b=rx*D2,x1=v[0]*Math.cos(a)+v[2]*Math.sin(a),z1=-v[0]*Math.sin(a)+v[2]*Math.cos(a);return[x1,v[1]*Math.cos(b)-z1*Math.sin(b)]};
const dv=(i,p)=>i===0?[0,-p[2],p[1]]:i===1?[-p[2],0,p[0]]:[-p[1],p[0],0];
let g=null;
sc.onpointerdown=e=>{if(e.target.closest('.fsb'))return;dn=true;lx=e.clientX;ly=e.clientY;sc.setPointerCapture(e.pointerId);
const t=e.target,c=t.classList&&t.classList.contains('f')&&t.style.background&&cubies.find(k=>k.el===t.parentNode);
g=c?{c,n:mv(c.R,N0[t.classList[1]]).map(Math.round),x:e.clientX,y:e.clientY,done:false}:null};
sc.onpointermove=e=>{if(!dn)return;
if(g){if(g.done||Math.hypot(e.clientX-g.x,e.clientY-g.y)<14)return;g.done=true;
const dx=e.clientX-g.x,dy=e.clientY-g.y,ps=g.c.p.map((v,i)=>v+g.n[i]/2);let best=null;
for(let i=0;i<3;i++){if(g.n[i])continue;const s=scr(dv(i,ps)),d=dx*s[0]+dy*s[1];if(!best||Math.abs(d)>Math.abs(best.d))best={i,d}}
const idx=g.c.p[best.i],sg=best.d>0?1:-1;enq(()=>spin(best.i,idx,sg));return}
ry+=(e.clientX-lx)*.6;rx=Math.max(-80,Math.min(80,rx-(e.clientY-ly)*.6));lx=e.clientX;ly=e.clientY;view()};
sc.onpointerup=sc.onpointercancel=()=>{dn=false;g=null};
const fsb=document.getElementById('fs'),de=document.documentElement;
const fit=()=>{zm=full?Math.min(innerHeight/300,innerWidth/330,2.4):1;view()};
function setFull(v){full=v;sc.classList.toggle('full',v);document.body.style.overflow=v?'hidden':'';fsb.textContent=v?'✕':'⛶';fsb.setAttribute('aria-label',v?'خروج من ملء الشاشة':'ملء الشاشة');fit();
try{if(v){Promise.resolve((de.requestFullscreen||de.webkitRequestFullscreen||(()=>{})).call(de)).catch(()=>{});screen.orientation&&screen.orientation.lock&&screen.orientation.lock('landscape').catch(()=>{})}
else{if(document.fullscreenElement)document.exitFullscreen();screen.orientation&&screen.orientation.unlock&&screen.orientation.unlock()}}catch(e){}}
fsb.onclick=()=>setFull(!full);
addEventListener('resize',()=>{if(full)fit()});
document.addEventListener('fullscreenchange',()=>{if(!document.fullscreenElement&&full)setFull(false)});
build();show(0);
</script>
</body>
</html>


