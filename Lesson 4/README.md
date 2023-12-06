### Variables - Переменные
> SASS o’zgaruvchilar juda oddiy ko’rinishga ega: dollar simvoli ($) bilan boshlanadigon nomga qiymat ko’rsatillishing o’zi kifoya. O’zgaruvchilar oddiy bo’lishiga qaramay, ular SASS ning eng foydali jihati hisoblanadi. Ular yordamida qaytarilishuini kamaytirish (reduce duplication), murakkab matimatik amallar bajarish va yana ko’pgina vazifalarni bajaradi.
- SCSS
```
// Variables
$border-dark: rgba($base-color, 0.88);
$border-type: solid;

.alert {
  border: 1px $border-type $border-dark;
}
```
- CSS
```
.alert {
  border: 1px solid rgba(198, 83, 140, 0.88);
}
```
### Scope - Объем

> Переменные, объявленные на верхнем уровне таблицы стилей, являются глобальными. Это означает что к ним можно получить доступ в любом месте модуля после их объявления. Но это верно не для всех переменных. Объявленные в блоках (фигурные скобки в SCSS или код с отступом в Sass) обычно являются локальными и могут только быть доступным внутри блока они были объявлены.
- SCSS
```
// global value
$primary-color: red;

.section {
    // local value
    $secondary-color: green;
    color: $border-dark;
    background-color: $secondary-color;
}
```
- CSS
```
.alert {
  border: 1px solid black;
}

.section {
  color: black;
  background-color: green;
}
```
### Shadowing - Слежение
> Локальные переменные могут даже быть объявлены с тем же именем, что и глобальная переменная. Если такое случается, на самом деле есть две разные переменные с одинаковым именем: одна локальный и один глобальный. Это помогает гарантировать, что автор, записывающий локальную переменную случайно не меняет значение глобальной переменной, они даже не осведомлен о.

- SCSS
```
// global
$variable: global value;

.content {
  // locaL 
  $variable: local value;
  value: $variable;
}

.sidebar {
  // global
  value: $variable;
}
```
- CSS
```
.content {
  value: local value;
}

.sidebar {
  value: global value;
}/*# sourceMappingURL=style.css.map */
```