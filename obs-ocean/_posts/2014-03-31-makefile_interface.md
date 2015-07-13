---
title: Makefile_interface
author: Eleanor Frajka-Williams
layout: post
header: no
permalink: /makefile_interface/
category_sticky_post:
  - 0
categories:
  - Analysis
  - Neutral density
tags:
  - code
  - downloads
---
Note: Graeme got an error that `gfortran` was not found, but by changing the line `FC=gfortran` to `FC=gfortran-mp-4.5`, it worked. (See bolded text below.)

`<br />
PROGRAM = glabel_matlab nsfces_matlab</p>
<p>FC = gfortran<strong>-mp-4.5</strong></p>
<p>FFLAGS = -O2 -ffixed-line-length-none</p>
<p>.KEEP_STATE:</p>
<p>.PRECIOUS :</p>
<p>LIBS       =  ../gamma.a -L/opt/local/lib -lnetcdff</p>
<p>all: glabel_matlab nsfces_matlab</p>
<p>glabel_matlab: glabel_matlab.o<br />
        $(FC) $(FFLAGS) $(LIBS) -o glabel_matlab glabel_matlab.o</p>
<p>nsfces_matlab: nsfces_matlab.o<br />
        $(FC) $(FFLAGS) $(LIBS) -o nsfces_matlab nsfces_matlab.o</p>
<p>clean :<br />
        rm -f *% core $@<br />
`