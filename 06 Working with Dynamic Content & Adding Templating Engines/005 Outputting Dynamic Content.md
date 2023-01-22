## 005 Outputting Dynamic Content
اینجا قراره که دیتایی از یوزر بگیریم و اون رو نمایش بدیم به صورت داینامیک. می آیم تو فایل `shop.js` اطلاعات رو به صورت `props` می فرستیم.
```js
router.get("/", (req, res, next) => {
  const products = adminData.products;
  res.render("shop", { prods: products, title: "Shop" });
});
```
اینجا ما تو آرگومان دوم تابع `render` دیتا هامون رو با کلید های مشخصی می فرستیم: توی فایل `shop.pug` هم به صورت زیر استفاده می کنیم:
```pug
doctype html
    head
        title #{title}
    body    
        main
            if prods.length > 0
                .grid 
                    each product in prods
                        article.card.product-item
                            header.card__header
                                h1.product__title #{product.title}
                            .card__image
                                img(src="https://cdn.pixabay.com/photo/2016/03/31/20/51/book-1296045_960_720.png", alt="A")
                            .card__content
                                h2.product__price $19.99
                                p.product__description A very interesting book about so many even more interesting things!
                            .card__actions
                                button.btn Add to Cart              
```
