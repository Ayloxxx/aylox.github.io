<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Aylox Furnitures — Mod Tracker</title>
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.min.js"></script>
<style>
:root{--bg:#F5F5F4;--surface:#FFFFFF;--surface2:#F0EFEE;--border:#E2E0DD;--border-strong:#C8C5C1;--text:#111111;--text-sec:#555550;--text-muted:#9A9892;--green:#639922;--green-bg:#EAF3DE;--green-text:#3B6D11;--red:#E24B4A;--red-bg:#FCEBEB;--red-text:#A32D2D;--amber:#EF9F27;--amber-bg:#FAEEDA;--amber-text:#633806;--purple:#7F77DD;--purple-bg:#EEEDFE;--purple-text:#3C3489;--blue:#3B82F6;--blue-bg:#EFF6FF;--blue-text:#1D4ED8;--radius:8px;--radius-lg:12px}
[data-theme="dark"]{--bg:#1A1A18;--surface:#242422;--surface2:#2E2E2B;--border:#3A3A37;--border-strong:#4E4E4A;--text:#F0EFEC;--text-sec:#A8A69F;--text-muted:#68665F;--green-bg:#1A2E0A;--green-text:#97C459;--red-bg:#2E0F0F;--red-text:#F09595;--amber-bg:#2E1E05;--amber-text:#FAC775;--purple-bg:#1E1B3A;--purple-text:#AFA9EC;--blue-bg:#1E2A3A;--blue-text:#93C5FD}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
body{font-family:-apple-system,BlinkMacSystemFont,'Inter','Segoe UI',sans-serif;background:var(--bg);color:var(--text);min-height:100vh;font-size:14px;line-height:1.5;transition:background .2s,color .2s}

/* Layout */
.app{max-width:1100px;margin:0 auto;padding:24px 20px 60px}

/* Header */
.header{display:flex;align-items:center;justify-content:space-between;background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-lg);padding:14px 20px;margin-bottom:16px}
.logo{display:flex;align-items:center;gap:12px}
.logo-icon{width:36px;height:36px;background:var(--green);border-radius:var(--radius);display:flex;align-items:center;justify-content:center;flex-shrink:0}
.logo-icon svg{width:20px;height:20px;stroke:white;fill:none;stroke-width:2}
.logo-name{font-size:15px;font-weight:600}
.logo-sub{font-size:11px;color:var(--text-muted);margin-top:1px}
.header-actions{display:flex;align-items:center;gap:8px}
.sync-dot{width:8px;height:8px;border-radius:50%;background:var(--green);flex-shrink:0;transition:background .3s}
.sync-dot.syncing{background:var(--amber);animation:pulse 1s infinite}
.sync-dot.error{background:var(--red)}
@keyframes pulse{0%,100%{opacity:1}50%{opacity:.4}}
.sync-label{font-size:11px;color:var(--text-muted)}
.btn-icon{width:34px;height:34px;border-radius:var(--radius);border:1px solid var(--border);background:transparent;cursor:pointer;color:var(--text-sec);display:flex;align-items:center;justify-content:center;transition:background .15s}
.btn-icon:hover{background:var(--surface2)}
.btn-icon svg{width:16px;height:16px;stroke:currentColor;fill:none;stroke-width:2}

/* Nav tabs */
.nav-tabs{display:flex;gap:4px;background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-lg);padding:6px;margin-bottom:16px;overflow-x:auto}
.nav-tab{padding:7px 14px;border-radius:var(--radius);border:none;background:transparent;color:var(--text-muted);font-size:13px;font-weight:500;cursor:pointer;white-space:nowrap;transition:background .15s,color .15s;display:flex;align-items:center;gap:6px}
.nav-tab svg{width:14px;height:14px;stroke:currentColor;fill:none;stroke-width:2}
.nav-tab.active{background:var(--surface2);color:var(--text);border:1px solid var(--border)}
.nav-tab:hover:not(.active){background:var(--surface2);color:var(--text-sec)}

/* Tab pages */
.tab-page{display:none}
.tab-page.active{display:block}

/* Stats bar */
.stats-bar{display:flex;align-items:center;gap:12px;background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-lg);padding:12px 20px;margin-bottom:16px}
.progress-wrap{flex:1}
.progress-label{display:flex;justify-content:space-between;margin-bottom:6px}
.progress-label span{font-size:12px;color:var(--text-sec)}
.progress-label strong{font-size:12px;color:var(--green);font-weight:600}
.progress-track{height:6px;background:var(--surface2);border-radius:3px;overflow:hidden}
.progress-fill{height:100%;background:var(--green);border-radius:3px;transition:width .4s ease}
.stat-pill{display:flex;align-items:center;gap:5px;font-size:12px;color:var(--text-muted);white-space:nowrap}
.stat-dot{width:7px;height:7px;border-radius:2px;flex-shrink:0}

/* Toolbar */
.toolbar{display:flex;gap:8px;margin-bottom:20px;flex-wrap:wrap;align-items:center}
.search-wrap{position:relative;flex:1;min-width:180px}
.search-wrap svg{position:absolute;left:10px;top:50%;transform:translateY(-50%);width:15px;height:15px;stroke:var(--text-muted);fill:none;stroke-width:2;pointer-events:none}
.search-input{width:100%;padding:8px 12px 8px 32px;border:1px solid var(--border);border-radius:var(--radius);background:var(--surface);color:var(--text);font-size:13px;outline:none;transition:border-color .15s}
.search-input:focus{border-color:var(--green)}
.search-input::placeholder{color:var(--text-muted)}
.filter-select{padding:8px 10px;border:1px solid var(--border);border-radius:var(--radius);background:var(--surface);color:var(--text);font-size:13px;cursor:pointer;outline:none}
.btn{padding:8px 14px;border-radius:var(--radius);border:1px solid var(--border);background:var(--surface);color:var(--text-sec);font-size:12px;font-weight:500;cursor:pointer;display:flex;align-items:center;gap:6px;transition:background .15s;white-space:nowrap}
.btn:hover{background:var(--surface2)}
.btn svg{width:14px;height:14px;stroke:currentColor;fill:none;stroke-width:2}
.btn-ai{background:var(--purple-bg);color:var(--purple-text);border-color:transparent}
.btn-ai:hover{opacity:.85;background:var(--purple-bg)}
.btn-primary{background:var(--green);color:white;border-color:transparent}
.btn-primary:hover{opacity:.9;background:var(--green)}
.btn-danger{background:var(--red-bg);color:var(--red-text);border-color:transparent}
.btn-danger:hover{opacity:.85}

/* AI Panel */
.ai-panel{background:var(--purple-bg);border:1px solid var(--border);border-radius:var(--radius-lg);padding:14px 16px;margin-bottom:16px;display:none}
.ai-panel.open{display:block}
.ai-panel-head{display:flex;align-items:center;justify-content:space-between;margin-bottom:10px}
.ai-panel-title{font-size:13px;font-weight:500;color:var(--purple-text);display:flex;align-items:center;gap:6px}
.ai-panel-title svg{width:15px;height:15px;stroke:currentColor;fill:none;stroke-width:2}
.ai-tabs{display:flex;gap:6px;margin-bottom:10px}
.ai-tab{padding:5px 12px;border-radius:var(--radius);border:1px solid transparent;background:transparent;color:var(--purple-text);font-size:12px;cursor:pointer;opacity:.6}
.ai-tab.active{background:var(--surface);border-color:var(--border);opacity:1;font-weight:500}
.ai-output{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius);padding:12px 14px;font-size:12px;color:var(--text-sec);min-height:60px;white-space:pre-wrap;line-height:1.7}
.ai-loading{color:var(--text-muted);font-style:italic}

/* Categories grid */
.categories{display:grid;grid-template-columns:repeat(auto-fill,minmax(300px,1fr));gap:14px}
.cat-card{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-lg);overflow:hidden}
.cat-head{padding:11px 14px;border-bottom:1px solid var(--border);display:flex;align-items:center;justify-content:space-between}
.cat-title{font-size:13px;font-weight:600;display:flex;align-items:center;gap:7px}
.cat-title svg{width:14px;height:14px;stroke:var(--text-muted);fill:none;stroke-width:2}
.cat-badge{font-size:11px;padding:2px 8px;border-radius:4px;background:var(--surface2);color:var(--text-muted);border:1px solid var(--border)}
.cat-badge.done{background:var(--green-bg);color:var(--green-text);border-color:transparent}

