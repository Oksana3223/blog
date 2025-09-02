---
title: Markup Languages. LaTeX
subtitle: Markup Languages. LaTeX

# Summary for listings and search engines
summary: Overview of markup languages and a detailed introduction to LaTeX - document structure, mathematics, figures, tables, bibliography, packages, and compilation.

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

# 🧩 Markup Languages. LaTeX  

## What are markup languages?  

A **markup language** is a way of describing the structure and formatting of text using special commands and tags.  
They can be divided into two groups:

- **Lightweight**: simple to read and write — *Markdown, reStructuredText, AsciiDoc*.  
- **Full-fledged (heavyweight/typographic)**: powerful and flexible — *LaTeX, HTML, XML/DocBook*.  

### Quick comparison

| Language    | Complexity | Purpose                          | Strengths                                 |
|-------------|------------|----------------------------------|-------------------------------------------|
| Markdown    | Low        | Notes, blogs, README             | Simplicity, readability                   |
| HTML        | Medium     | Web pages                        | Precise layout, web compatibility         |
| XML/DocBook | High       | Documentation, data exchange     | Strict structure, automation              |
| **LaTeX**   | Medium+    | Articles, reports, books, theses | Math, cross-references, bibliography, typography |

---

## Why LaTeX?  

LaTeX is a high-quality typesetting system, perfectly suited for **scientific texts**: articles, reports, coursework, and theses.

**Advantages:**
- ✨ Flawless **mathematical typesetting** (formulas, alignment, numbering).  
- 📚 **Bibliography** and citations out of the box (BibTeX/Biber).  
- 🔗 **Cross-references** for figures, tables, formulas, and sections.  
- 🧩 **Packages** for extended functionality (amsmath, hyperref, cleveref, etc.).  
- 🔁 **Reproducibility**: the source code *is* the document; compilation is deterministic.  

---

## Installation and tools  

- **Distributions:**  
  - Linux/Windows: *TeX Live*, Windows: *MiKTeX*, macOS: *MacTeX*.  
- **Editors:**  
  - *Overleaf* (online), *TeXstudio*, *TeXmaker*, *VS Code* (+ LaTeX Workshop plugin), *IntelliJ + TeXiFy*.  
- **Engines (compilers):**  
  - **pdfLaTeX** — classical, stable fonts (Type 1).  
  - **XeLaTeX** — native Unicode and system fonts.  
  - **LuaLaTeX** — extensibility with Lua, advanced typography.  
- **Build:**  
  - `latexmk` (auto dependency build), `arara` (declarative build rules).  

---

## Minimal document structure  

### Option A: pdfLaTeX (traditional, broader compatibility)
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

\title{Sample \LaTeX Document}
\author{Oksana Chumachenko}
\date{\today}

\begin{document}
\maketitle

\section{Introduction}
This is a minimal \LaTeX document example.

\end{document}
```

### Option B: XeLaTeX/LuaLaTeX (modern fonts and Unicode)
```tex
\documentclass[a4paper,12pt]{article}
\usepackage{fontspec}
\usepackage{polyglossia}
\setmainlanguage{english}
\setotherlanguage{russian}
\setmainfont{Times New Roman}

\usepackage{amsmath,amssymb,mathtools}
\usepackage{graphicx}
\usepackage{booktabs}
\usepackage{hyperref}
\usepackage{microtype}
\usepackage{geometry}
\geometry{margin=2.5cm}

\title{Sample \LaTeX Document}
\author{Oksana Chumachenko}
\date{\today}

\begin{document}
\maketitle

\section{Introduction}
Modern stack with Unicode and system fonts.

\end{document}
```

---

## Text markup  

- **Sections:** `\section{}`, `\subsection{}`, `\paragraph{}`  
- **Emphasis:** `\textbf{bold}`, `\emph{italic}`  
- **Lists:**  
  ```tex
  \begin{itemize}
    \item item
    \item another item
  \end{itemize}
  ```
- **Non-breaking space:** symbol `~` (e.g., “Fig.~\ref{fig:demo}”).  
- **Quotation marks:** in English — “quotes”: `“text”`.  

---

## Mathematics  

### Inline and display math
- Inline formula: `$E = mc^2$`  
- Displayed:  
  ```tex
  \[
    \int_0^{\infty} e^{-x^2}\,dx = \frac{\sqrt{\pi}}{2}.
  \]
  ```

### Numbering and alignment
```tex
\begin{equation}\label{eq:newton}
  F = m a
\end{equation}

\begin{align}
  a_n &= \frac{1}{n} \sum_{k=1}^{n} x_k, \\\\
  S_n &= \sum_{k=1}^{n} k = \frac{n(n+1)}{2}.
