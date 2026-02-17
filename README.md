<!DOCTYPE html>
<html lang="en" class="h-full">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Birthday Love Notebook</title>
<script src="https://cdn.tailwindcss.com/3.4.17"></script>
<link href="https://fonts.googleapis.com/css2?family=Patrick+Hand&family=Caveat:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
* { box-sizing: border-box; }
:root {
  --color-background: #FDF6E3;
  --color-surface: #FFFFFF;
  --color-text: #4A3728;
  --color-primary: #E87B7B;
  --color-secondary: #7BA3E8;
}

html, body { height: 100%; margin:0; padding:0; }
body {
  background: var(--color-background);
  font-family: 'Patrick Hand', cursive;
  color: var(--color-text);
}

.notebook-wrapper {
  width: 100%;
  min-height: 100%;
  background: var(--color-background);
  background-image: repeating-linear-gradient(
    transparent,
    transparent 32px,
    rgba(74,55,40,0.05) 32px,
    rgba(74,55,40,0.05) 34px
  );
  overflow-x: hidden;
  scroll-behavior: smooth;
}

.handwritten-title { font-family: 'Caveat', cursive; }
.handwritten-text { font-family: 'Patrick Hand', cursive; }

.photo-frame {
  background: var(--color-surface);
  padding: 8px 8px 24px 8px;
  box-shadow: 0 4px 6px rgba(0,0,0,0.1),
              0 2px 4px rgba(0,0,0,0.06),
              inset 0 0 40px rgba(0,0,0,0.03);
  position: relative;
}

.tape { position:absolute; width:60px; height:20px; background: rgba(255,248,220,0.7); box-shadow: 0 1px 2px rgba(0,0,0,0.1);}
.tape-top-left { top:-10px; left:10px; transform: rotate(-15deg); }
.tape-top-right { top:-10px; right:10px; transform: rotate(15deg); }

.section-reveal { opacity:0; transform: translateY(40px); transition: all 0.8s cubic-bezier(0.4,0,0.2,1);}
.section-reveal.visible { opacity:1; transform: translateY(0); }

.photo-reveal { opacity:0; transform: scale(0.8) rotate(var(--rotation,0deg)); transition: all 0.6s cubic-bezier(0.34,1.56,0.64,1);}
.photo-reveal.visible { opacity:1; transform: scale(1) rotate(var(--rotation,0deg)); }

.text-line { display:block; opacity:0; transform: translateX(-20px); transition: all 0.5s ease-out;}
.text-line.visible { opacity:1; transform: translateX(0); }

.placeholder-img {
  background: linear-gradient(135deg, var(--color-secondary) 0%, var(--color-primary) 100%);
  display:flex; align-items:center; justify-content:center;
  color:white; text-align:center; font-family:'Patrick Hand', cursive; font-size:14px;
  overflow:hidden;
}

.replay-btn { background: var(--color-primary); color:white; transition: all 0.3s ease; }
.replay-btn:hover { transform: scale(1.05); box-shadow: 0 4px 15px rgba(232,123,123,0.4); }

.overlay-heart {
  display:none; position:fixed; top:0; left:0; width:100%; height:100%;
  background: rgba(0,0,0,0.5); z-index:999; justify-content:center; align-items:center; flex-direction:column;
  color:white; font-family:'Caveat', cursive; font-weight:bold;
}
.overlay-heart .heart {
  font-size: 8rem; color: red; line-height:0.9;
  display:flex; justify-content:center; align-items:center; position:relative;
}
.overlay-heart .heart-text {
  position:absolute; font-size:2rem; text-align:center;
}
</style>
</head>
<body class="h-full">
<div class="notebook-wrapper" id="notebook">

<!-- Intro Section -->
<section class="min-h-screen flex flex-col items-center justify-center px-6 py-12 relative">
  <div class="section-reveal text-center max-w-2xl">
    <h1 class="handwritten-title text-5xl mb-4" id="intro-title">Happy Birthday, Sabrina!</h1>
    <p class="handwritten-text text-2xl opacity-80 mb-8" id="intro-subtitle">INSERT_SUBTITLE_HERE</p>
    <div class="photo-reveal relative" style="--rotation: -3deg;">
      <div class="photo-frame">
        <div class="tape tape-top-left"></div>
        <div class="tape tape-top-right"></div>
        <div class="placeholder-img w-64 h-64 md:w-80 md:h-80" id="intro-photo">
          Insert your GDrive link
        </div>
      </div>
    </div>
  </div>
</section>

<!-- Content Sections Container -->
<div id="sections-container"></div>

<!-- Final Heart Section -->
<section class="min-h-screen flex flex-col items-center justify-center px-6 py-12 relative">
  <button class="replay-btn mt-12 px-8 py-3 rounded-full handwritten-text text-xl" id="final-button">
    ♥ Let's Begin Your Celebration ♥
  </button>