/* Tasks */
.task-item{border-bottom:1px solid var(--border);border-left:3px solid transparent;transition:background .1s}
.task-item:last-of-type{border-bottom:none}
.task-item[data-prio="haute"]{border-left-color:var(--red)}
.task-item[data-prio="moyenne"]{border-left-color:var(--amber)}
.task-item[data-prio="basse"]{border-left-color:var(--green)}
.task-item:hover{background:var(--surface2)}
.task-item.completed .task-name{text-decoration:line-through;color:var(--text-muted)}
.task-row{padding:10px 14px;display:flex;align-items:flex-start;gap:10px;cursor:pointer}
.task-check{width:17px;height:17px;border-radius:4px;border:1.5px solid var(--border-strong);flex-shrink:0;margin-top:1px;display:flex;align-items:center;justify-content:center;cursor:pointer;transition:background .15s,border-color .15s}
.task-check:hover{border-color:var(--green)}
.task-check.checked{background:var(--green);border-color:var(--green)}
.task-check svg{width:10px;height:10px;fill:none;stroke:white;stroke-width:2.5;display:none;stroke-linecap:round;stroke-linejoin:round}
.task-check.checked svg{display:block}
.task-body{flex:1;min-width:0}
.task-name{font-size:13px;color:var(--text)}
.task-note{font-size:11px;color:var(--text-muted);margin-top:2px}
.task-meta{display:flex;align-items:center;gap:6px;margin-top:4px}
.prio-badge{font-size:10px;padding:1px 6px;border-radius:3px;font-weight:500}
.prio-haute{background:var(--red-bg);color:var(--red-text)}
.prio-moyenne{background:var(--amber-bg);color:var(--amber-text)}
.prio-basse{background:var(--green-bg);color:var(--green-text)}
.task-actions{display:flex;gap:4px;margin-left:auto;flex-shrink:0}
.task-btn{width:26px;height:26px;border-radius:var(--radius);border:none;background:transparent;cursor:pointer;color:var(--text-muted);display:flex;align-items:center;justify-content:center;transition:background .1s}
.task-btn:hover{background:var(--border);color:var(--text)}
.task-btn svg{width:13px;height:13px;stroke:currentColor;fill:none;stroke-width:2}
.task-chevron{color:var(--text-muted);transition:transform .2s;flex-shrink:0;display:flex;align-items:center}
.task-chevron svg{width:13px;height:13px;stroke:currentColor;fill:none;stroke-width:2}
.task-item.expanded .task-chevron{transform:rotate(180deg)}

/* Task description */
.task-desc{display:none;padding:0 14px 12px 41px;font-size:12px;color:var(--text-sec);line-height:1.7}
.task-desc.open{display:block}
.task-desc-text{margin-bottom:8px}
.task-desc-actions{display:flex;gap:6px;flex-wrap:wrap}
.task-desc-btn{padding:4px 10px;border-radius:var(--radius);border:1px solid var(--border);background:var(--surface2);color:var(--text-sec);font-size:11px;cursor:pointer;display:flex;align-items:center;gap:4px;transition:background .1s}
.task-desc-btn:hover{background:var(--border)}
.task-desc-btn svg{width:11px;height:11px;stroke:currentColor;fill:none;stroke-width:2}
.task-desc-btn.ai-desc{background:var(--purple-bg);color:var(--purple-text);border-color:transparent}
.task-desc-btn.ai-desc:hover{opacity:.8}
.ai-inline-out{margin-top:8px;padding:8px 10px;background:var(--surface);border:1px solid var(--border);border-radius:var(--radius);font-size:11px;color:var(--text-sec);line-height:1.7;display:none}
.ai-inline-out.open{display:block}

/* Quick add */
.add-task-row{padding:8px 14px}
.add-task-input{width:100%;padding:7px 10px;border:1px dashed var(--border);border-radius:var(--radius);background:transparent;color:var(--text);font-size:12px;outline:none;transition:border-color .15s}
.add-task-input:focus{border-color:var(--green);border-style:solid}
.add-task-input::placeholder{color:var(--text-muted)}

/* Modal */
.modal-bg{display:none;position:fixed;inset:0;background:rgba(0,0,0,.35);z-index:100;align-items:center;justify-content:center}
.modal-bg.open{display:flex}
.modal{background:var(--surface);border-radius:var(--radius-lg);border:1px solid var(--border);padding:20px;width:100%;max-width:480px;margin:20px;max-height:90vh;overflow-y:auto}
.modal-title{font-size:14px;font-weight:600;margin-bottom:14px}
.form-group{margin-bottom:12px}
.form-label{font-size:11px;color:var(--text-sec);margin-bottom:5px;display:block;font-weight:500}
.form-input,.form-select,.form-textarea{width:100%;padding:8px 10px;border:1px solid var(--border);border-radius:var(--radius);background:var(--surface2);color:var(--text);font-size:13px;outline:none;transition:border-color .15s;font-family:inherit}
.form-input:focus,.form-select:focus,.form-textarea:focus{border-color:var(--green)}
.form-textarea{resize:vertical;min-height:70px}
.form-row{display:flex;gap:8px}
.form-row .form-group{flex:1}
.modal-actions{display:flex;gap:8px;justify-content:flex-end;margin-top:16px}
.btn-cancel{padding:8px 16px;border-radius:var(--radius);border:1px solid var(--border);background:transparent;color:var(--text-sec);font-size:13px;cursor:pointer}
.btn-save{padding:8px 18px;border-radius:var(--radius);border:none;background:var(--green);color:white;font-size:13px;font-weight:500;cursor:pointer}
.ai-gen-btn{margin-top:6px;padding:5px 10px;border-radius:var(--radius);background:var(--purple-bg);color:var(--purple-text);border:none;font-size:11px;cursor:pointer;display:flex;align-items:center;gap:4px}
.ai-gen-btn svg{width:11px;height:11px;stroke:currentColor;fill:none;stroke-width:2}

/* Notes page */
.notes-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(280px,1fr));gap:14px}
.note-card{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-lg);overflow:hidden}
.note-head{padding:11px 14px;border-bottom:1px solid var(--border);display:flex;align-items:center;gap:7px;font-size:13px;font-weight:600}
.note-head svg{width:14px;height:14px;stroke:var(--text-muted);fill:none;stroke-width:2}
.note-textarea{width:100%;padding:12px 14px;border:none;background:transparent;color:var(--text);font-size:12px;line-height:1.7;outline:none;resize:none;min-height:140px;font-family:inherit}
.note-footer{padding:6px 14px;border-top:1px solid var(--border);display:flex;justify-content:flex-end}
.note-save-btn{padding:4px 10px;border-radius:var(--radius);border:none;background:var(--green);color:white;font-size:11px;cursor:pointer}

/* Changelog page */
.changelog-toolbar{display:flex;justify-content:flex-end;margin-bottom:14px}
.version-card{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-lg);margin-bottom:12px;overflow:hidden}
.version-head{padding:12px 16px;border-bottom:1px solid var(--border);display:flex;align-items:center;justify-content:space-between}
.version-tag{font-size:13px;font-weight:700;color:var(--green)}
.version-date{font-size:11px;color:var(--text-muted)}
.version-body{padding:12px 16px}
.version-entry{display:flex;gap:8px;align-items:flex-start;margin-bottom:6px;font-size:12px;color:var(--text-sec)}
.version-entry:last-child{margin-bottom:0}
.entry-dot{width:6px;height:6px;border-radius:50%;background:var(--green);flex-shrink:0;margin-top:5px}
.version-actions{display:flex;gap:6px;padding:8px 16px;border-top:1px solid var(--border)}

