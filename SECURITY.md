# Security Policy

## Supported Versions

Use this section to tell people about which versions of your project are
currently being supported with security updates.

| Version | Supported          |
| ------- | ------------------ |
| 5.1.x   | :white_check_mark: |
| 5.0.x   | :x:                |
| 4.0.x   | :white_check_mark: |
| < 4.0   | :x:                |

## Reporting a Vulnerability

Use this section to tell people how to report a vulnerability.

Tell them where to go, how often they can expect to get an update on a
reported vulnerability, what to expect if the vulnerability is accepted or
declined, etc.
<!DOCTYPE html>
<html lang="ps" dir="rtl" data-theme="dark">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>د عبدالله مختار د رسیداتو کتاب سیستم</title>
<link href="https://fonts.googleapis.com/css2?family=Noto+Nastaliq+Urdu&display=swap" rel="stylesheet">
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<style>
:root{--bg:#f8fafc;--panel:#ffffff;--text:#0f172a;--muted:#475569;--accent:#16a34a;--danger:#dc2626;--primary:#0ea5e9;--border:#e2e8f0;--input-bg:#ffffff;--tag-bg:#f1f5f9;}
[data-theme="dark"]{--bg:#0f172a;--panel:#111827;--text:#e5e7eb;--muted:#9ca3af;--accent:#22c55e;--danger:#ef4444;--primary:#38bdf8;--border:#374151;--input-bg:#0b1220;--tag-bg:#0b1220;}
*{box-sizing:border-box;}
body{margin:0;background:var(--bg);color:var(--text);font-family:"Noto Nastaliq Urdu",system-ui,sans-serif;}
.container{max-width:1000px;margin:1.5rem auto;padding:1rem;}
.header{display:flex;justify-content:space-between;align-items:center;color:var(--muted);margin-bottom:1rem;}
.toggle-btn{padding:0.45rem 0.8rem;border-radius:999px;border:1px solid var(--border);background:var(--tag-bg);color:var(--text);cursor:pointer;}
.card{background:var(--panel);border:1px solid var(--border);border-radius:10px;padding:1rem;margin-bottom:1rem;}
.grid{display:grid;gap:1rem;}
.row-3{grid-template-columns:repeat(3,1fr);}
.field{display:flex;flex-direction:column;gap:0.35rem;}
.label{font-size:0.95rem;color:var(--muted);}
input,textarea,select{background:var(--input-bg);color:var(--text);border:1px solid var(--border);border-radius:8px;padding:0.65rem 0.75rem;outline:none;}
textarea{min-height:80px;}
.actions{display:flex;gap:0.6rem;flex-wrap:wrap;margin-top:0.75rem;}
.btn{padding:0.55rem 0.9rem;border-radius:8px;border:1px solid var(--border);background:var(--input-bg);color:var(--text);cursor:pointer;}
.btn-primary{background:var(--primary);border-color:var(--primary);color:#042333;}
[data-theme="dark"] .btn-primary{color:#05151f;}
.btn-accent{background:var(--accent);border-color:var(--accent);color:#07240e;}
.btn-danger{background:var(--danger);border-color:var(--danger);color:#230707;}
.btn-recycle{background:#a1a1aa;border-color:#a1a1aa;color:#111;}
.table{width:100%;border-collapse:collapse;margin-top:1rem;}
.table th,.table td{border-bottom:1px solid var(--border);padding:0.6rem;text-align:right;}
#loginForm, #settingsLoginForm{position:fixed;top:0;left:0;width:100%;height:100%;background:var(--bg);display:flex;align-items:center;justify-content:center;z-index:1000;}
#loginForm .card, #settingsLoginForm .card{max-width:400px;width:100%;}
.selectCol{width:30px;text-align:center;}
.modal{display:none;position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,0.6);align-items:center;justify-content:center;z-index:1000;}
.modal .card{max-width:600px;width:90%;max-height:80vh;overflow-y:auto;padding:1rem;}
#excelPasteModal{width:100%;margin-top:0.5rem;height:80px;}
#searchModal .card{width:100%;height:100%;max-width:100%;max-height:100%;border-radius:0;}
/* ==============================
   بټنونه (Buttons) - Lifted Hover Effect
============================== */

.btn {
  padding: 0.55rem 0.9rem;
  border-radius: 8px;
  border: 1px solid #e2e8f0;
  background: #ffffff;
  color: #0f172a;
  font-size: 0.95rem;
  cursor: pointer;
  transition: all 0.2s ease;  /* نرم حرکت */
  box-shadow: 0 2px 5px rgba(0,0,0,0.15); /* لږ سایه */
}

.btn:hover {
  transform: translateY(-5px) scale(1.05); /* پورته شي + لږ غټ شي */
  box-shadow: 0 10px 20px rgba(0,0,0,0.25); /* قوي سایه */
}

/* Primary بټن */
.btn-primary {
  background: #0ea5e9;
  border-color: #0ea5e9;
  color: #ffffff;
}

.btn-primary:hover {
  background: #38bdf8;
  border-color: #38bdf8;
}

/* Accent بټن */
.btn-accent {
  background: #16a34a;
  border-color: #16a34a;
  color: #ffffff;
}

.btn-accent:hover {
  background: #22c55e;
  border-color: #22c55e;
}

/* Danger بټن */
.btn-danger {
  background: #dc2626;
  border-color: #dc2626;
  color: #ffffff;
}

.btn-danger:hover {
  background: #ef4444;
  border-color: #ef4444;
}

/* Disabled بټن */
.btn:disabled {
  opacity: 0.5;
  cursor: not-allowed;
  transform: none;
  box-shadow: 0 2px 5px rgba(0,0,0,0.15);
}
</style>
</head>
<body>

<!-- Excel Paste Modal -->
<div id="excelModal" class="modal">
  <div class="card">
    <h2>📥 Excel Paste</h2>
    <textarea id="excelPasteModal" placeholder="دلته Excel ډیټا پیسټ کړئ"></textarea>
    <div class="actions">
      <button class="btn btn-primary" id="saveExcelData">ثبت</button>
      <button class="btn" id="closeExcelModal">بند</button>
    </div>
  </div>
</div>

<!-- Settings Login Form -->
<div id="settingsLoginForm" style="display:none;">
  <div class="card">
    <h2>Settings Login</h2>
    <div class="field"><label class="label">Username</label><input type="text" id="settingsUsername"></div>
    <div class="field"><label class="label">Password</label><input type="password" id="settingsPassword"></div>
    <div class="actions">
      <button class="btn btn-primary" id="settingsLoginBtn">Login</button>
      <button class="btn" id="settingsLoginCancel">لغو</button>
    </div>
  </div>
</div>

<!-- Login Form -->
<div id="loginForm">
  <div class="card">
    <h2>Login</h2>
    <div class="field"><label class="label">کارکوونکی نوم</label><input type="text" id="loginName"></div>
    <div class="field"><label class="label">پاسورډ</label><input type="password" id="loginPass"></div>
    <div class="actions"><button class="btn btn-primary" id="loginBtn">لاګین</button></div>
  </div>
</div>

<!-- Main Container -->
<div class="container" id="mainContainer" style="display:none;">
  <div class="header">

<!-- Hidden File Input -->
<input type="file" id="profileInput" accept="image/*" style="display:none;">

    <div>دعبدالله مختاردرسيداتو کتاب سيستم</div>
    <!-- Profile Image -->
<div id="profileContainer">
  <img id="profileImg" src="" alt="Profile">
</div>
<style>
#profileContainer{
  position: sticky;        /* یوازې د فورم سر کې */
  top: 50px;
  width: 20px;
  height: 20px;
  margin: 10px auto 30px auto;
  border-radius: 190%;      /* 🔴 بشپړه دایره */
  overflow: hidden;        /* اړین */
  border: 0px solid #e60e0e5b;
  background: #fff;
  z-index: 25;
  display: none;
}

/* ⭐ دا ډېر مهم دی */
#profileContainer img{
  width: 100%;
  height: 100%;
  object-fit: cover;       /* 👈 عکس سم فِټ کېږي */
  object-position: center; /* 👈 تل منځ کې */
  display: block;
}
#profileContainer:hover{
  cursor: pointer;
  box-shadow: 0 0 10px rgba(0,0,0,0.3);
}
#profileContainer img{
  width: 100%;
  height: 100%;
  object-fit: cover;
}
#profileContainer {
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

#profileContainer:hover {
  transform: scale(7.10);        /* 👈 څومره غټ شي */
  z-index: 9999;                /* 👈 د نورو پورته */
  box-shadow: 0 15px 30px rgba(0,0,0,0.4);
}

</style>
    <div class="header" style="justify-content:center; gap:1rem;">
  <button class="toggle-btn" id="toggleTheme">سپین</button>
  <button class="toggle-btn" id="openSettings">⚙ تنظیمات</button>
</div>

  </div>
<div id="dashboardModal" class="modal">
  <div class="card" style="max-width:800px; width:95%;">
    <h2>📊 د مکتوبونو ډشبورډ</h2>
<!-- Summary Cards -->
<div class="summary-cards" style="display:flex;gap:1rem;margin-bottom:1rem;">
  <div class="card" style="flex:1;background:#38bdf8;color:white;padding:1rem;border-radius:8px;text-align:center;">
    ټول ثبتونه<br><strong id="totalRecords">0</strong>
  </div>
  <div class="card" style="flex:1;background:#22c55e;color:white;padding:1rem;border-radius:8px;text-align:center;">
    نن ثبتونه<br><strong id="todayRecords">0</strong>
  </div>
  <div class="card" style="flex:1;background:#f59e0b;color:white;padding:1rem;border-radius:8px;text-align:center;">
    د شعبو شمېر<br><strong id="deptCount">0</strong>
  </div>
</div>

    <!-- Line Chart -->
    <canvas id="lineChart" height="120" style="margin-bottom:1rem;"></canvas>

    <!-- Bar Chart -->
    <canvas id="dateChart" height="120" style="margin-bottom:1rem;"></canvas>

    <!-- Pie Chart -->
    <canvas id="deptChart" height="120" style="margin-bottom:1rem;"></canvas>

    <div class="actions">
      <button class="btn" onclick="closeDashboard()">بندول</button>
    </div>
  </div>
</div>

  <button class="btn" onclick="openDashboard()">📊 ډشبورډ</button>

  <!-- Form -->


  <div class="card">
    <h2>د رسید معلومات</h2>
<div class="field">
  <label style="font-weight:bold">
    <input type="checkbox" id="autoNumberToggle" checked>
    اتومات وارده نمبر فعال
  </label>
</div>
    <div class="grid row-3">
      <div class="field">
        
<label class="label">واردي نمبر</label>
<input type="text" id="incomingNumber" readonly>
</div>
      <div class="field"><label class="label">شعبه</label><input list="departmentsList" id="department"><datalist id="departmentsList"></datalist></div>
      <div class="field"><label class="label">نوم</label><input list="namesList" id="name"><datalist id="namesList"></datalist></div>
      <div class="field"><label class="label">د مکتوب تاريخ</label><input type="text" id="letterDate" placeholder="YYYY/MM/DD"></div>
      <div class="field"><label class="label">د مکتوب نمبر</label><input type="text" id="letterNumber"></div>
      <div class="field"><label class="label">مرسل</label><input list="sendersList" id="sender"><datalist id="sendersList"></datalist></div>
      <div class="field"><label class="label">مرسل اليه</label><input list="recipientsList" id="recipient"><datalist id="recipientsList"></datalist></div>
      <div class="field"><label class="label">د سند ډول</label><input list="docTypesList" id="docType"><datalist id="docTypesList"></datalist></div>
      <div class="field"><label class="label">موضوع</label><textarea id="receipts"></textarea></div>
      <div class="field"><label class="label">د رسيداتو تاريخ</label><input list="receiptDatesList" id="receiptDate"><datalist id="receiptDatesList"></datalist></div>
    </div>
    <div class="actions">
      <button class="btn btn-primary" id="saveRecord">ثبت معلومات</button>
      <button class="btn" id="resetForm">لغو</button>
      <button class="btn btn-recycle" id="viewRecycle">♻ Recycle Bin</button>
      <button class="btn btn-primary" id="importExcel">📥 Excel پیسټ</button>
      <button class="btn" id="toggleSearch">🔍 لټون</button>
      <button class="btn btn-danger" id="deleteSelected">🗑 ټاکل شوي حذف</button>
    </div>
  </div>

  <!-- Records Table -->
  <div class="card">
    <h2>ریکارډونه</h2>
    <table class="table" id="recordsTable">
      <thead>
        <tr>
          <th class="selectCol"><input type="checkbox" id="selectAll"></th>
          <th>واردي نمبر</th><th>شعبه</th><th>نوم</th><th>مکتوب نمبر</th><th>مرسل</th><th>مرسل اليه</th><th>د سند ډول</th><th>د رسيداتو تاريخ</th><th>عملیات</th>
        </tr>
      </thead>
      <tbody></tbody>
    </table>
  </div>
</div>

<!-- Settings Modal -->
<div id="settingsModal" class="modal">
  <div class="card">
    <h2>تنظیمات</h2>
    <div class="field"><label class="label">شعبې</label><textarea id="setDepartments"></textarea></div>
    <div class="field"><label class="label">نومونه</label><textarea id="setNames"></textarea></div>
    <div class="field"><label class="label">مرسل</label><textarea id="setSender"></textarea></div>
    <div class="field"><label class="label">مرسل اليه</label><textarea id="setRecipient"></textarea></div>
    <div class="field"><label class="label">د سند ډولونه</label><textarea id="setDocType"></textarea></div>
    <div class="field"><label class="label">د رسيداتو تاريخونه</label><textarea id="setReceiptDates"></textarea></div>
    <div class="field"><label class="label">Username</label><input type="text" id="setUsername"></div>
    <div class="field"><label class="label">Password</label><input type="password" id="setPassword"></div>
    <div class="actions"><button class="btn btn-primary" id="saveSettings">ذخیره</button><button class="btn" id="closeSettings">بندول</button></div>
  </div>
</div>

<!-- Recycle Modal -->
<div id="recycleModal" class="modal">
  <div class="card">
    <h2>Recycle Bin</h2>
    <table class="table">
      <table class="table">
  <thead>
    <tr>
      <th>واردي نمبر</th>
      <th>شعبه</th>
      <th>نوم</th>
      <th>مکتوب نمبر</th>
      <th>عملیات</th>
    </tr>
  </thead>
  <tbody></tbody>
</table>
    <div class="actions"><button class="btn" id="closeRecycle">بندول</button><button class="btn btn-danger" id="deleteRecycle">💀 Delete permanently</button></div>
  </div>
</div>

<!-- Search Modal -->
<div id="searchModal" class="modal">
  <div class="card">
    <h2>لټون</h2>
    <input type="text" id="modalSearchInput" placeholder="لټون ..." style="width:100%;padding:0.5rem;margin-top:0.5rem;border-radius:6px;border:1px solid #ccc;">
    <table class="table" style="margin-top:1rem;">
      <thead><tr><th>شعبه</th><th>نوم</th><th>مکتوب نمبر</th><th>مرسل</th><th>مرسل اليه</th><th>د سند ډول</th><th>د رسيداتو تاريخ</th><th>عملیات</th></tr></thead>
      <tbody id="modalSearchBody"></tbody>
    </table>
    <div class="actions"><button class="btn btn-primary" id="closeSearch">بندول</button></div>
  </div>
</div>

<!-- View Record Modal -->
<div id="viewModal" class="modal">
  <div class="card">
    <h2>د ریکارډ جزئیات</h2>
    <div id="viewContent" style="line-height:1.6;"></div>
    <div class="actions"><button class="btn btn-primary" id="closeView">بندول</button></div>
  </div>
</div>

<!-- Dashboard Modal -->
<div id="dashboardModal" class="modal">
  <div class="card">
    <h2>📊 د مکتوبونو ډشبورډ</h2>
    <canvas id="dateChart" height="120" style="margin-bottom:1rem;"></canvas>
    <canvas id="deptChart" height="120"></canvas>
    <div class="actions"><button class="btn" onclick="closeDashboard()">بندول</button></div>
  </div>
</div>

<script>
// --- Dashboard Modal ---
const dashboardModal = document.getElementById("dashboardModal");
let dateChartObj = null;
let deptChartObj = null;

function openDashboard(){
  dashboardModal.style.display = "flex";
  if(dateChartObj) dateChartObj.destroy();
  if(deptChartObj) deptChartObj.destroy();
  renderDateChart();
  renderDeptChart();
}

function closeDashboard(){ dashboardModal.style.display = "none"; }

// --- Login ---
let storedUser = JSON.parse(localStorage.getItem('loginUser')) || {username:'عبدالله مختار', password:'12345'};
const loginForm=document.getElementById("loginForm"), mainContainer=document.getElementById("mainContainer");
document.getElementById("loginBtn").addEventListener("click", ()=>{
  const name=document.getElementById("loginName").value.trim(), pass=document.getElementById("loginPass").value;
  if(name===storedUser.username && pass===storedUser.password){
    loginForm.style.display="none";
    mainContainer.style.display="block";
    loadSettings();
    renderTable();
    renderRecycle();
    document.getElementById("incomingNumber").value = generateIncomingNumber();
  } else alert("نوم یا پاسورډ غلط دی");
});

// --- Elements ---
const els={
  department:document.getElementById("department"),
  name:document.getElementById("name"),
  letterDate:document.getElementById("letterDate"),
  letterNumber:document.getElementById("letterNumber"),
  sender:document.getElementById("sender"),
  recipient:document.getElementById("recipient"),
  docType:document.getElementById("docType"),
  receipts:document.getElementById("receipts"),
  receiptDate:document.getElementById("receiptDate"),
  saveRecord:document.getElementById("saveRecord"),
  resetForm:document.getElementById("resetForm"),
  recordsTableBody:document.querySelector("#recordsTable tbody")
};

// --- Storage ---
const stateKey="receipt_records", recycleKey="recycle_records";
const records=JSON.parse(localStorage.getItem(stateKey)||"[]");
function generateIncomingNumber(){

  let max =0;

  records.forEach(r => {

    if(r.incomingNumber){

      const match =
      r.incomingNumber.match(/\d+$/);

      if(match){

        const num =
        parseInt(match[0]);

        if(num > max) max = num;

      }

    }

  });

  return "88و-" + (max + 1);

}
const recycle=JSON.parse(localStorage.getItem(recycleKey)||"[]");

// --- Load Settings ---
function loadSettings(){
  const defaults = {
    departments:["اداري","مالي","حقوقي"],
    names:["محمد","احمد","سارا"],
    senders:["محمد","احمد","سارا"],
    recipients:["مرکز","دفتر"],
    docTypes:["رسید","مکتوب","فیصله"],
    receiptDates:["2025/01/01","2025/01/02"]
  };

  const map = [
    {key:"departments", list:"departmentsList", textarea:"setDepartments"},
    {key:"names", list:"namesList", textarea:"setNames"},
    {key:"senders", list:"sendersList", textarea:"setSender"},
    {key:"recipients", list:"recipientsList", textarea:"setRecipient"},
    {key:"docTypes", list:"docTypesList", textarea:"setDocType"},
    {key:"receiptDates", list:"receiptDatesList", textarea:"setReceiptDates"}
  ];

  map.forEach(m=>{
    let data = localStorage.getItem(m.key);
    if(data === null){ localStorage.setItem(m.key, JSON.stringify(defaults[m.key])); data = JSON.stringify(defaults[m.key]); }
    const arr = JSON.parse(data);
    const dl = document.getElementById(m.list);
    if(dl){ dl.innerHTML=""; arr.forEach(v=>{const o=document.createElement("option"); o.value=v; dl.appendChild(o);}); }
    const ta=document.getElementById(m.textarea);
    if(ta) ta.value = arr.join("\n");
  });

  storedUser = JSON.parse(localStorage.getItem("loginUser")) || { username:"عبدالله مختار", password:"12345" };
  document.getElementById("setUsername").value = storedUser.username;
  document.getElementById("setPassword").value = storedUser.password;
}

// --- Settings Secure Open ---
const settingsModalEl = document.getElementById("settingsModal");
document.getElementById("openSettings").addEventListener("click",()=>{
  const u = prompt("Username داخل کړئ:");
  const p = prompt("Password داخل کړئ:");
  if(u===storedUser.username && p===storedUser.password){ settingsModalEl.style.display="flex"; } 
  else alert("Username یا Password غلط دی!");
});
document.getElementById("closeSettings").addEventListener("click",()=>{settingsModalEl.style.display="none";});

// --- Save Settings ---
document.getElementById("saveSettings").addEventListener("click",()=>{
  const map = [
    {key:"departments", textarea:"setDepartments"},
    {key:"names", textarea:"setNames"},
    {key:"senders", textarea:"setSender"},
    {key:"recipients", textarea:"setRecipient"},
    {key:"docTypes", textarea:"setDocType"},
    {key:"receiptDates", textarea:"setReceiptDates"}
  ];
  map.forEach(m=>{
    const ta=document.getElementById(m.textarea);
    if(ta){
      const arr=ta.value.split("\n").map(s=>s.trim()).filter(s=>s);
      localStorage.setItem(m.key, JSON.stringify(arr));
    }
  });
  const newUser={ username: document.getElementById("setUsername").value.trim(), password: document.getElementById("setPassword").value };
  localStorage.setItem("loginUser", JSON.stringify(newUser));
  storedUser = newUser;
  alert("تنظیمات ثبت شول");
  settingsModalEl.style.display="none";
});
const incomingInput = document.getElementById("incomingNumber");
const autoToggle = document.getElementById("autoNumberToggle");

// د اتومات نمبر فعالول که چیک‌باکس checked وي
function updateIncomingNumber() {
  if(autoToggle.checked){
    incomingInput.value = generateIncomingNumber();
    incomingInput.setAttribute("readonly", "readonly");
  } else {
    incomingInput.removeAttribute("readonly");
    incomingInput.value = "";
  }
}

// د فورم په load کې سمدلاسه نمبر جوړول
updateIncomingNumber();

// د چیک‌باکس event
autoToggle.addEventListener("change", updateIncomingNumber);

// --- نمبر جنریټ فنکشن ---
function generateIncomingNumber(){
  let max = 0;
  records.forEach(r => {
    if(r.incomingNumber){
      const parts = r.incomingNumber.split("-");
      if(parts.length > 1){
        const num = parseInt(parts[1]);
        if(!isNaN(num) && num > max){
          max = num;
        }
      }
    }
  });
  return "88و-" + (max + 1);
}
// --- Save Record ---
els.saveRecord.addEventListener("click", ()=>{
  if(!els.department.value || !els.letterNumber.value){alert("شعبه او مکتوب نمبر ضروري دی"); return;}
  const exists = records.some(r=>r.department===els.department.value && r.letterNumber===els.letterNumber.value);
  if(exists){ alert("دغه مکتوب مخکې ثبت شوی دی!"); return; }
 records.unshift({

incomingNumber:
document.getElementById("incomingNumber").value,

department:els.department.value,
name:els.name.value,
letterDate:els.letterDate.value,
letterNumber:els.letterNumber.value,
sender:els.sender.value,
recipient:els.recipient.value,
docType:els.docType.value,
receipts:els.receipts.value,
receiptDate:els.receiptDate.value

});
  localStorage.setItem(stateKey,JSON.stringify(records));
  renderTable();
  updateSummaryCards(); // ✅ تازه کول
  document.getElementById("incomingNumber").value =
generateIncomingNumber();
  els.resetForm.click();
});

// --- د Table رینډر وروسته هم تازه کول ---
renderTable = () => {
  els.recordsTableBody.innerHTML="";
  records.forEach((r,i)=>{
    const tr=document.createElement("tr");
    tr.innerHTML=`<td class="selectCol"><input type="checkbox" class="rowSelect"></td>
    <td>${r.incomingNumber||""}</td>
<td>${r.department}</td><td>${r.name}</td><td>${r.letterNumber}</td><td>${r.sender}</td><td>${r.recipient}</td><td>${r.docType}</td><td>${r.receiptDate}</td>
<td><button class="btn btn-accent" onclick="viewRecord(${i})">کتنه</button><button class="btn btn-danger" onclick="deleteRecord(${i})">حذف</button></td>`;
    els.recordsTableBody.appendChild(tr);
  });
  updateSummaryCards(); // ✅ Table تازه کولو وروسته
}
// Profile Upload
const profileBtn = document.getElementById("openSettings");
const profileInput = document.getElementById("profileInput");
const profileImg = document.getElementById("profileImg");

// بټن باندې کلیک → فایل انتخاب
profileBtn.addEventListener("click", () => {
    profileInput.click();
});

// فایل انتخاب → فورم کې ښکاره او LocalStorage ته ذخیره
profileInput.addEventListener("change", (e) => {
    const file = e.target.files[0];
    if(file){
        const reader = new FileReader();
        reader.onload = function(ev){
            profileImg.src = ev.target.result;
            localStorage.setItem("profileImage", ev.target.result); // تل پاتې
        }
        reader.readAsDataURL(file);
    }
});

// که مخکې عکس اپلوډ شوی وي، فورم کې ښکاره یې کړه
const savedImg = localStorage.getItem("profileImage");
if(savedImg) profileImg.src = savedImg;

// --- Reset Form ---
els.resetForm.addEventListener("click",()=>{["department","name","letterDate","letterNumber","sender","recipient","docType","receipts","receiptDate"].forEach(id=>document.getElementById(id).value="");});

// --- Render Table ---
// function renderTable(){
  els.recordsTableBody.innerHTML="";

  records.forEach((r,i)=>{

    const tr=document.createElement("tr");

    tr.innerHTML=`

<td class="selectCol">
<input type="checkbox" class="rowSelect">
</td>

<td>${r.incomingNumber || ""}</td>

<td>${r.department}</td>

<td>${r.name}</td>

<td>${r.letterNumber}</td>

<td>${r.sender}</td>

<td>${r.recipient}</td>

<td>${r.docType}</td>

<td>${r.receiptDate}</td>

<td>

<button class="btn btn-accent" onclick="viewRecord(${i})">
کتنه
</button>

<button class="btn btn-danger" onclick="deleteRecord(${i})">
حذف
</button>

</td>
`;

    els.recordsTableBody.appendChild(tr);

  });
// --- Delete Record ---
function deleteRecord(i){
  if(confirm("ایا دا ریکارډ حذف کړو؟")){
    recycle.unshift(records[i]);
    records.splice(i,1);
    localStorage.setItem(stateKey, JSON.stringify(records));
    localStorage.setItem(recycleKey, JSON.stringify(recycle));
    renderTable();
    renderRecycle();
  }
}

// --- Recycle ---
const recycleModal=document.getElementById("recycleModal"), recycleTable=recycleModal.querySelector("tbody");
document.getElementById("viewRecycle").addEventListener("click",()=>{recycleModal.style.display="flex"; renderRecycle();});
document.getElementById("closeRecycle").addEventListener("click",()=>{recycleModal.style.display="none";});
document.getElementById("deleteRecycle").addEventListener("click",()=>{if(confirm("ایا ټول ریکارډونه په بشپړ ډول حذف کړو؟")){recycle.length=0; renderRecycle(); localStorage.setItem(recycleKey,JSON.stringify(recycle));}});
function renderRecycle(){recycleTable.innerHTML=""; recycle.forEach((r,i)=>{const tr=document.createElement("tr");tr.innerHTML=`<td>${r.department}</td><td>${r.name}</td><td>${r.letterNumber}</td>
<td><button class="btn btn-accent" onclick="restoreRecord(${i})">↩ بېرته راوستل</button><button class="btn btn-danger" onclick="deleteRecycle(${i})">🗑 حذف</button></td>`; recycleTable.appendChild(tr);}); localStorage.setItem(recycleKey,JSON.stringify(recycle));}
function restoreRecord(i){records.unshift(recycle[i]); recycle.splice(i,1); renderTable(); renderRecycle();}
function deleteRecycle(i){if(confirm("ایا دا ریکارډ په بشپړ ډول حذف کړو؟")){recycle.splice(i,1); renderRecycle();}}

// --- Select All / Delete Selected ---
document.getElementById("deleteSelected").addEventListener("click",()=>{
  const selected = document.querySelectorAll(".rowSelect:checked");
  if(!selected.length) return alert("هیڅ ریکارډ انتخاب شوی نه دی");
  if(!confirm("ایا ټاکل شوي ریکارډونه حذف کړو؟")) return;
  const indexes = Array.from(selected).map(cb => Array.from(els.recordsTableBody.children).indexOf(cb.closest("tr"))).sort((a,b)=>b-a);
  indexes.forEach(i=>{ recycle.unshift(records[i]); records.splice(i,1); });
  localStorage.setItem(stateKey, JSON.stringify(records));
  localStorage.setItem(recycleKey, JSON.stringify(recycle));
  renderTable();
  renderRecycle();
});

// --- View Record Modal ---
const viewModal = document.getElementById("viewModal"); 
const viewContent = document.getElementById("viewContent");
document.getElementById("closeView").addEventListener("click", () => { viewModal.style.display = "none"; });
function viewRecord(i){

const r = records[i];

viewContent.innerHTML = `

<strong>واردي نمبر:</strong> ${r.incomingNumber}<br>

<strong>شعبه:</strong> ${r.department}<br>

<strong>نوم:</strong> ${r.name}<br>

<strong>د مکتوب تاريخ:</strong> ${r.letterDate}<br>

<strong>د مکتوب نمبر:</strong> ${r.letterNumber}<br>

<strong>مرسل:</strong> ${r.sender}<br>

<strong>مرسل اليه:</strong> ${r.recipient}<br>

<strong>د سند ډول:</strong> ${r.docType}<br>

<strong>موضوع:</strong> ${r.receipts}<br>

<strong>د رسيداتو تاريخ:</strong> ${r.receiptDate}

`;

viewModal.style.display = "flex";

}
// --- Search Modal ---
const searchModal=document.getElementById("searchModal"),modalSearchInput=document.getElementById("modalSearchInput"),modalSearchBody=document.getElementById("modalSearchBody");
document.getElementById("toggleSearch").addEventListener("click",()=>{searchModal.style.display="flex"; modalSearchInput.value=""; modalSearchBody.innerHTML="";});
document.getElementById("closeSearch").addEventListener("click",()=>{searchModal.style.display="none";});
modalSearchInput.addEventListener("input", ()=>{
  const query = modalSearchInput.value.toLowerCase();
  modalSearchBody.innerHTML = "";
  const filtered = records.filter(r=>r.department.toLowerCase().includes(query)||r.name.toLowerCase().includes(query)||r.letterNumber.toLowerCase().includes(query)||r.sender.toLowerCase().includes(query)||r.recipient.toLowerCase().includes(query)||r.docType.toLowerCase().includes(query)||r.receiptDate.toLowerCase().includes(query));
  filtered.forEach((r,i)=>{
    const tr = document.createElement("tr");
    tr.innerHTML = `<td>${r.department}</td><td>${r.name}</td><td>${r.letterNumber}</td><td>${r.sender}</td><td>${r.recipient}</td><td>${r.docType}</td><td>${r.receiptDate}</td><td><button class="btn btn-accent" onclick="viewRecordFromSearch(${i},'${query}')">کتنه</button></td>`;
    modalSearchBody.appendChild(tr);
  });
});


// --- Excel Paste ---
const excelModal = document.getElementById("excelModal");
document.getElementById("importExcel").addEventListener("click",()=>{excelModal.style.display="flex";});
document.getElementById("closeExcelModal").addEventListener("click",()=>{excelModal.style.display="none";});
document.getElementById("saveExcelData").addEventListener("click",()=>{
  const lines=document.getElementById("excelPasteModal").value.split("\n");
  lines.forEach(l=>{
    const cols=l.split(/\t|,/);
    if(cols.length>=4){
     document.getElementById("saveExcelData").addEventListener("click", () => {

  const lines = document.getElementById("excelPasteModal").value
    .split("\n")
    .filter(l => l.trim());

  let added = 0;
  let duplicates = 0;

  lines.forEach(l => {
    const cols = l.split(/\t|,/).map(c => c.trim());

    if (cols.length >= 4) {
      const isDuplicate = records.some(r =>
        r.department === cols[0] &&
        r.letterNumber === cols[3]
      );

      if (isDuplicate) {
        duplicates++;
      } else {
        records.unshift({
          department: cols[0] || "",
          name: cols[1] || "",
          letterDate: cols[2] || "",
          letterNumber: cols[3] || "",
          sender: cols[4] || "",
          recipient: cols[5] || "",
          docType: cols[6] || "",
          receipts: cols[7] || "",
          receiptDate: cols[8] || ""
        });
        added++;
      }
    }
  });

  localStorage.setItem(stateKey, JSON.stringify(records));
  renderTable();
  updateSummaryCards();

  document.getElementById("excelPasteModal").value = "";
  excelModal.style.display = "none";

  // ✅ واضح پیغام
  if (duplicates > 0) {
    alert(`⚠ ${duplicates} ریکارډونه مخکې ثبت شوي وو او داخل نه شول\n✅ ${added} نوي ریکارډونه ثبت شول`);
  } else {
    alert(`✅ ټول ${added} ریکارډونه په بریالیتوب سره ثبت شول`);
  }
});
    } 
  });
});

// --- Theme Toggle ---
const root=document.documentElement, btn=document.getElementById("toggleTheme");
btn.addEventListener("click",()=>{const current=root.getAttribute("data-theme"), next=current==="dark"?"light":"dark"; root.setAttribute("data-theme",next); btn.textContent=next==="dark"?"سپین":"تور"; localStorage.setItem("theme",next);});
const saved=localStorage.getItem("theme"); if(saved) root.setAttribute("data-theme",saved);

// --- Dashboard Charts ---
function renderDateChart(){
  const counts = {};
  records.forEach(r=>{if(r.letterDate) counts[r.letterDate] = (counts[r.letterDate]||0)+1;});
  const labels = Object.keys(counts).sort();
  const values = labels.map(d=>counts[d]);
  const ctx = document.getElementById("dateChart").getContext("2d");
  dateChartObj = new Chart(ctx, { type:'bar', data:{labels,datasets:[{label:"په تاریخ ثبت شوي مکتوبونه", data:values, backgroundColor:"#38bdf8"}]}});
}
function renderDeptChart(){
  const counts = {};
  records.forEach(r=>{if(r.department) counts[r.department] = (counts[r.department]||0)+1;});
  const labels = Object.keys(counts);
  const values = labels.map(d=>counts[d]);
  const ctx = document.getElementById("deptChart").getContext("2d");
  deptChartObj = new Chart(ctx, { type:'pie', data:{labels,datasets:[{label:"د شعبو پر اساس", data:values, backgroundColor:["#16a34a","#38bdf8","#ef4444","#f59e0b"]}]}});
}

// --- Settings Login Form ---
const settingsLoginForm = document.getElementById("settingsLoginForm");
document.getElementById("settingsLoginCancel").addEventListener("click", () => { settingsLoginForm.style.display = "none"; });
document.getElementById("settingsLoginBtn").addEventListener("click", () => {
    const u = document.getElementById("settingsUsername").value.trim();
    const p = document.getElementById("settingsPassword").value;
    if (u === storedUser.username && p === storedUser.password) { settingsLoginForm.style.display = "none"; settingsModal.style.display = "flex"; }
    else { alert("Username یا Password غلط دی!"); }
});
function updateSummaryCards() {
    const total = records.length;
    const today = records.filter(r => r.letterDate === new Date().toISOString().slice(0,10)).length;
    const departments = [...new Set(records.map(r => r.department))].length;

    document.getElementById("totalRecords").textContent = total;
    document.getElementById("todayRecords").textContent = today;
    document.getElementById("deptCount").textContent = departments;
}

</script>
<script>
const profile = document.getElementById("profileContainer");

// کله چې صفحه سکرول شي
window.addEventListener("scroll", () => {
  if (window.scrollY === 0) {
    profile.style.display = "block";   // ✅ د فورم سر
  } else {
    profile.style.display = "none";    // ❌ سکرول کې پټ
  }
});
// --- Line Chart Object ---
let lineChartObj = null;

// --- Line Chart د رسيداتو تاريخ پر اساس ---
function renderLineChart() {
  const counts = {};
  records.forEach(r => {
    if(r.receiptDate){               // ✅ دلته د رسيداتو تاريخ وکاروئ
      counts[r.receiptDate] = (counts[r.receiptDate] || 0) + 1;
    }
  });

  const labels = Object.keys(counts).sort();
  const data = labels.map(d => counts[d]);

  const ctx = document.getElementById("lineChart").getContext("2d");

  if(lineChartObj) lineChartObj.destroy(); // که مخکې چارټ وي، له منځه یوسه

  lineChartObj = new Chart(ctx, {
    type: 'line',
    data: {
      labels: labels,
      datasets: [{
        label: "په رسيداتو تاريخ ثبت شوي ریکارډونه",
        data: data,
        borderColor: "#38bdf8",
        backgroundColor: "rgba(56, 189, 248, 0.2)",
        tension: 0.3,
        fill: true
      }]
    },
    options: {
      responsive: true,
      plugins: {
        legend: { position: "top" },
        tooltip: { mode: "index", intersect: false }
      },
      scales: {
        x: { title: { display: true, text: "د رسيداتو تاريخ" } },
        y: { title: { display: true, text: "ریکارډونه" }, beginAtZero: true }
      }
    }
  });
}

// --- Recipient Chart Object (مرسل اليه پر اساس) ---
let recipientChartObj = null;

function renderRecipientChart() {
  const counts = {};
  records.forEach(r => {
    if(r.recipient){
      counts[r.recipient] = (counts[r.recipient] || 0) + 1;
    }
  });

  const labels = Object.keys(counts);
  const data = labels.map(l => counts[l]);

  const ctx = document.getElementById("recipientChart").getContext("2d");

  if(recipientChartObj) recipientChartObj.destroy();

  recipientChartObj = new Chart(ctx, {
    type: 'bar', // که غواړې Pie، type:'pie' هم وکارول شي
    data: {
      labels: labels,
      datasets: [{
        label: "د مکتوبونو شمېر پر اساس د مرسل اليه",
        data: data,
        backgroundColor: ["#38bdf8","#22c55e","#f59e0b","#ef4444","#a1a1aa"]
      }]
    },
    options: {
      responsive: true,
      plugins: {
        legend: { display: false },
        tooltip: { mode: "index", intersect: false }
      },
      scales: {
        x: { title: { display: true, text: "مرسل اليه" } },
        y: { title: { display: true, text: "ریکارډونه" }, beginAtZero: true }
      }
    }
  });
}

// --- د ډشبورډ پرانستل ---
function openDashboard(){
  dashboardModal.style.display = "flex";
  renderLineChart();       // ✅ Line Chart د رسيداتو تاريخ پر اساس
  renderDateChart();       // ✅ Bar Chart د مکتوب تاريخ پر اساس
  renderDeptChart();       // ✅ Pie Chart د شعبو پر اساس
  renderRecipientChart();  // ✅ نوې Bar Chart د مرسل اليه پر اساس
}

// --- د ډشبورډ بندول ---
function closeDashboard(){ 
  dashboardModal.style.display = "none"; 
}
// د لاګین وروسته یا د فورم پرانستلو کې
function showProfileOnTop(){
  window.scrollTo({ top: 0, behavior: "instant" });
  profile.style.display = "block";
}
</script>

</body>
</html>
