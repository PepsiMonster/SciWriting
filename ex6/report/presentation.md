---
marp: true
theme: gaia
paginate: true
size: 16:9
class: lead
transition: slide
math: mathjax
backgroundColor: '#d8c5e1'
color: '#333333'
style: |
  h1 { color: #263786; }
  code { font-size: 0.95em; }
---

# Лабораторная работа №6

## Библиография в LaTex

**Инструменты**: BibTex/Biber, стили author-year и numeric.

---
# Цели работы 

- Освоить цитирование и список литературы в LaTeX  

- Сравнить подходы:

  - `natbib` + **BibTeX**

  - `biblatex` + **Biber**

- Проверить:

  - добавление новых записей в `.bib`

  - ссылку на отсутствующий ключ

  - переключение стилей на numeric

---
# База источников .bib

- Источники хранятся в файле `*.bib`
- Каждая запись имеет ключ (например, `Graham1995`)
- Цитирование в тексте идёт по ключу:
  - `\citet{Graham1995}`
  - `\citep{Graham1995}`

```bibtex
@book{Lamport1994,
  author    = {Leslie Lamport},
  title     = {LaTeX: A Document Preparation System},
  year      = {1994},
  publisher = {Addison-Wesley}
}
```

---
# `natbib` команды для цитирования

* **Текстовая** ссылка: 
  * автор как часть предложения `\citet{Graham1995}`

* **В скобках**: 
  * `\citep{Graham1995}`

* **Страницы/комментарии**:
  * `\citep[p.~56]{Thomas2008}`, `\citep[См.][pp.~45--48]{Graham1995}`

---
# `natbib` пример в тексте

```latex

Пример по математике взят из \citet{Graham1995}.

Ссылка в скобках: \citep{Graham1995}.

С указанием страниц: \citep[p.~56]{Thomas2008}.

Несколько источников: \citep{Graham1995,Thomas2008}.

```

---
# Сборка `natbib` в bibtex

Для корректности ссылок и списка литературы нужен цикл в несколько компиляций
```bash

pdflatex main6.tex

bibtex main6

pdflatex main6.tex

pdflatex main6.tex

```

---
# Что происходит при сборке

1. Latex создает .aux (список использованных ключей)
2. BibTex формирует библиографию (.bbl)
3. 2й и 3й прогоны LaTex 
   1. подтягивают список литературы 
   2. донастраивают номера сслык и перекрестные ссылки

---
# Numeric-режим в `natbib`

Чтобы вместо author–year получить числовые ссылки:

```latex

\usepackage[numbers]{natbib}

\bibliographystyle{plain} % или unsrt

```

Тогда `\citep{...}` выглядит как [1], [2]

---
# Использование `biblatex`

* Более гибкий механизм оформления библиографии
* Обычно используется вместе в biber
* Стиль задается опциями пакета
```latex

\usepackage[style=numeric,backend=biber]{biblatex}

\addbibresource{learnlatex.bib}

```

---
# Сборка `biblatex` в Biber

$$
\text{LaTeX} \rightarrow \text{Biber} \rightarrow \text{LaTeX}
$$

```bash

pdflatex main6.tex

biber main6

pdflatex main6.tex

```

---
# Сравнение подходов

**natbib + BibTeX**

* простой и распространённый вариант

* удобно для классических шаблонов

* стили зависят от `.bst`

**biblatex + Biber**

* гибкие настройки прямо в LaTeX

* проще кастомизировать

* современный рекомендуемый подход во многих проектах

---
# Итоги работы

* Освоены `\citet` / `\citep` и параметры цитат

* Реализована база `.bib` и добавление новых записей

* Проверено поведение при отсутствующем ключе

* Выполнены эксперименты со стилями:

  * numeric в `natbib`

  * `style=numeric` в `biblatex`

* Отработаны процессы сборки BibTeX и Biber