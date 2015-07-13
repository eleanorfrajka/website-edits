---
title: Satellite data
author: Eleanor Frajka-Williams
layout: post
header: no
permalink: /satellite-data/
category_sticky_post:
  - 30
categories:
  - Oceanographic Data
  - Satellite data
tags:
  - Data
---
## Online Oceanographic Datasets and Data products from Satellites

<figure id="attachment_1085" style="width: 300px;" class="wp-caption alignright"><img src="http://i1.wp.com/69.195.124.112/~frajkawi/_sites/wp-content/uploads/2012/08/modis_sst1-300x259.png?resize=300%2C259" alt="Figure caption: Average SST from 2004 through 2010, from MODIS satellite." class="size-medium wp-image-1085" data-recalc-dims="1" />[1]<figcaption class="wp-caption-text">Figure caption: Average SST from 2004 through 2010, from MODIS satellite.</figcaption></figure>Below are a collection of oceanographic data sets (primarily for physical oceanography) that are freely available online. I&#8217;ve recorded the steps I&#8217;ve taken to access the data, and in some cases, Matlab scripts or functions to parse the data into Matlab.

> If the code or instructions below are helpful to you, I&#8217;d love to hear it. Always nice to know whether it&#8217;s worthwhile to put these kinds of instructions online. Even better, if you encounter and fix a relevant data-access issue that isn&#8217;t in the &#8220;troubleshooting&#8221; below or know a better way to access the data, let me know so I can add it to the page.

### Satellite data products

  1. [Sea surface height & velocities from altimetry][2]  
    (gridded AVISO, since 1992). This is the most commonly used gridded altimetry product available, providing sea surface height anomalies and surface velocities.
  2. [Sea surface height along satellite tracks &#8211; altimeters][3] (PODAAC, since 1992)
  3. [GRACE ocean mass/ocean bottom pressure][4] &#8211; thanks [Cecelia][5]! 
      * [Global surface winds from CCMP][6]  
        (Cross calibrated multi-platform). This is a surface wind product which is based on data (rather than reanalysis). Unfortunately, if you&#8217;re looking for recent wind data, this may not be the right product for you as it is updated rather infrequently.
      * [QuikSCAT surface winds][7].  
        This is surface wind data from a single scatterometer. It was operating until Nov 2009.
      * [Ocean color &#8211; MODIS Aqua][8]  
        (from 2002). Sea surface color-derived chlorophyll, available at 4km resolution (or better) since 2002. Some of the same download details can be used to access SeaWiFS data (1998-2008).
      * [Sea surface temperature &#8211; AMSR-E microwave satellite][9] (from 2002)</ol> 
    ### Other websites with data
    
      1. [Hadley Sea surface temperature][10]
      2. [Sea ice &#8211; all about the various data available][11] (links to the National Snow and Ice Data Center.)
    
    *&#8211;updated Mar 2014&#8211;*

 [1]: http://i0.wp.com/observationaloceanography.com/wp-content/uploads/2012/08/modis_sst1.png
 [2]: http://observationaloceanography.com/ssh-velocity-altimetry/ "SSH & velocity – Altimetry"
 [3]: http://observationaloceanography.com/along-track-gridded-altimetry/ "Along-track gridded altimetry"
 [4]: http://observationaloceanography.com/ocean-mass-grace/ "Ocean mass – GRACE"
 [5]: http://psc.apl.washington.edu/wordpress/people/students/cecilia-peralta-ferriz/
 [6]: http://observationaloceanography.com/winds-ccmp/ "Winds – CCMP (Cross-calibrated multi-platform)"
 [7]: http://observationaloceanography.com/winds-quikscat/ "Winds – QuikSCAT"
 [8]: http://observationaloceanography.com/ocean-color-modis-aqua/ "Ocean color – MODIS Aqua"
 [9]: http://observationaloceanography.com/sst-amsre/ "Sea surface temperatures – AMSRE microwave data"
 [10]: http://www.metoffice.gov.uk/hadobs/hadisst/
 [11]: http://nsidc.org/data/seaice/index.html
