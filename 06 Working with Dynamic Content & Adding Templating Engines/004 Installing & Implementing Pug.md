## 004 Installing & Implementing Pug
تو این قسمت قراره که ما یک `templating engines` به اسم `pug` نصب کنیم. برای همین کامند `npm i --save pug` رو تو کنسول می زنیم.

برای اینکه به `express` بفهمونیم که یک `template engines` داریم و ازش استفاده کن، تو فایل `app.js` از متد `set` استفاده می کنیم.
```js
const app = express();

app.set("view engine", "pug");
app.set("views", "views");
```
تو آرگومان `view engine` ما اسم موتور رو می نویسیم و تو دومی `views` پوشه ای که قراره فایل ها رندر بشه رو می نویسیم. یه فایل به اسم `shop.pug` درست می کنیم و می نویسیم:
```pug
doctype html
html(lang="en")
    head
        meta(charset="UTF-8")
        meta(http-equiv="X-UA-Compatible", content="IE=edge")
        meta(name="viewport", content="width=device-width, initial-scale=1.0")
        link(rel="stylesheet", href="/css/main.css")
        link(rel="stylesheet", href="/css/product.css")
        title shop
    body 
        header.main-header 
            nav.main-header__nav 
                ul.main-header__item-list 
                    li.main-header__item 
                        a.active(href="/") Shop 
                    li.main-header__item 
                        a.active(href="/") Add Product      
```
بعد برای رندر کردن این فایل می ریم قسمتی که قراره این رو به کاربر نشون بدیم و از متد `render` استفاده می کنیم.
```js
router.get("/", (req, res, next) => {
  res.render("shop");
});
```
