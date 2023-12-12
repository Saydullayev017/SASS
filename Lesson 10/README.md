#### CSS At-Rules

At-правила
Большая часть дополнительных функций Sass представлена ​​в виде новых at-правил, которые он добавляет поверхCSS: 

> @use загружает миксины, функции и переменные из других таблиц стилей Sass и объединяет CSS из нескольких таблиц стилей вместе.

> @forward загружает таблицу стилей Sass и делает свои примеси, функции и переменные доступными, когда ваша таблица стилей загружено правило @use.

> @import расширяет at-правило CSS для загрузки стили, примеси, функции и переменные из других таблиц стилей.

> @mixin и @include позволяют легко повторно использовать фрагменты стилей.

> @function определяет пользовательские функции, которые может использоваться в SassScript выражениях.

> @extend позволяет селекторам наследовать стили. от одного другого.

> @at-root помещает в него стили корень CSS документа.

> @error приводит к сбою компиляции с сообщение об ошибке .

> @warn печатает предупреждение без остановки компиляция полностью.

> @debug печатает сообщение для целей отладки .

> Правила управления потоком, такие как @if, @each, @for и @while контролировать, будут ли и сколько раз создаваться стили .

Sass также имеет особое поведение для обычного CSS at-правил: они могут содержать интерполяция, и их можно вкладывать в правила стиля. Некоторые из них, как @media и @supports также позволяют использовать SassScript непосредственно в само правило без интерполяции.

Sass поддерживает все at-правила, которые являются частью CSS. Чтобы оставаться гибким и совместимый с будущими версиями CSS, Sass имеет общую поддержку, по умолчанию охватывает почти все at-правила. At-правило CSS записывается @<name> <value>, @<name> { ... } или <а я=9>. Имя должно быть идентификатор, а значение (если оно существует) может быть практически любым. Оба имя и значение могут содержать интерполяцию.@<name> <value> { ... }

```
@namespace svg url(http://www.w3.org/2000/svg);

@font-face {
  font-family: "Open Sans";
  src: url("/fonts/OpenSans-Regular-webfont.woff2") format("woff2");
}

@counter-style thumbs {
  system: cyclic;
  symbols: "\1F44D";
}
```
```
@charset "UTF-8";
@namespace svg url(http://www.w3.org/2000/svg);
@font-face {
  font-family: "Open Sans";
  src: url("/fonts/OpenSans-Regular-webfont.woff2") format("woff2");
}
@counter-style thumbs {
  system: cyclic;
  symbols: "👍";
}

```
Если CSS at-правило вложено в правило стиля, они автоматически меняются местами. позиции так, чтобы at-правило находилось на верхнем уровне вывода CSS, а правило стиля находится внутри него. Это позволяет легко добавлять условные стили без необходимость переписать селектор правила стиля.

```
.print-only {
  display: none;

  @media print { display: block; }
}
```

```
.print-only {
  display: none;
}
@media print {
  .print-only {
    display: block;
  }
}
```

### @media
Правило выполняет все вышеперечисленное и даже больше. Помимо разрешения интерполяция позволяет использовать выражения SassScript непосредственно в функционалзапросы.@media 

```
$layout-breakpoint-small: 960px;

@media (min-width: $layout-breakpoint-small) {
  .hide-extra-small {
    display: none;
  }
}
```
```
@media (min-width: 960px) {
  .hide-extra-small {
    display: none;
  }
}

```
Когда это возможно, Sass также объединит медиа-запросы, вложенные в один другой, чтобы упростить поддержку браузеров, которые еще не поддерживают вложенные @media правила.

```
@media (hover: hover) {
  .button:hover {
    border: 2px solid black;

    @media (color) {
      border-color: #036;
    }
  }
}
```
```
@media (hover: hover) {
  .button:hover {
    border: 2px solid black;
  }
}
@media (hover: hover) and (color) {
  .button:hover {
    border-color: #036;
  }
}
```
@supports@supports постоянная ссылка
Правило также позволяет использовать выражения SassScript в объявлениезапросов.@supports 

```
@mixin sticky-position {
  position: fixed;
  @supports (position: sticky) {
    position: sticky;
  }
}

.banner {
  @include sticky-position;
}
```
```
.banner {
  position: fixed;
}
@supports (position: sticky) {
  .banner {
    position: sticky;
  }
}

```
#### @keyframes
постоянная ссылка
Правило работает так же, как общее правило at, за исключением того, что оно дочерние правила должны быть допустимыми правилами ключевых кадров (, или ), а не чем обычныеселекторы.@keyframes<number>%from

```
@keyframes slide-in {
  from {
    margin-left: 100%;
    width: 300%;
  }

  70% {
    margin-left: 90%;
    width: 150%;
  }

  to {
    margin-left: 0%;
    width: 100%;
  }
}
```

```
@keyframes slide-in {
  from {
    margin-left: 100%;
    width: 300%;
  }
  70% {
    margin-left: 90%;
    width: 150%;
  }
  to {
    margin-left: 0%;
    width: 100%;
  }
}
```