## 010 Using Express Router
می خوایم از یه ویژگی اکسپرس برای روت بندی استفاده کنیم. برای همین دو تا فایل به نام های `admin.js` و `shop.js` تو پوشه `routes` درست می کنیم:

```js
// admin.js

const express = require("express");

const router = express.Router();

router.get("/add-product", (req, res, next) => {
  res.send(
    "<form action='/product' method='POST'><input type='text' name='title'><button type='submit'>Add Product</button></form>"
  );
});

router.post("/product", (req, res, next) => {
  console.log(req.body);
  res.redirect("/");
});

module.exports = router;
```
```js
// shop.js

const express = require("express");

const router = express.Router();

router.get("/", (req, res, next) => {
  res.send("<h1>home page</h1>");
});

module.exports = router;
```
و توی فایل `app.js` به این صورت می نویسیم:
```js
const express = require("express");
const bodyParser = require("body-parser");

const adminRoutes = require("./routes/admin");
const shopRoutes = require("./routes/shop");

const app = express();

app.use(bodyParser.urlencoded({ extended: false }));

app.use(adminRoutes);
app.use(shopRoutes);

app.listen(3000);

```
