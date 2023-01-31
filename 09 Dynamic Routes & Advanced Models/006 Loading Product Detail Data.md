## 006 Loading Product Detail Data
خب برای اینکه بتونیم دیتای کالا رو به دست بیاریم باید این کار رو بکنیم. توی مدل `Product` به صورت زیر یه متد اضافه می کنیم:
```js
static findById(id, cb) {
    getProductsFromFile(products => {
      const product = products.find(p => p.id === id);
      cb(product);
    });
  }
```
این متد میاد از بین فایل هایی که وجود دارن، فایلی که آیدیش با آیدی ورودی مطابقت داره و بر می گردونه. الان توی فایل `Shop` به صورت زیر استفاده می کنیم:
```js
exports.getProduct = (req, res, next) => {
  const prodId = req.params.productId;
  Product.findById(prodId, product => {
    console.log(product);
  });
  res.redirect('/');
};
```
الان وقتی اطلاعات یه کالا رو می خوایم به صورت زیر تو کنسول نوشته میشه:
```console
{
  title: 'Another Product',
  imageUrl: 'data:book.jpg',
  description: 'Another very amazing product!',
  price: '20.99',
  id: '0.558673316244021'
}
```
