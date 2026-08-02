# RUNNA
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<meta name="robots" content="noindex, nofollow">
<meta name="theme-color" content="#0B0E14">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="apple-mobile-web-app-title" content="Sub 2">
<title>Sub 2</title>
<style>
*, *::before, *::after { box-sizing: border-box; }
html, body { margin:0; padding:0; }
body {
  --bg:#0B0E14; --panel:#141922; --panel2:#1A2029; --line:#222A36;
  --tx:#F2F5F9; --dim:#8A96A8; --faint:#5D6879;
  --ember:#FF6B35; --sun:#FFC94A; --dawn:#4CC9F0; --go:#5AD68A; --plum:#A98BFF;
  background:var(--bg); color:var(--tx); min-height:100vh;
  font-family: ui-sans-serif, -apple-system, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
  font-size:15px; line-height:1.5; -webkit-font-smoothing:antialiased;
  padding-bottom:calc(56px + env(safe-area-inset-bottom));
  -webkit-text-size-adjust:100%;
}
.num { font-family: ui-monospace, "SF Mono", Menlo, Consolas, monospace; font-variant-numeric:tabular-nums; letter-spacing:-.02em; }
.wrap { max-width:760px; margin:0 auto; padding:0 14px; }
.hidden { display:none !important; }

.top { position:sticky; top:0; z-index:20; background:rgba(11,14,20,.94); backdrop-filter:blur(10px);
  -webkit-backdrop-filter:blur(10px); border-bottom:1px solid var(--line); padding-top:env(safe-area-inset-top); }
.topin { max-width:760px; margin:0 auto; padding:12px 14px 0; }
.brandrow { display:flex; align-items:flex-start; justify-content:space-between; gap:10px; }
.brand { font-size:19px; font-weight:800; letter-spacing:.16em; text-transform:uppercase; }
.brand span { color:var(--ember); }
.count { font-size:11px; text-transform:uppercase; letter-spacing:.14em; color:var(--dim); text-align:right; }
.count b { display:block; font-size:17px; color:var(--tx); letter-spacing:-.02em; font-weight:700; }
.savechip { display:flex; align-items:center; gap:6px; margin-top:3px;
  font-size:9.5px; letter-spacing:.13em; text-transform:uppercase; color:var(--faint); }
.savechip i { width:6px; height:6px; border-radius:99px; background:var(--go); flex:none; }
.savechip[data-mode="off"] i, .savechip[data-mode="error"] i { background:var(--sun); }
.savechip[data-mode="loading"] i { background:var(--faint); }

.tabs { display:flex; gap:2px; margin-top:12px; overflow-x:auto; scrollbar-width:none; }
.tabs::-webkit-scrollbar { display:none; }
.tab { flex:1; white-space:nowrap; background:none; border:none; border-bottom:2px solid transparent;
  color:var(--faint); font:inherit; font-size:12px; font-weight:700; letter-spacing:.12em; text-transform:uppercase;
  padding:10px 12px; cursor:pointer; }
.tab[data-on="1"] { color:var(--tx); border-bottom-color:var(--ember); }

.card { background:var(--panel); border:1px solid var(--line); border-radius:14px; padding:16px; margin-top:14px; }
.eyebrow { font-size:10.5px; font-weight:700; letter-spacing:.16em; text-transform:uppercase; color:var(--faint); margin:0 0 10px; }
h2 { font-size:16px; font-weight:700; margin:0 0 2px; letter-spacing:-.01em; }
.sub { color:var(--dim); font-size:13px; margin:0; }

.tax { display:grid; grid-template-columns:1fr auto 1fr; align-items:center; gap:10px; margin:6px 0 2px; }
.taxcol { text-align:center; }
.taxval { font-size:30px; font-weight:700; line-height:1.05; }
.taxlab { font-size:10px; letter-spacing:.14em; text-transform:uppercase; color:var(--faint); margin-top:5px; }
.taxmid { text-align:center; }
.taxmid .d { font-size:15px; font-weight:700; color:var(--sun); }
.taxmid .l { font-size:9.5px; letter-spacing:.1em; text-transform:uppercase; color:var(--faint); }
.thermbar { height:4px; border-radius:99px; margin-top:14px; }

.grid2 { display:grid; grid-template-columns:1fr 1fr; gap:10px; }
.grid3 { display:grid; grid-template-columns:repeat(3,1fr); gap:10px; }
.stat { background:var(--panel2); border:1px solid var(--line); border-radius:11px; padding:11px 12px; }
.stat .k { font-size:9.5px; letter-spacing:.13em; text-transform:uppercase; color:var(--faint); }
.stat .v { font-size:20px; font-weight:700; margin-top:4px; }
.stat .n { font-size:11px; color:var(--dim); margin-top:2px; }

