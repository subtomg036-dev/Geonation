<!DOCTYPE html>
<html lang="ka">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Geonation Store</title>

<style>

*{margin:0;padding:0;box-sizing:border-box;font-family:sans-serif}

html{
scroll-behavior:smooth;
}

body{
background: radial-gradient(circle at top,#0b1a35,#02050d);
color:white;
overflow-x:hidden;
}

.navbar{
position:fixed;
top:20px;
left:50%;
transform:translateX(-50%);
width:80%;
display:flex;
justify-content:space-between;
align-items:center;
padding:15px 25px;
background:rgba(255,255,255,0.05);
backdrop-filter:blur(15px);
border-radius:20px;
border:1px solid rgba(255,255,255,0.1);
z-index:999;
}

.logo{
font-weight:bold;
font-size:20px;
background:linear-gradient(90deg,#00c3ff,#0077ff);
-webkit-background-clip:text;
color:transparent;
}

.links{
display:flex;
gap:25px;
}

.links a{
color:white;
text-decoration:none;
opacity:.7;
cursor:pointer;
}

.links a:hover{opacity:1}

.ip{
background:linear-gradient(90deg,#00c3ff,#0077ff);
padding:8px 15px;
border-radius:10px;
cursor:pointer;
}

.hero{
text-align:center;
padding-top:160px;
padding-bottom:80px;
}

.hero h1{
font-size:70px;
background:linear-gradient(90deg,#00c3ff,#0077ff);
-webkit-background-clip:text;
color:transparent;
}

.status{
margin-top:20px;
display:inline-block;
padding:10px 20px;
border-radius:20px;
background:rgba(0,191,255,0.1);
border:1px solid rgba(0,191,255,0.3);
}

.store{
display:flex;
justify-content:center;
flex-wrap:wrap;
gap:25px;
padding:40px;
}

.card{
width:240px;
padding:25px;
border-radius:20px;
background:rgba(255,255,255,0.05);
backdrop-filter:blur(10px);
border:1px solid rgba(255,255,255,0.1);
text-align:center;
transition:.3s;
}

.card:hover{
transform:translateY(-10px) scale(1.03);
box-shadow:0 0 25px rgba(0,191,255,0.4);
}

.card h2{color:#00c3ff;margin-bottom:10px;}
.price{margin-bottom:15px;font-size:20px;}
.buy{
background:linear-gradient(90deg,#00c3ff,#0077ff);
padding:10px;
border:none;
border-radius:10px;
cursor:pointer;
width:100%;
}

.section-title{
text-align:center;
font-size:32px;
margin-top:30px;
color:#00c3ff;
}

.op-items{
display:flex;
justify-content:center;
flex-wrap:wrap;
gap:25px;
padding:40px;
}

.circle{
position:fixed;
width:200px;
height:200px;
background:rgba(0,191,255,0.1);
border-radius:50%;
z-index:-1;
animation:float 10s infinite;
}

@keyframes float{
0%{transform:translateY(0)}
50%{transform:translateY(-50px)}
100%{transform:translateY(0)}
}

</style>
</head>

<body>

<div class="circle" style="top:20%;left:10%"></div>
<div class="circle" style="top:70%;left:80%"></div>

<div class="navbar">
<div class="logo">GEONATION</div>

<div class="links">
<a href="#">მთავარი</a>
<a href="#ranks">რანკები</a>
<a href="#items">ნივთები</a>
</div>

<div class="ip" onclick="copyIP()">Copy IP</div>
</div>

<section class="hero">
<h1>GEONATION</h1>
<p>ქართული Minecraft სერვერი</p>
<div class="status" id="status">იტვირთება...</div>
</section>

<!-- RANKS -->
<section class="store" id="ranks">
<div class="card"><h2>TITAN</h2><div class="price">1 GEL</div><button class="buy">ყიდვა</button></div>
<div class="card"><h2>WIZARD</h2><div class="price">3 GEL</div><button class="buy">ყიდვა</button></div>
<div class="card"><h2>ELITE</h2><div class="price">2.49 GEL</div><button class="buy">ყიდვა</button></div>
<div class="card"><h2>BOOSTER</h2><div class="price">3.99 GEL</div><button class="buy">ყიდვა</button></div>
<div class="card"><h2>VIP</h2><div class="price">5.49 GEL</div><button class="buy">ყიდვა</button></div>
</section>

<h2 class="section-title">Server OP Items</h2>

<!-- ITEMS -->
<section class="op-items" id="items">

<div class="card">
<h2>Amethyst Pickaxe</h2>
<div class="price">4.99 GEL</div>
<button class="buy">ყიდვა</button>
</div>

<div class="card">
<h2>Amethyst Axe</h2>
<div class="price">2.99 GEL</div>
<button class="buy">ყიდვა</button>
</div>

<div class="card">
<h2>$100k</h2>
<div class="price">0.99 GEL</div>
<button class="buy">ყიდვა</button>
</div>

<div class="card">
<h2>$1M</h2>
<div class="price">8.99 GEL</div>
<button class="buy">ყიდვა</button>
</div>

</section>

<script>
function copyIP(){
navigator.clipboard.writeText("geonation.fidelis.ge");
alert("IP დაკოპირდა!");
}

fetch("https://api.mcstatus.io/v2/status/java/geonation.fidelis.ge")
.then(res=>res.json())
.then(data=>{
document.getElementById("status").innerHTML =
data.online ? "🟢 Online: "+data.players.online+"/"+data.players.max : "🔴 Offline";
});
</script>

</body>
</html>
