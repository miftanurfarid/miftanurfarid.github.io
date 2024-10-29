---
layout: post
title: Creating a Problem Solution & Practice Template in LaTeX
date: 2021-06-03 15:06:00
description: Learn how to design a structured template for problem solutions and practice questions in LaTeX to enhance your documents.
tags: latex
categories: latex
---

**Creating a Problem Solution & Practice Template in LaTeX**

In a previous post, I demonstrated how to create an example environment in LaTeX. This time, I will show you how to create a template for problem solutions and practice questions in LaTeX.

In the preamble, include the following code:

```latex
\newcounter{example}
\counterwithin{example}{chapter}

\newcounter{practice}
\counterwithin{practice}{chapter}

\newcounter{solution}
\counterwithin{solution}{chapter}

\newcommand\Example{%
    \stepcounter{example}%
    \noindent
    \textbf{Example \theexample.}~%
    \setcounter{solution}{0}%
}

\newcommand\Practice{%
    \stepcounter{practice}%
    \noindent
    \textbf{Practice \thepractice.}~%
}

\newcommand\TheSolution{%
    \noindent
    \textbf{Answer:}\\%
}
```

An example of its usage is as follows:

```latex
\documentclass{book}
\usepackage[indonesian]{babel}

\newcounter{example}
\counterwithin{example}{chapter}

\newcounter{practice}
\counterwithin{practice}{chapter}

\newcounter{solution}
\counterwithin{solution}{chapter}

\newcommand\Example{%
    \stepcounter{example}%
    \noindent
    \textbf{Example \theexample.}~%
    \setcounter{solution}{0}%
}

\newcommand\Practice{%
    \stepcounter{practice}%
    \noindent
    \textbf{Practice \thepractice.}~%
}

\newcommand\TheSolution{%
    \noindent
    \textbf{Answer:}\\%
}

\parindent 0in
\parskip 1em

\begin{document}
     
    \chapter{This is the title of Chapter 1}
     
    \section{This is the title of Section 1}
     
    \subsection{This is the title of Subsection 1}
     
    \Example This is the first question in Subsection 1. If the question is long enough, it will appear like this. The example number follows the chapter number.
     
    \TheSolution This is the answer to Example 1.
     
    \Practice This is the first practice question in Chapter 1 without an answer.
     
    \Example This is the next example question.
     
    \TheSolution This is the answer to Example 2.
     
    \subsection{This is the title of Subsection 2}
         
    \Example This is the first question in Subsection 2. Although it is a different subsection, the example number continues from the previous one, as it is based on the chapter number.
     
    \TheSolution This is the answer to Example 1.
     
    \Practice This is the first practice question in Chapter 1 without an answer.
     
    \Example This is the next example question.
     
    \TheSolution This is the answer to Example 2.
         
    \section{This is Subsection 2}
     
    \Example This is the first question in Subsection 2. Although it is a different subsection, the example number continues from the previous one, as it is based on the chapter number.
     
    \TheSolution This is the answer to Example 1.
     
    \Practice This is the first practice question in Chapter 2 without an answer.
     
    \Example This is the next example question.
     
    \TheSolution This is the answer to Example 2.
     
    \chapter{This is the title of Chapter 2}
     
    \section{This is the title of Section 1}
     
    \subsection{This is the title of Subsection 1}
     
    \Example This is the first question in Subsection 1 of Chapter 2. If the question is long enough, it will appear like this. The example number follows the chapter number.
     
    \TheSolution This is the answer to Example 1.
     
    \Practice This is the first practice question in Chapter 1 without an answer.
     
    \Example This is the next example question.
     
    \TheSolution This is the answer to Example 2.
     
\end{document}
```

The result will look like this:

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/01-edited.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/02-edited.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/03-edited.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

Source: https://tex.stackexchange.com/questions/128337/problem-solution-template

