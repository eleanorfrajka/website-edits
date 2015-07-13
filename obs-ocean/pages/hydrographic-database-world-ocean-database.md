---
title: 'Hydrographic database &#8211; WOD'
author: Eleanor Frajka-Williams
layout: page
header: no
---
This is a giant database of hydrographic profiles, spanning the past 100+ years. How to download and parse into matlab.

URL: <http://www.nodc.noaa.gov/OC5/SELECT/dbsearch/dbsearch.html>

### Download the data in comma-delimited format

  1. From URL, choose &#8220;WOD select&#8221;
  2. Search criteria to use: Geographic coordinates, measured variables, dataset, (data exclusion &#8211; I haven&#8217;t done anything with this yet). Click &#8220;Build a query&#8221;.
  3. For Faroe&#8217;s, used 58 to 65 N, -20 to 0 E  
    For the Labrador Sea, I used 51 to 68 N, -67 to -43 E. Dataset: OSD, CTD, XBT, MBT, PFL, DRB  
    Variables: Check at least temp and salin in &#8220;1&#8221; column. Click &#8220;Get an inventory&#8221;.
  4. For Faroes: [58,65]N, [-20,0]E there were 56k OSD, 4k CTD, 17k XBT, 29k MBT, 1k PFL > 107k casts  
    For Lab Sea there were 19k OSD, 7k CTD, 6k XBT, 38k MBT, 8k PFL > 79k casts. Click &#8220;Download Data&#8221;.
  5. Choose &#8220;Comma delimited&#8221;, leave the rest the same. 
      * Enter e-mail address.
      * When e-mail arrives, download all files to a dedicated directory.

### Clean the data files using Matlab

  1. Clean data files. Tedious! You can do this by hand, which may be quicker, by opening each file and searching for the string `'---.---'` which is what they use for no data, and replacing it with a blank. If you use emacs, the query-replace command is  
    `esc-x %`  
    and when the first instance is found, use a bang &#8220;`!`&#8221; to replace all. Otherwise, you can use the script [clean_files.m][1] which is slow, but you don&#8217;t have to do anything.
  2. Parse the `*.csv` files into `*.mat` data files. Use [rowm\_all\_scr.m][2] which calls [read\_ocldb\_write_mat.m][3], [clean_files.m][1], [remove_str.m][4]. Update rowm\_all\_scr.m, saving your values for 
      * *input_dir* (wherever you put the `*.csv` files) 
      * *filename1* (the root of the file names, everything before the instrument name, &#8220;CTD&#8221; or &#8220;OSD&#8221;) 
      * *rep* (the number of files for each instrument. If CTD files run through CTD56, then `rep` should be 56 for the CTDs. 
      * *output_dir*(where you want to save your `*.mat` files). This script will create a `*.mat` file for each `*.csv` file with one variable, `cast1` which is a structure. The fields of the structure include: 
      * *inst-* instrument type: a 3 character string 
      * *number-* cast number from the file 
      * *lat,lon-* latitude and longitude of the cast 
      * *yy,mm,dd-* Year, month and date 
      * *salin-* empty if no salinity data 
      * *flag-* Value up to 3 if there&#8217;s a bad quality flag 
      * *index-* datanumber 
      * *depth-* depth vector of samples 
      * *temp-*temperature vector
    
    It will also create the huge structure `all_cast`which contains all the casts in it. You should probably save this to access it more easily. Next, make some cool plots of this huge amount of data!</li> </ol>

 [1]: http://www.personal.soton.ac.uk/eefw1u08/matlab/clean_files.m
 [2]: http://www.personal.soton.ac.uk/eefw1u08/matlab/rowm_all_scr.m
 [3]: http://www.personal.soton.ac.uk/eefw1u08/matlab/read_ocldb_write_mat.m
 [4]: http://www.personal.soton.ac.uk/eefw1u08/matlab/remove_str.m