---
title: 'SST &#8211; AMSRE microwave'
author: Eleanor Frajka-Williams
layout: page
header: no
---
SSMI provides the data. Read more about their satellite data products here: <http://www.ssmi.com/>

Browse daily images from [http://www.ssmi.com/sst/microwave\_oi\_sst_browse.html][1].

There are a number of optimally interpolated products, but I&#8217;m sticking to a single dataset here, rather than a merged one. Lots of current research active on how to merge different products, and I&#8217;m not up-to-date, so it&#8217;s simpler just to stick to one.

### Download the data using FTP

  1. Datafiles can be downloaded via ftp from ftp.discover-earth.org/sst using the command:  
    `$ ftp -i ftp.discover-earth.org`  
    Use &#8216;anonymous&#8217; as your login and provide your e-mail address as a password.  
    `> cd sst/daily/asmre/<br />
> mget *2011*gz`  
    I prefer to download one year at a time, in case something gets interrupted (or so I can have multiple tabs in a terminal window downloading simultaneously. For information, it appears to be taking me about 30 min per year (365 daily images) to download the data.
  2. Back on your local machine, unzip all the data with a  
    `$ gunzip *gz`  
    Each daily image file is about 1.0MB.

### Read into Matlab

  1. Load in the data using the [read\_rss\_oisst.m][2] code provided by [http://www.remss.com/sst/microwave\_oi\_sst_browse.html][3] at this location: <ftp://ftp.discover-earth.org/sst/daily/read_routines/matlab/>. It&#8217;s probably quickest to set up a script to call this, looping through each filename. Note, this is for the AMSRE OI fusion product, but if you want something else, matlab-files are similarly available.

*&#8211;updated Jul 2013&#8211;*

 [1]: http://www.ssmi.com/sst/microwave_oi_sst_browse.html
 [2]: ftp://ftp.discover-earth.org/sst/daily/read_routines/matlab/read_rss_oisst.m
 [3]: http://www.remss.com/sst/microwave_oi_sst_browse.html