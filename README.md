
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>OM JI Online Store</title>
<style>
*{box-sizing:border-box}
body{
 margin:0;
 font-family:Arial,sans-serif;
 background:#f5f5f5;
 color:#222;
}
header{
 background:#172554;
 color:white;
 padding:22px;
 text-align:center;
}
header h1{margin:0;font-size:32px}
nav{
 background:#1e3a8a;
 padding:13px;
 text-align:center;
}
nav a{
 color:white;
 text-decoration:none;
 margin:12px;
}
.hero{
 background:#facc15;
 text-align:center;
 padding:45px 15px;
}
.hero h2{font-size:30px}
.products{
 padding:25px 15px;
 text-align:center;
}
.grid{
 display:grid;
 grid-template-columns:repeat(auto-fit,minmax(180px,1fr));
 gap:18px;
 max-width:1000px;
 margin:auto;
}
.card{
 background:white;
 padding:15px;
 border-radius:12px;
 box-shadow:0 2px 8px #ddd;
}
.card img{
 width:100%;
 height:160px;
 object-fit:cover;
 border-radius:8px;
}
button{
 background:#16a34a;
 color:white;
 border:0;
 padding:11px 16px;
 border-radius:7px;
 cursor:pointer;
}
.cart{
 background:white;
 padding:20px;
 margin:20px auto;
 max-width:700px;
 border-radius:12px;
}
footer{
 background:#172554;
 color:white;
 text-align:center;
 padding:25px;
}
</style>
</head>
<body>

<header>
<h1>OM JI</h1>
<p>Welcome to Our Online Shopping Store</p>
</header>

<nav>
<a href="#home">Home</a>
<a href="#products">Products</a>
<a href="#cart">Cart</a>
<a href="#contact">Contact</a>
</nav>

<section class="hero" id="home">
<h2>Welcome to OM JI Store</h2>
<p>Best Products | Best Quality | Best Price</p>
<button onclick="document.getElementById('products').scrollIntoView()">
Shop Now
</button>
</section>

<section class="products" id="products">
<h2>Our Products</h2>
<div class="grid" id="productList"></div>
</section>

<section class="cart" id="cart">
<h2>🛒 Your Shopping Cart</h2>
<div id="cartItems">Your cart is empty.</div>
<h3 id="total">Total: ₹0</h3>
<button onclick="orderWhatsApp()">Order on WhatsApp</button>
</section>

<footer id="contact">
<h2>OM JI</h2>
<p>Thank you for shopping with us!</p>
<p>Contact: +91 XXXXXXXXXX</p>
<p>© 2026 OM JI Store</p>
</footer>

<script>
const products = [
 {name:"Product 1",price:499,image:"https://placehold.co/300x200?text=Product+1"},
 {name:"Product 2",price:799,image:"https://placehold.co/300x200?text=Product+2"},
 {name:"Product 3",price:999,image:"https://placehold.co/300x200?text=Product+3"},
 {name:"Product 4",price:299,image:"https://placehold.co/300x200?text=Product+4"}
];

let cart=[];

function showProducts(){
 document.getElementById("productList").innerHTML=
 products.map((p,i)=>`
 <div class="card">
 <img src="${p.image}" alt="${p.name}">
 <h3>${p.name}</h3>
 <h3>₹${p.price}</h3>
 <button onclick="addCart(${i})">Add to Cart</button>
 </div>`).join("");
}

function addCart(i){
 cart.push(products[i]);
 showCart();
}

function showCart(){
 let html="";
 let total=0;
 cart.forEach((p,i)=>{
 total+=p.price;
 html+=`<p>${p.name} - ₹${p.price}
 <button onclick="removeItem(${i})">Remove</button></p>`;
 });
 document.getElementById("cartItems").innerHTML=
 html||"Your cart is empty.";
 document.getElementById("total").innerText="Total: ₹"+total;
}

function removeItem(i){
 cart.splice(i,1);
 showCart();
}

function orderWhatsApp(){
 if(cart.length===0){
 alert("Please add products first!");
 return;
 }
 const phone="91XXXXXXXXXX";
 let message="Hello OM JI, I want to order:\n";
 let total=0;
 cart.forEach(p=>{
 message+=p.name+" - ₹"+p.price+"\n";
 total+=p.price;
 });
 message+="Total: ₹"+total;
 window.open("https://wa.me/"+phone+
 "?text="+encodeURIComponent(message),"_blank");
}

showProducts();
</script>

</body>
</html>
