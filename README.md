<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1.0"/>
<title>HoopsDraft — 4v4 Team Builder</title>
<style>
/* ═══════════════════════════════════════════════════
   HOOPSDRAFT  |  Self-Contained  |  No CDN Required
   Aesthetic: Hardwood Luxury — deep walnut + fire
   ═══════════════════════════════════════════════════ */
@import url('https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@400;600;700;800;900&family=Barlow:wght@300;400;500;600&display=swap');

*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}

:root{
  --bg:#0d0d0d;
  --court:#141210;
  --wood:#1a1510;
  --wood2:#211b14;
  --wood3:#2a2219;
  --line:#3d3020;
  --line2:rgba(255,255,255,0.07);
  --fire:#ff5722;
  --fire2:#ff8a50;
  --gold:#f0a500;
  --chalk:#f5f0e8;
  --chalk2:rgba(245,240,232,0.65);
  --chalk3:rgba(245,240,232,0.3);
  --chalk4:rgba(245,240,232,0.1);
  --green:#4caf7d;
  --blue:#4aa8e0;
  --red:#e05454;
  --r:10px;
  --r2:16px;
}

html{scroll-behavior:smooth}
body{
  background:var(--bg);
  color:var(--chalk);
  font-family:'Barlow',sans-serif;
  font-size:15px;
  min-height:100vh;
  overflow-x:hidden;
}

/* ── COURT LINES BG ─────── */
body::before{
  content:'';position:fixed;inset:0;z-index:0;pointer-events:none;
  background:
    radial-gradient(ellipse 100% 60% at 50% 0%,rgba(255,87,34,0.06) 0%,transparent 60%),
    radial-gradient(ellipse 80% 40% at 80% 100%,rgba(240,165,0,0.04) 0%,transparent 50%),
    repeating-linear-gradient(0deg,transparent,transparent 79px,rgba(255,255,255,0.018) 80px),
    repeating-linear-gradient(90deg,transparent,transparent 79px,rgba(255,255,255,0.018) 80px);
}

