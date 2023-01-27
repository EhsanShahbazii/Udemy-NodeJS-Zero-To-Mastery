## 006 Storing Data in Files Via the Model
الان می خوایم دیتا رو به جای اینکه توی آرایه نگه داریم، توی سیستم به صورت فایل ذخیره می کنیم. برای همین از `File System` استفاده می کنیم:
```js
const fs = require("fs");
const path = require("path");

save() {
  let p = path.join(
    path.dirname(process.mainModule.filename),
    "data",
    "products.json"
  );
  fs.readFile(p, (err, fileContent) => {
    let products = [];
    if (!err) {
      product = JSON.parse(fileContent);
    }
    products.push(this);
    fs.writeFile(p, JSON.stringify(products), (err) => {
      console.log(err);
    });
  });
}
```
اینجا ما یه آدرس درست کردیم که به پوشه `data` اشاره می کنه. بعد اول فایل رو می خونیم بعد بهش اضافه می کنیم.
```js
static fetchAll() {
  let p = path.join(
    path.dirname(process.mainModule.filename),
    "data",
    "products.json"
  );
  fs.readFile(p, (err, fileContent) => {
    if (err) {
      return [];
    }
    return JSON.parse(fileContent);
  });
  return products;
}
```
اینجا هم دوباره یه آدرس درست می کنیم و تمام فایل رو می خونیم. (منتهی الان اینجا به یه ارور برخورد می کنیم که در جلسه بعد اون رو رفع می کنیم.)
