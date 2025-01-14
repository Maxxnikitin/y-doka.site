---
title: "prompt()"
name: prompt
author: vindi-r
co-authors:
designers:
contributors:
summary:
---

## Кратко

При помощи директивы `prompt()` можно вывести на экран пользователя модальное окно c полем ввода и текстом-пояснением.

🤖Из-за того, что окно модальное — работа с интерфейсом браузера и страницами будет заблокирована. Это неудобно, плюс может восприниматься пользователем как попытка ограничивать его свободу. Модальное окно для пользователя — окно, которое блокирует работу пользователя с браузером до тех пор, пока пользователь это окно не закроет.

## Пример

<p class="codepen" data-height="265" data-theme-id="light" data-default-tab="html,result" data-user="vindi-r" data-slug-hash="OqZYEe" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="prompt() пример">
  <span>See the Pen <a href="https://codepen.io/vindi-r/pen/OqZYEe">
  prompt() пример</a> by vindi-r (<a href="https://codepen.io/vindi-r">@vindi-r</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

💡Это крайне быстрый вариант кода, который взаимодействует с пользователем, но окно созданное таким образом не изменяется через CSS, а значит использовать его лучше только для прототипирования интерфейса. В финальном варианте веб-страницы юзать модальное окно нежелательно.

## Как пишется

`prompt()` принимает 1 или 2 аргумента — это текст для отображения и значение по умолчанию для поля ввода.

Результат работы `prompt()` можно записать в переменную:

```js
var answer1 = prompt("Как тебя зовут?")
var answer2 = prompt("Как тебя зовут?", "Имя")
```

Если при вызове `prompt` использовать только один параметр, тогда в появившемся окне поле ввода не будет содержать "подсказки" ввода.

В случае когда использовано два параметра, то в поле ввода будет с "подсказкой" ввода. Это полезно, чтобы показать пользователю какой результат ввода ожидается.

## Как это понять

Аргументы `prompt()` должны быть строками. Если это не так — будет автоматическое приведение к строке. Такое поведение не доставляет проблем, пока аргумент является примитивом или встроенным типом, имеющим правила приведения к строке.

```js
prompt("Как тебя зовут?", "Саша")
// Текст: "Как тебя зовут?", значение поля ввода: "Саша"
prompt("Введите возраст", 18) // "Введите возраст", СТРОКА "18"
```

<p class="codepen" data-height="265" data-theme-id="light" data-default-tab="js,result" data-user="vindi-r" data-slug-hash="jJxjNM" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="prompt() как это понять">
  <span>See the Pen <a href="https://codepen.io/vindi-r/pen/jJxjNM">
  prompt() как это понять</a> by vindi-r (<a href="https://codepen.io/vindi-r">@vindi-r</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

💡 Результат prompt() — строка, если была нажата кнопка "OK" или null, если была нажата "Отмена".

Поэтому не стоит полагаться на то, что результат prompt() всегда будет строкой. Это может привезти к ошибкам в работе скрипта, например:

```js
var result = prompt("Введите четное число", "")
// вводим ДЕСЯТЬ и нажимаем ОК
if (result % 2 === 0) {
  // Проверка на четность
  alert("Число четное")
} else {
  alert("Число нечетное")
}

// Результат: сообщение "Число нечетное"
```

С точки зрения синтаксиса ошибок нет, но

- Нет явной обработки null — result примет значение null в случае нажатия кнопки "Отмена": Конечно **null % 2** выполнится без ошибок, но работа программы будет некорректной. Правильнее будет обработать и отказ от ввода числа.
- Нет обработки ситуаций, когда введено не число:

  В операции (**result % 2 === 0**) из-за деления на 2 JavaScript осуществляет приведение строки result к численному типу. Если не получится, то результат работы будет некорректным.

Более корректный вариант обработки ввода:

```js
var result = prompt("Введите четное число", "")
if (result === null) {
  alert("Вы отказались от ввода")
} else if (isNaN(result % 2)) {
  alert("Ошибка, введено НЕ ЧИСЛО")
} else if (result % 2 === 0) {
  alert("Число четное")
} else {
  alert("число нечетное")
}
```

Вариант обработки всех возможных случаев ввода более громоздкий, но он намеренно написан наиболее простым способом. В случае использование **switch..case** или отдельных самостоятельно написанных функций проверки код примет более элегантный вид.

## В работе

{% include "authors/vindi-r/in-work.njk" %}

🛠Ниже представлен пример использования prompt() с самостоятельно созданным диалоговым окном:

<p class="codepen" data-height="265" data-theme-id="light" data-default-tab="js,result" data-user="vindi-r" data-slug-hash="xBjowJ" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="prompt() в работе">
  <span>See the Pen <a href="https://codepen.io/vindi-r/pen/xBjowJ">
  prompt() в работе</a> by vindi-r (<a href="https://codepen.io/vindi-r">@vindi-r</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

{% include "authors/vindi-r/author.njk" %}
