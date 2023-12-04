## SASS Kompilyatorlari

> Dart SASS - SASS ning asosiy kompilyatori bo’lib, tezda yangilanib turadi va omma tomonidan qo’llab quvatlanadi. ishlash bo’yicha eng tezi.
> 

> Node SASS - LibSass ya’niy C yordamida yopzilgan kompilyatornio’rab turuvchi (wrapper) hisoblanadi. Tezligi bo’yicha Dart SASS dan keyingi o’rinda turadi.
> 

> Dart SASS JS - Dart SASS ning JS ko’rinishi. Tepadagilardan sekin hisoblanadi
<hr>

#### VScode extention
##### Live Sass Compiler

> https://marketplace.visualstudio.com/items?itemName=glenn2223.live-sass

![Alt Text](/Lesson%201/example.png)

<hr>

#### NPM orqali

> npm install -g sass

- Yangi fayl ochib ichida scss code ni joylashtiramza

example code :

```
$font-stack: Helvetica, sans-serif;
$primary-color: #333;

body {
    font: 100% $font-stack;
    color: $primary-color;
    background-color: red;
}
```  


> Va undan song teminalda shu code ni bajaramiza bu code compilyatsa qiladi , yaniy scss dan css ga code ni o’giradi :)
```
sass file.scss file.css
sass file.scss file.css --watch
```