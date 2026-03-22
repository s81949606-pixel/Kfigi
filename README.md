<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>Супраграм</title>
<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,sans-serif;-webkit-tap-highlight-color:transparent}
:root{--bg:#0e1621;--sb:#17212b;--chat:#0e1621;--out:#2b5278;--in:#182533;--tx:#e1e3e6;--tx2:#6c7883;--ac:#5288c1;--hv:#202b36;--bd:#0f1924;--gn:#5dc452;--rd:#e5533a;--inp:#242f3d;--sc:#2b3845;--mdbg:rgba(0,0,0,.55)}
html.light{--bg:#ffffff;--sb:#ffffff;--chat:#e8ecf0;--out:#effdde;--in:#ffffff;--tx:#222222;--tx2:#707579;--ac:#3390ec;--hv:#f0f0f0;--bd:#e0e0e0;--gn:#5dc452;--rd:#e5533a;--inp:#f0f2f5;--sc:#c4c9cc;--mdbg:rgba(0,0,0,.35)}
html.light .m-o{color:#000}
html.light .m-i{color:#000;border:1px solid var(--bd)}
html.light .m-ft{color:rgba(0,0,0,.35)!important}
html.light .m-sys span{background:#d6e6f2}
html.light .msg-date span{background:#d6e6f2;color:#555}
html.light .pop,.light .rbar{background:#fff;box-shadow:0 2px 16px rgba(0,0,0,.15)}
html.light .pop-i:hover,.light .dri:hover,.light .ci:hover{background:#f0f0f0}
html.light .ci.act{background:var(--ac)}
html.light .ci.act *{color:#fff!important}
html.light .md{background:#fff;color:#222}
html.light .toast{background:#fff;color:#222;box-shadow:0 2px 16px rgba(0,0,0,.12)}
html.light .dr{background:#fff}
html.light .dr-head{background:linear-gradient(135deg,#3390ec,#5bb8ff)}
html.light .dr-head *{color:#fff}
html.light .cpost{background:#fff;border:1px solid var(--bd)}
html.light .auth{background:#e8ecf0}
html.light .auth-c{background:#fff;box-shadow:0 2px 20px rgba(0,0,0,.08)}
html.light input,html.light textarea{color:#222!important}
html.light .rx{background:rgba(0,0,0,.04);color:#222}
html.light .rx:hover{background:rgba(0,0,0,.08)}
html.light .rx.my{background:rgba(51,144,236,.12)}
html.light ::selection{background:var(--ac);color:#fff}
html,body{height:100%;overflow:hidden;overscroll-behavior:none}
body{background:var(--bg);color:var(--tx);transition:background .3s,color .3s}
.hid{display:none!important}
::selection{background:var(--ac);color:#fff}
input,textarea,button{font-family:inherit;outline:none}
::-webkit-scrollbar{width:6px}
::-webkit-scrollbar-track{background:transparent}
::-webkit-scrollbar-thumb{background:var(--sc);border-radius:3px}
.fade-t{transition:opacity .25s ease,transform .25s ease}
.auth{display:flex;align-items:center;justify-content:center;height:100vh;background:var(--bg);transition:background .3s}
.auth-c{background:var(--sb);border-radius:14px;padding:40px 32px;width:380px;max-width:94vw;box-shadow:0 4px 60px rgba(0,0,0,.4);animation:slideUp .5s cubic-bezier(.4,0,.2,1);transition:background .3s}
@keyframes slideUp{from{opacity:0;transform:translateY(30px)}to{opacity:1;transform:none}}
.auth-logo{width:90px;height:90px;margin:0 auto 16px;border-radius:50%;background:linear-gradient(135deg,#5288c1,#6eb0f7);display:flex;align-items:center;justify-content:center;box-shadow:0 4px 20px rgba(82,136,193,.4);transition:transform .3s}
.auth-logo:hover{transform:scale(1.05) rotate(5deg)}
.auth-logo svg{width:46px;height:46px;fill:#fff}
.auth-c h1{text-align:center;font-size:24px;font-weight:700;margin-bottom:4px}
.auth-c .sub{text-align:center;font-size:13px;color:var(--tx2);margin-bottom:20px}
.auth-c .err{color:var(--rd);font-size:13px;text-align:center;min-height:18px;margin-bottom:6px;transition:.3s}
.fi{position:relative;margin-bottom:14px}
.fi input{width:100%;padding:14px 16px 6px;background:var(--inp);border:2px solid transparent;border-radius:10px;color:var(--tx);font-size:15px;transition:border .25s,background .25s}
.fi input:focus{border-color:var(--ac)}
.fi label{position:absolute;left:16px;top:50%;transform:translateY(-50%);font-size:14px;color:var(--tx2);pointer-events:none;transition:.25s}
.fi input:focus~label,.fi input:not(:placeholder-shown)~label{top:8px;font-size:10px;transform:none;color:var(--ac)}
.abtn{width:100%;padding:14px;background:var(--ac);color:#fff;border:none;border-radius:10px;font-size:15px;font-weight:600;cursor:pointer;transition:all .2s;margin-top:6px}
.abtn:hover{filter:brightness(1.1)}
.abtn:active{transform:scale(.97);filter:brightness(.95)}
.alink{text-align:center;margin-top:16px;color:var(--tx2);font-size:13px}
.alink span{color:var(--ac);cursor:pointer;transition:color .15s}
.alink span:hover{text-decoration:underline}
.iface-tog{display:flex;justify-content:center;gap:8px;margin-top:16px}
.iface-btn{padding:8px 18px;border-radius:20px;border:2px solid var(--ac);background:none;color:var(--ac);font-size:13px;cursor:pointer;transition:all .25s;font-weight:600}
.iface-btn.sel{background:var(--ac);color:#fff}
.iface-btn:hover{filter:brightness(1.1)}
.app{display:flex;height:100vh;width:100%;position:relative;transition:all .3s}
.app.phone .sb{width:100%;min-width:100%}
.app.phone .cha{position:fixed;inset:0;z-index:10;transform:translateX(100%);transition:transform .3s cubic-bezier(.4,0,.2,1)}
.app.phone .cha.open{transform:translateX(0)}
.app.phone .ch{padding-left:6px}
.app.phone .ch-back{display:flex!important}
.sb{width:320px;min-width:320px;background:var(--sb);display:flex;flex-direction:column;border-right:1px solid var(--bd);z-index:2;transition:background .3s,border .3s}
.sb-top{padding:8px 10px;display:flex;align-items:center;gap:8px}
.ham{width:40px;height:40px;display:flex;align-items:center;justify-content:center;cursor:pointer;border-radius:50%;transition:all .2s;flex-shrink:0}
.ham:hover{background:var(--hv)}
.ham:active{transform:scale(.9)}
.ham svg{fill:var(--tx2);width:22px;height:22px}
.sb-s{flex:1;position:relative}
.sb-s input{width:100%;padding:9px 12px 9px 36px;background:var(--inp);border:none;border-radius:22px;color:var(--tx);font-size:14px;transition:all .2s}
.sb-s input:focus{background:var(--sc)}
.sb-s input::placeholder{color:#4e5d6b}
.sb-s svg{position:absolute;left:11px;top:50%;transform:translateY(-50%);fill:#4e5d6b;width:16px;height:16px}
.sb-l{flex:1;overflow-y:auto}
.ci{display:flex;align-items:center;padding:8px 10px;cursor:pointer;transition:all .15s;gap:10px}
.ci:hover{background:var(--hv)}
.ci:active{transform:scale(.99);opacity:.85}
.ci.act{background:var(--ac)}
.ci.act .ci-last,.ci.act .ci-time{color:rgba(255,255,255,.7)}
.ci-av{width:50px;height:50px;border-radius:50%;flex-shrink:0;display:flex;align-items:center;justify-content:center;font-size:20px;font-weight:600;color:#fff;position:relative}
.ci-dot{position:absolute;bottom:2px;right:2px;width:12px;height:12px;background:var(--gn);border-radius:50%;border:2px solid var(--sb)}
.ci-nfo{flex:1;min-width:0}
.ci-nm{font-size:15px;font-weight:500;white-space:nowrap;overflow:hidden;text-overflow:ellipsis;display:flex;align-items:center;gap:4px}
.ci-last{font-size:13px;color:var(--tx2);white-space:nowrap;overflow:hidden;text-overflow:ellipsis;margin-top:2px}
.ci-meta{display:flex;flex-direction:column;align-items:flex-end;gap:5px;flex-shrink:0}
.ci-time{font-size:12px;color:var(--tx2)}
.ci-badge{background:var(--ac);color:#fff;font-size:11px;min-width:20px;height:20px;line-height:20px;text-align:center;padding:0 6px;border-radius:10px;font-weight:700}
.dr-ov{position:fixed;inset:0;background:rgba(0,0,0,.45);z-index:50;opacity:0;pointer-events:none;transition:opacity .3s}
.dr-ov.open{opacity:1;pointer-events:auto}
.dr{position:fixed;top:0;left:0;width:280px;height:100%;background:var(--sb);z-index:51;transform:translateX(-100%);transition:transform .3s cubic-bezier(.4,0,.2,1),background .3s;display:flex;flex-direction:column}
.dr.open{transform:translateX(0)}
.dr-head{padding:18px 16px;background:linear-gradient(135deg,#1a2636,#1e3048)}
.dr-av{margin-bottom:8px}
.dr-nm{font-size:15px;font-weight:600}
.dr-u{font-size:12px;color:var(--tx2);margin-top:2px}
.dr-items{flex:1;padding:6px 0;overflow-y:auto}
.dri{display:flex;align-items:center;gap:16px;padding:12px 18px;cursor:pointer;transition:all .15s;font-size:15px}
.dri:hover{background:var(--hv)}
.dri:active{opacity:.7}
.dri svg{fill:var(--tx2);width:20px;height:20px;flex-shrink:0}
.dri.red{color:var(--rd)}.dri.red svg{fill:var(--rd)}
.dr-foot{padding:14px 18px;border-top:1px solid var(--bd);font-size:11px;color:#3d4d5c}
.cha{flex:1;display:flex;flex-direction:column;min-width:0;background:var(--chat);transition:background .3s}
.cha-e{flex:1;display:flex;align-items:center;justify-content:center;flex-direction:column;gap:10px;color:var(--tx2);user-select:none}
.cha-e svg{width:120px;height:120px;fill:var(--sc);opacity:.5}
.ch{padding:8px 14px;background:var(--sb);border-bottom:1px solid var(--bd);display:flex;align-items:center;gap:10px;min-height:56px;z-index:3;transition:background .3s}
.ch-back{width:36px;height:36px;display:none;align-items:center;justify-content:center;border-radius:50%;cursor:pointer;transition:.15s;flex-shrink:0;border:none;background:none}
.ch-back:hover{background:var(--hv)}
.ch-back svg{fill:var(--tx2);width:22px;height:22px}
.ch-nfo{flex:1;min-width:0;cursor:pointer}
.ch-nm{font-size:15px;font-weight:600;display:flex;align-items:center;gap:4px}
.ch-st{font-size:12px;color:var(--tx2);margin-top:1px}
.ch-btn{width:38px;height:38px;display:flex;align-items:center;justify-content:center;border-radius:50%;cursor:pointer;transition:all .15s;border:none;background:none;flex-shrink:0}
.ch-btn:hover{background:var(--hv)}
.ch-btn:active{transform:scale(.9)}
.ch-btn svg{fill:var(--tx2);width:20px;height:20px}
.msgs{flex:1;overflow-y:auto;padding:8px 14px;display:flex;flex-direction:column;gap:2px;background:var(--chat);transition:background .3s}
.msg-date{text-align:center;padding:6px 0}
.msg-date span{background:#1a2636;padding:4px 12px;border-radius:10px;font-size:12px;color:var(--tx2)}
.m{max-width:65%;padding:7px 11px 20px;border-radius:12px;position:relative;word-wrap:break-word;font-size:14px;line-height:1.45;animation:mIn .25s ease}
@keyframes mIn{from{opacity:0;transform:translateY(8px)}to{opacity:1;transform:none}}
.m-o{background:var(--out);align-self:flex-end;border-bottom-right-radius:4px}
.m-i{background:var(--in);align-self:flex-start;border-bottom-left-radius:4px}
.m-tx{white-space:pre-wrap}
.m-ft{position:absolute;bottom:4px;right:8px;display:flex;align-items:center;gap:3px;font-size:11px;color:rgba(255,255,255,.4)}
.m-ck{font-size:13px}
.m-rx{display:flex;gap:3px;margin-top:4px;flex-wrap:wrap}
.rx{padding:2px 8px;background:rgba(255,255,255,.06);border-radius:12px;font-size:13px;cursor:pointer;transition:all .15s;border:1px solid transparent;user-select:none;line-height:1.6}
.rx:hover{background:rgba(255,255,255,.12);transform:scale(1.05)}
.rx.my{border-color:var(--ac);background:rgba(82,136,193,.18)}
.m-gift{text-align:center;padding:16px 20px 26px;min-width:220px}
.m-gift-i{font-size:64px;line-height:1;margin-bottom:8px}
.m-gift-t{font-size:14px;font-weight:600;color:var(--ac)}
.m-gift-x{font-size:13px;color:var(--tx2);margin-top:4px}
.m-sys{text-align:center;padding:6px 0;font-size:12px;color:var(--tx2);align-self:center;animation:mIn .25s ease}
.m-sys span{background:#1a2636;padding:3px 10px;border-radius:10px}
.pop{position:fixed;background:#1e2c3a;border-radius:10px;padding:5px 0;z-index:100;box-shadow:0 4px 24px rgba(0,0,0,.5);min-width:180px;animation:popIn .15s cubic-bezier(.4,0,.2,1)}
@keyframes popIn{from{opacity:0;transform:scale(.92) translateY(-4px)}to{opacity:1;transform:none}}
.pop-i{padding:10px 16px;cursor:pointer;font-size:14px;display:flex;align-items:center;gap:10px;transition:background .12s}
.pop-i:hover{background:var(--hv)}
.pop-i.red{color:var(--rd)}
.rbar{position:fixed;background:#1e2c3a;border-radius:20px;padding:4px 8px;display:flex;gap:2px;z-index:100;box-shadow:0 4px 20px rgba(0,0,0,.5);animation:popIn .15s cubic-bezier(.4,0,.2,1)}
.rbtn{font-size:22px;cursor:pointer;padding:4px;border-radius:8px;transition:all .15s;line-height:1}
.rbtn:hover{background:var(--hv);transform:scale(1.25)}
.inp{padding:8px 10px;background:var(--sb);border-top:1px solid var(--bd);display:flex;align-items:center;gap:8px;transition:background .3s}
.inp input{flex:1;padding:10px 14px;background:var(--inp);border:none;border-radius:22px;color:var(--tx);font-size:14px;transition:all .2s}
.inp input::placeholder{color:#4e5d6b}
.inp input:focus{background:var(--sc)}
.snd{width:40px;height:40px;border-radius:50%;background:var(--ac);border:none;cursor:pointer;display:flex;align-items:center;justify-content:center;transition:all .2s;flex-shrink:0}
.snd:hover{filter:brightness(1.1)}
.snd:active{transform:scale(.85)}
.snd svg{fill:#fff;width:18px;height:18px}
.mo{position:fixed;inset:0;background:var(--mdbg);z-index:60;display:flex;align-items:center;justify-content:center;animation:fi .2s ease}
@keyframes fi{from{opacity:0}to{opacity:1}}
.md{background:var(--sb);border-radius:14px;padding:24px;width:420px;max-width:94vw;max-height:85vh;overflow-y:auto;box-shadow:0 10px 50px rgba(0,0,0,.4);animation:mdIn .25s cubic-bezier(.4,0,.2,1);transition:background .3s}
@keyframes mdIn{from{opacity:0;transform:scale(.95) translateY(8px)}to{opacity:1;transform:none}}
.md h2{font-size:18px;font-weight:600;margin-bottom:14px;display:flex;align-items:center;gap:8px}
.md h2 .x{margin-left:auto;cursor:pointer;width:30px;height:30px;display:flex;align-items:center;justify-content:center;border-radius:50%;color:var(--tx2);font-size:18px;transition:all .15s}
.md h2 .x:hover{background:var(--hv);transform:rotate(90deg)}
.md label{display:block;font-size:12px;color:var(--tx2);margin:12px 0 4px;text-transform:uppercase;letter-spacing:.5px}
.md input,.md textarea{width:100%;padding:10px 14px;background:var(--inp);border:2px solid transparent;border-radius:8px;color:var(--tx);font-size:14px;transition:border .2s,background .2s}
.md input:focus,.md textarea:focus{border-color:var(--ac)}
.md textarea{resize:vertical;min-height:50px;font-family:inherit}
.btn{padding:11px 20px;background:var(--ac);color:#fff;border:none;border-radius:8px;font-size:14px;font-weight:600;cursor:pointer;transition:all .2s}
.btn:hover{filter:brightness(1.1)}
.btn:active{transform:scale(.97)}
.btn.red{background:var(--rd)}.btn.red:hover{filter:brightness(1.1)}
.btn.outline{background:none;border:2px solid var(--ac);color:var(--ac)}
.btn.outline:hover{background:rgba(82,136,193,.1)}
.av-ops{display:flex;gap:8px;margin-top:6px;flex-wrap:wrap}
.av-o{width:52px;height:52px;border-radius:50%;cursor:pointer;border:3px solid transparent;transition:all .2s;display:flex;align-items:center;justify-content:center;font-size:22px;font-weight:700;color:#fff;overflow:hidden;flex-shrink:0}
.av-o:hover,.av-o.sel{border-color:var(--ac);transform:scale(1.1)}
.av-o img{width:100%;height:100%;object-fit:cover}
.gc{display:flex;justify-content:center;gap:10px;margin:14px 0}
.gci{display:flex;flex-direction:column;align-items:center;padding:14px 10px;background:var(--inp);border-radius:12px;cursor:pointer;transition:all .2s;width:100px;border:2px solid transparent}
.gci:hover,.gci.sel{border-color:var(--ac);background:rgba(82,136,193,.1);transform:scale(1.05)}
.gci-i{font-size:44px;margin-bottom:4px;line-height:1}
.gci-n{font-size:12px;color:var(--tx2)}
.pg{display:inline-flex;flex-direction:column;align-items:center;padding:8px;background:var(--inp);border-radius:10px;cursor:pointer;margin:3px;position:relative;width:72px;transition:all .15s}
.pg:hover{background:var(--sc);transform:scale(1.05)}
.pg-i{font-size:32px;line-height:1}
.pg.dim{opacity:.35}
.pg-bd{position:absolute;top:3px;right:3px;font-size:9px;background:rgba(0,0,0,.55);padding:2px 5px;border-radius:4px}
.aci{display:flex;align-items:center;padding:10px;gap:10px;cursor:pointer;border-radius:8px;transition:all .15s;margin-bottom:4px}
.aci:hover{background:var(--hv);transform:translateX(2px)}
.aci.cur{background:rgba(82,136,193,.12);border:1px solid var(--ac)}
.cpost{background:var(--in);border-radius:12px;padding:12px;margin-bottom:6px;animation:mIn .25s ease;transition:background .3s}
.cpost-t{font-size:14px;line-height:1.5;margin-bottom:6px;white-space:pre-wrap}
.cpost-m{display:flex;align-items:center;gap:10px;font-size:12px;color:var(--tx2)}
.cpost-rx{display:flex;gap:3px;margin-top:6px;flex-wrap:wrap}
.sr{display:flex;align-items:center;padding:9px 12px;cursor:pointer;gap:10px;transition:all .15s}
.sr:hover{background:var(--hv)}
.sr:active{opacity:.7}
.sec{padding:8px 12px;color:#4e5d6b;font-size:11px;text-transform:uppercase;letter-spacing:.6px;display:flex;justify-content:space-between;align-items:center}
.sec span{color:var(--ac);text-transform:none;cursor:pointer;font-size:12px;letter-spacing:0}
.sec span:hover{text-decoration:underline}
.cfw{position:fixed;inset:0;pointer-events:none;z-index:200;overflow:hidden}
.cf{position:absolute;opacity:.9;will-change:transform}
.toast{position:fixed;bottom:30px;left:50%;transform:translateX(-50%) translateY(20px);background:#1e2c3a;color:var(--tx);padding:10px 22px;border-radius:10px;font-size:14px;z-index:300;box-shadow:0 4px 20px rgba(0,0,0,.4);animation:toastIn .35s cubic-bezier(.4,0,.2,1) forwards;pointer-events:none}
@keyframes toastIn{from{opacity:0;transform:translateX(-50%) translateY(30px)}to{opacity:1;transform:translateX(-50%) translateY(0)}}
.vf{color:var(--ac)!important}
.adm-u{display:flex;align-items:center;gap:10px;padding:8px 10px;border-radius:8px;transition:all .15s;margin-bottom:4px}
.adm-u:hover{background:var(--hv)}
.adm-u .vfb{cursor:pointer;padding:4px 10px;border-radius:6px;font-size:12px;border:1px solid var(--ac);color:var(--ac);background:none;transition:all .2s}
.adm-u .vfb:hover{background:var(--ac);color:#fff}
.theme-tog{display:flex;gap:8px;margin-top:6px}
.theme-btn{flex:1;padding:10px;border-radius:8px;border:2px solid transparent;background:var(--inp);cursor:pointer;text-align:center;font-size:13px;font-weight:600;color:var(--tx);transition:all .2s}
.theme-btn:hover{border-color:var(--ac);opacity:.85}
.theme-btn.sel{border-color:var(--ac);background:rgba(82,136,193,.15)}
.if-tog{display:flex;gap:8px;margin-top:6px}
.if-btn{flex:1;padding:10px;border-radius:8px;border:2px solid transparent;background:var(--inp);cursor:pointer;text-align:center;font-size:13px;font-weight:600;color:var(--tx);transition:all .2s}
.if-btn:hover{border-color:var(--ac);opacity:.85}
.if-btn.sel{border-color:var(--ac);background:rgba(82,136,193,.15)}
.typing{font-size:12px;color:var(--ac);font-style:italic;animation:blink 1.2s infinite}
@keyframes blink{0%,100%{opacity:.4}50%{opacity:1}}
/* Privacy toggle */
.prv-row{display:flex;align-items:center;justify-content:space-between;padding:10px 0;border-bottom:1px solid var(--bd)}
.prv-row:last-child{border:none}
.prv-label{font-size:14px;flex:1}
.prv-sub{font-size:11px;color:var(--tx2);margin-top:2px}
.prv-tog{width:44px;height:24px;border-radius:12px;background:var(--sc);cursor:pointer;position:relative;transition:background .25s;flex-shrink:0}
.prv-tog.on{background:var(--ac)}
.prv-tog::after{content:'';position:absolute;top:2px;left:2px;width:20px;height:20px;border-radius:50%;background:#fff;transition:transform .25s;box-shadow:0 1px 3px rgba(0,0,0,.3)}
.prv-tog.on::after{transform:translateX(20px)}
.exc-list{margin-top:6px;padding:4px 0}
.exc-item{display:flex;align-items:center;gap:8px;padding:4px 8px;background:var(--inp);border-radius:6px;margin:3px 0;font-size:13px}
.exc-rm{cursor:pointer;color:var(--rd);font-size:16px;margin-left:auto;transition:transform .15s}
.exc-rm:hover{transform:scale(1.3)}
.blocked-msg{text-align:center;padding:16px;color:var(--tx2);font-size:13px;background:var(--inp);border-radius:10px;margin:8px 14px}
</style>
</head>
<body>

<div id="authScreen" class="auth">
<div class="auth-c">
<div class="auth-logo"><svg viewBox="0 0 24 24"><path d="M20 2H4c-1.1 0-2 .9-2 2v18l4-4h14c1.1 0 2-.9 2-2V4c0-1.1-.9-2-2-2zm0 14H5.17L4 17.17V4h16v12z"/></svg></div>
<h1>Супраграм</h1>
<p class="sub" id="authSub">Создайте аккаунт</p>
<div class="err" id="authErr"></div>
<div id="regB">
<div class="fi"><input type="text" id="rNm" placeholder=" "><label>Имя</label></div>
<div class="fi"><input type="text" id="rUn" placeholder=" "><label>Username (англ, от 3 букв)</label></div>
<div class="fi"><input type="password" id="rPw" placeholder=" "><label>Пароль (от 4 символов)</label></div>
</div>
<div id="logB" class="hid">
<div class="fi"><input type="text" id="lUn" placeholder=" "><label>Username</label></div>
<div class="fi"><input type="password" id="lPw" placeholder=" "><label>Пароль</label></div>
</div>
<button class="abtn" id="authBtn">Создать аккаунт</button>
<div class="alink" id="authLnk">Уже есть аккаунт? <span id="authTog">Войти</span></div>
<div class="iface-tog">
<button class="iface-btn sel" id="ifPC" onclick="setIface('pc')">Компьютер</button>
<button class="iface-btn" id="ifPH" onclick="setIface('phone')">Телефон</button>
</div>
</div>
</div>

<div id="app" class="app hid">
<div class="dr-ov" id="drOv"></div>
<div class="dr" id="drawer">
<div class="dr-head">
<div class="dr-av" id="drAv"></div>
<div class="dr-nm" id="drNm"></div>
<div class="dr-u" id="drU"></div>
</div>
<div class="dr-items" id="drItems"></div>
<div class="dr-foot">Супраграм v5.0</div>
</div>
<div class="sb" id="sidebar">
<div class="sb-top">
<div class="ham" id="hamBtn"><svg viewBox="0 0 24 24"><path d="M3 18h18v-2H3v2zm0-5h18v-2H3v2zm0-7v2h18V6H3z"/></svg></div>
<div class="sb-s"><svg viewBox="0 0 24 24"><path d="M15.5 14h-.79l-.28-.27A6.47 6.47 0 0016 9.5 6.5 6.5 0 109.5 16c1.61 0 3.09-.59 4.23-1.57l.27.28v.79l5 4.99L20.49 19l-4.99-5zm-6 0C7.01 14 5 11.99 5 9.5S7.01 5 9.5 5 14 7.01 14 9.5 11.99 14 9.5 14z"/></svg><input type="text" id="sIn" placeholder="Поиск..."></div>
</div>
<div class="sb-l" id="sbL"></div>
</div>
<div class="cha" id="chaArea">
<div class="cha-e" id="chaE"><svg viewBox="0 0 24 24"><path d="M20 2H4c-1.1 0-2 .9-2 2v18l4-4h14c1.1 0 2-.9 2-2V4c0-1.1-.9-2-2-2zm0 14H5.17L4 17.17V4h16v12z"/></svg><div style="font-size:15px">Выберите чат</div></div>
<div id="chaV" class="hid" style="display:flex;flex-direction:column;flex:1;min-height:0">
<div class="ch" id="chaH"></div>
<div class="msgs" id="msgB"></div>
<div id="blockedBar" class="hid"></div>
<div class="inp" id="inpA"><input type="text" id="msgI" placeholder="Сообщение..."><button class="snd" id="sndB"><svg viewBox="0 0 24 24"><path d="M2.01 21L23 12 2.01 3 2 10l15 2-15 2z"/></svg></button></div>
</div>
</div>
</div>

<div id="mdlB"></div>

<script>
var AVATARS=[
  {id:1,bg:'#5288c1',type:'color'},
  {id:2,bg:'#e17076',type:'color'},
  {id:3,bg:'#7bc862',type:'color'},
  {id:4,bg:'#f5a623',type:'color'},
  {id:5,bg:'#a87bdb',type:'color'},
  {id:6,bg:'#ee7aae',type:'img',src:'data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA2NCA2NCI+PHJlY3Qgd2lkdGg9IjY0IiBoZWlnaHQ9IjY0IiByeD0iMzIiIGZpbGw9IiNmZjZiOTUiLz48Y2lyY2xlIGN4PSIyMiIgY3k9IjI4IiByPSI2IiBmaWxsPSIjZmZmIi8+PGNpcmNsZSBjeD0iNDIiIGN5PSIyOCIgcj0iNiIgZmlsbD0iI2ZmZiIvPjxjaXJjbGUgY3g9IjIyIiBjeT0iMjkiIHI9IjMiIGZpbGw9IiMyMjIiLz48Y2lyY2xlIGN4PSI0MiIgY3k9IjI5IiByPSIzIiBmaWxsPSIjMjIyIi8+PHBhdGggZD0iTTIwIDQyYzAgMCA2IDggMjQgMCIgc3Ryb2tlPSIjZmZmIiBzdHJva2Utd2lkdGg9IjIuNSIgZmlsbD0ibm9uZSIgc3Ryb2tlLWxpbmVjYXA9InJvdW5kIi8+PC9zdmc+'},
  {id:7,bg:'#64b5f6',type:'img',src:'data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA2NCA2NCI+PHJlY3Qgd2lkdGg9IjY0IiBoZWlnaHQ9IjY0IiByeD0iMzIiIGZpbGw9IiM0ZmMzZjciLz48Y2lyY2xlIGN4PSIyMCIgY3k9IjI2IiByPSI4IiBmaWxsPSIjZmZmIi8+PGNpcmNsZSBjeD0iNDQiIGN5PSIyNiIgcj0iOCIgZmlsbD0iI2ZmZiIvPjxjaXJjbGUgY3g9IjIyIiBjeT0iMjciIHI9IjQiIGZpbGw9IiMxMTEiLz48Y2lyY2xlIGN4PSI0NiIgY3k9IjI3IiByPSI0IiBmaWxsPSIjMTExIi8+PHBhdGggZD0iTTI0IDQwcTggOCAxNiAwIiBzdHJva2U9IiNmZmYiIHN0cm9rZS13aWR0aD0iMi41IiBmaWxsPSJub25lIiBzdHJva2UtbGluZWNhcD0icm91bmQiLz48L3N2Zz4='},
  {id:8,bg:'#ffb74d',type:'img',src:'data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA2NCA2NCI+PHJlY3Qgd2lkdGg9IjY0IiBoZWlnaHQ9IjY0IiByeD0iMzIiIGZpbGw9IiM3YzRkZmYiLz48Y2lyY2xlIGN4PSIyMiIgY3k9IjMwIiByPSI1IiBmaWxsPSIjZmZmIi8+PGNpcmNsZSBjeD0iNDIiIGN5PSIzMCIgcj0iNSIgZmlsbD0iI2ZmZiIvPjxjaXJjbGUgY3g9IjIyIiBjeT0iMzEiIHI9IjIuNSIgZmlsbD0iIzExMSIvPjxjaXJjbGUgY3k9IjMxIiBjeD0iNDIiIHI9IjIuNSIgZmlsbD0iIzExMSIvPjxwYXRoIGQ9Ik0xMCAxOGw4LTggOCA0IDgtNCA4IDgiIHN0cm9rZT0iI2ZmZDcwMCIgc3Ryb2tlLXdpZHRoPSIzIiBmaWxsPSIjZmZkNzAwIi8+PHBhdGggZD0iTTI2IDQ0cTYgNCAxMiAwIiBzdHJva2U9IiNmZmYiIHN0cm9rZS13aWR0aD0iMiIgZmlsbD0ibm9uZSIgc3Ryb2tlLWxpbmVjYXA9InJvdW5kIi8+PC9zdmc+'}
];
var GIFTS=[
  {id:'bear',name:'Mishka',icon:'\ud83e\uddf8',colors:['#e8956e','#f4c58a','#fff','#ffb347','#ff8c42'],effect:'warm'},
  {id:'pepe',name:'Pepe',icon:'\ud83d\udc38',colors:['#7bc862','#4cd964','#a8e6cf','#dcedc1','#fff'],effect:'green'},
  {id:'snoop',name:'Snoop Dog',icon:'\ud83d\udc15',colors:['#a87bdb','#c39bd3','#f0e6ff','#7d3cff','#fff'],effect:'purple'}
];
var RX=['\ud83d\udc4d','\ud83d\udc4e','\ud83d\udd25','\u2764\ufe0f','\ud83d\ude22','\ud83d\ude2e'];
var iface=localStorage.getItem('supra_iface')||'pc';
var theme=localStorage.getItem('supra_theme')||'dark';

function applyTheme(){
  if(theme==='light') document.documentElement.classList.add('light');
  else document.documentElement.classList.remove('light');
}
function applyIface(){
  var app=document.getElementById('app');
  if(!app)return;
  if(iface==='phone') app.classList.add('phone');
  else app.classList.remove('phone');
}
function setIface(v){
  iface=v;localStorage.setItem('supra_iface',v);
  document.getElementById('ifPC').classList.toggle('sel',v==='pc');
  document.getElementById('ifPH').classList.toggle('sel',v==='phone');
  applyIface();
}

function D(){try{return JSON.parse(localStorage.getItem('supra'))||{a:[],m:{},ch:{},sh:{},vf:{}};}catch(e){return{a:[],m:{},ch:{},sh:{},vf:{}};}}
function S(d){localStorage.setItem('supra',JSON.stringify(d));}
function me(){var d=D(),s=localStorage.getItem('supra_sid');if(!s)return null;return d.a.find(function(x){return x.u===s;})||null;}
function updMe(o){var d=D(),m=me();if(!m)return;var i=d.a.findIndex(function(x){return x.u===m.u;});if(i>=0){for(var k in o)d.a[i][k]=o[k];S(d);}}
function ck(a,b){return[a,b].sort().join('|');}
function esc(s){if(!s)return'';return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');}
function ft(t){if(!t)return'';var d=new Date(t),n=new Date(),p=function(v){return String(v).padStart(2,'0');};if(d.toDateString()===n.toDateString())return p(d.getHours())+':'+p(d.getMinutes());return p(d.getDate())+'.'+p(d.getMonth()+1)+' '+p(d.getHours())+':'+p(d.getMinutes());}
function fd(t){if(!t)return'';var d=new Date(t),today=new Date();if(d.toDateString()===today.toDateString())return'Сегодня';var y=new Date(today);y.setDate(y.getDate()-1);if(d.toDateString()===y.toDateString())return'Вчера';return d.toLocaleDateString('ru-RU',{day:'numeric',month:'long'});}

function avHTML(acc,sz){
  sz=sz||48;
  if(!acc)return'<div style="width:'+sz+'px;height:'+sz+'px;border-radius:50%;background:#3a4a5a;display:flex;align-items:center;justify-content:center;font-size:'+(sz/2.2)+'px;color:#fff;font-weight:600">?</div>';
  var av=AVATARS.find(function(x){return x.id===acc.av;})||AVATARS[0];
  var l=(acc.nm||acc.u||'?')[0].toUpperCase();
  if(av.type==='img'){
    return'<div style="width:'+sz+'px;height:'+sz+'px;border-radius:50%;overflow:hidden;flex-shrink:0"><img src="'+av.src+'" style="width:100%;height:100%;object-fit:cover" alt=""></div>';
  }
  return'<div style="width:'+sz+'px;height:'+sz+'px;border-radius:50%;background:'+av.bg+';display:flex;align-items:center;justify-content:center;font-size:'+(sz/2.2)+'px;color:#fff;font-weight:600;flex-shrink:0">'+l+'</div>';
}

function isOn(u){var d=D(),a=d.a.find(function(x){return x.u===u;});return a&&(Date.now()-a.ls<12000);}
function isVf(u){var d=D();return u==='surpa'||(d.vf&&d.vf[u]);}
function dname(target){var m2=me();if(!m2)return target;if(m2.nk&&m2.nk[target])return m2.nk[target];var d=D(),a=d.a.find(function(x){return x.u===target;});return a?a.nm:target;}

// === Privacy helpers ===
function getPrv(username){
  var d=D(),a=d.a.find(function(x){return x.u===username;});
  if(!a||!a.prv) return{noGift:false,noMsg:false,noCh:false,excGift:[],excMsg:[],excCh:[]};
  return{
    noGift:!!a.prv.noGift,
    noMsg:!!a.prv.noMsg,
    noCh:!!a.prv.noCh,
    excGift:a.prv.excGift||[],
    excMsg:a.prv.excMsg||[],
    excCh:a.prv.excCh||[]
  };
}
function canGift(fromU,toU){
  var p=getPrv(toU);
  if(!p.noGift)return true;
  return p.excGift.indexOf(fromU)>=0;
}
function canMsg(fromU,toU){
  var p=getPrv(toU);
  if(!p.noMsg)return true;
  return p.excMsg.indexOf(fromU)>=0;
}
function canAddCh(toU){
  var p=getPrv(toU);
  if(!p.noCh)return true;
  var u=me();
  return u&&p.excCh.indexOf(u.u)>=0;
}

function toast(msg){
  var t=document.createElement('div');t.className='toast';t.textContent=msg;
  document.body.appendChild(t);
  setTimeout(function(){t.style.opacity='0';t.style.transition='opacity .35s';setTimeout(function(){t.remove();},350);},2800);
}

// ===== AUTH =====
var authMode=0;
document.addEventListener('DOMContentLoaded',function(){
  applyTheme();
  applyIface();
  document.getElementById('ifPC').classList.toggle('sel',iface==='pc');
  document.getElementById('ifPH').classList.toggle('sel',iface==='phone');
  document.getElementById('authBtn').onclick=doAuth;
  document.getElementById('authTog').onclick=togAuth;
  document.getElementById('hamBtn').onclick=openDr;
  document.getElementById('drOv').onclick=closeDr;
  document.getElementById('sIn').oninput=function(){doSearch(this.value);};
  document.getElementById('sndB').onclick=doSend;
  document.getElementById('msgI').onkeydown=function(e){if(e.key==='Enter')doSend();};
  document.addEventListener('click',function(e){if(!e.target.closest('.pop')&&!e.target.closest('.rbar'))rmPop();});
  var s=localStorage.getItem('supra_sid');
  if(s){var d=D();if(d.a.find(function(x){return x.u===s;})){enterApp();return;}}
});

function togAuth(){
  authMode=1-authMode;
  document.getElementById('regB').classList.toggle('hid',authMode===1);
  document.getElementById('logB').classList.toggle('hid',authMode===0);
  document.getElementById('authBtn').textContent=authMode?'Войти':'Создать аккаунт';
  document.getElementById('authSub').textContent=authMode?'Войдите в аккаунт':'Создайте аккаунт';
  var lk=document.getElementById('authLnk');
  lk.innerHTML=authMode?'Нет аккаунта? <span id="authTog">Создать</span>':'Уже есть аккаунт? <span id="authTog">Войти</span>';
  document.getElementById('authTog').onclick=togAuth;
  document.getElementById('authErr').textContent='';
}

function doAuth(){
  var err=document.getElementById('authErr');
  err.textContent='';
  var d=D();
  if(authMode===1){
    var u=(document.getElementById('lUn').value||'').trim().toLowerCase();
    var p=document.getElementById('lPw').value||'';
    if(!u||!p){err.textContent='Заполните все поля';return;}
    var acc=d.a.find(function(x){return x.u===u&&x.pw===p;});
    if(!acc){err.textContent='Неверный username или пароль';return;}
    localStorage.setItem('supra_sid',acc.u);
    toast('Вход в @'+acc.u);
    enterApp();
  } else {
    var nm=(document.getElementById('rNm').value||'').trim();
    var un=(document.getElementById('rUn').value||'').trim().toLowerCase();
    var pw=document.getElementById('rPw').value||'';
    if(!nm){err.textContent='Введите имя';return;}
    if(!/^[a-z][a-z0-9_]{2,}$/.test(un)){err.textContent='Username: англ буквы, от 3 символов, начинается с буквы';return;}
    if(pw.length<4){err.textContent='Пароль минимум 4 символа';return;}
    if(d.a.find(function(x){return x.u===un;})){err.textContent='Username @'+un+' уже занят';return;}
    if(d.a.length>=3){err.textContent='Максимум 3 аккаунта';return;}
    d.a.push({nm:nm,u:un,pw:pw,av:1,bio:'',gifts:[],nk:{},prv:{noGift:false,noMsg:false,noCh:false,excGift:[],excMsg:[],excCh:[]},cr:Date.now(),ls:Date.now()});
    if(!d.sh)d.sh={};
    if(!d.sh[un])d.sh[un]=[];
    if(!d.vf)d.vf={};
    S(d);
    localStorage.setItem('supra_sid',un);
    toast('Аккаунт @'+un+' создан!');
    enterApp();
  }
}

// ===== APP =====
var cur=null;
var poll=null;

function enterApp(){
  document.getElementById('authScreen').classList.add('hid');
  document.getElementById('app').classList.remove('hid');
  applyIface();
  cur=null;showEmpty();updDr();renderList();
  if(poll)clearInterval(poll);
  poll=setInterval(function(){
    var m2=me();if(!m2)return;
    updMe({ls:Date.now()});
    renderList();
    if(cur)renderMsgs();
  },2500);
}

function logout(){
  localStorage.removeItem('supra_sid');closeDr();cur=null;
  if(poll)clearInterval(poll);
  document.getElementById('app').classList.add('hid');
  document.getElementById('authScreen').classList.remove('hid');
  document.getElementById('authErr').textContent='';
  ['rNm','rUn','rPw','lUn','lPw'].forEach(function(id){var e=document.getElementById(id);if(e)e.value='';});
  authMode=0;
  document.getElementById('regB').classList.remove('hid');
  document.getElementById('logB').classList.add('hid');
  document.getElementById('authBtn').textContent='Создать аккаунт';
  document.getElementById('authSub').textContent='Создайте аккаунт';
  var lk=document.getElementById('authLnk');
  lk.innerHTML='Уже есть аккаунт? <span id="authTog">Войти</span>';
  document.getElementById('authTog').onclick=togAuth;
  toast('Вы вышли из аккаунта');
}

// ===== DRAWER =====
function openDr(){document.getElementById('drawer').classList.add('open');document.getElementById('drOv').classList.add('open');updDr();}
function closeDr(){document.getElementById('drawer').classList.remove('open');document.getElementById('drOv').classList.remove('open');}

function updDr(){
  var u=me();if(!u)return;
  document.getElementById('drAv').innerHTML=avHTML(u,54);
  document.getElementById('drNm').innerHTML=esc(u.nm)+(isVf(u.u)?' <span class="vf">\u2714</span>':'');
  document.getElementById('drU').textContent='@'+u.u;
  var items='';
  items+='<div class="dri" onclick="closeDr();modal(\'profile\')"><svg viewBox="0 0 24 24"><path d="M12 12c2.7 0 5-2.3 5-5s-2.3-5-5-5-5 2.3-5 5 2.3 5 5 5zm0 2c-3.3 0-10 1.7-10 5v2h20v-2c0-3.3-6.7-5-10-5z"/></svg>Мой профиль</div>';
  items+='<div class="dri" onclick="closeDr();openSaved()"><svg viewBox="0 0 24 24"><path d="M17 3H7c-1.1 0-2 .9-2 2v16l7-3 7 3V5c0-1.1-.9-2-2-2z"/></svg>Избранное</div>';
  items+='<div class="dri" onclick="closeDr();modal(\'settings\')"><svg viewBox="0 0 24 24"><path d="M19.14 12.94c.04-.31.06-.63.06-.94s-.02-.63-.06-.94l2.03-1.58a.49.49 0 00.12-.61l-1.92-3.32a.488.488 0 00-.59-.22l-2.39.96c-.5-.38-1.03-.7-1.62-.94l-.36-2.54c-.04-.24-.24-.41-.48-.41h-3.84c-.24 0-.44.17-.47.41l-.36 2.54c-.59.24-1.13.57-1.62.94l-2.39-.96c-.22-.08-.47 0-.59.22L2.74 8.87c-.12.21-.08.47.12.61l2.03 1.58c-.04.31-.06.63-.06.94s.02.63.06.94l-2.03 1.58a.49.49 0 00-.12.61l1.92 3.32c.12.22.37.29.59.22l2.39-.96c.5.38 1.03.7 1.62.94l.36 2.54c.05.24.24.41.48.41h3.84c.24 0 .44-.17.47-.41l.36-2.54c.59-.24 1.13-.56 1.62-.94l2.39.96c.22.08.47 0 .59-.22l1.92-3.32c.12-.22.07-.47-.12-.61l-2.01-1.58zM12 15.6c-1.98 0-3.6-1.62-3.6-3.6s1.62-3.6 3.6-3.6 3.6 1.62 3.6 3.6-1.62 3.6-3.6 3.6z"/></svg>Настройки</div>';
  items+='<div class="dri" onclick="closeDr();modal(\'privacy\')"><svg viewBox="0 0 24 24"><path d="M12 1L3 5v6c0 5.55 3.84 10.74 9 12 5.16-1.26 9-6.45 9-12V5l-9-4zm0 10.99h7c-.53 4.12-3.28 7.79-7 8.94V12H5V6.3l7-3.11v8.8z"/></svg>Конфиденциальность</div>';
  items+='<div class="dri" onclick="closeDr();modal(\'newch\')"><svg viewBox="0 0 24 24"><path d="M20 2H4c-1.1 0-2 .9-2 2v18l4-4h14c1.1 0 2-.9 2-2V4c0-1.1-.9-2-2-2zm-1 11h-4v4h-2v-4H9v-2h4V7h2v4h4v2z"/></svg>Создать канал</div>';
  items+='<div class="dri" onclick="closeDr();modal(\'accounts\')"><svg viewBox="0 0 24 24"><path d="M16 11c1.66 0 3-1.34 3-3s-1.34-3-3-3-3 1.34-3 3 1.34 3 3 3zm-8 0c1.66 0 3-1.34 3-3S9.66 5 8 5 5 6.34 5 8s1.34 3 3 3zm0 2c-2.33 0-7 1.17-7 3.5V19h14v-2.5c0-2.33-4.67-3.5-7-3.5zm8 0c-.29 0-.62.02-.97.05 1.16.84 1.97 1.97 1.97 3.45V19h6v-2.5c0-2.33-4.67-3.5-7-3.5z"/></svg>Аккаунты</div>';
  if(u.u==='surpa'){
    items+='<div class="dri" style="color:#f5a623" onclick="closeDr();modal(\'admin\')"><svg viewBox="0 0 24 24" style="fill:#f5a623"><path d="M12 1L3 5v6c0 5.55 3.84 10.74 9 12 5.16-1.26 9-6.45 9-12V5l-9-4zm0 10.99h7c-.53 4.12-3.28 7.79-7 8.94V12H5V6.3l7-3.11v8.8z"/></svg>Админ панель</div>';
  }
  items+='<div class="dri red" onclick="closeDr();logout()"><svg viewBox="0 0 24 24"><path d="M17 7l-1.41 1.41L18.17 11H8v2h10.17l-2.58 2.58L17 17l5-5-5-5zM4 5h8V3H4c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h8v-2H4V5z"/></svg>Выйти</div>';
  document.getElementById('drItems').innerHTML=items;
}

// ===== CHAT LIST =====
function renderList(){
  var u=me();if(!u)return;
  var d=D(),box=document.getElementById('sbL');
  var sq=(document.getElementById('sIn').value||'').trim().toLowerCase();
  if(sq){searchRender(sq);return;}
  var chats=[];
  var sk='sv|'+u.u;
  var sm=d.m[sk]||[];
  chats.push({t:'saved',last:sm.length?sm[sm.length-1]:null,ur:0});
  var partners={};
  Object.keys(d.m).forEach(function(k){
    if(k.indexOf('|')<0||k.startsWith('sv|'))return;
    if(k.indexOf(u.u)>=0){var pp=k.split('|');var o=pp[0]===u.u?pp[1]:pp[0];if(o)partners[o]=true;}
  });
  (d.sh[u.u]||[]).forEach(function(x){partners[x]=true;});
  Object.keys(partners).forEach(function(p){
    var k2=ck(u.u,p),ms=d.m[k2]||[];
    var acc=d.a.find(function(x){return x.u===p;});
    var unr=ms.filter(function(x){return x.f===p&&!x.rd;}).length;
    chats.push({t:'dm',u:p,acc:acc,nm:dname(p),last:ms.length?ms[ms.length-1]:null,ur:unr});
  });
  Object.keys(d.ch||{}).forEach(function(cid){
    var c=d.ch[cid];
    if(c.mb.indexOf(u.u)>=0||c.ow===u.u){
      var ps=c.ps||[];
      chats.push({t:'ch',id:cid,nm:c.nm,last:ps.length?{tx:ps[ps.length-1].tx,tm:ps[ps.length-1].tm}:null,ur:0});
    }
  });
  chats.sort(function(a,b){if(a.t==='saved')return-1;if(b.t==='saved')return 1;var ta=a.last?a.last.tm||0:0,tb=b.last?b.last.tm||0:0;return tb-ta;});
  box.innerHTML=chats.map(function(c){
    if(c.t==='saved'){
      var act=cur==='saved'?' act':'';
      return'<div class="ci'+act+'" onclick="openSaved()"><div class="ci-av" style="background:var(--ac)"><svg viewBox="0 0 24 24" width="22" height="22" fill="#fff"><path d="M17 3H7c-1.1 0-2 .9-2 2v16l7-3 7 3V5c0-1.1-.9-2-2-2z"/></svg></div><div class="ci-nfo"><div class="ci-nm">Избранное</div><div class="ci-last">'+(c.last?esc(c.last.tx||'').substring(0,30):'Нет сообщений')+'</div></div>'+(c.last?'<div class="ci-meta"><span class="ci-time">'+ft(c.last.tm)+'</span></div>':'')+'</div>';
    }
    if(c.t==='dm'){
      var act=cur===c.u?' act':'',on=isOn(c.u);
      var ltx=c.last?((c.last.f===u.u?'<span style="color:var(--ac)">Вы: </span>':'')+esc(c.last.tx||'').substring(0,30)):'';
      return'<div class="ci'+act+'" onclick="openDM(\''+c.u+'\')"><div style="position:relative">'+avHTML(c.acc)+(on?'<div class="ci-dot"></div>':'')+'</div><div class="ci-nfo"><div class="ci-nm">'+esc(c.nm)+(isVf(c.u)?' <span class="vf">\u2714</span>':'')+'</div><div class="ci-last">'+ltx+'</div></div><div class="ci-meta">'+(c.last?'<span class="ci-time">'+ft(c.last.tm)+'</span>':'')+(c.ur?'<span class="ci-badge">'+c.ur+'</span>':'')+'</div></div>';
    }
    if(c.t==='ch'){
      var act=cur==='ch:'+c.id?' act':'';
      return'<div class="ci'+act+'" onclick="openCh(\''+c.id+'\')"><div class="ci-av" style="background:#a87bdb;width:50px;height:50px;border-radius:50%;display:flex;align-items:center;justify-content:center"><svg viewBox="0 0 24 24" width="22" height="22" fill="#fff"><path d="M20 2H4c-1.1 0-2 .9-2 2v18l4-4h14c1.1 0 2-.9 2-2V4c0-1.1-.9-2-2-2z"/></svg></div><div class="ci-nfo"><div class="ci-nm">'+esc(c.nm)+'</div><div class="ci-last">'+(c.last?esc(c.last.tx||'').substring(0,30):'Нет постов')+'</div></div>'+(c.last?'<div class="ci-meta"><span class="ci-time">'+ft(c.last.tm)+'</span></div>':'')+'</div>';
    }
    return'';
  }).join('');
}

// ===== SEARCH =====
function doSearch(v){if(!(v||'').trim()){renderList();return;}searchRender(v.trim().toLowerCase());}
function searchRender(q){
  var u=me(),d=D();
  var res=d.a.filter(function(a){return a.u!==u.u&&a.u.indexOf(q)>=0;});
  var box=document.getElementById('sbL');
  var hist=d.sh[u.u]||[];
  var h='';
  if(res.length){
    h+='<div class="sec">Результаты</div>';
    res.forEach(function(a){
      h+='<div class="sr" onclick="addSearch(\''+a.u+'\')">'+avHTML(a)+'<div><div style="font-weight:500">'+esc(a.nm)+(isVf(a.u)?' <span class="vf">\u2714</span>':'')+'</div><div style="font-size:12px;color:var(--tx2)">@'+a.u+'</div></div></div>';
    });
  } else if(q){
    h+='<div style="padding:24px;text-align:center;color:var(--tx2)">Никого не найдено</div>';
  }
  if(hist.length){
    h+='<div class="sec">Недавние <span onclick="clearHist()">Очистить</span></div>';
    hist.forEach(function(un){
      var a=d.a.find(function(x){return x.u===un;});
      if(a)h+='<div class="sr" onclick="openDM(\''+a.u+'\')">'+avHTML(a)+'<div><div style="font-weight:500">'+esc(a.nm)+'</div><div style="font-size:12px;color:var(--tx2)">@'+a.u+'</div></div></div>';
    });
  }
  box.innerHTML=h;
}
function addSearch(un){
  var u=me(),d=D();
  if(!d.sh[u.u])d.sh[u.u]=[];
  var i=d.sh[u.u].indexOf(un);if(i>=0)d.sh[u.u].splice(i,1);
  d.sh[u.u].unshift(un);if(d.sh[u.u].length>10)d.sh[u.u].pop();
  S(d);document.getElementById('sIn').value='';openDM(un);
}
function clearHist(){var u=me(),d=D();d.sh[u.u]=[];S(d);renderList();toast('История поиска очищена');}

// ===== OPEN CHATS =====
function showEmpty(){
  document.getElementById('chaE').classList.remove('hid');
  document.getElementById('chaV').classList.add('hid');
  document.getElementById('chaV').style.display='none';
  document.getElementById('blockedBar').classList.add('hid');
  if(iface==='phone'){document.getElementById('chaArea').classList.remove('open');}
}
function showChat(){
  document.getElementById('chaE').classList.add('hid');
  document.getElementById('chaV').classList.remove('hid');
  document.getElementById('chaV').style.display='flex';
  if(iface==='phone'){document.getElementById('chaArea').classList.add('open');}
}
function goBack(){
  cur=null;
  if(iface==='phone'){document.getElementById('chaArea').classList.remove('open');}
  else{showEmpty();}
  renderList();
}
function openSaved(){cur='saved';closeDr();showChat();renderHead();renderMsgs();renderList();document.getElementById('inpA').classList.remove('hid');document.getElementById('blockedBar').classList.add('hid');}
function openDM(un){
  cur=un;closeDr();
  var u=me(),d=D(),k=ck(u.u,un);
  if(d.m[k])d.m[k].forEach(function(x){if(x.f===un)x.rd=true;});
  S(d);showChat();renderHead();renderMsgs();renderList();
  // Check if messaging is blocked
  var blocked=!canMsg(u.u,un)&&u.u!==un;
  var blockedBar=document.getElementById('blockedBar');
  if(blocked){
    blockedBar.classList.remove('hid');
    blockedBar.innerHTML='<div class="blocked-msg">Этот пользователь запретил входящие сообщения</div>';
    document.getElementById('inpA').classList.add('hid');
  } else {
    blockedBar.classList.add('hid');
    document.getElementById('inpA').classList.remove('hid');
  }
}
function openCh(cid){cur='ch:'+cid;closeDr();showChat();renderHead();renderMsgs();renderList();document.getElementById('blockedBar').classList.add('hid');}

// ===== CHAT HEADER =====
function renderHead(){
  var u=me(),d=D(),h=document.getElementById('chaH');
  var backBtn='<div class="ch-back" onclick="goBack()"><svg viewBox="0 0 24 24"><path d="M20 11H7.83l5.59-5.59L12 4l-8 8 8 8 1.41-1.41L7.83 13H20v-2z"/></svg></div>';
  if(cur==='saved'){
    h.innerHTML=backBtn+'<div class="ci-av" style="background:var(--ac);width:42px;height:42px;display:flex;align-items:center;justify-content:center"><svg viewBox="0 0 24 24" width="20" height="20" fill="#fff"><path d="M17 3H7c-1.1 0-2 .9-2 2v16l7-3 7 3V5c0-1.1-.9-2-2-2z"/></svg></div><div class="ch-nfo"><div class="ch-nm">Избранное</div><div class="ch-st">сохранённые сообщения</div></div><div class="ch-btn" onclick="clearAll()" title="Очистить"><svg viewBox="0 0 24 24"><path d="M6 19c0 1.1.9 2 2 2h8c1.1 0 2-.9 2-2V7H6v12zM19 4h-3.5l-1-1h-5l-1 1H5v2h14V4z"/></svg></div>';
    return;
  }
  if(cur&&cur.startsWith('ch:')){
    var cid=cur.slice(3),c=d.ch[cid];if(!c)return;
    var isOwner=c.ow===u.u;
    h.innerHTML=backBtn+'<div class="ci-av" style="background:#a87bdb;width:42px;height:42px;border-radius:50%;display:flex;align-items:center;justify-content:center"><svg viewBox="0 0 24 24" width="20" height="20" fill="#fff"><path d="M20 2H4c-1.1 0-2 .9-2 2v18l4-4h14c1.1 0 2-.9 2-2V4c0-1.1-.9-2-2-2z"/></svg></div><div class="ch-nfo" onclick="modal(\'chinfo\',\''+cid+'\')"><div class="ch-nm">'+esc(c.nm)+'</div><div class="ch-st">'+(c.mb.length+1)+' подписчиков</div></div>'+(isOwner?'<div class="ch-btn" onclick="modal(\'chadd\',\''+cid+'\')" title="Добавить"><svg viewBox="0 0 24 24"><path d="M15 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm-9-2V7H4v3H1v2h3v3h2v-3h3v-2H6zm9 4c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z"/></svg></div>':'')+'<div class="ch-btn" onclick="modal(\'chinfo\',\''+cid+'\')" title="Инфо"><svg viewBox="0 0 24 24"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm1 15h-2v-6h2v6zm0-8h-2V7h2v2z"/></svg></div>'+(isOwner?'<div class="ch-btn" onclick="modal(\'chset\',\''+cid+'\')" title="Настройки"><svg viewBox="0 0 24 24"><path d="M19.14 12.94c.04-.31.06-.63.06-.94s-.02-.63-.06-.94l2.03-1.58a.49.49 0 00.12-.61l-1.92-3.32a.488.488 0 00-.59-.22l-2.39.96c-.5-.38-1.03-.7-1.62-.94l-.36-2.54c-.04-.24-.24-.41-.48-.41h-3.84c-.24 0-.44.17-.47.41l-.36 2.54c-.59.24-1.13.57-1.62.94l-2.39-.96c-.22-.08-.47 0-.59.22L2.74 8.87c-.12.21-.08.47.12.61l2.03 1.58c-.04.31-.06.63-.06.94s.02.63.06.94l-2.03 1.58a.49.49 0 00-.12.61l1.92 3.32c.12.22.37.29.59.22l2.39-.96c.5.38 1.03.7 1.62.94l.36 2.54c.05.24.24.41.48.41h3.84c.24 0 .44-.17.47-.41l.36-2.54c.59-.24 1.13-.56 1.62-.94l2.39.96c.22.08.47 0 .59-.22l1.92-3.32c.12-.22.07-.47-.12-.61l-2.01-1.58zM12 15.6c-1.98 0-3.6-1.62-3.6-3.6s1.62-3.6 3.6-3.6 3.6 1.62 3.6 3.6-1.62 3.6-3.6 3.6z"/></svg></div>':'');
    document.getElementById('inpA').classList.toggle('hid',!isOwner);
    return;
  }
  if(cur){
    var acc=d.a.find(function(x){return x.u===cur;}),on=isOn(cur);
    h.innerHTML=backBtn+'<div style="position:relative">'+avHTML(acc,42)+(on?'<div class="ci-dot" style="border-color:var(--sb)"></div>':'')+'</div><div class="ch-nfo" onclick="modal(\'vprof\',\''+cur+'\')"><div class="ch-nm">'+esc(dname(cur))+(isVf(cur)?' <span class="vf">\u2714</span>':'')+'</div><div class="ch-st">'+(on?'<span style="color:var(--gn)">в сети</span>':'был(а) недавно')+'</div></div><div class="ch-btn" onclick="dotMenu(event,\''+cur+'\')" title="Ещё"><svg viewBox="0 0 24 24"><path d="M12 8c1.1 0 2-.9 2-2s-.9-2-2-2-2 .9-2 2 .9 2 2 2zm0 2c-1.1 0-2 .9-2 2s.9 2 2 2 2-.9 2-2-.9-2-2-2zm0 6c-1.1 0-2 .9-2 2s.9 2 2 2 2-.9 2-2-.9-2-2-2z"/></svg></div>';
  }
}

// ===== MESSAGES =====
function renderMsgs(){
  var u=me(),d=D(),box=document.getElementById('msgB');
  if(!cur){box.innerHTML='';return;}
  if(cur==='saved'){
    var ms=d.m['sv|'+u.u]||[];
    box.innerHTML=dateSeps(ms.map(function(m,i){return mHTML(m,i,true);}),ms);
    box.scrollTop=box.scrollHeight;return;
  }
  if(cur.startsWith('ch:')){
    var cid=cur.slice(3),c=d.ch[cid];if(!c){box.innerHTML='';return;}
    var ps=c.ps||[];
    ps.forEach(function(p){if(!p.vb)p.vb=[];if(p.vb.indexOf(u.u)<0){p.vb.push(u.u);p.vw=(p.vw||0)+1;}});
    S(d);
    box.innerHTML=ps.length?ps.map(function(p,i){
      var myRx=null;if(p.rx)for(var r in p.rx)if(p.rx[r].indexOf(u.u)>=0){myRx=r;break;}
      return'<div class="cpost"><div class="cpost-t">'+esc(p.tx)+'</div><div class="cpost-m"><span>\ud83d\udc41 '+(p.vw||0)+'</span><span>'+ft(p.tm)+'</span></div><div class="cpost-rx">'+RX.map(function(r){var cnt=(p.rx&&p.rx[r])?p.rx[r].length:0;var my=myRx===r;return'<span class="rx'+(my?' my':'')+'" onclick="rxPost(\''+cid+'\','+i+',\''+r+'\')">'+r+(cnt?' '+cnt:'')+'</span>';}).join('')+'</div></div>';
    }).join(''):'<div style="text-align:center;color:var(--tx2);padding:40px">Пока нет постов</div>';
    box.scrollTop=box.scrollHeight;return;
  }
  var k=ck(u.u,cur),ms=d.m[k]||[];
  box.innerHTML=dateSeps(ms.map(function(m,i){return mHTML(m,i,false);}),ms);
  box.scrollTop=box.scrollHeight;
}

function dateSeps(htmlArr,msgs){
  if(!msgs.length)return'<div style="text-align:center;color:var(--tx2);padding:40px;font-size:14px">Нет сообщений</div>';
  var r='',ld='';
  for(var i=0;i<msgs.length;i++){
    var ds=fd(msgs[i].tm);
    if(ds!==ld){r+='<div class="msg-date"><span>'+ds+'</span></div>';ld=ds;}
    r+=htmlArr[i];
  }
  return r;
}

function mHTML(m,i,sv){
  var u=me(),out=m.f===u.u,cl='m '+(out?'m-o':'m-i');
  if(m.tp==='sys'){return'<div class="m-sys"><span>'+esc(m.tx)+'</span></div>';}
  if(m.tp==='gift'){
    var g=GIFTS.find(function(x){return x.id===m.gi;});
    return'<div class="'+cl+' m-gift" oncontextmenu="ctxMsg(event,'+i+','+sv+')" ondblclick="rxPk(event,'+i+','+sv+')"><div class="m-gift-i">'+(g?g.icon:'\ud83c\udf81')+'</div><div class="m-gift-t">\ud83c\udf81 Подарок: '+(g?g.name:'')+'</div>'+(m.gt?'<div class="m-gift-x">"'+esc(m.gt)+'"</div>':'')+'<div style="font-size:12px;color:var(--tx2);margin-top:4px">от @'+esc(m.f)+'</div><div class="m-ft"><span>'+ft(m.tm)+'</span>'+(out?'<span class="m-ck">'+(m.rd?'\u2713\u2713':'\u2713')+'</span>':'')+'</div>'+rxH(m,i,sv)+'</div>';
  }
  return'<div class="'+cl+'" oncontextmenu="ctxMsg(event,'+i+','+sv+')" ondblclick="rxPk(event,'+i+','+sv+')"><div class="m-tx">'+esc(m.tx)+'</div><div class="m-ft"><span>'+ft(m.tm)+'</span>'+(out?'<span class="m-ck">'+(m.rd?'\u2713\u2713':'\u2713')+'</span>':'')+'</div>'+rxH(m,i,sv)+'</div>';
}

function rxH(m,i,sv){
  if(!m.rx)return'';
  var u=me(),h='<div class="m-rx">';
  for(var r in m.rx){
    if(!m.rx[r].length)continue;
    var my=m.rx[r].indexOf(u.u)>=0;
    h+='<span class="rx'+(my?' my':'')+'" onclick="togRx('+i+',\''+r+'\','+sv+')">'+r+' '+m.rx[r].length+'</span>';
  }
  return h+'</div>';
}

// ===== SEND =====
function doSend(){
  var u=me(),inp=document.getElementById('msgI'),tx=(inp.value||'').trim();
  if(!tx)return;
  var d=D();
  if(cur==='saved'){
    var k='sv|'+u.u;if(!d.m[k])d.m[k]=[];
    d.m[k].push({f:u.u,tx:tx,tm:Date.now(),rd:true,rx:{}});
    S(d);inp.value='';renderMsgs();renderList();return;
  }
  if(cur&&cur.startsWith('ch:')){
    var cid=cur.slice(3),c=d.ch[cid];
    if(c&&c.ow===u.u){
      if(!c.ps)c.ps=[];
      c.ps.push({tx:tx,tm:Date.now(),rx:{},vw:0,vb:[]});
      S(d);inp.value='';renderMsgs();renderList();
    }
    return;
  }
  if(cur){
    // Check if target blocked messages from us
    if(!canMsg(u.u,cur)&&u.u!==cur){
      toast('Этот пользователь запретил входящие сообщения');
      return;
    }
    var k=ck(u.u,cur);if(!d.m[k])d.m[k]=[];
    d.m[k].push({f:u.u,tx:tx,tm:Date.now(),rd:false,rx:{}});
    S(d);inp.value='';renderMsgs();renderList();
  }
}

// ===== REACTIONS =====
function togRx(i,r,sv){
  var u=me(),d=D(),ms;
  if(sv){ms=d.m['sv|'+u.u]||[];}
  else{ms=d.m[ck(u.u,cur)]||[];}
  if(!ms[i])return;var m=ms[i];
  if(!m.rx)m.rx={};
  for(var k in m.rx){
    var idx=m.rx[k].indexOf(u.u);
    if(idx>=0){m.rx[k].splice(idx,1);if(!m.rx[k].length)delete m.rx[k];if(k===r){S(d);renderMsgs();return;}}
  }
  if(!m.rx[r])m.rx[r]=[];
  m.rx[r].push(u.u);S(d);renderMsgs();
}
function rxPost(cid,i,r){
  var u=me(),d=D(),c=d.ch[cid];if(!c||!c.ps[i])return;
  var p=c.ps[i];if(!p.rx)p.rx={};
  for(var k in p.rx){
    var idx=p.rx[k].indexOf(u.u);
    if(idx>=0){p.rx[k].splice(idx,1);if(!p.rx[k].length)delete p.rx[k];if(k===r){S(d);renderMsgs();return;}}
  }
  if(!p.rx[r])p.rx[r]=[];
  p.rx[r].push(u.u);S(d);renderMsgs();
}

function rxPk(e,i,sv){
  e.preventDefault();rmPop();
  var bar=document.createElement('div');bar.className='rbar';bar.id='_pop';
  bar.style.left=Math.min(e.clientX,window.innerWidth-220)+'px';
  bar.style.top=Math.max(e.clientY-50,10)+'px';
  bar.innerHTML=RX.map(function(r){return'<span class="rbtn" onclick="togRx('+i+',\''+r+'\','+sv+');rmPop()">'+r+'</span>';}).join('');
  document.body.appendChild(bar);
}

// ===== CONTEXT MENU =====
function ctxMsg(e,i,sv){
  e.preventDefault();rmPop();
  var u=me(),d=D(),ms;
  if(sv){ms=d.m['sv|'+u.u]||[];}else{ms=d.m[ck(u.u,cur)]||[];}
  var m=ms[i];if(!m)return;
  var el=document.createElement('div');el.className='pop';el.id='_pop';
  el.style.left=Math.min(e.clientX,window.innerWidth-190)+'px';
  el.style.top=Math.min(e.clientY,window.innerHeight-160)+'px';
  el.innerHTML='<div class="pop-i" onclick="copyM('+i+','+sv+')"><svg viewBox="0 0 24 24" width="18" height="18" fill="var(--tx2)"><path d="M16 1H4c-1.1 0-2 .9-2 2v14h2V3h12V1zm3 4H8c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h11c1.1 0 2-.9 2-2V7c0-1.1-.9-2-2-2zm0 16H8V7h11v14z"/></svg>Копировать</div><div class="pop-i" onclick="rxPk2('+i+','+sv+')"><svg viewBox="0 0 24 24" width="18" height="18" fill="var(--tx2)"><path d="M11.99 2C6.47 2 2 6.48 2 12s4.47 10 9.99 10C17.52 22 22 17.52 22 12S17.52 2 11.99 2zM12 20c-4.42 0-8-3.58-8-8s3.58-8 8-8 8 3.58 8 8-3.58 8-8 8zm3.5-9c.83 0 1.5-.67 1.5-1.5S16.33 8 15.5 8 14 8.67 14 9.5s.67 1.5 1.5 1.5zm-7 0c.83 0 1.5-.67 1.5-1.5S9.33 8 8.5 8 7 8.67 7 9.5 7.67 11 8.5 11zm3.5 6.5c2.33 0 4.31-1.46 5.11-3.5H6.89c.8 2.04 2.78 3.5 5.11 3.5z"/></svg>Реакция</div>'+(m.f===u.u?'<div class="pop-i red" onclick="delM('+i+','+sv+')"><svg viewBox="0 0 24 24" width="18" height="18" fill="var(--rd)"><path d="M6 19c0 1.1.9 2 2 2h8c1.1 0 2-.9 2-2V7H6v12zM19 4h-3.5l-1-1h-5l-1 1H5v2h14V4z"/></svg>Удалить</div>':'');
  document.body.appendChild(el);
}
function rxPk2(i,sv){rmPop();var e={clientX:window.innerWidth/2-100,clientY:window.innerHeight/2,preventDefault:function(){}};rxPk(e,i,sv);}
function copyM(i,sv){
  var u=me(),d=D(),ms;
  if(sv){ms=d.m['sv|'+u.u]||[];}else{ms=d.m[ck(u.u,cur)]||[];}
  if(ms[i])try{navigator.clipboard.writeText(ms[i].tx||'');toast('Скопировано');}catch(e){}
  rmPop();
}
function delM(i,sv){
  var u=me(),d=D();
  if(sv){var k='sv|'+u.u;if(d.m[k])d.m[k].splice(i,1);}
  else{var k=ck(u.u,cur);if(d.m[k])d.m[k].splice(i,1);}
  S(d);rmPop();renderMsgs();renderList();toast('Сообщение удалено');
}
function clearAll(){
  if(!confirm('Очистить историю?'))return;
  var u=me(),d=D();
  if(cur==='saved'){d.m['sv|'+u.u]=[];}
  else if(cur&&cur.startsWith('ch:')){var c=d.ch[cur.slice(3)];if(c)c.ps=[];}
  else if(cur){d.m[ck(u.u,cur)]=[];}
  S(d);renderMsgs();renderList();toast('История очищена');
}
function rmPop(){var e=document.getElementById('_pop');if(e)e.remove();}

// ===== DOT MENU =====
function dotMenu(e,un){
  e.stopPropagation();rmPop();
  var u=me();
  var giftBlocked=!canGift(u.u,un)&&u.u!==un;
  var el=document.createElement('div');el.className='pop';el.id='_pop';
  el.style.right='14px';el.style.top='56px';
  el.innerHTML='<div class="pop-i" onclick="rmPop();modal(\'vprof\',\''+un+'\')"><svg viewBox="0 0 24 24" width="18" height="18" fill="var(--tx2)"><path d="M12 12c2.7 0 5-2.3 5-5s-2.3-5-5-5-5 2.3-5 5 2.3 5 5 5zm0 2c-3.3 0-10 1.7-10 5v2h20v-2c0-3.3-6.7-5-10-5z"/></svg>Профиль</div><div class="pop-i" onclick="rmPop();modal(\'rename\',\''+un+'\')"><svg viewBox="0 0 24 24" width="18" height="18" fill="var(--tx2)"><path d="M3 17.25V21h3.75L17.81 9.94l-3.75-3.75L3 17.25zM20.71 7.04a1 1 0 000-1.42l-2.34-2.34a1 1 0 00-1.42 0l-1.83 1.83 3.75 3.75 1.84-1.82z"/></svg>Переименовать</div>'+(giftBlocked?'<div class="pop-i" style="opacity:.4;cursor:default"><svg viewBox="0 0 24 24" width="18" height="18" fill="var(--tx2)"><path d="M20 6h-2.18c.11-.31.18-.65.18-1a3 3 0 00-5.5-1.65l-.5.67-.5-.68A3 3 0 006 5c0 .35.07.69.18 1H4c-1.11 0-2 .89-2 2v11c0 1.11.89 2 2 2h16c1.11 0 2-.89 2-2V8c0-1.11-.89-2-2-2z"/></svg>Подарки запрещены</div>':'<div class="pop-i" onclick="rmPop();modal(\'gift\',\''+un+'\')"><svg viewBox="0 0 24 24" width="18" height="18" fill="var(--tx2)"><path d="M20 6h-2.18c.11-.31.18-.65.18-1a3 3 0 00-5.5-1.65l-.5.67-.5-.68A3 3 0 006 5c0 .35.07.69.18 1H4c-1.11 0-2 .89-2 2v11c0 1.11.89 2 2 2h16c1.11 0 2-.89 2-2V8c0-1.11-.89-2-2-2zm-5-2c.55 0 1 .45 1 1s-.45 1-1 1-1-.45-1-1 .45-1 1-1zM9 4c.55 0 1 .45 1 1s-.45 1-1 1-1-.45-1-1 .45-1 1-1zm11 15H4v-2h16v2zm0-5H4V8h5.08L7 10.83 8.62 12 11 8.76l1-1.36 1 1.36L15.38 12 17 10.83 14.92 8H20v6z"/></svg>Подарить подарок</div>')+'<div class="pop-i red" onclick="rmPop();clearAll()"><svg viewBox="0 0 24 24" width="18" height="18" fill="var(--rd)"><path d="M6 19c0 1.1.9 2 2 2h8c1.1 0 2-.9 2-2V7H6v12zM19 4h-3.5l-1-1h-5l-1 1H5v2h14V4z"/></svg>Очистить историю</div>';
  document.body.appendChild(el);
  setTimeout(function(){document.addEventListener('click',rmPop,{once:true});},10);
}

// ===== MODALS =====
var tmpAv=null,tmpGift=null;

function modal(type,ex){
  closeDr();rmPop();
  var mc=document.getElementById('mdlB'),u=me(),d=D();
  var W=function(inner){return'<div class="mo" id="mdlOv" onclick="if(event.target===this)clM()"><div class="md">'+inner+'</div></div>';};

  if(type==='profile'){
    var gs=(u.gifts||[]).filter(function(g){return!g.sd;});
    var gh=gs.length?'<div style="margin-top:16px"><div style="font-size:13px;color:var(--tx2);margin-bottom:8px">Подарки ('+gs.length+')</div><div style="display:flex;flex-wrap:wrap;justify-content:center">'+gs.map(function(g,idx){
      var gd=GIFTS.find(function(x){return x.id===g.gi;});
      var ri=u.gifts.indexOf(g);
      return'<div class="pg'+(g.hd?' dim':'')+'" onclick="modal(\'vgift\',\''+ri+'\')"><div class="pg-i">'+(gd?gd.icon:'\ud83c\udf81')+'</div>'+(g.hd?'<div class="pg-bd">\ud83d\udeab</div>':'')+'</div>';
    }).join('')+'</div></div>':'';
    mc.innerHTML=W('<h2>Мой профиль <span class="x" onclick="clM()">\u2715</span></h2><div style="text-align:center">'+avHTML(u,80)+'<div style="margin-top:10px;font-size:20px;font-weight:600">'+esc(u.nm)+(isVf(u.u)?' <span class="vf">\u2714</span>':'')+'</div><div style="color:var(--tx2);font-size:13px;margin-top:3px">@'+u.u+'</div>'+(u.bio?'<div style="color:var(--tx2);font-size:13px;margin-top:8px">'+esc(u.bio)+'</div>':'')+(isVf(u.u)?'<div style="color:var(--ac);font-size:13px;margin-top:10px;font-style:italic">данный акаунт легенды ле</div>':'')+'</div>'+gh+'<div style="margin-top:16px;text-align:center;font-size:11px;color:#3d4d5c">Зарегистрирован '+new Date(u.cr).toLocaleDateString('ru-RU')+'</div>');
    return;
  }

  if(type==='vprof'){
    var acc=d.a.find(function(x){return x.u===ex;});if(!acc)return;
    var gs=(acc.gifts||[]).filter(function(g){return!g.hd&&!g.sd;});
    var gh=gs.length?'<div style="margin-top:16px"><div style="font-size:13px;color:var(--tx2);margin-bottom:8px">Подарки ('+gs.length+')</div><div style="display:flex;flex-wrap:wrap;justify-content:center">'+gs.map(function(g,idx){
      var gd=GIFTS.find(function(x){return x.id===g.gi;});
      return'<div class="pg" onclick="viewOtherGift(\''+acc.u+'\','+idx+')"><div class="pg-i">'+(gd?gd.icon:'\ud83c\udf81')+'</div></div>';
    }).join('')+'</div></div>':'';
    mc.innerHTML=W('<h2>Профиль <span class="x" onclick="clM()">\u2715</span></h2><div style="text-align:center">'+avHTML(acc,80)+'<div style="margin-top:10px;font-size:20px;font-weight:600">'+esc(acc.nm)+(isVf(acc.u)?' <span class="vf">\u2714</span>':'')+'</div><div style="color:var(--tx2);font-size:13px;margin-top:3px">@'+acc.u+'</div>'+(acc.bio?'<div style="color:var(--tx2);font-size:13px;margin-top:8px">'+esc(acc.bio)+'</div>':'')+(isVf(acc.u)?'<div style="color:var(--ac);font-size:13px;margin-top:10px;font-style:italic">данный акаунт легенды ле</div>':'')+'<div style="margin-top:8px;font-size:12px;color:'+(isOn(acc.u)?'var(--gn)':'var(--tx2)')+'">'+(isOn(acc.u)?'\u25cf в сети':'был(а) недавно')+'</div></div>'+gh+'<button class="btn" style="width:100%;margin-top:16px" onclick="clM();openDM(\''+acc.u+'\')">Написать сообщение</button>');
    return;
  }

  if(type==='vgift'){
    var i=parseInt(ex),g=u.gifts[i];if(!g)return;
    var gd=GIFTS.find(function(x){return x.id===g.gi;});
    var from=d.a.find(function(x){return x.u===g.fr;});
    mc.innerHTML=W('<h2>Подарок <span class="x" onclick="clM()">\u2715</span></h2><div style="text-align:center;padding:12px"><div style="font-size:72px;line-height:1;margin-bottom:12px">'+(gd?gd.icon:'\ud83c\udf81')+'</div><div style="font-size:20px;font-weight:600">'+(gd?gd.name:'Подарок')+'</div><div style="color:var(--tx2);margin-top:10px;font-size:14px">От: <span style="color:var(--ac)">@'+esc(g.fr)+'</span>'+(from?' ('+esc(from.nm)+')':'')+'</div>'+(g.tx?'<div style="color:var(--tx);margin-top:10px;font-size:14px;font-style:italic;background:var(--inp);padding:10px 16px;border-radius:8px">"'+esc(g.tx)+'"</div>':'')+'<div style="color:#3d4d5c;margin-top:10px;font-size:12px">'+new Date(g.tm).toLocaleString('ru-RU')+'</div><div style="display:flex;gap:8px;justify-content:center;margin-top:16px"><button class="btn" onclick="togHide('+i+')">'+(g.hd?'Показать':'Скрыть')+'</button><button class="btn red" onclick="sellG('+i+')">Продать</button></div></div>');
    return;
  }

  if(type==='settings'){
    tmpAv=null;
    var curTheme=theme;
    var curIface=iface;
    mc.innerHTML=W('<h2>Настройки <span class="x" onclick="clM()">\u2715</span></h2><label>Имя</label><input type="text" id="sNm" value="'+esc(u.nm)+'"><label>Username</label><input type="text" id="sUn" value="'+u.u+'"><div style="font-size:11px;color:var(--tx2);margin-top:2px">Англ буквы/цифры, от 3 символов</div><label>Био / Описание</label><textarea id="sBio">'+esc(u.bio||'')+'</textarea><label>Аватар</label><div class="av-ops">'+AVATARS.map(function(av){
      var sel=u.av===av.id?' sel':'';
      if(av.type==='img'){
        return'<div class="av-o'+sel+'" onclick="pickAv('+av.id+',this)"><img src="'+av.src+'" alt=""></div>';
      }
      return'<div class="av-o'+sel+'" style="background:'+av.bg+'" onclick="pickAv('+av.id+',this)">'+((u.nm||'?')[0].toUpperCase())+'</div>';
    }).join('')+'</div><label>Тема оформления</label><div class="theme-tog"><div class="theme-btn'+(curTheme==='dark'?' sel':'')+'" onclick="pickTheme(\'dark\',this)"><div style="font-size:20px;margin-bottom:4px">\ud83c\udf19</div>Тёмная</div><div class="theme-btn'+(curTheme==='light'?' sel':'')+'" onclick="pickTheme(\'light\',this)"><div style="font-size:20px;margin-bottom:4px">\u2600\ufe0f</div>Светлая</div></div><label>Интерфейс</label><div class="if-tog"><div class="if-btn'+(curIface==='pc'?' sel':'')+'" onclick="pickIf(\'pc\',this)"><div style="font-size:20px;margin-bottom:4px">\ud83d\udcbb</div>Компьютер</div><div class="if-btn'+(curIface==='phone'?' sel':'')+'" onclick="pickIf(\'phone\',this)"><div style="font-size:20px;margin-bottom:4px">\ud83d\udcf1</div>Телефон</div></div><button class="btn" style="width:100%;margin-top:18px" onclick="saveSets()">Сохранить</button>');
    return;
  }

  if(type==='privacy'){
    if(!u.prv)u.prv={noGift:false,noMsg:false,noCh:false,excGift:[],excMsg:[],excCh:[]};
    var p=u.prv;
    var contacts=getContacts(u,d);
    mc.innerHTML=W('<h2><svg viewBox="0 0 24 24" width="20" height="20" style="fill:var(--ac)"><path d="M12 1L3 5v6c0 5.55 3.84 10.74 9 12 5.16-1.26 9-6.45 9-12V5l-9-4z"/></svg> Конфиденциальность <span class="x" onclick="clM()">\u2715</span></h2>'+
    '<div class="prv-row"><div><div class="prv-label">Запрет на подарки</div><div class="prv-sub">Никто не сможет подарить вам подарок</div></div><div class="prv-tog'+(p.noGift?' on':'')+'" onclick="togPrv(\'noGift\',this)"></div></div>'+
    '<div id="excGiftArea"'+(p.noGift?'':' class="hid"')+'><div style="font-size:12px;color:var(--tx2);margin:6px 0 4px">Исключения (могут дарить):</div><div id="excGiftList">'+renderExcList(p.excGift||[],d,'Gift')+'</div><div style="margin-top:4px"><select id="excGiftSel" style="padding:6px 10px;background:var(--inp);border:none;border-radius:6px;color:var(--tx);font-size:13px;width:100%"><option value="">+ Добавить исключение</option>'+contacts.filter(function(c){return(p.excGift||[]).indexOf(c)<0;}).map(function(c){var a=d.a.find(function(x){return x.u===c;});return'<option value="'+c+'">'+(a?a.nm:c)+' (@'+c+')</option>';}).join('')+'</select></div></div>'+
    '<div class="prv-row" style="margin-top:8px"><div><div class="prv-label">Запрет на сообщения</div><div class="prv-sub">Никто не сможет написать вам первым</div></div><div class="prv-tog'+(p.noMsg?' on':'')+'" onclick="togPrv(\'noMsg\',this)"></div></div>'+
    '<div id="excMsgArea"'+(p.noMsg?'':' class="hid"')+'><div style="font-size:12px;color:var(--tx2);margin:6px 0 4px">Исключения (могут писать):</div><div id="excMsgList">'+renderExcList(p.excMsg||[],d,'Msg')+'</div><div style="margin-top:4px"><select id="excMsgSel" style="padding:6px 10px;background:var(--inp);border:none;border-radius:6px;color:var(--tx);font-size:13px;width:100%"><option value="">+ Добавить исключение</option>'+contacts.filter(function(c){return(p.excMsg||[]).indexOf(c)<0;}).map(function(c){var a=d.a.find(function(x){return x.u===c;});return'<option value="'+c+'">'+(a?a.nm:c)+' (@'+c+')</option>';}).join('')+'</select></div></div>'+
    '<div class="prv-row" style="margin-top:8px"><div><div class="prv-label">Запрет на добавление в каналы</div><div class="prv-sub">Никто не сможет добавить вас в канал</div></div><div class="prv-tog'+(p.noCh?' on':'')+'" onclick="togPrv(\'noCh\',this)"></div></div>'+
    '<div id="excChArea"'+(p.noCh?'':' class="hid"')+'><div style="font-size:12px;color:var(--tx2);margin:6px 0 4px">Исключения (могут добавлять):</div><div id="excChList">'+renderExcList(p.excCh||[],d,'Ch')+'</div><div style="margin-top:4px"><select id="excChSel" style="padding:6px 10px;background:var(--inp);border:none;border-radius:6px;color:var(--tx);font-size:13px;width:100%"><option value="">+ Добавить исключение</option>'+contacts.filter(function(c){return(p.excCh||[]).indexOf(c)<0;}).map(function(c){var a=d.a.find(function(x){return x.u===c;});return'<option value="'+c+'">'+(a?a.nm:c)+' (@'+c+')</option>';}).join('')+'</select></div></div>'+
    '<button class="btn" style="width:100%;margin-top:18px" onclick="savePrv()">Сохранить</button>');
    // Bind selects
    setTimeout(function(){
      var gs=document.getElementById('excGiftSel');
      var ms=document.getElementById('excMsgSel');
      var cs=document.getElementById('excChSel');
      if(gs)gs.onchange=function(){if(this.value)addExc('Gift',this.value);};
      if(ms)ms.onchange=function(){if(this.value)addExc('Msg',this.value);};
      if(cs)cs.onchange=function(){if(this.value)addExc('Ch',this.value);};
    },50);
    return;
  }

  if(type==='rename'){
    mc.innerHTML=W('<h2>Переименовать <span class="x" onclick="clM()">\u2715</span></h2><label>Новое имя для @'+esc(ex)+'</label><input type="text" id="rnNm" value="'+esc(dname(ex))+'"><button class="btn" style="width:100%;margin-top:14px" onclick="doRename(\''+ex+'\')">Сохранить</button><button class="btn red" style="width:100%;margin-top:8px" onclick="doRenameClear(\''+ex+'\')">Сбросить</button>');
    return;
  }

  if(type==='gift'){
    tmpGift=null;
    // Check privacy
    if(!canGift(u.u,ex)&&u.u!==ex){
      mc.innerHTML=W('<h2>Подарить подарок <span class="x" onclick="clM()">\u2715</span></h2><div style="text-align:center;padding:30px"><div style="font-size:48px;margin-bottom:12px">\ud83d\udeab</div><div style="color:var(--tx2);font-size:15px">Этот пользователь запретил<br>получение подарков</div></div>');
      return;
    }
    mc.innerHTML=W('<h2>Подарить подарок <span class="x" onclick="clM()">\u2715</span></h2><div class="gc">'+GIFTS.map(function(g){return'<div class="gci" onclick="pickGift(\''+g.id+'\',this)"><div class="gci-i">'+g.icon+'</div><div class="gci-n">'+g.name+'</div></div>';}).join('')+'</div><label>Текст к подарку</label><input type="text" id="gTx" placeholder="Напишите что-нибудь..."><button class="btn" style="width:100%;margin-top:14px" onclick="sendGift(\''+ex+'\')">Подарить</button>');
    return;
  }

  if(type==='accounts'){
    mc.innerHTML=W('<h2>Аккаунты <span class="x" onclick="clM()">\u2715</span></h2>'+d.a.map(function(a){return'<div class="aci'+(a.u===u.u?' cur':'')+'\" onclick="switchAcc(\''+a.u+'\')">'+avHTML(a,42)+'<div style="flex:1"><div style="font-weight:500">'+esc(a.nm)+(isVf(a.u)?' <span class="vf">\u2714</span>':'')+'</div><div style="font-size:12px;color:var(--tx2)">@'+a.u+'</div></div>'+(a.u===u.u?'<span style="color:var(--ac);font-size:12px">текущий</span>':'')+'</div>';}).join('')+(d.a.length<3?'<button class="btn" style="width:100%;margin-top:14px" onclick="addAcc()">+ Добавить аккаунт</button>':'<div style="text-align:center;color:var(--tx2);margin-top:14px;font-size:13px">Максимум 3 аккаунта</div>'));
    return;
  }

  if(type==='newch'){
    var contacts=getContacts(u,d);
    mc.innerHTML=W('<h2>Создать канал <span class="x" onclick="clM()">\u2715</span></h2><label>Название</label><input type="text" id="chNm" placeholder="Мой канал"><label>Описание</label><textarea id="chDs" placeholder="О чём канал..."></textarea><label>Добавить участников</label><div style="max-height:160px;overflow-y:auto;margin-top:6px" id="chMb">'+contacts.map(function(c){var a=d.a.find(function(x){return x.u===c;});var blocked=!canAddCh(c);return'<label style="display:flex;align-items:center;gap:8px;padding:6px;cursor:'+(blocked?'default':'pointer')+';opacity:'+(blocked?'.4':'1')+'"><input type="checkbox" value="'+c+'"'+(blocked?' disabled':'')+' > '+(a?esc(a.nm):c)+' (@'+c+')'+(blocked?' <span style="font-size:11px;color:var(--rd);margin-left:4px">запрет</span>':'')+'</label>';}).join('')+(contacts.length?'':'<div style="color:var(--tx2);font-size:13px;padding:8px">Нет контактов. Найдите людей в поиске.</div>')+'</div><button class="btn" style="width:100%;margin-top:14px" onclick="mkCh()">Создать</button>');
    return;
  }

  if(type==='chinfo'){
    var c=d.ch[ex];if(!c)return;
    var members=[c.ow].concat(c.mb);
    mc.innerHTML=W('<h2>Информация <span class="x" onclick="clM()">\u2715</span></h2><div style="text-align:center"><div style="width:64px;height:64px;border-radius:50%;background:#a87bdb;display:flex;align-items:center;justify-content:center;margin:0 auto"><svg viewBox="0 0 24 24" width="30" height="30" fill="#fff"><path d="M20 2H4c-1.1 0-2 .9-2 2v18l4-4h14c1.1 0 2-.9 2-2V4c0-1.1-.9-2-2-2z"/></svg></div><div style="margin-top:10px;font-size:18px;font-weight:600">'+esc(c.nm)+'</div>'+(c.ds?'<div style="color:var(--tx2);font-size:13px;margin-top:6px">'+esc(c.ds)+'</div>':'')+'<div style="color:var(--tx2);font-size:12px;margin-top:6px">Создан: '+new Date(c.cr).toLocaleDateString('ru-RU')+'</div></div><div style="margin-top:16px"><div style="font-size:13px;color:var(--tx2);margin-bottom:8px">Участники ('+members.length+')</div>'+members.map(function(m){var a=d.a.find(function(x){return x.u===m;});return'<div style="display:flex;align-items:center;gap:10px;padding:6px 0">'+avHTML(a,36)+'<div><div style="font-weight:500;font-size:14px">'+esc(a?a.nm:m)+(isVf(m)?' <span class="vf">\u2714</span>':'')+'</div><div style="font-size:12px;color:var(--tx2)">@'+m+(m===c.ow?' \u00b7 владелец':'')+'</div></div></div>';}).join('')+'</div>');
    return;
  }

  if(type==='chadd'){
    var c=d.ch[ex];if(!c)return;
    var contacts=getContacts(u,d).filter(function(x){return c.mb.indexOf(x)<0&&x!==c.ow;});
    mc.innerHTML=W('<h2>Добавить участников <span class="x" onclick="clM()">\u2715</span></h2>'+(contacts.length?'<div id="addMb">'+contacts.map(function(cn){var a=d.a.find(function(x){return x.u===cn;});var blocked=!canAddCh(cn);return'<label style="display:flex;align-items:center;gap:8px;padding:6px;cursor:'+(blocked?'default':'pointer')+';opacity:'+(blocked?'.4':'1')+'"><input type="checkbox" value="'+cn+'"'+(blocked?' disabled':'')+' > '+(a?esc(a.nm):cn)+' (@'+cn+')'+(blocked?' <span style="font-size:11px;color:var(--rd);margin-left:4px">запрет</span>':'')+'</label>';}).join('')+'</div><button class="btn" style="width:100%;margin-top:14px" onclick="addToChannel(\''+ex+'\')">Добавить</button>':'<div style="text-align:center;color:var(--tx2);padding:20px">Все контакты уже в канале</div>'));
    return;
  }

  if(type==='chset'){
    var c=d.ch[ex];if(!c)return;
    mc.innerHTML=W('<h2>Настройки канала <span class="x" onclick="clM()">\u2715</span></h2><label>Название</label><input type="text" id="csNm" value="'+esc(c.nm)+'"><label>Описание</label><textarea id="csDs">'+esc(c.ds||'')+'</textarea><div style="margin-top:12px;font-size:13px;color:var(--tx2)">Участники: '+(c.mb.length+1)+'</div><button class="btn" style="width:100%;margin-top:14px" onclick="saveCh(\''+ex+'\')">Сохранить</button><button class="btn red" style="width:100%;margin-top:8px" onclick="delCh(\''+ex+'\')">Удалить канал</button>');
    return;
  }

  if(type==='admin'){
    if(u.u!=='surpa')return;
    mc.innerHTML=W('<h2><svg viewBox="0 0 24 24" width="20" height="20" style="fill:#f5a623"><path d="M12 1L3 5v6c0 5.55 3.84 10.74 9 12 5.16-1.26 9-6.45 9-12V5l-9-4z"/></svg> Админ панель <span class="x" onclick="clM()">\u2715</span></h2><div style="font-size:13px;color:var(--tx2);margin-bottom:12px">Все пользователи ('+d.a.length+')</div>'+d.a.map(function(a){
      var vf=isVf(a.u);
      return'<div class="adm-u">'+avHTML(a,38)+'<div style="flex:1"><div style="font-weight:500;font-size:14px">'+esc(a.nm)+(vf?' <span class="vf">\u2714</span>':'')+'</div><div style="font-size:12px;color:var(--tx2)">@'+a.u+'</div><div style="font-size:11px;color:#3d4d5c">Рег: '+new Date(a.cr).toLocaleDateString('ru-RU')+' \u00b7 '+(isOn(a.u)?'<span style="color:var(--gn)">\u25cf онлайн</span>':'оффлайн')+'</div></div>'+(a.u!=='surpa'?'<button class="vfb" onclick="toggleVf(\''+a.u+'\')">'+(vf?'Убрать \u2714':'Дать \u2714')+'</button>':'<span style="font-size:11px;color:var(--ac)">admin</span>')+'</div>';
    }).join(''));
    return;
  }
}

function clM(){
  var el=document.getElementById('mdlB');
  var mo=el.querySelector('.mo');
  if(mo){
    mo.style.opacity='0';mo.style.transition='opacity .2s';
    var md=mo.querySelector('.md');
    if(md){md.style.transform='scale(.95)';md.style.transition='transform .2s';}
    setTimeout(function(){el.innerHTML='';},200);
  } else {el.innerHTML='';}
}

function getContacts(u,d){
  var contacts=[];
  Object.keys(d.m).forEach(function(k){
    if(k.indexOf('|')<0||k.startsWith('sv|'))return;
    if(k.indexOf(u.u)>=0){var pp=k.split('|');var o=pp[0]===u.u?pp[1]:pp[0];if(o&&contacts.indexOf(o)<0)contacts.push(o);}
  });
  (d.sh[u.u]||[]).forEach(function(x){if(contacts.indexOf(x)<0)contacts.push(x);});
  return contacts;
}

function viewOtherGift(username,idx){
  var d=D(),acc=d.a.find(function(x){return x.u===username;});
  if(!acc)return;
  var visible=(acc.gifts||[]).filter(function(g){return!g.hd&&!g.sd;});
  var g=visible[idx];if(!g)return;
  var gd=GIFTS.find(function(x){return x.id===g.gi;});
  var from=d.a.find(function(x){return x.u===g.fr;});
  var mc=document.getElementById('mdlB');
  mc.innerHTML='<div class="mo" onclick="if(event.target===this)clM()"><div class="md"><h2>Подарок <span class="x" onclick="clM()">\u2715</span></h2><div style="text-align:center;padding:12px"><div style="font-size:72px;line-height:1;margin-bottom:12px">'+(gd?gd.icon:'\ud83c\udf81')+'</div><div style="font-size:20px;font-weight:600">'+(gd?gd.name:'Подарок')+'</div><div style="color:var(--tx2);margin-top:10px;font-size:14px">От: <span style="color:var(--ac)">@'+esc(g.fr)+'</span>'+(from?' ('+esc(from.nm)+')':'')+'</div>'+(g.tx?'<div style="color:var(--tx);margin-top:10px;font-style:italic;background:var(--inp);padding:10px 16px;border-radius:8px">"'+esc(g.tx)+'"</div>':'')+'<div style="color:#3d4d5c;margin-top:10px;font-size:12px">'+new Date(g.tm).toLocaleString('ru-RU')+'</div></div></div></div>';
}

// ===== PRIVACY =====
function renderExcList(list,d,type){
  if(!list||!list.length)return'<div style="font-size:12px;color:var(--tx2);padding:4px 0">Нет исключений</div>';
  return list.map(function(un){
    var a=d.a.find(function(x){return x.u===un;});
    return'<div class="exc-item">'+avHTML(a,24)+'<span>'+(a?esc(a.nm):un)+'</span><span style="font-size:11px;color:var(--tx2)">@'+un+'</span><span class="exc-rm" onclick="rmExc(\''+type+'\',\''+un+'\')">\u2715</span></div>';
  }).join('');
}

function togPrv(field,el){
  el.classList.toggle('on');
  var isOn=el.classList.contains('on');
  // Show/hide exception area
  var areaId;
  if(field==='noGift')areaId='excGiftArea';
  else if(field==='noMsg')areaId='excMsgArea';
  else areaId='excChArea';
  var area=document.getElementById(areaId);
  if(area){
    if(isOn)area.classList.remove('hid');
    else area.classList.add('hid');
  }
}

function addExc(type,username){
  var u=me(),d=D();
  var ai=d.a.findIndex(function(x){return x.u===u.u;});
  if(ai<0)return;
  if(!d.a[ai].prv)d.a[ai].prv={noGift:false,noMsg:false,noCh:false,excGift:[],excMsg:[],excCh:[]};
  var key='exc'+type;
  if(!d.a[ai].prv[key])d.a[ai].prv[key]=[];
  if(d.a[ai].prv[key].indexOf(username)<0){
    d.a[ai].prv[key].push(username);
    S(d);
    toast('@'+username+' добавлен в исключения');
    clM();
    setTimeout(function(){modal('privacy');},250);
  }
}

function rmExc(type,username){
  var u=me(),d=D();
  var ai=d.a.findIndex(function(x){return x.u===u.u;});
  if(ai<0)return;
  var key='exc'+type;
  if(d.a[ai].prv&&d.a[ai].prv[key]){
    var idx=d.a[ai].prv[key].indexOf(username);
    if(idx>=0)d.a[ai].prv[key].splice(idx,1);
    S(d);
    toast('@'+username+' удалён из исключений');
    clM();
    setTimeout(function(){modal('privacy');},250);
  }
}

function savePrv(){
  var u=me(),d=D();
  var ai=d.a.findIndex(function(x){return x.u===u.u;});
  if(ai<0)return;
  if(!d.a[ai].prv)d.a[ai].prv={};
  // Read toggles state
  var rows=document.querySelectorAll('.prv-tog');
  if(rows[0])d.a[ai].prv.noGift=rows[0].classList.contains('on');
  if(rows[1])d.a[ai].prv.noMsg=rows[1].classList.contains('on');
  if(rows[2])d.a[ai].prv.noCh=rows[2].classList.contains('on');
  S(d);
  clM();
  toast('Настройки конфиденциальности сохранены');
}

// Settings
function pickAv(id,el){tmpAv=id;document.querySelectorAll('.av-o').forEach(function(e){e.classList.remove('sel');});el.classList.add('sel');}
function pickTheme(t,el){theme=t;localStorage.setItem('supra_theme',t);applyTheme();document.querySelectorAll('.theme-btn').forEach(function(e){e.classList.remove('sel');});el.classList.add('sel');}
function pickIf(v,el){iface=v;localStorage.setItem('supra_iface',v);applyIface();document.querySelectorAll('.if-btn').forEach(function(e){e.classList.remove('sel');});el.classList.add('sel');}

function saveSets(){
  var nm=(document.getElementById('sNm').value||'').trim();
  var un=(document.getElementById('sUn').value||'').trim().toLowerCase();
  var bio=(document.getElementById('sBio').value||'').trim();
  if(!nm){toast('Введите имя');return;}
  if(!/^[a-z][a-z0-9_]{2,}$/.test(un)){toast('Username: англ, от 3 символов');return;}
  var u=me(),d=D();
  if(un!==u.u){
    if(d.a.find(function(x){return x.u===un;})){toast('Username занят');return;}
    var oldU=u.u;
    var newM={};
    Object.keys(d.m).forEach(function(k){
      var nk=k.replace(new RegExp(oldU.replace(/[.*+?^${}()|[\]\\]/g,'\\$&'),'g'),un);
      newM[nk]=d.m[k];
    });
    d.m=newM;
    Object.keys(d.m).forEach(function(k){
      (d.m[k]||[]).forEach(function(m){if(m.f===oldU)m.f=un;});
    });
    Object.keys(d.ch||{}).forEach(function(cid){
      var c=d.ch[cid];
      if(c.ow===oldU)c.ow=un;
      var mi=c.mb.indexOf(oldU);if(mi>=0)c.mb[mi]=un;
    });
    if(d.sh[oldU]){d.sh[un]=d.sh[oldU];delete d.sh[oldU];}
    d.a.forEach(function(a){
      if(a.gifts)a.gifts.forEach(function(g){if(g.fr===oldU)g.fr=un;});
      if(a.nk&&a.nk[oldU]){a.nk[un]=a.nk[oldU];delete a.nk[oldU];}
      // Update privacy exceptions
      if(a.prv){
        ['excGift','excMsg','excCh'].forEach(function(key){
          if(a.prv[key]){
            var idx=a.prv[key].indexOf(oldU);
            if(idx>=0)a.prv[key][idx]=un;
          }
        });
      }
    });
    if(d.vf&&d.vf[oldU]){d.vf[un]=true;delete d.vf[oldU];}
  }
  var o={nm:nm,u:un,bio:bio};if(tmpAv)o.av=tmpAv;
  var i=d.a.findIndex(function(x){return x.u===u.u||x.u===un;});
  if(i>=0)for(var k in o)d.a[i][k]=o[k];
  S(d);
  localStorage.setItem('supra_sid',un);
  tmpAv=null;clM();updDr();renderList();
  if(cur&&cur!=='saved'&&!cur.startsWith('ch:'))renderHead();
  toast('Настройки сохранены');
}

// Rename contact
function doRename(un){
  var nm=(document.getElementById('rnNm').value||'').trim();if(!nm)return;
  var d=D(),u=me(),i=d.a.findIndex(function(x){return x.u===u.u;});
  if(i>=0){if(!d.a[i].nk)d.a[i].nk={};d.a[i].nk[un]=nm;S(d);}
  clM();renderList();if(cur===un)renderHead();toast('Контакт переименован');
}
function doRenameClear(un){
  var d=D(),u=me(),i=d.a.findIndex(function(x){return x.u===u.u;});
  if(i>=0&&d.a[i].nk){delete d.a[i].nk[un];S(d);}
  clM();renderList();if(cur===un)renderHead();toast('Имя сброшено');
}

// Gifts
function pickGift(id,el){tmpGift=id;document.querySelectorAll('.gci').forEach(function(e){e.classList.remove('sel');});el.classList.add('sel');}
function sendGift(to){
  if(!tmpGift){toast('Выберите подарок');return;}
  var u=me(),d=D(),tx=(document.getElementById('gTx').value||'').trim();
  // Double-check privacy
  if(!canGift(u.u,to)&&u.u!==to){
    toast('Этот пользователь запретил подарки');
    clM();return;
  }
  var g=GIFTS.find(function(x){return x.id===tmpGift;});
  var ri=d.a.findIndex(function(x){return x.u===to;});
  if(ri>=0){if(!d.a[ri].gifts)d.a[ri].gifts=[];d.a[ri].gifts.push({gi:tmpGift,fr:u.u,tx:tx,tm:Date.now(),hd:false,sd:false});}
  var k=ck(u.u,to);if(!d.m[k])d.m[k]=[];
  d.m[k].push({f:u.u,tp:'gift',gi:tmpGift,gt:tx,tx:'\ud83c\udf81 '+u.nm+' подарил(а) подарок: '+(g?g.name:''),tm:Date.now(),rd:false,rx:{}});
  S(d);tmpGift=null;clM();renderMsgs();renderList();
  doConfetti(g);
  toast('Подарок отправлен!');
}
function togHide(i){var d=D(),u=me(),ai=d.a.findIndex(function(x){return x.u===u.u;});if(ai>=0&&d.a[ai].gifts[i]){d.a[ai].gifts[i].hd=!d.a[ai].gifts[i].hd;S(d);var s=d.a[ai].gifts[i].hd?'Подарок скрыт':'Подарок показан';toast(s);}clM();modal('profile');}
function sellG(i){if(!confirm('Продать подарок? Он исчезнет навсегда.'))return;var d=D(),u=me(),ai=d.a.findIndex(function(x){return x.u===u.u;});if(ai>=0&&d.a[ai].gifts[i]){d.a[ai].gifts[i].sd=true;S(d);toast('Подарок продан');}clM();modal('profile');}

// Admin
function toggleVf(un){
  var d=D();
  if(!d.vf)d.vf={};
  if(d.vf[un]){delete d.vf[un];toast('Галочка убрана у @'+un);}
  else{d.vf[un]=true;toast('Галочка выдана @'+un);}
  S(d);clM();modal('admin');
}

// Confetti
function doConfetti(g){
  var wrap=document.createElement('div');wrap.className='cfw';document.body.appendChild(wrap);
  var cols=g?g.colors:['#5288c1','#e17076','#7bc862','#f5a623','#fff'];
  for(var i=0;i<120;i++){
    var c=document.createElement('div');c.className='cf';
    c.style.background=cols[Math.floor(Math.random()*cols.length)];
    c.style.left=Math.random()*100+'vw';c.style.top='-14px';
    var s=5+Math.random()*10;c.style.width=s+'px';c.style.height=s+'px';
    c.style.borderRadius=Math.random()>.5?'50%':'2px';
    var dur=1500+Math.random()*3500,del=Math.random()*2500;
    c.animate([{transform:'translateY(0) rotate(0deg)',opacity:1},{transform:'translateY('+window.innerHeight+'px) rotate('+(300+Math.random()*500)+'deg)',opacity:0}],{duration:dur,delay:del,easing:'cubic-bezier(.25,.46,.45,.94)',fill:'forwards'});
    wrap.appendChild(c);
  }
  setTimeout(function(){wrap.remove();},7000);
}

// Channels
function mkCh(){
  var nm=(document.getElementById('chNm').value||'').trim();if(!nm){toast('Введите название');return;}
  var ds=(document.getElementById('chDs').value||'').trim();
  var u=me(),d=D(),mb=[];
  document.querySelectorAll('#chMb input:checked').forEach(function(e){mb.push(e.value);});
  var cid='c'+Date.now();if(!d.ch)d.ch={};
  d.ch[cid]={nm:nm,ds:ds,ow:u.u,mb:mb,ps:[],cr:Date.now()};
  S(d);clM();renderList();openCh(cid);toast('Канал "'+nm+'" создан');
}
function addToChannel(cid){
  var d=D(),c=d.ch[cid];if(!c)return;
  var added=0;
  document.querySelectorAll('#addMb input:checked').forEach(function(e){
    if(c.mb.indexOf(e.value)<0){c.mb.push(e.value);added++;}
  });
  S(d);clM();renderHead();toast('Добавлено: '+added);
}
function saveCh(cid){
  var d=D();
  d.ch[cid].nm=(document.getElementById('csNm').value||'').trim();
  d.ch[cid].ds=(document.getElementById('csDs').value||'').trim();
  S(d);clM();renderList();renderHead();toast('Канал обновлён');
}
function delCh(cid){
  if(!confirm('Удалить канал?'))return;
  var d=D();delete d.ch[cid];S(d);cur=null;clM();showEmpty();renderList();toast('Канал удалён');
}

// Accounts
function switchAcc(un){
  localStorage.setItem('supra_sid',un);cur=null;clM();showEmpty();updDr();renderList();
  toast('Переключено на @'+un);
}
function addAcc(){
  clM();cur=null;if(poll)clearInterval(poll);
  document.getElementById('app').classList.add('hid');
  document.getElementById('authScreen').classList.remove('hid');
  authMode=0;
  document.getElementById('regB').classList.remove('hid');
  document.getElementById('logB').classList.add('hid');
  document.getElementById('authBtn').textContent='Создать аккаунт';
  document.getElementById('authSub').textContent='Добавить новый аккаунт';
  var lk=document.getElementById('authLnk');
  lk.innerHTML='Уже есть аккаунт? <span id="authTog">Войти</span>';
  document.getElementById('authTog').onclick=togAuth;
  document.getElementById('authErr').textContent='';
  ['rNm','rUn','rPw'].forEach(function(id){var e=document.getElementById(id);if(e)e.value='';});
}
</script>
</body>
</html>

