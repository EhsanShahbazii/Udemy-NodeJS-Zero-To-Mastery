## 014 Serving HTML Pages
خب اینجا قراره که به یوزر سند `html` بفرستیم. برای همین میایم تو یه پوشه به نام `views` فایل هامون رو درست می کنیم. اسامی فایل ها `add-product` و `shop` هست.

الان تو فایل های `shop` و `admin` تغییراتی رو ایجاد می کنیم. برای ارسال فایل به یوزر از متد `sendFile` استفاده می کنیم.
```js
const express = require("express");

const router = express.Router();

router.get("/", (req, res, next) => {
  res.sendFile("../views/shop.html");
});

module.exports = router;
```
ولی اینجا به ارور بر میخوریم و میگه که باید آدرس دهیمون به صورت `absolute` باشه. برای همین از ماژول اصلی نود به نام `path` برای آدرس دهی استفاده می کنیم:
```js
const path = require("path");

const express = require("express");

const router = express.Router();

router.get("/", (req, res, next) => {
  res.sendFile(path.join(__dirname, "../", "views", "shop.html"));
});

module.exports = router;
```
این متد آدرسی رو درست می کنه و با استفاده از متد `join` هم آدرس ها رو به هم متصل می کنیم. همین طور تو فایل `admin` هم داریم:
```js
const path = require("path");

const express = require("express");

const router = express.Router();

router.get("/add-product", (req, res, next) => {
  res.sendFile(path.join(__dirname, "../", "views", "add-product.html"));
});

router.post("/add-product", (req, res, next) => {
  console.log(req.body);
  res.redirect("/");
});

module.exports = router;
```
