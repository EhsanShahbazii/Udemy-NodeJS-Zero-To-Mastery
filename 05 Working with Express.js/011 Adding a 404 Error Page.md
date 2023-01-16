## 011 Adding a 404 Error Page
برای اینکه اگه صفحه ای پیدا نشد ما `ERROR 404 page not found` رو نشون بدیم، به صورت زیر کدش رو تو فایل `app.js` می نویسیم:
```js
app.use((req, res, next) => {
  res.status(404).send("<h1>Error 404 not found</h1>");
}
```
می تونیم از تابع `status`، `setHeader` و ... به صورت زنجیر وار استفاده کنیم.
