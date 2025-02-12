---
title: "querySelector"
name: query-selector
author: N_Lopin
co-authors:
designers:
contributors:
summary:
  - селектор
  - найти элемент по селектору
  - selector
  - найти элемент в html
---

## Кратко

Метод определен для объекта `document` и любого HTML-элемента (`Element`) страницы. Позволяет найти элемент по CSS-селектору среди дочерних. Если элементов несколько, то вернется первый подходящий. Если подходящих элементов нет, то вернет `null`.

## Как пишется

Метод принимает один параметр — CSS-селектор в виде строки. Если передан не CSS селектор, то система выбросит ошибку. Например, можно выбрать первый элемент внутри `div`:

```html
<html>
  <head></head>
  <body>
    <div>
      <p>
        Князь Василий говорил всегда лениво, как актер говорит роль старой
        пиесы. Анна Павловна Шерер, напротив, несмотря на свои сорок лет, была
        преисполнена оживления и порывов.
      </p>
      <p>
        Быть энтузиасткой сделалось ее общественным положением, и иногда, когда
        ей даже того не хотелось, она, чтобы не обмануть ожиданий людей, знавших
        ее, делалась энтузиасткой. Сдержанная улыбка, игравшая постоянно на лице
        Анны Павловны, хотя и не шла к ее отжившим чертам, выражала, как у
        избалованных детей, постоянное сознание своего милого недостатка, от
        которого она не хочет, не может и не находит нужным исправляться.
      </p>
    </div>
    <p>Это параграф, дочерний для body</p>
    <script>
      let firstParagraph = document.querySelector("div>p")
      console.log(firstParagraph.textContent) // напечатает текст, начинающийся с "Князь Василий"

      // ищем несуществующий элемент
      let spanFromBody = document.querySelector("span")
      console.log(spanFromBody) // null
    </script>
  </body>
</html>
```

Динамический пример, введи селектор в поле поиска и жми «Искать»:

<p class="codepen" data-height="541" data-theme-id="light" data-default-tab="result" data-user="Lopinopulos" data-slug-hash="oReWwv" style="height: 541px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="Работа querySelector">
  <span>See the Pen <a href="https://codepen.io/Lopinopulos/pen/oReWwv">
  Работа querySelector</a> by Nikolai Lopin (<a href="https://codepen.io/Lopinopulos">@Lopinopulos</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

## Как понять

Метод работает с DOM, который связан с HTML разметкой. Каждый HTML-элемент имеет родительские и дочерние элементы:

- Родители — это элементы, которые содержат текущий элемент. В примере выше у первого элемента `p` есть два родительских элемента — `div` и `body`.
- Дочерние элементы — это элементы, которые содержит текущий элемент. Они могут быть, а могут не быть. Например, для тега `body` все элементы страницы дочерние. У `p` дочерний элемент — текст внутри тега.

Если работаешь с корнем страницы, объектом `document`, то поиск идет по всем элементам страницы (т.е. от `body`), если от конкретного элемента, то поиск идет только по всем дочерним.

## В работе

### Николай, front-end ниндзя

🛠 Для поиска первого элемента в качестве аргумента нужно передать строку `'*'`, ее называют wildcard.
