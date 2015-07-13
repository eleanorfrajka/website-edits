---
title: 'Ocean mass &#8211; GRACE'
author: Eleanor Frajka-Williams
layout: page
header: no
---
<figure id="attachment_1438" style="width: 300px;" class="wp-caption alignright">[<img src="http://i1.wp.com/69.195.124.112/~frajkawi/_sites/wp-content/uploads/2013/02/grace_eof_obp1-300x262.png?resize=300%2C262" alt="GRACE data for the North Atlantic from Oct 2004, CSR version projected onto EOFs, RL05." class="size-medium wp-image-1438" data-recalc-dims="1" />][1]<figcaption class="wp-caption-text">GRACE data for the North Atlantic from Oct 2004, CSR version projected onto EOFs, RL05.</figcaption></figure>  


### About the data

PODAAC provides the data. Information about the GRACE products available can be found at <http://grace.jpl.nasa.gov/data/GRACEMONTHLYMASSGRIDSOCEAN/>.

### Downloading and extracting

  1. The latest version (as of Feb 2013) is the RL05. This has a new correction from Aug 2012, and all months should be downloaded to replace older files. 
  2. **ASCII format**: 
      1. To get the monthly, global fields of ocean bottom pressure, go to <ftp://podaac-ftp.jpl.nasa.gov/allData/tellus/L3/ocean_mass/RL05/ascii/>.  
        Here the data are available in ASCII format.  
        If you have the Firefox free plugin [Download them all][2] then you can right click on this page, and download the files into the directory of your choice. 
      2. If you don&#8217;t have DTA, you can use anonymous ftp. At the time of initial writing (Feb 2013), this didn&#8217;t work for me, but I have since been able to use it. I typically log in using a  
        `$ ftp -i podaac-ftp.jpl.nasa.gov`  
        and then navigate to the directory I need, for example,  
        `> cd allData/tellus/L3/ocean_mass/RL05/ascii/`  
        and then use the mget command to download files.  
        `> mget *gz` 
      3. To unzip the data, quick the ftp using the &#8216;exit&#8217; command:  
        `> exit`  
        then on my local machine, in the download directory, extract the data using  
        `$ gunzip *`  
        to unzip all the data into ASCII format. If you aren&#8217;t on a Unix machine or a Mac, you can use gunzip within Matlab. Just navigate to the directory with the data files, and type a   
        `>> !gunzip *`
      * **Netcdf**: Netcdf format is easier to work with as all months are packaged into a single file. For these, instead of the `ascii/` directory, navigate to the `netcdf/<code> directory.  The file contains variables <code>lon` in degrees east (360 values), `lat` in degrees north (180 values), `time` with length 117 for the version from 2003-01 through 2013-04 for CSR, helpfully: `time_bounds` which is `117 x 2` so says the start and end time for the period that each data point represents, and finally, `lwe_thickness` or liquid water equivalent in \[cm\] (size 117 180 360). </ol> 
    ### Loading into Matlab
    
    **For ASCII version**: You now have a gaggle of *.txt files, but you want to parse them into Matlab format. I'm supplying a couple of the scripts I use. They are not written for speed, so even though the GRACE dataset is not particularly large, it will take a while to load it all in.
    
      1. Parse the individual \*.txt files into a \*.hdr file and a *.dat file using [parse\_grace\_to_dathdr.m](). 
      2. Now transform the \*.dat file into a \*.mat file in Matlab format. This part is particularly slow since it repeats the evaluation of the lat and lon vectors each time. Using [read\_grace\_ascii\_to\_mat.m]().
      3. If you are reading in a lot of files in order to make a time series, you will want to nest these functions in a loop.

 [1]: http://i1.wp.com/69.195.124.112/~frajkawi/_sites/wp-content/uploads/2013/02/grace_eof_obp1.png
 [2]: http://www.downthemall.net/