
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Aylox Furnitures — Mod Tracker</title>
<style>
  :root {
    --bg:#F5F5F4;--surface:#FFFFFF;--surface2:#F0EFEE;--border:#E2E0DD;
    --border-strong:#C8C5C1;--text:#111111;--text-sec:#555550;--text-muted:#9A9892;
    --green:#639922;--green-bg:#EAF3DE;--green-text:#3B6D11;
    --red:#E24B4A;--red-bg:#FCEBEB;--red-text:#A32D2D;
    --amber:#EF9F27;--amber-bg:#FAEEDA;--amber-text:#633806;
    --purple:#7F77DD;--purple-bg:#EEEDFE;--purple-text:#3C3489;
    --radius:8px;--radius-lg:12px;
  }
  [data-theme="dark"]{
    --bg:#1A1A18;--surface:#242422;--surface2:#2E2E2B;--border:#3A3A37;
    --border-strong:#4E4E4A;--text:#F0EFEC;--text-sec:#A8A69F;--text-muted:#68665F;
    --green-bg:#1A2E0A;--green-text:#97C459;--red-bg:#2E0F0F;--red-text:#F09595;
    --amber-bg:#2E1E05;--amber-text:#FAC775;--purple-bg:#1E1B3A;--purple-text:#AFA9EC;
  }
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

  /* Stats */
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

  /* Categories */
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
  .task-chevron{margin-left:auto;color:var(--text-muted);transition:transform .2s;flex-shrink:0}
  .task-chevron svg{width:13px;height:13px;stroke:currentColor;fill:none;stroke-width:2}
  .task-item.expanded .task-chevron{transform:rotate(180deg)}

  /* Description expandable */
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
  .modal{background:var(--surface);border-radius:var(--radius-lg);border:1px solid var(--border);padding:20px;width:100%;max-width:440px;margin:20px}
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

  /* Toast */
  .toast{position:fixed;bottom:24px;right:24px;background:var(--text);color:var(--surface);padding:10px 16px;border-radius:var(--radius);font-size:13px;z-index:200;opacity:0;transform:translateY(8px);transition:opacity .2s,transform .2s;pointer-events:none}
  .toast.show{opacity:1;transform:translateY(0)}

  /* Legend */
  .legend{display:flex;gap:14px;margin-top:20px;flex-wrap:wrap}
  .legend-item{display:flex;align-items:center;gap:5px;font-size:11px;color:var(--text-muted)}
  .legend-dot{width:8px;height:8px;border-radius:2px}

  /* Loader */
  .loader{text-align:center;padding:40px;color:var(--text-muted);font-size:13px}

  @media(max-width:600px){.categories{grid-template-columns:1fr}.toolbar{gap:6px}.stats-bar{flex-wrap:wrap}}
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
      <button class="btn-icon" id="themeBtn" onclick="toggleTheme()" title="Mode sombre">
        <svg id="iconMoon" viewBox="0 0 24 24"><path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"/></svg>
        <svg id="iconSun" viewBox="0 0 24 24" style="display:none"><circle cx="12" cy="12" r="5"/><line x1="12" y1="1" x2="12" y2="3"/><line x1="12" y1="21" x2="12" y2="23"/><line x1="4.22" y1="4.22" x2="5.64" y2="5.64"/><line x1="18.36" y1="18.36" x2="19.78" y2="19.78"/><line x1="1" y1="12" x2="3" y2="12"/><line x1="21" y1="12" x2="23" y2="12"/><line x1="4.22" y1="19.78" x2="5.64" y2="18.36"/><line x1="18.36" y1="5.64" x2="19.78" y2="4.22"/></svg>
      </button>
    </div>
  </div>

  <!-- Stats -->
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

  <!-- Toolbar -->
  <div class="toolbar">
    <div class="search-wrap">
      <svg viewBox="0 0 24 24"><circle cx="11" cy="11" r="8"/><line x1="21" y1="21" x2="16.65" y2="16.65"/></svg>
      <input class="search-input" id="searchInput" type="text" placeholder="Rechercher une tâche…" oninput="renderAll()">
    </div>
    <select class="filter-select" id="filterPrio" onchange="renderAll()">
      <option value="">Toutes les priorités</option>
      <option value="haute">Haute</option>
      <option value="moyenne">Moyenne</option>
      <option value="basse">Basse</option>
    </select>
    <select class="filter-select" id="filterStatus" onchange="renderAll()">
      <option value="">Tous les statuts</option>
      <option value="todo">À faire</option>
      <option value="done">Complétées</option>
    </select>
    <button class="btn btn-ai" onclick="toggleAIPanel()">
      <svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg>
      IA Claude
    </button>
    <button class="btn btn-primary" onclick="openAddModal()">
      <svg viewBox="0 0 24 24"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg>
      Nouvelle tâche
    </button>
  </div>

  <!-- AI Panel -->
  <div class="ai-panel" id="aiPanel">
    <div class="ai-panel-head">
      <div class="ai-panel-title">
        <svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg>
        Assistant Claude
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
    <div class="ai-output" id="aiOutput"><span class="ai-loading">Clique sur "Générer" pour lancer l'IA…</span></div>
  </div>

  <!-- Categories -->
  <div class="categories" id="categoriesContainer">
    <div class="loader">Chargement des tâches…</div>
  </div>

  <div class="legend">
    <div class="legend-item"><div class="legend-dot" style="background:var(--red)"></div>Priorité haute</div>
    <div class="legend-item"><div class="legend-dot" style="background:var(--amber)"></div>Priorité moyenne</div>
    <div class="legend-item"><div class="legend-dot" style="background:var(--green)"></div>Priorité basse</div>
  </div>
