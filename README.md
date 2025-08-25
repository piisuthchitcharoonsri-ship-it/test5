<!-- ...existing code... -->
<body>
  <header>🛍️ ร้านขายของโทนพาสเทล</header>

  <!-- Filter Buttons -->
  <div style="text-align:center; margin-top:20px;">
    <button onclick="filterProducts('all')">ทั้งหมด</button>
    <button onclick="filterProducts('clothes')">เสื้อผ้า</button>
    <button onclick="filterProducts('electronics')">อิเล็กทรอนิกส์</button>
  </div>

  <div class="container" id="product-list"></div>
<!-- ...existing code... -->
  <script>
    const products = [
      { id: 1, name: "เสื้อยืด", price: 250, category: "clothes", image: "https://i.pinimg.com/564x/1d/7b/14/1d7b14f26d9ebc4bdf016e5a6f7f5a3a.jpg" },
      { id: 2, name: "กางเกงยีนส์", price: 500, category: "clothes", image: "https://i.pinimg.com/564x/d8/28/0e/d8280e6b0f6d4d8846f2e647f727f9fc.jpg" },
      { id: 3, name: "หูฟัง", price: 800, category: "electronics", image: "https://i.pinimg.com/564x/42/ff/61/42ff613aeb2c292743ffb391d4fbf5e1.jpg" },
      { id: 4, name: "โทรศัพท์", price: 10000, category: "electronics", image: "https://i.pinimg.com/564x/31/0b/45/310b45c5d1ecfbe2ec99c4a1fb2a3163.jpg" }
    ];

    let cart = [];

    const productList = document.getElementById("product-list");

    function renderProducts(list) {
      productList.innerHTML = "";
      list.forEach(product => {
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
    }

    // Initial render
    renderProducts(products);

    function filterProducts(category) {
      if (category === "all") {
        renderProducts(products);
      } else {
        renderProducts(products.filter(p => p.category === category));
      }
    }

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
<!-- ...existing code... -->
