---
title: 'Winds &#8211; QuikSCAT'
author: Eleanor Frajka-Williams
layout: page
header: no
---
QuikSCAT is a scatterometer-based satellite wind product from the SeaWinds instrument on the QuikSCAT satellite. It was operating from 19 Jul 1999 through 22 Nov 2009. Data are provided by PODAAC. Find out about the available products at <http://podaac.jpl.nasa.gov/datasetlist?ids=Platform&values=QUIKSCAT>

The level 3 daily product at 0.25 degrees is described here: [http://podaac.jpl.nasa.gov/dataset/QSCAT\_LEVEL\_3_V2][1].

### Download the data using FTP

  1. Data are available in HDF format from <ftp://podaac-ftp.jpl.nasa.gov/allData/quikscat/L3/jpl/v2/hdf>. If you ftp to the directory, use  
    `$ ftp podaac-ftp.jpl.nasa.gov` 
  2. Change directory to the one with the data you want:  
    `<br />
230 Login successful.<br />
Remote system type is UNIX.<br />
Using binary mode to transfer files.<br />
ftp> cd allData/quikscat/L3/jpl/v2/hdf<br />
ftp> cd hdf<br />
250 Directory successfully changed.<br />
ftp> ls<br />
229 Entering Extended Passive Mode (|||53526|)<br />
150 Here comes the directory listing.<br />
drwxrwxr-x    2 ftp      ftp         16384 Aug 09  2012 1999<br />
drwxrwxr-x    2 ftp      ftp         28672 Aug 09  2012 2000<br />
drwxrwxr-x    2 ftp      ftp         28672 Aug 09  2012 2001<br />
drwxrwxr-x    2 ftp      ftp         32768 Aug 09  2012 2002<br />
drwxrwxr-x    2 ftp      ftp         28672 Aug 09  2012 2003<br />
drwxrwxr-x    2 ftp      ftp         28672 Aug 09  2012 2004<br />
drwxrwxr-x    2 ftp      ftp         28672 Aug 09  2012 2005<br />
drwxrwxr-x    2 ftp      ftp         28672 Aug 09  2012 2006<br />
drwxrwxr-x    2 ftp      ftp         28672 Feb 28  2011 2007<br />
drwxrwxr-x    2 ftp      ftp         28672 Feb 28  2011 2008<br />
drwxrwxr-x    2 ftp      ftp         28672 Feb 28  2011 2009<br />
226 Directory send OK.<br />
ftp><br />
`
  3. Change directory into each of the year directories and use `ftp> mget *gz` to download the data files. These will appear on your local machine in the directory from which you initiated the `ftp`. 

### Reading data into Matlab

The folks at PODAAC provide software for reading the data into Matlab. If you change directory to the location `/allData/quikscat/L3/jpl/v2/sw/MATLAB_new`, download the file `read_QuikSCAT_L3.m`.

### Other notes

Note, QuikScat ended in Nov 2009. I have heard that CCMP, also available on the JPL website, is a pretty good substitution. It is a blended product from several satellites.

*&#8212; last updated Jul 2013&#8211;*

 [1]: http://podaac.jpl.nasa.gov/dataset/QSCAT_LEVEL_3_V2