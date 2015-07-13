---
title: Matlab to GMT translation table
author: Eleanor Frajka-Williams
layout: page
header: no
permalink: '/figure-design/matlab-to-gmt-translation-table/'
---
When you&#8217;re just getting started, it can be hard to know what you&#8217;re looking for (without reading the full technical reference manual: <a http://www.soest.hawaii.edu/gmt5/gmt/pdf/GMT\_Docs.pdf">GMT\_Docs.pdf</a>. For basic conversions between Matlab plotting commands and those in GMT, see the table below. Note, you will probably need the man file for each command before you get it to run properly. See the html man pages here: [gmt.man.html][1] or you can always type a command at the command line with no options, and it will print the man file to the screen.

<table border="1">
  <tr>
    <td>
      <b>Matlab</b>
    </td>
    
    <td>
      <b>GMT stem</b>
    </td>
  </tr>
  
  <tr>
    <td>
      colorbar
    </td>
    
    <td>
      psscale
    </td>
  </tr>
  
  <tr>
    <td>
      contour(X,Y,Z)
    </td>
    
    <td>
      grdcontour datafile.nc
    </td>
  </tr>
  
  <tr>
    <td>
      contourf(X,Y,Z)
    </td>
    
    <td>
      pscontour -I datafile.xyz
    </td>
  </tr>
  
  <tr>
    <td>
      pcolor(X,Y,Z)
    </td>
    
    <td>
      grdimage data.nc
    </td>
  </tr>
  
  <tr>
    <td>
      plot(X,Y,&#8217;k&#8217;)
    </td>
    
    <td>
      psxy -Wblack data.xy
    </td>
  </tr>
  
  <tr>
    <td>
      quiver(X,Y,U,V)
    </td>
    
    <td>
      psxy -Sv data.xyAr
    </td>
  </tr>
  
  <tr>
    <td>
      plot(X,Y,&#8217;rx&#8217;)
    </td>
    
    <td>
      psxy -Wred -Sx.4i data.xy
    </td>
  </tr>
  
  <tr>
    <td>
      text(X,Y,&#8217;Hello world&#8217;)
    </td>
    
    <td>
      pstext
    </td>
  </tr>
</table>

A few handy functions without Matlab equivalent:

  * pswiggle: to plot anomalies along a track, e.g. altimeter signals along the track, or waterfall plots of temperature and salinity profiles
  * makecpt: to make a colormap
  * ps2raster: convert your \*.ps file into another file format (e.g. \*.png)
  * pscoast: Plots coastlines with options to shade the land or outline the coasts, and/or add rivers. Probably has an m_map equivalent.

See the full list of GMT functions on the html man pages: <http://www.soest.hawaii.edu/gmt5/gmt/html/gmt_man.html>.

*&#8211;updated Jun 2013&#8211;</li>

 [1]: http://www.soest.hawaii.edu/gmt5/gmt/html/gmt_man.html