/* Bugs page */
.bugs-toolbar{display:flex;justify-content:space-between;align-items:center;margin-bottom:14px;gap:8px;flex-wrap:wrap}
.bug-card{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-lg);padding:14px 16px;margin-bottom:10px;border-left:3px solid var(--red)}
.bug-card.in-progress{border-left-color:var(--amber)}
.bug-card.fixed{border-left-color:var(--green);opacity:.7}
.bug-head{display:flex;align-items:center;justify-content:space-between;margin-bottom:6px}
.bug-title{font-size:13px;font-weight:500}
.bug-status{font-size:10px;padding:2px 8px;border-radius:4px;font-weight:500}
.bug-open{background:var(--red-bg);color:var(--red-text)}
.bug-progress{background:var(--amber-bg);color:var(--amber-text)}
.bug-fixed{background:var(--green-bg);color:var(--green-text)}
.bug-desc{font-size:12px;color:var(--text-sec);line-height:1.6;margin-bottom:8px}
.bug-meta{display:flex;gap:8px;align-items:center}
.bug-version{font-size:11px;color:var(--text-muted)}
.bug-actions{display:flex;gap:6px;margin-left:auto}

/* Roadmap page */
.roadmap-cols{display:grid;grid-template-columns:repeat(auto-fill,minmax(240px,1fr));gap:14px}
.roadmap-col{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-lg);overflow:hidden}
.roadmap-head{padding:11px 14px;border-bottom:1px solid var(--border);display:flex;align-items:center;justify-content:space-between}
.roadmap-title{font-size:13px;font-weight:600;display:flex;align-items:center;gap:6px}
.roadmap-item{padding:9px 14px;border-bottom:1px solid var(--border);font-size:12px;color:var(--text-sec);display:flex;align-items:center;justify-content:space-between;gap:8px}
.roadmap-item:last-of-type{border-bottom:none}
.roadmap-item-name{flex:1}
.roadmap-add{padding:8px 14px}
.roadmap-add-input{width:100%;padding:6px 10px;border:1px dashed var(--border);border-radius:var(--radius);background:transparent;color:var(--text);font-size:12px;outline:none}
.roadmap-add-input:focus{border-color:var(--green);border-style:solid}
.roadmap-add-input::placeholder{color:var(--text-muted)}

/* Stats page */
.stats-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(300px,1fr));gap:14px;margin-bottom:20px}
.stat-card{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-lg);padding:16px}
.stat-card-title{font-size:12px;color:var(--text-muted);margin-bottom:12px;font-weight:500;text-transform:uppercase;letter-spacing:.05em}
.stat-number{font-size:32px;font-weight:700;color:var(--text);line-height:1}
.stat-sub{font-size:12px;color:var(--text-muted);margin-top:4px}
.chart-card{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-lg);padding:16px;margin-bottom:14px}
.chart-title{font-size:13px;font-weight:600;margin-bottom:14px}
.chart-wrap{position:relative;height:220px}

/* Toast */
.toast{position:fixed;bottom:24px;right:24px;background:var(--text);color:var(--surface);padding:10px 16px;border-radius:var(--radius);font-size:13px;z-index:200;opacity:0;transform:translateY(8px);transition:opacity .2s,transform .2s;pointer-events:none}
.toast.show{opacity:1;transform:translateY(0)}

/* Legend */
.legend{display:flex;gap:14px;margin-top:20px;flex-wrap:wrap}
.legend-item{display:flex;align-items:center;gap:5px;font-size:11px;color:var(--text-muted)}
.legend-dot{width:8px;height:8px;border-radius:2px}

/* Empty state */
.empty{text-align:center;padding:32px;color:var(--text-muted);font-size:13px}

@media(max-width:600px){.categories,.notes-grid,.roadmap-cols,.stats-grid{grid-template-columns:1fr}.toolbar,.bugs-toolbar{gap:6px}.stats-bar{flex-wrap:wrap}.nav-tabs{gap:2px}.nav-tab{padding:6px 10px;font-size:12px}}
</style>
</head>
<body>
<div class="app">

  <!-- Header -->
  <div class="header">
    <div class="logo">
      <div class="logo-icon">
        <svg viewBox="0 0 24 24"><path d="M6 11V7a6 6 0 0 1 12 0v4"/><path d="M4 11a2 2 0 0 1 2 2v2h12v-2a2 2 0 0 1 4 0v4a1 1 0 0 1-1 1H3a1 1 0 0 1-1-1v-4a2 2 0 0 1 2-2z"/><line x1="9" y1="19" x2="9" y2="21"/><line x1="15" y1="19" x2="15" y2="21"/></svg>
      </div>
      <div>
        <div class="logo-name">Aylox Furnitures</div>
        <div class="logo-sub">mod tracker — Forge 1.20.1</div>
      </div>
    </div>
    <div class="header-actions">
      <div class="sync-dot" id="syncDot"></div>
      <span class="sync-label" id="syncLabel">Connexion…</span>
      <button class="btn-icon" onclick="exportJSON()" title="Exporter JSON">
        <svg viewBox="0 0 24 24"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="7 10 12 15 17 10"/><line x1="12" y1="15" x2="12" y2="3"/></svg>
      </button>
      <button class="btn-icon" onclick="toggleTheme()" title="Mode sombre">
        <svg id="iconMoon" viewBox="0 0 24 24"><path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"/></svg>
        <svg id="iconSun" viewBox="0 0 24 24" style="display:none"><circle cx="12" cy="12" r="5"/><line x1="12" y1="1" x2="12" y2="3"/><line x1="12" y1="21" x2="12" y2="23"/><line x1="4.22" y1="4.22" x2="5.64" y2="5.64"/><line x1="18.36" y1="18.36" x2="19.78" y2="19.78"/><line x1="1" y1="12" x2="3" y2="12"/><line x1="21" y1="12" x2="23" y2="12"/><line x1="4.22" y1="19.78" x2="5.64" y2="18.36"/><line x1="18.36" y1="5.64" x2="19.78" y2="4.22"/></svg>
      </button>
    </div>
  </div>

  <!-- Nav tabs -->
  <div class="nav-tabs">
    <button class="nav-tab active" onclick="switchTab('tasks',this)">
      <svg viewBox="0 0 24 24"><polyline points="9 11 12 14 22 4"/><path d="M21 12v7a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h11"/></svg>
      Tâches
    </button>
    <button class="nav-tab" onclick="switchTab('notes',this)">
      <svg viewBox="0 0 24 24"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/><line x1="16" y1="13" x2="8" y2="13"/><line x1="16" y1="17" x2="8" y2="17"/><polyline points="10 9 9 9 8 9"/></svg>
      Notes
    </button>
    <button class="nav-tab" onclick="switchTab('changelog',this)">
      <svg viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/></svg>
      Changelog
    </button>
    <button class="nav-tab" onclick="switchTab('bugs',this)">
      <svg viewBox="0 0 24 24"><path d="M8 6l4-4 4 4"/><path d="M14.5 4.5A5 5 0 0 1 17 9v6a5 5 0 0 1-10 0V9a5 5 0 0 1 2.5-4.5"/><line x1="12" y1="10" x2="12" y2="14"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>
      Bugs
    </button>
    <button class="nav-tab" onclick="switchTab('roadmap',this)">
      <svg viewBox="0 0 24 24"><line x1="12" y1="20" x2="12" y2="10"/><line x1="18" y1="20" x2="18" y2="4"/><line x1="6" y1="20" x2="6" y2="16"/></svg>
      Roadmap
    </button>
    <button class="nav-tab" onclick="switchTab('stats',this);renderStats()">
      <svg viewBox="0 0 24 24"><rect x="18" y="3" width="4" height="18"/><rect x="10" y="8" width="4" height="13"/><rect x="2" y="13" width="4" height="8"/></svg>
      Stats
    </button>
  </div>

  <!-- ═══ TAB: TÂCHES ═══ -->
  <div class="tab-page active" id="tab-tasks">
    <div class="stats-bar">
      <div class="progress-wrap">
        <div class="progress-label">
          <span id="progressLabel">Chargement…</span>
          <strong id="progressPct">0%</strong>
        </div>
        <div class="progress-track"><div class="progress-fill" id="progressFill" style="width:0%"></div></div>
      </div>
      <div class="stat-pill"><div class="stat-dot" style="background:var(--red)"></div>Haute</div>
      <div class="stat-pill"><div class="stat-dot" style="background:var(--amber)"></div>Moyenne</div>
      <div class="stat-pill"><div class="stat-dot" style="background:var(--green)"></div>Basse</div>
    </div>
    <div class="toolbar">
      <div class="search-wrap">
        <svg viewBox="0 0 24 24"><circle cx="11" cy="11" r="8"/><line x1="21" y1="21" x2="16.65" y2="16.65"/></svg>
        <input class="search-input" id="searchInput" type="text" placeholder="Rechercher une tâche…" oninput="renderTasks()">
      </div>
      <select class="filter-select" id="filterPrio" onchange="renderTasks()">
        <option value="">Toutes les priorités</option>
        <option value="haute">Haute</option>
        <option value="moyenne">Moyenne</option>
        <option value="basse">Basse</option>
      </select>
      <select class="filter-select" id="filterStatus" onchange="renderTasks()">
        <option value="">Tous les statuts</option>
        <option value="todo">À faire</option>
        <option value="done">Complétées</option>
      </select>
      <button class="btn btn-ai" onclick="toggleAIPanel()">
        <svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg>
        IA
      </button>
      <button class="btn btn-primary" onclick="openAddModal()">
        <svg viewBox="0 0 24 24"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg>
        Nouvelle tâche
      </button>
    </div>
    <div class="ai-panel" id="aiPanel">
      <div class="ai-panel-head">
        <div class="ai-panel-title">
          <svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg>
          Assistant IA
        </div>
        <button class="btn-icon" onclick="toggleAIPanel()">
          <svg viewBox="0 0 24 24"><line x1="18" y1="6" x2="6" y2="18"/><line x1="6" y1="6" x2="18" y2="18"/></svg>
        </button>
      </div>
      <div class="ai-tabs">
        <button class="ai-tab active" onclick="setAITab('suggest',this)">Suggérer des tâches</button>
        <button class="ai-tab" onclick="setAITab('summary',this)">Résumé d'avancement</button>
      </div>
      <div style="margin-bottom:8px">
        <button class="btn btn-ai" onclick="runAI()">
          <svg viewBox="0 0 24 24" style="width:13px;height:13px"><polygon points="5 3 19 12 5 21 5 3"/></svg>
          Générer
        </button>
      </div>
      <div class="ai-output" id="aiOutput"><span class="ai-loading">Clique sur "Générer"…</span></div>
    </div>
    <div class="categories" id="categoriesContainer">
      <div class="empty">Chargement…</div>
    </div>
    <div class="legend">
      <div class="legend-item"><div class="legend-dot" style="background:var(--red)"></div>Priorité haute</div>
      <div class="legend-item"><div class="legend-dot" style="background:var(--amber)"></div>Priorité moyenne</div>
      <div class="legend-item"><div class="legend-dot" style="background:var(--green)"></div>Priorité basse</div>
    </div>
  </div>

  <!-- ═══ TAB: NOTES ═══ -->
  <div class="tab-page" id="tab-notes">
    <div class="notes-grid" id="notesGrid"></div>
  </div>

  <!-- ═══ TAB: CHANGELOG ═══ -->
  <div class="tab-page" id="tab-changelog">
    <div class="changelog-toolbar">
      <button class="btn btn-primary" onclick="openChangelogModal()">
        <svg viewBox="0 0 24 24"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg>
        Nouvelle version
      </button>
    </div>
    <div id="changelogList"><div class="empty">Aucune version encore. Crée ta première !</div></div>
  </div>

  <!-- ═══ TAB: BUGS ═══ -->
  <div class="tab-page" id="tab-bugs">
    <div class="bugs-toolbar">
      <select class="filter-select" id="filterBugStatus" onchange="renderBugs()">
        <option value="">Tous les bugs</option>
        <option value="ouvert">Ouverts</option>
        <option value="en cours">En cours</option>
        <option value="corrigé">Corrigés</option>
      </select>
      <button class="btn btn-primary" onclick="openBugModal()">
        <svg viewBox="0 0 24 24"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg>
        Nouveau bug
      </button>
    </div>
    <div id="bugsList"><div class="empty">Aucun bug recensé. Super !</div></div>
  </div>

  <!-- ═══ TAB: ROADMAP ═══ -->
  <div class="tab-page" id="tab-roadmap">
    <div class="roadmap-cols" id="roadmapCols"></div>
  </div>

  <!-- ═══ TAB: STATS ═══ -->
  <div class="tab-page" id="tab-stats">
    <div class="stats-grid" id="statsGrid"></div>
    <div class="chart-card">
      <div class="chart-title">Avancement par catégorie</div>
      <div class="chart-wrap"><canvas id="chartCat"></canvas></div>
    </div>
    <div class="chart-card">
      <div class="chart-title">Répartition par priorité</div>
      <div class="chart-wrap"><canvas id="chartPrio"></canvas></div>
    </div>
  </div>
