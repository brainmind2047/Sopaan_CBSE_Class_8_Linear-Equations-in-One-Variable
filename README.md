<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Sopaan · Linear Equations in One Variable</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,500;9..144,700&family=Source+Sans+3:wght@400;600;700&family=IBM+Plex+Mono:wght@500;600&display=swap">
<style>
  html,body{margin:0;} img{max-width:100%;} [hidden]{display:none !important;}
  :root{
    --navy:#16264A; --navy-2:#1F3B6B; --gold:#C79A3E; --gold-soft:#F3E7C9;
    --paper:#FBF9F4; --paper-2:#F1EAD8; --card:#FFFFFF;
    --ink:#211E1A; --ink-soft:#655D4C; --rule:#E4DCC8;
    --success:#2E8B57; --success-soft:#E1F2E7;
    --danger:#BF4B45; --danger-soft:#FAE3E1;
    --locked:#C7BEA9;
    --focus:#1F3B6B;
    --accent-text:#1F3B6B; --retry-text:#8A661F;
    color-scheme:light;
  }
  @media (prefers-color-scheme: dark){
    :root:not([data-theme="light"]){
      --navy:#0E1830; --navy-2:#16264A; --gold:#E0B75B; --gold-soft:#3A2F16;
      --paper:#141210; --paper-2:#1C1914; --card:#1C1914;
      --ink:#EDE7DA; --ink-soft:#B2A996; --rule:#3A342A;
      --success:#7BC79A; --success-soft:#1B2E22;
      --danger:#E38884; --danger-soft:#331D1B;
      --locked:#4A4436;
      --focus:#E0B75B;
      --accent-text:#E0B75B; --retry-text:#E0B75B;
      color-scheme:dark;
    }
  }
  :root[data-theme="dark"]{
    --navy:#0E1830; --navy-2:#16264A; --gold:#E0B75B; --gold-soft:#3A2F16;
    --paper:#141210; --paper-2:#1C1914; --card:#1C1914;
    --ink:#EDE7DA; --ink-soft:#B2A996; --rule:#3A342A;
    --success:#7BC79A; --success-soft:#1B2E22;
    --danger:#E38884; --danger-soft:#331D1B;
    --locked:#4A4436;
    --focus:#E0B75B;
    --accent-text:#E0B75B; --retry-text:#E0B75B;
    color-scheme:dark;
  }

  *{box-sizing:border-box;}
  body{background:var(--paper); color:var(--ink); font-family:'Source Sans 3',-apple-system,'Segoe UI',sans-serif; padding-inline:0; padding-block:0;}
  h1,h2,h3{font-family:'Fraunces',Georgia,serif; text-wrap:balance; margin:0;}
  .num{font-family:'IBM Plex Mono',ui-monospace,monospace; font-variant-numeric:tabular-nums;}

  header.brand{
    background:linear-gradient(155deg,var(--navy) 0%, var(--navy-2) 100%);
    color:#F4EFDF; padding-block:calc(20px + env(safe-area-inset-top,0px)) 18px; padding-inline:20px;
  }
  .brand-row{display:flex; align-items:center; gap:12px; max-width:900px; margin:0 auto;}
  .crest{
    width:42px; height:42px; border-radius:10px; background:var(--gold); color:var(--navy);
    display:flex; align-items:center; justify-content:center; font-family:'Fraunces',serif; font-weight:700; font-size:18px; flex-shrink:0;
  }
  .brand-name{font-size:12px; letter-spacing:.08em; text-transform:uppercase; color:var(--gold); font-weight:700;}
  .series-name{font-size:19px; font-weight:700; font-family:'Fraunces',serif;}
  .chapter-eyebrow{max-width:900px; margin:14px auto 0; font-size:12px; letter-spacing:.06em; text-transform:uppercase; color:#AEB9D6;}
  .chapter-title{font-size:28px; max-width:900px; margin:2px auto 0;}
  .chapter-sub{font-size:14.5px; color:var(--gold); font-weight:700; max-width:900px; margin:3px auto 0;}

  .chapter-progress{max-width:900px; margin:14px auto 0; display:flex; align-items:center; gap:10px;}
  .cp-track{flex:1; height:6px; border-radius:99px; background:rgba(255,255,255,.18); overflow:hidden;}
  .cp-fill{height:100%; background:var(--gold); border-radius:99px; transition:width .3s ease;}
  .cp-label{font-size:11.5px; color:#CFD7EA; white-space:nowrap;}

  .tabbar{position:sticky; top:env(safe-area-inset-top,0px); z-index:15; background:var(--paper); border-bottom:1px solid var(--rule); overflow-x:auto; white-space:nowrap;}
  .tabbar-inner{max-width:900px; margin:0 auto; display:flex; padding-inline:16px;}
  .tab-btn{font-family:inherit; font-size:14px; font-weight:600; color:var(--ink-soft); background:none; border:none; padding:13px 16px; cursor:pointer; position:relative; flex-shrink:0;}
  .tab-btn.active{color:var(--accent-text);}
  .tab-btn.active::after{content:''; position:absolute; left:12px; right:12px; bottom:0; height:3px; background:var(--gold); border-radius:3px 3px 0 0;}
  .tab-count{font-size:11px; color:var(--ink-soft); margin-left:5px;}

  .slide-progress{max-width:900px; margin:0 auto; padding:10px 16px 0; display:flex; align-items:center; gap:10px;}
  .sp-track{flex:1; height:5px; border-radius:99px; background:var(--rule); overflow:hidden;}
  .sp-fill{height:100%; background:var(--accent-text); border-radius:99px; transition:width .3s ease;}
  .sp-label{font-size:12px; color:var(--ink-soft); white-space:nowrap; font-weight:600;}

  .wrap{max-width:900px; margin:0 auto; padding:16px 16px calc(110px + env(safe-area-inset-bottom,0px));}

  .qcard{background:var(--card); border:1px solid var(--rule); border-radius:14px; padding:18px;}
  .qhead{display:flex; align-items:flex-start; gap:10px; margin-bottom:10px;}
  .qnum{width:32px; height:32px; border-radius:8px; background:var(--gold-soft); color:var(--accent-text); display:flex; align-items:center; justify-content:center; font-weight:700; font-family:'Fraunces',serif; flex-shrink:0; font-size:14px;}
  .qtext{font-size:16px; line-height:1.55; flex:1;}
  .qtag{font-size:10.5px; color:var(--gold); background:var(--gold-soft); padding:2px 7px; border-radius:99px; font-weight:700; margin-left:6px; white-space:nowrap;}
  .marks-pill{font-size:11px; font-weight:700; color:var(--ink-soft); border:1px solid var(--rule); padding:3px 9px; border-radius:99px; margin-left:auto; flex-shrink:0; white-space:nowrap;}
  .step-badge{font-size:11px; font-weight:700; color:var(--accent-text); background:var(--paper-2); border:1px solid var(--rule); padding:3px 9px; border-radius:99px; display:inline-block; margin-bottom:12px;}

  .options{display:flex; flex-direction:column; gap:8px; margin-top:10px;}
  .opt{display:flex; align-items:center; gap:10px; padding:11px 12px; border:1.5px solid var(--rule); border-radius:10px; cursor:pointer; font-size:15px; background:var(--paper);}
  .opt input{accent-color:var(--navy-2);}
  .opt.is-correct{border-color:var(--success); background:var(--success-soft);}
  .opt.is-wrong{border-color:var(--danger); background:var(--danger-soft);}
  .opt.locked{cursor:not-allowed;}

  .subpart-label{font-weight:700; font-size:12.5px; color:var(--accent-text); text-transform:uppercase; letter-spacing:.03em; margin:14px 0 6px;}
  .or-divider{text-align:center; font-size:11px; font-weight:700; letter-spacing:.08em; color:var(--ink-soft); margin:8px 0;}

  .steps{display:flex; flex-direction:column; gap:10px;}
  .step-line{font-size:14.5px; line-height:1.9; background:var(--paper); border:1px dashed var(--rule); border-radius:10px; padding:9px 12px;}
  .step-line.resolved{opacity:.9;}
  .blank-input{font-family:'IBM Plex Mono',monospace; font-size:14px; border:1.5px solid var(--rule); border-radius:6px; padding:3px 8px; width:120px; background:var(--card); color:var(--ink); margin:0 2px;}
  .blank-input:focus{outline:none; border-color:var(--focus); box-shadow:0 0 0 3px var(--gold-soft);}
  .blank-input.is-correct{border-color:var(--success); background:var(--success-soft);}
  .blank-input.is-wrong{border-color:var(--danger); background:var(--danger-soft);}
  .blank-input[disabled]{opacity:.85;}
  .reveal-note{font-size:12px; color:var(--danger); padding-left:2px; margin-top:-2px;}

  .feedback{font-size:13.5px; padding:10px 12px; border-radius:9px; margin-top:14px; display:none;}
  .feedback.show{display:block;}
  .feedback.ok{background:var(--success-soft); color:var(--success);}
  .feedback.retry{background:var(--gold-soft); color:var(--retry-text);}
  .feedback.reveal{background:var(--danger-soft); color:var(--danger);}
  .feedback.err{background:var(--danger-soft); color:var(--danger);}
  .attempts-dots{display:inline-flex; gap:4px; margin-left:2px;}
  .attempts-dots span{width:6px; height:6px; border-radius:50%; background:var(--ink-soft); opacity:.3; display:inline-block;}
  .attempts-dots span.used{opacity:1; background:var(--danger);}

  .ar-box{background:var(--paper-2); border-radius:10px; padding:10px 12px; margin-bottom:12px; font-size:13px; color:var(--ink-soft);}

  .navbar{
    position:fixed; left:0; right:0; bottom:0; z-index:30; background:var(--paper);
    border-top:1px solid var(--rule); padding:10px 16px calc(10px + env(safe-area-inset-bottom,0px));
  }
  .navbar-inner{max-width:900px; margin:0 auto; display:flex; gap:8px; flex-wrap:wrap; align-items:center;}
  .btn{font-family:inherit; font-size:13.5px; font-weight:700; padding:10px 14px; border-radius:9px; border:1.5px solid var(--rule); background:var(--card); color:var(--ink); cursor:pointer;}
  .btn:hover{border-color:var(--navy-2);}
  .btn:disabled{opacity:.4; cursor:not-allowed;}
  .btn-primary{background:var(--navy-2); color:#fff; border-color:var(--navy-2);}
  .navbar .spacer{flex:1;}

  .fab{position:fixed; right:16px; bottom:calc(74px + env(safe-area-inset-bottom,0px)); background:var(--gold); color:var(--navy); border:none; border-radius:999px; padding:11px 16px; font-family:inherit; font-weight:700; font-size:13px; display:flex; align-items:center; gap:7px; cursor:pointer; box-shadow:0 6px 16px rgba(0,0,0,.18); z-index:35;}
  .fab-badge{background:rgba(255,255,255,.55); border-radius:99px; padding:1px 7px; font-size:11px;}

  .overlay{position:fixed; inset:0; background:rgba(20,18,14,.45); z-index:50; display:none; align-items:flex-end; justify-content:center;}
  .overlay.show{display:flex;}
  .palette{background:var(--card); width:min(480px,100%); max-height:78vh; overflow-y:auto; border-radius:18px 18px 0 0; padding:18px 18px calc(18px + env(safe-area-inset-bottom,0px)); border:1px solid var(--rule); border-bottom:none;}
  @media (min-width:640px){ .overlay{align-items:center;} .palette{border-radius:18px; border-bottom:1px solid var(--rule); max-height:74vh;} }
  .palette-head{display:flex; align-items:center; justify-content:space-between; margin-bottom:6px;}
  .palette-head h2{font-size:16px;}
  .palette-close{background:none; border:none; font-size:20px; color:var(--ink-soft); cursor:pointer; padding:4px;}
  .palette-legend{display:flex; gap:12px; flex-wrap:wrap; font-size:11px; color:var(--ink-soft); margin:10px 0 14px;}
  .palette-legend span{display:inline-flex; align-items:center; gap:5px;}
  .dot{width:9px; height:9px; border-radius:50%; display:inline-block;}
  .dot.correct{background:var(--success);} .dot.revealed{background:var(--danger);}
  .dot.skipped{background:var(--gold);} .dot.locked{background:var(--locked);}
  .dot.current{background:var(--navy-2);}
  .chip-grid{display:grid; grid-template-columns:repeat(auto-fill,minmax(48px,1fr)); gap:8px;}
  .chip{border:1.5px solid var(--rule); border-radius:9px; padding:8px 4px; text-align:center; font-family:'IBM Plex Mono',monospace; font-size:12.5px; font-weight:600; cursor:pointer; background:var(--paper); color:var(--ink);}
  .chip[data-status="correct"]{border-color:var(--success); background:var(--success-soft); color:var(--success);}
  .chip[data-status="revealed"]{border-color:var(--danger); background:var(--danger-soft); color:var(--danger);}
  .chip[data-status="skipped"]{border-color:var(--gold); background:var(--gold-soft); color:var(--retry-text);}
  .chip[data-status="locked"]{border-color:var(--rule); color:var(--locked); cursor:not-allowed; background:var(--paper-2);}
  .chip[data-status="current"]{outline:2px solid var(--navy-2); outline-offset:1px;}

  .toast{position:fixed; left:50%; bottom:calc(140px + env(safe-area-inset-bottom,0px)); transform:translateX(-50%); background:var(--ink); color:var(--paper); padding:9px 16px; border-radius:99px; font-size:13px; opacity:0; pointer-events:none; transition:opacity .25s ease; z-index:60;}
  .toast.show{opacity:1;}

  .done-card{text-align:center; padding:36px 20px;}
  .done-card .big{font-size:38px; margin-bottom:6px;}
  .score-pills{display:flex; gap:10px; justify-content:center; flex-wrap:wrap; margin:16px 0;}
  .score-pill{padding:8px 16px; border-radius:99px; font-size:13px; font-weight:700;}

  footer.brandfoot{max-width:900px; margin:14px auto 0; padding:0 16px calc(110px + env(safe-area-inset-bottom,0px)); text-align:center; font-size:12px; color:var(--ink-soft);}

  .mode-pill{font-family:inherit; font-size:12.5px; font-weight:700; color:var(--navy); background:var(--gold); border:none; border-radius:99px; padding:6px 14px; cursor:pointer; margin-top:12px; display:inline-flex; align-items:center; gap:6px;}
  .mode-pick{display:flex; flex-direction:column; gap:14px; padding:8px 0 24px;}
  .mode-card{background:var(--card); border:1.5px solid var(--rule); border-radius:16px; padding:22px; cursor:pointer; text-align:left;}
  .mode-card:hover{border-color:var(--navy-2);}
  .mode-card .mode-icon{font-size:26px; margin-bottom:8px;}
  .mode-card h3{font-size:18px; margin-bottom:6px;}
  .mode-card p{font-size:13.5px; color:var(--ink-soft); line-height:1.5; margin:0;}
  .quiz-hint{font-size:12.5px; color:var(--ink-soft); background:var(--paper-2); border-radius:9px; padding:8px 12px; margin-bottom:14px;}
  .review-row{border:1px solid var(--rule); border-radius:10px; padding:11px 13px; margin-bottom:10px;}
  .review-tag{font-size:11.5px; font-weight:700; margin-bottom:4px; display:block;}
  .review-tag.ok{color:var(--success);} .review-tag.bad{color:var(--danger);} .review-tag.na{color:var(--ink-soft);}
  .review-q{font-size:13.5px; margin-bottom:6px; color:var(--ink-soft);}
  .review-ans{font-size:13px; margin-bottom:2px;}

  .who-row{max-width:900px; margin:12px auto 0; display:flex; flex-wrap:wrap; gap:8px; align-items:center;}
  .who-row .mode-pill{margin-top:0;}
  .who{display:inline-flex; flex-wrap:wrap; align-items:center; gap:6px; font-size:12.5px; color:#CFD7EA;}
  .who b{color:#F4EFDF;}
  .who button{font-family:inherit; font-size:12px; font-weight:700; color:#F4EFDF; background:rgba(255,255,255,.12); border:1px solid rgba(255,255,255,.22); border-radius:99px; padding:5px 11px; cursor:pointer;}
  .who button:hover{background:rgba(255,255,255,.2);}
  .login-card{max-width:460px; margin:8px auto 0; background:var(--card); border:1px solid var(--rule); border-radius:16px; padding:22px;}
  .login-card h2{font-size:21px; margin-bottom:4px;}
  .login-card p.lead{font-size:13.5px; color:var(--ink-soft); margin:0 0 16px; line-height:1.5;}
  .fld{display:flex; flex-direction:column; gap:5px; margin-bottom:12px;}
  .fld label{font-size:12px; font-weight:700; letter-spacing:.04em; text-transform:uppercase; color:var(--ink-soft);}
  .fld input{font-family:inherit; font-size:15px; padding:10px 12px; border:1.5px solid var(--rule); border-radius:9px; background:var(--paper); color:var(--ink);}
  .fld input:focus{outline:none; border-color:var(--focus); box-shadow:0 0 0 3px var(--gold-soft);}
  .fld-row{display:grid; grid-template-columns:1fr 1fr; gap:10px;}
  .login-err{font-size:13px; color:var(--danger); background:var(--danger-soft); border-radius:8px; padding:8px 10px; margin-bottom:12px;}
  .login-note{font-size:12px; color:var(--ink-soft); margin-top:12px; line-height:1.5;}
  .known{margin:0 0 16px; display:flex; flex-direction:column; gap:6px;}
  .known-label{font-size:12px; font-weight:700; letter-spacing:.04em; text-transform:uppercase; color:var(--ink-soft);}
  .known-btn{display:flex; justify-content:space-between; align-items:center; gap:10px; text-align:left; font-family:inherit; font-size:14.5px; padding:10px 12px; border:1.5px solid var(--rule); border-radius:10px; background:var(--paper); color:var(--ink); cursor:pointer;}
  .known-btn:hover{border-color:var(--navy-2);}
  .known-btn small{font-size:12px; color:var(--ink-soft);}
  .rec-card{background:var(--card); border:1px solid var(--rule); border-radius:14px; padding:18px; margin-bottom:14px;}
  .rec-card h2{font-size:19px; margin-bottom:10px;}
  .rec-card h3{font-size:15px; margin:4px 0 8px;}
  .rec-table-wrap{overflow-x:auto;}
  .rec-table{width:100%; border-collapse:collapse; font-size:13.5px; font-variant-numeric:tabular-nums;}
  .rec-table th{text-align:left; font-size:11.5px; text-transform:uppercase; letter-spacing:.04em; color:var(--ink-soft); padding:6px 8px; border-bottom:1px solid var(--rule); white-space:nowrap;}
  .rec-table td{padding:8px; border-bottom:1px solid var(--rule); white-space:nowrap;}
  .rec-bar{display:inline-block; width:70px; height:6px; border-radius:99px; background:var(--rule); overflow:hidden; vertical-align:middle; margin-right:6px;}
  .rec-bar i{display:block; height:100%; background:var(--success);}
  .rec-empty{font-size:13.5px; color:var(--ink-soft);}
  .sec-sub{max-width:900px; margin:0 auto; padding:10px 16px 0; font-size:12.5px; font-weight:700; color:var(--accent-text); letter-spacing:.02em;}
  .opt{flex-wrap:wrap;}
  .opt-l{font-family:'IBM Plex Mono',monospace; font-size:13px; font-weight:600; color:var(--ink-soft);}
  .opt-t{flex:1; min-width:0;}
  .opt.is-chosen:not(.is-correct):not(.is-wrong){border-color:var(--navy-2); background:var(--gold-soft);}
  .opt-tag{font-size:11px; font-weight:700; padding:2px 8px; border-radius:99px; background:var(--card); border:1px solid currentColor; white-space:nowrap;}
  .opt.is-correct .opt-tag{color:var(--success);} .opt.is-wrong .opt-tag{color:var(--danger);} .opt.is-chosen:not(.is-correct):not(.is-wrong) .opt-tag{color:var(--accent-text);}
  .chosen{font-size:13.5px; margin-top:10px; padding:8px 12px; border-radius:9px;}
  .chosen.ok{background:var(--success-soft); color:var(--success);} .chosen.bad{background:var(--danger-soft); color:var(--danger);}
  .chosen + .chosen{margin-top:6px;}
  .solution{margin-top:14px; border:1px solid var(--rule); border-left:4px solid var(--gold); background:var(--paper-2); border-radius:10px; padding:12px 14px;}
  .sol-h{font-family:'Fraunces',Georgia,serif; font-weight:700; font-size:14px; color:var(--accent-text); margin-bottom:6px;}
  .sol-line{font-size:14.5px; line-height:1.7;}
  .rev-sol summary{cursor:pointer; font-size:12.5px; font-weight:700; color:var(--accent-text); margin-top:6px;}
  .rev-sol .solution{margin-top:8px;}
  .chapter-credit{max-width:900px; margin:4px auto 0; font-size:12px; color:#CFD7EA;}
  footer.brandfoot a{color:inherit;}
  .blank-input.wide{width:260px; max-width:100%; font-family:'Source Sans 3',sans-serif;}
  .blank-input.expr{width:170px; max-width:100%;}
  /*fix-layout*/ .cp-fill,.sp-fill{width:0;} .fld{min-width:0;} .fld input{width:100%; min-width:0; box-sizing:border-box;}
  .fig{margin:6px 0 10px; display:flex; justify-content:center;}
  .figsvg{width:100%; max-width:340px; height:auto; overflow:visible;}
  .figsvg .ln,.figsvg .arm{stroke:var(--ink); stroke-width:1.6; fill:none;}
  .figsvg .arm{stroke:var(--accent-text); stroke-width:2;}
  .figsvg .pt{fill:var(--ink);}
  .figsvg .lb{fill:var(--ink); font:600 13px 'Source Sans 3',sans-serif;}
  .figsvg .al{fill:var(--accent-text); font:700 12px 'Source Sans 3',sans-serif;}
  .figsvg .wg{fill:var(--gold-soft); stroke:var(--gold); stroke-width:1.2;}
  .figsvg .wg2{fill:rgba(199,154,62,.35); stroke:var(--gold); stroke-width:1.2;}
  .figsvg .ra{fill:none; stroke:var(--ink); stroke-width:1.2;}
  .figsvg .ahd{fill:var(--ink);}
  .figsvg .pr{fill:var(--paper-2); stroke:var(--ink-soft); stroke-width:1.2;}
  .figsvg .tk{stroke:var(--ink-soft); stroke-width:.8;}
  .figsvg .po{fill:var(--ink); font:600 8.5px 'IBM Plex Mono',monospace;}
  .figsvg .pi{fill:var(--danger); font:600 7.5px 'IBM Plex Mono',monospace;}
  .figsvg .sh{fill:var(--gold-soft); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .sh2{fill:rgba(199,154,62,.38); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .sh3{fill:rgba(199,154,62,.22); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .none{fill:none;}
  .figsvg .hid{stroke-dasharray:5 4; fill:none;}
  .figsvg .tick{stroke:var(--ink); stroke-width:1.4; fill:none;}
  .figsvg .shd{fill:var(--accent-text); fill-opacity:.55;}
  .figsvg .cell{fill:var(--card); stroke:var(--ink); stroke-width:1.1;}
  .figsvg .dr{fill:var(--danger);} .figsvg .dw{fill:var(--card); stroke:var(--ink); stroke-width:1.2;}
  .figsvg .dotfill{fill:var(--danger);}
  .tt{border-collapse:collapse; font-size:13.5px; margin:4px auto; font-variant-numeric:tabular-nums;} .tt th,.tt td{border:1px solid var(--rule); padding:4px 9px; text-align:left;} .tt th{background:var(--paper-2); font-weight:700;} .ttw{overflow-x:auto; max-width:100%;}
  .fq{display:inline-flex; flex-direction:column; vertical-align:middle; text-align:center; font-size:.82em; line-height:1.12; margin:0 2px;}
  .fq>span:first-child{border-bottom:1.5px solid currentColor; padding:0 2px;}
  .fq>span:last-child{padding:0 2px;}
  .mx{white-space:nowrap;}
  .blank-input.fr{width:110px;}
  @media (prefers-reduced-motion:reduce){ *{transition:none !important;} }
.datline{display:block;margin-top:8px;padding:8px 10px;border-radius:8px;background:var(--paper-2);font:500 14px/1.7 'IBM Plex Mono',monospace;word-spacing:2px;overflow-wrap:anywhere;}

  .theory{display:flex;flex-direction:column;gap:16px;padding-bottom:40px;}
  .hub{display:grid;grid-template-columns:1fr;gap:12px;}
  @media (min-width:640px){ .hub{grid-template-columns:repeat(3,1fr);} }
  .hub-card{background:var(--card);border:1px solid var(--rule);border-radius:14px;padding:16px;display:flex;flex-direction:column;gap:8px;}
  .hub-card h3{font-family:'Fraunces',serif;font-size:18px;margin:0;color:var(--accent-text);}
  .hub-card p{margin:0;font-size:14px;color:var(--ink-soft);line-height:1.5;}
  .hub-btns{display:flex;flex-wrap:wrap;gap:8px;margin-top:auto;}
  .hub-btn{min-height:40px;border:1.5px solid var(--rule);background:var(--paper-2);color:var(--ink);border-radius:10px;padding:8px 12px;font:600 14px 'Source Sans 3',sans-serif;cursor:pointer;text-align:left;}
  .hub-btn:hover{border-color:var(--gold);}
  .hub-btn.primary{background:var(--navy);color:#F4EFDF;border-color:var(--navy);}
  .note{background:var(--card);border:1px solid var(--rule);border-radius:14px;padding:18px;scroll-margin-top:120px;}
  .note h2{font-family:'Fraunces',serif;font-size:22px;margin:0 0 4px;color:var(--ink);}
  .note .lt{font-size:13.5px;color:var(--ink-soft);margin:0 0 12px;}
  .note .lt b{color:var(--accent-text);}
  .note h4{font:700 15px 'Source Sans 3',sans-serif;margin:16px 0 6px;color:var(--accent-text);}
  .note p,.note li{font-size:15.5px;line-height:1.6;}
  .note ul{padding-left:20px;margin:6px 0;}
  .keybox{background:var(--gold-soft);border-left:4px solid var(--gold);border-radius:8px;padding:10px 12px;margin:10px 0;font-size:15px;line-height:1.6;}
  .keybox b{color:var(--ink);}
  .ex{background:var(--paper-2);border-radius:10px;padding:12px;margin:10px 0;}
  .ex .exh{font-family:'Fraunces',serif;font-weight:700;color:var(--accent-text);margin-bottom:4px;}
  .ex .exl{font-size:15px;line-height:1.7;}
  .ttab{width:100%;border-collapse:collapse;font-size:14.5px;margin:8px 0;}
  .ttab th,.ttab td{border:1px solid var(--rule);padding:7px 8px;text-align:left;vertical-align:top;}
  .ttab th{background:var(--paper-2);}
  .tscroll{overflow-x:auto;}
  .mono{font-family:'IBM Plex Mono',monospace;font-size:.92em;}
  @media (max-width:480px){ .ttab{font-size:13.5px;} .ttab th,.ttab td{padding:6px;} }
  .note .figsvg{max-width:100%;height:auto;display:block;margin:8px auto;}


  .rep-top{display:flex;flex-wrap:wrap;gap:18px;align-items:center;justify-content:center;margin-top:8px;}
  .rep-legend{flex:1;min-width:220px;display:flex;flex-direction:column;gap:8px;}
  .rep-cap{font:700 13px 'Source Sans 3',sans-serif;color:var(--ink-soft);text-transform:uppercase;letter-spacing:.05em;}
  .rep-li{display:flex;align-items:center;gap:6px;font-size:15px;}
  .rep-n{margin-left:auto;white-space:nowrap;padding-left:8px;font-family:'IBM Plex Mono',monospace;font-weight:600;}
  .sw{display:inline-block;width:12px;height:12px;border-radius:3px;flex:none;}
  .rep-grid{display:grid;grid-template-columns:1fr;gap:12px;}
  @media (min-width:640px){ .rep-grid{grid-template-columns:1fr 1fr;} }
  .rep-card{background:var(--card);border:1px solid var(--rule);border-radius:14px;padding:14px;display:flex;flex-direction:column;gap:10px;}
  .rep-h{display:flex;align-items:center;gap:8px;font:700 16px 'Source Sans 3',sans-serif;}
  .crit{display:inline-grid;place-items:center;width:28px;height:28px;border-radius:50%;color:var(--card);font:700 15px Fraunces,serif;flex:none;}
  .rep-row{display:flex;gap:14px;align-items:center;}
  .rep-stats{display:flex;flex-direction:column;gap:5px;font-size:14.5px;}
  .rep-stats div{display:flex;align-items:center;gap:6px;}
  .rep-lvl{margin-top:4px;color:var(--accent-text);} .rep-lvl span{color:var(--ink-soft);font-size:13px;}
  .rep-note{font-size:13px;color:var(--ink-soft);}


  .skip-chips{display:flex;flex-wrap:wrap;gap:8px;justify-content:center;margin:12px 0;}
  .skip-chips .chip{min-width:48px;min-height:40px;cursor:pointer;border:1.5px solid var(--gold);background:var(--gold-soft);color:var(--retry-text);border-radius:10px;font:600 14px 'IBM Plex Mono',monospace;}
  .skip-btns{display:flex;flex-wrap:wrap;gap:10px;justify-content:center;margin-top:12px;}


  .kb-toggle{border:none;background:transparent;font-size:15px;cursor:pointer;padding:0 2px;vertical-align:middle;opacity:.7;}
  .vkb{position:fixed;left:0;right:0;bottom:0;z-index:80;background:var(--paper-2);border-top:1px solid var(--rule);box-shadow:0 -6px 20px rgba(0,0,0,.12);padding:6px 6px 8px;display:none;}
  .vkb.show{display:block;}
  .vkb-top{display:flex;justify-content:space-between;align-items:center;max-width:640px;margin:0 auto 4px;font:600 12px 'Source Sans 3',sans-serif;color:var(--ink-soft);}
  .vkb-link{border:none;background:none;color:var(--accent-text);font:600 12px 'Source Sans 3',sans-serif;cursor:pointer;text-decoration:underline;}
  .vkb-row{display:flex;gap:5px;max-width:640px;margin:0 auto 5px;}
  .vkb-k{flex:1;min-height:42px;border:1px solid var(--rule);border-radius:8px;background:var(--card);color:var(--ink);font:600 17px 'IBM Plex Mono',monospace;cursor:pointer;padding:0;}
  .vkb-k.fn{font:600 13px 'Source Sans 3',sans-serif;background:var(--gold-soft);}
  .vkb-k.done{background:var(--navy);color:#F4EFDF;border-color:var(--navy);}
  .vkb-k:active{transform:scale(.96);}
  body.kb-open .wrap{padding-bottom:360px;}
  body.kb-open .fab{display:none;}
  .tool-bar{display:flex;gap:8px;flex-wrap:wrap;margin:-4px 0 10px;}
  .tool-btn{min-height:36px;border:1.5px solid var(--gold);background:var(--gold-soft);color:var(--ink);border-radius:18px;padding:4px 12px;font:600 13.5px 'Source Sans 3',sans-serif;cursor:pointer;}
  .tool-panel{position:fixed;z-index:85;background:var(--card);border:1px solid var(--rule);border-radius:14px;box-shadow:0 10px 30px rgba(0,0,0,.25);display:none;}
  .tool-panel.show{display:block;}
  .tp-head{display:flex;align-items:center;gap:8px;padding:8px 10px;border-bottom:1px solid var(--rule);font:600 14px 'Source Sans 3',sans-serif;}
  .tp-note{font-size:12px;color:var(--ink-soft);font-weight:500;}
  .tp-x{margin-left:auto;border:1px solid var(--rule);background:var(--paper-2);color:var(--ink);border-radius:8px;min-height:32px;padding:2px 10px;cursor:pointer;font:600 13px 'Source Sans 3',sans-serif;}
  .tp-x + .tp-x{margin-left:0;}
  .calc{right:12px;bottom:84px;width:min(330px,calc(100vw - 24px));}
  body.calc-open .wrap{padding-bottom:440px;}
  body.calc-open .fab{display:none;}
  @media (max-width:640px){ .calc{left:6px;right:6px;width:auto;} .calc-keys button{min-height:36px;} }
  .calc-disp{padding:8px 12px;text-align:right;background:var(--paper-2);}
  .calc-expr{font:500 13px 'IBM Plex Mono',monospace;color:var(--ink-soft);min-height:18px;word-break:break-all;}
  .calc-res{font:600 24px 'IBM Plex Mono',monospace;color:var(--ink);word-break:break-all;}
  .calc-keys{display:grid;grid-template-columns:repeat(6,1fr);gap:5px;padding:8px;}
  .calc-keys button{min-height:40px;border:1px solid var(--rule);border-radius:8px;background:var(--card);color:var(--ink);font:600 14px 'IBM Plex Mono',monospace;cursor:pointer;padding:0;}
  .calc-keys button.fn{background:var(--gold-soft);font-family:'Source Sans 3',sans-serif;font-size:13px;}
  .calc-keys button.eq{grid-column:span 2;background:var(--navy);color:#F4EFDF;border-color:var(--navy);}
  .desmos{left:50%;top:50%;transform:translate(-50%,-50%);width:min(760px,calc(100vw - 16px));height:min(560px,calc(100vh - 90px));flex-direction:column;}
  .desmos.show{display:flex;}
  #desmosBox{flex:1;min-height:0;border-radius:0 0 14px 14px;overflow:hidden;}
  .desmos-msg{padding:24px;text-align:center;color:var(--ink-soft);}
  .chip[data-status="skipped"]{cursor:pointer;}
  .chip[data-status="answered"]{border-color:var(--accent-text);color:var(--accent-text);}


  button.crest-home{border:none;padding:0;position:relative;cursor:pointer;transition:transform .15s ease;}
  button.crest-home:hover,button.crest-home:focus-visible{transform:scale(1.06);outline:2px solid var(--gold);outline-offset:2px;}
  .crest-h{position:absolute;right:-7px;bottom:-7px;width:18px;height:18px;border-radius:50%;background:#F4EFDF;color:var(--navy);font:700 12px/18px 'Source Sans 3',sans-serif;text-align:center;box-shadow:0 1px 3px rgba(0,0,0,.3);}
  .brand .brand-row{position:relative;}
  .bmasw{position:absolute;left:50%;top:50%;transform:translate(-50%,-50%);display:flex;flex-shrink:0;white-space:nowrap;align-items:center;gap:6px;background:rgba(255,255,255,.12);border:1px solid rgba(255,255,255,.25);border-radius:99px;padding:5px 14px;color:#F4EFDF;}
  .bmasw-ic{font-size:16px;} .bmasw-t{font:600 20px 'IBM Plex Mono',monospace;letter-spacing:.02em;min-width:62px;text-align:center;}
  .bmasw-b{border:none;background:rgba(255,255,255,.18);color:#F4EFDF;border-radius:50%;width:30px;height:30px;cursor:pointer;font-size:13px;}
  .bmasw.off{display:none;}
  @media (max-width:560px){ .bmasw{position:static;transform:none;margin-left:auto;padding:4px 5px 4px 8px;gap:4px;} .bmasw-ic{display:none;} .bmasw-t{font-size:16px;min-width:48px;} .bmasw-b{width:26px;height:26px;} .brand .series-name{font-size:15px;} .brand .brand-name{font-size:10.5px;} .brand .brand-row>div:not(.bmasw){min-width:0;} }
  .bmasw-done{font:600 15px 'IBM Plex Mono',monospace;color:var(--accent-text);margin:4px 0 8px;}
  .sp-fab{position:fixed;left:14px;bottom:84px;z-index:60;border:1.5px solid var(--navy-2);background:var(--card);color:var(--ink);border-radius:99px;padding:9px 14px;font:700 14px 'Source Sans 3',sans-serif;box-shadow:0 4px 14px rgba(0,0,0,.15);cursor:pointer;}
  .sp-fab.on{background:var(--navy);color:#F4EFDF;}
  body.kb-open .sp-fab{display:none;}
  .sp-canvas{position:absolute;z-index:55;display:none;touch-action:none;cursor:crosshair;}
  .sp-canvas.passive{pointer-events:none;cursor:default;}
  .sp-bar{position:fixed;top:8px;left:8px;right:8px;margin:0 auto;width:max-content;z-index:90;display:none;align-items:center;gap:6px;background:var(--card);border:1px solid var(--rule);border-radius:14px;padding:6px 8px;box-shadow:0 6px 20px rgba(0,0,0,.2);max-width:calc(100vw - 16px);flex-wrap:wrap;justify-content:center;}
  .sp-lbl{font:700 13px 'Source Sans 3',sans-serif;color:var(--ink-soft);margin-right:2px;}
  .sp-pen,.sp-tool{width:38px;height:38px;border-radius:10px;border:1.5px solid var(--rule);background:var(--paper);cursor:pointer;display:inline-flex;align-items:center;justify-content:center;font-size:17px;padding:0;color:var(--ink);}
  .sp-pen i{width:20px;height:20px;border-radius:50%;display:block;}
  .sp-pen.on,.sp-tool.on{border-color:var(--navy-2);box-shadow:0 0 0 3px var(--gold-soft);}
  @media (max-width:560px){ .sp-lbl{display:none;} .sp-pen,.sp-tool{width:34px;height:34px;} .sp-fab span{display:none;} }

  /* larger reading sizes */
  .chapter-eyebrow{font-size:13.5px;}
  .chapter-title{font-size:36px;line-height:1.15;}
  .chapter-sub{font-size:16.5px;}
  .tab-btn{font-size:15.5px;}
  .sec-sub{font-size:15px;}
  .qtext{font-size:19px;line-height:1.55;}
  .qnum{width:36px;height:36px;font-size:16px;}
  .opt{font-size:17.5px;padding:12px 14px;}
  .step-line{font-size:17.5px;line-height:2;}
  .blank-input{font-size:16px;}
  .sol-line{font-size:16.5px;}
  .feedback{font-size:15px;}
  .note h2{font-size:28px;}
  .note h4{font-size:19px;}
  .note p,.note li{font-size:17.5px;line-height:1.65;}
  .note .lt{font-size:15.5px;}
  .ex .exh{font-size:18px;} .ex .exl{font-size:16.5px;}
  .keybox{font-size:16.5px;}
  .ttab{font-size:15.5px;}
  .hub-card h3{font-size:21px;} .hub-card p{font-size:15.5px;} .hub-btn{font-size:15px;}
  @media (max-width:480px){ .chapter-title{font-size:30px;} .qtext{font-size:18px;} .opt,.step-line{font-size:16.5px;} .note h2{font-size:24px;} .note p,.note li{font-size:16.5px;} }
</style>
</head>
<body>
<header class="brand">
  <div class="brand-row">
    <div class="crest">BM</div>
    <div>
      <div class="brand-name">Brain &amp; Mind Academy</div>
      <div class="series-name">Sopaan <span style="font-weight:400;font-size:14px;color:#CFD7EA;">Practice Series</span></div>
    </div>
  </div>
  <div class="chapter-eyebrow">Class 8 Mathematics · Chapter 9</div>
  <div class="chapter-title">Linear Equations in One Variable</div>
  <div class="chapter-sub">Theory Notes · Practice by Learning Objective · Learning Assessment</div><div class="chapter-credit">Mixed multiple-choice and fill-in-the-blank practice · Chapter 9</div>
  <div class="chapter-progress">
    <div class="cp-track"><div class="cp-fill" id="cpFill"></div></div>
    <div class="cp-label" id="cpLabel">0% complete</div>
  </div>
  <div class="who-row"><button class="mode-pill" id="modePill" hidden>Choose a mode</button><span class="who" id="whoBar" hidden></span></div>
</header>

<nav class="tabbar"><div class="tabbar-inner" id="tabbar"></div></nav>
<div class="sec-sub" id="secSub"></div><div class="slide-progress"><div class="sp-track"><div class="sp-fill" id="spFill"></div></div><div class="sp-label" id="spLabel">Question 1 of 49</div></div>
<div class="wrap" id="wrap"></div>
<footer class="brandfoot">Brain &amp; Mind Academy · Sopaan Practice Series · Class 8 Mathematics · Chapter 9<br>Chapter follows the Class 8 mathematics syllabus (New Enjoying Mathematics, Class 8). Theory notes, questions, learning assessments and worked solutions are written by Brain &amp; Mind Academy.</footer>

<div class="navbar"><div class="navbar-inner" id="navbarInner"></div></div>
<button class="fab" id="paletteFab"><span>Questions</span><span class="fab-badge" id="fabBadge">0/49</span></button>

<div class="overlay" id="overlay">
  <div class="palette" role="dialog" aria-label="Question palette">
    <div class="palette-head"><h2 id="paletteTitle">Question palette</h2><button class="palette-close" id="paletteClose">&times;</button></div>
    <div class="palette-legend">
      <span><i class="dot current"></i>Current</span><span><i class="dot correct"></i>Correct</span>
      <span><i class="dot revealed"></i>Revealed</span><span><i class="dot skipped"></i>Skipped</span>
      <span><i class="dot locked"></i>Locked</span>
    </div>
    <div class="chip-grid" id="paletteBody"></div>
  </div>
</div>
<div class="toast" id="toast"></div>

<script>
(function(){
"use strict";

/* ================= audio ================= */
var audioCtx=null;
function ensureAudio(){ if(!audioCtx){ try{ audioCtx=new (window.AudioContext||window.webkitAudioContext)(); }catch(e){} } return audioCtx; }
function playTone(freqs,dur,type){
  var ctx=ensureAudio(); if(!ctx) return;
  try{
    var t0=ctx.currentTime;
    freqs.forEach(function(f,i){
      var o=ctx.createOscillator(), g=ctx.createGain();
      o.type=type||'sine'; o.frequency.value=f;
      var start=t0+i*dur;
      g.gain.setValueAtTime(0.0001,start);
      g.gain.exponentialRampToValueAtTime(0.16,start+0.02);
      g.gain.exponentialRampToValueAtTime(0.0001,start+dur);
      o.connect(g); g.connect(ctx.destination);
      o.start(start); o.stop(start+dur+0.02);
    });
  }catch(e){}
}
function playSuccess(){ playTone([523.25,659.25,783.99],0.11,'sine'); }
function playWrong(){ playTone([220,185],0.14,'square'); }
function playReveal(){ playTone([300,220],0.16,'triangle'); }

/* ================= helpers ================= */
function norm(s){
  return String(s===undefined||s===null?'':s).trim().toLowerCase().replace(/\s+/g,'')
    .replace(/[×∗*·]/g,'x').replace(/÷/g,'/').replace(/–|—|−/g,'-')
    .replace(/[²]/g,'^2').replace(/[³]/g,'^3').replace(/[⁴]/g,'^4').replace(/[⁵]/g,'^5')
    .replace(/[⁶]/g,'^6').replace(/[⁷]/g,'^7').replace(/[⁸]/g,'^8').replace(/[⁹]/g,'^9')
    .replace(/\^/g,'');
}
function parseNum(s){
  if(s===undefined||s===null) return null;
  var t=String(s).trim().replace(/,/g,'').replace(/[−–—]/g,'-').replace(/\s+/g,''); if(t==='') return null;
  var neg=false; if(t[0]==='-'){neg=true;t=t.slice(1);}
  var m=t.match(/^(\d+)\/(\d+)$/);
  if(m){ var v=parseInt(m[1],10)/parseInt(m[2],10); return neg?-v:v; }
  if(/^\d+(\.\d+)?$/.test(t)){ var v2=parseFloat(t); return neg?-v2:v2; }
  return null;
}
/* ---- expression checker: compares answers like (P-2w)/2 and P/2-w at random values ---- */
function exprPrep(s){
  return String(s).toLowerCase().replace(/\s+/g,'').replace(/^[a-z]\(x\)=/i,'').replace(/^y=/i,'').replace(/[×∗·]/g,'*').replace(/÷/g,'/').replace(/[−–—]/g,'-')
    .replace(/²/g,'^2').replace(/³/g,'^3').replace(/⁴/g,'^4').replace(/⁵/g,'^5').replace(/⁶/g,'^6').replace(/⁷/g,'^7').replace(/⁸/g,'^8').replace(/⁹/g,'^9').replace(/π/g,'#').replace(/pi/gi,'#').replace(/½/g,'(1/2)');
}
function exprCompile(src){
  var s=exprPrep(src), i=0, toks=[], absDepth=0;
  while(i<s.length){
    var ch=s[i];
    if(/[0-9.]/.test(ch)){ var j=i; while(j<s.length && /[0-9.]/.test(s[j])) j++; toks.push({k:'n',v:parseFloat(s.slice(i,j))}); i=j; continue; }
    if(/[a-zA-Z#]/.test(ch)){ toks.push({k:'v',v:ch}); i++; continue; }
    if(ch==='|'){ var pv=toks[toks.length-1]; var opn=(absDepth===0)||!pv||('+-*/^(['.indexOf(pv.k)>=0); if(opn){ absDepth++; toks.push({k:'['}); } else { absDepth--; toks.push({k:']'}); } i++; continue; }
    if('+-*/^()'.indexOf(ch)>=0){ toks.push({k:ch}); i++; continue; }
    return null;
  }
  var out=[];
  for(var t=0;t<toks.length;t++){
    var a=toks[t], b=out[out.length-1];
    if(b && (b.k==='n'||b.k==='v'||b.k===')'||b.k===']') && (a.k==='n'||a.k==='v'||a.k==='('||a.k==='[')) out.push({k:'&'});
    out.push(a);
  }
  var p=0;
  function peek(){ return out[p]; }
  function parseE(){ var n=parseT(); while(peek() && (peek().k==='+'||peek().k==='-')){ var o=out[p++].k, r=parseT(); n=(function(l,r,o){return function(e){ return o==='+'?l(e)+r(e):l(e)-r(e); };})(n,r,o); } return n; }
  function parseI(){ var n=parseU(); while(peek() && peek().k==='&'){ p++; var r=parseP(); n=(function(l,r){return function(e){ return l(e)*r(e); };})(n,r); } return n; }
  function parseT(){ var n=parseI(); while(peek() && (peek().k==='*'||peek().k==='/')){ var o=out[p++].k, r=parseI(); n=(function(l,r,o){return function(e){ return o==='*'?l(e)*r(e):l(e)/r(e); };})(n,r,o); } return n; }
  function parseU(){ if(peek() && peek().k==='-'){ p++; var u=parseU(); return function(e){ return -u(e); }; } if(peek() && peek().k==='+'){ p++; return parseU(); } return parseP(); }
  function parseP(){ var b=parseA(); if(peek() && peek().k==='^'){ p++; var x=parseU(); return function(e){ return Math.pow(b(e),x(e)); }; } return b; }
  function parseA(){
    var t=out[p++]; if(!t) throw 0;
    if(t.k==='n') return function(){ return t.v; };
    if(t.k==='v') return t.v==='#' ? function(){ return Math.PI; } : function(e){ return e[t.v]; };
    if(t.k==='('){ var n=parseE(); if(!peek()||peek().k!==')') throw 0; p++; return n; }
    if(t.k==='['){ var m=parseE(); if(!peek()||peek().k!==']') throw 0; p++; return function(e){ return Math.abs(m(e)); }; }
    throw 0;
  }
  try{ var f=parseE(); if(p!==out.length) return null; return f; }catch(e){ return null; }
}
function exprEqual(input,answer){
  var f=exprCompile(input), g=exprCompile(answer); if(!f||!g) return false;
  var hits=0;
  for(var trial=0;trial<8;trial++){
    var env={}; 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'.split('').forEach(function(c){ env[c]=1.3+Math.random()*4.1; });
    var x=f(env), y=g(env);
    if(!isFinite(x)||!isFinite(y)) continue;
    if(Math.abs(x-y)>1e-7*Math.max(1,Math.abs(x),Math.abs(y))) return false;
    hits++;
  }
  return hits>=3;
}
function wordsNorm(s){ return String(s||'').toLowerCase().replace(/\band\b/g,' ').replace(/[^a-z]/g,''); }
function listNorm(s){ return (String(s||'').replace(/[−–—]/g,'-').replace(/(\d) (?=\d{3}\b)/g,'$1').match(/-?\d+(\.\d+)?/g)||[]).join(','); }
function powNorm(s){ return String(s||'').toLowerCase().replace(/\s+/g,'').replace(/[×∗*·.]/g,'x').replace(/[⁰¹²³⁴⁵⁶⁷⁸⁹]+/g,function(m){ return '^'+m.split('').map(function(c){ return '⁰¹²³⁴⁵⁶⁷⁸⁹'.indexOf(c); }).join(''); }).replace(/\^1(?!\d)/g,''); }
function fr(s){ return String(s).replace(/\{(\d+) (\d+)\/(\d+)\}/g,'<span class="mx">$1<span class="fq"><span>$2</span><span>$3</span></span></span>').replace(/\{(\d+)\/(\d+)\}/g,'<span class="fq"><span>$1</span><span>$2</span></span>'); }
function gcdI(a,b){ a=Math.abs(a); b=Math.abs(b); while(b){ var t=a%b; a=b; b=t; } return a; }
function fracParse(s){ s=String(s===undefined||s===null?'':s).trim().replace(/[\u2044\u2215\u00f7]/g,'/').replace(/\s+/g,' ').replace(/\s*\/\s*/g,'/'); var m;
  if((m=s.match(/^(-?\d+)$/))) return {v:+m[1],form:'int',n:+m[1],d:1};
  if((m=s.match(/^(-?\d+)\/(\d+)$/))){ if(+m[2]===0) return null; return {v:m[1]/m[2],form:'frac',n:+m[1],d:+m[2]}; }
  if((m=s.match(/^(-?)(\d+)(?: |\+)(\d+)\/(\d+)$/))){ if(+m[4]===0) return null; var sg=m[1]?-1:1; return {v:sg*(+m[2]+m[3]/m[4]),form:'mixed',w:sg*m[2],n:+m[3],d:+m[4]}; }
  if((m=s.match(/^-?\d*\.\d+$/))) return {v:parseFloat(s),form:'dec'};
  return null; }
function fracOK(mode,input,answer){
  if(mode==='flist'){ var A=String(input).split(/[,;]/).map(function(x){return x.trim();}).filter(Boolean), K=String(answer).split(/[,;]/).map(function(x){return x.trim();});
    if(A.length!==K.length) return false; return A.every(function(x,i){ var a=fracParse(x), k=fracParse(K[i]); return a&&k&&Math.abs(a.v-k.v)<1e-9; }); }
  var a=fracParse(input), k=fracParse(answer); if(!a||!k) return false;
  var same=Math.abs(a.v-k.v)<1e-9; if(!same) return false;
  if(mode==='fv') return true;
  if(mode==='dec') return a.form==='dec'||a.form==='int';
  if(mode==='fe') return (a.form==='frac'&&k.form==='frac'&&a.n===k.n&&a.d===k.d)||(a.form==='int'&&k.form==='int');
  if(mode==='fi') return a.form==='frac'||(a.form==='int'&&k.form==='int');
  if(mode==='fl') return a.form==='int'||(a.form==='frac'&&gcdI(a.n,a.d)===1)||(a.form==='mixed'&&a.n<a.d&&gcdI(a.n,a.d)===1);
  if(mode==='fm') return a.form==='int'||(a.form==='mixed'&&a.n>0&&a.n<a.d&&gcdI(a.n,a.d)===1);
  return false; }
function answerMatches(input,answer,accept,expr){
  if(expr==='dec'||expr==='fv'||expr==='fe'||expr==='fl'||expr==='fm'||expr==='fi'||expr==='flist'){ if(input===undefined||input===null||String(input).trim()==='') return false; return fracOK(expr,input,answer); }
  if(input===undefined||input===null||String(input).trim()==='') return false;
  if(expr==='words'){ return [answer].concat(accept||[]).some(function(a){ if(/\d/.test(a)) return norm(a)===norm(input); var w=wordsNorm(a); return w!=='' && w===wordsNorm(input); }); }
  if(expr==='list'){ return [answer].concat(accept||[]).some(function(a){ return listNorm(a)===listNorm(input); }); }
  if(expr==='pow'){ return [answer].concat(accept||[]).some(function(a){ return powNorm(a)===powNorm(input); }); }
  if(expr==='time'){ var tn=function(x){ var t=String(x).toLowerCase().replace(/[\s.]/g,'').replace(/[:h]/g,''); if(/^\d{3}(am|pm)?$/.test(t)) t='0'+t; return t; }; return [answer].concat(accept||[]).some(function(a){ return tn(a)===tn(input); }); }
  if(expr==='glist'){ var gn=function(x){ return String(x).toUpperCase().split(/[\s,;]+/).filter(Boolean).sort().join(','); }; return [answer].concat(accept||[]).some(function(a){ return gn(a)===gn(input); }); }
  if(expr==='coord'){ var cn=function(x){ return String(x).replace(/[\u2212\u2013\u2014]/g,'-').replace(/[\s()\[\]]/g,''); }; return [answer].concat(accept||[]).some(function(a){ return cn(a)===cn(input); }); }
  if(expr==='dlist'){ var dn=function(x){ return (String(x).replace(/[−–—]/g,'-').match(/-?\d*\.?\d+/g)||[]).map(Number).join(','); }; return [answer].concat(accept||[]).some(function(a){ return dn(a)===dn(input); }); }
  if(expr==='set'){ var sn=function(x){ return (String(x).match(/-?\d+/g)||[]).map(Number).sort(function(a,b){return a-b;}).join(','); }; return [answer].concat(accept||[]).some(function(a){ return sn(a)===sn(input); }); }
  if(expr==='primes'){ var pn=function(x){ var t=powNorm(x).replace(/[^0-9x^]/g,''); var out=[]; t.split('x').forEach(function(tok){ if(!tok) return; var m=tok.split('^'); var b=+m[0], e=m[1]?+m[1]:1; for(var i=0;i<e;i++) out.push(b); }); return out.sort(function(a,b){return a-b;}).join(','); }; return [answer].concat(accept||[]).some(function(a){ return pn(a)===pn(input); }); }
  if(expr==='angle'){ var an=function(x){ return String(x).toUpperCase().replace(/[^A-Z]/g,''); }; var k=an(answer), v=an(input); return v===k || v===k.split('').reverse().join(''); }
  if(expr==='trans'){ var tv=function(x){ var s=String(x).toLowerCase().replace(/[−–—]/g,'-').replace(/\b(units?|squares?|and|then|steps?|to|the|a)\b/g,' ').replace(/[,;.]/g,' '); var re=/(\d+)\s*(right|left|up|down|r|l|u|d)\b/g, m, dx=0, dy=0, n=0; while((m=re.exec(s))){ var v=+m[1], d=m[2][0]; if(d==='r')dx+=v; else if(d==='l')dx-=v; else if(d==='u')dy+=v; else dy-=v; n++; } if(!n||s.replace(re,'').replace(/\s+/g,'')!=='') return null; return dx+','+dy; }; var ti=tv(input); return ti!==null && [answer].concat(accept||[]).some(function(a){ return tv(a)===ti; }); }
  if(expr==='rot'){ var rv=function(x){ var s=String(x).toLowerCase().replace(/quarter[\s-]*turn/g,'90').replace(/half[\s-]*turn/g,'180').replace(/three[\s-]*quarter[\s-]*turn/g,'270'); var m=s.match(/\b(90|180|270)\b/); if(!m) return null; var a=+m[1]; if(a===180) return '180'; var dir=/anti|counter|acw|ccw/.test(s)?-1:(/clockwise|\bcw\b/.test(s)?1:0); if(!dir) return null; return String(((a*dir)%360+360)%360); }; var ri=rv(input); return ri!==null && ri===rv(answer); }
  if(expr==='expanded'){ var f=function(x){ return String(x).replace(/\s+/g,'').replace(/,/g,''); }; return [answer].concat(accept||[]).some(function(a){ return f(a)===f(input); }); }
  if(expr===true && input!==undefined && input!==null && String(input).trim()!==''){
    if(exprEqual(input,answer)) return true;
    var alt=String(input).replace(/\/\s*(\d+(?:\.\d+)?)\s*([a-zA-Z(])/g,'/$1*$2'); if(alt!==String(input) && exprEqual(alt,answer)) return true;
    return (accept||[]).some(function(a){ return exprEqual(input,a); });
  }
  if(input===undefined||input===null||String(input).trim()==='') return false;
  var n1=parseNum(input), n2=parseNum(answer);
  if(n1!==null && n2!==null){ if(Math.abs(n1-n2)<1e-3) return true; return (accept||[]).some(function(a){ var n3=parseNum(a); return n3!==null && Math.abs(n1-n3)<1e-3; }); }
  var cands=[answer].concat(accept||[]); var ni=norm(input);
  for(var i=0;i<cands.length;i++){ if(norm(cands[i])===ni) return true; }
  return false;
}
function esc(s){ return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;'); }

/* ================= DATA ================= */
var AR_OPTIONS = ["Both A and R are true, and R is the correct explanation of A","Both A and R are true, but R is NOT the correct explanation of A","A is true but R is false","A is false but R is true"];
var THEORY = "<div class=\"hub\"><div class=\"hub-card\"><h3>📖 Theory notes</h3><p>Explained notes for every part of the chapter, following the book, with the rules for solving equations and solved examples.</p><div class=\"hub-btns\"><button class=\"hub-btn\" data-jump=\"n91\">9.1 notes</button><button class=\"hub-btn\" data-jump=\"n92\">9.2 notes</button><button class=\"hub-btn\" data-jump=\"n93\">9.3 notes</button><button class=\"hub-btn\" data-jump=\"n94\">9.4 notes</button><button class=\"hub-btn\" data-jump=\"n95\">9.5 notes</button><button class=\"hub-btn\" data-jump=\"n96\">9.6 notes</button></div></div><div class=\"hub-card\"><h3>🎯 Practice by learning objective</h3><p>Every Looking Back item, Example, Try This and Exercise question of the chapter, one sheet per objective, mixing multiple-choice and fill-in-the-blank questions. The bold tag shows where each question is in the book.</p><div class=\"hub-btns\"><button class=\"hub-btn\" data-go=\"s1\">9.1 · Solving simple linear equations</button><button class=\"hub-btn\" data-go=\"s2\">9.2 · Forming and solving equations</button><button class=\"hub-btn\" data-go=\"s3\">9.3 · Unknowns on both sides</button><button class=\"hub-btn\" data-go=\"s4\">9.4 · Brackets, fractions and products</button><button class=\"hub-btn\" data-go=\"s5\">9.5 · Numbers, ages, coins and mixtures</button><button class=\"hub-btn\" data-go=\"s6\">9.6 · Solutions, shapes, speed and digits</button></div></div><div class=\"hub-card\"><h3>📝 Learning assessment</h3><p>Four short assessments built from the Chapter Check-up, one per skill area. Take them in Quiz mode and open the report to see your results as pie charts.</p><div class=\"hub-btns\"><button class=\"hub-btn\" data-go=\"s7\">A · Knowing and understanding</button><button class=\"hub-btn\" data-go=\"s8\">B · Investigating patterns</button><button class=\"hub-btn\" data-go=\"s9\">C · Communicating</button><button class=\"hub-btn\" data-go=\"s10\">D · Applying mathematics in real-life contexts</button><button class=\"hub-btn primary\" data-go=\"report\">📊 View my report</button></div></div></div><section class=\"note\" id=\"nintro\"><h2>About this chapter</h2><p>An <b>equation</b> is a statement that two expressions are equal, such as 2x + 3 = 9. It is a <b>linear equation in one variable</b> when it has only one unknown and the highest power of that unknown is 1. The value of the unknown that makes both sides equal is the <b>solution</b> or <b>root</b> of the equation.</p><p>The practice sheets contain <b>all</b> the questions of the chapter in book order. Each question starts with a tag such as <b>Example 7</b>, <b>Try This</b>, <b>Ex 9A · Q2(c)</b> or <b>Check-up · Q5</b>.</p><div class=\"tscroll\"><table class=\"ttab\"><tr><th>Assessment</th><th>Skill area</th><th>What it checks</th></tr><tr><td>A</td><td>Knowing and understanding</td><td>Solving equations correctly.</td></tr><tr><td>B</td><td>Investigating patterns</td><td>Number machines and patterns written as expressions.</td></tr><tr><td>C</td><td>Communicating</td><td>Writing equations from words and spotting errors.</td></tr><tr><td>D</td><td>Applying mathematics in real-life contexts</td><td>Money, business, mixtures and everyday problems.</td></tr></table></div><p><b>Tools:</b> ⏱ at the top times each tab (pause or reset it). ✏️ opens a scratchpad with four pens for rough work. Tap the BM badge to go back to the home page.</p><p><b>Typing answers:</b> type only the value of the unknown. Negative numbers with the − key (<span class=\"mono\">-4</span>); fractions as <span class=\"mono\">-2/5</span> or <span class=\"mono\">125/2</span>; mixed numbers as <span class=\"mono\">62 1/2</span>; decimals such as <span class=\"mono\">62.5</span> are also accepted. Areas in the Computational Thinking questions are typed with ^, e.g. <span class=\"mono\">9x^2</span>.</p></section><section class=\"note\" id=\"n91\"><h2>9.1 Solving simple linear equations</h2><p class=\"lt\"><b>Objective:</b> Solve linear equations with the unknown on one side by doing the same operation on both sides, including cross-multiplication.</p><p>An equation is like a balance: whatever you do to one side you must do to the other, and it stays balanced. To find the unknown, <b>undo</b> what has been done to it, using the inverse operation.</p><div class=\"tscroll\"><table class=\"ttab\"><tr><th>Equation</th><th>Do to both sides</th><th>Solution</th></tr><tr><td>4x = 20</td><td>divide by 4</td><td>x = 5</td></tr><tr><td>−5x = 20</td><td>divide by −5</td><td>x = −4</td></tr><tr><td>{x/3} = 60</td><td>multiply by 3</td><td>x = 180</td></tr><tr><td>x − 3 = 4</td><td>add 3</td><td>x = 7</td></tr><tr><td>x + 10 = 7</td><td>subtract 10</td><td>x = −3</td></tr></table></div><p><b>Cross-multiplication:</b> if {a/b} = {c/d} then a × d = b × c. So {x/3} = 60 gives x = 60 × 3 = 180 at once.</p><div class=\"ex\"><div class=\"exh\">Book Example 5 · If 3x/(−5) = 30, find x</div><div class=\"exl\">Multiply both sides by the multiplicative inverse of {−3/5}, i.e. by {−5/3}.<br>x = 30 × ({−5/3}) = <b>−50</b>.<br>Or cross-multiply: 3x = 30 × (−5) = −150, so x = −50.</div></div><h4>Two steps</h4><p>When the unknown has been multiplied and then had a number added, undo the addition first and the multiplication second.</p><div class=\"ex\"><div class=\"exh\">Book Example 11 · If {3x/4} + 3 = 18, find x</div><div class=\"exl\">Subtract 3 from both sides: {3x/4} = 15.<br>Cross-multiply: 3x = 15 × 4 = 60.<br>x = {60/3} = <b>20</b>.</div></div><div class=\"keybox\"><b>Check your answer</b> by putting it back into the original equation: (3 × 20)/4 + 3 = 15 + 3 = 18 ✓.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s1\">Practise 9.1 →</button></div></section><section class=\"note\" id=\"n92\"><h2>9.2 Forming and solving equations</h2><p class=\"lt\"><b>Objective:</b> Translate statements, percentages and ratios into linear equations and solve them.</p><p>To solve a word problem: (1) let the unknown quantity be x, (2) write the other quantities in terms of x, (3) turn the sentence into an equation, (4) solve it, (5) answer the question and check.</p><div class=\"tscroll\"><table class=\"ttab\"><tr><th>Words</th><th>Algebra</th></tr><tr><td>thrice a number</td><td>3x</td></tr><tr><td>{1/3} of a number</td><td>{x/3}</td></tr><tr><td>10% of a number</td><td>{10/100} × x</td></tr><tr><td>4 less than a number</td><td>x − 4</td></tr><tr><td>two numbers in the ratio 6 : 5</td><td>6x and 5x</td></tr></table></div><div class=\"ex\"><div class=\"exh\">Book Example 12 · Thrice a number is 60</div><div class=\"exl\">Let the number be x. Then 3x = 60.<br>x = {60/3} = <b>20</b>.</div></div><div class=\"ex\"><div class=\"exh\">Ratios · Ex 9A Q10</div><div class=\"exl\">Sahil and Nikhil: ages 4x and 3x. In 5 years: 4x + 5 and 3x + 5.<br>(4x + 5)/(3x + 5) = {5/4} → 4(4x + 5) = 5(3x + 5) → 16x + 20 = 15x + 25 → x = 5.<br>Present ages: <b>20 years and 15 years</b>.</div></div><div class=\"keybox\"><b>Percentages:</b> 30% of a sum is ₹300 means {30/100} × x = 300, so x = 300 × {100/30} = ₹1000.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s2\">Practise 9.2 →</button></div></section><section class=\"note\" id=\"n93\"><h2>9.3 Unknowns on both sides</h2><p class=\"lt\"><b>Objective:</b> Solve linear equations with the unknown on both sides by transposing terms.</p><p>When the unknown appears on both sides, first collect all the unknown terms on one side and all the numbers on the other.</p><p><b>Transposition:</b> a term can be moved to the other side of the equation by changing its sign: + becomes −, − becomes +. (This is the same as adding or subtracting it on both sides.)</p><div class=\"ex\"><div class=\"exh\">Book Example 13 · 10m − 28 = 6 − 7m</div><div class=\"exl\">Transpose −7m and −28: 10m + 7m = 6 + 28.<br>17m = 34, so m = <b>2</b>.</div></div><div class=\"ex\"><div class=\"exh\">Book Example 15 · 9.3x + {3/5} = 2.7x + 13.8</div><div class=\"exl\">{3/5} = 0.6. Subtract 0.6: 9.3x = 2.7x + 13.2.<br>Subtract 2.7x: 6.6x = 13.2.<br>x = 13.2/6.6 = <b>2</b>.</div></div><div class=\"keybox\"><b>Tip:</b> collect the unknowns on the side where their coefficient stays positive, to avoid sign mistakes.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s3\">Practise 9.3 →</button></div></section><section class=\"note\" id=\"n94\"><h2>9.4 Brackets, fractions and products</h2><p class=\"lt\"><b>Objective:</b> Solve equations with brackets, fractions (LCM) and products whose x² terms cancel, using cross-multiplication.</p><ul><li><b>Brackets:</b> remove them first (watch a minus sign in front of a bracket: −(x − 1) = −x + 1).</li><li><b>Fractions:</b> multiply every term by the LCM of the denominators, or combine one side and cross-multiply.</li><li><b>Products:</b> multiply out; the x<sup>2</sup> terms on the two sides cancel, leaving a linear equation.</li></ul><div class=\"ex\"><div class=\"exh\">Book Example 16 · (2x − 17)/2 − (x − (x − 1)/3) = 12</div><div class=\"exl\">Remove the brackets: (2x − 17)/2 − x + (x − 1)/3 = 12.<br>Multiply by 6: 3(2x − 17) − 6x + 2(x − 1) = 72 → 6x − 51 − 6x + 2x − 2 = 72.<br>2x − 53 = 72 → 2x = 125 → x = <b>{62 1/2}</b>.</div></div><div class=\"ex\"><div class=\"exh\">Book Example 17 · (x − 4)(x − 6) = (x − 2)(x − 4)</div><div class=\"exl\">x<sup>2</sup> − 10x + 24 = x<sup>2</sup> − 6x + 8.<br>Cancel x<sup>2</sup>: −10x + 6x = 8 − 24 → −4x = −16.<br>x = <b>4</b>.</div></div><div class=\"ex\"><div class=\"exh\">Book Example 18 · (2x + 1)/(3x + 5) = {11/20}</div><div class=\"exl\">Cross-multiply: 20(2x + 1) = 11(3x + 5).<br>40x + 20 = 33x + 55 → 7x = 35 → x = <b>5</b>.</div></div><div class=\"keybox\"><b>Never</b> put a value that makes a denominator zero into the answer: in 3/(x − 1) − … the value x = 1 is not allowed.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s4\">Practise 9.4 →</button></div></section><section class=\"note\" id=\"n95\"><h2>9.5 Numbers, ages, coins and mixtures</h2><p class=\"lt\"><b>Objective:</b> Use linear equations to solve problems on numbers, ages, coins, consecutive numbers and mixtures.</p><div class=\"tscroll\"><table class=\"ttab\"><tr><th>Problem type</th><th>How to set it up</th></tr><tr><td>Consecutive numbers</td><td>x, x + 1, x + 2 (even or odd: x, x + 2, x + 4)</td></tr><tr><td>Ages</td><td>in x years: add x to <b>every</b> age; x years ago: subtract x from every age</td></tr><tr><td>Coins / notes</td><td>value = number of coins × value of one coin</td></tr><tr><td>Mixtures</td><td>cost of first part + cost of second part = cost of the mixture</td></tr></table></div><div class=\"ex\"><div class=\"exh\">Book Example 22 · Amit 20, Leela 4</div><div class=\"exl\">In x years: Amit 20 + x, Leela 4 + x.<br>20 + x = 2(4 + x) → 20 + x = 8 + 2x → x = <b>12 years</b>.</div></div><div class=\"ex\"><div class=\"exh\">Book Example 24 · Coins</div><div class=\"exl\">₹5 coins: x (value ₹5x); ₹2 coins: 2x (value ₹4x).<br>5x + 4x = 36 → 9x = 36 → x = 4: <b>4 coins of ₹5 and 8 coins of ₹2</b>.</div></div><div class=\"ex\"><div class=\"exh\">Book Example 26 · Tea mixture</div><div class=\"exl\">x kg at ₹144 + 10 kg at ₹180 = (x + 10) kg at ₹156.<br>144x + 1800 = 156x + 1560 → 240 = 12x → x = <b>20 kg</b>.</div></div><div class=\"keybox\"><b>Answer the question asked:</b> if x is the smaller number, remember to give the larger number too.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s5\">Practise 9.5 →</button></div></section><section class=\"note\" id=\"n96\"><h2>9.6 Solutions, shapes, speed and digits</h2><p class=\"lt\"><b>Objective:</b> Use linear equations to solve problems on solutions, rectangles and squares, speed and distance, and two-digit numbers.</p><ul><li><b>Solutions:</b> adding water does not change the amount of acid; adding alcohol changes both the alcohol and the total.</li><li><b>Rectangles:</b> perimeter = 2(length + breadth), area = length × breadth.</li><li><b>Speed:</b> distance = speed × time. Moving towards each other or in opposite directions, the distances add up.</li><li><b>Digits:</b> a two-digit number with tens digit x and units digit y is 10x + y (not xy). Reversed it is 10y + x.</li></ul><div class=\"ex\"><div class=\"exh\">Book Example 27 · Making the acid 8%</div><div class=\"exl\">Add x litres of water: total (50 + x) litres, acid still 10 litres.<br>{8/100} × (50 + x) = 10 → 400 + 8x = 1000 → x = <b>75 litres</b>.</div></div><div class=\"ex\"><div class=\"exh\">Book Example 30 · Trains towards each other</div><div class=\"exl\">After x hours: 60x + 90x = 750.<br>150x = 750 → x = <b>5 hours</b>.</div></div><div class=\"ex\"><div class=\"exh\">Book Example 33 · Units digit 3, number = 7 × sum of digits</div><div class=\"exl\">Tens digit x: number 10x + 3, sum x + 3.<br>10x + 3 = 7(x + 3) → 3x = 18 → x = 6: the number is <b>63</b>.</div></div><div class=\"keybox\"><b>Check with the story:</b> 63 = 7 × (6 + 3) = 7 × 9 ✓.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s6\">Practise 9.6 →</button></div></section><section class=\"note\" id=\"nsum\"><h2>Chapter checklist</h2><ul><li>Solve linear equations with the unknown on one side by doing the same operation on both sides, including cross-multiplication.</li><li>Translate statements, percentages and ratios into linear equations and solve them.</li><li>Solve linear equations with the unknown on both sides by transposing terms.</li><li>Solve equations with brackets, fractions (LCM) and products whose x² terms cancel, using cross-multiplication.</li><li>Use linear equations to solve problems on numbers, ages, coins, consecutive numbers and mixtures.</li><li>Use linear equations to solve problems on solutions, rectangles and squares, speed and distance, and two-digit numbers.</li></ul><div class=\"hub-btns\" style=\"margin-top:10px\"><button class=\"hub-btn\" data-go=\"s7\">Assessment A</button><button class=\"hub-btn\" data-go=\"s8\">Assessment B</button><button class=\"hub-btn\" data-go=\"s9\">Assessment C</button><button class=\"hub-btn\" data-go=\"s10\">Assessment D</button><button class=\"hub-btn primary\" data-go=\"report\">📊 Report</button></div></section>";
var REPORT = [["s7", "A", "Knowing and understanding"], ["s8", "B", "Investigating patterns"], ["s9", "C", "Communicating"], ["s10", "D", "Applying mathematics in real-life contexts"]];
var SECTIONS = [{"id": "s1", "label": "9.1 Simple equations", "sub": "Solving linear equations with the unknown on one side", "slides": [{"kind": "mcq", "text": "<b>Looking Back · Q1</b> · Is 3 a root of z − {2/3} = {5/6}?", "opts": ["No, the root is {1/6}", "No, the root is {7/3}", "Yes, 3 − {2/3} = {5/6}", "No, the root is {3/2}"], "correct": 3, "tag": "", "sol": "z = {5/6} + {2/3} = {5/6} + {4/6} = {9/6} = {3/2}. Check 3: 3 − {2/3} = {7/3} ≠ {5/6}. So 3 is not a root."}, {"kind": "blank", "p": "<b>Looking Back · Q2</b> · Find the root of (2x − 4)/5 = 6.", "tag": "", "marks": "", "flat": [{"t": "2x − 4 = __B1__", "a": {"B1": "30"}}, {"t": "x = __B1__", "a": {"B1": "17"}, "expr": "fv"}], "sol": "Multiply both sides by 5: 2x − 4 = 30.\nAdd 4: 2x = 34, so x = 17."}, {"kind": "mcq", "text": "<b>Looking Back · Q3</b> · Solve A = {1/2}bh for h.", "opts": ["h = 2Ab", "h = {A/2b}", "h = {b/2A}", "h = {2A/b}"], "correct": 3, "tag": "", "sol": "Multiply both sides by 2: 2A = bh. Divide both sides by b: h = {2A/b}."}, {"kind": "mcq", "text": "<b>Example 1</b> · If 4x = 20, find the value of x.", "opts": ["24", "80", "5", "16"], "correct": 2, "tag": "", "sol": "Divide both sides by 4: {4x/4} = {20/4}, so x = 5."}, {"kind": "blank", "p": "<b>Examples 2 and 3</b> · Find the value of x.", "tag": "", "marks": "", "flat": [{"t": "Example 2: −2x = −8, x = __B1__", "a": {"B1": "4"}, "expr": "fv"}, {"t": "Example 3: −5x = 20, x = __B1__", "a": {"B1": "-4"}, "expr": "fv"}], "sol": "Divide both sides by −2: x = {−8/−2} = 4.\nDivide both sides by −5: x = {20/−5} = −4."}, {"kind": "mcq", "text": "<b>Example 4</b> · If {x/3} = 60, find x.", "opts": ["180", "20", "63", "57"], "correct": 0, "tag": "", "sol": "Multiply both sides by 3: x = 60 × 3 = 180 (or cross-multiply)."}, {"kind": "blank", "p": "<b>Example 5</b> · If 3x/(−5) = 30, find the value of x.", "tag": "", "marks": "", "flat": [{"t": "Multiply both sides by the multiplicative inverse of {−3/5}, i.e. by __B1__", "a": {"B1": "-5/3"}, "expr": "fl"}, {"t": "x = __B1__", "a": {"B1": "-50"}, "expr": "fv"}], "sol": "The reciprocal of {−3/5} is {−5/3}.\nx = 30 × ({−5/3}) = −50. (Cross-multiplying: 3x = 30 × (−5) = −150, x = −50.)"}, {"kind": "mcq", "text": "<b>Examples 6 and 7</b> · Find x:  Example 6: x − 3 = 4   Example 7: x − 5 = −8", "opts": ["x = 7 and x = 3", "x = 1 and x = −13", "x = 1 and x = 3", "x = 7 and x = −3"], "correct": 3, "tag": "", "sol": "Example 6: add 3 to both sides, x = 7. Example 7: add 5 to both sides, x = −8 + 5 = −3."}, {"kind": "blank", "p": "<b>Examples 8 and 9</b> · Find the value of x.", "tag": "", "marks": "", "flat": [{"t": "Example 8: x + 3 = 8, x = __B1__", "a": {"B1": "5"}, "expr": "fv"}, {"t": "Example 9: x + 10 = 7, x = __B1__", "a": {"B1": "-3"}, "expr": "fv"}], "sol": "Subtract 3 from both sides: x = 8 − 3 = 5.\nSubtract 10 from both sides: x = 7 − 10 = −3."}, {"kind": "mcq", "text": "<b>Example 10</b> · If 2x + 3 = 9, find x.", "opts": ["4.5", "6", "3", "12"], "correct": 2, "tag": "", "sol": "Subtract 3 from both sides: 2x = 6. Divide both sides by 2: x = 3."}, {"kind": "blank", "p": "<b>Example 11</b> · If {3x/4} + 3 = 18, find x.", "tag": "", "marks": "", "flat": [{"t": "Subtract 3 from both sides: {3x/4} = __B1__", "a": {"B1": "15"}}, {"t": "Cross-multiply: 3x = __B1__", "a": {"B1": "60"}}, {"t": "x = __B1__", "a": {"B1": "20"}, "expr": "fv"}], "sol": "18 − 3 = 15.\n3x = 15 × 4 = 60.\nx = {60/3} = 20."}, {"kind": "blank", "p": "<b>Try This</b> · Find x if:", "tag": "", "marks": "", "flat": [{"t": "a) 5x + 2 = 7, x = __B1__", "a": {"B1": "1"}, "expr": "fv"}, {"t": "b) {2x/3} = 12, x = __B1__", "a": {"B1": "18"}, "expr": "fv"}, {"t": "c) x − 7 = −3, x = __B1__", "a": {"B1": "4"}, "expr": "fv"}, {"t": "d) {5x/2} + 5 = 20, x = __B1__", "a": {"B1": "6"}, "expr": "fv"}], "sol": "5x = 5, x = 1.\n2x = 36, x = 18.\nx = −3 + 7 = 4.\n{5x/2} = 15, 5x = 30, x = 6."}, {"kind": "mcq", "text": "<b>Ex 9A · Q1(a–d)</b> · Solve for the unknown:  a) x − 5 = 6   b) x − 5 = 4   c) x − 7 = 18   d) x − 30 = 72", "opts": ["a) 11  b) 9  c) 25  d) 42", "a) 11  b) 9  c) 25  d) 102", "a) 11  b) 1  c) 25  d) 102", "a) 1  b) −1  c) 11  d) 42"], "correct": 1, "tag": "", "sol": "Add the number that is subtracted to both sides: a) 6 + 5 = 11. b) 4 + 5 = 9. c) 18 + 7 = 25. d) 72 + 30 = 102."}, {"kind": "blank", "p": "<b>Ex 9A · Q1(e–h)</b> · Solve for the unknown.", "tag": "", "marks": "", "flat": [{"t": "e) x − 23 = −143, x = __B1__", "a": {"B1": "-120"}, "expr": "fv"}, {"t": "f) y − 15 = −22, y = __B1__", "a": {"B1": "-7"}, "expr": "fv"}, {"t": "g) x − 10 = 63, x = __B1__", "a": {"B1": "73"}, "expr": "fv"}, {"t": "h) c − {1/2} = −4, c = __B1__", "a": {"B1": "-7/2"}, "expr": "fv"}], "sol": "x = −143 + 23 = −120.\ny = −22 + 15 = −7.\nx = 63 + 10 = 73.\nc = −4 + {1/2} = {−7/2} = −{3 1/2}."}, {"kind": "mcq", "text": "<b>Ex 9A · Q1(i–l)</b> · Solve for the unknown:  i) x − 15 = −29   j) t − 114 = 26   k) x − 86 = −42   l) k − 64 = 164", "opts": ["i) −14  j) 88  k) 44  l) 100", "i) −14  j) 140  k) 44  l) 228", "i) −44  j) 140  k) −128  l) 228", "i) 14  j) 140  k) 44  l) 228"], "correct": 1, "tag": "", "sol": "i) −29 + 15 = −14. j) 26 + 114 = 140. k) −42 + 86 = 44. l) 164 + 64 = 228."}, {"kind": "blank", "p": "<b>Ex 9A · Q2(a–d)</b> · Solve for the unknown.", "tag": "", "marks": "", "flat": [{"t": "a) 4 = 5x − 6, x = __B1__", "a": {"B1": "2"}, "expr": "fv"}, {"t": "b) 5x − 3 = 12, x = __B1__", "a": {"B1": "3"}, "expr": "fv"}, {"t": "c) 3(x + 1) = 6, x = __B1__", "a": {"B1": "1"}, "expr": "fv"}, {"t": "d) 7(m − 9) = 35, m = __B1__", "a": {"B1": "14"}, "expr": "fv"}], "sol": "10 = 5x, x = 2.\n5x = 15, x = 3.\nx + 1 = 2, x = 1.\nm − 9 = 5, m = 14."}, {"kind": "mcq", "text": "<b>Ex 9A · Q2(e–h)</b> · Solve:  e) 8(x + 3) + 2 = 42   f) 16 − 3(x − 7) = −14   g) 5x + 8(2x − 9) = 54   h) 4 = 5x + 6", "opts": ["e) 2  f) 17  g) 18  h) {−2/5}", "e) {5/2}  f) 17  g) 6  h) {2/5}", "e) 2  f) 17  g) 6  h) {−2/5}", "e) 2  f) −17  g) 6  h) {−2/5}"], "correct": 2, "tag": "", "sol": "e) 8(x + 3) = 40, x + 3 = 5, x = 2. f) 16 − 3x + 21 = −14, −3x = −51, x = 17. g) 5x + 16x − 72 = 54, 21x = 126, x = 6. h) 5x = 4 − 6 = −2, x = {−2/5}."}, {"kind": "blank", "p": "<b>Ex 9A · Q2(i–l)</b> · Solve for the unknown.", "tag": "", "marks": "", "flat": [{"t": "i) −16 = −a − 2, a = __B1__", "a": {"B1": "14"}, "expr": "fv"}, {"t": "j) 30 = 6(8 + x), x = __B1__", "a": {"B1": "-3"}, "expr": "fv"}, {"t": "k) 12(3 − a) = 24, a = __B1__", "a": {"B1": "1"}, "expr": "fv"}, {"t": "l) 7(x + 3) + 2 = 44, x = __B1__", "a": {"B1": "3"}, "expr": "fv"}], "sol": "a = −2 + 16 = 14.\n8 + x = 5, x = −3.\n3 − a = 2, a = 1.\n7(x + 3) = 42, x + 3 = 6, x = 3."}, {"kind": "blank", "p": "<b>Ex 9A · Q2(m–p)</b> · Solve for the unknown.", "tag": "", "marks": "", "flat": [{"t": "m) 3(x − 5) − 7 = 14, x = __B1__", "a": {"B1": "12"}, "expr": "fv"}, {"t": "n) {x/6} = 5, x = __B1__", "a": {"B1": "30"}, "expr": "fv"}, {"t": "o) {t/3} = 20, t = __B1__", "a": {"B1": "60"}, "expr": "fv"}, {"t": "p) {x/4} = {1/2}, x = __B1__", "a": {"B1": "2"}, "expr": "fv"}], "sol": "3(x − 5) = 21, x − 5 = 7, x = 12.\nx = 5 × 6 = 30.\nt = 20 × 3 = 60.\n2x = 4, x = 2."}, {"kind": "mcq", "text": "<b>Ex 9A · Q2(q–t)</b> · Solve:  q) x/0.03 = 0.03   r) {r/9} = −11   s) x/(−4) = {1/8}   t) x/(−4) = {3/4}", "opts": ["q) 0.09  r) −99  s) {−1/32}  t) −3", "q) 0.0009  r) 99  s) {1/2}  t) 3", "q) 0.0009  r) −99  s) {−1/2}  t) −3", "q) 1  r) −99  s) {−1/2}  t) −3"], "correct": 2, "tag": "", "sol": "q) x = 0.03 × 0.03 = 0.0009. r) r = −11 × 9 = −99. s) x = {1/8} × (−4) = {−1/2}. t) x = {3/4} × (−4) = −3."}, {"kind": "blank", "p": "<b>Ex 9A · Q2(u–x)</b> · Solve for the unknown.", "tag": "", "marks": "", "flat": [{"t": "u) 16/(5x) = {1/10}, x = __B1__", "a": {"B1": "32"}, "expr": "fv"}, {"t": "v) (y + 3)/5 = 14, y = __B1__", "a": {"B1": "67"}, "expr": "fv"}, {"t": "w) 36/(x + 2) = 12, x = __B1__", "a": {"B1": "1"}, "expr": "fv"}, {"t": "x) 3/(2x) + 7/(2x) = 5, x = __B1__", "a": {"B1": "1"}, "expr": "fv"}], "sol": "Cross-multiply: 5x = 160, x = 32.\ny + 3 = 70, y = 67.\n36 = 12(x + 2), x + 2 = 3, x = 1.\n10/(2x) = 5, so 10 = 10x, x = 1."}]}, {"id": "s2", "label": "9.2 Forming equations", "sub": "Forming and solving equations from statements", "slides": [{"kind": "mcq", "text": "<b>Looking Back · Q4</b> · Frame the algebraic expression (equation) for the given statement: A number x is 8 times another number. Their difference is 42.", "opts": ["x − 8 = 42", "8x − x = 42", "x − {x/8} = 42", "{x/8} − x = 42"], "correct": 2, "tag": "", "sol": "The other number is {x/8}, because x is 8 times it. The larger minus the smaller is 42: x − {x/8} = 42. (Solving: {7x/8} = 42, x = 48 and the other number is 6.)"}, {"kind": "blank", "p": "<b>Looking Back · Q5</b> · Raghav has twice as much money as Jessica. Together they have ₹150. How much money does Jessica have?", "tag": "", "marks": "", "flat": [{"t": "Jessica ₹x, Raghav ₹2x: x + 2x = __B1__", "a": {"B1": "150"}}, {"t": "Jessica has ₹__B1__", "a": {"B1": "50"}, "expr": "fv"}], "sol": "x + 2x = 150.\n3x = 150, x = 50. (Raghav has ₹100.)"}, {"kind": "blank", "p": "<b>Example 12</b> · Thrice a number is 60. Find the number.", "tag": "", "marks": "", "flat": [{"t": "3x = 60, so x = __B1__", "a": {"B1": "20"}, "expr": "fv"}], "sol": "Divide both sides by 3: x = 20."}, {"kind": "mcq", "text": "<b>Ex 9A · Q3(a–e)</b> · What is the number?  a) Twice a number is 40.  b) Five times a number is 30.  c) Half of a number is 16.  d) Eight times a number is 32.  e) {1/3} of a number is 18.", "opts": ["a) 20  b) 6  c) 32  d) 4  e) 6", "a) 20  b) 6  c) 8  d) 4  e) 6", "a) 20  b) 6  c) 32  d) 4  e) 54", "a) 80  b) 150  c) 8  d) 256  e) 6"], "correct": 2, "tag": "", "sol": "a) 2x = 40, x = 20. b) 5x = 30, x = 6. c) {x/2} = 16, x = 32. d) 8x = 32, x = 4. e) {x/3} = 18, x = 54."}, {"kind": "blank", "p": "<b>Ex 9A · Q3(f–j)</b> · What is the number?", "tag": "", "marks": "", "flat": [{"t": "f) One and a half times a number is 150: __B1__", "a": {"B1": "100"}, "expr": "fv"}, {"t": "g) {1/5} of a number is 60: __B1__", "a": {"B1": "300"}, "expr": "fv"}, {"t": "h) {1/10} of a number is 49: __B1__", "a": {"B1": "490"}, "expr": "fv"}, {"t": "i) 10% of a number is 63: __B1__", "a": {"B1": "630"}, "expr": "fv"}, {"t": "j) I thought of a number. If I multiply it by 9, the number will be 117: __B1__", "a": {"B1": "13"}, "expr": "fv"}], "sol": "{3/2}x = 150, x = 150 × {2/3} = 100.\nx = 60 × 5 = 300.\nx = 49 × 10 = 490.\n{10/100}x = 63, x = 630.\n9x = 117, x = 13."}, {"kind": "mcq", "text": "<b>Ex 9A · Q4</b> · Five times Raju’s pocket money is ₹80. What is his pocket money?", "opts": ["₹85", "₹16", "₹75", "₹400"], "correct": 1, "tag": "", "sol": "5x = 80, so x = 16. His pocket money is ₹16."}, {"kind": "blank", "p": "<b>Ex 9A · Q5</b> · 30% of a sum of money is ₹300. What is that amount?", "tag": "", "marks": "", "flat": [{"t": "{30/100} × x = 300, so x = ₹__B1__", "a": {"B1": "1000"}, "expr": "fv"}], "sol": "x = 300 × {100/30} = ₹1000."}, {"kind": "mcq", "text": "<b>Ex 9A · Q6</b> · {1/6} of the length of a stick is 5 cm. What is the length of the stick?", "opts": ["6 cm", "{5/6} cm", "30 cm", "11 cm"], "correct": 2, "tag": "", "sol": "{x/6} = 5, so x = 30 cm."}, {"kind": "blank", "p": "<b>Ex 9A · Q7</b> · Savita’s age is 4 years less than that of Rajan. If Savita is 18 years old, what is Rajan’s age?", "tag": "", "marks": "", "flat": [{"t": "x − 4 = 18, Rajan’s age = __B1__ years", "a": {"B1": "22"}, "expr": "fv"}], "sol": "x = 18 + 4 = 22 years."}, {"kind": "mcq", "text": "<b>Ex 9A · Q8</b> · The attendance of a class today is 32. This is 4 less than the total number of students in the class. What is the total number of students?", "opts": ["36", "28", "128", "8"], "correct": 0, "tag": "", "sol": "x − 4 = 32, so x = 36 students."}, {"kind": "blank", "p": "<b>Ex 9A · Q9</b> · Hari’s father gave him ₹70. Now he has ₹130. How much money did Hari have in the beginning?", "tag": "", "marks": "", "flat": [{"t": "x + 70 = 130, x = ₹__B1__", "a": {"B1": "60"}, "expr": "fv"}], "sol": "x = 130 − 70 = ₹60."}, {"kind": "blank", "p": "<b>Ex 9A · Q10</b> · The ages of Sahil and Nikhil are in the ratio 4 : 3. Five years hence, the ratio of their ages will be 5 : 4. Find their present ages.", "tag": "", "marks": "", "flat": [{"t": "Ages 4x and 3x: (4x + 5)/(3x + 5) = {5/4} gives x = __B1__", "a": {"B1": "5"}, "expr": "fv"}, {"t": "Sahil = __B1__ years", "a": {"B1": "20"}}, {"t": "Nikhil = __B1__ years", "a": {"B1": "15"}}], "sol": "Cross-multiply: 4(4x + 5) = 5(3x + 5) → 16x + 20 = 15x + 25 → x = 5.\n4 × 5 = 20 years.\n3 × 5 = 15 years. Check: in 5 years 25 : 20 = 5 : 4 ✓."}, {"kind": "mcq", "text": "<b>Ex 9A · Q11</b> · A student has obtained 35% marks in a test. If the student scored 24.5 marks, find the maximum marks.", "opts": ["70", "85.75", "60", "8.575"], "correct": 0, "tag": "", "sol": "{35/100} × x = 24.5, so x = 24.5 × {100/35} = 70 marks."}, {"kind": "blank", "p": "<b>Ex 9A · Q12</b> · Akhil sold an article for ₹500 and gained 25% on it. Find the cost price of the article.", "tag": "", "marks": "", "flat": [{"t": "CP = ₹x: x + {25/100}x = 500, so x = ₹__B1__", "a": {"B1": "400"}, "expr": "fv"}], "sol": "{125/100}x = 500, x = 500 × {100/125} = ₹400."}, {"kind": "mcq", "text": "<b>Ex 9A · Q13</b> · Two numbers are in the ratio 6 : 5. If the sum of the numbers is 110, find the numbers.", "opts": ["55 and 55", "36 and 25", "66 and 44", "60 and 50"], "correct": 3, "tag": "", "sol": "Let them be 6x and 5x: 11x = 110, x = 10. The numbers are 60 and 50."}]}, {"id": "s3", "label": "9.3 Unknowns on both sides", "sub": "Solving equations with the unknown on both sides", "slides": [{"kind": "blank", "p": "<b>Example 13</b> · If 10m − 28 = 6 − 7m, find m.", "tag": "", "marks": "", "flat": [{"t": "Add 7m to both sides: __B1__m − 28 = 6", "a": {"B1": "17"}}, {"t": "Add 28 to both sides: 17m = __B1__", "a": {"B1": "34"}}, {"t": "m = __B1__", "a": {"B1": "2"}, "expr": "fv"}], "sol": "10m + 7m = 17m.\n6 + 28 = 34.\nm = {34/17} = 2."}, {"kind": "mcq", "text": "<b>Example 14</b> · Solve 2(x + 3) + 3(x + 1) = 4(2x − 3) + 3.", "opts": ["x = 6", "x = {9/13}", "x = 2", "x = −6"], "correct": 0, "tag": "", "sol": "Remove the brackets: 2x + 6 + 3x + 3 = 8x − 12 + 3, i.e. 5x + 9 = 8x − 9. Transpose: 5x − 8x = −9 − 9, −3x = −18, x = 6."}, {"kind": "blank", "p": "<b>Example 15</b> · Solve 9.3x + {3/5} = 2.7x + 13.8.", "tag": "", "marks": "", "flat": [{"t": "Subtract {3/5} = 0.6: 9.3x = 2.7x + __B1__", "a": {"B1": "13.2"}, "expr": "dec"}, {"t": "Subtract 2.7x: __B1__x = 13.2", "a": {"B1": "6.6"}, "expr": "dec"}, {"t": "x = __B1__", "a": {"B1": "2"}, "expr": "fv"}], "sol": "13.8 − 0.6 = 13.2.\n9.3 − 2.7 = 6.6.\nx = 13.2/6.6 = 2."}, {"kind": "mcq", "text": "<b>Try This (a)</b> · Solve 3x − 1 = x + 3.", "opts": ["x = 4", "x = {1/2}", "x = 2", "x = 1"], "correct": 2, "tag": "", "sol": "3x − x = 3 + 1, 2x = 4, x = 2."}, {"kind": "blank", "p": "<b>Ex 9B · Q1(a–d)</b> · Solve.", "tag": "", "marks": "", "flat": [{"t": "a) 4a = 6a + 1, a = __B1__", "a": {"B1": "-1/2"}, "expr": "fv"}, {"t": "b) 4x = 2x + 30, x = __B1__", "a": {"B1": "15"}, "expr": "fv"}, {"t": "c) 11m = 42 + 4m, m = __B1__", "a": {"B1": "6"}, "expr": "fv"}, {"t": "d) 13y = −12y + 100, y = __B1__", "a": {"B1": "4"}, "expr": "fv"}], "sol": "−2a = 1, a = {−1/2}.\n2x = 30, x = 15.\n7m = 42, m = 6.\n25y = 100, y = 4."}, {"kind": "blank", "p": "<b>Ex 9B · Q1(e–h)</b> · Solve.", "tag": "", "marks": "", "flat": [{"t": "e) 10m − 28 = 6 − 7m, m = __B1__", "a": {"B1": "2"}, "expr": "fv"}, {"t": "f) −3x = −5x + 22, x = __B1__", "a": {"B1": "11"}, "expr": "fv"}, {"t": "g) 3y = 8 − 13y, y = __B1__", "a": {"B1": "1/2"}, "expr": "fv"}, {"t": "h) 3.3x + 22 = −11 − 7.7x, x = __B1__", "a": {"B1": "-3"}, "expr": "fv"}], "sol": "17m = 34, m = 2 (Example 13).\n2x = 22, x = 11.\n16y = 8, y = {1/2}.\n3.3x + 7.7x = −11 − 22, 11x = −33, x = −3."}, {"kind": "mcq", "text": "<b>Ex 9B · Q1(i–k)</b> · Solve:  i) 18x = −13x + 62   j) 5x − 3 = 12 + 8x   k) 5(x + 43) = 2(3x + 4)", "opts": ["i) 2  j) 5  k) 207", "i) 2  j) −5  k) −207", "i) 2  j) −5  k) 207", "i) 12.4  j) −5  k) 207"], "correct": 2, "tag": "", "sol": "i) 31x = 62, x = 2. j) 5x − 8x = 12 + 3, −3x = 15, x = −5. k) 5x + 215 = 6x + 8, x = 215 − 8 = 207."}, {"kind": "blank", "p": "<b>Ex 9B · Q3</b> · What value of y will make the given equation true?  10 − y = y − 10", "tag": "", "marks": "", "flat": [{"t": "y = __B1__", "a": {"B1": "10"}, "expr": "fv"}], "sol": "10 + 10 = y + y, so 2y = 20 and y = 10."}]}, {"id": "s4", "label": "9.4 Brackets & fractions", "sub": "Equations with brackets, fractions and products", "slides": [{"kind": "blank", "p": "<b>Example 16</b> · Solve (2x − 17)/2 − (x − (x − 1)/3) = 12.", "tag": "", "marks": "", "flat": [{"t": "Multiply by 6: 3(2x − 17) − 6x + 2(x − 1) = __B1__", "a": {"B1": "72"}}, {"t": "Simplify: 2x − 53 = 72, so 2x = __B1__", "a": {"B1": "125"}}, {"t": "x = __B1__", "a": {"B1": "125/2"}, "expr": "fv"}], "sol": "Remove the brackets: (2x − 17)/2 − x + (x − 1)/3 = 12; the LCM is 6, and 12 × 6 = 72.\n6x − 51 − 6x + 2x − 2 = 2x − 53; 2x = 72 + 53 = 125.\nx = {125/2} = {62 1/2}."}, {"kind": "mcq", "text": "<b>Example 17</b> · Solve (x − 4)(x − 6) = (x − 2)(x − 4).", "opts": ["x = 2", "x = −4", "x = 6", "x = 4"], "correct": 3, "tag": "", "sol": "x<sup>2</sup> − 10x + 24 = x<sup>2</sup> − 6x + 8. Cancel x<sup>2</sup>: −10x + 6x = 8 − 24, −4x = −16, x = 4."}, {"kind": "blank", "p": "<b>Example 18</b> · Solve (2x + 1)/(3x + 5) = {11/20}.", "tag": "", "marks": "", "flat": [{"t": "Cross-multiply: 20(2x + 1) = 11(3x + 5), i.e. 40x + 20 = 33x + __B1__", "a": {"B1": "55"}}, {"t": "x = __B1__", "a": {"B1": "5"}, "expr": "fv"}], "sol": "11 × 5 = 55.\n40x − 33x = 55 − 20, 7x = 35, x = 5."}, {"kind": "mcq", "text": "<b>Example 19</b> · Solve (2x − 3)/4 − (2x − 1)/2 = (x − 2)/3.", "opts": ["x = {5/2}", "x = −{1/2}", "x = 2", "x = {1/2}"], "correct": 3, "tag": "", "sol": "LCM 4 on the left: (2x − 3 − 4x + 2)/4 = (−2x − 1)/4. Cross-multiply: 3(−2x − 1) = 4(x − 2), −6x − 3 = 4x − 8, −10x = −5, x = {1/2}."}, {"kind": "blank", "p": "<b>Example 20</b> · Solve 3/(x − 1) − 2/(x − 2) = 1/(x − 3).", "tag": "", "marks": "", "flat": [{"t": "Left side over (x − 1)(x − 2): numerator 3(x − 2) − 2(x − 1) = x − __B1__", "a": {"B1": "4"}}, {"t": "After cross-multiplying and cancelling x<sup>2</sup>: −7x + 12 = −3x + __B1__", "a": {"B1": "2"}}, {"t": "x = __B1__", "a": {"B1": "5/2"}, "expr": "fv"}], "sol": "3x − 6 − 2x + 2 = x − 4.\n(x − 4)(x − 3) = (x − 1)(x − 2): x<sup>2</sup> − 7x + 12 = x<sup>2</sup> − 3x + 2.\n−4x = −10, x = {10/4} = {5/2}."}, {"kind": "mcq", "text": "<b>Try This (b)</b> · Solve (x + 3)(x + 5) = (x + 1)(x + 4).", "opts": ["x = {11/3}", "x = {−19/3}", "x = {−11/3}", "x = −11"], "correct": 2, "tag": "", "sol": "x<sup>2</sup> + 8x + 15 = x<sup>2</sup> + 5x + 4. Cancel x<sup>2</sup>: 3x = −11, x = {−11/3}."}, {"kind": "blank", "p": "<b>Try This (c, d)</b> · Solve.", "tag": "", "marks": "", "flat": [{"t": "c) (3x + 2)/(2x + 3) = {1/2}, x = __B1__", "a": {"B1": "-1/4"}, "expr": "fv"}, {"t": "d) 2/(x + 1) = 1/(3x − 2), x = __B1__", "a": {"B1": "1"}, "expr": "fv"}], "sol": "Cross-multiply: 6x + 4 = 2x + 3, 4x = −1, x = {−1/4}.\nCross-multiply: 2(3x − 2) = x + 1, 6x − 4 = x + 1, 5x = 5, x = 1."}, {"kind": "blank", "p": "<b>Ex 9B · Q2(a–c)</b> · Solve.", "tag": "", "marks": "", "flat": [{"t": "a) (x − 6)(x + 7) = (x + 3)(x − 11), x = __B1__", "a": {"B1": "1"}, "expr": "fv"}, {"t": "b) (x + 7)(x + 9) = (x + 3)(x + 21), x = __B1__", "a": {"B1": "0"}, "expr": "fv"}, {"t": "c) (x + 1)(x + 2) = (x − 3)(x − 4), x = __B1__", "a": {"B1": "1"}, "expr": "fv"}], "sol": "x<sup>2</sup> + x − 42 = x<sup>2</sup> − 8x − 33: 9x = 9, x = 1.\nx<sup>2</sup> + 16x + 63 = x<sup>2</sup> + 24x + 63: 8x = 0, x = 0.\nx<sup>2</sup> + 3x + 2 = x<sup>2</sup> − 7x + 12: 10x = 10, x = 1."}, {"kind": "mcq", "text": "<b>Ex 9B · Q2(d)</b> · Solve (x + 2)/(x + 5) = x/(x + 6).", "opts": ["x = 12", "x = 4", "x = −2", "x = −4"], "correct": 3, "tag": "", "sol": "Cross-multiply: (x + 2)(x + 6) = x(x + 5), x<sup>2</sup> + 8x + 12 = x<sup>2</sup> + 5x, 3x = −12, x = −4."}, {"kind": "blank", "p": "<b>Ex 9B · Q2(e–g)</b> · Solve.", "tag": "", "marks": "", "flat": [{"t": "e) (5x − 7)/(3x + 1) = 1, x = __B1__", "a": {"B1": "4"}, "expr": "fv"}, {"t": "f) (3x − 8)/(2x − 5) = {1/3}, x = __B1__", "a": {"B1": "19/7"}, "expr": "fv"}, {"t": "g) (5x + 2)/(x − 3) = {−9/4}, x = __B1__", "a": {"B1": "19/29"}, "expr": "fv"}], "sol": "5x − 7 = 3x + 1, 2x = 8, x = 4.\n9x − 24 = 2x − 5, 7x = 19, x = {19/7}.\n4(5x + 2) = −9(x − 3), 20x + 8 = −9x + 27, 29x = 19, x = {19/29}."}, {"kind": "mcq", "text": "<b>Ex 9B · Q2(h)</b> · Solve 3/(x − 1) − 2/(x − 2) = 1/(x − 3).", "opts": ["x = −{5/2}", "x = {5/2}", "x = {2/5}", "x = 4"], "correct": 1, "tag": "", "sol": "This is Example 20: (x − 4)(x − 3) = (x − 1)(x − 2), x<sup>2</sup> − 7x + 12 = x<sup>2</sup> − 3x + 2, −4x = −10, x = {5/2}."}, {"kind": "blank", "p": "<b>Ex 9B · Q2(i, j)</b> · Solve.", "tag": "", "marks": "", "flat": [{"t": "i) {x/3} + 7 = {2x/3} + 2, x = __B1__", "a": {"B1": "15"}, "expr": "fv"}, {"t": "j) {x/3} − 7 = {2x/3} + 2, x = __B1__", "a": {"B1": "-27"}, "expr": "fv"}], "sol": "7 − 2 = {2x/3} − {x/3}: {x/3} = 5, x = 15.\n−7 − 2 = {x/3}: x = −27."}, {"kind": "blank", "p": "<b>Ex 9B · Q2(k–m)</b> · Solve.", "tag": "", "marks": "", "flat": [{"t": "k) (m − 17)/2 = 2m − 7, m = __B1__", "a": {"B1": "-1"}, "expr": "fv"}, {"t": "l) 7 − x = (2x − 7)/5, x = __B1__", "a": {"B1": "6"}, "expr": "fv"}, {"t": "m) {x/2} − (x − 4)/6 = {5/3}, x = __B1__", "a": {"B1": "3"}, "expr": "fv"}], "sol": "m − 17 = 4m − 14, −3m = 3, m = −1.\n35 − 5x = 2x − 7, 42 = 7x, x = 6.\nMultiply by 6: 3x − (x − 4) = 10, 2x + 4 = 10, x = 3."}, {"kind": "mcq", "text": "<b>Ex 9B · Q4</b> · Solve for x: (x<sup>2</sup> − 14x + 49)/(x<sup>2</sup> − 49) = {3/17}.", "opts": ["x = {7/10}", "x = 10", "x = 7", "x = −10"], "correct": 1, "tag": "", "sol": "x<sup>2</sup> − 14x + 49 = (x − 7)<sup>2</sup> and x<sup>2</sup> − 49 = (x − 7)(x + 7), so the left side is (x − 7)/(x + 7) (x ≠ 7). Cross-multiply: 17x − 119 = 3x + 21, 14x = 140, x = 10."}]}, {"id": "s5", "label": "9.5 Numbers, ages, coins", "sub": "Applications: numbers, ages, coins and mixtures", "slides": [{"kind": "blank", "p": "<b>Example 21</b> · One number is three times another number. If the larger number is subtracted from 60, the result is 5 less than the smaller number subtracted from 55. Find the numbers.", "tag": "", "marks": "", "flat": [{"t": "60 − 3x = 55 − x − 5 gives x = __B1__", "a": {"B1": "5"}, "expr": "fv"}, {"t": "Smaller number = __B1__", "a": {"B1": "5"}}, {"t": "Larger number = __B1__", "a": {"B1": "15"}}], "sol": "60 − 3x = 50 − x, 10 = 2x, x = 5.\nThe smaller number is x = 5.\nThe larger number is 3x = 15."}, {"kind": "mcq", "text": "<b>Example 22</b> · Amit is now 20 years old and Leela is 4 years old. In how many years will Amit be twice as old as Leela?", "opts": ["6 years", "16 years", "12 years", "8 years"], "correct": 2, "tag": "", "sol": "In x years: 20 + x = 2(4 + x), 20 + x = 8 + 2x, x = 12 years. (Then Amit 32, Leela 16.)"}, {"kind": "blank", "p": "<b>Example 23</b> · Sindhu is 40 years old and Smita is 20 years old. How many years ago was Sindhu three times as old as Smita?", "tag": "", "marks": "", "flat": [{"t": "40 − x = 3(20 − x) gives x = __B1__ years", "a": {"B1": "10"}, "expr": "fv"}], "sol": "40 − x = 60 − 3x, 2x = 20, x = 10 years ago (Sindhu 30, Smita 10)."}, {"kind": "mcq", "text": "<b>Example 24</b> · Jimmy has 2 times as many ₹2 coins as ₹5 coins. If he has a total of ₹36, how many coins of each kind does he have? (Let the number of ₹5 coins be x.)", "opts": ["6 coins of ₹5 and 3 coins of ₹2", "4 coins of ₹5 and 8 coins of ₹2", "4 coins of ₹5 and 4 coins of ₹2", "8 coins of ₹5 and 4 coins of ₹2"], "correct": 1, "tag": "", "sol": "Total value 5x + 4x = 9x = 36, x = 4. ₹5 coins: 4; ₹2 coins: 2 × 4 = 8. Check: 20 + 16 = 36.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 279 82\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect x=\"4.0\" y=\"4\" width=\"102.4\" height=\"24\" style=\"fill:var(--paper-2);stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"55.2\" y=\"17.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Kind of coin</text><rect x=\"106.4\" y=\"4\" width=\"59.2\" height=\"24\" style=\"fill:var(--paper-2);stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"136.0\" y=\"17.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Number</text><rect x=\"165.6\" y=\"4\" width=\"109.6\" height=\"24\" style=\"fill:var(--paper-2);stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"220.4\" y=\"17.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Value</text><rect x=\"4.0\" y=\"28\" width=\"102.4\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"55.2\" y=\"41.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">₹5</text><rect x=\"106.4\" y=\"28\" width=\"59.2\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"136.0\" y=\"41.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x</text><rect x=\"165.6\" y=\"28\" width=\"109.6\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"220.4\" y=\"41.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">₹5x</text><rect x=\"4.0\" y=\"52\" width=\"102.4\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"55.2\" y=\"65.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">₹2</text><rect x=\"106.4\" y=\"52\" width=\"59.2\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"136.0\" y=\"65.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2x</text><rect x=\"165.6\" y=\"52\" width=\"109.6\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"220.4\" y=\"65.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">₹2 × 2x = ₹4x</text></svg>"}, {"kind": "blank", "p": "<b>Example 25</b> · The sum of three consecutive numbers is 93. Find the numbers.", "tag": "", "marks": "", "flat": [{"t": "x + (x + 1) + (x + 2) = 93, so 3x + 3 = 93 and x = __B1__", "a": {"B1": "30"}}, {"t": "The numbers (in increasing order) are __B1__", "a": {"B1": "30, 31, 32"}, "expr": "dlist", "accept": ["32, 31, 30"]}], "sol": "3x = 90, x = 30.\n30, 31 and 32."}, {"kind": "mcq", "text": "<b>Example 26</b> · How many kilograms of tea worth ₹144 per kg should be mixed with 10 kg of tea worth ₹180 per kg to produce a mixture which will cost ₹156 per kg?", "opts": ["20 kg", "30 kg", "15 kg", "10 kg"], "correct": 0, "tag": "", "sol": "144x + 1800 = 156(x + 10) = 156x + 1560. So 240 = 12x, x = 20 kg."}, {"kind": "blank", "p": "<b>Try This · Q1</b> · The sum of three consecutive even numbers is 30. Find the numbers.", "tag": "", "marks": "", "flat": [{"t": "x + (x + 2) + (x + 4) = 30; the numbers (in increasing order) are __B1__", "a": {"B1": "8, 10, 12"}, "expr": "dlist", "accept": ["12, 10, 8"]}], "sol": "3x + 6 = 30, x = 8: the numbers are 8, 10 and 12."}, {"kind": "mcq", "text": "<b>Try This · Q2</b> · Rahul is now 10 years old and Tina is 2 years old. In how many years will Rahul be twice as old as Tina?", "opts": ["6 years", "4 years", "3 years", "8 years"], "correct": 0, "tag": "", "sol": "10 + x = 2(2 + x), 10 + x = 4 + 2x, x = 6 years."}, {"kind": "blank", "p": "<b>Ex 9C · Q1</b> · A number is twice another number. If their sum is 96, what are the numbers?", "tag": "", "marks": "", "flat": [{"t": "x + 2x = 96, x = __B1__", "a": {"B1": "32"}, "expr": "fv"}, {"t": "The larger number = __B1__", "a": {"B1": "64"}}], "sol": "3x = 96, x = 32.\n2x = 64."}, {"kind": "mcq", "text": "<b>Ex 9C · Q2</b> · The difference between two numbers is 18. If their sum is 86, what are the numbers?", "opts": ["43 and 43", "52 and 34", "68 and 18", "50 and 36"], "correct": 1, "tag": "", "sol": "x + (x − 18) = 86, 2x = 104, x = 52; the other is 34."}, {"kind": "blank", "p": "<b>Ex 9C · Q3</b> · Divide 72 into two parts so that the larger part exceeds the smaller part by 12. Find both the parts.", "tag": "", "marks": "", "flat": [{"t": "x + (x + 12) = 72, smaller part = __B1__", "a": {"B1": "30"}, "expr": "fv"}, {"t": "Larger part = __B1__", "a": {"B1": "42"}}], "sol": "2x = 60, x = 30.\n30 + 12 = 42."}, {"kind": "mcq", "text": "<b>Ex 9C · Q4</b> · When a number is multiplied by 4 and then diminished by 7, the result is 65. Find the number.", "opts": ["14.5", "16", "18", "72"], "correct": 2, "tag": "", "sol": "4x − 7 = 65, 4x = 72, x = 18."}, {"kind": "blank", "p": "<b>Ex 9C · Q5</b> · A number is twice another number. When the larger number is subtracted from 50, the result is 2 more than when the smaller is subtracted from 40. Find the numbers.", "tag": "", "marks": "", "flat": [{"t": "50 − 2x = (40 − x) + 2 gives smaller number x = __B1__", "a": {"B1": "8"}, "expr": "fv"}, {"t": "Larger number = __B1__", "a": {"B1": "16"}}], "sol": "50 − 2x = 42 − x, x = 8.\n2 × 8 = 16. Check: 50 − 16 = 34 and 40 − 8 = 32; 34 = 32 + 2 ✓."}, {"kind": "mcq", "text": "<b>Ex 9C · Q6</b> · In 4 years’ time, a baby will be 5 times as old as she is now. Find the age of the baby.", "opts": ["{4/5} year", "1 year", "5 years", "4 years"], "correct": 1, "tag": "", "sol": "x + 4 = 5x, 4 = 4x, x = 1 year."}, {"kind": "blank", "p": "<b>Ex 9C · Q7</b> · Banu is 20 years older than Binu. In 5 years, Banu will be twice as old as Binu. Find their present ages.", "tag": "", "marks": "", "flat": [{"t": "(x + 20) + 5 = 2(x + 5): Binu = __B1__ years", "a": {"B1": "15"}, "expr": "fv"}, {"t": "Banu = __B1__ years", "a": {"B1": "35"}}], "sol": "x + 25 = 2x + 10, x = 15.\n15 + 20 = 35. Check: in 5 years 40 = 2 × 20 ✓."}, {"kind": "mcq", "text": "<b>Ex 9C · Q8</b> · Manjit is now 12 years old and Mala is two years old. In how many years will Manjit be three times as old as Mala?", "opts": ["6 years", "2 years", "3 years", "5 years"], "correct": 2, "tag": "", "sol": "12 + x = 3(2 + x), 12 + x = 6 + 3x, 6 = 2x, x = 3 years."}, {"kind": "blank", "p": "<b>Ex 9C · Q9</b> · Sheila is now 15 years older than her younger brother Sanjay. Ten years from now, Sheila will be twice as old as Sanjay. Find the present age of each of them.", "tag": "", "marks": "", "flat": [{"t": "(x + 15) + 10 = 2(x + 10): Sanjay = __B1__ years", "a": {"B1": "5"}, "expr": "fv"}, {"t": "Sheila = __B1__ years", "a": {"B1": "20"}}], "sol": "x + 25 = 2x + 20, x = 5.\n5 + 15 = 20. Check: in 10 years 30 = 2 × 15 ✓."}, {"kind": "mcq", "text": "<b>Ex 9C · Q10</b> · Jagdish has three more ₹5 coins than ₹10 coins. If he has ₹195 in total, how many of each kind of coins does he have?", "opts": ["15 coins of ₹10 and 12 coins of ₹5", "11 coins of ₹10 and 14 coins of ₹5", "13 coins of ₹10 and 16 coins of ₹5", "12 coins of ₹10 and 15 coins of ₹5"], "correct": 3, "tag": "", "sol": "₹10 coins x, ₹5 coins x + 3: 10x + 5(x + 3) = 195, 15x = 180, x = 12. So 12 coins of ₹10 and 15 coins of ₹5."}, {"kind": "blank", "p": "<b>Ex 9C · Q11</b> · Sanjiv has ₹60 in 10-rupee and 5-rupee coins. If the 10-rupee coins exceed the number of 5-rupee coins by three, how many coins of each does he have?", "tag": "", "marks": "", "flat": [{"t": "5x + 10(x + 3) = 60: 5-rupee coins = __B1__", "a": {"B1": "2"}, "expr": "fv"}, {"t": "10-rupee coins = __B1__", "a": {"B1": "5"}}], "sol": "15x + 30 = 60, x = 2.\n2 + 3 = 5. Check: 10 + 50 = 60 ✓."}, {"kind": "blank", "p": "<b>Ex 9C · Q12</b> · Find three consecutive numbers (list them in increasing order).", "tag": "", "marks": "", "flat": [{"t": "a) i. sum 48: __B1__", "a": {"B1": "15, 16, 17"}, "expr": "dlist", "accept": ["17, 16, 15"]}, {"t": "a) ii. sum 342: __B1__", "a": {"B1": "113, 114, 115"}, "expr": "dlist", "accept": ["115, 114, 113"]}, {"t": "b) three consecutive even numbers with sum 96: __B1__", "a": {"B1": "30, 32, 34"}, "expr": "dlist", "accept": ["34, 32, 30"]}], "sol": "3x + 3 = 48, x = 15.\n3x + 3 = 342, x = 113.\n3x + 6 = 96, x = 30."}, {"kind": "mcq", "text": "<b>Ex 9C · Q13(a)</b> · How many kilograms of sweets worth ₹110 per kg must be mixed with 30 kg of sweets of ₹80 per kg to produce a mixture which costs ₹100 per kg?", "opts": ["45 kg", "90 kg", "60 kg", "30 kg"], "correct": 2, "tag": "", "sol": "110x + 2400 = 100(x + 30) = 100x + 3000, 10x = 600, x = 60 kg."}, {"kind": "blank", "p": "<b>Ex 9C · Q13(b)</b> · How many kilograms of butter worth ₹140 per kg must be mixed with 20 kg of butter worth ₹150 per kg to produce a mixture worth ₹144 per kg?", "tag": "", "marks": "", "flat": [{"t": "140x + 3000 = 144(x + 20): x = __B1__ kg", "a": {"B1": "30"}, "expr": "fv"}], "sol": "140x + 3000 = 144x + 2880, 120 = 4x, x = 30 kg."}, {"kind": "mcq", "text": "<b>Ex 9C · Q14</b> · Sushil is now 4 times as old as Sunil. Five years ago, Sushil was 7 times as old as Sunil was then. Find the present age of each of them.", "opts": ["Sushil 20 years, Sunil 5 years", "Sushil 40 years, Sunil 10 years", "Sushil 48 years, Sunil 12 years", "Sushil 28 years, Sunil 7 years"], "correct": 1, "tag": "", "sol": "4x − 5 = 7(x − 5), 4x − 5 = 7x − 35, 3x = 30, x = 10. Sunil 10, Sushil 40."}, {"kind": "blank", "p": "<b>Ex 9C · Q15</b> · Sonu’s grandmother is 80 years old and Sonu is 20 years old. How many years ago was his grandmother 7 times as old as Sonu?", "tag": "", "marks": "", "flat": [{"t": "80 − x = 7(20 − x): x = __B1__ years", "a": {"B1": "10"}, "expr": "fv"}], "sol": "80 − x = 140 − 7x, 6x = 60, x = 10 years ago (70 and 10)."}]}, {"id": "s6", "label": "9.6 Solutions, shapes, speed", "sub": "Applications: solutions, rectangles, speed and digits", "slides": [{"kind": "blank", "p": "<b>Example 27</b> · A 50-litre solution of acid and water contains 10 litres of acid. How much water must be added to make the solution 8% acidic?", "tag": "", "marks": "", "flat": [{"t": "(50 + x) × {8/100} = 10 gives x = __B1__ litres", "a": {"B1": "75"}, "expr": "fv"}], "sol": "400 + 8x = 1000, 8x = 600, x = 75 litres. Check: 8% of 125 = 10 ✓."}, {"kind": "mcq", "text": "<b>Example 28</b> · The length of a rectangle exceeds twice its width by 3. Find the length and breadth of the rectangle if its perimeter is 246 m.", "opts": ["length 163 m, breadth 80 m", "length 40 m, breadth 83 m", "length 81 m, breadth 42 m", "length 83 m, breadth 40 m"], "correct": 3, "tag": "", "sol": "Width x, length 2x + 3. 2(2x + 3 + x) = 6x + 6 = 246, 6x = 240, x = 40. Length = 2 × 40 + 3 = 83 m."}, {"kind": "blank", "p": "<b>Example 29</b> · The length of a rectangle exceeds its width by 7 m. If the width is decreased by 3 m and the length is decreased by 10 m, the area is decreased by 95 sq. m. Find the dimensions of the rectangle.", "tag": "", "marks": "", "flat": [{"t": "x(x + 7) = (x − 3)(x − 3) + 95 gives width x = __B1__ m", "a": {"B1": "8"}, "expr": "fv"}, {"t": "Length = __B1__ m", "a": {"B1": "15"}}], "sol": "x<sup>2</sup> + 7x = x<sup>2</sup> − 6x + 9 + 95, 13x = 104, x = 8 m.\n8 + 7 = 15 m.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 280 150\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><text class=\"lb\" x=\"140.0\" y=\"12.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Original rectangle</text><rect x=\"40\" y=\"30\" width=\"170\" height=\"80\" style=\"fill:none;stroke:var(--ink);stroke-width:1.8\"/><text class=\"al\" x=\"125.0\" y=\"128.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x + 7</text><text class=\"al\" x=\"240.0\" y=\"70.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x</text></svg>"}, {"kind": "mcq", "text": "<b>Example 30</b> · Two trains started at the same time from two towns 750 km apart and travelled towards each other at 60 km/h and 90 km/h. After how many hours will they pass each other?", "opts": ["3 hours", "12.5 hours", "25 hours", "5 hours"], "correct": 3, "tag": "", "sol": "Together they cover the 750 km: 60x + 90x = 750, 150x = 750, x = 5 hours."}, {"kind": "blank", "p": "<b>Example 31</b> · Two trains, one travelling 15 km/h faster than the other, leave the same station at the same time, one travelling east and the other west. At the end of 6 hours they are 570 km apart. What is the speed of each train?", "tag": "", "marks": "", "flat": [{"t": "6x + 6(x + 15) = 570: slower train = __B1__ km/h", "a": {"B1": "40"}, "expr": "fv"}, {"t": "Faster train = __B1__ km/h", "a": {"B1": "55"}}], "sol": "12x + 90 = 570, 12x = 480, x = 40 km/h.\n40 + 15 = 55 km/h."}, {"kind": "mcq", "text": "<b>Example 32</b> · A truck travelling at 40 km/h left Delhi. An hour later, a car leaves Delhi and catches up with the truck after four hours. What was the average speed of the car?", "opts": ["60 km/h", "50 km/h", "40 km/h", "45 km/h"], "correct": 1, "tag": "", "sol": "The truck travels 5 hours, the car 4 hours, the same distance: 4x = 5 × 40 = 200, x = 50 km/h."}, {"kind": "blank", "p": "<b>Example 33</b> · The units digit of a 2-digit number is 3. The number is seven times the sum of the digits. Find the number.", "tag": "", "marks": "", "flat": [{"t": "Tens digit x: 7(x + 3) = 10x + 3 gives x = __B1__", "a": {"B1": "6"}, "expr": "fv"}, {"t": "The number = __B1__", "a": {"B1": "63"}}], "sol": "7x + 21 = 10x + 3, 18 = 3x, x = 6.\n10 × 6 + 3 = 63."}, {"kind": "mcq", "text": "<b>Try This · Q1</b> · The length of a rectangle exceeds its width by 2 m. If its perimeter is 20 m, find its dimensions.", "opts": ["length 11 m, width 9 m", "length 6 m, width 4 m", "length 7 m, width 5 m", "length 5 m, width 3 m"], "correct": 1, "tag": "", "sol": "2(x + x + 2) = 20, 4x + 4 = 20, x = 4. Width 4 m, length 6 m."}, {"kind": "blank", "p": "<b>Try This · Q2</b> · A 40-litre solution of alcohol and water contains 10 litres of alcohol. How much alcohol must be added to produce a solution of 50% alcohol?", "tag": "", "marks": "", "flat": [{"t": "10 + x = {50/100} × (40 + x): x = __B1__ litres", "a": {"B1": "20"}, "expr": "fv"}], "sol": "10 + x = 20 + {x/2}, {x/2} = 10, x = 20 litres (then 30 litres of alcohol in 60 litres)."}, {"kind": "mcq", "text": "<b>Ex 9D · Q1</b> · A 60-litre solution of alcohol and water contains 20 litres of alcohol. How much alcohol must be added to produce a solution of 50% alcohol?", "opts": ["20 litres", "30 litres", "40 litres", "10 litres"], "correct": 0, "tag": "", "sol": "20 + x = {1/2}(60 + x), 40 + 2x = 60 + x, x = 20 litres."}, {"kind": "blank", "p": "<b>Ex 9D · Q2</b> · How much salt (in kg) must be added to 60 litres of a 20% solution of salt to increase it to a 40% solution of salt? (Take 1 litre as 1 kg.)", "tag": "", "marks": "", "flat": [{"t": "Salt now = __B1__ kg", "a": {"B1": "12"}}, {"t": "12 + x = {40/100}(60 + x): x = __B1__ kg", "a": {"B1": "20"}, "expr": "fv"}], "sol": "20% of 60 = 12 kg.\n12 + x = 24 + 0.4x, 0.6x = 12, x = 20 kg."}, {"kind": "mcq", "text": "<b>Ex 9D · Q3</b> · The length of a rectangle exceeds its width by 4 m. If its perimeter is 40 m, find its dimensions.", "opts": ["length 14 m, width 10 m", "length 10 m, width 6 m", "length 12 m, width 8 m", "length 22 m, width 18 m"], "correct": 2, "tag": "", "sol": "2(x + x + 4) = 40, 4x + 8 = 40, x = 8. Width 8 m, length 12 m."}, {"kind": "blank", "p": "<b>Ex 9D · Q4</b> · Here is a square. Find the value of x and also the length of the side of the square.", "tag": "", "marks": "", "flat": [{"t": "4x − 7 = 3x + 5, x = __B1__", "a": {"B1": "12"}, "expr": "fv"}, {"t": "Side = __B1__", "a": {"B1": "41"}}], "sol": "The sides of a square are equal: x = 12.\n4 × 12 − 7 = 41 (and 3 × 12 + 5 = 41).", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 280 210\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect x=\"60\" y=\"20\" width=\"150\" height=\"150\" style=\"fill:none;stroke:var(--ink);stroke-width:1.8\"/><path class=\"ra\" d=\"M70.0,170.0 L70.0,160.0 L60.0,160.0\"/><path class=\"ra\" d=\"M210.0,160.0 L200.0,160.0 L200.0,170.0\"/><path class=\"ra\" d=\"M200.0,20.0 L200.0,30.0 L210.0,30.0\"/><path class=\"ra\" d=\"M60.0,30.0 L70.0,30.0 L70.0,20.0\"/><line class=\"ln\" x1=\"60.0\" y1=\"192.0\" x2=\"210.0\" y2=\"192.0\" marker-end=\"url(#ah)\" marker-start=\"url(#ahs)\"/><text class=\"al\" x=\"135.0\" y=\"206.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4x − 7</text><line class=\"ln\" x1=\"232.0\" y1=\"20.0\" x2=\"232.0\" y2=\"170.0\" marker-end=\"url(#ah)\" marker-start=\"url(#ahs)\"/><text class=\"al\" x=\"260.0\" y=\"95.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3x + 5</text></svg>"}, {"kind": "mcq", "text": "<b>Ex 9D · Q5</b> · If one side of a square is increased by 2 metres and the other side is reduced by 2 metres, a rectangle is formed whose perimeter is 48 m. Find the side of the original square.", "opts": ["14 m", "24 m", "12 m", "10 m"], "correct": 2, "tag": "", "sol": "2[(x + 2) + (x − 2)] = 48, 4x = 48, x = 12 m."}, {"kind": "blank", "p": "<b>Ex 9D · Q6</b> · The length of a rectangle exceeds its width by 5 m. If the width is increased by 1 m and the length is decreased by 2 m, the area of the new rectangle is 4 sq. m less than the area of the original rectangle. Find the dimensions of the original rectangle.", "tag": "", "marks": "", "flat": [{"t": "(x + 1)(x + 3) = x(x + 5) − 4: width = __B1__ m", "a": {"B1": "7"}, "expr": "fv"}, {"t": "Length = __B1__ m", "a": {"B1": "12"}}], "sol": "x<sup>2</sup> + 4x + 3 = x<sup>2</sup> + 5x − 4, x = 7 m.\n7 + 5 = 12 m. Check: 8 × 10 = 80 = 84 − 4 ✓."}, {"kind": "mcq", "text": "<b>Ex 9D · Q7</b> · The length of a rectangle exceeds its width by 3 m. If the width is increased by 4 m and the length is decreased by 6 m, the area is decreased by 22 sq. m. Find the dimensions of the rectangle.", "opts": ["width 4 m, length 7 m", "width 8 m, length 11 m", "width 5 m, length 8 m", "width 6 m, length 9 m"], "correct": 2, "tag": "", "sol": "(x + 4)(x − 3) = x(x + 3) − 22: x<sup>2</sup> + x − 12 = x<sup>2</sup> + 3x − 22, 2x = 10, x = 5. Width 5 m, length 8 m (check 9 × 2 = 18 = 40 − 22 ✓)."}, {"kind": "blank", "p": "<b>Ex 9D · Q8</b> · Two cars leave a town at the same time in opposite directions at 50 km/h and 60 km/h. In how many hours will they be 550 km apart?", "tag": "", "marks": "", "flat": [{"t": "50t + 60t = 550, t = __B1__ hours", "a": {"B1": "5"}, "expr": "fv"}], "sol": "110t = 550, t = 5 hours."}, {"kind": "mcq", "text": "<b>Ex 9D · Q9</b> · Two trains start from the same station at 11 p.m. in opposite directions at 72 km/h and 63 km/h. At what time will they be 810 km apart?", "opts": ["5 a.m. (next day)", "4 a.m. (next day)", "5 p.m. (next day)", "6 a.m. (next day)"], "correct": 0, "tag": "", "sol": "72t + 63t = 810, 135t = 810, t = 6 hours. 11 p.m. + 6 hours = 5 a.m."}, {"kind": "blank", "p": "<b>Ex 9D · Q10</b> · The distance between two towns is 458 km. Two trains start from these two stations at the same time and travel towards each other at 45 km/h and 60 km/h. In how many hours will they be 38 km apart?", "tag": "", "marks": "", "flat": [{"t": "45t + 60t = 458 − 38, t = __B1__ hours", "a": {"B1": "4"}, "expr": "fv"}], "sol": "105t = 420, t = 4 hours (before they meet)."}, {"kind": "mcq", "text": "<b>Ex 9D · Q11</b> · Two ships leave their bases, 725 km apart, and travel towards each other at 30 km/h and 35 km/h. In how many hours will they be 75 km apart?", "opts": ["12 hours", "10 hours", "11 hours", "9 hours"], "correct": 1, "tag": "", "sol": "30t + 35t = 725 − 75 = 650, 65t = 650, t = 10 hours."}, {"kind": "blank", "p": "<b>Ex 9D · Q12</b> · A car leaves Agra at 11 a.m. travelling at 50 km/h. How fast would a second car be travelling, if it leaves Agra an hour later and overtakes the first car at 5 p.m. on the same day?", "tag": "", "marks": "", "flat": [{"t": "Distance of the first car by 5 p.m. = __B1__ km", "a": {"B1": "300"}}, {"t": "5x = 300, speed of the second car = __B1__ km/h", "a": {"B1": "60"}, "expr": "fv"}], "sol": "11 a.m. to 5 p.m. is 6 hours: 6 × 50 = 300 km.\nThe second car travels 12 noon to 5 p.m., 5 hours: x = 60 km/h."}, {"kind": "mcq", "text": "<b>Ex 9D · Q13</b> · The sum of the digits of a 2-digit number is 7. If the digits are reversed, the number formed is 9 less than the original number. Find the number.", "opts": ["43", "61", "52", "34"], "correct": 0, "tag": "", "sol": "Tens x, units 7 − x. 10(7 − x) + x = 10x + (7 − x) − 9: 70 − 9x = 9x − 2, 18x = 72, x = 4. The number is 43 (34 = 43 − 9 ✓)."}, {"kind": "blank", "p": "<b>Ex 9D · Q14</b> · The sum of the digits of a 2-digit number is 10. If we reverse the digits, the new number will be 54 more than the original number. What is the original number?", "tag": "", "marks": "", "flat": [{"t": "Tens digit x: 10(10 − x) + x = 10x + (10 − x) + 54 gives x = __B1__", "a": {"B1": "2"}, "expr": "fv"}, {"t": "Original number = __B1__", "a": {"B1": "28"}}], "sol": "100 − 9x = 9x + 64, 18x = 36, x = 2.\nUnits digit 8: the number is 28 (82 = 28 + 54 ✓)."}, {"kind": "mcq", "text": "<b>Ex 9D · Q15</b> · The tens digit of a two-digit number exceeds the units digit by 5. If the digits are reversed, the new number is less by 45. If the sum of their digits is 9, find the number.", "opts": ["72", "27", "81", "63"], "correct": 0, "tag": "", "sol": "Units x, tens x + 5: x + (x + 5) = 9, x = 2, tens 7. The number is 72; reversed 27 = 72 − 45 ✓."}]}, {"id": "s7", "label": "Assessment A", "sub": "Knowing and understanding", "slides": [{"kind": "mcq", "text": "<b>Check-up · MCQ 1</b> · If a whole number is substituted for a, which expression is greatest?", "opts": ["a + 10", "a − 10", "a − 9", "a + 9"], "correct": 0, "tag": "", "sol": "Adding the largest number gives the greatest value: a + 10."}, {"kind": "blank", "p": "<b>Check-up · Q2</b> · Solve for the unknown.", "tag": "", "marks": "", "flat": [{"t": "a) {3/−5}x = 15, x = __B1__", "a": {"B1": "-25"}, "expr": "fv"}, {"t": "b) {4/5}x = {12/25}, x = __B1__", "a": {"B1": "3/5"}, "expr": "fv"}, {"t": "c) {5/8}x = 2.5, x = __B1__", "a": {"B1": "4"}, "expr": "fv"}, {"t": "d) {−13y/2} = 2 × 6, y = __B1__", "a": {"B1": "-24/13"}, "expr": "fv"}], "sol": "x = 15 × ({−5/3}) = −25.\nx = {12/25} × {5/4} = {3/5}.\nx = 2.5 × {8/5} = 4.\n−13y = 24, y = {−24/13}."}, {"kind": "blank", "p": "<b>Check-up · Q4(a–d)</b> · Solve the following.", "tag": "", "marks": "", "flat": [{"t": "a) x + 7 = −17, x = __B1__", "a": {"B1": "-24"}, "expr": "fv"}, {"t": "b) 5x + 3 = 23, x = __B1__", "a": {"B1": "4"}, "expr": "fv"}, {"t": "c) 8x − 7 = −23, x = __B1__", "a": {"B1": "-2"}, "expr": "fv"}, {"t": "d) 16a − 3 = −5, a = __B1__", "a": {"B1": "-1/8"}, "expr": "fv"}], "sol": "x = −17 − 7 = −24.\n5x = 20, x = 4.\n8x = −16, x = −2.\n16a = −2, a = {−1/8}."}, {"kind": "mcq", "text": "<b>Check-up · Q4(e–h)</b> · Solve:  e) {x/5} + 9 = 13   f) {t/3} − 5 = −6   g) {2x/3} − 15 = −7   h) 5x + 8(2x − 9) = 54", "opts": ["e) 110  f) −33  g) 33  h) 6", "e) 20  f) −3  g) 12  h) 6", "e) 20  f) −3  g) {16/3}  h) 6", "e) 20  f) 3  g) 12  h) 6"], "correct": 1, "tag": "", "sol": "e) {x/5} = 4, x = 20. f) {t/3} = −1, t = −3. g) {2x/3} = 8, x = 12. h) 21x − 72 = 54, x = 6."}, {"kind": "blank", "p": "<b>Check-up · Q5(a, c, d)</b> · Solve.", "tag": "", "marks": "", "flat": [{"t": "a) 3x + 4 = 2x + 11, x = __B1__", "a": {"B1": "7"}, "expr": "fv"}, {"t": "c) 5(x − 13) = 10x − (2x + 5), x = __B1__", "a": {"B1": "-20"}, "expr": "fv"}, {"t": "d) 4p − 0.5 = 5p − 0.5, p = __B1__", "a": {"B1": "0"}, "expr": "fv"}], "sol": "x = 11 − 4 = 7.\n5x − 65 = 8x − 5, −60 = 3x, x = −20.\n4p − 5p = 0, p = 0."}, {"kind": "mcq", "text": "<b>Check-up · Q5(b)</b> · Solve (x − 1)/2 − (x − 2)/3 = (x − 4)/7.", "opts": ["x = −17", "x = −31", "x = {−31/7}", "x = 31"], "correct": 1, "tag": "", "sol": "Multiply by 42: 21(x − 1) − 14(x − 2) = 6(x − 4), 21x − 21 − 14x + 28 = 6x − 24, 7x + 7 = 6x − 24, x = −31."}, {"kind": "blank", "p": "<b>Check-up · Q5(e, f)</b> · Solve.", "tag": "", "marks": "", "flat": [{"t": "e) {7/2}(y − 1) = 4 + 3y, y = __B1__", "a": {"B1": "15"}, "expr": "fv"}, {"t": "f) x − (2x − (5x − 1)/3) = (x − 1)/3 + {1/2}, x = __B1__", "a": {"B1": "3/2"}, "expr": "fv"}], "sol": "7y − 7 = 8 + 6y, y = 15.\nLeft side = −x + (5x − 1)/3 = (2x − 1)/3. So (2x − 1)/3 − (x − 1)/3 = {1/2}, {x/3} = {1/2}, x = {3/2}."}, {"kind": "mcq", "text": "<b>HOTS · Q4</b> · With what number should you multiply both sides of each equation to solve it?  a) {3/4}s = 36   b) {2/3}n = 26", "opts": ["a) 4  b) 3", "a) {3/4}  b) {2/3}", "a) {4/3}  b) {2/3}", "a) {4/3}  b) {3/2}"], "correct": 3, "tag": "", "sol": "Multiply by the reciprocal of the coefficient: a) {4/3} gives s = 48. b) {3/2} gives n = 39."}]}, {"id": "s8", "label": "Assessment B", "sub": "Investigating patterns", "slides": [{"kind": "blank", "p": "<b>Check-up · Brain Teaser (a)</b> · A machine: Stage 1 enter a number; Stage 2 doubles it; Stage 3 adds 9; Stage 4 multiplies by 4; Stage 5 prints the result on a ticket. Complete the table.", "tag": "", "marks": "", "flat": [{"t": "i. 4 → __B1__", "a": {"B1": "68"}}, {"t": "ii. 44 → __B1__", "a": {"B1": "388"}}, {"t": "iii. −4 → __B1__", "a": {"B1": "4"}}, {"t": "iv. 0 → __B1__", "a": {"B1": "36"}}], "sol": "4 → 8 → 17 → 68.\n44 → 88 → 97 → 388.\n−4 → −8 → 1 → 4.\n0 → 0 → 9 → 36."}, {"kind": "mcq", "text": "<b>Check-up · Brain Teaser (b)</b> · Can you derive the expression on which the five stages of this machine are based? (n = number entered)", "opts": ["4n + 18", "2(4n + 9) = 8n + 18", "4(2n + 9) = 8n + 36", "8n + 9"], "correct": 2, "tag": "", "sol": "Double: 2n. Add 9: 2n + 9. Multiply by 4: 4(2n + 9) = 8n + 36."}, {"kind": "blank", "p": "<b>Check-up · Brain Teaser (c)</b> · Swap the positions of Stage 2 and Stage 3 (add 9 first, then double). Enter 7 at Stage 1.", "tag": "", "marks": "", "flat": [{"t": "Old machine prints __B1__", "a": {"B1": "92"}}, {"t": "New machine prints __B1__", "a": {"B1": "128"}}, {"t": "Difference = __B1__", "a": {"B1": "36"}}], "sol": "4(2 × 7 + 9) = 4 × 23 = 92.\n4 × 2(7 + 9) = 8 × 16 = 128. (New rule: 8n + 72.)\n128 − 92 = 36, the same for every number since (8n + 72) − (8n + 36) = 36."}, {"kind": "mcq", "text": "<b>HOTS · Q1</b> · If a whole number is substituted for a, which expression is greater?  a) a + 9 or a + 10   b) a − 9 or a − 10   c) a − 10 or a + 9", "opts": ["a) a + 10  b) a − 9  c) a − 10", "a) a + 10  b) a − 10  c) a − 10", "a) a + 9  b) a − 10  c) a + 9", "a) a + 10  b) a − 9  c) a + 9"], "correct": 3, "tag": "", "sol": "Adding more makes a number greater; subtracting less leaves it greater. a) a + 10. b) a − 9. c) a + 9."}, {"kind": "blank", "p": "<b>Check-up · Q6</b> · Find three consecutive even numbers such that the sum of the first and the last numbers exceeds the second number by 10.", "tag": "", "marks": "", "flat": [{"t": "x + (x + 4) = (x + 2) + 10 gives x = __B1__", "a": {"B1": "8"}, "expr": "fv"}, {"t": "The numbers (in increasing order) are __B1__", "a": {"B1": "8, 10, 12"}, "expr": "dlist", "accept": ["12, 10, 8"]}], "sol": "2x + 4 = x + 12, x = 8.\n8, 10, 12. Check: 8 + 12 = 20 = 10 + 10 ✓."}, {"kind": "mcq", "text": "<b>HOTS · Q3</b> · 3a = 100 and 3b = 200. Which is greater, a or b?", "opts": ["b, because b = {200/3} = 2a", "They are equal, because both are 3 times a number", "a, because a = {100/3} and b = {3/200}", "a, because 3a = 100 is a whole number"], "correct": 0, "tag": "", "sol": "a = {100/3} and b = {200/3} = 2a, so b is greater."}, {"kind": "blank", "p": "Three consecutive numbers x, x + 1, x + 2 have the sum 3x + 3 = 3(x + 1), which is 3 × the middle number.", "tag": "", "marks": "", "flat": [{"t": "Sum 60: middle number = __B1__", "a": {"B1": "20"}}, {"t": "Sum 99: middle number = __B1__", "a": {"B1": "33"}}, {"t": "Sum 303: smallest number = __B1__", "a": {"B1": "100"}}], "sol": "60 ÷ 3 = 20 (19, 20, 21).\n99 ÷ 3 = 33 (32, 33, 34).\n303 ÷ 3 = 101 is the middle number, so the smallest is 100."}, {"kind": "mcq", "text": "Using the pattern above, which of these can NOT be the sum of three consecutive whole numbers?", "opts": ["99", "3", "102", "100"], "correct": 3, "tag": "", "sol": "The sum is always 3 × the middle number, a multiple of 3. 100 is not a multiple of 3. (3 = 0 + 1 + 2.)"}]}, {"id": "s9", "label": "Assessment C", "sub": "Communicating", "slides": [{"kind": "mcq", "text": "<b>HOTS · Q5</b> · What is wrong with this solution?  6x − 24 = 30 ⇒ {6x/6} − 24 = {30/6} ⇒ x − 24 = 5 ⇒ x = 29", "opts": ["Only 6x and 30 were divided by 6; −24 was not", "24 should be subtracted, not added, in the last step", "Nothing is wrong; x = 29 is the correct root", "6x should have been divided by 24, not by 6"], "correct": 0, "tag": "", "sol": "Dividing both sides by 6 means dividing every term: x − 4 = 5, x = 9. Or add 24 first: 6x = 54, x = 9."}, {"kind": "blank", "p": "<b>HOTS · Q5</b> · Solve 6x − 24 = 30 correctly.", "tag": "", "marks": "", "flat": [{"t": "Add 24: 6x = __B1__", "a": {"B1": "54"}}, {"t": "x = __B1__", "a": {"B1": "9"}, "expr": "fv"}], "sol": "30 + 24 = 54.\nx = {54/6} = 9. Check: 54 − 24 = 30 ✓."}, {"kind": "mcq", "text": "<b>HOTS · Q2</b> · If m is the marked price of a pair of jeans, d is the discount on it and s is the selling price (after discount), which equation connects m, d and s?", "opts": ["s = m + d", "s = m − d", "m = s − d", "d = m + s"], "correct": 1, "tag": "", "sol": "The selling price is the marked price minus the discount: s = m − d (so m = s + d)."}, {"kind": "blank", "p": "<b>Check-up · Q3</b> · Form an equation and solve.", "tag": "", "marks": "", "flat": [{"t": "a) {2/3} of the total marks is 60. Total marks = __B1__", "a": {"B1": "90"}, "expr": "fv"}, {"t": "b) A man spends {2/5} of his income, i.e. ₹3000, on his food. Income = ₹__B1__", "a": {"B1": "7500"}, "expr": "fv"}, {"t": "c) {2/3} of the students of the school are boys. If there are 800 boys, number of students = __B1__", "a": {"B1": "1200"}, "expr": "fv"}], "sol": "{2/3}x = 60, x = 90.\n{2/5}x = 3000, x = 7500.\n{2/3}x = 800, x = 1200."}, {"kind": "mcq", "text": "Which equation says “When 7 is subtracted from three times a number, the result is 20”?", "opts": ["3(x − 7) = 20", "3x − 7 = 20", "3x = 20 − 7", "7 − 3x = 20"], "correct": 1, "tag": "", "sol": "Three times the number is 3x; subtract 7 from it: 3x − 7 = 20."}, {"kind": "blank", "p": "Complete the explanation for solving 5x + 5 = 20 by transposing.", "tag": "", "marks": "", "flat": [{"t": "+5 moves to the right as −5: 5x = 20 − 5 = __B1__", "a": {"B1": "15"}}, {"t": "Then divide both sides by 5 (the __B1__ of x).", "a": {"B1": "coefficient"}, "expr": "words", "accept": ["coefficient of x"]}, {"t": "x = __B1__", "a": {"B1": "3"}, "expr": "fv"}], "sol": "20 − 5 = 15.\n5 is the coefficient of x.\nx = {15/5} = 3."}, {"kind": "mcq", "text": "Riya solves 3x = 12 like this: “x = 12 − 3 = 9.” What should she have done?", "opts": ["Multiplied both sides by 3, so x = 36", "Divided both sides by 3, so x = 4", "Added 3 to both sides, so x = 15", "Divided 3 by 12, so x = {1/4}"], "correct": 1, "tag": "", "sol": "3x means 3 × x, so undo it by dividing by 3: x = 4. Check: 3 × 4 = 12 ✓."}]}, {"id": "s10", "label": "Assessment D", "sub": "Applying mathematics in real-life contexts", "slides": [{"kind": "blank", "p": "<b>Check-up · Q7</b> · How many kilograms of tea worth ₹300 per kg should be mixed with 10 kg of tea worth ₹240 per kg to produce a mixture costing ₹260 per kg?", "tag": "", "marks": "", "flat": [{"t": "300x + 2400 = 260(x + 10): x = __B1__ kg", "a": {"B1": "5"}, "expr": "fv"}], "sol": "300x + 2400 = 260x + 2600, 40x = 200, x = 5 kg."}, {"kind": "blank", "p": "<b>Check-up · Q8(a)</b> · Ankita started a handicraft business with an investment of ₹7,14,600. The monthly operating cost of her business is given in the table. She hired six people to run the operations. She earned only the operating cost in the first four months. From the fifth month she earned ₹50,000 per month above the operating cost. After how many months did she recover her investment?", "tag": "", "marks": "", "flat": [{"t": "Monthly operating cost = ₹__B1__", "a": {"B1": "155000"}}, {"t": "Number of whole months of ₹50,000 surplus needed = __B1__", "a": {"B1": "15"}}, {"t": "She recovers her investment after __B1__ months", "a": {"B1": "19"}}], "sol": "20,000 + 5000 + 40,000 + 6 × 15,000 = ₹1,55,000.\n714600 ÷ 50000 = 14.292, so 14 months give only ₹7,00,000; the 15th month completes it.\n4 months with no surplus + 15 months = 19 months.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 277 130\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect x=\"4.0\" y=\"4\" width=\"196.0\" height=\"24\" style=\"fill:var(--paper-2);stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"102.0\" y=\"17.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Operations</text><rect x=\"200.0\" y=\"4\" width=\"73.6\" height=\"24\" style=\"fill:var(--paper-2);stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"236.8\" y=\"17.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Expenses</text><rect x=\"4.0\" y=\"28\" width=\"196.0\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"102.0\" y=\"41.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Rent</text><rect x=\"200.0\" y=\"28\" width=\"73.6\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"236.8\" y=\"41.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">₹20,000</text><rect x=\"4.0\" y=\"52\" width=\"196.0\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"102.0\" y=\"65.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Electricity</text><rect x=\"200.0\" y=\"52\" width=\"73.6\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"236.8\" y=\"65.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">₹5000</text><rect x=\"4.0\" y=\"76\" width=\"196.0\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"102.0\" y=\"89.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Overheads</text><rect x=\"200.0\" y=\"76\" width=\"73.6\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"236.8\" y=\"89.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">₹40,000</text><rect x=\"4.0\" y=\"100\" width=\"196.0\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"102.0\" y=\"113.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Average salary per person</text><rect x=\"200.0\" y=\"100\" width=\"73.6\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"236.8\" y=\"113.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">₹15,000</text></svg>"}, {"kind": "mcq", "text": "<b>Check-up · Q8(b)</b> · Ankita hired some more employees once she recovered her investment. If she now has n employees, which expression shows her monthly operating cost (in ₹)?", "opts": ["20,000 + 15,000n", "65,000 + 15,000n", "65,000n + 15,000", "1,55,000n"], "correct": 1, "tag": "", "sol": "Rent + electricity + overheads = 20,000 + 5000 + 40,000 = ₹65,000 each month, plus ₹15,000 for each of the n employees."}, {"kind": "blank", "p": "<b>Check-up · Q8(c)</b> · If her operating cost after hiring is ₹2,15,000 per month, find the total number of employees she has.", "tag": "", "marks": "", "flat": [{"t": "65000 + 15000n = 215000: n = __B1__", "a": {"B1": "10"}, "expr": "fv"}], "sol": "15000n = 150000, n = 10 employees."}, {"kind": "mcq", "text": "<b>Check-up · Everyday Maths Q9</b> · An officer got an increase in salary of ₹2450 on his promotion. Now he has a salary of ₹27,000. What was his earlier salary?", "opts": ["₹25,550", "₹24,550", "₹24,650", "₹29,450"], "correct": 1, "tag": "", "sol": "x + 2450 = 27000, x = ₹24,550."}, {"kind": "mcq", "text": "<b>Check-up · Everyday Maths Q10</b> · A newspaper boy got 42 new customers this month. He is now distributing to 673 customers. How many customers did he have before?", "opts": ["641 (from x + 32 = 673)", "715 (from x − 42 = 673)", "631 (from x + 42 = 673)", "621 (from x + 52 = 673)"], "correct": 2, "tag": "", "sol": "Let the old number be x. x + 42 = 673, so x = 673 − 42 = 631."}, {"kind": "blank", "p": "<b>Check-up · Everyday Maths Q11</b> · In a purse there are ₹20, ₹10 and ₹50 notes. The number of ₹50 notes exceeds two times the ₹10 notes by one. The number of ₹20 notes is 5 less than the number of ₹10 notes. The total value is ₹860. Find the number of each variety of notes.", "tag": "", "marks": "", "flat": [{"t": "10x + 50(2x + 1) + 20(x − 5) = 860: ₹10 notes = __B1__", "a": {"B1": "7"}, "expr": "fv"}, {"t": "₹50 notes = __B1__", "a": {"B1": "15"}}, {"t": "₹20 notes = __B1__", "a": {"B1": "2"}}], "sol": "130x − 50 = 860, 130x = 910, x = 7.\n2 × 7 + 1 = 15.\n7 − 5 = 2. Check: 70 + 750 + 40 = 860 ✓."}, {"kind": "blank", "p": "<b>Computational Thinking · Q1–4</b> · The floor plan of a 2 BHK flat has a rectangular living room, two square bedrooms (same size), two rectangular bathrooms (same size), a rectangular kitchen, a rectangular balcony and some lobby space. The dimensions are in the table. Find (type powers with ^, e.g. 9x^2):", "tag": "", "marks": "", "flat": [{"t": "1) Area of both the bedrooms = __B1__ sq. m", "a": {"B1": "32x^2"}, "expr": true}, {"t": "2) Area of both the bathrooms = __B1__ sq. m", "a": {"B1": "6x^2"}, "expr": true}, {"t": "3) Area of the balcony = __B1__ sq. m", "a": {"B1": "7x^2"}, "expr": true}, {"t": "4) Sum of the living room and kitchen area = __B1__ sq. m", "a": {"B1": "20x^2"}, "expr": true}], "sol": "Each bedroom is 4x × 4x = 16x<sup>2</sup>; two bedrooms: 2 × 16x<sup>2</sup> = 32x<sup>2</sup>.\nEach bathroom is x × 3x = 3x<sup>2</sup>; two bathrooms: 6x<sup>2</sup>.\n7x × x = 7x<sup>2</sup>.\nLiving room 5x × 2.4x = 12x<sup>2</sup>; kitchen 4x × 2x = 8x<sup>2</sup>; sum 20x<sup>2</sup>.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 286 154\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect x=\"4.0\" y=\"4\" width=\"95.2\" height=\"24\" style=\"fill:var(--paper-2);stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"51.6\" y=\"17.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Room</text><rect x=\"99.2\" y=\"4\" width=\"88.0\" height=\"24\" style=\"fill:var(--paper-2);stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"143.2\" y=\"17.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Length (m)</text><rect x=\"187.2\" y=\"4\" width=\"95.2\" height=\"24\" style=\"fill:var(--paper-2);stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"234.8\" y=\"17.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Breadth (m)</text><rect x=\"4.0\" y=\"28\" width=\"95.2\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"51.6\" y=\"41.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Bedroom</text><rect x=\"99.2\" y=\"28\" width=\"88.0\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"143.2\" y=\"41.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4x</text><rect x=\"187.2\" y=\"28\" width=\"95.2\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"234.8\" y=\"41.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4x</text><rect x=\"4.0\" y=\"52\" width=\"95.2\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"51.6\" y=\"65.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Living room</text><rect x=\"99.2\" y=\"52\" width=\"88.0\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"143.2\" y=\"65.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5x</text><rect x=\"187.2\" y=\"52\" width=\"95.2\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"234.8\" y=\"65.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2.4x</text><rect x=\"4.0\" y=\"76\" width=\"95.2\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"51.6\" y=\"89.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Kitchen</text><rect x=\"99.2\" y=\"76\" width=\"88.0\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"143.2\" y=\"89.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4x</text><rect x=\"187.2\" y=\"76\" width=\"95.2\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"234.8\" y=\"89.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2x</text><rect x=\"4.0\" y=\"100\" width=\"95.2\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"51.6\" y=\"113.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Bathroom</text><rect x=\"99.2\" y=\"100\" width=\"88.0\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"143.2\" y=\"113.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x</text><rect x=\"187.2\" y=\"100\" width=\"95.2\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"234.8\" y=\"113.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3x</text><rect x=\"4.0\" y=\"124\" width=\"95.2\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"51.6\" y=\"137.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Balcony</text><rect x=\"99.2\" y=\"124\" width=\"88.0\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"143.2\" y=\"137.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">7x</text><rect x=\"187.2\" y=\"124\" width=\"95.2\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"234.8\" y=\"137.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x</text></svg>"}, {"kind": "mcq", "text": "<b>Computational Thinking · Q5</b> · If the total area of the flat is 70x<sup>2</sup> sq. m, find the area of the lobby space. (Use the table of room sizes.)", "opts": ["5x<sup>2</sup> sq. m", "21x<sup>2</sup> sq. m", "14x<sup>2</sup> sq. m", "8x<sup>2</sup> sq. m"], "correct": 0, "tag": "", "sol": "Rooms: bedrooms 32x<sup>2</sup> + bathrooms 6x<sup>2</sup> + balcony 7x<sup>2</sup> + living room and kitchen 20x<sup>2</sup> = 65x<sup>2</sup>. Lobby = 70x<sup>2</sup> − 65x<sup>2</sup> = 5x<sup>2</sup>. (21x<sup>2</sup> counts only one bedroom and one bathroom; 8x<sup>2</sup> forgets the balcony.)", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 286 154\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect x=\"4.0\" y=\"4\" width=\"95.2\" height=\"24\" style=\"fill:var(--paper-2);stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"51.6\" y=\"17.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Room</text><rect x=\"99.2\" y=\"4\" width=\"88.0\" height=\"24\" style=\"fill:var(--paper-2);stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"143.2\" y=\"17.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Length (m)</text><rect x=\"187.2\" y=\"4\" width=\"95.2\" height=\"24\" style=\"fill:var(--paper-2);stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"234.8\" y=\"17.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Breadth (m)</text><rect x=\"4.0\" y=\"28\" width=\"95.2\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"51.6\" y=\"41.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Bedroom</text><rect x=\"99.2\" y=\"28\" width=\"88.0\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"143.2\" y=\"41.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4x</text><rect x=\"187.2\" y=\"28\" width=\"95.2\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"234.8\" y=\"41.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4x</text><rect x=\"4.0\" y=\"52\" width=\"95.2\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"51.6\" y=\"65.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Living room</text><rect x=\"99.2\" y=\"52\" width=\"88.0\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"143.2\" y=\"65.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5x</text><rect x=\"187.2\" y=\"52\" width=\"95.2\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"234.8\" y=\"65.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2.4x</text><rect x=\"4.0\" y=\"76\" width=\"95.2\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"51.6\" y=\"89.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Kitchen</text><rect x=\"99.2\" y=\"76\" width=\"88.0\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"143.2\" y=\"89.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4x</text><rect x=\"187.2\" y=\"76\" width=\"95.2\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"234.8\" y=\"89.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2x</text><rect x=\"4.0\" y=\"100\" width=\"95.2\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"51.6\" y=\"113.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Bathroom</text><rect x=\"99.2\" y=\"100\" width=\"88.0\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"143.2\" y=\"113.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x</text><rect x=\"187.2\" y=\"100\" width=\"95.2\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"234.8\" y=\"113.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3x</text><rect x=\"4.0\" y=\"124\" width=\"95.2\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"51.6\" y=\"137.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Balcony</text><rect x=\"99.2\" y=\"124\" width=\"88.0\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"143.2\" y=\"137.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">7x</text><rect x=\"187.2\" y=\"124\" width=\"95.2\" height=\"24\" style=\"fill:none;stroke:var(--ink);stroke-width:1\"/><text class=\"lb\" x=\"234.8\" y=\"137.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x</text></svg>"}, {"kind": "blank", "p": "<b>Computational Thinking · Q6</b> · For x = 1 m, find the values of the expressions obtained in parts 1–5.", "tag": "", "marks": "", "flat": [{"t": "1) Both bedrooms = __B1__ sq. m", "a": {"B1": "32"}}, {"t": "2) Both bathrooms = __B1__ sq. m", "a": {"B1": "6"}}, {"t": "3) Balcony = __B1__ sq. m", "a": {"B1": "7"}}, {"t": "4) Living room + kitchen = __B1__ sq. m", "a": {"B1": "20"}}, {"t": "5) Lobby = __B1__ sq. m", "a": {"B1": "5"}}], "sol": "32 × 1<sup>2</sup> = 32.\n6 × 1<sup>2</sup> = 6.\n7 × 1<sup>2</sup> = 7.\n20 × 1<sup>2</sup> = 20.\n5 × 1<sup>2</sup> = 5. Check: 32 + 6 + 7 + 20 + 5 = 70 ✓."}]}];
/* ================= build slide lists ================= */
var SLIDES = {}; SECTIONS.forEach(function(sec){ SLIDES[sec.id]=sec.slides; });
var TAB_DEFS = SECTIONS.map(function(sec){ return {id:sec.id, label:sec.label, sub:sec.sub}; });

/* ================= state ================= */
function blankItem(slide){
  if(slide.kind==='mcq'||slide.kind==='ar'){
    return {status:'unanswered', attempts:0, choice:undefined};
  }
  return {status:'unanswered', curStep:0, stepStates: slide.flat.map(function(){ return {status:'unanswered', attempts:0, inputs:{}}; })};
}
function defaultState(){
  var s={tabs:{}};
  TAB_DEFS.forEach(function(td){
    s.tabs[td.id] = { idx:0, maxReached:0, items: SLIDES[td.id].map(function(sl){ return blankItem(sl); }) };
  });
  return s;
}
var appState = {mode:null, learning:null, quiz:null};
var state = null;      // alias for appState[appState.mode]
var MODE = null;
var activeTab=TAB_DEFS[0].id;

function setMode(m){
  appState.mode = m;
  if(!appState[m]) appState[m] = defaultState();
  state = appState[m];
  MODE = m;
}
/* ================= student accounts (saved on this device) ================= */
var SHEET_KEY='sopaan-c8-ch9';
var ACC_KEY='sopaan-students-v1';
var storageOK=true;
var MEM={};
function lsGet(k){ var r=null; try{ r=localStorage.getItem(k); }catch(e){ storageOK=false; }
  if(r===null||r===undefined) r=MEM[k]||null; try{ return r?JSON.parse(r):null; }catch(e){ return null; } }
function lsSet(k,v){ var j=JSON.stringify(v); MEM[k]=j; try{ localStorage.setItem(k,j); return true; }catch(e){ storageOK=false; return false; } }
try{ localStorage.setItem('sopaan-probe','1'); localStorage.removeItem('sopaan-probe'); }catch(e){ storageOK=false; }
function hashPin(pin,salt){ var h=2166136261, str=salt+'|'+pin; for(var i=0;i<str.length;i++){ h^=str.charCodeAt(i); h=Math.imul(h,16777619)>>>0; } return h.toString(36); }
function accKey(name,roll){ return (name.trim().toLowerCase().replace(/\s+/g,' ')+'#'+roll.trim().toLowerCase()); }
function accounts(){ return lsGet(ACC_KEY)||{students:{}}; }
var student=null; // {key,name,roll}
var records=[];   // finished-tab history for this student on this sheet
function progKey(){ return SHEET_KEY+'::'+student.key; }

function loadState(){
  appState = {mode:null, learning:null, quiz:null}; records=[]; activeTab=TAB_DEFS[0].id;
  var saved=lsGet(progKey());
  if(!saved) return;
  try{
    ['learning','quiz'].forEach(function(m){
      if(saved[m] && saved[m].tabs){
        var fresh = defaultState();
        TAB_DEFS.forEach(function(td){
          if(saved[m].tabs[td.id] && saved[m].tabs[td.id].items && saved[m].tabs[td.id].items.length===SLIDES[td.id].length){
            fresh.tabs[td.id] = saved[m].tabs[td.id];
          }
        });
        appState[m] = fresh;
      }
    });
    if(saved.mode==='learning' || saved.mode==='quiz') appState.mode = saved.mode;
    if(saved.activeTab && TAB_DEFS.some(function(t){ return t.id===saved.activeTab; })) activeTab = saved.activeTab;
    if(Array.isArray(saved.records)) records = saved.records;
  }catch(e){}
}
function saveState(){
  if(!student) return;
  lsSet(progKey(), {mode:appState.mode, learning:appState.learning, quiz:appState.quiz, activeTab:activeTab, records:records, updated:Date.now()});
  var acc=accounts(); if(acc.students[student.key]){ acc.students[student.key].last=Date.now(); lsSet(ACC_KEY,acc); }
}
function addRecord(mode, tabId, correct, revealed, skipped, total){
  records.unshift({at:Date.now(), mode:mode, tab:tabId, correct:correct, revealed:revealed, skipped:skipped, total:total});
  if(records.length>60) records.length=60;
  saveState();
}
function fmtDate(ms){ try{ return new Date(ms).toLocaleString(undefined,{day:'numeric',month:'short',hour:'2-digit',minute:'2-digit'}); }catch(e){ return ''; } }

function renderWho(){
  var el=document.getElementById('whoBar');
  if(!student){ el.hidden=true; el.innerHTML=''; return; }
  el.hidden=false;
  el.innerHTML='Signed in as <b>'+esc(student.name)+'</b> · Roll '+esc(student.roll)+
    ' <button id="btnRecord">My record</button> <button id="btnSignOut">Sign out</button>';
  document.getElementById('btnRecord').addEventListener('click', renderRecord);
  document.getElementById('btnSignOut').addEventListener('click', signOut);
}
function signOut(){
  saveState(); student=null; state=null; MODE=null;
  var acc=accounts(); delete acc.current; lsSet(ACC_KEY,acc);
  document.getElementById('modePill').hidden=true;
  renderWho(); renderLogin();
}
function signIn(key){
  var acc=accounts(); var st=acc.students[key]; if(!st) return;
  student={key:key, name:st.name, roll:st.roll};
  acc.current=key; st.last=Date.now(); lsSet(ACC_KEY,acc);
  loadState(); renderWho();
  if(appState.mode==='learning' || appState.mode==='quiz'){
    setMode(appState.mode); document.getElementById('modePill').hidden=false; updateModePill();
    showChrome(true); buildTabbar(); renderSlide();
    showToast('Welcome back, '+st.name.split(' ')[0]+'. Picking up where you left off.');
  } else {
    renderModePicker();
  }
}
function renderLogin(msg){
  showChrome(false);
  var acc=accounts(); var keys=Object.keys(acc.students).sort(function(a,b){ return (acc.students[b].last||0)-(acc.students[a].last||0); });
  var h='<div class="login-card"><h2>Student sign-in</h2>'+
    '<p class="lead">Sign in to save your answers, see your record and continue where you left off next time.</p>';
  if(!storageOK) h+='<div class="login-err">This browser is blocking saved data (for example, a private window). You can still practise, but progress will not be kept after you close the page.</div>';
  if(msg) h+='<div class="login-err">'+esc(msg)+'</div>';
  if(keys.length){
    h+='<div class="known"><span class="known-label">Continue as</span>';
    keys.slice(0,6).forEach(function(k){ var st=acc.students[k];
      h+='<button class="known-btn" data-k="'+esc(k)+'"><span>'+esc(st.name)+' <small>· Roll '+esc(st.roll)+'</small></span><small>'+(st.last?'Last active '+fmtDate(st.last):'')+'</small></button>'; });
    h+='</div>';
  }
  h+='<form id="loginForm" novalidate>'+
    '<div class="fld"><label for="lgName">Full name</label><input id="lgName" autocomplete="name" required></div>'+
    '<div class="fld-row"><div class="fld"><label for="lgRoll">Roll no.</label><input id="lgRoll" required></div>'+
    '<div class="fld"><label for="lgPin">4-digit PIN</label><input id="lgPin" type="password" inputmode="numeric" maxlength="4" autocomplete="off" required></div></div>'+
    '<button class="btn btn-primary" type="submit" style="width:100%;">Sign in</button>'+
    '<p class="login-note">New here? Enter your name, roll no. and a PIN you will remember, and your profile is created. Progress is saved on this device, so use the same device and browser to continue.</p>'+
    '</form></div>';
  var wrap=document.getElementById('wrap'); wrap.innerHTML=h;
  wrap.querySelectorAll('.known-btn').forEach(function(b){
    b.addEventListener('click', function(){
      var st=accounts().students[b.dataset.k];
      document.getElementById('lgName').value=st.name; document.getElementById('lgRoll').value=st.roll;
      document.getElementById('lgPin').focus();
    });
  });
  document.getElementById('loginForm').addEventListener('submit', function(e){
    e.preventDefault();
    var name=document.getElementById('lgName').value.trim(), roll=document.getElementById('lgRoll').value.trim(), pin=document.getElementById('lgPin').value.trim();
    if(!name||!roll){ renderLoginErr('Enter your name and roll no.'); return; }
    if(!/^\d{4}$/.test(pin)){ renderLoginErr('Your PIN must be exactly 4 digits.'); return; }
    var k=accKey(name,roll); var acc=accounts();
    if(acc.students[k]){
      if(acc.students[k].pin!==hashPin(pin,k)){ renderLoginErr('That PIN does not match this name and roll no. Try again.'); return; }
    } else {
      acc.students[k]={name:name.replace(/\s+/g,' '), roll:roll, pin:hashPin(pin,k), created:Date.now()};
      lsSet(ACC_KEY,acc);
    }
    signIn(k);
  });
}
function renderLoginErr(m){
  var n=document.getElementById('lgName').value, r=document.getElementById('lgRoll').value;
  renderLogin(m); document.getElementById('lgName').value=n; document.getElementById('lgRoll').value=r; document.getElementById('lgPin').focus();
}
function tabSummary(m){
  var st=appState[m]; if(!st) return null;
  return TAB_DEFS.map(function(td){
    var items=st.tabs[td.id].items, n=items.length;
    var c=items.filter(function(i){return i.status==='correct';}).length;
    var done=items.filter(function(i){return i.status!=='unanswered';}).length;
    return {label:td.label, n:n, done:done, correct:c};
  });
}
function renderRecord(){
  showChrome(false);
  var tabLabel=function(id){ var t=TAB_DEFS.find(function(x){return x.id===id;}); return t?t.label:id; };
  var h='<div class="rec-card"><h2>'+esc(student.name)+'’s record</h2><p class="rec-empty" style="margin:0 0 12px;">Roll '+esc(student.roll)+' · Linear Equations in One Variable</p>';
  ['learning','quiz'].forEach(function(m){
    var sum=tabSummary(m);
    h+='<h3>'+(m==='learning'?'📘 Learning Sheet':'📝 Quiz Mode')+'</h3>';
    if(!sum){ h+='<p class="rec-empty">Not started yet.</p>'; return; }
    h+='<div class="rec-table-wrap"><table class="rec-table"><thead><tr><th>Section</th><th>Progress</th><th>Correct first time</th></tr></thead><tbody>';
    sum.forEach(function(r){ var pct=Math.round(r.done/r.n*100);
      h+='<tr><td>'+r.label+'</td><td><span class="rec-bar"><i style="width:'+pct+'%"></i></span>'+r.done+' / '+r.n+'</td><td>'+(m==='quiz'?'—':r.correct+' / '+r.n)+'</td></tr>'; });
    h+='</tbody></table></div>';
  });
  h+='</div><div class="rec-card"><h3>Finished sections</h3>';
  if(!records.length){ h+='<p class="rec-empty">No sections finished yet. Each time you finish a tab, your score is recorded here.</p>'; }
  else {
    h+='<div class="rec-table-wrap"><table class="rec-table"><thead><tr><th>When</th><th>Mode</th><th>Section</th><th>Score</th></tr></thead><tbody>';
    records.forEach(function(r){ h+='<tr><td>'+fmtDate(r.at)+'</td><td>'+(r.mode==='quiz'?'Quiz':'Learning')+'</td><td>'+tabLabel(r.tab)+'</td><td>'+r.correct+' / '+r.total+(r.mode==='learning'?' <span class="rec-empty">('+r.revealed+' revealed, '+r.skipped+' skipped)</span>':'')+'</td></tr>'; });
    h+='</tbody></table></div>';
  }
  h+='</div><button class="btn btn-primary" id="btnBack">'+(MODE?'Back to practice':'Choose a mode')+'</button>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('btnBack').addEventListener('click', function(){
    if(MODE){ showChrome(true); buildTabbar(); renderSlide(); } else renderModePicker();
  });
  window.scrollTo({top:0});
}

/* ================= tab bar ================= */
function buildTabbar(){
  var el=document.getElementById('tabbar');
  el.innerHTML = '<button class="tab-btn'+(activeTab==='theory'?' active':'')+'" data-tab="theory">Theory<span class="tab-count">notes</span></button>' + TAB_DEFS.map(function(t){
    return '<button class="tab-btn'+(t.id===activeTab?' active':'')+'" data-tab="'+t.id+'">'+t.label+'<span class="tab-count">'+SLIDES[t.id].length+'</span></button>';
  }).join('') + '<button class="tab-btn'+(activeTab==='report'?' active':'')+'" data-tab="report">📊 Report<span class="tab-count">pie</span></button>';
  el.querySelectorAll('.tab-btn').forEach(function(btn){
    btn.addEventListener('click', function(){ activeTab=btn.dataset.tab; buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); });
  });
}

/* ================= rendering ================= */
function canProceed(item){ return item.status==='correct'||item.status==='revealed'||item.status==='skipped'; }

function renderSlide(){
  if(!state.tabs[activeTab]){ activeTab=TAB_DEFS[0].id; }
  var ts = state.tabs[activeTab];
  var slides = SLIDES[activeTab];
  if(ts.idx>=slides.length||ts.idx<0) ts.idx=0;
  var idx = ts.idx;
  var slide = slides[idx];
  var item = ts.items[idx];

  var tdef=TAB_DEFS.find(function(t){return t.id===activeTab;});
  document.getElementById('spLabel').textContent = tdef.label+' · Question '+(idx+1)+' of '+slides.length;
  document.getElementById('secSub').textContent = tdef.label+' — '+tdef.sub;
  document.getElementById('spFill').style.width = Math.round(((idx)/(Math.max(slides.length-1,1)))*100)+'%';

  var h='<div class="qcard">';
  if(slide.kind==='mcq' || slide.kind==='ar'){
    h += renderChoiceBody(slide, item, idx);
  } else {
    h += renderBlankBody(slide, item, idx);
  }
  h += '<div class="feedback" id="feedbackBox"></div>';
  if(MODE==='learning' && (item.status==='correct'||item.status==='revealed')) h += solutionHTML(slide);
  h += '</div>';

  document.getElementById('wrap').innerHTML = h;
  wireSlideEvents(slide, item, idx);
  restoreFeedback(item);
  renderNavbar(item);
  updateFab();
  saveState();
}

function solutionHTML(slide){
  if(!slide.sol) return '';
  return '<div class="solution"><div class="sol-h">Solution</div>'+slide.sol.split('\n').map(function(l){ return '<div class="sol-line">'+fr(esc(l))+'</div>'; }).join('')+'</div>';
}
var LETTERS=['a','b','c','d','e','f'];
function chosenHTML(slide,item){
  var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
  if(item.choice===undefined) return '';
  var ok=item.choice===slide.correct;
  var h='<div class="chosen '+(ok?'ok':'bad')+'"><b>Your answer:</b> ('+LETTERS[item.choice]+') '+fr(esc(opts[item.choice]))+(ok?' ✓':' ✗')+'</div>';
  if(!ok) h+='<div class="chosen ok"><b>Correct answer:</b> ('+LETTERS[slide.correct]+') '+fr(esc(opts[slide.correct]))+'</div>';
  return h;
}
function renderChoiceBody(slide, item, idx){
  var h='<div class="qhead"><div class="qnum">'+(idx+1)+'</div>';
  if(slide.kind==='mcq'){
    h += '<div class="qtext">'+fr(esc(slide.text))+(slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  } else {
    h += '<div class="qtext"><span class="qtag" style="margin-left:0;margin-right:6px;">A / R</span>Assertion (A): '+fr(esc(slide.a))+'<br>Reason (R): '+fr(esc(slide.r))+(slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  }
  h += '</div>';
  if(slide.fig) h += '<div class="fig">'+slide.fig+'</div>';
  var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
  if(MODE==='quiz') h += '<div class="quiz-hint">Quiz mode — pick an option. The correct answer is revealed once you finish this tab.</div>';
  var locked = MODE==='learning' && (item.status==='correct' || item.status==='revealed');
  h += '<div class="options">';
  opts.forEach(function(opt,i){
    var cls='opt';
    if(locked){
      if(i===slide.correct) cls+=' is-correct';
      else if(item.choice===i) cls+=' is-wrong';
      cls+=' locked';
    }
    if(item.choice===i) cls+=' is-chosen';
    h += '<label class="'+cls+'"><input type="radio" name="choice" value="'+i+'" '+(item.choice===i?'checked':'')+' '+(locked?'disabled':'')+'> <span class="opt-l">('+LETTERS[i]+')</span> <span class="opt-t">'+fr(esc(opt))+'</span>'+(item.choice===i?'<span class="opt-tag">'+(locked?(i===slide.correct?'Your answer ✓':'Your answer ✗'):'Selected')+'</span>':'')+'</label>';
  });
  h += '</div>';
  if(locked) h += chosenHTML(slide,item);
  return h;
}

function renderBlankBody(slide, item, idx){
  var h='<div class="qhead"><div class="qnum">'+(idx+1)+'</div><div class="qtext">';
  if(slide.kind==='case'){ h += '<b>'+esc(slide.title)+'.</b> '+esc(slide.body); }
  else { var pp=fr(esc(slide.p)).split('\n'); h += pp[0]+pp.slice(1).map(function(x){return '<span class="datline">'+x+'</span>';}).join(''); }
  h += (slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  if(slide.marks) h += '<div class="marks-pill">'+slide.marks+'</div>';
  h += '</div>';
  if(slide.fig) h += '<div class="fig">'+slide.fig+'</div>';

  var total = slide.flat.length;
  var hasExpr = slide.flat.some(function(s){ return s.expr===true; });
  var hasFrac = slide.flat.some(function(s){ return ['fv','fe','fl','fm','fi','flist'].indexOf(s.expr)>=0; });
  var blankCount=0; slide.flat.forEach(function(s){ blankCount+=Object.keys(s.a).length; });

  if(MODE==='quiz'){
    h += '<div class="step-badge">'+blankCount+' blank'+(blankCount===1?'':'s')+' in this question</div>';
    h += '<div class="quiz-hint">Quiz mode — fill in what you can. Correct answers are revealed once you finish this tab.</div>';
    if(hasFrac) h += '<div class="quiz-hint">Type fractions like <b>3/4</b> and mixed numbers like <b>2 3/4</b> (whole number, space, fraction).</div>';
    if(hasExpr) h += '<div class="quiz-hint">Type answers like <b>2x-5</b>, <b>x^2-4</b> or <b>3+2i</b>. Use ^ for powers, | | for absolute value and pi for π. Any equivalent form is accepted.</div>';
    h += '<div class="steps">';
    for(var qi=0; qi<total; qi++){
      var qstep = slide.flat[qi];
      var qss = item.stepStates[qi];
      if(qstep.partLabel) h += '<div class="subpart-label">'+esc(qstep.partLabel)+'</div>';
      if(qstep.orDivider) h += '<div class="or-divider">OR</div>';
      var qline = fr(qstep.t);
      Object.keys(qstep.a).forEach(function(bkey){
        var val = qss.inputs[bkey]||'';
        var inp='<input class="blank-input'+(['fv','fe','fl','fm','fi','dec'].indexOf(qstep.expr)>=0?' fr':(qstep.expr==='flist'||qstep.expr==='dlist'||qstep.expr==='glist')?' wide':qstep.expr===true?' expr':(qstep.expr==='words'||qstep.expr==='list'||qstep.expr==='expanded'||qstep.expr==='set'||qstep.expr==='primes'||qstep.expr==='trans'||qstep.expr==='rot'?' wide':''))+'" data-step="'+qi+'" data-bkey="'+bkey+'" value="'+esc(val)+'">';
        qline = qline.replace('__'+bkey+'__', inp);
      });
      if(qstep.fig) h += '<div class="fig">'+qstep.fig+'</div>';
      h += '<div class="step-line">'+qline+'</div>';
    }
    h += '</div>';
    return h;
  }

  if(hasFrac) h += '<div class="quiz-hint">Type fractions like <b>3/4</b> and mixed numbers like <b>2 3/4</b> (whole number, space, fraction).</div>';
  if(hasExpr) h += '<div class="quiz-hint">Type answers like <b>2x-5</b>, <b>x^2-4</b> or <b>3+2i</b>. Use ^ for powers, | | for absolute value and pi for π. Any equivalent form is accepted.</div>';
  var locked = item.status==='correct' || item.status==='revealed';
  var upto = locked ? total-1 : item.curStep;
  h += '<div class="step-badge">Step '+(Math.min(item.curStep,total-1)+1)+' of '+total+'</div>';
  h += '<div class="steps">';
  for(var i=0;i<=upto;i++){
    var step = slide.flat[i];
    var ss = item.stepStates[i];
    if(step.partLabel) h += '<div class="subpart-label">'+esc(step.partLabel)+'</div>';
    if(step.orDivider) h += '<div class="or-divider">OR</div>';
    var resolved = ss.status==='correct' || ss.status==='revealed';
    var line = fr(step.t);
    Object.keys(step.a).forEach(function(bkey){
      var fs = ss.inputs['fs_'+bkey];
      var cls = fs==='correct'?'is-correct':(fs==='wrong'?'is-wrong':'');
      var val = ss.inputs[bkey]||'';
      var dis = resolved ? 'disabled':'';
      var inp='<input class="blank-input '+cls+(['fv','fe','fl','fm','fi','dec'].indexOf(step.expr)>=0?' fr':(step.expr==='flist'||step.expr==='dlist'||step.expr==='glist')?' wide':step.expr===true?' expr':(step.expr==='words'||step.expr==='list'||step.expr==='expanded'||step.expr==='set'||step.expr==='primes'||step.expr==='trans'||step.expr==='rot'?' wide':''))+'" data-step="'+i+'" data-bkey="'+bkey+'" value="'+esc(val)+'" '+dis+'>';
      line = line.replace('__'+bkey+'__', inp);
    });
    if(step.fig) h += '<div class="fig">'+step.fig+'</div>';
    h += '<div class="step-line'+(resolved?' resolved':'')+'">'+line+'</div>';
    if(ss.status==='revealed'){
      var reveals=[];
      Object.keys(step.a).forEach(function(bkey){ reveals.push(bkey+' = '+esc(step.a[bkey])); });
      h += '<div class="reveal-note">correct: '+reveals.join(', ')+'</div>';
    }
  }
  h += '</div>';
  return h;
}

var __flash=null;
function restoreFeedback(item){
  var fb=document.getElementById('feedbackBox'); if(!fb) return;
  if(__flash){ fb.className='feedback show '+__flash.c; fb.innerHTML=__flash.h; __flash=null; return; }
  if(MODE==='quiz'){ fb.className='feedback'; fb.innerHTML=''; return; }
  if(item.status==='correct'){ fb.className='feedback show ok'; fb.innerHTML='<b>All done — correct!</b>'; }
  else if(item.status==='revealed'){ fb.className='feedback show reveal'; fb.innerHTML='<b>Answer revealed above.</b> Move on whenever you’re ready.'; }
  else if(item.status==='skipped'){ fb.className='feedback show retry'; fb.innerHTML='Skipped — you can answer it now and press <b>Check</b>, or come back later from the Question Palette.'; }
  else { fb.className='feedback'; fb.innerHTML=''; }
}

function slideIsAnswered(slide,item){
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice!==undefined;
  return item.stepStates.some(function(ss){ return Object.keys(ss.inputs).some(function(k){ return k.indexOf('fs_')!==0 && ss.inputs[k] && String(ss.inputs[k]).trim()!==''; }); });
}
function renderNavbar(item){
  var ts = state.tabs[activeTab];
  var slides = SLIDES[activeTab];
  var slide = slides[ts.idx];
  var isLast = ts.idx === slides.length-1;
  var h='';
  h += '<button class="btn" id="btnPrev" '+(ts.idx===0?'disabled':'')+'>&larr; Previous</button>';

  if(MODE==='quiz'){
    h += '<button class="btn" id="btnSkip">Skip</button>';
    h += '<span class="spacer"></span>';
    h += '<button class="btn btn-primary" id="btnNext">'+(isLast?'Finish':'Next →')+'</button>';
  } else {
    h += '<button class="btn" id="btnSkip" '+(item.status!=='unanswered'?'disabled':'')+'>Skip</button>';
    h += '<span class="spacer"></span>';
    h += '<button class="btn btn-primary" id="btnCheck" '+((item.status!=='unanswered'&&item.status!=='skipped')?'disabled':'')+'>Check</button>';
    h += '<button class="btn btn-primary" id="btnNext" '+(canProceed(item)?'':'disabled')+'>'+(isLast?'Finish':'Next →')+'</button>';
  }
  document.getElementById('navbarInner').innerHTML = h;

  document.getElementById('btnPrev').addEventListener('click', function(){ if(ts.idx>0){ ts.idx--; renderSlide(); } });

  if(MODE==='quiz'){
    document.getElementById('btnSkip').addEventListener('click', function(){
      item.status='skipped';
      advanceQuiz(ts, slides);
    });
    document.getElementById('btnNext').addEventListener('click', function(){
      item.status = slideIsAnswered(slide,item) ? 'answered' : 'unanswered';
      advanceQuiz(ts, slides);
    });
  } else {
    document.getElementById('btnSkip').addEventListener('click', function(){
      if(item.status==='unanswered'){ item.status='skipped'; renderSlide(); }
    });
    document.getElementById('btnNext').addEventListener('click', function(){
      if(!canProceed(item)) return;
      if(ts.idx < slides.length-1){ ts.idx++; ts.maxReached=Math.max(ts.maxReached, ts.idx); renderSlide(); }
      else { renderFinished(); }
    });
    document.getElementById('btnCheck').addEventListener('click', function(){ handleCheck(); });
  }
}
function advanceQuiz(ts, slides){
  if(ts.idx < slides.length-1){ ts.idx++; ts.maxReached=Math.max(ts.maxReached, ts.idx); renderSlide(); }
  else { renderFinished(); }
}

function wireSlideEvents(slide, item, idx){
  document.querySelectorAll('input[type="radio"][name="choice"]').forEach(function(r){
    r.addEventListener('change', function(){ item.choice=parseInt(r.value,10); saveState();
      document.querySelectorAll('.opt').forEach(function(l){ l.classList.remove('is-chosen'); var t=l.querySelector('.opt-tag'); if(t) t.remove(); });
      var lab=r.closest('.opt'); lab.classList.add('is-chosen'); var tg=document.createElement('span'); tg.className='opt-tag'; tg.textContent='Selected'; lab.appendChild(tg); });
  });
  document.querySelectorAll('.blank-input').forEach(function(inp){
    inp.addEventListener('input', function(){
      var si=parseInt(inp.dataset.step,10), bk=inp.dataset.bkey;
      item.stepStates[si].inputs[bk]=inp.value;
      saveState();
    });
  });
}

function handleCheck(){
  var ts = state.tabs[activeTab];
  var slide = SLIDES[activeTab][ts.idx];
  var item = ts.items[ts.idx];
  if(item.status==='skipped') item.status='unanswered';
  var fb = document.getElementById('feedbackBox');

  if(slide.kind==='mcq' || slide.kind==='ar'){
    if(item.choice===undefined){ fb.className='feedback show err'; fb.innerHTML='Please choose an option first.'; return; }
    var ok = item.choice===slide.correct;
    if(ok){
      item.status='correct'; playSuccess();
      fb.className='feedback show ok'; fb.innerHTML='<b>Correct!</b>';
    } else {
      item.attempts=(item.attempts||0)+1;
      if(item.attempts>=2){ item.status='revealed'; playReveal(); }
      else { playWrong(); fb.className='feedback show retry'; fb.innerHTML='<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'; __flash={c:'retry',h:'<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'}; }
    }
    renderSlide();
    return;
  }

  // blank / case
  var step = slide.flat[item.curStep];
  var ss = item.stepStates[item.curStep];
  var blanks = Object.keys(step.a);
  var missing = blanks.some(function(k){ return !ss.inputs[k] || String(ss.inputs[k]).trim()===''; });
  if(missing){ fb.className='feedback show err'; fb.innerHTML='Fill in every blank in this step before checking.'; return; }

  var allGood=true;
  blanks.forEach(function(k){
    var good=answerMatches(ss.inputs[k], step.a[k], step.accept, step.expr);
    ss.inputs['fs_'+k]=good?'correct':'wrong';
    if(!good) allGood=false;
  });

  if(allGood){
    ss.status='correct'; playSuccess();
    advanceStepOrFinish(item, slide);
  } else {
    ss.attempts=(ss.attempts||0)+1;
    if(ss.attempts>=2){
      ss.status='revealed'; playReveal();
      advanceStepOrFinish(item, slide);
    } else {
      playWrong();
      fb.className='feedback show retry';
      fb.innerHTML='<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'; __flash={c:'retry',h:'<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'};
      renderSlide();
      return;
    }
  }
  renderSlide();
}

function advanceStepOrFinish(item, slide){
  var total = slide.flat.length;
  var hasExpr = slide.flat.some(function(s){ return s.expr===true; });
  var hasFrac = slide.flat.some(function(s){ return ['fv','fe','fl','fm','fi','flist'].indexOf(s.expr)>=0; });
  if(item.curStep < total-1){
    item.curStep++;
  } else {
    var anyRevealed = item.stepStates.some(function(ss){ return ss.status==='revealed'; });
    item.status = anyRevealed ? 'revealed' : 'correct';
  }
}

/* ================= palette ================= */
var overlay=document.getElementById('overlay');
function statusOf(tabId,i){
  var ts=state.tabs[tabId];
  if(i>ts.maxReached) return 'locked';
  if(i===ts.idx) return 'current';
  return ts.items[i].status==='unanswered' ? 'locked' : ts.items[i].status;
}
function buildPalette(){
  var slides=SLIDES[activeTab];
  document.getElementById('paletteTitle').textContent = TAB_DEFS.find(function(t){return t.id===activeTab;}).label+' · Question palette';
  var body=document.getElementById('paletteBody');
  var html='';
  for(var i=0;i<slides.length;i++){
    html += '<div class="chip" data-status="'+statusOf(activeTab,i)+'" data-idx="'+i+'">'+(i+1)+'</div>';
  }
  body.innerHTML = html;
  body.querySelectorAll('.chip').forEach(function(chip){
    chip.addEventListener('click', function(){
      var i=parseInt(chip.dataset.idx,10);
      var ts=state.tabs[activeTab];
      if(i>ts.maxReached){ showToast('Finish the earlier questions to unlock this one.'); return; }
      ts.idx=i; closePalette(); renderSlide();
    });
  });
}
function openPalette(){ buildPalette(); overlay.classList.add('show'); }
function closePalette(){ overlay.classList.remove('show'); }
var toastTimer;
function showToast(msg){
  var t=document.getElementById('toast'); t.textContent=msg; t.classList.add('show');
  clearTimeout(toastTimer); toastTimer=setTimeout(function(){ t.classList.remove('show'); },2200);
}
document.getElementById('paletteFab').addEventListener('click', openPalette);
document.getElementById('paletteClose').addEventListener('click', closePalette);
overlay.addEventListener('click', function(e){ if(e.target===overlay) closePalette(); });

function updateFab(){
  var slides=SLIDES[activeTab];
  var done=state.tabs[activeTab].items.filter(function(it){ return it.status==='correct'||it.status==='revealed'||it.status==='skipped'; }).length;
  document.getElementById('fabBadge').textContent = done+'/'+slides.length;
}

/* ================= overall progress + finish ================= */
function updateChapterProgress(){
  var total=0, done=0;
  TAB_DEFS.forEach(function(td){
    state.tabs[td.id].items.forEach(function(it){
      total++;
      if(it.status==='correct'||it.status==='revealed'||it.status==='skipped') done++;
    });
  });
  var pct = total>0 ? Math.round((done/total)*100) : 0;
  document.getElementById('cpFill').style.width=pct+'%';
  document.getElementById('cpLabel').textContent=pct+'% complete';
}
function isSlideCorrect(tabId,i){
  var slide=SLIDES[tabId][i], item=state.tabs[tabId].items[i];
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice===slide.correct;
  return slide.flat.every(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).every(function(k){ return answerMatches(ss.inputs[k], step.a[k], step.accept, step.expr); });
  });
}
function isSlideAttempted(tabId,i){
  var slide=SLIDES[tabId][i], item=state.tabs[tabId].items[i];
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice!==undefined;
  return slide.flat.some(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).some(function(k){ return ss.inputs[k] && String(ss.inputs[k]).trim()!==''; });
  });
}
function slideLabel(slide){
  var t = slide.kind==='case' ? slide.title : (slide.kind==='ar' ? slide.a : (slide.p||slide.text||''));
  t = String(t);
  return t.length>90 ? t.slice(0,90)+'…' : t;
}
function slideAnswerText(slide, item, correctSide){
  if(slide.kind==='mcq'||slide.kind==='ar'){
    var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
    if(correctSide) return '('+LETTERS[slide.correct]+') '+opts[slide.correct];
    return item.choice!==undefined ? '('+LETTERS[item.choice]+') '+opts[item.choice] : '— not attempted —';
  }
  return slide.flat.map(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).map(function(k){
      return correctSide ? step.a[k] : (ss.inputs[k] || '—');
    }).join(', ');
  }).join('  |  ');
}

function renderFinished(){
  if(MODE==='quiz'){ renderQuizResults(); return; }
  var ts=state.tabs[activeTab];
  var correct=ts.items.filter(function(i){return i.status==='correct';}).length;
  var revealed=ts.items.filter(function(i){return i.status==='revealed';}).length;
  var skipped=ts.items.filter(function(i){return i.status==='skipped';}).length;
  var h='<div class="qcard done-card"><div class="big">✨</div><h2>Tab complete</h2>';
  h+='<p style="color:var(--ink-soft);font-size:14px;">You worked through all '+ts.items.length+' questions in this tab.</p>';
  if(!ts.recorded){ ts.recorded=true; addRecord('learning', activeTab, correct, revealed, skipped, ts.items.length); }
  h+='<div class="score-pills">'+
     '<span class="score-pill" style="background:var(--success-soft);color:var(--success);">'+correct+' correct</span>'+
     '<span class="score-pill" style="background:var(--danger-soft);color:var(--danger);">'+revealed+' revealed</span>'+
     '<span class="score-pill" style="background:var(--gold-soft);color:var(--retry-text);">'+skipped+' skipped</span></div>'+
     '<button class="btn btn-primary" id="btnReview">Review from question 1</button></div>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('navbarInner').innerHTML='';
  document.getElementById('btnReview').addEventListener('click', function(){ ts.idx=0; ts.recorded=false; renderSlide(); });
  updateChapterProgress(); saveState();
}

function renderQuizResults(){
  var ts=state.tabs[activeTab];
  var slides=SLIDES[activeTab];
  var correctCount=0, attemptedCount=0;
  var rowsHtml = slides.map(function(slide,i){
    var item=ts.items[i];
    var ok=isSlideCorrect(activeTab,i);
    var att=isSlideAttempted(activeTab,i);
    if(ok) correctCount++;
    if(att) attemptedCount++;
    var tagCls = ok?'ok':(att?'bad':'na');
    var tagText = ok?'Correct':(att?'Incorrect':'Not attempted');
    var row='<div class="review-row">';
    row+='<span class="review-tag '+tagCls+'">Q'+(i+1)+' · '+tagText+'</span>';
    row+='<div class="review-q">'+fr(esc(slideLabel(slide)))+'</div>';
    row+='<div class="review-ans"><b>Your answer:</b> '+fr(esc(slideAnswerText(slide,item,false)))+'</div>';
    if(!ok) row+='<div class="review-ans" style="color:var(--success);"><b>Correct answer:</b> '+fr(esc(slideAnswerText(slide,item,true)))+'</div>';
    if(slide.sol) row+='<details class="rev-sol"><summary>Show solution</summary>'+solutionHTML(slide)+'</details>';
    row+='</div>';
    return row;
  }).join('');

  addRecord('quiz', activeTab, correctCount, 0, 0, slides.length);
  var h='<div class="qcard done-card" style="text-align:left;">';
  h+='<div style="text-align:center;"><div class="big">🏁</div><h2>Quiz complete</h2>';
  h+='<p style="color:var(--ink-soft);font-size:14px;">'+correctCount+' / '+slides.length+' correct · '+attemptedCount+' attempted</p></div>';
  h+='<div style="margin-top:16px;">'+rowsHtml+'</div>';
  h+='<div style="text-align:center;margin-top:6px;"><button class="btn btn-primary" id="btnReview">Review from question 1</button></div>';
  h+='</div>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('navbarInner').innerHTML='';
  document.getElementById('btnReview').addEventListener('click', function(){ ts.idx=0; renderSlide(); });
  playSuccess();
  updateChapterProgress(); saveState();
}

/* ================= mode picker ================= */
function updateModePill(){
  var btn=document.getElementById('modePill');
  if(!btn) return;
  btn.textContent = MODE==='quiz' ? '📝 Quiz Mode · switch' : '📘 Learning Sheet · switch';
}
function showChrome(show){
  document.querySelector('.tabbar').style.display = show?'':'none';
  document.querySelector('.slide-progress').style.display = show?'':'none';
  document.querySelector('.navbar').style.display = show?'':'none';
  document.getElementById('paletteFab').style.display = show?'':'none';
}
function renderModePicker(){
  showChrome(false);
  var wrap=document.getElementById('wrap');
  wrap.innerHTML =
    '<div class="mode-pick">'+
      '<div class="mode-card" data-pick="learning"><div class="mode-icon">📘</div><h3>Learning Sheet</h3>'+
      '<p>Work through each question step by step with instant feedback — two tries, then the correct value is revealed right there so you can keep moving.</p></div>'+
      '<div class="mode-card" data-pick="quiz"><div class="mode-icon">📝</div><h3>Quiz Mode</h3>'+
      '<p>Attempt every question with no hints along the way. Your score and the full answer key are shown together once you finish the tab — just like the real exam.</p></div>'+
    '</div>';
  wrap.querySelectorAll('[data-pick]').forEach(function(card){
    card.addEventListener('click', function(){
      setMode(card.dataset.pick); activeTab='theory';
      document.getElementById('modePill').hidden=false;
      updateModePill();
      showChrome(true);
      buildTabbar();
      renderSlide();
    });
  });
}
document.getElementById('modePill').addEventListener('click', function(){
  if(!appState.mode){ return; }
  setMode(appState.mode==='quiz' ? 'learning' : 'quiz');
  updateModePill();
  showChrome(true);
  buildTabbar();
  renderSlide();
});

/* ================= boot ================= */
var _origRenderSlide = renderSlide;
renderSlide = function(){ _origRenderSlide(); updateChapterProgress(); updateModePill(); };


/* ================= theory tab ================= */
function renderTheory(){
  var wrap=document.getElementById('wrap');
  wrap.innerHTML='<div class="theory">'+fr(THEORY)+'</div>';
  document.querySelector('.slide-progress').style.display='none';
  document.querySelector('.navbar').style.display='none';
  document.getElementById('paletteFab').style.display='none';
  document.getElementById('secSub').textContent='Theory — notes, key ideas and worked examples';
  wrap.querySelectorAll('[data-go]').forEach(function(b){ b.addEventListener('click',function(){ activeTab=b.dataset.go; buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); }); });
  wrap.querySelectorAll('[data-jump]').forEach(function(b){ b.addEventListener('click',function(){ var t=document.getElementById(b.dataset.jump); if(t) t.scrollIntoView({behavior:'smooth',block:'start'}); }); });
}
var _rsTheory = renderSlide;
renderSlide = function(){
  if(activeTab==='theory'){ renderTheory(); buildTabbar(); updateChapterProgress(); updateModePill(); saveState(); return; }
  document.querySelector('.slide-progress').style.display='';
  document.querySelector('.navbar').style.display='';
  document.getElementById('paletteFab').style.display='';
  _rsTheory();
};


/* ================= MYP criterion report ================= */
var CRIT_COL={A:'var(--accent-text)',B:'var(--gold)',C:'#8A6FC4',D:'#2F9AA0'};
function critStats(){
  return REPORT.map(function(r){
    var tabId=r[0], slides=SLIDES[tabId], ts=state&&state.tabs[tabId];
    var c=0,w=0,n=0;
    slides.forEach(function(sl,i){
      if(!ts||!ts.items[i]){ n++; return; }
      var it=ts.items[i];
      if(MODE==='learning'){
        if(it.status==='correct') c++; else if(it.status==='revealed') w++; else n++;
      } else {
        if(isSlideCorrect(tabId,i)) c++; else if(isSlideAttempted(tabId,i)) w++; else n++;
      }
    });
    var tot=slides.length, pct=tot?Math.round(c/tot*100):0;
    var lvl=Math.round(c/Math.max(tot,1)*8);
    return {tab:tabId,letter:r[1],name:r[2],c:c,w:w,n:n,tot:tot,pct:pct,lvl:lvl};
  });
}
function arcPath(cx,cy,r,a0,a1){
  if(a1-a0>=Math.PI*2-1e-6){ return 'M'+(cx-r)+','+cy+' a'+r+','+r+' 0 1,0 '+(2*r)+',0 a'+r+','+r+' 0 1,0 '+(-2*r)+',0 Z'; }
  var x0=cx+r*Math.sin(a0), y0=cy-r*Math.cos(a0), x1=cx+r*Math.sin(a1), y1=cy-r*Math.cos(a1);
  return 'M'+cx+','+cy+' L'+x0.toFixed(2)+','+y0.toFixed(2)+' A'+r+','+r+' 0 '+((a1-a0)>Math.PI?1:0)+',1 '+x1.toFixed(2)+','+y1.toFixed(2)+' Z';
}
function pieSVG(parts,size,hole,center,sub){
  var tot=parts.reduce(function(s,p){return s+p.v;},0), cx=size/2, cy=size/2, r=size/2-4, a=0, h='';
  if(!tot){ h+='<circle cx="'+cx+'" cy="'+cy+'" r="'+r+'" style="fill:var(--paper-2);stroke:var(--rule)"/>'; }
  parts.forEach(function(p){ if(!p.v) return; var b=a+p.v/tot*Math.PI*2; h+='<path d="'+arcPath(cx,cy,r,a,b)+'" style="fill:'+p.col+';stroke:var(--card);stroke-width:2"><title>'+esc(p.label)+': '+p.v+'</title></path>'; a=b; });
  if(hole) h+='<circle cx="'+cx+'" cy="'+cy+'" r="'+(r*hole)+'" style="fill:var(--card)"/>';
  if(center) h+='<text x="'+cx+'" y="'+(cy-(sub?4:0))+'" text-anchor="middle" dominant-baseline="middle" style="fill:var(--ink);font:700 '+(size>150?22:15)+'px Fraunces,serif">'+center+'</text>';
  if(sub) h+='<text x="'+cx+'" y="'+(cy+16)+'" text-anchor="middle" style="fill:var(--ink-soft);font:600 11px \'Source Sans 3\',sans-serif">'+sub+'</text>';
  return '<svg viewBox="0 0 '+size+' '+size+'" width="'+size+'" height="'+size+'" role="img">'+h+'</svg>';
}
function band(l){ return l===0?'0':(l<=2?'1–2':(l<=4?'3–4':(l<=6?'5–6':'7–8'))); }
function renderReport(){
  var st=critStats(), totC=0, totQ=0;
  st.forEach(function(s){ totC+=s.c; totQ+=s.tot; });
  var h='<div class="theory">';
  h+='<section class="note"><h2>Chapter test report</h2><p class="lt">'+(MODE==='quiz'?'<b>Quiz mode</b> results: answers are marked when you finish each test tab.':'<b>Learning mode</b> results: a question counts as correct only if you got it without the answer being revealed. Switch to Quiz mode for an exam-style score.')+'</p>';
  h+='<div class="rep-top"><div class="rep-pie">'+pieSVG(st.map(function(s){return {v:s.c,col:CRIT_COL[s.letter],label:'Criterion '+s.letter};}),200,0.55,totC+'/'+totQ,'correct')+'</div>';
  h+='<div class="rep-legend"><div class="rep-cap">Marks earned, by criterion</div>'+st.map(function(s){ return '<div class="rep-li"><span class="sw" style="background:'+CRIT_COL[s.letter]+'"></span><b>'+s.letter+'</b>&nbsp;'+esc(s.name)+'<span class="rep-n">'+s.c+' / '+s.tot+'</span></div>'; }).join('')+'</div></div></section>';
  h+='<div class="rep-grid">'+st.map(function(s){
    return '<div class="rep-card"><div class="rep-h"><span class="crit" style="background:'+CRIT_COL[s.letter]+'">'+s.letter+'</span>'+esc(s.name)+'</div>'+
      '<div class="rep-row">'+pieSVG([{v:s.c,col:'var(--success)',label:'Correct'},{v:s.w,col:'var(--danger)',label:'Incorrect'},{v:s.n,col:'var(--locked)',label:'Not attempted'}],120,0.5,s.pct+'%')+
      '<div class="rep-stats"><div><span class="sw" style="background:var(--success)"></span>Correct <b>'+s.c+'</b></div><div><span class="sw" style="background:var(--danger)"></span>Incorrect <b>'+s.w+'</b></div><div><span class="sw" style="background:var(--locked)"></span>Not attempted <b>'+s.n+'</b></div>'+
      '<div class="rep-lvl">Indicative level <b>'+s.lvl+'</b> / 8 <span>(band '+band(s.lvl)+')</span></div></div></div>'+
      '<button class="hub-btn" data-go="'+s.tab+'">Open Test '+s.letter+' →</button></div>';
  }).join('')+'</div>';
  h+='<p class="rep-note">Indicative level = fraction of questions correct × 8, rounded. It is a practice guide only; your teacher awards the real MYP criterion levels.</p></div>';
  var wrap=document.getElementById('wrap'); wrap.innerHTML=h;
  document.querySelector('.slide-progress').style.display='none';
  document.querySelector('.navbar').style.display='none';
  document.getElementById('paletteFab').style.display='none';
  document.getElementById('secSub').textContent='Report — chapter test results by MYP criterion';
  wrap.querySelectorAll('[data-go]').forEach(function(b){ b.addEventListener('click',function(){ activeTab=b.dataset.go; buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); }); });
}
var _rsReport = renderSlide;
renderSlide = function(){
  if(activeTab==='report'){ renderReport(); buildTabbar(); updateChapterProgress(); updateModePill(); saveState(); return; }
  _rsReport();
};


/* ================= skipped-question return ================= */
function firstSkippedIdx(ts){
  for(var i=0;i<ts.items.length;i++){
    var it=ts.items[i];
    if(MODE==='quiz'){ if(!isSlideAttempted(activeTab,i)) return i; }
    else if(it.status==='skipped'||it.status==='unanswered') return i;
  }
  return -1;
}
function skippedList(ts){
  var out=[]; for(var i=0;i<ts.items.length;i++){ var it=ts.items[i];
    if(MODE==='quiz' ? !isSlideAttempted(activeTab,i) : (it.status==='skipped'||it.status==='unanswered')) out.push(i); }
  return out;
}
function renderSkipGate(ts){
  var list=skippedList(ts);
  var h='<div class="qcard done-card"><div class="big">⏭️</div><h2>You skipped '+list.length+' question'+(list.length>1?'s':'')+'</h2>'+
    '<p style="color:var(--ink-soft);font-size:14px;">Answer them now, or submit the tab as it is. Answers are marked only when you submit.</p>'+
    '<div class="skip-chips">'+list.map(function(i){ return '<button class="chip skip-go" data-i="'+i+'">Q'+(i+1)+'</button>'; }).join('')+'</div>'+
    '<div class="skip-btns"><button class="btn btn-primary" id="btnGoSkipped">Answer skipped questions</button><button class="btn" id="btnSubmitAnyway">Submit anyway</button></div></div>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('navbarInner').innerHTML='';
  var go=function(i){ ts.idx=i; ts.maxReached=Math.max(ts.maxReached,i); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); };
  document.getElementById('btnGoSkipped').addEventListener('click',function(){ go(list[0]); });
  document.querySelectorAll('.skip-go').forEach(function(b){ b.addEventListener('click',function(){ go(parseInt(b.dataset.i,10)); }); });
  document.getElementById('btnSubmitAnyway').addEventListener('click',function(){ ts.submitOK=true; renderFinished(); ts.submitOK=false; });
  saveState();
}
var _rfSkip = renderFinished;
renderFinished = function(){
  var ts=state.tabs[activeTab];
  if(MODE==='quiz' && !ts.submitOK && skippedList(ts).length){ renderSkipGate(ts); return; }
  _rfSkip();
  if(MODE==='learning'){
    var list=skippedList(ts);
    if(list.length){
      var card=document.querySelector('.done-card');
      if(card){ var d=document.createElement('div'); d.className='skip-btns';
        d.innerHTML='<button class="btn btn-primary" id="btnGoSkipped">Attempt skipped questions ('+list.length+')</button>';
        card.appendChild(d);
        document.getElementById('btnGoSkipped').addEventListener('click',function(){ ts.idx=list[0]; ts.recorded=false; renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); }); }
    }
  }
};


/* ================= approx answers (physics: within 1%) ================= */
var _amTools = answerMatches;
answerMatches = function(input,answer,accept,expr){
  if(expr==='approx'){
    var n1=parseNum(input); if(n1===null) return false;
    return [answer].concat(accept||[]).some(function(a){ var n2=parseNum(a); if(n2===null) return false; return Math.abs(n1-n2) <= Math.max(0.011*Math.abs(n2), 1e-9); });
  }
  return _amTools(input,answer,accept,expr);
};

/* ================= palette: every question already reached can be opened ================= */
statusOf = function(tabId,i){
  var ts=state.tabs[tabId];
  if(i>ts.maxReached) return 'locked';
  if(i===ts.idx) return 'current';
  var s=ts.items[i].status;
  if(s==='unanswered') return 'skipped';
  return s;
};

/* ================= on-screen keyboard ================= */
var KB={on:true, page:'num', target:null};
try{ var kbp=localStorage.getItem('sopaan-kb-pref'); if(kbp==='off') KB.on=false; }catch(e){}
function kbSave(){ try{ localStorage.setItem('sopaan-kb-pref', KB.on?'on':'off'); }catch(e){} }
var KEYS_NUM=[['7','8','9','(',')'],['4','5','6','−','/'],['1','2','3','.',','],['0',':','%','°','⌫'],['abc','←','→','Clear','Done']];
var KEYS_FRAC=[['7','8','9','/'],['4','5','6','−'],['1','2','3','space'],['0',',','⌫','Clear'],['abc','←','→','Done']];
var KEYS_ALG=[['7','8','9','x','y','n'],['4','5','6','+','−','a'],['1','2','3','×','÷','b'],['0','.','(',')','^','²'],['/','π','|','t','⌫','Clear'],['abc','←','→','Done']];
function kbLayoutFor(inp){ try{ var ts=state.tabs[activeTab], sl=SLIDES[activeTab][ts.idx], stp=sl.flat[parseInt(inp.dataset.step,10)]; var m=stp.expr, key=String(stp.a[inp.dataset.bkey]||'');
  if(m==='words'||m==='glist'||m==='angle') return 'abc'; if(m===true||m==='pow'||m==='primes') return 'alg';
  if(['fv','fe','fl','fm','fi','flist'].indexOf(m)>=0) return 'frac'; if(m==='dec'||m==='approx'||m==='dlist'||m==='set'||m==='coord'||m==='list'||m==='time') return 'num';
  if(/^[\-−]?\d+ \d+\/\d+$/.test(key)||/^[\-−]?\d+\/\d+$/.test(key)) return 'frac'; if(/[a-df-z]/i.test(key.replace(/pi/gi,''))) return /\d/.test(key)?'alg':'abc'; return 'num'; }catch(e){ return 'num'; } }
var KEYS_ABC=[['q','w','e','r','t','y','u','i','o','p'],['a','s','d','f','g','h','j','k','l','-'],['z','x','c','v','b','n','m',',',':','/'],['123','space','←','→','⌫','Done']];
function kbBuild(){
  var el=document.getElementById('vkb'); if(!el){ el=document.createElement('div'); el.id='vkb'; el.className='vkb'; document.body.appendChild(el);
    el.addEventListener('pointerdown',function(e){ var b=e.target.closest('button[data-k]'); e.preventDefault(); if(b) kbPress(b.dataset.k); });
    el.addEventListener('mousedown',function(e){ e.preventDefault(); }); }
  var rows={num:KEYS_NUM,frac:KEYS_FRAC,alg:KEYS_ALG,abc:KEYS_ABC}[KB.page]||KEYS_NUM;
  el.innerHTML='<div class="vkb-top"><span>⌨️ Keyboard</span><button data-k="device" class="vkb-link">Use device keyboard</button></div>'+
    rows.map(function(r){ return '<div class="vkb-row">'+r.map(function(k){
      var cls='vkb-k'+(/^(abc|123|Done|Clear|⌫|←|→|space)$/.test(k)?' fn':'')+(k==='Done'?' done':'');
      return '<button type="button" class="'+cls+'" data-k="'+k+'">'+(k==='space'?'space':k)+'</button>'; }).join('')+'</div>'; }).join('');
  return el;
}
function kbShow(inp){ KB.target=inp; KB.home=kbLayoutFor(inp); KB.page=KB.home; if(!KB.on) return; var cp=document.getElementById('calcPanel'); if(cp&&cp.classList.contains('show')) return; var el=kbBuild(); var nb=document.querySelector('.navbar'); el.style.bottom=(nb?nb.getBoundingClientRect().height:0)+'px'; el.classList.add('show'); document.body.classList.add('kb-open'); setTimeout(function(){ var r=inp.getBoundingClientRect(), top=el.getBoundingClientRect().top; if(r.bottom>top-12) window.scrollBy({top:r.bottom-top+60,behavior:'smooth'}); else if(r.top<60) window.scrollBy({top:r.top-80,behavior:'smooth'}); },30); }
function kbHide(){ var el=document.getElementById('vkb'); if(el) el.classList.remove('show'); document.body.classList.remove('kb-open'); }
function kbInsert(s){
  var t=KB.target; if(!t||t.disabled) return;
  var a=t.selectionStart==null?t.value.length:t.selectionStart, b=t.selectionEnd==null?a:t.selectionEnd;
  t.value=t.value.slice(0,a)+s+t.value.slice(b); var p=a+s.length; try{ t.setSelectionRange(p,p); }catch(e){}
  t.dispatchEvent(new Event('input',{bubbles:true}));
}
function kbPress(k){
  var t=KB.target; if(k==='device'){ KB.on=false; kbSave(); kbHide(); document.querySelectorAll('.blank-input').forEach(function(i){ i.removeAttribute('inputmode'); }); if(t){ t.blur(); setTimeout(function(){ t.focus(); },50); } showToast('Device keyboard on. Tap ⌨️ on any blank to bring the on-screen keyboard back.'); return; }
  if(k==='Done'){ kbHide(); if(t) t.blur(); return; }
  if(k==='abc'||k==='123'){ KB.page=(k==='abc')?'abc':(KB.home&&KB.home!=='abc'?KB.home:'num'); kbBuild(); return; }
  if(!t) return;
  if(k==='⌫'){ var a=t.selectionStart, b=t.selectionEnd; if(a===b&&a>0){ t.value=t.value.slice(0,a-1)+t.value.slice(b); try{t.setSelectionRange(a-1,a-1);}catch(e){} } else { t.value=t.value.slice(0,a)+t.value.slice(b); try{t.setSelectionRange(a,a);}catch(e){} } t.dispatchEvent(new Event('input',{bubbles:true})); return; }
  if(k==='Clear'){ t.value=''; t.dispatchEvent(new Event('input',{bubbles:true})); return; }
  if(k==='←'||k==='→'){ var p=(t.selectionStart||0)+(k==='←'?-1:1); p=Math.max(0,Math.min(t.value.length,p)); try{t.setSelectionRange(p,p);}catch(e){} return; }
  var map={'−':'-','space':' '}; kbInsert(map[k]!==undefined?map[k]:k);
}
function kbWire(){
  document.querySelectorAll('.blank-input').forEach(function(inp){
    if(inp.dataset.kb) return; inp.dataset.kb='1';
    if(KB.on) inp.setAttribute('inputmode','none');
    inp.addEventListener('focus',function(){ kbShow(inp); });
    var btn=document.createElement('button'); btn.type='button'; btn.className='kb-toggle'; btn.title='On-screen keyboard'; btn.textContent='⌨️'; btn.tabIndex=-1;
    btn.addEventListener('mousedown',function(e){ e.preventDefault(); });
    btn.addEventListener('click',function(){ KB.on=true; kbSave(); document.querySelectorAll('.blank-input').forEach(function(i){ i.setAttribute('inputmode','none'); }); inp.focus(); kbShow(inp); });
    if(!inp.disabled) inp.insertAdjacentElement('afterend',btn);
  });
}
document.addEventListener('focusout',function(e){ setTimeout(function(){ var a=document.activeElement; if(!a||!a.classList||!a.classList.contains('blank-input')){ if(!document.querySelector('#vkb:hover')) kbHide(); } },120); });

/* ================= calculator ================= */
var CALC={expr:'', ans:0};
function calcEval(src){
  var s=String(src).replace(/×/g,'*').replace(/÷/g,'/').replace(/−/g,'-').replace(/π/g,'(PI)').replace(/Ans/g,'('+CALC.ans+')').replace(/\^/g,'**').replace(/√\(/g,'sqrt(').replace(/²/g,'**2').replace(/E/g,'*10**');
  s=s.replace(/(^|[(*\/+\-,])-/g,'$1(-1)*');
  if(/[^0-9+\-*/().,a-z A-Z]/.test(s)) throw 0;
  var ok=s.replace(/sin|cos|tan|asin|acos|atan|sqrt|log|ln|PI|abs/g,''); if(/[a-zA-Z]/.test(ok)) throw 0;
  var f=new Function('sin','cos','tan','asin','acos','atan','sqrt','log','ln','PI','abs','return ('+s+');');
  var d=Math.PI/180;
  var v=f(function(x){return Math.sin(x*d);},function(x){return Math.cos(x*d);},function(x){return Math.tan(x*d);},
    function(x){return Math.asin(x)/d;},function(x){return Math.acos(x)/d;},function(x){return Math.atan(x)/d;},Math.sqrt,Math.log10,Math.log,Math.PI,Math.abs);
  if(typeof v!=='number'||!isFinite(v)) throw 0; return v;
}
function fmtNum(v){ if(Math.abs(v)>=1e10||(Math.abs(v)<1e-6&&v!==0)) return v.toExponential(6).replace(/\.?0+e/,'e'); return String(parseFloat(v.toPrecision(10))); }
var CKEYS=[['sin(','cos(','tan(','√(','^','²'],['asin(','acos(','atan(','(',')','π'],['7','8','9','÷','⌫','AC'],['4','5','6','×','E','Ans'],['1','2','3','−','(−)','Insert'],['0','.','=','+']];
function openCalc(){
  var p=document.getElementById('calcPanel');
  if(!p){ p=document.createElement('div'); p.id='calcPanel'; p.className='tool-panel calc';
    p.innerHTML='<div class="tp-head"><b>🧮 Calculator</b><span class="tp-note">degrees · tap a blank, then Insert</span><button class="tp-x" data-c="close">✕</button></div>'+
      '<div class="calc-disp"><div class="calc-expr" id="calcExpr"></div><div class="calc-res" id="calcRes">0</div></div>'+
      '<div class="calc-keys">'+CKEYS.map(function(r){ return r.map(function(k){ return '<button type="button" data-c="'+k+'" class="'+(k==='='?'eq':(/^(AC|⌫|Insert)$/.test(k)?'fn':''))+'">'+({'sin(':'sin','cos(':'cos','tan(':'tan','asin(':'sin⁻¹','acos(':'cos⁻¹','atan(':'tan⁻¹','√(':'√'}[k]||k)+'</button>'; }).join(''); }).join('')+'</div>';
    document.body.appendChild(p);
    p.addEventListener('mousedown',function(e){ if(e.target.closest('button')) e.preventDefault(); });
    p.addEventListener('click',function(e){ var b=e.target.closest('button[data-c]'); if(!b) return; calcKey(b.dataset.c); });
  }
  kbHide(); var nb=document.querySelector('.navbar'); p.style.bottom=((nb?nb.getBoundingClientRect().height:0)+8)+'px'; p.classList.add('show'); document.body.classList.add('calc-open'); calcShow();
}
function calcShow(res){ document.getElementById('calcExpr').textContent=CALC.expr||' '; if(res!==undefined) document.getElementById('calcRes').textContent=res; }
function calcKey(k){
  if(k==='close'){ document.getElementById('calcPanel').classList.remove('show'); document.body.classList.remove('calc-open'); return; }
  if(k==='AC'){ CALC.expr=''; calcShow('0'); return; }
  if(k==='⌫'){ CALC.expr=CALC.expr.replace(/(asin\(|acos\(|atan\(|sin\(|cos\(|tan\(|√\(|Ans|.)$/,''); calcShow(); return; }
  if(k==='='){ try{ var v=calcEval(CALC.expr); CALC.ans=v; calcShow(fmtNum(v)); }catch(e){ calcShow('Error'); } return; }
  if(k==='(−)'){ CALC.expr+='−'; calcShow(); return; }
  if(k==='Insert'){ var r=document.getElementById('calcRes').textContent; if(KB.target && !KB.target.disabled && r!=='Error'){ KB.target.value=r; KB.target.dispatchEvent(new Event('input',{bubbles:true})); showToast('Inserted '+r+' into the blank.'); } else showToast('Tap a blank first, then press Insert.'); return; }
  CALC.expr+=k; calcShow();
}

/* ================= Desmos ================= */
var DESMOS_KEY='dcb31709b452b1cf9dc26972add0fda6', desmosCalc=null, desmosLoading=false;
function openDesmos(exprs){
  var p=document.getElementById('desmosPanel');
  if(!p){ p=document.createElement('div'); p.id='desmosPanel'; p.className='tool-panel desmos';
    p.innerHTML='<div class="tp-head"><b>📈 Desmos graphing calculator</b><button class="tp-x" id="desmosReset">Reset graph</button><button class="tp-x" id="desmosClose">✕</button></div><div id="desmosBox"><div class="desmos-msg">Loading Desmos…</div></div>';
    document.body.appendChild(p);
    document.getElementById('desmosClose').addEventListener('click',function(){ p.classList.remove('show'); });
    document.getElementById('desmosReset').addEventListener('click',function(){ if(desmosCalc) desmosSet(p._exprs||[]); });
  }
  p._exprs=exprs||[]; p.classList.add('show');
  if(window.Desmos){ desmosInit(); desmosSet(p._exprs); return; }
  if(desmosLoading) return; desmosLoading=true;
  var sc=document.createElement('script'); sc.src='https://www.desmos.com/api/v1.9/calculator.js?apiKey='+DESMOS_KEY;
  sc.onload=function(){ desmosInit(); desmosSet(p._exprs); };
  sc.onerror=function(){ desmosLoading=false; document.getElementById('desmosBox').innerHTML='<div class="desmos-msg">Desmos needs an internet connection. <a href="https://www.desmos.com/calculator" target="_blank" rel="noopener">Open Desmos in a new tab</a>.</div>'; };
  document.head.appendChild(sc);
}
function desmosInit(){ if(desmosCalc) return; var box=document.getElementById('desmosBox'); box.innerHTML=''; desmosCalc=Desmos.GraphingCalculator(box,{expressionsCollapsed:false,settingsMenu:false,border:false,degreeMode:true}); }
function desmosSet(exprs){ if(!desmosCalc) return; desmosCalc.setBlank(); (exprs||[]).forEach(function(e,i){ if(typeof e==='string') desmosCalc.setExpression({id:'e'+i,latex:e}); else desmosCalc.setExpression(Object.assign({id:'e'+i},e)); }); }

/* ================= toolbar on each question ================= */
var _rsTools = renderSlide;
renderSlide = function(){
  _rsTools();
  kbHide();
  if(activeTab==='theory'||activeTab==='report') return;
  var ts=state.tabs[activeTab]; if(!ts) return;
  var slide=SLIDES[activeTab][ts.idx], card=document.querySelector('#wrap .qcard');
  if(card && slide && slide.tools && slide.tools.length && !card.querySelector('.tool-bar')){
    var bar=document.createElement('div'); bar.className='tool-bar';
    bar.innerHTML=(slide.tools.indexOf('calc')>=0?'<button type="button" class="tool-btn" data-t="calc">🧮 Calculator</button>':'')+
                  (slide.tools.indexOf('desmos')>=0?'<button type="button" class="tool-btn" data-t="desmos">📈 Desmos graph</button>':'');
    card.insertBefore(bar, card.firstChild);
    bar.addEventListener('click',function(e){ var b=e.target.closest('[data-t]'); if(!b) return; if(b.dataset.t==='calc') openCalc(); else openDesmos(slide.desmos||[]); });
  }
  kbWire();
};



/* ================= signed fractions in text: {−3/4}, {3/−4}, {−2 1/3}, {p/q} ================= */
fr = function(s){ return String(s).replace(/&lt;(\/?)(b|sup|sub|i)>/g,'<$1$2>')
  .replace(/\{([−-]?\d+) (\d+)\/(\d+)\}/g,'<span class="mx">$1<span class="fq"><span>$2</span><span>$3</span></span></span>')
  .replace(/\{([−-]?[A-Za-z0-9]+)\/([−-]?[A-Za-z0-9]+)\}/g,'<span class="fq"><span>$1</span><span>$2</span></span>'); };
/* ================= BMA badge → main page of this sheet (theory hub) ================= */
(function(){
  var c=document.querySelector('.brand .crest'); if(!c) return;
  var a=document.createElement('button'); a.type='button'; a.className='crest crest-home'; a.title='Back to the main page (theory notes)'; a.setAttribute('aria-label','Main page');
  a.innerHTML='BM<span class="crest-h">⌂</span>'; c.parentNode.replaceChild(a,c);
  a.addEventListener('click',function(){
    if(!student||!MODE){ window.scrollTo({top:0,behavior:'smooth'}); return; }
    if(typeof kbHide==='function') kbHide(); if(typeof SP!=='undefined'&&SP.on) spToggle(false);
    var cp=document.getElementById('calcPanel'); if(cp) cp.classList.remove('show'); document.body.classList.remove('calc-open');
    activeTab = (typeof THEORY!=='undefined') ? 'theory' : TAB_DEFS[0].id;
    buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'});
  });
})();

/* ================= session clock: starts at sign-in and keeps running ================= */
var CLK={t0:null};
(function(){
  var row=document.querySelector('.brand .brand-row'); if(!row) return;
  var d=document.createElement('div'); d.className='bmasw off'; d.id='swBox'; d.title='Time since you signed in';
  d.innerHTML='<span class="bmasw-ic">⏱</span><span class="bmasw-t" id="swT">00:00</span>';
  row.appendChild(d); setInterval(swTick,1000);
})();
function swFmt(s){ s=Math.floor(s||0); var h=Math.floor(s/3600), m=Math.floor(s%3600/60), x=s%60; return (h?h+':'+String(m).padStart(2,'0'):String(m).padStart(2,'0'))+':'+String(x).padStart(2,'0'); }
function swTick(){
  var box=document.getElementById('swBox'); if(!box) return;
  if(student && !CLK.t0) CLK.t0=Date.now();
  if(!student) CLK.t0=null;
  box.classList.toggle('off',!CLK.t0);
  document.getElementById('swT').textContent = CLK.t0 ? swFmt((Date.now()-CLK.t0)/1000) : '00:00';
}
function swTab(){ try{ if(!state||!state.tabs||activeTab==='theory'||activeTab==='report') return null; return state.tabs[activeTab]||null; }catch(e){ return null; } }
var _rsSW = renderSlide;
renderSlide = function(){ _rsSW(); swTick(); };
var _rfSW = renderFinished;
renderFinished = function(){ _rfSW(); var done=document.querySelector('#wrap .done-card'); if(CLK.t0 && done && !done.querySelector('.bmasw-done')){ var p=document.createElement('p'); p.className='bmasw-done'; p.textContent='⏱ Time since sign-in: '+swFmt((Date.now()-CLK.t0)/1000); var h2=done.querySelector('h2'); if(h2) h2.insertAdjacentElement('afterend',p); else done.appendChild(p); } };

/* ================= scratchpad (Khan-style, 4 pens) ================= */
var SP={on:false, draw:true, color:'ink', size:3, erase:false, store:{}, key:null, cv:null, ctx:null, down:false, last:null};
var SP_COL={ink:null, blue:'#2563EB', red:'#DC2626', green:'#16A34A'};
function spInk(){ return getComputedStyle(document.documentElement).getPropertyValue('--ink').trim()||'#211E1A'; }
function spKey(){ var ts=swTab(); return ts ? (MODE+'|'+activeTab+'|'+ts.idx) : null; }
function spBuild(){
  if(SP.cv) return;
  var cv=document.createElement('canvas'); cv.id='spCanvas'; cv.className='sp-canvas'; document.body.appendChild(cv);
  var bar=document.createElement('div'); bar.id='spBar'; bar.className='sp-bar';
  bar.innerHTML='<span class="sp-lbl">✏️ Scratchpad</span>'+
    ['ink','blue','red','green'].map(function(c){ return '<button type="button" class="sp-pen" data-c="'+c+'" title="'+(c==='ink'?'black':c)+' pen"><i style="background:'+(c==='ink'?'var(--ink)':SP_COL[c])+'"></i></button>'; }).join('')+
    '<button type="button" class="sp-tool" data-t="erase" title="Eraser">🧽</button><button type="button" class="sp-tool" data-t="size" title="Pen size">●</button><button type="button" class="sp-tool" data-t="scroll" title="Pause drawing to scroll or answer">✋</button>'+
    '<button type="button" class="sp-tool" data-t="clear" title="Clear page">🗑</button><button type="button" class="sp-tool" data-t="close" title="Close scratchpad">✕</button>';
  document.body.appendChild(bar);
  bar.addEventListener('click',function(e){ var b=e.target.closest('button'); if(!b) return;
    if(b.dataset.c){ SP.color=b.dataset.c; SP.erase=false; SP.draw=true; }
    else if(b.dataset.t==='erase'){ SP.erase=true; SP.draw=true; }
    else if(b.dataset.t==='size'){ SP.size = SP.size===3?6:(SP.size===6?1.5:3); b.textContent = SP.size===6?'⬤':(SP.size===1.5?'·':'●'); }
    else if(b.dataset.t==='scroll'){ SP.draw=!SP.draw; }
    else if(b.dataset.t==='clear'){ spClear(); }
    else if(b.dataset.t==='close'){ spToggle(false); return; }
    spUI(); });
  SP.cv=cv; SP.ctx=cv.getContext('2d');
  cv.addEventListener('pointerdown',function(e){ if(!SP.draw) return; e.preventDefault(); cv.setPointerCapture(e.pointerId); SP.down=true; SP.last=spPt(e); spDot(SP.last); });
  cv.addEventListener('pointermove',function(e){ if(!SP.down) return; e.preventDefault(); var p=spPt(e); spLine(SP.last,p); SP.last=p; });
  var up=function(){ if(SP.down){ SP.down=false; spSave(); } };
  cv.addEventListener('pointerup',up); cv.addEventListener('pointercancel',up); cv.addEventListener('pointerleave',up);
  window.addEventListener('resize',function(){ if(SP.on) spFit(true); });
}
function spPt(e){ var r=SP.cv.getBoundingClientRect(); return {x:e.clientX-r.left, y:e.clientY-r.top}; }
function spStyle(){ var c=SP.ctx; c.lineCap='round'; c.lineJoin='round'; c.globalCompositeOperation=SP.erase?'destination-out':'source-over'; c.strokeStyle=c.fillStyle=(SP.color==='ink'?spInk():SP_COL[SP.color]); c.lineWidth=SP.erase?22:SP.size; }
function spDot(p){ spStyle(); var c=SP.ctx; c.beginPath(); c.arc(p.x,p.y,(SP.erase?11:SP.size/2),0,Math.PI*2); c.fill(); }
function spLine(a,b){ spStyle(); var c=SP.ctx; c.beginPath(); c.moveTo(a.x,a.y); c.lineTo(b.x,b.y); c.stroke(); }
function spSave(){ if(SP.key&&SP.cv){ try{ SP.store[SP.key]=SP.cv.toDataURL(); }catch(e){} } }
function spClear(){ if(!SP.ctx) return; SP.ctx.save(); SP.ctx.setTransform(1,0,0,1,0,0); SP.ctx.clearRect(0,0,SP.cv.width,SP.cv.height); SP.ctx.restore(); if(SP.key) delete SP.store[SP.key]; }
function spFit(keep){
  var wrap=document.getElementById('wrap'); if(!wrap||!SP.cv) return;
  var r=wrap.getBoundingClientRect(), top=r.top+window.scrollY, h=Math.max(wrap.scrollHeight, window.innerHeight-r.top)+40, w=document.documentElement.clientWidth;
  var old=keep&&SP.key?SP.store[SP.key]:null, dpr=window.devicePixelRatio||1;
  SP.cv.style.top=top+'px'; SP.cv.style.left='0px'; SP.cv.style.width=w+'px'; SP.cv.style.height=h+'px';
  SP.cv.width=Math.round(w*dpr); SP.cv.height=Math.round(h*dpr); SP.ctx.setTransform(dpr,0,0,dpr,0,0);
  if(old){ var im=new Image(); im.onload=function(){ SP.ctx.save(); SP.ctx.setTransform(1,0,0,1,0,0); SP.ctx.drawImage(im,0,0); SP.ctx.restore(); }; im.src=old; }
}
function spLoad(){ spSave(); SP.key=spKey(); spFit(false); var d=SP.key&&SP.store[SP.key]; if(d){ var im=new Image(); im.onload=function(){ SP.ctx.save(); SP.ctx.setTransform(1,0,0,1,0,0); SP.ctx.drawImage(im,0,0); SP.ctx.restore(); }; im.src=d; } }
function spUI(){
  var bar=document.getElementById('spBar'); if(!bar) return;
  bar.querySelectorAll('.sp-pen').forEach(function(b){ b.classList.toggle('on', !SP.erase && SP.draw && b.dataset.c===SP.color); });
  bar.querySelector('[data-t=erase]').classList.toggle('on', SP.erase && SP.draw);
  bar.querySelector('[data-t=scroll]').classList.toggle('on', !SP.draw);
  SP.cv.classList.toggle('passive', !SP.draw);
  var fb=document.getElementById('spFab'); if(fb) fb.classList.toggle('on',SP.on);
}
function spToggle(on){
  spBuild(); SP.on=(on===undefined)?!SP.on:on;
  document.body.classList.toggle('sp-open',SP.on); SP.cv.style.display=SP.on?'block':'none'; document.getElementById('spBar').style.display=SP.on?'flex':'none';
  if(SP.on){ SP.draw=true; SP.erase=false; spLoad(); if(typeof kbHide==='function') kbHide(); } else { spSave(); }
  spUI();
}
(function(){ var f=document.createElement('button'); f.type='button'; f.id='spFab'; f.className='sp-fab'; f.innerHTML='✏️ <span>Scratchpad</span>'; f.title='Open a scratchpad to write your working'; f.addEventListener('click',function(){ spToggle(); }); document.body.appendChild(f); })();
var _rsSP = renderSlide;
renderSlide = function(){ _rsSP(); var fab=document.getElementById('spFab'); var q=!!swTab(); if(fab) fab.style.display=q?'':'none'; if(!q && SP.on) spToggle(false); if(SP.on) setTimeout(spLoad,30); };

renderLogin();
})();
</script>
</body>
</html>
