<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Only For You</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
body{
  margin:0;
  font-family:'Segoe UI',sans-serif;
  background:linear-gradient(135deg,#0f2027,#203a43,#2c5364);
  color:white;
  text-align:center;
  overflow:hidden;
}

.page{
  min-height:100vh;
  display:flex;
  flex-direction:column;
  justify-content:center;
  align-items:center;
  padding:25px;
  animation:fadeIn 1.2s ease;
}

.hidden{display:none;}

h1{font-weight:500;}
p{opacity:0.9; line-height:1.5;}

input{
  margin-top:15px;
  padding:12px;
  width:90%;
  max-width:300px;
  border-radius:25px;
  border:none;
  text-align:center;
  font-size:16px;
}

button{
  margin-top:15px;
  padding:12px 30px;
  border:none;
  border-radius:25px;
  background:#ff4d6d;
  color:white;
  font-size:16px;
}

.hint{
  margin-top:12px;
  font-size:13px;
  opacity:0.75;
}

.shake{animation:shake 0.4s;}

@keyframes fadeIn{
  from{opacity:0; transform:translateY(20px);}
  to{opacity:1; transform:translateY(0);}
}

@keyframes shake{
  0%{transform:translateX(0);}
  25%{transform:translateX(-6px);}
  50%{transform:translateX(6px);}
  75%{transform:translateX(-6px);}
  100%{transform:translateX(0);}
}

.heart{
  position:fixed;
  bottom:-20px;
  font-size:18px;
  animation:float 6s linear infinite;
  opacity:0.7;
}

@keyframes float{
  from{transform:translateY(0);}
  to{transform:translateY(-110vh);}
}
</style>
</head>

<body>

<!-- PAGE 1 -->
<div class="page" id="p1">
  <h1>Hey… 🤍</h1>
  <p>This isn’t a message.<br>It’s a little walk.</p>
  <input id="pw1" placeholder="Enter the word">
  <button onclick="check(1)">Continue</button>
  <div class="hint">Hint: The name you hear when I smile alone</div>
</div>

<!-- PAGE 2 -->
<div class="page hidden" id="p2">
  <h1>You’re close 🌙</h1>
  <p>Some things don’t change,<br>even when we go quiet.</p>
  <input id="pw2" placeholder="Enter the word">
  <button onclick="check(2)">Continue</button>
  <div class="hint">Hint: What you call me when you’re soft</div>
</div>

<!-- PAGE 3 -->
<div class="page hidden" id="p3">
  <h1>Slow down 🤍</h1>
  <p>This one needs honesty.</p>
  <input id="pw3" placeholder="Enter the word">
  <button onclick="check(3)">Continue</button>
  <div class="hint">Hint: Where we felt safe without talking</div>
</div>

<!-- PAGE 4 -->
<div class="page hidden" id="p4">
  <h1>Almost there ✨</h1>
  <p>I didn’t plan this.<br>I just followed my heart.</p>
  <input id="pw4" placeholder="Enter the word">
  <button onclick="check(4)">Continue</button>
  <div class="hint">Hint: The place closest to the sky</div>
</div>

<!-- PAGE 5 -->
<div class="page hidden" id="p5">
  <h1>Look up 🌌</h1>
  <p>
    I’m not saying much.<br><br>
    <b>Come to the terrace.</b><br>
    I’m already here… waiting.
  </p>
  <p style="margin-top:20px;opacity:0.8;">
    — always your chazzi 🤍
  </p>
</div>

<script>
const passwords = {
  1: "pariii",        // CHANGE
  2: "chazzi",        // CHANGE
  3: "terrace",       // CHANGE
  4: "sky"            // CHANGE
};

function check(n){
  const input = document.getElementById("pw"+n).value.toLowerCase();
  const page = document.getElementById("p"+n);

  if(input === passwords[n]){
    page.classList.add("hidden");
    document.getElementById("p"+(n+1)).classList.remove("hidden");
    hearts();
    navigator.vibrate && navigator.vibrate([150,80,150]);
  }else{
    page.classList.add("shake");
    setTimeout(()=>page.classList.remove("shake"),400);
    navigator.vibrate && navigator.vibrate(200);
  }
}

function hearts(){
  for(let i=0;i<5;i++){
    const h=document.createElement("div");
    h.className="heart";
    h.innerText="🤍";
    h.style.left=Math.random()*100+"vw";
    document.body.appendChild(h);
    setTimeout(()=>h.remove(),6000);
  }
}
</script>

</body>
</html>
