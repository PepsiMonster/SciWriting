---
## Front matter
title: "Отчет по лабораторной работе №1 по предмету Practical scientific writing"
author: "Лобов Михаил Сергеевич"

## Generic options
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true
toc-depth: 2
lof: true
lot: true
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt

## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
    - spelling=modern
    - babelshorthands=true
polyglossia-otherlangs:
  name: english

## I18n babel
babel-lang: russian
babel-otherlangs: english

## Fonts
mainfont: IBM Plex Serif
romanfont: IBM Plex Serif
sansfont: IBM Plex Sans
monofont: IBM Plex Mono
mathfont: STIX Two Math
mainfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
romanfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
sansfontoptions: Ligatures=Common,Ligatures=TeX,Scale=MatchLowercase,Scale=0.94
monofontoptions: Scale=MatchLowercase,Scale=0.94,FakeStretch=0.9
mathfontoptions:

## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric

## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"

## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float}
  - \floatplacement{figure}{H}
---

# Цель работы 

Изучить базовую структуру LaTex документа (преамбула и тело) и научиться компилировать `.tex` в PDF с помощью `pdflatex`, а также освоить работу со спецсимволами и сносками.

# Задание

1. Создать простой LaTex документ и разработать его структуру:
   1. преамбула
   2. тело окружения `\begin{...}`
2. Добавить комментарии, сноску и сделать несколько абзацев
3. Проверить работу жесткого неразрывного пробела
4. Вывести в документе набор спецсимволов LaTex и способы их печати
5. Подготовить русскую и английскую версии исходников и результатов компиляции
6. Опубликовать результаты в репозитории GitHub

# Теоретическое введение 

LaTeX — это система компьютерной вёрстки, в которой документ создаётся как текстовый файл с разметкой-командами. В отличие от WYSIWYG-редакторов, LaTeX описывает *структуру* документа (разделы, абзацы, списки, таблицы), а итоговый вид формируется на этапе компиляции в PDF.

Базовая структура LaTex документа включает:
- **Преамбулу**, все то, что идет до `\begin{document}`
```latex
\documentclass[a4paper,12pt]{article}
\usepackage[T1]{fontenc}
```
- **Тело документа**, все то, что идет между `\begin{document}` и `\end{document}`
```latex
\begin{document}

...

\end{document}
```

Абзацы в LaTex отделяются **пустой строкой**. Спецсимволы (`\`, `{`, `}`, `%`, `$`, `&`, `#`, `_` и др.) имеют служебное значение и печатаются с экранированием (например, `\%`, `\{`), либо командами (`\textbackslash`, `\textasciitilde`).

# Выполнение лаборатной работы

## 1. Создание минимального документа 

Был создан `main2.tex` (английская версия) со структурой:
```latex
\documentclass{article}
\usepackage[T1]{fontenc}

\begin{document}
Hey world!
This is a second document.
\end{document}
```
Для выполнения компиляции использовалась команда `pdflate main2.tex`. В результате получен файл main2.pdf, а также main2.log и main2.aux.

## 2. Структура документа и окружения

Документ был расширен до примера с комментариями, сноской и 2мя абзацами. Также показано, что окружения должны корректно закрываться: для каждого \begin{x} должен быть \end{x}, причём при вложенности закрытие идёт в обратном порядке.

## 3. Неразрывный пробел

Добавлен пример hard space ~ для предотвращения переноса строки межлу связанными фрагментами текста.

## 4. Специальные символы LaTex

В документ добавлен список наиболее часто используемых спецсимволов и способов их печати:
```latex
\begin{itemize}
  \item Curly braces: \{ and \}
  \item Dollar sign: \$ (so we can show money like \$10)
  \item Percent sign: \% (otherwise it starts a comment)
  \item Ampersand: \& (otherwise used in tables)
  \item Hash: \# 
  \item Underscore: \_ (often used in math, so needs escaping in text)
  \item Backslash: \textbackslash
  \item Caret: \textasciicircum
  \item Tilda: \textasciitilde
\end{itemize}
```

## 5. Русская версия документа

Для русской версии документа подготовлен файл main2_ru.tex со следующими настройками локализации:
```latex 
\documentclass[a4paper,12pt]{article}
\usepackage[T2A]{fontenc}
\usepackage[utf8]{inputenc}
\usepackage[russian]{babel}
```

Это обеспечивает корректный набор кирилицы в pdflatex.

# Формирование отчета

Подготовлены исходные файлы: main2.tex, main2_ru.tex.

Выполнена компиляция в PDF: main2.pdf, main2_ru.pdf.

Сформирован отчёт в Markdown и презентация в формате Marp.

Материалы опубликованы в репозитории.

# Выводы

В ходе работы освоены базовые принципы LaTex:
- структура документа
- разделение на преамбулу и тело
- правила создания абзацев
- использование окружений, комментариев и сносок

Отдельно изучены способы печати спецсимволов и применение неразрывного пробела ~. Подготовлены русская и английская версия исодников и результатов компиляции, а также оформленны материалы для публикации на GitHub.

# Список литературы

LearnLaTex: https://www.learnlatex.org/
LaTex Project: https://www.latex-project.org/
Tex Live: https://www.tug.org/texlive/

# Приложения

Репозиторий с материалами:
https://github.com/PepsiMonster/SciWriting/tree/main/ex2