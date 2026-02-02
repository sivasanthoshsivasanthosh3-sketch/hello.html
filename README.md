<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Do You Love Me 💖</title>

<style>
/* ================= RESET ================= */
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family: 'Poppins', Arial, sans-serif;
}

/* ================= BACKGROUND ================= */
body{
    height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    background:linear-gradient(270deg,#ff4d6d,#6a5cff,#00d4ff);
    background-size:600% 600%;
    animation:bgMove 12s ease infinite;
}

@keyframes bgMove{
    0%{background-position:0% 50%}
    50%{background-position:100% 50%}
    100%{background-position:0% 50%}
}

/* ================= CARD ================= */
.container{
    width:360px;
    height:560px;
    background:rgba(255,255,255,0.18);
    backdrop-filter:blur(14px);
    border-radius:25px;
    padding:25px;
    text-align:center;
    position:relative;
    overflow:hidden;
    box-shadow:0 20px 40px rgba(0,0,0,0.3);
}

/* ================= TITLE ================= */
h1{
    color:#fff;
    font-size:24px;
    margin-bottom:10px;
    text-shadow:0 0 10px rgba(255,255,255,0.5);
}

/* ================= EMOJI / IMAGE ================= */
.emoji{
    font-size:120px;
    margin:30px 0;
    transition:0.3s;
}

/* ================= BUTTON AREA ================= */
.buttons{
    position:relative;
    height:150px;
}

button{
    padding:12px 26px;
    font-size:16px;
    border:none;
    border-radius:30px;
    cursor:pointer;
    position:absolute;
    transition:0.2s;
}

/* YES BUTTON */
#yes{
    background:linear-gradient(135deg,#00ff9d,#00c9ff);
    color:#003;
    left:60px;
    bottom:20px;
    box-shadow:0 0 15px rgba(0,255,200,0.8);
    
}

/* NO BUTTON */
#no{
    background:linear-gradient(135deg,#ff4d4d,#ff0000);
    color:white;
    right:60px;
    bottom:20px;
    box-shadow:0 0 15px rgba(255,0,0,0.7);
}

/* ================= RESULT ================= */
.result{
    position:absolute;
    inset:0;
    background:linear-gradient(135deg,#ff9a9e,#fad0c4);
    display:none;
    flex-direction:column;
    justify-content:center;
    align-items:center;
}

.result h2{
    font-size:28px;
    color:#ff0055;
}

.hearts{
    position:absolute;
    inset:0;
    pointer-events:none;
}

.heart{
    position:absolute;
    font-size:20px;
    animation:float 4s linear infinite;
}

@keyframes float{
    from{transform:translateY(100%);opacity:1;}
    to{transform:translateY(-120%);opacity:0;}
}
</style>
</head>

<body>

<div class="container">

    <h1>Do you love me? 💖</h1>

    <div class="emoji" id="emoji">🥺</div>

    <div class="buttons">
        <button id="yes">Yes 💕</button>
        <button id="no">No 😏</button>
    </div>

    <!-- RESULT -->
    <div class="result" id="result">
         <img src="C:\Users\siva\Downloads\teddy 2.gif" alt="cute" height"300px" width="200px"/>
        <h2>I knew it 😍</h2>
        <div class="hearts" id="hearts"></div>
    </div>

</div>

<script>
const noBtn = document.getElementById("no");
const yesBtn = document.getElementById("yes");
const emoji = document.getElementById("emoji");
const result = document.getElementById("result");
const heartsBox = document.getElementById("hearts");

/* NO BUTTON ESCAPE + ANGER */
function moveNo(){
    const x = Math.random() * 220;
    const y = Math.random() * 100;

    noBtn.style.left = x + "px";
    noBtn.style.top = y + "px";

    emoji.innerText = "😡";
    setTimeout(()=> emoji.innerText="🥺", 600);
}

noBtn.addEventListener("mouseover", moveNo);
noBtn.addEventListener("click", moveNo);

/* YES BUTTON ACTION */
yesBtn.addEventListener("click", ()=>{
    result.style.display = "flex";
    createHearts();
});

/* HEART GENERATOR */
function createHearts(){
    for(let i=0;i<30;i++){
        const heart = document.createElement("div");
        heart.className="heart";
        heart.innerText="❤️";
        heart.style.left=Math.random()*100+"%";
        heart.style.animationDuration=(2+Math.random()*3)+"s";
        heartsBox.appendChild(heart);

        setTimeout(()=>heart.remove(),4000);
    }
}
</script>

</body>
</html>
