<!DOCTYPE html><html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Elite Game Top-Up</title>
<style>
body {margin:0;font-family:Arial;background:#020617;color:white;}
header {background:#020617;padding:15px;text-align:center;}
h1 {color:#22c55e;}
.container {padding:20px;}
.card {background:#0f172a;margin:15px auto;padding:20px;width:90%;border-radius:15px;box-shadow:0 0 15px rgba(0,0,0,0.7);} 
input, select {padding:10px;margin:10px;width:85%;border-radius:8px;border:none;}
button {padding:12px 20px;background:#22c55e;border:none;border-radius:10px;font-weight:bold;cursor:pointer;}
.admin {background:#111827;padding:15px;margin-top:20px;border-radius:10px;}
</style>
</head>
<body><header>
<h1>🎮 Elite Top-Up Store</h1>
<p>Instant & Secure Gaming Top-Ups</p>
</header><div class="container"><div class="card">
<h2>🛒 Place Order</h2>
<select id="game">
<option>Free Fire</option>
<option>PUBG Mobile</option>
<option>Call of Duty</option>
</select><select id="package">
<option>100 UC / Diamonds - Rs 300</option>
<option>300 UC / Diamonds - Rs 800</option>
<option>500 UC / Diamonds - Rs 1300</option>
</select><input type="text" id="playerId" placeholder="Enter Player ID"><select id="payment">
<option>EasyPaisa</option>
<option>JazzCash</option>
</select><input type="file" id="screenshot"><br>
<button onclick="placeOrder()">🚀 Submit Order</button>
</div><div class="card">
<h2>📊 Order Status</h2>
<p id="status">No orders yet</p>
</div><div class="card admin">
<h2>🔐 Admin Panel</h2>
<input type="password" id="adminPass" placeholder="Enter Admin Password">
<button onclick="loginAdmin()">Login</button><div id="adminArea" style="display:none;">
<h3>Orders</h3>
<ul id="ordersList"></ul>
</div>
</div></div><script>
let orders = [];

function placeOrder(){
  let game = document.getElementById('game').value;
  let pack = document.getElementById('package').value;
  let id = document.getElementById('playerId').value;
  let pay = document.getElementById('payment').value;

  if(id === ""){
    alert("Enter Player ID");
    return;
  }

  let order = {game, pack, id, pay};
  orders.push(order);

  document.getElementById('status').innerText = "Order Submitted! Contact on WhatsApp.";

  let message = `*New Order*%0A🎮 ${game}%0A📦 ${pack}%0A🆔 ${id}%0A💳 ${pay}`;
  window.open(`https://wa.me/923701048016?text=${message}`, '_blank');
}

function loginAdmin(){
  let pass = document.getElementById('adminPass').value;
  if(pass === "admin123"){
    document.getElementById('adminArea').style.display = 'block';
    showOrders();
  } else {
    alert("Wrong Password");
  }
}

function showOrders(){
  let list = document.getElementById('ordersList');
  list.innerHTML = "";
  orders.forEach((o,i)=>{
    let li = document.createElement('li');
    li.innerText = `${i+1}. ${o.game} | ${o.pack} | ${o.id}`;
    list.appendChild(li);
  });
}
</script></body>
</html>
