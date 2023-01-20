## 017 Using a Helper Function for Navigation
می تونیم توی آدرس دهی ها به جای `/..`، فقط از `..` استفاده کنیم.

خب می تونیم تو آدرس دهی هامون تغییراتی بدیم که بهینه تر و تمیز بشه. به این صورت که یه پوشه `util` ایجاد می کنیم و فایل `path.js` رو درست می کنیم.

توی این فایل هم می خوایم که آدرس فایل اصلی برنامه مون که همون فایل `app.js` هست رو برامون بده. برای این کار می نویسیم:
```js
const path = require("path");

module.exports = path.dirname(process.mainModule.filename);
```
الان می تونیم ازش تو فایل های `shop.js` و `admin.js` استفاده کنیم. به طور مثال تو فایل `shop` داریم:
```js
const mainDir = require("../util/path");

router.get("/", (req, res, next) => {
  res.sendFile(path.join(mainDir, "views", "shop.html"));
});
```
