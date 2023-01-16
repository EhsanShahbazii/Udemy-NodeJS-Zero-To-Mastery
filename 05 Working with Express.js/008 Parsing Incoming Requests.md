## 008 Parsing Incoming Requests
اینجا قراره که دیتایی که یوزر می فرسته رو بگیریم. برای همین از یه پکیجی به نام `body-parser` استفاده می کنیم. پس برای همین اونو نصب می کنیم.

به این صورت که کامند `npm i --save body-paeser` رو اجرا می کنیم. بعد به صورت زیر استفاده می کنیم:
```js
const express = require("express");
const bodyParser = require("body-parser");

const app = express();

app.use(bodyParser.urlencoded({ extended: false }));
```
اول از همه باید `body` رو تبدیل کنیم. برای همین از `bodyParser.urlencoded({ extended: false })` استفاده می کنیم. بعد یه فرم می سازیم و به صورت زیر بقیه کد رو می زنیم.
```js
app.use("/add-product", (req, res, next) => {
  res.send(
    "<form action='/product' method='POST'><input type='text' name='title'><button type='submit'>Add Product</button></form>"
  );
});

app.use("/product", (req, res, next) => {
  console.log(req.body);
  res.redirect("/");
});

app.use("/", (req, res, next) => {
  res.send("<h1>home page</h1>");
});

app.listen(3000);
```
متد `req.body` مربوط به `express` هست. الان یوزر توی اینپوت عبارت `you don't know js` رو می نویسه و اینجا به صورت زیر دریافت میشه:
```console
[Object: null prototype] { title: "you don't know js" }
```
