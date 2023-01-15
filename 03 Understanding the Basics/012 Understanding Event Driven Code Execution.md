## 012 Understanding Event Driven Code Execution
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
      fs.writeFileSync("message.txt", message);
    });
    res.statusCode = 302;
    res.setHeader("Location", "/");
    return res.end();
  }
  res.write(`
    <h2>Hello Dear</h2>
    `);
  res.end();
});

server.listen(3000);
```
