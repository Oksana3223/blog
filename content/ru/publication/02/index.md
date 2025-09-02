---
title: Языки разметки. LaTeX
subtitle: Языки разметки. LaTeX

# Summary for listings and search engines
summary: Обзор языков разметки и подробное введение в LaTeX - структура документа, математика, рисунки, таблицы, библиография, пакеты и сборка.

# Link this post with a project
projects: []

# Date published
date: '2025-08-22T00:00:00Z'

# Date updated
lastmod: '2025-08-22T00:00:00Z'

# Is this an unpublished draft?
draft: false

# Show this page in the Featured widget?
featured: true

authors:
  - admin

tags:
  - Academic
  - LaTeX
  - Markup
  - Writing
  - Typesetting

categories:
  - Tools
  - TeX
---

# 🧩 Языки разметки. LaTeX  

## Что такое языки разметки?  

**Язык разметки** — это способ описывать структуру и оформление текста с помощью специальных команд и тегов.  
Их удобно разделить на две группы:

- **Лёгкие (lightweight)**: простые для чтения и написания — *Markdown, reStructuredText, AsciiDoc*.  
- **Полноценные (heavyweight/типографские)**: мощные и гибкие — *LaTeX, HTML, XML/DocBook*.  

### Краткое сравнение

| Язык        | Сложность | Назначение                         | Сильные стороны                              |
|-------------|-----------|------------------------------------|-----------------------------------------------|
| Markdown    | Низкая    | Заметки, блоги, README             | Простота, читаемость                          |
| HTML        | Средняя   | Веб-страницы                       | Точная верстка, совместимость с вебом         |
| XML/DocBook | Высокая   | Документация, обмен данными        | Строгая структура, автоматизация              |
| **LaTeX**   | Средняя+  | Статьи, отчёты, книги, диссертации | Математика, ссылки, библиография, типографика |

---

## Почему именно LaTeX?  

LaTeX — это система высококачественной типографики, идеально подходящая для **научных текстов**: статей, отчётов, курсовых и дипломов.

**Преимущества:**
- ✨ Безупречная **математическая верстка** (формулы, выравнивание, нумерация).  
- 📚 **Библиография** и цитирование «из коробки» (BibTeX/Biber).  
- 🔗 **Кросс-ссылки** на рисунки, таблицы, формулы и разделы.  
- 🧩 **Пакеты** для расширения функциональности (amsmath, hyperref, cleveref и др.).  
- 🔁 **Воспроизводимость**: код документа — это и есть исходник, сборка детерминирована.

---

## Установка и инструменты  

- **Дистрибутивы:**  
  - Linux/Windows: *TeX Live*, Windows: *MiKTeX*, macOS: *MacTeX*.  
- **Редакторы:**  
  - *Overleaf* (онлайн), *TeXstudio*, *TeXmaker*, *VS Code* (+ плагин LaTeX Workshop), *IntelliJ + TeXiFy*.  
- **Движки (компиляторы):**  
  - **pdfLaTeX** — классика, стабильные шрифты (Type 1).  
  - **XeLaTeX** — нативный Unicode и системные шрифты.  
  - **LuaLaTeX** — расширяемость на Lua, продвинутая типографика.  
- **Сборка:**  
  - `latexmk` (автосборка зависимостей), `arara` (декларативные правила).

---

## Минимальная структура документа  

### Вариант A: pdfLaTeX (традиционный, шире совместимость)
```tex
\documentclass[a4paper,12pt]{article}

\usepackage[T2A]{fontenc}
\usepackage[utf8]{inputenc}
\usepackage[russian,english]{babel}

\usepackage{amsmath,amssymb,mathtools}
\usepackage{graphicx}
\usepackage{booktabs}
\usepackage{hyperref}
\usepackage{microtype}
\usepackage{geometry}
\geometry{margin=2.5cm}

\title{Пример документа \LaTeX}
\author{Оксана Чумаченко}
\date{\today}

\begin{document}
\maketitle

\section{Введение}
Это минимальный пример документа на \LaTeX.

\end{document}
```

### Вариант B: XeLaTeX/LuaLaTeX (современные шрифты и Unicode)
```tex
\documentclass[a4paper,12pt]{article}
\usepackage{fontspec}
\usepackage{polyglossia}
\setmainlanguage{russian}
\setotherlanguage{english}
\setmainfont{Times New Roman}

\usepackage{amsmath,amssymb,mathtools}
\usepackage{graphicx}
\usepackage{booktabs}
\usepackage{hyperref}
\usepackage{microtype}
\usepackage{geometry}
\geometry{margin=2.5cm}

\title{Пример документа \LaTeX}
\author{Оксана Чумаченко}
\date{\today}

\begin{document}
\maketitle

\section{Введение}
Современный стек с Unicode и системными шрифтами.

\end{document}
```

---

## Разметка текста  

- **Разделы:** `\section{}`, `\subsection{}`, `\paragraph{}`  
- **Выделение:** `\textbf{жирный}`, `\emph{курсив}`  
- **Списки:**  
  ```tex
  \begin{itemize}
    \item пункт
    \item ещё пункт
  \end{itemize}
  ```
- **Неразрывный пробел:** символ `~` (напр., «рис.~\ref{fig:demo}»).  
- **Кавычки:** в русском наборе — «ёлочки»: `«текст»`.  

---

## Математика  

### Встроенная и блочная
- Встроенная формула: `$E = mc^2$`  
- Блочная:  
  ```tex
  \[
    \int_0^{\infty} e^{-x^2}\,dx = \frac{\sqrt{\pi}}{2}.
  \]
  ```

