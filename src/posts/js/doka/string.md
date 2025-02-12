---
title: "Строка"
name: string
author: vindi-r
co-authors:
designers:
contributors:
summary:
---

## Кратко

Любые текстовые данные в JavaScript — это строки. Отдельного типа данных как «символ» не существует, это все равно тип строка, пусть и единичного размера.

## Как пишется

Есть несколько вариантов записи строки в переменную. Через одинарные или двойные кавычки и через обратный апостроф.

После примера будет показаны различия в записи через разные варианты:

```js
let str = "Строка текста"
let str2 = "Строка текста"
```

Все замечательно, пока не нужно записать перенос строки или двойную кавычку в тексте. Что тогда делать?

Для этого используется _экранирование_ 😎

```js
let str = 'Символ " означает кавычку'
let str2 = "Одинарная кавычка ' выглядит так"
let str3 = "Строка 1\nСтрока 2"
console.log(str) // Символ " означает кавычку
console.log(str2) // Одинарная кавычка ' выглядит так
console.log(str3) // Этот текст будет расположен на двух строчках
// Строка 1
// Строка 2
```

## Как это понять

Через строки происходит взаимодействие с пользователем. Показываются диалоговые окна, записывается реакция юзеров.

Хотя строка и простой тип данных, есть множество операций, как над целой строкой, так и над ее частями.

### 💡Длина строки

Часто используемая операция над строкой — вычисление ее длины:

```js
let str = "Строка какого-то текста неизвестной длины"
console.log(str.length) // 41
```

Один из вариантов использования — оповестить пользователя об ограничении максимальной длины сообщения:

