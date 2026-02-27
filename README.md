<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Mesas VIP – La Playa Aniversario IX</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:ital,wght@0,400;0,500;0,600;0,700;1,400&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #5a1a06;
    --venue: #c05828;
    --venue-light: #d06838;
    --silver-zone: rgba(255,255,255,0.12);
    --gold-zone: rgba(255,200,80,0.15);
    --back-zone: rgba(200,180,230,0.12);
    --pista: rgba(0,0,0,0.10);
    --reserved: #e07040;
    --sold: #3a2828;
    --accent: #FFD166;
    --white: #fff;
  }
  * { box-sizing: border-box; margin: 0; padding: 0; }
  body {
    background: radial-gradient(ellipse at top, #7a2510 0%, #4a1205 100%);
    font-family: 'DM Sans', sans-serif;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 0 0 80px;
  }

  /* HEADER */
  header {
    width: 100%; max-width: 520px;
    padding: 28px 24px 8px;
    display: flex; flex-direction: column; align-items: center; gap: 4px;
  }
  .brand { display: flex; justify-content: space-between; width: 100%; align-items: flex-start; }
  .brand-name { font-family: 'Bebas Neue', sans-serif; font-size: 28px; color: var(--white); letter-spacing: 2px; line-height: 1; }
  .brand-sub { font-size: 9px; letter-spacing: 4px; color: rgba(255,255,255,0.55); text-transform: uppercase; margin-top: 2px; }
  .brand-date .date { font-family: 'Bebas Neue', sans-serif; font-size: 26px; color: var(--white); letter-spacing: 2px; text-align: right; }
  .brand-date .venue-sub { font-size: 9px; letter-spacing: 3px; color: rgba(255,255,255,0.45); text-transform: uppercase; text-align: right; }
  h1 { font-family: 'Bebas Neue', sans-serif; font-size: clamp(50px,13vw,78px); color: var(--white); letter-spacing: 6px; text-align: center; line-height: 1; text-shadow: 0 4px 24px rgba(0,0,0,0.4); }

  /* SOLD % BAR */
  .sold-bar-wrap {
    width: 100%; max-width: 520px;
    padding: 0 24px 14px;
  }
  .sold-bar-header { display: flex; justify-content: space-between; align-items: baseline; margin-bottom: 6px; }
  .sold-bar-label { font-size: 11px; letter-spacing: 2px; text-transform: uppercase; color: rgba(255,255,255,0.5); }
  .sold-bar-pct { font-family: 'Bebas Neue', sans-serif; font-size: 22px; color: var(--accent); letter-spacing: 1px; }
  .sold-bar-track {
    height: 6px; background: rgba(255,255,255,0.1); border-radius: 3px; overflow: hidden;
  }
  .sold-bar-fill {
    height: 100%; border-radius: 3px;
    background: linear-gradient(90deg, #e07040, #FFD166);
    transition: width 0.6s cubic-bezier(0.34,1.56,0.64,1);
  }
  .sold-bar-detail { font-size: 11px; color: rgba(255,255,255,0.35); margin-top: 4px; }

  /* LEGEND */
  .legend {
    display: flex; gap: 14px; justify-content: center; flex-wrap: wrap;
    padding: 0 16px 14px;
  }
  .legend-item { display: flex; align-items: center; gap: 5px; font-size: 11px; color: rgba(255,255,255,0.65); }
  .dot { width: 13px; height: 13px; border-radius: 50%; flex-shrink: 0; }
  .dot.ds { background: #b0b8c8; }
  .dot.dg { background: #e8b84b; }
  .dot.db { background: #c0a8d0; }
  .dot.dr { background: var(--reserved); }
  .dot.dd { background: var(--sold); border: 1px solid rgba(255,255,255,0.15); }

  /* MAP WRAPPER */
  .map-wrapper { width: 100%; max-width: 520px; padding: 0 12px; }
  .venue {
    background: var(--venue);
    border-radius: 18px;
    padding: 14px 14px 18px;
    box-shadow: inset 0 0 60px rgba(0,0,0,0.15), 0 10px 50px rgba(0,0,0,0.5);
    border: 2px solid rgba(255,255,255,0.1);
  }

  /* TOP BAR */
  .top-bar { display: flex; align-items: center; justify-content: space-between; margin-bottom: 10px; gap: 8px; }
  .ingreso-block {
    background: var(--venue-light); border-radius: 10px 10px 0 10px;
    padding: 6px 12px 7px; display: flex; flex-direction: column; align-items: center;
  }
  .label-ingreso { font-family: 'Bebas Neue', sans-serif; font-size: 17px; color: var(--white); letter-spacing: 2px; }
  .arrows { font-size: 12px; color: rgba(255,255,255,0.75); }
  .barra-central {
    background: rgba(255,255,255,0.17); border: 1.5px solid rgba(255,255,255,0.28);
    border-radius: 20px; padding: 5px 16px;
    display: flex; align-items: center; gap: 5px;
    font-family: 'Bebas Neue', sans-serif; font-size: 14px; color: var(--white); letter-spacing: 2px;
  }
  .banos { font-size: 16px; color: rgba(255,255,255,0.45); }

  /* FLOOR */
  .floor { display: grid; grid-template-columns: auto 1fr auto; gap: 9px; align-items: start; }

  /* VIP SILVER */
  .vip-silver-zone {
    background: var(--silver-zone); border: 1.5px solid rgba(255,255,255,0.18);
    border-radius: 14px; padding: 9px 7px 9px 5px;
    display: flex; gap: 5px; align-items: flex-start;
  }
  .barra-lateral {
    writing-mode: vertical-rl; transform: rotate(180deg);
    font-family: 'Bebas Neue', sans-serif; font-size: 12px; letter-spacing: 2px;
    color: rgba(255,255,255,0.6); white-space: nowrap;
    display: flex; align-items: center; gap: 3px;
  }
  .silver-label-col {
    writing-mode: vertical-rl; transform: rotate(180deg);
    font-family: 'Bebas Neue', sans-serif; font-size: 13px; letter-spacing: 3px;
    color: rgba(255,255,255,0.45); display: flex; align-items: center; justify-content: center;
  }
  .silver-grid { display: grid; grid-template-columns: repeat(2,1fr); gap: 6px; }
  #silverOuter { display: flex; flex-direction: column; gap: 6px; }

  /* PISTA */
  .pista-col { display: flex; flex-direction: column; gap: 9px; }
  .pista-area {
    background: var(--pista); border-radius: 12px;
    padding: 8px; display: flex; flex-direction: column; gap: 0;
  }
  .pista-row { display: flex; justify-content: center; gap: 12px; padding: 5px 0; }
  .pista-text {
    font-family: 'Bebas Neue', sans-serif; font-size: clamp(20px,6vw,34px);
    letter-spacing: 10px; color: rgba(255,255,255,0.16); text-align: center;
    padding: 8px 0; user-select: none;
  }

  /* RIGHT COL */
  .right-col { display: flex; flex-direction: column; gap: 8px; align-items: center; }
  .back-zone {
    background: var(--back-zone); border: 1.5px solid rgba(200,180,230,0.2);
    border-radius: 12px; padding: 8px 6px;
    display: flex; flex-direction: row; align-items: center; gap: 5px;
  }
  .back-label {
    writing-mode: vertical-rl; transform: rotate(180deg);
    font-family: 'Bebas Neue', sans-serif; font-size: 12px; letter-spacing: 3px;
    color: rgba(255,255,255,0.45); white-space: nowrap;
  }
  .back-grid { display: grid; grid-template-columns: repeat(2,1fr); gap: 6px; }
  .cabina {
    background: rgba(255,255,255,0.14); border: 1.5px solid rgba(255,255,255,0.22);
    border-radius: 12px; padding: 10px 10px;
    display: flex; flex-direction: column; align-items: center; gap: 3px;
  }
  .cabina-label { font-family: 'Bebas Neue', sans-serif; font-size: 12px; letter-spacing: 2px; color: rgba(255,255,255,0.65); }
  .cabina-icon { font-size: 22px; }

  /* VIP GOLD */
  .vip-gold-zone {
    background: var(--gold-zone); border: 1.5px solid rgba(230,180,60,0.35);
    border-radius: 14px; padding: 10px 11px; margin-top: 9px;
    display: flex; flex-direction: column; gap: 8px;
  }
  .gold-top-row, .gold-bottom-row { display: flex; gap: 6px; align-items: center; flex-wrap: wrap; }
  .gold-mid-row { display: flex; align-items: center; justify-content: space-between; gap: 8px; }
  .gold-zone-label { font-family: 'Bebas Neue', sans-serif; font-size: 17px; letter-spacing: 4px; color: rgba(255,220,100,0.75); }
  .barra-gold {
    background: rgba(230,180,60,0.22); border: 1px solid rgba(230,180,60,0.35);
    border-radius: 14px; padding: 4px 10px;
    font-family: 'Bebas Neue', sans-serif; font-size: 12px; letter-spacing: 2px; color: rgba(255,220,100,0.75);
    display: flex; align-items: center; gap: 4px;
  }
  #goldSideCol { display: flex; flex-direction: column; gap: 6px; }

  /* BOTTOM */
  .bottom-row { display: flex; justify-content: space-between; align-items: center; padding: 12px 0 0; }
  .terraza-label { font-family: 'Bebas Neue', sans-serif; font-size: 15px; letter-spacing: 3px; color: rgba(255,255,255,0.45); }

  /* TABLE BUTTON */
  .table {
    width: 37px; height: 37px; border-radius: 50%; border: none; cursor: pointer;
    font-family: 'Bebas Neue', sans-serif; font-size: 13px;
    display: flex; align-items: center; justify-content: center;
    transition: transform 0.15s ease, box-shadow 0.15s ease;
    position: relative; flex-shrink: 0;
    box-shadow: 0 2px 8px rgba(0,0,0,0.35);
  }
  .table:hover:not(.sold) { transform: scale(1.2); box-shadow: 0 5px 18px rgba(0,0,0,0.5); z-index: 10; }
  .table:active:not(.sold) { transform: scale(0.94); }
  .table.silver { background: radial-gradient(circle at 35% 35%, #d4dce8, #8a96aa); color: #1a1a2e; border: 1.5px solid rgba(255,255,255,0.45); }
  .table.gold   { background: radial-gradient(circle at 35% 35%, #f5d070, #c8900a); color: #3a2500; border: 1.5px solid rgba(255,240,160,0.5); }
  .table.back-t { background: radial-gradient(circle at 35% 35%, #c8b4e0, #7a60a0); color: #fff; border: 1.5px solid rgba(200,180,230,0.45); }
  .table.reserved { background: radial-gradient(circle at 35% 35%, #f0805a, #b04820) !important; color: #fff !important; border-color: rgba(255,150,100,0.4) !important; }
  .table.sold { background: var(--sold) !important; color: rgba(255,255,255,0.25) !important; cursor: not-allowed; border: 1px solid rgba(255,255,255,0.08) !important; }

  /* MODAL */
  .modal-overlay {
    display: none; position: fixed; inset: 0;
    background: rgba(0,0,0,0.65); z-index: 100;
    align-items: flex-end; justify-content: center;
    backdrop-filter: blur(5px);
  }
  .modal-overlay.active { display: flex; }
  .modal {
    background: linear-gradient(160deg, #3a1a08 0%, #5a2808 100%);
    border: 1.5px solid rgba(255,200,100,0.2);
    border-radius: 24px 24px 0 0;
    padding: 24px 24px 40px;
    width: 100%; max-width: 520px;
    animation: slideUp 0.32s cubic-bezier(0.34,1.56,0.64,1);
    position: relative;
  }
  @keyframes slideUp { from { transform: translateY(100%); opacity:0; } to { transform: translateY(0); opacity:1; } }
  .modal-handle { width: 38px; height: 4px; background: rgba(255,255,255,0.18); border-radius: 2px; margin: 0 auto 18px; }
  .modal-zone-badge {
    display: inline-block; font-size: 10px; letter-spacing: 3px; text-transform: uppercase;
    padding: 3px 10px; border-radius: 20px; margin-bottom: 8px; font-weight: 600;
  }
  .badge-silver { background: rgba(176,184,200,0.18); color: #c0c8d8; border: 1px solid rgba(176,184,200,0.28); }
  .badge-gold   { background: rgba(232,184,75,0.18); color: #e8c060; border: 1px solid rgba(232,184,75,0.28); }
  .badge-back   { background: rgba(192,168,208,0.18); color: #c0a8d0; border: 1px solid rgba(192,168,208,0.28); }
  .modal-title { font-family: 'Bebas Neue', sans-serif; font-size: 36px; color: var(--white); letter-spacing: 3px; line-height: 1; }
  .modal-price { font-family: 'Bebas Neue', sans-serif; font-size: 26px; margin: 5px 0 3px; }
  .price-silver { color: #c0c8d8; } .price-gold { color: #e8c060; } .price-back { color: #c0a8d0; }
  .modal-desc { font-size: 13px; color: rgba(255,255,255,0.5); margin-bottom: 16px; line-height: 1.55; min-height: 20px; }
  .modal-status {
    display: inline-flex; align-items: center; gap: 6px;
    font-size: 11px; font-weight: 600; letter-spacing: 1px; text-transform: uppercase; margin-bottom: 18px;
  }
  .status-dot { width: 7px; height: 7px; border-radius: 50%; }
  .status-available { color: #7dcea0; } .status-available .status-dot { background: #7dcea0; }
  .status-reserved  { color: #e07040; } .status-reserved .status-dot  { background: #e07040; }
  .btn-whatsapp {
    display: flex; align-items: center; justify-content: center; gap: 10px;
    background: linear-gradient(135deg, #25D366, #128C7E);
    color: white; border: none; border-radius: 14px; padding: 15px;
    width: 100%; font-family: 'DM Sans', sans-serif; font-size: 15px; font-weight: 600;
    cursor: pointer; transition: transform 0.15s, box-shadow 0.15s;
    box-shadow: 0 4px 20px rgba(37,211,102,0.28); text-decoration: none;
  }
  .btn-whatsapp:hover { transform: translateY(-2px); box-shadow: 0 6px 24px rgba(37,211,102,0.38); }
  .btn-whatsapp svg { width: 21px; height: 21px; fill: white; flex-shrink: 0; }
  .btn-close {
    position: absolute; top: 16px; right: 18px;
    background: rgba(255,255,255,0.1); border: none; color: white;
    width: 30px; height: 30px; border-radius: 50%; cursor: pointer; font-size: 15px;
    display: flex; align-items: center; justify-content: center; transition: background 0.15s;
  }
  .btn-close:hover { background: rgba(255,255,255,0.2); }

  /* ADMIN TOGGLE */
  .admin-toggle {
    margin-top: 22px;
    background: rgba(255,255,255,0.07); border: 1px solid rgba(255,255,255,0.13);
    color: rgba(255,255,255,0.55); border-radius: 10px; padding: 10px 20px;
    font-family: 'DM Sans', sans-serif; font-size: 13px; cursor: pointer;
    letter-spacing: 1px; transition: all 0.2s; display: flex; align-items: center; gap: 8px;
  }
  .admin-toggle:hover { background: rgba(255,255,255,0.12); color: white; }

  /* PASSWORD MODAL */
  .pw-overlay {
    display: none; position: fixed; inset: 0;
    background: rgba(0,0,0,0.75); z-index: 200;
    align-items: center; justify-content: center;
    backdrop-filter: blur(6px);
  }
  .pw-overlay.active { display: flex; }
  .pw-box {
    background: linear-gradient(160deg, #3a1a08, #5a2808);
    border: 1.5px solid rgba(255,200,100,0.2);
    border-radius: 20px; padding: 32px 28px;
    width: 90%; max-width: 340px;
    display: flex; flex-direction: column; align-items: center; gap: 16px;
    animation: slideUp 0.28s cubic-bezier(0.34,1.56,0.64,1);
  }
  .pw-icon { font-size: 36px; }
  .pw-title { font-family: 'Bebas Neue', sans-serif; font-size: 26px; letter-spacing: 3px; color: white; }
  .pw-subtitle { font-size: 12px; color: rgba(255,255,255,0.4); letter-spacing: 1px; text-align: center; }
  .pw-input {
    width: 100%; background: rgba(0,0,0,0.35); color: white;
    border: 1.5px solid rgba(255,255,255,0.15); border-radius: 10px;
    padding: 12px 16px; font-size: 16px; font-family: 'DM Sans', sans-serif;
    text-align: center; letter-spacing: 2px;
  }
  .pw-input:focus { outline: none; border-color: var(--accent); }
  .pw-btn {
    width: 100%; background: linear-gradient(135deg, var(--accent), #e8a020);
    color: #3a2000; border: none; border-radius: 10px; padding: 13px;
    font-family: 'DM Sans', sans-serif; font-size: 15px; font-weight: 700;
    cursor: pointer; transition: all 0.2s;
  }
  .pw-btn:hover { transform: translateY(-1px); box-shadow: 0 4px 16px rgba(255,209,102,0.3); }
  .pw-error { font-size: 12px; color: #e07040; display: none; }
  .pw-close {
    position: absolute; top: 12px; right: 14px;
    background: rgba(255,255,255,0.1); border: none; color: white;
    width: 28px; height: 28px; border-radius: 50%; cursor: pointer; font-size: 14px;
    display: flex; align-items: center; justify-content: center;
  }

  /* ADMIN PANEL */
  .admin-panel {
    display: none; width: 100%; max-width: 520px;
    margin-top: 14px; background: rgba(0,0,0,0.28);
    border: 1px solid rgba(255,255,255,0.1); border-radius: 16px; padding: 20px;
  }
  .admin-panel.active { display: block; }
  .admin-section-title {
    font-size: 10px; letter-spacing: 2px; text-transform: uppercase;
    color: rgba(255,255,255,0.35); margin-bottom: 10px; margin-top: 18px;
  }
  .admin-section-title:first-child { margin-top: 0; }
  .admin-panel-title { font-family: 'Bebas Neue', sans-serif; font-size: 22px; letter-spacing: 3px; color: var(--white); margin-bottom: 16px; }

  /* WA config */
  .admin-wa-row { display: flex; gap: 8px; align-items: center; }
  .admin-input {
    background: rgba(0,0,0,0.3); color: white; border: 1px solid rgba(255,255,255,0.15);
    border-radius: 8px; padding: 8px 10px; font-size: 13px; font-family: 'DM Sans', sans-serif;
    flex: 1;
  }
  .admin-input:focus { outline: none; border-color: var(--accent); }

  /* Table admin grid */
  .admin-tables-grid { display: flex; flex-direction: column; gap: 8px; max-height: 420px; overflow-y: auto; }
  .admin-table-row {
    background: rgba(255,255,255,0.05); border-radius: 10px; padding: 10px 12px;
    display: grid; grid-template-columns: 60px 1fr 1fr auto; gap: 8px; align-items: center;
  }
  .admin-table-id { font-size: 12px; font-weight: 700; color: rgba(255,255,255,0.8); }
  .admin-table-row input, .admin-table-row select {
    background: rgba(0,0,0,0.3); color: white; border: 1px solid rgba(255,255,255,0.13);
    border-radius: 7px; padding: 6px 8px; font-size: 12px; font-family: 'DM Sans', sans-serif; width: 100%;
  }
  .admin-table-row input:focus, .admin-table-row select:focus { outline: none; border-color: var(--accent); }
  .admin-table-row input::placeholder { color: rgba(255,255,255,0.25); }
  .admin-col-headers {
    display: grid; grid-template-columns: 60px 1fr 1fr auto; gap: 8px;
    padding: 0 12px 4px; font-size: 10px; letter-spacing: 1px; text-transform: uppercase;
    color: rgba(255,255,255,0.3);
  }

  /* Save + Export */
  .admin-actions { display: flex; gap: 10px; margin-top: 16px; flex-wrap: wrap; align-items: center; }
  .btn-save {
    background: linear-gradient(135deg, var(--accent), #e8a020); color: #3a2000;
    border: none; border-radius: 10px; padding: 11px 22px;
    font-family: 'DM Sans', sans-serif; font-size: 14px; font-weight: 700;
    cursor: pointer; transition: all 0.2s;
  }
  .btn-save:hover { transform: translateY(-1px); box-shadow: 0 4px 16px rgba(255,209,102,0.3); }
  .btn-export {
    background: rgba(255,255,255,0.08); color: rgba(255,255,255,0.7);
    border: 1px solid rgba(255,255,255,0.15); border-radius: 10px; padding: 11px 22px;
    font-family: 'DM Sans', sans-serif; font-size: 14px; font-weight: 600;
    cursor: pointer; transition: all 0.2s; display: flex; align-items: center; gap: 7px;
  }
  .btn-export:hover { background: rgba(255,255,255,0.14); color: white; }
  .saved-toast { display:none; font-size:12px; color:#7dcea0; animation: fadePop 0.3s ease; }
  @keyframes fadePop { from{opacity:0;transform:scale(0.8)}to{opacity:1;transform:scale(1)} }

  @media(max-width:420px){
    .table{width:33px;height:33px;font-size:12px;}
    .floor{gap:6px;}
    .admin-table-row{grid-template-columns:50px 1fr 1fr;}
    .admin-table-row select{grid-column:1/-1;}
  }
</style>
</head>
<body>

<header>
  <div class="brand">
    <div class="brand-left">
      <div class="brand-name">La Playa</div>
      <div class="brand-sub">Aniversario IX</div>
    </div>
    <div class="brand-date">
      <div class="date">30.04.26</div>
      <div class="venue-sub">Morocco</div>
    </div>
  </div>
  <h1>MESAS VIP</h1>
</header>

<!-- SOLD % BAR -->
<div class="sold-bar-wrap">
  <div class="sold-bar-header">
    <div class="sold-bar-label">Disponibilidad</div>
    <div class="sold-bar-pct" id="soldPct">0% vendido</div>
  </div>
  <div class="sold-bar-track"><div class="sold-bar-fill" id="soldFill" style="width:0%"></div></div>
  <div class="sold-bar-detail" id="soldDetail"></div>
</div>

<!-- LEGEND -->
<div class="legend">
  <div class="legend-item"><div class="dot ds"></div> Silver</div>
  <div class="legend-item"><div class="dot dg"></div> Gold</div>
  <div class="legend-item"><div class="dot db"></div> Back</div>
  <div class="legend-item"><div class="dot dr"></div> Reservada</div>
  <div class="legend-item"><div class="dot dd"></div> Agotada</div>
</div>

<!-- MAP -->
<div class="map-wrapper">
  <div class="venue">
    <div class="top-bar">
      <div class="ingreso-block">
        <div class="label-ingreso">INGRESO</div>
        <div class="arrows">↓ ↓</div>
      </div>
      <div style="display:flex;align-items:center;gap:8px;">
        <span class="banos">🚻</span>
        <div class="barra-central">BARRA 🍹</div>
        <span class="banos">🚻</span>
      </div>
    </div>

    <div class="floor">
      <!-- LEFT: VIP SILVER -->
      <div class="vip-silver-zone">
        <div id="silverOuter" style="display:flex;flex-direction:column;gap:6px;"></div>
        <div class="barra-lateral">🍹 BARRA</div>
        <div class="silver-label-col">VIP SILVER</div>
        <div class="silver-grid" id="silverGrid"></div>
      </div>

      <!-- CENTER: PISTA -->
      <div class="pista-col">
        <div class="pista-area">
          <div class="pista-row" id="pistaTopRow"></div>
          <div class="pista-text">P I S T A</div>
          <div class="pista-row" id="pistaBottomRow"></div>
        </div>
      </div>

      <!-- RIGHT: BACK + CABINA -->
      <div class="right-col">
        <div class="back-zone">
          <div class="back-label">BACK</div>
          <div class="back-grid" id="backGrid"></div>
        </div>
        <div class="cabina">
          <div class="cabina-icon">🎧</div>
          <div class="cabina-label">CABINA</div>
        </div>
      </div>
    </div>

    <!-- VIP GOLD -->
    <div class="vip-gold-zone">
      <div class="gold-top-row" id="goldTopRow"></div>
      <div class="gold-mid-row">
        <div class="gold-zone-label">VIP GOLD</div>
        <div class="barra-gold">🍹 BARRA</div>
        <div id="goldSideCol"></div>
      </div>
      <div class="gold-bottom-row" id="goldBottomRow"></div>
    </div>

    <div class="bottom-row">
      <div class="arrows" style="color:rgba(255,255,255,0.4)">↓ ↓</div>
      <div class="terraza-label">TERRAZA</div>
    </div>
  </div>
</div>

<!-- ADMIN TOGGLE -->
<button class="admin-toggle" onclick="askPassword()">🔐 Panel Administrador</button>

<!-- PASSWORD MODAL -->
<div class="pw-overlay" id="pwOverlay">
  <div class="pw-box" style="position:relative;">
    <button class="pw-close" onclick="closePw()">✕</button>
    <div class="pw-icon">🔐</div>
    <div class="pw-title">ACCESO ADMIN</div>
    <div class="pw-subtitle">Solo personal autorizado</div>
    <input class="pw-input" id="pwInput" type="password" placeholder="Contraseña" onkeydown="if(event.key==='Enter')checkPw()">
    <div class="pw-error" id="pwError">Contraseña incorrecta</div>
    <button class="pw-btn" onclick="checkPw()">Ingresar</button>
  </div>
</div>

<!-- ADMIN PANEL -->
<div class="admin-panel" id="adminPanel">
  <div class="admin-panel-title">⚙ Configuración</div>

  <div class="admin-section-title">WhatsApp para reservas</div>
  <div class="admin-wa-row">
    <input class="admin-input" id="waNumber" type="text" placeholder="ej: 5491112345678" value="5491112345678">
  </div>

  <div class="admin-section-title" style="margin-top:16px;">Mesas — precio, descripción y estado</div>
  <div class="admin-col-headers">
    <div>Mesa</div><div>Precio</div><div>Descripción</div><div>Estado</div>
  </div>
  <div class="admin-tables-grid" id="adminGrid"></div>

  <div class="admin-actions">
    <button class="btn-save" onclick="saveAdmin()">💾 Guardar cambios</button>
    <button class="btn-export" onclick="exportHTML()">⬇ Exportar HTML</button>
    <span class="saved-toast" id="savedToast">✓ Guardado</span>
  </div>
</div>

<!-- MODAL -->
<div class="modal-overlay" id="modalOverlay" onclick="closeModalOutside(event)">
  <div class="modal">
    <div class="modal-handle"></div>
    <button class="btn-close" onclick="closeModal()">✕</button>
    <div class="modal-zone-badge" id="modalBadge"></div>
    <div class="modal-title" id="modalTitle"></div>
    <div class="modal-price" id="modalPrice"></div>
    <div class="modal-desc" id="modalDesc"></div>
    <div class="modal-status" id="modalStatus"></div>
    <a class="btn-whatsapp" id="modalWA" href="#" target="_blank">
      <svg viewBox="0 0 24 24"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
      Reservar por WhatsApp
    </a>
  </div>
</div>

<script>
// ─── CONFIG ──────────────────────────────────────────────────────────────────
const CONFIG = {
  waNumber: '5491112345678'
};

// ─── TABLE DATA ───────────────────────────────────────────────────────────────
// zone: silver | gold | back
// state: available | reserved | sold
const TABLES = {
  1:  { zone:'silver', state:'available', price:'$80.000', desc:'' },
  2:  { zone:'silver', state:'available', price:'$80.000', desc:'' },
  3:  { zone:'silver', state:'available', price:'$80.000', desc:'' },
  4:  { zone:'silver', state:'available', price:'$85.000', desc:'' },
  5:  { zone:'silver', state:'available', price:'$85.000', desc:'' },
  6:  { zone:'silver', state:'available', price:'$85.000', desc:'' },
  7:  { zone:'silver', state:'available', price:'$90.000', desc:'' },
  8:  { zone:'silver', state:'available', price:'$90.000', desc:'' },
  9:  { zone:'silver', state:'available', price:'$75.000', desc:'' },
  10: { zone:'silver', state:'available', price:'$75.000', desc:'' },
  11: { zone:'silver', state:'available', price:'$75.000', desc:'' },
  12: { zone:'silver', state:'available', price:'$80.000', desc:'' },
  20: { zone:'silver', state:'available', price:'$100.000', desc:'' },
  21: { zone:'silver', state:'available', price:'$100.000', desc:'' },
  22: { zone:'silver', state:'available', price:'$100.000', desc:'' },
  23: { zone:'silver', state:'available', price:'$100.000', desc:'' },
  24: { zone:'silver', state:'available', price:'$100.000', desc:'' },
  25: { zone:'silver', state:'available', price:'$100.000', desc:'' },
  26: { zone:'back',   state:'available', price:'$150.000', desc:'' },
  27: { zone:'back',   state:'available', price:'$150.000', desc:'' },
  28: { zone:'back',   state:'available', price:'$150.000', desc:'' },
  29: { zone:'back',   state:'available', price:'$150.000', desc:'' },
  30: { zone:'gold',   state:'available', price:'$120.000', desc:'' },
  31: { zone:'gold',   state:'available', price:'$120.000', desc:'' },
  32: { zone:'gold',   state:'available', price:'$120.000', desc:'' },
  33: { zone:'gold',   state:'available', price:'$120.000', desc:'' },
  35: { zone:'gold',   state:'available', price:'$130.000', desc:'' },
  36: { zone:'gold',   state:'available', price:'$130.000', desc:'' },
  37: { zone:'gold',   state:'available', price:'$130.000', desc:'' },
  38: { zone:'gold',   state:'available', price:'$130.000', desc:'' },
  39: { zone:'gold',   state:'available', price:'$130.000', desc:'' },
  40: { zone:'gold',   state:'available', price:'$130.000', desc:'' },
  41: { zone:'gold',   state:'available', price:'$140.000', desc:'' },
  42: { zone:'gold',   state:'available', price:'$140.000', desc:'' },
};

// ─── SOLD BAR ────────────────────────────────────────────────────────────────
function updateSoldBar() {
  const all = Object.keys(TABLES).length;
  const sold = Object.values(TABLES).filter(t => t.state === 'sold' || t.state === 'reserved').length;
  const soldOnly = Object.values(TABLES).filter(t => t.state === 'sold').length;
  const pct = Math.round((sold / all) * 100);
  document.getElementById('soldPct').textContent = pct + '% vendido';
  document.getElementById('soldFill').style.width = pct + '%';
  const avail = all - sold;
  document.getElementById('soldDetail').textContent = `${soldOnly} agotadas · ${sold - soldOnly} reservadas · ${avail} disponibles`;
}

// ─── MAKE TABLE BUTTON ───────────────────────────────────────────────────────
function makeTable(id) {
  const t = TABLES[id];
  const btn = document.createElement('button');
  btn.className = `table ${t.zone === 'gold' ? 'gold' : t.zone === 'back' ? 'back-t' : 'silver'}`;
  if (t.state === 'reserved') btn.classList.add('reserved');
  if (t.state === 'sold')     btn.classList.add('sold');
  btn.textContent = id;
  btn.dataset.id = id;
  if (t.state !== 'sold') btn.onclick = () => openModal(id);
  return btn;
}

// ─── RENDER MAP ──────────────────────────────────────────────────────────────
function renderMap() {
  // Silver main grid
  const sg = document.getElementById('silverGrid');
  sg.innerHTML = '';
  [8,7,6,5,4,3,2,1,12].forEach(id => sg.appendChild(makeTable(id)));

  // Silver outer
  const so = document.getElementById('silverOuter');
  so.innerHTML = '';
  [9,10,11].forEach(id => so.appendChild(makeTable(id)));

  // Pista
  const pt = document.getElementById('pistaTopRow');    pt.innerHTML = '';
  const pb = document.getElementById('pistaBottomRow'); pb.innerHTML = '';
  [23,24,25].forEach(id => pt.appendChild(makeTable(id)));
  [20,21,22].forEach(id => pb.appendChild(makeTable(id)));

  // Back
  const bg = document.getElementById('backGrid'); bg.innerHTML = '';
  [27,28,26,29].forEach(id => bg.appendChild(makeTable(id)));

  // Gold
  const gt = document.getElementById('goldTopRow');    gt.innerHTML = '';
  const gb = document.getElementById('goldBottomRow'); gb.innerHTML = '';
  const gs = document.getElementById('goldSideCol');   gs.innerHTML = '';
  [35,36,37,38,39,40].forEach(id => gt.appendChild(makeTable(id)));
  [30,31,32,33].forEach(id => gb.appendChild(makeTable(id)));
  [41,42].forEach(id => gs.appendChild(makeTable(id)));

  updateSoldBar();
}

// ─── MODAL ───────────────────────────────────────────────────────────────────
function openModal(id) {
  const t = TABLES[id];
  const zoneNames = { silver:'VIP Silver', gold:'VIP Gold', back:'Back' };
  document.getElementById('modalBadge').className = `modal-zone-badge badge-${t.zone}`;
  document.getElementById('modalBadge').textContent = zoneNames[t.zone];
  document.getElementById('modalTitle').textContent = `MESA ${id}`;
  document.getElementById('modalPrice').className = `modal-price price-${t.zone}`;
  document.getElementById('modalPrice').textContent = t.price || '—';
  document.getElementById('modalDesc').textContent = t.desc || '';

  const statusEl = document.getElementById('modalStatus');
  const waBtn = document.getElementById('modalWA');
  if (t.state === 'available') {
    statusEl.className = 'modal-status status-available';
    statusEl.innerHTML = '<div class="status-dot"></div> Disponible';
  } else {
    statusEl.className = 'modal-status status-reserved';
    statusEl.innerHTML = '<div class="status-dot"></div> Reservada';
  }
  const msg = encodeURIComponent(`Hola! Quiero reservar la Mesa ${id} (${zoneNames[t.zone]}) para La Playa Aniversario IX el 30/04/26.`);
  waBtn.href = `https://wa.me/${CONFIG.waNumber}?text=${msg}`;

  document.getElementById('modalOverlay').classList.add('active');
  document.body.style.overflow = 'hidden';
}
function closeModal() {
  document.getElementById('modalOverlay').classList.remove('active');
  document.body.style.overflow = '';
}
function closeModalOutside(e) {
  if (e.target === document.getElementById('modalOverlay')) closeModal();
}

// ─── ADMIN ───────────────────────────────────────────────────────────────────
function toggleAdmin() {
  const panel = document.getElementById('adminPanel');
  panel.classList.toggle('active');
  if (panel.classList.contains('active')) buildAdminGrid();
}

function buildAdminGrid() {
  document.getElementById('waNumber').value = CONFIG.waNumber;
  const grid = document.getElementById('adminGrid');
  grid.innerHTML = '';
  const zoneIcon = { silver:'🥈', gold:'🥇', back:'🎧' };
  Object.keys(TABLES).map(Number).sort((a,b)=>a-b).forEach(id => {
    const t = TABLES[id];
    const row = document.createElement('div');
    row.className = 'admin-table-row';

    const label = document.createElement('div');
    label.className = 'admin-table-id';
    label.textContent = `${zoneIcon[t.zone]} ${id}`;

    const priceInput = document.createElement('input');
    priceInput.type = 'text';
    priceInput.placeholder = 'Precio';
    priceInput.value = t.price || '';
    priceInput.dataset.id = id;
    priceInput.dataset.field = 'price';

    const descInput = document.createElement('input');
    descInput.type = 'text';
    descInput.placeholder = 'Descripción...';
    descInput.value = t.desc || '';
    descInput.dataset.id = id;
    descInput.dataset.field = 'desc';

    const sel = document.createElement('select');
    sel.dataset.id = id;
    sel.dataset.field = 'state';
    [['available','✅'],['reserved','🟠'],['sold','⛔']].forEach(([val,lbl]) => {
      const opt = document.createElement('option');
      opt.value = val; opt.textContent = lbl;
      if (t.state === val) opt.selected = true;
      sel.appendChild(opt);
    });

    row.appendChild(label);
    row.appendChild(priceInput);
    row.appendChild(descInput);
    row.appendChild(sel);
    grid.appendChild(row);
  });
}

function saveAdmin() {
  CONFIG.waNumber = document.getElementById('waNumber').value.trim();
  document.querySelectorAll('[data-field]').forEach(el => {
    const id = Number(el.dataset.id);
    const field = el.dataset.field;
    if (TABLES[id]) TABLES[id][field] = el.value;
  });
  renderMap();
  const toast = document.getElementById('savedToast');
  toast.style.display = 'inline';
  setTimeout(() => toast.style.display = 'none', 2500);
}

// ─── EXPORT HTML ─────────────────────────────────────────────────────────────
function exportHTML() {
  // Save current admin state first
  CONFIG.waNumber = document.getElementById('waNumber').value.trim();
  document.querySelectorAll('[data-field]').forEach(el => {
    const id = Number(el.dataset.id);
    if (TABLES[id]) TABLES[id][el.dataset.field] = el.value;
  });

  // Serialize TABLES and CONFIG into the HTML
  const html = document.documentElement.outerHTML;
  const tablesJSON = JSON.stringify(TABLES, null, 2);
  const configJSON = JSON.stringify(CONFIG);

  // Replace the TABLES and CONFIG declarations in the exported file
  const updated = html
    .replace(/const TABLES = \{[\s\S]*?\};/, `const TABLES = ${tablesJSON};`)
    .replace(/const CONFIG = \{[\s\S]*?\};/, `const CONFIG = ${configJSON};`);

  const blob = new Blob([updated], { type: 'text/html' });
  const a = document.createElement('a');
  a.href = URL.createObjectURL(blob);
  a.download = 'index.html';
  a.click();
}


// ─── PASSWORD ────────────────────────────────────────────────────────────────
const ADMIN_PW = 'Playitalovers26';
let adminUnlocked = false;

function askPassword() {
  if (adminUnlocked) { toggleAdmin(); return; }
  document.getElementById('pwOverlay').classList.add('active');
  document.getElementById('pwInput').value = '';
  document.getElementById('pwError').style.display = 'none';
  setTimeout(() => document.getElementById('pwInput').focus(), 100);
}

function checkPw() {
  if (document.getElementById('pwInput').value === ADMIN_PW) {
    adminUnlocked = true; closePw(); toggleAdmin();
  } else {
    document.getElementById('pwError').style.display = 'block';
    document.getElementById('pwInput').value = '';
    document.getElementById('pwInput').focus();
  }
}

function closePw() {
  document.getElementById('pwOverlay').classList.remove('active');
}

// ─── INIT ─────────────────────────────────────────────────────────────────────
renderMap();
</script>
</body>
</html>
