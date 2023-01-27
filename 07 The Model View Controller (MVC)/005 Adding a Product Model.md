## 005 Adding a Product Model
الان باید `models` رو درست کنیم. در پوشه `modals` فایل `product.js` رو درست می کنیم. الان این مدل ماست. به صورت زیر می نویسیم:
```js
const products = [];

module.exports = class Product {
  constructor(title) {
    this.title = title;
  }

  save() {
    products.push(this);
  }

  static fetchAll() {
    return products;
  }
};
```
ما یک کلاس `Product` درست کردیم. متد `save` آبجکت جدید رو توی آرایه `product` ذخیره می کنه. متد `fetchAll` هم کل آبجکت هارو بر می گردونه. منتهی باید دقت کنیم که این
متد مستفل از آبجکت ها هست و مختص کلاس هست. یعنی برای استفاده ازش نیازی نیست آبجکت جدیدی از این کلاس بسازیم. برای همین از کلید `static` استفاده می کنیم.
