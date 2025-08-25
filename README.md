<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ร้านขายของพาสเทล</title>
  <style>
    body {
      font-family: "Prompt", sans-serif;
      background-color: #fdf6f0;
      margin: 0;
      padding: 0;
    }
    header {
      background-color: #f9c5d5;
      padding: 1rem;
      text-align: center;
      font-size: 1.8rem;
      font-weight: bold;
      color: #fff;
    }
    .container {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 20px;
      padding: 20px;
    }
    .product {
      background: #fff;
      border-radius: 15px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
      padding: 15px;
      text-align: center;
      transition: transform 0.2s;
    }
    .product:hover {
      transform: scale(1.05);
    }
    .product img {
      width: 100%;
      height: 200px;
      object-fit: cover;
      border-radius: 12px;
    }
    button {
      background-color: #a1c4fd;
      border: none;
      padding: 10px 15px;
      margin-top: 10px;
      border-radius: 10px;
      cursor: pointer;
      font-size: 1rem;
      color: #fff;
    }
    button:hover {
      background-color: #779be7;
    }
    .cart {
      position: fixed;
      bottom: 20px;
      right: 20px;
      background: #f9c5d5;
      padding: 15px;
      border-radius: 12px;
      color: white;
      font-weight: bold;
      cursor: pointer;
      box-shadow: 0 4px 10px rgba(0,0,0,0.2);
    }
  </style>
</head>
<body>
  <header>🛍️ ร้านขายของโทนพาสเทล</header>

  <div class="container" id="product-list"></div>

  <div class="cart" onclick="viewCart()">🛒 ตะกร้า (<span id="cart-count">0</span>)</div>

  <script>
    const products = [
      { id: 1, name: "เสื้อยืด", price: 250, category: "clothes", image: "https://i.pinimg.com/564x/1d/7b/14/1d7b14f26d9ebc4bdf016e5a6f7f5a3a.jpg" },
      { id: 2, name: "กางเกงยีนส์", price: 500, category: "clothes", image: "https://i.pinimg.com/564x/d8/28/0e/d8280e6b0f6d4d8846f2e647f727f9fc.jpg" },
      { id: 3, name: "หูฟัง", price: 800, category: "electronics", image: "https://i.pinimg.com/564x/42/ff/61/42ff613aeb2c292743ffb391d4fbf5e1.jpg" },
      { id: 4, name: "โทรศัพท์", price: 10000, category: "electronics", image: "https://i.pinimg.com/564x/31/0b/45/310b45c5d1ecfbe2ec99c4a1fb2a3163.jpg" }
    ];

    let cart = [];

    const productList = document.getElementById("product-list");

    products.forEach(product => {
      const item = document.createElement("div");
      item.className = "product";
      item.innerHTML = `
        <img src="${product.image}" alt="${product.name}">
        <h3>${product.name}</h3>
        <p>${product.price} บาท</p>
        <button onclick="addToCart(${product.id})">ใส่ตะกร้า</button>
      `;
      productList.appendChild(item);
    });

    function addToCart(id) {
      cart.push(id);
      document.getElementById("cart-count").innerText = cart.length;
      alert("เพิ่มลงตะกร้าแล้ว!");
    }

    function viewCart() {
      if (cart.length === 0) {
        alert("ยังไม่มีสินค้าในตะกร้า");
      } else {
        alert("คุณมี " + cart.length + " รายการในตะกร้า");
      }
    }
  </script>
</body>
</html>
