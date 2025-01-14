---
title: "class"
name: class
author: ABatickaya
co-authors:
designers:
contributors: skorobaeus
summary:
  - класс
  - атрибут
---

## Кратко

Универсальный атрибут тега, с помощью которого можно задать _имя_ любому элементу на странице. Имя элемента в дальнейшем используется в качестве селектора в CSS и позволяет управлять стилями элемента.

## Пример

На странице может быть множество одинаковых тегов. Например, несколько заголовков второго уровня.

```html
...
<!-- Первый заголовок -->
<h2>В Санкт-Петербурге</h2>
<p>Ветер, по Питерскому обыкновению, дул сразу со всех четырёх сторон.</p>
<!-- Второй заголовок -->
<h2>В России</h2>
<p>«Умом Россию не понять...»</p>
<!-- Третий заголовок -->
<h2>В мире</h2>
<p>На Брайтон Бич опять идут дожди.</p>
...
```

{% demo "/class/nostyle", "Без классов", 380 %}

🤖 Как при текущей разметке можно изменить цвет текста первого заголовка? Можно обернуть все заголовки в разные дополнительные теги. И использовать их комбинации в качестве селекторов для написания стилей. Но это решение будет неверным. Разметка _распухнет_, её сложно будет читать. Так делать не нужно.

Для того, чтобы выделить какой-то отдельный элемент или набор элементов и применить стили выборочно можно использовать атрибут `class`.

```html
...
<!-- Первый заголовок -->
<h2 class="news__local">В Санкт-Петербурге</h2>
<p>Ветер, по Питерскому обыкновению, дул сразу со всех четырёх сторон.</p>
<!-- Второй заголовок -->
<h2 class="news__country">В России</h2>
<p>«Умом Россию не понять...»</p>
<!-- Третий заголовок -->
<h2 class="news__world">В мире</h2>
<p>На Брайтон Бич опять идут дожди.</p>
...
```

В коде выше каждому заголовку второго уровня заданы разные имена классов. Это позволит без особых проблем написать стили только для первого заголовка.

```css
.news__local {
  color: #ed6742;
}
```

{% demo "/class/withstyle", "С классами", 380 %}

Цель достигнута, при этом стили остальных заголовков второго уровня остались прежними.

## Как это понять

Имя класса может быть произвольным. Ты самостоятельно придумываешь это название и задаёшь его элементу при помощи атрибута `class`. Для того, чтобы использовать имя класса в качестве селектора достаточно написать его в CSS, поставив перед именем точку. По точке браузер поймёт, что ему нужно искать не тег, а именно класс.

## Как пишется

Атрибут класса можно задать любому тегу в HTML-разметке. Как и любой другой атрибут, класс прописывается внутри треугольных скобок открывающего тега.

HTML

```html
<p class="text">
  Его экзистенциальная тоска выступает как побудительный мотив творчества,
  однако символизм начинает импрессионизм.
</p>
```

При выборе имени класса следует придерживаться нескольких правил:

1. В именах классов используй только английские слова.

```html
<!-- Плохо -->
<p class="osnovnoy-text">
  Его экзистенциальная тоска выступает как побудительный мотив творчества,
  однако символизм начинает импрессионизм.
</p>

<!-- Хорошо -->
<p class="main-text">
  Его экзистенциальная тоска выступает как побудительный мотив творчества,
  однако символизм начинает импрессионизм.
</p>
```

2. Имена классов пишутся маленькими буквами.

```html
<!-- Плохо -->
<p class="Main-Text">
  Его экзистенциальная тоска выступает как побудительный мотив творчества,
  однако символизм начинает импрессионизм.
</p>

<!-- Хорошо -->
<p class="main-text">
  Его экзистенциальная тоска выступает как побудительный мотив творчества,
  однако символизм начинает импрессионизм.
</p>
```

3. Для разделения двух слов используются тире (`-`) или знак подчёркивания (`_`). Не используй camelCase 🐫

```html
<!-- Плохо -->
<p class="mainText">
  Его экзистенциальная тоска выступает как побудительный мотив творчества,
  однако символизм начинает импрессионизм.
</p>

<!-- Хорошо -->
<p class="main-text">
  Его экзистенциальная тоска выступает как побудительный мотив творчества,
  однако символизм начинает импрессионизм.
</p>

<!-- Хорошо -->
<p class="main__text">
  Его экзистенциальная тоска выступает как побудительный мотив творчества,
  однако символизм начинает импрессионизм.
</p>
```

4. Лучше не использовать больше трёх слов в имени класса.

