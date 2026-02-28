---
## Front matter
title: "Отчет по лабораторной работе №6 по предмету Computer skills for scientific writing"
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

# Отчет по лабораторной работе №6 

# Цель работы

Изучить оформление библеографических ссылок и списка литературы в LaTex с использованием пакетов `natlib` и `bibtex`, а также освоить рабочий процесс сборки библиографии с помощью BibTex и Biber. 

# Задание 

1. Проверить примеры оформления библиографии для `natbib` и `biblatex`.

2. Для `natbib` выполнить последовательность компиляции: LaTeX → BibTeX → LaTeX → LaTeX.

3. Для `biblatex` выполнить последовательность компиляции: LaTeX → Biber → LaTeX.

4. Создать новую запись в базе `.bib` и добавить новую цитату в документ.

5. Добавить цитирование ключа, которого нет в базе, и посмотреть, как это отображается в PDF.

6. Поэкспериментировать со стилями:

   - `natbib` в numeric-режиме;

   - `biblatex` с опцией `style=numeric`.

# Теоретическое введение 

В LaTeX принято хранить источники в отдельной библиографической базе формата BibTeX (`.bib`). В тексте документа используются команды цитирования (например, `\cite`, `\citet`, `\citep`), которые обращаются к ключам записей из базы. На этапе компиляции LaTeX формирует служебные файлы (`.aux`), после чего BibTeX или Biber собирают список литературы и возвращают результат в последующие прогоны LaTeX. Из-за этого библиография и ссылки обычно требуют нескольких прогонов компиляции (часто минимум \(2\), а с BibTeX/Biber — больше).

Пакет `natbib` расширяет стандартные возможности цитирования и поддерживает разные форматы ссылок:

- текстовые ссылки (например, `\citet{...}`);

- ссылки в скобках (например, `\citep{...}`);

- параметры страниц/комментариев в цитатах.

`biblatex` является более современным решением и обычно используется вместе с процессором `biber`. Он даёт более гибкую настройку стилей и формата списка литературы.

# Выполнение лабораторной работы

## Подготовка библиографической базы

Для данного задания создан файл базы learnlatex.bib, содержащий несколько записей (книга и статья), а также добавлена новая запись (например книга Л. Лэмпорта о LaTex). Далее в тексте документа ваыполнено цитирование по ключам записей. 

Также добалена ссылка на ключ, отсутствующий в базе, чтобы отследить предупреждения компилятор и внешний вид ссылки в PDF.

## Цитирования в ntbib

В документе проверены:

- текстовые цитаты: `\citet{...}`;

- цитаты в скобках: `\citep{...}`;

- цитаты с указанием страниц (например, `\citep[p.~56]{...}`);

- несколько источников в одной ссылке: `\citep{key1,key2}`.

## Сборка документа (natbib + BibTex)

Для корректного формирования списка литературы выполнена последовательность сборки:

1) Первый прогон LaTex (формирование .aux и списка цитирований)
2) Запуск BibTex (генерация библиографии)
3) Второй прогон LaTex (подхват списка литературы)
4) Третий прогон LaTex (фиксирование ссылок и номеров)

## Эксперимент со стилем numeric для natbib 

Для проверки numeric-режима включены настройки natbib для числовых ссылок и выбран подходящий стиль библиографии. В результате команды `\citep{}` отображаются числовыми ссылками вида [1],[2].

## Эксперимент с biblatex + biber

Отдельно подготовлен вариант документа с использованием `biblatex` и выполнена сборка по схеме:

LaTex -> Biber -> LaTex

Также была проверена настройка style=numeric, чтобы сравнить поведение с numeric-режимом natbib.

# Формирование отчета

- Подготовлен исходный `.tex` файл(ы) с примерами для `natbib` и `biblatex`.

- Сформирован итоговый PDF(ы) после корректной последовательности компиляции.

- Зафиксированы результаты экспериментов: новый источник в базе, отсутствующий ключ, переключение стилей цитирования.

# Выводы 

В ходе работы осваены дво подхода к библиографии в LaTex: `natbib` и `biblatex`. Установлено, что библиография требует многопроходной сбокри, так как данные о ссылка и списке литературы формируются через служебные файлы. Проверено добавленгие источников и поведение при цитировании отсутствующего ключа. Выполненосравненеи author-year и numeric-представления ссылок.

# Приложения

- Репозиторий с исходниками и результатами работы (подставь актуальную ссылку):

  - https://github.com/PepsiMonster/SciWriting/tree/main/ex6

# Список литературы

1. Lamport L. *LaTeX: A Document Preparation System*. Addison-Wesley, 1994.

2. Graham R. L., Knuth D. E., Patashnik O. *Concrete Mathematics*. Addison-Wesley, 1995.

3. CTAN: пакет `natbib` (документация).

4. CTAN: пакет `biblatex` (документация) и `biber`.