---
marp: true
theme: default  # Меняем на default для большего контроля
paginate: true
size: 16:9
class: lead
transition: slide
math: mathjax
backgroundColor: '#FFFDF6'
color: '#1F1F1F'
style: |
  /* Beaver цветовая схема с элементами Warsaw */
  
  :root {
    --primary-color: #8B1A1A;
    --secondary-color: #B22222;
    --accent-color: #D2691E;
    --light-bg: #FFFDF6;
    --dark-text: #1F1F1F;
    --code-bg: #F5F5F5;
  }
  
  /* СЛАЙДЫ ПО УМОЛЧАНИЮ - ПО ЛЕВОМУ КРАЮ */
  section {
    background-color: var(--light-bg);
    font-family: 'Helvetica Neue', Arial, sans-serif;
    padding: 40px 60px;
    text-align: left;  /* ГЛОБАЛЬНОЕ ВЫРАВНИВАНИЕ ПО ЛЕВОМУ КРАЮ */
  }
  
  /* ОТДЕЛЬНЫЙ КЛАСС ДЛЯ ЦЕНТРИРОВАННЫХ СЛАЙДОВ */
  section.centered,
  section.center {
    text-align: center;
  }
  
  /* Для lead слайда оставляем центрирование */
  section.lead {
    text-align: center;
    padding-top: 120px;
  }
  
  /* Специальный класс для центрированных списков */
  section.centered ul,
  section.centered ol,
  section.center ul,
  section.center ol,
  section.lead ul,
  section.lead ol {
    display: inline-block;
    text-align: left;
    margin-left: auto;
    margin-right: auto;
  }
  
  /* Warsaw заголовки */
  h1 {
    color: var(--primary-color);
    border-bottom: 3px solid var(--secondary-color);
    padding-bottom: 15px;
    margin-bottom: 30px;
    font-size: 2.5em;
    font-weight: 700;
    text-shadow: 1px 1px 2px rgba(0,0,0,0.1);
  }
  
  h2 {
    color: var(--secondary-color);
    border-left: 5px solid var(--accent-color);
    padding-left: 15px;
    margin-top: 40px;
    font-weight: 600;
  }
  
  h3 {
    color: var(--accent-color);
    font-weight: 600;
  }
  
  /* Списки - всегда по левому краю */
  ul, ol {
    padding-left: 25px;
    text-align: left;
  }
  
  li {
    margin: 8px 0;
  }
  
  li::marker {
    color: var(--primary-color);
  }
  
  /* Остальные стили без изменений */
  p {
    line-height: 1.6;
    margin: 15px 0;
  }
  
  code {
    background-color: var(--code-bg);
    color: var(--primary-color);
    padding: 2px 6px;
    border-radius: 3px;
    font-family: 'Monaco', 'Consolas', monospace;
    font-size: 0.9em;
    border: 1px solid #E0E0E0;
  }
  
  pre {
    background-color: var(--code-bg);
    border: 1px solid #E0E0E0;
    border-left: 5px solid var(--accent-color);
    padding: 20px;
    border-radius: 0 5px 5px 0;
    overflow: auto;
    box-shadow: 0 2px 4px rgba(0,0,0,0.05);
  }
  
  pre code {
    background-color: transparent;
    border: none;
    padding: 0;
  }
  
  blockquote {
    border-left: 4px solid var(--accent-color);
    background-color: #F9F9F9;
    padding: 15px 20px;
    margin: 20px 0;
    font-style: italic;
  }
  
  table {
    border-collapse: collapse;
    width: 100%;
    margin: 20px 0;
    box-shadow: 0 2px 3px rgba(0,0,0,0.1);
  }
  
  th {
    background-color: var(--primary-color);
    color: white;
    padding: 12px;
    text-align: left;
  }
  
  td {
    padding: 10px 12px;
    border-bottom: 1px solid #E0E0E0;
  }
  
  tr:nth-child(even) {
    background-color: #F8F8F8;
  }
  
  a {
    color: var(--secondary-color);
    text-decoration: none;
    border-bottom: 1px dotted var(--secondary-color);
  }
  
  a:hover {
    border-bottom: 2px solid var(--secondary-color);
  }
  
  hr {
    border: none;
    height: 2px;
    background: linear-gradient(to right, transparent, var(--primary-color), transparent);
    margin: 40px 0;
  }
  
  section.lead h1 {
    border-bottom: none;
    font-size: 3.5em;
    margin-bottom: 20px;
    color: var(--primary-color);
  }
  
  section.lead h2 {
    border-left: none;
    color: var(--accent-color);
    font-weight: 400;
  }
  
  footer {
    color: var(--accent-color);
    font-size: 0.9em;
  }
  
  .warsaw-box {
    background: white;
    border: 2px solid var(--primary-color);
    border-radius: 5px;
    padding: 20px;
    margin: 20px 0;
    box-shadow: 0 3px 6px rgba(0,0,0,0.1);
  }
  
  .alert {
    background-color: #FFF3CD;
    border-left: 5px solid var(--accent-color);
    padding: 15px;
    margin: 20px 0;
  }
  
  .highlight {
    background-color: rgba(139, 26, 26, 0.1);
    padding: 2px 5px;
    border-radius: 3px;
  }
