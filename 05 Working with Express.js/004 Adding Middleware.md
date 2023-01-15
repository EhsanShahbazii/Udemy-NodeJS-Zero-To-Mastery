## 004 Adding Middleware
خب `express` متد هایی داره که با متد `( )use` آشنا می شیم. این متد تو هر ریکوئستی فراخوانی میشه. می تونیم چند تا از این متد هارو بنویسیم.
```js
const http = require("http");

const express = require("express");

const app = express();

app.use((req, res, next) => {
  console.log("I'm in the middleware. 1");
});

app.use((req, res, next) => {
  console.log("I'm in the middleware. 2");
});

const server = http.createServer(app);

server.listen(3000);
```
الان اینجا اگه سرور رو ران کنیم فقط عبارت زیر تو کنسول چاپ میشه:
```console
I'm in the middleware. 1
```
برای اینکه متد بعدی هم اجرا بشه نیازه که از متد `( )next` استفاده کنیم. این متد باعث میشه که بعد فراخوانی تابع، بره تابع بعدی رو هم فراخوانی بکنه.
```js
const http = require("http");

const express = require("express");

const app = express();

app.use((req, res, next) => {
  console.log("I'm in the middleware. 1");
  next();
});

app.use((req, res, next) => {
  console.log("I'm in the middleware. 2");
});

const server = http.createServer(app);

server.listen(3000);
```
الان توی کنسول وقتی سرور رو ران کنیم این عبارت رو می بینیم:
```console
I'm in the middleware. 1
I'm in the middleware. 2
```
