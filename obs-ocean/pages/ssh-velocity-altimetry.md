---
title: 'SSH &amp; velocity &#8211; Altimetry'
author: Eleanor Frajka-Williams
layout: page
header: no
---
<figure id="attachment_1138" style="width: 300px;" class="wp-caption alignright">[<img src="http://i2.wp.com/69.195.124.112/~frajkawi/_sites/wp-content/uploads/2012/08/aviso_ssh1-300x264.png?resize=300%2C264" alt="Figure caption. AVISO sea surface height, from 2000 to 2009." class="size-medium wp-image-1138" data-recalc-dims="1" />][1]<figcaption class="wp-caption-text">Figure caption. AVISO sea surface height, from 2000 to 2009.</figcaption></figure>URL: [AVISO global products][2] on a 1/3 x 1/3 deg grid.

Note: you will need to register with AVISO in order to get a username/password to access the data. This is free for research users, but can take some time **(as I recall, about 1 week).** Register here: <http://www.aviso.oceanobs.com/en/data/registration-form.html>.

### Downloading the data using extraction

  1. **For geographic and temporal extraction** go to [geographic and temporal extraction][3] page. Scrolling down the page, choose your poison. These use the same codes as above, DT/NRT and MADT/MSLA. Make sure you&#8217;re global unless there&#8217;s a specific region you fall into that they focus on (like mediterranean).
  2. **Click your choice**
  3. **Choose &#8220;Downloading and extraction service&#8221;** to follow the rest of these instructions. If you&#8217;re familiar with OpenDAP that might be a better option for you.
  4. **Fill out the form** keeping &#8220;netcdf&#8221; as the format, filling in the appropriate lat/lon limits, and the time range of your choice. Check both the Grid\_0002 and Grid\_0001 boxes.
  5. **Click &#8220;Download&#8221;**
  6. **Save the file**, which includes little tags to indicate what data you chose

### Downloaded global files

For this, you still need an account with AVISO: [Register here][4]. This is not an automatic process, so be prepared to wait a week or two for your account details.

  1. **On your computer** start in the directory where you want the data to live.
  2. **FTP to the aviso site** using  
    `<br />
$ ftp -i ftp.aviso.oceanobs.com`  
    Then log in using the username and password provided to you by AVISO. 
  3. **Navigate to the directory with your data**.
  4. **mget the files** using  
    `ftp> mget *` 

### Load the data into Matlab

  1. Matlab can now read netcdf files. If you don&#8217;t have netcdf on your version of Matlab, then you can download the [snctools and mexnc packages][5], then use these commands:  
    `<br />
nc_dump(filename);<br />
nc_getvarnames(filename);</p>
<p>U = nc_varget(filename,'Grid_0001');<br />
V = nc_varget(filename,'Grid_0002');<br />
Lat = nc_varget(filename,'NbLatitudes');<br />
Lon = nc_varget(filename,'NbLongitudes');<br />
time = nc_varget(filename,'time');<br />
`

 [1]: http://i0.wp.com/69.195.124.112/~frajkawi/_sites/wp-content/uploads/2012/08/aviso_ssh1.png
 [2]: http://www.aviso.oceanobs.com/en/data/products/sea-surface-height-products/global/index.html
 [3]: http://atoll-motu.aviso.oceanobs.com/?action=listcatalog&service=AvisoDT
 [4]: http://www.aviso.oceanobs.com/en/data/registration-form.html
 [5]: http://mexcdf.sourceforge.net/