## 004 Adding the Product ID to the Path
الان می خوایم که برای هر کالا یه آیدی یونیک درست کنیم و با استفاده از اون بتونیم مقادیر و اطلاعات اون کالا رو نشون بدیم برای همین توی فایل `product.js` که مدل ماست می نویسیم:
```js
save() {
    this.id = Math.random().toString();
    getProductsFromFile((products) => {
      products.push(this);
      fs.writeFile(p, JSON.stringify(products), (err) => {
        console.log(err);
      });
    });
  }
```
بعد توی قسمت `views` توی `product-list.ejs` می نویسیم:
```ejs
<div class="card__actions">
    <a href="/products/<%= product.id %>" class="btn">Detail</a>
    <form action="/add-to-cart" method="POST">
        <button class="btn">Add to Cart</button>
    </form>
</div>
```
اینجا لینکی که اضافه کردیم آدرسش به صورت `<% product.id %>` هست که همون آدرس یونیک برای کالا هاست.
