---
title: 'Analysis &#8211; overview'
author: Eleanor Frajka-Williams
layout: post
permalink: /analysis-overview/
header: no
category_sticky_post:
  - 47
categories:
  - Analysis
tags:
  - stub
---
I use a Mac, with Matlab as my primary tool for data processing. Below are a few resources I&#8217;ve compiled for integrating freely available data with Matlab, compiling Neutral density code in Fortran on a Mac, and making figures using GMT.

## Oceanographic data

  * [Oceanographic data][1] free to download.  
    including QuikScat, World Ocean Atlas, World Ocean Database, AVISO gridded altimetry, gridded along-track altimetry, Argo float profiles, Sea surface color from SeaWiFS and MODIS satellites, ETOPO bathymetry, NCEP reanalysis 2 products and more as I find them and use them myself.

## Neutral density

  * [Neutral density code][2]. Neutral density is a (relatively) new way to represent conservative density in the ocean. Installing the code to calculate it is somewhat tricky, and I&#8217;ve finally managed to compile the CSIRO neutral density code on my Mac. Since it was an extended process, I&#8217;ve documented how I&#8217;ve done it, in case it can be helpful to others. Many thanks to Sally Close and Steve Alderson for their help.

## Macports

  * Macports isn&#8217;t really a tool for oceanography, but it&#8217;s an important step to installing either GMT5 or the CSIRO neutral density code on a Mac.  
    See the general instructions [here][3].

 [1]: http://frajka-williams.com/resources/data-sources/
 [2]: http://frajka-williams.com/resources/neutral-density/
 [3]: http://frajka-williams.com/resources/using-macports-for-oceanography/