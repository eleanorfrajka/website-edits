---
title: 'Ocean color &#8211; MODIS'
author: Eleanor Frajka-Williams
layout: page
category_sticky_post:
  - 0
header: no
---
<figure id="attachment_1087" style="width: 208px;" class="wp-caption alignright">[<img src="http://i1.wp.com/69.195.124.112/~frajkawi/_sites/wp-content/uploads/2012/10/modis_chl1-208x300.png?resize=208%2C300" alt="MODIS chlorophyll from Sea surface color, averaged from Sep 2002 to Sep 2012." class="size-medium wp-image-1087" data-recalc-dims="1" />][1]<figcaption class="wp-caption-text">MODIS chlorophyll from Sea surface color, averaged from Sep 2002 to Sep 2012.</figcaption></figure>NASA provides the data at <http://oceancolor.gsfc.nasa.gov/>

Browse images at their [level 3 browser][2] where you can select products, time resolution (daily to monthly and longer), and spatial resolution (4 or 9 km).

### Downloading the data using wget

The instructions below will be to download 9km resolution 8-day composites of chlorophyll a, from the MODIS sensor on the Aqua platform. Note that NASA&#8217;s ocean biology team have moved away from using FTP data download in favor of http data download. Their forum post on the topic (how-to) can be found [here][3].

  1. Data files can be downloaded from oceancolor.gsfc.nasa.gov using the wget* command  
    `% wget -q -O - http://oceandata.sci.gsfc.nasa.gov/MODISA/Mapped/8Day/9km/chlor/2002/ | grep CHL | wget -N --wait=0.5 --random-wait --force-html -i -`  
    This is actually 3 separate commands, separated by the &#8220;pipe&#8221; operator, the &#8220;|&#8221; which takes the result of the previous command and pipes it into the following command. So the first wget through before the first pipe lists the contents on the website specified [//oceandata.sci.gsfc.nasa.gov/MODISA/Mapped/8Day/9km/chlor/2002/][4]. If you navigate to that link in your web browser, you will see the listing of files in that directory. The second command, the `grep CHL` selects only those lines which match the string &#8220;CHL&#8221;, which is in all the file names of interest. One could equally have chosen &#8220;9km&#8221; as the matching string. Finally, those lines are piped through the last `wget` command which downloads them into whatever directory on your local machine you were currently operating in. 
  2. To download a different product, you can navigate up or down directory in your web browser to find the appropriate location. Note that this only downloaded those data files from 2002, so it needs to be repeated for each year of data you would like to retrieve.

*Note that for a Mac you need to install wget on your machine. If you use a package manager like Macports, you can install it with the command  
`$ sudo port install wget`  
Be sure your Xcode has been updated (via the Mac App store), otherwise you may run into issues. For information on installing Macports, see <http://www.macports.org/>.

### Un-compressing the data

  1. For *.bz2 files (about 8MB each), use the command  
    `$ bunzip2 *`
  2. Each unzipped file represents a global image of ocean color data, at 9km resolution, and is about 36 MB large. 

### Reading into Matlab

You can download all four m-files listed below in a zip file here: [color_mfiles.zip][5].

  1. There&#8217;re four pieces of Matlab code that I&#8217;ve written to load the data. They serve a few purposes. The first function, `load_color_1file.m` can read a single HDF color file, and convert it into a structure with 3 fields: data (for the chlorophyll data as a matrix), lon and lat, for longitude and latitude.
  2. The second function loads a full year of data from a single directory on your local computer and is `load_color_1yr.m`. It calls the first function. This means that all chlorophyll files should be in one directory, and no other files from the NASA website (like PAR or k490) should be in that same directory. 
  3. The third file is a script that loads all years for a specific region. It is `color_extractreg_scr.m`. You define the region with latlim, lonlim. The result of running the script is to generate one matfile per year. This is in part because some of these files can be quite large, depending on the time and space resolution of the data you&#8217;ve downloaded, and the size of the region you&#8217;ve chosen. It is also helpful when updating your files as more data becomes available, because you only need to create the most recent year.
  4. The last file is also a script, and all it does is to concatenate together the different years of data. It is `color_catyrs_scr.m`. You can also change the region definitions (i.e. make them a further subset of the previous regions selected in `color_extractreg_scr.m`. However, because they work from the single year files that were created in step 3, you can&#8217;t define a new larger region at this point, but would need to rerun step 3 first with the larger region, before running this one.

*&#8211;updated May 2014&#8211;*

 [1]: http://i2.wp.com/observationaloceanography.com/wp-content/uploads/2012/10/modis_chl1.png
 [2]: http://oceancolor.gsfc.nasa.gov/cgi/l3?per=DAY
 [3]: http://oceancolor.gsfc.nasa.gov/forum/oceancolor/topic_show.pl?tid=3081
 [4]: http://oceandata.sci.gsfc.nasa.gov/MODISA/Mapped/8Day/9km/chlor/2002/
 [5]: https://www.dropbox.com/s/fk90waoxa4qjq2h/color_mfiles.zip