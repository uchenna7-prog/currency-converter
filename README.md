# Currency Converter App

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Tesla-Style Resume Timeline — Uchendu Uchenna</title>
<style>
  *{box-sizing:border-box;margin:0;padding:0}
  body{
    font-family: 'Inter', sans-serif;
    background:#000;
    color:#fff;
    min-height:200vh;
    padding:40px 20px;
  }
  h1{text-align:center;font-weight:500;margin-bottom:60px;}
  .timeline{
    position:relative;
    max-width:700px;
    margin:0 auto;
    padding-left:40px;
  }

 
  .timeline::before{
    content:'';
    position:absolute;
    left:20px;
    top:0;
    width:2px;
    height:100%;
    background:#222;
  }

  
  .progress-line{
    position:absolute;
    left:20px;
    top:0;
    width:2px;
    height:0;
    background:#e82127;
    z-index:2;
  }

 
  .moving-dot{
    position:absolute;
    left:20px;
    width:14px;
    height:14px;
    background:#e82127;
    border-radius:50%;
    transform:translate(-50%,0);
    z-index:3;
  }


  .dot{
    position:absolute;
    left:20px;
    width:12px;
    height:12px;
    border:2px solid #e82127;
    border-radius:50%;
    background:#000;
    transform:translate(-50%,0);
    z-index:1;
    transition:background .3s;
  }

  .dot.filled{background:#e82127;}

  .item{
    position:relative;
    margin:120px 0;
    padding-left:60px;
  }
  .item h3{margin-bottom:6px;}
  .item .date{color:#999;font-size:0.9em;margin-bottom:10px;}
  .item p{color:#ccc;font-size:0.95em;line-height:1.6;}
</style>
</head>
<body>
<h1>Experience & Summary — Uchendu Uchenna</h1>

<section class="timeline" id="timeline">
  <div class="progress-line" id="progress"></div>
  <div class="moving-dot" id="moving"></div>

  <div class="dot" style="top:0px"></div>
  <div class="dot" style="top:260px"></div>
  <div class="dot" style="top:520px"></div>
  <div class="dot" style="top:780px"></div>
  <div class="dot" style="top:1040px"></div>

  <div class="item" style="top:-10px">
    <h3>Smart Home — Team Lead & Designer</h3>
    <div class="date">Feb 2025</div>
    <p>Led a 5-person team to build a smart home prototype; focused on hardware design, collaboration, and IoT integration.</p>
  </div>

  <div class="item" style="top:250px">
    <h3>Computer Science Student</h3>
    <div class="date">University of Port Harcourt</div>
    <p>Studying algorithms, AI, and hardware-software systems aiming to merge computer science with electrical engineering.</p>
  </div>

  <div class="item" style="top:510px">
    <h3>Python & Game Projects</h3>
    <div class="date">2024–2025</div>
    <p>Created Tetris, Snake, and DOOM-style 3D games using Python (Pygame/Tkinter) to sharpen algorithmic and creative skills.</p>
  </div>

  <div class="item" style="top:770px">
    <h3>Community Service</h3>
    <div class="date">Feb 2025</div>
    <p>Visited an infant orphanage to donate food and supplies, practicing leadership and empathy after competition participation.</p>
  </div>

  <div class="item" style="top:1030px">
    <h3>Career Goal — AI Engineer</h3>
    <div class="date">Ongoing</div>
    <p>Aiming to become an AI engineer and drive innovation in Nigeria’s tech ecosystem through research and startup creation.</p>
  </div>
</section>

<script>
const progress=document.getElementById('progress');
const moving=document.getElementById('moving');
const dots=document.querySelectorAll('.dot');
const timeline=document.getElementById('timeline');

window.addEventListener('scroll',()=>{
  const rect=timeline.getBoundingClientRect();
  const scrollY=window.scrollY+window.innerHeight/2;
  const start=timeline.offsetTop;
  const end=start+timeline.offsetHeight;
  const progressHeight=Math.min(Math.max(scrollY-start,0),timeline.offsetHeight);
  progress.style.height=progressHeight+'px';
  moving.style.top=progressHeight+'px';

  
  dots.forEach((dot,i)=>{
    const dotTop=timeline.offsetTop+parseFloat(dot.style.top);
    if(scrollY>dotTop){dot.classList.add('filled');}
    else{dot.classList.remove('filled');}
  });
});
</script>
</body>
</html>