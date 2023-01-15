## 005 How Middleware Works
این قسمت با متد جدیدی به نام `( )send` آشنا می شیم که برای ریسپانس استفاده میشه.
```js
const http = require("http");

const express = require("express");

const app = express();

app.use((req, res, next) => {
  console.log("i'm in the middleware. 1");
  next();
});

app.use((req, res, next) => {
  console.log("i'm in the middleware. 2");
  res.send("<h1>Hello World!</h1>");
});

const server = http.createServer(app);

server.listen(3000);
```
```js
app.use((req, res, next) => {
  console.log("i'm in the middleware. 2");
  res.send("<h1>Hello World!</h1>");
});
```