/* ── SCROLLBAR ─────────── */
::-webkit-scrollbar{width:6px;height:6px}
::-webkit-scrollbar-track{background:var(--bg)}
::-webkit-scrollbar-thumb{background:var(--line);border-radius:3px}
::-webkit-scrollbar-thumb:hover{background:#4a3c2a}

/* ═══════════════════════ LAYOUT ═══════════════════ */
#app{position:relative;z-index:1;max-width:1380px;margin:0 auto;padding:0 1.5rem}

/* ── HEADER ─────────────── */
.hdr{
  display:flex;align-items:center;justify-content:space-between;
  padding:1.25rem 0;
  border-bottom:1px solid var(--line);
  margin-bottom:2rem;
  position:sticky;top:0;z-index:200;
  background:rgba(13,13,13,0.92);backdrop-filter:blur(16px);
  margin-left:-1.5rem;margin-right:-1.5rem;
  padding-left:1.5rem;padding-right:1.5rem;
}
.logo{
  font-family:'Barlow Condensed',sans-serif;
  font-size:2rem;font-weight:900;letter-spacing:.06em;
  display:flex;align-items:center;gap:.5rem;
  color:var(--chalk);
}
.logo-ball{font-size:1.6rem;filter:drop-shadow(0 0 8px rgba(255,87,34,.5))}
.logo em{color:var(--fire);font-style:normal}

.hdr-tabs{display:flex;gap:.25rem}
.tab{
  font-family:'Barlow Condensed',sans-serif;font-weight:700;font-size:.95rem;
  letter-spacing:.08em;text-transform:uppercase;
  padding:8px 20px;border-radius:8px;cursor:pointer;
  background:transparent;border:none;color:var(--chalk3);
  transition:.2s;
}
.tab:hover{color:var(--chalk);background:var(--chalk4)}
.tab.active{color:var(--fire);background:rgba(255,87,34,.12)}
.tab-badge{
  display:inline-flex;align-items:center;justify-content:center;
  width:18px;height:18px;border-radius:50%;
  background:var(--fire);color:#fff;font-size:.65rem;font-weight:700;
  margin-left:5px;vertical-align:middle;
}

/* ═══════════════════════ PANELS ════════════════════ */
.panel{display:none;animation:fadeIn .25s ease}
.panel.active{display:block}
@keyframes fadeIn{from{opacity:0;transform:translateY(6px)}to{opacity:1;transform:none}}

/* ── PAGE TITLES ─────────── */
.page-title{
  font-family:'Barlow Condensed',sans-serif;
  font-size:clamp(2.4rem,5vw,3.8rem);font-weight:900;
  letter-spacing:.04em;line-height:.95;
  color:var(--chalk);
  margin-bottom:.35rem;
}
.page-sub{color:var(--chalk3);font-size:.95rem;margin-bottom:2rem}
.page-title span{color:var(--fire)}

/* ── SECTION BOX ─────────── */
.box{
  background:var(--wood);
  border:1px solid var(--line);
  border-radius:var(--r2);
  overflow:hidden;
}
.box-hdr{
  display:flex;align-items:center;justify-content:space-between;
  padding:1rem 1.5rem;
  background:var(--wood2);
  border-bottom:1px solid var(--line);
  flex-wrap:wrap;gap:.75rem;
}
.box-title{
  font-family:'Barlow Condensed',sans-serif;
  font-size:1.2rem;font-weight:800;letter-spacing:.08em;text-transform:uppercase;
  color:var(--chalk);
  display:flex;align-items:center;gap:.6rem;
}
.box-title-icon{color:var(--fire);font-size:1.1em}

/* ═══════════════════════ BUTTONS ════════════════════ */
.btn{
  display:inline-flex;align-items:center;gap:6px;
  padding:9px 20px;border-radius:8px;
  font-family:'Barlow Condensed',sans-serif;
  font-size:.95rem;font-weight:700;letter-spacing:.06em;text-transform:uppercase;
  cursor:pointer;border:none;transition:.18s;white-space:nowrap;text-decoration:none;
}
.btn-fire{background:var(--fire);color:#fff}
.btn-fire:hover{background:#ff7043;transform:translateY(-1px);box-shadow:0 4px 20px rgba(255,87,34,.35)}
.btn-ghost{background:var(--wood3);color:var(--chalk2);border:1px solid var(--line)}
.btn-ghost:hover{background:var(--wood2);color:var(--chalk);border-color:var(--chalk3)}
.btn-gold{background:var(--gold);color:#1a1000}
.btn-gold:hover{background:#f5b520}
.btn-danger{background:rgba(224,84,84,.15);color:var(--red);border:1px solid rgba(224,84,84,.3)}
.btn-danger:hover{background:rgba(224,84,84,.25)}
.btn-sm{padding:6px 14px;font-size:.85rem}
.btn-lg{padding:13px 32px;font-size:1.15rem}
.btn:disabled{opacity:.35;cursor:not-allowed;transform:none !important;box-shadow:none !important}

/* ═══════════════════════ FORMS ═══════════════════════ */
.form-grid{
  display:grid;
  grid-template-columns:2fr repeat(5,1fr) 1.5fr 1.5fr;
  gap:.85rem;
  padding:1.25rem 1.5rem;
}
@media(max-width:960px){.form-grid{grid-template-columns:1fr 1fr 1fr}}
@media(max-width:540px){.form-grid{grid-template-columns:1fr}}
.field{display:flex;flex-direction:column;gap:5px}
.field label{
  font-size:.7rem;font-weight:600;text-transform:uppercase;
  letter-spacing:.1em;color:var(--chalk3);
}
.field label .tip{font-weight:400;text-transform:none;letter-spacing:0;color:var(--chalk4)}
.field input,.field select{
  background:var(--wood3);border:1px solid var(--line);
  border-radius:7px;color:var(--chalk);
  padding:9px 12px;font-family:'Barlow',sans-serif;font-size:.9rem;
  transition:border-color .18s;
}
.field input:focus,.field select:focus{outline:none;border-color:var(--fire)}
.field select option{background:var(--wood2)}
.form-actions{
  display:flex;gap:.6rem;padding:.75rem 1.5rem 1.25rem;
  border-top:1px solid var(--line);background:var(--wood2);
}

/* ═══════════════════════ TABLES ══════════════════════ */
.tbl-wrap{overflow-x:auto}
table{width:100%;border-collapse:collapse;font-size:.88rem}
thead{background:var(--wood2)}
th{
  padding:10px 14px;text-align:left;
  font-size:.68rem;text-transform:uppercase;letter-spacing:.1em;
  color:var(--chalk3);font-weight:600;
  border-bottom:1px solid var(--line);
  white-space:nowrap;
}
td{
  padding:10px 14px;
  border-bottom:1px solid rgba(255,255,255,0.04);
  color:var(--chalk);vertical-align:middle;
}
tbody tr{background:var(--wood);transition:.15s}
tbody tr:hover{background:var(--wood2)}
tbody tr:last-child td{border-bottom:none}
.empty-row td{text-align:center;color:var(--chalk4);padding:3.5rem;font-style:italic}

/* ─ OVR ────────── */
.ovr{
  font-family:'Barlow Condensed',sans-serif;
  font-size:1.2rem;font-weight:800;
}
.ovr-s{color:var(--green)}
.ovr-m{color:var(--gold)}
.ovr-l{color:var(--red)}

/* ─ SKILL BARS ─── */
.sbar{display:flex;align-items:center;gap:6px;min-width:60px}
.sbar-v{min-width:14px;text-align:right;font-weight:600;font-size:.85rem}
.sbar-t{flex:1;height:4px;background:var(--wood3);border-radius:2px;min-width:30px}
.sbar-f{height:100%;border-radius:2px;background:linear-gradient(90deg,var(--gold),var(--fire));transition:width .5s ease}

/* ─ HEIGHT TAGS ── */
.htag{
  display:inline-flex;align-items:center;gap:4px;
  padding:3px 9px;border-radius:20px;
  font-size:.72rem;font-weight:700;text-transform:uppercase;letter-spacing:.05em;
}
.htag-big{background:rgba(74,168,224,.15);color:var(--blue)}
.htag-medium{background:rgba(240,165,0,.15);color:var(--gold)}
.htag-small{background:rgba(76,175,125,.15);color:var(--green)}

/* ─ DELETE BTN ─── */
.del-btn{
  background:none;border:none;cursor:pointer;
  color:var(--chalk4);font-size:.95rem;padding:4px 8px;border-radius:6px;
  transition:.18s;
}
.del-btn:hover{background:rgba(224,84,84,.15);color:var(--red)}

/* ─ EDIT BTN ─── */
.edit-btn{
  background:none;border:none;cursor:pointer;
  color:var(--chalk4);font-size:.9rem;padding:4px 8px;border-radius:6px;
  transition:.18s;
}
.edit-btn:hover{background:rgba(240,165,0,.15);color:var(--gold)}

/* ═══════════════════ ROSTER SELECT PANEL ════════════════ */
.match-controls{
  display:flex;align-items:center;justify-content:space-between;
  flex-wrap:wrap;gap:1rem;
  padding:1.25rem 1.5rem;
}
.active-count{
  font-family:'Barlow Condensed',sans-serif;
  font-size:1.4rem;font-weight:800;letter-spacing:.04em;
}
.active-count span{color:var(--fire)}
.match-controls .hint{color:var(--chalk3);font-size:.85rem}

.player-select-grid{
  display:grid;
  grid-template-columns:repeat(auto-fill,minmax(220px,1fr));
  gap:.85rem;
  padding:1.25rem 1.5rem;
}
.player-card{
  background:var(--wood2);
  border:2px solid var(--line);
  border-radius:var(--r);
  padding:.9rem 1rem;
  cursor:pointer;
  transition:.2s;
  user-select:none;
  position:relative;
  overflow:hidden;
}
.player-card::before{
  content:'';position:absolute;inset:0;
  background:linear-gradient(135deg,rgba(255,87,34,0) 0%,rgba(255,87,34,.06) 100%);
  opacity:0;transition:.2s;
}
.player-card:hover{border-color:var(--chalk3);transform:translateY(-2px)}
.player-card:hover::before{opacity:1}
.player-card.selected{border-color:var(--fire);background:rgba(255,87,34,.1)}
.player-card.selected::before{opacity:1}
.pc-check{
  position:absolute;top:.6rem;right:.6rem;
  width:20px;height:20px;border-radius:50%;
  background:var(--fire);color:#fff;font-size:.7rem;
  display:none;align-items:center;justify-content:center;font-weight:700;
}
.player-card.selected .pc-check{display:flex}
.pc-name{font-weight:600;font-size:.95rem;margin-bottom:.3rem;padding-right:22px}
.pc-meta{display:flex;align-items:center;gap:.4rem;margin-bottom:.5rem}
.pc-pos{color:var(--chalk3);font-size:.78rem}
.pc-ovr{
  font-family:'Barlow Condensed',sans-serif;font-size:1rem;font-weight:800;
  margin-left:auto;
}

/* ═══════════════════ TEAMS OUTPUT ════════════════════ */
.teams-topbar{
  display:flex;align-items:center;justify-content:space-between;
  flex-wrap:wrap;gap:1rem;margin-bottom:1.75rem;
}
.teams-grid{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(280px,1fr));
  gap:1.25rem;margin-bottom:2rem;
}
.team-card{
  border-radius:var(--r2);overflow:hidden;
  border:1px solid var(--line);
  transition:.2s;
}
.team-card:hover{transform:translateY(-3px);box-shadow:0 10px 40px rgba(0,0,0,.5)}
.tc-header{
  padding:1.1rem 1.25rem;
  display:flex;align-items:center;justify-content:space-between;
  border-bottom:1px solid rgba(255,255,255,.08);
}
.tc-name{
  font-family:'Barlow Condensed',sans-serif;
  font-size:1.75rem;font-weight:900;letter-spacing:.06em;
}
.tc-ovr-wrap{text-align:right}
.tc-ovr{
  font-family:'Barlow Condensed',sans-serif;
  font-size:2.2rem;font-weight:900;line-height:1;
}
.tc-ovr-lbl{font-size:.65rem;text-transform:uppercase;letter-spacing:.12em;color:rgba(255,255,255,.5)}
.tc-players{background:rgba(0,0,0,.25)}
.tc-player{
  display:flex;align-items:center;gap:.75rem;
  padding:.75rem 1.25rem;
  border-bottom:1px solid rgba(255,255,255,.05);
}
.tc-player:last-child{border-bottom:none}
.tc-avatar{
  width:34px;height:34px;border-radius:50%;
  display:flex;align-items:center;justify-content:center;
  font-family:'Barlow Condensed',sans-serif;font-size:.9rem;font-weight:800;
  flex-shrink:0;background:rgba(255,255,255,.1);color:#fff;
}
.tc-pinfo{flex:1;min-width:0}
.tc-pname{font-weight:600;font-size:.9rem;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.tc-pmeta{font-size:.75rem;color:rgba(255,255,255,.5);margin-top:1px}
.tc-povr{
  font-family:'Barlow Condensed',sans-serif;
  font-size:1.1rem;font-weight:800;flex-shrink:0;
}
.tc-footer{
  padding:.75rem 1.25rem;
  background:rgba(0,0,0,.15);
  display:flex;gap:.4rem;flex-wrap:wrap;
  border-top:1px solid rgba(255,255,255,.05);
}
.tc-tag{
  font-size:.7rem;padding:3px 9px;border-radius:20px;
  background:rgba(255,255,255,.06);color:rgba(255,255,255,.5);
  border:1px solid rgba(255,255,255,.08);
}

/* team color themes */
.tc-a{background:linear-gradient(135deg,#1a1008 0%,#2a1800 100%)}
.tc-a .tc-header{background:rgba(255,87,34,.12)}
.tc-a .tc-name,.tc-a .tc-ovr{color:#ff7043}
.tc-a{border-top:3px solid #ff5722}
.tc-b{background:linear-gradient(135deg,#0e1a14 0%,#0a1810 100%)}
.tc-b .tc-header{background:rgba(76,175,125,.12)}
.tc-b .tc-name,.tc-b .tc-ovr{color:#4caf7d}
.tc-b{border-top:3px solid #4caf7d}
.tc-c{background:linear-gradient(135deg,#0c1520 0%,#091018 100%)}
.tc-c .tc-header{background:rgba(74,168,224,.12)}
.tc-c .tc-name,.tc-c .tc-ovr{color:#4aa8e0}
.tc-c{border-top:3px solid #4aa8e0}
.tc-d{background:linear-gradient(135deg,#1a1600 0%,#1a1400 100%)}
.tc-d .tc-header{background:rgba(240,165,0,.12)}
.tc-d .tc-name,.tc-d .tc-ovr{color:#f0a500}
.tc-d{border-top:3px solid #f0a500}

/* ─ BALANCE METER ── */
.balance-section{
  background:var(--wood);border:1px solid var(--line);
  border-radius:var(--r2);padding:1.5rem;margin-bottom:1.5rem;
}
.balance-title{
  font-family:'Barlow Condensed',sans-serif;
  font-size:1.1rem;font-weight:800;letter-spacing:.08em;text-transform:uppercase;
  color:var(--chalk2);margin-bottom:1.25rem;
}
.bm-rows{display:flex;flex-direction:column;gap:.75rem}
.bm-row{display:flex;align-items:center;gap:1rem}
.bm-name{
  font-family:'Barlow Condensed',sans-serif;
  font-size:1rem;font-weight:800;letter-spacing:.05em;min-width:90px;
}
.bm-track{flex:1;height:12px;background:var(--wood3);border-radius:6px;overflow:hidden}
.bm-fill{height:100%;border-radius:6px;transition:width .9s cubic-bezier(.22,1,.36,1)}
.bm-val{
  font-family:'Barlow Condensed',sans-serif;
  font-size:1.15rem;font-weight:800;min-width:38px;text-align:right;
}

/* ─ MATCHUPS ────── */
.matchups-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(300px,1fr));gap:1rem;margin-bottom:1.75rem}
.mu-card{
  background:var(--wood);border:1px solid var(--line);
  border-radius:var(--r);padding:1rem 1.25rem;
  display:flex;align-items:center;justify-content:space-between;gap:.75rem;
}
.mu-team{text-align:center;flex:1}
.mu-tname{font-family:'Barlow Condensed',sans-serif;font-size:1.3rem;font-weight:900;letter-spacing:.04em}
.mu-tovr{font-size:.78rem;color:var(--chalk3);margin-top:2px}
.mu-vs{font-family:'Barlow Condensed',sans-serif;font-size:1rem;font-weight:800;color:var(--chalk4);flex-shrink:0}
.mu-diff{font-size:.72rem;margin-top:4px}
.diff-0{color:var(--green)}
.diff-1{color:var(--gold)}
.diff-2{color:var(--red)}

/* ═══════════════════ UPLOAD ════════════════════ */
.upload-zone{
  border:2px dashed var(--line);
  border-radius:var(--r);
  padding:2.5rem;text-align:center;
  cursor:pointer;transition:.2s;position:relative;
  margin:1.25rem 1.5rem;
}
.upload-zone:hover,.upload-zone.over{
  border-color:var(--fire);background:rgba(255,87,34,.05);
}
.upload-zone input{position:absolute;inset:0;opacity:0;cursor:pointer;width:100%;height:100%}
.uz-icon{font-size:2.5rem;margin-bottom:.75rem}
.uz-primary{font-weight:600;font-size:1rem;color:var(--chalk)}
.uz-secondary{font-size:.85rem;color:var(--chalk3);margin-top:.3rem}
.uz-link{color:var(--fire);font-size:.82rem;margin-top:.75rem;display:block}
.upload-fb{
  margin:0 1.5rem .75rem;font-size:.875rem;font-weight:500;min-height:1.5rem;
  padding:8px 14px;border-radius:7px;
}
.upload-fb.ok{background:rgba(76,175,125,.12);color:var(--green);border:1px solid rgba(76,175,125,.25)}
.upload-fb.err{background:rgba(224,84,84,.12);color:var(--red);border:1px solid rgba(224,84,84,.25)}

/* ─ COL FORMAT GUIDE ── */
.col-guide{display:grid;grid-template-columns:repeat(auto-fill,minmax(200px,1fr));gap:.75rem;padding:1.25rem 1.5rem}
.cg-item{background:var(--wood2);border:1px solid var(--line);border-radius:8px;padding:.75rem 1rem}
.cg-col{font-family:monospace;font-size:.85rem;color:var(--fire);font-weight:600;margin-bottom:.3rem}
.cg-desc{font-size:.78rem;color:var(--chalk3)}
.cg-vals{font-size:.72rem;color:var(--chalk4);margin-top:.25rem}

/* ═══════════════════ MODAL ════════════════════ */
.modal-bg{
  position:fixed;inset:0;z-index:1000;
  background:rgba(0,0,0,.75);backdrop-filter:blur(6px);
  display:none;align-items:center;justify-content:center;padding:1rem;
}
.modal-bg.open{display:flex}
.modal{
  background:var(--wood);border:1px solid var(--line);
  border-radius:var(--r2);max-width:680px;width:100%;
  box-shadow:0 30px 80px rgba(0,0,0,.6);
  animation:modalIn .25s ease;
}
@keyframes modalIn{from{opacity:0;transform:scale(.95)}to{opacity:1;transform:none}}
.modal-hdr{
  display:flex;align-items:center;justify-content:space-between;
  padding:1.25rem 1.5rem;border-bottom:1px solid var(--line);
  background:var(--wood2);border-radius:var(--r2) var(--r2) 0 0;
}
.modal-title{font-family:'Barlow Condensed',sans-serif;font-size:1.3rem;font-weight:800;letter-spacing:.06em}
.modal-close{
  background:none;border:none;cursor:pointer;color:var(--chalk3);
  font-size:1.3rem;padding:4px;transition:.18s;
}
.modal-close:hover{color:var(--red)}
.modal-body .form-grid{padding:1.25rem 1.5rem}
.modal-foot{padding:.75rem 1.5rem;background:var(--wood2);border-top:1px solid var(--line);display:flex;gap:.6rem;justify-content:flex-end;border-radius:0 0 var(--r2) var(--r2)}

/* ═══════════════════ TOAST ════════════════════ */
.toast{
  position:fixed;bottom:1.75rem;left:50%;
  transform:translateX(-50%) translateY(20px);
  background:var(--wood2);border:1px solid var(--line);
  border-radius:10px;padding:11px 22px;
  font-size:.9rem;font-weight:500;
  opacity:0;transition:all .3s ease;z-index:999;
  white-space:nowrap;pointer-events:none;
  box-shadow:0 8px 30px rgba(0,0,0,.4);
}
.toast.show{opacity:1;transform:translateX(-50%) translateY(0)}
.toast.ok{border-color:var(--green);color:var(--green)}
.toast.err{border-color:var(--red);color:var(--red)}

/* ═══════════════════ MISC ═════════════════════ */
.stats-bar{
  display:flex;gap:1rem;flex-wrap:wrap;margin-bottom:1.75rem;
}
.stat-pill{
  background:var(--wood);border:1px solid var(--line);
  border-radius:var(--r);padding:.8rem 1.25rem;
  display:flex;flex-direction:column;align-items:center;
  min-width:80px;
}
.sp-num{font-family:'Barlow Condensed',sans-serif;font-size:1.8rem;font-weight:900;color:var(--fire);line-height:1}
.sp-lbl{font-size:.68rem;text-transform:uppercase;letter-spacing:.1em;color:var(--chalk3);margin-top:3px}

.divider{height:1px;background:var(--line);margin:1.75rem 0}

.no-result{
  text-align:center;padding:4rem 2rem;
  color:var(--chalk3);
}
.no-result-icon{font-size:3.5rem;margin-bottom:1rem;display:block}
.no-result h3{font-family:'Barlow Condensed',sans-serif;font-size:1.5rem;font-weight:800;letter-spacing:.04em;margin-bottom:.5rem;color:var(--chalk2)}

.selected-banner{
  background:rgba(255,87,34,.1);border:1px solid rgba(255,87,34,.25);
  border-radius:var(--r);padding:.85rem 1.25rem;
  display:flex;align-items:center;justify-content:space-between;
  flex-wrap:wrap;gap:.75rem;margin-bottom:1.5rem;
}
.sb-text{font-family:'Barlow Condensed',sans-serif;font-size:1.1rem;font-weight:800;letter-spacing:.04em}
.sb-text span{color:var(--fire)}

/* ── RESPONSIVE ── */
@media(max-width:768px){
  .hdr-tabs .tab{padding:7px 12px;font-size:.82rem}
  .form-grid{padding:.75rem 1rem}
}
@media(max-width:500px){
  .logo-text{display:none}
  .hdr{gap:.5rem}
}
</style>
</head>
<body>
<div id="app">

  <!-- HEADER -->
  <header class="hdr">
    <div class="logo">
      <span class="logo-ball">🏀</span>
      <span class="logo-text">Hoops<em>Draft</em></span>
    </div>
    <nav class="hdr-tabs">
      <button class="tab active" onclick="switchTab('roster')">
        Roster <span class="tab-badge" id="badge-roster">0</span>
      </button>
      <button class="tab" onclick="switchTab('select')">
        Match Day <span class="tab-badge" id="badge-select">0</span>
      </button>
      <button class="tab" onclick="switchTab('teams')">Teams</button>
      <button class="tab" onclick="switchTab('import')">Import</button>
    </nav>
  </header>

  <!-- ════════════════ ROSTER PANEL ════════════════ -->
  <div class="panel active" id="panel-roster">
    <h1 class="page-title">Player <span>Roster</span></h1>
    <p class="page-sub">Manage your full player database. Add, edit, or remove players at any time.</p>

    <div class="stats-bar">
      <div class="stat-pill"><span class="sp-num" id="ct-total">0</span><span class="sp-lbl">Total</span></div>
      <div class="stat-pill"><span class="sp-num" id="ct-big">0</span><span class="sp-lbl">Big</span></div>
      <div class="stat-pill"><span class="sp-num" id="ct-med">0</span><span class="sp-lbl">Medium</span></div>
      <div class="stat-pill"><span class="sp-num" id="ct-sm">0</span><span class="sp-lbl">Small</span></div>
    </div>

    <div class="box">
      <div class="box-hdr">
        <div class="box-title"><span class="box-title-icon">📋</span>All Players</div>
        <div style="display:flex;gap:.5rem;flex-wrap:wrap">
          <button class="btn btn-fire btn-sm" onclick="openAddModal()">+ Add Player</button>
          <button class="btn btn-ghost btn-sm" onclick="exportCSV()">↓ Export CSV</button>
          <button class="btn btn-danger btn-sm" onclick="clearAll()">✕ Clear All</button>
        </div>
      </div>
      <div class="tbl-wrap">
        <table>
          <thead>
            <tr>
              <th>#</th><th>Name</th><th>Height</th><th>Position</th>
              <th>Scoring</th><th>Defense</th><th>Athletic</th><th>Passing</th><th>Rebounding</th>
              <th style="text-align:center">OVR</th><th></th>
            </tr>
          </thead>
          <tbody id="rosterBody">
            <tr class="empty-row"><td colspan="11">No players yet — add a player above or import a file.</td></tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>

  <!-- ════════════════ MATCH DAY PANEL ════════════════ -->
  <div class="panel" id="panel-select">
    <h1 class="page-title">Match <span>Day</span></h1>
    <p class="page-sub">Select exactly 16 players (or 4–16) who are available for today's game.</p>

    <div class="box" style="margin-bottom:1.5rem">
      <div class="match-controls">
        <div>
          <div class="active-count">Selected: <span id="sel-count">0</span> / 16</div>
          <div class="hint">Click a player card to toggle selection. Need at least 4 to generate teams.</div>
        </div>
        <div style="display:flex;gap:.6rem;flex-wrap:wrap">
          <button class="btn btn-ghost btn-sm" onclick="selectAll()">Select All</button>
          <button class="btn btn-ghost btn-sm" onclick="clearSelected()">Clear</button>
          <button class="btn btn-fire btn-sm" onclick="quickSelect16()">Auto-Select 16</button>
        </div>
      </div>
    </div>

    <div class="player-select-grid" id="selectGrid"></div>

    <div style="margin-top:1.5rem;display:flex;justify-content:flex-end">
      <button class="btn btn-gold btn-lg" id="genBtn" onclick="generateTeams()" disabled>
        ⚡ Generate Balanced Teams
      </button>
    </div>
  </div>

  <!-- ════════════════ TEAMS PANEL ════════════════ -->
  <div class="panel" id="panel-teams">
    <div class="teams-topbar">
      <div>
        <h1 class="page-title">Generated <span>Teams</span></h1>
        <p class="page-sub">Algorithm: Snake draft + OVR weighting + height balancing</p>
      </div>
      <div style="display:flex;gap:.6rem;flex-wrap:wrap">
        <button class="btn btn-ghost" onclick="reshuffleTeams()">🔀 Re-Shuffle</button>
        <button class="btn btn-ghost" onclick="window.print()">🖨 Print</button>
        <button class="btn btn-ghost" onclick="switchTab('select')">← Back</button>
      </div>
    </div>

    <div id="teamsOutput">
      <div class="no-result">
        <span class="no-result-icon">🏀</span>
        <h3>No Teams Yet</h3>
        <p>Go to <strong>Match Day</strong>, select your players, and hit Generate.</p>
      </div>
    </div>
  </div>

  <!-- ════════════════ IMPORT PANEL ════════════════ -->
  <div class="panel" id="panel-import">
    <h1 class="page-title">Import <span>Players</span></h1>
    <p class="page-sub">Upload a .csv or .xlsx file to bulk-load your roster.</p>

    <div class="box" style="margin-bottom:1.5rem">
      <div class="box-hdr">
        <div class="box-title"><span class="box-title-icon">📂</span>Upload File</div>
        <button class="btn btn-ghost btn-sm" onclick="downloadTemplate()">⬇ Download Template CSV</button>
      </div>
      <div class="upload-zone" id="uploadZone">
        <div class="uz-icon">📁</div>
        <div class="uz-primary">Drop your .csv or .xlsx file here</div>
        <div class="uz-secondary">or click to browse</div>
        <span class="uz-link">Supports Excel (.xlsx) and CSV (.csv)</span>
        <input type="file" id="fileInput" accept=".csv,.xlsx,.xls"/>
      </div>
      <div class="upload-fb" id="uploadFb" style="display:none"></div>
    </div>

    <div class="box">
      <div class="box-hdr">
        <div class="box-title"><span class="box-title-icon">📐</span>Required Columns</div>
      </div>
      <div class="col-guide">
        <div class="cg-item"><div class="cg-col">name</div><div class="cg-desc">Player full name</div></div>
        <div class="cg-item"><div class="cg-col">scoring</div><div class="cg-desc">Offensive scoring</div><div class="cg-vals">1 – 10</div></div>
        <div class="cg-item"><div class="cg-col">defense</div><div class="cg-desc">Defensive skill</div><div class="cg-vals">1 – 10</div></div>
        <div class="cg-item"><div class="cg-col">athleticism</div><div class="cg-desc">Speed & explosiveness</div><div class="cg-vals">1 – 10</div></div>
        <div class="cg-item"><div class="cg-col">passing</div><div class="cg-desc">Playmaking ability</div><div class="cg-vals">1 – 10</div></div>
        <div class="cg-item"><div class="cg-col">rebounding</div><div class="cg-desc">Board control</div><div class="cg-vals">1 – 10</div></div>
        <div class="cg-item"><div class="cg-col">height</div><div class="cg-desc">Height category</div><div class="cg-vals">big / medium / small</div></div>
        <div class="cg-item"><div class="cg-col">position <em style="color:var(--chalk4)">(opt)</em></div><div class="cg-desc">Playing position</div><div class="cg-vals">Guard / Forward / Center / Wing</div></div>
      </div>
      <div style="padding:.5rem 1.5rem 1.25rem">
        <div style="background:var(--wood2);border:1px solid var(--line);border-radius:8px;padding:.9rem 1.1rem">
          <div style="font-size:.7rem;text-transform:uppercase;letter-spacing:.1em;color:var(--chalk3);margin-bottom:.5rem;font-weight:600">OVR Formula</div>
          <div style="font-family:'Barlow Condensed',sans-serif;color:var(--fire);font-size:1.05rem;letter-spacing:.02em">
            OVR = (Scoring×1.3 + Defense×1.2 + Athleticism×1.0 + Passing×0.9 + Rebounding×0.8) ÷ 6.2
          </div>
        </div>
      </div>
    </div>
  </div>

</div><!-- /app -->

<!-- ════════ ADD / EDIT MODAL ════════ -->
<div class="modal-bg" id="playerModal">
  <div class="modal">
    <div class="modal-hdr">
      <div class="modal-title" id="modalTitle">Add Player</div>
      <button class="modal-close" onclick="closeModal()">✕</button>
    </div>
    <div class="modal-body">
      <div class="form-grid">
        <div class="field" style="grid-column:1/-1">
          <label>Player Name</label>
          <input type="text" id="m-name" placeholder="Full Name" />
        </div>
        <div class="field">
          <label>Scoring <span class="tip">1–10</span></label>
          <input type="number" id="m-scoring" min="1" max="10" placeholder="7" />
        </div>
        <div class="field">
          <label>Defense <span class="tip">1–10</span></label>
          <input type="number" id="m-defense" min="1" max="10" placeholder="7" />
        </div>
        <div class="field">
          <label>Athleticism <span class="tip">1–10</span></label>
          <input type="number" id="m-athleticism" min="1" max="10" placeholder="7" />
        </div>
        <div class="field">
          <label>Passing <span class="tip">1–10</span></label>
          <input type="number" id="m-passing" min="1" max="10" placeholder="7" />
        </div>
        <div class="field">
          <label>Rebounding <span class="tip">1–10</span></label>
          <input type="number" id="m-rebounding" min="1" max="10" placeholder="7" />
        </div>
        <div class="field">
          <label>Height</label>
          <select id="m-height">
            <option value="big">Big (6'3"+)</option>
            <option value="medium" selected>Medium (5'10"–6'2")</option>
            <option value="small">Small (Under 5'10")</option>
          </select>
        </div>
        <div class="field">
          <label>Position</label>
          <select id="m-position">
            <option>Guard</option>
            <option>Forward</option>
            <option>Center</option>
            <option>Wing</option>
          </select>
        </div>
      </div>
    </div>
    <div class="modal-foot">
      <button class="btn btn-ghost" onclick="closeModal()">Cancel</button>
      <button class="btn btn-fire" onclick="savePlayer()">Save Player</button>
    </div>
  </div>
</div>

<!-- TOAST -->
<div class="toast" id="toast"></div>

<!-- ════════════════════ XLSX PARSER (inline, no CDN) ════════════════════ -->
<!-- Self-contained XLSX/CSV parsing using FileReader + manual binary parse -->

<script>
/* ══════════════════════════════════════════════
   STATE
══════════════════════════════════════════════ */
let roster = JSON.parse(localStorage.getItem('hd_roster') || '[]');
let selected = new Set(JSON.parse(localStorage.getItem('hd_selected') || '[]'));
let lastTeams = JSON.parse(localStorage.getItem('hd_teams') || 'null');
let editIdx = null;

/* ══════════════════════════════════════════════
   TABS
══════════════════════════════════════════════ */
function switchTab(name) {
  document.querySelectorAll('.panel').forEach(p => p.classList.remove('active'));
  document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
  document.getElementById('panel-' + name).classList.add('active');
  document.querySelectorAll('.tab').forEach(t => {
    if (t.getAttribute('onclick') && t.getAttribute('onclick').includes("'"+name+"'")) t.classList.add('active');
  });
  if (name === 'select') renderSelectGrid();
  if (name === 'teams') renderTeamsOutput();
}

/* ══════════════════════════════════════════════
   OVR
══════════════════════════════════════════════ */
function calcOVR(p) {
  const raw = (p.scoring*1.3 + p.defense*1.2 + p.athleticism*1.0 + p.passing*0.9 + p.rebounding*0.8) / 6.2;
  return Math.min(10, Math.max(1, +raw.toFixed(1)));
}
function ovrCls(v) { return v>=8?'ovr-s':v>=6?'ovr-m':'ovr-l'; }
function htCls(h)  { return `htag htag-${h}`; }
function htLabel(h){ return h==='big'?'🔵 Big':h==='small'?'🟢 Small':'🟡 Medium'; }

/* ══════════════════════════════════════════════
   PERSIST
══════════════════════════════════════════════ */
function save() {
  localStorage.setItem('hd_roster', JSON.stringify(roster));
  localStorage.setItem('hd_selected', JSON.stringify([...selected]));
  if (lastTeams) localStorage.setItem('hd_teams', JSON.stringify(lastTeams));
}

/* ══════════════════════════════════════════════
   ROSTER RENDER
══════════════════════════════════════════════ */
function renderRoster() {
  const tbody = document.getElementById('rosterBody');
  document.getElementById('badge-roster').textContent = roster.length;
  document.getElementById('ct-total').textContent = roster.length;
  document.getElementById('ct-big').textContent   = roster.filter(p=>p.height==='big').length;
  document.getElementById('ct-med').textContent   = roster.filter(p=>p.height==='medium').length;
  document.getElementById('ct-sm').textContent    = roster.filter(p=>p.height==='small').length;

  if (!roster.length) {
    tbody.innerHTML = '<tr class="empty-row"><td colspan="11">No players yet — add one or import a file.</td></tr>';
    return;
  }
  tbody.innerHTML = roster.map((p,i) => {
    const ovr = calcOVR(p);
    return `<tr>
      <td style="color:var(--chalk3)">${i+1}</td>
      <td><strong>${esc(p.name)}</strong></td>
      <td><span class="${htCls(p.height)}">${htLabel(p.height)}</span></td>
      <td style="color:var(--chalk3)">${esc(p.position||'—')}</td>
      <td>${sbar(p.scoring)}</td>
      <td>${sbar(p.defense)}</td>
      <td>${sbar(p.athleticism)}</td>
      <td>${sbar(p.passing)}</td>
      <td>${sbar(p.rebounding)}</td>
      <td style="text-align:center"><span class="ovr ${ovrCls(ovr)}">${ovr}</span></td>
      <td style="white-space:nowrap">
        <button class="edit-btn" onclick="openEditModal(${i})" title="Edit">✏</button>
        <button class="del-btn" onclick="deletePlayer(${i})" title="Remove">✕</button>
      </td>
    </tr>`;
  }).join('');
}

function sbar(v) {
  return `<div class="sbar">
    <span class="sbar-v">${v}</span>
    <div class="sbar-t"><div class="sbar-f" style="width:${v*10}%"></div></div>
  </div>`;
}
function esc(s){ return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;'); }

/* ══════════════════════════════════════════════
   MODAL
══════════════════════════════════════════════ */
function openAddModal() {
  editIdx = null;
  document.getElementById('modalTitle').textContent = 'Add Player';
  clearModalForm();
  document.getElementById('playerModal').classList.add('open');
  document.getElementById('m-name').focus();
}
function openEditModal(i) {
  editIdx = i;
  const p = roster[i];
  document.getElementById('modalTitle').textContent = 'Edit Player';
  document.getElementById('m-name').value = p.name;
  document.getElementById('m-scoring').value = p.scoring;
  document.getElementById('m-defense').value = p.defense;
  document.getElementById('m-athleticism').value = p.athleticism;
  document.getElementById('m-passing').value = p.passing;
  document.getElementById('m-rebounding').value = p.rebounding;
  document.getElementById('m-height').value = p.height;
  document.getElementById('m-position').value = p.position || 'Guard';
  document.getElementById('playerModal').classList.add('open');
}
function closeModal() {
  document.getElementById('playerModal').classList.remove('open');
  editIdx = null;
}
function clearModalForm() {
  ['m-name','m-scoring','m-defense','m-athleticism','m-passing','m-rebounding'].forEach(id=>{
    document.getElementById(id).value='';
  });
  document.getElementById('m-height').value = 'medium';
  document.getElementById('m-position').value = 'Guard';
}
function savePlayer() {
  const name = document.getElementById('m-name').value.trim();
  if (!name) return toast('Please enter a player name','err');
  const stats = ['scoring','defense','athleticism','passing','rebounding'].map(s=>{
    const v = parseInt(document.getElementById('m-'+s).value);
    return isNaN(v)||v<1||v>10 ? null : v;
  });
  if (stats.includes(null)) return toast('All skill ratings must be 1–10','err');
  const player = {
    name,
    scoring:stats[0], defense:stats[1], athleticism:stats[2],
    passing:stats[3], rebounding:stats[4],
    height: document.getElementById('m-height').value,
    position: document.getElementById('m-position').value
  };
  if (editIdx !== null) {
    roster[editIdx] = player;
    toast(`${name} updated ✓`,'ok');
  } else {
    roster.push(player);
    toast(`${name} added to roster ✓`,'ok');
  }
  save(); renderRoster(); closeModal();
}

/* ══════════════════════════════════════════════
   DELETE / CLEAR
══════════════════════════════════════════════ */
function deletePlayer(i) {
  const name = roster[i].name;
  selected.delete(i); // note: indices shift — rebuild selected by name
  const selNames = [...selected].map(idx => roster[idx]?.name).filter(Boolean);
  roster.splice(i, 1);
  // Rebuild selected by name match
  selected = new Set();
  selNames.forEach(n => {
    const ni = roster.findIndex(p=>p.name===n);
    if (ni>=0) selected.add(ni);
  });
  save(); renderRoster();
  toast(`${name} removed`,'err');
}
function clearAll() {
  if (!roster.length) return;
  if (!confirm('Clear entire roster? This cannot be undone.')) return;
  roster=[]; selected=new Set(); lastTeams=null;
  localStorage.removeItem('hd_teams');
  save(); renderRoster();
  toast('Roster cleared','err');
}

/* ══════════════════════════════════════════════
   SELECT GRID
══════════════════════════════════════════════ */
function renderSelectGrid() {
  const grid = document.getElementById('selectGrid');
  if (!roster.length) {
    grid.innerHTML = '<div style="grid-column:1/-1;text-align:center;padding:3rem;color:var(--chalk3)">No players in roster. Add players first.</div>';
    updateSelCount(); return;
  }
  grid.innerHTML = roster.map((p,i) => {
    const ovr = calcOVR(p);
    const isSel = selected.has(i);
    return `<div class="player-card${isSel?' selected':''}" onclick="toggleSelect(${i})" id="pc-${i}">
      <div class="pc-check">✓</div>
      <div class="pc-name">${esc(p.name)}</div>
      <div class="pc-meta">
        <span class="htag htag-${p.height}" style="font-size:.65rem;padding:2px 7px">${htLabel(p.height)}</span>
        <span class="pc-pos">${esc(p.position||'')}</span>
        <span class="pc-ovr ${ovrCls(ovr)}">${ovr}</span>
      </div>
      <div class="sbar" style="margin-top:4px">
        <div class="sbar-t" style="min-width:0"><div class="sbar-f" style="width:${ovr*10}%"></div></div>
      </div>
    </div>`;
  }).join('');
  updateSelCount();
}

function toggleSelect(i) {
  if (selected.has(i)) { selected.delete(i); } else {
    if (selected.size >= 16) return toast('Max 16 players for this session','err');
    selected.add(i);
  }
  const card = document.getElementById('pc-'+i);
  if (card) card.classList.toggle('selected', selected.has(i));
  updateSelCount();
  save();
}

function updateSelCount() {
  const n = selected.size;
  document.getElementById('sel-count').textContent = n;
  document.getElementById('badge-select').textContent = n;
  document.getElementById('genBtn').disabled = n < 4;
}

function selectAll() {
  selected = new Set(roster.map((_,i)=>i).slice(0,16));
  renderSelectGrid(); save();
}
function clearSelected() {
  selected = new Set();
  renderSelectGrid(); save();
}
function quickSelect16() {
  // Top 16 by OVR
  const sorted = roster.map((p,i)=>({i,ovr:calcOVR(p)})).sort((a,b)=>b.ovr-a.ovr).slice(0,16);
  selected = new Set(sorted.map(x=>x.i));
  renderSelectGrid(); save();
  toast(`Top ${sorted.length} players selected`,'ok');
}

/* ══════════════════════════════════════════════
   TEAM GENERATION ALGORITHM
══════════════════════════════════════════════ */
function generateTeams() {
  const pool = [...selected].map(i => ({...roster[i], ovr:calcOVR(roster[i])}));
  if (pool.length < 4) return toast('Need at least 4 players','err');

  // Sort by OVR desc
  pool.sort((a,b) => b.ovr - a.ovr);

  const numTeams = Math.min(4, Math.floor(pool.length / 1));
  const teams = [[],[],[],[]];
  const teamOVR = [0,0,0,0];
  const heightCount = [
    {big:0,medium:0,small:0},{big:0,medium:0,small:0},
    {big:0,medium:0,small:0},{big:0,medium:0,small:0}
  ];

  // Round-robin snake draft with height awareness
  pool.forEach((player, idx) => {
    if (idx >= 16) return;
    const teamSize = Math.ceil(pool.length / 4);
    const candidates = [0,1,2,3].filter(t => teams[t].length < teamSize);
    if (!candidates.length) return;

    // Score each team — lower = better target
    const scored = candidates.map(t => {
      const ovrScore  = teamOVR[t] * 2.5;
      const hPenalty  = heightCount[t][player.height] >= 2 ? 4 : 0;
      const sizePenalty = teams[t].length * 0.1;
      return { t, score: ovrScore + hPenalty + sizePenalty };
    });
    scored.sort((a,b) => a.score - b.score);
    const chosen = scored[0].t;
    teams[chosen].push(player);
    teamOVR[chosen] += player.ovr;
    heightCount[chosen][player.height]++;
  });

  const NAMES = ['Ballers','Hoopers','Buckets','Grinders'];
  const CLASSES = ['tc-a','tc-b','tc-c','tc-d'];
  const COLORS = ['#ff7043','#4caf7d','#4aa8e0','#f0a500'];

  lastTeams = teams.map((players, i) => ({
    name: NAMES[i],
    cls: CLASSES[i],
    color: COLORS[i],
    players,
    avgOVR: players.length ? +(players.reduce((s,p)=>s+p.ovr,0)/players.length).toFixed(1) : 0
  }));

  save();
  switchTab('teams');
  toast('Teams generated! 🔥','ok');
}

function reshuffleTeams() {
  // Shuffle selected pool order then re-run
  const indices = [...selected];
  for (let i=indices.length-1;i>0;i--) {
    const j=Math.floor(Math.random()*(i+1));
    [indices[i],indices[j]]=[indices[j],indices[i]];
  }
  const newSet = new Set(indices);
  selected = newSet;
  generateTeams();
}

/* ══════════════════════════════════════════════
   TEAMS RENDER
══════════════════════════════════════════════ */
function renderTeamsOutput() {
  const out = document.getElementById('teamsOutput');
  if (!lastTeams) {
    out.innerHTML = `<div class="no-result">
      <span class="no-result-icon">🏀</span>
      <h3>No Teams Yet</h3>
      <p>Go to <strong>Match Day</strong>, select players, and hit Generate.</p>
    </div>`;
    return;
  }

  // Balance meters
  const maxOVR = Math.max(...lastTeams.map(t=>t.avgOVR));
  const balHTML = `<div class="balance-section">
    <div class="balance-title">⚖ Team Balance</div>
    <div class="bm-rows">
      ${lastTeams.map(t=>`<div class="bm-row">
        <span class="bm-name" style="color:${t.color}">${t.name}</span>
        <div class="bm-track"><div class="bm-fill" style="width:${maxOVR>0?(t.avgOVR/maxOVR*100):0}%;background:${t.color}"></div></div>
        <span class="bm-val" style="color:${t.color}">${t.avgOVR}</span>
      </div>`).join('')}
    </div>
  </div>`;

  // Matchups
  const pairs = [[0,1],[2,3],[0,2],[1,3],[0,3],[1,2]];
  const muHTML = `<div class="matchups-grid">
    ${pairs.map(([a,b])=>{
      const ta=lastTeams[a],tb=lastTeams[b];
      const diff=Math.abs(ta.avgOVR-tb.avgOVR);
      const dcls=diff<=0.3?'diff-0':diff<=0.8?'diff-1':'diff-2';
      const dlbl=diff<=0.3?'⚖ Even':diff<=0.8?`▲ ${diff.toFixed(1)} diff`:`⚠ ${diff.toFixed(1)} gap`;
      return `<div class="mu-card">
        <div class="mu-team">
          <div class="mu-tname" style="color:${ta.color}">${ta.name}</div>
          <div class="mu-tovr">OVR ${ta.avgOVR}</div>
        </div>
        <div style="text-align:center">
          <div class="mu-vs">VS</div>
          <div class="mu-diff ${dcls}">${dlbl}</div>
        </div>
        <div class="mu-team">
          <div class="mu-tname" style="color:${tb.color}">${tb.name}</div>
          <div class="mu-tovr">OVR ${tb.avgOVR}</div>
        </div>
      </div>`;
    }).join('')}
  </div>`;

  // Team cards
  const cardHTML = `<div class="teams-grid">
    ${lastTeams.map(t=>`<div class="team-card ${t.cls}">
      <div class="tc-header">
        <div class="tc-name">${t.name}</div>
        <div class="tc-ovr-wrap">
          <div class="tc-ovr">${t.avgOVR}</div>
          <div class="tc-ovr-lbl">Avg OVR</div>
        </div>
      </div>
      <div class="tc-players">
        ${t.players.map(p=>`<div class="tc-player">
          <div class="tc-avatar" style="background:${t.color}22;color:${t.color}">${p.name.charAt(0)}</div>
          <div class="tc-pinfo">
            <div class="tc-pname">${esc(p.name)}</div>
            <div class="tc-pmeta">${esc(p.position||'Player')} · ${htLabel(p.height)}</div>
          </div>
          <div class="tc-povr ${ovrCls(p.ovr)}">${p.ovr}</div>
        </div>`).join('')}
      </div>
      <div class="tc-footer">
        ${buildTags(t.players).map(tg=>`<span class="tc-tag">${tg}</span>`).join('')}
      </div>
    </div>`).join('')}
  </div>`;

  out.innerHTML = balHTML + muHTML + cardHTML;
}

function buildTags(players) {
  const h={big:0,medium:0,small:0};
  players.forEach(p=>h[p.height]++);
  const tags=[];
  if(h.big)    tags.push(`${h.big}× Big`);
  if(h.medium) tags.push(`${h.medium}× Med`);
  if(h.small)  tags.push(`${h.small}× Small`);
  const top = players.reduce((a,b)=>a.scoring>b.scoring?a:b,players[0]);
  if(top) tags.push(`🔥 ${top.name.split(' ')[0]}`);
  return tags;
}

/* ══════════════════════════════════════════════
   FILE IMPORT (pure JS, no CDN)
══════════════════════════════════════════════ */
const uploadZone = document.getElementById('uploadZone');
const fileInput  = document.getElementById('fileInput');

uploadZone.addEventListener('dragover', e=>{e.preventDefault();uploadZone.classList.add('over')});
uploadZone.addEventListener('dragleave',()=>uploadZone.classList.remove('over'));
uploadZone.addEventListener('drop', e=>{
  e.preventDefault();uploadZone.classList.remove('over');
  if(e.dataTransfer.files.length) handleFile(e.dataTransfer.files[0]);
});
fileInput.addEventListener('change', e=>{if(e.target.files.length) handleFile(e.target.files[0])});

function handleFile(file) {
  const ext = file.name.split('.').pop().toLowerCase();
  if (ext==='csv') {
    const fr=new FileReader();
    fr.onload=e=>processCSV(e.target.result, file.name);
    fr.readAsText(file);
  } else if (ext==='xlsx'||ext==='xls') {
    const fr=new FileReader();
    fr.onload=e=>processXLSX(e.target.result, file.name);
    fr.readAsArrayBuffer(file);
  } else {
    showFb('Unsupported file. Use .csv or .xlsx','err');
  }
}

/* ─ CSV ───────────────────────────────── */
function processCSV(text, fname) {
  const lines = text.split(/\r?\n/).filter(l=>l.trim());
  if (!lines.length) return showFb('Empty file','err');

  const headers = parseCSVLine(lines[0]).map(h=>h.trim().toLowerCase());
  const rows = [];
  for (let i=1;i<lines.length;i++) {
    const vals = parseCSVLine(lines[i]);
    const obj={};
    headers.forEach((h,j)=>{ obj[h]=(vals[j]||'').trim(); });
    rows.push(obj);
  }
  importRows(rows, fname);
}

function parseCSVLine(line) {
  const result=[], re=/("(?:[^"]|"")*"|[^,]*)/g;
  let m;
  while((m=re.exec(line))!==null) {
    if(m.index===re.lastIndex) re.lastIndex++;
    let v=m[1];
    if(v.startsWith('"')&&v.endsWith('"')) v=v.slice(1,-1).replace(/""/g,'"');
    result.push(v);
  }
  return result;
}

/* ─ XLSX (minimal binary parser) ──────── */
function processXLSX(buffer, fname) {
  try {
    const rows = parseXLSXSimple(buffer);
    if (!rows || !rows.length) return showFb('Could not read Excel file','err');
    importRows(rows, fname);
  } catch(e) {
    showFb('Excel parse error: '+e.message,'err');
  }
}

// Minimal XLSX reader — extracts first sheet as array of objects
function parseXLSXSimple(buffer) {
  const u8 = new Uint8Array(buffer);
  // Check ZIP magic
  if (u8[0]!==0x50||u8[1]!==0x4B) throw new Error('Not a valid .xlsx file');

  // Parse ZIP entries
  const files = parseZIP(u8);

  // Find shared strings
  let strings = [];
  const ssFile = files['xl/sharedStrings.xml'];
  if (ssFile) {
    const ssXML = decode(ssFile);
    strings = [...ssXML.matchAll(/<t(?:\s[^>]*)?>([^<]*)<\/t>/g)].map(m=>xmlDecode(m[1]));
  }

  // Find first sheet
  let sheetXML = '';
  for (const key of Object.keys(files)) {
    if (key.match(/xl\/worksheets\/sheet1/)) {
      sheetXML = decode(files[key]); break;
    }
  }
  if (!sheetXML) throw new Error('No worksheet found');

  // Parse rows
  const rows = [];
  const rowRe = /<row[^>]*>([\s\S]*?)<\/row>/g;
  let rm;
  while ((rm=rowRe.exec(sheetXML))!==null) {
    const cells=[];
    const cellRe = /<c\s([^>]*)>([\s\S]*?)<\/c>/g;
    let cm;
    while((cm=cellRe.exec(rm[1]))!==null) {
      const attrs=cm[1], inner=cm[2];
      const ref=((attrs.match(/r="([^"]+)"/)||[])[1])||'';
      const type=((attrs.match(/t="([^"]+)"/)||[])[1])||'';
      let val='';
      const vm=inner.match(/<v>([^<]*)<\/v>/);
      if(vm) {
        val=vm[1];
        if(type==='s') val=strings[parseInt(val)]||'';
        else if(type==='inlineStr') { const im=inner.match(/<t>([^<]*)<\/t>/); if(im) val=im[1]; }
      }
      const col = ref.replace(/[0-9]/g,'');
      cells.push({col, val: xmlDecode(val)});
    }
    rows.push(cells);
  }

  // First row = headers
  if (rows.length<2) return [];
  const headers = rows[0].map(c=>c.val.toLowerCase().trim());
  const result = [];
  for (let i=1;i<rows.length;i++) {
    const obj={};
    rows[i].forEach((c,j)=>{
      if(headers[j]) obj[headers[j]]=c.val;
    });
    if (Object.values(obj).some(v=>v)) result.push(obj);
  }
  return result;
}

function parseZIP(u8) {
  const files={};
  let i=0;
  while(i<u8.length-4) {
    if(u8[i]===0x50&&u8[i+1]===0x4B&&u8[i+2]===0x03&&u8[i+3]===0x04) {
      const fnLen=u8[i+26]|(u8[i+27]<<8);
      const extLen=u8[i+28]|(u8[i+29]<<8);
      const compMethod=u8[i+8]|(u8[i+9]<<8);
      const compSize=u8[i+18]|(u8[i+19]<<8)|(u8[i+20]<<16)|(u8[i+21]<<24);
      const fname=new TextDecoder().decode(u8.slice(i+30,i+30+fnLen));
      const dataStart=i+30+fnLen+extLen;
      const compData=u8.slice(dataStart,dataStart+compSize);
      if(compMethod===0) {
        files[fname]=compData;
      } else if(compMethod===8) {
        try { files[fname]=inflateRaw(compData); } catch(e){}
      }
      i=dataStart+compSize;
    } else { i++; }
  }
  return files;
}

function decode(u8) {
  return new TextDecoder('utf-8').decode(u8);
}

function xmlDecode(s) {
  return s.replace(/&amp;/g,'&').replace(/&lt;/g,'<').replace(/&gt;/g,'>').replace(/&quot;/g,'"').replace(/&apos;/g,"'");
}

// Minimal inflate implementation (deflate raw)
function inflateRaw(data) {
  // Use DecompressionStream if available (modern browsers)
  if (typeof DecompressionStream !== 'undefined') {
    // synchronous fallback not possible; we'll use sync approach below
  }
  return pako_inflate(data);
}

// Embedded minimal pako inflate (deflate algorithm)
// This is a trimmed-down inflate for XLSX support
function pako_inflate(input) {
  const HUFF = buildHuffTables();
  let src=0, dst=0, last=0;
  const ib=new Uint8Array(input);
  const out=new Uint8Array(input.length*6);
  let bits=0, bitBuf=0;

  function readBits(n) {
    while(bits<n) { bitBuf|=(ib[src++]<<bits); bits+=8; }
    const v=bitBuf&((1<<n)-1); bitBuf>>=n; bits-=n; return v;
  }
  function readCode(tree) {
    let code=0,len=0;
    while(true){
      code=(code<<1)|readBits(1); len++;
      if(len>15) throw new Error('bad code');
      const v=tree[len]?tree[len][code]:undefined;
      if(v!==undefined) return v;
    }
  }

  do {
    last=readBits(1);
    const btype=readBits(2);
    if(btype===0) {
      bitBuf=0;bits=0;
      const len=ib[src]|(ib[src+1]<<8); src+=4;
      for(let i=0;i<len;i++) out[dst++]=ib[src++];
    } else if(btype===1||btype===2) {
      let litTree,distTree;
      if(btype===1) {
        litTree=HUFF.fixed_lit; distTree=HUFF.fixed_dist;
      } else {
        const hlit=readBits(5)+257, hdist=readBits(5)+1, hclen=readBits(4)+4;
        const clens=new Array(19).fill(0);
        const order=[16,17,18,0,8,7,9,6,10,5,11,4,12,3,13,2,14,1,15];
        for(let i=0;i<hclen;i++) clens[order[i]]=readBits(3);
        const clTree=buildTree(clens);
        const lens=[];
        while(lens.length<hlit+hdist) {
          const sym=readCode(clTree);
          if(sym<16) { lens.push(sym); }
          else if(sym===16) { const r=readBits(2)+3; for(let i=0;i<r;i++) lens.push(lens[lens.length-1]); }
          else if(sym===17) { const r=readBits(3)+3; for(let i=0;i<r;i++) lens.push(0); }
          else { const r=readBits(7)+11; for(let i=0;i<r;i++) lens.push(0); }
        }
        litTree=buildTree(lens.slice(0,hlit));
        distTree=buildTree(lens.slice(hlit));
      }
      while(true) {
        const sym=readCode(litTree);
        if(sym===256) break;
        if(sym<256) { out[dst++]=sym; }
        else {
          const LEXT=[0,0,0,0,0,0,0,0,1,1,1,1,2,2,2,2,3,3,3,3,4,4,4,4,5,5,5,5,0];
          const LBASE=[3,4,5,6,7,8,9,10,11,13,15,17,19,23,27,31,35,43,51,59,67,83,99,115,131,163,195,227,258];
          const DEXT=[0,0,0,0,1,1,2,2,3,3,4,4,5,5,6,6,7,7,8,8,9,9,10,10,11,11,12,12,13,13];
          const DBASE=[1,2,3,4,5,7,9,13,17,25,33,49,65,97,129,193,257,385,513,769,1025,1537,2049,3073,4097,6145,8193,12289,16385,24577];
          const li=sym-257;
          const len=LBASE[li]+readBits(LEXT[li]);
          const dsym=readCode(distTree);
          const dist=DBASE[dsym]+readBits(DEXT[dsym]);
          for(let i=0;i<len;i++) { out[dst]=out[dst-dist]; dst++; }
        }
      }
    } else throw new Error('reserved block');
  } while(!last);
  return out.slice(0,dst);
}

function buildTree(lengths) {
  const maxBits=Math.max(...lengths);
  const blCount=new Array(maxBits+1).fill(0);
  lengths.forEach(l=>{ if(l) blCount[l]++; });
  const nextCode=new Array(maxBits+2).fill(0);
  for(let i=1;i<=maxBits;i++) nextCode[i+1]=(nextCode[i]+blCount[i])<<1;
  const tree={};
  lengths.forEach((l,sym)=>{
    if(!l) return;
    if(!tree[l]) tree[l]={};
    tree[l][nextCode[l]++]=sym;
  });
  return tree;
}

function buildHuffTables() {
  const fll=new Array(288).fill(0).map((_,i)=>i<=143?8:i<=255?9:i<=279?7:8);
  const fdl=new Array(32).fill(5);
  return { fixed_lit:buildTree(fll), fixed_dist:buildTree(fdl) };
}

/* ─ ROW IMPORT ───────────────────────────── */
function importRows(rows, fname) {
  const REQ=['name','scoring','defense','athleticism','passing','rebounding','height'];
  if(!rows.length) return showFb('File is empty','err');
  const keys=Object.keys(rows[0]);
  const miss=REQ.filter(r=>!keys.includes(r));
  if(miss.length) return showFb(`Missing columns: ${miss.join(', ')}. See format guide above.`,'err');

  const valid=[], errs=[];
  rows.forEach((row,i)=>{
    const name=String(row.name||'').trim();
    if(!name) return errs.push(`Row ${i+2}: missing name`);
    const stats=['scoring','defense','athleticism','passing','rebounding'].map(s=>{
      const v=parseFloat(row[s]);
      return (isNaN(v)||v<1||v>10)?null:Math.round(v);
    });
    if(stats.includes(null)) return errs.push(`Row ${i+2} (${name}): invalid stat`);
    valid.push({
      name, scoring:stats[0], defense:stats[1], athleticism:stats[2],
      passing:stats[3], rebounding:stats[4],
      height:normalizeHeight(row.height),
      position:String(row.position||'Guard').trim()
    });
  });

  if(!valid.length) return showFb('No valid rows found','err');
  roster=[...valid];
  selected=new Set();
  lastTeams=null;
  save(); renderRoster();
  let msg=`✓ Imported ${valid.length} player${valid.length>1?'s':''} from ${fname}`;
  if(errs.length) msg+=` (${errs.length} skipped)`;
  showFb(msg,'ok');
  toast(msg,'ok');
  setTimeout(()=>switchTab('roster'),800);
}

function normalizeHeight(v) {
  const s=String(v||'').toLowerCase().trim();
  if(s.includes('big')||s==='tall'||s==='large'||s==='l') return 'big';
  if(s.includes('small')||s==='short'||s==='s') return 'small';
  return 'medium';
}

function showFb(msg, type) {
  const el=document.getElementById('uploadFb');
  el.style.display='block';
  el.textContent=msg;
  el.className='upload-fb '+type;
}

/* ── EXPORT CSV ───────────────────────────── */
function exportCSV() {
  if(!roster.length) return toast('Nothing to export','err');
  const hdr='name,scoring,defense,athleticism,passing,rebounding,height,position\n';
  const body=roster.map(p=>`${p.name},${p.scoring},${p.defense},${p.athleticism},${p.passing},${p.rebounding},${p.height},${p.position||'Guard'}`).join('\n');
  const blob=new Blob([hdr+body],{type:'text/csv'});
  const a=document.createElement('a');
  a.href=URL.createObjectURL(blob);
  a.download='hoopsdraft_roster.csv';
  a.click();
  URL.revokeObjectURL(a.href);
  toast('CSV exported ✓','ok');
}

function downloadTemplate() {
  const hdr='name,scoring,defense,athleticism,passing,rebounding,height,position\n';
  const rows=[
    'Marcus Johnson,9,7,8,6,5,medium,Guard',
    'DeShawn Carter,7,9,8,7,8,big,Forward',
    'Tyrell Brooks,8,6,9,8,4,small,Guard',
    'Andre Williams,6,8,7,5,9,big,Center',
    'Chris Okafor,7,7,6,9,6,medium,Wing',
    'Jordan Miles,9,5,9,7,5,small,Guard',
    'Kevin Nash,5,9,6,6,9,big,Center',
    'Darius Powell,8,7,7,8,6,medium,Wing',
    'Malik Turner,6,8,8,7,7,medium,Forward',
    'Isaac Reed,7,6,9,6,5,small,Guard',
    'Evan Thomas,8,7,6,7,8,big,Forward',
    'Jamal Foster,6,9,7,8,7,medium,Wing',
    'Nathan Rivera,9,6,8,5,6,medium,Guard',
    'Quincy Adams,5,8,7,7,9,big,Center',
    'Trevor Hall,7,7,8,9,5,small,Guard',
    'Xavier Long,8,8,7,6,8,big,Forward'
  ].join('\n');
  const blob=new Blob([hdr+rows],{type:'text/csv'});
  const a=document.createElement('a');
  a.href=URL.createObjectURL(blob);
  a.download='hoopsdraft_template.csv';
  a.click();
  URL.revokeObjectURL(a.href);
  toast('Template downloaded ✓','ok');
}

/* ── TOAST ─────────────────────────────────── */
function toast(msg, type='') {
  const t=document.getElementById('toast');
  t.textContent=msg;
  t.className='toast show '+(type==='ok'?'ok':type==='err'?'err':'');
  clearTimeout(t._tm);
  t._tm=setTimeout(()=>t.className='toast',2800);
}

/* ── KEYBOARD ────────────────────────────── */
document.addEventListener('keydown', e=>{
  if(e.key==='Escape') closeModal();
  if((e.ctrlKey||e.metaKey)&&e.key==='Enter') {
    if(document.getElementById('playerModal').classList.contains('open')) savePlayer();
  }
});
document.getElementById('playerModal').addEventListener('click',e=>{
  if(e.target===e.currentTarget) closeModal();
});

/* ── INIT ───────────────────────────────── */
renderRoster();
updateSelCount();
if(lastTeams) {
  // Hydrate teams badge if coming back
  document.getElementById('badge-select').textContent = selected.size;
}
</script>
</body>
</html>
