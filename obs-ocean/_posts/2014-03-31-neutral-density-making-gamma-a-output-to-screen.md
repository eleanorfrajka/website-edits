---
title: 'Neutral density: Making gamma.a output to screen'
author: Eleanor Frajka-Williams
layout: post
header: no
permalink: /neutral-density-making-gamma-a-output-to-screen/
category_sticky_post:
  - 0
categories:
  - Analysis
  - Neutral density
tags:
  - code
  - downloads
  - Installing
---
This is what it should look like when you make gamma.a

`246-150:gamma eddifying$ make -f Makefile_gamma<br />
gfortran-mp-4.5 -O -ffixed-line-length-none  -c -o atg.o atg.f<br />
ar rv gamma.a atg.o<br />
ar: creating archive gamma.a<br />
a - atg.o<br />
gfortran-mp-4.5 -O -ffixed-line-length-none  -c -o depth-ns.o depth-ns.f<br />
ar rv gamma.a depth-ns.o<br />
a - depth-ns.o<br />
gfortran-mp-4.5 -O -ffixed-line-length-none  -c -o depth-scv.o depth-scv.f<br />
ar rv gamma.a depth-scv.o<br />
a - depth-scv.o<br />
gfortran-mp-4.5 -O -ffixed-line-length-none  -c -o derthe.o derthe.f<br />
ar rv gamma.a derthe.o<br />
a - derthe.o<br />
gfortran-mp-4.5 -O -ffixed-line-length-none  -c -o eosall.o eosall.f<br />
ar rv gamma.a eosall.o<br />
a - eosall.o<br />
gfortran-mp-4.5 -O -ffixed-line-length-none  -c -o eos8d.o eos8d.f<br />
ar rv gamma.a eos8d.o<br />
a - eos8d.o<br />
gfortran-mp-4.5 -O -ffixed-line-length-none  -c -o e-solve.o e-solve.f<br />
ar rv gamma.a e-solve.o<br />
a - e-solve.o<br />
gfortran-mp-4.5 -O -ffixed-line-length-none  -c -o gamma-errors.o gamma-errors.f<br />
ar rv gamma.a gamma-errors.o<br />
a - gamma-errors.o<br />
gfortran-mp-4.5 -O -ffixed-line-length-none  -c -o gamma-n.o gamma-n.f<br />
ar rv gamma.a gamma-n.o<br />
a - gamma-n.o<br />
gfortran-mp-4.5 -O -ffixed-line-length-none  -c -o goor.o goor.f<br />
ar rv gamma.a goor.o<br />
a - goor.o<br />
gfortran-mp-4.5 -O -ffixed-line-length-none  -c -o gamma-qdr.o gamma-qdr.f<br />
ar rv gamma.a gamma-qdr.o<br />
a - gamma-qdr.o<br />
gfortran-mp-4.5 -O -ffixed-line-length-none  -c -o get-lunit.o get-lunit.f<br />
ar rv gamma.a get-lunit.o<br />
a - get-lunit.o<br />
gfortran-mp-4.5 -O -ffixed-line-length-none  -c -o goor-solve.o goor-solve.f<br />
ar rv gamma.a goor-solve.o<br />
a - goor-solve.o<br />
gfortran-mp-4.5 -O -ffixed-line-length-none  -c -o index.o index.f<br />
ar rv gamma.a index.o<br />
a - index.o<br />
gfortran-mp-4.5 -O -ffixed-line-length-none  -c -o neutral-surfaces.o neutral-surfaces.f<br />
ar rv gamma.a neutral-surfaces.o<br />
a - neutral-surfaces.o<br />
gfortran-mp-4.5 -O -ffixed-line-length-none  -c -o ocean-test.o ocean-test.f<br />
ar rv gamma.a ocean-test.o<br />
a - ocean-test.o<br />
ar rv gamma.a read-nc.o<br />
a - read-nc.o<br />
gfortran-mp-4.5 -O -ffixed-line-length-none  -c -o scv-solve.o scv-solve.f<br />
ar rv gamma.a scv-solve.o<br />
a - scv-solve.o<br />
gfortran-mp-4.5 -O -ffixed-line-length-none  -c -o sig-vals.o sig-vals.f<br />
ar rv gamma.a sig-vals.o<br />
a - sig-vals.o<br />
gfortran-mp-4.5 -O -ffixed-line-length-none  -c -o stp-interp.o stp-interp.f<br />
ar rv gamma.a stp-interp.o<br />
a - stp-interp.o<br />
gfortran-mp-4.5 -O -ffixed-line-length-none  -c -o svan.o svan.f<br />
ar rv gamma.a svan.o<br />
a - svan.o<br />
gfortran-mp-4.5 -O -ffixed-line-length-none  -c -o theta.o theta.f<br />
ar rv gamma.a theta.o<br />
a - theta.o<br />
rm gamma-errors.o atg.o theta.o ocean-test.o eosall.o index.o goor-solve.o stp-interp.o depth-scv.o gamma-n.o svan.o goor.o neutral-surfaces.o eos8d.o sig-vals.o derthe.o gamma-qdr.o scv-solve.o e-solve.o get-lunit.o depth-ns.o`