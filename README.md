#Babo bear salary
<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>🧋 Boba Bear Rayong — Finance</title>
<style>
:root{
  --primary:#7C3AED;--primary-light:#EDE9FE;
  --income:#10B981;--income-light:#D1FAE5;
  --expense:#EF4444;--expense-light:#FEE2E2;
  --net:#3B82F6;--net-light:#DBEAFE;
  --bg:#F5F3FF;--card:#fff;--text:#1F2937;
  --muted:#6B7280;--border:#E5E7EB;--radius:14px;
  --shadow:0 2px 12px rgba(124,58,237,.09);
}
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:'Segoe UI',Tahoma,sans-serif;background:var(--bg);color:var(--text);min-height:100vh}
.app-header{background:linear-gradient(135deg,#7C3AED,#5B21B6);color:#fff;padding:16px 20px;display:flex;align-items:center;gap:12px;box-shadow:0 2px 10px rgba(0,0,0,.2)}
.app-header .logo{font-size:28px}
.app-header h1{font-size:18px;font-weight:800}
.app-header small{font-size:11px;opacity:.8;display:block}
.user-info{margin-left:auto;display:flex;align-items:center;gap:8px;font-size:12px}
.user-avatar{width:32px;height:32px;border-radius:50%;border:2px solid rgba(255,255,255,.5)}
.nav-tabs{display:flex;background:#fff;border-bottom:2px solid var(--border);overflow-x:auto;position:sticky;top:0;z-index:50}
.nav-tab{flex:1;min-width:75px;padding:11px 6px;text-align:center;font-size:12px;font-weight:600;cursor:pointer;border:none;background:none;color:var(--muted);border-bottom:3px solid transparent;transition:.2s;white-space:nowrap}
.nav-tab.active{color:var(--primary);border-bottom-color:var(--primary)}
.login-screen{display:flex;flex-direction:column;align-items:center;justify-content:center;min-height:100vh;padding:20px;text-align:center;background:var(--bg)}
.login-card{background:#fff;border-radius:20px;padding:32px 24px;box-shadow:0 8px 40px rgba(124,58,237,.15);max-width:340px;width:100%}
.login-card .logo{font-size:60px;margin-bottom:12px}
.login-card h2{font-size:22px;font-weight:800;color:var(--primary);margin-bottom:6px}
.login-card p{font-size:13px;color:var(--muted);margin-bottom:24px;line-height:1.6}
.btn-google{display:flex;align-items:center;justify-content:center;gap:10px;width:100%;padding:14px;background:#fff;border:2px solid var(--border);border-radius:10px;font-size:14px;font-weight:700;color:var(--text);cursor:pointer;transition:.2s;text-decoration:none}
.btn-google:hover{background:#f9fafb;border-color:var(--primary)}
.btn-google img{width:20px;height:20px}
.page{display:none;padding:14px;max-width:540px;margin:0 auto;padding-bottom:30px}
.page.active{display:block}
.card{background:var(--card);border-radius:var(--radius);box-shadow:var(--shadow);padding:15px;margin-bottom:13px}
.card-title{font-size:14px;font-weight:700;color:var(--primary);margin-bottom:11px;display:flex;align-items:center;gap:6px}
.form-row{margin-bottom:10px}
.form-row label{font-size:12px;color:var(--muted);display:block;margin-bottom:4px;font-weight:600}
.form-row input,.form-row select,.form-row textarea{width:100%;padding:9px 12px;border:1.5px solid var(--border);border-radius:8px;font-size:13px;color:var(--text);transition:.2s;background:#fff}
.form-row input:focus,.form-row select:focus,.form-row textarea:focus{outline:none;border-color:var(--primary);box-shadow:0 0 0 3px var(--primary-light)}
.form-row textarea{resize:vertical;min-height:60px}
.row2{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.btn{padding:10px 16px;border:none;border-radius:9px;font-size:13px;font-weight:700;cursor:pointer;transition:.2s;display:inline-flex;align-items:center;gap:6px}
.btn:disabled{opacity:.5;cursor:not-allowed}
.btn-primary{background:var(--primary);color:#fff}
.btn-primary:hover:not(:disabled){background:#5B21B6}
.btn-income{background:var(--income);color:#fff}
.btn-income:hover:not(:disabled){background:#059669}
.btn-expense{background:var(--expense);color:#fff}
.btn-expense:hover:not(:disabled){background:#DC2626}
.btn-outline{background:#fff;color:var(--primary);border:1.5px solid var(--primary)}
.btn-outline:hover{background:var(--primary-light)}
.btn-sm{padding:6px 10px;font-size:11px}
.btn-danger-sm{background:var(--expense-light);color:var(--expense);padding:5px 9px;font-size:11px;border:none;border-radius:7px;cursor:pointer;font-weight:600}
.btn-edit-sm{background:var(--primary-light);color:var(--primary);padding:5px 9px;font-size:11px;border:none;border-radius:7px;cursor:pointer;font-weight:600;margin-right:4px}
.btn-row{display:flex;gap:8px;flex-wrap:wrap}
.kpi-grid{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:13px}
.kpi-card{border-radius:12px;padding:14px;text-align:center}
.kpi-card.income{background:var(--income-light)}
.kpi-card.expense{background:var(--expense-light)}
.kpi-card.net{background:var(--net-light);grid-column:1/-1}
.kpi-label{font-size:11px;color:var(--muted);font-weight:600;margin-bottom:4px}
.kpi-value{font-size:19px;font-weight:800}
.kpi-card.income .kpi-value{color:var(--income)}
.kpi-card.expense .kpi-value{color:var(--expense)}
.kpi-card.net .kpi-value{color:var(--net)}
.event-item{border:1.5px solid var(--border);border-radius:10px;padding:12px;margin-bottom:10px;background:#fff;transition:.2s}
.event-item:hover{border-color:var(--primary)}
.event-name{font-size:14px;font-weight:700}
.event-date{font-size:11px;color:var(--muted);margin-top:2px}
.event-badges{display:flex;gap:6px;margin-top:8px;flex-wrap:wrap}
.badge{padding:3px 8px;border-radius:20px;font-size:11px;font-weight:700}
.badge-income{background:var(--income-light);color:var(--income)}
.badge-expense{background:var(--expense-light);color:var(--expense)}
.badge-net-pos{background:var(--net-light);color:var(--net)}
.badge-net-neg{background:var(--expense-light);color:var(--expense)}
.record-item{display:flex;justify-content:space-between;align-items:center;padding:8px 0;border-bottom:1px solid var(--border);font-size:13px}
.record-item:last-child{border-bottom:none}
.record-label{font-weight:600}
.record-date{font-size:11px;color:var(--muted)}
.record-note{font-size:11px;color:var(--muted);font-style:italic}
.record-amount{font-weight:700;font-size:14px;white-space:nowrap}
.record-amount.income{color:var(--income)}
.record-amount.expense{color:var(--expense)}
.summary-row{display:flex;justify-content:space-between;padding:9px 0;border-bottom:1px dashed var(--border);font-size:13px}
.summary-row.total{font-weight:800;font-size:14px;border-bottom:none;padding-top:11px}
.summary-row .lbl{color:var(--muted)}
.val-inc{color:var(--income);font-weight:700}
.val-exp{color:var(--expense);font-weight:700}
.val-pos{color:var(--net);font-weight:700}
.val-neg{color:var(--expense);font-weight:700}
.modal-overlay{display:none;position:fixed;inset:0;background:rgba(0,0,0,.5);z-index:100;align-items:center;justify-content:center;padding:16px}
.modal-overlay.open{display:flex}
.modal{background:#fff;border-radius:var(--radius);width:100%;max-width:480px;max-height:90vh;overflow-y:auto;padding:20px;box-shadow:0 8px 40px rgba(0,0,0,.2);animation:slideUp .25s ease}
@keyframes slideUp{from{transform:translateY(30px);opacity:0}to{transform:translateY(0);opacity:1}}
.modal-title{font-size:16px;font-weight:800;margin-bottom:16px;color:var(--primary);display:flex;align-items:center;gap:8px}
.modal-close{margin-left:auto;background:none;border:none;font-size:20px;cursor:pointer;color:var(--muted)}
.filter-bar{display:flex;gap:8px;margin-bottom:13px;flex-wrap:wrap}
.filter-bar select,.filter-bar input{padding:7px 10px;border:1.5px solid var(--border);border-radius:8px;font-size:12px;background:#fff;flex:1;min-width:100px}
.chart-wrap{position:relative;height:220px}
.day-block{border:1px solid var(--border);border-radius:10px;margin-bottom:8px;overflow:hidden}
.day-block-head{background:var(--primary-light);padding:8px 12px;display:flex;justify-content:space-between;align-items:center;font-size:12px}
.day-block-head .dl{font-weight:700;color:var(--primary)}
.day-block-body{padding:10px 12px}
.toast{position:fixed;bottom:20px;left:50%;transform:translateX(-50%);background:#1F2937;color:#fff;padding:10px 20px;border-radius:20px;font-size:13px;font-weight:600;z-index:200;opacity:0;transition:.3s;pointer-events:none;white-space:nowrap}
.toast.show{opacity:1}
.sync-status{font-size:11px;color:var(--muted);text-align:right;padding:4px 0}
.sync-status.ok{color:var(--income)}
.sync-status.err{color:var(--expense)}
.sync-status.ing{color:var(--primary)}
.spinner{display:inline-block;width:14px;height:14px;border:2px solid var(--primary-light);border-top-color:var(--primary);border-radius:50%;animation:spin .7s linear infinite;vertical-align:middle;margin-right:4px}
@keyframes spin{to{transform:rotate(360deg)}}
.empty{text-align:center;padding:28px 16px;color:var(--muted)}
.empty .icon{font-size:38px;margin-bottom:8px}
.empty p{font-size:13px}
.loading-overlay{position:fixed;inset:0;background:rgba(255,255,255,.9);display:flex;flex-direction:column;align-items:center;justify-content:center;z-index:300;font-size:14px;color:var(--primary);gap:12px}
.loading-overlay .big-spinner{width:40px;height:40px;border:4px solid var(--primary-light);border-top-color:var(--primary);border-radius:50%;animation:spin .8s linear infinite}
@media(max-width:360px){.kpi-grid{grid-template-columns:1fr}.row2{grid-template-columns:1fr}}
</style>
</head>
<body>

<!-- LOADING -->
<div id="loading-overlay" class="loading-overlay">
  <div class="big-spinner"></div>
  <div id="loading-text">กำลังตรวจสอบการเข้าสู่ระบบ...</div>
</div>

<!-- LOGIN -->
<div id="login-screen" class="login-screen" style="display:none">
  <div class="login-card">
    <div class="logo">🧋</div>
    <h2>Boba Bear Rayong</h2>
    <p>ระบบบันทึกรายรับ-รายจ่าย<br>ร้านชานมไข่มุก<br><br>เข้าสู่ระบบด้วย Google เพื่อซิงค์ข้อมูลกับ Google Sheets</p>
    <a id="btn-signin" href="#" class="btn-google" onclick="handleSignIn(event)">
      <img src="https://www.gstatic.com/firebasejs/ui/2.0.0/images/auth/google.svg" alt="G"/>
      เข้าสู่ระบบด้วย Google
    </a>
    <div id="login-status" style="margin-top:12px;font-size:12px;color:var(--muted)"></div>
  </div>
</div>

<!-- APP -->
<div id="app-shell" style="display:none">
  <div class="app-header">
    <span class="logo">🧋</span>
    <div><h1>Boba Bear Rayong</h1><small>Finance Tracker</small></div>
    <div class="user-info">
      <img id="user-avatar" class="user-avatar" src="" alt=""/>
      <div>
        <div id="user-name" style="font-size:11px;font-weight:700"></div>
        <div style="font-size:10px;opacity:.7;cursor:pointer" onclick="handleSignOut()">ออกจากระบบ</div>
      </div>
    </div>
  </div>
  <div class="nav-tabs">
    <button class="nav-tab active" data-page="dashboard">📊 Dashboard</button>
    <button class="nav-tab" data-page="events">🎪 งาน</button>
    <button class="nav-tab" data-page="record">✏️ บันทึก</button>
  </div>

  <!-- DASHBOARD -->
  <div class="page active" id="page-dashboard">
    <div class="filter-bar" style="margin-top:8px">
      <select id="dash-type" onchange="renderDashboard()">
        <option value="month">📅 รายเดือน</option>
        <option value="event">🎪 รายงาน Event</option>
      </select>
      <select id="dash-month" onchange="renderDashboard()"></select>
      <select id="dash-event" style="display:none" onchange="renderDashboard()"><option value="">-- ทุก Event --</option></select>
    </div>
    <div class="kpi-grid">
      <div class="kpi-card income"><div class="kpi-label">💰 รายรับรวม</div><div class="kpi-value" id="k-income">฿0</div></div>
      <div class="kpi-card expense"><div class="kpi-label">💸 รายจ่ายรวม</div><div class="kpi-value" id="k-expense">฿0</div></div>
      <div class="kpi-card net"><div class="kpi-label">📈 กำไรสุทธิ</div><div class="kpi-value" id="k-net">฿0</div></div>
    </div>
    <div class="card">
      <div class="card-title">📊 กราฟรายรับ-รายจ่าย</div>
      <div class="chart-wrap"><canvas id="dash-chart"></canvas></div>
    </div>
    <div class="card">
      <div class="card-title">📋 รายการล่าสุด</div>
      <div id="dash-list"><div class="empty"><div class="icon">📭</div><p>ยังไม่มีข้อมูล</p></div></div>
    </div>
    <div class="sync-status" id="ss-dash"></div>
  </div>

  <!-- EVENTS -->
  <div class="page" id="page-events">
    <div style="display:flex;justify-content:space-between;align-items:center;margin:4px 0 12px">
      <strong style="font-size:15px">🎪 งาน / Events</strong>
      <button class="btn btn-primary btn-sm" onclick="openNewEventModal()">+ เพิ่มงาน</button>
    </div>
    <div id="event-list"></div>
    <div class="sync-status" id="ss-events"></div>
  </div>

  <!-- RECORD -->
  <div class="page" id="page-record">
    <div style="margin:4px 0 12px">
      <strong style="font-size:15px">✏️ บันทึกรายวัน</strong>
      <div style="font-size:12px;color:var(--muted);margin-top:2px">เลือก Event แล้วบันทึกรายรับ-รายจ่าย</div>
    </div>
    <div class="card">
      <div class="card-title">🎪 เลือก Event</div>
      <div class="form-row">
        <label>Event / งานที่ออก</label>
        <select id="rec-event" onchange="onRecordEventChange()"><option value="">-- เลือก Event --</option></select>
      </div>
      <div id="rec-date-wrap" style="display:none">
        <div class="form-row"><label>วันที่บันทึก (แก้ไขได้)</label><input type="date" id="rec-date" onchange="renderDailyRecords()"/></div>
      </div>
    </div>
    <div id="rec-entry" style="display:none">
      <div class="card">
        <div class="card-title" style="color:var(--income)">💰 เพิ่มรายรับ</div>
        <div class="row2">
          <div class="form-row"><label>จำนวนเงิน (บาท)</label><input type="number" id="inc-amt" placeholder="0" min="0"/></div>
          <div class="form-row"><label>หมวดหมู่</label>
            <select id="inc-cat"><option>ขายชานม</option><option>ขายขนม</option><option>ขายสินค้าอื่น</option><option>อื่นๆ</option></select>
          </div>
        </div>
        <div class="form-row"><label>หมายเหตุ</label><input type="text" id="inc-note" placeholder="เช่น ยอดขายช่วงเที่ยง"/></div>
        <button class="btn btn-income" id="btn-add-inc" onclick="addRecord('income')" style="width:100%">+ เพิ่มรายรับ</button>
      </div>
      <div class="card">
        <div class="card-title" style="color:var(--expense)">💸 เพิ่มรายจ่าย</div>
        <div class="row2">
          <div class="form-row"><label>จำนวนเงิน (บาท)</label><input type="number" id="exp-amt" placeholder="0" min="0"/></div>
          <div class="form-row"><label>หมวดหมู่</label>
            <select id="exp-cat"><option>ค่าวัตถุดิบ</option><option>ค่าเดินทาง</option><option>ค่าเช่าพื้นที่</option><option>ค่าบรรจุภัณฑ์</option><option>ค่าไฟ/น้ำ</option><option>อื่นๆ</option></select>
          </div>
        </div>
        <div class="form-row"><label>หมายเหตุ</label><input type="text" id="exp-note" placeholder="เช่น ซื้อชาไทย"/></div>
        <button class="btn btn-expense" id="btn-add-exp" onclick="addRecord('expense')" style="width:100%">+ เพิ่มรายจ่าย</button>
      </div>
      <div class="card">
        <div class="card-title">📋 รายการวันนี้ (<span id="daily-date-lbl">-</span>)</div>
        <div id="daily-list"><div class="empty" style="padding:14px"><p>ยังไม่มีรายการ</p></div></div>
        <div style="margin-top:10px;padding-top:10px;border-top:2px solid var(--border)">
          <div class="summary-row"><span class="lbl">รายรับรวม</span><span class="val-inc" id="ds-inc">฿0</span></div>
          <div class="summary-row"><span class="lbl">รายจ่ายรวม</span><span class="val-exp" id="ds-exp">฿0</span></div>
          <div class="summary-row total"><span>กำไรสุทธิ</span><span id="ds-net">฿0</span></div>
        </div>
      </div>
    </div>
    <div class="sync-status" id="ss-rec"></div>
  </div>
</div>

<!-- MODAL EVENT FORM -->
<div class="modal-overlay" id="modal-event">
  <div class="modal">
    <div class="modal-title">🎪 <span id="modal-ev-title">เพิ่มงานใหม่</span>
      <button class="modal-close" onclick="closeModal('modal-event')">✕</button>
    </div>
    <input type="hidden" id="ev-id"/>
    <div class="form-row"><label>ชื่องาน / Event *</label><input type="text" id="ev-name" placeholder="เช่น งานเทศกาลสงกรานต์ 2568"/></div>
    <div class="row2">
      <div class="form-row"><label>วันเริ่มงาน *</label><input type="date" id="ev-start"/></div>
      <div class="form-row"><label>วันจบงาน *</label><input type="date" id="ev-end"/></div>
    </div>
    <div class="form-row"><label>สถานที่</label><input type="text" id="ev-loc" placeholder="เช่น สวนสาธารณะ"/></div>
    <div class="form-row"><label>หมายเหตุ</label><textarea id="ev-note"></textarea></div>
    <div class="btn-row" style="margin-top:14px">
      <button class="btn btn-primary" id="btn-save-ev" onclick="saveEvent()" style="flex:1">💾 บันทึก</button>
      <button class="btn btn-outline" onclick="closeModal('modal-event')">ยกเลิก</button>
    </div>
  </div>
</div>

<!-- MODAL EVENT DETAIL -->
<div class="modal-overlay" id="modal-detail">
  <div class="modal">
    <div class="modal-title">📋 <span id="modal-detail-name"></span>
      <button class="modal-close" onclick="closeModal('modal-detail')">✕</button>
    </div>
    <div id="modal-detail-body"></div>
  </div>
</div>

<div class="toast" id="toast"></div>

<script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.0/dist/chart.umd.min.js"></script>
<script>
// ══════════════════════════════════════
// CONFIG
// ══════════════════════════════════════
const CLIENT_ID    = '287915428157-u1b12rguf2l7o4tmuku7g3jhmq5sdbat.apps.googleusercontent.com';
const REDIRECT_URI = 'https://phalapan.github.io/boba-bear-rayong/';
const SCOPES       = 'https://www.googleapis.com/auth/spreadsheets https://www.googleapis.com/auth/drive.file https://www.googleapis.com/auth/userinfo.profile';
const SHEET_TITLE  = 'Boba Bear Rayong';

// ══════════════════════════════════════
// STATE
// ══════════════════════════════════════
let accessToken  = null;
let spreadsheetId = localStorage.getItem('boba_sheet_id') || null;
let events = [], records = [];
let dashChart = null;

// ══════════════════════════════════════
// UTILS
// ══════════════════════════════════════
function uid(){ return Date.now().toString(36)+Math.random().toString(36).slice(2,7); }
function fmt(n){ return '฿'+(n||0).toLocaleString('th-TH',{minimumFractionDigits:2,maximumFractionDigits:2}); }
function today(){ return new Date().toISOString().slice(0,10); }

function showToast(msg,ok=true){
  const t=document.getElementById('toast');
  t.textContent=msg; t.style.background=ok?'#065F46':'#991B1B';
  t.classList.add('show'); setTimeout(()=>t.classList.remove('show'),2800);
}
function setSS(id,msg,cls=''){
  const el=document.getElementById(id); if(!el)return;
  el.textContent=msg; el.className='sync-status '+(cls||'');
}
function closeModal(id){ document.getElementById(id).classList.remove('open'); }
function openModal(id) { document.getElementById(id).classList.add('open'); }
function showLoading(msg='กำลังโหลด...'){
  document.getElementById('loading-overlay').style.display='flex';
  document.getElementById('loading-text').textContent=msg;
}
function hideLoading(){ document.getElementById('loading-overlay').style.display='none'; }
function showLogin(){ document.getElementById('login-screen').style.display='flex'; hideLoading(); }
function showApp()  { document.getElementById('app-shell').style.display='block'; document.getElementById('login-screen').style.display='none'; hideLoading(); }

// ══════════════════════════════════════
// OAUTH — REDIRECT FLOW (iPhone Safe)
// ══════════════════════════════════════
function buildAuthUrl(){
  const params = new URLSearchParams({
    client_id    : CLIENT_ID,
    redirect_uri : REDIRECT_URI,
    response_type: 'token',
    scope        : SCOPES,
    include_granted_scopes: 'true',
    state        : 'boba_auth'
  });
  return 'https://accounts.google.com/o/oauth2/v2/auth?' + params.toString();
}

function handleSignIn(e){
  e.preventDefault();
  // Full page redirect — works on ALL browsers including Safari/iPhone
  window.location.href = buildAuthUrl();
}

function handleSignOut(){
  if(accessToken){
    fetch('https://oauth2.googleapis.com/revoke?token='+accessToken,{method:'POST'}).catch(()=>{});
  }
  accessToken = null;
  localStorage.removeItem('boba_token');
  localStorage.removeItem('boba_token_exp');
  document.getElementById('app-shell').style.display='none';
  showLogin();
  showToast('ออกจากระบบแล้ว');
}

// ── Parse token from URL hash (after redirect back) ──
function parseTokenFromHash(){
  const hash = window.location.hash.substring(1);
  if(!hash) return null;
  const params = new URLSearchParams(hash);
  if(params.get('state') !== 'boba_auth') return null;
  const token   = params.get('access_token');
  const expires = params.get('expires_in');
  if(!token) return null;
  // Save token + expiry
  const expTime = Date.now() + (parseInt(expires)||3600)*1000;
  localStorage.setItem('boba_token',     token);
  localStorage.setItem('boba_token_exp', expTime.toString());
  // Clean URL (remove hash)
  history.replaceState(null,'',window.location.pathname);
  return token;
}

function getSavedToken(){
  const token  = localStorage.getItem('boba_token');
  const expStr = localStorage.getItem('boba_token_exp');
  if(!token || !expStr) return null;
  if(Date.now() > parseInt(expStr) - 60000) return null; // expired
  return token;
}

// ══════════════════════════════════════
// GOOGLE API CALLS (fetch-based, no gapi)
// ══════════════════════════════════════
async function gFetch(url, options={}){
  const res = await fetch(url,{
    ...options,
    headers:{ 'Authorization':'Bearer '+accessToken, 'Content-Type':'application/json', ...(options.headers||{}) }
  });
  if(res.status===401){ handleSignOut(); throw new Error('Token หมดอายุ กรุณา Login ใหม่'); }
  return res.json();
}

async function fetchUserProfile(){
  try{
    const u = await gFetch('https://www.googleapis.com/oauth2/v3/userinfo');
    document.getElementById('user-name').textContent   = u.name||u.email||'';
    document.getElementById('user-avatar').src         = u.picture||'';
  }catch(e){}
}

async function initSheet(){
  if(spreadsheetId){ await ensureHeaders(); return; }
  setSS('ss-dash','⏳ สร้าง Google Sheet...','ing');
  const body = {
    properties:{title:SHEET_TITLE},
    sheets:[{properties:{title:'Events'}},{properties:{title:'Records'}}]
  };
  const res = await gFetch('https://sheets.googleapis.com/v4/spreadsheets',{method:'POST',body:JSON.stringify(body)});
  spreadsheetId = res.spreadsheetId;
  localStorage.setItem('boba_sheet_id', spreadsheetId);
  await ensureHeaders();
}

async function ensureHeaders(){
  // Events header
  const ev = await gFetch(`https://sheets.googleapis.com/v4/spreadsheets/${spreadsheetId}/values/Events!A1`);
  if(!ev.values){
    await gFetch(`https://sheets.googleapis.com/v4/spreadsheets/${spreadsheetId}/values/Events!A1?valueInputOption=RAW`,{
      method:'PUT', body:JSON.stringify({values:[['id','name','start','end','location','note','updatedAt']]})
    });
  }
  // Records header
  const rec = await gFetch(`https://sheets.googleapis.com/v4/spreadsheets/${spreadsheetId}/values/Records!A1`);
  if(!rec.values){
    await gFetch(`https://sheets.googleapis.com/v4/spreadsheets/${spreadsheetId}/values/Records!A1?valueInputOption=RAW`,{
      method:'PUT', body:JSON.stringify({values:[['id','eventId','type','amount','category','note','date','createdAt']]})
    });
  }
}

async function loadAllData(){
  setSS('ss-dash','⏳ กำลังโหลด...','ing');
  try{
    const [evRes,recRes] = await Promise.all([
      gFetch(`https://sheets.googleapis.com/v4/spreadsheets/${spreadsheetId}/values/Events!A2:G`),
      gFetch(`https://sheets.googleapis.com/v4/spreadsheets/${spreadsheetId}/values/Records!A2:H`)
    ]);
    events  = (evRes.values||[]).filter(r=>r[0]).map(r=>({id:r[0],name:r[1],start:r[2],end:r[3],location:r[4]||'',note:r[5]||'',updatedAt:r[6]||''}));
    records = (recRes.values||[]).filter(r=>r[0]).map(r=>({id:r[0],eventId:r[1],type:r[2],amount:parseFloat(r[3])||0,category:r[4],note:r[5]||'',date:r[6],createdAt:r[7]||''}));
    populateSelects(); renderEventList(); renderDashboard();
    setSS('ss-dash','✅ โหลดแล้ว '+new Date().toLocaleTimeString('th-TH'),'ok');
  }catch(e){
    setSS('ss-dash','❌ '+e.message,'err');
  }
}

async function appendRow(sheet,values){
  await gFetch(`https://sheets.googleapis.com/v4/spreadsheets/${spreadsheetId}/values/${sheet}!A1:append?valueInputOption=RAW&insertDataOption=INSERT_ROWS`,{
    method:'POST', body:JSON.stringify({values:[values]})
  });
}

async function findRowIndex(sheet,id){
  const res = await gFetch(`https://sheets.googleapis.com/v4/spreadsheets/${spreadsheetId}/values/${sheet}!A:A`);
  const rows = res.values||[];
  for(let i=0;i<rows.length;i++) if(rows[i][0]===id) return i+1;
  return -1;
}

async function updateRow(sheet,rowIdx,values){
  const col = String.fromCharCode(64+values.length);
  await gFetch(`https://sheets.googleapis.com/v4/spreadsheets/${spreadsheetId}/values/${sheet}!A${rowIdx}:${col}${rowIdx}?valueInputOption=RAW`,{
    method:'PUT', body:JSON.stringify({values:[values]})
  });
}

async function deleteSheetRow(sheet,rowIdx){
  // Get sheetId
  const meta = await gFetch(`https://sheets.googleapis.com/v4/spreadsheets/${spreadsheetId}?fields=sheets.properties`);
  const sh   = meta.sheets.find(s=>s.properties.title===sheet);
  if(!sh) return;
  await gFetch(`https://sheets.googleapis.com/v4/spreadsheets/${spreadsheetId}:batchUpdate`,{
    method:'POST',
    body:JSON.stringify({requests:[{deleteDimension:{range:{sheetId:sh.properties.sheetId,dimension:'ROWS',startIndex:rowIdx-1,endIndex:rowIdx}}}]})
  });
}

// ══════════════════════════════════════
// NAV
// ══════════════════════════════════════
document.querySelectorAll('.nav-tab').forEach(btn=>{
  btn.addEventListener('click',()=>{
    document.querySelectorAll('.nav-tab').forEach(b=>b.classList.remove('active'));
    document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
    btn.classList.add('active');
    document.getElementById('page-'+btn.dataset.page).classList.add('active');
    if(btn.dataset.page==='dashboard') renderDashboard();
    if(btn.dataset.page==='events')    renderEventList();
    if(btn.dataset.page==='record')    initRecordPage();
  });
});

// ══════════════════════════════════════
// EVENTS CRUD
// ══════════════════════════════════════
function openNewEventModal(){
  document.getElementById('ev-id').value='';
  document.getElementById('modal-ev-title').textContent='เพิ่มงานใหม่';
  ['ev-name','ev-loc','ev-note'].forEach(id=>document.getElementById(id).value='');
  document.getElementById('ev-start').value=today();
  document.getElementById('ev-end').value=today();
  openModal('modal-event');
}
function editEvent(id){
  const ev=events.find(e=>e.id===id); if(!ev)return;
  document.getElementById('ev-id').value=id;
  document.getElementById('modal-ev-title').textContent='แก้ไขงาน';
  document.getElementById('ev-name').value=ev.name;
  document.getElementById('ev-start').value=ev.start;
  document.getElementById('ev-end').value=ev.end;
  document.getElementById('ev-loc').value=ev.location||'';
  document.getElementById('ev-note').value=ev.note||'';
  openModal('modal-event');
}

async function saveEvent(){
  const name=document.getElementById('ev-name').value.trim();
  const start=document.getElementById('ev-start').value;
  const end=document.getElementById('ev-end').value;
  if(!name||!start||!end){showToast('กรุณากรอกให้ครบ',false);return;}
  if(start>end){showToast('วันเริ่มต้องไม่เกินวันจบ',false);return;}
  const id=document.getElementById('ev-id').value;
  const payload={id:id||uid(),name,start,end,location:document.getElementById('ev-loc').value,note:document.getElementById('ev-note').value,updatedAt:new Date().toISOString()};
  const btn=document.getElementById('btn-save-ev');
  btn.disabled=true; btn.innerHTML='<span class="spinner"></span>บันทึก...';
  try{
    if(id){
      const idx=events.findIndex(e=>e.id===id);
      if(idx>-1) events[idx]=payload; else events.push(payload);
      const rowIdx=await findRowIndex('Events',id);
      if(rowIdx>-1) await updateRow('Events',rowIdx,[payload.id,payload.name,payload.start,payload.end,payload.location,payload.note,payload.updatedAt]);
      else await appendRow('Events',[payload.id,payload.name,payload.start,payload.end,payload.location,payload.note,payload.updatedAt]);
    } else {
      events.push(payload);
      await appendRow('Events',[payload.id,payload.name,payload.start,payload.end,payload.location,payload.note,payload.updatedAt]);
    }
    closeModal('modal-event'); renderEventList(); populateSelects();
    showToast('✅ บันทึกงานสำเร็จ'); setSS('ss-events','✅ Sync แล้ว','ok');
  }catch(e){ showToast('❌ '+e.message,false); }
  btn.disabled=false; btn.innerHTML='💾 บันทึก';
}

async function deleteEvent(id){
  if(!confirm('ลบงานนี้?')) return;
  try{
    const rowIdx=await findRowIndex('Events',id);
    if(rowIdx>-1) await deleteSheetRow('Events',rowIdx);
    events=events.filter(e=>e.id!==id);
    renderEventList(); populateSelects(); showToast('🗑️ ลบงานแล้ว');
  }catch(e){ showToast('❌ '+e.message,false); }
}

function renderEventList(){
  const c=document.getElementById('event-list');
  if(!events.length){c.innerHTML='<div class="empty"><div class="icon">🎪</div><p>ยังไม่มีงาน</p></div>';return;}
  c.innerHTML=[...events].sort((a,b)=>b.start.localeCompare(a.start)).map(ev=>{
    const recs=records.filter(r=>r.eventId===ev.id);
    const ti=recs.filter(r=>r.type==='income').reduce((s,r)=>s+r.amount,0);
    const te=recs.filter(r=>r.type==='expense').reduce((s,r)=>s+r.amount,0);
    const net=ti-te;
    return `<div class="event-item">
      <div style="display:flex;justify-content:space-between;align-items:flex-start">
        <div><div class="event-name">🎪 ${ev.name}</div><div class="event-date">📅 ${ev.start} → ${ev.end}${ev.location?' | 📍'+ev.location:''}</div></div>
        <div><button class="btn-edit-sm" onclick="editEvent('${ev.id}')">✏️</button><button class="btn-danger-sm" onclick="deleteEvent('${ev.id}')">🗑️</button></div>
      </div>
      <div class="event-badges">
        <span class="badge badge-income">+${fmt(ti)}</span>
        <span class="badge badge-expense">-${fmt(te)}</span>
        <span class="badge ${net>=0?'badge-net-pos':'badge-net-neg'}">${net>=0?'✅':'⚠️'} ${fmt(net)}</span>
      </div>
      <div style="margin-top:8px"><button class="btn btn-outline btn-sm" onclick="showEventDetail('${ev.id}')">📋 รายละเอียด</button></div>
    </div>`;
  }).join('');
}

function showEventDetail(id){
  const ev=events.find(e=>e.id===id); if(!ev)return;
  const recs=records.filter(r=>r.eventId===id).sort((a,b)=>a.date.localeCompare(b.date));
  const ti=recs.filter(r=>r.type==='income').reduce((s,r)=>s+r.amount,0);
  const te=recs.filter(r=>r.type==='expense').reduce((s,r)=>s+r.amount,0);
  const net=ti-te;
  const byDate={};
  recs.forEach(r=>{if(!byDate[r.date])byDate[r.date]=[];byDate[r.date].push(r);});
  let html=`<div style="font-size:12px;color:var(--muted);margin-bottom:12px">📅 ${ev.start} → ${ev.end}${ev.location?' | 📍'+ev.location:''}${ev.note?'<br>📝 '+ev.note:''}</div>`;
  Object.keys(byDate).sort().forEach(date=>{
    const dr=byDate[date];
    const di=dr.filter(r=>r.type==='income').reduce((s,r)=>s+r.amount,0);
    const de=dr.filter(r=>r.type==='expense').reduce((s,r)=>s+r.amount,0);
    html+=`<div class="day-block"><div class="day-block-head"><span class="dl">📅 ${date}</span><span>+${fmt(di)} / -${fmt(de)}</span></div><div class="day-block-body">
      ${dr.map(r=>`<div class="record-item"><div><div class="record-label">${r.type==='income'?'💰':'💸'} ${r.category}</div>${r.note?`<div class="record-note">${r.note}</div>`:''}</div><div style="display:flex;align-items:center;gap:6px"><span class="record-amount ${r.type}">${r.type==='income'?'+':'-'}${fmt(r.amount)}</span><button class="btn-danger-sm" onclick="deleteRecordFromDetail('${r.id}','${id}')">×</button></div></div>`).join('')}
    </div></div>`;
  });
  html+=`<div style="background:var(--primary-light);border-radius:10px;padding:12px;margin-top:10px">
    <div class="summary-row"><span class="lbl">รายรับรวม</span><span class="val-inc">${fmt(ti)}</span></div>
    <div class="summary-row"><span class="lbl">รายจ่ายรวม</span><span class="val-exp">${fmt(te)}</span></div>
    <div class="summary-row total"><span>กำไรสุทธิ</span><span class="${net>=0?'val-pos':'val-neg'}">${fmt(net)}</span></div>
  </div>`;
  document.getElementById('modal-detail-name').textContent=ev.name;
  document.getElementById('modal-detail-body').innerHTML=html;
  openModal('modal-detail');
}

// ══════════════════════════════════════
// RECORDS CRUD
// ══════════════════════════════════════
function initRecordPage(){ populateSelects(); renderDailyRecords(); }

function populateSelects(){
  const sel=document.getElementById('rec-event');
  const cur=sel.value;
  const dashEv=document.getElementById('dash-event');
  sel.innerHTML='<option value="">-- เลือก Event --</option>';
  dashEv.innerHTML='<option value="">-- ทุก Event --</option>';
  [...events].sort((a,b)=>b.start.localeCompare(a.start)).forEach(ev=>{
    sel.innerHTML+=`<option value="${ev.id}">${ev.name} (${ev.start})</option>`;
    dashEv.innerHTML+=`<option value="${ev.id}">${ev.name}</option>`;
  });
  if(cur) sel.value=cur;
}

function onRecordEventChange(){
  const id=document.getElementById('rec-event').value;
  document.getElementById('rec-date-wrap').style.display=id?'block':'none';
  document.getElementById('rec-entry').style.display=id?'block':'none';
  if(!id)return;
  const ev=events.find(e=>e.id===id);
  const di=document.getElementById('rec-date');
  di.value=today(); if(ev){di.min=ev.start;di.max=ev.end;}
  renderDailyRecords();
}

function renderDailyRecords(){
  const eventId=document.getElementById('rec-event').value;
  const date=document.getElementById('rec-date')?.value||today();
  document.getElementById('daily-date-lbl').textContent=date;
  const recs=records.filter(r=>r.eventId===eventId&&r.date===date);
  const list=document.getElementById('daily-list');
  list.innerHTML=recs.length
    ? recs.map(r=>`<div class="record-item"><div><div class="record-label">${r.type==='income'?'💰':'💸'} ${r.category}</div>${r.note?`<div class="record-note">${r.note}</div>`:''}</div><div style="display:flex;align-items:center;gap:6px"><span class="record-amount ${r.type}">${r.type==='income'?'+':'-'}${fmt(r.amount)}</span><button class="btn-danger-sm" onclick="deleteRecord('${r.id}')">×</button></div></div>`).join('')
    : '<div class="empty" style="padding:14px"><p>ยังไม่มีรายการ</p></div>';
  const ti=recs.filter(r=>r.type==='income').reduce((s,r)=>s+r.amount,0);
  const te=recs.filter(r=>r.type==='expense').reduce((s,r)=>s+r.amount,0);
  const net=ti-te;
  document.getElementById('ds-inc').textContent=fmt(ti);
  document.getElementById('ds-exp').textContent=fmt(te);
  const nEl=document.getElementById('ds-net');
  nEl.textContent=fmt(net); nEl.className=net>=0?'val-pos':'val-neg';
}

async function addRecord(type){
  const eventId=document.getElementById('rec-event').value;
  if(!eventId){showToast('กรุณาเลือก Event ก่อน',false);return;}
  const amtEl=document.getElementById(type==='income'?'inc-amt':'exp-amt');
  const catEl=document.getElementById(type==='income'?'inc-cat':'exp-cat');
  const noteEl=document.getElementById(type==='income'?'inc-note':'exp-note');
  const amount=parseFloat(amtEl.value);
  if(!amount||amount<=0){showToast('กรุณากรอกจำนวนเงิน',false);return;}
  const btnId=type==='income'?'btn-add-inc':'btn-add-exp';
  const btn=document.getElementById(btnId);
  btn.disabled=true; btn.innerHTML='<span class="spinner"></span>บันทึก...';
  const rec={id:uid(),eventId,type,amount,category:catEl.value,note:noteEl.value,date:document.getElementById('rec-date').value||today(),createdAt:new Date().toISOString()};
  try{
    await appendRow('Records',[rec.id,rec.eventId,rec.type,rec.amount,rec.category,rec.note,rec.date,rec.createdAt]);
    records.push(rec);
    amtEl.value=''; noteEl.value='';
    renderDailyRecords();
    showToast(type==='income'?'✅ เพิ่มรายรับแล้ว':'✅ เพิ่มรายจ่ายแล้ว');
    setSS('ss-rec','✅ บันทึกลง Sheet แล้ว','ok');
  }catch(e){ showToast('❌ '+e.message,false); setSS('ss-rec','❌ '+e.message,'err'); }
  btn.disabled=false;
  btn.innerHTML=type==='income'?'+ เพิ่มรายรับ':'+ เพิ่มรายจ่าย';
}

async function deleteRecord(id){
  try{
    const rowIdx=await findRowIndex('Records',id);
    if(rowIdx>-1) await deleteSheetRow('Records',rowIdx);
    records=records.filter(r=>r.id!==id);
    renderDailyRecords(); showToast('🗑️ ลบรายการแล้ว');
  }catch(e){ showToast('❌ '+e.message,false); }
}

async function deleteRecordFromDetail(id,eventId){
  await deleteRecord(id); showEventDetail(eventId);
}

// ══════════════════════════════════════
// DASHBOARD
// ══════════════════════════════════════
function initMonthFilter(){
  const sel=document.getElementById('dash-month');
  const months=new Set(records.map(r=>r.date.slice(0,7)));
  months.add(today().slice(0,7));
  const cur=sel.value;
  sel.innerHTML=[...months].sort().reverse().map(m=>`<option value="${m}">${m}</option>`).join('');
  if(cur) sel.value=cur;
}

function renderDashboard(){
  initMonthFilter();
  const type=document.getElementById('dash-type').value;
  document.getElementById('dash-month').style.display=type==='month'?'block':'none';
  document.getElementById('dash-event').style.display=type==='event'?'block':'none';
  let filtered=records,labels=[],incData=[],expData=[];
  if(type==='month'){
    const month=document.getElementById('dash-month').value||today().slice(0,7);
    filtered=records.filter(r=>r.date.startsWith(month));
  } else {
    const evId=document.getElementById('dash-event').value;
    if(evId) filtered=records.filter(r=>r.eventId===evId);
  }
  const days={};
  filtered.forEach(r=>{if(!days[r.date])days[r.date]={inc:0,exp:0};if(r.type==='income')days[r.date].inc+=r.amount;else days[r.date].exp+=r.amount;});
  labels=Object.keys(days).sort();
  incData=labels.map(d=>days[d].inc); expData=labels.map(d=>days[d].exp);
  const ti=filtered.filter(r=>r.type==='income').reduce((s,r)=>s+r.amount,0);
  const te=filtered.filter(r=>r.type==='expense').reduce((s,r)=>s+r.amount,0);
  const net=ti-te;
  document.getElementById('k-income').textContent=fmt(ti);
  document.getElementById('k-expense').textContent=fmt(te);
  document.getElementById('k-net').textContent=fmt(net);
  document.getElementById('k-net').style.color=net>=0?'var(--net)':'var(--expense)';
  const ctx=document.getElementById('dash-chart').getContext('2d');
  if(dashChart){dashChart.destroy();dashChart=null;}
  if(labels.length){
    dashChart=new Chart(ctx,{
      type:'bar',
      data:{labels:labels.map(l=>l.slice(5)),datasets:[
        {label:'รายรับ',data:incData,backgroundColor:'rgba(16,185,129,.75)',borderRadius:6},
        {label:'รายจ่าย',data:expData,backgroundColor:'rgba(239,68,68,.75)',borderRadius:6}
      ]},
      options:{responsive:true,maintainAspectRatio:false,
        plugins:{legend:{position:'top',labels:{font:{size:11}}},tooltip:{callbacks:{label:c=>fmt(c.raw)}}},
        scales:{y:{ticks:{callback:v=>'฿'+v.toLocaleString()},grid:{color:'rgba(0,0,0,.05)'}}}}
    });
  }
  const list=document.getElementById('dash-list');
  if(!filtered.length){list.innerHTML='<div class="empty"><div class="icon">📭</div><p>ไม่มีข้อมูล</p></div>';return;}
  list.innerHTML=[...filtered].sort((a,b)=>b.date.localeCompare(a.date)).slice(0,30)
    .map(r=>`<div class="record-item"><div><div class="record-label">${r.type==='income'?'💰':'💸'} ${r.category}</div><div class="record-date">${r.date}${r.note?' · '+r.note:''}</div></div><span class="record-amount ${r.type}">${r.type==='income'?'+':'-'}${fmt(r.amount)}</span></div>`).join('');
}

// ══════════════════════════════════════
// BOOT
// ══════════════════════════════════════
async function boot(){
  showLoading('กำลังตรวจสอบการเข้าสู่ระบบ...');

  // 1. ลอง parse token จาก URL hash (กลับมาจาก Google redirect)
  let token = parseTokenFromHash();

  // 2. ถ้าไม่มี ลองใช้ token ที่บันทึกไว้
  if(!token) token = getSavedToken();

  if(!token){
    showLogin();
    return;
  }

  accessToken = token;
  showLoading('กำลังโหลดข้อมูล...');

  try{
    await fetchUserProfile();
    showApp();
    await initSheet();
    await loadAllData();
  }catch(e){
    showToast('❌ '+e.message, false);
    showLogin();
  }
}

let resizeTimer;
window.addEventListener('resize',()=>{
  clearTimeout(resizeTimer);
  resizeTimer=setTimeout(()=>{if(document.getElementById('page-dashboard').classList.contains('active'))renderDashboard();},150);
});

boot();
</script>
</body>
</html>
