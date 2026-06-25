# Asra
<!DOCTYPE html>
<html lang="fa">
<head>
<meta charset="UTF-8">
<title>💖 Romantic Game</title>

<!-- 🌸 فونت فارسی شیک -->
<link href="https://fonts.googleapis.com/css2?family=Vazirmatn:wght@300;400;600&display=swap" rel="stylesheet">

<style>
body{
    margin:0;
    font-family:'Vazirmatn', sans-serif;
    text-align:center;
    overflow:hidden;
    color:white;

    background: radial-gradient(circle at top, #3b0a45, #000);
}

/* 💖 قلب‌ها */
.heart{
    position:fixed;
    bottom:-20px;
    color:#ff4da6;
    font-size:18px;
    animation: floatUp 6s linear infinite;
}

@keyframes floatUp{
    0%{transform:translateY(0);opacity:0;}
    20%{opacity:1;}
    100%{transform:translateY(-110vh);opacity:0;}
}

.container{margin-top:60px;}

h1,h2{color:#ffb6c1;}

button{
    margin:6px;
    padding:10px 18px;
    border:none;
    border-radius:12px;
    background:#ff69b4;
    color:white;
    font-family:'Vazirmatn', sans-serif;
    cursor:pointer;
}

button:hover{background:#ff85c1;}

.step{display:none;}
#step1{display:block;}

#hint{
    color:#ffd1dc;
    min-height:20px;
}

#text{
    white-space:pre-line;
    margin-top:20px;
    color:#ffe6f0;
    font-size:17px;
    line-height:1.9;
}
</style>
</head>

<body>

<script>
function spawnHeart(){
    const h=document.createElement("div");
    h.className="heart";
    h.innerHTML="💖";
    h.style.left=Math.random()*100+"vw";
    h.style.fontSize=(15+Math.random()*25)+"px";
    h.style.animationDuration=(4+Math.random()*3)+"s";
    document.body.appendChild(h);
    setTimeout(()=>h.remove(),7000);
}
setInterval(spawnHeart,250);
</script>

<div class="container">

<!-- مرحله 1 -->
<div id="step1" class="step">
    <h1>🌷 اسم قشنگت رو انتخاب کن</h1>

    <button onclick="choose('Asra')">Asra 💎</button>
    <button onclick="choose('Sara')">Sara 🌸</button>
    <button onclick="choose('Negin')">Negin ✨</button>
</div>

<!-- مرحله 2 -->
<div id="step2" class="step">
    <h2 id="story"></h2>

    <p>💌 برای ادامه داستان جواب بده:</p>
    <p><b>7 + 5 = ؟</b></p>

    <button onclick="answer(10)">10</button>
    <button onclick="answer(12)">12</button>
    <button onclick="answer(13)">13</button>

    <p id="hint"></p>
</div>

<!-- مرحله 3 -->
<div id="step3" class="step">
    <h2>🌸 کمی صبر کن...</h2>
    <div id="text"></div>
</div>

<!-- مرحله 4 -->
<div id="step4" class="step">
    <h2>💖 روز دختر مبارک</h2>

    <p style="font-size:17px; line-height:2; color:#ffe6f0;">
        🌷 روز دختر مبارک Asra 🌷<br><br>

        بعضی اسم‌ها فقط اسم نیستند…<br>
        بعضی‌ها تبدیل میشن به یک حس، یک آرامش، یک دنیای قشنگ ✨<br><br>

        تو از اون آدم‌هایی هستی که حضورشون شبیه نور ملایم بعد از تاریکیه…<br>
        بی‌صدا، اما عمیق 💖<br><br>

        شاید این فقط یک بازی باشه…<br>
        ولی بعضی جمله‌ها حتی توی بازی هم واقعی به نظر میان 🌸<br><br>

        اگر دنیا یه داستان باشه، بعضی آدم‌ها نقش اصلی نیستند…<br>
        اما بدون اون‌ها داستان اصلاً معنی نداره ✨<br><br>

        روز دختر فقط یک اسم روی تقویم نیست…<br>
        یه بهونه‌ست برای یادآوری اینکه تو چقدر می‌تونی خاص باشی 💌<br><br>

        و تو، Asra…<br>
        از اون خاص‌ترین‌ها هستی 💖🌷
    </p>
</div>

</div>

<script>

let name="";
let tries=0;

function show(id){
    document.querySelectorAll(".step").forEach(s=>s.style.display="none");
    document.getElementById(id).style.display="block";
}

function choose(n){

    if(n !== "Asra"){
        alert("❌ فقط Asra رو انتخاب کن");
        return;
    }

    name=n;
    show("step2");

    document.getElementById("story").innerText=
    "💖 "+n+" انتخاب شد...";
}

function answer(a){
    tries++;

    if(a===12){
        show("step3");
        typeText();
    }else{
        document.getElementById("hint").innerText=
        "❌ اشتباهه... دوباره امتحان کن ("+(3-tries)+" فرصت)";
    }
}

function typeText(){

let t=
"💌 Asra...\n\n"+
"گاهی اسم‌ها فقط اسم نیستند...\n"+
"آن‌ها یک حس هستند 🌸\n\n"+
"روز دختر مبارک 💖";

let i=0;
let out=document.getElementById("text");
out.innerText="";

let interval=setInterval(()=>{

out.innerText=t.slice(0,i);
i++;

if(i>t.length){
clearInterval(interval);
setTimeout(()=>show("step4"),2500);
}

},40);

}

</script>

</body>
</html>