</div>

<!-- Modal -->
<div class="modal-bg" id="modalBg" onclick="closeModalIfBg(event)">
  <div class="modal">
    <div class="modal-title">Nouvelle tâche</div>
    <div class="form-group">
      <label class="form-label">Nom de la tâche *</label>
      <input class="form-input" id="newName" placeholder="ex: Créer le modèle 3D de la chaise" oninput="clearError('newName')">
      <div id="newNameErr" style="font-size:11px;color:var(--red);margin-top:4px;display:none">Ce champ est requis.</div>
    </div>
    <div class="form-row">
      <div class="form-group">
        <label class="form-label">Catégorie *</label>
        <select class="form-select" id="newCat"></select>
      </div>
      <div class="form-group">
        <label class="form-label">Priorité</label>
        <select class="form-select" id="newPrio">
          <option value="haute">Haute</option>
          <option value="moyenne" selected>Moyenne</option>
          <option value="basse">Basse</option>
        </select>
      </div>
    </div>
    <div class="form-group">
      <label class="form-label">Note courte (optionnel)</label>
      <input class="form-input" id="newNote" placeholder="ex: nécessite Blockbench">
    </div>
    <div class="form-group">
      <label class="form-label">Description détaillée</label>
      <textarea class="form-textarea" id="newDesc" placeholder="Décris la tâche en détail…"></textarea>
      <button class="ai-gen-btn" onclick="aiGenerateDesc()">
        <svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg>
        Générer la description avec l'IA
      </button>
    </div>
    <div class="modal-actions">
      <button class="btn-cancel" onclick="closeModal()">Annuler</button>
      <button class="btn-save" onclick="saveTask()">Ajouter</button>
    </div>
  </div>
</div>

<div class="toast" id="toast"></div>

<script>
// ═══════════════════════════════════════
// CONFIG SUPABASE
// ═══════════════════════════════════════
const SB_URL = "https://uvewquzymkqxlovwduzs.supabase.co";
const SB_KEY = "sb_publishable__IOYh5ALGwgmKYYYzwWgsA_61FVxDRa";

