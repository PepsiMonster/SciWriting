---
## Front matter
lang: ru-RU
title: Презентация лабораторной работы №1
subtitle: Простейший шаблон
author:
  - Лобов М. С.
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 26 января 2026

## i18n babel
babel-lang: russian
babel-otherlangs: english

## Formatting pdf
toc: false
toc-title: Содержание
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
mainfont: "Times New Roman"
sansfont: "Arial"
monofont: "Consolas"
header-includes:
 - \usepackage{bm}
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'
---

# Лабораторная работа №7
## Презентации в LaTex с Beamer

Выбранная тема презентации: "5G сети и распрострение сигнала

---
# Цель работы 

Освоить создание презентации в LaTex с использованием Beamer:
* Структура презентации (`frame` и титульный слайд)
* Оформление темы и цветовой схемы
* Структурирование контента (блоки, списки, колонки)
* Поэтапное появление элементов (\pause, \uncover, оверлеи)

---
# Задачи
1. Создать презентацию в `beamer` с титульным слайдом, оформлением и т.д.
2. Использовать `block`, `itemize`, `enumerate`, `columns`
3. Реализовать последовательное появление элементов
4. Настроить внешний вид на этапе преамбулы
5. Добавить схему или рисунок 
6. Скомпилировать pdf и подготовить прочие материалы

---
# Структура `Beamer` презентации (1)
Минимальная преамбула (каркас)
```latex
\documentclass[handout,xcolor={svgnames}]{beamer} 

\usetheme{Warsaw}
\usecolortheme{beaver}

\usepackage[utf8]{inputenc}
\usepackage[russian]{babel}
\usepackage{amsmath,amssymb}
\usepackage{graphicx}
\usepackage{tikz}
```
---
# Структура `Beamer` презентации (2)
Содержательная титульный слайд и содержание
```latex
\title{5G сети и распространение сигнала}
\author{Лобов Михаил} % присутствует на каждом слайде
\institute{RUDN University}
\date{\today}

\begin{document}
\begin{frame}\titlepage\end{frame}
\begin{frame}{Заголовок}
Содержимое
\end{frame}
\end{document}
```

---
# Оформление и локализация 
В работе использовано:
* тема: `Warsaw`

* цветовая схема: `beaver`

* русский язык: `babel`

* математика: `amsmath`, `amssymb`

* пакеты `[T2A]{frontenc}`, `[utf8]{inpuitenc}`, `[russian]{babel}` для русскоязычного варианта

---
# Математика в слайдах 

Примеры формул, использованных в презентации:

  

Ослабление сигнала с расстоянием:

```latex
P_{\text{получ}} \propto \frac{1}{d^{\alpha}}, \quad \alpha \approx 2\text{--}4
```

Определение отношения сигнал/шум:

```latex
\text{SNR} = \frac{P_{\text{сигнала}}}{P_{\text{шума}}}
```

---
# Поэтапное появление элементов

- `\pause` - простой шаговый показ
- `\uncover` - точный контроль появления

Пример:
```latex
\begin{itemize}

  \item<1-> Пункт 1
  \item<2-> Пункт 2

\end{itemize}

\uncover<3->{Текст появляется на шаге 3.}

```

---
# Компановка колонки и `Tikz`
Для удобного макета использовалось `columns`:
```latex
\begin{columns}
  \begin{column}{0.55\textwidth}
    Текст + списки
  \end{column}

  \begin{column}{0.45\textwidth}
    \begin{tikzpicture}
    \end{tikzpicture}
  \end{column}

\end{columns}
```

---
# Компиляция и проверка
Сборка PDF файлов 
```powershell
pdflatex main7_ru.tex
pdflatex main7.tex
pdflatex main7_slides.tex
pdflatex main7_ru_slides.tex
```
Возможны повторные прогоны компиляции для стабилизции вспомогательных элементов (ссылки, нумерация, оглавление и т.д.)

---

# Результаты работы 

**Подготовлено:** 

* Исходники презентаций main7.tex/main7_ru.tex 
* Исходники для формирования презентаций без поэтапного вывода main7_ru_slides.tex и main7_slides.tex
* Скомпилированные pdf файлы презентаций
* Отчет и презентация markdown 
* Видеоотчеты о проделанной работе

---

# Итог

Освоены возможности Beamer для создания презентаций в LaTex:
* структура `frame` и логика оформления

* блоки, списки, колонки

* постепенное раскрытие контента (\pause, \uncover)

* математические формулы и схемы TikZ

---

# Приложения

## Источники и ссылки

  

* Документация Beamer (User Guide)

* Документация LaTeX Project

* D. Tse, P. Viswanath — *Fundamentals of Wireless Communication*

* A. Goldsmith — *Wireless Communications*

  

**Репозиторий:** [https://github.com/PepsiMonster/SciWriting/tree/main/ex7](https://github.com/PepsiMonster/SciWriting/tree/main/ex7)