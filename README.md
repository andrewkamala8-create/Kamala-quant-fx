# Kamala-quant-fx
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>KAMALA QUANT</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;500;600;700&family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
:root{
  --bg:#060810;--panel:#0b0e18;--card:#101422;--inp:#080b14;
  --b:#182030;--bhi:#243050;
  --teal:#00c9a7;--teal2:#00c9a722;--teal3:#00c9a710;
  --amber:#f5a623;--amber2:#f5a62320;
  --violet:#a78bfa;--violet2:#a78bfa18;
  --bull:#20d472;--bear:#f03e55;--bull2:#20d47218;--bear2:#f03e5518;
  --t1:#dde4f0;--t2:#7d8ea8;--t3:#3d4d65;
  --gold:#f0b429;--gold2:#f0b42918;
  --r:7px;
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth}
body{font-family:'Inter',sans-serif;background:var(--bg);color:var(--t1);min-height:100vh;display:flex;flex-direction:column}

/* ── STICKY HEADER ── */
#hdr{
  position:sticky;top:0;z-index:100;
  background:rgba(6,8,16,.97);border-bottom:1px solid var(--b);
  backdrop-filter:blur(16px);display:flex;align-items:center;
  gap:12px;padding:10px 22px;flex-wrap:wrap;
}
.logo{
  font-family:'JetBrains Mono',monospace;font-weight:700;font-size:14px;
  letter-spacing:5px;color:var(--teal);text-shadow:0 0 28px #00c9a760;
  white-space:nowrap;user-select:none;flex-shrink:0;
}
.logo b{color:var(--gold);text-shadow:0 0 20px #f0b42960}
.vsep{width:1px;height:26px;background:var(--b);flex-shrink:0}
#pairs{display:flex;gap:4px;flex-wrap:wrap}
.pb{
  font-family:'JetBrains Mono',monospace;font-size:10px;font-weight:600;
  letter-spacing:.8px;padding:5px 10px;border:1px solid var(--b);
  background:transparent;color:var(--t2);cursor:pointer;border-radius:var(--r);transition:all .18s;
}
.pb:hover{border-color:var(--teal);color:var(--teal)}
.pb.active{border-color:var(--teal);background:var(--teal2);color:var(--teal);box-shadow:0 0 12px var(--teal3)}
.hright{margin-left:auto;display:flex;align-items:center;gap:12px;font-family:'JetBrains Mono',monospace;flex-shrink:0}
#tk-price{font-size:17px;font-weight:700;color:var(--teal);transition:color .4s}
#tk-chg{font-size:10px;font-weight:700;padding:3px 8px;border-radius:4px}
.pos{color:var(--bull);background:var(--bull2)}.neg{color:var(--bear);background:var(--bear2)}
#wsdot{width:7px;height:7px;border-radius:50%;background:var(--bear);animation:pulse 2s infinite;flex-shrink:0}
#wsdot.on{background:var(--bull)}
#settings-toggle{
  background:transparent;border:1px solid var(--b);color:var(--t3);
  font-family:'JetBrains Mono',monospace;font-size:9px;font-weight:600;letter-spacing:1px;
  padding:5px 10px;border-radius:var(--r);cursor:pointer;transition:all .2s;
}
#settings-toggle:hover{border-color:var(--amber);color:var(--amber)}
@keyframes pulse{0%,100%{opacity:1}50%{opacity:.3}}

/* ── PAGE ── */
#page{flex:1;max-width:1300px;width:100%;margin:0 auto;padding:20px 22px 130px;display:flex;flex-direction:column;gap:18px}

/* ── SECTION HEADER ── */
.sh{
  font-family:'JetBrains Mono',monospace;font-size:9px;font-weight:700;
  letter-spacing:3.5px;color:var(--t3);text-transform:uppercase;
  display:flex;align-items:center;gap:10px;margin-bottom:12px;
}
.sh::after{content:'';flex:1;height:1px;background:var(--b)}
.sh .badge{
  font-size:8px;padding:2px 7px;border-radius:10px;letter-spacing:1px;
  border:1px solid;font-weight:700;
}
.badge-live{background:var(--bull2);border-color:var(--bull);color:var(--bull)}
.badge-ai{background:var(--violet2);border-color:var(--violet);color:var(--violet)}

/* ── SETTINGS PANEL ── */
#settings-panel{
  background:var(--panel);border:1px solid var(--bhi);border-radius:var(--r);
  overflow:hidden;display:none;
}
#settings-panel.open{display:block}
.settings-inner{padding:18px 20px;display:flex;flex-direction:column;gap:14px}
.field-row{display:flex;align-items:center;gap:12px;flex-wrap:wrap}
.field-label{
  font-family:'JetBrains Mono',monospace;font-size:9px;letter-spacing:2px;
  color:var(--t3);text-transform:uppercase;white-space:nowrap;min-width:100px;
}
.field-input{
  flex:1;background:var(--inp);border:1px solid var(--b);color:var(--t1);
  font-family:'JetBrains Mono',monospace;font-size:11.5px;
  padding:9px 13px;border-radius:var(--r);outline:none;min-width:200px;
  transition:border-color .2s;
}
.field-input:focus{border-color:var(--teal)}
.field-input::placeholder{color:var(--t3)}
.save-btn{
  font-family:'JetBrains Mono',monospace;font-size:9px;font-weight:700;letter-spacing:1px;
  padding:8px 16px;border:1px solid var(--teal);background:var(--teal2);
  color:var(--teal);cursor:pointer;border-radius:var(--r);transition:all .2s;white-space:nowrap;
}
.save-btn:hover{background:var(--teal);color:#060810}
.settings-note{
  font-family:'JetBrains Mono',monospace;font-size:9px;color:var(--t3);
  padding:10px 14px;background:var(--card);border:1px solid var(--b);border-radius:5px;
  line-height:1.6;
}
.key-status{
  font-family:'JetBrains Mono',monospace;font-size:9px;
  padding:3px 9px;border-radius:10px;border:1px solid;
}
.key-set{background:var(--bull2);border-color:var(--bull);color:var(--bull)}
.key-unset{background:var(--bear2);border-color:var(--bear);color:var(--bear)}

/* ── STATS ── */
#stats-grid{display:grid;grid-template-columns:repeat(5,1fr);gap:8px}
.sbox{background:var(--panel);border:1px solid var(--b);border-radius:var(--r);padding:13px 15px}
.sbox .sl{font-family:'JetBrains Mono',monospace;font-size:8px;letter-spacing:1.5px;color:var(--t3);text-transform:uppercase;margin-bottom:6px}
.sbox .sv{font-family:'JetBrains Mono',monospace;font-size:14px;font-weight:700;color:var(--t1)}
.sbox .ss{font-family:'JetBrains Mono',monospace;font-size:9px;color:var(--t3);margin-top:3px}

/* ── TRADINGVIEW ── */
#tv-wrap{background:var(--panel);border:1px solid var(--b);border-radius:var(--r);overflow:hidden;height:520px;position:relative}
#tv-chart{width:100%;height:100%}
.tv-tf-bar{
  position:absolute;top:0;left:0;right:0;z-index:10;
  display:flex;gap:4px;padding:8px 12px;background:rgba(11,14,24,.9);
  border-bottom:1px solid var(--b);backdrop-filter:blur(8px);flex-wrap:wrap;
}
.tv-tf-btn{
  font-family:'JetBrains Mono',monospace;font-size:9px;font-weight:600;
  padding:4px 9px;border:1px solid var(--b);background:transparent;
  color:var(--t3);cursor:pointer;border-radius:4px;transition:all .15s;letter-spacing:.5px;
}
.tv-tf-btn:hover{color:var(--t1);border-color:var(--bhi)}
.tv-tf-btn.active{background:var(--teal2);border-color:var(--teal);color:var(--teal)}

/* ── MTF KLINES ── */
#mtf-wrap{background:var(--panel);border:1px solid var(--b);border-radius:var(--r);overflow:hidden}
#tf-bar{display:flex;border-bottom:1px solid var(--b);background:var(--card)}
.tf-btn{
  font-family:'JetBrains Mono',monospace;font-size:11px;font-weight:600;
  padding:9px 18px;cursor:pointer;color:var(--t3);border-right:1px solid var(--b);
  transition:all .15s;border-bottom:2px solid transparent;position:relative;top:1px;
}
.tf-btn:hover{color:var(--t1)}.tf-btn.active{color:var(--teal);border-bottom-color:var(--teal);background:var(--panel)}
.kline-meta{
  display:flex;gap:16px;flex-wrap:wrap;
  padding:8px 14px;background:var(--card);border-bottom:1px solid var(--b);
  font-family:'JetBrains Mono',monospace;font-size:9px;color:var(--t3);
}
.kline-meta span{color:var(--t2)}.kline-meta b{color:var(--teal)}
#kline-scroll{overflow-x:auto;max-height:260px;overflow-y:auto}
#ktable{width:100%;border-collapse:collapse;font-family:'JetBrains Mono',monospace;font-size:10px}
#ktable th{
  position:sticky;top:0;background:var(--card);padding:6px 10px;
  text-align:right;color:var(--t3);font-size:8px;letter-spacing:1px;
  text-transform:uppercase;border-bottom:1px solid var(--b);
}
#ktable th:first-child{text-align:left}
#ktable td{padding:5px 10px;text-align:right;border-bottom:1px solid #0c0f1c;color:var(--t2)}
#ktable td:first-child{text-align:left;color:var(--t3)}
.fvg-u{display:inline-block;padding:1px 5px;border-radius:2px;font-size:8px;font-weight:700;background:var(--bull2);color:var(--bull)}
.fvg-d{display:inline-block;padding:1px 5px;border-radius:2px;font-size:8px;font-weight:700;background:var(--bear2);color:var(--bear)}
.ob-t{display:inline-block;padding:1px 5px;border-radius:2px;font-size:8px;font-weight:700;background:var(--violet2);color:var(--violet)}
.bos-u{display:inline-block;padding:1px 5px;border-radius:2px;font-size:8px;font-weight:700;background:var(--bull2);color:var(--bull)}
.bos-d{display:inline-block;padding:1px 5px;border-radius:2px;font-size:8px;font-weight:700;background:var(--bear2);color:var(--bear)}
.live-candle{animation:livePulse 1.5s infinite}
@keyframes livePulse{0%,100%{opacity:1}50%{opacity:.65}}

