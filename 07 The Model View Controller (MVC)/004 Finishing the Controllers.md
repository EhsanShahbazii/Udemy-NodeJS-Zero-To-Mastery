## 004 Finishing the Controllers
خب الان فقط یدونه قسمت `404Error` مونده. برای همین تو پوشه `controllers` فایل `error` درست می کنیم و اونجا می نویسیم:
```js
exports.get404 = (req, res, next) => {
  res.status(404).render('404', { pageTitle: 'Page Not Found' });
};
```
