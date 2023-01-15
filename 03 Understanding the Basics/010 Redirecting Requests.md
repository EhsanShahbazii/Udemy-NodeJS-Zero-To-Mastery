## 010 Redirecting Requests
می خوایم اینجا از یه ماژول دیگه به نام `fs` استفاده کنیم. فرضا یوزر یه دیتایی رو تو اینپوت نوشته و ما می خوایم اونو ذخیره کنیم.
```js
const http = require("http");
const fs = require("fs");

const server = http.createServer((req, res) => {
  res.setHeader("Content-Type", "text/html");
  const url = req.url;
  const method = req.method;
  if (url === "/") {
    res.write(`
    <form action="/message" method="POST">
    <input type="text" name="message">
    <button type="submit">Submit</button>
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
تا اینجا همان کد قبلی رو داریم فقط میایم ماژول `fs` رو ایمپورت می کنیم.
```js
  if (url === "/message" && method === "POST") {
    fs.writeFileSync("message.txt", "Hi Ehsan");
    res.statusCode = 302;
    res.setHeader("Location", "/");
    return res.end();
  }
```
فقط میایم بعد شرط اولی یه شرط دیگه میزاریم و می گیم اگه `"url === "/message` باشه یعنی ما به این روت فرستاده بشیم ببینیم اگه متد ما `method === POST` باشه بیا
یه فایل به اسم `message.txt` درست کن و محتواش رو `Hi Ehsan` قرار بده.
