## 004 The Node Lifecycle & Event Loop
وقتی ما دستور `node app.js` رو می زنیم، اسکریپت ها شروع میشن و تمام توابع و متغیر و... اجرا میشن. منتهی این اجرا تموم نمیشه و همواره در حال اجراست.

به این اتفاق `event loop` میگن. برای اینکه ما سرور رو از کار بیاندازیم باید متد `( )process.exit` رو فراخوانی کنیم.
```js
const http = require('http');

const server = http.createServer((req, res) => {
  console.log(req);
  procees.exit();
});

sever.listen(3000);
```
این باعث میشه وقتی به سرور یه ریکوِئستی برسه، این متد فراخوانی میشه و سرور ما خاموش میشه.

[صفحه قبلی](004%20The%20Node%20Lifecycle%20&%20Event%20Loop.md)

[صفحه بعدی](006%20Understanding%20Requests.md)
