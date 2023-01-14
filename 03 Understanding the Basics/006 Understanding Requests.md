### 006 Understanding Requests
ریکوئست متد های خیلی زیادی داره که اینجا با سه تاش به نام های `url`، `method` و `header` آشنا می شیم.

```js
const http = require("http");

const server = http.createServer((req, res) => {
  console.log(req.url, req.method, req.headers);
});

server.listen(3000);
```
که اگه تو کنسول نگاه کنیم می بینیم که مقادیر `url` ، `method` و `header` به صورت زیر هستن:
```js
url : /
method: GET
header: {
  host: 'localhost:3000',
  connection: 'keep-alive',
  'sec-ch-ua': '"Chromium";v="108", "Opera";v="94", "Not)A;Brand";v="99"',
  'sec-ch-ua-mobile': '?0',
  'sec-ch-ua-platform': '"Windows"',
  'upgrade-insecure-requests': '1',
  'user-agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) 
   Chrome/108.0.0.0 Safari/537.36 OPR/94.0.0.0',
   accept: 'text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;
   q=0.8,application/signed-exchange;v=b3;q=0.9',
  'sec-fetch-site': 'none',
  'sec-fetch-mode': 'navigate',
  'sec-fetch-user': '?1',
  'sec-fetch-dest': 'document',
  'accept-encoding': 'gzip, deflate, br',
  'accept-language': 'en-US,en;q=0.9',
  cookie: 'Webstorm-207d96f1=74c3acf4-b870-4723-9c77-f7ea2dd96f2a'
}
```
