<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Neon Empire: Trap House</title>

<link href="https://fonts.googleapis.com/css2?family=Neon+Tubes&display=swap" rel="stylesheet" />

<style>
body {
  margin:0; padding:0;
  font-family:'Neon Tubes', cursive, Arial;
  background: radial-gradient(ellipse at bottom, #0f0 0%, #000 80%), #000;
  color:#0ff;
  overflow-x:hidden;
}

@keyframes pulse {
  0%,100% { text-shadow:0 0 10px #0ff,0 0 20px #0ff; }
  50% { text-shadow:0 0 20px #0ff,0 0 40px #0ff; }
}

#intro {
  position:fixed; inset:0;
  background:rgba(0,0,0,0.95);
  display:flex; flex-direction:column;
  justify-content:center; align-items:center;
  text-align:center; padding:20px;
  z-index:9999;
}

#intro h1 {
  font-size:3em;
  animation:pulse 2s infinite alternate;
}

.gate {
  max-width:700px;
  border:2px solid #0ff;
  border-radius:14px;
  padding:16px;
  background:#111;
  box-shadow:0 0 20px #0ff;
}

label { display:block; margin-top:10px; }
input {
  width:100%;
  padding:10px;
  border-radius:10px;
  border:none;
}

button {
  width:100%;
  margin-top:14px;
  padding:14px;
  font-size:1.2em;
  border-radius:12px;
  background:none;
  color:#0ff;
  border:3px solid #0ff;
  cursor:pointer;
}
button:hover {
  background:#0ff;
  color:#000;
}

#main { display:none; padding:20px; text-align:center; }

.neon-bg {
  height:250px;
  background:url('https://images.unsplash.com/photo-1578717870479-862009162911?auto=format&fit=crop&w=1350&q=80') center/cover;
  border-radius:15px;
  box-shadow:0 0 30px #0ff;
  cursor:pointer;
}

.doors {
  display:flex; flex-wrap:wrap; justify-content:center;
  margin-top:20px;
}
.door {
  width:140px; height:140px;
  margin:10px;
  border:3px solid #0ff;
  border-radius:15px;
  display:flex;
  justify-content:center;
  align-items:center;
  cursor:pointer;
  box-shadow:0 0 20px #0ff;
}

.section {
  display:none;
  max-width:700px;
  margin:20px auto;
  padding:20px;
  border-radius:15px;
  border:3px solid #0ff;
  background:#111;
}

.section.active { display:block; }

#nugg {
  position:fixed;
  width:70px; height:70px;
  background:#0ff;
  border-radius:50%;
  display:flex;
  justify-content:center;
  align-items:center;
  font-weight:bold;
  top:40px; left:40px;
  box-shadow:0 0 30px #0ff;
  cursor:pointer;
}
</style>
</head>

<body>

<div id="intro">
  <h1>🔥 Neon Empire 🔥</h1>
  <div class="gate">
    <label>Username</label>
    <input id="user">
    <label>Password</label>
    <input id="pass" type="password">
    <label>
      <input type="checkbox" id="age"> I am 18+/21+ (legal age)
    </label>
    <button onclick="enter()">Enter</button>
    <p style="font-size:0.8em;opacity:0.8">
      Demo login: <b>neonguest / letmein</b>
    </p>
  </div>
</div>

<div id="main">
  <h1>🔱 Neon Trap House 🔱</h1>
  <div class="neon-bg" onclick="showDoors()"></div>

  <div class="doors" id="doors" style="display:none"> 
    <div class="door" onclick="openRoom('vending')">Vending</div>
    <div class="door" onclick="openRoom('accessories')">Accessories</div>
    <div class="door" onclick="openRoom('puff')">Puff Puff</div>
  </div>

  <div id="vending" class="section">Vending Items Coming Soon</div>
  <div id="accessories" class="section">Accessories Only (Legal)</div>
  <div id="puff" class="section">Puff Puff Zone</div>
</div>

<div id="nugg">🤘</div>

<script>
const USER="neonguest", PASS="letmein";

function enter(){
  if(!age.checked) return alert("Confirm age");
  if(user.value!==USER||pass.value!==PASS)
    return alert("Wrong login");
  intro.style.display="none";
  main.style.display="block";
  bounce();
}

function showDoors(){ doors.style.display="flex"; }

function openRoom(id){
  document.querySelectorAll('.section').forEach(s=>s.classList.remove('active'));
  document.getElementById(id).classList.add('active');
}

function bounce(){
  setInterval(()=>{
    nugg.style.transform=`translate(${Math.random()*200}px,${Math.random()*200}px)`;
  },3000);
}
</script>

</body>
</html>