</div>

<!-- Modal tâche (ajout + édition) -->
<div class="modal-bg" id="modalBg" onclick="closeModalIfBg(event)">
  <div class="modal">
    <div class="modal-title" id="modalTaskTitle">Nouvelle tâche</div>
    <div class="form-group">
      <label class="form-label" for="newName">Nom de la tâche *</label>
      <input class="form-input" id="newName" placeholder="ex: Créer le modèle 3D de la chaise" oninput="clearError('newName')">
      <div id="newNameErr" style="font-size:11px;color:var(--red);margin-top:4px;display:none">Ce champ est requis.</div>
    </div>
    <div class="form-row">
      <div class="form-group">
        <label class="form-label" for="newCat">Catégorie *</label>
        <select class="form-select" id="newCat"></select>
      </div>
      <div class="form-group">
        <label class="form-label" for="newPrio">Priorité</label>
        <select class="form-select" id="newPrio">
          <option value="haute">Haute</option>
          <option value="moyenne" selected>Moyenne</option>
          <option value="basse">Basse</option>
        </select>
      </div>
    </div>
    <div class="form-group">
      <label class="form-label" for="newNote">Note courte (optionnel)</label>
      <input class="form-input" id="newNote" placeholder="ex: nécessite Blockbench">
    </div>
    <div class="form-group">
      <label class="form-label" for="newDesc">Description détaillée</label>
      <textarea class="form-textarea" id="newDesc" placeholder="Décris la tâche en détail…"></textarea>
      <button class="ai-gen-btn" onclick="aiGenerateDesc()">
        <svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg>
        Générer la description avec l'IA
      </button>
    </div>
    <div class="modal-actions">
      <button class="btn-cancel" onclick="closeModal('modalBg')">Annuler</button>
      <button class="btn-save" id="modalTaskSave" onclick="saveTask()">Ajouter</button>
    </div>
  </div>
</div>

<!-- Modal changelog -->
<div class="modal-bg" id="changelogModalBg" onclick="closeModalIfBgId(event,'changelogModalBg')">
  <div class="modal">
    <div class="modal-title">Nouvelle version</div>
    <div class="form-group">
      <label class="form-label" for="clVersion">Numéro de version *</label>
      <input class="form-input" id="clVersion" placeholder="ex: 1.2.0">
    </div>
    <div class="form-group">
      <label class="form-label" for="clDate">Date</label>
      <input class="form-input" id="clDate" type="date">
    </div>
    <div class="form-group">
      <label class="form-label" for="clChanges">Changements (un par ligne) *</label>
      <textarea class="form-textarea" id="clChanges" placeholder="Ajout de la chaise en bois&#10;Correction du bug d'inventaire&#10;Nouvelles textures" style="min-height:100px"></textarea>
    </div>
    <div class="modal-actions">
      <button class="btn-cancel" onclick="closeModal('changelogModalBg')">Annuler</button>
      <button class="btn-save" onclick="saveChangelog()">Ajouter</button>
    </div>
  </div>
</div>

<!-- Modal bug -->
<div class="modal-bg" id="bugModalBg" onclick="closeModalIfBgId(event,'bugModalBg')">
  <div class="modal">
    <div class="modal-title" id="bugModalTitle">Nouveau bug</div>
    <div class="form-group">
      <label class="form-label" for="bugTitle">Titre du bug *</label>
      <input class="form-input" id="bugTitle" placeholder="ex: La chaise disparaît au rechargement">
    </div>
    <div class="form-group">
      <label class="form-label" for="bugDesc">Description</label>
      <textarea class="form-textarea" id="bugDesc" placeholder="Comment reproduire le bug…"></textarea>
    </div>
    <div class="form-row">
      <div class="form-group">
        <label class="form-label" for="bugStatus">Statut</label>
        <select class="form-select" id="bugStatus">
          <option value="ouvert">Ouvert</option>
          <option value="en cours">En cours</option>
          <option value="corrigé">Corrigé</option>
        </select>
      </div>
      <div class="form-group">
        <label class="form-label" for="bugVersion">Version affectée</label>
        <input class="form-input" id="bugVersion" placeholder="ex: 1.1.0">
      </div>
    </div>
    <div class="modal-actions">
      <button class="btn-cancel" onclick="closeModal('bugModalBg')">Annuler</button>
      <button class="btn-save" id="bugSaveBtn" onclick="saveBug()">Ajouter</button>
    </div>
  </div>
