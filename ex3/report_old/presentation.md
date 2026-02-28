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

# Лабораторная работа №3
## Набор математических формул $LaTex$

---

# Цель работы

- Освоить математический режим \LaTeX
- Научиться набирать формулы в inline и display режимах
- Использовать пакет `amsmath` для многострочных выражений
- Попробовать греческие буквы и математические шрифты
- Проверить опции `[fleqn]` и `[leqno]`

---

# Задание

1. Переключить примеры между inline и display
2. Добавить греческие буквы (нижний и верхний регистр)
3. Поэкспериментировать со шрифтами в математике и их вложенностью
4. Применить `[fleqn]` для выравнивания формул слева
5. Применить `[leqno]` для переноса номеров формул влево

---

# Math mode: особенности

- В математическом режимер пробелы игнорируются
  - их необходимо явно задавать
- Отступы между символами ставятся автоматически
- Формулы набираются логически, а не рисуются

---

# Inline va Display

**Inline** - формула внутри строки

sample text and formula: $y = mx + c$

**Display** - формула отдельным блоком:

$$
y = mx + c
$$

---

# Индексы и степени

- Надстрочный индекс: $a^b$
- Пожстрочный индекс: $a_b$
- Комбинирование: $a_b^c$

Из-за специфики markdown отображение $LaTex$ было изменено, оригинальный вид:
\( a^{b} \), \( a_{b} \), \( a_{b}^{c} \).

---

# Греческие буквы 

Строчные:  
$$\alpha, \beta, \gamma, \theta, \lambda, \pi, \omega $$

Прописные:  
$$ \Gamma, \Delta, \Theta, \Lambda, \Pi, \Omega $$

---

# Интеграл и дифференциал

Пример несобственного интеграла:

$$
\int_{-\infty}^{+\infty} e^{-x^2}\,dx
$$

Тонкий пробел перед $dx$: `\,`

---

# Нумерование формул

Внутри окружения `equation`:

$$
\text{(пример)} \quad \int_{-\infty}^{+\infty} e^{-x^2}\,dx
$$

Нумерация назначается в документе автоматически.

---

# `amthmath`

Пакет `amthmath` позволяет использовать:
- многострочные формулы
- выравнивание по знакам
- матрицу и улучшенные окружения
- вставка текста внутри математики через `$\text{содержание}$`

---

# `align`: выравнивание по знакам

$$
\begin{aligned}
a &= b + 1 \\
c &= d + 2 \\
e &= f + 3
\end{aligned}
$$

**Как выглядит без разметки:**
\begin{aligned}
a &= b + 1 \\
c &= d + 2 \\
e &= f + 3
\end{aligned}

Удобно для систем и преобразований.

---

# `gather и multline`

`gather` - строки без выравнивания

$$
\begin{gathered}
x^2 + x = 10 \\
P(x)=ax^{5}+bx^{4}+cx^{3}+dx^{2}+ex + f
\end{gathered}
$$

**Оригинал:**
\begin{gathered}
x^2 + x = 10 \\
P(x)=ax^{5}+bx^{4}+cx^{3}+dx^{2}+ex + f
\end{gathered}

`multline` - длинная формула на несколько строк.

---

# Матрицы в `amthmath` 

$$
\begin{pmatrix}
a & b & c \\
d & e & f
\end{pmatrix}
\quad
\begin{bmatrix}
a & b & c \\
d & e & f
\end{bmatrix}
$$

**Оригинал:**
\begin{pmatrix}
a & b & c \\
d & e & f
\end{pmatrix}
\quad

---

# Шрифты в математике

$\mathrm{d}x$ - прямой шрифт
$\mathit{word}$ - слово как текст
$\mathbf{M}x$ - матрица или вектор
$\mathsf{A}x$ 
$\mathtt{code}$
$\mathbb{R}$

---

# Вложенность шрифтов

По итогам компиляции, было установлено, что:

- Команды перебивают друг друга
- Не все шрифты применимы ко всем символам
- для греческих букв и знаков лучше использовать \bm{} 

Пример: 
$$
\alpha + {\alpha} < \beta + {\beta}
$$

---

# Опции `[fleqn]` и `[leqno]`

`[fleqn]` делает формулы “по левому краю” — удобно в отчётах и ГОСТ-оформлении. 
По умолчанию номера формул центрируются.
`[leqno]` переносит номера формул влево — полезно для некоторых шаблонов/требований.
По умолчанию номера формул показываются справа.

---

# Итог

В ходе работы:

- освоены inline и display режимы
- добавлены греческие буквы и индексы
- применён `amsmath` для многострочных формул и матриц
- протестированы математические шрифты и вложенность
- проверены опции `[fleqn]` и `[leqno]`