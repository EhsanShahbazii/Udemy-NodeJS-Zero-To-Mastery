## 006 Express.js - Looking Behind the Scenes
تو این قسمت قراره یه ذره تو مفاهیم عمیق بشیم. برای همین ریپوی `express` رو یه نگاهی می کنیم. ما تو `response` از متد `( )send` استفاده کردیم.

اگه به فایل تو آدرس `express/lib/response.js` بریم میبینیم که از خط `111` متد `send` رو میبینیم:
```js
res.send = function send(body) {
  var chunk = body;
  var encoding;
  var req = this.req;
  var type;

  // settings
  var app = this.app;

  // allow status / body
  if (arguments.length === 2) {
    // res.send(body, status) backwards compat
    if (typeof arguments[0] !== 'number' && typeof arguments[1] === 'number') {
      deprecate('res.send(body, status): Use res.status(status).send(body) instead');
      this.statusCode = arguments[1];
    } else {
      deprecate('res.send(status, body): Use res.status(status).send(body) instead');
      this.statusCode = arguments[0];
      chunk = arguments[1];
    }
  }

...
```
که میاد اول تایپ `body` پیدا میکنه و تو مرحله دوم میاد `Content-Type` رو ست میکنه.
```js
switch (typeof chunk) {
    // string defaulting to html
    case 'string':
      if (!this.get('Content-Type')) {
        this.type('html');
      }
      break;
    case 'boolean':
    case 'number':
    case 'object':
      if (chunk === null) {
        chunk = '';
      } else if (Buffer.isBuffer(chunk)) {
        if (!this.get('Content-Type')) {
          this.type('bin');
        }
      } else {
        return this.json(chunk);
      }
      break;
  }

  // write strings in utf-8
  if (typeof chunk === 'string') {
    encoding = 'utf8';
    type = this.get('Content-Type');

    // reflect this in content-type
    if (typeof type === 'string') {
      this.set('Content-Type', setCharset(type, 'utf-8'));
    }
  }
...
```
حتی میتونیم به جای اینکه خودمون سرور رو درست کنیم، از متد `( )listen` استفاده کنیم:
```js
app.listen = function listen() {
  var server = http.createServer(this);
  return server.listen.apply(server, arguments);
};
```
پس میتونیم فقط عبارت زیر رو بنویسیم و سرور درست کنیم:
```js
app.listen();
```
