  
<!DOCTYPE html>  
<html lang="en">  
<head>  
<meta charset="UTF-8">  
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no">  
<meta name="apple-mobile-web-app-capable" content="yes">  
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">  
<title>The Elder Scrolls: Map & Timeline</title>  
<style>  
:root{--bg:#0c0f14;--panel:#151a22;--light:#1e2530;--gold:#d4af37;--dim:#9c7f24;--text:#e8e6e1;--muted:#9aa0a6;--border:#2c3545}  
*{box-sizing:border-box;margin:0;padding:0}  
body{font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,Georgia,serif;background:var(--bg);color:var(--text);line-height:1.5;padding-bottom:40px}  
header{text-align:center;padding:18px 14px 12px;border-bottom:1px solid var(--border);background:linear-gradient(180deg,#161b24 0%,#0c0f14 100%)}  
header h1{font-size:1.4rem;letter-spacing:2px;color:var(--gold);text-transform:uppercase}  
header p{font-size:.82rem;color:var(--muted);margin-top:3px}  
.tabs{display:flex;justify-content:center;gap:8px;padding:10px;background:var(--panel);border-bottom:1px solid var(--border);position:sticky;top:0;z-index:20}  
.tab-btn{background:var(--light);color:var(--text);border:1px solid var(--border);padding:8px 14px;border-radius:6px;font-size:.85rem;font-weight:600;cursor:pointer}  
.tab-btn.active{background:var(--gold);color:#0c0f14;border-color:var(--gold)}  
.section{display:none;padding:14px;max-width:960px;margin:0 auto}  
.section.active{display:block}  
.hint{text-align:center;font-size:.82rem;color:var(--muted);margin-bottom:10px}  
.map-box{position:relative;width:100%;height:420px;background:radial-gradient(circle at center,#142233 0%,#09101a 100%);border:1px solid var(--dim);border-radius:10px;overflow:hidden;touch-action:none}  
.zoom-ui{position:absolute;top:10px;right:10px;display:flex;flex-direction:column;gap:6px;z-index:10}  
.z-btn{width:34px;height:34px;background:rgba(21,26,34,.92);color:var(--gold);border:1px solid var(--dim);border-radius:6px;font-size:1.1rem;font-weight:700;cursor:pointer}  
svg#map{width:100%;height:100%;cursor:grab}  
.prov{stroke:#1b222c;stroke-width:1.4;cursor:pointer;transition:filter .2s}  
.prov:hover{filter:brightness(1.22);stroke:var(--gold);stroke-width:2}  
.lbl{font-size:9px;font-weight:700;fill:#fff;text-anchor:middle;letter-spacing:.7px;text-shadow:0 1px 3px #000;pointer-events:none}  
.city{font-size:6.5px;fill:#f5e6b3;text-anchor:middle;text-shadow:0 1px 2px #000;pointer-events:none}  
.realm-bar{display:flex;flex-wrap:wrap;gap:6px;justify-content:center;margin-top:12px}  
.realm-btn{background:var(--panel);color:var(--gold);border:1px solid var(--border);padding:6px 10px;border-radius:5px;font-size:.78rem;cursor:pointer}  
.realm-btn:hover{border-color:var(--gold)}  
.card{margin-top:14px;background:var(--panel);border:1px solid var(--dim);border-radius:8px;padding:15px}  
.card h2{color:var(--gold);font-size:1.15rem;margin-bottom:4px}  
.meta{font-size:.8rem;color:var(--muted);margin-bottom:8px}  
.card p#l-desc{font-size:.9rem;color:var(--text)}  
.item{background:var(--panel);border-left:3px solid var(--gold);padding:12px 14px;margin-bottom:10px;border-radius:0 6px 6px 0}  
.badge{display:inline-block;background:var(--light);color:var(--gold);font-size:.72rem;font-weight:700;padding:2px 7px;border-radius:4px;margin-bottom:4px}  
.item h3{font-size:1rem;color:#fff}  
.item p{font-size:.86rem;color:#cfd3da;margin-top:4px}  
.tip{margin-top:18px;padding:12px;background:var(--light);border:1px dashed var(--dim);border-radius:8px;font-size:.8rem;color:var(--muted);text-align:center}  
</style>  
</head>  
<body>  
<header>  
  <h1>The Elder Scrolls</h1>  
  <p>Offline Atlas of Nirn &amp; Chronological Lore Explorer</p>  
</header>  
<nav class="tabs">  
  <button class="tab-btn active" onclick="tab('map-sec',this)">Map of Nirn</button>  
  <button class="tab-btn" onclick="tab('era-sec',this)">Eras &amp; Events</button>  
  <button class="tab-btn" onclick="tab('game-sec',this)">Game Order</button>  
</nav>  
  
<section id="map-sec" class="section active">  
  <p class="hint">Use + / − to zoom, drag to pan, and tap any province, landmark, or outer realm</p>  
  <div class="map-box">  
    <div class="zoom-ui">  
      <button class="z-btn" onclick="zoom(.3)">+</button>  
      <button class="z-btn" onclick="zoom(-.3)">−</button>  
      <button class="z-btn" onclick="resetMap()">↺</button>  
    </div>  
    <svg id="map" viewBox="0 0 800 560">  
      <g id="vp">  
        <g transform="translate(735,65)" opacity=".75"><circle r="22" fill="none" stroke="#d4af37"/><polygon points="0,-20 4,-4 20,0 4,4 0,20 -4,4 -20,0 -4,-4" fill="#d4af37"/><text x="0" y="-25" fill="#d4af37" font-size="10" font-weight="bold" text-anchor="middle">N</text></g>  
        <path class="prov" fill="#4a6b82" d="M 115,130 L 145,105 L 185,95 L 225,88 L 245,112 L 220,138 L 195,148 L 185,175 L 160,178 L 148,155 L 122,165 L 105,152 Z" onclick="lore('highrock')"/>  
        <text x="168" y="132" class="lbl">HIGH ROCK</text>  
        <path class="prov" fill="#9e6b43" d="M 145,182 L 192,178 L 222,142 L 265,155 L 288,188 L 272,235 L 235,252 L 195,248 L 162,262 L 142,238 L 152,208 Z" onclick="lore('hammerfell')"/>  
        <circle class="prov" fill="#9e6b43" cx="152" cy="274" r="7" onclick="lore('hammerfell')"/>  
        <text x="215" y="212" class="lbl">HAMMERFELL</text>  
        <path class="prov" fill="#526a7a" d="M 228,88 L 285,72 L 355,68 L 425,78 L 455,115 L 442,168 L 395,182 L 335,178 L 288,185 L 265,152 L 225,136 Z" onclick="lore('skyrim')"/>  
        <path class="prov" fill="#637b8c" d="M 468,54 L 486,50 L 494,68 L 482,82 L 465,74 Z" onclick="lore('skyrim')"/>  
        <text x="350" y="122" class="lbl">SKYRIM</text>  
        <path class="prov" fill="#6e4b5e" d="M 456,112 L 515,96 L 575,118 L 605,165 L 592,225 L 555,258 L 512,252 L 492,215 L 465,188 L 444,166 Z" onclick="lore('morrowind')"/>  
        <path class="prov" fill="#82566d" d="M 505,122 L 542,115 L 562,142 L 552,172 L 505,165 Z" onclick="lore('morrowind')"/>  
        <text x="532" y="195" class="lbl">MORROWIND</text>  
        <path class="prov" fill="#4f6d4a" d="M 288,186 L 335,179 L 395,183 L 443,169 L 465,190 L 490,220 L 478,285 L 425,310 L 365,305 L 315,280 L 274,238 Z" onclick="lore('cyrodiil')"/>  
        <text x="385" y="248" class="lbl">CYRODIIL</text>  
        <path class="prov" fill="#3b5948" d="M 491,218 L 512,253 L 556,259 L 585,315 L 565,385 L 495,380 L 472,330 L 479,286 Z" onclick="lore('blackmarsh')"/>  
        <text x="528" y="325" class="lbl">BLACK MARSH</text>  
        <path class="prov" fill="#a8844c" d="M 365,306 L 425,311 L 468,290 L 462,388 L 395,395 L 360,355 Z" onclick="lore('elsweyr')"/>  
        <text x="415" y="355" class="lbl">ELSWEYR</text>  
        <path class="prov" fill="#3a6332" d="M 272,265 L 315,281 L 364,307 L 359,360 L 342,415 L 275,405 L 252,340 Z" onclick="lore('valenwood')"/>  
        <text x="310" y="355" class="lbl">VALENWOOD</text>  
        <path class="prov" fill="#8c7a3e" d="M 105,365 L 175,350 L 195,435 L 130,455 L 95,415 Z" onclick="lore('summerset')"/>  
        <path class="prov" fill="#8c7a3e" d="M 192,345 L 222,340 L 228,385 L 198,390 Z" onclick="lore('summerset')"/>  
        <text x="148" y="405" class="lbl">SUMMERSET</text>  
        <!-- Rivers, Mountains & Red Mountain -->  
        <path d="M 382,222 L 395,248 L 418,275 L 432,306 M 272,118 L 315,112 L 348,96" fill="none" stroke="#3b7ea1" stroke-width="1.8" stroke-linecap="round" pointer-events="none"/>  
        <circle cx="382" cy="222" r="5" fill="#3b7ea1" pointer-events="none"/>  
        <path d="M 290,174 L 298,164 L 306,174 M 335,170 L 343,160 L 351,170 M 385,172 L 393,162 L 401,172 M 442,122 L 450,112 L 458,122 M 446,148 L 454,138 L 462,148" fill="none" stroke="rgba(255,255,255,.45)" stroke-width="1.4" stroke-linecap="round" pointer-events="none"/>  
        <path d="M 342,142 L 352,126 L 362,142" fill="none" stroke="#fff" stroke-width="1.8" stroke-linecap="round" pointer-events="none"/>  
        <polygon points="532,132 524,148 540,148" fill="#b84a39" stroke="#ff9e7d" stroke-width="1" pointer-events="none"/>  
        <text x="532" y="157" class="city" style="fill:#ffb8a6">Red Mountain</text>  
        <!-- Capital Cities -->  
        <circle cx="382" cy="222" r="2.8" fill="#d4af37" stroke="#000" pointer-events="none"/><text x="382" y="215" class="city" style="font-weight:700">Imperial City</text>  
        <circle cx="288" cy="84" r="2.4" fill="#d4af37" stroke="#000" pointer-events="none"/><text x="288" y="79" class="city">Solitude</text>  
        <circle cx="132" cy="148" r="2.4" fill="#d4af37" stroke="#000" pointer-events="none"/><text x="132" y="157" class="city">Daggerfall</text>  
        <circle cx="176" cy="184" r="2.4" fill="#d4af37" stroke="#000" pointer-events="none"/><text x="176" y="193" class="city">Sentinel</text>  
        <circle cx="525" cy="222" r="2.4" fill="#d4af37" stroke="#000" pointer-events="none"/><text x="525" y="231" class="city">Mournhold</text>  
        <circle cx="534" cy="364" r="2.4" fill="#d4af37" stroke="#000" pointer-events="none"/><text x="534" y="373" class="city">Lilmoth</text>  
        <circle cx="424" cy="322" r="2.4" fill="#d4af37" stroke="#000" pointer-events="none"/><text x="424" y="317" class="city">Rimmen</text>  
        <circle cx="312" cy="326" r="2.4" fill="#d4af37" stroke="#000" pointer-events="none"/><text x="312" y="321" class="city">Elden Root</text>  
        <circle cx="122" cy="422" r="2.4" fill="#d4af37" stroke="#000" pointer-events="none"/><text x="122" y="431" class="city">Alinor</text>  
      </g>  
    </svg>  
  </div>  
  <div class="realm-bar">  
    <button class="realm-btn" onclick="lore('atmora')">Atmora (North)</button>  
    <button class="realm-btn" onclick="lore('akavir')">Akavir (East)</button>  
    <button class="realm-btn" onclick="lore('yokuda')">Yokuda (West)</button>  
    <button class="realm-btn" onclick="lore('pyandonea')">Pyandonea (South)</button>  
    <button class="realm-btn" onclick="lore('oblivion')">Oblivion &amp; Aetherius</button>  
  </div>  
  <div class="card">  