<p class="codepen" data-height="265" data-theme-id="light" data-default-tab="html,result" data-user="vindi-r" data-slug-hash="QPBEjO" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="Строки - как понять">
  <span>See the Pen <a href="https://codepen.io/vindi-r/pen/QPBEjO">
  Строки - как понять</a> by vindi-r (<a href="https://codepen.io/vindi-r">@vindi-r</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

### 💡Доступ к элементам строки

Хоть строка и примитивный тип данных, можно получить доступ к каждому символу любой строки:

```js
let str = "Это строка"
console.log(str[4]) // с
```

Выглядит это, как обращение к элементу массива. Да похоже, но в отличие от массива — нельзя заменить конкретный символ в строке через такое обращение. Если очень нужно, то придется создать новую строку с измененным символом или [воспользоваться методом replace]().

### 💡Смена регистра

Для приведения строки к нижнему регистру используется метод toLowerCase(), а для приведения к верхнему — toUpperCase()

```js
console.log("СОБАКА".toLowerCase()) // собака
console.log("котик".toUpperCase()) // КОТИК
```

Зачем это нужно? К примеру, для нормализации текста, например в полях ввода:

<p class="codepen" data-height="265" data-theme-id="light" data-default-tab="html,result" data-user="vindi-r" data-slug-hash="zXLoJL" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="Строки - как понять">
  <span>See the Pen <a href="https://codepen.io/vindi-r/pen/zXLoJL">
  Строки - как понять</a> by vindi-r (<a href="https://codepen.io/vindi-r">@vindi-r</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

### 💡Поиск подстроки

Для поиска одной строки внутри другой есть метод indexOf()

```js
let str = "Строка текста ABCDEFGH"
let index = str.indexOf("ABC") // 14
let notFoundIndex = str.indexOf("test") // -1
```

Что дает эта информация? В переменной index появится номер позиции с которой начинается подстрока `ABC`. Если же поиск не удастся, то в переменной будет -1.

### 💡Взятие подстроки

Самый удобный способ получить подстроку это slice(). Метод slice может принимать один или два аргумента.

Если указаны два аргумента (start, end), то получится строка, которая начинается с символа start и заканчивается символом end.

Если указан один аргумент (start), то результатом будет строка, начинающаяся с символа start, но без ограничения по символам.

```js
let str = "Звук кота: мяу"
console.log(str.slice(0, 4)) // Звук
// из str взяты символы начиная с позиции 0 и до позиции 4
console.log(str.slice(-3)) // мяу
// из str взяты символы начиная с 3 последних и до конца строки
```

Также существуют методы substr и substring. Их использование менее удобно чем slice. Причина простая — методы называются похоже, и в некоторых случаях ведут себя похоже, а иногда совершенно по разному. Это приводит к путанице, вот пример:

```js
let str = "Звук кота: мяу"
console.log(str.substr(0, 4)) // Звук
console.log(str.substr(-3)) // мяу
// Те же индексы при упортреблении substring
console.log(str.substring(0, 4)) // Звук
console.log(str.substring(-3)) // Звук кота: мяу
// substring игнорирует отрицательные индексы, считает, что там 0
```

При взятии подстроки с нулевого элемента все методы ведут себя похоже. А вот в случае с ненулевым начальным индексом уже заметна разница.

```js
let str = "Мяу говорит кот, облизываясь"
// Будет взята подстрока начиная с индекса 4 по 11
console.log(str.slice(4, 11)) // говорит
// Будет взята подстрока начиная с индекса 4, в количестве 11 символов
console.log(str.substr(4, 11)) // говорит кот
// Будет взята подстрока начиная с индекса 4 по 11
console.log(str.substring(4, 11)) // говорит
```

Чтобы не путаться, лучше использовать slice, так как он поддерживает отрицательные индексы взятия подстроки, и его сложно перепутать с другими методами. Это удобно.

К примеру, можно модифицировать то, что пишет пользователь, по каким-либо правилам:

<p class="codepen" data-height="265" data-theme-id="light" data-default-tab="js,result" data-user="vindi-r" data-slug-hash="zXLZLN" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="Строки - как понять">
  <span>See the Pen <a href="https://codepen.io/vindi-r/pen/zXLZLN">
  Строки - как понять</a> by vindi-r (<a href="https://codepen.io/vindi-r">@vindi-r</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

### 💡Замена подстроки

Для простой замены одной части строки на другой существует метод replace()

```js
let str = "Яблоко - вкусный овощ"
let correct = str.replace("овощ", "фрукт")
let notChanged = str.replace("апельсин", "банан")
console.log(correct) // Яблоко - вкусный фрукт
console.log(notChanged) // Яблоко - вкусный овощ
```

Если строка на замену не найдена, то никакой замены не произойдет. Поэтому можно без страха пробовать заменить данные, не боясь, что программа остановится из-за ошибки.

Метод replace() заменяет подстроку только один раз. Чтобы изменить более одного раза необходимо использовать регулярные выражения или циклы.

```js
let str = "Какова цена яблока? Какого яблока? Я их не продаю."
let correct = str.replace(/яблока/g, "помидора")
console.log(str) // Какова цена яблока? Какого яблока? Я их не продаю.
console.log(correct) // Какова цена помидора? Какого помидора? Я их не продаю.
```

### 💡Сравнение строк

Строки сравниваются между собой посимвольно по следующему алгоритму.

Сравниваем строки s1 и s2.

1. Сначала сравниваются символы `s1[0]` и `s2[0]`. Если они разные, то возвращается `true` или `false`.
2. Потом сравниваются символы `s1[1]` и `s2[1]` и так далее, пока символы не будут разными. Когда такая пара найдется, то в результате сравнения вернется `true` или `false`. Если какая-то строка закончилась, то она считается меньшей, а если закончились обе — они, по итогу, равны.

Для сравнения одного символа с другим используется код символов в [Unicode таблице.](https://unicode-table.com/ru/)

## В работе

{% include "authors/vindi-r/in-work.njk" %}

🛠При работе с формами и вводом значений следует очищать поля ввода от замыкающих пробелов. Например если в поле ввода e-mail окажутся пробелы по концам — есть шанс что пользователь этого не увидит, а у нас сохранится неправильный адрес почты.

❗️Не используй этот принцип для обработки паролей!

<p class="codepen" data-height="265" data-theme-id="light" data-default-tab="html,result" data-user="vindi-r" data-slug-hash="ZZjrzB" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="Строки - в работе">
  <span>See the Pen <a href="https://codepen.io/vindi-r/pen/ZZjrzB">
  Строки - в работе</a> by vindi-r (<a href="https://codepen.io/vindi-r">@vindi-r</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

🛠Множественная замена в строке возможна через цикл или через регулярные выражения:

```js
let str = "Яблоко - вкусный овощ. Яблоко - вкусный овощ. Яблоко - вкусный овощ"
let hasApple = str.indexOf("Яблоко") !== -1
while (hasApple === true) {
  str = str.replace("Яблоко", "Помидор")
  hasApple = str.indexOf("Яблоко") !== -1
}
console.log(str) // Помидор - вкусный овощ. Помидор - вкусный овощ. Помидор - вкусный овощ
```

Для решения задачи по смене яблок на помидоры код выглядит слишком избыточно. Вариант с replace через регулярные выражения проще и удобнее, но для этого нужно изучить базовый синтаксис использования регулярных выражений.

```js
let str = "Яблоко - вкусный овощ. Яблоко - вкусный овощ. Яблоко - вкусный овощ"
let changedStr = str.replace(/Яблоко/g, "Помидор")
console.log(changedStr) // Помидор - вкусный овощ. Помидор - вкусный овощ. Помидор - вкусный овощ
```

🛠Сравнение чисел: Если числа представлены в виде строк, то может получится неожиданный результат, например 2 будет больше чем 14 🤖

Поэтому если тебе нужно сравнить два числа, то их стоит принудительно приводить к числовому типу:

<p class="codepen" data-height="265" data-theme-id="light" data-default-tab="js,result" data-user="vindi-r" data-slug-hash="JVBLQG" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="Строки - в работе">
  <span>See the Pen <a href="https://codepen.io/vindi-r/pen/JVBLQG">
  Строки - в работе</a> by vindi-r (<a href="https://codepen.io/vindi-r">@vindi-r</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

{% include "authors/vindi-r/author.njk" %}
