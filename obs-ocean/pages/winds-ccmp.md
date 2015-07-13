---
title: 'Winds &#8211; CCMP'
author: Eleanor Frajka-Williams
layout: page
header: no
---
[<img src="http://i1.wp.com/69.195.124.112/~frajkawi/_sites/wp-content/uploads/2012/08/ccmp_winds1-300x210.png?resize=300%2C210" alt="Winds over the North Atlantic from CCMP, 2010" class="alignright size-medium wp-image-1068" data-recalc-dims="1" />][1]CCMP is a global wind product based on satellite data (rather than reanalysis). Since QuikScat ended in Nov 2009, I have heard that CCMP is a pretty good substitution. Their briefest description of CCMP is &#8220;The CCMP datasets combine cross-calibrated satellite winds obtained from Remote Sensing Systems (REMSS) using a Variational Analysis Method (VAM) to produce a high-resolution (0.25 degree) gridded analysis.&#8221; Data are provided by PODAAC. More complete information about the CCMP products available can be found at their &#8220;Data Discovery&#8221; portal [here][2].

### Downloading the data using ftp

  1. If you aren&#8217;t sure what you want, I suggest starting with the &#8220;value-added 5-day mean ocean surface wind and pseudostress to approximate a satellite-only climatological data record.&#8221; Information about this particular version can be found here: [http://podaac.jpl.nasa.gov/dataset/CCMP\_MEASURES\_ATLAS\_L4\_OW\_L3\_5A\_5DAY\_WIND\_VECTORS\_FLK?ids=&values=][3]. 
  2. Get the CCMP datafiles from Level 4 pentads (5-day product), 0.25 degree at <ftp://podaac-ftp.jpl.nasa.gov/allData/ccmp/L3.5a/pentad/flk>.  
    I typically log in using a   
    `$ ftp -i podaac-ftp.jpl.nasa.gov`  
    and then navigate to the directory I need, for example,  
    `> cd OceanWinds/ccmp/L3.5a/pentad/flk`  
    and further to a year, ranging from 1987 to 2011 (as of writing), and month, from 01 to 12,  
    `> cd 2011/01`  
    then use the mget command to download files.  
    `> mget *gz` 
  3. To unzip the data, quick the ftp connection using the &#8216;exit&#8217; command:  
    `> exit`  
    then in a terminal window, use  
    `$ gunzip *`  
    to unzip all the data into netcdf format.

### Reading into Matlab

The files are in a standard netcdf format, so I suggest the tools &#8220;mexnc&#8221; and &#8220;snctools&#8221; to read them into Matlab. Update: The latest versions of Matlab (at least from Matlab 2012) have some native netcdf tools. Try a `>> help ncread` to see if you have them.

### Other notes

One disadvantage of using this product is that it is not updated particularly frequently. At time of update, Jul 2013, the product is available through Dec 31, 2011.)

*&#8211;last updated Jul 2013&#8211;*

 [1]: http://i2.wp.com/observationaloceanography.com/wp-content/uploads/2012/08/ccmp_winds1.png
 [2]: http://podaac.jpl.nasa.gov/datasetlist?ids=Measurement:Collections&values=Ocean+Winds:Cross-Calibrated+Multi-Platform+Ocean+Surface+Wind+Vector+Analysis+Fields&search=
 [3]: http://podaac.jpl.nasa.gov/dataset/CCMP_MEASURES_ATLAS_L4_OW_L3_5A_5DAY_WIND_VECTORS_FLK?ids=&values=