### коменты и специальные функции

#### В SCSS 
SCSS постоянной ссылке
Комментарии в SCSS работают аналогично комментариям на других языках, например JavaScript. Однострочные комментарии начинаются с // и продолжаются до конца строки. Ничто в однострочном комментарии не создается как CSS; что касается Sass, их может и не быть. Их еще называют немыми комментариями, потому что они не создают никакогоCSS. 

Многострочные комментарии начинаются с /* и заканчиваются следующим */. Если многострочный комментарий где-то написан, что оператор разрешен, это скомпилирован в комментарий CSS. Напротив, их еще называют громким комментарием. с молчаливыми комментариями. Многострочный комментарий, скомпилированный в CSS, может содержать интерполяция, которая будет оцениваться перед компиляцией комментария.

По умолчанию многострочные комментарии будут удалены из скомпилированного CSS в сжатый режим. Однако если комментарий начинается с /*!, он всегда будет включен в вывод CSS .

```
// This comment won't be included in the CSS.

/* But this comment will, except in compressed mode. */

/* It can also contain interpolation:
* 1 + 1 = #{1 + 1} */

/*! This comment will be included even in compressed mode. */

p /* Multi-line comments can be written anywhere
  * whitespace is allowed. */ .sans {
  font: Helvetica, // So can single-line comments.
        sans-serif;
}
```

#### В SASS
В постоянной ссылке Sass
Комментарии с синтаксисом с отступом работают немного по-другому: они на основе отступов, как и остальной синтаксис. Например, SCSS, тихие комментарии. написанные с помощью //, никогда не создаются как CSS, но в отличие от SCSS.// также закомментировано все с отступом под отверстием  

Синтаксические комментарии с отступом, начинающиеся с /*, работают с отступом так же способом, за исключением того, что они скомпилированы в CSS. Поскольку объем комментария в зависимости от отступа закрывающий */ не является обязательным. Также как SCSS, /* комментарии могут содержать интерполяцию и могут начинаться с /*!, чтобы избежать удалено в сжатом режиме.

Комментарии также можно использовать внутри выражений в синтаксисе с отступом. В этом В этом случае они имеют точно такой же синтаксис, как и вSCSS. 

```
Объяснять
// This comment won't be included in the CSS.
  This is also commented out.

/* But this comment will, except in compressed mode.

/* It can also contain interpolation:
  1 + 1 = #{1 + 1}

/*! This comment will be included even in compressed mode.

p .sans
  font: Helvetica, /* Inline comments must be closed. */ sans-serif
```

#### url()
URL() постоянная ссылка
Функция обычно используется в CSS, но у него другой синтаксис чем другие функции: он может принимать либо заключенный в кавычки , либо не заключенный в кавычки URL. Потому что без кавычек URL не является допустимым выражением SassScript, Sass требует специальной логики для разобратьего.url() 

Если аргумент url() является допустимым URL без кавычек, Sass анализирует его как есть, хотя интерполяция также может использоваться для внедрения значений SassScript. Если это недопустимый URL, например, если он содержит переменные или функция вызывает — он анализируется как обычная простая CSS функция  позвонить.
### SCSS
```
$roboto-font-path: "../fonts/roboto";

@font-face {
    // This is parsed as a normal function call that takes a quoted string.
    src: url("#{$roboto-font-path}/Roboto-Thin.woff2") format("woff2");

    font-family: "Roboto";
    font-weight: 100;
}

@font-face {
    // This is parsed as a normal function call that takes an arithmetic
    // expression.
    src: url($roboto-font-path + "/Roboto-Light.woff2") format("woff2");

    font-family: "Roboto";
    font-weight: 300;
}

@font-face {
    // This is parsed as an interpolated special function.
    src: url(#{$roboto-font-path}/Roboto-Regular.woff2) format("woff2");

    font-family: "Roboto";
    font-weight: 400;
}
```
### CSS
```
@font-face {
  src: url("../fonts/roboto/Roboto-Thin.woff2") format("woff2");
  font-family: "Roboto";
  font-weight: 100;
}
@font-face {
  src: url("../fonts/roboto/Roboto-Light.woff2") format("woff2");
  font-family: "Roboto";
  font-weight: 300;
}
@font-face {
  src: url(../fonts/roboto/Roboto-Regular.woff2) format("woff2");
  font-family: "Roboto";
  font-weight: 400;
}
```

Функция element() определена в спецификации CSS, и поскольку ее идентификаторы могут быть проанализированы как цвета, они требуют специального анализа.

expression() и функции, начинающиеся с progid:, являются устаревшими. Функции Internet Explorer, использующие нестандартный синтаксис. Хотя они нет более не поддерживаемый современными браузерами, Sass продолжает анализировать их на предмет обратной совместимости.

Sass допускает любой текст в этих вызовах функций, включая вложенные круглые скобки. Ничто не интерпретируется как выражение SassScript, за исключением того, что интерполяцию можно использовать для ввода динамических значений.

```
$logo-element: logo-bg;

.logo {
  background: element(##{$logo-element});
}
```