</div>

<div class="toast" id="toast"></div>

<script>
// ═══════════════════════════════════════
// CONFIG
// ═══════════════════════════════════════
const SB_URL = "https://uvewquzymkqxlovwduzs.supabase.co";
const SB_KEY = "sb_publishable__IOYh5ALGwgmKYYYzwWgsA_61FVxDRa";
const AI_PROXY = "https://aylox-ai-proxy.aydindnt7.workers.dev/";

const CATEGORIES = [
  {id:"base",label:"Base / structure",icon:"code"},
  {id:"meubles",label:"Meubles & objets",icon:"sofa"},
  {id:"food",label:"Nourriture & boissons",icon:"burger"},
  {id:"textures",label:"Textures & modèles",icon:"photo"},
  {id:"publi",label:"Publication",icon:"upload"}
];

// ═══════════════════════════════════════
// STATE
// ═══════════════════════════════════════
let tasks = [];
let notes = {};     // { cat_id: "texte" }
let changelogs = [];
let bugs = [];
let roadmap = {};   // { version: ["item1","item2"] }
let expandedTasks = new Set();
let currentAITab = "suggest";
let editingTaskId = null;
let editingBugId = null;
let chartCat = null;
let chartPrio = null;

// ═══════════════════════════════════════
// SUPABASE
// ═══════════════════════════════════════
async function sb(path, opts={}) {
  const res = await fetch(`${SB_URL}/rest/v1/${path}`, {
    ...opts,
    headers: {
      "apikey": SB_KEY,
      "Authorization": `Bearer ${SB_KEY}`,
      "Content-Type": "application/json",
      "Prefer": opts.prefer || "return=representation",
      ...(opts.headers||{})
    }
  });
  if (!res.ok) throw new Error(await res.text());
  const t = await res.text();
  return t ? JSON.parse(t) : null;
}

// ═══════════════════════════════════════
// INIT
// ═══════════════════════════════════════
async function init() {
  setSyncStatus("syncing","Connexion…");
  try {
    await Promise.all([loadTasks(), loadMeta()]);
    setSyncStatus("ok","Synchronisé");
    setInterval(async()=>{ await loadTasks(); }, 15000);
  } catch(e) {
    setSyncStatus("error","Erreur connexion");
    document.getElementById("categoriesContainer").innerHTML = `<div class="empty" style="color:var(--red)">Impossible de se connecter.</div>`;
  }
}

async function loadTasks() {
  const data = await sb("tasks?select=*&order=position.asc,created_at.asc",{prefer:"return=representation"});
  tasks = data || [];
  renderTasks();
  updateProgress();
}

// Notes, changelog, bugs, roadmap stockés dans une table key-value simple
async function loadMeta() {
  try {
    const data = await sb("meta?select=*",{prefer:"return=representation"});
    if (data) {
      data.forEach(row => {
        try {
          if (row.key === "notes") notes = JSON.parse(row.value);
          if (row.key === "changelogs") changelogs = JSON.parse(row.value);
          if (row.key === "bugs") bugs = JSON.parse(row.value);
          if (row.key === "roadmap") roadmap = JSON.parse(row.value);
        } catch {}
      });
    }
    renderNotes();
    renderChangelog();
    renderBugs();
    renderRoadmap();
  } catch(e) {
    // La table meta n'existe peut-être pas encore — on l'ignore
  }
}

async function saveMeta(key, value) {
  try {
    await sb("meta", {
      method: "POST",
      body: JSON.stringify({key, value: JSON.stringify(value)}),
      prefer: "resolution=merge-duplicates,return=minimal",
      headers: {"Prefer": "resolution=merge-duplicates,return=minimal"}
    });
  } catch {}
}

// ═══════════════════════════════════════
// SYNC STATUS
// ═══════════════════════════════════════
function setSyncStatus(state, label) {
  const dot = document.getElementById("syncDot");
  const lbl = document.getElementById("syncLabel");
  dot.className = "sync-dot" + (state==="syncing"?" syncing":state==="error"?" error":"");
  lbl.textContent = label;
}

// ═══════════════════════════════════════
// NAVIGATION ONGLETS
// ═══════════════════════════════════════
function switchTab(name, el) {
  document.querySelectorAll(".tab-page").forEach(p => p.classList.remove("active"));
  document.querySelectorAll(".nav-tab").forEach(t => t.classList.remove("active"));
  document.getElementById("tab-"+name).classList.add("active");
  el.classList.add("active");
}

// ═══════════════════════════════════════
// RENDU TÂCHES
// ═══════════════════════════════════════
const ICONS = {
  code:`<svg viewBox="0 0 24 24"><polyline points="16 18 22 12 16 6"/><polyline points="8 6 2 12 8 18"/></svg>`,
  sofa:`<svg viewBox="0 0 24 24"><path d="M6 11V7a6 6 0 0 1 12 0v4"/><path d="M4 11a2 2 0 0 1 2 2v2h12v-2a2 2 0 0 1 4 0v4a1 1 0 0 1-1 1H3a1 1 0 0 1-1-1v-4a2 2 0 0 1 2-2z"/></svg>`,
  burger:`<svg viewBox="0 0 24 24"><line x1="3" y1="6" x2="21" y2="6"/><path d="M3 11h18a1 1 0 0 1 1 1v3a4 4 0 0 1-4 4H5a4 4 0 0 1-4-4v-3a1 1 0 0 1 1-1z"/><line x1="3" y1="19" x2="21" y2="19"/></svg>`,
  photo:`<svg viewBox="0 0 24 24"><rect x="3" y="3" width="18" height="18" rx="2"/><circle cx="8.5" cy="8.5" r="1.5"/><polyline points="21 15 16 10 5 21"/></svg>`,
  upload:`<svg viewBox="0 0 24 24"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="17 8 12 3 7 8"/><line x1="12" y1="3" x2="12" y2="15"/></svg>`
};

