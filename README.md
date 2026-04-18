<!DOCTYPE html>
<html lang="uk">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sushi & Wine</title>

<style>
body { font-family: Arial; margin: 0; background: #f5f5f5; }

header {
  background: #111;
  color: white;
  text-align: center;
  padding: 20px;
}

.container { padding: 20px; }

.menu {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
}

.item {
  background: white;
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0 2px 5px rgba(0,0,0,0.2);
}

.item img {
  width: 100%;
  height: 160px;
  object-fit: cover;
}

.item h3 { margin: 10px; }
.item p { margin: 10px; }

button {
  margin: 10px;
  padding: 10px;
  background: #e63946;
  color: white;
  border: none;
  border-radius: 5px;
  width: calc(100% - 20px);
}

.cart {
  position: fixed;
  right: 0;
  top: 0;
  width: 280px;
  height: 100%;
  background: white;
  padding: 20px;
  box-shadow: -2px 0 5px rgba(0,0,0,0.2);
}
</style>
</head>

<body>

<header>
<h1>🍣 Sushi & Wine</h1>
</header>

<div class="container">
<h2>Меню</h2>
<div class="menu" id="menu"></div>
</div>

<div class="cart">
<h2>Кошик</h2>
<ul id="cart"></ul>
<p><b>Сума:</b> <span id="total">0</span> грн</p>
<button onclick="checkout()">Замовити</button>
</div>

<script>
const items = [
{
 name: "Філадельфія",
 price: 250,
 img: "https://images.pexels.com/photos/357756/pexels-photo-357756.jpeg"
},
{
 name: "Каліфорнія",
 price: 220,
 img: "https://images.pexels.com/photos/2098085/pexels-photo-2098085.jpeg"
},
{
 name: "Червоне вино",
 price: 300,
 img: "https://images.pexels.com/photos/434311/pexels-photo-434311.jpeg"
},
{
 name: "Біле вино",
 price: 280,
 img: "https://images.pexels.com/photos/1407846/pexels-photo-1407846.jpeg"
}
];

const menu = document.getElementById("menu");
const cartList = document.getElementById("cart");
const totalEl = document.getElementById("total");

let cart = [];

items.forEach((item, i) => {
  const div = document.createElement("div");
  div.className = "item";
  div.innerHTML = `
    <img src="${item.img}">
    <h3>${item.name}</h3>
    <p>${item.price} грн</p>
    <button onclick="add(${i})">Додати</button>
  `;
  menu.appendChild(div);
});

function add(i){
  cart.push(items[i]);
  render();
}

function render(){
  cartList.innerHTML="";
  let total=0;

  cart.forEach(item=>{
    let li=document.createElement("li");
    li.textContent=item.name+" - "+item.price+" грн";
    cartList.appendChild(li);
    total+=item.price;
  });

  totalEl.textContent=total;
}

function checkout(){
  alert("Замовлення оформлено!");
  cart=[];
  render();
}
</script>

</body>
</html>