\end{align}
```

### Custom commands (macros)
```tex
\newcommand{\R}{\mathbb{R}}
\newcommand{\vect}[1]{\mathbf{#1}}
```

---

## Figures and tables  

### Figures
```tex
\begin{figure}[htbp]
  \centering
  \includegraphics[width=.6\textwidth]{figs/example.png}
  \caption{Sample illustration}
  \label{fig:demo}
\end{figure}
```

### Tables (with clean lines)
```tex
\begin{table}[htbp]
  \centering
  \caption{Comparison of markup languages}
  \label{tab:markup}
  \begin{tabular}{llll}
    \toprule
    Language & Complexity & Purpose & Strengths \\\\
    \midrule
    Markdown & Low & Notes, README & Simplicity \\\\
    HTML     & Medium & Web & Layout control \\\\
    LaTeX    & Medium+ & Scientific texts & Math, references \\\\
    \bottomrule
  \end{tabular}
\end{table}
```

> Tips: include `\usepackage{graphicx}` and store images in a `figs/` folder. For tables, use `booktabs` and avoid “grids” with too many vertical lines.

---

## References and bibliography  

- **Cross-references:**  
  - Label an object: `\label{eq:newton}`  
  - Refer to it: `see equation~\eqref{eq:newton}` or `Fig.~\ref{fig:demo}`.  
- **Hyperlinks:** load `hyperref` (usually closer to the end of the preamble).  

### BibTeX/BibLaTeX

**File `refs.bib`:**
```bibtex
@article{lamport1994latex,
  author  = {Lamport, Leslie},
  title   = {LaTeX: A Document Preparation System},
  journal = {Addison-Wesley},
  year    = {1994}
}
```

**Usage (biblatex + biber):**
```tex
\usepackage[backend=biber,style=numeric,sorting=nty]{biblatex}
\addbibresource{refs.bib}

Text with citation \parencite{lamport1994latex}.

\printbibliography
```

> For classic BibTeX, use `\bibliographystyle{plain}` + `\bibliography{refs}`.

---

## Project structure  

```
project/
├─ main.tex
├─ tex/        # chapters and sections (\input or \include)
├─ figs/       # figures
├─ bib/        # bibliography (refs.bib)
└─ build/      # build artifacts
```

In `main.tex` include parts like:
```tex
\input{tex/intro.tex}
\input{tex/methods.tex}
```

---

## Build and automation  

- **latexmk**:
  ```bash
  latexmk -pdf -interaction=nonstopmode -halt-on-error main.tex
  ```
  Automatically detects how many times to run the compiler and calls `biber`/`bibtex` if needed.

- **Engine selection**:
  - `-pdf` → pdfLaTeX,  
  - `-xelatex` → XeLaTeX,  
  - `-lualatex` → LuaLaTeX.  

- **Collaboration**: Overleaf supports version history and comments; locally use Git.  

---

## Common errors and their causes  

- **Undefined control sequence** — typo in a command name or missing package.  
- **Missing $ inserted** — math written outside `$...$`/`\\[...\\]`.  
- **Overfull \hbox** — line too long; try `\sloppy`, hyphenation, or rephrasing.  
- **File not found** — incorrect path to a figure/file.  
- **Package clash** — package conflicts; reorder loading (`hyperref` near the end).  

---

## Starter preamble (recommended)  

```tex
\documentclass[a4paper,12pt]{article}

% Language/Unicode
\usepackage{fontspec}
\usepackage{polyglossia}
\setmainlanguage{english}
\setotherlanguage{russian}
\setmainfont{Times New Roman}

% Math and symbols
\usepackage{amsmath,amssymb,mathtools}

% Hyperlinks and clever refs
\usepackage{hyperref}
\usepackage[nameinlink,noabbrev]{cleveref}

% Graphics and tables
\usepackage{graphicx}
\usepackage{booktabs}
\usepackage{caption}
\usepackage{subcaption}

% Typography and margins
\usepackage{microtype}
\usepackage{geometry}
\geometry{margin=2.5cm}
```

---

## Best practices  

- Write **semantically**: commands should reflect meaning, not appearance.  
- Avoid manual spacing/hyphenation — rely on LaTeX mechanisms.  
- Use `~` for non-breaking spaces: “Fig.~1”, “Ch.~2”, “etc.”.  
- Store figures in vector format (PDF/SVG→PDF) for clarity.  
- Split documents into parts and track your project with Git.  

---

## Conclusion  

LaTeX is a powerful tool for academic typesetting: it provides high-quality formula rendering, automated references and bibliography, and reproducibility of publications.  
By mastering the basics (structure, math, figures, tables, references, bibliography), you’ll be ready to prepare **coursework, articles, and presentations** at a professional level.  

🚀 If needed, a project template can be prepared for specific department or journal requirements.  