/* ── MARKET ROW ── */
#mkt-row{display:grid;grid-template-columns:1fr 1fr;gap:14px}
.mkt-box{background:var(--panel);border:1px solid var(--b);border-radius:var(--r);padding:16px}
.bhead{
  display:grid;grid-template-columns:1fr 1fr 1fr;
  font-family:'JetBrains Mono',monospace;font-size:8px;letter-spacing:1px;
  color:var(--t3);text-transform:uppercase;padding:4px 0;
  border-bottom:1px solid var(--b);margin-bottom:5px;
}
.bhead span:last-child,.brow>span:last-child{text-align:right}
.brow{display:grid;grid-template-columns:1fr 1fr 1fr;font-family:'JetBrains Mono',monospace;font-size:10px;padding:3px 0;position:relative}
.brow .bar{position:absolute;top:0;height:100%;opacity:.12;border-radius:2px;right:0}
.ask .bar{background:var(--bear)}.bid .bar{background:var(--bull)}
.ask span:first-child{color:var(--bear)}.bid span:first-child{color:var(--bull)}
.spread{font-family:'JetBrains Mono',monospace;font-size:9px;color:var(--amber);background:var(--amber2);text-align:center;padding:5px;border-radius:5px;margin-top:8px}
.trow{
  display:grid;grid-template-columns:1fr 1fr 1fr 1fr;
  font-family:'JetBrains Mono',monospace;font-size:9.5px;
  padding:3.5px 0;border-bottom:1px solid #0c0f1c;
  animation:fadein .3s ease;
}
@keyframes fadein{from{opacity:0;transform:translateY(-3px)}to{opacity:1;transform:translateY(0)}}
.tb{color:var(--bull)}.ts{color:var(--bear)}
.th-row{
  display:grid;grid-template-columns:1fr 1fr 1fr 1fr;
  font-family:'JetBrains Mono',monospace;font-size:8px;letter-spacing:1px;
  color:var(--t3);text-transform:uppercase;padding:4px 0;
  border-bottom:1px solid var(--b);margin-bottom:4px;
}

/* ── SIGNALS ── */
#signals-wrap{background:var(--panel);border:1px solid var(--b);border-radius:var(--r);overflow:hidden}
#sig-head{
  display:flex;align-items:center;gap:12px;flex-wrap:wrap;
  padding:12px 18px;border-bottom:1px solid var(--b);background:var(--card);
}
#sig-title{font-family:'JetBrains Mono',monospace;font-size:10px;font-weight:700;letter-spacing:3px;color:var(--gold)}
#sig-status{font-family:'JetBrains Mono',monospace;font-size:8.5px;color:var(--t3);flex:1}
#gen-btn{
  font-family:'JetBrains Mono',monospace;font-size:10px;font-weight:700;letter-spacing:1px;
  padding:7px 18px;border:1px solid var(--gold);background:var(--gold2);
  color:var(--gold);cursor:pointer;border-radius:var(--r);transition:all .2s;
}
#gen-btn:hover:not(:disabled){background:var(--gold);color:#060810;box-shadow:0 0 20px #f0b42950}
#gen-btn:disabled{border-color:var(--b);background:transparent;color:var(--t3);cursor:not-allowed}
#sig-grid{display:grid;grid-template-columns:repeat(6,1fr);gap:9px;padding:16px 18px}
.sigbox{background:var(--card);border:1px solid var(--b);border-radius:var(--r);padding:12px 8px;text-align:center;transition:all .3s;cursor:default}
.sigbox .stf{font-family:'JetBrains Mono',monospace;font-size:9px;letter-spacing:1px;color:var(--t3);margin-bottom:7px}
.sigbox .sdir{font-family:'JetBrains Mono',monospace;font-size:14px;font-weight:700;margin-bottom:5px}
.sigbox .sconf{font-family:'JetBrains Mono',monospace;font-size:9px;color:var(--t3)}
.sigbox .sreason{font-family:'Inter',sans-serif;font-size:9px;color:var(--t3);margin-top:5px;line-height:1.4;display:none}
.sigbox:hover .sreason{display:block}
.sigbox.LONG{border-color:var(--bull);box-shadow:0 0 14px var(--bull2)}.sigbox.LONG .sdir{color:var(--bull)}
.sigbox.SHORT{border-color:var(--bear);box-shadow:0 0 14px var(--bear2)}.sigbox.SHORT .sdir{color:var(--bear)}
.sigbox.NEUTRAL{border-color:var(--amber)}.sigbox.NEUTRAL .sdir{color:var(--amber)}
#sig-summary{padding:0 18px 16px;display:none}
.sig-meta-row{
  display:flex;gap:18px;flex-wrap:wrap;margin-bottom:8px;
  font-family:'JetBrains Mono',monospace;font-size:9px;color:var(--gold);
}
.sig-body{font-family:'Inter',sans-serif;font-size:12.5px;color:var(--t2);line-height:1.65}

/* ── MEMORY PANEL ── */
#memory-panel{background:var(--panel);border:1px solid var(--bhi);border-radius:var(--r);overflow:hidden}
#mem-head{
  display:flex;align-items:center;gap:12px;
  padding:12px 18px;border-bottom:1px solid var(--b);background:var(--card);
}
#mem-title{font-family:'JetBrains Mono',monospace;font-size:10px;font-weight:700;letter-spacing:3px;color:var(--violet)}
#mem-count{font-family:'JetBrains Mono',monospace;font-size:8.5px;color:var(--t3)}
#clear-mem-btn{
  margin-left:auto;
  font-family:'JetBrains Mono',monospace;font-size:9px;letter-spacing:1px;
  padding:5px 12px;border:1px solid var(--b);background:transparent;
  color:var(--t3);cursor:pointer;border-radius:var(--r);transition:all .2s;
}
#clear-mem-btn:hover{border-color:var(--bear);color:var(--bear)}
#mem-body{padding:14px 18px;display:flex;flex-direction:column;gap:8px;max-height:200px;overflow-y:auto}
.mem-item{
  display:flex;gap:10px;padding:8px 12px;
  background:var(--card);border:1px solid var(--b);border-radius:5px;
  border-left:3px solid var(--violet);
}
.mem-icon{font-size:14px;flex-shrink:0;margin-top:1px}
.mem-text{font-family:'Inter',sans-serif;font-size:12px;color:var(--t2);line-height:1.55;flex:1}
.mem-text strong{color:var(--violet);font-size:10px;font-family:'JetBrains Mono',monospace;letter-spacing:1px}
.mem-empty{font-family:'JetBrains Mono',monospace;font-size:10px;color:var(--t3);text-align:center;padding:16px}

/* ══════════════════
   CONVERSATION
══════════════════ */
#conv-section{background:var(--panel);border:1px solid var(--b);border-radius:var(--r);display:flex;flex-direction:column;overflow:hidden;min-height:700px}
#conv-topbar{
  display:flex;align-items:center;gap:10px;flex-wrap:wrap;
  padding:12px 18px;background:var(--card);border-bottom:1px solid var(--b);
}
#conv-label{font-family:'JetBrains Mono',monospace;font-size:10px;font-weight:700;letter-spacing:3px;color:var(--teal);flex-shrink:0}
#msg-count{font-family:'JetBrains Mono',monospace;font-size:8.5px;background:var(--panel);border:1px solid var(--b);color:var(--t3);padding:2px 9px;border-radius:10px}
.mlabel{font-family:'JetBrains Mono',monospace;font-size:8px;letter-spacing:2px;color:var(--t3);text-transform:uppercase;flex-shrink:0}
#model-select{
  background:var(--inp);border:1px solid var(--b);color:var(--teal);
  font-family:'JetBrains Mono',monospace;font-size:10.5px;
  padding:6px 10px;border-radius:var(--r);cursor:pointer;outline:none;transition:border-color .2s;
  min-width:180px;max-width:340px;flex:1;
}
#model-select:hover,#model-select:focus{border-color:var(--teal)}
#model-select option{background:#101422;color:var(--t1)}
#model-count{font-family:'JetBrains Mono',monospace;font-size:8px;color:var(--t3);white-space:nowrap}
#refresh-m{background:transparent;border:1px solid var(--b);color:var(--t2);font-size:13px;padding:4px 8px;border-radius:var(--r);cursor:pointer;transition:all .2s}
#refresh-m:hover{border-color:var(--teal);color:var(--teal)}
#clear-conv{
  font-family:'JetBrains Mono',monospace;font-size:8.5px;
  background:transparent;border:1px solid var(--b);color:var(--t3);
  padding:5px 11px;border-radius:var(--r);cursor:pointer;transition:all .2s;margin-left:auto;
}
#clear-conv:hover{border-color:var(--bear);color:var(--bear)}

