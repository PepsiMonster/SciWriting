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
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'
---

# Лабораторная работа №2
## Структура LaTex-документа

Лобов Михаил Сергеевич

---

# Цель работы 


- Изучить базовую структуру LaTeX-документа
- Научиться компилировать `.tex` в PDF через `pdflatex`
- Освоить: абзацы, комментарии, сноски, спецсимволы, неразрывный пробел `~`
- Подготовить русскую и английскую версии результата

---

# Задание 

1. Создать простой LaTex документ и разработать его структуру: *преамбула*, *тело окружения `\begin{...}`*
2. Добавить комментарии, сноску и сделать несколько абзацев
3. Проверить работу жесткого неразрывного пробела
4. Вывести в документе набор спецсимволов LaTex и способы их печати
5. Подготовить русскую и английскую версии исходников и результатов компиляции
6. Опубликовать результаты в репозитории GitHub

---

# Теоретическое введение


- **Преамбула** — настройки до `\begin{document}`
- **Тело** — содержимое между `\begin{document}` и `\end{document}`
- Абзацы отделяются **пустой строкой**
- Окружения должны быть закрыты:  
  `\begin{x}` … `\end{x}`

---

# Базовый текстовый документ

```latex
\documentclass{article}
\usepackage[T1]{fontenc}

\begin{document}
Hey world!
\end{document}
```
Компиляция осуществляется командой:
```powershell
pdflatex main2.tex
```

---

# Добавляем *жизни* в документ

- Комментарии через `%`
- Сноска через `\footnote{...}`
- Неразрывный пробел через `~`

---

### Спецсимволы в LaTex

Символы требующие экранирования: `\{` `\}` `\$` `\%` `\&` `\#` `\_`

Создание их в latex:
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

---

# Русская версия документа

Чтобы кирилица отображалась корректно, треюбуется дополнить преамбулу

```latex
\documentclass[a4paper,12pt]{article}
\usepackage[T2A]{fontenc}
\usepackage[utf8]{inputenc}
\usepackage[russian]{babel}
```

Компиляция стандартнрая:

```powershell
pdflatex main2_ru.tex
```

---

# Публикация результатов

- Исходники main2.tex,pdf и main2_ru.tex,pdf
- Отчет и презентация
- Скринкасты работы, отчетов и защиты
- Отчет и презентация md, pdf/html

---

# Итоги

1. Освоена базовая структура LaTeX-документа

2. Получены корректные PDF-результаты на EN и RU

3. Изучены спецсимволы, окружения, абзацы, ~, комментарии и сноски

4. Материалы подготовлены к сдаче и публикации