### Нумерация и выравнивание
```tex
\begin{equation}\label{eq:newton}
  F = m a
\end{equation}

\begin{align}
  a_n &= \frac{1}{n} \sum_{k=1}^{n} x_k, \\
  S_n &= \sum_{k=1}^{n} k = \frac{n(n+1)}{2}.
\end{align}
```

### Собственные команды (макросы)
```tex
\newcommand{\R}{\mathbb{R}}
\newcommand{\vect}[1]{\mathbf{#1}}
```

---

## Рисунки и таблицы  

### Рисунки
```tex
\begin{figure}[htbp]
  \centering
  \includegraphics[width=.6\textwidth]{figs/example.png}
  \caption{Пример иллюстрации}
  \label{fig:demo}
\end{figure}
```

### Таблицы (с красивыми линиями)
```tex
\begin{table}[htbp]
  \centering
  \caption{Сравнение языков разметки}
  \label{tab:markup}
  \begin{tabular}{llll}
    \toprule
    Язык & Сложность & Назначение & Сильные стороны \\
    \midrule
    Markdown & Низкая & Заметки, README & Простота \\
    HTML     & Средняя & Веб & Контроль вёрстки \\
    LaTeX    & Средняя+ & Научные тексты & Математика, ссылки \\
    \bottomrule
  \end{tabular}
\end{table}
```

> Советы: подключите `\usepackage{graphicx}` и храните изображения в папке `figs/`. Для таблиц используйте `booktabs` и избегайте «сеток» из множества вертикальных линий.

---

## Ссылки и библиография  

- **Кросс-ссылки:**  
  - Пометьте объект меткой: `\label{eq:newton}`  
  - Сошлитесь: `см.~уравнение~\eqref{eq:newton}` или `рис.~\ref{fig:demo}`.  
- **Гиперссылки:** подключите `hyperref` (обычно ближе к концу преамбулы).

### BibTeX/BibLaTeX

**Файл `refs.bib`:**
```bibtex
@article{lamport1994latex,
  author  = {Lamport, Leslie},
  title   = {LaTeX: A Document Preparation System},
  journal = {Addison-Wesley},
  year    = {1994}
}
```

**Подключение (biblatex + biber):**
```tex
\usepackage[backend=biber,style=gost-numeric,sorting=nty]{biblatex}
\addbibresource{refs.bib}

Текст с цитированием \parencite{lamport1994latex}.

\printbibliography
```

> Для классического BibTeX используйте `\bibliographystyle{plain}` + `\bibliography{refs}`.

---

## Структура проекта  

```
project/
├─ main.tex
├─ tex/        # главы и разделы (\input или \include)
├─ figs/       # рисунки
├─ bib/        # библиография (refs.bib)
└─ build/      # артефакты сборки
```

В `main.tex` подключайте части так:
```tex
\input{tex/intro.tex}
\input{tex/methods.tex}
```

---

## Сборка и автоматизация  

- **latexmk**:
  ```bash
  latexmk -pdf -interaction=nonstopmode -halt-on-error main.tex
  ```
  Автоматически определяет, сколько раз запустить компилятор, и вызывает `biber`/`bibtex` при необходимости.

- **Выбор движка**:
  - `-pdf` → pdfLaTeX,
  - `-xelatex` → XeLaTeX,
  - `-lualatex` → LuaLaTeX.

- **Совместная работа**: Overleaf поддерживает историю версий и комментарии; локально используйте Git.

---

## Частые ошибки и их причины  

- **Undefined control sequence** — опечатка в имени команды или забытый пакет.  
- **Missing $ inserted** — математика вне `$...$`/`\[...\]`.  
- **Overfull \hbox** — слишком длинная строка; попробуйте `\sloppy`, переносы или перефразируйте.  
- **File not found** — неверный путь к рисунку/файлу.  
- **Package clash** — конфликт пакетов; упорядочьте подключения (`hyperref` ближе к концу).

---

## Набор для старта (рекомендуемая преамбула)  

```tex
\documentclass[a4paper,12pt]{article}

% Русский/Unicode
\usepackage{fontspec}
\usepackage{polyglossia}
\setmainlanguage{russian}
\setotherlanguage{english}
\setmainfont{Times New Roman}

% Математика и символы
\usepackage{amsmath,amssymb,mathtools}

% Гиперссылки и кликабельные рефы
\usepackage{hyperref}
\usepackage[nameinlink,noabbrev]{cleveref}

% Графика и таблицы
\usepackage{graphicx}
\usepackage{booktabs}
\usepackage{caption}
\usepackage{subcaption}

% Типографика и поля
\usepackage{microtype}
\usepackage{geometry}
\geometry{margin=2.5cm}
```

---

## Лучшие практики  

- Пишите **семантически**: команды отражают смысл, а не «как выглядит».  
- Избегайте ручных пробелов/переносов — полагайтесь на механизмы LaTeX.  
- Используйте `~` для неразрывных конструкций: «рис.~1», «гл.~2», «и т.~д.».  
- Храните рисунки в векторе (PDF/SVG→PDF) для чёткости.  
- Делите документ на части и ведите проект в Git.  

---

## Итог  

LaTeX — мощный инструмент академической вёрстки: он обеспечивает качественный набор формул, автоматизацию ссылок и библиографии, а также воспроизводимость публикаций.  
Освоив базовый стек (структура, математика, рисунки, таблицы, ссылки, библиография), вы сможете уверенно готовить **курсовые, статьи и презентации** на профессиональном уровне.

🚀 Если нужно, можно подготовить шаблон проекта под конкретные требования кафедры или журнала.

