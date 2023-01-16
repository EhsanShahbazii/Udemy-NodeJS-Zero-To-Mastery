## 009 Limiting Middleware Execution to POST Requests
برای فیلتر کردن روت بندی هامون می تونیم از متد های `get` و `post` به جای `use` استفاده کنیم. به این صورت که:

اگه از متد `post` استفاده کنیم، تنها وقتی که به صورت متد `POST` به این روت هدایت میشه این تابع اجرا میشه. یعنی اگه توی آدرس سایت بنویسیم `localHost:3000/product`
یه این صفحه هدایت نمیشیم.
```js
app.post("/product", (req, res, next) => {
  console.log(req.body);
  res.redirect("/");
});
```
و اگه از متد `get` استفاده کنیم، هم وقتی که به صورت متد `GET` به این روت هدایت میشیم و هم به صورت وقتی که آدرسش رو می نویسیم.
```js
app.get("/product", (req, res, next) => {
  console.log(req.body);
  res.redirect("/");
});
```
