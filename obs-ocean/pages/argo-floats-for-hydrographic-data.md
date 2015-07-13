---
title: Argo profile data
author: Eleanor Frajka-Williams
layout: page
header: no
---
[<img src="http://i2.wp.com/observationaloceanography.com/wp-content/uploads/2014/03/argo_labsea-255x300.png?fit=255%2C300" alt="argo_labsea" class="alignright size-medium wp-image-2587" data-recalc-dims="1" />][1]Basic instructions to download and parse Argo hydrographic profiles into Matlab, *by ocean basin*. The Argo community provides several ways to access and download individual profile data. I have used the method by individual float number/call sign, where I identified the call signs I was interested in first (using the index files) and then downloaded all profiles from those call signs. However, in working with larger datasets, I find that I&#8217;d like to download an entire ocean basin. The instructions here will be for downloading an entire ocean basin.

### Steps

  * **Identify the ocean basin file** &#8211; Argo defines three main ocean basins: Atlantic, Pacific and Indian. The instructions (and code) provided will be for the Atlantic. 
      * If this is your first time downloading the data, you can download the whole thing at once. At the time of writing (May 2015), the Atlantic basin download was about 750 MB, as a tarred, gzipped file. If you want everything, you can find it here:  
        <ftp://ftp.ifremer.fr/ifremer/argo/etc/argo-zip/geo/>.  
          
        Choose the basin you want and download it to your computer (e.g., right click, save target as).
      * If you&#8217;re updating your files, you may be able to download individual months at a time.
  * **Unzip the file** &#8211; While the compressed file was less than a gigabyte, unzipped and untarred, this file is a whopping 31 GB. If you don&#8217;t have the space to work with a file of this size, you may need a different method to access the data  
      
    On a Mac, from the command line, you can use the command:  
    `% tar -xvf atlantic_ocean.tar.gz`  
      
    On my computer, untarring this file took longer than downloading it.
  * **Load some data into Matlab** &#8211; I&#8217;ve provided two files to load these data into Matlab, [load\_argo\_1month.m][2] (which will load any one month of Argo basin data) and [load\_argo\_select.m][3] (which loads all Argo profiles in a given geographic region and time range). </li> 

  
  


* * *

  
  
</p> 

## The following is the old version

**Proceed with caution**

Basic instructions to download and parse Argo hydrographic profiles into Matlab. There are two main steps: find the float numbers you want using the index files, then download the profile data for each float. I&#8217;ve included Matlab scripts to help access the data.

### Download the index files

Start at [http://www.nodc.noaa.gov/argo/accessDaa.htm][4].

For geographically selected data (single basin) and limited time:

  1. From URL click III. Argo Basins Data
  2. For each year and month of interest, right click the INDEX file and save to a data directory, eg. `../data/labsea/argo/AtlanticIndex`
  3. Unzip files by cd&#8217;ing into that dir and calling  
    `$ unzip *`

### Read the index file into Matlab

  1. Convert text index files to mat data with [read\_argotxt\_write_mat.m][5] (function), [rawm\_all\_scr.m][6] (script). These will load and parse individiual index files into data structures and variables.
  2. Determine floats needed using [select\_float\_data_all.m][7] (script) which uses the index files you&#8217;ve extracted. This saves a Matlab file of `callSigns` and other pertinent data for the region and time period you select. 
  3. Give the output file an appropriate name. This will be loaded in the `argoprof_example_scr.m` in the next step.

### Download the float profiles

  1. From URL click IV. Argo Floats Data
  2. For each float number needed (as determined above), right click the data file (float number) and choose &#8220;Save as..&#8221; to a data directory, eg. `../data/labsea/argo/FloatData`

### Read the netcdf files into Matlab

  1. For the profiles you&#8217;ve identified in the previous step, download the profile data then convert these netCDF format datafiles to `*.mat` using [read\_nc\_write_mat.m][8] (function) and [argoprof\_example\_scr.m][9] (script).

Also calls: [findbetw.m][10].

*&#8211;updated May 2015&#8211;*

 [1]: http://i1.wp.com/observationaloceanography.com/wp-content/uploads/2014/03/argo_labsea.png
 [2]: http://observationaloceanography.com/in-situ-data/argo-floats-for-hydrographic-data/load_argo_1month-m/
 [3]: http://observationaloceanography.com/in-situ-data/argo-floats-for-hydrographic-data/load_argo_select-m/
 [4]: http://www.nodc.noaa.gov/argo/accessData.htm
 [5]: http://observationaloceanography.com/in-situ-data/argo-floats-for-hydrographic-data/read_argotxt_write_mat-m/
 [6]: http://observationaloceanography.com/in-situ-data/argo-floats-for-hydrographic-data/rawm_all_scr-m/
 [7]: http://observationaloceanography.com/in-situ-data/argo-floats-for-hydrographic-data/select_float_data_all-m/
 [8]: http://observationaloceanography.com/in-situ-data/argo-floats-for-hydrographic-data/read_nc_write_mat-m/
 [9]: http://observationaloceanography.com/in-situ-data/argo-floats-for-hydrographic-data/argoprof_example_scr-m/
 [10]: http://observationaloceanography.com/data-analysis-2/code-snippets/findbetw-m/