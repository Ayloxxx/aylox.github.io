<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8"><meta name="viewport" content="width=device-width,initial-scale=1">
<title>Aylox Furnitures — Studio</title>
<script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.1/dist/chart.umd.min.js"></script>
<style>
:root{color-scheme:light;--bg:#f5f6f4;--panel:#fff;--panel2:#f8f9f7;--line:#e7e9e4;--line2:#d9ddd5;--ink:#20251f;--muted:#747d70;--soft:#9aa195;--green:#648d43;--green2:#4f7532;--green-bg:#edf4e8;--red:#d65b56;--red-bg:#fbeeed;--amber:#c58a31;--amber-bg:#fbf3e5;--purple:#7568bb;--purple-bg:#f0eef9;--shadow:0 8px 30px rgba(32,45,25,.045);--r:13px;--sidebar:248px}
[data-theme=dark]{color-scheme:dark;--bg:#151815;--panel:#1d221d;--panel2:#232923;--line:#303830;--line2:#3b453b;--ink:#edf1e9;--muted:#a2ad9e;--soft:#748071;--green:#8fb66c;--green2:#a4c981;--green-bg:#293723;--red:#e17b75;--red-bg:#3b2827;--amber:#dfb16a;--amber-bg:#3a3021;--purple:#a69bdd;--purple-bg:#302c43;--shadow:0 8px 30px rgba(0,0,0,.14)}
*{box-sizing:border-box}body{margin:0;background:var(--bg);color:var(--ink);font:14px/1.5 Inter,-apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif;min-height:100vh}button,input,select,textarea{font:inherit}button{cursor:pointer}.shell{min-height:100vh}.sidebar{position:fixed;inset:0 auto 0 0;width:var(--sidebar);padding:25px 17px 18px;background:var(--panel);border-right:1px solid var(--line);display:flex;flex-direction:column;z-index:20}.brand{display:flex;align-items:center;gap:11px;padding:0 9px 27px}.brand-mark{width:38px;height:38px;border-radius:12px;background:linear-gradient(145deg,#83a963,#4e7636);display:grid;place-items:center;color:white;font-weight:800;font-size:17px;box-shadow:0 5px 14px #648d4333}.brand-name{font-size:14px;font-weight:750;letter-spacing:-.3px}.brand-sub{font-size:10px;color:var(--soft);margin-top:2px;letter-spacing:.08em;text-transform:uppercase}.nav-label{font-size:10px;color:var(--soft);font-weight:700;letter-spacing:.12em;padding:0 11px;margin:8px 0 9px}.nav{display:grid;gap:4px}.nav button{border:0;background:transparent;color:var(--muted);padding:10px 12px;border-radius:9px;text-align:left;display:flex;align-items:center;gap:11px;font-size:13px;font-weight:550;transition:.16s}.nav button:hover{background:var(--panel2);color:var(--ink)}.nav button.active{background:var(--green-bg);color:var(--green2);font-weight:700}.nav svg{width:17px;height:17px;stroke:currentColor;fill:none;stroke-width:1.8;flex:none}.side-bottom{margin-top:auto}.project-mini{padding:13px;border:1px solid var(--line);background:var(--panel2);border-radius:11px;margin:12px 2px}.mini-title{font-size:11px;font-weight:700}.mini-sub{font-size:10px;color:var(--muted);margin-top:3px}.mini-track,.track{height:6px;border-radius:20px;background:var(--line);overflow:hidden}.mini-track{margin-top:10px}.mini-fill,.track-fill{height:100%;background:var(--green);border-radius:20px;transition:width .25s}.side-foot{display:flex;justify-content:space-between;align-items:center;padding:12px 8px 0;color:var(--soft);font-size:10px}.main{margin-left:var(--sidebar);padding:27px clamp(20px,4vw,54px) 55px;max-width:1600px}.topbar{display:flex;align-items:center;justify-content:space-between;gap:16px;margin-bottom:28px}.crumb{font-size:11px;color:var(--soft);margin-bottom:4px}.page-title{font-size:25px;letter-spacing:-.8px;font-weight:750;line-height:1.2}.page-sub{font-size:12px;color:var(--muted);margin-top:5px}.top-actions{display:flex;align-items:center;gap:9px}.sync{display:flex;align-items:center;gap:7px;font-size:11px;color:var(--muted);margin-right:7px}.sync-dot{width:7px;height:7px;border-radius:50%;background:var(--green)}.sync-dot.busy{background:var(--amber);animation:pulse .8s infinite}.sync-dot.error{background:var(--red)}@keyframes pulse{50%{opacity:.3}}.icon-btn,.btn{border:1px solid var(--line);background:var(--panel);color:var(--muted);border-radius:9px;display:inline-flex;align-items:center;justify-content:center;gap:8px;transition:.15s}.icon-btn{width:36px;height:36px}.icon-btn svg,.btn svg{width:15px;height:15px;stroke:currentColor;fill:none;stroke-width:1.8}.icon-btn:hover,.btn:hover{border-color:var(--line2);background:var(--panel2);color:var(--ink)}.btn{padding:8px 12px;font-size:12px;font-weight:650;white-space:nowrap}.btn.primary{background:var(--green);border-color:var(--green);color:white}.btn.primary:hover{background:var(--green2)}.btn.soft{background:var(--green-bg);border-color:transparent;color:var(--green2)}.btn.danger{background:var(--red-bg);border-color:transparent;color:var(--red)}.btn.purple{background:var(--purple-bg);border-color:transparent;color:var(--purple)}.page{display:none;animation:fade .2s ease}.page.active{display:block}@keyframes fade{from{opacity:.5;transform:translateY(4px)}to{opacity:1;transform:none}}.grid{display:grid;gap:14px}.overview{grid-template-columns:repeat(4,minmax(0,1fr));margin-bottom:16px}.card{background:var(--panel);border:1px solid var(--line);border-radius:var(--r);box-shadow:var(--shadow)}.metric{padding:17px 18px;min-height:116px}.metric-top{display:flex;align-items:center;justify-content:space-between;color:var(--muted);font-size:11px;font-weight:600}.metric-icon{width:30px;height:30px;border-radius:9px;display:grid;place-items:center;background:var(--panel2);color:var(--green)}.metric-icon svg{width:15px;height:15px;stroke:currentColor;fill:none;stroke-width:1.8}.metric-value{font-size:27px;font-weight:760;letter-spacing:-1px;margin-top:12px;line-height:1}.metric-note{font-size:10px;color:var(--soft);margin-top:6px}.dashboard-grid{grid-template-columns:minmax(0,1.55fr) minmax(260px,.85fr);margin-bottom:15px}.card-head{display:flex;align-items:center;justify-content:space-between;padding:16px 18px 12px}.card-title{font-size:13px;font-weight:750;letter-spacing:-.2px}.card-hint{font-size:10px;color:var(--soft);margin-top:3px}.progress-card{padding:2px 18px 18px}.progress-main{display:flex;align-items:end;justify-content:space-between;margin:8px 0 10px}.progress-number{font-size:34px;font-weight:780;letter-spacing:-1.4px}.progress-caption{font-size:11px;color:var(--muted)}.progress-list{display:grid;gap:13px;margin-top:18px}.progress-line{display:grid;grid-template-columns:125px 1fr 35px;gap:10px;align-items:center;font-size:11px}.progress-line span:first-child{color:var(--muted)}.progress-line b{text-align:right;font-size:10px;color:var(--muted)}.activity{padding:0 18px 12px}.activity-item{display:flex;gap:10px;padding:10px 0;border-bottom:1px solid var(--line)}.activity-item:last-child{border:0}.activity-dot{width:7px;height:7px;border-radius:50%;background:var(--green);margin-top:6px;flex:none}.activity-text{font-size:11px;color:var(--muted)}.activity-text strong{color:var(--ink);font-weight:650}.activity-time{font-size:9px;color:var(--soft);margin-top:2px}.section-head{display:flex;align-items:center;justify-content:space-between;gap:12px;margin:25px 0 12px}.section-head h2{font-size:14px;margin:0;font-weight:750}.toolbar{display:flex;align-items:center;gap:8px;flex-wrap:wrap;margin-bottom:15px}.search{position:relative;flex:1;min-width:180px}.search svg{position:absolute;left:11px;top:50%;transform:translateY(-50%);width:15px;height:15px;stroke:var(--soft);fill:none;stroke-width:1.8}.field,.select,.textarea{border:1px solid var(--line);background:var(--panel);color:var(--ink);border-radius:9px;padding:9px 11px;outline:none;font-size:12px;width:100%;transition:border .15s}.search .field{padding-left:34px}.field:focus,.select:focus,.textarea:focus{border-color:var(--green)}.field::placeholder,.textarea::placeholder{color:var(--soft)}.select{width:auto;min-width:130px}.categories{display:grid;grid-template-columns:repeat(auto-fit,minmax(285px,1fr));gap:13px}.category{overflow:hidden}.category-head{padding:13px 15px;border-bottom:1px solid var(--line);display:flex;align-items:center;justify-content:space-between}.category-name{font-size:12px;font-weight:750;display:flex;align-items:center;gap:8px}.category-icon{width:27px;height:27px;border-radius:8px;background:var(--panel2);display:grid;place-items:center;color:var(--green)}.category-icon svg{width:14px;height:14px;stroke:currentColor;fill:none;stroke-width:1.8}.count{font-size:10px;color:var(--muted);background:var(--panel2);padding:3px 8px;border-radius:20px}.count.done{background:var(--green-bg);color:var(--green2)}.task{padding:11px 14px;border-bottom:1px solid var(--line);border-left:2px solid transparent}.task:last-of-type{border-bottom:0}.task[data-prio=haute]{border-left-color:var(--red)}.task[data-prio=moyenne]{border-left-color:var(--amber)}.task[data-prio=basse]{border-left-color:var(--green)}.task:hover{background:var(--panel2)}.task-top{display:flex;gap:9px;align-items:flex-start}.check{width:17px;height:17px;border:1.5px solid var(--line2);border-radius:5px;background:transparent;flex:none;margin-top:1px;display:grid;place-items:center;color:white}.check.checked{background:var(--green);border-color:var(--green)}.check svg{width:11px;height:11px;stroke:currentColor;fill:none;stroke-width:2.5}.task-content{min-width:0;flex:1}.task-name{font-size:12px;font-weight:620;line-height:1.4;overflow-wrap:anywhere}.task.done .task-name{text-decoration:line-through;color:var(--soft)}.task-note{font-size:10px;color:var(--soft);margin-top:3px}.task-bottom{display:flex;align-items:center;gap:7px;margin:6px 0 0 26px}.pill{font-size:9px;padding:2px 6px;border-radius:4px;font-weight:700;text-transform:capitalize}.pill.haute{background:var(--red-bg);color:var(--red)}.pill.moyenne{background:var(--amber-bg);color:var(--amber)}.pill.basse{background:var(--green-bg);color:var(--green2)}.task-actions{display:flex;gap:2px;margin-left:auto}.mini-action{border:0;background:transparent;color:var(--soft);width:25px;height:25px;border-radius:6px;display:grid;place-items:center}.mini-action:hover{background:var(--line);color:var(--ink)}.mini-action svg{width:13px;height:13px;stroke:currentColor;fill:none;stroke-width:1.8}.task-desc{margin:9px 0 0 26px;padding:9px 10px;background:var(--panel2);border-radius:8px;font-size:11px;color:var(--muted);white-space:pre-wrap;display:none}.task-desc.open{display:block}.add-inline{padding:9px 13px}.add-inline input{width:100%;border:1px dashed var(--line2);border-radius:8px;background:transparent;padding:7px 9px;color:var(--ink);font-size:11px;outline:none}.add-inline input:focus{border-color:var(--green)}.empty{padding:28px 15px;text-align:center;color:var(--soft);font-size:12px}.notes-grid,.roadmap-grid,.stats-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(250px,1fr));gap:13px}.note-card{overflow:hidden}.note-head{padding:12px 14px;border-bottom:1px solid var(--line);font-size:12px;font-weight:700}.note-area{display:block;width:100%;min-height:165px;resize:vertical;border:0;background:transparent;padding:13px 14px;color:var(--ink);outline:none;font-size:12px;line-height:1.65}.note-foot{border-top:1px solid var(--line);padding:8px 12px;display:flex;justify-content:flex-end}.version-card,.bug-card{margin-bottom:12px;overflow:hidden}.version-head{padding:13px 16px;display:flex;justify-content:space-between;align-items:center;border-bottom:1px solid var(--line)}.version-name{font-weight:750;color:var(--green);font-size:13px}.version-date{font-size:10px;color:var(--soft)}.version-body{padding:12px 16px}.version-entry{font-size:12px;color:var(--muted);padding:4px 0;display:flex;gap:9px}.version-entry:before{content:"";width:6px;height:6px;background:var(--green);border-radius:50%;margin-top:6px;flex:none}.card-actions{padding:8px 14px;border-top:1px solid var(--line);display:flex;justify-content:flex-end}.bug-card{padding:14px 16px;border-left:3px solid var(--red)}.bug-card.en-cours{border-left-color:var(--amber)}.bug-card.corrige{border-left-color:var(--green)}.bug-head{display:flex;justify-content:space-between;gap:10px;align-items:center}.bug-title{font-size:12px;font-weight:700}.bug-status{font-size:9px;font-weight:700;padding:3px 7px;border-radius:5px;background:var(--red-bg);color:var(--red);white-space:nowrap}.bug-status.en-cours{background:var(--amber-bg);color:var(--amber)}.bug-status.corrige{background:var(--green-bg);color:var(--green2)}.bug-desc{font-size:11px;color:var(--muted);margin:8px 0}.bug-foot{display:flex;align-items:center;justify-content:space-between;gap:8px}.bug-version{font-size:10px;color:var(--soft)}.roadmap-col{overflow:hidden}.roadmap-head{padding:13px 15px;border-bottom:1px solid var(--line);display:flex;align-items:center;justify-content:space-between}.roadmap-name{font-size:12px;font-weight:750}.roadmap-item{display:flex;align-items:center;gap:8px;padding:10px 13px;border-bottom:1px solid var(--line);font-size:11px;color:var(--muted)}.roadmap-item span{flex:1}.roadmap-add{padding:9px 12px}.roadmap-add input{width:100%;border:1px dashed var(--line2);background:transparent;border-radius:7px;padding:7px 9px;color:var(--ink);font-size:11px;outline:none}.stat-grid{grid-template-columns:repeat(3,minmax(0,1fr));margin-bottom:14px}.chart-card{padding:16px 18px;margin-bottom:14px}.chart-wrap{height:250px;position:relative}.chart-title{font-size:12px;font-weight:750;margin-bottom:13px}.modal-backdrop{position:fixed;inset:0;background:#10160f88;backdrop-filter:blur(3px);z-index:50;display:none;align-items:center;justify-content:center;padding:18px}.modal-backdrop.open{display:flex}.modal{width:min(480px,100%);max-height:90vh;overflow:auto;background:var(--panel);border:1px solid var(--line);border-radius:15px;box-shadow:0 20px 70px #0003;padding:20px}.modal-head{display:flex;align-items:center;justify-content:space-between;margin-bottom:17px}.modal-title{font-size:15px;font-weight:750}.form-group{margin-bottom:12px}.form-label{display:block;font-size:10px;font-weight:700;color:var(--muted);margin-bottom:5px}.textarea{resize:vertical;min-height:85px}.form-row{display:grid;grid-template-columns:1fr 1fr;gap:10px}.modal-actions{display:flex;justify-content:flex-end;gap:8px;margin-top:17px}.toast{position:fixed;right:22px;bottom:80px;z-index:200;padding:11px 15px;border-radius:9px;background:var(--ink);color:var(--panel);font-size:11px;box-shadow:var(--shadow);opacity:0;transform:translateY(8px);transition:.2s;pointer-events:none}.toast.show{opacity:1;transform:none}.mobile-menu{display:none}

/* ── Drawer IA ── */
.ai-launcher{position:fixed;right:25px;bottom:24px;z-index:70;display:flex;align-items:center;gap:9px;padding:12px 17px;border:none;background:linear-gradient(135deg,#789e59,#4e7636);color:#fff;border-radius:999px;box-shadow:0 10px 28px rgba(65,99,42,.28);font-size:12px;font-weight:750;cursor:pointer;transition:transform .18s,box-shadow .18s}.ai-launcher:hover{transform:translateY(-2px);box-shadow:0 14px 32px rgba(65,99,42,.34)}.ai-launcher-spark{font-size:17px}.ai-online-dot{width:7px;height:7px;border-radius:50%;background:#d7f3bd;box-shadow:0 0 0 3px rgba(255,255,255,.18)}
.ai-scrim{position:fixed;inset:0;background:rgba(12,18,12,.28);z-index:80;opacity:0;pointer-events:none;transition:opacity .22s}.ai-scrim.open{opacity:1;pointer-events:auto}
.ai-drawer{position:fixed;z-index:90;right:0;top:0;height:100dvh;width:min(440px,100vw);background:var(--panel);border-left:1px solid var(--line);box-shadow:-18px 0 55px rgba(0,0,0,.14);display:flex;flex-direction:column;transform:translateX(105%);transition:transform .25s cubic-bezier(.2,.8,.2,1)}.ai-drawer.open{transform:translateX(0)}
.ai-drawer-head{height:64px;flex:none;display:flex;align-items:center;justify-content:space-between;padding:0 16px;border-bottom:1px solid var(--line)}.ai-brand{display:flex;align-items:center;gap:10px}.ai-brand-icon{width:34px;height:34px;border-radius:11px;background:var(--purple-bg);color:var(--purple);display:grid;place-items:center;font-size:18px}.ai-brand strong{display:block;font-size:13px;color:var(--ink)}.ai-brand small{display:block;color:var(--soft);font-size:10px;margin-top:1px}
.ai-context-bar{flex:none;padding:8px 16px;display:flex;align-items:center;gap:7px;background:var(--panel2);border-bottom:1px solid var(--line);font-size:10px;color:var(--muted)}.ai-context-dot{width:6px;height:6px;border-radius:50%;background:var(--green);flex:none}.ai-context-bar b{color:var(--ink);font-weight:700}.ai-context-bar button{margin-left:auto;border:0;background:none;color:var(--muted);cursor:pointer;font-size:14px;padding:0 2px}
.ai-suggestions{padding:10px 14px 2px;display:flex;gap:6px;overflow-x:auto;flex:none;scrollbar-width:none}.ai-suggestions::-webkit-scrollbar{display:none}.ai-suggestions button{white-space:nowrap;border:1px solid var(--line);background:var(--panel2);color:var(--muted);border-radius:999px;padding:6px 10px;font-size:10px;flex:none}.ai-suggestions button:hover{border-color:var(--purple);color:var(--purple)}
.ai-chat{flex:1;overflow-y:auto;padding:14px 14px 20px;display:flex;flex-direction:column;gap:11px;scroll-behavior:smooth}
.ai-welcome{text-align:center;margin:auto 10px;color:var(--muted)}.ai-welcome-mark{width:42px;height:42px;border-radius:14px;background:var(--purple-bg);color:var(--purple);display:grid;place-items:center;font-size:22px;margin:0 auto 11px}.ai-welcome strong{display:block;color:var(--ink);font-size:14px;margin-bottom:7px}.ai-welcome p{font-size:11px;line-height:1.7;max-width:270px;margin:0 auto}
.ai-message{max-width:92%;display:flex;flex-direction:column;gap:3px}.ai-message.user{align-self:flex-end;align-items:flex-end}.ai-message.assistant{align-self:flex-start}.ai-message-role{font-size:9px;color:var(--soft);padding:0 3px}.ai-message-body{font-size:12px;line-height:1.7;padding:9px 12px;border-radius:12px;white-space:pre-wrap;overflow-wrap:anywhere}.ai-message.user .ai-message-body{background:var(--green-bg);color:var(--ink);border-bottom-right-radius:3px}.ai-message.assistant .ai-message-body{background:var(--panel2);border:1px solid var(--line);color:var(--ink);border-bottom-left-radius:3px}.ai-message.error .ai-message-body{background:var(--red-bg);color:var(--red)}
.ai-typing{align-self:flex-start;display:flex;gap:4px;padding:12px 14px;background:var(--panel2);border:1px solid var(--line);border-radius:12px;border-bottom-left-radius:3px}.ai-typing i{width:6px;height:6px;background:var(--soft);border-radius:50%;animation:aiBounce .8s infinite alternate;display:block}.ai-typing i:nth-child(2){animation-delay:.2s}.ai-typing i:nth-child(3){animation-delay:.4s}@keyframes aiBounce{to{opacity:.25;transform:translateY(-3px)}}
.ai-composer{margin:0 12px 10px;border:1px solid var(--line2);background:var(--panel2);border-radius:13px;padding:9px 10px 7px;flex:none}.ai-composer:focus-within{border-color:var(--purple);box-shadow:0 0 0 3px color-mix(in srgb,var(--purple) 10%,transparent)}.ai-composer textarea{display:block;width:100%;resize:none;max-height:120px;border:0;outline:0;background:transparent;color:var(--ink);font:12px/1.55 inherit;padding:2px 3px}.ai-composer textarea::placeholder{color:var(--soft)}.ai-composer-foot{display:flex;align-items:center;justify-content:space-between;margin-top:5px;padding-left:3px}.ai-composer-foot small{font-size:9px;color:var(--soft)}.ai-send{width:28px;height:28px;border:0;border-radius:8px;background:var(--green);color:white;font-size:18px;line-height:1;display:grid;place-items:center}.ai-send:disabled{opacity:.4;cursor:wait}
.ai-disclaimer{text-align:center;color:var(--soft);font-size:9px;padding:0 14px 10px;flex:none}

@media(max-width:1050px){:root{--sidebar:215px}.overview{grid-template-columns:repeat(2,1fr)}}
@media(max-width:760px){:root{--sidebar:0px}.sidebar{width:250px;transform:translateX(-105%);transition:transform .2s;box-shadow:var(--shadow)}.sidebar.open{transform:none}.main{margin:0;padding:20px 15px 40px}.mobile-menu{display:inline-flex}.topbar{align-items:flex-start}.page-title{font-size:21px}.sync{display:none}.dashboard-grid{grid-template-columns:1fr}.overview{gap:9px}.metric{padding:13px;min-height:103px}.metric-value{font-size:24px}.stat-grid{grid-template-columns:1fr 1fr}.toolbar .search{flex-basis:100%}.categories{grid-template-columns:1fr}.top-actions{gap:6px}.top-actions .btn span{display:none}.ai-launcher{right:15px;bottom:15px}}
@media(max-width:420px){.overview{grid-template-columns:1fr 1fr}.stat-grid{grid-template-columns:1fr}.form-row{grid-template-columns:1fr}}
</style>
</head>
<body>
<div class="shell">

<!-- ═══ SIDEBAR ═══ -->
<aside class="sidebar" id="sidebar">
  <div class="brand">
    <div class="brand-mark">A</div>
    <div><div class="brand-name">Aylox Furnitures</div><div class="brand-sub">Mod development studio</div></div>
  </div>
  <div class="nav-label">ESPACE DE TRAVAIL</div>
  <nav class="nav" id="nav">
    <button class="active" data-page="dashboard"><svg viewBox="0 0 24 24"><rect x="3" y="3" width="7" height="7" rx="1"/><rect x="14" y="3" width="7" height="7" rx="1"/><rect x="14" y="14" width="7" height="7" rx="1"/><rect x="3" y="14" width="7" height="7" rx="1"/></svg>Vue d'ensemble</button>
    <button data-page="tasks"><svg viewBox="0 0 24 24"><path d="m5 12 4 4L19 6"/><path d="M20 12v7a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h11"/></svg>Tâches</button>
    <button data-page="notes"><svg viewBox="0 0 24 24"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><path d="M14 2v6h6M8 13h8M8 17h8"/></svg>Notes</button>
    <button data-page="changelog"><svg viewBox="0 0 24 24"><circle cx="12" cy="12" r="9"/><path d="M12 7v5l3 2"/></svg>Changelog</button>
    <button data-page="bugs"><svg viewBox="0 0 24 24"><path d="M8 6 12 2l4 4M12 22v-8M5 9H2m20 0h-3M5 15H2m20 0h-3M7 6l-2-2m14 0-2 2"/><rect x="7" y="6" width="10" height="14" rx="5"/></svg>Suivi des bugs</button>
    <button data-page="roadmap"><svg viewBox="0 0 24 24"><path d="M4 19V5m0 0 5 3 5-3 6 3v11l-6-3-5 3-5-3"/></svg>Roadmap</button>
    <button data-page="stats"><svg viewBox="0 0 24 24"><path d="M4 19V9m8 10V4m8 15v-7"/></svg>Statistiques</button>
  </nav>
  <div class="side-bottom">
    <div class="project-mini">
      <div class="mini-title">Forge 1.20.1</div>
      <div class="mini-sub">Suivi du développement</div>
      <div class="mini-track"><div class="mini-fill" id="sideProgress" style="width:0%"></div></div>
      <div class="mini-sub" id="sideProgressText">0% terminé</div>
    </div>
    <div class="side-foot"><span>AYLOX STUDIO</span><span>v1.0</span></div>
  </div>
</aside>

<!-- ═══ MAIN ═══ -->
<main class="main">
  <header class="topbar">
    <div style="display:flex;align-items:flex-start;gap:11px">
      <button class="icon-btn mobile-menu" id="menuBtn" aria-label="Menu"><svg viewBox="0 0 24 24"><path d="M4 6h16M4 12h16M4 18h16"/></svg></button>
      <div>
        <div class="crumb">AYLOX FURNITURES / <span id="crumb">OVERVIEW</span></div>
        <div class="page-title" id="pageTitle">Vue d'ensemble</div>
        <div class="page-sub" id="pageSub">Le centre de contrôle de ton mod Minecraft.</div>
      </div>
    </div>
    <div class="top-actions">
      <div class="sync"><i class="sync-dot" id="syncDot"></i><span id="syncLabel">Connexion…</span></div>
      <button class="icon-btn" id="exportBtn" title="Exporter les données"><svg viewBox="0 0 24 24"><path d="M12 3v12m-5-5 5 5 5-5M4 17v3h16v-3"/></svg></button>
      <button class="icon-btn" id="themeBtn" title="Changer de thème"><svg viewBox="0 0 24 24"><path d="M20 15.5A8 8 0 0 1 8.5 4 8.5 8.5 0 1 0 20 15.5Z"/></svg></button>
      <button class="btn primary" id="quickAdd"><svg viewBox="0 0 24 24"><path d="M12 5v14M5 12h14"/></svg><span>Nouvelle tâche</span></button>
    </div>
  </header>

  <!-- Dashboard -->
  <section class="page active" id="page-dashboard">
    <div class="grid overview" id="overviewMetrics"></div>
    <div class="grid dashboard-grid">
      <div class="card">
        <div class="card-head"><div><div class="card-title">Progression du projet</div><div class="card-hint">Avancement de toutes les tâches</div></div><span class="count" id="dashTaskCount">0 tâches</span></div>
        <div class="progress-card">
          <div class="progress-main"><div><div class="progress-number" id="dashPct">0%</div><div class="progress-caption" id="dashDone">0 tâche terminée</div></div><div style="text-align:right;font-size:10px;color:var(--soft)">OBJECTIF<br><b style="color:var(--green)">100%</b></div></div>
          <div class="track"><div class="track-fill" id="dashTrack" style="width:0%"></div></div>
          <div class="progress-list" id="dashCategories"></div>
        </div>
      </div>
      <div class="card">
        <div class="card-head"><div><div class="card-title">Activité récente</div><div class="card-hint">Dernières actions sur le projet</div></div></div>
        <div class="activity" id="activityList"><div class="empty">Aucune activité pour le moment.</div></div>
      </div>
    </div>
    <div class="section-head"><h2>Tâches à traiter</h2><button class="btn" data-goto="tasks">Voir toutes les tâches →</button></div>
    <div class="card" id="priorityTasks"></div>
  </section>

  <!-- Tâches -->
  <section class="page" id="page-tasks">
    <div class="toolbar">
      <div class="search"><svg viewBox="0 0 24 24"><circle cx="11" cy="11" r="8"/><path d="m21 21-4.4-4.4"/></svg><input class="field" id="taskSearch" placeholder="Rechercher une tâche…"></div>
      <select class="select" id="prioFilter"><option value="">Toutes les priorités</option><option value="haute">Haute</option><option value="moyenne">Moyenne</option><option value="basse">Basse</option></select>
      <select class="select" id="statusFilter"><option value="">Tous les statuts</option><option value="todo">À faire</option><option value="done">Terminées</option></select>
      <button class="btn primary" id="addTaskBtn">＋ Ajouter</button>
    </div>
    <div class="categories" id="categories"></div>
  </section>

  <!-- Notes -->
  <section class="page" id="page-notes">
    <div class="section-head" style="margin-top:0"><div><h2>Carnet de développement</h2><div class="page-sub">Tes notes sont synchronisées avec Supabase.</div></div></div>
    <div class="notes-grid" id="notesGrid"></div>
  </section>

  <!-- Changelog -->
  <section class="page" id="page-changelog">
    <div class="section-head" style="margin-top:0"><div><h2>Historique des versions</h2><div class="page-sub">Garde une trace des nouveautés et corrections.</div></div><button class="btn primary" id="addVersion">＋ Nouvelle version</button></div>
    <div id="changelogList"></div>
  </section>

  <!-- Bugs -->
  <section class="page" id="page-bugs">
    <div class="section-head" style="margin-top:0"><div><h2>Registre des bugs</h2><div class="page-sub">Centralise les problèmes à résoudre.</div></div><button class="btn primary" id="addBug">＋ Signaler un bug</button></div>
    <div class="toolbar"><select class="select" id="bugFilter"><option value="">Tous les statuts</option><option value="ouvert">Ouverts</option><option value="en cours">En cours</option><option value="corrigé">Corrigés</option></select></div>
    <div id="bugsList"></div>
  </section>

  <!-- Roadmap -->
  <section class="page" id="page-roadmap">
    <div class="section-head" style="margin-top:0"><div><h2>Feuille de route</h2><div class="page-sub">Organise les prochaines étapes du mod.</div></div></div>
    <div class="roadmap-grid" id="roadmapGrid"></div>
  </section>

  <!-- Stats -->
  <section class="page" id="page-stats">
    <div class="section-head" style="margin-top:0"><div><h2>Statistiques du projet</h2><div class="page-sub">Une vue chiffrée de l'avancement.</div></div></div>
    <div class="grid stat-grid" id="statsMetrics"></div>
    <div class="card chart-card"><div class="chart-title">Avancement par catégorie</div><div class="chart-wrap"><canvas id="chartCat"></canvas></div></div>
    <div class="card chart-card"><div class="chart-title">Répartition par priorité</div><div class="chart-wrap"><canvas id="chartPrio"></canvas></div></div>
  </section>
</main>
</div>

<!-- ═══ MODAL ═══ -->
<div class="modal-backdrop" id="modalBackdrop">
  <div class="modal">
    <div class="modal-head"><div class="modal-title" id="modalTitle">Nouvelle tâche</div><button class="icon-btn" id="modalClose">×</button></div>
    <div id="modalContent"></div>
    <div class="modal-actions"><button class="btn" id="modalCancel">Annuler</button><button class="btn primary" id="modalSave">Enregistrer</button></div>
  </div>
</div>

<!-- ═══ TOAST ═══ -->
<div class="toast" id="toast"></div>

<!-- ═══ BOUTON IA ═══ -->
<button class="ai-launcher" id="aiLauncher" aria-label="Ouvrir l'assistant IA">
  <span class="ai-launcher-spark">✦</span>
  Assistant Aylox
  <span class="ai-online-dot"></span>
</button>

<!-- ═══ SCRIM ═══ -->
<div class="ai-scrim" id="aiScrim"></div>

<!-- ═══ DRAWER IA ═══ -->
<aside class="ai-drawer" id="aiDrawer" role="complementary" aria-label="Assistant IA">
  <div class="ai-drawer-head">
    <div class="ai-brand">
      <div class="ai-brand-icon">✦</div>
      <div><strong>Assistant Aylox</strong><small>Forge 1.20.1 · IA intégrée</small></div>
    </div>
    <div style="display:flex;gap:6px">
      <button class="icon-btn" id="aiClear" title="Effacer la conversation">
        <svg viewBox="0 0 24 24"><path d="M3 6h18M8 6V4h8v2M19 6l-1 14H6L5 6"/></svg>
      </button>
      <button class="icon-btn" id="aiClose" title="Fermer">
        <svg viewBox="0 0 24 24"><path d="M18 6 6 18M6 6l12 12"/></svg>
      </button>
    </div>
  </div>

  <div class="ai-context-bar">
    <span class="ai-context-dot"></span>
    Contexte : <b id="aiContextLabel">chargement…</b>
    <button id="aiContextRefresh" title="Rafraîchir le contexte">↺</button>
  </div>

  <div class="ai-suggestions" id="aiSuggestions">
    <button data-prompt="Propose 5 nouvelles tâches utiles pour ce mod.">💡 Nouvelles tâches</button>
    <button data-prompt="Fais un bilan rapide de l'avancement du projet.">📊 Bilan projet</button>
    <button data-prompt="Quelles sont les priorités les plus urgentes à traiter ?">🔥 Priorités urgentes</button>
    <button data-prompt="Donne-moi 3 conseils pour avancer plus vite sur le mod.">🚀 Conseils dev</button>
  </div>

  <div class="ai-chat" id="aiChat">
    <div class="ai-welcome" id="aiWelcome">
      <div class="ai-welcome-mark">✦</div>
      <strong>Bonjour ! Je suis ton assistant Aylox.</strong>
      <p>Je connais l'état de tes tâches et peux t'aider à avancer sur le mod. Pose-moi une question ou utilise les suggestions ci-dessus.</p>
    </div>
  </div>

  <div class="ai-composer" id="aiComposer">
    <textarea id="aiInput" rows="2" placeholder="Pose une question sur le mod…"></textarea>
    <div class="ai-composer-foot">
      <small>Entrée pour envoyer · Maj+Entrée pour sauter une ligne</small>
      <button class="ai-send" id="aiSend" title="Envoyer">
        <svg viewBox="0 0 24 24" width="14" height="14" stroke="currentColor" fill="none" stroke-width="2.2"><path d="M22 2 11 13M22 2 15 22l-4-9-9-4 20-7Z"/></svg>
      </button>
    </div>
  </div>
  <div class="ai-disclaimer">Les réponses sont générées par IA et peuvent contenir des erreurs.</div>
</aside>

<script>
// ════ CONFIG ════
const SB_URL = 'https://uvewquzymkqxlovwduzs.supabase.co';
const SB_KEY = 'sb_publishable__IOYh5ALGwgmKYYYzwWgsA_61FVxDRa';
const AI_PROXY = 'https://aylox-ai-proxy.aydindnt7.workers.dev/';

const CATEGORIES = [
  {id:'base',    label:'Base / structure',    icon:'code'},
  {id:'meubles', label:'Meubles & objets',     icon:'sofa'},
  {id:'food',    label:'Nourriture & boissons',icon:'food'},
  {id:'textures',label:'Textures & modèles',   icon:'image'},
  {id:'publi',   label:'Publication',          icon:'upload'}
];
const ROADMAP_VERSIONS = ['V1 (actuelle)', 'V2', 'V3', 'Idées futures'];
const PAGE_INFO = {
  dashboard: ['Vue d\'ensemble',   'Le centre de contrôle de ton mod Minecraft.'],
  tasks:     ['Tâches',            'Organise, priorise et suis le développement.'],
  notes:     ['Notes',             'Ton carnet de développement.'],
  changelog: ['Changelog',         'L\'historique des versions du mod.'],
  bugs:      ['Suivi des bugs',    'Les problèmes identifiés et leur résolution.'],
  roadmap:   ['Roadmap',           'Les prochaines évolutions d\'Aylox Furnitures.'],
  stats:     ['Statistiques',      'Les chiffres clés du développement.']
};
const ICONS = {
  code:   '<path d="m8 8-4 4 4 4m8-8 4 4-4 4m-3-11-2 14"/>',
  sofa:   '<path d="M5 11V8a3 3 0 0 1 3-3h8a3 3 0 0 1 3 3v3M4 11a2 2 0 0 1 2 2v3h12v-3a2 2 0 0 1 4 0v4H2v-4a2 2 0 0 1 2-2Zm2 5v3m12-3v3"/>',
  food:   '<path d="M3 10h18M5 10a7 7 0 0 1 14 0M4 14h16l-2 5H6l-2-5Z"/>',
  image:  '<rect x="3" y="3" width="18" height="18" rx="2"/><circle cx="8.5" cy="8.5" r="1.5"/><path d="m21 15-5-5L5 21"/>',
  upload: '<path d="M12 16V3m-5 5 5-5 5 5M4 15v5h16v-5"/>'
};

// ════ ÉTAT ════
let tasks = [], notes = {}, changelogs = [], bugs = [], roadmap = {};
let expanded = new Set(), editingTask = null, editingBug = null, charts = {};
let collapsedCats = new Set();
let activity = [], toastTimer;

// ════ UTILS ════
const $ = id => document.getElementById(id);
const esc = s => String(s ?? '').replace(/[&<>"']/g, c => ({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]));

async function sb(path, opts = {}) {
  const headers = {
    'apikey': SB_KEY, 'Authorization': 'Bearer ' + SB_KEY,
    'Content-Type': 'application/json',
    'Prefer': opts.prefer || 'return=representation',
    ...(opts.headers || {})
  };
  const res = await fetch(SB_URL + '/rest/v1/' + path, { ...opts, headers });
  if (!res.ok) throw new Error((await res.text()) || res.statusText);
  const raw = await res.text();
  return raw ? JSON.parse(raw) : null;
}

function sync(state, label) {
  $('syncDot').className = 'sync-dot' + (state === 'busy' ? ' busy' : state === 'error' ? ' error' : '');
  $('syncLabel').textContent = label;
}
function toast(msg) {
  $('toast').textContent = msg;
  $('toast').classList.add('show');
  clearTimeout(toastTimer);
  toastTimer = setTimeout(() => $('toast').classList.remove('show'), 2400);
}
function record(message) {
  activity.unshift({ message, time: new Date().toISOString() });
  activity = activity.slice(0, 7);
  renderActivity();
}
function relativeDate(date) {
  const d = new Date(date), diff = Math.max(0, Date.now() - d.getTime()), m = Math.floor(diff / 60000);
  if (m < 1) return 'à l\'instant';
  if (m < 60) return `il y a ${m} min`;
  const h = Math.floor(m / 60);
  if (h < 24) return `il y a ${h} h`;
  return d.toLocaleDateString('fr-FR');
}

// ════ INIT ════
async function init() {
  sync('busy', 'Connexion…');
  try {
    const [td, md] = await Promise.all([
      sb('tasks?select=*&order=position.asc,created_at.asc'),
      sb('meta?select=*')
    ]);
    tasks = td || [];
    (md || []).forEach(r => {
      try {
        const v = typeof r.value === 'string' ? JSON.parse(r.value) : r.value;
        if (r.key === 'notes')      notes      = v || {};
        if (r.key === 'changelogs') changelogs = v || [];
        if (r.key === 'bugs')       bugs       = v || [];
        if (r.key === 'roadmap')    roadmap    = v || {};
      } catch(e) { console.warn('Meta illisible:', r.key, e); }
    });
    renderAll();
    sync('ok', 'Synchronisé');
    updateAIContext();
    setInterval(refreshTasks, 30000);
  } catch(e) {
    console.error(e);
    sync('error', 'Connexion impossible');
    $('categories').innerHTML = '<div class="card empty">Impossible de charger les données. Vérifie Supabase et les politiques RLS.</div>';
    toast('Erreur de connexion Supabase');
  }
}

async function refreshTasks() {
  try {
    const data = await sb('tasks?select=*&order=position.asc,created_at.asc');
    tasks = data || [];
    renderAll();
    updateAIContext();
  } catch(e) { console.warn('Synchronisation automatique échouée', e); }
}

async function saveMeta(key, value) {
  const payload = { key, value: JSON.stringify(value) };
  await sb('meta?on_conflict=key', {
    method: 'POST', body: JSON.stringify(payload),
    prefer: 'resolution=merge-duplicates,return=minimal',
    headers: { 'Prefer': 'resolution=merge-duplicates,return=minimal' }
  });
}

// ════ RENDER ════
function renderAll() {
  renderDashboard(); renderTasks(); renderNotes();
  renderChangelog(); renderBugs(); renderRoadmap(); renderStatsMetrics();
  $('sideProgress').style.width = progress() + '%';
  $('sideProgressText').textContent = progress() + '% terminé';
}
function progress() {
  return tasks.length ? Math.round(tasks.filter(t => t.done).length / tasks.length * 100) : 0;
}
function metric(label, value, note, icon) {
  return `<div class="card metric"><div class="metric-top"><span>${label}</span><span class="metric-icon"><svg viewBox="0 0 24 24">${icon}</svg></span></div><div class="metric-value">${value}</div><div class="metric-note">${note}</div></div>`;
}

function renderDashboard() {
  const done = tasks.filter(t => t.done).length, openBugs = bugs.filter(b => b.status === 'ouvert').length;
  $('overviewMetrics').innerHTML =
    metric('Progression globale', progress() + '%', done + ' sur ' + tasks.length + ' tâches', '<path d="M4 19V5m0 14h16M7 15l4-4 3 2 6-7"/>') +
    metric('Tâches terminées', done, 'sur ' + tasks.length + ' tâches au total', '<path d="m5 12 4 4L19 6"/>') +
    metric('Bugs ouverts', openBugs, bugs.length + ' bugs recensés', '<path d="M12 9v4m0 4h.01M10 3h4l7 18H3L10 3Z"/>') +
    metric('Versions publiées', changelogs.length, 'entrées dans le changelog', '<path d="M12 3v18m9-9H3"/>');
  $('dashPct').textContent = progress() + '%';
  $('dashDone').textContent = done + ' / ' + tasks.length + ' tâches terminées';
  $('dashTaskCount').textContent = tasks.length + ' tâches';
  $('dashTrack').style.width = progress() + '%';
  $('dashCategories').innerHTML = CATEGORIES.map(c => {
    const ts = tasks.filter(t => t.cat_id === c.id), d = ts.filter(t => t.done).length, p = ts.length ? Math.round(d / ts.length * 100) : 0;
    return `<div class="progress-line"><span>${esc(c.label)}</span><div class="track"><div class="track-fill" style="width:${p}%"></div></div><b>${d}/${ts.length}</b></div>`;
  }).join('');
  const urgent = tasks.filter(t => !t.done && t.prio === 'haute').slice(0, 5);
  $('priorityTasks').innerHTML = urgent.length
    ? urgent.map(t => `<div class="task" data-prio="haute"><div class="task-top"><button class="check" data-done="${esc(t.id)}" aria-label="Terminer"></button><div class="task-content"><div class="task-name">${esc(t.name)}</div><div class="task-note">${esc(CATEGORIES.find(c => c.id === t.cat_id)?.label || '')}</div></div><span class="pill haute">Haute</span></div></div>`).join('')
    : '<div class="empty">Aucune tâche urgente. Rien à signaler.</div>';
  renderActivity();
}

function renderActivity() {
  $('activityList').innerHTML = activity.length
    ? activity.map(a => `<div class="activity-item"><i class="activity-dot"></i><div><div class="activity-text">${a.message}</div><div class="activity-time">${relativeDate(a.time)}</div></div></div>`).join('')
    : '<div class="empty">Les actions récentes apparaîtront ici.</div>';
}

function filteredTasks() {
  const q = $('taskSearch').value.toLowerCase().trim(), p = $('prioFilter').value, s = $('statusFilter').value;
  return CATEGORIES.map(c => ({
    ...c,
    tasks: tasks.filter(t =>
      t.cat_id === c.id &&
      (!q || (t.name || '').toLowerCase().includes(q) || (t.description || '').toLowerCase().includes(q)) &&
      (!p || t.prio === p) &&
      (!s || (s === 'done' ? t.done : !t.done))
    )
  }));
}

function renderTasks() {
  const groups = filteredTasks();
  $('categories').innerHTML = groups.map(c => {
    const done = c.tasks.filter(t => t.done).length;
    const isCollapsed = collapsedCats.has(c.id);
    const body = isCollapsed ? '' : (c.tasks.length ? c.tasks.map(renderTask).join('') : '<div class="empty">Aucune tâche ici.</div>') + '<div class="add-inline"><input placeholder="＋ Ajouter rapidement…" data-quick="' + c.id + '"></div>';
    return `<div class="card category">
      <div class="category-head">
        <div class="category-name"><span class="category-icon"><svg viewBox="0 0 24 24">${ICONS[c.icon]}</svg></span>${esc(c.label)}</div>
        <div style="display:flex;align-items:center;gap:6px">
          <span class="count ${c.tasks.length && done === c.tasks.length ? 'done' : ''}">${done}/${c.tasks.length}</span>
          <button class="mini-action" data-toggle-cat="${c.id}"><svg viewBox="0 0 24 24"><path d="${isCollapsed ? 'm6 9 6 6 6-6' : 'm18 15-6-6-6 6'}"/></svg></button>
        </div>
      </div>
    ${body}
    </div>`;
  }).join('');
}

function renderTask(t) {
  const open = expanded.has(String(t.id));
  return `<div class="task ${t.done ? 'done' : ''}" data-prio="${esc(t.prio)}">
    <div class="task-top">
      <button class="check ${t.done ? 'checked' : ''}" data-done="${esc(t.id)}" aria-label="Changer le statut">${t.done ? '<svg viewBox="0 0 12 12"><path d="m2 6 2.5 2.5L10 3"/></svg>' : ''}</button>
      <div class="task-content"><div class="task-name">${esc(t.name)}</div>${t.note ? `<div class="task-note">${esc(t.note)}</div>` : ''}</div>
      <div class="task-actions">
        <button class="mini-action" data-edit-task="${esc(t.id)}" title="Modifier"><svg viewBox="0 0 24 24"><path d="m15 5 4 4M4 20l4-.8L19 8a2.8 2.8 0 0 0-4-4L4 15l0 5Z"/></svg></button>
        <button class="mini-action" data-delete-task="${esc(t.id)}" title="Supprimer"><svg viewBox="0 0 24 24"><path d="M4 7h16M10 11v6m4-6v6M6 7l1 14h10l1-14M9 7V4h6v3"/></svg></button>
        <button class="mini-action" data-expand="${esc(t.id)}" title="Description"><svg viewBox="0 0 24 24"><path d="m6 9 6 6 6-6"/></svg></button>
      </div>
    </div>
    <div class="task-bottom">
      <span class="pill ${esc(t.prio)}">${esc(t.prio)}</span>
      ${t.description ? '<span style="font-size:9px;color:var(--soft)">Description disponible</span>' : ''}
    </div>
    <div class="task-desc ${open ? 'open' : ''}">
      ${t.description ? esc(t.description) : '<i>Aucune description.</i>'}
      <div style="margin-top:9px"><button class="btn purple" data-ai-desc="${esc(t.id)}">✦ Améliorer avec l'IA</button></div>
    </div>
  </div>`;
}

// ════ MODAL ════
function openModal(title, html, onSave) {
  $('modalTitle').textContent = title;
  $('modalContent').innerHTML = html;
  $('modalBackdrop').classList.add('open');
  $('modalSave').onclick = async () => {
    try { await onSave(); } catch(e) { console.error(e); toast('Échec de la sauvegarde : ' + e.message); }
  };
}
function closeModal() { $('modalBackdrop').classList.remove('open'); }

function taskForm(t = {}) {
  return `<div class="form-group"><label class="form-label">NOM DE LA TÂCHE *</label><input class="field" id="fName" maxlength="180" value="${esc(t.name || '')}" placeholder="Ex. Ajouter un nouveau meuble"></div>
  <div class="form-row">
    <div class="form-group"><label class="form-label">CATÉGORIE</label><select class="select" style="width:100%" id="fCat">${CATEGORIES.map(c => `<option value="${c.id}" ${t.cat_id === c.id ? 'selected' : ''}>${esc(c.label)}</option>`).join('')}</select></div>
    <div class="form-group"><label class="form-label">PRIORITÉ</label><select class="select" style="width:100%" id="fPrio"><option value="haute" ${t.prio === 'haute' ? 'selected' : ''}>Haute</option><option value="moyenne" ${!t.prio || t.prio === 'moyenne' ? 'selected' : ''}>Moyenne</option><option value="basse" ${t.prio === 'basse' ? 'selected' : ''}>Basse</option></select></div>
  </div>
  <div class="form-group"><label class="form-label">NOTE COURTE</label><input class="field" id="fNote" value="${esc(t.note || '')}" placeholder="Contexte ou dépendance"></div>
  <div class="form-group"><label class="form-label">DESCRIPTION</label><textarea class="textarea" id="fDesc" placeholder="Détails techniques, comportement attendu…">${esc(t.description || '')}</textarea><button class="btn purple" style="margin-top:7px" id="genDesc">✦ Générer avec l'IA</button></div>`;
}

function addTask(t = null) {
  editingTask = t?.id ?? null;
  openModal(t ? 'Modifier la tâche' : 'Nouvelle tâche', taskForm(t || {}), async () => {
    const name = $('fName').value.trim();
    if (!name) { $('fName').focus(); toast('Le nom de la tâche est obligatoire.'); return; }
    const data = { name, cat_id: $('fCat').value, prio: $('fPrio').value, note: $('fNote').value.trim(), description: $('fDesc').value.trim() };
    sync('busy', 'Sauvegarde…');
    if (editingTask) {
      const id = editingTask;
      await sb(`tasks?id=eq.${encodeURIComponent(id)}`, { method: 'PATCH', body: JSON.stringify(data), prefer: 'return=minimal' });
      Object.assign(tasks.find(x => String(x.id) === String(id)), data);
      record('Tâche modifiée : <strong>' + esc(name) + '</strong>');
    } else {
      const id = 't' + Date.now(), position = tasks.filter(x => x.cat_id === data.cat_id).length;
      const row = { id, ...data, done: false, position };
      await sb('tasks', { method: 'POST', body: JSON.stringify(row), prefer: 'return=minimal' });
      tasks.push(row);
      record('Nouvelle tâche : <strong>' + esc(name) + '</strong>');
    }
    closeModal(); sync('ok', 'Synchronisé'); renderAll(); updateAIContext(); toast('Tâche enregistrée');
  });
  $('genDesc').onclick = async () => {
    const n = $('fName').value.trim();
    if (!n) { toast('Ajoute d\'abord un nom.'); return; }
    const b = $('genDesc'); b.disabled = true; b.textContent = 'Génération…';
    try { $('fDesc').value = await callAI(`Pour le mod Minecraft Aylox Furnitures Forge 1.20.1, écris une description technique concrète de 3 à 5 phrases pour : ${n}. Direct, sans introduction.`); }
    catch(e) { toast('Erreur IA : ' + e.message); }
    finally { b.disabled = false; b.textContent = '✦ Générer avec l\'IA'; }
  };
}

async function toggleDone(id) {
  const t = tasks.find(x => String(x.id) === String(id));
  if (!t) return;
  const old = t.done; t.done = !old; renderAll();
  sync('busy', 'Sauvegarde…');
  try {
    await sb(`tasks?id=eq.${encodeURIComponent(id)}`, { method: 'PATCH', body: JSON.stringify({ done: t.done }), prefer: 'return=minimal' });
    sync('ok', 'Synchronisé');
    record((t.done ? 'Tâche terminée : ' : 'Tâche rouverte : ') + '<strong>' + esc(t.name) + '</strong>');
    updateAIContext();
  } catch(e) { t.done = old; renderAll(); sync('error', 'Erreur de sauvegarde'); toast('Impossible de modifier cette tâche'); }
}

async function deleteTask(id) {
  const t = tasks.find(x => String(x.id) === String(id));
  if (!t || !confirm('Supprimer la tâche « ' + t.name + ' » ?')) return;
  try {
    await sb(`tasks?id=eq.${encodeURIComponent(id)}`, { method: 'DELETE', prefer: 'return=minimal' });
    tasks = tasks.filter(x => String(x.id) !== String(id));
    renderAll(); updateAIContext();
    record('Tâche supprimée : <strong>' + esc(t.name) + '</strong>');
    toast('Tâche supprimée');
  } catch(e) { toast('Suppression impossible : ' + e.message); }
}

async function quickAdd(input) {
  const name = input.value.trim();
  if (!name) return;
  const cat_id = input.dataset.quick, id = 't' + Date.now();
  const row = { id, cat_id, name, prio: 'moyenne', note: '', description: '', done: false, position: tasks.filter(t => t.cat_id === cat_id).length };
  input.disabled = true;
  try {
    await sb('tasks', { method: 'POST', body: JSON.stringify(row), prefer: 'return=minimal' });
    tasks.push(row); renderAll(); updateAIContext();
    record('Tâche ajoutée : <strong>' + esc(name) + '</strong>');
    toast('Tâche ajoutée');
  } catch(e) { input.disabled = false; toast('Ajout impossible : ' + e.message); }
}

// Notes
function renderNotes() {
  $('notesGrid').innerHTML = CATEGORIES.map(c =>
    `<div class="card note-card"><div class="note-head">${esc(c.label)}</div><textarea class="note-area" id="note-${c.id}" placeholder="Notes, idées, détails techniques…">${esc(notes[c.id] || '')}</textarea><div class="note-foot"><button class="btn primary" data-save-note="${c.id}">Sauvegarder</button></div></div>`
  ).join('');
}
async function saveNote(id) {
  notes[id] = $('note-' + id).value;
  try {
    await saveMeta('notes', notes);
    toast('Note sauvegardée');
    record('Note mise à jour : <strong>' + esc(CATEGORIES.find(c => c.id === id).label) + '</strong>');
  } catch(e) { toast('Erreur de sauvegarde des notes : ' + e.message); }
}

// Changelog
function renderChangelog() {
  $('changelogList').innerHTML = changelogs.length
    ? changelogs.map(c => `<div class="card version-card"><div class="version-head"><span class="version-name">Version ${esc(c.version)}</span><span class="version-date">${esc(c.date || 'Date non précisée')}</span></div><div class="version-body">${(c.changes || []).map(x => `<div class="version-entry">${esc(x)}</div>`).join('')}</div><div class="card-actions"><button class="btn danger" data-delete-cl="${esc(c.id)}">Supprimer</button></div></div>`).join('')
    : '<div class="card empty">Aucune version enregistrée. Ajoute la première version du mod.</div>';
}
function addVersion() {
  openModal('Nouvelle version',
    `<div class="form-group"><label class="form-label">VERSION *</label><input class="field" id="clVersion" placeholder="1.1.0"></div>
     <div class="form-group"><label class="form-label">DATE</label><input class="field" id="clDate" type="date" value="${new Date().toISOString().slice(0,10)}"></div>
     <div class="form-group"><label class="form-label">CHANGEMENTS — UN PAR LIGNE *</label><textarea class="textarea" id="clChanges" style="min-height:130px" placeholder="Nouveau meuble ajouté&#10;Correction du bug d\'inventaire"></textarea></div>`,
    async () => {
      const version = $('clVersion').value.trim(), changes = $('clChanges').value.split('\n').map(x => x.trim()).filter(Boolean);
      if (!version || !changes.length) { toast('Version et changements obligatoires.'); return; }
      changelogs.unshift({ id: 'cl' + Date.now(), version, date: $('clDate').value, changes });
      await saveMeta('changelogs', changelogs);
      closeModal(); renderChangelog(); renderDashboard();
      record('Version ajoutée : <strong>v' + esc(version) + '</strong>');
      toast('Version ajoutée');
    }
  );
}
async function deleteChangelog(id) {
  if (!confirm('Supprimer cette entrée du changelog ?')) return;
  changelogs = changelogs.filter(x => String(x.id) !== String(id));
  try { await saveMeta('changelogs', changelogs); renderChangelog(); renderDashboard(); toast('Version supprimée'); }
  catch(e) { toast('Erreur : ' + e.message); }
}

// Bugs
function renderBugs() {
  const f = $('bugFilter').value, list = bugs.filter(b => !f || b.status === f);
  $('bugsList').innerHTML = list.length
    ? list.map(b => `<div class="card bug-card ${b.status === 'en cours' ? 'en-cours' : b.status === 'corrigé' ? 'corrige' : ''}"><div class="bug-head"><div class="bug-title">${esc(b.title)}</div><span class="bug-status ${b.status === 'en cours' ? 'en-cours' : b.status === 'corrigé' ? 'corrige' : ''}">${esc(b.status)}</span></div>${b.desc ? `<div class="bug-desc">${esc(b.desc)}</div>` : ''}<div class="bug-foot"><span class="bug-version">${b.version ? 'Version concernée : ' + esc(b.version) : 'Version non précisée'}</span><div style="display:flex;gap:6px"><button class="btn" data-edit-bug="${esc(b.id)}">Modifier</button><button class="btn danger" data-delete-bug="${esc(b.id)}">Supprimer</button></div></div></div>`).join('')
    : '<div class="card empty">Aucun bug dans cette sélection.</div>';
}
function addBug(b = null) {
  editingBug = b?.id ?? null;
  openModal(b ? 'Modifier le bug' : 'Signaler un bug',
    `<div class="form-group"><label class="form-label">TITRE *</label><input class="field" id="bugTitle" value="${esc(b?.title || '')}" placeholder="Décris le problème en quelques mots"></div>
     <div class="form-group"><label class="form-label">DESCRIPTION</label><textarea class="textarea" id="bugDesc" placeholder="Étapes pour reproduire, résultat attendu…">${esc(b?.desc || '')}</textarea></div>
     <div class="form-row">
       <div class="form-group"><label class="form-label">STATUT</label><select class="select" id="bugStatus" style="width:100%"><option ${!b || b.status === 'ouvert' ? 'selected' : ''}>ouvert</option><option ${b?.status === 'en cours' ? 'selected' : ''}>en cours</option><option ${b?.status === 'corrigé' ? 'selected' : ''}>corrigé</option></select></div>
       <div class="form-group"><label class="form-label">VERSION AFFECTÉE</label><input class="field" id="bugVersion" value="${esc(b?.version || '')}" placeholder="1.0.0"></div>
     </div>`,
    async () => {
      const title = $('bugTitle').value.trim();
      if (!title) { toast('Le titre est obligatoire.'); return; }
      const row = { id: editingBug || 'bug' + Date.now(), title, desc: $('bugDesc').value.trim(), status: $('bugStatus').value, version: $('bugVersion').value.trim() };
      if (editingBug) bugs = bugs.map(x => String(x.id) === String(editingBug) ? row : x);
      else bugs.unshift(row);
      await saveMeta('bugs', bugs);
      closeModal(); renderBugs(); renderDashboard();
      toast('Bug enregistré');
      record('Bug ' + (editingBug ? 'modifié' : 'ajouté') + ' : <strong>' + esc(title) + '</strong>');
    }
  );
}
async function deleteBug(id) {
  if (!confirm('Supprimer ce bug ?')) return;
  bugs = bugs.filter(b => String(b.id) !== String(id));
  try { await saveMeta('bugs', bugs); renderBugs(); renderDashboard(); toast('Bug supprimé'); }
  catch(e) { toast('Erreur : ' + e.message); }
}

// Roadmap
function renderRoadmap() {
  $('roadmapGrid').innerHTML = ROADMAP_VERSIONS.map(v => {
    const items = roadmap[v] || [];
    return `<div class="card roadmap-col"><div class="roadmap-head"><span class="roadmap-name">${esc(v)}</span><span class="count">${items.length}</span></div>
      ${items.map((item, i) => `<div class="roadmap-item"><span>${esc(item)}</span><button class="mini-action" data-delete-roadmap="${ROADMAP_VERSIONS.indexOf(v)}:${i}">×</button></div>`).join('')}
      <div class="roadmap-add"><input data-roadmap-add="${esc(v)}" placeholder="＋ Ajouter une idée…"></div>
    </div>`;
  }).join('');
}
async function addRoadmap(v, input) {
  const value = input.value.trim();
  if (!value) return;
  roadmap[v] = roadmap[v] || [];
  roadmap[v].push(value);
  try { await saveMeta('roadmap', roadmap); renderRoadmap(); toast('Idée ajoutée'); }
  catch(e) { toast('Erreur : ' + e.message); }
}
async function deleteRoadmap(key) {
  const [v, i] = key.split(':');
  roadmap[ROADMAP_VERSIONS[Number(v)]].splice(Number(i), 1);
  try { await saveMeta('roadmap', roadmap); renderRoadmap(); toast('Élément supprimé'); }
  catch(e) { toast('Erreur : ' + e.message); }
}

// Stats
function renderStatsMetrics() {
  const done = tasks.filter(t => t.done).length, high = tasks.filter(t => !t.done && t.prio === 'haute').length, open = bugs.filter(b => b.status === 'ouvert').length;
  $('statsMetrics').innerHTML =
    metric('Progression', progress() + '%', done + '/' + tasks.length + ' tâches', '<path d="M4 19V5m0 14h16"/>') +
    metric('Priorité haute', high, 'tâches non terminées', '<path d="M12 9v4m0 4h.01M10 3h4l7 18H3L10 3Z"/>') +
    metric('Bugs ouverts', open, 'sur ' + bugs.length + ' bugs', '<path d="M12 9v4m0 4h.01"/>');
}
function renderCharts() {
  if (!window.Chart) return;
  const dark = document.documentElement.dataset.theme === 'dark', tc = dark ? '#a2ad9e' : '#747d70', grid = dark ? '#303830' : '#e7e9e4';
  Object.values(charts).forEach(c => c?.destroy());
  const labels = CATEGORIES.map(c => c.label), done = CATEGORIES.map(c => tasks.filter(t => t.cat_id === c.id && t.done).length), total = CATEGORIES.map(c => tasks.filter(t => t.cat_id === c.id).length);
  charts.cat = new Chart($('chartCat'), { type: 'bar', data: { labels, datasets: [{ label: 'Terminées', data: done, backgroundColor: '#789e59', borderRadius: 5 }, { label: 'Restantes', data: total.map((n, i) => n - done[i]), backgroundColor: dark ? '#3b453b' : '#e7e9e4', borderRadius: 5 }] }, options: { responsive: true, maintainAspectRatio: false, plugins: { legend: { labels: { color: tc, font: { size: 10 } } } }, scales: { x: { stacked: true, ticks: { color: tc, font: { size: 10 } }, grid: { display: false } }, y: { stacked: true, ticks: { color: tc, precision: 0 }, grid: { color: grid } } } } });
  const ps = ['haute', 'moyenne', 'basse'], pd = ps.map(p => tasks.filter(t => t.prio === p && t.done).length), pt = ps.map(p => tasks.filter(t => t.prio === p).length);
  charts.prio = new Chart($('chartPrio'), { type: 'bar', data: { labels: ['Haute', 'Moyenne', 'Basse'], datasets: [{ label: 'Terminées', data: pd, backgroundColor: ['#d65b56', '#c58a31', '#648d43'], borderRadius: 5 }, { label: 'Restantes', data: pt.map((n, i) => n - pd[i]), backgroundColor: dark ? '#3b453b' : '#e7e9e4', borderRadius: 5 }] }, options: { responsive: true, maintainAspectRatio: false, plugins: { legend: { labels: { color: tc, font: { size: 10 } } } }, scales: { x: { stacked: true, ticks: { color: tc }, grid: { display: false } }, y: { stacked: true, ticks: { color: tc, precision: 0 }, grid: { color: grid } } } } });
}

// ════ IA — appel proxy ════
async function callAI(prompt) {
  const r = await fetch(AI_PROXY, { method: 'POST', headers: { 'Content-Type': 'application/json' }, body: JSON.stringify({ prompt }) });
  if (!r.ok) throw new Error('Proxy IA indisponible (' + r.status + ')');
  const j = await r.json();
  if (j.error) throw new Error(j.error);
  return j.text || 'Aucune réponse reçue.';
}

// ════ IA — amélioration de description de tâche ════
async function aiImproveTask(id) {
  const t = tasks.find(x => String(x.id) === String(id));
  if (!t) return;
  try {
    const text = await callAI(`Améliore la description technique de cette tâche pour le mod Minecraft Aylox Furnitures Forge 1.20.1. Tâche : ${t.name}. Description actuelle : ${t.description || 'aucune'}. Donne 3 à 5 phrases concrètes, sans introduction.`);
    if (confirm('Suggestion IA :\n\n' + text + '\n\nRemplacer la description actuelle ?')) {
      await sb(`tasks?id=eq.${encodeURIComponent(id)}`, { method: 'PATCH', body: JSON.stringify({ description: text }), prefer: 'return=minimal' });
      t.description = text; renderTasks(); toast('Description mise à jour');
    }
  } catch(e) { toast('Erreur IA : ' + e.message); }
}

// ════ IA — DRAWER (nouveau système) ════
let aiMessages = []; // historique de la conversation courante

function buildAIContext() {
  // Résumé compact des tâches pour le prompt système
  const done = tasks.filter(t => t.done).length;
  const lines = CATEGORIES.map(c => {
    const ts = tasks.filter(t => t.cat_id === c.id);
    const d = ts.filter(t => t.done).length;
    return `${c.label}: ${d}/${ts.length} terminées`;
  }).join(', ');
  return `Mod Minecraft Aylox Furnitures (Forge 1.20.1). Avancement global : ${progress()}% (${done}/${tasks.length} tâches). Détail : ${lines}. Bugs ouverts : ${bugs.filter(b => b.status === 'ouvert').length}.`;
}

function updateAIContext() {
  const ctx = buildAIContext();
  $('aiContextLabel').textContent = `${progress()}% · ${tasks.filter(t => t.done).length}/${tasks.length} tâches`;
}

function openAIDrawer() {
  $('aiDrawer').classList.add('open');
  $('aiScrim').classList.add('open');
  $('aiInput').focus();
}
function closeAIDrawer() {
  $('aiDrawer').classList.remove('open');
  $('aiScrim').classList.remove('open');
}

function appendAIMessage(role, text) {
  // Supprime le message de bienvenue dès le premier échange
  const welcome = $('aiWelcome');
  if (welcome) welcome.remove();

  const div = document.createElement('div');
  div.className = 'ai-message ' + role;
  div.innerHTML = `<div class="ai-message-role">${role === 'user' ? 'Toi' : 'Aylox IA'}</div><div class="ai-message-body">${esc(text)}</div>`;
  $('aiChat').appendChild(div);
  $('aiChat').scrollTop = $('aiChat').scrollHeight;
  return div;
}

function showAITyping() {
  const div = document.createElement('div');
  div.id = 'aiTypingIndicator';
  div.className = 'ai-typing';
  div.innerHTML = '<i></i><i></i><i></i>';
  $('aiChat').appendChild(div);
  $('aiChat').scrollTop = $('aiChat').scrollHeight;
}
function hideAITyping() {
  const el = $('aiTypingIndicator');
  if (el) el.remove();
}

async function sendAIMessage(userText) {
  const text = (userText || $('aiInput').value).trim();
  if (!text) return;
  $('aiInput').value = '';
  $('aiSend').disabled = true;

  appendAIMessage('user', text);
  aiMessages.push({ role: 'user', content: text });
  showAITyping();

  // Prompt système injecté à chaque appel (stateless proxy)
  const context = buildAIContext();
  const systemInfo = `Tu es l'assistant intégré de l'outil de développement du mod Minecraft Aylox Furnitures (Forge 1.20.1). Contexte actuel : ${context}. Réponds en français, de façon concise et utile pour un développeur de mod.`;
  const fullPrompt = `[CONTEXTE SYSTÈME : ${systemInfo}]\n\nHistorique :\n${aiMessages.slice(-6).map(m => `${m.role === 'user' ? 'Utilisateur' : 'Assistant'}: ${m.content}`).join('\n')}\n\nAssistant:`;

  try {
    const reply = await callAI(fullPrompt);
    hideAITyping();
    appendAIMessage('assistant', reply);
    aiMessages.push({ role: 'assistant', content: reply });
  } catch(e) {
    hideAITyping();
    const errDiv = appendAIMessage('error', 'Impossible de contacter l\'assistant : ' + e.message);
    errDiv.className = 'ai-message error';
  } finally {
    $('aiSend').disabled = false;
    $('aiInput').focus();
  }
}

function clearAIChat() {
  aiMessages = [];
  $('aiChat').innerHTML = `<div class="ai-welcome" id="aiWelcome">
    <div class="ai-welcome-mark">✦</div>
    <strong>Bonjour ! Je suis ton assistant Aylox.</strong>
    <p>Je connais l'état de tes tâches et peux t'aider à avancer sur le mod. Pose-moi une question ou utilise les suggestions ci-dessus.</p>
  </div>`;
}

// ════ NAVIGATION ════
function navigate(page) {
  document.querySelectorAll('.page').forEach(p => p.classList.toggle('active', p.id === 'page-' + page));
  document.querySelectorAll('#nav button').forEach(b => b.classList.toggle('active', b.dataset.page === page));
  $('pageTitle').textContent = PAGE_INFO[page][0];
  $('pageSub').textContent = PAGE_INFO[page][1];
  $('crumb').textContent = page.toUpperCase();
  $('sidebar').classList.remove('open');
  if (page === 'stats') renderCharts();
}

function exportJSON() {
  const data = { exportedAt: new Date().toISOString(), categories: CATEGORIES, tasks, notes, changelogs, bugs, roadmap };
  const blob = new Blob([JSON.stringify(data, null, 2)], { type: 'application/json' }), url = URL.createObjectURL(blob), a = document.createElement('a');
  a.href = url; a.download = 'aylox-furnitures-tracker.json'; a.click(); URL.revokeObjectURL(url);
  toast('Export JSON téléchargé');
}

function applyTheme(mode) {
  document.documentElement.dataset.theme = mode === 'dark' ? 'dark' : 'light';
  localStorage.setItem('aylox_theme', mode);
  $('themeBtn').innerHTML = mode === 'dark'
    ? '<svg viewBox="0 0 24 24"><circle cx="12" cy="12" r="4"/><path d="M12 2v2m0 16v2M4.9 4.9l1.4 1.4m11.4 11.4 1.4 1.4M2 12h2m16 0h2M4.9 19.1l1.4-1.4M17.7 6.3l1.4-1.4"/></svg>'
    : '<svg viewBox="0 0 24 24"><path d="M20 15.5A8 8 0 0 1 8.5 4 8.5 8.5 0 1 0 20 15.5Z"/></svg>';
  if ($('page-stats').classList.contains('active')) renderCharts();
}

// ════ EVENT LISTENERS ════
document.addEventListener('click', e => {
  const b = e.target.closest('button');
  if (!b) return;
  if (b.dataset.page)        navigate(b.dataset.page);
  if (b.dataset.goto)        navigate(b.dataset.goto);
  if (b.dataset.done)        toggleDone(b.dataset.done);
  if (b.dataset.editTask)    { const t = tasks.find(x => String(x.id) === b.dataset.editTask); if (t) addTask(t); }
  if (b.dataset.deleteTask)  deleteTask(b.dataset.deleteTask);
  if (b.dataset.expand)      { const id = b.dataset.expand; expanded.has(id) ? expanded.delete(id) : expanded.add(id); renderTasks(); }
  if (b.dataset.saveNote)    saveNote(b.dataset.saveNote);
  if (b.dataset.deleteCl)    deleteChangelog(b.dataset.deleteCl);
  if (b.dataset.editBug)     { const bug = bugs.find(x => String(x.id) === b.dataset.editBug); if (bug) addBug(bug); }
  if (b.dataset.deleteBug)   deleteBug(b.dataset.deleteBug);
  if (b.dataset.deleteRoadmap) deleteRoadmap(b.dataset.deleteRoadmap);
  if (b.dataset.aiDesc)      aiImproveTask(b.dataset.aiDesc);
  if (b.dataset.toggleCat) {
    const id = b.dataset.toggleCat;
    collapsedCats.has(id) ? collapsedCats.delete(id) : collapsedCats.add(id);
    renderTasks();
  }
  // Suggestions IA rapides
  if (b.dataset.prompt)      sendAIMessage(b.dataset.prompt);
});

document.addEventListener('keydown', e => {
  if (e.key === 'Enter' && e.target.matches('[data-quick]'))       quickAdd(e.target);
  if (e.key === 'Enter' && e.target.matches('[data-roadmap-add]')) addRoadmap(e.target.dataset.roadmapAdd, e.target);
  if (e.key === 'Escape') { closeModal(); closeAIDrawer(); }
});

// Envoi avec Entrée dans le composer IA (Maj+Entrée = saut de ligne)
$('aiInput').addEventListener('keydown', e => {
  if (e.key === 'Enter' && !e.shiftKey) { e.preventDefault(); sendAIMessage(); }
});

$('nav').addEventListener('click', e => { const b = e.target.closest('button[data-page]'); if (b) navigate(b.dataset.page); });
$('quickAdd').onclick    = () => addTask();
$('addTaskBtn').onclick  = () => addTask();
$('taskSearch').oninput  = renderTasks;
$('prioFilter').onchange = renderTasks;
$('statusFilter').onchange = renderTasks;
$('bugFilter').onchange  = renderBugs;
$('addVersion').onclick  = addVersion;
$('addBug').onclick      = () => addBug();
$('exportBtn').onclick   = exportJSON;
$('themeBtn').onclick    = () => applyTheme(document.documentElement.dataset.theme === 'dark' ? 'light' : 'dark');
$('menuBtn').onclick     = () => $('sidebar').classList.toggle('open');
$('modalClose').onclick  = closeModal;
$('modalCancel').onclick = closeModal;
$('modalBackdrop').onclick = e => { if (e.target === $('modalBackdrop')) closeModal(); };

// Drawer IA
$('aiLauncher').onclick       = openAIDrawer;
$('aiClose').onclick          = closeAIDrawer;
$('aiScrim').onclick          = closeAIDrawer;
$('aiSend').onclick           = () => sendAIMessage();
$('aiClear').onclick          = clearAIChat;
$('aiContextRefresh').onclick = updateAIContext;

// Thème & init
applyTheme(localStorage.getItem('aylox_theme') === 'dark' ? 'dark' : 'light');
init();

// ════ IA — appel proxy ════
async function callAI(prompt) {
  const r = await fetch(AI_PROXY, { method: 'POST', headers: { 'Content-Type': 'application/json' }, body: JSON.stringify({ prompt }) });
  if (!r.ok) throw new Error('Proxy IA indisponible (' + r.status + ')');
  const j = await r.json();
  if (j.error) throw new Error(j.error);
  return j.text || 'Aucune réponse reçue.';
}

// ════ IA — amélioration de description de tâche ════
async function aiImproveTask(id) {
  const t = tasks.find(x => String(x.id) === String(id));
  if (!t) return;
  try {
    const text = await callAI(`Améliore la description technique de cette tâche pour le mod Minecraft Aylox Furnitures Forge 1.20.1. Tâche : ${t.name}. Description actuelle : ${t.description || 'aucune'}. Donne 3 à 5 phrases concrètes, sans introduction.`);
    if (confirm('Suggestion IA :\n\n' + text + '\n\nRemplacer la description actuelle ?')) {
      await sb(`tasks?id=eq.${encodeURIComponent(id)}`, { method: 'PATCH', body: JSON.stringify({ description: text }), prefer: 'return=minimal' });
      t.description = text; renderTasks(); toast('Description mise à jour');
    }
  } catch(e) { toast('Erreur IA : ' + e.message); }
}

// ════ IA — DRAWER ════
let aiMessages = [];

// Contexte détaillé : liste toutes les tâches avec leurs IDs pour que l'IA puisse les cibler
function buildAIContext() {
  const done = tasks.filter(t => t.done).length;
  const taskList = tasks.map(t =>
    `[${t.id}] "${t.name}" | cat:${t.cat_id} | prio:${t.prio} | ${t.done ? 'terminée' : 'à faire'}`
  ).join('\n');
  const bugList = bugs.map(b => `[${b.id}] "${b.title}" | statut:${b.status}`).join('\n');
  return { summary: `${progress()}% (${done}/${tasks.length} tâches). Bugs ouverts : ${bugs.filter(b => b.status === 'ouvert').length}.`, taskList, bugList };
}

function updateAIContext() {
  $('aiContextLabel').textContent = `${progress()}% · ${tasks.filter(t => t.done).length}/${tasks.length} tâches`;
}

function openAIDrawer() {
  $('aiDrawer').classList.add('open');
  $('aiScrim').classList.add('open');
  $('aiInput').focus();
}
function closeAIDrawer() {
  $('aiDrawer').classList.remove('open');
  $('aiScrim').classList.remove('open');
}

function appendAIMessage(role, text) {
  const welcome = $('aiWelcome');
  if (welcome) welcome.remove();
  const div = document.createElement('div');
  div.className = 'ai-message ' + role;
  div.innerHTML = `<div class="ai-message-role">${role === 'user' ? 'Toi' : 'Aylox IA'}</div><div class="ai-message-body">${esc(text)}</div>`;
  $('aiChat').appendChild(div);
  $('aiChat').scrollTop = $('aiChat').scrollHeight;
  return div;
}

function showAITyping() {
  const div = document.createElement('div');
  div.id = 'aiTypingIndicator';
  div.className = 'ai-typing';
  div.innerHTML = '<i></i><i></i><i></i>';
  $('aiChat').appendChild(div);
  $('aiChat').scrollTop = $('aiChat').scrollHeight;
}
function hideAITyping() {
  const el = $('aiTypingIndicator');
  if (el) el.remove();
}

// ════ IA — exécution des actions ════
// L'IA répond avec du texte libre + optionnellement %%ACTION%%{...}%%
// On parse le bloc action, on l'exécute, puis on informe l'IA du résultat

async function executeAIAction(action) {
  const { type, payload } = action;

  // --- TÂCHES ---
  if (type === 'add_task') {
    const id = 't' + Date.now();
    const cat = CATEGORIES.find(c => c.id === payload.cat_id) ? payload.cat_id : 'base';
    const row = {
      id, name: payload.name, cat_id: cat,
      prio: payload.prio || 'moyenne',
      note: payload.note || '', description: payload.description || '',
      done: false, position: tasks.filter(t => t.cat_id === cat).length
    };
    await sb('tasks', { method: 'POST', body: JSON.stringify(row), prefer: 'return=minimal' });
    tasks.push(row);
    record('IA — Tâche ajoutée : <strong>' + esc(row.name) + '</strong>');
    return `Tâche "${row.name}" ajoutée dans "${CATEGORIES.find(c=>c.id===cat)?.label}".`;
  }

  if (type === 'edit_task') {
    const t = tasks.find(x => String(x.id) === String(payload.id));
    if (!t) throw new Error('Tâche introuvable : ' + payload.id);
    const data = {};
    if (payload.name)        data.name        = payload.name;
    if (payload.cat_id)      data.cat_id      = payload.cat_id;
    if (payload.prio)        data.prio        = payload.prio;
    if (payload.note  !== undefined) data.note = payload.note;
    if (payload.description !== undefined) data.description = payload.description;
    if (payload.done  !== undefined) data.done = payload.done;
    await sb(`tasks?id=eq.${encodeURIComponent(t.id)}`, { method: 'PATCH', body: JSON.stringify(data), prefer: 'return=minimal' });
    Object.assign(t, data);
    record('IA — Tâche modifiée : <strong>' + esc(t.name) + '</strong>');
    return `Tâche "${t.name}" mise à jour.`;
  }

  if (type === 'delete_task') {
    const t = tasks.find(x => String(x.id) === String(payload.id));
    if (!t) throw new Error('Tâche introuvable : ' + payload.id);
    await sb(`tasks?id=eq.${encodeURIComponent(t.id)}`, { method: 'DELETE', prefer: 'return=minimal' });
    tasks = tasks.filter(x => String(x.id) !== String(t.id));
    record('IA — Tâche supprimée : <strong>' + esc(t.name) + '</strong>');
    return `Tâche "${t.name}" supprimée.`;
  }

  if (type === 'toggle_task') {
    const t = tasks.find(x => String(x.id) === String(payload.id));
    if (!t) throw new Error('Tâche introuvable : ' + payload.id);
    t.done = !t.done;
    await sb(`tasks?id=eq.${encodeURIComponent(t.id)}`, { method: 'PATCH', body: JSON.stringify({ done: t.done }), prefer: 'return=minimal' });
    record('IA — Tâche ' + (t.done ? 'terminée' : 'rouverte') + ' : <strong>' + esc(t.name) + '</strong>');
    return `Tâche "${t.name}" marquée comme ${t.done ? 'terminée ✓' : 'à faire'}.`;
  }

  // --- BUGS ---
  if (type === 'add_bug') {
    const row = {
      id: 'bug' + Date.now(), title: payload.title,
      desc: payload.desc || '', status: payload.status || 'ouvert',
      version: payload.version || ''
    };
    bugs.unshift(row);
    await saveMeta('bugs', bugs);
    record('IA — Bug ajouté : <strong>' + esc(row.title) + '</strong>');
    return `Bug "${row.title}" signalé (statut : ${row.status}).`;
  }

  if (type === 'edit_bug') {
    const b = bugs.find(x => String(x.id) === String(payload.id));
    if (!b) throw new Error('Bug introuvable : ' + payload.id);
    if (payload.title)   b.title   = payload.title;
    if (payload.desc !== undefined) b.desc = payload.desc;
    if (payload.status)  b.status  = payload.status;
    if (payload.version !== undefined) b.version = payload.version;
    await saveMeta('bugs', bugs);
    record('IA — Bug modifié : <strong>' + esc(b.title) + '</strong>');
    return `Bug "${b.title}" mis à jour (statut : ${b.status}).`;
  }

  if (type === 'delete_bug') {
    const b = bugs.find(x => String(x.id) === String(payload.id));
    if (!b) throw new Error('Bug introuvable : ' + payload.id);
    bugs = bugs.filter(x => String(x.id) !== String(b.id));
    await saveMeta('bugs', bugs);
    record('IA — Bug supprimé : <strong>' + esc(b.title) + '</strong>');
    return `Bug "${b.title}" supprimé.`;
  }

  // --- CHANGELOG ---
  if (type === 'add_changelog') {
    const entry = {
      id: 'cl' + Date.now(), version: payload.version,
      date: payload.date || new Date().toISOString().slice(0, 10),
      changes: payload.changes || []
    };
    changelogs.unshift(entry);
    await saveMeta('changelogs', changelogs);
    record('IA — Version ajoutée : <strong>v' + esc(entry.version) + '</strong>');
    return `Version ${entry.version} ajoutée au changelog (${entry.changes.length} changement(s)).`;
  }

  // --- ROADMAP ---
  if (type === 'add_roadmap') {
    const v = payload.version;
    if (!ROADMAP_VERSIONS.includes(v)) throw new Error('Version roadmap invalide : ' + v);
    roadmap[v] = roadmap[v] || [];
    roadmap[v].push(payload.item);
    await saveMeta('roadmap', roadmap);
    return `"${payload.item}" ajouté à la roadmap ${v}.`;
  }

  throw new Error('Action inconnue : ' + type);
}

// ════ IA — envoi de message principal ════
async function sendAIMessage(userText) {
  const text = (userText || $('aiInput').value).trim();
  if (!text) return;
  $('aiInput').value = '';
  $('aiSend').disabled = true;

  appendAIMessage('user', text);
  aiMessages.push({ role: 'user', content: text });
  showAITyping();

  const ctx = buildAIContext();

  // Prompt système : contexte + liste des actions disponibles
  const systemPrompt = `Tu es l'assistant intégré de l'outil de développement du mod Minecraft Aylox Furnitures (Forge 1.20.1).

ÉTAT ACTUEL DU PROJET :
${ctx.summary}

LISTE DES TÂCHES (id | nom | catégorie | priorité | statut) :
${ctx.taskList || '(aucune tâche)'}

LISTE DES BUGS (id | titre | statut) :
${ctx.bugList || '(aucun bug)'}

CATÉGORIES DISPONIBLES : base, meubles, food, textures, publi
PRIORITÉS DISPONIBLES : haute, moyenne, basse
STATUTS BUG : ouvert, en cours, corrigé
VERSIONS ROADMAP : "V1 (actuelle)", "V2", "V3", "Idées futures"

TU PEUX EFFECTUER DES ACTIONS RÉELLES sur le projet. Pour ce faire, inclus à la fin de ta réponse un bloc action dans ce format exact :
%%ACTION%%{"type":"add_task","payload":{"name":"...","cat_id":"...","prio":"..."}}%%

ACTIONS DISPONIBLES :
- add_task       : payload { name*, cat_id*, prio, note, description }
- edit_task      : payload { id*, name, cat_id, prio, note, description, done }
- delete_task    : payload { id* }
- toggle_task    : payload { id* }  (bascule terminée/à faire)
- add_bug        : payload { title*, desc, status, version }
- edit_bug       : payload { id*, title, desc, status, version }
- delete_bug     : payload { id* }
- add_changelog  : payload { version*, date, changes[] }
- add_roadmap    : payload { version*, item* }

RÈGLES :
- N'exécute UNE SEULE action par réponse.
- Si l'utilisateur demande plusieurs actions, fais-en une et demande confirmation pour la suite.
- Réponds TOUJOURS en français, de façon concise.
- Si tu ne fais pas d'action, ne mets pas de bloc %%ACTION%%.
- Le bloc %%ACTION%% doit être du JSON valide.`;

  const fullPrompt = `[SYSTÈME]\n${systemPrompt}\n\n[HISTORIQUE]\n${aiMessages.slice(-8).map(m => `${m.role === 'user' ? 'Utilisateur' : 'Assistant'}: ${m.content}`).join('\n')}\n\nAssistant:`;

  try {
    const reply = await callAI(fullPrompt);
    hideAITyping();

    // Sépare le texte du bloc action
    const actionMatch = reply.match(/%%ACTION%%(\{[\s\S]*?\})%%/);
    const displayText = reply.replace(/%%ACTION%%[\s\S]*?%%/g, '').trim();

    // Affiche le texte
    if (displayText) {
      appendAIMessage('assistant', displayText);
      aiMessages.push({ role: 'assistant', content: displayText });
    }

    // Exécute l'action si présente
    if (actionMatch) {
      let action;
      try {
        action = JSON.parse(actionMatch[1]);
      } catch(e) {
        appendAIMessage('error', 'L\'IA a renvoyé une action invalide (JSON malformé).');
        return;
      }

      // Indicateur d'exécution
      showAITyping();
      try {
        const result = await executeAIAction(action);
        hideAITyping();
        renderAll();
        updateAIContext();
        sync('ok', 'Synchronisé');

        // Message de confirmation de l'action
        const confirmMsg = '✓ ' + result;
        appendAIMessage('assistant', confirmMsg);
        aiMessages.push({ role: 'assistant', content: confirmMsg });
        toast(result);
      } catch(e) {
        hideAITyping();
        appendAIMessage('error', 'Échec de l\'action : ' + e.message);
        sync('error', 'Erreur action IA');
      }
    }

  } catch(e) {
    hideAITyping();
    const errDiv = appendAIMessage('assistant', 'Impossible de contacter l\'assistant : ' + e.message);
    errDiv.className = 'ai-message error';
  } finally {
    $('aiSend').disabled = false;
    $('aiInput').focus();
  }
}

function clearAIChat() {
  aiMessages = [];
  $('aiChat').innerHTML = `<div class="ai-welcome" id="aiWelcome">
    <div class="ai-welcome-mark">✦</div>
    <strong>Bonjour ! Je suis ton assistant Aylox.</strong>
    <p>Je connais l'état de tes tâches et peux t'aider à avancer sur le mod. Pose-moi une question ou utilise les suggestions ci-dessus.</p>
  </div>`;
}
  
</script>
</body>
</html>
