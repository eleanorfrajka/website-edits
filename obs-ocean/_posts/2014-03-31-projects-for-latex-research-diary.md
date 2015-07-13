---
title: Projects for Latex research diary
author: Eleanor Frajka-Williams
layout: post
header: no
permalink: /projects-for-latex-research-diary/
category_sticky_post:
  - 0
categories:
  - Communication
  - Latex
tags:
  - Latex
---
### Separate entries by project

I work on several projects in parallel, and I want to be able to create anthologies for individual projects, rather than search through an annual anthology.  
This required a little bit more modification.

  * I decided to prompt the user for a project name in the `src/add_entry.sh` script, which required the addition of two lines of code  
    echo -n &#8220;Pick a project name (Sverdrup, Antilles, GRACE): &#8221;  
    read -e PROJECT
  * For organisational purposes, this project name is saved in the filename as well,  
    `filename=$year-$month-$day-$PROJECT.tex<br />
`
  * I also decided to put this information in the `chead` of the document (center header) so that I can easily determine from looking at a page in the annual anthology what the topic is.  
    The simplest way to do this seemed to be to update the daily entry template, `src/entry.tex` to define the project in the same way as the user an institution:  
    `newcommand{project}{@project}`  
    which then allows the substitution of the project the user filled in from the script, by adding an additional line to `src/add_entry.sh` with the other `sed` lines:  
    `sed -i~ "s/@project/$PROJECT/g" $filename<br />
`

### Letting the anthology know about the separate projects

The `src/add_entry.sh` only knew about the project name because we prompted the user for it, then buried it in the text in the `project` definition, but also saved it in the filename. In order for anthology to know about the projects, we need a way to strip them out of the individual entry and put them together again.

The script `src/create_anthology.sh` reads the filename in the for loop near the end. I&#8217;ve added 4 lines to this&#8211;to take the filename, modify it to select only the non-date/non-extension part of it (i.e. the project name), and the put this project name back into the Tex document:  
``<br />
for i in $( ls $Year/$Year-*.tex ); do<br />
projj=${i%.*}<br />
ll=${#projj}<br />
proj=${projj:16:$ll}<br />
echo -e "n%%% --- $i --- %%%n" >> $tmpName<br />
echo "rhead{`grep workingDate $i | cut -d { -f 4 | cut -d } -f 1`}" >> $tmpName<br />
echo "chead{textsc{$proj}}" >> $tmpName<br />
sed -n '/begin{document}/,/end{document}/p' $i >> $tmpName<br />
echo -e "n" >> $tmpName<br />
echo "newpage" >> $tmpName<br />
done<br />
``  
In more detail:

  * The new action here is that `i` is the filename of an individual entry, like `2013/2013-08-08-Sverdrup.tex`. I need to remove the extension, which is done in the line `projj=${i%.*}` and saved to the new variable `projj`.
  * I then needed to strip the date information, which is everything up to character 16. The line `ll=${#projj}` gets the length of the string `projj`, and then `proj=${projj:16:$ll}` is the string `Sverdrup`.
  * This string `Sverdrup` is then added to the body of the new Latex document with the line `echo "chead{textsc{$proj}}" >> $tmpName` which updates the center header just for that entry.

And *voila!*, the anthology has page headers that tell the name of the project.

### Updated `src/compile_today.sh` for projects

Since the names of the projects are now in the Tex filenames, the script `src/compile_today.sh` also needed to be updated to handle the different project names. This was done with a similar loop as in `src/create_anthology.sh`  
`<br />
#!/bin/bash`

year=\`date +%G\`  
month=\`date +%m\`  
day=\`date +%d\`

TEXFILE=$year-$month-$day.tex  
Name=$year-$month-$day

for i in $( ls $Name*.tex ); do  
echo &#8220;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;&#8221;  
echo &#8220;Compiling $i&#8221;  
latex -interaction=batchmode -halt-on-error $i  
projj=${i%.*}  
dvips -q $projj.dvi  
ps2pdf $projj.ps  
done

### Creating anthologies by project

And now, the whole reason for separating by topics was to create anthologies by individual topic. This only required a slight modification of the `create_anthology.sh` for a `create_project.sh`, as well as an update to `Makefile`:

I&#8217;ve actually made 3 new changes here.

  * I&#8217;ve added some lines to the end of my Tex files to allow for citations within the notes to my bibliography `*.bib` file.
  * I&#8217;ve created a new title page using the the lovely one I found here: <http://www.latextemplates.com/template/formal-text-rich-title-page>, and put this as well as a few other bits into a new template page called `src/titlepage.tex`.
  * And I moved the latex-ing and bibtex-ing into the `src/create_project.sh` rather than leaving it in the `Makefile`

.

Below are the individual updates, briefly annotated, but for convenience, the `create_project.sh` and `titlepage.tex` are attached to the bottom of this page.

  1. The new lines are in choosing the project to tex:  
    `<br />
echo "Pick a project name (Sverdrup, HEA, GRACE, Workflow, RoyalSoc): "<br />
read -e PROJECT<br />
`
  2. Updating the file name for the research diary, which I now call 2013-Notes-GRACE.tex for the topic &#8220;GRACE&#8221;:  
    `<br />
Name="$Year-Notes-$PROJECT"<br />
`
  3. Defining the `project` within Latex:  
    `echo "newcommand{project}{$PROJECT}" >> $FileName<br />
`
  4. Then adding my new titlepage and other bits:  
    `<br />
cat src/titlepage.tex >> $FileName`
  5. Since I have the bibliography in each individual entry as well, the stripping of the good-bits of the notes is now here:  
    `<br />
sed -n '/begin{document}/,/bibliographystyle{apalike}/p' $i >> $tmpName<br />
`
  6. And the removal of those end bits updated:  
    `<br />
sed -i~ 's/bibliographystyle{apalike}//g' $tmpName<br />
`
  7. Finally, dumping back in the end bits:  
    `<br />
echo "bibliographystyle{apalike}" >> $FileName<br />
echo "bibliography{/Users/eddifying/Dropbox/_Documents/Bibtex/abbrv_full,/Users/eddifying/Dropbox/_Documents/Bibtex/totall}" >> $FileName<br />
`
  8. And then tex-ing the whole mess:  
    `<br />
latex $Name<br />
bibtex $Name<br />
latex -interaction=batchmode -halt-on-error $Name<br />
latex -interaction=batchmode -halt-on-error $Name<br />
dvips -q $Name<br />
ps2pdf $Name.ps<br />
`

For convenience, the files `create_project.sh` are attached, as is the `titlepage.tex`.