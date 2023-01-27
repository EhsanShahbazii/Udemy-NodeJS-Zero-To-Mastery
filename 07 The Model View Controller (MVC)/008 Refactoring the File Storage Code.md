## 008 Refactoring the File Storage Code
الان می خوایم کد ها رو کمی بهتر بنویسیم برای همین به صورت زیر می نویسیم:
```js
const p = path.join(
  path.dirname(process.mainModule.filename),
  'data',
  'products.json'
);

const getProductsFromFile = cb => {
  fs.readFile(p, (err, fileContent) => {
    if (err) {
      cb([]);
    } else {
      cb(JSON.parse(fileContent));
    }
  });
};
```
دو تا متد گلوبال توی فایل `product.js` درست کردیم و به صورت زیر استفاده می کنیم:
```js
module.exports = class Product {
  constructor(t) {
    this.title = t;
  }

  save() {
    getProductsFromFile(products => {
      products.push(this);
      fs.writeFile(p, JSON.stringify(products), err => {
        console.log(err);
      });
    });
  }

  static fetchAll(cb) {
    getProductsFromFile(cb);
  }
};
```
