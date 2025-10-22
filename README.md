<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Delicious Bites Restaurant</title>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      margin: 0;
      padding: 0;
      background-color: #f5f5f5;
      color: #333;
    }

    header {
      background-color: #8B0000;
      color: white;
      padding: 30px 0;
      text-align: center;
    }

    header h1 {
      font-size: 3em;
      margin: 0;
      letter-spacing: 4px;
      font-weight: 700;
    }

    header p {
      font-size: 1.2em;
      margin-top: 10px;
      font-style: italic;
      font-weight: 300;
    }

    nav {
      background-color: #333;
      text-align: center;
      padding: 12px 0;
    }

    nav a {
      color: white;
      text-decoration: none;
      margin: 0 20px;
      font-size: 1.1em;
      font-weight: 600;
      cursor: pointer;
      transition: color 0.3s;
    }

    nav a:hover {
      color: #F4A261;
    }

    section {
      display: none;
      padding: 40px 20px;
      text-align: center;
      background-color: #fefefe;
    }

    #home {
      display: block;
      padding: 80px 20px;
      background: linear-gradient(135deg, #8B0000 0%, #F4A261 100%);
      color: white;
      text-align: center;
      min-height: 80vh;
      box-sizing: border-box;
    }

    #home > div {
      max-width: 900px;
      margin: 0 auto;
    }

    #home h2 {
      font-size: 3.5em;
      margin-bottom: 0.2em;
      font-weight: 700;
      letter-spacing: 2px;
    }

    #home p.lead {
      font-size: 1.5em;
      margin-bottom: 1em;
      font-style: italic;
      font-weight: 300;
    }

    #home p.desc {
      font-size: 1.1em;
      max-width: 600px;
      margin: 0 auto 2em auto;
      line-height: 1.6;
    }

    #home img {
      width: 280px;
      border-radius: 15px;
      margin-bottom: 25px;
      box-shadow: 0 4px 15px rgba(0,0,0,0.3);
    }

    #home button {
      background-color: white;
      color: #8B0000;
      border: none;
      padding: 15px 35px;
      font-size: 1.2em;
      font-weight: 600;
      border-radius: 30px;
      cursor: pointer;
      transition: background-color 0.3s;
    }

    #home button:hover {
      background-color: #f4a261;
      color: white;
    }

    .menu-item {
      background-color: white;
      width: 280px;
      margin: 15px;
      padding: 20px;
      display: inline-block;
      border-radius: 10px;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
      text-align: left;
      cursor: pointer;
      transition: transform 0.2s;
    }

    .menu-item:hover {
      transform: translateY(-5px);
    }

    .menu-item h3 {
      margin-top: 0;
      color: #8B0000;
    }

    .menu-item p {
      color: #666;
    }

    .menu-item strong {
      color: #F4A261;
    }

    footer {
      background-color: #8B0000;
      color: white;
      text-align: center;
      padding: 15px 0;
      margin-top: 40px;
    }

    /* Modal */
    .modal {
      display: none;
      position: fixed;
      z-index: 1000;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
      overflow: auto;
      background-color: rgba(0, 0, 0, 0.6);
    }

    .modal-content {
      background-color: #fff;
      margin: 5% auto;
      padding: 30px;
      border-radius: 10px;
      width: 90%;
      max-width: 500px;
      position: relative;
      text-align: left;
      box-sizing: border-box;
    }

    .close {
      color: #aaa;
      position: absolute;
      top: 10px;
      right: 20px;
      font-size: 28px;
      font-weight: bold;
      cursor: pointer;
    }

    .close:hover {
      color: #8B0000;
    }

    .order-button,
    .submit-button {
      background-color: #8B0000;
      color: white;
      border: none;
      padding: 12px 20px;
      margin-top: 15px;
      border-radius: 5px;
      cursor: pointer;
      font-weight: 600;
      font-size: 1em;
    }

    .order-button:hover,
    .submit-button:hover {
      background-color: #a00000;
    }

    form input,
    form select,
    form textarea {
      width: 100%;
      padding: 10px;
      margin-top: 10px;
      border: 1px solid #ccc;
      border-radius: 5px;
      box-sizing: border-box;
      font-size: 1em;
      font-family: inherit;
    }

    .confirmation {
      color: green;
      font-weight: bold;
      margin-top: 20px;
      font-size: 1.1em;
    }
  </style>

  <script>
    let selectedItem = "";

    function showSection(id) {
      const sections = document.querySelectorAll("section");
      sections.forEach(sec => sec.style.display = "none");
      document.getElementById(id).style.display = "block";
    }

    function showModal(title, description, price) {
      selectedItem = title;
      document.getElementById("modal-title").innerText = title;
      document.getElementById("modal-description").innerText = description;
      document.getElementById("modal-price").innerText = price;
      document.getElementById("modal-details").style.display = "block";
      document.getElementById("modal-form").style.display = "none";
      document.getElementById("modal-confirmation").style.display = "none";
      document.getElementById("modal").style.display = "block";

      // Clear form inputs
      document.getElementById('cust-name').value = "";
      document.getElementById('cust-phone').value = "";
      document.getElementById('cust-address').value = "";
      document.getElementById('cust-payment').value = "";
    }

    function closeModal() {
      document.getElementById("modal").style.display = "none";
    }

    function showOrderForm() {
      document.getElementById("modal-details").style.display = "none";
      document.getElementById("modal-form").style.display = "block";
    }

    function submitOrder() {
      const name = document.getElementById('cust-name').value.trim();
      const phone = document.getElementById('cust-phone').value.trim();
      const address = document.getElementById('cust-address').value.trim();
      const payment = document.getElementById('cust-payment').value;

      if (!name || !phone || !address || !payment) {
        alert("Please fill all the fields.");
        return;
      }

      // Simple phone validation
      const phoneRegex = /^[0-9]{10}$/;
      if (!phoneRegex.test(phone)) {
        alert("Please enter a valid 10-digit phone number.");
        return;
      }

      document.getElementById("modal-form").style.display = "none";
      document.getElementById("modal-confirmation").innerHTML = `
        <p class="confirmation">
          ✅ Thank you, <strong>${name}</strong>!<br>
          Your order for <strong>${selectedItem}</strong> has been placed.<br><br>
          💳 Payment Method: <strong>${payment}</strong><br>
          📍 Delivery Address: <strong>${address}</strong><br>
          ⏰ Estimated Delivery Time: <strong>30–40 minutes</strong>
        </p>`;
      document.getElementById("modal-confirmation").style.display = "block";
    }

    window.onclick = function (event) {
      const modal = document.getElementById("modal");
      if (event.target === modal) {
        closeModal();
      }
    };
  </script>
