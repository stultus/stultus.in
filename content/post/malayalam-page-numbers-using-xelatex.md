+++
date = "2013-10-03T09:32:45-04:00"
draft = false
title = "Malayalam Page Numbers in XeLatex"
highlight = true
tags = ["xelatex", "malayalam", "hack", "unicode"]
+++

Recently I had an opportunity to be a part of an effort to enable [SCERT](http://www.scert.kerala.gov.in/)(The Govt. organization which is responsible for the content, curriculum and the textbooks which are used in the schools of the state) to use unicode technologies for textbook publishing. 

As part of this effort, we tried to typeset Malayalam textbooks for 5th, 7th and 11th standards using `xelatex`. 

I wrote the following macro to automatically generate the page numbers using [malayalam numerals](https://en.wikipedia.org/wiki/Malayalam_script#Other_symbols)

```
    %%%———–Malayalam Page Number—————%%%%

    \makeatletter
    \def\@malnumber#1{\expandafter\@@malnumber\number#1\@nil}
    \def\@@malnumber#1{%
    \ifx#1\@nil
    \else
    \char\numexpr#1+”0D66\relax
    \expandafter\@@malnumber\fi}
    \def\malcounter#1{\expandafter\@malnumber\csname c@#1\endcsname}
    \def\malnumeral#1{\@@malnumber#1\@nil}
    \makeatother

    \def\MalpageNum{\malcounter{page}}
```
The `\MalpageNum` command will provide the current page number using the Malayalam numerals.

Happy Hacking!!
