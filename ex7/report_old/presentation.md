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

$$
P_{\text{получ}} \propto \frac{1}{d^{\alpha}}, \quad \alpha \approx 2\text{--}4
$$

Определение отношения сигнал/шум:

$$
\text{SNR} = \frac{P_{\text{сигнала}}}{P_{\text{шума}}}
$$

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