.raceline { margin-top:16px; }
.track { position:relative; height:8px; border-radius:99px; background:linear-gradient(90deg,#3A2318,#2A2F1E,#17301F); border:1px solid var(--line); }
.marker { position:absolute; top:-5px; width:3px; height:18px; border-radius:2px; background:var(--tx); box-shadow:0 0 0 3px rgba(11,14,20,.9); }
.tickrow { display:flex; justify-content:space-between; margin-top:9px; font-size:10.5px; letter-spacing:.1em; text-transform:uppercase; color:var(--faint); }
.tickrow b { display:block; font-size:15px; letter-spacing:-.02em; margin-top:3px; }

label { display:block; font-size:10.5px; letter-spacing:.13em; text-transform:uppercase; color:var(--faint); margin:0 0 5px; }
input, select, textarea {
  width:100%; background:var(--panel2); border:1px solid var(--line); color:var(--tx);
  border-radius:9px; padding:10px 11px; font:inherit; font-size:16px; outline:none; -webkit-appearance:none; appearance:none;
}
select { background-image:linear-gradient(45deg,transparent 50%,var(--faint) 50%),linear-gradient(135deg,var(--faint) 50%,transparent 50%);
  background-position:calc(100% - 18px) 19px, calc(100% - 13px) 19px; background-size:5px 5px,5px 5px; background-repeat:no-repeat; }
input:focus, select:focus, textarea:focus { border-color:var(--ember); box-shadow:0 0 0 3px rgba(255,107,53,.14); }
input.bad { border-color:#FF6B7D; }
textarea { resize:vertical; min-height:62px; }
.fields { display:grid; grid-template-columns:1fr 1fr; gap:11px; }
.full { grid-column:1 / -1; }
.hint { font-size:12px; color:var(--faint); margin-top:6px; }
.hint.bad { color:#FF6B7D; }

.chips { display:flex; flex-wrap:wrap; gap:6px; }
.chip { background:var(--panel2); border:1px solid var(--line); color:var(--dim); border-radius:99px;
  padding:9px 16px; font:inherit; font-size:13px; font-weight:600; cursor:pointer; }
.chip[data-on="1"] { background:var(--ember); border-color:var(--ember); color:#1A0A02; font-weight:700; }

.btn { background:var(--ember); color:#1A0A02; border:none; border-radius:10px; padding:12px 18px;
  font:inherit; font-size:14px; font-weight:700; letter-spacing:.03em; cursor:pointer; }
.btn:active { transform:translateY(1px); }
.btn:disabled { opacity:.45; }
.btn.ghost { background:transparent; border:1px solid var(--line); color:var(--dim); }
.btn.danger { background:transparent; border:1px solid #4A2530; color:#FF6B7D; }
.btnrow { display:flex; gap:9px; margin-top:14px; flex-wrap:wrap; }

.rows { margin-top:4px; }
.row { display:flex; gap:11px; padding:12px 0; border-top:1px solid var(--line); }
.rail { width:3px; border-radius:99px; flex:none; background:var(--line); }
.rbody { flex:1; min-width:0; }
.rtop { display:flex; justify-content:space-between; gap:10px; align-items:baseline; }
.rdate { font-size:12px; letter-spacing:.1em; text-transform:uppercase; color:var(--dim); }
.rdist { font-size:17px; font-weight:700; }
.rmeta { display:flex; flex-wrap:wrap; gap:5px 14px; margin-top:6px; font-size:12.5px; color:var(--dim); }
.rmeta b { color:var(--tx); font-weight:600; }
.adj { color:var(--dawn); }
.note { margin-top:7px; font-size:13px; color:var(--dim); font-style:italic; }
.rowacts { display:flex; gap:14px; margin-top:8px; }
.lnk { background:none; border:none; padding:0; font:inherit; font-size:11.5px; letter-spacing:.1em;
  text-transform:uppercase; color:var(--faint); cursor:pointer; }

.week { border:1px solid var(--line); border-radius:12px; margin-top:9px; overflow:hidden; background:var(--panel); }
.week[data-now="1"] { border-color:var(--ember); }
.whead { display:flex; align-items:center; gap:11px; padding:13px 14px; cursor:pointer; }
.wno { font-size:10px; letter-spacing:.12em; text-transform:uppercase; color:var(--faint); width:56px; flex:none; }
.wno b { display:block; font-size:16px; color:var(--tx); letter-spacing:-.02em; }
.wmid { flex:1; min-width:0; }
.wphase { font-size:10px; letter-spacing:.13em; text-transform:uppercase; font-weight:700; }
.wmiles { font-size:13px; color:var(--dim); margin-top:2px; }
.wprog { font-size:12px; color:var(--faint); flex:none; }
.wbody { border-top:1px solid var(--line); padding:4px 14px 12px; }
.sess { display:flex; gap:11px; padding:11px 0; border-bottom:1px solid var(--line); }
.sess:last-child { border-bottom:none; }
.sess.rest { opacity:.5; }
.box { width:22px; height:22px; border-radius:6px; border:1.5px solid var(--line); background:var(--panel2);
  flex:none; margin-top:2px; cursor:pointer; display:flex; align-items:center; justify-content:center;
  color:#0B0E14; font-size:13px; font-weight:900; padding:0; }
.box[data-on="1"] { background:var(--go); border-color:var(--go); }
.sday { width:34px; flex:none; font-size:10.5px; letter-spacing:.1em; text-transform:uppercase; color:var(--faint); margin-top:4px; }
.sbody { flex:1; min-width:0; }
.stitle { font-size:14px; font-weight:600; }
.stitle.done { color:var(--faint); text-decoration:line-through; }
.sdet { font-size:12.5px; color:var(--dim); margin-top:3px; }
.space { font-size:12px; color:var(--dawn); margin-top:4px; }
.tagline { display:inline-block; font-size:9.5px; letter-spacing:.1em; text-transform:uppercase;
  border:1px solid var(--line); border-radius:99px; padding:2px 8px; color:var(--faint); margin-left:7px; }
.heatnote { background:rgba(255,107,53,.07); border:1px solid rgba(255,107,53,.24); border-radius:9px;
  padding:9px 11px; font-size:12.5px; color:#FFB48A; margin:10px 0 2px; }

.empty { text-align:center; padding:34px 16px; color:var(--dim); font-size:14px; }
.empty b { display:block; color:var(--tx); font-size:15px; margin-bottom:5px; }
.warnbar { background:rgba(255,201,74,.09); border:1px solid rgba(255,201,74,.28); color:var(--sun);
  border-radius:10px; padding:12px 13px; font-size:12.5px; margin-top:14px; }
.okbar { background:rgba(90,214,138,.08); border:1px solid #25412F; color:var(--go);
  border-radius:10px; padding:11px 13px; font-size:12.5px; margin-top:12px; }
.legend { display:flex; flex-wrap:wrap; gap:5px 14px; margin-top:10px; font-size:11.5px; color:var(--dim); }
.dot { display:inline-block; width:8px; height:8px; border-radius:99px; margin-right:6px; vertical-align:middle; }
table { width:100%; border-collapse:collapse; font-size:12.5px; }
th { text-align:right; font-size:9.5px; letter-spacing:.12em; text-transform:uppercase; color:var(--faint); padding:8px 6px; font-weight:700; }
th:first-child, td:first-child { text-align:left; }
td { text-align:right; padding:9px 6px; border-top:1px solid var(--line); }
.scroll { overflow-x:auto; margin:0 -4px; }
.chart { display:block; max-width:100%; height:auto; margin:0 auto; }
textarea.backup { font-family:ui-monospace, Menlo, Consolas, monospace; font-size:11px; line-height:1.45; min-height:96px; color:var(--dim); }

@media (max-width:520px){
  .fields { grid-template-columns:1fr; }
  .grid3 { grid-template-columns:1fr 1fr; }
  .taxval { font-size:26px; }
}
@media (prefers-reduced-motion: reduce){ * { transition:none !important; animation:none !important; } }
</style>
</head>
<body>

<header class="top">
  <div class="topin">
    <div class="brandrow">
      <div>
        <div class="brand">Sub <span>2</span></div>
        <div class="savechip" id="savechip" data-mode="loading"><i></i><span id="savetext">checking</span></div>
      </div>
      <div class="count">to race day<b class="num" id="daysout">0 days</b></div>
    </div>
    <nav class="tabs" id="tabs">
      <button class="tab" data-tab="dash" data-on="1">Dashboard</button>
      <button class="tab" data-tab="log">Log a run</button>
      <button class="tab" data-tab="plan">Plan</button>
      <button class="tab" data-tab="set">Settings</button>
    </nav>
  </div>
</header>

<main class="wrap">
  <div id="banner"></div>

  <!-- DASHBOARD -->
  <section id="view-dash"></section>

  <!-- LOG -->
  <section id="view-log" class="hidden">
    <div class="card">
      <div class="eyebrow" id="formTitle">New run</div>
      <div class="fields">
        <div>
          <label for="f-date">Date</label>
          <input type="date" id="f-date">
        </div>
        <div>
          <label for="f-dist">Distance in miles</label>
          <input type="number" inputmode="decimal" step="0.01" id="f-dist" placeholder="5.0">
        </div>
        <div class="full">
          <label for="f-dur">Duration</label>
          <input type="text" id="f-dur" placeholder="48:30" autocomplete="off" autocorrect="off" spellcheck="false">
          <div class="hint" id="durHint">Minutes colon seconds, like 48:30. Over an hour, use 1:12:45.</div>
        </div>
        <div>
          <label for="f-ahr">Average heart rate</label>
          <input type="number" inputmode="numeric" id="f-ahr" placeholder="150">
        </div>
        <div>
          <label for="f-mhr">Max heart rate</label>
          <input type="number" inputmode="numeric" id="f-mhr" placeholder="172">
        </div>
        <div>
          <label for="f-temp">Temperature in Fahrenheit</label>
          <input type="number" inputmode="numeric" id="f-temp" placeholder="103">
        </div>
        <div>
          <label for="f-type">Run type</label>
          <select id="f-type">
            <option value="easy">easy</option>
            <option value="tempo">tempo</option>
            <option value="interval">interval</option>
            <option value="long">long</option>
            <option value="recovery">recovery</option>
          </select>
        </div>
        <div class="full">
          <label>Perceived effort, 1 is a stroll and 5 is all out</label>
          <div class="chips" id="effortChips">
            <button class="chip" data-effort="1">1</button>
            <button class="chip" data-effort="2" data-on="1">2</button>
            <button class="chip" data-effort="3">3</button>
            <button class="chip" data-effort="4">4</button>
            <button class="chip" data-effort="5">5</button>
          </div>
        </div>
        <div class="full">
          <label for="f-notes">Notes</label>
          <textarea id="f-notes" placeholder="Legs, hydration, sleep, how the IT band felt"></textarea>
        </div>
      </div>
      <div id="livePace"></div>
      <div class="btnrow">
        <button class="btn" id="saveRun" disabled>Save run</button>
        <button class="btn ghost hidden" id="cancelEdit">Cancel</button>
      </div>
      <p class="sub" id="formNote" style="margin-top:10px">Distance and duration are what turn this into a pace. The rest is optional.</p>
    </div>
    <div class="card">
      <div class="eyebrow">History</div>
      <div id="history"></div>
    </div>
  </section>

  <!-- PLAN -->
  <section id="view-plan" class="hidden"></section>

  <!-- SETTINGS -->
  <section id="view-set" class="hidden">
    <div class="card">
      <div class="eyebrow">Race</div>
      <div class="fields">
        <div>
          <label for="s-date">Race date</label>
          <input type="date" id="s-date">
        </div>
        <div>
          <label for="s-name">Race name</label>
          <input type="text" id="s-name">
        </div>
      </div>
      <p class="sub" style="margin-top:10px">Changing the date rebuilds the plan week by week from next Monday.</p>
    </div>

    <div class="card">
      <div class="eyebrow">Fitness inputs</div>
      <div class="fields">
        <div>
          <label for="s-mile">Mile record</label>
          <input type="text" id="s-mile" inputmode="text">
        </div>
        <div>
          <label for="s-5k">5K record</label>
          <input type="text" id="s-5k" inputmode="text">
        </div>
        <div>
          <label for="s-start">Starting weekly miles</label>
          <input type="number" id="s-start">
        </div>
        <div>
          <label for="s-peak">Peak weekly miles</label>
          <input type="number" id="s-peak">
        </div>
      </div>
      <p class="sub" style="margin-top:10px">The 5K record seeds your starting projection and every target pace in the plan. Enter times as minutes colon seconds.</p>
    </div>

    <div class="card">
      <div class="eyebrow">Backup</div>
      <h2>Your escape hatch</h2>
      <p class="sub">Copy this text and your whole log travels with you. Browser storage survives closing the app and restarting the phone, but clearing site data wipes it, so keep a copy somewhere.</p>
      <div class="btnrow">
        <button class="btn ghost" id="copyBackup">Copy backup</button>
        <button class="btn ghost" id="toggleRestore">Restore from backup</button>
      </div>
      <div id="backupArea" style="margin-top:12px"></div>
      <div id="setMsg"></div>
    </div>

    <div class="card">
      <div class="eyebrow">Data</div>
      <div class="grid2" id="dataStats"></div>
      <div class="btnrow" id="resetRow">
        <button class="btn danger" id="resetBtn">Clear all data</button>
      </div>
      <p class="sub" style="margin-top:10px">Runs, completed sessions, and these settings save automatically on every change.</p>
    </div>
  </section>
</main>

<script>
"use strict";

/* ================================================================
   SUB 2  ·  standalone. no dependencies, no network, no backend.
   Data lives in this browser via localStorage.
   ================================================================ */

var KEY = "sub2:state:v1";
var HALF = 13.1094;
var GOAL_SEC = 7199;
var GOAL_PACE = GOAL_SEC / HALF;

var DEFAULT_PROFILE = {
  raceDate: "2027-02-07",
  raceName: "February half marathon",
  startMileage: 14,
  peakMileage: 34,
  milePRsec: 418,
  fiveKPRsec: 1635
};

var TYPE_COLOR = {
  easy: "#4CC9F0", tempo: "#FF6B35", interval: "#FF4D6D",
  long: "#A98BFF", recovery: "#5AD68A"
};
var PHASE_COLOR = {
  "Heat base": "#FF6B35", "Build": "#FFC94A",
  "Race specific": "#A98BFF", "Taper": "#4CC9F0", "Race week": "#5AD68A"
};
var DAYS = ["Mon","Tue","Wed","Thu","Fri","Sat","Sun"];

/* ---------------------------- utils ---------------------------- */
function pad(n){ return String(n).padStart(2,"0"); }
function esc(s){
  return String(s == null ? "" : s).replace(/[&<>"']/g, function(c){
    return {"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[c];
  });
}
function fmtClock(sec){
  if(!isFinite(sec) || sec <= 0) return "n/a";
  var s = Math.round(sec), h = Math.floor(s/3600), m = Math.floor((s%3600)/60);
  return h > 0 ? h+":"+pad(m)+":"+pad(s%60) : m+":"+pad(s%60);
}
function fmtPace(sec){
  if(!isFinite(sec) || sec <= 0) return "n/a";
  var s = Math.round(sec);
  return Math.floor(s/60)+":"+pad(s%60);
}
function parseDuration(v){
  var raw = String(v == null ? "" : v).trim();
  if(!raw) return 0;
  var parts = raw.split(":");
  if(parts.length > 3) return 0;
  var nums = [];
  for(var i=0;i<parts.length;i++){
    var t = parts[i].trim();
    if(t === ""){ nums.push(0); continue; }
    if(!/^\d+(\.\d+)?$/.test(t)) return 0;
    nums.push(Number(t));
  }
  var sec;
  if(nums.length === 1) sec = nums[0]*60;
  else if(nums.length === 2) sec = nums[0]*60 + nums[1];
  else sec = nums[0]*3600 + nums[1]*60 + nums[2];
  return sec > 0 ? Math.round(sec) : 0;
}
function durationReadback(sec){
  if(sec <= 0) return "";
  var h = Math.floor(sec/3600), m = Math.floor((sec%3600)/60), s = sec%60, out = [];
  if(h) out.push(h+" hour"+(h>1?"s":""));
  if(m) out.push(m+" minute"+(m>1?"s":""));
  if(s) out.push(s+" second"+(s>1?"s":""));
  return out.join(" ");
}
function parseMMSS(v){
  var p = String(v).split(":").map(Number);
  if(p.length === 2 && p.every(function(n){ return isFinite(n); })) return p[0]*60 + p[1];
  return null;
}
function heatFactor(t){ return 1 + 0.002 * Math.max(0, (Number(t) || 60) - 60); }
function riegel(miles, sec, target){ return sec * Math.pow(target/miles, 1.06); }

function tempColor(t){
  var v = Math.max(55, Math.min(115, Number(t) || 70));
  var stops = [[55,[76,201,240]],[75,[90,214,138]],[90,[255,201,74]],[105,[255,107,53]],[115,[255,61,61]]];
  for(var i=0;i<stops.length-1;i++){
    var a = stops[i][0], ca = stops[i][1], b = stops[i+1][0], cb = stops[i+1][1];
    if(v <= b){
      var k = (v-a)/(b-a);
      return "rgb("+ca.map(function(x,j){ return Math.round(x + (cb[j]-x)*k); }).join(",")+")";
    }
  }
  return "rgb(255,61,61)";
}

function mondayOf(d){
  var x = new Date(d.getFullYear(), d.getMonth(), d.getDate());
  x.setDate(x.getDate() - ((x.getDay()+6)%7));
  return x;
}
function addDays(d,n){ var x = new Date(d); x.setDate(x.getDate()+n); return x; }
function ymd(d){ return d.getFullYear()+"-"+pad(d.getMonth()+1)+"-"+pad(d.getDate()); }
function parseYMD(s){
  var p = String(s||"").split("-").map(Number);
  if(!p[0] || !p[1] || !p[2]) return new Date();
  return new Date(p[0], p[1]-1, p[2]);
}
function shortDate(s){
  var d = parseYMD(s);
  return d.toLocaleString("en-US",{month:"short"})+" "+d.getDate();
}

/* ------------------------ run derivations ------------------------ */
function decorate(r){
  var dist = Number(r.distance) || 0;
  var dur = Number(r.durationSec) || 0;
  var pace = dist > 0 ? dur/dist : 0;
  var adj = pace / heatFactor(r.tempF);
  return {
    id:r.id, date:r.date, type:r.type, notes:r.notes, effort:r.effort,
    tempF:r.tempF, avgHR:r.avgHR, maxHR:r.maxHR,
    dist:dist, dur:dur, pace:pace, adjPace:adj, tax:pace-adj,
    projected: (dist >= 1.5 && dur > 0) ? riegel(dist, adj*dist, HALF) : 0
  };
}
function currentProjection(runs){
  var cutoff = addDays(new Date(), -49);
  var pool = runs.map(decorate).filter(function(r){
    return r.dist >= 2 && Number(r.effort) >= 3 && parseYMD(r.date) >= cutoff && r.projected > 0;
  });
  if(!pool.length) return null;
  return pool.reduce(function(best,r){ return r.projected < best.projected ? r : best; });
}

/* ------------------------------ plan ------------------------------ */
var BASE_Q = [
  "Easy run plus 6 x 20 second strides, walk back recovery",
  "Easy run plus 8 x 20 second strides, relaxed turnover",
  "4 x 3 minutes at steady effort, 2 minute jog between",
  "5 x 3 minutes at steady effort, 2 minute jog between",
  "3 x 5 minutes at threshold, 2 minute jog between",
  "4 x 5 minutes at threshold, 2 minute jog between",
  "2 x 10 minutes at threshold, 3 minute jog between",
  "4 x 6 minutes at threshold, 90 second jog between"
];
var BUILD_Q = [
  "20 minute continuous tempo at threshold",
  "5 x 800m at 5K effort, 90 second jog between",
  "2 x 12 minutes at threshold, 3 minute jog between",
  "25 minute continuous tempo at threshold",
  "6 x 800m at 5K effort, 90 second jog between",
  "3 x 10 minutes at threshold, 2 minute jog between"
];
var SPEC_Q = [
  "2 x 2 miles at goal half pace, 3 minute jog between",
  "30 minute continuous tempo at threshold",
  "3 x 2 miles at goal half pace, 3 minute jog between",
  "4 x 1 mile at threshold, 2 minute jog between",
  "6 x 1000m at 5K effort, 2 minute jog between",
  "5 miles at goal half pace inside a longer run"
];
var DOWN_Q = [
  "Easy run plus 8 x 20 second strides",
  "3 x 4 minutes at threshold, 2 minute jog between"
];
var TAPER_Q = [
  "2 x 2 miles at goal half pace, 3 minute jog between",
  "3 x 1 mile at goal half pace, 2 minute jog between"
];

function buildPlan(profile, basePaceIn){
  var today = new Date();
  var dow = (today.getDay()+6)%7;
  var start = mondayOf(today);
  if(dow > 2) start = addDays(start, 7);

  var raceMonday = mondayOf(parseYMD(profile.raceDate));
  var N = Math.round((raceMonday - start)/(7*86400000)) + 1;
  if(!isFinite(N) || N < 6) N = 6;
  if(N > 60) N = 60;

  var cap = Number(profile.peakMileage) || 34;
  var startM = Number(profile.startMileage) || 14;
  var buildEnd = Math.max(3, N-3);
  function r5(x){ return Math.round(x*2)/2; }

  var basePace = Math.max(400, Math.min(900, basePaceIn));
  var target = Math.min(GOAL_PACE, basePace);

  var weeks = [], last = startM;
  var bi=0, ui=0, si=0, di=0, ti=0;

  for(var w=1; w<=N; w++){
    var mon = addDays(start, (w-1)*7);
    var isDown = (w <= buildEnd && w%4 === 0);

    var m;
    if(w > buildEnd){
      var t = w - buildEnd;
      m = t===1 ? cap*0.78 : (t===2 ? cap*0.6 : cap*0.46);
    } else if(w === 1) m = startM;
    else if(isDown) m = last*0.72;
    else m = Math.min(cap, last*1.07);
    m = r5(m);
    if(w <= buildEnd && !isDown) last = m;

    var phase;
    if(w === N) phase = "Race week";
    else if(w > buildEnd) phase = "Taper";
    else if(w <= Math.round(N*0.37)) phase = "Heat base";
    else if(w <= Math.round(N*0.67)) phase = "Build";
    else phase = "Race specific";

    var long;
    if(w === N) long = HALF;
    else if(w === N-1) long = Math.min(7, r5(m*0.42));
    else if(w === N-2) long = Math.min(9, r5(m*0.4));
    else long = Math.min(12, Math.max(3, r5(m*0.35)));

    var p = Math.pow((w-1)/Math.max(1,N-1), 0.8);
    var P = basePace + (target - basePace)*p;
    var k = 1 - 0.22*p;
    var paces = {
      recovery:[P+195*k, P+240*k],
      easy:[P+150*k, P+195*k],
      long:[P+135*k, P+180*k],
      steady:P+50*k,
      hm:P,
      threshold:P-20,
      interval:P-50
    };

    var q;
    if(w === N) q = "3 miles easy with 4 x 1 minute at goal half pace";
    else if(phase === "Taper") q = TAPER_Q[ti++ % TAPER_Q.length];
    else if(isDown) q = DOWN_Q[di++ % DOWN_Q.length];
    else if(phase === "Heat base") q = BASE_Q[bi++ % BASE_Q.length];
    else if(phase === "Build") q = BUILD_Q[ui++ % BUILD_Q.length];
    else q = SPEC_Q[si++ % SPEC_Q.length];

    var qKind = /goal half pace/.test(q) ? "hm"
      : (/threshold|tempo/.test(q) ? "threshold"
      : (/5K effort/.test(q) ? "interval"
      : (/steady/.test(q) ? "steady" : "easy")));

    var fiveRuns = phase !== "Heat base";
    var qMiles = Math.min(8, Math.max(3, r5(m*0.19)));
    var rest = Math.max(3, m - long - qMiles);
    var u = rest/(fiveRuns ? 3 : 2);

    var sessions;
    if(w === N){
      sessions = [
        {day:"Mon", kind:"rest", title:"Rest, light lift only"},
        {day:"Tue", kind:"hm", title:"Sharpener", miles:3, detail:q},
        {day:"Wed", kind:"rest", title:"Rest, no lower body lifting"},
        {day:"Thu", kind:"easy", title:"Shakeout", miles:2, detail:"Easy with 4 x 20 second strides"},
        {day:"Fri", kind:"rest", title:"Rest, feet up, hydrate and salt"},
        {day:"Sat", kind:"recovery", title:"Shakeout", miles:1.5, detail:"15 minutes very easy, 3 strides"},
        {day:"Sun", kind:"hm", title:"RACE DAY", miles:HALF, detail:profile.raceName+". Even splits, do not bank time in the first 3 miles."}
      ];
    } else {
      sessions = [
        fiveRuns
          ? {day:"Mon", kind:"recovery", title:"Recovery jog", miles:r5(u*0.75), detail:"Flat, conversational, shorten stride"}
          : {day:"Mon", kind:"rest", title:"Rest or lift"},
        {day:"Tue", kind:"easy", title:"Easy plus strides", miles:r5(fiveRuns ? u*1.15 : u), detail:"Finish with 6 x 20 second strides"},
        {day:"Wed", kind:qKind, title:"Quality", miles:qMiles, detail:q+". Includes warmup and cooldown."},
        {day:"Thu", kind:"rest", title:"Rest or cross train"},
        {day:"Fri", kind:"easy", title:"Easy", miles:r5(fiveRuns ? u*1.1 : u), detail:"Pure aerobic, no pace pressure"},
        {day:"Sat", kind:"long", title:"Long run", miles:long,
          detail: (phase === "Race specific" || phase === "Taper") ? "Last 2 to 3 miles at goal half pace"
            : (phase === "Build" ? "Steady effort, last mile a touch quicker"
            : "Fully conversational, walk breaks are fine in the heat")},
        {day:"Sun", kind:"rest", title:"Rest"}
      ];
    }

    var mo = mon.getMonth();
    weeks.push({
      w:w, mon:ymd(mon), miles:m, long:long, phase:phase, isDown:isDown,
      sessions:sessions, paces:paces, heat:(mo >= 6 && mo <= 9),
      label: mon.toLocaleString("en-US",{month:"short"})+" "+mon.getDate()
    });
  }
  return { weeks:weeks, N:N };
}

function paceTextFor(kind, paces){
  function rng(a){ return fmtPace(a[0])+" to "+fmtPace(a[1]); }
  if(kind === "recovery") return rng(paces.recovery);
  if(kind === "easy") return rng(paces.easy);
  if(kind === "long") return rng(paces.long);
  if(kind === "steady") return fmtPace(paces.steady);
  if(kind === "threshold") return fmtPace(paces.threshold);
  if(kind === "interval") return fmtPace(paces.interval);
  if(kind === "hm") return fmtPace(paces.hm);
  return "";
}

/* ---------------------------- storage ---------------------------- */
var storageMode = "loading";

function probeStorage(){
  try {
    var t = "sub2:probe";
    localStorage.setItem(t, "1");
    var back = localStorage.getItem(t);
    localStorage.removeItem(t);
    return back === "1" ? "ok" : "off";
  } catch(e){ return "off"; }
}
function loadState(){
  try {
    var raw = localStorage.getItem(KEY);
    return raw ? JSON.parse(raw) : null;
  } catch(e){ return null; }
}
function persist(){
  if(storageMode === "off") return;
  try {
    localStorage.setItem(KEY, JSON.stringify({ runs:state.runs, done:state.done, profile:state.profile, v:1 }));
    setSaveChip("ok", Date.now());
  } catch(e){
    setSaveChip("error", null, e && e.message ? e.message : "write failed");
  }
}

/* ------------------------------ state ------------------------------ */
var state = { runs:[], done:{}, profile:Object.assign({}, DEFAULT_PROFILE) };
var tab = "dash";
var editingId = null;
var form = { effort:2 };
var openWeeks = {};
var showRestore = false;
var confirmReset = false;

/* ------------------------------ charts ------------------------------ */
function chartW(){
  var vw = Math.min(760, window.innerWidth || 760);
  return Math.max(270, Math.round(vw - 60));
}
function svgOpen(w,h){ return '<svg class="chart" viewBox="0 0 '+w+' '+h+'" width="'+w+'" height="'+h+'" xmlns="http://www.w3.org/2000/svg">'; }
function gridLine(x1,y1,x2,y2){ return '<line x1="'+x1+'" y1="'+y1+'" x2="'+x2+'" y2="'+y2+'" stroke="#222A36" stroke-width="1"/>'; }
function txt(x,y,s,fill,anchor,size){
  return '<text x="'+x+'" y="'+y+'" fill="'+(fill||"#5D6879")+'" font-size="'+(size||10)+'" text-anchor="'+(anchor||"middle")+'" font-family="ui-monospace,Menlo,monospace">'+esc(s)+'</text>';
}

function barChart(data){
  var W = chartW(), H = 210, L = 34, R = 8, T = 10, B = 26;
  if(!data.length) return '<div class="empty">No weeks to show yet.</div>';
  var vals = [];
  data.forEach(function(d){ vals.push(d.actual); if(d.target) vals.push(d.target); });
  var yMax = Math.max(1, Math.max.apply(null, vals)) * 1.15;
  var iw = W - L - R, ih = H - T - B;
  var band = iw / data.length;
  var bw = Math.min(30, band * 0.6);
  function X(i){ return L + band*i + band/2; }
  function Y(v){ return T + ih - (v/yMax)*ih; }

  var s = svgOpen(W,H);
  for(var g=0; g<=3; g++){
    var yv = yMax*g/3, y = Y(yv);
    s += gridLine(L, y, W-R, y);
    s += txt(L-6, y+3, Math.round(yv), "#5D6879", "end", 10);
  }
  data.forEach(function(d,i){
    if(d.actual > 0){
      var y = Y(d.actual);
      s += '<rect x="'+(X(i)-bw/2)+'" y="'+y+'" width="'+bw+'" height="'+(T+ih-y)+'" rx="3" fill="#FF6B35"/>';
    }
  });
  var pts = [], seg = [];
  data.forEach(function(d,i){
    if(d.target != null) seg.push(X(i)+","+Y(d.target));
    else { if(seg.length) pts.push(seg); seg = []; }
  });
  if(seg.length) pts.push(seg);
  pts.forEach(function(p){
    if(p.length > 1) s += '<polyline points="'+p.join(" ")+'" fill="none" stroke="#4CC9F0" stroke-width="2" stroke-dasharray="5 4"/>';
  });
  var step = Math.ceil(data.length/(W < 400 ? 4 : 6));
  data.forEach(function(d,i){
    if(i % step === 0 || i === data.length-1) s += txt(X(i), H-8, d.label, "#5D6879", "middle", 10);
  });
  return s + "</svg>";
}

function paceChart(series){
  var W = chartW(), H = 220, L = 52, R = 10, T = 12, B = 26;
  if(series.length < 2) return '<div class="empty">Two runs and the trend line starts drawing.</div>';
  var all = [];
  series.forEach(function(d){ all.push(d.raw, d.adj); });
  all.push(GOAL_PACE);
  var lo = Math.min.apply(null, all) - 20, hi = Math.max.apply(null, all) + 20;
  var iw = W - L - R, ih = H - T - B;
  function X(i){ return L + (series.length === 1 ? iw/2 : iw*i/(series.length-1)); }
  function Y(v){ return T + (v-lo)/((hi-lo)||1)*ih; }

  var s = svgOpen(W,H);
  for(var g=0; g<=3; g++){
    var pv = lo + (hi-lo)*g/3, y = Y(pv);
    s += gridLine(L, y, W-R, y);
    s += txt(L-7, y+3, fmtPace(pv), "#5D6879", "end", 10);
  }
  var gy = Y(GOAL_PACE);
  if(gy > T && gy < T+ih){
    s += '<line x1="'+L+'" y1="'+gy+'" x2="'+(W-R)+'" y2="'+gy+'" stroke="#5AD68A" stroke-width="1.5" stroke-dasharray="5 4"/>';
    s += txt(W-R-2, gy-6, "goal "+fmtPace(GOAL_PACE), "#5AD68A", "end", 10);
  }
  [["raw","#FF6B35"],["adj","#4CC9F0"]].forEach(function(pair){
    var key = pair[0], col = pair[1];
    var pts = series.map(function(d,i){ return X(i)+","+Y(d[key]); });
    s += '<polyline points="'+pts.join(" ")+'" fill="none" stroke="'+col+'" stroke-width="2" stroke-linejoin="round"/>';
    series.forEach(function(d,i){ s += '<circle cx="'+X(i)+'" cy="'+Y(d[key])+'" r="2.6" fill="'+col+'"/>'; });
  });
  var step = Math.ceil(series.length/(W < 400 ? 3 : 5));
  series.forEach(function(d,i){
    if(i % step === 0 || i === series.length-1) s += txt(X(i), H-8, d.label, "#5D6879", "middle", 10);
  });
  return s + "</svg>";
}

function scatterChart(points){
  var W = chartW(), H = 230, L = 52, R = 12, T = 12, B = 28;
  if(!points.length) return '<div class="empty">Add average heart rate to a run to plot efficiency.</div>';
  var hrs = points.map(function(p){ return p.hr; });
  var pcs = points.map(function(p){ return p.pace; });
  pcs.push(GOAL_PACE);
  var xlo = Math.min.apply(null,hrs)-6, xhi = Math.max.apply(null,hrs)+6;
  var ylo = Math.min.apply(null,pcs)-20, yhi = Math.max.apply(null,pcs)+20;
  var iw = W-L-R, ih = H-T-B;
  function X(v){ return L + (v-xlo)/((xhi-xlo)||1)*iw; }
  function Y(v){ return T + (v-ylo)/((yhi-ylo)||1)*ih; }

  var s = svgOpen(W,H);
  for(var g=0; g<=3; g++){
    var pv = ylo + (yhi-ylo)*g/3, y = Y(pv);
    s += gridLine(L, y, W-R, y);
    s += txt(L-7, y+3, fmtPace(pv), "#5D6879", "end", 10);
  }
  for(var g2=0; g2<=3; g2++){
    var hv = xlo + (xhi-xlo)*g2/3, x = X(hv);
    s += gridLine(x, T, x, T+ih);
    s += txt(x, H-9, Math.round(hv)+" bpm", "#5D6879", "middle", 10);
  }
  var gy = Y(GOAL_PACE);
  if(gy > T && gy < T+ih){
    s += '<line x1="'+L+'" y1="'+gy+'" x2="'+(W-R)+'" y2="'+gy+'" stroke="#5AD68A" stroke-width="1.5" stroke-dasharray="5 4"/>';
  }
  points.forEach(function(p){
    s += '<circle cx="'+X(p.hr)+'" cy="'+Y(p.pace)+'" r="5" fill="'+(TYPE_COLOR[p.type]||"#8A96A8")+'" fill-opacity="0.85"/>';
  });
  return s + "</svg>";
}

/* ------------------------------ derived ------------------------------ */
function baselineHalf(){ return riegel(3.10686, Number(state.profile.fiveKPRsec) || 1635, HALF); }
function bestEffort(){ return currentProjection(state.runs); }
function currentHalf(){
  var b = bestEffort(), base = baselineHalf();
  return b ? Math.min(b.projected, base) : base;
}
function thePlan(){ return buildPlan(state.profile, currentHalf()/HALF); }

/* ------------------------------ render ------------------------------ */
function statCard(k,v,n,color){
  return '<div class="stat"><div class="k">'+esc(k)+'</div><div class="v num"'+(color?' style="color:'+color+'"':'')+'>'+esc(v)+'</div>'+(n?'<div class="n">'+esc(n)+'</div>':'')+'</div>';
}

function setSaveChip(mode, at, reason){
  storageMode = mode === "error" ? storageMode : mode;
  var chip = document.getElementById("savechip");
  var t = document.getElementById("savetext");
  chip.setAttribute("data-mode", mode);
  if(mode === "ok") t.textContent = at ? "saved "+new Date(at).toLocaleTimeString([], {hour:"numeric", minute:"2-digit"}) : "saving on";
  else if(mode === "off") t.textContent = "not saving";
  else if(mode === "error") t.textContent = "save failed";
  else t.textContent = "checking";
  renderBanner(reason);
}

function renderBanner(reason){
  var el = document.getElementById("banner");
  if(storageMode === "off"){
    el.innerHTML = '<div class="warnbar">This browser is blocking local storage, most likely private browsing mode. The app works but forgets on close. Turn off private browsing, or use Copy backup under Settings before you leave.</div>';
  } else if(reason){
    el.innerHTML = '<div class="warnbar">A save failed: '+esc(reason)+'. Your data is still on screen. If the storage is full, clear an old backup and try again.</div>';
  } else {
    el.innerHTML = "";
  }
}

function renderDash(){
  var dec = state.runs.map(decorate).sort(function(a,b){ return a.date.localeCompare(b.date); });
  var plan = thePlan();
  var h = "";

  /* heat tax */
  var withTemp = dec.filter(function(r){ return r.tempF; });
  var heatRun = withTemp.length ? withTemp.reduce(function(a,b){ return b.tax > a.tax ? b : a; }) : null;
  var avgTax = dec.length ? dec.reduce(function(s,r){ return s+r.tax; },0)/dec.length : 0;

  h += '<section class="card"><div class="eyebrow">The heat tax</div>';
  if(heatRun){
    h += '<div class="tax">'
      + '<div class="taxcol"><div class="taxval num" style="color:'+tempColor(heatRun.tempF)+'">'+fmtPace(heatRun.pace)+'</div><div class="taxlab">what the watch said</div></div>'
      + '<div class="taxmid"><div class="d num">+'+Math.round(heatRun.tax)+'s</div><div class="l">per mile</div></div>'
      + '<div class="taxcol"><div class="taxval num" style="color:var(--dawn)">'+fmtPace(heatRun.adjPace)+'</div><div class="taxlab">worth at 60 degrees</div></div>'
      + '</div>'
      + '<div class="thermbar" style="background:linear-gradient(90deg,'+tempColor(heatRun.tempF)+',#4CC9F0)"></div>'
      + '<p class="sub" style="margin-top:12px">Your most heat taxed run, '+esc(shortDate(heatRun.date))+' at '+esc(heatRun.tempF)+' degrees. Across everything logged, Phoenix is charging you about '+Math.round(avgTax)+' seconds per mile.</p>';
  } else if(dec.length){
    h += '<div class="empty"><b>Add a temperature</b>Your runs are saved, but without the temperature there is nothing to correct. Edit one and put the number in.</div>';
  } else {
    h += '<div class="empty"><b>Nothing logged yet</b>Log one run and this turns into a side by side of your raw pace and what it was actually worth in 60 degree air.'
      + '<div class="btnrow" style="justify-content:center"><button class="btn" data-go="log">Log your first run</button></div></div>';
  }
  h += '</section>';

  /* goal */
  var base = baselineHalf(), cur = currentHalf(), best = bestEffort();
  var gap = base - GOAL_SEC;
  var pct = gap > 0 ? Math.max(0, Math.min(100, ((base-cur)/gap)*100)) : 100;
  h += '<section class="card"><div class="eyebrow">Progress to sub 2</div>'
    + '<h2>'+fmtClock(cur)+' projected</h2>'
    + '<p class="sub">'+(best
        ? 'From your '+best.dist+' mile effort on '+esc(shortDate(best.date))+', corrected to 60 degrees.'
        : 'From your 5K personal record. Log a run of 2 or more miles at effort 3 or higher to replace this.')+'</p>'
    + '<div class="raceline"><div class="track"><div class="marker" style="left:'+pct+'%"></div></div>'
    + '<div class="tickrow"><span>starting point<b class="num">'+fmtClock(base)+'</b></span>'
    + '<span style="text-align:right;color:var(--go)">the goal<b class="num">1:59:59</b></span></div></div>'
    + '<div class="grid3" style="margin-top:14px">'
    + statCard("Closed", Math.round(pct)+"%", "of the gap", "var(--go)")
    + statCard("Still to find", fmtClock(Math.max(0, cur-GOAL_SEC)), "over 13.1")
    + statCard("Goal pace", fmtPace(GOAL_PACE), "per mile", "var(--dawn)")
    + '</div></section>';

  /* weekly mileage */
  var map = {};
  dec.forEach(function(r){
    var k = ymd(mondayOf(parseYMD(r.date)));
    map[k] = (map[k]||0) + r.dist;
  });
  var planMap = {};
  plan.weeks.forEach(function(w){ planMap[w.mon] = w.miles; });
  var keys = {};
  Object.keys(map).forEach(function(k){ keys[k] = 1; });
  plan.weeks.slice(0,8).forEach(function(w){ keys[w.mon] = 1; });
  var weekly = Object.keys(keys).sort().slice(-14).map(function(k){
    return { k:k, label:shortDate(k), actual:Math.round((map[k]||0)*10)/10, target:planMap[k] != null ? planMap[k] : null };
  });
  var thisMon = ymd(mondayOf(new Date()));
  var tw = weekly.filter(function(x){ return x.k === thisMon; })[0];
  var last7 = dec.filter(function(r){ return parseYMD(r.date) >= addDays(new Date(),-7); });
  var total = dec.reduce(function(s,r){ return s+r.dist; },0);

  h += '<section class="card"><div class="eyebrow">Weekly mileage</div>'
    + '<div class="grid3" style="margin-bottom:12px">'
    + statCard("This week", (tw ? tw.actual : 0).toFixed(1), tw && tw.target ? "target "+tw.target : "no target")
    + statCard("Last 7 days", last7.reduce(function(s,r){ return s+r.dist; },0).toFixed(1), last7.length+" runs")
    + statCard("All time", total.toFixed(1), dec.length+" runs")
    + '</div>'
    + barChart(weekly)
    + '<div class="legend"><span><i class="dot" style="background:#FF6B35"></i>Logged</span><span><i class="dot" style="background:#4CC9F0"></i>Plan target</span></div>'
    + '</section>';

  /* pace trend */
  var series = dec.filter(function(r){ return r.dist >= 1; }).map(function(r){
    return { label:shortDate(r.date), raw:r.pace, adj:r.adjPace };
  });
  h += '<section class="card"><div class="eyebrow">Pace trend</div>'
    + '<h2 style="margin-bottom:10px">Raw against heat corrected</h2>'
    + paceChart(series)
    + (series.length > 1 ? '<div class="legend"><span><i class="dot" style="background:#FF6B35"></i>Raw pace</span><span><i class="dot" style="background:#4CC9F0"></i>Corrected to 60 degrees</span></div>' : '')
    + '</section>';

  /* efficiency */
  var pts = dec.filter(function(r){ return r.avgHR && r.dist >= 1; }).map(function(r){
    return { hr:Number(r.avgHR), pace:r.adjPace, type:r.type };
  });
  var types = {};
  pts.forEach(function(p){ types[p.type] = 1; });
  h += '<section class="card"><div class="eyebrow">Aerobic efficiency</div>'
    + '<h2 style="margin-bottom:4px">Heart rate against corrected pace</h2>'
    + '<p class="sub" style="margin-bottom:10px">Points drifting down and left over the months is the whole game: same effort, more speed.</p>'
    + scatterChart(pts)
    + (pts.length ? '<div class="legend">'+Object.keys(types).map(function(t){
        return '<span><i class="dot" style="background:'+(TYPE_COLOR[t]||"#8A96A8")+'"></i>'+esc(t)+'</span>';
      }).join("")+'</div>' : '')
    + '</section>';

  /* table */
  if(dec.length){
    h += '<section class="card"><div class="eyebrow">Every run, corrected</div><div class="scroll"><table>'
      + '<thead><tr><th>Date</th><th>Mi</th><th>Temp</th><th>Pace</th><th>At 60</th><th>Gain</th><th>Avg HR</th></tr></thead><tbody>';
    dec.slice().reverse().forEach(function(r){
      h += '<tr><td style="color:var(--dim)">'+esc(shortDate(r.date))+'</td>'
        + '<td class="num">'+r.dist.toFixed(1)+'</td>'
        + '<td class="num" style="color:'+tempColor(r.tempF)+'">'+(r.tempF ? esc(r.tempF) : "n/a")+'</td>'
        + '<td class="num">'+fmtPace(r.pace)+'</td>'
        + '<td class="num adj">'+fmtPace(r.adjPace)+'</td>'
        + '<td class="num" style="color:var(--sun)">'+(r.tax >= 1 ? Math.round(r.tax)+"s" : "n/a")+'</td>'
        + '<td class="num">'+(r.avgHR ? esc(r.avgHR) : "n/a")+'</td></tr>';
    });
    h += '</tbody></table></div></section>';
  }

  document.getElementById("view-dash").innerHTML = h;
}

function renderHistory(){
  var list = state.runs.map(decorate).sort(function(a,b){ return b.date.localeCompare(a.date); });
  if(!list.length){
    document.getElementById("history").innerHTML = '<div class="empty"><b>No runs yet</b>Saved runs land here, newest first.</div>';
    return;
  }
  var h = '<div class="rows">';
  list.forEach(function(r){
    h += '<div class="row">'
      + '<div class="rail" style="background:'+(r.tempF ? tempColor(r.tempF) : "var(--line)")+'"></div>'
      + '<div class="rbody"><div class="rtop">'
      + '<span class="rdate">'+esc(shortDate(r.date))+' · '+esc(r.type)+'</span>'
      + '<span class="rdist num">'+r.dist.toFixed(2)+' mi</span></div>'
      + '<div class="rmeta"><span>'+fmtClock(r.dur)+'</span>'
      + '<span><b class="num">'+fmtPace(r.pace)+'</b> per mile</span>'
      + (r.tempF ? '<span class="adj num">'+fmtPace(r.adjPace)+' at 60</span><span>'+esc(r.tempF)+' degrees</span>' : '')
      + (r.avgHR ? '<span>'+esc(r.avgHR)+(r.maxHR ? " / "+esc(r.maxHR) : "")+' bpm</span>' : '')
      + '<span>effort '+esc(r.effort)+'</span></div>'
      + (r.notes ? '<div class="note">'+esc(r.notes)+'</div>' : '')
      + '<div class="rowacts"><button class="lnk" data-edit="'+esc(r.id)+'">Edit</button>'
      + '<button class="lnk" data-del="'+esc(r.id)+'">Delete</button></div>'
      + '</div></div>';
  });
  document.getElementById("history").innerHTML = h + '</div>';
}

function renderPlan(){
  var plan = thePlan();
  var thisMon = ymd(mondayOf(new Date()));
  var runDates = {};
  state.runs.forEach(function(r){ runDates[r.date] = 1; });

  var totalSessions = 0, doneCount = 0;
  plan.weeks.forEach(function(w){ totalSessions += w.sessions.filter(function(s){ return s.kind !== "rest"; }).length; });
  Object.keys(state.done).forEach(function(k){ if(state.done[k]) doneCount++; });
  var peak = Math.max.apply(null, plan.weeks.map(function(w){ return w.miles; }));

  if(!Object.keys(openWeeks).length){
    var cw = plan.weeks.filter(function(w){ return w.mon === thisMon; })[0] || plan.weeks[0];
    openWeeks[cw.w] = true;
  }

  var h = '<section class="card"><div class="eyebrow">The build</div>'
    + '<h2>'+plan.N+' weeks to '+esc(state.profile.raceName)+'</h2>'
    + '<p class="sub">Mileage climbs 7 percent a week at most, with a cutback every fourth week and a hard ceiling of 12 miles on the long run until race day. That is the guardrail against another IT band flare.</p>'
    + '<div class="grid3" style="margin-top:13px">'
    + statCard("Sessions done", String(doneCount), "of "+totalSessions, "var(--go)")
    + statCard("Peak week", String(peak), "miles")
    + statCard("Longest run", "12", "miles before race day")
    + '</div></section>';

  plan.weeks.forEach(function(w){
    var runSess = w.sessions.filter(function(s){ return s.kind !== "rest"; });
    var nDone = runSess.filter(function(s){ return state.done[w.w+":"+s.day]; }).length;
    var isNow = w.mon === thisMon;
    var isOpen = !!openWeeks[w.w];

    h += '<div class="week" data-now="'+(isNow?"1":"0")+'">'
      + '<div class="whead" data-week="'+w.w+'">'
      + '<div class="wno">week<b class="num">'+w.w+'</b></div>'
      + '<div class="wmid"><div class="wphase" style="color:'+PHASE_COLOR[w.phase]+'">'+esc(w.phase)+(w.isDown ? " · cutback" : "")
      + (isNow ? '<span class="tagline" style="color:var(--ember);border-color:var(--ember)">this week</span>' : '')+'</div>'
      + '<div class="wmiles"><span class="num">'+esc(w.label)+'</span> · <span class="num">'+w.miles+'</span> miles · long run <span class="num">'+(w.long === HALF ? "13.1" : w.long)+'</span></div></div>'
      + '<div class="wprog num">'+nDone+'/'+runSess.length+'</div></div>';

    if(isOpen){
      h += '<div class="wbody">';
      if(w.heat){
        h += '<div class="heatnote">Phoenix heat window. Run before sunrise or move it to a treadmill, carry fluid on anything past 40 minutes, and let effort set the pace rather than the number on your watch.</div>';
      }
      w.sessions.forEach(function(s){
        var key = w.w+":"+s.day;
        if(s.kind === "rest"){
          h += '<div class="sess rest"><div class="box" style="visibility:hidden"></div><div class="sday">'+esc(s.day)+'</div>'
            + '<div class="sbody"><div class="stitle" style="font-weight:500">'+esc(s.title)+'</div></div></div>';
          return;
        }
        var isDone = !!state.done[key];
        var date = ymd(addDays(parseYMD(w.mon), DAYS.indexOf(s.day)));
        var logged = !!runDates[date];
        h += '<div class="sess">'
          + '<button class="box" data-sess="'+key+'" data-on="'+(isDone?"1":"0")+'" aria-label="mark complete">'+(isDone?"✓":"")+'</button>'
          + '<div class="sday">'+esc(s.day)+'</div><div class="sbody">'
          + '<div class="stitle'+(isDone?" done":"")+'">'+esc(s.title)+' · <span class="num">'+(s.miles === HALF ? "13.1" : s.miles)+'</span> mi'
          + (logged && !isDone ? '<span class="tagline" style="color:var(--go);border-color:#25412F">run logged</span>' : '')+'</div>'
          + '<div class="sdet">'+esc(s.detail)+'</div>'
          + '<div class="space num">'+esc(paceTextFor(s.kind, w.paces))+' per mile</div>'
          + '</div></div>';
      });
      h += '</div>';
    }
    h += '</div>';
  });

  h += '<section class="card"><div class="eyebrow">How the target paces move</div>'
    + '<p class="sub">Every pace above is pulled off your current projected half marathon pace, then walked toward '+fmtPace(GOAL_PACE)+' as the weeks go by. Easy runs sit roughly two and a half to three minutes slower than that, threshold sits about 20 seconds faster, and interval work about 50 seconds faster. Log faster efforts and the whole ladder tightens on its own.</p></section>';

  document.getElementById("view-plan").innerHTML = h;
}

function renderSettings(){
  document.getElementById("s-date").value = state.profile.raceDate;
  document.getElementById("s-name").value = state.profile.raceName;
  document.getElementById("s-mile").value = fmtPace(state.profile.milePRsec);
  document.getElementById("s-5k").value = fmtClock(state.profile.fiveKPRsec);
  document.getElementById("s-start").value = state.profile.startMileage;
  document.getElementById("s-peak").value = state.profile.peakMileage;

  var backup = JSON.stringify({ runs:state.runs, done:state.done, profile:state.profile, v:1 });
  document.getElementById("backupArea").innerHTML = showRestore
    ? '<label for="restoreBox">Paste a backup</label>'
      + '<textarea class="backup" id="restoreBox" placeholder=\'{"runs":[...\'></textarea>'
      + '<div class="hint">This replaces everything currently in the app.</div>'
      + '<div class="btnrow"><button class="btn" id="doRestore">Restore</button></div>'
    : '<label for="backupBox">Backup text</label><textarea class="backup" id="backupBox" readonly>'+esc(backup)+'</textarea>';

  document.getElementById("toggleRestore").textContent = showRestore ? "Cancel restore" : "Restore from backup";

  document.getElementById("dataStats").innerHTML =
    statCard("Runs saved", String(state.runs.length)) +
    statCard("Sessions checked", String(Object.keys(state.done).length));

  document.getElementById("resetRow").innerHTML = confirmReset
    ? '<button class="btn danger" id="confirmReset">Yes, delete every run and check mark</button><button class="btn ghost" id="keepData">Keep my data</button>'
    : '<button class="btn danger" id="resetBtn">Clear all data</button>';
}

function setMsg(text, good){
  document.getElementById("setMsg").innerHTML = text ? '<div class="'+(good?"okbar":"warnbar")+'">'+esc(text)+'</div>' : "";
}

function renderHeader(){
  var days = Math.max(0, Math.ceil((parseYMD(state.profile.raceDate) - new Date())/86400000));
  document.getElementById("daysout").textContent = days+" days";
}

function renderTabs(){
  Array.prototype.forEach.call(document.querySelectorAll(".tab"), function(b){
    b.setAttribute("data-on", b.getAttribute("data-tab") === tab ? "1" : "0");
  });
  ["dash","log","plan","set"].forEach(function(id){
    document.getElementById("view-"+id).classList.toggle("hidden", id !== tab);
  });
}

function renderAll(){
  renderHeader();
  renderTabs();
  renderDash();
  renderHistory();
  renderPlan();
  renderSettings();
}

/* ------------------------------ form ------------------------------ */
function readForm(){
  return {
    date: document.getElementById("f-date").value,
    dist: Number(document.getElementById("f-dist").value) || 0,
    durationSec: parseDuration(document.getElementById("f-dur").value),
    durText: document.getElementById("f-dur").value.trim(),
    avgHR: document.getElementById("f-ahr").value,
    maxHR: document.getElementById("f-mhr").value,
    tempF: document.getElementById("f-temp").value,
    type: document.getElementById("f-type").value,
    notes: document.getElementById("f-notes").value
  };
}
function clearForm(){
  document.getElementById("f-date").value = ymd(new Date());
  ["f-dist","f-dur","f-ahr","f-mhr","f-temp","f-notes"].forEach(function(id){ document.getElementById(id).value = ""; });
  document.getElementById("f-type").value = "easy";
  form.effort = 2;
  editingId = null;
  document.getElementById("formTitle").textContent = "New run";
  document.getElementById("saveRun").textContent = "Save run";
  document.getElementById("cancelEdit").classList.add("hidden");
  syncChips();
  updateLive();
}
function syncChips(){
  Array.prototype.forEach.call(document.querySelectorAll("[data-effort]"), function(b){
    b.setAttribute("data-on", Number(b.getAttribute("data-effort")) === form.effort ? "1" : "0");
  });
}
function updateLive(){
  var f = readForm();
  var durEl = document.getElementById("f-dur");
  var hint = document.getElementById("durHint");
  var bad = f.durText.length > 0 && f.durationSec === 0;
  durEl.classList.toggle("bad", bad);
  hint.classList.toggle("bad", bad);
  hint.textContent = bad
    ? "Use minutes colon seconds, like 48:30. Over an hour, use 1:12:45."
    : (f.durationSec > 0 ? durationReadback(f.durationSec) : "Minutes colon seconds, like 48:30. Over an hour, use 1:12:45.");

  var valid = f.dist > 0 && f.durationSec > 0;
  document.getElementById("saveRun").disabled = !valid;
  document.getElementById("formNote").classList.toggle("hidden", valid);

  var live = document.getElementById("livePace");
  if(valid){
    var pace = f.durationSec / f.dist;
    var adj = pace / heatFactor(f.tempF);
    live.innerHTML = '<div class="grid3" style="margin-top:13px">'
      + statCard("Pace", fmtPace(pace), "per mile", tempColor(f.tempF))
      + statCard("At 60 degrees", fmtPace(adj), "per mile", "var(--dawn)")
      + statCard("Heat tax", Math.round(pace-adj)+"s", "per mile", "var(--sun)")
      + '</div>';
  } else live.innerHTML = "";
}
function saveRun(){
  var f = readForm();
  if(!(f.dist > 0 && f.durationSec > 0)) return;
  var rec = {
    id: editingId || ("r"+Date.now()),
    date: f.date || ymd(new Date()),
    distance: f.dist,
    durationSec: f.durationSec,
    avgHR: f.avgHR ? Number(f.avgHR) : null,
    maxHR: f.maxHR ? Number(f.maxHR) : null,
    effort: form.effort,
    tempF: f.tempF ? Number(f.tempF) : null,
    type: f.type,
    notes: f.notes.trim()
  };
  if(editingId){
    state.runs = state.runs.map(function(r){ return r.id === editingId ? rec : r; });
  } else {
    state.runs.push(rec);
  }
  state.runs.sort(function(a,b){ return a.date.localeCompare(b.date); });
  persist();
  clearForm();
  renderAll();
}
function editRun(id){
  var r = state.runs.filter(function(x){ return x.id === id; })[0];
  if(!r) return;
  editingId = id;
  document.getElementById("f-date").value = r.date;
  document.getElementById("f-dist").value = r.distance;
  document.getElementById("f-dur").value = fmtClock(r.durationSec);
  document.getElementById("f-ahr").value = r.avgHR == null ? "" : r.avgHR;
  document.getElementById("f-mhr").value = r.maxHR == null ? "" : r.maxHR;
  document.getElementById("f-temp").value = r.tempF == null ? "" : r.tempF;
  document.getElementById("f-type").value = r.type;
  document.getElementById("f-notes").value = r.notes || "";
  form.effort = Number(r.effort) || 2;
  document.getElementById("formTitle").textContent = "Edit run";
  document.getElementById("saveRun").textContent = "Save changes";
  document.getElementById("cancelEdit").classList.remove("hidden");
  syncChips();
  updateLive();
  tab = "log";
  renderTabs();
  window.scrollTo({ top:0, behavior:"smooth" });
}

/* ------------------------------ events ------------------------------ */
document.getElementById("tabs").addEventListener("click", function(e){
  var b = e.target.closest("[data-tab]");
  if(!b) return;
  tab = b.getAttribute("data-tab");
  renderTabs();
  window.scrollTo({ top:0 });
});

document.addEventListener("click", function(e){
  var t = e.target;
  if(!t || !t.closest) return;

  var go = t.closest("[data-go]");
  if(go){ tab = go.getAttribute("data-go"); renderTabs(); window.scrollTo({top:0}); return; }

  var chip = t.closest("[data-effort]");
  if(chip){ form.effort = Number(chip.getAttribute("data-effort")); syncChips(); return; }

  var ed = t.closest("[data-edit]");
  if(ed){ editRun(ed.getAttribute("data-edit")); return; }

  var del = t.closest("[data-del]");
  if(del){
    var id = del.getAttribute("data-del");
    state.runs = state.runs.filter(function(r){ return r.id !== id; });
    persist(); renderAll(); return;
  }

  var wk = t.closest("[data-week]");
  if(wk){
    var n = wk.getAttribute("data-week");
    openWeeks[n] = !openWeeks[n];
    renderPlan(); return;
  }

  var sess = t.closest("[data-sess]");
  if(sess){
    var key = sess.getAttribute("data-sess");
    if(state.done[key]) delete state.done[key]; else state.done[key] = true;
    persist(); renderPlan(); renderDash(); return;
  }

  if(t.id === "saveRun"){ saveRun(); return; }
  if(t.id === "cancelEdit"){ clearForm(); return; }

  if(t.id === "toggleRestore"){ showRestore = !showRestore; setMsg(""); renderSettings(); return; }
  if(t.id === "copyBackup"){
    var text = JSON.stringify({ runs:state.runs, done:state.done, profile:state.profile, v:1 });
    if(navigator.clipboard && navigator.clipboard.writeText){
      navigator.clipboard.writeText(text).then(function(){
        setMsg("Backup copied. Paste it somewhere safe, like a note to yourself.", true);
      }).catch(function(){
        setMsg("Clipboard is blocked here. Long press the text below, select all, and copy it by hand.");
      });
    } else {
      setMsg("Clipboard is blocked here. Long press the text below, select all, and copy it by hand.");
    }
    return;
  }
  if(t.id === "doRestore"){
    var box = document.getElementById("restoreBox");
    try {
      var o = JSON.parse(box.value);
      if(!o || !Array.isArray(o.runs)) throw new Error("shape");
      state.runs = o.runs;
      state.done = (o.done && typeof o.done === "object") ? o.done : {};
      state.profile = Object.assign({}, DEFAULT_PROFILE, o.profile || {});
      showRestore = false;
      persist();
      renderAll();
      setMsg("Restored "+o.runs.length+" run"+(o.runs.length === 1 ? "" : "s")+".", true);
    } catch(err){
      setMsg("That text did not parse. Paste the whole backup, opening brace to closing brace.");
    }
    return;
  }

  if(t.id === "resetBtn"){ confirmReset = true; setMsg(""); renderSettings(); return; }
  if(t.id === "keepData"){ confirmReset = false; renderSettings(); return; }
  if(t.id === "confirmReset"){
    try { localStorage.removeItem(KEY); } catch(err){}
    state = { runs:[], done:{}, profile:Object.assign({}, DEFAULT_PROFILE) };
    openWeeks = {}; confirmReset = false;
    renderAll();
    setMsg("Cleared. Fresh slate.", true);
    return;
  }
});

["f-dist","f-dur","f-temp"].forEach(function(id){
  document.getElementById(id).addEventListener("input", updateLive);
});

document.getElementById("s-date").addEventListener("change", function(e){
  state.profile.raceDate = e.target.value; persist(); openWeeks = {}; renderAll();
});
document.getElementById("s-name").addEventListener("input", function(e){
  state.profile.raceName = e.target.value; persist(); renderPlan();
});
document.getElementById("s-mile").addEventListener("change", function(e){
  var v = parseMMSS(e.target.value); if(v){ state.profile.milePRsec = v; persist(); }
});
document.getElementById("s-5k").addEventListener("change", function(e){
  var v = parseMMSS(e.target.value); if(v){ state.profile.fiveKPRsec = v; persist(); renderAll(); }
});
document.getElementById("s-start").addEventListener("change", function(e){
  state.profile.startMileage = Number(e.target.value) || 14; persist(); renderPlan(); renderDash();
});
document.getElementById("s-peak").addEventListener("change", function(e){
  state.profile.peakMileage = Number(e.target.value) || 34; persist(); renderPlan(); renderDash();
});

var resizeTimer = null;
window.addEventListener("resize", function(){
  clearTimeout(resizeTimer);
  resizeTimer = setTimeout(function(){ if(tab === "dash") renderDash(); }, 200);
});

/* ------------------------------ boot ------------------------------ */
(function boot(){
  storageMode = probeStorage();
  if(storageMode === "ok"){
    var s = loadState();
    if(s){
      state.runs = Array.isArray(s.runs) ? s.runs : [];
      state.done = (s.done && typeof s.done === "object") ? s.done : {};
      state.profile = Object.assign({}, DEFAULT_PROFILE, s.profile || {});
    }
    setSaveChip("ok", null);
  } else {
    setSaveChip("off");
  }
  clearForm();
  renderAll();
})();
</script>
</body>
</html>
