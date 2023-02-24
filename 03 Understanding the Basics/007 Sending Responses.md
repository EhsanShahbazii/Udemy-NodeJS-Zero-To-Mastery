## 007 Sending Responses
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

## گزیده ای از رفرنس ها
متد `setHeader` مثال هایی به صورت زیر دارد:
```js
response.setHeader('Content-Type', 'text/html');
response.setHeader('Content-Length', Buffer.byteLength(body));
response.setHeader('Set-Cookie', ['type=ninja', 'language=javascript']);

const contentType = response.getHeader('content-type');
// contentType is 'text/html'

const contentLength = response.getHeader('Content-Length');
// contentLength is of type number

const setCookie = response.getHeader('set-cookie');
// setCookie is of type string[]
```
[صفحه قبلی](006%20Understanding%20Requests.md)

[صفحه بعدی](009%20Routing%20Requests.md)
