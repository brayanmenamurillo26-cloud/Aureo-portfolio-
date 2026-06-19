<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Aureo — Roblox Developer</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@600;700;800&family=Inter:wght@400;500;600;700&family=JetBrains+Mono:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  :root{
    --bg-void:#0a0b0f;
    --bg-panel:#14161d;
    --bg-panel-2:#1b1e28;
    --line:#272b38;
    --line-soft:#1e2129;
    --orange:#ff6a3d;
    --orange-dim:#ff6a3d33;
    --cyan:#2fd6e8;
    --cyan-dim:#2fd6e833;
    --text:#f2f3f6;
    --muted:#8b92a5;
    --muted-2:#5c6379;
    --radius:14px;
  }

  *{margin:0;padding:0;box-sizing:border-box;}
  html{scroll-behavior:smooth;}

  button{
    font-family:inherit;
    color:inherit;
    background:none;
    border:none;
    padding:0;
    margin:0;
    cursor:pointer;
    -webkit-appearance:none;
    appearance:none;
    text-align:inherit;
  }

  @media (prefers-reduced-motion: reduce){
    html{scroll-behavior:auto;}
    *{animation-duration:0.001ms !important; animation-iteration-count:1 !important; transition-duration:0.001ms !important;}
  }

  body{
    background:var(--bg-void);
    color:var(--text);
    font-family:'Inter',sans-serif;
    line-height:1.6;
    overflow-x:hidden;
  }

  ::selection{background:var(--orange); color:#0a0b0f;}

  .eyebrow{
    font-family:'JetBrains Mono',monospace;
    font-size:13px;
    font-weight:600;
    color:var(--cyan);
    letter-spacing:0.06em;
    margin-bottom:14px;
    display:flex;
    align-items:center;
    gap:8px;
  }
  .eyebrow::before{content:"//"; color:var(--orange);}

  h1,h2,h3{
    font-family:'Orbitron',sans-serif;
    letter-spacing:0.01em;
  }

  .wrap{max-width:1080px; margin:0 auto; padding:0 24px;}
  section{padding:96px 0;}

  /* ===== NAV ===== */
  header{
    position:fixed; top:0; left:0; right:0; z-index:100;
    background:rgba(10,11,15,0.85);
    backdrop-filter:blur(10px);
    border-bottom:1px solid var(--line-soft);
  }
  nav.wrap{
    display:flex; align-items:center; justify-content:space-between;
    height:72px;
    max-width:1080px;
  }
  .logo{
    font-family:'Orbitron',sans-serif;
    font-weight:800;
    font-size:19px;
    color:var(--text);
    display:flex; align-items:center; gap:10px;
    text-decoration:none;
  }
  .logo-mark{
    width:32px; height:32px;
    border-radius:50%;
    object-fit:cover;
    border:1.5px solid var(--orange);
    box-shadow:0 0 14px var(--orange-dim);
  }
  .logo span{color:var(--orange);}
  .navlinks{display:flex; gap:34px; list-style:none;}
  .navlinks button{
    color:var(--muted);
    text-decoration:none;
    font-size:14.5px;
    font-weight:500;
    transition:color .2s;
  }
  .navlinks button:hover{color:var(--text);}
  .nav-cta{
    font-family:'JetBrains Mono',monospace;
    font-size:13px; font-weight:600;
    color:var(--bg-void);
    background:var(--orange);
    padding:9px 18px;
    border-radius:8px;
    text-decoration:none;
    white-space:nowrap;
    transition:transform .2s, box-shadow .2s;
  }
  .nav-cta:hover{ transform:translateY(-2px); box-shadow:0 6px 20px var(--orange-dim);}
  .burger{display:none; flex-direction:column; gap:5px; background:none; border:none; cursor:pointer; padding:8px;}
  .burger span{width:22px; height:2px; background:var(--text);}
  .mobile-menu{
    display:none;
    flex-direction:column;
    background:var(--bg-panel);
    border-bottom:1px solid var(--line-soft);
    padding:8px 24px 20px;
  }
  .mobile-menu button{
    color:var(--muted); text-decoration:none; padding:12px 0;
    border-bottom:1px solid var(--line-soft); font-size:15px;
    width:100%; display:block;
  }
  .mobile-menu.open{display:flex;}

  /* ===== HERO ===== */
  .hero{
    position:relative;
    min-height:100svh;
    display:flex; align-items:center;
    padding-top:140px;
    overflow:hidden;
  }
  .grid-floor{
    position:absolute; left:0; right:0; bottom:0; height:60%;
    background-image:
      linear-gradient(var(--line-soft) 1px, transparent 1px),
      linear-gradient(90deg, var(--line-soft) 1px, transparent 1px);
    background-size:48px 48px;
    transform:perspective(420px) rotateX(62deg);
    transform-origin:bottom;
    mask-image:linear-gradient(to top, black 10%, transparent 85%);
    -webkit-mask-image:linear-gradient(to top, black 10%, transparent 85%);
    opacity:0.55;
  }
  .glow-orb{
    position:absolute; border-radius:50%; filter:blur(90px);
    pointer-events:none;
  }
  .glow-orb.one{ width:420px; height:420px; background:var(--orange); opacity:0.16; top:-120px; right:-80px;}
  .glow-orb.two{ width:380px; height:380px; background:var(--cyan); opacity:0.12; bottom:-140px; left:-100px;}

  .hero-inner{ position:relative; z-index:2; text-align:center; width:100%;}

  .avatar-ring{
    width:128px; height:128px;
    margin:0 auto 32px;
    border-radius:50%;
    padding:4px;
    background:conic-gradient(from 0deg, var(--orange), var(--cyan), var(--orange));
    box-shadow:0 0 0 1px var(--line-soft), 0 0 36px var(--orange-dim), 0 0 50px var(--cyan-dim);
  }
  .avatar-ring-inner{
    width:100%; height:100%;
    border-radius:50%;
    overflow:hidden;
    background:var(--bg-void);
    border:3px solid var(--bg-void);
  }
  .avatar-ring-inner img{
    width:100%; height:100%;
    object-fit:cover;
    display:block;
  }

  .hero h1{
    font-size:clamp(34px,6vw,58px);
    font-weight:800;
    margin-bottom:18px;
  }
  .hero h1 .accent{color:var(--orange);}
  .hero p.lead{
    color:var(--muted);
    font-size:clamp(15px,2vw,18.5px);
    max-width:560px;
    margin:0 auto 38px;
  }
  .hero p.lead b{ color:var(--text); font-weight:600;}

  .hero-actions{ display:flex; gap:16px; justify-content:center; flex-wrap:wrap; margin-bottom:64px;}
  .btn{
    font-family:'JetBrains Mono',monospace;
    font-size:14px; font-weight:600;
    padding:14px 28px;
    border-radius:9px;
    text-decoration:none;
    cursor:pointer;
    transition:transform .2s, box-shadow .2s, background .2s;
    display:inline-flex; align-items:center; gap:8px;
  }
  .btn-primary{ background:var(--orange); color:#0a0b0f;}
  .btn-primary:hover{ transform:translateY(-2px); box-shadow:0 8px 26px var(--orange-dim);}
  .btn-ghost{ background:transparent; color:var(--text); border:1px solid var(--line);}
  .btn-ghost:hover{ border-color:var(--cyan); color:var(--cyan);}

  .stat-row{
    display:grid;
    grid-template-columns:repeat(3,1fr);
    gap:16px;
    max-width:680px;
    margin:0 auto;
  }
  .stat{
    background:var(--bg-panel);
    border:1px solid var(--line-soft);
    border-radius:var(--radius);
    padding:20px 14px;
  }
  .stat .num{
    font-family:'Orbitron',sans-serif;
    font-size:24px; font-weight:700; color:var(--orange);
  }
  .stat .label{
    font-family:'JetBrains Mono',monospace;
    font-size:11px; color:var(--muted); text-transform:uppercase;
    letter-spacing:0.04em; margin-top:6px;
  }

  /* ===== SECTION HEADERS ===== */
  .sec-head{ max-width:600px; margin-bottom:48px;}
  .sec-head h2{ font-size:clamp(26px,4vw,36px); font-weight:700;}

  /* ===== ABOUT ===== */
  .about-grid{
    display:grid;
    grid-template-columns:1.05fr 0.95fr;
    gap:56px;
    align-items:center;
  }
  .about-list{ list-style:none; display:flex; flex-direction:column; gap:18px;}
  .about-list li{
    display:flex; gap:12px;
    color:var(--muted);
    font-size:15.5px;
  }
  .about-list li::before{
    content:"▹"; color:var(--orange); flex-shrink:0; font-size:15px; margin-top:1px;
  }
  .about-list li b{ color:var(--text); font-weight:600;}
  .about-media{
    background:var(--bg-panel);
    border:1px solid var(--line-soft);
    border-radius:var(--radius);
    padding:18px;
  }
  .about-media img{ width:100%; border-radius:8px; display:block;}
  .about-media .cap{
    font-family:'JetBrains Mono',monospace;
    font-size:12.5px; color:var(--muted-2);
    margin-top:14px;
  }

  /* ===== SKILLS ===== */
  .badges{ display:flex; flex-wrap:wrap; gap:10px; margin-bottom:48px;}
  .badge{
    font-family:'JetBrains Mono',monospace;
    font-size:13px; font-weight:500;
    color:var(--text);
    background:var(--bg-panel);
    border:1px solid var(--line);
    padding:9px 16px;
    border-radius:999px;
  }
  .badge .dot{ width:6px; height:6px; border-radius:50%; display:inline-block; margin-right:8px;}

  .cards3{ display:grid; grid-template-columns:repeat(3,1fr); gap:20px;}
  .card{
    background:var(--bg-panel);
    border:1px solid var(--line-soft);
    border-radius:var(--radius);
    padding:26px;
  }
  .card h3{ font-family:'Inter',sans-serif; font-size:16px; font-weight:700; margin-bottom:16px; display:flex; align-items:center; gap:9px;}
  .card-icon{ width:26px; height:26px; border-radius:7px; display:flex; align-items:center; justify-content:center; font-size:13px; flex-shrink:0;}
  .card.can .card-icon{ background:#1d3b2c; color:#5fe3a0;}
  .card.cant .card-icon{ background:#3b2020; color:#ff8585;}
  .card.rates .card-icon{ background:#33291a; color:var(--orange);}
  .card ul{ list-style:none; display:flex; flex-direction:column; gap:11px;}
  .card ul li{ font-size:14px; color:var(--muted); padding-left:16px; position:relative;}
  .card ul li::before{ content:"–"; position:absolute; left:0; color:var(--muted-2);}
  .rate-row{ display:flex; justify-content:space-between; align-items:center; padding:11px 0; border-bottom:1px solid var(--line-soft); font-size:14px;}
  .rate-row:last-of-type{ border-bottom:none;}
  .rate-row span:first-child{ color:var(--muted);}
  .rate-row .price{ font-family:'JetBrains Mono',monospace; color:var(--orange); font-weight:600; font-size:13px; background:var(--orange-dim); padding:3px 9px; border-radius:6px;}
  .rate-range{
    display:flex; align-items:baseline; gap:10px;
    font-family:'JetBrains Mono',monospace;
    margin-bottom:14px;
  }
  .rate-from{ font-size:20px; font-weight:600; color:var(--text);}
  .rate-arrow{ color:var(--muted-2); font-size:15px;}
  .rate-to{ font-size:22px; font-weight:700; color:var(--orange);}
  .rate-desc{ font-size:13.5px; color:var(--muted); margin-bottom:14px;}
  .rate-note{ font-size:12px; color:var(--muted-2); margin-top:0; font-style:italic;}

  /* ===== PROJECTS ===== */
  .proj-grid{ display:grid; grid-template-columns:repeat(2,1fr); gap:22px;}
  .proj-card{
    background:var(--bg-panel);
    border:1px solid var(--line-soft);
    border-radius:var(--radius);
    overflow:hidden;
    transition:transform .25s, border-color .25s, box-shadow .25s;
  }
  .proj-card:hover{ transform:translateY(-4px); border-color:var(--orange); box-shadow:0 14px 36px rgba(0,0,0,0.4);}
  .proj-media{ position:relative; background:#000;}
  .proj-media img{ width:100%; display:block; aspect-ratio:16/10; object-fit:cover;}
  .proj-media.duo{ display:grid; grid-template-columns:1fr 1fr; gap:2px;}
  .proj-media.duo img{ aspect-ratio:4/5;}
  .role-tag{
    position:absolute; top:12px; left:12px;
    font-family:'JetBrains Mono',monospace;
    font-size:11px; font-weight:600;
    background:rgba(10,11,15,0.85);
    border:1px solid var(--cyan);
    color:var(--cyan);
    padding:5px 11px;
    border-radius:999px;
    backdrop-filter:blur(4px);
  }
  .proj-body{ padding:22px;}
  .proj-body h3{ font-family:'Inter',sans-serif; font-size:17px; font-weight:700; margin-bottom:9px;}
  .proj-body p{ font-size:14px; color:var(--muted);}

  /* ===== TERMS ===== */
  .terms-grid{ display:grid; grid-template-columns:repeat(3,1fr); gap:20px;}
  .term-card{
    background:var(--bg-panel);
    border:1px solid var(--line-soft);
    border-radius:var(--radius);
    padding:26px;
  }
  .term-card .ti{ font-size:22px; margin-bottom:14px; display:block;}
  .term-card h3{ font-family:'Inter',sans-serif; font-size:15.5px; font-weight:700; margin-bottom:10px;}
  .term-card p{ font-size:13.5px; color:var(--muted);}

  /* ===== CONTACT ===== */
  .contact-box{
    background:linear-gradient(155deg,var(--bg-panel),var(--bg-panel-2));
    border:1px solid var(--line-soft);
    border-radius:20px;
    padding:56px 40px;
    text-align:center;
    position:relative;
    overflow:hidden;
  }
  .contact-box::before{
    content:""; position:absolute; inset:0;
    background:radial-gradient(circle at 50% 0%, var(--orange-dim), transparent 60%);
    pointer-events:none;
  }
  .contact-box h2{ font-size:clamp(24px,4vw,32px); margin-bottom:14px; position:relative;}
  .contact-box > p{ color:var(--muted); max-width:480px; margin:0 auto 36px; position:relative;}
  .contact-row{ display:flex; gap:16px; justify-content:center; flex-wrap:wrap; position:relative;}
  .contact-pill{
    display:flex; align-items:center; gap:12px;
    background:var(--bg-void);
    border:1px solid var(--line);
    padding:14px 22px;
    border-radius:12px;
    text-decoration:none;
    color:var(--text);
    font-size:14.5px;
    transition:border-color .2s, transform .2s;
  }
  .contact-pill:hover{ border-color:var(--orange); transform:translateY(-2px);}
  .contact-pill .ic{ font-size:18px;}
  .contact-pill .meta{ display:flex; flex-direction:column; align-items:flex-start;}
  .contact-pill .meta b{ font-size:14px;}
  .contact-pill .meta span{ font-family:'JetBrains Mono',monospace; font-size:12px; color:var(--muted);}

  #contact{ scroll-margin-top:90px;}
  #projects{ scroll-margin-top:90px;}
  footer{
    padding:32px 24px;
    text-align:center;
    color:var(--muted-2);
    font-size:13px;
    border-top:1px solid var(--line-soft);
    font-family:'JetBrains Mono',monospace;
  }

  .reveal{ opacity:0; transform:translateY(18px); transition:opacity .6s ease, transform .6s ease;}
  .reveal.show{ opacity:1; transform:translateY(0);}

  /* ===== RESPONSIVE ===== */
  @media (max-width:880px){
    .navlinks{ display:none;}
    .burger{ display:flex;}
    .about-grid{ grid-template-columns:1fr;}
    .cards3{ grid-template-columns:1fr;}
    .proj-grid{ grid-template-columns:1fr;}
    .terms-grid{ grid-template-columns:1fr;}
    .stat-row{ grid-template-columns:repeat(3,1fr); gap:10px;}
    .stat .num{ font-size:19px;}
    section{ padding:72px 0;}
  }
  @media (max-width:480px){
    .stat-row{ grid-template-columns:1fr; }
  }
</style>
</head>
<body>

<header>
  <nav class="wrap">
    <button type="button" class="logo" data-target="home"><img class="logo-mark" src="data:image/jpeg;base64,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