---

# Лабораторная работа №4

## Including graphics $LaTex$

Тема: подключение изображений, floats, ссылок, `\label`, `\ref`, сравнение `\textwidth` и `\linewidth`.

---

# Цель работы

-   Научиться подключать внешние изображения в LaTeX через `graphicx`

-   Освоить параметры изменения вида рисунков: размер, поворот, обрезка

-   Понять, как работают *floats* и спецификаторы размещения

-   Разобраться с перекрёстными ссылками и количеством прогонов

    компиляции

-   Сравнить `\textwidth` и `\linewidth` (в т.ч. в режиме `twocolumn`)

---

# Задание

1.  Вставить собственное изображение из подпапки `figs/`

2.  Исследовать `height`, `width`, `scale`, `angle`, `trim`, `clip`

3.  Добавить «длинный» текст через `lipsum`, протестировать float'ы `[h,t,b,p]`

4.  Сравнить `\textwidth` и `\linewidth` (обычный режим и `twocolumn`)

5.  Проверить работу `\label/\ref`, включая намеренно неправильные случаи

---

# Структура проекта


-   `main4_ru.tex` / `main4.tex` --- исходники (RU/EN)

-   `figs/image.png` --- своё изображение

-   `main4_ru.pdf` / `main4.pdf` --- результат компиляции

-   `report.md` → `report.pdf`, `report.docx`

-   `presentation.md` → `presentation.pdf`

---

# Подключение графиков 

Для внешних изображений испольуется пакет `graphicx`:
```latex
\usepackage{graphicx}
```
Картинку графика храним в подпапке, на которую указываем путь в преамбуле:
```latex
\graphicspath{{figs/}}
```

---

# Вставка изображения

Минимальный(базовый) пример:
```latex

\begin{center}

  \includegraphics[height=2cm]{image.png}

\end{center}

```
---

# Управление размером

Часто задают размеры относительно текста страницы:

```latex
\includegraphics[height=0.35\textheight]{image.png}

\includegraphics[width=0.55\textwidth]{image.png}
```

**width** - ширина
**height** - высота

Пропорции сохраняются автоматически.

---

# Масштаб и поворот

```latex
\includegraphics[scale=0.6]{image.png}

\includegraphics[angle=15, scale=0.6]{image.png}
```

**scale** - общий масштаб
**angle** - поворот в градусах

---

# Обрезка trim и clip

`trim` задается как **left, botom, right, top**.

```latex
\includegraphics[clip,trim=20 10 80 40,
  width=0.6\textwidth]{image.png}
```

