## 012 Filtering Paths
برای اینکه بتونیم برای هر روت `path` های مخصوص خودشون رو بدیم می تونیم به صورت زیر توی فایل `app.js` بنویسیم:
```js
app.use("/admin", adminRoutes);
```
این میاد روت هایی که تو فایل `admin` قرار دارن تغییر میده و اولشون یه `admin/` میزاره. برای راحتی کار هم روت `product` رو حذف می کنیم. به صورت زیر:
```js
const express = require("express");

const router = express.Router();

// admin/add-product => GET
router.get("/add-product", (req, res, next) => {
  res.send(
    "<form action='/product' method='POST'><input type='text' name='title'><button type='submit'>Add Product</button></form>"
  );
});

// admin/add-product => POST
router.post("/add-product", (req, res, next) => {
  console.log(req.body);
  res.redirect("/");
});

module.exports = router;
```
