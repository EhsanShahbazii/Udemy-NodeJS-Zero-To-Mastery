## 007 Handling Different Routes
تو این قسمت قراره نحوه روت بندی رو بفهمیم. برای همین با متد `( )use` که پارامتر های `(path, ...callbacks)use` رو میگیره.
```js
const express = require("express");

const app = express();

app.use("/", (req, res, next) => {
  console.log("always run!");
  next();
});

app.use("/product", (req, res, next) => {
  console.log("product page!");
});

app.use("/", (req, res, next) => {
  console.log("home page!");
});

app.listen();
```
