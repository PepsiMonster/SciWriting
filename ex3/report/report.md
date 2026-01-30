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

Освоить набор базовых приемов набора математических формул в $LaTex$, а именно: работу в математическом режиме (inline и display) использование расширения пакета amsmath, вывод греческих букв, применение различных математических шрифтов (в т.ч. с вложенностью), а также настройку оформления формул с помощью опций класса документа (fleqn, lenqo).

# Задание 

Создать документ .tex со следующими приемами:

1. Переклчать примеры формул между inline- и display- режимами, посмотреть различия. 
2. Добавить греческие буквы в разных регистрах.
3. Проверить команды смены математических шрифтов и посмотеть, что происходит при вложенности.
4. Изменть выравнивание формул опцией [fleqn].
5. Изменить размещение номеров форму опцией [leqno].
6. Подготовить русскую и английскую версии $LaTex$ документа, скомпилировать PDF файл, заполнить отчет и презентацию, опубликовать материалы.

# Теоретическое введение
Математический режим $LaTex$ предназначен для логичного набора формул: пробелы внутри формул игнорируются, а типографическе отступы между математическоими символами подбираются автоматически. Формулы можно набирать в тексте (inline) и отдельно в строке (display). Для более сложных конструкций часто используют пакет amsmath, который добавляет окружения выравнивания (`align`, `gather`, `multline`), матрицы и команды для типовых математических объектов.

В формулах смена шрифта можент нести смысловую нагрузку (например, $\mathrm{d}$ как дифференциал, $\mathbb{R}$ как множество и так далее).

# Выполнение лаборатоной работы 

## 1. Inline и display математика

Проверено влияние режима на внешний вид формул:

- inline-формулы “встраиваются” в строку и стараются не разрывать межстрочный интервал;
    
- display-формулы выделяются отдельным блоком и визуально читаются лучше для “крупных” выражений

Пример: (y = mx + c) (inline) и [<font color="cyan"> y = mx + c </font>] (display).

## 2. Верхние и нижние индексы, а также ручные пробелы

Использованы над- и подстрочные индексы вида $a^b + c^d$, а также примеры, показывающие, что пробелы в математичке не "считываются" и при необходимости добавляются командами тонких/средних пробелов.

## 3. Греческие буквы

Добавлены строчные и прописные символы:

$$
a^{b} \text{ or } a_{b} \text{ and } x_{n}^{1000}
$$

## 4. Интеграл и аккуратный (dx)

Набран пример интеграла и оформлен дифференциал (dx) с корректным интервалом

## 5. Нумерованные формулы и опции расположения

Проверено окружение `equations` для автоматической нумерации формул, а также влияние опции [leqno] на перенос номера формулы в левую часть

## 6. `amthmath`: align, gather, multline, матрицы 

- Использовано окружение `align` для выравнивания нескольких строк по знаку отношения и вставки текста внутри математики. 
- Дополнительно протестированны `gather` и `multline` для многострочных выражений без табличного выравнивания. 
- Набьраны примеры матриц в скобках разных типов 

## 7. Шрифты в математике и вложенность 

Использованы на практике команды ((\mathrm{}), (\mathit{}), (\mathbf{}), (\mathsf{}), (\mathtt{}), (\mathbb{})), и показано, как меняется результат при попытках вложить одни стили в другие 

## 8. Русская и английская версия документы 

Подготовлены два варианта $LaTeX$-документа (RU/EN) с идентичным набором экспериментов и получены итоговые PDF-файлы после компиляции.

# Формирование отчета и презентации

1. Зафиксированы исходники $LaTex$
2. Сформирован отчет в markdown и конвертирован в pdf и docx средствами pandoc
3. Модготовлена презентация в markdown (Marp) и тоже конвертирована во все необходимые форматы
4. Скринкасты выполнения и защиты опубликованы на Rutube и Vkvideo 

# Выводы 

В ходе работы были отработные гланвые базовые операции для набора формул $LaTex$: 
- выбор режима (inline/display) 
- ввод индексов и специальных символов 
- набор интегралов и нумерация формул 
- пакет `amsmath` существенно упрощает оформление многострочных выражений
- опции `[fleqn]` и `[leqno]`, которые позволяют быстро менять стиль расположения формул и их номеров

Отдельно подтверждено, что смена математических шрифтов должна применяться осмысленно, так как она влияет на только на внешний вид, но и на интерпртицию обозначений при компиляции.

# Списко литературы

LearnLaTex: https://www.learnlatex.org/
LaTex Project: https://www.latex-project.org/
Tex Live: https://www.tug.org/texlive/

# Приложения

Репозиторий с материалами:
https://github.com/PepsiMonster/SciWriting/tree/main/ex3