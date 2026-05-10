
<link href="https://fonts.googleapis.com/css2?family=Fredoka+One&family=Nunito:wght@400;700;800&display=swap" rel="stylesheet">
<style>
*{box-sizing:border-box;margin:0;padding:0}
body{background:transparent}
#app{width:100%;max-width:380px;margin:0 auto;font-family:'Nunito',sans-serif;background:var(--color-background-primary);border:.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-lg);overflow:hidden;user-select:none;-webkit-user-select:none}
.screen{display:none}.screen.active{display:block}
canvas{display:block;width:100%}
.home-body{padding:14px 20px 18px}
.game-title{font-family:'Fredoka One',cursive;font-size:36px;color:#6C63FF;text-align:center;line-height:1.1;margin-bottom:3px}
.game-sub{font-size:13px;color:var(--color-text-secondary);text-align:center;margin-bottom:14px}
.stat-row{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:14px}
.stat-box{background:var(--color-background-secondary);border:.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-md);padding:10px 12px;text-align:center}
.stat-label{font-size:11px;color:var(--color-text-secondary)}
.stat-val{font-size:22px;font-weight:700;color:var(--color-text-primary);font-family:'Fredoka One',cursive}
.btn-primary{width:100%;padding:15px;margin-bottom:9px;background:#6C63FF;color:#fff;border:none;border-radius:var(--border-radius-md);font-size:18px;font-family:'Fredoka One',cursive;cursor:pointer;transition:opacity .1s,transform .1s}
.btn-primary:active{opacity:.88;transform:scale(.98)}
.btn-secondary{width:100%;padding:12px;background:var(--color-background-secondary);color:var(--color-text-primary);border:.5px solid var(--color-border-secondary);border-radius:var(--border-radius-md);font-size:15px;font-family:'Nunito',sans-serif;font-weight:700;cursor:pointer}
.btn-secondary:active{background:var(--color-background-tertiary)}
.shop-header{display:flex;align-items:center;gap:10px;padding:13px 16px;border-bottom:.5px solid var(--color-border-tertiary)}
.shop-title{font-family:'Fredoka One',cursive;font-size:20px;color:var(--color-text-primary);flex:1}
.shop-pts{font-size:15px;color:#F59E0B;font-weight:800;font-family:'Fredoka One',cursive}
.btn-back{background:none;border:.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-md);padding:6px 12px;cursor:pointer;color:var(--color-text-primary);font-size:13px;font-family:'Nunito',sans-serif;font-weight:600}
.shop-body{padding:10px 14px 18px}
.shop-cat{font-size:11px;color:var(--color-text-secondary);font-weight:700;letter-spacing:.06em;margin:12px 0 8px}
.upg-card{display:flex;align-items:center;gap:12px;background:var(--color-background-primary);border:.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-lg);padding:13px 14px;margin-bottom:8px}
.upg-icon{width:44px;height:44px;flex-shrink:0;border-radius:var(--border-radius-md);display:flex;align-items:center;justify-content:center;font-size:24px}
.upg-info{flex:1;min-width:0}
.upg-name{font-size:14px;font-weight:800;color:var(--color-text-primary)}
.upg-desc{font-size:12px;color:var(--color-text-secondary);margin-top:2px;line-height:1.4}
.upg-stat{font-size:11px;color:var(--color-text-tertiary);margin-top:2px}
.upg-bar-wrap{height:4px;background:var(--color-background-tertiary);border-radius:2px;margin-top:5px;overflow:hidden}
.upg-bar-fill{height:100%;border-radius:2px;transition:width .3s}
.btn-buy{flex-shrink:0;padding:8px 12px;background:#6C63FF;color:#fff;border:none;border-radius:var(--border-radius-md);font-size:12px;font-weight:700;font-family:'Nunito',sans-serif;cursor:pointer;white-space:nowrap}
.btn-buy:active{opacity:.85}
.btn-buy.locked{background:var(--color-background-secondary);color:var(--color-text-secondary);border:.5px solid var(--color-border-tertiary);cursor:not-allowed}
.btn-buy.maxed{background:#059669;cursor:default}
#hud-bar{display:grid;grid-template-columns:1fr 1fr 1fr 1fr;gap:3px;padding:7px 10px;border-bottom:.5px solid var(--color-border-tertiary);background:var(--color-background-secondary)}
.hud-cell{text-align:center}
.hud-label{font-size:9px;color:var(--color-text-secondary);font-weight:700;letter-spacing:.04em}
.hud-val{font-size:15px;font-weight:700;color:var(--color-text-primary);font-family:'Fredoka One',cursive}
#ctrl-row{display:grid;grid-template-columns:1fr 1fr;gap:8px;padding:8px 12px;border-top:.5px solid var(--color-border-tertiary)}
.ctrl-btn{background:var(--color-background-secondary);border:.5px solid var(--color-border-secondary);border-radius:var(--border-radius-md);padding:16px 0;font-size:26px;cursor:pointer;text-align:center;-webkit-tap-highlight-color:transparent;transition:background .1s,transform .08s}
.ctrl-btn.held,.ctrl-btn:active{background:var(--color-background-tertiary);transform:scale(.95)}
#gameover-body{padding:24px 20px;text-align:center}
.go-title{font-family:'Fredoka One',cursive;font-size:28px;color:var(--color-text-primary);margin-bottom:5px}
.go-sub{font-size:13px;color:var(--color-text-secondary);margin-bottom:14px}
.go-grid{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:12px}
.go-box{background:var(--color-background-secondary);border-radius:var(--border-radius-md);padding:14px 12px}
.go-box-label{font-size:11px;color:var(--color-text-secondary)}
.go-box-val{font-size:22px;font-weight:700;font-family:'Fredoka One',cursive;color:var(--color-text-primary)}
.lives-display{display:flex;justify-content:center;gap:6px;margin-bottom:16px;font-size:26px}
</style>

<div id="app">
  <div id="screen-home" class="screen active">
    <canvas id="cv-home" width="380" height="170"></canvas>
    <div class="home-body">
      <div class="game-title">Sky Jumper</div>
      <div class="game-sub">Saute toujours plus haut, améliore ton héros !</div>
      <div class="stat-row">
        <div class="stat-box"><div class="stat-label">🏆 Record</div><div class="stat-val" id="home-record">0m</div></div>
        <div class="stat-box"><div class="stat-label">⭐ Points</div><div class="stat-val" id="home-pts">0</div></div>
      </div>
      <button class="btn-primary" onclick="startGame()">🚀 Jouer !</button>
      <button class="btn-secondary" onclick="openShop()">🛍️ Boutique d'améliorations</button>
    </div>
  </div>

  <div id="screen-shop" class="screen">
    <div class="shop-header">
      <button class="btn-back" onclick="openHome()">← Retour</button>
      <div class="shop-title">Boutique</div>
      <div class="shop-pts" id="shop-pts">0 pts</div>
    </div>
    <div class="shop-body" id="shop-list"></div>
  </div>

  <div id="screen-game" class="screen">
    <div id="hud-bar">
      <div class="hud-cell"><div class="hud-label">POINTS</div><div class="hud-val" id="hud-pts">0</div></div>
      <div class="hud-cell"><div class="hud-label">HAUTEUR</div><div class="hud-val" id="hud-h">0m</div></div>
      <div class="hud-cell"><div class="hud-label">RECORD</div><div class="hud-val" id="hud-rec">0m</div></div>
      <div class="hud-cell"><div class="hud-label">VIES</div><div class="hud-val" id="hud-lives">❤️</div></div>
    </div>
    <canvas id="cv-game" width="380" height="310"></canvas>
    <div id="ctrl-row">
      <button class="ctrl-btn" id="btn-left">◀</button>
      <button class="ctrl-btn" id="btn-right">▶</button>
    </div>
  </div>

  <div id="screen-over" class="screen">
    <div id="gameover-body">
      <div class="go-title" id="go-title">Partie terminée !</div>
      <div class="go-sub" id="go-sub"></div>
      <div class="lives-display" id="go-lives"></div>
      <div class="go-grid">
        <div class="go-box"><div class="go-box-label">Hauteur</div><div class="go-box-val" id="go-h">0m</div></div>
        <div class="go-box"><div class="go-box-label">Points gagnés</div><div class="go-box-val" id="go-pts">+0</div></div>
      </div>
      <div class="go-grid">
        <div class="go-box"><div class="go-box-label">Meilleur combo</div><div class="go-box-val" id="go-combo">x0</div></div>
        <div class="go-box"><div class="go-box-label">Total cumulé</div><div class="go-box-val" id="go-total">0</div></div>
      </div>
      <button class="btn-primary" onclick="startGame()" style="margin-top:10px;margin-bottom:9px">🔄 Rejouer</button>
      <button class="btn-secondary" onclick="openHome()">🏠 Accueil</button>
    </div>
  </div>
</div>

<script>
'use strict';

// ═══════════════════════════════════════
//  CONSTANTES
// ═══════════════════════════════════════
const CW = 380, CH = 310;
const GRAVITY   = 0.54;
const FEET      = 20;    // offset pied depuis charY
const BEVEL     = 6;     // hauteur biseau 3D → surface = p.y - BEVEL
const FRONT     = 10;    // hauteur face avant plateforme
const GAP_MIN   = 50;    // espacement vertical min entre plateformes
const GAP_MAX   = 68;    // espacement vertical max
const INVINC    = 90;    // frames d'invincibilité
const RESPAWN   = 52;    // frames animation mort
const CAM_RATIO = 0.38;  // position cible du perso dans l'écran

// ═══════════════════════════════════════
//  UPGRADES (sans répulsif parasyte)
// ═══════════════════════════════════════
const UPGRADES = [
  { id:'speed',  name:'Vitesse',      icon:'👟', cat:'move', desc:'Déplacement gauche/droite plus rapide', color:'#EDE9FE', bar:'#7C3AED', baseCost:80,  costMult:2.2, maxLvl:5, lvl:0, stat: l => l ? `+${l*20}% vitesse`   : 'Niveau de base' },
  { id:'jump',   name:'Hauteur saut', icon:'⬆️', cat:'move', desc:'Saute plus haut à chaque rebond',       color:'#D1FAE5', bar:'#059669', baseCost:120, costMult:2.5, maxLvl:5, lvl:0, stat: l => l ? `+${l*15}% hauteur`  : 'Niveau de base' },
  { id:'magnet', name:'Aimant',       icon:'🧲', cat:'move', desc:'Plateformes plus larges',                color:'#E0F2FE', bar:'#0284C7', baseCost:200, costMult:2.8, maxLvl:4, lvl:0, stat: l => l ? `+${l*12}px largeur` : 'Inactif'         },
  { id:'life',   name:'Vie bonus',    icon:'❤️', cat:'surv', desc:'Une vie supplémentaire par niveau',     color:'#FFE4E6', bar:'#E11D48', baseCost:300, costMult:3.5, maxLvl:3, lvl:0, stat: l => l ? `${1+l} vies`        : '1 vie de base'   },
  { id:'shield', name:'Bouclier',     icon:'🛡️', cat:'surv', desc:'Absorbe 1 chute sans perdre de vie',    color:'#FEF3C7', bar:'#D97706', baseCost:250, costMult:3.0, maxLvl:3, lvl:0, stat: l => l ? `${l} charge${l>1?'s':''}` : 'Inactif'    },
];
const getUpg  = id => UPGRADES.find(u => u.id === id);
const upgCost = u  => u.lvl >= u.maxLvl ? Infinity : Math.floor(u.baseCost * Math.pow(u.costMult, u.lvl));

// ═══════════════════════════════════════
//  ZONES D'AMBIANCE
// ═══════════════════════════════════════
const ZONES = [
  { name:'Plaines', minH:0,    sky0:'#87CEEB', sky1:'#C8EFA0', g0:'#7EC850', g1:'#5CA832', m0:'rgba(160,195,220,.35)', m1:'rgba(120,185,130,.45)', trees:true,  flowers:true,  stars:false, moon:false },
  { name:'Forêt',   minH:1000, sky0:'#3A7BD5', sky1:'#6BA868', g0:'#4A9040', g1:'#2E6820', m0:'rgba(40,100,70,.5)',    m1:'rgba(30,80,50,.55)',    trees:true,  flowers:false, stars:false, moon:false },
  { name:'Nuages',  minH:2500, sky0:'#1A6EC0', sky1:'#4AAAE0', g0:'#60A8E0', g1:'#3A88C8', m0:'rgba(60,120,200,.28)', m1:'rgba(100,170,230,.35)', trees:false, flowers:false, stars:true,  moon:false },
  { name:'Espace',  minH:4500, sky0:'#060B1E', sky1:'#111E44', g0:'#1A2E70', g1:'#0B1A48', m0:'rgba(20,40,120,.5)',   m1:'rgba(10,25,80,.6)',     trees:false, flowers:false, stars:true,  moon:true  },
];
const getZoneIdx = h => { for (let i = ZONES.length-1; i >= 0; i--) if (h >= ZONES[i].minH) return i; return 0; };

// ═══════════════════════════════════════
//  COULEURS PLATEFORMES
// ═══════════════════════════════════════
const PALETTES = [
  { top:'#6EE7B7', front:'#34D399', side:'#059669', shine:'#A7F3D0' },
  { top:'#FDE68A', front:'#FBBF24', side:'#D97706', shine:'#FEF3C7' },
  { top:'#C4B5FD', front:'#A78BFA', side:'#7C3AED', shine:'#EDE9FE' },
  { top:'#FCA5A5', front:'#F87171', side:'#DC2626', shine:'#FEE2E2' },
  { top:'#93C5FD', front:'#60A5FA', side:'#2563EB', shine:'#DBEAFE' },
  { top:'#F9A8D4', front:'#F472B6', side:'#BE185D', shine:'#FCE7F3' },
  { top:'#FCD34D', front:'#F59E0B', side:'#B45309', shine:'#FEF3C7' },
];

// ═══════════════════════════════════════
//  RAF — un seul actif, token anti-zombie
// ═══════════════════════════════════════
const RAF = (() => {
  let id = null, tok = 0;
  return {
    start(fn) {
      tok++;
      if (id !== null) { cancelAnimationFrame(id); id = null; }
      const myTok = tok;
      const loop  = () => { if (tok !== myTok) return; id = requestAnimationFrame(loop); fn(); };
      id = requestAnimationFrame(loop);
    },
    stop() { tok++; if (id !== null) { cancelAnimationFrame(id); id = null; } }
  };
})();

// ═══════════════════════════════════════
//  SCORES GLOBAUX
// ═══════════════════════════════════════
let globalPts = 0, globalBest = 0;

// ═══════════════════════════════════════
//  NAVIGATION ÉCRANS
// ═══════════════════════════════════════
function showScreen(id) {
  document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
  document.getElementById('screen-' + id).classList.add('active');
}

function openHome() {
  RAF.stop(); Input.reset();
  document.getElementById('home-record').textContent = globalBest + 'm';
  document.getElementById('home-pts').textContent    = Math.round(globalPts).toLocaleString();
  showScreen('home');
  homeAnim();
}

function openShop() {
  RAF.stop(); Input.reset();
  buildShop();
  showScreen('shop');
}

// ═══════════════════════════════════════
//  BOUTIQUE
// ═══════════════════════════════════════
function buildShop() {
  document.getElementById('shop-pts').textContent = Math.round(globalPts).toLocaleString() + ' pts';
  const list = document.getElementById('shop-list');
  list.innerHTML = '';
  [{ id:'move', label:'MOBILITÉ & SAUT' }, { id:'surv', label:'SURVIE & DÉFENSE' }].forEach(cat => {
    const sec = document.createElement('div'); sec.className = 'shop-cat'; sec.textContent = cat.label; list.appendChild(sec);
    UPGRADES.filter(u => u.cat === cat.id).forEach(u => {
      const cost = upgCost(u), maxed = u.lvl >= u.maxLvl, can = !maxed && globalPts >= cost;
      const pct  = Math.round(u.lvl / u.maxLvl * 100);
      const d    = document.createElement('div'); d.className = 'upg-card';
      d.innerHTML = `
        <div class="upg-icon" style="background:${u.color}">${u.icon}</div>
        <div class="upg-info">
          <div class="upg-name">${u.name} <span style="font-size:11px;color:var(--color-text-secondary);font-weight:400">niv.${u.lvl}/${u.maxLvl}</span></div>
          <div class="upg-desc">${u.desc}</div>
          <div class="upg-stat">${u.stat(u.lvl)}</div>
          <div class="upg-bar-wrap"><div class="upg-bar-fill" style="width:${pct}%;background:${u.bar}"></div></div>
        </div>
        <button class="btn-buy ${can?'':maxed?'maxed':'locked'}" onclick="buyUpg('${u.id}')">
          ${maxed ? '✓ Max' : cost.toLocaleString() + ' pts'}
        </button>`;
      list.appendChild(d);
    });
  });
}

function buyUpg(id) {
  const u = getUpg(id), cost = upgCost(u);
  if (globalPts < cost || u.lvl >= u.maxLvl) return;
  globalPts -= cost; u.lvl++; buildShop();
}

// ═══════════════════════════════════════
//  INPUT
// ═══════════════════════════════════════
const Input = (() => {
  let L = false, R = false;
  document.addEventListener('keydown', e => { if (e.key==='ArrowLeft'||e.key==='a'||e.key==='A') L=true;  if (e.key==='ArrowRight'||e.key==='d'||e.key==='D') R=true;  });
  document.addEventListener('keyup',   e => { if (e.key==='ArrowLeft'||e.key==='a'||e.key==='A') L=false; if (e.key==='ArrowRight'||e.key==='d'||e.key==='D') R=false; });
  function wire(btn, isL) {
    const set = v => { isL ? L=v : R=v; v ? btn.classList.add('held') : btn.classList.remove('held'); };
    btn.addEventListener('touchstart', e => { e.preventDefault(); set(true);  }, {passive:false});
    btn.addEventListener('touchend',   e => { e.preventDefault(); set(false); }, {passive:false});
    btn.addEventListener('mousedown',  () => set(true));
    btn.addEventListener('mouseup',    () => set(false));
    btn.addEventListener('mouseleave', () => set(false));
  }
  return {
    get left()  { return L; },
    get right() { return R; },
    reset() { L = false; R = false; },
    setupButtons() {
      ['btn-left','btn-right'].forEach((bid, i) => {
        const old = document.getElementById(bid), nb = old.cloneNode(true);
        old.parentNode.replaceChild(nb, old);
        wire(nb, i === 0);
      });
    }
  };
})();

// ═══════════════════════════════════════
//  PARTICULES
// ═══════════════════════════════════════
const Particles = (() => {
  let list = [];
  function add(x,y,vx,vy,color,r,shape='c') { list.push({x,y,vx,vy,color,r,shape,life:1}); }

  function star5(ctx,x,y,r) {
    ctx.beginPath();
    for (let i=0;i<5;i++) {
      const a=i*Math.PI*2/5-Math.PI/2, a2=a+Math.PI/5;
      i===0 ? ctx.moveTo(x+Math.cos(a)*r, y+Math.sin(a)*r) : ctx.lineTo(x+Math.cos(a)*r, y+Math.sin(a)*r);
      ctx.lineTo(x+Math.cos(a2)*r*.42, y+Math.sin(a2)*r*.42);
    }
    ctx.closePath(); ctx.fill();
  }

  return {
    clear() { list = []; },
    burst(x,y,ci) {
      const c = PALETTES[ci%PALETTES.length];
      for (let i=0;i<12;i++) { const a=Math.random()*Math.PI*2,s=1.5+Math.random()*4.5,big=i<3; add(x,y,Math.cos(a)*s,Math.sin(a)*s-2.5,big?c.shine:c.front,big?5:2+Math.random()*2.5); }
    },
    trail(x,y)     { add(x,y+15,(Math.random()-.5)*1.2,1.5+Math.random()*1.5,`hsl(${255+Math.random()*40},75%,72%)`,2.5+Math.random()*2); },
    stars(x,y,n=5) { for(let i=0;i<n;i++) add(x+(Math.random()-.5)*28,y,(Math.random()-.5)*3,-2-Math.random()*3,'#FFD700',4,'s'); },
    dust(x,y)       { for(let i=0;i<5;i++) add(x+(Math.random()-.5)*20,y,(Math.random()-.5)*2.5,-1-Math.random()*1.5,'rgba(210,185,150,.75)',2.5+Math.random()*2.5); },
    hit(x,y)        { for(let i=0;i<8;i++){const a=Math.random()*Math.PI*2;add(x,y,Math.cos(a)*5,Math.sin(a)*5-2,'#FF4444',4,'s');} },
    shieldBurst(x,y){ for(let i=0;i<8;i++){const a=i*Math.PI/4;add(x,y,Math.cos(a)*5,Math.sin(a)*5-2,'#FFD700',4,'s');} },
    tick(ctx) {
      list = list.filter(p => p.life > 0);
      list.forEach(p => { p.x+=p.vx; p.y+=p.vy; p.vy+=.13; p.life-=.038; ctx.save(); ctx.globalAlpha=Math.max(0,p.life); ctx.fillStyle=p.color; p.shape==='s'?star5(ctx,p.x,p.y,p.r):(ctx.beginPath(),ctx.arc(p.x,p.y,p.r,0,Math.PI*2),ctx.fill()); ctx.restore(); });
      ctx.globalAlpha=1;
    }
  };
})();

// ═══════════════════════════════════════
//  NOTIFICATIONS
// ═══════════════════════════════════════
const Notifs = (() => {
  let list = [];
  return {
    clear() { list = []; },
    add(text,color,icon='',x=CW/2,y=75,big=false) {
      if (list.some(n=>n.text===text&&n.life>.65)) return;
      list.push({text,color:color||'white',icon,x,y,life:1,vy:-.8,big,toast:false});
    },
    toast(x,y,pts,combo) {
      const text=combo>=3?`+${pts} 🔥`:`+${pts}`, color=combo>=5?'#FFD700':combo>=3?'#FFA500':'rgba(255,255,255,.9)';
      list.push({text,color,x,y,life:1,vy:-1.6,toast:true});
    },
    tick(ctx) {
      list = list.filter(n=>n.life>0);
      list.forEach(n => {
        n.y+=n.vy; n.life-=n.toast?.028:.016;
        const a=Math.min(1,n.life*4)*n.life;
        ctx.save(); ctx.globalAlpha=a;
        if (n.toast) {
          ctx.font='bold 12px Fredoka One,cursive'; ctx.textAlign='center'; ctx.fillStyle=n.color; ctx.fillText(n.text,n.x,n.y);
        } else {
          const lb=(n.icon?n.icon+' ':'')+n.text, fs=n.big?15:12;
          ctx.font=`bold ${fs}px Fredoka One,cursive`;
          const tw=ctx.measureText(lb).width;
          ctx.fillStyle='rgba(0,0,0,.55)'; ctx.beginPath(); ctx.roundRect(n.x-tw/2-10,n.y-fs,tw+20,fs+10,8); ctx.fill();
          ctx.fillStyle=n.color; ctx.textAlign='center'; ctx.fillText(lb,n.x,n.y);
        }
        ctx.restore();
      });
      ctx.textAlign='left'; ctx.globalAlpha=1;
    }
  };
})();

// ═══════════════════════════════════════
//  PLATEFORMES
// ═══════════════════════════════════════
const Platforms = (() => {
  let list = [];

  function pltW(diff) {
    const ex = getUpg('magnet').lvl * 12;
    return Math.max(55, 92 - diff*4) + ex + Math.random()*26;
  }
  function make(y, w, forced) {
    const x = forced ? CW/2-w/2 : 10+Math.random()*(CW-w-20);
    return { x, y, w, ci:Math.floor(Math.random()*PALETTES.length), bounced:false, flash:0, destroyed:false };
  }

  return {
    get list() { return list; },

    init() {
      list = [];
      list.push(make(CH-60, 150, true));           // plateforme de départ large
      for (let i=1;i<10;i++) list.push(make(CH-60-i*55, pltW(0), false));
    },

    surfaceY(p) { return p.y - BEVEL; },

    shiftAll(dy) { list.forEach(p => p.y += dy); },

    tickFlash() { list.forEach(p => { if (p.flash>0) p.flash-=.07; }); },

    recycle(camY, diff) {
      // Calcule topY une fois, en excluant les plateformes déjà en dehors
      let topY = Infinity;
      list.forEach(p => { if (!p.destroyed && p.y < topY) topY = p.y; });
      if (!isFinite(topY)) topY = camY;

      list.forEach(p => {
        if (p.y - camY > CH+60 || p.destroyed) {
          // Placer au-dessus de topY avec gap aléatoire borné
          const gap = GAP_MIN + Math.random()*(GAP_MAX-GAP_MIN) + diff;
          p.y       = topY - gap;
          p.w       = pltW(diff);
          p.x       = 10 + Math.random()*(CW-p.w-20);
          p.ci      = Math.floor(Math.random()*PALETTES.length);
          p.bounced = false;
          p.flash   = 0;
          p.destroyed = false;
          topY = p.y; // mise à jour pour les prochaines recyclées ce frame
        }
      });
    },

    draw(ctx, camY) {
      list.forEach(p => {
        if (p.destroyed) return;
        const sy = p.y - camY;
        if (sy < -30 || sy > CH+30) return;
        drawPlt(ctx, p, sy);
      });
    }
  };

  function drawPlt(ctx, p, sy) {
    const c = PALETTES[p.ci], {x,w} = p;
    // Ombre
    ctx.fillStyle='rgba(0,0,0,.10)'; ctx.beginPath(); ctx.ellipse(x+w/2,sy+FRONT+5,w*.44,4,0,0,Math.PI*2); ctx.fill();
    // Face avant
    ctx.fillStyle=c.front; ctx.beginPath(); ctx.roundRect(x,sy,w,FRONT,[0,0,4,4]); ctx.fill();
    // Dessus biseauté
    ctx.fillStyle=c.top; ctx.beginPath(); ctx.moveTo(x,sy); ctx.lineTo(x+BEVEL,sy-BEVEL); ctx.lineTo(x+w+BEVEL,sy-BEVEL); ctx.lineTo(x+w,sy); ctx.closePath(); ctx.fill();
    // Côté droit
    ctx.fillStyle=c.side; ctx.beginPath(); ctx.moveTo(x+w,sy); ctx.lineTo(x+w+BEVEL,sy-BEVEL); ctx.lineTo(x+w+BEVEL,sy-BEVEL+FRONT); ctx.lineTo(x+w,sy+FRONT); ctx.closePath(); ctx.fill();
    // Brillance
    ctx.fillStyle=c.shine; ctx.beginPath(); ctx.roundRect(x+8,sy-BEVEL+1,Math.min(44,w-18),3,1); ctx.fill();
    // Mousse sur vertes/roses
    if (p.ci===0||p.ci===5) { ctx.fillStyle='rgba(80,200,80,.44)'; for(let i=0;i<4;i++){const gx=x+12+i*(w-24)/3;ctx.beginPath();ctx.arc(gx,sy-BEVEL,3.5,Math.PI,0);ctx.fill();} }
    // Flash rebond
    if (p.flash>0) { ctx.fillStyle=`rgba(255,255,255,${p.flash*.44})`; ctx.beginPath(); ctx.roundRect(x,sy-BEVEL,w+BEVEL,FRONT+BEVEL,3); ctx.fill(); }
  }
})();

// ═══════════════════════════════════════
//  FOND
// ═══════════════════════════════════════
function drawBg(ctx, totalH, T) {
  const zi=getZoneIdx(totalH), z=ZONES[zi];
  const sky=ctx.createLinearGradient(0,0,0,CH); sky.addColorStop(0,z.sky0); sky.addColorStop(1,z.sky1);
  ctx.fillStyle=sky; ctx.fillRect(0,0,CW,CH);

  if (z.stars) {
    const ba=zi===3?1:.6;
    for(let i=0;i<45;i++){const sx=(i*137.5)%CW,sy=(i*79.3)%(CH*.55),p=(.4+.6*Math.sin(T*.04+i*1.3))*ba;ctx.fillStyle=`rgba(255,255,210,${p})`;ctx.beginPath();ctx.arc(sx,sy,i%7?1:2,0,Math.PI*2);ctx.fill();}
  }

  if (z.moon) {
    ctx.fillStyle='rgba(220,230,255,.95)'; ctx.beginPath(); ctx.arc(55,45,20,0,Math.PI*2); ctx.fill();
    ctx.fillStyle='rgba(180,200,240,.55)'; ctx.beginPath(); ctx.arc(55,45,30,0,Math.PI*2); ctx.fill();
    [[50,42,3],[63,50,2],[47,54,1.5]].forEach(([x,y,r])=>{ctx.fillStyle='rgba(185,200,238,.55)';ctx.beginPath();ctx.arc(x,y,r,0,Math.PI*2);ctx.fill();});
    ctx.fillStyle='rgba(255,140,80,.7)'; ctx.beginPath(); ctx.arc(320,60,18,0,Math.PI*2); ctx.fill();
    ctx.fillStyle='rgba(200,100,50,.4)'; ctx.beginPath(); ctx.ellipse(320,60,28,8,-.3,0,Math.PI*2); ctx.fill();
  } else {
    ctx.fillStyle='rgba(255,235,80,.95)'; ctx.beginPath(); ctx.arc(52,48,24,0,Math.PI*2); ctx.fill();
    ctx.fillStyle='rgba(255,255,160,.4)';  ctx.beginPath(); ctx.arc(52,48,36,0,Math.PI*2); ctx.fill();
    for(let i=0;i<8;i++){const a=i*Math.PI/4+T*.008;ctx.strokeStyle='rgba(255,230,60,.28)';ctx.lineWidth=3;ctx.beginPath();ctx.moveTo(52+Math.cos(a)*26,48+Math.sin(a)*26);ctx.lineTo(52+Math.cos(a)*40,48+Math.sin(a)*40);ctx.stroke();}
  }

  if (zi<3) {
    const oF=totalH*.022,oM=totalH*.05,oN=totalH*.095;
    ctx.fillStyle='rgba(255,255,255,.35)';
    [[290,35,12],[40,25,10],[170,48,11],[355,18,9]].forEach(([x,y,r])=>{const cx=((x-oF)%CW+CW*2)%CW;ctx.beginPath();ctx.ellipse(cx,y,r*1.8,r*.65,0,0,Math.PI*2);ctx.fill();});
    ctx.fillStyle='rgba(255,255,255,.6)';
    [[95,62,18],[255,52,16],[370,72,13],[18,78,12]].forEach(([x,y,r])=>{const cx=((x-oM)%CW+CW*2)%CW;ctx.beginPath();ctx.ellipse(cx,y,r*1.7,r*.72,0,0,Math.PI*2);ctx.fill();ctx.beginPath();ctx.ellipse(cx-r*.7,y+r*.35,r*.95,r*.62,0,0,Math.PI*2);ctx.fill();ctx.beginPath();ctx.ellipse(cx+r*.7,y+r*.28,r*.88,r*.58,0,0,Math.PI*2);ctx.fill();});
    if (zi<2) { ctx.fillStyle='rgba(255,255,255,.88)';[[165,40,25],[335,30,19]].forEach(([x,y,r])=>{const cx=((x-oN)%CW+CW*2)%CW;ctx.beginPath();ctx.ellipse(cx,y,r*1.9,r*.82,0,0,Math.PI*2);ctx.fill();ctx.beginPath();ctx.ellipse(cx-r*.85,y+r*.42,r*1.1,r*.75,0,0,Math.PI*2);ctx.fill();ctx.beginPath();ctx.ellipse(cx+r*.85,y+r*.32,r,r*.68,0,0,Math.PI*2);ctx.fill();}); }
  }

  const moff=totalH*.011;
  ctx.fillStyle=z.m0; ctx.beginPath(); ctx.moveTo(0,CH); for(let x=0;x<=CW;x+=6)ctx.lineTo(x,CH*.52+Math.sin((x+moff)*.008)*65+Math.sin((x+moff)*.016)*28); ctx.lineTo(CW,CH); ctx.closePath(); ctx.fill();
  ctx.fillStyle=z.m1; ctx.beginPath(); ctx.moveTo(0,CH); for(let x=0;x<=CW;x+=5)ctx.lineTo(x,CH*.67+Math.sin((x+moff*1.4)*.013)*38+Math.sin((x+moff*.7)*.022)*15); ctx.lineTo(CW,CH); ctx.closePath(); ctx.fill();

  if (z.trees) {
    const tf=totalH*.065;
    [[30,CH-50,18,1],[80,CH-60,21,0],[185,CH-46,17,1],[275,CH-64,22,0],[345,CH-52,18,1],[125,CH-57,20,0]].forEach(([tx,ty,tr,v],i)=>{
      const ttx=((tx-tf*(.4+i*.05))%CW+CW*2)%CW;
      ctx.fillStyle='#5A3A1A'; ctx.fillRect(ttx-4,ty+tr,8,22);
      const lc=v?['#3A8C2A','#4AAF38','#5EC040']:['#2D7A20','#3A9E30','#4BBF40'];
      [[ttx,ty,tr],[ttx-5,ty-6,tr*.55],[ttx+6,ty-5,tr*.5]].forEach(([ax,ay,ar],j)=>{ctx.fillStyle=lc[j];ctx.beginPath();ctx.arc(ax,ay,ar,0,Math.PI*2);ctx.fill();});
    });
  }

  const ho=totalH*.085;
  ctx.fillStyle=z.g0; ctx.beginPath(); ctx.moveTo(0,CH); for(let x=0;x<=CW;x+=5)ctx.lineTo(x,CH-45+Math.sin((x+ho)*.016)*22+Math.sin((x+ho*.6)*.01)*10); ctx.lineTo(CW,CH); ctx.closePath(); ctx.fill();
  ctx.fillStyle=z.g1; ctx.fillRect(0,CH-14,CW,14);

  if (z.flowers) {
    const FC=['#FF7BAC','#FFD93D','#FF9EE0','#A0E0FF','#FFB347','#C8F56A'];
    for(let i=0;i<24;i++){const gx=((i*17+ho*.28)%(CW-6)+3);ctx.fillStyle='#3A9022';ctx.fillRect(gx,CH-23,2,10);ctx.fillStyle=FC[i%FC.length];ctx.beginPath();ctx.arc(gx+1,CH-24,3.8,0,Math.PI*2);ctx.fill();}
  }

  if (zi>0) { ctx.fillStyle='rgba(255,255,255,.72)'; ctx.font='bold 11px Nunito,sans-serif'; ctx.textAlign='right'; ctx.fillText(z.name,CW-10,22); ctx.textAlign='left'; }
}

// ═══════════════════════════════════════
//  PERSONNAGE
// ═══════════════════════════════════════
function drawArm(ctx, side, angle) {
  ctx.save(); ctx.translate(side*12,-10); ctx.rotate(angle);
  ctx.fillStyle='#7C3AED'; ctx.beginPath(); ctx.roundRect(-4,0,8,15,4); ctx.fill();
  ctx.fillStyle='#FBBF9E'; ctx.beginPath(); ctx.arc(0,17,5.5,0,Math.PI*2); ctx.fill();
  ctx.restore();
}

function drawChar(ctx, x, y, vy, lH, rH, jLvl, T, combo, shCh, invT) {
  ctx.save(); ctx.translate(x,y);
  if (invT>0 && Math.floor(invT/6)%2===1) ctx.globalAlpha=.32;

  let sy=1,sx=1;
  if (vy<-6){const s=Math.min(.38,Math.abs(vy)/28);sy=1+s;sx=1-s*.45;}
  else if (vy>5){const s=Math.min(.26,vy/22);sy=1-s;sx=1+s*.45;}
  ctx.rotate((lH?-1:rH?1:0)*.11);

  // Ombre
  ctx.fillStyle='rgba(0,0,0,.12)'; ctx.beginPath(); ctx.ellipse(0,22,13*sx,4,0,0,Math.PI*2); ctx.fill();

  // Bouclier
  if (shCh>0) {
    const sa=.28+.15*Math.sin(T*.08);
    ctx.fillStyle=`rgba(255,220,50,${sa})`; ctx.beginPath(); ctx.arc(0,-20*sy,28,0,Math.PI*2); ctx.fill();
    ctx.strokeStyle=`rgba(255,200,0,${sa+.32})`; ctx.lineWidth=2; ctx.beginPath(); ctx.arc(0,-20*sy,28,0,Math.PI*2); ctx.stroke();
  }

  // Ailes
  if (jLvl>0) {
    const ww=15+jLvl*5,wf=Math.sin(T*.2)*13,wa=Math.min(.88,.5+jLvl*.1);
    ctx.fillStyle=`rgba(180,140,255,${wa})`;
    ctx.beginPath(); ctx.ellipse(-17,-16*sy+wf,ww,8,-.5,0,Math.PI*2); ctx.fill();
    ctx.beginPath(); ctx.ellipse( 17,-16*sy+wf,ww,8, .5,0,Math.PI*2); ctx.fill();
    ctx.fillStyle=`rgba(220,200,255,${wa+.12})`;
    ctx.beginPath(); ctx.ellipse(-17,-19*sy+wf,ww*.5,4.5,-.5,0,Math.PI*2); ctx.fill();
    ctx.beginPath(); ctx.ellipse( 17,-19*sy+wf,ww*.5,4.5, .5,0,Math.PI*2); ctx.fill();
  }

  ctx.save(); ctx.scale(sx,sy);

  // Jambes + chaussures
  ctx.fillStyle='#E85D20'; ctx.beginPath(); ctx.roundRect(-9,2,8,13,3); ctx.fill(); ctx.beginPath(); ctx.roundRect(1,2,8,13,3); ctx.fill();
  ctx.fillStyle='#C03000'; ctx.beginPath(); ctx.roundRect(-10,13,10,5,[2,2,3,3]); ctx.fill(); ctx.beginPath(); ctx.roundRect(0,13,10,5,[2,2,3,3]); ctx.fill();

  // Corps
  const bg=ctx.createLinearGradient(-12,-20,12,4); bg.addColorStop(0,'#A78BFA'); bg.addColorStop(.5,'#7C3AED'); bg.addColorStop(1,'#5B21B6');
  ctx.fillStyle=bg; ctx.beginPath(); ctx.roundRect(-12,-20,24,24,[6,6,4,4]); ctx.fill();
  ctx.fillStyle='rgba(255,255,255,.2)'; ctx.beginPath(); ctx.roundRect(-8,-17,7,5,3); ctx.fill(); ctx.beginPath(); ctx.roundRect(1,-17,7,5,3); ctx.fill();
  ctx.fillStyle='rgba(0,0,0,.18)'; ctx.beginPath(); ctx.roundRect(-12,-1,24,5,[0,0,4,4]); ctx.fill();

  // Bras
  let aL,aR;
  if (lH){aL=-1.3;aR=.5;} else if (rH){aL=.5;aR=-1.3;} else if (vy<-5){aL=aR=-2;} else if (vy>5){aL=aR=.95;} else {const sw=Math.sin(T*.13)*.55;aL=sw;aR=-sw;}
  drawArm(ctx,-1,aL); drawArm(ctx,1,aR);

  // Tête
  ctx.fillStyle='#FBBF9E'; ctx.beginPath(); ctx.arc(0,-32,14,0,Math.PI*2); ctx.fill();
  ctx.fillStyle='rgba(255,235,210,.32)'; ctx.beginPath(); ctx.arc(-4,-37,7,0,Math.PI*2); ctx.fill();

  // Cheveux
  ctx.fillStyle='#6B3A1F'; ctx.beginPath(); ctx.ellipse(0,-44,11,6,0,0,Math.PI*2); ctx.fill(); ctx.beginPath(); ctx.arc(-9,-40,5.5,-.6,Math.PI+.6); ctx.fill(); ctx.beginPath(); ctx.arc(9,-40,5.5,-.6,Math.PI+.6); ctx.fill();
  const mw=Math.sin(T*.12)*2; ctx.beginPath(); ctx.ellipse(6,-48+mw,4,6,.25,0,Math.PI*2); ctx.fill();
  ctx.fillStyle='#8B4F2A'; ctx.beginPath(); ctx.ellipse(-2,-47,2.5,4,-.1,0,Math.PI*2); ctx.fill();

  // Yeux
  const eh=vy<-5?1.4:vy>6?.6:1;
  ctx.fillStyle='#1A1230'; ctx.beginPath(); ctx.ellipse(-4.8,-33,3.2,3.2*eh,0,0,Math.PI*2); ctx.fill(); ctx.beginPath(); ctx.ellipse(4.8,-33,3.2,3.2*eh,0,0,Math.PI*2); ctx.fill();
  ctx.fillStyle='white'; ctx.beginPath(); ctx.arc(-3.5,-34.5,1.3,0,Math.PI*2); ctx.fill(); ctx.beginPath(); ctx.arc(6.1,-34.5,1.3,0,Math.PI*2); ctx.fill();

  // Sourcils
  ctx.strokeStyle='#5C3A1E'; ctx.lineWidth=2.2; ctx.lineCap='round';
  if (vy<-3){ctx.beginPath();ctx.moveTo(-8,-38);ctx.lineTo(-2,-40);ctx.stroke();ctx.beginPath();ctx.moveTo(8,-38);ctx.lineTo(2,-40);ctx.stroke();}
  else if(vy>5){ctx.beginPath();ctx.moveTo(-8,-37);ctx.lineTo(-2,-36);ctx.stroke();ctx.beginPath();ctx.moveTo(8,-37);ctx.lineTo(2,-36);ctx.stroke();}
  else{ctx.beginPath();ctx.moveTo(-8,-37);ctx.lineTo(-2,-37);ctx.stroke();ctx.beginPath();ctx.moveTo(8,-37);ctx.lineTo(2,-37);ctx.stroke();}

  // Joues
  ctx.fillStyle='rgba(255,140,150,.48)'; ctx.beginPath(); ctx.ellipse(-7,-29,4,2.5,0,0,Math.PI*2); ctx.fill(); ctx.beginPath(); ctx.ellipse(7,-29,4,2.5,0,0,Math.PI*2); ctx.fill();

  // Bouche
  if (vy<-5){ctx.fillStyle='#BF4060';ctx.beginPath();ctx.ellipse(0,-26,5,4.5,0,0,Math.PI*2);ctx.fill();ctx.fillStyle='white';ctx.beginPath();ctx.ellipse(0,-26,3,2.5,0,0,Math.PI*2);ctx.fill();}
  else if(vy>5){ctx.strokeStyle='#BF4060';ctx.lineWidth=2;ctx.beginPath();ctx.arc(0,-26,4,-.2,Math.PI+.2,true);ctx.stroke();}
  else{ctx.strokeStyle='#BF4060';ctx.lineWidth=2;ctx.beginPath();ctx.arc(0,-26,4,.15,Math.PI-.15);ctx.stroke();}

  // Combo badge
  if (combo>=3){ctx.fillStyle='rgba(255,200,0,.92)';ctx.beginPath();ctx.roundRect(-20,-56,40,15,7);ctx.fill();ctx.fillStyle='#5A2A00';ctx.font='bold 9px Fredoka One,cursive';ctx.textAlign='center';ctx.fillText(`x${combo}`,0,-45);ctx.textAlign='left';}

  ctx.restore(); ctx.globalAlpha=1; ctx.restore();
}

// ═══════════════════════════════════════
//  HUD IN-GAME
// ═══════════════════════════════════════
function refreshHUD() {
  document.getElementById('hud-pts').textContent  = Math.round(gamePts).toLocaleString();
  document.getElementById('hud-h').textContent    = gameH + 'm';
  document.getElementById('hud-rec').textContent  = globalBest + 'm';
  let lv=''; for(let i=0;i<lives;i++)lv+='❤️'; for(let i=lives;i<maxLives;i++)lv+='🖤';
  document.getElementById('hud-lives').textContent = lv;
}

function drawHudCanvas(ctx) {
  ctx.fillStyle='rgba(0,0,0,.42)'; ctx.beginPath(); ctx.roundRect(8,8,88,24,6); ctx.fill();
  ctx.fillStyle='white'; ctx.font='bold 13px Fredoka One,cursive'; ctx.fillText('↑ '+gameH+'m',16,25);
  if (shieldCh>0) {
    ctx.fillStyle='rgba(255,200,0,.88)'; ctx.beginPath(); ctx.roundRect(CW-70,8,62,24,6); ctx.fill();
    ctx.fillStyle='#4A2A00'; ctx.font='bold 12px Fredoka One,cursive'; ctx.textAlign='right'; ctx.fillText('🛡️'.repeat(shieldCh),CW-10,25); ctx.textAlign='left';
  }
  if (combo>=2) {
    const cy2=shieldCh>0?36:8;
    ctx.fillStyle='rgba(255,165,0,.92)'; ctx.beginPath(); ctx.roundRect(CW-88,cy2,80,24,6); ctx.fill();
    ctx.fillStyle='#3A1500'; ctx.font='bold 12px Fredoka One,cursive'; ctx.textAlign='right'; ctx.fillText('🔥 x'+combo,CW-10,cy2+17); ctx.textAlign='left';
  }
}

// ═══════════════════════════════════════
//  ÉTAT DU JEU
// ═══════════════════════════════════════
let cx,cy,vx,vy, camY,totalH, gamePts,gameH, lives,maxLives, shieldCh, combo,bestCombo,comboTimer, invincT,respawnT,isDead, frameT, lastZone,lastBand;

const jumpPow = () => 14 + getUpg('jump').lvl * 2;
const maxVel  = () => 4.5 + getUpg('speed').lvl * .9;
const accl    = () => .58  + getUpg('speed').lvl * .1;
const startY  = () => CH - 60 - FEET - 2;

function initState() {
  cx=CW/2; cy=startY(); vx=0; vy=-jumpPow();
  camY=0; totalH=0; gamePts=0; gameH=0;
  maxLives=1+getUpg('life').lvl; lives=maxLives;
  shieldCh=getUpg('shield').lvl;
  combo=0; bestCombo=0; comboTimer=0;
  invincT=INVINC; respawnT=0; isDead=false; frameT=0;
  lastZone=0; lastBand=Math.floor(globalBest/500)*500;
  Platforms.init(); Particles.clear(); Notifs.clear();
}

function doRespawn() {
  cx=CW/2; cy=startY(); vx=0; vy=-jumpPow();
  camY=0; totalH=0; combo=0; comboTimer=0;
  invincT=INVINC; respawnT=0; isDead=false; lastZone=0;
  Platforms.init(); Particles.clear();
}

// ═══════════════════════════════════════
//  GAME OVER
// ═══════════════════════════════════════
function showGameOver() {
  RAF.stop(); Input.reset();
  globalPts += gamePts;
  if (gameH > globalBest) globalBest = gameH;
  const title = gameH>=globalBest&&gameH>0 ? 'Nouveau record ! 🏆' : bestCombo>=5 ? 'Super combo ! 🔥' : 'Partie terminée !';
  document.getElementById('go-title').textContent = title;
  document.getElementById('go-h').textContent     = gameH+'m';
  document.getElementById('go-pts').textContent   = '+'+Math.round(gamePts).toLocaleString();
  document.getElementById('go-combo').textContent = 'x'+bestCombo;
  document.getElementById('go-total').textContent = Math.round(globalPts).toLocaleString();
  document.getElementById('go-sub').textContent   = 'Tu as gagné '+Math.round(gamePts).toLocaleString()+' points !';
  const el=document.getElementById('go-lives'); el.innerHTML='';
  for(let i=0;i<maxLives;i++){const s=document.createElement('span');s.textContent=i<lives?'❤️':'🖤';el.appendChild(s);}
  showScreen('over');
}

// ═══════════════════════════════════════
//  BOUCLE DE JEU
// ═══════════════════════════════════════
function gameStep() {
  const cv=document.getElementById('cv-game'); if(!cv) return;
  const ctx=cv.getContext('2d');
  frameT++;

  // ── Phase mort ──
  if (isDead) {
    respawnT--;
    if (respawnT<=0) doRespawn();
    ctx.clearRect(0,0,CW,CH);
    drawBg(ctx,totalH,frameT);
    Platforms.draw(ctx,camY);
    Particles.tick(ctx);
    Notifs.tick(ctx);
    drawHudCanvas(ctx);
    return;
  }

  // ── Invincibilité ──
  if (invincT>0) invincT--;

  // ── Physique ──
  const mv=maxVel(), ac=accl();
  if      (Input.left)  vx -= ac;
  else if (Input.right) vx += ac;
  else                  vx *= .80;
  vx = Math.max(-mv, Math.min(mv, vx));
  vy += GRAVITY;
  cx += vx; cy += vy;
  if (cx<8)    cx=CW-8;
  if (cx>CW-8) cx=8;
  if (vy<-5 && frameT%2===0) Particles.trail(cx,cy);

  // ── Collision plateformes ──
  // Descente uniquement — test de franchissement de surface
  if (vy>0) {
    const foot=cy+FEET, prevFoot=foot-vy;
    let landed=false;
    for (const p of Platforms.list) {
      if (p.destroyed||landed) continue;
      const surf=p.y-BEVEL;
      if (prevFoot<=surf && foot>=surf && cx+8>p.x && cx-8<p.x+p.w) {
        cy=surf-FEET; vy=0; landed=true; p.flash=1;
        if (!p.bounced) {
          p.bounced=true;
          combo++; if(combo>bestCombo)bestCombo=combo; comboTimer=85;
          const pts=Math.max(1,combo); gamePts+=pts;
          gameH=Math.max(gameH,Math.round(totalH/5));
          if(gameH>globalBest) globalBest=gameH;
          Particles.burst(cx,surf-camY,p.ci);
          Particles.dust(cx,surf-camY);
          if(combo>=3) Particles.stars(cx,surf-camY-10);
          Notifs.toast(cx,surf-camY-14,pts,combo);
          if(Math.round(gamePts)%5===0) refreshHUD();
        }
      }
    }
    if (landed && vy===0) vy=-jumpPow(); // rebond immédiat
  }

  if (comboTimer>0) comboTimer--; else combo=0;
  Platforms.tickFlash();

  // ── Caméra ──
  const scY=cy-camY;
  if (scY < CH*CAM_RATIO) {
    const d=CH*CAM_RATIO-scY;
    camY-=d; totalH+=d;
    Platforms.shiftAll(d);
  }

  // ── Mort par chute ──
  if (!isDead && cy-camY > CH+130) {
    Particles.hit(cx,CH);
    if (shieldCh>0) {
      shieldCh--;
      Particles.shieldBurst(cx,CH);
      Notifs.add('Bouclier !','#FFD700','🛡️',CW/2,120);
      refreshHUD();
      isDead=true; respawnT=RESPAWN;
    } else {
      lives--;
      refreshHUD();
      if (lives<=0) { showGameOver(); return; }
      Notifs.add('Aïe !','#FF6060','💔',CW/2,120);
      isDead=true; respawnT=RESPAWN;
    }
  }

  // ── Recyclage plateformes ──
  Platforms.recycle(camY, Math.min(10,totalH/500));

  // ── Notifications événements ──
  const band=Math.floor(gameH/500)*500;
  if (band>0&&band>lastBand&&gameH>0) {
    lastBand=band;
    if (gameH>=globalBest-20) { Notifs.add('Nouveau record !','#FFD700','🏆',CW/2,70,true); Particles.stars(cx,cy-camY-20); }
  }
  const zi=getZoneIdx(totalH);
  if (zi>lastZone) {
    lastZone=zi;
    const icons=['🌲','☁️','🚀'];
    Notifs.add('Zone '+ZONES[zi].name+' !','white',icons[zi-1]||'⭐',CW/2,75);
  }
  if (combo===5)  Notifs.add('Super combo !','#FFA500','🔥',CW/2,100);
  if (combo===10) Notifs.add('COMBO x10 !', '#FF4500','💥',CW/2,100,true);

  // ── Rendu ──
  ctx.clearRect(0,0,CW,CH);
  drawBg(ctx,totalH,frameT);
  Particles.tick(ctx);
  Platforms.draw(ctx,camY);
  drawChar(ctx,cx,cy-camY,vy,Input.left,Input.right,getUpg('jump').lvl,frameT,combo,shieldCh,invincT);
  Notifs.tick(ctx);
  drawHudCanvas(ctx);
}

// ═══════════════════════════════════════
//  DÉMARRAGE PARTIE
// ═══════════════════════════════════════
function startGame() {
  RAF.stop(); Input.reset();
  initState();
  showScreen('game');
  refreshHUD();
  Input.setupButtons();
  RAF.start(gameStep);
}

// ═══════════════════════════════════════
//  ANIMATION ACCUEIL
// ═══════════════════════════════════════
function homeAnim() {
  const cv=document.getElementById('cv-home'); if(!cv) return;
  const ctx=cv.getContext('2d');
  const H=170, PLT_Y=H-65, SURF=PLT_Y-BEVEL;
  let hcy=SURF-FEET, hvy=-14, T=0, hp=[];
  const demoPlt={x:CW/2-65,y:PLT_Y,w:130,ci:0,bounced:false,flash:0,destroyed:false};

  // Expose drawPlt for home canvas (accède via closure Platforms)
  RAF.start(() => {
    T++; hvy+=GRAVITY; hcy+=hvy;
    if (hvy>0&&hcy+FEET>=SURF) {
      hcy=SURF-FEET; hvy=-14;
      for(let i=0;i<6;i++){const a=Math.random()*Math.PI*2,s=2+Math.random()*3;hp.push({x:CW/2,y:SURF,vx:Math.cos(a)*s,vy:Math.sin(a)*s-2,life:.8,r:3.5});}
    }
    ctx.clearRect(0,0,CW,H);
    const sky=ctx.createLinearGradient(0,0,0,H);sky.addColorStop(0,'#87CEEB');sky.addColorStop(1,'#C8EFA0');
    ctx.fillStyle=sky;ctx.fillRect(0,0,CW,H);
    ctx.fillStyle='rgba(255,235,80,.9)';ctx.beginPath();ctx.arc(50,40,20,0,Math.PI*2);ctx.fill();
    ctx.fillStyle='rgba(255,255,255,.8)';[[110,28,13],[245,20,10],[325,33,12]].forEach(([x,y,r])=>{ctx.beginPath();ctx.ellipse(x,y,r*1.7,r*.7,0,0,Math.PI*2);ctx.fill();});
    ctx.fillStyle='#7EC850';ctx.fillRect(0,H-16,CW,16);
    // Dessine la plateforme démo manuellement
    const c=PALETTES[0],{x,y,w}=demoPlt,sy=PLT_Y;
    ctx.fillStyle=c.front;ctx.beginPath();ctx.roundRect(x,sy,w,FRONT,[0,0,4,4]);ctx.fill();
    ctx.fillStyle=c.top;ctx.beginPath();ctx.moveTo(x,sy);ctx.lineTo(x+BEVEL,sy-BEVEL);ctx.lineTo(x+w+BEVEL,sy-BEVEL);ctx.lineTo(x+w,sy);ctx.closePath();ctx.fill();
    ctx.fillStyle=c.side;ctx.beginPath();ctx.moveTo(x+w,sy);ctx.lineTo(x+w+BEVEL,sy-BEVEL);ctx.lineTo(x+w+BEVEL,sy-BEVEL+FRONT);ctx.lineTo(x+w,sy+FRONT);ctx.closePath();ctx.fill();
    ctx.fillStyle=c.shine;ctx.beginPath();ctx.roundRect(x+8,sy-BEVEL+1,Math.min(44,w-18),3,1);ctx.fill();
    ctx.fillStyle='rgba(80,200,80,.44)';for(let i=0;i<4;i++){const gx=x+12+i*(w-24)/3;ctx.beginPath();ctx.arc(gx,sy-BEVEL,3.5,Math.PI,0);ctx.fill();}
    // Particules
    hp=hp.filter(p=>p.life>0);
    hp.forEach(p=>{p.x+=p.vx;p.y+=p.vy;p.vy+=.15;p.life-=.05;ctx.globalAlpha=p.life;ctx.fillStyle=PALETTES[0].shine;ctx.beginPath();ctx.arc(p.x,p.y,p.r,0,Math.PI*2);ctx.fill();});
    ctx.globalAlpha=1;
    drawChar(ctx,CW/2,hcy,hvy,false,false,0,T,0,0,0);
  });
}

// ── Init ──
openHome();
</script>
