## 009 Routing Requests
می تونیم ریکوئست ها رو روت بندی کنیم. به این شکل که مثلا اگه یوزر به روت `message` رفت، اون صفحه براش  لود بشه.
```js
const http = require("http");

const server = http.createServer((req, res) => {
  res.setHeader("Content-Type", "text/html");
  const url = req.url;
  if (url === "/") {
    res.write(`
    <input type="text" name="message">
    <button type="submit"></button>
    </form>
    `);
    return res.end();
  }
  res.write(`
    <h2>Hello Dear</h2>
    `);
  res.end();
});

server.listen(3000);
```
اگه یوزر دکمه `submit` رو بزنه، هدایت میشه به صفحه `message`.
