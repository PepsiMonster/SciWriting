---
## Front matter
title: "Отчет по лабораторной работе №4 по предмету Computer skills for scientific writing"
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

# Лабораторная работа №4

# Цель работы

Изучить основы подключения графики в LaTex с использованием пакета `graphicx`, освоить управлние размером/поворотом/обрезной изображений , работу с плаваюзщеми объектами (floats), а также механизмамаи перекрестных ссылок `\label и /ref` и влияние параметров \textwidth и \linewidth. 

# Задание

1. Подключить внешнее изображение в документ LaTeX, заменив демонстрационные изображения на собственное.

2. Исследовать параметры `height`, `width`, `scale`, `angle`, `trim` и `clip` в `\includegraphics`.

3. Сформировать «длинный» пример с использованием `lipsum` и проверить работу float’ов с позиционными спецификаторами `[h]`, `[t]`, `[b]`, `[p]`, а также принудительным `[H]`.

4. Сравнить поведение размеров рисунка при задании относительно `\textwidth` и `\linewidth` (в том числе в режиме `twocolumn`).

5. Проверить работу перекрёстных ссылок и выяснить, сколько прогонов компиляции требуется для корректной подстановки номеров.

6. Экспериментально проверить, что произойдёт при размещении `\label` **до** `\caption` у рисунка и при размещении `\label` **после** `\end{equation}` у формулы.

7. Подготовить отчёт и презентацию, опубликовать материалы в репозитории и оформить ссылки на скринкасты.

# Теоретическое введение

LaTeX поддерживает подключение внешней графики через пакет `graphicx`, который добавляет команду `\includegraphics`. В качестве исходных форматов обычно используются PNG/JPG (растровые) и PDF (векторный). При задании размера через `width` или `height` LaTeX автоматически сохраняет пропорции изображения.

Для технических документов важна концепция «плавающих» объектов (floats): LaTeX может переносить рисунки и подписи на более удачное место, чтобы избежать больших пустых областей и улучшить верстку. Управление размещением выполняется через позиционные спецификаторы `[h]`, `[t]`, `[b]`, `[p]`. Пакет `float` добавляет спецификатор `[H]`, который пытается поставить рисунок строго «здесь», но может ухудшить внешний вид документа за счёт больших разрывов.

Для технических документов важна концепция «плавающих» объектов (floats): LaTeX может переносить рисунки и подписи на более удачное место, чтобы избежать больших пустых областей и улучшить верстку. Управление размещением выполняется через позиционные спецификаторы `[h]`, `[t]`, `[b]`, `[p]`. Пакет `float` добавляет спецификатор `[H]`, который пытается поставить рисунок строго «здесь», но может ухудшить внешний вид документа за счёт больших разрывов.

Разница между `\textwidth` и `\linewidth` особенно заметна в режиме `twocolumn`: `\textwidth` соответствует ширине текстового блока страницы, а `\linewidth` — текущей ширине строки (например, ширине колонки), поэтому одинаковый коэффициент может давать различный итоговый размер изображения.

# Выполнение лабораторной работы

1. Подготовка структуры проекта: 
   1. созданы документы main4.tex и main4_ru.tex
   2. создана подпапка figs с графиком 
2. Подключение пакетов и пути к изображениями до начала документа
   1. В преамбуле подключены основные пакеты для работы с графиком, float и ссылками.
```latex
   \usepackage{graphicx}
   \usepackage{lipsum}
   \usepackage{float}
   \usepackage[hidelinks]{hyperref}

   \graphicspath{{figs/}}
```

3. Вставка изображения в документ
```latex
   \begin{center}

     \includegraphics[height=2cm]{image.png}

   \end{center}
```
![alt text](image.png)

4. Эксперименты с параметрами размера и вида изображения
   1. Сравнены способы задания размера через `height` и `width`.
   2. Проверены трансформации `scale` и `angle`.
   3. Выполнена обрезка с помощью `trim` и `clip` (формат `left bottom right top`).

Пример обрезки:
```latex
   \includegraphics[clip, trim=20 10 80 40, width=0.6\textwidth]{image.png}
```
5. Плавающие изображения и спецификаторы

   - Добавлен «рыбный» текст `lipsum`, чтобы у LaTeX появилось пространство для перестановки float’ов.

   - Созданы рисунки с `[ht]`, `[tb]`, `[p]`, а также принудительное размещение `[H]`.

   - Зафиксировано, что LaTeX может переносить рисунки на следующую страницу при нехватке места, особенно при крупных `width/height`.

6. Сравнение `\textwidth & \linewidth`
   - Изображение масштабировалось относительно `\textwidth` и `\linewidth`.

   - Документ компилировался в обычном режиме и в режиме `twocolumn` (включение параметра `twocolumn` в строке `\documentclass`).

   - Отмечено, что в `twocolumn` относительный размер по `\linewidth` соответствует ширине текущей колонки и визуально отличается от масштаба по `\textwidth`.

7. Перекрестные ссылки 

   - Добавлены метки рисунков через `\label{figs:...}` и ссылки на них с последюущим отображением `\ref{fig:...}` в тексте. 
   - Необходимо 2 прогона компиляции для правильного отображения
   - Отдельно выполнена компиляция с неправильно размещенными `\label` перед `\caption`. Получен рисунок с невеным номером
   - Аналогично при неправильной полседовательности `\equation` получает неправильный номер
  
8. Компиляция 

Для русской весии использована сборка pdflatex с кодировкой [`T2A`, язык `babel`]. Для перекрестных ссылок минимум 2 запуска:
```powershell
pdflatex main4_ru.tex
pdflatex main4_ru.tex

pdflatex main4.tex
pdflatex main4.tex
```

# Формирование отчета

1. Подготовлены исходный текст отчета в markdown и конвертированы в pdf и docx с использованием pandoc. 
2. Подгтовлена презентация и конвертирована в pdf
3. Исторговые артефакты опубликованы в репозитории

# Выводы

В ходе работы были освоены базовые и расширенные способы встаки изображений в LaTex: управление размерами, поворотом и обрезкой, а также организация изображений в подпапке через `\graphicspath`. На практике подтверждено, что механизм работы float заметно влияет на итоговое расположение рисунков, а принудительное [H] может ухудшить внешний вид после верстки. Эксперименты показали различие между \textwidth и \linewidth в режиме twocolumn. Было проверено, что корректная работа перекрестных ссылок требует как минимум 2 прогонов компиляции, а неправильное рпасположение `\label` до `\caption` или после `\end{equation}` приводит к некорретным ссылкам.

# Список литературы 

LearnLaTex: https://www.learnlatex.org/
LaTex Project: https://www.latex-project.org/
Tex Live: https://www.tug.org/texlive/

# Приложения

Репозиторий с материалами:
https://github.com/PepsiMonster/SciWriting/tree/main/ex4