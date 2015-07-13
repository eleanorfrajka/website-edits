---
title: 'Bathymetry &#8211; ETOPO1'
author: Eleanor Frajka-Williams
layout: page
header: no
---
How to download, parse into Matlab, and plot bathymetry of the world&#8217;s oceans.

URL: <http://www.ngdc.noaa.gov/mgg/global/global.html>

### Download the data

  * If you want the global dataset (382 MB zipped) then grab it from the link above. For a custom grid, there&#8217;s a new option <http://maps.ngdc.noaa.gov/viewers/wcs-client/> which is quite handy, and you can download to XYZ, NetCDF and GMT NetCDF among others.

To use the Matlab scripts, choose XYZ then skip below.

### Previous instructions

  1. My old instructions were for the NGDC grid translator. For these, use the following website: <http://www.ngdc.noaa.gov/mgg/gdas/gd_designagrid.html>
  2. Create a grid id (I used &#8220;faroeice&#8221;)  
    grid database: ETOPO1 is the latest version  
    grid area: (55,70)N (-30,0)E == 30W to 0E  
    grid cell size: 2-minutes (note, for large geographic regions, might prefer 4 or 10-minute grid size)  
    grid format: Choose:  
    &#8220;XYZ (lon, lat, depth)&#8221;, &#8220;No Header&#8221;, &#8220;Comma&#8221; and check &#8220;Omit Empty&#8221;SUBMIT
  3. Retrieve Individual files  
    Find: faroeice_####.xyz</p> 
    Right click and save to a dedicated directory. (I used ./data/etopo2/)</li> </ol> 
    
    ### Read into Matlab
    
      1. Use Matlab [read\_xyz\_scr.m][1] which calls [read_xyz.m][2]Update the following variables in the code:  
        *input_dir* (/home/eleanor/data/etopo2/)  
        *filename* (faroeice_####.xyz)  
        *lat_lim* e.g. [56 67]  
        *lon_lim* e.g. [-20 0]</p> 
        NOTE: WOA and WOD plotting scripts use bathymetry. </li> 
        
          * After reading in the data, use a  
            `>save FaroesBathy bathy`  
            where bathy.lat, bathy.lon and bathy.depth are read by [read_bathy.m][3]
          * If you&#8217;d like to create a plot of the bathymetry, you can use [read_bathy.m][3] but set *PLOTflag=1*</li> </ol> 
            
            #### PLOT USING GMT
            
            Use the script [faroesbathy.csh][4] with [.gmtdefaults4][5] (optional).
            
            ### Other
            
            Need something higher resolution? LDEO at Columbia has swath data online. I haven&#8217;t accessed it yet, but the website is here: <http://www.geomapapp.org/>.
            
            *&#8211;last updated July 2013&#8211;*

 [1]: http://www.personal.soton.ac.uk/eefw1u08/matlab/read_xyz_scr.m
 [2]: http://www.personal.soton.ac.uk/eefw1u08/matlab/read_xyz.m
 [3]: http://www.personal.soton.ac.uk/eefw1u08/matlab/read_bathy.m
 [4]: http://www.personal.soton.ac.uk/eefw1u08/GMT/faroesbathy.csh
 [5]: http://www.personal.soton.ac.uk/eefw1u08/GMT/.gmtdefaults4