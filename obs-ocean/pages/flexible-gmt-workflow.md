---
title: Flexible GMT Workflow
author: Eleanor Frajka-Williams
layout: page
category_sticky_post:
  - 0
header: no
permalink: '/figure-design/flexible-gmt-workflow/'
---
*Once you have GMT installed on your computer, and you&#8217;ve tried out a few sample scripts (or have spent a few years using GMT), you may want to think about more efficient ways to work with GMT. *

## Why do anything more than one script per figure?

This is intended to show you a way to use GMT which is

  * Flexible for rapid updates of figures (as in when the reviewer or co-author says a line is hard to see, or if you suddenly decide to change all your colormaps for salinity in a paper to something with better contrast/colorblind friendly).
  * Consistent in formatting a set of figures for a paper (same aspect ratios of figures, same font sizes and types, etc)
  * Conducive to updating figures without getting back into analysis code (as in if you want to change a figure for a talk or proposal, but don’t want to re-run the Matlab scripts you used to analyse the data and create the figure).  
    GMT also naturally creates a separation between your analysis software (i.e. Matlab) and presenta- tion of the results. This separation helps ensure a trackable workflow from the start to final analysed datasets.

While you can have a single script per figure, I prefer to set up a new directory (with substructure) for each project I&#8217;m working on. I separate projects based on the datasets or sets of analyses I&#8217;ve carried out. In this directory, there will be a single \`parent&#8217; script, from which all individual figure scripts are called. The parent script will also contain various settings and parameters, more than are in gmt.conf, for how I want figures in that project to appear.

If this sounds useful to you, then continue on&#8230;

## How to use this page:

Once you have GMT downloaded and installed on your computer,

  1. Get the PDF describing what to do: [GMT_workflow (PDF)][1] 
  2. Get the working directory. Download the zip file with the sample directory and scripts: [http://bit.ly/10gNNrF][2]. Unzip it on your computer
  3. Once you have the directory downloaded and unzipped, try the commands and edits suggested below to get a feel for how GMT works.

## What you&#8217;ll be able to do:

The working directory will contain everything you need to generate figures including

  * A map in Mercator projection, with land, lines, symbols and text annotation.
  * A figure with hydrographic sections of temperature, salinity and bathymetry, using a pattern fill.
  * A time series using native GMT time format.
  * A time series with custom axes, starting from Matlab time format.

*&#8212; updated Nov 2013&#8211;*

 [1]: http://observationaloceanography.com/wp-content/uploads/2013/06/GMT_workflow1.pdf
 [2]: https://www.dropbox.com/s/0tetp73y3k9rs20/2013_crashcourse_g5_new.zip