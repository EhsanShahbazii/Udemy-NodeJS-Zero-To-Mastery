## 003 Installing Express.js
برای استفاده از پکیج `express.js` به صورت زیر می نویسیم و کامند `npm i --save express` رو توی کنسول می زنیم:
```js
const http = require("http");

const express = require("express");

const app = express();

const server = http.createServer(app);

server.listen(3000);
```
