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