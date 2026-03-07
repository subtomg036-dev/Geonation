<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Geonation</title>

<style>

html,body{
margin:0;
padding:0;
min-height:100vh;
font-family:Arial;
color:white;
text-align:center;

background:linear-gradient(270deg,#000000,#003d1f,#000000);
background-size:600% 600%;
animation:bgMove 12s ease infinite;
}

@keyframes bgMove{
0%{background-position:0% 50%;}
50%{background-position:100% 50%;}
100%{background-position:0% 50%;}
}

/* HEADER */

.header{
background:linear-gradient(#2faa3b,#0b6b25);
padding:90px 0 70px 0;
}

/* LOGO */

.logo{
font-size:90px;
font-weight:bold;
color:#00ff66;
text-shadow:0 0 10px #00ff66,0 0 40px #00ff66;
animation:logoGlow 2s infinite alternate;
}

@keyframes logoGlow{
from{text-shadow:0 0 10px #00ff66;}
to{text-shadow:0 0 60px #00ff66;}
}

/* STATUS */

.status{
margin-top:20px;
font-size:18px;
}

/* DOT */

.dot{
height:12px;
width:12px;
border-radius:50%;
display:inline-block;
margin-left:6px;
}

.green{background:#00ff00;}
.red{background:#ff0000;}

/* LOADING */

.loading::after{
content:"";
animation:dots 1s infinite;
}

@keyframes dots{
0%{content:"";}
33%{content:".";}
66%{content:"..";}
100%{content:"...";}
}

/* BUTTONS */

.top-right{
position:absolute;
top:20px;
right:20px;
}

.top-left{
position:absolute;
top:20px;
left:20px;
}

.btn{
padding:10px 20px;
border-radius:12px;
text-decoration:none;
color:white;
font-weight:bold;
margin-left:10px;
border:none;
cursor:pointer;
}

/* BUTTON COLORS */

.tiktok{
background:red;
box-shadow:0 0 10px red,0 0 20px red;
animation:redGlow 2s infinite alternate;
}

.discord{
background:#3b82f6;
box-shadow:0 0 10px #3b82f6,0 0 20px #3b82f6;
animation:blueGlow 2s infinite alternate;
}

.buy{
background:#00aa55;
box-shadow:0 0 10px #00ff88;
}

@keyframes redGlow{
from{box-shadow:0 0 5px red;}
to{box-shadow:0 0 25px red;}
}

@keyframes blueGlow{
from{box-shadow:0 0 5px #3b82f6;}
to{box-shadow:0 0 25px #3b82f6;}
}

/* BOX STYLE */

.box{
display:inline-block;
padding:30px;
margin:20px;
border-radius:20px;
background:#111;
box-shadow:0 0 10px #00ff66;
width:220px;
transition:0.3s;
}

.box:hover{
transform:scale(1.08);
box-shadow:0 0 25px #00ff66;
}

/* SHOP */

.shop{
display:none;
position:fixed;
top:0;
left:0;
width:100%;
height:100%;

background:linear-gradient(270deg,#000000,#003d1f,#000000);
background-size:600% 600%;
animation:bgMove 12s ease infinite;
}

.shop-content{
margin-top:150px;
}

.close{
position:absolute;
top:20px;
right:20px;
font-size:22px;
cursor:pointer;
}

/* RANK SECTION */

.ranks{
margin-top:120px;
padding-bottom:100px;
}

.rank-title{
font-size:40px;
margin-bottom:40px;
text-shadow:0 0 10px #00ff66;
}

.rank-price{
margin-top:10px;
color:#00ff88;
}

</style>
</head>

<body>

<div class="top-left">
<button class="btn buy" onclick="openShop()">Buy Keys</button>
</div>

<div class="top-right">
<a class="btn tiktok" href="https://www.tiktok.com/@mc_itzzmg" target="_blank">TikTok</a>
<a class="btn tiktok" href="https://www.tiktok.com/@mastrasss._" target="_blank">TikTok</a>
<a class="btn discord" href="https://discord.gg/mXTK57sF" target="_blank">Discord</a>
</div>

<div class="header">

<div class="logo">GEONATION</div>

<div class="status">
Server: <span id="serverStatus" class="loading">Checking</span>
<span id="dot" class="dot"></span>
</div>

<div class="status">
Players: <span id="players" class="loading">Checking</span>
</div>

</div>

<!-- SHOP -->

<div class="shop" id="shop">

<div class="close" onclick="closeShop()">✖</div>

<div class="shop-content">

<div class="box">
<h3>Amethyst Key</h3>
<p>3 GEL</p>
</div>

<div class="box">
<h3>Legendary Key</h3>
<p>2 GEL</p>
</div>

<div class="box">
<h3>Lite Key</h3>
<p>1 GEL</p>
</div>

</div>

</div>

<!-- RANKS -->

<div class="ranks">

<div class="rank-title">Server Ranks</div>

<div class="box">
<h3>💎 ADMIN</h3>
<p class="rank-price">2 GEL</p>
</div>

<div class="box">
<h3>⚔️ WARRIOR</h3>
<p class="rank-price">1 GEL</p>
</div>

<div class="box">
<h3>⚜️ ELITE</h3>
<p class="rank-price">1.5 GEL</p>
</div>

<div class="box">
<h3>🛡️ TITAN</h3>
<p class="rank-price">1 GEL</p>
</div>

<div class="box">
<h3>👤 MEMBER</h3>
<p class="rank-price">Free</p>
</div>

<div class="box">
<h3>🟣 MEDIA</h3>
<p class="rank-price">DM on Discord</p>
</div>

</div>

<script>

const serverIP="172.104.225.18";

setTimeout(checkServer,5000);

function checkServer(){

fetch(`https://api.mcsrvstat.us/2/${serverIP}`)
.then(res=>res.json())
.then(data=>{

const status=document.getElementById("serverStatus");
const players=document.getElementById("players");
const dot=document.getElementById("dot");

status.classList.remove("loading");
players.classList.remove("loading");

if(data.online){

status.innerText="Online";
dot.classList.add("green");

players.innerText=data.players.online+" / "+data.players.max;

}else{

status.innerText="Offline";
dot.classList.add("red");

players.innerText="0";

}

})

}

function openShop(){
document.getElementById("shop").style.display="block";
}

function closeShop(){
document.getElementById("shop").style.display="none";
}

</script>

</body>
</html>
