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