// Helper fetch Supabase REST
async function sb(path, opts = {}) {
  const url = `${SB_URL}/rest/v1/${path}`;
  const res = await fetch(url, {
    ...opts,
    headers: {
      "apikey": SB_KEY,
      "Authorization": `Bearer ${SB_KEY}`,
      "Content-Type": "application/json",
      "Prefer": opts.prefer || "return=representation",
      ...(opts.headers || {})
    }
  });
  if (!res.ok) {
    const err = await res.text();
    throw new Error(err);
  }
  const text = await res.text();
  return text ? JSON.parse(text) : null;
}

// ═══════════════════════════════════════
// CATÉGORIES (config locale fixe)
// ═══════════════════════════════════════
const CATEGORIES = [
  { id:"base",     label:"Base / structure",      icon:"code"   },
  { id:"meubles",  label:"Meubles & objets",       icon:"sofa"   },
  { id:"food",     label:"Nourriture & boissons",  icon:"burger" },
  { id:"textures", label:"Textures & modèles",     icon:"photo"  },
  { id:"publi",    label:"Publication",            icon:"upload" }
];

const DEFAULT_TASKS = [
  {id:"b1",cat_id:"base",    name:"Enregistrement de tous les blocs",      prio:"haute",   note:"",                      description:"S'assurer que chaque meuble/objet est bien déclaré dans le registre Forge (BlockRegistry, ItemRegistry). Vérifier l'absence de conflits d'ID.",done:false,position:0},
  {id:"b2",cat_id:"base",    name:"Recettes de craft JSON",                prio:"haute",   note:"crafting + furnace",    description:"Créer et vérifier toutes les recettes JSON pour chaque item — crafting table et furnace. Chaque recette dans data/<modid>/recipes/.",done:false,position:1},
  {id:"b3",cat_id:"base",    name:"Tags Forge (blocs / items)",            prio:"moyenne", note:"",                      description:"Ajouter les tags appropriés (forge:furniture, etc.) pour la compatibilité avec d'autres mods. Dossiers data/forge/tags/.",done:false,position:2},
  {id:"b4",cat_id:"base",    name:"Groupe créatif personnalisé",           prio:"moyenne", note:"",                      description:"Créer un onglet créatif dédié 'Aylox Furnitures' avec icône dans le menu inventaire créatif.",done:false,position:3},
  {id:"b5",cat_id:"base",    name:"Support client & serveur",              prio:"basse",   note:"",                      description:"Vérifier que le mod fonctionne en environnement serveur (synchronisation blocs, NBT, pas de code client-only côté serveur).",done:false,position:4},
  {id:"m1",cat_id:"meubles", name:"Poubelle (trash bin)",                  prio:"haute",   note:"décoratif ou interactif ?", description:"Bloc décoratif de base pour la V1. Définir si interaction possible (ouvrir un inventaire pour 'jeter' des items) ou purement cosmétique.",done:false,position:0},
  {id:"m2",cat_id:"meubles", name:"Caisse enregistreuse (cash register)",  prio:"haute",   note:"",                      description:"Objet de déco pour shops/restaurants. Animation d'ouverture au clic ? Son au clic ? À définir pour la V1.",done:false,position:1},
  {id:"m3",cat_id:"meubles", name:"Ordinateur (computer)",                 prio:"haute",   note:"GUI possible ?",        description:"Bloc décoratif ou interactif avec GUI texte. Pour la V1 on peut partir sur purement décoratif et prévoir l'interaction en V2.",done:false,position:2},
  {id:"m4",cat_id:"meubles", name:"Chaises & sièges",                      prio:"moyenne", note:"",                      description:"Meubles de base pour maisons/restaurants. La mécanique 's'asseoir' nécessite une entité ArmorStand invisible — à prévoir ou reporter en V2.",done:false,position:3},
  {id:"m5",cat_id:"meubles", name:"Tables (basse, haute, bureau)",         prio:"moyenne", note:"variantes de bois ?",   description:"Différentes variantes de tables adaptées aux contextes. Utiliser des blockstates pour les variantes de matériaux (oak, spruce, dark_oak…).",done:false,position:4},
  {id:"m6",cat_id:"meubles", name:"Étagères & rangements",                 prio:"basse",   note:"",                      description:"Éléments muraux décoratifs pour bibliothèques, maisons, bureaux. Modèle custom avec face_attaching blockstate.",done:false,position:5},
  {id:"f1",cat_id:"food",    name:"Items nourriture (burger, etc.)",       prio:"haute",   note:"",                      description:"Enregistrement des food items avec valeurs de saturation/faim dans FoodProperties. Chaque item a son modèle JSON et sa texture 16×16.",done:false,position:0},
  {id:"f2",cat_id:"food",    name:"Boissons (drinks)",                     prio:"haute",   note:"effets de potion ?",    description:"Items buvables. Peut hériter de PotionItem ou Item custom avec use_animation DRINK. Effets de potion optionnels.",done:false,position:1},
  {id:"f3",cat_id:"food",    name:"Recettes crafting nourriture",          prio:"moyenne", note:"",                      description:"JSON de craft pour chaque food item. Certains items peuvent nécessiter une recette furnace/smoker (cuisson).",done:false,position:2},
  {id:"f4",cat_id:"food",    name:"Blocs déco nourriture (plateau, etc.)", prio:"basse",   note:"",                      description:"Versions blocs posables de la nourriture pour décorer comptoirs et tables de restaurant. Modèle custom flat ou 3D.",done:false,position:3},
  {id:"t1",cat_id:"textures",name:"Modèles 3D (blockstates + JSON)",       prio:"haute",   note:"Blockbench recommandé", description:"Fichiers model JSON pour chaque bloc (toutes orientations/variantes via blockstates). Exporter depuis Blockbench en format Java Edition.",done:false,position:0},
  {id:"t2",cat_id:"textures",name:"Textures PNG tous items",               prio:"haute",   note:"16×16 ou 32×32",       description:"Sprites cohérents avec le style Minecraft vanilla. Dossier assets/<modid>/textures/block/ et /item/.",done:false,position:1},
  {id:"t3",cat_id:"textures",name:"Icônes inventaire",                     prio:"moyenne", note:"",                      description:"Textures spécifiques pour l'affichage en main et dans l'inventaire (item model). Fichier assets/<modid>/models/item/<item>.json.",done:false,position:2},
  {id:"t4",cat_id:"textures",name:"Fichiers lang (en_us, fr_fr)",          prio:"basse",   note:"",                      description:"Fichiers JSON de traduction pour les noms de blocs/items en anglais (en_us.json obligatoire) et français (fr_fr.json en bonus).",done:false,position:3},
  {id:"p1",cat_id:"publi",   name:"Page CurseForge — description complète",prio:"moyenne", note:"118 DL actuels",        description:"Rédiger une description détaillée avec screenshots, liste des features, changelogs structurés. Ajouter des images in-game dans la galerie.",done:false,position:0},
  {id:"p2",cat_id:"publi",   name:"Page Modrinth — modération en cours",   prio:"moyenne", note:"en attente d'approbation", description:"Suivre l'approbation de la modération Modrinth. Une fois validé, compléter les métadonnées : tags, screenshots, description, liens.",done:false,position:1},
  {id:"p3",cat_id:"publi",   name:"Screenshots & galerie",                 prio:"basse",   note:"",                      description:"Captures in-game de qualité (F1 pour masquer le HUD) dans différents builds : maison, restaurant, bureau.",done:false,position:2},
  {id:"p4",cat_id:"publi",   name:"Discord — recueillir les retours",      prio:"basse",   note:"discord.gg/AeajWdB4wF", description:"Animer le Discord déjà lié sur CurseForge. Créer un canal #suggestions et #bug-report pour la communauté.",done:false,position:3}
];