```html
<!-- Плохо -->
<p class="daily-news__main-alert-text">
  Его экзистенциальная тоска выступает как побудительный мотив творчества,
  однако символизм начинает импрессионизм.
</p>

<!-- Хорошо -->
<p class="news__main-text">
  Его экзистенциальная тоска выступает как побудительный мотив творчества,
  однако символизм начинает импрессионизм.
</p>
```

5. Не используй в названиях классов цифры или числительные. Завтра порядок блоков может измениться и нумерация будет сбивать с толку.

```html
<!-- Плохо -->
<p class="text1">
  Его экзистенциальная тоска выступает как побудительный мотив творчества,
  однако символизм начинает импрессионизм.
</p>
<p class="text-two">Экзистенциализм сложен.</p>
<p class="text3">Художественное переживание последовательно.</p>

<!-- Хорошо -->
<p class="main-text">
  Его экзистенциальная тоска выступает как побудительный мотив творчества,
  однако символизм начинает импрессионизм.
</p>
<p class="sub-text">Экзистенциализм сложен.</p>
<p class="note-text">Художественное переживание последовательно.</p>
```

6. Не задавай имя класса по контенту или по тегу. Контент — вещь живая. Если он изменится, то класс потеряет свою актуальность, что осложнит чтение и понимание кода. Теги также могут измениться в процессе жизни сайта.

```html
<!-- Плохо -->
<p class="p-text">
  Его экзистенциальная тоска выступает как побудительный мотив творчества,
  однако символизм начинает импрессионизм.
</p>
<p class="difficult">Экзистенциализм сложен.</p>
<p class="perezhivanie">Художественное переживание последовательно.</p>

<!-- Хорошо -->
<p class="main-text">
  Его экзистенциальная тоска выступает как побудительный мотив творчества,
  однако символизм начинает импрессионизм.
</p>
<p class="sub-text">Экзистенциализм сложен.</p>
<p class="note-text">Художественное переживание последовательно.</p>
```

7. Не опирайся на внешний вид элемента при выборе имени класса. В разработке есть тенденция к быстрым изменениям. Поэтому завтра внешний вид сайта может полностью измениться. При подборе имён классов по смыслу элемента позволит избежать изменения HTML-разметки.

```html
<!-- Плохо -->
<p class="green-text">
  Его экзистенциальная тоска выступает как побудительный мотив творчества,
  однако символизм начинает импрессионизм.
</p>

<!-- Хорошо -->
<p class="main-text">
  Его экзистенциальная тоска выступает как побудительный мотив творчества,
  однако символизм начинает импрессионизм.
</p>
```

Есть несколько методологий именования классов. Самой популярной на сегодняшний день является [БЭМ](https://ru.bem.info/methodology/). Методология призвана определить дополнительные правила именования классов и облегчить процесс придумывания имён.

## Подсказки

💡 У элемента может быть несколько классов. Перечисляй классы, разделяя их пробелом.

```html
<p class="sub-text news-text">Экзистенциализм сложен.</p>
```

💡 Поскольку стили принято задавать только селекторам по классу, пиши классы всем элементам сразу в процессе создания HTML-разметки.

## В работе

🛠 Раньше в вёрстке довольно часто использовались идентификаторы — атрибут `id`. Теперь их лучше не использовать и заменить на класс. Точно не стоит использовать идентификаторы для стилизации элементов.

Причина в том, что идентификатор должен быть уникальным. В разметке может быть только один идентификатор с определённым именем. Это крайне неудобно для написания стилей, поскольку придётся многократно повторять одни и те же стили, но для разных идентификаторов. С классами эта проблема решается просто. Пропиши всем элементам, для которых нужно задать определённый внешний вид, один и тот же класс.

У многих начинающих разработчиков существует представление, что идентификаторы требуются для связи JavaScript и HTML, но это не так. В современном виде JavaScript предоставляет удобные инструменты поиска и манипуляции элементами по их классу. Так что и здесь классы пригодятся!

🛠 После того, как разметка и стили написаны, посмотри на них внимательно. Высока вероятность, что написано несколько одинаковых блоков стилей для разных классов. Имеет смысл оптимизировать код и вынести повторяющиеся стили в отдельный блок и задать всем похожим элементам один класс.

🛠 Представляй каждый блок, из которого состоит страница, как самостоятельный элемент, который можно будет убрать с текущей страницы и перенести на другую. Задавай такие имена классов, которые не будут привязаны к странице. Думай компонентами 😉

{% include "authors/ABatickaya/author.njk" %}
