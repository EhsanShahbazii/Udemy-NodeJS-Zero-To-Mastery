## 015 Working on the Layout with Partials
توی موتور قالب `ejs` ما `layout` نداریم. برای هندل کردن این موضوع می تونیم از کامپوننت شکل بودن `ejs` استفاده کنیم. به این صورت که قسمت هایی که لازم داریم رو
توی پوشه `includes` درست می کنیم و هر جا که نیاز هست استفاده می کنیم. مثلا فایل `head.ejs` به صورت زیر است:
```ejs
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title><%= pageTitle %></title>
    <link rel="stylesheet" href="/css/main.css">
```
الان ما می آیم جایی که می خوایم از این استفاده کنیم از سینتکس `<% ( )include -%>` استفاده می کنیم و آدرس فایل رو به این می دیم:
```ejs
<%- include('includes/head.ejs') %>
</head>

<body>
    <%- include('includes/navigation.ejs') %>
    <h1>Page Not Found!</h1>

<%- include('includes/end.ejs') %>
```
