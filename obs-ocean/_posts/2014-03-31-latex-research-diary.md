---
title: Latex Research Diary
author: Eleanor Frajka-Williams
layout: post
header: no
permalink: /latex-research-diary/
category_sticky_post:
  - 18
categories:
  - Communication
  - Latex
tags:
  - Latex
  - Mac
---
I was looking for a better way to organise my research notes, and googling &#8220;Latex template for research notebook&#8221; stumbled upon [WriteLatex][1]. WriteLatex is an interesting cloud-storage idea for all your work, and could be very useful for collaborating on manuscripts. I tested out the **WriteLatex for Research** template and quite liked it, but I prefer something that doesn&#8217;t require my online presence to run. I found that the original template is available in a standalone package which has scripts to create entries and yearly-anthologies of notes. *Wonderful! *

It was designed for Unix/Linux. *Pity.*

So find below, the edits I made to the package to get it to run on my Mac OSX.

I also added one extra utility that was useful for me: the ability to organize entries by projects, and create individual anthologies per project. After it&#8217;s running on your computer, those edits are described [here][2].

## Using the Research-diary-project scripts for Latex

To make [Mikhail Klassen&#8217;s research diary style-file for Latex][3] work on Mac OS X, I had to make a couple of edits.

### File edits

Since I&#8217;m in the UK, I changed the papersize from `letterpaper` to `a4paper`

Since I&#8217;m using `latex` and not `pdftex`, I edited the file `src/entry.tex` which is the template for each daily entry, to have `logoEPS` rather than `logoPNG`.

### Latex and Path updates

These require Latex and dvips on your computer, both of which are part of the [MacTex][4] package for Latex. However, I found that I was unable to use them at the command line. (Test this by opening a terminal window and typing `$ latex`. If you get the error `Command not found`, you likely have the same issue.) So I edited my `PATH` in my `/Users/eddifying/.profile` file, which had previously be edited to get `gmt5` to work. The `export PATH` line now reads:  
`<br />
export PATH=/opt/local/bin:/opt/local/sbin:/opt/local/lib/gmt5/bin/:/usr/texbin/:$PATH<br />
`

### Edits to `src/add_entry.sh`

For the file `src/add_entry.sh`, the `sed` command would not work for me without an `extension` (see &#8220;`$ man sed`&#8221; for information on the `-i` option). So for the four lines with a `sed -i`, I added a tilde after the `-i` to become `sed -i~`, with the rest of the lines unchanged.

### Edits to `Makefile`

As instructed in the `Makefile` comments, update your year, name and institution.

Also, the `Makefile` may be an older version, because when I tried to run `$ make anthology`, I got the error  
`<br />
Creating anthology for research diary entries from the year 2013<br />
/bin/bash: scripts/create_anthology.sh: No such file or directory<br />
`  
which should be expected because the package I downloaded did not have a directory called `scripts/`, but I did find the file `create_anthology` in the `src/` directory. So this was updated in the `Makefile`.

I also removed the line under `anthology:` beginning with `okular`, since that seems to be a program to view pdf files.

*Note to fix: I don&#8217;t understand why when running latex as I call a `$ make anthology`, my `latex` command produces a `.dvi`-file rather than a `.pdf`-file, whereas when I ran the `add_entry`, it skipped straight to a pdf (rendering `dvips` and `ps2pdf` unnecessary). Possibly something about updating the path in one terminal window and not another?*

### Edits to `src/create_anthology.sh`

As before with `src/add_entry.sh`, all instances of the command `sed -i` were updated to `sed -i~`.

References to the directory `scripts/` were updated to `src/`

The line `echo "usepackage{researchdiary}" >> $FileName`  
was updated to reflect the location of the `research_diary.sty` file as  
`<br />
echo "usepackage{$Year/research_diary}" >> $FileName<br />
`

*And that should be enough to get research-diary working on your Mac!*

*&#8211;updated Aug 2013&#8211;*

 [1]: https://www.writelatex.com/signup?ref=f40bc79901a9
 [2]: http://observationaloceanography.com/projects-for-latex-research-diary/ "Projects for Latex research diary"
 [3]: https://github.com/mikhailklassen/research-diary-project
 [4]: http://tug.org/mactex/