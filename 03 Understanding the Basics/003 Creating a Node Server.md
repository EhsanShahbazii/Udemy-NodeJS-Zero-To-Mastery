## 003 Creating a Node Server
برای ساخت یه سرور از ماژول اصلی `http` استفاده می کنیم:
```js
const http = require('http');

const server = http.createServer((req, res) => {
  console.log(req);
});

sever.listen(3000);
```
الان تو پورت `3000` سرور درست میشه. تو پورت های دیگعی هم می تونیم. حالت دیفالت تو پورت `80` هست یا همون `/http://localhost:80`.

## گزیده ای از رفرنس های اصلی
برای ساختن یه سرور به صورت زیر می تونیم بنویسیم:
```js
const http = require('http');

const hostname = '127.0.0.1';
const port = 3000;

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello World\n');
});

server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
```
ما `statusCode`، `setHeader` و `end` استفاده کردیم به معنیشون به صورت زیر هست:
```js
res.statusCode = 200;
```
اینجا ما کد `200` رو می نویسیم که از اینجا نشون بدیم ریسپانس موفقیت آمیز بود یعنی `successful` بود.
```js
res.setHeader('Content-Type', 'text/plain');
```
اینجا ما هدر رو ست می کنیم که بگیم این سندی که توی ریسپانس لود می کنیم از جنس چیه که اینجا از جنس `text/plain` هست.
```js
res.end('Hello World\n');
```
و در آخر هم ما ریسپانس رو می بندیم و یه آرگومان بهش می دیم که نمایش بده.

[Previous page](003%20Creating%20a%20Node%20Server.md)
[Next page](004%20The%20Node%20Lifecycle%20&%20Event%20Loop.md)
