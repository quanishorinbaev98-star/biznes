<!DOCTYPE html>
<html lang="uz">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Quvonch Urinbayev — Biznes Maslahatchi</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet"/>
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
:root{
  --bg:#07090f;
  --bg2:#0c0f1a;
  --card:#10141f;
  --border:#1a2035;
  --blue:#00c6ff;
  --blue2:#0072ff;
  --purple:#7c3aed;
  --text:#eef2ff;
  --muted:#6b7a99;
  --white:#ffffff;
}
html{scroll-behavior:smooth}
body{background:var(--bg);color:var(--text);font-family:'DM Sans',sans-serif;overflow-x:hidden;line-height:1.6}

/* CANVAS */
#canvas-bg{position:fixed;top:0;left:0;width:100%;height:100%;z-index:0;pointer-events:none}

/* NAV */
nav{
  position:fixed;top:0;left:0;right:0;z-index:100;
  display:flex;align-items:center;justify-content:space-between;
  padding:16px 48px;
  background:rgba(7,9,15,0.7);
  backdrop-filter:blur(20px);
  border-bottom:1px solid rgba(0,198,255,0.08);
}
.nav-brand{
  font-family:'Syne',sans-serif;font-weight:800;font-size:1.05rem;
  background:linear-gradient(90deg,var(--blue),#a78bfa);
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
  letter-spacing:-0.01em;
}
.nav-links{display:flex;gap:28px;align-items:center}
.nav-links a{color:var(--muted);text-decoration:none;font-size:0.85rem;font-weight:500;transition:color .2s}
.nav-links a:hover{color:var(--blue)}
.nav-cta{
  background:linear-gradient(135deg,var(--blue2),var(--purple));
  color:#fff;font-size:0.8rem;font-weight:600;
  padding:8px 18px;border-radius:8px;text-decoration:none;
  transition:opacity .2s,transform .2s;
}
.nav-cta:hover{opacity:.85;transform:translateY(-1px)}

/* HERO */
.hero{
  position:relative;z-index:1;
  min-height:100vh;display:flex;flex-direction:column;
  align-items:center;justify-content:center;
  text-align:center;padding:120px 24px 80px;
}
.hero-badge{
  display:inline-flex;align-items:center;gap:8px;
  background:rgba(0,198,255,0.08);border:1px solid rgba(0,198,255,0.2);
  border-radius:100px;padding:6px 16px;margin-bottom:28px;
  font-size:0.75rem;font-weight:600;letter-spacing:.1em;text-transform:uppercase;
  color:var(--blue);
  opacity:0;animation:riseIn .7s .1s forwards;
}
.badge-dot{width:6px;height:6px;border-radius:50%;background:var(--blue);animation:blink 1.5s infinite}
.hero-name{
  font-family:'Syne',sans-serif;font-weight:800;
  font-size:clamp(1rem,.8rem + 2vw,1.1rem);
  color:var(--blue);letter-spacing:.25em;text-transform:uppercase;
  margin-bottom:12px;
  opacity:0;animation:riseIn .7s .25s forwards;
}
.hero-title{
  font-family:'Syne',sans-serif;font-weight:800;
  font-size:clamp(2.6rem,6.5vw,5rem);
  line-height:1.06;letter-spacing:-.035em;
  margin-bottom:20px;
  opacity:0;animation:riseIn .7s .4s forwards;
}
.hero-title .line2{
  background:linear-gradient(90deg,var(--blue),#818cf8,#c084fc);
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
}
.hero-sub{
  font-size:1.05rem;color:var(--muted);max-width:520px;margin:0 auto 36px;
  opacity:0;animation:riseIn .7s .55s forwards;
}
.hero-btns{
  display:flex;gap:12px;justify-content:center;flex-wrap:wrap;
  opacity:0;animation:riseIn .7s .7s forwards;
}
.btn-primary{
  background:linear-gradient(135deg,var(--blue2),var(--purple));
  color:#fff;font-weight:700;font-size:.9rem;
  padding:14px 28px;border-radius:10px;text-decoration:none;
  transition:transform .2s,box-shadow .2s;
  box-shadow:0 0 24px rgba(0,114,255,.3);
}
.btn-primary:hover{transform:translateY(-3px);box-shadow:0 8px 32px rgba(0,114,255,.4)}
.btn-ghost{
  background:transparent;border:1px solid rgba(0,198,255,.25);
  color:var(--blue);font-weight:600;font-size:.9rem;
  padding:14px 28px;border-radius:10px;text-decoration:none;
  transition:background .2s,transform .2s;
}
.btn-ghost:hover{background:rgba(0,198,255,.07);transform:translateY(-3px)}

.hero-cards{
  display:flex;gap:16px;margin-top:60px;flex-wrap:wrap;justify-content:center;
  opacity:0;animation:riseIn .7s .9s forwards;
}
.hcard{
  background:rgba(16,20,31,.8);border:1px solid var(--border);
  border-radius:14px;padding:20px 24px;min-width:140px;text-align:center;
  backdrop-filter:blur(10px);
}
.hcard-num{
  font-family:'Syne',sans-serif;font-weight:800;font-size:1.8rem;
  background:linear-gradient(135deg,var(--blue),#818cf8);
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
}
.hcard-label{font-size:.75rem;color:var(--muted);margin-top:4px}

/* SECTIONS */
.wrap{position:relative;z-index:1;max-width:1100px;margin:0 auto;padding:0 24px}
.sec{padding:90px 0;border-top:1px solid var(--border)}
.sec-tag{font-size:.7rem;font-weight:700;letter-spacing:.18em;text-transform:uppercase;color:var(--blue);margin-bottom:14px}
.sec-title{font-family:'Syne',sans-serif;font-weight:800;font-size:clamp(1.8rem,3.5vw,2.6rem);letter-spacing:-.025em;line-height:1.12;margin-bottom:12px}
.sec-desc{color:var(--muted);max-width:520px;font-size:.97rem}

/* STEPS TIMELINE */
.timeline{margin-top:56px;display:flex;flex-direction:column;gap:0}
.tl-item{
  display:grid;grid-template-columns:56px 1fr;gap:0;
  position:relative;
}
.tl-left{display:flex;flex-direction:column;align-items:center;padding-top:4px}
.tl-circle{
  width:40px;height:40px;border-radius:50%;
  background:linear-gradient(135deg,var(--blue2),var(--purple));
  display:flex;align-items:center;justify-content:center;
  font-family:'Syne',sans-serif;font-weight:800;font-size:.8rem;color:#fff;
  box-shadow:0 0 16px rgba(0,114,255,.35);flex-shrink:0;
  transition:transform .3s;z-index:1;
}
.tl-item:hover .tl-circle{transform:scale(1.12)}
.tl-line{flex:1;width:2px;background:linear-gradient(to bottom,rgba(0,198,255,.3),transparent);margin:6px 0}
.tl-item:last-child .tl-line{display:none}
.tl-right{padding:4px 0 40px 20px}
.tl-title{font-family:'Syne',sans-serif;font-weight:700;font-size:1.1rem;margin-bottom:6px}
.tl-desc{color:var(--muted);font-size:.9rem;line-height:1.7;max-width:560px}
.tl-tag{
  display:inline-block;margin-top:8px;
  background:rgba(0,198,255,.08);border:1px solid rgba(0,198,255,.15);
  color:var(--blue);font-size:.72rem;font-weight:600;
  padding:3px 10px;border-radius:20px;
}

/* GAME SECTION */
.game-sec{padding:90px 0;border-top:1px solid var(--border)}
.game-wrap{position:relative;z-index:1;max-width:1100px;margin:0 auto;padding:0 24px}
.game-box{
  margin-top:48px;background:var(--card);border:1px solid var(--border);
  border-radius:20px;overflow:hidden;
}
.game-header{
  padding:16px 24px;border-bottom:1px solid var(--border);
  display:flex;align-items:center;justify-content:space-between;
}
.game-title-row{display:flex;align-items:center;gap:10px}
.game-dot{width:8px;height:8px;border-radius:50%;background:var(--blue);animation:blink 1s infinite}
.game-label{font-family:'Syne',sans-serif;font-weight:700;font-size:.9rem}
.game-score-row{display:flex;gap:20px}
.gscore{text-align:right}
.gscore-num{font-family:'Syne',sans-serif;font-weight:800;font-size:1.1rem;color:var(--blue)}
.gscore-label{font-size:.7rem;color:var(--muted)}
#game-canvas{display:block;width:100%;height:320px;cursor:crosshair}
.game-footer{
  padding:14px 24px;border-top:1px solid var(--border);
  display:flex;align-items:center;justify-content:space-between;
  flex-wrap:wrap;gap:10px;
}
.game-inst{font-size:.8rem;color:var(--muted)}
#game-restart{
  background:linear-gradient(135deg,var(--blue2),var(--purple));
  color:#fff;border:none;border-radius:8px;
  font-family:'Syne',sans-serif;font-weight:700;font-size:.82rem;
  padding:8px 20px;cursor:pointer;transition:opacity .2s,transform .2s;
}
#game-restart:hover{opacity:.85;transform:translateY(-1px)}

/* MINDSET */
.mindset-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:16px;margin-top:52px}
.mcard{
  background:var(--card);border:1px solid var(--border);
  border-radius:14px;padding:28px;
  transition:border-color .25s,transform .25s;
  position:relative;overflow:hidden;
}
.mcard::before{
  content:'';position:absolute;top:0;left:0;right:0;height:2px;
  background:linear-gradient(90deg,var(--blue2),var(--purple));
  transform:scaleX(0);transform-origin:left;transition:transform .3s;
}
.mcard:hover{border-color:rgba(0,198,255,.25);transform:translateY(-4px)}
.mcard:hover::before{transform:scaleX(1)}
.mcard-icon{font-size:1.6rem;margin-bottom:14px}
.mcard-text{color:var(--muted);font-size:.9rem;line-height:1.75;font-style:italic;margin-bottom:14px}
.mcard-by{font-size:.78rem;color:var(--blue);font-weight:600}

/* AI CHAT */
.chat-outer{margin-top:48px}
.chat-box{
  background:var(--card);border:1px solid var(--border);
  border-radius:20px;overflow:hidden;
}
.chat-top{
  padding:16px 24px;border-bottom:1px solid var(--border);
  display:flex;align-items:center;gap:12px;
}
.chat-avatar{
  width:36px;height:36px;border-radius:10px;
  background:linear-gradient(135deg,var(--blue2),var(--purple));
  display:flex;align-items:center;justify-content:center;
  font-family:'Syne',sans-serif;font-weight:800;font-size:.8rem;color:#fff;
}
.chat-name{font-family:'Syne',sans-serif;font-weight:700;font-size:.9rem}
.chat-status{font-size:.72rem;color:var(--blue);display:flex;align-items:center;gap:5px}
.status-dot{width:5px;height:5px;border-radius:50%;background:var(--blue);animation:blink 1.5s infinite}
.chat-msgs{padding:24px;min-height:300px;max-height:400px;overflow-y:auto;display:flex;flex-direction:column;gap:14px}
.chat-msgs::-webkit-scrollbar{width:3px}
.chat-msgs::-webkit-scrollbar-thumb{background:var(--border);border-radius:3px}
.cmsg{display:flex;gap:10px;max-width:88%}
.cmsg.user{align-self:flex-end;flex-direction:row-reverse}
.cmsg-av{width:30px;height:30px;border-radius:8px;display:flex;align-items:center;justify-content:center;font-size:.7rem;font-weight:700;flex-shrink:0}
.cmsg.ai .cmsg-av{background:rgba(0,198,255,.1);color:var(--blue);border:1px solid rgba(0,198,255,.2)}
.cmsg.user .cmsg-av{background:rgba(124,58,237,.15);color:#a78bfa;border:1px solid rgba(124,58,237,.2)}
.cmsg-text{padding:10px 14px;border-radius:12px;font-size:.875rem;line-height:1.6}
.cmsg.ai .cmsg-text{background:#0c0f1a;border:1px solid var(--border);border-radius:4px 12px 12px 12px;color:var(--text)}
.cmsg.user .cmsg-text{background:linear-gradient(135deg,var(--blue2),var(--purple));color:#fff;border-radius:12px 4px 12px 12px}
.typing-dots{display:flex;gap:4px;align-items:center;padding:2px 0}
.typing-dots span{width:5px;height:5px;border-radius:50%;background:var(--blue);animation:bounce 1.1s infinite}
.typing-dots span:nth-child(2){animation-delay:.18s}
.typing-dots span:nth-child(3){animation-delay:.36s}
.chat-suggest{padding:0 24px 12px;display:flex;gap:8px;flex-wrap:wrap}
.sug{background:transparent;border:1px solid var(--border);color:var(--muted);font-size:.75rem;padding:6px 12px;border-radius:20px;cursor:pointer;transition:border-color .2s,color .2s;font-family:'DM Sans',sans-serif}
.sug:hover{border-color:var(--blue);color:var(--blue)}
.chat-inp-row{padding:14px 20px;border-top:1px solid var(--border);display:flex;gap:10px;align-items:flex-end}
#c-input{
  flex:1;background:#0c0f1a;border:1px solid var(--border);
  border-radius:10px;padding:11px 14px;color:var(--text);
  font-family:'DM Sans',sans-serif;font-size:.875rem;resize:none;
  outline:none;min-height:42px;max-height:110px;transition:border-color .2s;
}
#c-input:focus{border-color:rgba(0,198,255,.35)}
#c-input::placeholder{color:var(--muted)}
#c-send{
  background:linear-gradient(135deg,var(--blue2),var(--purple));
  border:none;border-radius:10px;width:42px;height:42px;
  cursor:pointer;display:flex;align-items:center;justify-content:center;
  flex-shrink:0;transition:opacity .2s,transform .15s;
}
#c-send:hover{opacity:.85}
#c-send:active{transform:scale(.93)}
#c-send:disabled{opacity:.35;cursor:not-allowed}
#c-send svg{width:16px;height:16px;fill:#fff}

/* CONTACT */
.contact-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:16px;margin-top:52px}
.contact-card{
  background:var(--card);border:1px solid var(--border);
  border-radius:16px;padding:28px;text-decoration:none;
  display:flex;flex-direction:column;gap:12px;
  transition:border-color .25s,transform .25s,box-shadow .25s;
  position:relative;overflow:hidden;
}
.contact-card::after{
  content:'';position:absolute;inset:0;
  background:linear-gradient(135deg,rgba(0,114,255,.04),rgba(124,58,237,.04));
  opacity:0;transition:opacity .25s;
}
.contact-card:hover{border-color:rgba(0,198,255,.3);transform:translateY(-5px);box-shadow:0 16px 40px rgba(0,0,0,.3)}
.contact-card:hover::after{opacity:1}
.contact-icon{font-size:2rem}
.contact-platform{font-family:'Syne',sans-serif;font-weight:700;font-size:1rem;color:var(--text)}
.contact-handle{color:var(--blue);font-size:.9rem;font-weight:500}
.contact-arrow{
  width:32px;height:32px;border-radius:8px;
  background:rgba(0,198,255,.08);border:1px solid rgba(0,198,255,.15);
  display:flex;align-items:center;justify-content:center;
  align-self:flex-end;margin-top:auto;transition:background .2s;
}
.contact-card:hover .contact-arrow{background:rgba(0,198,255,.15)}
.contact-arrow svg{width:14px;height:14px;stroke:var(--blue);fill:none;stroke-width:2.5}

/* FOOTER */
footer{
  position:relative;z-index:1;
  border-top:1px solid var(--border);
  padding:36px 24px;text-align:center;
  color:var(--muted);font-size:.82rem;
  max-width:1100px;margin:0 auto;
}
footer strong{color:var(--blue);font-weight:600}

/* ANIMATIONS */
@keyframes riseIn{from{opacity:0;transform:translateY(22px)}to{opacity:1;transform:translateY(0)}}
@keyframes blink{0%,100%{opacity:1}50%{opacity:.2}}
@keyframes bounce{0%,80%,100%{transform:translateY(0)}40%{transform:translateY(-7px)}}

/* SCROLL REVEAL */
.reveal{opacity:0;transform:translateY(28px);transition:opacity .6s,transform .6s}
.reveal.visible{opacity:1;transform:translateY(0)}

@media(max-width:768px){
  nav{padding:14px 20px}
  .nav-links{display:none}
  .mindset-grid,.contact-grid{grid-template-columns:1fr}
  .hero-cards{gap:10px}
  .hcard{min-width:120px;padding:16px}
}
</style>
</head>
<body>

<canvas id="canvas-bg"></canvas>

<nav>
  <div class="nav-brand">Q · Urinbayev</div>
  <div class="nav-links">
    <a href="#steps">Bosqichlar</a>
    <a href="#game">O'yin</a>
    <a href="#chat">Maslahat</a>
    <a href="#contact">Aloqa</a>
  </div>
  <a href="#contact" class="nav-cta">Bog'lanish</a>
</nav>

<!-- HERO -->
<div class="hero">
  <div class="hero-badge"><span class="badge-dot"></span>Biznes Maslahatchi · Toshkent</div>
  <div class="hero-name">Quvonch Urinbayev</div>
  <h1 class="hero-title">
    0 dan<br/><span class="line2">o'z biznesingni</span><br/>qur
  </h1>
  <p class="hero-sub">Pul yo'q. Tajriba yo'q. Aloqalar yo'q. Hech narsa bahona emas — faqat harakat kerak.</p>
  <div class="hero-btns">
    <a href="#steps" class="btn-primary">Bosqichlarni ko'r →</a>
    <a href="#contact" class="btn-ghost">Bog'lanish</a>
  </div>
  <div class="hero-cards">
    <div class="hcard"><div class="hcard-num">7</div><div class="hcard-label">Asosiy bosqich</div></div>
    <div class="hcard"><div class="hcard-num">$0</div><div class="hcard-label">Kapital kerak</div></div>
    <div class="hcard"><div class="hcard-num">∞</div><div class="hcard-label">Imkoniyat</div></div>
    <div class="hcard"><div class="hcard-num">24/7</div><div class="hcard-label">Online maslahat</div></div>
  </div>
</div>

<!-- STEPS -->
<div class="wrap" id="steps">
  <div class="sec reveal">
    <div class="sec-tag">Yo'l xaritasi</div>
    <h2 class="sec-title">7 bosqich — haqiqiy yo'l</h2>
    <p class="sec-desc">Nazariya emas. Har bir bosqich — shu bugun boshlasa bo'ladigan konkret harakat.</p>
    <div class="timeline">
      <div class="tl-item">
        <div class="tl-left"><div class="tl-circle">1</div><div class="tl-line"></div></div>
        <div class="tl-right"><div class="tl-title">🔍 Muammoni top</div><div class="tl-desc">Odamlarni bezovta qiladigan narsani toping. G'oya emas — muammoni echish soting. Har kuni 10 ta muammo yozing, eng katta biri — sizning biznesingiz.</div><span class="tl-tag">Bugundan boshlanadi</span></div>
      </div>
      <div class="tl-item">
        <div class="tl-left"><div class="tl-circle">2</div><div class="tl-line"></div></div>
        <div class="tl-right"><div class="tl-title">🎯 Kim uchun?</div><div class="tl-desc">Hammaga sotmoqchi bo'lsangiz — hech kimga sotmaysiz. Bir aniq guruhni tanlang: talabalar, onalar, tadbirkorlar. Ularni yaxshi tushunish — kuchingiz.</div><span class="tl-tag">1-3-kun</span></div>
      </div>
      <div class="tl-item">
        <div class="tl-left"><div class="tl-circle">3</div><div class="tl-line"></div></div>
        <div class="tl-right"><div class="tl-title">⚡ MVP — eng oddiy versiya</div><div class="tl-desc">Mukammal bo'lmasin — ishlaydigani bo'lsin. 30 kunda sotsa bo'ladigan narsa chiqaring. Keyin yaxshilaysiz. Hozir eng muhimi — bozorda bo'lish.</div><span class="tl-tag">1 oy ichida</span></div>
      </div>
      <div class="tl-item">
        <div class="tl-left"><div class="tl-circle">4</div><div class="tl-line"></div></div>
        <div class="tl-right"><div class="tl-title">💬 Birinchi mijoz</div><div class="tl-desc">Do'stlaringizga ayting. Telegram kanalga yozing. Instagram'da post qo'ying. Birinchi mijoz topish — eng qiyin. Lekin eng muhimi — u haqiqiy.</div><span class="tl-tag">Ijtimoiy tarmoq</span></div>
      </div>
      <div class="tl-item">
        <div class="tl-left"><div class="tl-circle">5</div><div class="tl-line"></div></div>
        <div class="tl-right"><div class="tl-title">💰 Birinchi to'lov</div><div class="tl-desc">Narx qo'yishdan qo'rqmang. Arzon narx sifatsizlik belgisi. Birinchi to'lov sizni "ishbilarmon" qiladi — bu his hamma narsani o'zgartiradi.</div><span class="tl-tag">Eng muhim an</span></div>
      </div>
      <div class="tl-item">
        <div class="tl-left"><div class="tl-circle">6</div><div class="tl-line"></div></div>
        <div class="tl-right"><div class="tl-title">📈 Tizim qur</div><div class="tl-desc">Hamma narsani o'zingiz qilmang. Nima avtomatlashtirilsa bo'ladi? Nima topshirilsa bo'ladi? Vaqtingiz — eng qimmat resurs. Uni tejang.</div><span class="tl-tag">Avtomasshtab</span></div>
      </div>
      <div class="tl-item">
        <div class="tl-left"><div class="tl-circle">7</div><div class="tl-line"></div></div>
        <div class="tl-right"><div class="tl-title">🚀 Miqyoslashtirish</div><div class="tl-desc">Endi kengayish vaqti. Yangi bozorlar, yangi mahsulotlar, jamoa. Faqat asoslar mustahkam bo'lganda. Shoshmasdan — lekin to'xtamasdan.</div><span class="tl-tag">Kelajak</span></div>
      </div>
    </div>
  </div>
</div>

<!-- GAME -->
<div class="game-sec" id="game">
  <div class="game-wrap reveal">
    <div class="sec-tag">Mini O'yin</div>
    <h2 class="sec-title">Bizneschi refleksi</h2>
    <p class="sec-desc">To'siqlarga urinmasdan imkoniyatlarga bosing! Har bir biznes imkoniyati — ball. Qanchalik tez qabul qilasiz?</p>
    <div class="game-box">
      <div class="game-header">
        <div class="game-title-row">
          <div class="game-dot"></div>
          <div class="game-label">Imkoniyat ovchisi</div>
        </div>
        <div class="game-score-row">
          <div class="gscore"><div class="gscore-num" id="g-score">0</div><div class="gscore-label">Ball</div></div>
          <div class="gscore"><div class="gscore-num" id="g-level">1</div><div class="gscore-label">Daraja</div></div>
          <div class="gscore"><div class="gscore-num" id="g-time">30</div><div class="gscore-label">Vaqt</div></div>
        </div>
      </div>
      <canvas id="game-canvas"></canvas>
      <div class="game-footer">
        <div class="game-inst">💡 <span style="color:var(--blue)">Yashil</span> imkoniyatlarga bosing · <span style="color:#f87171">Qizil</span> to'siqlarga tegmang</div>
        <button id="game-restart">Qayta boshlash</button>
      </div>
    </div>
  </div>
</div>

<!-- MINDSET -->
<div class="wrap">
  <div class="sec reveal">
    <div class="sec-tag">Tafakkur</div>
    <h2 class="sec-title">Fikrlash tarzi — hamma narsasi</h2>
    <p class="sec-desc">Muvaffaqiyatli tadbirkorlar boshqacha bilmaydi — ular boshqacha harakat qiladi.</p>
    <div class="mindset-grid">
      <div class="mcard">
        <div class="mcard-icon">⚡</div>
        <div class="mcard-text">"Muvaffaqiyatsizlik — yo'lning bir qismi, to'siq emas. Har bir 'yo'q' to'g'ri 'ha'ga yaqinlashtiradi."</div>
        <div class="mcard-by">Jeff Bezos printsipi</div>
      </div>
      <div class="mcard">
        <div class="mcard-icon">🔥</div>
        <div class="mcard-text">"Pul yo'qligi sabab emas — bahona. Kreativlik resurs yo'qligida eng ko'p ishlaydi."</div>
        <div class="mcard-by">Tadbirkorlik haqiqati</div>
      </div>
      <div class="mcard">
        <div class="mcard-icon">🎯</div>
        <div class="mcard-text">"Bugun ishlamagan ertaga ham ishlamaydi. Motivatsiya o'tib ketadi — intizom qoladi."</div>
        <div class="mcard-by">Jocko Willink printsipi</div>
      </div>
    </div>
  </div>
</div>

<!-- AI CHAT -->
<div class="wrap" id="chat">
  <div class="sec reveal">
    <div class="sec-tag">Bepul Maslahat</div>
    <h2 class="sec-title">Savol bering — javob oling</h2>
    <p class="sec-desc">Biznes g'oyangizni tahlil qiling, yo'nalish tanlang, savollaringizga javob oling.</p>
    <div class="chat-outer">
      <div class="chat-box">
        <div class="chat-top">
          <div class="chat-avatar">QU</div>
          <div>
            <div class="chat-name">Quvonch Urinbayev — AI Maslahat</div>
            <div class="chat-status"><span class="status-dot"></span>Hozir faol</div>
          </div>
        </div>
        <div class="chat-msgs" id="chat-messages">
          <div class="cmsg ai">
            <div class="cmsg-av">Q</div>
            <div class="cmsg-text">Salom! 👋 Biznes g'oyangiz bormi yoki qayerdan boshlashni bilmayapsizmi? Savolingizni yozing — men sizga haqiqiy, amaliy yo'l ko'rsataman. Hech qanday to'siq yo'q.</div>
          </div>
        </div>
        <div class="chat-suggest">
          <button class="sug" onclick="qs(this)">💡 Biznes g'oya bering</button>
          <button class="sug" onclick="qs(this)">💰 0 dan qanday boshlash?</button>
          <button class="sug" onclick="qs(this)">📱 Online biznes turlari</button>
          <button class="sug" onclick="qs(this)">🇺🇿 O'zbekistonda qanday biznes?</button>
        </div>
        <div class="chat-inp-row">
          <textarea id="c-input" placeholder="Savolingizni yozing..." rows="1"
            onkeydown="if(event.key==='Enter'&&!event.shiftKey){event.preventDefault();sendMsg()}"
            oninput="this.style.height='auto';this.style.height=this.scrollHeight+'px'"></textarea>
          <button id="c-send" onclick="sendMsg()">
            <svg viewBox="0 0 24 24"><path d="M22 2L11 13M22 2L15 22l-4-9-9-4 20-7z"/></svg>
          </button>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- CONTACT -->
<div class="wrap" id="contact">
  <div class="sec reveal">
    <div class="sec-tag">Aloqa</div>
    <h2 class="sec-title">Bog'laning</h2>
    <p class="sec-desc">Savol, taklif yoki hamkorlik uchun istalgan kanal orqali murojaat qiling.</p>
    <div class="contact-grid">
      <a href="https://t.me/urinbayev_q" target="_blank" class="contact-card">
        <div class="contact-icon">✈️</div>
        <div class="contact-platform">Telegram</div>
        <div class="contact-handle">@urinbayev_q</div>
        <div class="contact-arrow"><svg viewBox="0 0 24 24"><path d="M7 17L17 7M17 7H7M17 7v10"/></svg></div>
      </a>
      <a href="https://instagram.com/your.quvonc" target="_blank" class="contact-card">
        <div class="contact-icon">📸</div>
        <div class="contact-platform">Instagram</div>
        <div class="contact-handle">@your.quvonc</div>
        <div class="contact-arrow"><svg viewBox="0 0 24 24"><path d="M7 17L17 7M17 7H7M17 7v10"/></svg></div>
      </a>
      <a href="tel:+998940358281" class="contact-card">
        <div class="contact-icon">📞</div>
        <div class="contact-platform">Telefon</div>
        <div class="contact-handle">+998 94 035 82 81</div>
        <div class="contact-arrow"><svg viewBox="0 0 24 24"><path d="M7 17L17 7M17 7H7M17 7v10"/></svg></div>
      </a>
    </div>
  </div>
</div>

<footer>
  <p>© 2025 <strong>Quvonch Urinbayev</strong> · Toshkent, O'zbekiston · Barcha huquqlar himoyalangan</p>
</footer>

<script>
/* ── CANVAS BACKGROUND ── */
(function(){
  const cv=document.getElementById('canvas-bg');
  const ctx=cv.getContext('2d');
  let W,H,pts=[],mouse={x:-999,y:-999};
  const N=80;
  function resize(){W=cv.width=innerWidth;H=cv.height=innerHeight}
  resize();window.addEventListener('resize',resize);
  window.addEventListener('mousemove',e=>{mouse.x=e.clientX;mouse.y=e.clientY});
  for(let i=0;i<N;i++)pts.push({x:Math.random()*innerWidth,y:Math.random()*innerHeight,vx:(Math.random()-.5)*.4,vy:(Math.random()-.5)*.4,r:Math.random()*2+1});
  function draw(){
    ctx.clearRect(0,0,W,H);
    pts.forEach(p=>{
      p.x+=p.vx;p.y+=p.vy;
      if(p.x<0||p.x>W)p.vx*=-1;
      if(p.y<0||p.y>H)p.vy*=-1;
      const dm=Math.hypot(p.x-mouse.x,p.y-mouse.y);
      if(dm<120){p.x+=(p.x-mouse.x)*.02;p.y+=(p.y-mouse.y)*.02}
      ctx.beginPath();ctx.arc(p.x,p.y,p.r,0,Math.PI*2);
      ctx.fillStyle='rgba(0,198,255,.45)';ctx.fill();
    });
    for(let i=0;i<N;i++)for(let j=i+1;j<N;j++){
      const d=Math.hypot(pts[i].x-pts[j].x,pts[i].y-pts[j].y);
      if(d<110){
        ctx.beginPath();ctx.moveTo(pts[i].x,pts[i].y);ctx.lineTo(pts[j].x,pts[j].y);
        ctx.strokeStyle=`rgba(0,114,255,${.18*(1-d/110)})`;ctx.lineWidth=.6;ctx.stroke();
      }
    }
    requestAnimationFrame(draw);
  }
  draw();
})();

/* ── SCROLL REVEAL ── */
const obs=new IntersectionObserver(es=>es.forEach(e=>{if(e.isIntersecting)e.target.classList.add('visible')}),{threshold:.12});
document.querySelectorAll('.reveal').forEach(el=>obs.observe(el));

/* ── MINI GAME ── */
(function(){
  const cv=document.getElementById('game-canvas');
  const ctx=cv.getContext('2d');
  let W,H;
  function resize(){
    const r=cv.parentElement.getBoundingClientRect();
    W=cv.width=r.width;H=cv.height=320;
    cv.style.height='320px';
  }
  resize();window.addEventListener('resize',resize);

  let score=0,level=1,timeLeft=30,running=false,objects=[],timerID=null,rafID=null;

  const OBJ_TYPES=[
    {label:'💡',color:'#22c55e',pts:10,bad:false},
    {label:'📈',color:'#00c6ff',pts:15,bad:false},
    {label:'💰',color:'#f59e0b',pts:20,bad:false},
    {label:'🚧',color:'#ef4444',pts:-15,bad:true},
    {label:'❌',color:'#dc2626',pts:-20,bad:true},
  ];

  function spawnObj(){
    const t=OBJ_TYPES[Math.floor(Math.random()*OBJ_TYPES.length)];
    objects.push({x:Math.random()*(W-60)+30,y:Math.random()*(H-60)+30,r:24,vx:(Math.random()-.5)*(1+level*.4),vy:(Math.random()-.5)*(1+level*.4),...t,alpha:1,hit:false});
  }

  function startGame(){
    score=0;level=1;timeLeft=30;objects=[];running=true;
    document.getElementById('g-score').textContent=0;
    document.getElementById('g-level').textContent=1;
    document.getElementById('g-time').textContent=30;
    for(let i=0;i<6;i++)spawnObj();
    clearInterval(timerID);
    timerID=setInterval(()=>{
      if(!running)return;
      timeLeft--;
      document.getElementById('g-time').textContent=timeLeft;
      if(timeLeft<=0){running=false;clearInterval(timerID);showOver();}
      if(timeLeft%8===0&&timeLeft>0){level++;document.getElementById('g-level').textContent=level;spawnObj();spawnObj();}
    },1000);
    cancelAnimationFrame(rafID);
    loop();
  }

  function showOver(){
    ctx.clearRect(0,0,W,H);
    ctx.fillStyle='rgba(7,9,15,.85)';ctx.fillRect(0,0,W,H);
    ctx.textAlign='center';
    ctx.font='bold 28px Syne,sans-serif';
    const grad=ctx.createLinearGradient(W/2-80,0,W/2+80,0);
    grad.addColorStop(0,'#00c6ff');grad.addColorStop(1,'#7c3aed');
    ctx.fillStyle=grad;
    ctx.fillText('O\'yin tugadi!',W/2,H/2-30);
    ctx.font='500 18px DM Sans,sans-serif';ctx.fillStyle='#eef2ff';
    ctx.fillText('Natija: '+score+' ball',W/2,H/2+10);
    ctx.font='500 13px DM Sans,sans-serif';ctx.fillStyle='#6b7a99';
    ctx.fillText('Qayta boshlash uchun tugmani bosing',W/2,H/2+44);
  }

  function loop(){
    if(!running){return;}
    ctx.clearRect(0,0,W,H);
    objects.forEach(o=>{
      o.x+=o.vx;o.y+=o.vy;
      if(o.x-o.r<0||o.x+o.r>W)o.vx*=-1;
      if(o.y-o.r<0||o.y+o.r>H)o.vy*=-1;
      ctx.save();ctx.globalAlpha=o.alpha;
      ctx.beginPath();ctx.arc(o.x,o.y,o.r,0,Math.PI*2);
      ctx.fillStyle=o.color+'22';ctx.fill();
      ctx.strokeStyle=o.color;ctx.lineWidth=2;ctx.stroke();
      ctx.font=`${o.r}px serif`;ctx.textAlign='center';ctx.textBaseline='middle';
      ctx.fillStyle='#fff';ctx.fillText(o.label,o.x,o.y);
      ctx.restore();
    });
    rafID=requestAnimationFrame(loop);
  }

  function handleClick(e){
    if(!running)return;
    const rect=cv.getBoundingClientRect();
    const cx=(e.clientX||e.touches[0].clientX)-rect.left;
    const cy=(e.clientY||e.touches[0].clientY)-rect.top;
    objects.forEach(o=>{
      const d=Math.hypot(cx-o.x,cy-o.y);
      if(d<o.r+8){
        score+=o.pts;if(score<0)score=0;
        document.getElementById('g-score').textContent=score;
        o.x=Math.random()*(W-60)+30;
        o.y=Math.random()*(H-60)+30;
        showPop(cx,cy,o.pts,o.bad);
      }
    });
  }

  function showPop(x,y,pts,bad){
    const div=document.createElement('div');
    div.textContent=(bad?'':'+')+(pts>0?pts:pts);
    div.style.cssText=`position:fixed;left:${x}px;top:${y-20}px;font-family:Syne,sans-serif;font-weight:800;font-size:1.1rem;color:${bad?'#f87171':'#22c55e'};pointer-events:none;z-index:999;transition:transform .6s,opacity .6s;transform:translateY(0);opacity:1`;
    document.body.appendChild(div);
    setTimeout(()=>{div.style.transform='translateY(-40px)';div.style.opacity='0';},10);
    setTimeout(()=>div.remove(),700);
  }

  cv.addEventListener('click',handleClick);
  cv.addEventListener('touchstart',e=>{e.preventDefault();handleClick(e);},{passive:false});
  document.getElementById('game-restart').addEventListener('click',startGame);

  // Draw start screen
  ctx.textAlign='center';ctx.font='bold 22px Syne,sans-serif';
  const g=ctx.createLinearGradient(W/2-60,0,W/2+60,0);
  g.addColorStop(0,'#00c6ff');g.addColorStop(1,'#7c3aed');
  ctx.fillStyle=g;ctx.fillText('Boshlash uchun tugmani bosing',W/2,H/2);
})();

/* ── AI CHAT ── */
const SYS=`Sen Quvonch Urinbayev nomidan ishlaydigan biznes maslahatchi AI assistantisan. Foydalanuvchi O'zbekistondan.

Qoidalar:
- Faqat o'zbek tilida javob ber
- Qisqa, aniq, amaliy javoblar (180 so'zdan oshmasin)
- O'zbekiston bozorini hisobga ol
- Rag'batlantir, lekin haqiqiy bo'l
- Markdown ishlatma — oddiy matn
- Konkret, boshlasa bo'ladigan maslahat ber`;

const hist=[];

function appendM(role,txt){
  const w=document.getElementById('chat-messages');
  const d=document.createElement('div');
  d.className=`cmsg ${role==='user'?'user':'ai'}`;
  d.innerHTML=`<div class="cmsg-av">${role==='user'?'Sen':'Q'}</div><div class="cmsg-text">${txt.replace(/\n/g,'<br/>')}</div>`;
  w.appendChild(d);w.scrollTop=w.scrollHeight;
}
function showTyping(){
  const w=document.getElementById('chat-messages');
  const d=document.createElement('div');d.className='cmsg ai';d.id='typ';
  d.innerHTML=`<div class="cmsg-av">Q</div><div class="cmsg-text"><div class="typing-dots"><span></span><span></span><span></span></div></div>`;
  w.appendChild(d);w.scrollTop=w.scrollHeight;
}
function hideTyping(){const e=document.getElementById('typ');if(e)e.remove();}

async function sendMsg(){
  const inp=document.getElementById('c-input');
  const btn=document.getElementById('c-send');
  const txt=inp.value.trim();if(!txt)return;
  inp.value='';inp.style.height='auto';
  appendM('user',txt);hist.push({role:'user',content:txt});
  btn.disabled=true;showTyping();
  try{
    const r=await fetch('https://api.anthropic.com/v1/messages',{
      method:'POST',headers:{'Content-Type':'application/json'},
      body:JSON.stringify({model:'claude-sonnet-4-6',max_tokens:1000,system:SYS,messages:hist})
    });
    const d=await r.json();
    const rep=d.content?.map(b=>b.text||'').join('')||'Xatolik. Qayta urinib ko\'ring.';
    hideTyping();appendM('ai',rep);hist.push({role:'assistant',content:rep});
  }catch(e){hideTyping();appendM('ai','Tarmoq xatosi. Qayta urinib ko\'ring 🔄');}
  btn.disabled=false;
}
function qs(b){document.getElementById('c-input').value=b.textContent.slice(2).trim();sendMsg();}
</script>
</body>
</html>