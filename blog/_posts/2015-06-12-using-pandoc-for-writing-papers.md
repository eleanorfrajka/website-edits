---
layout: post
title: "Using Pandoc/Markdown for writing"
category: workflow
permalink: /:year/:month-:day-:title.html
date: "2015-06-12"
updated: "2015-07-07"
tags:
 - workflow
---

## Tools for writing in Academia

Traditionally, scientists communicate their results by writing.  While social media and other platforms now abound, writing is still a critical part of what we do.  What tools should you use for writing?  The two biggest contenders are **Latex** and **Word**.  However, each has their problems.

For me, the problem boils down to:
- I like the look of, referencing, equation formatting and bibliography handling of Latex. 
- In working with other people on manuscripts, I like using track changes in Word.  Some co-authors insist on it.

Maintaining active copies of both is inefficient.

The solution I've now come across is using Pandoc and markdown.  This particular solution has one primary benefit:
- Markdown is easier to read than tex, and allows you to write without the distraction of formatting.

## Original solution

I started with the very helpful example from nikolasanders.  This got me most of the way there.

## Useful modifications

- Citations
    - Found the citation styles corresponding to a typical oceanographic journal, `american-geophysical-union.csl`.  More are available.
    - To cite more than one paper in a set of brackets, join with semi-colons

    `[@Lee-etal-1996; @Roberts-etal-2013]`

- Controlling the appearance
    - **Latex template:** Updated the `template1.latex` file more to my liking
    - **Word styles:** Created a `reference.docx` file to change the default styles in a Word document
    - **Numbered sections in Word:** Part of this `reference.docx` was chosing header 1, header 2 and header 3 to be numbered format with outline so that the sections were numbered like in latex.
    - **Numbered sections in Latex:** Added pandoc option `--number-sections` to number my sections
- Automatic referencing:
    - **Added filter for figure referencing:** `pandoc-fignos` which then  requires `{#fig:mylabel}` to be referenced as `@fig:mylabel`

- Created a script file so I wouldn't have to remember my commands and filters
    - Instead of just creating the .docx and latex .pdf file, I also wanted to see what the .tex file looked like.  This was useful in understanding how the `template1.latex` file was used.  Added this line to my script

    `pandoc -S -o antilles-paper.tex --number-sections --filter pandoc-fignos --template=template1 --filter pandoc-citeproc antilles-paper.md`


