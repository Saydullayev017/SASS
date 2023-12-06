### Properties - Xossalar

> SASS dagi xossalarning korinishi va ishlash tartibi CSS ning bilan bir xil hisoblanadi: brinchi xossaning nomi yozilib, undan so’ng ikki nuqta (:) qo’yilib, xossaning qiymati ko’rsatilib o’tiladi

- CSS
```
.circle {
	width: 100px;
	height: 100px;
	border-radius: 50px;
}
```
- SCSS
```
.circle {
	width: 100px;
	height: 100px;
	border-radius: 50px;
}
```

### Nesting
>Ko’pgina CSS xossalari bir xil prefeks bilan boshlanadi. Masalan: font-family, font-size va font-weight - bular hammasi font- prefeksiga ega. SASS yordamida prefiksni qayta-qayta yozmasdan, xossalari nesting qilish orqali ancha tartibli kod yozilishi imkonyati mavjud. Bu holatda tashqi xossa nomi ichki xossaga chiziqcha (-) bilan ajratilib kompilyatsa bo’ladi.

- SCSS 
```
.heading {
	font: {
		family: 'Helvetica', serif;
		size: 48px;
		weight: 800;
	}
}
```
-CSS 
```
.heading {
  font-family: "Helvetica", serif;
  font-size: 48px;
  font-weight: 800;
}
```
### Short hands
> bzaga yenglik bo’lishi uchun shortHand lar mavjud bular bzada exampleda ko’rib turganimzadek margin: auto {} deb yozdik bu yerda bizada avtomatiga margin: auto; avtomat uzgaradi.

- SCSS
```
.info-page{ 
	margin: auto {
		bottom: 10px;
		top: 2px;
	}
}
```
- CSS
```
.info-page {
  margin: auto;
  margin-bottom: 10px;
  margin-top: 2px;
}

```
> [Style Rules Documentation](https://sass-lang.com/documentation/style-rules/)