// ═══════════════════════════════════════
// STATE
// ═══════════════════════════════════════
let tasks = [];           // toutes les tâches chargées depuis Supabase
let expandedTasks = new Set();
let currentAITab = "suggest";
let pollInterval = null;

// ═══════════════════════════════════════
// SYNC STATUS
// ═══════════════════════════════════════
function setSyncStatus(state, label) {
  const dot = document.getElementById("syncDot");
  const lbl = document.getElementById("syncLabel");
  dot.className = "sync-dot" + (state === "syncing" ? " syncing" : state === "error" ? " error" : "");
  lbl.textContent = label;
}

// ═══════════════════════════════════════
// INIT — charger ou seeder les données
// ═══════════════════════════════════════
async function init() {
  setSyncStatus("syncing", "Connexion…");
  try {
    const existing = await sb("tasks?select=id&limit=1", { prefer: "return=representation" });
    if (!existing || existing.length === 0) {
      // Première fois : insérer les tâches par défaut
      setSyncStatus("syncing", "Premier lancement…");
      await sb("tasks", {
        method: "POST",
        body: JSON.stringify(DEFAULT_TASKS),
        prefer: "return=minimal"
      });
    }
    await loadTasks();
    setSyncStatus("ok", "Synchronisé");
    // Polling toutes les 10s pour détecter les changements des autres utilisateurs
    pollInterval = setInterval(async () => {
      await loadTasks();
    }, 10000);
  } catch(e) {
    setSyncStatus("error", "Erreur de connexion");
    document.getElementById("categoriesContainer").innerHTML =
      `<div class="loader" style="color:var(--red)">Impossible de se connecter à la base de données.<br>Vérifie ta connexion internet.</div>`;
  }
}