function esc(s){return String(s??"").replace(/&/g,"&amp;").replace(/</g,"&lt;").replace(/>/g,"&gt;").replace(/"/g,"&quot;").replace(/\n/g,"<br>")}

function getFiltered() {
  const q = document.getElementById("searchInput").value.toLowerCase().trim();
  const prio = document.getElementById("filterPrio").value;
  const status = document.getElementById("filterStatus").value;
  return CATEGORIES.map(cat=>({
    ...cat,
    tasks: tasks.filter(t=>{
      if (t.cat_id!==cat.id) return false;
      if (q && !t.name.toLowerCase().includes(q) && !(t.description||"").toLowerCase().includes(q)) return false;
      if (prio && t.prio!==prio) return false;
      if (status==="todo" && t.done) return false;
      if (status==="done" && !t.done) return false;
      return true;
    })
  }));
}

function renderTasks() {
  updateProgress();
  const filtered = getFiltered();
  document.getElementById("categoriesContainer").innerHTML = filtered.map(renderCategory).join("");
}

function updateProgress() {
  const done = tasks.filter(t=>t.done).length;
  const pct = tasks.length ? Math.round((done/tasks.length)*100) : 0;
  document.getElementById("progressLabel").textContent = `${done} / ${tasks.length} tâches complétées`;
  document.getElementById("progressPct").textContent = `${pct}%`;
  document.getElementById("progressFill").style.width = pct+"%";
}

function renderCategory(cat) {
  const done = cat.tasks.filter(t=>t.done).length;
  const total = cat.tasks.length;
  return `
  <div class="cat-card">
    <div class="cat-head">
      <div class="cat-title">${ICONS[cat.icon]||""} ${esc(cat.label)}</div>
      <span class="cat-badge${total>0&&done===total?" done":""}">${done}/${total}</span>
    </div>
    ${cat.tasks.map(renderTask).join("")}
    <div class="add-task-row">
      <input class="add-task-input" placeholder="+ Ajouter une tâche…" onkeydown="quickAdd(event,'${cat.id}',this)">
    </div>
  </div>`;
}

function renderTask(t) {
  const isOpen = expandedTasks.has(t.id);
  return `
  <div class="task-item${t.done?" completed":""}${isOpen?" expanded":""}" data-prio="${t.prio}" id="task-${t.id}">
    <div class="task-row" onclick="toggleDesc('${t.id}')">
      <div class="task-check${t.done?" checked":""}" onclick="event.stopPropagation();toggleDone('${t.id}')">
        <svg viewBox="0 0 12 12"><polyline points="2,6 5,9 10,3"/></svg>
      </div>
      <div class="task-body">
        <div class="task-name">${esc(t.name)}</div>
        ${t.note?`<div class="task-note">${esc(t.note)}</div>`:""}
        <div class="task-meta">
          <span class="prio-badge prio-${t.prio}">${t.prio}</span>
          ${t.description?`<span style="font-size:10px;color:var(--text-muted)">description</span>`:""}
        </div>
      </div>
      <div class="task-actions" onclick="event.stopPropagation()">
        <button class="task-btn" onclick="openEditTaskModal('${t.id}')" title="Modifier">
          <svg viewBox="0 0 24 24"><path d="M11 4H4a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2v-7"/><path d="M18.5 2.5a2.121 2.121 0 0 1 3 3L12 15l-4 1 1-4 9.5-9.5z"/></svg>
        </button>
        <button class="task-btn" onclick="deleteTask('${t.id}')" title="Supprimer">
          <svg viewBox="0 0 24 24"><polyline points="3 6 5 6 21 6"/><path d="M19 6l-1 14H6L5 6"/><path d="M10 11v6"/><path d="M14 11v6"/></svg>
        </button>
      </div>
      <div class="task-chevron">
        <svg viewBox="0 0 24 24"><polyline points="6 9 12 15 18 9"/></svg>
      </div>
    </div>
    <div class="task-desc${isOpen?" open":""}" id="desc-${t.id}">
      <div class="task-desc-text">${t.description?esc(t.description):'<span style="color:var(--text-muted);font-style:italic">Aucune description.</span>'}</div>
      <div class="ai-inline-out" id="aiout-${t.id}"></div>
      <div class="task-desc-actions">
        <button class="task-desc-btn ai-desc" onclick="aiDescTask('${t.id}')">
          <svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg>
          Améliorer avec l'IA
        </button>
      </div>
    </div>
  </div>`;
}

// ═══════════════════════════════════════
// INTERACTIONS TÂCHES
// ═══════════════════════════════════════
async function toggleDone(id) {
  const task = tasks.find(t=>t.id===id);
  if (!task) return;
  task.done = !task.done;
  renderTasks();
  setSyncStatus("syncing","Sauvegarde…");
  try {
    await sb(`tasks?id=eq.${id}`,{method:"PATCH",body:JSON.stringify({done:task.done}),prefer:"return=minimal"});
    setSyncStatus("ok","Synchronisé");
  } catch {
    task.done = !task.done;
    renderTasks();
    setSyncStatus("error","Erreur");
  }
}

function toggleDesc(id) {
  expandedTasks.has(id)?expandedTasks.delete(id):expandedTasks.add(id);
  renderTasks();
}

async function deleteTask(id) {
  if (!confirm("Supprimer cette tâche ?")) return;
  tasks = tasks.filter(t=>t.id!==id);
  expandedTasks.delete(id);
  renderTasks();
  try {
    await sb(`tasks?id=eq.${id}`,{method:"DELETE",prefer:"return=minimal"});
    showToast("Tâche supprimée");
  } catch { await loadTasks(); }
}

async function quickAdd(e, catId, input) {
  if (e.key!=="Enter"||!input.value.trim()) return;
  const name = input.value.trim();
  const id = "t"+Date.now();
  const position = tasks.filter(t=>t.cat_id===catId).length;
  const newTask = {id,cat_id:catId,name,prio:"moyenne",note:"",description:"",done:false,position};
  tasks.push(newTask);
  input.value = "";
  renderTasks();
  try {
    await sb("tasks",{method:"POST",body:JSON.stringify(newTask),prefer:"return=minimal"});
    showToast("Tâche ajoutée !");
  } catch { tasks=tasks.filter(t=>t.id!==id); renderTasks(); }
}

// ═══════════════════════════════════════
// MODAL TÂCHE (AJOUT + ÉDITION)
// ═══════════════════════════════════════
function openAddModal() {
  editingTaskId = null;
  document.getElementById("modalTaskTitle").textContent = "Nouvelle tâche";
  document.getElementById("modalTaskSave").textContent = "Ajouter";
  const sel = document.getElementById("newCat");
  sel.innerHTML = CATEGORIES.map(c=>`<option value="${c.id}">${c.label}</option>`).join("");
  ["newName","newNote","newDesc"].forEach(id=>document.getElementById(id).value="");
  document.getElementById("newPrio").value="moyenne";
  document.getElementById("modalBg").classList.add("open");
}

function openEditTaskModal(id) {
  const task = tasks.find(t=>t.id===id);
  if (!task) return;
  editingTaskId = id;
  document.getElementById("modalTaskTitle").textContent = "Modifier la tâche";
  document.getElementById("modalTaskSave").textContent = "Enregistrer";
  const sel = document.getElementById("newCat");
  sel.innerHTML = CATEGORIES.map(c=>`<option value="${c.id}">${c.label}</option>`).join("");
  document.getElementById("newName").value = task.name;
  document.getElementById("newNote").value = task.note||"";
  document.getElementById("newDesc").value = task.description||"";
  document.getElementById("newPrio").value = task.prio;
  document.getElementById("newCat").value = task.cat_id;
  document.getElementById("modalBg").classList.add("open");
}

async function saveTask() {
  const name = document.getElementById("newName").value.trim();
  if (!name) { document.getElementById("newNameErr").style.display="block"; return; }
  const catId = document.getElementById("newCat").value;
  const prio = document.getElementById("newPrio").value;
  const note = document.getElementById("newNote").value.trim();
  const description = document.getElementById("newDesc").value.trim();

  if (editingTaskId) {
    // Édition
    const task = tasks.find(t=>t.id===editingTaskId);
    if (!task) return;
    Object.assign(task,{name,cat_id:catId,prio,note,description});
    renderTasks();
    closeModal("modalBg");
    setSyncStatus("syncing","Sauvegarde…");
    try {
      await sb(`tasks?id=eq.${editingTaskId}`,{method:"PATCH",body:JSON.stringify({name,cat_id:catId,prio,note,description}),prefer:"return=minimal"});
      setSyncStatus("ok","Synchronisé");
      showToast("Tâche modifiée !");
    } catch { setSyncStatus("error","Erreur"); }
  } else {
    // Ajout
    const id = "t"+Date.now();
    const position = tasks.filter(t=>t.cat_id===catId).length;
    const newTask = {id,cat_id:catId,name,prio,note,description,done:false,position};
    tasks.push(newTask);
    renderTasks();
    closeModal("modalBg");
    try {
      await sb("tasks",{method:"POST",body:JSON.stringify(newTask),prefer:"return=minimal"});
      showToast("Tâche ajoutée !");
    } catch { tasks=tasks.filter(t=>t.id!==id); renderTasks(); }
  }
}

// ═══════════════════════════════════════
// NOTES
// ═══════════════════════════════════════
function renderNotes() {
  document.getElementById("notesGrid").innerHTML = CATEGORIES.map(cat=>`
    <div class="note-card">
      <div class="note-head">${ICONS[cat.icon]||""} ${esc(cat.label)}</div>
      <textarea class="note-textarea" id="note-${cat.id}" placeholder="Tes notes pour cette catégorie…">${esc(notes[cat.id]||"")}</textarea>
      <div class="note-footer">
        <button class="note-save-btn" onclick="saveNote('${cat.id}')">Sauvegarder</button>
      </div>
    </div>`).join("");
}

async function saveNote(catId) {
  const val = document.getElementById("note-"+catId).value;
  notes[catId] = val;
  await saveMeta("notes", notes);
  showToast("Note sauvegardée !");
}

// ═══════════════════════════════════════
// CHANGELOG
// ═══════════════════════════════════════
function openChangelogModal() {
  document.getElementById("clVersion").value="";
  document.getElementById("clDate").value=new Date().toISOString().split("T")[0];
  document.getElementById("clChanges").value="";
  document.getElementById("changelogModalBg").classList.add("open");
}

async function saveChangelog() {
  const version = document.getElementById("clVersion").value.trim();
  const date = document.getElementById("clDate").value;
  const changes = document.getElementById("clChanges").value.trim().split("\n").filter(l=>l.trim());
  if (!version||!changes.length) return;
  changelogs.unshift({id:"cl"+Date.now(),version,date,changes});
  await saveMeta("changelogs",changelogs);
  renderChangelog();
  closeModal("changelogModalBg");
  showToast("Version ajoutée !");
}

function renderChangelog() {
  if (!changelogs.length) {
    document.getElementById("changelogList").innerHTML='<div class="empty">Aucune version encore. Crée ta première !</div>';
    return;
  }
  document.getElementById("changelogList").innerHTML = changelogs.map(cl=>`
    <div class="version-card">
      <div class="version-head">
        <span class="version-tag">v${esc(cl.version)}</span>
        <span class="version-date">${cl.date||""}</span>
      </div>
      <div class="version-body">
        ${cl.changes.map(c=>`<div class="version-entry"><div class="entry-dot"></div><div>${esc(c)}</div></div>`).join("")}
      </div>
      <div class="version-actions">
        <button class="btn btn-danger" onclick="deleteChangelog('${cl.id}')">
          <svg viewBox="0 0 24 24"><polyline points="3 6 5 6 21 6"/><path d="M19 6l-1 14H6L5 6"/></svg>
          Supprimer
        </button>
      </div>
    </div>`).join("");
}

async function deleteChangelog(id) {
  changelogs = changelogs.filter(c=>c.id!==id);
  await saveMeta("changelogs",changelogs);
  renderChangelog();
  showToast("Version supprimée");
}

// ═══════════════════════════════════════
// BUGS
// ═══════════════════════════════════════
function openBugModal(id=null) {
  editingBugId = id;
  const bug = id ? bugs.find(b=>b.id===id) : null;
  document.getElementById("bugModalTitle").textContent = id ? "Modifier le bug" : "Nouveau bug";
  document.getElementById("bugSaveBtn").textContent = id ? "Enregistrer" : "Ajouter";
  document.getElementById("bugTitle").value = bug?.title||"";
  document.getElementById("bugDesc").value = bug?.desc||"";
  document.getElementById("bugStatus").value = bug?.status||"ouvert";
  document.getElementById("bugVersion").value = bug?.version||"";
  document.getElementById("bugModalBg").classList.add("open");
}

async function saveBug() {
  const title = document.getElementById("bugTitle").value.trim();
  if (!title) return;
  const desc = document.getElementById("bugDesc").value.trim();
  const status = document.getElementById("bugStatus").value;
  const version = document.getElementById("bugVersion").value.trim();
  if (editingBugId) {
    const bug = bugs.find(b=>b.id===editingBugId);
    if (bug) Object.assign(bug,{title,desc,status,version});
  } else {
    bugs.unshift({id:"bug"+Date.now(),title,desc,status,version});
  }
  await saveMeta("bugs",bugs);
  renderBugs();
  closeModal("bugModalBg");
  showToast(editingBugId?"Bug modifié !":"Bug ajouté !");
}

function renderBugs() {
  const filter = document.getElementById("filterBugStatus").value;
  const filtered = filter ? bugs.filter(b=>b.status===filter) : bugs;
  if (!filtered.length) {
    document.getElementById("bugsList").innerHTML='<div class="empty">Aucun bug trouvé !</div>';
    return;
  }
  document.getElementById("bugsList").innerHTML = filtered.map(b=>`
    <div class="bug-card ${b.status==="en cours"?"in-progress":b.status==="corrigé"?"fixed":""}">
      <div class="bug-head">
        <div class="bug-title">${esc(b.title)}</div>
        <span class="bug-status ${b.status==="ouvert"?"bug-open":b.status==="en cours"?"bug-progress":"bug-fixed"}">${b.status}</span>
      </div>
      ${b.desc?`<div class="bug-desc">${esc(b.desc)}</div>`:""}
      <div class="bug-meta">
        ${b.version?`<span class="bug-version">v${esc(b.version)}</span>`:""}
        <div class="bug-actions">
          <button class="btn" onclick="openBugModal('${b.id}')">
            <svg viewBox="0 0 24 24"><path d="M11 4H4a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2v-7"/><path d="M18.5 2.5a2.121 2.121 0 0 1 3 3L12 15l-4 1 1-4 9.5-9.5z"/></svg>
            Modifier
          </button>
          <button class="btn btn-danger" onclick="deleteBug('${b.id}')">
            <svg viewBox="0 0 24 24"><polyline points="3 6 5 6 21 6"/><path d="M19 6l-1 14H6L5 6"/></svg>
            Supprimer
          </button>
        </div>
      </div>
    </div>`).join("");
}

async function deleteBug(id) {
  bugs = bugs.filter(b=>b.id!==id);
  await saveMeta("bugs",bugs);
  renderBugs();
  showToast("Bug supprimé");
}

// ═══════════════════════════════════════
// ROADMAP
// ═══════════════════════════════════════
const ROADMAP_VERSIONS = ["V1 (actuelle)","V2","V3","Idées futures"];

function renderRoadmap() {
  document.getElementById("roadmapCols").innerHTML = ROADMAP_VERSIONS.map(v=>{
    const items = roadmap[v]||[];
    return `
    <div class="roadmap-col">
      <div class="roadmap-head">
        <div class="roadmap-title">
          <svg viewBox="0 0 24 24" style="width:14px;height:14px;stroke:var(--green);fill:none;stroke-width:2"><circle cx="12" cy="12" r="10"/></svg>
          ${esc(v)}
        </div>
        <span class="cat-badge">${items.length}</span>
      </div>
      ${items.map((item,i)=>`
        <div class="roadmap-item">
          <span class="roadmap-item-name">${esc(item)}</span>
          <button class="task-btn" onclick="deleteRoadmapItem('${esc(v)}',${i})" title="Supprimer">
            <svg viewBox="0 0 24 24"><line x1="18" y1="6" x2="6" y2="18"/><line x1="6" y1="6" x2="18" y2="18"/></svg>
          </button>
        </div>`).join("")}
      <div class="roadmap-add">
        <input class="roadmap-add-input" placeholder="+ Ajouter une idée…" onkeydown="addRoadmapItem(event,'${esc(v)}',this)">
      </div>
    </div>`;
  }).join("");
}

async function addRoadmapItem(e, version, input) {
  if (e.key!=="Enter"||!input.value.trim()) return;
  if (!roadmap[version]) roadmap[version]=[];
  roadmap[version].push(input.value.trim());
  input.value="";
  await saveMeta("roadmap",roadmap);
  renderRoadmap();
}

async function deleteRoadmapItem(version, index) {
  roadmap[version].splice(index,1);
  await saveMeta("roadmap",roadmap);
  renderRoadmap();
  showToast("Élément supprimé");
}

// ═══════════════════════════════════════
// STATS
// ═══════════════════════════════════════
function renderStats() {
  const done = tasks.filter(t=>t.done).length;
  const total = tasks.length;
  const pct = total?Math.round((done/total)*100):0;
  const haute = tasks.filter(t=>t.prio==="haute"&&!t.done).length;
  const bugs_open = bugs.filter(b=>b.status==="ouvert").length;

  document.getElementById("statsGrid").innerHTML = `
    <div class="stat-card">
      <div class="stat-card-title">Progression globale</div>
      <div class="stat-number">${pct}%</div>
      <div class="stat-sub">${done} / ${total} tâches complétées</div>
    </div>
    <div class="stat-card">
      <div class="stat-card-title">Tâches haute priorité restantes</div>
      <div class="stat-number" style="color:var(--red)">${haute}</div>
      <div class="stat-sub">à traiter en priorité</div>
    </div>
    <div class="stat-card">
      <div class="stat-card-title">Bugs ouverts</div>
      <div class="stat-number" style="color:var(--amber)">${bugs_open}</div>
      <div class="stat-sub">${bugs.length} bugs recensés au total</div>
    </div>
    <div class="stat-card">
      <div class="stat-card-title">Versions publiées</div>
      <div class="stat-number" style="color:var(--green)">${changelogs.length}</div>
      <div class="stat-sub">dans le changelog</div>
    </div>`;

  // Chart par catégorie
  const catLabels = CATEGORIES.map(c=>c.label);
  const catDone = CATEGORIES.map(c=>tasks.filter(t=>t.cat_id===c.id&&t.done).length);
  const catTotal = CATEGORIES.map(c=>tasks.filter(t=>t.cat_id===c.id).length);

  if (chartCat) chartCat.destroy();
  const isDark = document.documentElement.dataset.theme==="dark";
  const textColor = isDark?"#A8A69F":"#555550";
  chartCat = new Chart(document.getElementById("chartCat"),{
    type:"bar",
    data:{
      labels:catLabels,
      datasets:[
        {label:"Complétées",data:catDone,backgroundColor:"#639922",borderRadius:4},
        {label:"Restantes",data:catTotal.map((t,i)=>t-catDone[i]),backgroundColor:isDark?"#3A3A37":"#E2E0DD",borderRadius:4}
      ]
    },
    options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{labels:{color:textColor,font:{size:11}}}},scales:{x:{stacked:true,ticks:{color:textColor,font:{size:11}}},y:{stacked:true,ticks:{color:textColor,font:{size:11}}}}}
  });

  // Chart par priorité
  const hd=tasks.filter(t=>t.prio==="haute"&&t.done).length;
  const ht=tasks.filter(t=>t.prio==="haute").length;
  const md=tasks.filter(t=>t.prio==="moyenne"&&t.done).length;
  const mt=tasks.filter(t=>t.prio==="moyenne").length;
  const ld=tasks.filter(t=>t.prio==="basse"&&t.done).length;
  const lt=tasks.filter(t=>t.prio==="basse").length;

  if (chartPrio) chartPrio.destroy();
  chartPrio = new Chart(document.getElementById("chartPrio"),{
    type:"bar",
    data:{
      labels:["Haute","Moyenne","Basse"],
      datasets:[
        {label:"Complétées",data:[hd,md,ld],backgroundColor:["#E24B4A","#EF9F27","#639922"],borderRadius:4},
        {label:"Restantes",data:[ht-hd,mt-md,lt-ld],backgroundColor:isDark?"#3A3A37":"#E2E0DD",borderRadius:4}
      ]
    },
    options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{labels:{color:textColor,font:{size:11}}}},scales:{x:{stacked:true,ticks:{color:textColor,font:{size:11}}},y:{stacked:true,ticks:{color:textColor,font:{size:11}}}}}
  });
}

