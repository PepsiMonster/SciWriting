---
## Front matter
title: "Отчет по лабораторной работе №7 по предмету Computer skills for scientific writing"
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

# Лабораторная работа №7

# Цель работы  

Освоить создание презентаций в $LaTex$ с помощью класса `beamer`. Изучить структуру презентации, работу с окружением `frame`, оформление блоков и колонок а также способы поэтапного появления элементов на слайде с использованием `\pause` и `\uncover`. 

# Задачи

1. создать презентаци. в классе `beamer` с титульным слайдом и набором тематических слайдов. 
2. Испольозованть элементы `block`, `itemize`, `enumerate`, `columns` изучении ранее в курсе.
3. Реализовать поэтапное появлние элементов с помощью `\pause`, `\uncover`, а также оверлеев у пунктов спска `\item` 
4. Настроить оформление через тему и цветовую схему `Beamer`
5. Скомпилировать презентацию в pdf, подготовить материалы, опубликовать.

# Теоретическое введение

Класс `beamer` в $LaTex$ является стандартным инструментом для создания академических презентаций, обеспечивающий типографское качество верстки, поддержку сложных математических формул и т.д. 

# Выполнение лабораторной работы

## Структура презентации

Презентация была создана в классе `beamer` и имеет стандартную структуру:

* Преамбула с подключением пакетов:
```latex
\documentclass[xcolor={svgnames}]{beamer}

\usetheme{Warsaw}
\usecolortheme{beaver}

\usepackage[utf8]{inputenc}
\usepackage[russian]{babel}
\usepackage{amsmath,amssymb}
\usepackage{graphicx}
\usepackage{tikz}
```

* Название, автора и дату:
```latex
\title{5G сети и распространение сигнала}
\author{Лобов Михаил}
\institute{RUDN University}
\date{\today}
```

* Тело документа с набором окружений `frame`, включая титульный слайд, созданный через `\titlepage` 

## Оформление 

Для внешнего оформления использованы тема `Warsaw`, цветовая схема `beaver` и расширенная палитра цвтов $xcolor={svgnames}$.

Для работы русского языка использовались пакеты `babel` и кодировка входного текста UTF-8, а также подключение кадировки шрифтов `T2A`. Математические формулы набирались с помощью `amsmath`.

## Поэтапное появление элементов

Для получения поэтапного появления элементов использованы:

* `\pause` - для последовательно открытия логических блоков
* `\uncover{...}` и оверлеи `\item<...->` для точного управления появлнием фразментов текста и пунктов списков. 

## Колонки и иллюстрации 

Для компактного, визуально удобного размещения контента применялось окружение `columns`, где в одной колонке размещен текст, а во творой схема на `tikz`. 

## Компиляция 

Возможны 2 варианта компиляции в зависимости от класса документа. 
* Первый $\documentclass[xcolor={svgnames}]{beamer}$ учтет наши `\pause` и `\uncover` и покажет также промежуточные результаты.
* Второй $\documentclass[handout,xcolor={svgnames}]{beamer}$ позволит учитывать только `\frame` и не будет отображать промежуточные результаты. 

Для сборки презентации в PDF использована команда:
```powershell
pdflatex main7_ru.tex
pdflatex main7.tex
pdflatex main7_slides.tex
pdflatex main7_ru_slides.tex
```

# Выводы

В ходе лабораторной работы освоен базовый рабочий процесс создания презентаций в LaTex и ипользованием `beamer`. Для создания слайдов использована структура `frame`, слайды оформлены темой Warsaw с цветовой схемой beaver. В теле презентации были использованы блоки, колонны, иллюстрации, механизмы показа по шагам. Полученный pdf документ являет собой короткую презентацию на тему 5G сетей.

# Список литературы

LearnLaTex: https://www.learnlatex.org/
LaTex Project: https://www.latex-project.org/
Tex Live: https://www.tug.org/texlive/

# Приложения

Репозиторий с материалами:
https://github.com/PepsiMonster/SciWriting/tree/main/ex7