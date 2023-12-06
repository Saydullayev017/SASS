### Selectors - Селекторы

> Style qoidalari SASS’ning asosi hisoblanadi va ularning ishlash tartibi CSS’niki bilan bir xil hisoblanadi. brinchi bo’lib style bermoqchi bo’lgan elementimiz tanlab olinadi va unga CSS xossalarini ko’rsatish orqali style beriladi
- SCSS :
```
.button { 
	padding: 3px 10px;
	font-size: 12px;
	border-radius: 3px;
	border: 1px solid #e1e4e8;
}
```
- CSS :
```
.button { 
	padding: 3px 10px;
	font-size: 12px;
	border-radius: 3px;
	border: 1px solid #e1e4e8;
}
```
### Nesting - Вложение
> Но Sass хочет сделать вашу жизнь проще. Вместо того, чтобы повторять одно и то же селекторов снова и снова, вы можете писать одни правила стиля внутри других. Sass автоматически объединит селектор внешнего правила с селектором внутреннего правила.
- SCSS :
```
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  li { display: inline-block; }

  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}
```
- CSS :
```
nav ul {
  margin: 0;
  padding: 0;
  list-style: none;
}
nav li {
  display: inline-block;
}
nav a {
  display: block;
  padding: 6px 12px;
  text-decoration: none;
	}
```
> Вложенные правила очень полезны, но они также могут затруднить визуализацию. сколько CSS вы на самом деле генерируете. Чем глубже вы гнездитесь, тем больше пропускная способность, необходимая для обслуживания вашего CSS, и тем больше работы требуется браузеру для отрендерите это. Держите эти селекторы поверхностными! обычно вложенность не советуется больше чем 3 вложености !!!
### Selector lists - Списки выбора
> Вложенные правила позволяют грамотно обрабатывать списки селекторов (то есть разделенные запятыми селекторы). Каждый комплексный селектор (те, что между запятыми) является вложенным. отдельно, а затем снова объединяются в список списка.
- SCSS :
```
.alert, .warning {
  ul, p {
    margin-right: 0;
    margin-left: 0;
    padding-bottom: 0;
  }
}
```
- CSS :
```
.alert ul, .alert p, .warning ul, .warning p {
  margin-right: 0;
  margin-left: 0;
  padding-bottom: 0;
}
```
### Combinators - Селекторные комбинаторы
> Вы также можете вкладывать селекторы, использующие комбинаторы. Вы можете поставить комбинатор в конце внешнего селектора, в начале внутреннего селектор или даже все по отдельности между двумя.
- SCSS
```
ul > {
  li {
    list-style-type: none;
  }
}

h2 {
  + p {
    border-top: 1px solid gray;
  }
}

p {
  ~ {
    span {
      opacity: 0.8;
    }
  }
}
```
- CSS
```

ul > li {
  list-style-type: none;
}

h2 + p {
  border-top: 1px solid gray;
}

p ~ span {
  opacity: 0.8;
}
```