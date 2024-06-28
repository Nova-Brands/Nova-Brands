<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nova Brands - Your One-Stop Shop for Fashion and Tech!</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f9f9f9;
            color: #333;
        }

        header {
            background-color: #ff6347;
            color: white;
            padding: 1rem 0;
            text-align: center;
        }

        nav ul {
            list-style: none;
            padding: 0;
            text-align: center;
            margin: 0;
            background-color: #ffa07a;
        }

        nav ul li {
            display: inline;
            margin: 0 1rem;
        }

        nav ul li a {
            color: white;
            text-decoration: none;
            font-weight: bold;
        }

        section {
            padding: 2rem;
            margin: 2rem auto;
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            max-width: 800px;
        }

        section#home {
            background-color: #ffebcd;
        }

        .product {
            margin-bottom: 1.5rem;
        }

        .product img {
            max-width: 100%;
            height: auto;
            border-radius: 8px;
            box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
        }

        .product-details {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .cart {
            margin: 2rem 0;
        }

        .cart button {
            padding: 0.5rem 1rem;
            background-color: #ff6347;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        .order-form {
            margin-top: 2rem;
        }

        .order-form input, .order-form textarea {
            display: block;
            width: 100%;
            padding: 0.5rem;
            margin-bottom: 1rem;
            border: 1px solid #ccc;
            border-radius: 5px;
        }

        .order-form button {
            padding: 0.5rem 1rem;
            background-color: #ffa07a;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        footer {
            background-color: #ff6347;
            color: white;
            text-align: center;
            padding: 1rem 0;
            position: fixed;
            width: 100%;
            bottom: 0;
        }

        .contact-info {
            background-color: #ffa07a;
            color: white;
            padding: 1rem;
            border-radius: 8px;
        }

        .center {
            text-align: center;
        }
    </style>
</head>
<body>
    <header>
        <h1>Nova Brands</h1>
        <p>Your One-Stop Shop for Fashion and Tech!</p>
    </header>

    <nav>
        <ul>
            <li><a href="#home">Home</a></li>
            <li><a href="#about">About Us</a></li>
            <li><a href="#products">Products</a></li>
            <li><a href="#contact">Contact Us</a></li>
        </ul>
    </nav>

    <section id="home" class="center">
        <h2>Our Collection</h2>
        <p>Discover the best shoes, phones, and clothes at Nova Brands. Quality products at unbeatable prices.</p>
    </section>

    <section id="about">
        <h2>About Us</h2>
        <p>Nova Brands is dedicated to providing high-quality products to our customers. Whether you're looking for the latest in fashion, footwear, or technology, we've got you covered. Our mission is to offer trendy, affordable, and reliable products that meet your needs.</p>
    </section>

    <section id="products">
        <h2>Our Products</h2>
        <div class="product">
            <h3>Shoes</h3>
            <div class="product-details">
                <p>Stylish Running Shoes</p>
                <p>R800</p>
            </div>
            <img src="https://via.placeholder.com/400x300?text=Stylish+Running+Shoes" alt="Shoes">
            <div class="cart">
                <button onclick="addToCart('Stylish Running Shoes', 800)">Add to Cart</button>
            </div>
        </div>
        <div class="product">
            <h3>Phones</h3>
            <div class="product-details">
                <p>iPhone 13 Pro</p>
                <p>R15,000</p>
            </div>
            <img src="https://via.placeholder.com/400x300?text=iPhone+13+Pro" alt="iPhone 13 Pro">
            <div class="cart">
                <button onclick="addToCart('iPhone 13 Pro', 15000)">Add to Cart</button>
            </div>
        </div>
        <div class="product">
            <h3>Clothes</h3>
            <div class="product-details">
                <p>Fashionable T-Shirt</p>
                <p>R250</p>
            </div>
            <img src="https://via.placeholder.com/400x300?text=Fashionable+T-Shirt" alt="Clothes">
            <div class="cart">
                <button onclick="addToCart('Fashionable T-Shirt', 250)">Add to Cart</button>
            </div>
        </div>
    </section>

    <section id="order">
        <h2>Place Your Order</h2>
        <form class="order-form" id="order-form" onsubmit="submitOrder(event)">
            <label for="name">Name:</label>
            <input type="text" id="name" name="name" required>

            <label for="email">Email:</label>
            <input type="email" id="email" name="email" required>

            <label for="address">Address:</label>
            <textarea id="address" name="address" required></textarea>

            <label for="cart-items">Cart Items:</label>
            <textarea id="cart-items" name="cart-items" readonly></textarea>

            <button type="submit">Submit Order</button>
        </form>
    </section>

    <section id="contact">
        <h2>Contact Us</h2>
        <div class="contact-info">
            <p>Email: info@novabrands.com</p>
            <p>Phone: 123-456-7890</p>
        </div>
    </section>

    <footer>
        <p>&copy; 2024 Nova Brands. All rights reserved.</p>
    </footer>

    <script src="https://cdn.emailjs.com/dist/email.min.js"></script>
    <script>
        emailjs.init('YOUR_EMAILJS_USER_ID');

        let cart = [];

        function addToCart(product, price) {
            cart.push({product, price});
            alert(product + ' has been added to your cart!');
            updateCartItems();
        }

        function updateCartItems() {
            const cartItems = cart.map(item => `${item.product} - R${item.price}`).join('\n');
            document.getElementById('cart-items').value = cartItems;
        }

        function submitOrder(event) {
            event.preventDefault();

            const form = document.getElementById('order-form');