// ═══════════════════════════════════════
// MODALS HELPERS
// ═══════════════════════════════════════
function closeModal(id) { document.getElementById(id).classList.remove("open"); }
function closeModalIfBg(e) { if(e.target===document.getElementById("modalBg")) closeModal("modalBg"); }
function closeModalIfBgId(e,id) { if(e.target===document.getElementById(id)) closeModal(id); }
function clearError(id) { document.getElementById(id+"Err").style.display="none"; }

// ═══════════════════════════════════════
// EXPORT
// ═══════════════════════════════════════
function exportJSON() {
  const json = JSON.stringify({categories:CATEGORIES,tasks,notes,changelogs,bugs,roadmap},null,2);
  const a = document.createElement("a");
  a.href = URL.createObjectURL(new Blob([json],{type:"application/json"}));
  a.download = "aylox-tracker.json";
  a.click();
  showToast("Export téléchargé !");
}

// ═══════════════════════════════════════
// AI
// ═══════════════════════════════════════
function toggleAIPanel() { document.getElementById("aiPanel").classList.toggle("open"); }
function setAITab(tab,el) {
  currentAITab=tab;
  document.querySelectorAll(".ai-tab").forEach(t=>t.classList.remove("active"));
  el.classList.add("active");
}

async function callAI(prompt) {
  const res = await fetch(AI_PROXY,{method:"POST",headers:{"Content-Type":"application/json"},body:JSON.stringify({prompt})});
  const json = await res.json();
  return json.text||"Pas de réponse.";
}

