---
title: Makefile_gamma
author: Eleanor Frajka-Williams
layout: post
header: no
permalink: /makefile_gamma/
category_sticky_post:
  - 0
categories:
  - Analysis
  - Neutral density
tags:
  - code
  - downloads
---
``<br />
###<br />
###              DJ subroutine library gamma.a<br />
###</p>
<p>#include <makelib.mk></p>
<p>FC = gfortran-mp-4.5</p>
<p>SOURCES = atg.f<br />
          depth-ns.f<br />
          depth-scv.f<br />
          derthe.f<br />
          eosall.f<br />
          eos8d.f<br />
          e-solve.f<br />
          gamma-errors.f<br />
          gamma-n.f<br />
          goor.f<br />
          gamma-qdr.f<br />
          get-lunit.f<br />
          goor-solve.f<br />
          index.f<br />
          neutral-surfaces.f<br />
          ocean-test.f<br />
          read-nc.f<br />
          scv-solve.f<br />
          sig-vals.f<br />
          stp-interp.f<br />
          svan.f<br />
          theta.f</p>
<p>CPP-SOURCES = read-nc.F</p>
<p>OBJECTS = $(SOURCES:.f=.o)</p>
<p>FFLAGS = -O -ffixed-line-length-none</p>
<p>################################################################################</p>
<p>gamma.a: gamma.a($(OBJECTS))</p>
<p>read-nc.o: read-nc.F<br />
        gfortran-mp-4.5 $(FFLAGS) -DPWD="'`pwd`'" -c read-nc.F</p>
<p>clean:<br />
        -rm -f *% *.bak<br />
``