async function loadTasks() {
  try {
    const data = await sb("tasks?select=*&order=position.asc,created_at.asc", { prefer: "return=representation" });
    tasks = data || [];
    renderAll();
    setSyncStatus("ok", "Synchronisé");
  } catch(e) {
    setSyncStatus("error", "Erreur sync");
  }
}

// ═══════════════════════════════════════
// RENDU
// ═══════════════════════════════════════
const ICONS = {
  code:   `<svg viewBox="0 0 24 24"><polyline points="16 18 22 12 16 6"/><polyline points="8 6 2 12 8 18"/></svg>`,
  sofa:   `<svg viewBox="0 0 24 24"><path d="M6 11V7a6 6 0 0 1 12 0v4"/><path d="M4 11a2 2 0 0 1 2 2v2h12v-2a2 2 0 0 1 4 0v4a1 1 0 0 1-1 1H3a1 1 0 0 1-1-1v-4a2 2 0 0 1 2-2z"/></svg>`,
  burger: `<svg viewBox="0 0 24 24"><line x1="3" y1="6" x2="21" y2="6"/><path d="M3 11h18a1 1 0 0 1 1 1v3a4 4 0 0 1-4 4H5a4 4 0 0 1-4-4v-3a1 1 0 0 1 1-1z"/><line x1="3" y1="19" x2="21" y2="19"/></svg>`,
  photo:  `<svg viewBox="0 0 24 24"><rect x="3" y="3" width="18" height="18" rx="2"/><circle cx="8.5" cy="8.5" r="1.5"/><polyline points="21 15 16 10 5 21"/></svg>`,
  upload: `<svg viewBox="0 0 24 24"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="17 8 12 3 7 8"/><line x1="12" y1="3" x2="12" y2="15"/></svg>`
};

