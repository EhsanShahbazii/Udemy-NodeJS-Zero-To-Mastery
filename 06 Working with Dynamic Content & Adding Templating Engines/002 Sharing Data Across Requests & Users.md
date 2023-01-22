## 002 Sharing Data Across Requests & Users
الان می خوایم دیتا هارو به صورت داینامیک به کاربر نشون بدیم. دیتا هارو یه جایی ذخیره کنیم. برای همین این تغییرات رو می دیم:
توی فایل `admin.js` ما یه آرایه خالی درست می کنیم و دیتا هایی که یوزر میده رو اونجا ذخیره می کنیم.
```js
const products = [];

router.post('/add-product', (req, res, next) => {
  products.push({ title: req.body.title });
  res.redirect('/');
});

exports.routes = router;
exports.products = products;
```
بعد که اکسپورتشون کردیم می تونیم تو جاهای دیگه هم بهش دسترسی داشته باشیم و ازش استفاده کنیم. توی فایل اصلی `app.js` این تغییرات رو می دیم:
```js
app.use('/admin', adminData.routes);
```
الان می خوایم اون دیتا رو نشون بدیم. برای همین توی فایل `shop.js` از اون لاگ می گیریم:
```js
const rootDir = require('../util/path');
const adminData = require('./admin');

const router = express.Router();

router.get('/', (req, res, next) => {
  console.log('shop.js', adminData.products);
  res.sendFile(path.join(rootDir, 'views', 'shop.html'));
});
```