</section>

</div>

<div class="overlay-heart" id="heart-overlay">
  <div class="heart">❤️
    <div class="heart-text">27th year<br>Strong baby girl</div>
  </div>
</div>

<script>
// =========================
// CONFIGURATION
// =========================
const birthdayContent = {
  intro: { title:"Happy Birthday, Sabrina!", subtitle:"Sabrina Hannah", image:"Insert your GDrive link" },
  sections:[
    { image:"Insert your GDrive link", text: [
      `Hey baby, happy 27th birthday. You’re getting older already yeah, but your heart still remains young and pure, and that’s something I will forever cherish deeply.`,
      `The smartest in whatever you do. The easiest to laugh at my jokes (but also the biggest killjoy sometimes just to stop me from exaggerating myself). The striking fancy outfits, the cute quirky face, the constant yapping and nagging whenever I make mistakes, and lastly, the prettiest smile that has been affectionating me all this while.`,
      `I will always remember the first time we started knowing each other. I was an introverted dick (I hope I’m not still now hehe). Little did I know, it would become the greatest gift I could have ever asked for in my life.`,
      `They say behind strength is consistency, and you are the most hardworking girl I’ve ever met. Your attention to detail, your respect for others, the way you show up as the best friend anyone could ask for, and the best partner I could ever receive.`
    ]},
    { image:"Insert your GDrive link", text:[
      `I just hope you don’t cry too much, because it pains me to see you that way. I promise I will continue working hard to make this work, and to do things right with you.`,
      `This will be the first and last birthday we celebrate before we enter our marriage, and I want you to know you are the best decision I have ever made.`,
      `I never regret loving you. Even though sometimes you ask me for justification, for a clear definition of why, I still can’t fully put it into words.`,
      `I hope you enjoy this small, last-minute birthday plan I prepared for you.`
    ]}
  ]
};

// =========================
// GENERATE SECTIONS
// =========================
function generateSections(){
  const container=document.getElementById('sections-container');
  birthdayContent.sections.forEach((section,index)=>{
    const rotation=(Math.random()*10-5).toFixed(1);
    let sectionHTML=`
      <section class="py-12 px-6 relative section-reveal">
        <div class="max-w-4xl mx-auto flex flex-col items-center gap-4">
          <div class="photo-reveal relative" style="--rotation:${rotation}deg;">
            <div class="photo-frame">
              <div class="tape tape-top-left"></div>
              <div class="tape tape-top-right"></div>
              <div class="placeholder-img w-64 h-64 md:w-80 md:h-80">${section.image}</div>
            </div>
          </div>
          <div class="handwritten-text text-xl mt-4 space-y-2">
            ${section.text.map(p=>`<p class="text-line">${p}</p>`).join('')}
          </div>
        </div>
      </section>
    `;
    container.innerHTML+=sectionHTML;
  });
}

// =========================
// SCROLL ANIMATION
// =========================
function initScrollAnimations(){
  const observer=new IntersectionObserver((entries)=>{
    entries.forEach(entry=>{
      if(entry.isIntersecting){
        entry.target.querySelectorAll('.section-reveal').forEach(el=>el.classList.add('visible'));
        setTimeout(()=>{entry.target.querySelectorAll('.photo-reveal').forEach(el=>el.classList.add('visible'))},200);
        setTimeout(()=>{entry.target.querySelectorAll('.text-line').forEach(el=>el.classList.add('visible'))},300);
      }
    });
  },{root:null,threshold:0.2});
  document.querySelectorAll('section').forEach(section=>observer.observe(section));
}

// =========================
// FINAL HEART BUTTON
// =========================
const finalButton=document.getElementById('final-button');
const heartOverlay=document.getElementById('heart-overlay');
let heartShown=false;
finalButton.addEventListener('click',()=>{
  if(!heartShown){
    heartOverlay.style.display='flex';
    heartShown=true;
  }else{
    heartOverlay.style.display='none';
    heartShown=false;
    document.getElementById('notebook').scrollTo({top:0,behavior:'smooth'});
    // reset animations
    document.querySelectorAll('.section-reveal,.photo-reveal,.text-line').forEach(el=>el.classList.remove('visible'));
    setTimeout(()=>{initScrollAnimations();},200);
  }
});

// =========================
// INIT
// =========================
document.addEventListener('DOMContentLoaded',()=>{
  document.getElementById('intro-title').textContent=birthdayContent.intro.title;
  document.getElementById('intro-subtitle').textContent=birthdayContent.intro.subtitle;
  document.getElementById('intro-photo').textContent=birthdayContent.intro.image;
  generateSections();
  setTimeout(()=>{initScrollAnimations();},100);
});
</script>
</body>
</html>
