<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>M TRADE ™ | Myanmar Streetwear</title>
<style>
body { margin:0; font-family:Poppins, Arial, sans-serif; background:#111; color:#fff; }
header { display:flex; justify-content:space-between; align-items:center; padding:15px; background:#000; }
header h1 { font-size:1.5rem; }
nav a { color:#fff; margin-left:15px; text-decoration:none; }
.container { padding:20px; }
.product { background:#222; padding:15px; margin-bottom:15px; border-radius:10px; }
.product img { width:100%; border-radius:10px; }
.product h3 { margin:10px 0 5px; }
.product p { margin:5px 0; }
.product button { padding:10px; background:#ff3; color:#000; border:none; border-radius:5px; cursor:pointer; }
.ad { margin:20px 0; background:#333; padding:20px; text-align:center; border-radius:10px; }
footer { padding:20px; text-align:center; background:#000; margin-top:20px; }
#cart { background:#222; padding:15px; border-radius:10px; margin-top:15px; }
button.checkout { background:#0f0; color:#000; padding:10px 15px; border:none; border-radius:5px; cursor:pointer; font-weight:bold; }
</style>
</head>
<body>

<header>
    <h1>M TRADE ™</h1>
    <nav>
        <a href="#home">Home</a>
        <a href="#products">Products</a>
        <a href="#content">Content</a>
        <a href="#checkout">Checkout</a>
    </nav>
</header>

<div class="container" id="home">
    <h2>Welcome to M TRADE Streetwear</h2>
    <p>Browse, shop, and pay securely while enjoying ad-supported content!</p>
</div>

<div class="container" id="products">
    <h2>Our Products</h2>

    <div class="product">
        <img src="assets/grow_tee.png" alt="Grow Oversized Tee">
        <h3>Grow Oversized Tee</h3>
        <p>Price: 15,000 MMK</p>
        <button onclick="addToCart('Grow Oversized Tee', 15000)">Add to Cart</button>
    </div>

    <div class="product">
        <img src="assets/street_cap.png" alt="Street Cap">
        <h3>Street Cap</h3>
        <p>Price: 8,000 MMK</p>
        <button onclick="addToCart('Street Cap', 8000)">Add to Cart</button>
    </div>

    <div id="cart"></div>
</div>

<div class="container ad">
    <!-- Ad Space: Replace with Google AdSense / PropellerAds -->
    <p>Ad Space – Revenue flows directly to your WavePay, hidden from users.</p>
</div>

<div class="container" id="content">
    <h2>Streetwear Tips & Viral Content</h2>
    <p>Check out the latest outfit inspiration, TikTok trends, and styling tips.</p>
</div>

<div class="container" id="checkout">
    <h2>Secure Checkout</h2>
    <p>Pay securely via WavePay – account details are hidden for safety.</p>
    <button class="checkout" onclick="checkout()">Pay Now</button>
</div>

<footer>
    <p>&copy; 2026 M TRADE ™ | Myanmar Streetwear</p>
</footer>

<script>
let cart = [];

function addToCart(name, price){
    let existing = cart.find(item => item.name === name);
    if(existing){ existing.qty += 1; } 
    else { cart.push({ name, price, qty: 1 }); }
    updateCartDisplay();
}

function updateCartDisplay(){
    let cartDiv = document.getElementById("cart");
    cartDiv.innerHTML = "";
    let total = 0;
    cart.forEach(item => {
        let itemTotal = item.price * item.qty;
        total += itemTotal;
        cartDiv.innerHTML += `<p>${item.name} x${item.qty} = ${itemTotal} MMK</p>`;
    });
    if(cart.length > 0){
        cartDiv.innerHTML += `<h3>Total: ${total} MMK</h3>`;
        cartDiv.innerHTML += `<button class="checkout" onclick="checkout()">Checkout via WavePay</button>`;
    }
}

function checkout(){
    let total = cart.reduce((sum, item) => sum + item.price * item.qty, 0);
    alert(`Your total is ${total} MMK. Payment is processed securely via WavePay.`);
    cart = [];
    updateCartDisplay();
}
</script>

</body>
</html>