</head>

<body>

  <header>
    <h1>Delicious Bites</h1>
    <p>🍽️ Welcome to the taste of happiness — Bhimavaram's best bites!</p>
  </header>

  <nav>
    <a onclick="showSection('home')">Home</a>
    <a onclick="showSection('menu')">Menu</a>
    <a onclick="showSection('contact')">Contact</a>
  </nav>

  <!-- Home Section -->
  <section id="home">
    <div>
      <h2>Delicious Bites</h2>
      <p class="lead">Experience authentic flavors crafted with passion in Bhimavaram.</p>
      <p class="desc">
        At Delicious Bites, we bring you a curated menu blending traditional tastes with modern culinary artistry.
        Whether you crave classic pizzas, rich Indian curries, or aromatic biryanis, we promise fresh ingredients and impeccable service.
      </p>

      <!-- Added image -->
      <img src="https://images.unsplash.com/photo-1600891964599-f61ba0e24092?auto=format&fit=crop&w=600&q=80" 
           alt="Delicious food" />

      <button onclick="showSection('menu')">View Our Menu</button>
    </div>
  </section>

  <!-- Menu Section -->
  <section id="menu">
    <h2>Our Menu</h2>

    <div class="menu-item" onclick="showModal('Pizza Margherita', 'Classic pizza with tomato sauce, mozzarella, and basil.', '₹249')">
      <h3>Pizza Margherita</h3>
      <p>Click to order</p>
      <strong>₹249</strong>
    </div>

    <div class="menu-item" onclick="showModal('Butter Chicken', 'Rich creamy chicken cooked with Indian spices.', '₹279')">
      <h3>Butter Chicken</h3>
      <p>Click to order</p>
      <strong>₹279</strong>
    </div>

    <div class="menu-item" onclick="showModal('Paneer Biryani', 'Spicy and aromatic paneer biryani served with raita.', '₹199')">
      <h3>Paneer Biryani</h3>
      <p>Click to order</p>
      <strong>₹199</strong>
    </div>
  </section>

  <!-- Contact Section -->
  <section id="contact">
    <h2>Contact Us</h2>
    <p><strong>📞 Phone:</strong> 9995559955</p>
    <p><strong>📍 Address:</strong> Bhimavaram, Andhra Pradesh</p>
  </section>

  <!-- Modal -->
  <div id="modal" class="modal">
    <div class="modal-content">
      <span class="close" onclick="closeModal()">&times;</span>

      <!-- Details -->
      <div id="modal-details">
        <h2 id="modal-title"></h2>
        <p id="modal-description"></p>
        <p><strong>Price: </strong><span id="modal-price"></span></p>
        <button class="order-button" onclick="showOrderForm()">Order Now</button>
      </div>

      <!-- Order Form -->
      <div id="modal-form" style="display:none;">
        <h3>Place Your Order</h3>
        <form onsubmit="event.preventDefault(); submitOrder();">
          <label for="cust-name">Name:</label>
          <input type="text" id="cust-name" required />

          <label for="cust-phone">Phone Number:</label>
          <input type="tel" id="cust-phone" placeholder="10-digit number" required />

          <label for="cust-address">Delivery Address:</label>
          <textarea id="cust-address" rows="3" required></textarea>

          <label for="cust-payment">Payment Method:</label>
          <select id="cust-payment" required>
            <option value="" disabled selected>Select Payment Method</option>
            <option value="Cash on Delivery">Cash on Delivery</option>
            <option value="UPI">UPI</option>
            <option value="Credit/Debit Card">Credit/Debit Card</option>
          </select>

          <button type="submit" class="submit-button">Place Order</button>
        </form>
      </div>

      <!-- Confirmation -->
      <div id="modal-confirmation" style="display:none;"></div>
    </div>
  </div>

  <footer>
    &copy; 2025 Delicious Bites Restaurant. All rights reserved.
  </footer>

</body>
</html>