--- 

# Зачем нужен lipsum 

Чтобы $LaTex$ мог двигать float графики нужен был объемный текст

```latex 
\usepackage{lipsum}

...

\lipsum[1-4]
```

---

# Floats: рисунки как плавающие объекты

Пример float'а:

```latex
\begin{figure}[ht]
  \centering
  \includegraphics[width=0.6\textwidth]{image.png}
  \caption{Пример float с [ht].}
  \label{fig:ht}
\end{figure}
```

Внутри float лучше использовать `\centering`, а не `center`

---

# Спецификаторы размещения

-   `[h]` --- here (если получится)

-   `[t]` --- top (вверх страницы)

-   `[b]` --- bottom (вниз страницы)

-   `[p]` --- отдельная страница для float'ов

LaTeX выбирает оптимально, если места «здесь» нет

---

# Принудительно «строго здесь»: \[H\]

Пакет `float` добавляет `[H]`:

```latex
\usepackage{float}

\begin{figure}[H]

  \centering

  \includegraphics[width=0.55\textwidth]{image.png}

  \caption{Строгое размещение [H].}

  \label{fig:H}

\end{figure}
```

Может создавать большие пустые области --- использовать осторожно

---

# Перекрёстные ссылки

Ставим метку:

```latex
\label{fig:ht}
```
Ссылаемся:

```latex
см. рисунок~\ref{fig:ht}
```

Тильда `~` не даёт переносить строку между словом и номером
  
---

# Почему нужны 2 прогона компиляции

`\label`/`\ref` используют `.aux` файл:

1.  1-й прогон: LaTeX «собирает» номера и записывает их в `.aux`

2.  2-й прогон: подставляет номера в текст

Если присутвуют `??` --- просто собираем ещё раз Обычно нужно минимум 2 прогона.

---

# Где правильно ставить `\label `{=tex}в figure


✅ Правильно: **после** (или внутри) `\caption`
  
```latex

\caption{...}

\label{fig:ok}

```

❌ Неправильно: до `\caption`

```latex
\label{fig:wrong}
\caption{...}
```

Потому что `\label` ссылается на **последний пронумерованный объект**

---

# `\label `{=tex}в equation: правильно и неправильно

✅ Правильно (внутри окружения):

```latex
\begin{equation}
e^{i\pi}+1=0
\label{eq:inside}

\end{equation}
```

❌ Неправильно (после окружения)
  

```latex
\begin{equation}
a^2+b^2=c^2
\end{equation}
\label{eq:outside}
```

---

# `\textwidth `{=tex}vs `\linewidth`{=tex}

-   `\textwidth` --- ширина текстового блока страницы

-   `\linewidth` --- текущая ширина строки (может отличаться локально)
- 
В `twocolumn` разница заметна: `\linewidth` ≈ ширина колонки

---

# Эксперимент с twocolumn

Компилируем два варианта:

```latex
\documentclass[a4paper,12pt]{article}
\documentclass[a4paper,12pt,twocolumn]{article}

```

И сравниваем:
```latex
\includegraphics[width=0.8\textwidth]{image.png}
\includegraphics[width=0.8\linewidth]{image.png}
```

---

# Компиляция

Обычно достаточно `pdflatex` (и два прогона):

```powershell
pdflatex main4_ru.tex

pdflatex main4_ru.tex

```

Для EN-версии аналогично:

```powershell
pdflatex main4.tex

pdflatex main4.tex

```

---

# Итоги

Выполнено:


-   Подключена собственная графика из `figs/`

-   Проверены `height/width/scale/angle/trim/clip`

-   Исследованы float'ы и спецификаторы `[h,t,b,p]` + `[H]`

-   Изучены перекрёстные ссылки и необходимость (2) прогонов

-   Показана разница `\textwidth` и `\linewidth` (в т.ч. `twocolumn`)

-   Подготовлены отчёт и презентация, материалы опубликованы

  
