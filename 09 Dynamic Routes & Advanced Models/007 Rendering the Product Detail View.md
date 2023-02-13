## 007 Rendering the Product Detail View
قراره که یه صفحه برای کالا درست کنیم که اطلاعاتش رو تو اونجا نشون بدیم. برای همین یه صفحه به اسم `product-detail` درست می کنیم:
```ejs
<%- include('../includes/head.ejs') %>
    </head>

    <body>
        <%- include('../includes/navigation.ejs') %>
        <main class="centered">
            <h1><%= product.title %></h1>
            <hr>
            <div>
                <img src="<%= product.imageUrl %>" alt="<%= product.title %>">
            </div>
            <h2><%= product.price %></h2>
            <p><%= product.description %></p>
            <form action="/cart" method="post">
                <button class="btn" type="submit">Add to Cart</button>
            </form>
        </main>
        <%- include('../includes/end.ejs') %>
```
الان توی فایل `shop.js` این کد رو می نویسیم:
```js
exports.getProduct = (req, res, next) => {
  const prodId = req.params.productId;
  Product.findById(prodId, product => {
    res.render('shop/product-detail', {
      product: product,
      pageTitle: product.title,
      path: '/products'
    });
  });
};
```