#chat-area{flex:1;overflow-y:auto;padding:26px 24px;display:flex;flex-direction:column;gap:20px;min-height:620px}

.syspill{
  align-self:center;font-family:'JetBrains Mono',monospace;font-size:8.5px;
  color:var(--t3);background:var(--card);border:1px solid var(--b);
  padding:4px 16px;border-radius:20px;letter-spacing:.8px;max-width:80%;text-align:center;
}

.mgroup{display:flex;flex-direction:column;gap:6px;animation:fadein .28s ease}
.mgroup.me{align-self:flex-end;align-items:flex-end;max-width:85%}
.mgroup.ai{align-self:flex-start;align-items:flex-start;max-width:90%}
.mmeta{display:flex;align-items:center;gap:8px;font-family:'JetBrains Mono',monospace;font-size:8px;color:var(--t3);padding:0 4px}
.mgroup.me .mmeta{flex-direction:row-reverse}
.mtag{padding:2px 8px;border-radius:10px;font-size:7.5px;font-weight:700;border:1px solid;letter-spacing:.5px}
.mtag.you{background:var(--teal2);border-color:var(--teal);color:var(--teal)}
.mtag.bot{background:var(--violet2);border-color:var(--violet);color:var(--violet)}
.mtime{color:var(--t3);font-size:8px}

