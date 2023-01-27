## 007 Fetching Data from Files Via the Model
علت اینکه این مشکل پیش میاد اینه که متد ها `async` هستن برای همین `undefiend` بر می گردونه. برای رفع این ارور منطقی میایم از `call back` استفاده می کنیم:
```js
static fetchAll(cb) {
  let p = path.join(
    path.dirname(process.mainModule.filename),
    "data",
    "products.json"
  );
  fs.readFile(p, (err, fileContent) => {
    if (err) {
      cb([]);
    }
    return JSON.parse(fileContent);
  });
  cb(products);
}
```
بعد میایم اونجایی که از این تابع استفاده کردیم به صورت `call back` می نویسیم. توی پوشه `controller` فایل `products.js` به صورت زیر:
```js
exports.getProducts = (req, res, next) => {
  Product.fetchAll((products) => {
    res.render("shop", {
      prods: products,
      pageTitle: "Shop",
      path: "/",
      hasProducts: products.length > 0,
      activeShop: true,
      productCSS: true,
    });
  });
};
```
