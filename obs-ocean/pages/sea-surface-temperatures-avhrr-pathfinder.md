---
title: 'SST &#8211; AVHRR infrared'
author: Eleanor Frajka-Williams
layout: page
header: no
---
PO.DAAC and NOAA NODC both host the data. Read about data access from NOAA here: <http://www.nodc.noaa.gov/sog/pathfinder4km/available.html> or the various products in more detail on PODAAC here: <http://podaac.jpl.nasa.gov/datasetlist?search=Pathfinder>. The full resolution L3 product is 4 km. AVHRR is an infrared imager, so cannot see through clouds.

As of Oct 2013, the latest version available is Version 5.2. Browse images from the earlier, 5.0 version here: <http://data.nodc.noaa.gov/pathfinder/Version5.0/browse_images/>.

This is a single data source dataset (Level 3), rather than a merged one.

<img src="http://i0.wp.com/data.nodc.noaa.gov/pathfinder/Version5.0/browse_images/7day/2006/DecloudedSST/200646.s04w3pfv50-sst-qual7.hdf.jpg" alt="AVHRR declouded SST, Version 5.0" data-recalc-dims="1" />

### Download the data using FTP

  1. Datafiles can be downloaded via ftp from ftp://ftp.nodc.noaa.gov/pub/data.nodc/pathfinder using the command:  
    `$ ftp -i ftp.nodc.noaa.gov`  
    Use &#8216;anonymous&#8217; as your login and provide your e-mail address as a password.  
    `> cd pub/data.nodc/pathfinder/Version5.2/2012<br />
> mget *day*nc`  
    for daytime temperatures or for nighttime temperatures, use  
    `> mget *night*nc`  
    Because the data are arranged in subdirectories by year, it is simplest to download one year at a time.  
    For information, it appears to be taking me about 30 min per year (365 daily images) to download the data.

### Read into Matlab

  1. These are netcdf files, so for a later version of Matlab (from 2011, I think) you can use the built-in netcdf tools to read the file. See if you have them by trying a `>> help ncdisp`.
  2. Otherwise, you can download the `mexnc` and `snctools` toolboxes.

*&#8211;updated Oct 2013&#8211;*