function esc(s) {
  return String(s ?? "")
    .replace(/&/g,"&amp;").replace(/</g,"&lt;").replace(/>/g,"&gt;")
    .replace(/"/g,"&quot;").replace(/\n/g,"<br>");
}

function getFiltered() {
  const q = document.getElementById("searchInput").value.toLowerCase().trim();
  const prio = document.getElementById("filterPrio").value;
  const status = document.getElementById("filterStatus").value;
  return CATEGORIES.map(cat => ({
    ...cat,
    tasks: tasks.filter(t => {
      if (t.cat_id !== cat.id) return false;
      if (q && !t.name.toLowerCase().includes(q) && !(t.description||"").toLowerCase().includes(q)) return false;
      if (prio && t.prio !== prio) return false;
      if (status === "todo" && t.done) return false;
      if (status === "done" && !t.done) return false;
      return true;
    })
  }));
}

function renderAll() {
  updateProgress();
  renderCategories();
}

function updateProgress() {
  const all = tasks;
  const done = all.filter(t => t.done).length;
  const pct = all.length ? Math.round((done / all.length) * 100) : 0;
  document.getElementById("progressLabel").textContent = `${done} / ${all.length} tâches complétées`;
  document.getElementById("progressPct").textContent = `${pct}%`;
  document.getElementById("progressFill").style.width = pct + "%";
}

function renderCategories() {
  const filtered = getFiltered();
  document.getElementById("categoriesContainer").innerHTML = filtered.map(renderCategory).join("");
}

function renderCategory(cat) {
  const done = cat.tasks.filter(t => t.done).length;
  const total = cat.tasks.length;
  const allDone = total > 0 && done === total;
  return `
  <div class="cat-card">
    <div class="cat-head">
      <div class="cat-title">${ICONS[cat.icon]||""} ${esc(cat.label)}</div>
      <span class="cat-badge${allDone?" done":""}">${done}/${total}</span>
    </div>
    ${cat.tasks.map(renderTask).join("")}
    <div class="add-task-row">
      <input class="add-task-input" placeholder="+ Ajouter rapidement une tâche…"
        onkeydown="quickAdd(event,'${cat.id}',this)">
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
        <button class="task-desc-btn" onclick="deleteTask('${t.id}')">
          <svg viewBox="0 0 24 24"><polyline points="3 6 5 6 21 6"/><path d="M19 6l-1 14H6L5 6"/><path d="M10 11v6"/><path d="M14 11v6"/><path d="M9 6V4h6v2"/></svg>
          Supprimer
        </button>
      </div>
    </div>
  </div>`;
}

// ═══════════════════════════════════════
// INTERACTIONS
// ═══════════════════════════════════════
async function toggleDone(id) {
  const task = tasks.find(t => t.id === id);
  if (!task) return;
  const newDone = !task.done;
  task.done = newDone; // optimistic update
  renderAll();
  setSyncStatus("syncing", "Sauvegarde…");
  try {
    await sb(`tasks?id=eq.${id}`, {
      method: "PATCH",
      body: JSON.stringify({ done: newDone }),
      prefer: "return=minimal"
    });
    setSyncStatus("ok", "Synchronisé");
  } catch {
    task.done = !newDone; // rollback
    renderAll();
    setSyncStatus("error", "Erreur de sauvegarde");
  }
}

function toggleDesc(id) {
  if (expandedTasks.has(id)) expandedTasks.delete(id);
  else expandedTasks.add(id);
  renderAll();
}

async function deleteTask(id) {
  if (!confirm("Supprimer cette tâche ?")) return;
  tasks = tasks.filter(t => t.id !== id);
  expandedTasks.delete(id);
  renderAll();
  setSyncStatus("syncing", "Suppression…");
  try {
    await sb(`tasks?id=eq.${id}`, { method: "DELETE", prefer: "return=minimal" });
    setSyncStatus("ok", "Synchronisé");
    showToast("Tâche supprimée");
  } catch {
    setSyncStatus("error", "Erreur suppression");
    await loadTasks();
  }
}

async function quickAdd(e, catId, input) {
  if (e.key !== "Enter" || !input.value.trim()) return;
  const name = input.value.trim();
  const id = "t" + Date.now();
  const catTasks = tasks.filter(t => t.cat_id === catId);
  const position = catTasks.length;
  const newTask = { id, cat_id: catId, name, prio: "moyenne", note: "", description: "", done: false, position };
  tasks.push(newTask);
  input.value = "";
  renderAll();
  setSyncStatus("syncing", "Sauvegarde…");
  try {
    await sb("tasks", { method: "POST", body: JSON.stringify(newTask), prefer: "return=minimal" });
    setSyncStatus("ok", "Synchronisé");
    showToast("Tâche ajoutée !");
  } catch {
    tasks = tasks.filter(t => t.id !== id);
    renderAll();
    setSyncStatus("error", "Erreur ajout");
  }
}

// ═══════════════════════════════════════
// MODAL
// ═══════════════════════════════════════
function openAddModal() {
  const sel = document.getElementById("newCat");
  sel.innerHTML = CATEGORIES.map(c => `<option value="${c.id}">${c.label}</option>`).join("");
  ["newName","newNote","newDesc"].forEach(id => document.getElementById(id).value = "");
  document.getElementById("newPrio").value = "moyenne";
  document.getElementById("modalBg").classList.add("open");
}
function closeModal() { document.getElementById("modalBg").classList.remove("open"); }
function closeModalIfBg(e) { if (e.target === document.getElementById("modalBg")) closeModal(); }
function clearError(id) { document.getElementById(id+"Err").style.display = "none"; }

async function saveTask() {
  const name = document.getElementById("newName").value.trim();
  if (!name) { document.getElementById("newNameErr").style.display = "block"; return; }
  const catId = document.getElementById("newCat").value;
  const prio = document.getElementById("newPrio").value;
  const note = document.getElementById("newNote").value.trim();
  const description = document.getElementById("newDesc").value.trim();
  const id = "t" + Date.now();
  const position = tasks.filter(t => t.cat_id === catId).length;
  const newTask = { id, cat_id: catId, name, prio, note, description, done: false, position };
  tasks.push(newTask);
  renderAll();
  closeModal();
  setSyncStatus("syncing", "Sauvegarde…");
  try {
    await sb("tasks", { method: "POST", body: JSON.stringify(newTask), prefer: "return=minimal" });
    setSyncStatus("ok", "Synchronisé");
    showToast("Tâche ajoutée !");
  } catch {
    tasks = tasks.filter(t => t.id !== id);
    renderAll();
    setSyncStatus("error", "Erreur ajout");
  }
}

// ═══════════════════════════════════════
// EXPORT
// ═══════════════════════════════════════
function exportJSON() {
  const json = JSON.stringify({ categories: CATEGORIES, tasks }, null, 2);
  const blob = new Blob([json], { type: "application/json" });
  const a = document.createElement("a");
  a.href = URL.createObjectURL(blob);
  a.download = "aylox-tracker.json";
  a.click();
  showToast("Export téléchargé !");
}

// ═══════════════════════════════════════
// AI PANEL
// ═══════════════════════════════════════
function toggleAIPanel() { document.getElementById("aiPanel").classList.toggle("open"); }
function setAITab(tab, el) {
  currentAITab = tab;
  document.querySelectorAll(".ai-tab").forEach(t => t.classList.remove("active"));
  el.classList.add("active");
}

async function runAI() {
  const out = document.getElementById("aiOutput");
  out.innerHTML = '<span class="ai-loading">Claude réfléchit…</span>';
  const summary = CATEGORIES.map(cat => {
    const catTasks = tasks.filter(t => t.cat_id === cat.id);
    const done = catTasks.filter(t => t.done).length;
    const list = catTasks.map(t => `  - [${t.done?"x":" "}] ${t.name} (${t.prio})`).join("\n");
    return `### ${cat.label} (${done}/${catTasks.length} faites)\n${list}`;
  }).join("\n\n");

  const prompt = currentAITab === "suggest"
    ? `Tu es un assistant pour le développement du mod Minecraft "Aylox Furnitures" (Forge 1.20.1, ajoute meubles/caisse enregistreuse/poubelle/ordinateur/boissons/nourriture).\n\nTâches actuelles :\n${summary}\n\nPropose 5 nouvelles tâches pertinentes manquantes. Format : nom, catégorie, priorité, description technique (2-3 phrases). Sois précis et pratique.`
    : `Tu es un assistant pour le mod Minecraft "Aylox Furnitures" (Forge 1.20.1).\n\nÉtat actuel :\n${summary}\n\nGénère un résumé d'avancement structuré : ce qui est fait, ce qui reste prioritaire, 2-3 conseils concrets. Sois concis et encourageant.`;

  try {
    const res = await fetch("https://aylox-ai-proxy.aydindnt7.workers.dev/", {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({ prompt })
    });
    const json = await res.json();
    out.textContent = json.text || "Pas de réponse.";
  } catch {
    out.textContent = "Erreur de connexion à l'IA. Réessaie dans un moment.";
  }
}

async function aiGenerateDesc() {
  const name = document.getElementById("newName").value.trim();
  if (!name) { document.getElementById("newNameErr").style.display = "block"; return; }
  const descEl = document.getElementById("newDesc");
  descEl.value = "L'IA génère…";
  descEl.disabled = true;
  try {
    const res = await fetch("https://aylox-ai-proxy.aydindnt7.workers.dev/", {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({
        prompt: `Pour le mod Minecraft "Aylox Furnitures" (Forge 1.20.1), génère une description technique courte (3-4 phrases max) pour cette tâche : "${name}". Sois précis, pratique, sans intro ni conclusion.`
      })
    });
    const json = await res.json();
    descEl.value = json.text || "";
  } catch { descEl.value = ""; }
  descEl.disabled = false;
}

async function aiDescTask(id) {
  const task = tasks.find(t => t.id === id);
  if (!task) return;
  const aiOut = document.getElementById("aiout-"+id);
  aiOut.className = "ai-inline-out open";
  aiOut.textContent = "L'IA améliore la description…";
  try {
    const res = await fetch("https://aylox-ai-proxy.aydindnt7.workers.dev/", {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({
        prompt: `Pour le mod Minecraft "Aylox Furnitures" (Forge 1.20.1), améliore cette description de tâche.\n\nTâche : "${task.name}"\nDescription actuelle : "${task.description||"aucune"}"\n\nGénère une description améliorée, précise et utile pour un développeur Forge. 3-5 phrases max. Pas d'intro, juste la description.`
      })
    });
    const json = await res.json();
    const text = json.text || "";
    aiOut.dataset.text = text;
    aiOut.innerHTML = `<strong style="color:var(--purple-text);font-size:11px">Suggestion IA :</strong><br><br>${esc(text)}<br><br>
      <button class="task-desc-btn" onclick="applyAIDesc('${id}')">Appliquer cette description</button>`;
  } catch {
    aiOut.textContent = "Erreur IA. Réessaie.";
  }
}

async function applyAIDesc(id) {
  const aiOut = document.getElementById("aiout-"+id);
  const text = aiOut.dataset.text;
  const task = tasks.find(t => t.id === id);
  if (!task || !text) return;
  task.description = text;
  renderAll();
  setSyncStatus("syncing", "Sauvegarde…");
  try {
    await sb(`tasks?id=eq.${id}`, { method: "PATCH", body: JSON.stringify({ description: text }), prefer: "return=minimal" });
    setSyncStatus("ok", "Synchronisé");
    showToast("Description mise à jour !");
  } catch {
    setSyncStatus("error", "Erreur sauvegarde");
  }
}

// ═══════════════════════════════════════
// THÈME
// ═══════════════════════════════════════
function initTheme() {
  const saved = localStorage.getItem("aylox_theme");
  if (saved === "dark") applyTheme("dark");
}
function toggleTheme() {
  applyTheme(document.documentElement.dataset.theme === "dark" ? "light" : "dark");
}
function applyTheme(mode) {
  document.documentElement.dataset.theme = mode === "dark" ? "dark" : "";
  localStorage.setItem("aylox_theme", mode);
  document.getElementById("iconMoon").style.display = mode === "dark" ? "none" : "block";
  document.getElementById("iconSun").style.display = mode === "dark" ? "block" : "none";
}

// ═══════════════════════════════════════
// TOAST
// ═══════════════════════════════════════
let toastTimer;
function showToast(msg) {
  const t = document.getElementById("toast");
  t.textContent = msg;
  t.classList.add("show");
  clearTimeout(toastTimer);
  toastTimer = setTimeout(() => t.classList.remove("show"), 2500);
}

// ═══════════════════════════════════════
// DÉMARRAGE
// ═══════════════════════════════════════
initTheme();
init();
</script>
</body>
</html>
