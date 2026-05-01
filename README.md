# Codsoft
<!DOCTYPE html>
<html>
<head>
    <title>E-Commerce Store</title>
    <style>
        body { font-family: Arial; margin: 20px; }
        .product { border: 1px solid #ccc; padding: 10px; margin: 10px; }
        button { padding: 5px 10px; }
        #cart { border-top: 2px solid black; margin-top: 20px; }
    </style>
</head>
<body>

<h1>🛒 Simple E-Commerce Store</h1>

<input type="text" id="search" placeholder="Search product..." onkeyup="filterProducts()">

<div id="products"></div>

<h2>🧾 Cart</h2>
<div id="cart"></div>
<h3 id="total"></h3>
<button onclick="checkout()">Checkout</button>

<script>
let products = [
    {id:1, name:"Shoes", price:1000},
    {id:2, name:"Shirt", price:500},
    {id:3, name:"Watch", price:1500},
    {id:4, name:"Bag", price:800}
];

let cart = [];

function displayProducts(list) {
    let html = "";
    list.forEach(p => {
        html += `
        <div class="product">
            <h3>${p.name}</h3>
            <p>₹${p.price}</p>
            <button onclick="addToCart(${p.id})">Add to Cart</button>
        </div>`;
    });
    document.getElementById("products").innerHTML = html;
}

function addToCart(id) {
    let product = products.find(p => p.id === id);
    cart.push(product);
    displayCart();
}

function displayCart() {
    let html = "";
    let total = 0;

    cart.forEach(item => {
        html += `<p>${item.name} - ₹${item.price}</p>`;
        total += item.price;
    });

    document.getElementById("cart").innerHTML = html;
    document.getElementById("total").innerText = "Total: ₹" + total;
}

function checkout() {
    alert("Order placed successfully!");
    cart = [];
    displayCart();
}

function filterProducts() {
    let search = document.getElementById("search").value.toLowerCase();
    let filtered = products.filter(p => p.name.toLowerCase().includes(search));
    displayProducts(filtered);
}

// Initial load
displayProducts(products);
</script>

</body>
</html>
