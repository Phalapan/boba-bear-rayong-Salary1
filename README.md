#Babobear
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
  --ice:#3B82F6;--ice-light:#DBEAFE;
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
.kpi-card.ice{background:var(--ice-light)}
.kpi-card.net{background:var(--net-light);grid-column:1/-1}
.kpi-label{font-size:11px;color:var(--muted);font-weight:600;margin-bottom:4px}
.kpi-value{font-size:19px;font-weight:800}
.kpi-card.income .kpi-value{color:var(--income)}
.kpi-card.expense .kpi-value{color:var(--expense)}
.kpi-card.ice .kpi-value{color:var(--ice)}
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
.filter-bar{display:flex;gap:8px;margin-bottom:13px;flex-wrap:wrap;align-items:center}
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
.cat-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px;align-items:center}
.cat-legend-item{display:flex;align-items:flex-start;gap:6px;font-size:11px;margin-bottom:6px}
.cat-dot{width:10px;height:10px;border-radius:50%;flex-shrink:0;margin-top:2px}
.cat-legend-label{font-weight:700;color:var(--text)}
.cat-legend-val{color:var(--muted);font-size:10px}
.cat-table{width:100%;border-collapse:collapse;font-size:12px;margin-top:8px}
.cat-table th{text-align:left;padding:6px 8px;background:var(--primary-light);color:var(--primary);font-weight:700;font-size:11px}
.cat-table th:last-child{text-align:right}
.cat-table td{padding:7px 8px;border-bottom:1px solid var(--border);vertical-align:top}
.cat-table td:last-child{text-align:right;font-weight:700;white-space:nowrap}
.cat-table tr:last-child td{border-bottom:none}
.note-pill{display:inline-block;border-radius:10px;padding:2px 7px;font-size:10px;margin:2px 2px 0 0}
.note-pill.inc{background:var(--income-light);color:var(--income)}
.note-pill.exp{background:var(--expense-light);color:var(--expense)}
.note-pill.ice{background:var(--ice-light);color:var(--ice)}
/* detail dashboard */
.detail-day-block{border:1.5px solid var(--border);border-radius:12px;margin-bottom:12px;overflow:hidden}
.detail-day-head{background:linear-gradient(135deg,var(--primary),#5B21B6);color:#fff;padding:10px 14px;display:flex;justify-content:space-between;align-items:center}
.detail-day-head .date-lbl{font-weight:800;font-size:13px}
.detail-day-head .day-net{font-size:12px;opacity:.9}
.detail-section{padding:10px 14px;border-bottom:1px solid var(--border)}
.detail-section:last-child{border-bottom:none}
.detail-section-title{font-size:11px;font-weight:800;margin-bottom:8px;text-transform:uppercase;letter-spacing:.5px}
.detail-row{display:flex;justify-content:space-between;align-items:flex-start;padding:5px 0;border-bottom:1px dashed var(--border);font-size:12px}
.detail-row:last-child{border-bottom:none}
.detail-row-cat{font-weight:700;flex:1}
.detail-row-note{font-size:10px;color:var(--muted);font-style:italic;margin-top:2px}
.detail-row-amt{font-weight:800;white-space:nowrap;margin-left:8px}
.detail-row-amt.inc{color:var(--income)}
.detail-row-amt.exp{color:var(--expense)}
.detail-row-amt.ice{color:var(--ice)}
.detail-total-row{display:flex;justify-content:space-between;padding:8px 14px;font-size:12px;font-weight:700;background:#f9fafb}
/* ice highlight */
.ice-tag{display:inline-block;background:var(--ice-light);color:var(--ice);border-radius:8px;padding:1px 6px;font-size:10px;font-weight:700;margin-left:4px}
@media(max-width:360px){.kpi-grid{grid-template-columns:1fr}.row2{grid-template-columns:1fr}.cat-grid{grid-template-columns:1fr}}
</style>
</head>
<body>

<div id="loading-overlay" class="loading-overlay">
  <div class="big-spinner"></div>
  <div id="loading-text">กำลังตรวจสอบการเข้าสู่ระบบ...</div>
</div>

<div id="login-screen" class="login-screen" style="display:none">
  <div class="login-card">
    <div class="logo">🧋</div>
    <h2>Boba Bear Rayong</h2>
    <p>ระบบบันทึกรายรับ-รายจ่าย<br>ร้านชานมไข่มุก<br><br>เข้าสู่ระบบด้วย Google เพื่อซิงค์ข้อมูลกับ Google Sheets</p>
    <a href="#" class="btn-google" onclick="handleSignIn(event)">
      <img src="https://www.gstatic.com/firebasejs/ui/2.0.0/images/auth/google.svg" alt="G"/>
      เข้าสู่ระบบด้วย Google
    </a>
  </div>
</div>

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
    <button class="nav-tab" data-page="detail">📋 Detail</button>
    <button class="nav-tab" data-page="events">🎪 งาน</button>
    <button class="nav-tab" data-page="record">✏️ บันทึก</button>
  </div>

  <!-- ══ DASHBOARD ══ -->
  <div class="page active" id="page-dashboard">
    <div class="filter-bar" style="margin-top:8px">
      <select id="dash-type" onchange="onDashTypeChange()">
        <option value="day">📅 รายวัน</option>
        <option value="month">📆 รายเดือน</option>
        <option value="event">🎪 รายงาน Event</option>
      </select>
      <select id="dash-day" onchange="renderDashboard()"></select>
      <select id="dash-month" style="display:none" onchange="renderDashboard()"></select>
      <select id="dash-event" style="display:none" onchange="onDashEventChange()">
        <option value="">-- ทั้งหมด --</option>
      </select>
      <select id="dash-event-day" style="display:none" onchange="renderDashboard()">
        <option value="">-- ทุกวัน --</option>
      </select>
      <button class="btn btn-outline btn-sm" onclick="loadAllData()" style="white-space:nowrap">🔄</button>
    </div>

    <div class="kpi-grid">
      <div class="kpi-card income"><div class="kpi-label">💰 รายรับรวม</div><div class="kpi-value" id="k-income">฿0</div></div>
      <div class="kpi-card expense"><div class="kpi-label">💸 รายจ่ายรวม</div><div class="kpi-value" id="k-expense">฿0</div></div>
      <div class="kpi-card ice" style="grid-column:unset"><div class="kpi-label">🧊 ค่าน้ำแข็ง</div><div class="kpi-value" id="k-ice">฿0</div></div>
      <div class="kpi-card net"><div class="kpi-label">📈 กำไรสุทธิ</div><div class="kpi-value" id="k-net">฿0</div></div>
    </div>

    <div class="card">
      <div class="card-title">📊 รายรับ-รายจ่าย</div>
      <div class="chart-wrap"><canvas id="dash-chart"></canvas></div>
    </div>

    <div class="card">
      <div class="card-title" style="color:var(--income)">💰 รายรับ แยกหมวดหมู่</div>
      <div class="cat-grid">
        <div class="chart-wrap" style="height:180px"><canvas id="chart-inc-cat"></canvas></div>
        <div id="inc-cat-legend"></div>
      </div>
      <div id="inc-cat-table"></div>
    </div>

    <div class="card">
      <div class="card-title" style="color:var(--expense)">💸 รายจ่าย แยกหมวดหมู่ <span class="ice-tag">🧊 แยกน้ำแข็ง</span></div>
      <div class="cat-grid">
        <div class="chart-wrap" style="height:180px"><canvas id="chart-exp-cat"></canvas></div>
        <div id="exp-cat-legend"></div>
      </div>
      <div id="exp-cat-table"></div>
    </div>

    <div class="card">
      <div class="card-title">📋 รายการล่าสุด</div>
      <div id="dash-list"></div>
    </div>
    <div class="sync-status" id="ss-dash"></div>
  </div>

  <!-- ══ DETAIL DASHBOARD ══ -->
  <div class="page" id="page-detail">
    <div class="filter-bar" style="margin-top:8px">
      <select id="det-event" onchange="onDetEventChange()">
        <option value="">-- ทุก Event --</option>
      </select>
      <select id="det-day" onchange="renderDetail()">
        <option value="">-- ทุกวัน --</option>
      </select>
      <button class="btn btn-outline btn-sm" onclick="renderDetail()" style="white-space:nowrap">🔄</button>
    </div>
    <div id="detail-container"></div>
    <div class="sync-status" id="ss-detail"></div>
  </div>

  <!-- ══ EVENTS ══ -->
  <div class="page" id="page-events">
    <div style="display:flex;justify-content:space-between;align-items:center;margin:4px 0 12px">
      <strong style="font-size:15px">🎪 งาน / Events</strong>
      <button class="btn btn-primary btn-sm" onclick="openNewEventModal()">+ เพิ่มงาน</button>
    </div>
    <div id="event-list"></div>
    <div class="sync-status" id="ss-events"></div>
  </div>

  <!-- ══ RECORD ══ -->
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
            <select id="exp-cat"><option>ค่าวัตถุดิบ</option><option>ค่าน้ำแข็ง</option><option>ค่าเดินทาง</option><option>ค่าเช่าพื้นที่</option><option>ค่าบรรจุภัณฑ์</option><option>ค่าไฟ/น้ำ</option><option>อื่นๆ</option></select>
          </div>
        </div>
        <div class="form-row"><label>หมายเหตุ</label><input type="text" id="exp-note" placeholder="เช่น ซื้อชาไทย"/></div>
        <button class="btn btn-expense" id="btn-add-exp" onclick="addRecord('expense')" style="width:100%">+ เพิ่มรายจ่าย</button>
      </div>
      <div class="card">
        <div class="card-title">📋 รายการวันนี้ (<span id="daily-date-lbl">-</span>)</div>
        <div id="daily-list"></div>
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

<!-- MODAL EVENT -->
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
    <div class="form-row"><label>สถานที่</label><input type="text" id="ev-loc"/></div>
    <div class="form-row"><label>หมายเหตุ</label><textarea id="ev-note"></textarea></div>
    <div class="btn-row" style="margin-top:14px">
      <button class="btn btn-primary" id="btn-save-ev" onclick="saveEvent()" style="flex:1">💾 บันทึก</button>
      <button class="btn btn-outline" onclick="closeModal('modal-event')">ยกเลิก</button>
    </div>
  </div>
</div>

<!-- MODAL DETAIL -->
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
// ════════════════════════════════
// CONFIG
// ════════════════════════════════
const CLIENT_ID    = '287915428157-u1b12rguf2l7o4tmuku7g3jhmq5sdbat.apps.googleusercontent.com';
const REDIRECT_URI = 'https://phalapan.github.io/boba-bear-rayong-Salary1/';
const SCOPES       = 'https://www.googleapis.com/auth/spreadsheets https://www.googleapis.com/auth/drive.file https://www.googleapis.com/auth/userinfo.profile';
const SHEET_ID     = '1gqtRRYzw2hZteJBosRhqhdcq7M9YtsVesbQubzMy67w';

// ════════════════════════════════
// STATE
// ════════════════════════════════
let accessToken = null;
let spreadsheetId = SHEET_ID;
let events = [], records = [];
let dashChart=null, incCatChart=null, expCatChart=null;

const COLORS_INC = ['#10B981','#34D399','#059669','#6EE7B7','#047857','#A7F3D0','#065F46','#BBF7D0'];
const COLORS_EXP = ['#EF4444','#F87171','#DC2626','#FCA5A5','#B91C1C','#FECACA','#991B1B','#FEE2E2'];
const COLOR_ICE  = '#3B82F6';

// ════════════════════════════════
// UTILS
// ════════════════════════════════
function uid(){ return Date.now().toString(36)+Math.random().toString(36).slice(2,7); }
function fmt(n){ return '฿'+(n||0).toLocaleString('th-TH',{minimumFractionDigits:2,maximumFractionDigits:2}); }
function today(){ return new Date().toISOString().slice(0,10); }
function isIce(r){ return r.type==='expense' && (r.category||'').includes('น้ำแข็ง'); }

function showToast(msg,ok=true){
  const t=document.getElementById('toast');
  t.textContent=msg; t.style.background=ok?'#065F46':'#991B1B';
  t.classList.add('show'); setTimeout(()=>t.classList.remove('show'),2800);
}
function setSS(id,msg,cls=''){const el=document.getElementById(id);if(!el)return;el.textContent=msg;el.className='sync-status '+(cls||'');}
function closeModal(id){document.getElementById(id).classList.remove('open');}
function openModal(id){document.getElementById(id).classList.add('open');}
function showLoading(msg=''){document.getElementById('loading-overlay').style.display='flex';if(msg)document.getElementById('loading-text').textContent=msg;}
function hideLoading(){document.getElementById('loading-overlay').style.display='none';}
function showLogin(){document.getElementById('login-screen').style.display='flex';hideLoading();}
function showApp(){document.getElementById('app-shell').style.display='block';document.getElementById('login-screen').style.display='none';hideLoading();}

// ════════════════════════════════
// OAUTH
// ════════════════════════════════
function buildAuthUrl(){
  return 'https://accounts.google.com/o/oauth2/v2/auth?'+new URLSearchParams({
    client_id:CLIENT_ID,redirect_uri:REDIRECT_URI,
    response_type:'token',scope:SCOPES,
    include_granted_scopes:'true',state:'boba_auth'
  }).toString();
}
function handleSignIn(e){e.preventDefault();window.location.href=buildAuthUrl();}
function handleSignOut(){
  if(accessToken)fetch('https://oauth2.googleapis.com/revoke?token='+accessToken,{method:'POST'}).catch(()=>{});
  accessToken=null;
  localStorage.removeItem('boba_token');localStorage.removeItem('boba_token_exp');
  document.getElementById('app-shell').style.display='none';
  showLogin();showToast('ออกจากระบบแล้ว');
}
function parseTokenFromHash(){
  const hash=window.location.hash.substring(1);if(!hash)return null;
  const p=new URLSearchParams(hash);
  if(p.get('state')!=='boba_auth')return null;
  const token=p.get('access_token');if(!token)return null;
  localStorage.setItem('boba_token',token);
  localStorage.setItem('boba_token_exp',(Date.now()+(parseInt(p.get('expires_in'))||3600)*1000).toString());
  history.replaceState(null,'',window.location.pathname);
  return token;
}
function getSavedToken(){
  const token=localStorage.getItem('boba_token');
  const exp=localStorage.getItem('boba_token_exp');
  if(!token||!exp||Date.now()>parseInt(exp)-60000)return null;
  return token;
}

// ════════════════════════════════
// API
// ════════════════════════════════
async function gFetch(url,options={}){
  const res=await fetch(url,{...options,headers:{'Authorization':'Bearer '+accessToken,'Content-Type':'application/json',...(options.headers||{})}});
  if(res.status===401){handleSignOut();throw new Error('Token หมดอายุ');}
  return res.json();
}
async function fetchUserProfile(){
  try{const u=await gFetch('https://www.googleapis.com/oauth2/v3/userinfo');
    document.getElementById('user-name').textContent=u.name||u.email||'';
    document.getElementById('user-avatar').src=u.picture||'';
  }catch(e){}
}
async function ensureHeaders(){
  const ev=await gFetch(`https://sheets.googleapis.com/v4/spreadsheets/${spreadsheetId}/values/Events!A1`);
  if(!ev.values)await gFetch(`https://sheets.googleapis.com/v4/spreadsheets/${spreadsheetId}/values/Events!A1?valueInputOption=RAW`,{method:'PUT',body:JSON.stringify({values:[['id','name','start','end','location','note','updatedAt']]})});
  const rec=await gFetch(`https://sheets.googleapis.com/v4/spreadsheets/${spreadsheetId}/values/Records!A1`);
  if(!rec.values)await gFetch(`https://sheets.googleapis.com/v4/spreadsheets/${spreadsheetId}/values/Records!A1?valueInputOption=RAW`,{method:'PUT',body:JSON.stringify({values:[['id','eventId','type','amount','category','note','date','createdAt']]})});
}
async function loadAllData(){
  setSS('ss-dash','⏳ กำลังโหลด...','ing');
  try{
    const [evRes,recRes]=await Promise.all([
      gFetch(`https://sheets.googleapis.com/v4/spreadsheets/${spreadsheetId}/values/Events!A2:G`),
      gFetch(`https://sheets.googleapis.com/v4/spreadsheets/${spreadsheetId}/values/Records!A2:H`)
    ]);
    events=(evRes.values||[]).filter(r=>r[0]).map(r=>({id:r[0],name:r[1],start:r[2],end:r[3],location:r[4]||'',note:r[5]||'',updatedAt:r[6]||''}));
    records=(recRes.values||[]).filter(r=>r[0]).map(r=>({id:r[0],eventId:r[1],type:r[2],amount:parseFloat(r[3])||0,category:r[4],note:r[5]||'',date:r[6],createdAt:r[7]||''}));
    populateAllSelects();
    renderEventList();
    renderDashboard();
    renderDetail();
    setSS('ss-dash','✅ โหลดแล้ว '+new Date().toLocaleTimeString('th-TH'),'ok');
  }catch(e){setSS('ss-dash','❌ '+e.message,'err');}
}
async function appendRow(sheet,values){
  await gFetch(`https://sheets.googleapis.com/v4/spreadsheets/${spreadsheetId}/values/${sheet}!A1:append?valueInputOption=RAW&insertDataOption=INSERT_ROWS`,{method:'POST',body:JSON.stringify({values:[values]})});
}
async function findRowIndex(sheet,id){
  const res=await gFetch(`https://sheets.googleapis.com/v4/spreadsheets/${spreadsheetId}/values/${sheet}!A:A`);
  const rows=res.values||[];
  for(let i=0;i<rows.length;i++)if(rows[i][0]===id)return i+1;
  return -1;
}
async function updateRow(sheet,rowIdx,values){
  const col=String.fromCharCode(64+values.length);
  await gFetch(`https://sheets.googleapis.com/v4/spreadsheets/${spreadsheetId}/values/${sheet}!A${rowIdx}:${col}${rowIdx}?valueInputOption=RAW`,{method:'PUT',body:JSON.stringify({values:[values]})});
}
async function deleteSheetRow(sheet,rowIdx){
  const meta=await gFetch(`https://sheets.googleapis.com/v4/spreadsheets/${spreadsheetId}?fields=sheets.properties`);
  const sh=meta.sheets.find(s=>s.properties.title===sheet);if(!sh)return;
  await gFetch(`https://sheets.googleapis.com/v4/spreadsheets/${spreadsheetId}:batchUpdate`,{method:'POST',body:JSON.stringify({requests:[{deleteDimension:{range:{sheetId:sh.properties.sheetId,dimension:'ROWS',startIndex:rowIdx-1,endIndex:rowIdx}}}]})});
}

// ════════════════════════════════
// NAV
// ════════════════════════════════
document.querySelectorAll('.nav-tab').forEach(btn=>{
  btn.addEventListener('click',()=>{
    document.querySelectorAll('.nav-tab').forEach(b=>b.classList.remove('active'));
    document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
    btn.classList.add('active');
    document.getElementById('page-'+btn.dataset.page).classList.add('active');
    if(btn.dataset.page==='dashboard')renderDashboard();
    if(btn.dataset.page==='detail')renderDetail();
    if(btn.dataset.page==='events')renderEventList();
    if(btn.dataset.page==='record')initRecordPage();
  });
});

// ════════════════════════════════
// SELECTS POPULATE
// ════════════════════════════════
function populateAllSelects(){
  const sorted=[...events].sort((a,b)=>b.start.localeCompare(a.start));

  // rec-event
  const recSel=document.getElementById('rec-event');
  const recCur=recSel.value;
  recSel.innerHTML='<option value="">-- เลือก Event --</option>';
  sorted.forEach(ev=>recSel.innerHTML+=`<option value="${ev.id}">${ev.name} (${ev.start})</option>`);
  if(recCur)recSel.value=recCur;

  // dash-event
  const dashEv=document.getElementById('dash-event');
  dashEv.innerHTML='<option value="">-- ทั้งหมด --</option>';
  sorted.forEach(ev=>dashEv.innerHTML+=`<option value="${ev.id}">${ev.name}</option>`);

  // det-event
  const detEv=document.getElementById('det-event');
  const detCur=detEv.value;
  detEv.innerHTML='<option value="">-- ทุก Event --</option>';
  sorted.forEach(ev=>detEv.innerHTML+=`<option value="${ev.id}">${ev.name}</option>`);
  if(detCur)detEv.value=detCur;

  // dash-day filter
  initDashDayFilter();
  initDashMonthFilter();
}

function initDashDayFilter(){
  const sel=document.getElementById('dash-day');
  const cur=sel.value;
  const days=[...new Set(records.map(r=>r.date))].sort().reverse();
  if(!days.includes(today()))days.unshift(today());
  sel.innerHTML=days.map(d=>`<option value="${d}">${d}</option>`).join('');
  if(cur&&days.includes(cur))sel.value=cur;
}

function initDashMonthFilter(){
  const sel=document.getElementById('dash-month');
  const cur=sel.value;
  const months=[...new Set(records.map(r=>r.date.slice(0,7)))].sort().reverse();
  const thisMonth=today().slice(0,7);
  if(!months.includes(thisMonth))months.unshift(thisMonth);
  sel.innerHTML=months.map(m=>`<option value="${m}">${m}</option>`).join('');
  if(cur&&months.includes(cur))sel.value=cur;
}

function populateDashEventDayFilter(eventId){
  const sel=document.getElementById('dash-event-day');
  const recs=eventId?records.filter(r=>r.eventId===eventId):records;
  const days=[...new Set(recs.map(r=>r.date))].sort().reverse();
  sel.innerHTML='<option value="">-- ทุกวัน --</option>';
  days.forEach(d=>sel.innerHTML+=`<option value="${d}">${d}</option>`);
}

function populateDetDayFilter(eventId){
  const sel=document.getElementById('det-day');
  const recs=eventId?records.filter(r=>r.eventId===eventId):records;
  const days=[...new Set(recs.map(r=>r.date))].sort().reverse();
  sel.innerHTML='<option value="">-- ทุกวัน --</option>';
  days.forEach(d=>sel.innerHTML+=`<option value="${d}">${d}</option>`);
}

// ════════════════════════════════
// DASHBOARD FILTER LOGIC
// ════════════════════════════════
function onDashTypeChange(){
  const type=document.getElementById('dash-type').value;
  document.getElementById('dash-day').style.display=type==='day'?'block':'none';
  document.getElementById('dash-month').style.display=type==='month'?'block':'none';
  document.getElementById('dash-event').style.display=type==='event'?'block':'none';
  document.getElementById('dash-event-day').style.display=type==='event'?'block':'none';
  renderDashboard();
}

function onDashEventChange(){
  const evId=document.getElementById('dash-event').value;
  populateDashEventDayFilter(evId);
  renderDashboard();
}

function getFilteredRecords(){
  const type=document.getElementById('dash-type').value;
  if(type==='day'){
    const day=document.getElementById('dash-day').value||today();
    return records.filter(r=>r.date===day);
  } else if(type==='month'){
    const month=document.getElementById('dash-month').value||today().slice(0,7);
    return records.filter(r=>r.date.startsWith(month));
  } else {
    const evId=document.getElementById('dash-event').value;
    const day=document.getElementById('dash-event-day').value;
    let filtered=evId?records.filter(r=>r.eventId===evId):[...records];
    if(day)filtered=filtered.filter(r=>r.date===day);
    return filtered;
  }
}

// ════════════════════════════════
// DASHBOARD RENDER
// ════════════════════════════════
function groupByCategory(recs){
  const map={};
  recs.forEach(r=>{
    const key=r.category||'อื่นๆ';
    if(!map[key])map[key]={cat:key,total:0,notes:[]};
    map[key].total+=r.amount;
    if(r.note&&!map[key].notes.includes(r.note))map[key].notes.push(r.note);
  });
  return Object.values(map).sort((a,b)=>b.total-a.total);
}

// แยกน้ำแข็งออกจากรายจ่าย
function splitIceFromExpense(expRecs){
  const iceRecs=expRecs.filter(r=>isIce(r));
  const normalRecs=expRecs.filter(r=>!isIce(r));
  return {iceRecs,normalRecs};
}

function renderCatChart(canvasId,catData,colors){
  const ctx=document.getElementById(canvasId)?.getContext('2d');
  if(!ctx)return null;
  return new Chart(ctx,{
    type:'doughnut',
    data:{
      labels:catData.map(d=>d.cat),
      datasets:[{data:catData.map(d=>d.total),backgroundColor:colors.slice(0,catData.length),borderWidth:2,borderColor:'#fff'}]
    },
    options:{responsive:true,maintainAspectRatio:false,
      plugins:{legend:{display:false},
        tooltip:{callbacks:{label:c=>{
          const total=catData.reduce((s,d)=>s+d.total,0);
          return ` ${fmt(c.raw)} (${total?Math.round(c.raw/total*100):0}%)`;
        }}}
      }
    }
  });
}

function renderCatLegend(containerId,catData,colors){
  const total=catData.reduce((s,d)=>s+d.total,0);
  document.getElementById(containerId).innerHTML=catData.map((d,i)=>`
    <div class="cat-legend-item">
      <div class="cat-dot" style="background:${colors[i%colors.length]}"></div>
      <div>
        <div class="cat-legend-label">${d.cat}</div>
        <div class="cat-legend-val">${fmt(d.total)} · ${total?Math.round(d.total/total*100):0}%</div>
      </div>
    </div>`).join('');
}

function renderCatTable(containerId,catData,cssType){
  if(!catData.length){document.getElementById(containerId).innerHTML='';return;}
  const total=catData.reduce((s,d)=>s+d.total,0);
  const rows=catData.map(d=>{
    const pills=d.notes.map(n=>`<span class="note-pill ${cssType}">${n}</span>`).join('');
    const pct=total?Math.round(d.total/total*100):0;
    const isIceCat=d.cat.includes('น้ำแข็ง');
    return `<tr${isIceCat?' style="background:var(--ice-light)"':''}>
      <td><div style="font-weight:700">${d.cat}${isIceCat?' <span class="ice-tag">🧊</span>':''}</div>${pills?`<div style="margin-top:3px">${pills}</div>`:''}</td>
      <td><div>${fmt(d.total)}</div><div style="font-size:10px;color:var(--muted)">${pct}%</div></td>
    </tr>`;
  }).join('');
  document.getElementById(containerId).innerHTML=`
    <table class="cat-table">
      <thead><tr><th>หมวดหมู่ / หมายเหตุ</th><th>ยอด</th></tr></thead>
      <tbody>${rows}</tbody>
      <tfoot><tr style="background:var(--primary-light)"><td style="font-weight:800;color:var(--primary)">รวม</td><td style="font-weight:800;color:var(--primary);text-align:right">${fmt(total)}</td></tr></tfoot>
    </table>`;
}

function renderDashboard(){
  initDashDayFilter();
  initDashMonthFilter();
  const type=document.getElementById('dash-type').value;
  document.getElementById('dash-day').style.display=type==='day'?'block':'none';
  document.getElementById('dash-month').style.display=type==='month'?'block':'none';
  document.getElementById('dash-event').style.display=type==='event'?'block':'none';
  document.getElementById('dash-event-day').style.display=type==='event'?'block':'none';

  const filtered=getFilteredRecords();
  const ti=filtered.filter(r=>r.type==='income').reduce((s,r)=>s+r.amount,0);
  const te=filtered.filter(r=>r.type==='expense').reduce((s,r)=>s+r.amount,0);
  const tice=filtered.filter(r=>isIce(r)).reduce((s,r)=>s+r.amount,0);
  const net=ti-te;
  document.getElementById('k-income').textContent=fmt(ti);
  document.getElementById('k-expense').textContent=fmt(te);
  document.getElementById('k-ice').textContent=fmt(tice);
  document.getElementById('k-net').textContent=fmt(net);
  document.getElementById('k-net').style.color=net>=0?'var(--net)':'var(--expense)';

  // กราฟ bar
  const days={};
  filtered.forEach(r=>{if(!days[r.date])days[r.date]={inc:0,exp:0,ice:0};
    if(r.type==='income')days[r.date].inc+=r.amount;
    else if(isIce(r))days[r.date].ice+=r.amount;
    else days[r.date].exp+=r.amount;
  });
  const labels=Object.keys(days).sort();
  const ctx=document.getElementById('dash-chart').getContext('2d');
  if(dashChart){dashChart.destroy();dashChart=null;}
  if(labels.length){
    dashChart=new Chart(ctx,{
      type:'bar',
      data:{labels:labels.map(l=>l.slice(5)),datasets:[
        {label:'รายรับ',data:labels.map(d=>days[d].inc),backgroundColor:'rgba(16,185,129,.75)',borderRadius:6},
        {label:'รายจ่าย',data:labels.map(d=>days[d].exp),backgroundColor:'rgba(239,68,68,.75)',borderRadius:6},
        {label:'🧊 น้ำแข็ง',data:labels.map(d=>days[d].ice),backgroundColor:'rgba(59,130,246,.75)',borderRadius:6}
      ]},
      options:{responsive:true,maintainAspectRatio:false,
        plugins:{legend:{position:'top',labels:{font:{size:10}}},tooltip:{callbacks:{label:c=>fmt(c.raw)}}},
        scales:{y:{ticks:{callback:v=>'฿'+v.toLocaleString()},grid:{color:'rgba(0,0,0,.05)'}}}}
    });
  }

  // รายรับ หมวดหมู่
  const incRecs=filtered.filter(r=>r.type==='income');
  const incCat=groupByCategory(incRecs);
  if(incCatChart){incCatChart.destroy();incCatChart=null;}
  if(incCat.length){
    incCatChart=renderCatChart('chart-inc-cat',incCat,COLORS_INC);
    renderCatLegend('inc-cat-legend',incCat,COLORS_INC);
    renderCatTable('inc-cat-table',incCat,'inc');
  }else{
    document.getElementById('inc-cat-legend').innerHTML='<div class="empty" style="padding:10px"><p>ไม่มีข้อมูล</p></div>';
    document.getElementById('inc-cat-table').innerHTML='';
  }

  // รายจ่าย — แยกน้ำแข็งออก
  const expRecs=filtered.filter(r=>r.type==='expense');
  const {iceRecs,normalRecs}=splitIceFromExpense(expRecs);
  // รวมน้ำแข็งเป็น 1 กลุ่มพิเศษ
  const iceCatGroup=iceRecs.length?[{cat:'🧊 ค่าน้ำแข็ง',total:iceRecs.reduce((s,r)=>s+r.amount,0),notes:[...new Set(iceRecs.map(r=>r.note).filter(Boolean))]}]:[];
  const normalCat=groupByCategory(normalRecs);
  const expCat=[...normalCat,...iceCatGroup];
  const expColors=[...COLORS_EXP.slice(0,normalCat.length),COLOR_ICE];

  if(expCatChart){expCatChart.destroy();expCatChart=null;}
  if(expCat.length){
    expCatChart=renderCatChart('chart-exp-cat',expCat,expColors);
    renderCatLegend('exp-cat-legend',expCat,expColors);
    renderCatTable('exp-cat-table',expCat,'exp');
  }else{
    document.getElementById('exp-cat-legend').innerHTML='<div class="empty" style="padding:10px"><p>ไม่มีข้อมูล</p></div>';
    document.getElementById('exp-cat-table').innerHTML='';
  }

  // รายการล่าสุด
  const list=document.getElementById('dash-list');
  if(!filtered.length){list.innerHTML='<div class="empty"><div class="icon">📭</div><p>ไม่มีข้อมูล</p></div>';return;}
  list.innerHTML=[...filtered].sort((a,b)=>b.date.localeCompare(a.date)).slice(0,30)
    .map(r=>`<div class="record-item">
      <div style="flex:1">
        <div class="record-label">${r.type==='income'?'💰':isIce(r)?'🧊':'💸'} ${r.category}</div>
        <div class="record-date">${r.date}</div>
        ${r.note?`<div class="record-note">📝 ${r.note}</div>`:''}
      </div>
      <span class="record-amount ${r.type}" style="${isIce(r)?'color:var(--ice)':''}">${r.type==='income'?'+':'-'}${fmt(r.amount)}</span>
    </div>`).join('');
}

// ════════════════════════════════
// DETAIL DASHBOARD
// ════════════════════════════════
function onDetEventChange(){
  const evId=document.getElementById('det-event').value;
  populateDetDayFilter(evId);
  renderDetail();
}

function renderDetail(){
  const evId=document.getElementById('det-event').value;
  const day=document.getElementById('det-day').value;
  let filtered=evId?records.filter(r=>r.eventId===evId):[...records];
  if(day)filtered=filtered.filter(r=>r.date===day);

  const container=document.getElementById('detail-container');
  if(!filtered.length){container.innerHTML='<div class="empty"><div class="icon">📋</div><p>ไม่มีข้อมูล</p></div>';return;}

  // Group by date
  const byDate={};
  filtered.forEach(r=>{if(!byDate[r.date])byDate[r.date]=[];byDate[r.date].push(r);});
  const dates=Object.keys(byDate).sort().reverse();

  // รวมทั้งหมด
  const totalInc=filtered.filter(r=>r.type==='income').reduce((s,r)=>s+r.amount,0);
  const totalExp=filtered.filter(r=>r.type==='expense').reduce((s,r)=>s+r.amount,0);
  const totalIce=filtered.filter(r=>isIce(r)).reduce((s,r)=>s+r.amount,0);
  const totalNet=totalInc-totalExp;

  // Summary card
  let html=`<div class="card" style="background:linear-gradient(135deg,#7C3AED,#5B21B6);color:#fff">
    <div style="font-size:13px;font-weight:800;margin-bottom:10px">📊 สรุปรวม${evId?' — '+events.find(e=>e.id===evId)?.name:' — ทุก Event'}${day?' | '+day:''}</div>
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:8px">
      <div style="background:rgba(255,255,255,.15);border-radius:10px;padding:10px;text-align:center">
        <div style="font-size:10px;opacity:.8">💰 รายรับ</div>
        <div style="font-size:16px;font-weight:800">${fmt(totalInc)}</div>
      </div>
      <div style="background:rgba(255,255,255,.15);border-radius:10px;padding:10px;text-align:center">
        <div style="font-size:10px;opacity:.8">💸 รายจ่าย</div>
        <div style="font-size:16px;font-weight:800">${fmt(totalExp)}</div>
      </div>
      <div style="background:rgba(59,130,246,.4);border-radius:10px;padding:10px;text-align:center">
        <div style="font-size:10px;opacity:.8">🧊 น้ำแข็ง</div>
        <div style="font-size:16px;font-weight:800">${fmt(totalIce)}</div>
      </div>
      <div style="background:rgba(255,255,255,.25);border-radius:10px;padding:10px;text-align:center">
        <div style="font-size:10px;opacity:.8">📈 กำไรสุทธิ</div>
        <div style="font-size:16px;font-weight:800">${fmt(totalNet)}</div>
      </div>
    </div>
  </div>`;

  // แต่ละวัน
  dates.forEach(date=>{
    const dayRecs=byDate[date];
    const dInc=dayRecs.filter(r=>r.type==='income').reduce((s,r)=>s+r.amount,0);
    const dExp=dayRecs.filter(r=>r.type==='expense').reduce((s,r)=>s+r.amount,0);
    const dNet=dInc-dExp;
    const eventName=events.find(e=>e.id===dayRecs[0]?.eventId)?.name||'';

    // แยก income / expense / ice
    const incRecs=dayRecs.filter(r=>r.type==='income');
    const expRecsDay=dayRecs.filter(r=>r.type==='expense'&&!isIce(r));
    const iceRecsDay=dayRecs.filter(r=>isIce(r));

    // group by category
    const incCatDay=groupByCategory(incRecs);
    const expCatDay=groupByCategory(expRecsDay);
    const iceCatDay=groupByCategory(iceRecsDay);

    html+=`<div class="detail-day-block">
      <div class="detail-day-head">
        <div>
          <div class="date-lbl">📅 ${date}</div>
          ${eventName?`<div style="font-size:10px;opacity:.8">🎪 ${eventName}</div>`:''}
        </div>
        <div class="day-net">กำไร: ${fmt(dNet)}</div>
      </div>`;

    // รายรับ
    if(incCatDay.length){
      html+=`<div class="detail-section">
        <div class="detail-section-title" style="color:var(--income)">💰 รายรับ — ${fmt(dInc)}</div>
        ${incCatDay.map(d=>`<div class="detail-row">
          <div style="flex:1">
            <div class="detail-row-cat">${d.cat}</div>
            ${d.notes.length?`<div class="detail-row-note">📝 ${d.notes.join(', ')}</div>`:''}
          </div>
          <div class="detail-row-amt inc">${fmt(d.total)}</div>
        </div>`).join('')}
      </div>`;
    }

    // รายจ่าย (ไม่รวมน้ำแข็ง)
    if(expCatDay.length){
      html+=`<div class="detail-section">
        <div class="detail-section-title" style="color:var(--expense)">💸 รายจ่าย — ${fmt(expRecsDay.reduce((s,r)=>s+r.amount,0))}</div>
        ${expCatDay.map(d=>`<div class="detail-row">
          <div style="flex:1">
            <div class="detail-row-cat">${d.cat}</div>
            ${d.notes.length?`<div class="detail-row-note">📝 ${d.notes.join(', ')}</div>`:''}
          </div>
          <div class="detail-row-amt exp">${fmt(d.total)}</div>
        </div>`).join('')}
      </div>`;
    }

    // น้ำแข็ง (แยกต่างหาก)
    if(iceCatDay.length){
      html+=`<div class="detail-section" style="background:var(--ice-light)">
        <div class="detail-section-title" style="color:var(--ice)">🧊 ค่าน้ำแข็ง — ${fmt(iceRecsDay.reduce((s,r)=>s+r.amount,0))}</div>
        ${iceCatDay.map(d=>`<div class="detail-row">
          <div style="flex:1">
            <div class="detail-row-cat">${d.cat}</div>
            ${d.notes.length?`<div class="detail-row-note">📝 ${d.notes.join(', ')}</div>`:''}
          </div>
          <div class="detail-row-amt ice">${fmt(d.total)}</div>
        </div>`).join('')}
      </div>`;
    }

    html+=`<div class="detail-total-row">
      <span>💰 ${fmt(dInc)} &nbsp;|&nbsp; 💸 ${fmt(dExp)}</span>
      <span style="color:${dNet>=0?'var(--income)':'var(--expense)'};font-weight:800">กำไร ${fmt(dNet)}</span>
    </div></div>`;
  });

  container.innerHTML=html;
}

// ════════════════════════════════
// EVENTS CRUD
// ════════════════════════════════
function openNewEventModal(){
  document.getElementById('ev-id').value='';
  document.getElementById('modal-ev-title').textContent='เพิ่มงานใหม่';
  ['ev-name','ev-loc','ev-note'].forEach(id=>document.getElementById(id).value='');
  document.getElementById('ev-start').value=today();
  document.getElementById('ev-end').value=today();
  openModal('modal-event');
}
function editEvent(id){
  const ev=events.find(e=>e.id===id);if(!ev)return;
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
  btn.disabled=true;btn.innerHTML='<span class="spinner"></span>บันทึก...';
  try{
    if(id){
      const idx=events.findIndex(e=>e.id===id);
      if(idx>-1)events[idx]=payload;else events.push(payload);
      const rowIdx=await findRowIndex('Events',id);
      if(rowIdx>-1)await updateRow('Events',rowIdx,[payload.id,payload.name,payload.start,payload.end,payload.location,payload.note,payload.updatedAt]);
      else await appendRow('Events',[payload.id,payload.name,payload.start,payload.end,payload.location,payload.note,payload.updatedAt]);
    }else{
      events.push(payload);
      await appendRow('Events',[payload.id,payload.name,payload.start,payload.end,payload.location,payload.note,payload.updatedAt]);
    }
    closeModal('modal-event');renderEventList();populateAllSelects();
    showToast('✅ บันทึกงานสำเร็จ');setSS('ss-events','✅ Sync แล้ว','ok');
  }catch(e){showToast('❌ '+e.message,false);}
  btn.disabled=false;btn.innerHTML='💾 บันทึก';
}
async function deleteEvent(id){
  if(!confirm('ลบงานนี้?'))return;
  try{
    const rowIdx=await findRowIndex('Events',id);
    if(rowIdx>-1)await deleteSheetRow('Events',rowIdx);
    events=events.filter(e=>e.id!==id);
    renderEventList();populateAllSelects();showToast('🗑️ ลบงานแล้ว');
  }catch(e){showToast('❌ '+e.message,false);}
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
  const ev=events.find(e=>e.id===id);if(!ev)return;
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
      ${dr.map(r=>`<div class="record-item"><div><div class="record-label">${r.type==='income'?'💰':isIce(r)?'🧊':'💸'} ${r.category}</div>${r.note?`<div class="record-note">📝 ${r.note}</div>`:''}</div><div style="display:flex;align-items:center;gap:6px"><span class="record-amount ${r.type}" style="${isIce(r)?'color:var(--ice)':''}">${r.type==='income'?'+':'-'}${fmt(r.amount)}</span><button class="btn-danger-sm" onclick="deleteRecordFromDetail('${r.id}','${id}')">×</button></div></div>`).join('')}
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

// ════════════════════════════════
// RECORDS CRUD
// ════════════════════════════════
function initRecordPage(){populateAllSelects();renderDailyRecords();}
function onRecordEventChange(){
  const id=document.getElementById('rec-event').value;
  document.getElementById('rec-date-wrap').style.display=id?'block':'none';
  document.getElementById('rec-entry').style.display=id?'block':'none';
  if(!id)return;
  const ev=events.find(e=>e.id===id);
  const di=document.getElementById('rec-date');
  di.value=today();if(ev){di.min=ev.start;di.max=ev.end;}
  renderDailyRecords();
}
function renderDailyRecords(){
  const eventId=document.getElementById('rec-event').value;
  const date=document.getElementById('rec-date')?.value||today();
  document.getElementById('daily-date-lbl').textContent=date;
  const recs=records.filter(r=>r.eventId===eventId&&r.date===date);
  const list=document.getElementById('daily-list');
  list.innerHTML=recs.length
    ?recs.map(r=>`<div class="record-item"><div><div class="record-label">${r.type==='income'?'💰':isIce(r)?'🧊':'💸'} ${r.category}</div>${r.note?`<div class="record-note">📝 ${r.note}</div>`:''}</div><div style="display:flex;align-items:center;gap:6px"><span class="record-amount ${r.type}" style="${isIce(r)?'color:var(--ice)':''}">${r.type==='income'?'+':'-'}${fmt(r.amount)}</span><button class="btn-danger-sm" onclick="deleteRecord('${r.id}')">×</button></div></div>`).join('')
    :'<div class="empty" style="padding:14px"><p>ยังไม่มีรายการ</p></div>';
  const ti=recs.filter(r=>r.type==='income').reduce((s,r)=>s+r.amount,0);
  const te=recs.filter(r=>r.type==='expense').reduce((s,r)=>s+r.amount,0);
  const net=ti-te;
  document.getElementById('ds-inc').textContent=fmt(ti);
  document.getElementById('ds-exp').textContent=fmt(te);
  const nEl=document.getElementById('ds-net');
  nEl.textContent=fmt(net);nEl.className=net>=0?'val-pos':'val-neg';
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
  btn.disabled=true;btn.innerHTML='<span class="spinner"></span>บันทึก...';
  const rec={id:uid(),eventId,type,amount,category:catEl.value,note:noteEl.value,date:document.getElementById('rec-date').value||today(),createdAt:new Date().toISOString()};
  try{
    await appendRow('Records',[rec.id,rec.eventId,rec.type,rec.amount,rec.category,rec.note,rec.date,rec.createdAt]);
    records.push(rec);
    amtEl.value='';noteEl.value='';
    renderDailyRecords();
    showToast(type==='income'?'✅ เพิ่มรายรับแล้ว':'✅ เพิ่มรายจ่ายแล้ว');
    setSS('ss-rec','✅ บันทึกลง Sheet แล้ว','ok');
  }catch(e){showToast('❌ '+e.message,false);setSS('ss-rec','❌ '+e.message,'err');}
  btn.disabled=false;
  btn.innerHTML=type==='income'?'+ เพิ่มรายรับ':'+ เพิ่มรายจ่าย';
}
async function deleteRecord(id){
  try{
    const rowIdx=await findRowIndex('Records',id);
    if(rowIdx>-1)await deleteSheetRow('Records',rowIdx);
    records=records.filter(r=>r.id!==id);
    renderDailyRecords();showToast('🗑️ ลบรายการแล้ว');
  }catch(e){showToast('❌ '+e.message,false);}
}
async function deleteRecordFromDetail(id,eventId){await deleteRecord(id);showEventDetail(eventId);}

// ════════════════════════════════
// BOOT
// ════════════════════════════════
async function boot(){
  showLoading('กำลังตรวจสอบการเข้าสู่ระบบ...');
  let token=parseTokenFromHash();
  if(!token)token=getSavedToken();
  if(!token){showLogin();return;}
  accessToken=token;
  showLoading('กำลังโหลดข้อมูล...');
  try{
    await fetchUserProfile();
    showApp();
    await ensureHeaders();
    await loadAllData();
  }catch(e){showToast('❌ '+e.message,false);showLogin();}
}

let resizeTimer;
window.addEventListener('resize',()=>{
  clearTimeout(resizeTimer);
  resizeTimer=setTimeout(()=>{
    if(document.getElementById('page-dashboard').classList.contains('active'))renderDashboard();
  },150);
});

boot();
</script>
</body>
</html>