.bubble{padding:13px 17px;border-radius:10px;font-family:'Inter',sans-serif;font-size:13.5px;line-height:1.72;word-break:break-word}
.mgroup.me .bubble{background:var(--teal2);border:1px solid #00c9a738;border-radius:14px 14px 3px 14px;color:var(--t1)}
.mgroup.ai .bubble{background:var(--card);border:1px solid var(--b);border-radius:3px 14px 14px 14px;color:var(--t1)}

/* rich content */
.bubble h1,.bubble h2,.bubble h3{color:var(--teal);margin:12px 0 6px;font-family:'JetBrains Mono',monospace;font-size:13px;font-weight:700}
.bubble strong{color:var(--t1);font-weight:700}.bubble em{color:var(--amber);font-style:normal;font-weight:500}
.bubble code{background:#080b14;padding:2px 6px;border-radius:3px;font-family:'JetBrains Mono',monospace;font-size:11px;color:var(--teal)}
.bubble pre{background:#080b14;border:1px solid var(--b);border-radius:6px;padding:13px 15px;overflow-x:auto;margin:9px 0;font-family:'JetBrains Mono',monospace;font-size:11px;color:var(--t2);line-height:1.6}
.bubble pre code{background:none;padding:0;color:inherit}
.bubble ul,.bubble ol{padding-left:22px;margin:7px 0}.bubble li{margin:4px 0;line-height:1.65}
.bubble hr{border:none;border-top:1px solid var(--b);margin:12px 0}
.bubble blockquote{border-left:3px solid var(--teal);padding:7px 14px;margin:9px 0;background:var(--teal3);color:var(--t2);font-size:12.5px;border-radius:0 6px 6px 0}
.bubble table{border-collapse:collapse;width:100%;margin:9px 0;font-size:12px}
.bubble table th{background:#0b0e18;color:var(--t2);padding:6px 10px;text-align:left;border:1px solid var(--b);font-family:'JetBrains Mono',monospace;font-size:10px}
.bubble table td{padding:5px 10px;border:1px solid var(--b);color:var(--t1)}
.bubble table tr:nth-child(even) td{background:#0d1020}
.bubble a{color:var(--teal);text-decoration:underline}
.bubble p{margin:5px 0}

/* typing */
.typing-bub{display:flex;align-items:center;gap:9px;padding:13px 17px;background:var(--card);border:1px solid var(--b);border-radius:3px 14px 14px 14px}
.dots span{display:inline-block;width:6px;height:6px;border-radius:50%;background:var(--teal);animation:dp 1.2s infinite}
.dots span:nth-child(2){animation-delay:.2s}.dots span:nth-child(3){animation-delay:.4s}
@keyframes dp{0%,80%,100%{opacity:.2;transform:scale(.65)}40%{opacity:1;transform:scale(1)}}
.typing-txt{font-family:'JetBrains Mono',monospace;font-size:10px;color:var(--t3)}

/* ── FIXED INPUT ── */
#input-fixed{
  position:fixed;bottom:0;left:0;right:0;z-index:200;
  background:rgba(6,8,16,.97);border-top:1px solid var(--bhi);
  backdrop-filter:blur(16px);padding:12px 22px;
}
#input-inner{max-width:1300px;margin:0 auto;display:flex;gap:10px;align-items:flex-end}
#chat-input{
  flex:1;background:var(--card);border:1px solid var(--b);color:var(--t1);
  font-family:'Inter',sans-serif;font-size:13.5px;
  padding:11px 16px;border-radius:10px;outline:none;resize:none;
  min-height:46px;max-height:140px;overflow-y:auto;
  transition:border-color .2s,box-shadow .2s;line-height:1.55;
}
#chat-input:focus{border-color:var(--teal);box-shadow:0 0 0 3px var(--teal3)}
#chat-input::placeholder{color:var(--t3)}
#send-btn{
  background:var(--teal);border:none;color:#060810;
  font-family:'JetBrains Mono',monospace;font-size:11px;font-weight:700;
  padding:0 22px;height:46px;border-radius:10px;
  cursor:pointer;letter-spacing:1px;transition:all .2s;white-space:nowrap;flex-shrink:0;
}
#send-btn:hover:not(:disabled){background:#00dfbb;box-shadow:0 0 22px #00c9a755}
#send-btn:disabled{background:var(--t3);cursor:not-allowed;box-shadow:none}

::-webkit-scrollbar{width:3px;height:3px}
::-webkit-scrollbar-track{background:transparent}
::-webkit-scrollbar-thumb{background:var(--b);border-radius:2px}
::-webkit-scrollbar-thumb:hover{background:#2a3a55}

@media(max-width:900px){
  #stats-grid{grid-template-columns:repeat(3,1fr)}
  #mkt-row{grid-template-columns:1fr}
  #sig-grid{grid-template-columns:repeat(3,1fr)}
  #tv-wrap{height:380px}
}
@media(max-width:600px){
  #stats-grid{grid-template-columns:1fr 1fr}
  #sig-grid{grid-template-columns:repeat(2,1fr)}
  #page{padding:12px 12px 120px}
  #hdr{padding:8px 12px}
}
</style>
</head>
<body>

<!-- STICKY HEADER -->
<div id="hdr">
  <div class="logo">KAMALA <b>QUANT</b></div>
  <div class="vsep"></div>
  <div id="pairs">
    <button class="pb active" data-s="PAXGUSDT" data-d="PAXG/USDT">PAXG/USDT</button>
    <button class="pb" data-s="EURUSDT"  data-d="EUR/USDT">EUR/USDT</button>
    <button class="pb" data-s="BTCUSDT"  data-d="BTC/USDT">BTC/USDT</button>
    <button class="pb" data-s="ETHUSDT"  data-d="ETH/USDT">ETH/USDT</button>
    <button class="pb" data-s="SOLUSDT"  data-d="SOL/USDT">SOL/USDT</button>
    <button class="pb" data-s="BNBUSDT"  data-d="BNB/USDT">BNB/USDT</button>
  </div>
  <div class="hright">
    <div id="wsdot"></div>
    <div id="tk-price">—</div>
    <div id="tk-chg" class="pos">—</div>
    <button id="settings-toggle">⚙ SETTINGS</button>
  </div>
</div>

<!-- PAGE -->
<div id="page">

  <!-- SETTINGS -->
  <div id="settings-panel">
    <div class="settings-inner">
      <div class="sh" style="margin-bottom:6px">API CONFIGURATION <span class="badge badge-ai">STORED LOCALLY</span></div>
      <div class="settings-note">
        Your API key is stored only in your browser's localStorage — it is never sent anywhere except directly to OpenRouter.
        Never commit this key to GitHub. Add your key here manually each time, or save it locally below.
      </div>
      <div class="field-row">
        <div class="field-label">OPENROUTER KEY</div>
        <input type="password" class="field-input" id="api-key-input" placeholder="sk-or-v1-…  (paste your OpenRouter key)">
        <div id="key-status" class="key-status key-unset">NOT SET</div>
        <button class="save-btn" id="save-key-btn">SAVE KEY</button>
        <button class="save-btn" style="border-color:var(--bear);background:var(--bear2);color:var(--bear)" id="clear-key-btn">CLEAR</button>
      </div>
      <div class="settings-note" style="color:var(--t2)">
        ⚠ To use on GitHub Pages: open the app → Settings → paste key → Save. The key lives only in this browser tab's localStorage.
        Get your free key at <strong>openrouter.ai/keys</strong>
      </div>
    </div>
  </div>

  <!-- STATS -->
  <div>
    <div class="sh">LIVE MARKET STATS <span class="badge badge-live">LIVE</span></div>
    <div id="stats-grid">
      <div class="sbox"><div class="sl">LAST PRICE</div><div class="sv" id="s-price">—</div><div class="ss" id="s-pair-lbl">PAXG/USDT</div></div>
      <div class="sbox"><div class="sl">24H HIGH</div><div class="sv" id="s-high">—</div><div class="ss" id="s-high-dist">—</div></div>
      <div class="sbox"><div class="sl">24H LOW</div><div class="sv" id="s-low">—</div><div class="ss" id="s-low-dist">—</div></div>
      <div class="sbox"><div class="sl">24H VOLUME</div><div class="sv" id="s-vol">—</div><div class="ss" id="s-trades">Trades: —</div></div>
      <div class="sbox"><div class="sl">24H CHANGE</div><div class="sv" id="s-chng">—</div><div class="ss" id="s-bias">Bias: —</div></div>
    </div>
  </div>

  <!-- TRADINGVIEW CHART -->
  <div>
    <div class="sh">TRADINGVIEW CHART <span class="badge badge-live">LIVE</span></div>
    <div id="tv-wrap">
      <div class="tv-tf-bar">
        <span style="font-family:'JetBrains Mono',monospace;font-size:9px;color:var(--t3);letter-spacing:1px;margin-right:4px">TF:</span>
        <button class="tv-tf-btn" data-i="1">1m</button>
        <button class="tv-tf-btn" data-i="5">5m</button>
        <button class="tv-tf-btn active" data-i="15">15m</button>
        <button class="tv-tf-btn" data-i="60">1h</button>
        <button class="tv-tf-btn" data-i="240">4h</button>
        <button class="tv-tf-btn" data-i="D">1D</button>
        <button class="tv-tf-btn" data-i="W">1W</button>
      </div>
      <div id="tv-chart" style="padding-top:46px;height:100%"></div>
    </div>
  </div>

  <!-- MTF KLINES -->
  <div>
    <div class="sh">MULTI-TIMEFRAME KLINES · OHLCV <span class="badge badge-live">BINANCE REAL-TIME</span></div>
    <div id="mtf-wrap">
      <div id="tf-bar">
        <div class="tf-btn active" data-tf="1m">1m</div>
        <div class="tf-btn" data-tf="5m">5m</div>
        <div class="tf-btn" data-tf="15m">15m</div>
        <div class="tf-btn" data-tf="1h">1h</div>
        <div class="tf-btn" data-tf="4h">4h</div>
        <div class="tf-btn" data-tf="1d">1D</div>
      </div>
      <div class="kline-meta" id="kline-meta">Loading market structure data…</div>
      <div id="kline-scroll">
        <table id="ktable">
          <thead>
            <tr>
              <th style="text-align:left">TIME</th>
              <th>OPEN</th><th>HIGH</th><th>LOW</th><th>CLOSE</th>
              <th>VOL (USDT)</th><th>TRADES</th><th>CHG%</th><th>SMC TAGS</th>
            </tr>
          </thead>
          <tbody id="ktbody"></tbody>
        </table>
      </div>
    </div>
  </div>

  <!-- ORDER BOOK + TRADES -->
  <div>
    <div class="sh">ORDER BOOK &amp; RECENT TRADES <span class="badge badge-live">LIVE</span></div>
    <div id="mkt-row">
      <div class="mkt-box">
        <div class="sh" style="margin-bottom:10px">ORDER BOOK</div>
        <div style="display:grid;grid-template-columns:1fr 1fr;gap:12px">
          <div>
            <div class="bhead" style="color:var(--bear)"><span>ASK PRICE</span><span>QTY</span><span>TOTAL</span></div>
            <div id="asks-list"></div>
          </div>
          <div>
            <div class="bhead" style="color:var(--bull)"><span>BID PRICE</span><span>QTY</span><span>TOTAL</span></div>
            <div id="bids-list"></div>
          </div>
        </div>
        <div class="spread" id="spread-row">SPREAD —</div>
      </div>
      <div class="mkt-box">
        <div class="sh" style="margin-bottom:10px">RECENT TRADES</div>
        <div class="th-row"><span>PRICE</span><span>QTY</span><span>SIDE</span><span>TIME</span></div>
        <div id="trades-list"></div>
      </div>
    </div>
  </div>

  <!-- AI SIGNALS -->
  <div>
    <div class="sh">AI SIGNALS · MULTI-TIMEFRAME <span class="badge badge-ai">AI POWERED</span></div>
    <div id="signals-wrap">
      <div id="sig-head">
        <div id="sig-title">⚡ AI MARKET SIGNALS</div>
        <div id="sig-status">Ready — uses live OHLCV + memory context</div>
        <button id="gen-btn">GENERATE SIGNALS ▶</button>
      </div>
      <div id="sig-grid">
        <div class="sigbox" id="sb-1m"><div class="stf">1m</div><div class="sdir">—</div><div class="sconf">—</div><div class="sreason"></div></div>
        <div class="sigbox" id="sb-5m"><div class="stf">5m</div><div class="sdir">—</div><div class="sconf">—</div><div class="sreason"></div></div>
        <div class="sigbox" id="sb-15m"><div class="stf">15m</div><div class="sdir">—</div><div class="sconf">—</div><div class="sreason"></div></div>
        <div class="sigbox" id="sb-1h"><div class="stf">1h</div><div class="sdir">—</div><div class="sconf">—</div><div class="sreason"></div></div>
        <div class="sigbox" id="sb-4h"><div class="stf">4h</div><div class="sdir">—</div><div class="sconf">—</div><div class="sreason"></div></div>
        <div class="sigbox" id="sb-1d"><div class="stf">1D</div><div class="sdir">—</div><div class="sconf">—</div><div class="sreason"></div></div>
      </div>
      <div id="sig-summary"></div>
    </div>
  </div>

  <!-- MEMORY PANEL -->
  <div>
    <div class="sh">AI MEMORY <span class="badge badge-ai">PERSISTENT</span></div>
    <div id="memory-panel">
      <div id="mem-head">
        <div id="mem-title">🧠 WHAT I REMEMBER</div>
        <div id="mem-count">0 memories</div>
        <button id="clear-mem-btn">CLEAR MEMORY</button>
      </div>
      <div id="mem-body">
        <div class="mem-empty">No memories yet — start chatting and I'll remember key insights</div>
      </div>
    </div>
  </div>

  <!-- CONVERSATION -->
  <div>
    <div class="sh">AI CONVERSATION <span class="badge badge-ai">WITH MEMORY</span></div>
    <div id="conv-section">
      <div id="conv-topbar">
        <div id="conv-label">💬 CHAT</div>
        <div id="msg-count">0 messages</div>
        <div class="mlabel" style="margin-left:8px">MODEL</div>
        <select id="model-select"><option value="">Loading models…</option></select>
        <div id="model-count">—</div>
        <button id="refresh-m" title="Refresh models list">⟳</button>
        <button id="clear-conv">CLEAR CHAT</button>
      </div>
      <div id="chat-area">
        <div class="syspill">KAMALA QUANT · AI TERMINAL · MEMORY ENABLED</div>
      </div>
    </div>
  </div>

</div><!-- /page -->

<!-- FIXED INPUT -->
<div id="input-fixed">
  <div id="input-inner">
    <textarea id="chat-input" placeholder="Ask anything — trading, macro, strategy, crypto, forex, or just chat…   Enter to send · Shift+Enter new line" rows="1"></textarea>
    <button id="send-btn">SEND ▶</button>
  </div>
</div>

<!-- TradingView -->
<script src="https://s3.tradingview.com/tv.js"></script>

<script>
// ═══════════════════════════════════════════════════
// CONFIG & STATE
// ═══════════════════════════════════════════════════
const OR_BASE='https://openrouter.ai/api/v1';
const BN='https://api.binance.com/api/v3';
const BN_WS='wss://stream.binance.com:9443/ws';
const SITE='https://kamalaquant.app';
const BRAND='KAMALA QUANT';
const LS_KEY='kq_key';
const LS_HIST='kq_history';
const LS_MEM='kq_memory';

let OR_KEY='';
let sym='PAXGUSDT',disp='PAXG/USDT';
let ws=null,tvWidget=null,tvInterval='15';
let stats24={},klines={},activeTf='1m';
let chatHistory=[];
let memories=[];
let busy=false,msgCount=0;

// ═══════════════════════════════════════════════════
// UTILS
// ═══════════════════════════════════════════════════
const fp=v=>{const n=+v;if(isNaN(n))return'—';return n>10000?n.toFixed(2):n>1?n.toFixed(4):n.toFixed(6)};
const fv=(n,d=2)=>{const v=+n;if(isNaN(v))return'—';if(v>=1e9)return(v/1e9).toFixed(2)+'B';if(v>=1e6)return(v/1e6).toFixed(2)+'M';if(v>=1e3)return(v/1e3).toFixed(2)+'K';return v.toFixed(d)};
const esc=s=>String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
const tsNow=()=>new Date().toLocaleTimeString('en-GB',{hour:'2-digit',minute:'2-digit',second:'2-digit'});
const dtfmt=ms=>{const d=new Date(ms);return d.toLocaleString('en-GB',{month:'short',day:'2-digit',hour:'2-digit',minute:'2-digit'})};
const sleep=ms=>new Promise(r=>setTimeout(r,ms));

// markdown
function md(txt){
  if(!txt)return'';
  let s=esc(txt);
  s=s.replace(/```(\w*)\n?([\s\S]*?)```/g,(_,l,c)=>`<pre><code>${c.trim()}</code></pre>`);
  s=s.replace(/`([^`\n]+)`/g,(_,c)=>`<code>${c}</code>`);
  s=s.replace(/^### (.+)$/gm,'<h3>$1</h3>');
  s=s.replace(/^## (.+)$/gm,'<h2>$1</h2>');
  s=s.replace(/^# (.+)$/gm,'<h1>$1</h1>');
  s=s.replace(/\*\*([^*\n]+)\*\*/g,'<strong>$1</strong>');
  s=s.replace(/\*([^*\n]+)\*/g,'<em>$1</em>');
  s=s.replace(/^&gt; (.+)$/gm,'<blockquote>$1</blockquote>');
  s=s.replace(/^---$/gm,'<hr>');
  s=s.replace(/^\s*[-*•] (.+)$/gm,'<li>$1</li>');
  s=s.replace(/(<li>[\s\S]*?<\/li>\n?)+/g,m=>`<ul>${m}</ul>`);
  s=s.replace(/^\d+\. (.+)$/gm,'<li>$1</li>');
  // table
  s=s.replace(/(\|.+\|\n?)+/g,tbl=>{
    const rows=tbl.trim().split('\n').filter(r=>r.trim()&&!r.match(/^\|[-\s|:]+\|$/));
    if(!rows.length)return tbl;
    const cells=r=>r.split('|').filter((_,i,a)=>i>0&&i<a.length-1).map(c=>`<td>${c.trim()}</td>`).join('');
    const hcells=r=>r.split('|').filter((_,i,a)=>i>0&&i<a.length-1).map(c=>`<th>${c.trim()}</th>`).join('');
    return `<table><thead><tr>${hcells(rows[0])}</tr></thead><tbody>${rows.slice(1).map(r=>`<tr>${cells(r)}</tr>`).join('')}</tbody></table>`;
  });
  s=s.replace(/\n{2,}/g,'</p><p>');
  s=`<p>${s}</p>`;
  s=s.replace(/<p><\/p>/g,'');
  s=s.replace(/\n/g,'<br>');
  return s;
}

// ═══════════════════════════════════════════════════
// API KEY MANAGEMENT
// ═══════════════════════════════════════════════════
function loadKey(){
  OR_KEY=localStorage.getItem(LS_KEY)||'';
  const inp=document.getElementById('api-key-input');
  const st=document.getElementById('key-status');
  if(OR_KEY){
    inp.value=OR_KEY;
    st.textContent='KEY SET ✓'; st.className='key-status key-set';
  } else {
    st.textContent='NOT SET'; st.className='key-status key-unset';
  }
}
function saveKey(){
  const v=document.getElementById('api-key-input').value.trim();
  if(!v){alert('Paste your OpenRouter key first');return;}
  OR_KEY=v;
  localStorage.setItem(LS_KEY,v);
  const st=document.getElementById('key-status');
  st.textContent='SAVED ✓'; st.className='key-status key-set';
  addSys('OpenRouter key saved to localStorage ✓');
  loadModels();
}
function clearKey(){
  OR_KEY='';localStorage.removeItem(LS_KEY);
  document.getElementById('api-key-input').value='';
  const st=document.getElementById('key-status');
  st.textContent='CLEARED'; st.className='key-status key-unset';
  addSys('API key cleared');
}

// ═══════════════════════════════════════════════════
// MEMORY SYSTEM
// ═══════════════════════════════════════════════════
function loadMemory(){
  try{memories=JSON.parse(localStorage.getItem(LS_MEM)||'[]')}catch{memories=[]}
  renderMemory();
}
function saveMemory(){localStorage.setItem(LS_MEM,JSON.stringify(memories.slice(-30)))}
function addMemory(text,icon='💡'){
  if(!text||text.length<10)return;
  const m={text,icon,ts:Date.now(),pair:disp};
  memories.push(m);
  saveMemory();renderMemory();
}
function renderMemory(){
  const el=document.getElementById('mem-body');
  document.getElementById('mem-count').textContent=`${memories.length} memories`;
  if(!memories.length){el.innerHTML='<div class="mem-empty">No memories yet — start chatting and I\'ll learn your preferences</div>';return;}
  el.innerHTML=memories.slice(-20).reverse().map(m=>`
    <div class="mem-item">
      <div class="mem-icon">${m.icon}</div>
      <div class="mem-text"><strong>${m.pair||''} · ${new Date(m.ts).toLocaleDateString('en-GB')}</strong><br>${esc(m.text)}</div>
    </div>`).join('');
}
function clearMemory(){if(!confirm('Clear all AI memory?'))return;memories=[];saveMemory();renderMemory();addSys('Memory cleared')}
function buildMemoryContext(){
  if(!memories.length)return'';
  return`\n\nLONG-TERM MEMORY (from past sessions):\n`+memories.slice(-12).map(m=>`- [${m.pair}] ${m.text}`).join('\n');
}

// Extract and save memory from AI responses
async function extractMemory(userMsg,aiReply){
  if(!OR_KEY||memories.length>28)return;
  const prompt=`The user said: "${userMsg.slice(0,200)}"\nThe AI replied: "${aiReply.slice(0,400)}"\n\nExtract 0-2 key insights worth remembering for future sessions (trading preferences, key levels mentioned, strategy preferences, user goals). Return ONLY a JSON array of short strings, max 15 words each. Example: ["Prefers M15 entries on EUR/USDT","Key resistance at 1.0850 mentioned"]. Return [] if nothing important.`;
  try{
    const res=await fetch(`${OR_BASE}/chat/completions`,{
      method:'POST',
      headers:{Authorization:`Bearer ${OR_KEY}`,'HTTP-Referer':SITE,'X-Title':BRAND,'Content-Type':'application/json'},
      body:JSON.stringify({model:document.getElementById('model-select').value||'openai/gpt-4o-mini',max_tokens:200,messages:[{role:'user',content:prompt}]})
    });
    const data=await res.json();
    const raw=data.choices?.[0]?.message?.content||'[]';
    const arr=JSON.parse(raw.replace(/```json|```/g,'').trim());
    const icons=['💡','📊','🎯','📌','⚡','🔑'];
    if(Array.isArray(arr))arr.forEach((t,i)=>{if(typeof t==='string')addMemory(t,icons[i%icons.length])});
  }catch(e){console.log('memory extract skipped',e.message)}
}

// Persist conversation to localStorage
function saveHistory(){localStorage.setItem(LS_HIST,JSON.stringify(chatHistory.slice(-40)))}
function loadHistory(){
  try{
    const h=JSON.parse(localStorage.getItem(LS_HIST)||'[]');
    if(h.length){
      chatHistory=h;
      h.forEach(m=>{
        if(m.role==='user')renderUserBubble(m.content,false);
        else if(m.role==='assistant')renderAiBubble(m.content,m.model||'AI',false);
      });
      msgCount=h.length;updateCount();
      addSys(`Restored ${h.length} messages from previous session`);
    }
  }catch{chatHistory=[]}
}

// ═══════════════════════════════════════════════════
// TRADINGVIEW CHART
// ═══════════════════════════════════════════════════
function initChart(symbol,interval){
  interval=interval||tvInterval;
  tvInterval=interval;
  const container=document.getElementById('tv-chart');
  if(tvWidget){try{tvWidget.remove()}catch(e){}}
  container.innerHTML='';
  if(typeof TradingView==='undefined'){
    container.innerHTML='<div style="display:flex;align-items:center;justify-content:center;height:100%;font-family:\'JetBrains Mono\',monospace;font-size:12px;color:var(--t3)">TradingView loading…</div>';
    return;
  }
  // Map Binance pair to TradingView symbol
  const tvSym=`BINANCE:${symbol}`;
  tvWidget=new TradingView.widget({
    container_id:'tv-chart',
    autosize:true,
    symbol:tvSym,
    interval:interval,
    timezone:'Etc/UTC',
    theme:'dark',
    style:'1',
    locale:'en',
    toolbar_bg:'#0b0e18',
    enable_publishing:false,
    hide_top_toolbar:false,
    hide_legend:false,
    hide_side_toolbar:false,
    allow_symbol_change:false,
    save_image:false,
    backgroundColor:'#060810',
    gridColor:'rgba(24,32,48,0.8)',
    studies:[],
    overrides:{
      'paneProperties.background':'#060810',
      'paneProperties.backgroundType':'solid',
      'paneProperties.gridLinesMode':'none',
      'scalesProperties.textColor':'#7d8ea8',
      'mainSeriesProperties.candleStyle.upColor':'#20d472',
      'mainSeriesProperties.candleStyle.downColor':'#f03e55',
      'mainSeriesProperties.candleStyle.borderUpColor':'#20d472',
      'mainSeriesProperties.candleStyle.borderDownColor':'#f03e55',
      'mainSeriesProperties.candleStyle.wickUpColor':'#20d47280',
      'mainSeriesProperties.candleStyle.wickDownColor':'#f03e5580',
    }
  });
  document.querySelectorAll('.tv-tf-btn').forEach(b=>b.classList.toggle('active',b.dataset.i===interval));
}

// ═══════════════════════════════════════════════════
// MODEL LOADING
// ═══════════════════════════════════════════════════
const PREFERRED=['openai/gpt-4o','openai/gpt-4o-mini','openai/o3-mini',
  'anthropic/claude-sonnet-4-6','anthropic/claude-3-5-haiku','anthropic/claude-opus-4-6',
  'google/gemini-2.0-flash-001','meta-llama/llama-3.3-70b-instruct',
  'deepseek/deepseek-chat','deepseek/deepseek-r1','mistralai/mistral-large',
  'x-ai/grok-2','perplexity/sonar-pro'];
const FALLBACK=['openai/gpt-4o','openai/gpt-4o-mini','anthropic/claude-sonnet-4-6',
  'anthropic/claude-3-5-haiku','google/gemini-2.0-flash-001',
  'meta-llama/llama-3.3-70b-instruct','deepseek/deepseek-chat',
  'mistralai/mistral-large','x-ai/grok-2'];

async function loadModels(){
  if(!OR_KEY){addSys('Set your OpenRouter API key in Settings first');return;}
  const sel=document.getElementById('model-select'),cnt=document.getElementById('model-count');
  sel.innerHTML='<option value="">Loading…</option>';cnt.textContent='…';
  try{
    const r=await fetch(`${OR_BASE}/models`,{headers:{Authorization:`Bearer ${OR_KEY}`}});
    const d=await r.json();
    const all=(d.data||[]).filter(m=>m.id&&m.id.includes('/')).sort((a,b)=>a.id.localeCompare(b.id));
    sel.innerHTML='';
    const rg=document.createElement('optgroup');rg.label='★ RECOMMENDED';
    PREFERRED.forEach(pid=>{const m=all.find(x=>x.id===pid);if(!m)return;const o=document.createElement('option');o.value=m.id;o.textContent=m.id+(m.context_length?` [${fv(m.context_length,0)}ctx]`:'');rg.appendChild(o)});
    if(rg.children.length)sel.appendChild(rg);
    const byP={};
    all.forEach(m=>{const[p]=m.id.split('/');if(!byP[p])byP[p]=[];byP[p].push(m)});
    Object.keys(byP).sort().forEach(prov=>{
      const grp=document.createElement('optgroup');grp.label=`— ${prov.toUpperCase()} —`;
      byP[prov].forEach(m=>{const o=document.createElement('option');o.value=m.id;o.textContent=m.id+(m.context_length?` [${fv(m.context_length,0)}ctx]`:'')+(m.pricing?.prompt?` $${(+m.pricing.prompt*1e6).toFixed(2)}/1M`:'');grp.appendChild(o)});
      sel.appendChild(grp);
    });
    const def=PREFERRED.find(p=>all.find(m=>m.id===p));
    if(def)sel.value=def;
    cnt.textContent=`${all.length} models`;
    addSys(`${all.length} models loaded`);
  }catch(e){
    sel.innerHTML='';const fg=document.createElement('optgroup');fg.label='FALLBACK';
    FALLBACK.forEach(id=>{const o=document.createElement('option');o.value=id;o.textContent=id;fg.appendChild(o)});
    sel.appendChild(fg);if(FALLBACK[0])sel.value=FALLBACK[0];
    cnt.textContent='fallback';addSys('Model fetch failed — using fallback list');
  }
}

// ═══════════════════════════════════════════════════
// BINANCE DATA
// ═══════════════════════════════════════════════════
async function fetch24h(s){
  try{
    const r=await fetch(`${BN}/ticker/24hr?symbol=${s}`);
    const d=await r.json();stats24=d;
    const p=+d.lastPrice,h=+d.highPrice,l=+d.lowPrice,c=+d.priceChangePercent;
    document.getElementById('s-price').textContent=fp(p);
    document.getElementById('s-pair-lbl').textContent=disp;
    document.getElementById('s-high').textContent=fp(h);
    document.getElementById('s-high-dist').textContent=`+${((h-p)/p*100).toFixed(2)}% from price`;
    document.getElementById('s-low').textContent=fp(l);
    document.getElementById('s-low-dist').textContent=`${((l-p)/p*100).toFixed(2)}% from price`;
    document.getElementById('s-vol').textContent=fv(d.quoteVolume,0)+' USDT';
    document.getElementById('s-trades').textContent='Trades: '+fv(d.count,0);
    const ce=document.getElementById('s-chng');
    ce.textContent=(c>=0?'+':'')+c.toFixed(2)+'%';ce.style.color=c>=0?'var(--bull)':'var(--bear)';
    document.getElementById('s-bias').textContent='Bias: '+(c>=0?'BULLISH ↑':'BEARISH ↓');
    document.getElementById('tk-price').textContent=fp(p);
    const tc=document.getElementById('tk-chg');
    tc.textContent=(c>=0?'+':'')+c.toFixed(2)+'%';tc.className=c>=0?'pos':'neg';
  }catch(e){console.error('24h',e)}
}

async function fetchKlines(s,tf,lim=100){
  const key=`${s}_${tf}`;
  try{
    // Fetch latest data — lim candles, last one is FORMING (live)
    const r=await fetch(`${BN}/klines?symbol=${s}&interval=${tf}&limit=${lim}`);
    const raw=await r.json();
    klines[key]=raw.map((k,i)=>({
      t:+k[0],o:+k[1],h:+k[2],l:+k[3],c:+k[4],v:+k[5],qv:+k[7],n:+k[8],
      forming:i===raw.length-1 // last candle is still forming
    }));
    return klines[key];
  }catch(e){console.error('klines',tf,e);return[]}
}

async function fetchAllTf(s){await Promise.all(['1m','5m','15m','1h','4h','1d'].map(tf=>fetchKlines(s,tf,100)))}

async function fetchBook(s){
  try{const r=await fetch(`${BN}/depth?symbol=${s}&limit=16`);const d=await r.json();renderBook(d.asks,d.bids)}catch(e){}
}
async function fetchTrades(s){
  try{
    const r=await fetch(`${BN}/trades?symbol=${s}&limit=26`);
    const d=await r.json();
    document.getElementById('trades-list').innerHTML=d.slice(-26).reverse().map(t=>{
      const b=!t.isBuyerMaker,cls=b?'tb':'ts';
      const tm=new Date(t.time).toLocaleTimeString('en-GB',{hour:'2-digit',minute:'2-digit',second:'2-digit'});
      return`<div class="trow"><span class="${cls}">${fp(t.price)}</span><span style="color:var(--t2)">${fv(+t.qty,4)}</span><span class="${cls}">${b?'BUY':'SELL'}</span><span style="color:var(--t3)">${tm}</span></div>`;
    }).join('');
  }catch(e){}
}

function renderBook(asks,bids){
  const aEl=document.getElementById('asks-list'),bEl=document.getElementById('bids-list');
  const tA=asks.slice(0,16).reverse(),tB=bids.slice(0,16);
  const mA=Math.max(...tA.map(r=>+r[1])),mB=Math.max(...tB.map(r=>+r[1]));
  const row=(r,s,mx)=>{
    const p=+r[0],q=+r[1],tot=(p*q).toFixed(0),pct=Math.min((q/mx)*100,100);
    return`<div class="brow ${s}"><span>${fp(r[0])}</span><span style="color:var(--t2)">${fv(q,4)}</span><span style="color:var(--t3);text-align:right">${fv(tot,0)}</span><div class="bar" style="width:${pct}%"></div></div>`;
  };
  aEl.innerHTML=tA.map(r=>row(r,'ask',mA)).join('');
  bEl.innerHTML=tB.map(r=>row(r,'bid',mB)).join('');
  if(asks[0]&&bids[0]){
    const sp=+asks[0][0]-+bids[0][0],spp=(sp/+asks[0][0]*100).toFixed(4);
    document.getElementById('spread-row').textContent=`SPREAD  ${fp(sp)}  (${spp}%)`;
  }
}

// SMC tagging
function tagCandle(cs,i){
  const c=cs[i],tags=[];
  if(i>=1){const p=cs[i-1];if(c.c>c.o&&p.c<p.o&&c.c>p.h)tags.push('<span class="ob-t">OB↑</span>');if(c.c<c.o&&p.c>p.o&&c.c<p.l)tags.push('<span class="ob-t">OB↓</span>')}
  if(i>=2){const a=cs[i-2];if(c.l>a.h)tags.push('<span class="fvg-u">FVG↑</span>');if(c.h<a.l)tags.push('<span class="fvg-d">FVG↓</span>')}
  if(i>=3){const w=cs.slice(Math.max(0,i-6),i);const mH=Math.max(...w.map(x=>x.h)),mL=Math.min(...w.map(x=>x.l));if(c.c>mH&&c.c>c.o)tags.push('<span class="bos-u">BOS↑</span>');if(c.c<mL&&c.c<c.o)tags.push('<span class="bos-d">BOS↓</span>')}
  return tags.join(' ');
}

function renderKlineTable(cs){
  const body=document.getElementById('ktbody');
  const last=cs.slice(-28).reverse();
  // Update meta bar
  const conf=cs.slice(0,-1); // confirmed candles only
  const sH=Math.max(...conf.slice(-20).map(c=>c.h)),sL=Math.min(...conf.slice(-20).map(c=>c.l));
  const rng=sH-sL;const cur=cs[cs.length-1];
  document.getElementById('kline-meta').innerHTML=
    `<span>Swing H: <b>${fp(sH)}</b></span><span>Swing L: <b>${fp(sL)}</b></span>`+
    `<span>Premium: <b>>${fp(sL+rng*.75)}</b></span><span>Discount: <b>&lt;${fp(sL+rng*.25)}</b></span>`+
    `<span>EQ: <b>${fp(sL+rng*.5)}</b></span>`+
    `<span style="color:var(--amber)">⚠ FORMING: <b>${fp(cur.c)}</b> (not confirmed)</span>`;
  body.innerHTML=last.map((c,idx)=>{
    const ri=cs.length-1-idx;
    const chg=(c.c-c.o)/c.o*100,bull=c.c>=c.o;
    const tags=c.forming?'<span style="color:var(--amber);font-size:9px;font-weight:700;font-family:\'JetBrains Mono\'">⚡ FORMING</span>':tagCandle(cs,ri);
    return`<tr class="${c.forming?'live-candle':''}" style="background:${c.forming?'rgba(245,166,35,.06)':bull?'rgba(32,212,114,.04)':'rgba(240,62,85,.04)'}">
      <td>${dtfmt(c.t)}${c.forming?' <span style="color:var(--amber);font-size:8px">●</span>':''}</td>
      <td style="color:var(--t2)">${fp(c.o)}</td>
      <td style="color:var(--bull)">${fp(c.h)}</td>
      <td style="color:var(--bear)">${fp(c.l)}</td>
      <td style="color:${bull?'var(--bull)':'var(--bear)'};font-weight:700">${fp(c.c)}</td>
      <td style="color:var(--t2)">${fv(c.qv,0)}</td>
      <td style="color:var(--t3)">${fv(c.n,0)}</td>
      <td style="color:${chg>=0?'var(--bull)':'var(--bear)'}">${chg>=0?'+':''}${chg.toFixed(2)}%</td>
      <td>${tags||'<span style="color:var(--t3)">—</span>'}</td>
    </tr>`;
  }).join('');
}

function switchTf(tf){
  activeTf=tf;
  document.querySelectorAll('.tf-btn').forEach(t=>t.classList.toggle('active',t.dataset.tf===tf));
  const cs=klines[`${sym}_${tf}`];
  if(cs&&cs.length)renderKlineTable(cs);
  else{document.getElementById('ktbody').innerHTML='<tr><td colspan="9" style="text-align:center;color:var(--t3);padding:18px;font-family:\'JetBrains Mono\',monospace;font-size:10px">Loading…</td></tr>';fetchKlines(sym,tf,100).then(c=>{if(c.length)renderKlineTable(c)})}
}

// ═══════════════════════════════════════════════════
// WEBSOCKET — Live Price Updates
// ═══════════════════════════════════════════════════
function connectWS(s){
  if(ws){try{ws.close()}catch(e){}}
  const dot=document.getElementById('wsdot');
  // Subscribe to miniTicker + kline stream for live candle updates
  ws=new WebSocket(`${BN_WS}/${s.toLowerCase()}@miniTicker`);
  ws.onopen=()=>dot.classList.add('on');
  ws.onclose=()=>{dot.classList.remove('on');setTimeout(()=>connectWS(s),3000)};
  ws.onerror=()=>dot.classList.remove('on');
  let lp=0;
  ws.onmessage=e=>{
    const d=JSON.parse(e.data),p=+d.c;
    const el=document.getElementById('tk-price');
    if(lp&&p!==lp){el.style.color=p>lp?'var(--bull)':'var(--bear)';setTimeout(()=>{el.style.color='var(--teal)'},700)}
    el.textContent=fp(d.c);
    document.getElementById('s-price').textContent=fp(d.c);
    // Update the forming candle in current TF cache
    const key=`${s}_${activeTf}`;
    if(klines[key]&&klines[key].length){
      const last=klines[key][klines[key].length-1];
      if(last.forming){
        last.c=p;
        last.h=Math.max(last.h,p);
        last.l=Math.min(last.l,p);
        // Re-render only the first row (forming)
        const firstRow=document.querySelector('#ktbody tr:first-child');
        if(firstRow){
          firstRow.querySelector('td:nth-child(5)').textContent=fp(p);
          firstRow.querySelector('td:nth-child(3)').textContent=fp(last.h);
          firstRow.querySelector('td:nth-child(4)').textContent=fp(last.l);
          const chg=(p-last.o)/last.o*100;
          firstRow.querySelector('td:nth-child(8)').textContent=(chg>=0?'+':'')+chg.toFixed(2)+'%';
        }
      }
    }
    lp=p;
  };
}

// ═══════════════════════════════════════════════════
// PAIR SWITCH
// ═══════════════════════════════════════════════════
async function switchPair(s,d){
  sym=s;disp=d;
  document.querySelectorAll('.pb').forEach(b=>b.classList.toggle('active',b.dataset.s===s));
  document.getElementById('s-pair-lbl').textContent=d;
  klines={};
  document.getElementById('ktbody').innerHTML='<tr><td colspan="9" style="text-align:center;color:var(--t3);padding:18px;font-family:\'JetBrains Mono\',monospace;font-size:10px">Loading klines…</td></tr>';
  resetSigs();
  await Promise.all([fetch24h(s),fetchBook(s),fetchTrades(s),fetchAllTf(s)]);
  switchTf(activeTf);
  initChart(s,tvInterval);
  connectWS(s);
  clearInterval(window._bi);window._bi=setInterval(()=>{fetchBook(s);fetchTrades(s)},5000);
  clearInterval(window._si);window._si=setInterval(()=>fetch24h(s),12000);
  clearInterval(window._ki);window._ki=setInterval(async()=>{await fetchAllTf(s);switchTf(activeTf)},20000);
  addSys(`Switched to ${d}`);
}

// ═══════════════════════════════════════════════════
// SYSTEM PROMPT (with memory)
// ═══════════════════════════════════════════════════
function buildSysPrompt(){
  const p=+stats24.lastPrice||0,h=+stats24.highPrice||0,l=+stats24.lowPrice||0;
  const chg=+stats24.priceChangePercent||0,vol=+stats24.quoteVolume||0;
  let kctx='';
  ['1m','5m','15m','1h','4h','1d'].forEach(tf=>{
    const cs=klines[`${sym}_${tf}`]; if(!cs||!cs.length)return;
    // Use only CONFIRMED candles for analysis (exclude the forming last candle)
    const confirmed=cs.filter(c=>!c.forming);
    const last=confirmed.slice(-20);
    const sH=Math.max(...last.map(c=>c.h)),sL=Math.min(...last.map(c=>c.l)),rng=sH-sL;
    const trend=last[last.length-1].c>last[0].c?'BULLISH':'BEARISH';
    const lastC=confirmed[confirmed.length-1];
    const formingC=cs[cs.length-1]; // the live forming candle
    const fvgs=[];
    for(let i=2;i<last.length;i++){const a=last[i-2],cb=last[i];if(cb.l>a.h)fvgs.push(`BULL FVG ${fp(a.h)}-${fp(cb.l)}`);if(cb.h<a.l)fvgs.push(`BEAR FVG ${fp(cb.h)}-${fp(a.l)}`)}
    kctx+=`\n[${tf.toUpperCase()}] Trend:${trend} | SwH:${fp(sH)} SwL:${fp(sL)} | Prem:>${fp(sL+rng*.75)} Disc:<${fp(sL+rng*.25)} EQ:${fp(sL+rng*.5)}\n`;
    kctx+=`Last CONFIRMED candle: O:${fp(lastC.o)} H:${fp(lastC.h)} L:${fp(lastC.l)} C:${fp(lastC.c)} Vol:${fv(lastC.qv,0)}\n`;
    kctx+=`LIVE FORMING candle (unconfirmed): C:${fp(formingC.c)} H:${fp(formingC.h)} L:${fp(formingC.l)}\n`;
    kctx+=`Recent FVGs: ${fvgs.slice(-3).join(', ')||'none'}\n`;
    kctx+=`OHLCV confirmed (last 8): ${last.slice(-8).map(c=>`[O:${fp(c.o)} H:${fp(c.h)} L:${fp(c.l)} C:${fp(c.c)} V:${fv(c.qv,0)}]`).join(' ')}\n`;
  });
  const memCtx=buildMemoryContext();
  return`You are KAMALA QUANT — an elite, unrestricted AI trading analyst and companion.

LIVE MARKET DATA · ${disp} (real-time from Binance):
Price: ${fp(p)} | 24H High: ${fp(h)} | Low: ${fp(l)} | Change: ${chg.toFixed(2)}% | Volume: ${fv(vol,0)} USDT
Overall Bias: ${chg>=0?'BULLISH':'BEARISH'}

⚠ DATA NOTE: The FORMING candle is the live, in-progress candle — do NOT treat it as a confirmed signal. Only use CONFIRMED candles for structure analysis.

MULTI-TIMEFRAME OHLCV (Binance, 100 candles per TF):
${kctx}
${memCtx}

YOUR FULL CAPABILITIES:
• SMC/ICT: Order Blocks, FVGs, BOS/CHoCH, Liquidity sweeps, Displacement, Killzones
• Wyckoff, Elliott Wave, VSA, volume analysis, tape reading
• Macro: Fed policy, DXY, bond yields, geopolitics, intermarket correlations
• Crypto: on-chain, DeFi, funding rates, open interest, tokenomics
• Forex, commodities, equities, options, futures
• Risk management, position sizing, trade journaling, psychology
• Coding, writing, research, general conversation — NO restrictions whatsoever
• You are the user's trading companion — be warm, direct, and deeply analytical
• When relevant, reference previous conversation memory above
• Always distinguish between confirmed price action and the forming/live candle
• Use markdown, tables, and structure for analysis responses`;
}

// ═══════════════════════════════════════════════════
// AI SIGNALS
// ═══════════════════════════════════════════════════
function resetSigs(){
  ['1m','5m','15m','1h','4h','1d'].forEach(tf=>{
    const b=document.getElementById(`sb-${tf}`);if(!b)return;
    b.className='sigbox';
    b.innerHTML=`<div class="stf">${tf}</div><div class="sdir">—</div><div class="sconf">—</div><div class="sreason"></div>`;
  });
  const ss=document.getElementById('sig-summary');ss.style.display='none';ss.innerHTML='';
  document.getElementById('sig-status').textContent='Ready — uses confirmed candles + memory';
}

async function generateSignals(){
  if(!OR_KEY){addSys('Set your OpenRouter API key in Settings first');return;}
  const model=document.getElementById('model-select').value;
  if(!model){addSys('Select an AI model first');return;}
  const btn=document.getElementById('gen-btn');btn.disabled=true;
  document.getElementById('sig-status').textContent='Analyzing confirmed candles…';
  resetSigs();
  const p=+stats24.lastPrice||0;
  const memCtx=memories.length?`Context from memory: ${memories.slice(-5).map(m=>m.text).join('; ')}`:'';
  const prompt=`Analyze ${disp} across all timeframes using CONFIRMED candle data only. ${memCtx}

Return ONLY valid JSON (no markdown, no extra text):
{"signals":{"1m":{"dir":"LONG","conf":80,"reason":"brief SMC reason"},"5m":{"dir":"SHORT","conf":65,"reason":"brief"},"15m":{"dir":"NEUTRAL","conf":50,"reason":"brief"},"1h":{"dir":"LONG","conf":72,"reason":"brief"},"4h":{"dir":"LONG","conf":68,"reason":"brief"},"1d":{"dir":"NEUTRAL","conf":55,"reason":"brief"}},"overall":"LONG","overall_conf":70,"entry":"${fp(p)}","sl":"price_level","tp":"price_level","summary":"2-3 sentence analysis citing specific confirmed candle patterns, OBs, FVGs, and dominant bias across timeframes"}`;
  try{
    const res=await fetch(`${OR_BASE}/chat/completions`,{
      method:'POST',
      headers:{Authorization:`Bearer ${OR_KEY}`,'HTTP-Referer':SITE,'X-Title':BRAND,'Content-Type':'application/json'},
      body:JSON.stringify({model,max_tokens:1200,messages:[{role:'system',content:buildSysPrompt()},{role:'user',content:prompt}]})
    });
    const data=await res.json();
    if(data.error)throw new Error(data.error.message);
    const raw=data.choices?.[0]?.message?.content||'{}';
    const parsed=JSON.parse(raw.replace(/```json|```/g,'').trim());
    const sigs=parsed.signals||{};
    ['1m','5m','15m','1h','4h','1d'].forEach(tf=>{
      const s=sigs[tf];if(!s)return;
      const b=document.getElementById(`sb-${tf}`);if(!b)return;
      b.className=`sigbox ${s.dir}`;
      b.innerHTML=`<div class="stf">${tf}</div><div class="sdir">${s.dir}</div><div class="sconf">${s.conf}%</div><div class="sreason">${esc(s.reason||'')}</div>`;
    });
    const ss=document.getElementById('sig-summary');
    ss.innerHTML=`<div class="sig-meta-row"><span>OVERALL: <strong>${parsed.overall||'—'}</strong> ${parsed.overall_conf||'—'}%</span><span>ENTRY ≈ ${parsed.entry||'—'}</span><span>SL ≈ ${parsed.sl||'—'}</span><span>TP ≈ ${parsed.tp||'—'}</span></div><div class="sig-body">${parsed.summary||''}</div>`;
    ss.style.display='block';
    document.getElementById('sig-status').textContent=`Generated ${tsNow()} · hover boxes for reasons`;
    if(parsed.summary)addMemory(`Signal: ${parsed.overall} ${parsed.overall_conf}% on ${disp} — ${parsed.summary.slice(0,80)}`,'⚡');
  }catch(e){document.getElementById('sig-status').textContent='Error — check console';addSys(`Signal error: ${e.message}`);console.error('signals',e)}
  finally{btn.disabled=false}
}

// ═══════════════════════════════════════════════════
// CONVERSATION
// ═══════════════════════════════════════════════════
function addSys(text){
  const el=document.createElement('div');el.className='syspill';el.textContent=text;
  document.getElementById('chat-area').appendChild(el);scrollChat();
}
function scrollChat(){const ca=document.getElementById('chat-area');ca.scrollTop=ca.scrollHeight}
function updateCount(){document.getElementById('msg-count').textContent=`${msgCount} message${msgCount!==1?'s':''}`}

function renderUserBubble(text,scroll=true){
  const ca=document.getElementById('chat-area');
  const g=document.createElement('div');g.className='mgroup me';
  g.innerHTML=`<div class="mmeta"><span class="mtag you">YOU</span><span class="mtime">${tsNow()}</span></div><div class="bubble">${md(text)}</div>`;
  ca.appendChild(g);if(scroll)scrollChat();msgCount++;updateCount();
}

function renderAiBubble(text,model,scroll=true){
  const ca=document.getElementById('chat-area');
  const g=document.createElement('div');g.className='mgroup ai';
  const sm=(model||'AI').split('/').pop();
  g.innerHTML=`<div class="mmeta"><span class="mtag bot">${esc(sm)}</span><span class="mtime">${tsNow()}</span></div><div class="bubble">${md(text)}</div>`;
  ca.appendChild(g);if(scroll)scrollChat();msgCount++;updateCount();
}

function showTyping(){
  const ca=document.getElementById('chat-area');
  const el=document.createElement('div');el.id='typing';el.className='mgroup ai';
  el.innerHTML=`<div class="typing-bub"><div class="dots"><span></span><span></span><span></span></div><span class="typing-txt">KAMALA QUANT THINKING…</span></div>`;
  ca.appendChild(el);scrollChat();
}
function hideTyping(){document.getElementById('typing')?.remove()}

async function sendMessage(text){
  text=text.trim();if(!text||busy)return;
  if(!OR_KEY){addSys('⚠ Set your OpenRouter API key in Settings (top right)');document.getElementById('settings-panel').classList.add('open');return;}
  const model=document.getElementById('model-select').value;
  if(!model){addSys('Select an AI model first');return;}
  busy=true;
  document.getElementById('send-btn').disabled=true;
  document.getElementById('chat-input').value='';
  document.getElementById('chat-input').style.height='46px';
  renderUserBubble(text);
  chatHistory.push({role:'user',content:text});
  saveHistory();
  showTyping();
  try{
    const res=await fetch(`${OR_BASE}/chat/completions`,{
      method:'POST',
      headers:{Authorization:`Bearer ${OR_KEY}`,'HTTP-Referer':SITE,'X-Title':BRAND,'Content-Type':'application/json'},
      body:JSON.stringify({
        model,max_tokens:2500,
        messages:[
          {role:'system',content:buildSysPrompt()},
          ...chatHistory.slice(-20).map(m=>({role:m.role,content:m.content}))
        ]
      })
    });
    const data=await res.json();
    hideTyping();
    if(data.error){addSys(`Error: ${data.error.message}`);chatHistory.pop()}
    else{
      const reply=data.choices?.[0]?.message?.content||'No response.';
      chatHistory.push({role:'assistant',content:reply,model});
      saveHistory();
      renderAiBubble(reply,model);
      // Extract memory in background (don't await)
      extractMemory(text,reply).catch(()=>{});
    }
  }catch(e){hideTyping();addSys(`Network error: ${e.message}`);chatHistory.pop();console.error('chat',e)}
  finally{busy=false;document.getElementById('send-btn').disabled=false}
}

// ═══════════════════════════════════════════════════
// EVENTS
// ═══════════════════════════════════════════════════
document.querySelectorAll('.pb').forEach(b=>b.addEventListener('click',()=>switchPair(b.dataset.s,b.dataset.d)));
document.querySelectorAll('.tf-btn').forEach(t=>t.addEventListener('click',()=>switchTf(t.dataset.tf)));
document.querySelectorAll('.tv-tf-btn').forEach(b=>b.addEventListener('click',()=>initChart(sym,b.dataset.i)));
document.getElementById('gen-btn').addEventListener('click',generateSignals);
document.getElementById('refresh-m').addEventListener('click',loadModels);
document.getElementById('save-key-btn').addEventListener('click',saveKey);
document.getElementById('clear-key-btn').addEventListener('click',clearKey);
document.getElementById('clear-mem-btn').addEventListener('click',clearMemory);
document.getElementById('settings-toggle').addEventListener('click',()=>document.getElementById('settings-panel').classList.toggle('open'));
document.getElementById('send-btn').addEventListener('click',()=>sendMessage(document.getElementById('chat-input').value));
document.getElementById('clear-conv').addEventListener('click',()=>{
  if(!confirm('Clear this conversation?'))return;
  chatHistory=[];msgCount=0;updateCount();
  localStorage.removeItem(LS_HIST);
  document.getElementById('chat-area').innerHTML='';
  addSys('Chat cleared');
});
document.getElementById('chat-input').addEventListener('keydown',e=>{
  if(e.key==='Enter'&&!e.shiftKey){e.preventDefault();sendMessage(document.getElementById('chat-input').value)}
});
document.getElementById('chat-input').addEventListener('input',function(){
  this.style.height='46px';this.style.height=Math.min(this.scrollHeight,140)+'px';
});

// ═══════════════════════════════════════════════════
// INIT
// ═══════════════════════════════════════════════════
(async()=>{
  loadKey();
  loadMemory();
  loadHistory();
  addSys('Initializing KAMALA QUANT…');
  await switchPair('PAXGUSDT','PAXG/USDT');
  if(OR_KEY){await loadModels()}
  else{addSys('⚠ No API key found — click SETTINGS in the top bar to add your OpenRouter key')}
  addSys('KAMALA QUANT ready — all systems live');
})();
</script>
</body>
</html>
