## 005 Extracting Dynamic Params
می خوایم دیتایی که از طریق `url` می فرستیم رو استخراج کنیم. برای همین تو قسمت `routes` فایل `shop.js` این متد رو می نویسیم:
```js
router.get("/product/:productId", shopController.getProduct);
```
ولی باید دقت کنیم که این مدل نوشتن `productId:` شامل هر چیزی میشه و اگه یه `delete/` بعد این داشته باشیم، هرگز اجرا نمیشه.

بعد برای هندل کردن متد `getProduct` تو قسمت `controllers` فایل `shop.js` می نویسیم:
```js
exports.getProduct = (req, res, next) => {
  const prodId = req.params.productId;
  res.redirect("/");
};
```
می تونیم از طریق متد `params` پارامتر هایی که از این طریق ارسال می کنیم رو استخراج کنیم.
