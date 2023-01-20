## 013 Creating HTML Pages
این قسمت قراره که فایل های `html` رو درست کنیم و به یوزر بفرستیم.
 
 محتوای فایل `shop` به صورت زیر است:
```html
<body>
    <header>
        <nav>
            <ul>
                <li><a href="/">Shop</a></li>
                <li><a href="/admin/add-product">Add Product</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <h1>My Products</h1>
        <p>List of all the products...</p>
    </main>


</body>
```
و همچنین محتوای فایل `add-product` هم به شرح زیر است:
```html
<body>
    <header>
        <nav>
            <ul>
                <li><a href="/">Shop</a></li>
                <li><a href="/admin/add-product">Add Product</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <form action="/add-product" method="POST">
            <input type="text" name="title">
            <button type="submit">Add Product</button>
        </form>
    </main>


</body>
```
