---
title: "quotes"
name: quotes
author: ABatickaya
co-authors:
designers:
contributors:
summary:
  - quotes
---

## Кратко

CSS-свойство, позволяющее задать вид кавычек на сайте или в отдельном блоке. В каждом языке принято использовать определённый вид кавычек. Например, в русском используются кавычки-ёлочки «», а в английском кавычки-лапки “”.

Указанный в значении вид кавычек будет автоматически выставляться вокруг текста, обёрнутого в тег `<q>` ([«q»](/html/doka/q/)), или при указании у свойства `content` псевдоэлементов `:before` и `:after` значений `open-quote` / `close-quote`.

## Пример

Этому свойству можно указать сразу несколько значений: 1 открывающая кавычка, 2 закрывающая кавычка, 3 открывающая кавычка вложенной цитаты, 4 закрывающая кавычка вложенной цитаты:

```css
body {
  quotes: "«" "»" "„" "“";
}

span:before {
  content: open-quote;
}

span:after {
  content: close-quote;
}
```

```html
<p>
  <q>Скажи <span>церемония</span> по слогам</q>, — попросила она.
</p>
```

В итоге текст будет выглядеть так:

<p class="codepen" data-height="265" data-theme-id="light" data-default-tab="css,result" data-user="solarrust" data-slug-hash="LYGBgdE" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="quotes">
  <span>See the Pen <a href="https://codepen.io/solarrust/pen/LYGBgdE">
  quotes</a> by Alena (<a href="https://codepen.io/solarrust">@solarrust</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

## Как пишется

```css
/* Ключевые слова */
quotes: none;
quotes: auto;

/* Кавычки */
quotes: "«" "»"; /* Открывающая и закрывающая кавычки */
quotes: "«" "»" "‹" "›"; /* Два уровня кавычек */
```

`none` — ключевое слово, сбрасывает любые настройки, кавычки не будут отображаться.

`auto` — кавычки будут соответствовать языку документа.

## Подсказки

💡 Попробуйте скопировать текст из интерактивного примера выше и вставить куда-нибудь, например, в блокнот. Во вставленном тексте не будет кавычек. Всё потому что их не существует физически в тексте, они расставлены при помощи стилей. Об этой особенности стоит помнить.

## В работе

🛠 Это свойство может быть очень полезно когда вы разрабатывает большой сайт, который будут наполнять контентом другие люди. Чтобы созданный дизайн соблюдался во всех мелочах вы можете принудительно прописать тот вид кавычек, который будет расставляться в текстах. Но при других обстоятельствах это свойство редко пригождается 🤷‍♀️

{% include "authors/ABatickaya/author.njk" %}
