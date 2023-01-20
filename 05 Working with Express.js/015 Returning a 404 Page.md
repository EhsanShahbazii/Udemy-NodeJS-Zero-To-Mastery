## 015 Returning a 404 Page
می خوایم صفحه `Error 404 page not found` رو درست کنیم. برای همین توی پوشه `views` فایل `404Error.html` رو درست می کنیم.
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>404 ERROR PAGE NOT FOUND</title>
  </head>
  <body>
    <h1>page not found</h1>
  </body>
</html>
```
الان توی فایل `app.js` این تغییر رو میدیم:
```js
const path = require("path");

app.use((req, res, next) => {
  res.status(404).sendFile(path.join(__dirname, "views", "404Error.html"));
});
```
