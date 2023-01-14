### 007 Sending Responses
می تونیم ریسپانس هم بفرستیم. اینجا با متد های ریسپانس که `setHeader` و `write` هست آشنا می شیم.
```js
const http = require("http");

const server = http.createServer((req, res) => {
  res.setHeader('Content-Type', 'text/html');
  res.write(`
  <h2>Ehsan</h2>
  <h3>FrontEnd Developer</h3>
  `);
});

server.listen(3000);
```
که الان اگه به پورت `3000` بریم می بینیم که دو تا تگ `h2` و `h3` وجود داره.
