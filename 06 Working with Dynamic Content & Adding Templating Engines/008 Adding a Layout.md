## 008 Adding a Layout
خب بعضی وقتا کامپوننت هایی وجود دارن که باید تو بعضی سند های دیگه اونا نوشته بشه. برای همین توی `pug` ویژگی وجود داره که با اون میتونیم این کار ها رو انجام بدیم.

مثلا توی پوشه `layouts` ما یه چهار چوب اصلی می سازیم به صورت زیر. مثلا فایل `main-layout.pug`.
```pug
<!DOCTYPE html>
html(lang="en")
    head
        meta(charset="UTF-8")
        meta(name="viewport", content="width=device-width, initial-scale=1.0")
        meta(http-equiv="X-UA-Compatible", content="ie=edge")
        title #{pageTitle}
        link(rel="stylesheet", href="/css/main.css")
        block styles
    body   
        header.main-header
            nav.main-header__nav
                ul.main-header__item-list
                    li.main-header__item
                        a(href="/", class=(path === '/' ? 'active' : '')) Shop
                    li.main-header__item
                        a(href="/admin/add-product", class=(path === '/admin/add-product' ? 'active' : '')) Add Product
        block content
```
اینجا ما قسمت هایی که داینامیک هست رو با کلید `block` نشون می دیم و تو سند های دیگه این بلاک ها رو می فرستیم به این فایل که نشون بده.

الان برای استفاده مثلا توی فایل `add-product.pug` به صورت زیر می نویسیم و از کلید `extends` استفاده می کنیم تا به اون چهار چوب اصلی وصل بشیم.
```pug
extends layouts/main-layout.pug

block styles
    link(rel="stylesheet", href="/css/forms.css")
    link(rel="stylesheet", href="/css/product.css")

block content
    main
        form.product-form(action="/admin/add-product", method="POST")
            .form-control
                label(for="title") Title
                input(type="text", name="title")#title
            button.btn(type="submit") Add Product
```
