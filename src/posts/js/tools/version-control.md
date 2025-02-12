---
title: "Системы управления версиями"
name: version-control
author: kamyshev
co-authors:
designers:
contributors:
tags:
  - sprint-4
  - sprint-10
summary:
  - git
  - vcs
  - гит
  - create repository
  - создать репозиторий
---

## Кратко

Системы контроля версий — VCS (version control systems) — были придуманы, чтобы следить за историей изменений исходного кода и комфортно работать над ним большой командой.

Самая популярная из систем — Git. Ее используют в большинстве проектов. Некоторые компании используют другие системы, например SVN или Mercurial, другие — создают собственные решения, чтобы лучше покрыть свои специфичные потребности.

## Как понять

При разработке программ часто происходят ошибки — одно из изменений может сломать всё приложение. В таком случае нужно быстро вернуть пользователям последнюю работающую версию. С другой стороны, когда над проектом работает большое число людей, бывает полезно знать — кто, когда и какое изменение внес. Обе эти проблемы решаются сохранением полной истории изменений исходного кода в **системе контроля версий**.

В 2005 году была создана самая популярная на данный момент VCS — **Git** (произносится «гит»). Для базовых нужд достаточно самых простых возможностей, они покроют 90% всех потребностей. Но сначала нужно определить несколько понятий.

**Репозиторий** — это общее название для хранилища исходного кода. Часто говорят об **удаленном репозитории** (копия кода на каком-то сервере) и **локальном репозитории** (копия на компьютере разработчика).

Код в репозитории хранится в виде истории **коммитов** — небольших изменений исходного кода. Можно сказать, что репозитории хранят только историю изменений, а текущее состояние кода представляют просто последовательно применяя все эти изменения.

Важное отличие VCS от любого другого хранилища файлов с историей — это коммиты. С их помощью можно записать изменение одной строки в одном файле и двух строк в другом с общим комментарием.

![Линейная история коммитов](/assets/images/posts/js/version-control/git_01.png)

При этом история может ветвиться. То есть в какой-то момент, один из разработчиков может начать делать изменения и после коммита А сделать коммиты Б и В, а другой разработчик после коммита А сделает коммиты Г и Д. Так появится две альтернативные истории изменений. Такие параллельные истории называются **ветками**. Чтобы совместить эти изменения в единой кодовой базе, ветки нужно будет слить.

Обычные хранилища файлов не могут показывать параллельные истории одного и того же файла, а VCS — умеет.

![Сливание ветки в репозиторий](/assets/images/posts/js/version-control/git_02.png)

## Как пользоваться

Система контроля версий — это интерактивная история разработки. С помощью VCS можно не только узнать кто и когда внес определенную правку, но и вернуть состояние исходного кода на **любой момент** времени.

Чтобы воспользоваться Git, нужно [установить его](https://git-scm.com/downloads) на свой компьютер. После этого в терминале следует перейти в папку проекта и инициализировать репозиторий.

```
git init
```

Теперь можно добавить все файлы проекта к списку отслеживаемых изменений.

```
git add all
```

И создать новый коммит.

```
git commit -m "Комментарий к первому коммиту"
```

Последние две команды стоит выполнять после каждого значимого изменения исходного кода, добавляя осмысленный комментарий.
