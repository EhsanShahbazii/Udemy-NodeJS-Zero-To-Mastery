## 011 Parsing Request Bodies
الان می خوایم با نحوه دریافت و کار کردن با دیتایی که یوزر فرستاده آشنا بشیم. برای همین ما از متد جدید ریکوئست مثل `( )on` آشنا بشیم.

همون کد های قبلی رو داریم فقط تو شرط دوم این رو می نویسیم:
```js
if (url === "/message" && method === "POST") {
    const body = [];
    req.on("data", (chunk) => {
      body.push(chunk);
    });
    req.on("end", () => {
      const parsBody = Buffer.concat(body).toString();
      const message = parsBody.split("=")[1];
      fs.writeFileSync("message.txt", message);
    });
    res.statusCode = 302;
    res.setHeader("Location", "/");
    return res.end();
  }
```
متد `("data")on` میاد هر زمان که دیتایی از طرف یوزر می گیره رو توی متغیر `body` ذخیره می کنه. وقتی که دیگه این استریم دیتا تموم بشه متد `("end")on` کار می کنه.

توی این متد هم ما میخوایم دیتایی رو که گرفتیم رو ذخیره کنیم. ولی نوع دیتا متفاوته و میشه گفت `buffer` هست.

اگه یوزر توی اینپوت بنویسه `ehsan` و سابمیت رو بزنه، دیتا به این صورت گرفته میشه. توی `message` عنوانی که برای اینپوت نوشتیم `name=message`، دیتامون با این عنوان گرفته میشه.
```js
parseBody => <Buffer 6d 65 73 73 61 67 65 3d 65 68 73 61 6e>
message => message=ehsan
```
برای همین ما یه `split` می کنیم و دومین عنصر که دیتای ماست رو می گیریم.
