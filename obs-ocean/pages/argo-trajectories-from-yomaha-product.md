---
title: 'Argo trajectory data &#8211; YoMaHa'
author: Eleanor Frajka-Williams
layout: page
header: no
---
Basic instructions to download a product of Argo speeds calculated from the GPS positions.

URL: <http://apdrc.soest.hawaii.edu/projects/Argo/data/trjctry/?F=2>

### Download the data

  1. From the URL above, download the zipped data by right-clicking on the file `yomaha07.dat.gz` and selecting &#8220;save link as&#8230;&#8221;
  2. Unzip it into some directory using  
    `$ gunzip yomaha07.dat.gz`

### Read into Matlab

  1. Load it and make a few plots using: [basic\_yomaha\_scr.m][1]

 [1]: http://www.personal.soton.ac.uk/eefw1u08/matlab/basic_yomaha_scr.m