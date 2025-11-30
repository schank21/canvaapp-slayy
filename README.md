<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Slayy – Mokup HYPER-DECO</title>
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <script src="https://unpkg.com/lucide@latest"></script>
  <style>
    /* ----------  RESET  ---------- */
    *,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
    body{font-family:system-ui,-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,"Helvetica Neue",Arial;font-size:14px;background:#0f0f0f;display:flex;align-items:center;justify-content:center;min-height:100vh;padding:1rem;overflow:hidden}

    /* ----------  PALETTE  ---------- */
    :root{
      --denim-50:#eef2ff;
      --denim-600:#4f46e5;
      --denim-700:#4338ca;
      --denim-900:#312e81;
      --pop:#f43f5e;
      --pop-light:#fb7185;
    }

    /* ----------  PHONE FRAME  ---------- */
    .phone{
      position:relative;
      width:100%;
      max-width:420px;
      background:#000;
      border-radius:3rem;
      padding:.75rem;
      box-shadow:0 0 40px 0 var(--denim-600),0 25px 50px -12px rgba(0,0,0,.6);
      overflow:hidden;
      z-index:0
    }
    /* reflexe + lueur */
    .phone::before{
      content:'';
      position:absolute;
      inset:0;
      border-radius:3rem;
      padding:2px;
      background:linear-gradient(135deg,var(--denim-600),var(--pop));
      -webkit-mask:linear-gradient(#fff 0 0) content-box,linear-gradient(#fff 0 0);
      mask:linear-gradient(#fff 0 0) content-box,linear-gradient(#fff 0 0);
      -webkit-mask-composite:xor;
      mask-composite:exclude;
      z-index:-1
    }
    .screen{
      background:#fff;
      border-radius:2.5rem;
      overflow:hidden;
      height:calc(100vh - 4rem);
      max-height:800px;
      display:flex;
      flex-direction:column;
      position:relative
    }

    /* ----------  PARTICULES  ---------- */
    .particles{
      position:absolute;
      inset:0;
      pointer-events:none;
      overflow:hidden;
      z-index:0
    }
    .particle{
      position:absolute;
      width:4px;height:4px;
      background:var(--denim-600);
      border-radius:50%;
      opacity:.6;
      animation:float 20s infinite linear
    }
    @keyframes float{
      0%{transform:translateY(110vh) scale(1)}
      100%{transform:translateY(-10vh) scale(1.8)}
    }

    /* ----------  STATUS BAR  ---------- */
    .status{
      display:flex;
      justify-content:space-between;
      align-items:center;
      padding:.75rem 1.5rem .5rem;
      font-size:.65rem;
      font-weight:600;
      position:relative;
      z-index:2
    }

    /* ----------  HOME HERO  ---------- */
    .hero{
      position:relative;
      isolation:isolate;
      padding:2.5rem 2rem 2rem;
      color:#fff;
      overflow:hidden;
      z-index:1
    }
    /* fond animé */
    .hero::before{
      content:'';
      position:absolute;
      inset:-100%;
      background:linear-gradient(135deg,var(--denim-700),var(--denim-900),var(--pop),var(--denim-700));
      background-size:400% 400%;
      animation:gradientShift 12s ease infinite;
      z-index:-2
    }
    @keyframes gradientShift{
      0%{background-position:0% 50%}
      50%{background-position:100% 50%}
      100%{background-position:0% 50%}
    }
    /* bulles glass */
    .bubble{
      position:absolute;
      border-radius:50%;
      background:rgba(255,255,255,.08);
      backdrop-filter:blur(12px);
      -webkit-backdrop-filter:blur(12px);
      border:1px solid rgba(255,255,255,.15);
      box-shadow:0 8px 32px 0 rgba(0,0,0,.37)
    }
    .b1{width:12rem;height:12rem;top:-4rem;right:-4rem;animation:bob 8s ease-in-out infinite}
    .b2{width:8rem;height:8rem;bottom:-3rem;left:-3rem;animation:bob 10s ease-in-out infinite reverse}
    @keyframes bob{
      0%,100%{transform:translateY(0)}
      50%{transform:translateY(-1rem)}
    }

    .hero h1{
      font-family:Georgia,serif;
      font-style:italic;
      font-size:3.5rem;
      line-height:1;
      margin-bottom:.25rem;
      text-shadow:0 0 20px rgba(255,255,255,.3)
    }
    .hero p{margin-bottom:1.5rem;font-size:.875rem;opacity:.9}
    .btn-primary{
      width:100%;
      background:#fff;
      color:var(--denim-700);
      border:none;
      border-radius:9999px;
      padding:1rem;
      font-weight:700;
      font-size:1.05rem;
      display:flex;
      align-items:center;
      justify-content:center;
      gap:.5rem;
      box-shadow:0 0 20px 0 rgba(255,255,255,.4);
      cursor:pointer;
      transition:transform .2s
    }
    .btn-primary:hover{transform:scale(1.03)}
    .btn-primary:active{transform:scale(.98)}

    /* ----------  SECTIONS  ---------- */
    .section{padding:1.5rem;position:relative;z-index:2}
    .section-title{
      font-family:Georgia,serif;
      font-size:1.25rem;
      margin-bottom:1rem;
      color:#1f2937
    }
    .step{
      display:flex;
      align-items:flex-start;
      gap:1rem;
      background:rgba(255,255,255,.7);
      backdrop-filter:blur(8px);
      -webkit-backdrop-filter:blur(8px);
      border-radius:1rem;
      padding:1rem;
      box-shadow:0 4px 6px -1px rgba(0,0,0,.05),0 2px 4px -2px rgba(0,0,0,.05);
      border-left:4px solid;
      transition:transform .2s
    }
    .step:hover{transform:scale(1.02)}
    .step-icon{
      flex-shrink:0;
      width:3rem;height:3rem;
      border-radius:50%;
      display:grid;place-items:center;
      color:#fff;
      box-shadow:0 4px 6px -1px rgba(0,0,0,.1)
    }
    .step.denim .step-icon{background:linear-gradient(135deg, var(--denim-600), var(--denim-700))}
    .step.denim{border-color:var(--denim-600)}
    .step.slate .step-icon{background:linear-gradient(135deg, #64748b, #475569)}
    .step.slate{border-color:#64748b}
    .step.pop .step-icon{background:linear-gradient(135deg, var(--pop), var(--pop-light))}
    .step.pop{border-color:var(--pop)}

    /* ----------  PROMO  ---------- */
    .promo{
      position:relative;
      isolation:isolate;
      border-radius:1rem;
      padding:1.5rem;
      color:#fff;
      margin-top:1.5rem;
      overflow:hidden;
      box-shadow:0 0 20px 0 var(--pop-light)
    }
    .promo::before{
      content:'';
      position:absolute;
      inset:0;
      background:linear-gradient(90deg, var(--pop), #e11d48);
      z-index:-1
    }
    .promo-bg{
      position:absolute;
      width:10rem;height:10rem;
      top:-3rem;right:-3rem;
      background:rgba(255,255,255,.08);
      border-radius:50%;
      filter:blur(20px)
    }

    /* ----------  GRID  ---------- */
    .grid2{
      display:grid;
      grid-template-columns:repeat(2,1fr);
      gap:1rem;
      margin-top:1rem
    }
    .card{
      position:relative;
      border-radius:1rem;
      overflow:hidden;
      box-shadow:0 4px 6px -1px rgba(0,0,0,.05);
      cursor:pointer;
      transition:transform .2s
    }
    .card:hover{transform:scale(1.02)}
    .card-img{
      aspect-ratio:3/4;
      background:linear-gradient(135deg, var(--denim-50), #c7d2fe);
      display:grid;place-items:center
    }
    .card-icon{width:4rem;height:4rem;color:var(--denim-700);opacity:.7}
    .card-fav{
      position:absolute;
      top:.5rem;right:.5rem;
      background:rgba(255,255,255,.8);
      backdrop-filter:blur(4px);
      border-radius:50%;
      padding:.5rem;
      line-height:0
    }
    .card-info{
      position:absolute;
      bottom:0;left:0;right:0;
      background:rgba(255,255,255,.92);
      backdrop-filter:blur(4px);
      padding:.75rem
    }
    .card-info strong{display:block;font-size:.8125rem;color:#111}
    .card-info span{color:var(--denim-700);font-weight:700;font-size:.8125rem}

    /* ----------  SCAN  ---------- */
    .scan{flex:1;display:flex;flex-direction:column;background:#000;color:#fff}
    .scan-header{padding:2rem 1.5rem 1rem}
    .scan-header a{display:inline-flex;align-items:center;gap:.5rem;color:#d1d5db;text-decoration:none;font-size:.875rem}
    .scan-header h2{font-family:Georgia,serif;font-style:italic;font-size:1.75rem;margin-top:.5rem}
    .scan-header p{color:#9ca3af;font-size:.8125rem;margin-top:.25rem}
    .scan-body{flex:1;position:relative;display:grid;place-items:center}
    .scan-body::before{
      content:'';
      position:absolute;
      inset:0;
      background:radial-gradient(circle at center, #1f2937 0%, #000 70%)
    }
    .scan-frame{
      position:relative;
      width:14rem;height:28rem;
      border:4px dashed var(--denim-600);
      border-radius:2rem;
      display:grid;place-items:center;
      box-shadow:0 0 20px 0 var(--denim-600),inset 0 0 20px 0 rgba(99,102,241,.3)
    }
    .scan-frame svg{color:var(--denim-400);opacity:.5;width:8rem;height:8rem}
    .scan-hint{
      position:absolute;
      bottom:4rem;left:50%;
      transform:translateX(-50%);
      background:var(--denim-600);
      color:#fff;
      padding:.5rem 1rem;
      border-radius:9999px;
      font-size:.8125rem;
      display:flex;align-items:center;gap:.5rem;
      box-shadow:0 10px 15px -3px rgba(0,0,0,.2)
    }
    .scan-btn{
      margin:2rem auto;
      width:5rem;height:5rem;
      background:var(--pop);
      border:4px solid #fff;
      border-radius:50%;
      box-shadow:0 0 20px 0 var(--pop-light);
      cursor:pointer;
      transition:background .2s
    }
    .scan-btn:hover{background:#e11d48}
    .scan-btn svg{margin:auto}

    /* ----------  BOTTOM BAR  ---------- */
    .bar{
      background:rgba(255,255,255,.8);
      backdrop-filter:blur(8px);
      border-top:1px solid #e5e7eb;
      display:flex;
      justify-content:space-around;
      padding:.5rem 0
    }
    .bar-item{
      flex:1;
      display:flex;
      flex-direction:column;
      align-items:center;
      gap:.25rem;
      background:none;
      border:none;
      color:#9ca3af;
      font-size:.65rem;
      font-weight:600;
      cursor:pointer
    }
    .bar-item.active{color:var(--denim-600)}
  </style>
</head>
<body>

<div class="phone">
  <div class="particles" id="particles"></div>
  <div class="screen">

    <!-- STATUS BAR -->
    <div class="status">
      <span>9:41</span>
      <div style="display:flex;gap:.25rem;align-items:center">
        <span style="width:1rem;height:.75rem;border:1px solid #111;border-radius:2px"></span>
        <span style="width:.25rem;height:.5rem;background:#111;border-radius:1px"></span>
      </div>
    </div>

    <!-- HOME -->
    <div id="home" class="home">
      <div class="hero">
        <div class="bubble b1"></div><div class="bubble b2"></div>
        <div style="display:flex;align-items:center;gap:.5rem;margin-bottom:.75rem">
          <span style="width:2rem;height:.25rem;background:var(--pop);border-radius:99px"></span>
          <span style="font-size:.65rem;font-weight:700;letter-spacing:.1em;color:#e0e7ff">NOUVEAU</span>
        </div>
        <h1>Slayy</h1>
        <p>Ton jean parfait, virtuellement tien ✨</p>
        <button class="btn-primary" onclick="showScan()">
          <i data-lucide="camera" width="24" height="24"></i>
          Scanner ma silhouette
        </button>
      </div>

      <div class="section">
        <h2 class="section-title">Comment ça marche ?</h2>

        <div class="step denim">
          <div class="step-icon"><i data-lucide="camera"></i></div>
          <div>
            <strong>1. Scanne-toi</strong>
            <p style="font-size:.8125rem;color:#4b5563">Capture ta silhouette en 3 s.</p>
          </div>
        </div>

        <div class="step slate">
          <div class="step-icon"><i data-lucide="sparkles"></i></div>
          <div>
            <strong>2. Projette ton jean</strong>
            <p style="font-size:.8125rem;color:#4b5563">Essaie des centaines de modèles en AR.</p>
          </div>
        </div>

        <div class="step pop">
          <div class="step-icon"><i data-lucide="share-2"></i></div>
          <div>
            <strong>3. Partage & Achète</strong>
            <p style="font-size:.8125rem;color:#4b5563">Montre ton fit et commande en 1 clic.</p>
          </div>
        </div>

        <div class="promo">
          <div class="promo-bg"></div>
          <p style="font-size:.65rem;font-weight:700">🔥 OFFRE LIMITÉE</p>
          <p style="font-family:Georgia,serif;font-style:italic;font-size:1.5rem;margin-top:.25rem">–20 % sur ta 1ère commande</p>
          <p style="font-size:.8125rem;opacity:.9">Code : SLAYY20</p>
        </div>

        <div style="margin-top:2rem">
          <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:1rem">
            <h2 class="section-title">Nouveautés</h2>
            <button style="font-size:.8125rem;font-weight:600;color:var(--denim-600)">Voir tout</button>
          </div>
          <div class="grid2">
            <!-- CARD 1 -->
            <div class="card">
              <div class="card-img"><i data-lucide="user" class="card-icon"></i></div>
              <button class="card-fav"><i data-lucide="heart" color="var(--pop)"></i></button>
              <div class="card-info">
                <strong>Slim Fit Blue</strong>
                <span>8 500 DZD</span>
              </div>
            </div>
            <!-- CARD 2 -->
            <div class="card">
              <div class="card-img"><i data-lucide="user" class="card-icon"></i></div>
              <button class="card-fav"><i data-lucide="heart" color="var(--pop)"></i></button>
              <div class="card-info">
                <strong>Straight Raw</strong>
                <span>9 200 DZD</span>
              </div>
            </div>
            <!-- CARD 3 -->
            <div class="card">
              <div class="card-img"><i data-lucide="user" class="card-icon"></i></div>
              <button class="card-fav"><i data-lucide="heart" color="var(--pop)"></i></button>
              <div class="card-info">
                <strong>Wide Leg Light</strong>
                <span>7 900 DZD</span>
              </div>
            </div>
            <!-- CARD 4 -->
            <div class="card">
              <div class="card-img"><i data-lucide="user" class="card-icon"></i></div>
              <button class="card-fav"><i data-lucide="heart" color="var(--pop)"></i></button>
              <div class="card-info">
                <strong>Skinny Black</strong>
                <span>8 000 DZD</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- SCAN -->
    <div id="scan" class="scan" style="display:none">
      <div class="scan-header">
        <a href="#" onclick="showHome()"><i data-lucide="arrow-left"></i> Retour</a>
        <h2>Scanne ta silhouette</h2>
        <p>Place-toi à 2 m, corps entier visible</p>
      </div>
      <div class="scan-body">
        <div class="scan-frame"><i data-lucide="user"></i></div>
        <div class="scan-hint"><i data-lucide="sparkles"></i> Positionne-toi dans le cadre</div>
      </div>
      <button class="scan-btn" aria-label="Capturer"><i data-lucide="camera" color="#fff"></i></button>
    </div>

    <!-- BOTTOM BAR -->
    <div class="bar" id="bar">
      <button class="bar-item active"><i data-lucide="home"></i>Accueil</button>
      <button class="bar-item"><i data-lucide="search"></i>Explorer</button>
      <button class="bar-item"><i data-lucide="heart"></i>Favoris</button>
      <button class="bar-item"><i data-lucide="shopping-bag"></i>Panier</button>
    </div>

  </div>
</div>

<!-- APP INFO -->
<div style="text-align:center;margin-top:1.5rem">
  <h3 style="font-family:Georgia,serif;font-style:italic;font-size:1.5rem;color:#fff;text-shadow:0 0 10px var(--denim-600)">Slayy</h3>
  <p style="font-size:.8125rem;color:#9ca3af">Essayage virtuel de jeans • Mode & Tech</p>
</div>

<script>
  /* ----------  PARTICLES GENERATOR  ---------- */
  const particles = document.getElementById('particles');
  for(let i=0;i<40;i++){
    const p = document.createElement('div');
    p.className='particle';
    p.style.left = Math.random()*100 + '%';
    p.style.animationDelay = Math.random()*20 + 's';
    p.style.animationDuration = (15+Math.random()*10) + 's';
    particles.appendChild(p);
  }

  /* ----------  SWITCH SCREENS  ---------- */
  function showScan(){
    document.getElementById('home').style.display='none';
    document.getElementById('scan').style.display='flex';
    document.getElementById('bar').style.display='flex';
  }
  function showHome(){
    document.getElementById('scan').style.display='none';
    document.getElementById('home').style.display='block';
    document.getElementById('bar').style.display='flex';
  }
  /* ----------  LUCIDE ICONS  ---------- */
  lucide.createIcons();
</script>

</body>
</html>
