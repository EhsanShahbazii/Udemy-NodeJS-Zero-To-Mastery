## 002 What is the MVC
در واقع به زبان ساده `MVC` نوعی معماری که مخفف `Model View Controller` هست. ما تو پروژه قسمت های مختلف رو از هم جدا می کنیم. مثلا تو پوشه `controllers` می نویسیم:

```js
const products = [];

exports.getAddProduct = (req, res, next) => {
  res.render('add-product', {
    pageTitle: 'Add Product',
    path: '/admin/add-product',
    formsCSS: true,
    productCSS: true,
    activeAddProduct: true
  });
};

exports.postAddProduct = (req, res, next) => {
  products.push({ title: req.body.title });
  res.redirect('/');
};

exports.getProducts = (req, res, next) => {
  res.render('shop', {
    prods: products,
    pageTitle: 'Shop',
    path: '/',
    hasProducts: products.length > 0,
    activeShop: true,
    productCSS: true
  });
};
```
