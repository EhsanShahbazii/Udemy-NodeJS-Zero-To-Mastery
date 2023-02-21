## 008 Passing Data with POST Requests
برای اینکه اطلاعات یه کالا رو بتونیم استخراج کنیم برای همین نیاز به آی دی اون داریم. برای همین توی فایل `product-detail.ejs` می نویسیم:
```ejs
<form action="/cart" method="post">
  <button class="btn" type="submit">Add to Cart</button>
  <input type="hidden" name="productId" value="<%= product.id %>">
</form>
```
دلیل اینکه یه اینپوت به صورت `hidden` درست می کنیم اینه که میخوایم اطلاعات کالا رو به صورت `request body` استخراج کنیم. توی متد `POST` اینپوت ها و بقیه موارد توی `body` ذخیره می شن. الان توی فایل `shop.js` قسمت کنترلر ها می نویسیم:
```js
exports.postCard = (req, res, next) => {
  const prodId = req.body.productId;
  console.log(prodId);
  res.redirect("/card");
};
```
الان کافیه که `router` رو به این کنترلر وصل کنیم. پس توی فایل `shop.js` قسمت  `router` می نویسیم:
```js
router.post("/cart", shopController.getCart);
```
برای راحتی کار می تونیم یه فایل به نام `add-to-card.ejs` بسازیم و بنویسیم:
```ejs
<form action="/cart" method="post">
  <button class="btn" type="submit">Add to Cart</button>
  <input type="hidden" name="productId" value="<%= product.id %>" />
</form>
```
بعد اون رو `include` کنیم اونجا هایی که استفاده میشه: به صورت زیر می نویسیم:
```ejs
<%- include('../includes/add-to-card.ejs') %>
```
