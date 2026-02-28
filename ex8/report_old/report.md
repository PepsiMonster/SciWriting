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

Освоить базовые приемы создания графических объектов в $LaTex$ с помощью пакета TikZ:
* Построение графа 
* Построение графика функции
* Использование рекурсии для генерации изображений

# Задание
1. Сверстать граф (узлы, ребра и диагонали)
2. Сверстать график функции (кривая, оси, подписи)
3. Взять пример с фракталами и адаптировать его для генерации ковра Серпинского в несколько итераций

# Теоретическое введение

TikZ - пакет Latex, позволяющий при помощи разметки описывать рисунки. После компиляции в документе появляется векторное изображение в формате pdf на ряду с остальным содержанием. Для графа с помощью команд задаются положения вершин в полярных координатах и они соединяются линиями; для графика функции используется команда plot, которая строит прямую по формуле; для более сложных построений, например фракталов, применяется рекурсия, когда рисунок собирается из уменьшеных копий самого себя. Таким образом TikZ превращает LaTex в графический конструктор, в котором можно создавать схемы и диаграммы наряду с текстом в одном документе.  

# Выполнение лабораторной работы

## Граф из вершин по окружности

1. Создан документ класса standalone.
2. В tikzpicture опредлен радиус окружности $R$
3. Узлы (A,B,C,D,E) размещены в полярных координатах 
4. Проведены ребра (получился многоугольник) и добавлены пунктиром диагонали

![alt text](image1.png)

## График функции

1. Построены оси `x` и `y` 
2. Начало координат отмечено как `O`
3. Построен график $y=\sin x$
4. Добавлены подписи осей и функции

![alt text](image2.png)

## Ковер Серпинского

1. Реализован макрос `\carpet{<x>}{<y>}{<size>}{<depth>}`
   1. при глубине 0 рисуется заполенный квадрат
   2. при глубине>0 область делится на сетку 3 на 3, центральный квадрат пропускается, для остальных вызывается рекурсия
2. Для демонстрации нескольких итераций изображения результатов каждой итерации идут последовательно, образуя "галарею" глубин
3. Проверена компиляция и визуальная корректность результата

![alt text](image3.png)

# Итоги

* Создан граф с узлами по окружности и диагонали
* Создан график функции $y = \sin x$ с базовой разметкой координатной плоскости
* Реализована генерация ковра Серпинского с несколькими итерациями (и уровнями глубины) 

# Выводы

Пакет TikZ позволяет создавать рисунки “как код”: от простых схем (узлы и рёбра) до графиков функций и фракталов. Использование координатных систем, стилей линий, `plot`, а также циклов/рекурсии делает возможной автоматическую генерацию сложной графики прямо в LaTeX без внешних редакторов.

# Список источников 

1. Документация PGF/TikZ (CTAN): `pgf` / `tikz` package documentation.

2. Wikibooks: LaTeX/PGF/TikZ (раздел по TikZ).

3. TeXample: база примеров TikZ (идеи оформления и приёмов).

# Приложения

* `main8_1.tex` — упражнение 8.2.1 (граф).

* `main8_2.tex` — упражнение 8.2.2 (график (y=\sin x)).

* `main8_3.tex` — упражнение 8.2.3 (ковёр Серпинского, итерации (0\ldots 5)).

* PDF-результаты компиляции для каждого упражнения.

* Репозиторий с материалами:
https://github.com/PepsiMonster/SciWriting/tree/main/ex7