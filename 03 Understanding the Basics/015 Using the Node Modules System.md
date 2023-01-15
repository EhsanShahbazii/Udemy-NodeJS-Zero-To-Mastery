## 015 Using the Node Modules System
اینجا قراره ما کد رو ماژولار بنویسیم. برای همین توی فایل `app.js` تغییراتی اعمال می کنیم و نهایت به صورت زیر میشه:
```js
const http = require("http");

const requestHandler = require("./routes");

const server = http.createServer(requestHandler);

server.listen(3000);
```
بقیه کد هارو توی فایلی به اسم `routes.js` می نویسیم و ایمپورت می کنیم.
```js
const fs = require("fs");

const requestHandler = (req, res) => {
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
  if (url === "/message" && method === "POST") {
    const body = [];
    req.on("data", (chunk) => {
      body.push(chunk);
      console.log(chunk);
    });
    return req.on("end", () => {
      const parsBody = Buffer.concat(body).toString();
      console.log(parsBody);
      const message = parsBody.split("=")[1];
      fs.writeFile("message.txt", message, (err) => {
        res.statusCode = 302;
        res.setHeader("Location", "/");
        return res.end();
      });
    });
  }
  res.write(`
    <h2>Hello Dear</h2>
    `);
  res.end();
};

module.exports = requestHandler;
```
برای دسترسی به فایل `routes.js` تو `app.js` باید این ماژول رو اکسپورت کنیم برای همین ما چند تا روش داریم که یکیش `module.exports` هست.
