---
title: 'Hydrographic Atlas &#8211; WOA'
author: Eleanor Frajka-Williams
layout: page
header: no
---
This is a global climatology (i.e. average data fields), based on objectively mapping the data in the World Ocean Database (a collection of CTD, bottle, float and other data).

URL: <http://www.nodc.noaa.gov/OC5/WOA09/pr_woa09.html>

### Download the product

  1. Choose the resolution you want (1 degree), data field (temperature), then in the &#8220;Available file types&#8221; choose &#8220;All fields in csv format&#8221; at the bottom. In the right hand box, choose &#8220;climatology_csv.tar&#8221;. If you don&#8217;t choose the &#8220;all fields&#8221; option, the M<atlab scripts below may not be able to parse the data format.
  2. After downloading, move the file to the directory where you want to store the data, and extract the data. 
      1. Extract the tarball on your local machine using  
        `$ tar -xvf climatology_csv.tar`.  
        This creates a bunch of `t_<em>TT</em>_1d.tar.gz` files where `<em>TT</em>` ranges from 00 to 16 for the time period (annual, 4 seasons, 12 months).
      2. Unzip the data files on your local machine using  
        `$ gunzip *gz`.  
        If applied to a single file as `$ gunzip t_00_1d.tar.gz`, it will unzip this file, leaving `t_00_1d.tar`.
      3. Extract these tarballs as well using  
        `% tar -xvf *tar`.  
        If applied to a single file as `$ tar -xvf t_00_1d.tar` it will untar this packet of files, resulting in `t_00_<em>DD</em>_1d.csv` where `<em>DD</em>` ranges from 01 to 40, the standard depth levels (see Table 2 in [woa09documentation.pdf][1]).

### Read into Matlab

  1. Use the scripts [rcwm_scr.m][2] and [read\_csv\_write_mat][3] to parse the `*.csv` files into Matlab. You will need to update the variable names at the top of `rcwm_scr.m` to match the directories you&#8217;d like to use, and the data fields and resolutions you&#8217;ve downloaded.

*&#8211;updated Jul 2013&#8211;*

 [1]: ftp://ftp.nodc.noaa.gov/pub/WOA09/DOC/woa09documentation.pdf
 [2]: http://www.personal.soton.ac.uk/eefw1u08/matlab/rcwm_scr.m
 [3]: http://www.personal.soton.ac.uk/eefw1u08/matlab/read_csv_write_mat.m