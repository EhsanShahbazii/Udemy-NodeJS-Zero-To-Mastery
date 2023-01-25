## 009 Finishing the Pug Template
الان می خوایم کمی داینامیک تر کنیم. می خوایم تو هر صفحه ای که رفتیم هم `title` اون صفحه عوض بشه و هم تو منو قسمتی که هستیم `active` بشه.

برای همین ما دو تا متغیر `pageTitle` و `path` می فرستیم برای فایل های `pug` و اونجا استفاده می کنیم. مثلا توی فایل `admin.js` به صورت زیر عمل می کنیم:
```js
router.get('/add-product', (req, res, next) => {
  res.render('add-product', { pageTitle: 'Add Product', path: '/admin/add-product' });
});

```
حالا توی فایل `main-layout.pug` به صورت زیر می نویسیم:
```pug
li.main-header__item
   a(href="/", class=(path === '/' ? 'active' : '')) Shop
li.main-header__item
   a(href="/admin/add-product", class=(path === '/admin/add-product' ? 'active' : '')) Add Product
 ```
 و برای تایتل صفحات هم به صورت زیر استفاد می کنیم:
 ```pug
 title #{pageTitle}
 ```
