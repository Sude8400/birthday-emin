<!doctype html>
<html lang="tr">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>HAPPY BIRTHDAY EMİN YAMAN 🎈</title>
<style>
  :root{
    --bg1:#ff5f6d; /* kırmızı-pembe ton */
    --bg2:#ffc371; /* yumuşak sarı/pembe */
    --card:#fff;
    --accent:#ff4d6d;
    --glass: rgba(255,255,255,0.08);
  }
  html,body{height:100%;margin:0;font-family: "Segoe UI", Roboto, "Helvetica Neue", Arial;}
  body{
    background: linear-gradient(135deg,var(--bg1),#ff758c 40%,#ff9a9e 60%,var(--bg2));
    overflow:hidden;
    color:#222;
    -webkit-font-smoothing:antialiased;
    -moz-osx-font-smoothing:grayscale;
  }

  /* kalpli arka plan için layer */
  #hearts {
    position:fixed;inset:0;pointer-events:none;z-index:0;
  }

  /* Container */
  .wrap{
    position:relative;z-index:3;min-height:100vh;display:flex;align-items:center;justify-content:center;padding:40px;
  }
  .card{
    width:900px;max-width:96%;background:linear-gradient(180deg, rgba(255,255,255,0.12), rgba(255,255,255,0.06));
    border-radius:18px;padding:28px;box-shadow:0 10px 30px rgba(0,0,0,0.2);backdrop-filter: blur(6px);
    display:grid;grid-template-columns:1fr 430px;gap:20px;align-items:center;
  }

  /* left */
  .titleWrap{text-align:left;padding:10px;}
  h1{margin:0;font-size:48px;letter-spacing:1px;color:#fff;text-shadow:0 4px 18px rgba(0,0,0,0.35);}
  .sub{margin-top:14px;color:rgba(255,255,255,0.92);font-size:18px}

  /* right - visual */
  .visual{
    height:320px;display:flex;align-items:center;justify-content:center;position:relative;
  }

  /* balon alanı */
  .balloon{
    position:absolute;bottom:-40px;width:70px;height:110px;border-radius:40px 40px 40px 40px;transform-origin:center bottom;
    display:flex;align-items:flex-end;justify-content:center;box-shadow:0 8px 18px rgba(0,0,0,0.25);
  }
  .balloon::after{
    content:"";position:absolute;bottom:-12px;width:2px;height:28px;background:rgba(0,0,0,0.12);
  }

  /* buton */
  .btn{
    margin-top:20px;display:inline-block;padding:12px 18px;border-radius:12px;background:linear-gradient(90deg,#fff2,#ffffff45);border:1px solid rgba(255,255,255,0.12);
    cursor:pointer;font-weight:600;color:#fff;backdrop-filter: blur(4px);
  }

  /* modal/sürpriz sayfa */
  #surprise{
    position:fixed;inset:0;background:linear-gradient(180deg, rgba(0,0,0,0.35), rgba(0,0,0,0.45));display:none;align-items:center;justify-content:center;z-index:10;
  }
  .panel{
    width:900px;max-width:96%;background:linear-gradient(180deg,#ffffff, #fff0);padding:24px;border-radius:18px;box-shadow:0 14px 40px rgba(0,0,0,0.5);position:relative;overflow:hidden;
    display:grid;grid-template-columns:1fr 420px;gap:20px;align-items:center;
  }

  .surpriseText{font-size:28px;font-weight:700;color:#ff3660;}
  .cakeArea{display:flex;flex-direction:column;align-items:center;gap:12px;padding-top:10px}

  /* pasta (basit svg yerleştirme) */
  .cakeBox{width:340px;height:260px;display:flex;align-items:center;justify-content:center;position:relative}

  /* mumlar için sınıf */
  .candle{transition:opacity 700ms ease;}
  .muted{opacity:0.18}

  /* mikrofon butonu */
  .micBtn{padding:10px 14px;border-radius:999px;border:0;background:linear-gradient(90deg,#ff6b81,#ff2d55);color:white;cursor:pointer;font-weight:700;box-shadow:0 8px 20px rgba(255,80,110,0.24);}

  /* konfeti canvas */
  #confettiCanvas{position:fixed;left:0;top:0;width:100%;height:100%;pointer-events:none;z-index:9;display:none}

  /* açılış konfeti anim için */
  .hidden{display:none}

  /* küçük responsive */
  @media (max-width:920px){
    .card{grid-template-columns:1fr; padding:18px;}
    .visual{height:260px}
  }

  footer{position:fixed;left:12px;bottom:12px;color:rgba(255,255,255,0.65);font-size:13px;z-index:6}
</style>
</head>
<body>
  <div id="hearts"></div>

  <div class="wrap">
    <div class="card">
      <div class="titleWrap">
        <h1>HAPPY BIRTHDAY EMİN YAMAN 🎈</h1>
        <p class="sub">Bugün senin günün! Balonlar uçuyor, konfeti patlıyor — sürprizi açmak için butona tıkla.</p>
        <div style="margin-top:18px;">
          <button id="openSurprise" class="btn">Sürpriz için tıkla 🎁</button>
        </div>
      </div>

      <div class="visual" id="visual">
        <!-- balonlar JS ile eklenecek -->
      </div>
    </div>
  </div>

  <!-- Surprise modal / second page -->
  <div id="surprise" aria-hidden="true">
    <div class="panel">
      <div style="padding:10px;">
        <div class="surpriseText">DOĞUM GÜNÜN KUTLU OLSUUNN AŞKIIMMM :)) 💞</div>
        <p style="margin-top:14px;color:#333">Mikrofona üfle ve mumları söndür! 🎂</p>
        <div style="margin-top:24px;display:flex;gap:12px;align-items:center;">
          <button id="micBtn" class="micBtn">Mikrofonu Aç & Üfle</button>
          <button id="closeSurprise" class="btn" style="background:transparent;border:1px dashed rgba(0,0,0,0.08);">Kapat</button>
        </div>
        <div style="margin-top:20px;color:#666;font-size:13px">(Tarayıcı mikrofon izni isteyecektir. İzin verip, üfleme hareketini sesle yapın.)</div>
      </div>

      <div class="cakeArea" id="cakeArea">
        <div class="cakeBox" id="cakeBox">
          <!-- inline SVG cake -->
          <svg width="320" height="220" viewBox="0 0 320 220" fill="none" xmlns="http://www.w3.org/2000/svg">
            <!-- cake base -->
            <rect x="40" y="80" rx="18" ry="18" width="240" height="110" fill="#fff8f9" stroke="#ffd6e0" stroke-width="3"/>
            <rect x="60" y="40" rx="14" ry="14" width="200" height="70" fill="#ff5f79" stroke="#ff2d55" stroke-width="3"/>
            <!-- icing -->
            <path d="M60 70 Q 100 100 160 70 Q 220 40 260 70" fill="#fff" opacity="0.9"/>
            <!-- candles -->
            <g id="candles">
              <g transform="translate(110,20)">
                <rect x="-6" y="34" width="12" height="36" fill="#fffae6" stroke="#ffe08a" rx="3" class="candle"/>
                <path d="M0 28 Q2 22 0 18 Q-2 22 0 28 Z" fill="#ffdf5a"/>
                <circle cx="0" cy="14" r="6" fill="#ffb35c"/>
              </g>
              <g transform="translate(160,20)">
                <rect x="-6" y="34" width="12" height="36" fill="#fffae6" stroke="#ffe08a" rx="3" class="candle"/>
                <path d="M0 28 Q2 22 0 18 Q-2 22 0 28 Z" fill="#ffdf5a"/>
                <circle cx="0" cy="14" r="6" fill="#ffb35c"/>
              </g>
              <g transform="translate(135,20)">
                <rect x="-6" y="34" width="12" height="36" fill="#fffae6" stroke="#ffe08a" rx="3" class="candle"/>
                <path d="M0 28 Q2 22 0 18 Q-2 22 0 28 Z" fill="#ffdf5a"/>
                <circle cx="0" cy="14" r="6" fill="#ffb35c"/>
              </g>
            </g>
          </svg>
        </div>
        <div style="text-align:center">
          <div id="blowHint" style="color:#444;font-weight:600">Üfleme algılanmadı yet: —</div>
        </div>
      </div>
    </div>
  </div>

  <canvas id="confettiCanvas"></canvas>

  <footer>Bu sayfa senin için hazırlandı — paylaşmak için yayımla 🎉</footer>

<script>
/* -------------------------
   Helpers: random and ease
---------------------------*/
const rand = (a,b)=>(Math.random()*(b-a)+a)|0;

/* ---------- hearts background (floating hearts) ---------- */
const heartsLayer = document.getElementById('hearts');
function createHeart(x,y,size,delay,spd,opacity){
  const el = document.createElement('div');
  el.className='heart';
  Object.assign(el.style,{
    position:'absolute', left: x+'px', top: y+'px', width:size+'px', height:size+'px',
    transform:'translate(-50%,-50%) rotate(45deg)', background:'linear-gradient(45deg, rgba(255,255,255,0.18), rgba(255,255,255,0.06))',
    borderRadius:'12px', opacity:opacity, pointerEvents:'none', zIndex:1
  });
  // create heart shape via :before & :after using inner spans
  el.innerHTML = '<span style="position:absolute;left:0;top:0;width:100%;height:100%;"></span>';
  // style via CSS transform to look heart
  el.style.background = 'transparent';
  const s = size;
  const heartSVG = `<svg width="${s}" height="${s}" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg" style="filter:drop-shadow(0 6px 14px rgba(0,0,0,0.18));">
    <path d="M12 21s-8-5.33-8-10.5S8.5 2 12 7c3.5-5 8 1.5 8 3.5S20 15.67 12 21z" fill="rgba(255,255,255,0.14)"/>
    <path d="M12 21s-8-5.33-8-10.5S8.5 2 12 7c3.5-5 8 1.5 8 3.5S20 15.67 12 21z" fill="url(#g)"/>
    <defs><linearGradient id="g" x1="0" x2="1" y1="0" y2="1"><stop offset="0" stop-color="#ff7a89"/><stop offset="1" stop-color="#ff3b69"/></linearGradient></defs>
  </svg>`;
  el.innerHTML = heartSVG;
  heartsLayer.appendChild(el);
  // animation: floating down slowly and fade
  const start = Date.now()+delay;
  function anim(){
    const t = (Date.now()-start)/1000;
    if(t<0){requestAnimationFrame(anim);return;}
    el.style.transform = `translate(-50%,-${t*spd}px) rotate(${t*10}deg)`;
    el.style.opacity = Math.max(0, opacity - t*0.06);
    if(el.style.opacity>0) requestAnimationFrame(anim);
    else el.remove();
  }
  anim();
}
(function spawnHearts(){
  const w = innerWidth, h = innerHeight;
  for(let i=0;i<18;i++){
    createHeart(rand(0,w), rand(0,h+200), rand(18,46), rand(200,2000), rand(6,18)/1.2, Math.random()*0.7+0.12);
  }
  setInterval(()=>{ createHeart(rand(0,innerWidth), innerHeight+40, rand(18,46), 0, rand(6,18)/1.2, Math.random()*0.7+0.12); }, 1800);
})();

/* ---------------- balloons in the right visual ---------------- */
const visual = document.getElementById('visual');
const BAL_COLORS = ['#ff6b81', '#ff9aa2', '#ffd3b6', '#fcb3ff', '#ffd7e2', '#79f2ff', '#ffdf5b'];
function createBalloon(leftPct, color, delay, size){
  const b = document.createElement('div');
  b.className='balloon';
  b.style.left = leftPct+'%';
  b.style.width = size+'px';
  b.style.height = Math.round(size*1.45)+'px';
  b.style.background = `radial-gradient(circle at 30% 20%, rgba(255,255,255,0.6), rgba(255,255,255,0.06)), linear-gradient(180deg, ${color}, ${darken(color, -20)})`;
  b.style.transition='transform 0.3s';
  visual.appendChild(b);
  // float animation
  const startY = 50 + Math.random()*30;
  const dur = rand(8,20);
  function anim(s=0){
    b.animate([
      { transform:`translateY(0) scale(1)` },
      { transform:`translateY(-${400+Math.random()*200}px) scale(1.06)` }
    ], { duration: dur*1000, iterations:1, easing:'cubic-bezier(.2,.8,.2,1)', delay: delay*1000 + Math.random()*800 });
    setTimeout(()=>{ b.remove(); }, (delay+dur+0.6)*1000);
  }
  anim();
}

function darken(hex, amt){
  // hex like #rrggbb
  const c = hex.replace('#','');
  const r = Math.max(0, Math.min(255, parseInt(c.substring(0,2),16)+amt));
  const g = Math.max(0, Math.min(255, parseInt(c.substring(2,4),16)+amt));
  const b = Math.max(0, Math.min(255, parseInt(c.substring(4,6),16)+amt));
  return `rgb(${r},${g},${b})`;
}
(function spawnBalloons(){
  for(let i=0;i<7;i++){
    createBalloon(10 + i*12 + Math.random()*6, BAL_COLORS[i%BAL_COLORS.length], i*0.6, 64 + Math.random()*40);
  }
  // periodic spawn
  setInterval(()=>{ createBalloon(10 + Math.random()*80, BAL_COLORS[rand(0,BAL_COLORS.length-1)], 0, 48 + Math.random()*60); }, 2600);
})();


/* ---------------- open surprise & confetti ---------------- */
const openBtn = document.getElementById('openSurprise');
const surprise = document.getElementById('surprise');
const closeSurprise = document.getElementById('closeSurprise');
const confettiCanvas = document.getElementById('confettiCanvas');
const ctx = confettiCanvas.getContext('2d');

function sizeCanvas(){ confettiCanvas.width=innerWidth; confettiCanvas.height=innerHeight; }
sizeCanvas(); addEventListener('resize', sizeCanvas);

openBtn.addEventListener('click', ()=> {
  surprise.style.display='flex';
  confettiCanvas.style.display='block';
  runConfetti(120);
  playMelody(); // start music
});
closeSurprise.addEventListener('click', ()=> {
  surprise.style.display='none';
  confettiCanvas.style.display='none';
  stopMelody();
});

/* simple confetti particles */
let confetti = [];
function runConfetti(n){
  confetti = [];
  const colors = ['#ff3b69','#fff36b','#7af0ff','#ff9aa2','#ffd3b6'];
  for(let i=0;i<n;i++){
    confetti.push({
      x: Math.random()*confettiCanvas.width,
      y: Math.random()*confettiCanvas.height*0.2,
      vx: (Math.random()-0.5)*6,
      vy: Math.random()*3+2,
      r: Math.random()*8+6,
      color: colors[Math.floor(Math.random()*colors.length)],
      rot: Math.random()*360,
      speed: Math.random()*2+1
    });
  }
  (function frame(){
    ctx.clearRect(0,0,confettiCanvas.width,confettiCanvas.height);
    confetti.forEach((p)=> {
      p.x += p.vx; p.y += p.vy; p.vy += 0.06;
      p.rot += p.vx*0.6;
      ctx.save();
      ctx.translate(p.x,p.y);
      ctx.rotate(p.rot*Math.PI/180);
      ctx.fillStyle = p.color;
      ctx.fillRect(-p.r/2, -p.r/2, p.r, p.r*0.6);
      ctx.restore();
    });
    confetti = confetti.filter(p => p.y < confettiCanvas.height+50);
    if(confetti.length) requestAnimationFrame(frame);
    else { confettiCanvas.style.display='none'; ctx.clearRect(0,0,confettiCanvas.width,confettiCanvas.height); }
  })();
}

/* ----------------- melody via WebAudio (Happy Birthday synth) ----------------- */
let audioCtx=null, melodyGain=null, melodyOsc=null, playTimer=null;
const tempo = 1.0; // speed multiplier
// note frequency map (A4=440)
const notes = {
  'C4':261.63,'D4':293.66,'E4':329.63,'F4':349.23,'G4':392.00,'A4':440.00,'B4':493.88,
  'C5':523.25,'D5':587.33,'E5':659.25,'F5':698.46,'G5':783.99
};
// Happy Birthday notes sequence (simple)
const sequence = [
  ['G4',0.5],['G4',0.5],['A4',1.0],['G4',1.0],['C5',1.0],['B4',2.0],
  ['G4',0.5],['G4',0.5],['A4',1.0],['G4',1.0],['D5',1.0],['C5',2.0],
  ['G4',0.5],['G4',0.5],['G5',1.0],['E5',1.0],['C5',1.0],['B4',1.0],['A4',1.0],
  ['F5',0.5],['F5',0.5],['E5',1.0],['C5',1.0],['D5',1.0],['C5',2.0]
];

function startAudioContext(){
  if(!audioCtx){
    audioCtx = new (window.AudioContext || window.webkitAudioContext)();
    melodyGain = audioCtx.createGain();
    melodyGain.gain.value = 0.14;
    melodyGain.connect(audioCtx.destination);
  }
}
function playMelody(){
  startAudioContext();
  let t = audioCtx.currentTime + 0.2;
  sequence.forEach(note => {
    const [n,dur] = note;
    const osc = audioCtx.createOscillator();
    const g = audioCtx.createGain();
    osc.type = 'sine';
    osc.frequency.value = notes[n]||300;
    g.gain.value = 0;
    osc.connect(g); g.connect(melodyGain);
    osc.start(t);
    g.gain.linearRampToValueAtTime(0.14, t+0.01);
    g.gain.linearRampToValueAtTime(0.0, t+ dur*0.85 * tempo);
    osc.stop(t + dur * tempo + 0.02);
    t += dur * tempo;
  });
}

function stopMelody(){
  // we don't persist oscillator references; but new melody plays only on show. simply suspend audioCtx
  if(audioCtx) audioCtx.suspend && audioCtx.suspend();
}

/* ---------------- microphone blow detection ---------------- */
const micBtn = document.getElementById('micBtn');
const blowHint = document.getElementById('blowHint');
let micStream = null, analyser=null, dataArray=null, listening=false;
let candlesOut = false;

micBtn.addEventListener('click', async ()=>{
  if(!listening){ // start listening
    try{
      micStream = await navigator.mediaDevices.getUserMedia({ audio: true });
      startAudioContext();
      const src = audioCtx.createMediaStreamSource(micStream);
      analyser = audioCtx.createAnalyser();
      analyser.fftSize = 2048;
      src.connect(analyser);
      dataArray = new Uint8Array(analyser.fftSize);
      listening = true;
      micBtn.textContent = 'Mikrofon Açık — Üfle!';
      detectBlow();
    }catch(e){
      alert('Mikrofona erişilemedi. Lütfen tarayıcı izinlerini kontrol et.');
    }
  } else {
    stopMic();
  }
});

function stopMic(){
  if(micStream){
    micStream.getTracks().forEach(t=>t.stop());
    micStream=null;
  }
  listening=false;
  micBtn.textContent='Mikrofonu Aç & Üfle';
}

let blowCount = 0;
function detectBlow(){
  if(!analyser) return;
  analyser.getByteTimeDomainData(dataArray);
  // compute rms
  let sum=0;
  for(let i=0;i<dataArray.length;i++){
    const v = (dataArray[i]-128)/128;
    sum += v*v;
  }
  const rms = Math.sqrt(sum/dataArray.length);
  // console.log(rms);
  if(rms > 0.12){ // threshold for a blow/loud exhale
    blowHint.textContent = 'Üfleme algılandı! 🎉';
    blowCount++;
    if(blowCount >= 2 && !candlesOut){ // require 2 strong blows for sure
      extinguishCandles();
    }
  } else {
    blowHint.textContent = 'Üfleme algılanmadı yet: —';
  }
  // continue reading if still listening
  if(listening) requestAnimationFrame(detectBlow);
}

function extinguishCandles(){
  candlesOut = true;
  // fade candle flames (we simulate by fading .candle)
  document.querySelectorAll('.candle').forEach(c => c.classList.add('muted'));
  blowHint.textContent = 'Mumlar söndü! Mutlu yıllar! 🎂';
  // celebratory confetti burst
  runConfetti(200);
  // small particle smoke animation could be added
  // stop mic to be polite
  stopMic();
}

/* ----------------- Extra: open surprise reveals cake with small entrance animation ---------------- */
const cakeBox = document.getElementById('cakeBox');
openBtn.addEventListener('click', ()=> {
  cakeBox.animate([{ transform:'translateY(80px) scale(0.8)', opacity:0 }, { transform:'translateY(0) scale(1)', opacity:1 }], { duration:700, easing:'cubic-bezier(.2,.8,.2,1)' });
});

/* --------------- small note: clicking outside closes surprise --------------- */
surprise.addEventListener('click', (e)=> {
  if(e.target===surprise){ surprise.style.display='none'; stopMelody(); confettiCanvas.style.display='none'; }
});

/* --------------- initial small floating hearts & animated background spawn --------------- */
(function moreHearts(){
  // add gentle hearts occasionally to full screen
  setInterval(()=>{ createHeart(rand(0,innerWidth), innerHeight+40, rand(24,56), 0, rand(6,18)/1.2, Math.random()*0.7+0.14); }, 1400);
})();

/* Prevent autoplay audio issues: resume AudioContext on first user gesture */
window.addEventListener('click', function resumeAudio(){ if(audioCtx && audioCtx.state === 'suspended') audioCtx.resume(); }, { once:true });

/* That's it! Enjoy the page :) */
</script>
</body>
</html>
