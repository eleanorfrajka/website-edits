---
title: Satellite data
author: Eleanor Frajka-Williams
layout: page
header: no
---
<figure id="attachment_1085" style="width: 300px;" class="wp-caption alignright">[<img src="http://i1.wp.com/69.195.124.112/~frajkawi/_sites/wp-content/uploads/2012/08/modis_sst1-300x259.png?resize=300%2C259" alt="Figure caption: Average SST from 2004 through 2010, from MODIS satellite." class="size-medium wp-image-1085" data-recalc-dims="1" />][1]<figcaption class="wp-caption-text">Figure caption: Average SST from 2004 through 2010, from MODIS satellite.</figcaption></figure>  
Satellite observations provide an unprecedented view of the ocean variability in space and time, though primarily at the sea surface. Below are a collection of oceanographic data sets (primarily for physical oceanography) that are freely available online. I&#8217;ve recorded the steps I&#8217;ve taken to access the data, and in some cases, Matlab scripts or functions to parse the data into Matlab.

> If the code or instructions below are helpful to you, I&#8217;d love to hear it. Always nice to know whether it&#8217;s worthwhile to put these kinds of instructions online. Even better, if you encounter and fix a relevant data-access issue that isn&#8217;t in the &#8220;troubleshooting&#8221; below or know a better way to access the data, let me know so I can add it to the page.

### Satellite data products

  1. **Sea surface height (SSH) &#8211; along track**, from satellite altimetry. These data are available directly under the satellite orbits. The product described here is the Beckley product, available from PODAAC. See [along-track gridded SSH][2].
  2. **Sea surface height (SSH) & velocity** from satellite altimetry. Steps to download [Gridded products from AVISO][3], at a product resolution of daily and 1/4 degree.
  3. **Sea surface temperature (SST)** from AMSR-E microwave satellite, since 2002. Microwave is useful because it can see through clouds, however data are absent near coastlines. See [steps to download AMSR-E][4].
  4. **Sea surface temperature (SST)** from AVHRR infrared satellite. These data are higher resolution than microwave, but there are gaps when there are clouds. See [steps to download data][5].
  5. **Ocean Mass/Ocean Bottom Pressure (OBP)** from GRACE gravity satellites. The latest version (as of May 2015) is Release 5. See [steps to download][6] &#8211; thanks [Cecelia][7]! 
      * **Ocean color/chlorophyll** from MODIS Aqua, since 2002. (Steps are similar if you want the SeaWiFS data, 1997-2008). See [steps to download][8], available at 4km resolution (or better).
      * **Surface winds from QuikSCAT**, a single scatterometer from 2002-2009. See [steps to access data][9].
      * **Multi-source surface winds**, but all based on data, the CCMP (Cross-calibrated multi-platform) global surface winds. See [steps to access CCMP][10]. This is a surface wind product which is based on data (rather than reanalysis). Unfortunately, if you&#8217;re looking for recent wind data, this may not be the right product for you as it is updated rather infrequently.</ol> 
    ### Other websites with data
    
      1. [Hadley Sea surface temperature][11]
      2. [Sea ice &#8211; all about the various data available][12] (links to the National Snow and Ice Data Center)
    
    *&#8211;updated May 2015&#8211;*

 [1]: http://i0.wp.com/observationaloceanography.com/wp-content/uploads/2012/08/modis_sst1.png
 [2]: http://observationaloceanography.com/along-track-gridded-altimetry/ "Along-track gridded altimetry"
 [3]: http://observationaloceanography.com/ssh-velocity-altimetry/ "SSH & velocity – Altimetry"
 [4]: http://observationaloceanography.com/sst-amsre/ "Sea surface temperatures – AMSRE microwave data"
 [5]: http://observationaloceanography.com/satellite-data/sea-surface-temperatures-avhrr-pathfinder/
 [6]: http://observationaloceanography.com/ocean-mass-grace/ "Ocean mass – GRACE"
 [7]: http://psc.apl.washington.edu/wordpress/people/students/cecilia-peralta-ferriz/
 [8]: http://observationaloceanography.com/ocean-color-modis-aqua/ "Ocean color – MODIS Aqua"
 [9]: http://observationaloceanography.com/winds-quikscat/ "Winds – QuikSCAT"
 [10]: http://observationaloceanography.com/winds-ccmp/ "Winds – CCMP (Cross-calibrated multi-platform)"
 [11]: http://www.metoffice.gov.uk/hadobs/hadisst/
 [12]: http://nsidc.org/data/seaice/index.html