async function runAI() {
  const out = document.getElementById("aiOutput");
  out.innerHTML='<span class="ai-loading">L\'IA réfléchit…</span>';
  const summary = CATEGORIES.map(cat=>{
    const catTasks=tasks.filter(t=>t.cat_id===cat.id);
    const done=catTasks.filter(t=>t.done).length;
    return `### ${cat.label} (${done}/${catTasks.length})\n${catTasks.map(t=>`  - [${t.done?"x":" "}] ${t.name} (${t.prio})`).join("\n")}`;
  }).join("\n\n");
  const prompt = currentAITab==="suggest"
    ? `Mod Minecraft "Aylox Furnitures" (Forge 1.20.1). Tâches actuelles:\n${summary}\n\nPropose 5 nouvelles tâches pertinentes. Format: nom, catégorie, priorité, description courte.`
    : `Mod Minecraft "Aylox Furnitures". État:\n${summary}\n\nFais un résumé d'avancement: ce qui est fait, priorités restantes, 2-3 conseils. Sois concis et encourageant.`;
  try { out.textContent = await callAI(prompt); }
  catch { out.textContent="Erreur IA. Réessaie."; }
}

async function aiGenerateDesc() {
  const name = document.getElementById("newName").value.trim();
  if (!name) { document.getElementById("newNameErr").style.display="block"; return; }
  const descEl = document.getElementById("newDesc");
  descEl.value="L'IA génère…"; descEl.disabled=true;
  try { descEl.value = await callAI(`Pour le mod Minecraft "Aylox Furnitures" (Forge 1.20.1), génère une description technique courte (3-4 phrases) pour cette tâche: "${name}". Direct, sans intro.`); }
  catch { descEl.value=""; }
  descEl.disabled=false;
}

async function aiDescTask(id) {
  const task = tasks.find(t=>t.id===id);
  if (!task) return;
  const aiOut = document.getElementById("aiout-"+id);
  aiOut.className="ai-inline-out open";
  aiOut.textContent="L'IA améliore la description…";
  try {
    const text = await callAI(`Pour le mod "Aylox Furnitures" (Forge 1.20.1), améliore cette description.\nTâche: "${task.name}"\nActuelle: "${task.description||"aucune"}"\n3-5 phrases, direct, sans intro.`);
    aiOut.dataset.text=text;
    aiOut.innerHTML=`<strong style="color:var(--purple-text);font-size:11px">Suggestion IA :</strong><br><br>${esc(text)}<br><br><button class="task-desc-btn" onclick="applyAIDesc('${id}')">Appliquer</button>`;
  } catch { aiOut.textContent="Erreur IA. Réessaie."; }
}

async function applyAIDesc(id) {
  const text = document.getElementById("aiout-"+id).dataset.text;
  const task = tasks.find(t=>t.id===id);
  if (!task||!text) return;
  task.description=text;
  renderTasks();
  try {
    await sb(`tasks?id=eq.${id}`,{method:"PATCH",body:JSON.stringify({description:text}),prefer:"return=minimal"});
    showToast("Description mise à jour !");
  } catch { setSyncStatus("error","Erreur"); }
}

// ═══════════════════════════════════════
// THÈME
// ═══════════════════════════════════════
function toggleTheme() {
  applyTheme(document.documentElement.dataset.theme==="dark"?"light":"dark");
}
function applyTheme(mode) {
  document.documentElement.dataset.theme=mode==="dark"?"dark":"";
  localStorage.setItem("aylox_theme",mode);
  document.getElementById("iconMoon").style.display=mode==="dark"?"none":"block";
  document.getElementById("iconSun").style.display=mode==="dark"?"block":"none";
}

// ═══════════════════════════════════════
// TOAST
// ═══════════════════════════════════════
let toastTimer;
function showToast(msg) {
  const t=document.getElementById("toast");
  t.textContent=msg; t.classList.add("show");
  clearTimeout(toastTimer);
  toastTimer=setTimeout(()=>t.classList.remove("show"),2500);
}

// ═══════════════════════════════════════
// INIT
// ═══════════════════════════════════════
const saved=localStorage.getItem("aylox_theme");
if(saved==="dark") applyTheme("dark");
init();
</script>
</body>
</html>
