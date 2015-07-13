---
title: Matlab-to-GMT functions to export data
author: Eleanor Frajka-Williams
layout: page
category_sticky_post:
  - 0
header: no
permalink: '/figure-design/matlab-to-gmt-functions-to-export-data/'
---
This is a brief collection of functions I wrote for my own use to export Matlab time series and maps into ASCII format for GMT. Note, ASCII is very fluffy (i.e. data are not compressed in anyway) and so if you&#8217;re working with very large datasets (rather than an 8-year time series of 12-hourly data, which is not particularly large), you may want to explore other methods for saving/exporting data in <font face="courier">netcdf</font> format for use with your GMT scripts.

  1. [create_xy.m:][1] To create a two-column ASCII file with, for instance, a ship track in latitude and longitude.
  2. [create_THz.m:][2] To create a time series where the time is formatted for GMT. While Matlab uses the number <font face="courier">730505.5</font> to represent Jan 20, 2000 at 12 noon, GMT expects this to be represented as <font face="courier">2000-01-20T12:00:00</font>. So this function is similar to <font face="courier">create_xy.m</font>, but the first column is interpreted as representing time in Matlab time format, and is output into the ASCII file in GMT time format.
  3. [create_xyz.m:][3] To create a map in ASCII format, where the first column is the x-position, the second column the y-position, and the third column the value at the location (x,y).
  4. [create_xyAr.m:][4] To create a map of vectors (i.e. arrows), to be used with GMT function <font face="courier">psxy -Sv</font> similar to Matlab <font face="courier">quiver</font>. Here the <font face="courier">A</font> represents *Angle* and the <font face="courier">r</font> is *radius*. These have to do with how GMT plots arrows, as the angle (in degrees) clockwise from the x-axis (due east or the vector pointing to the right), with a length given by a radius <font face="courier">r</font>
  5. [create_THxz.m:][5] To create data where one axis is time (TH), the second axis is given by x, and the value at the time TH and position x is given by z. This is useful for hovmueller diagrams.

Am I missing any that you&#8217;d like to see added? Send me a message.

*&#8211;updated Jul 2013&#8211;*

 [1]: https://www.dropbox.com/s/tmpmi04pnx0w636/create_xy.m?dl=0 "create_xy.m"
 [2]: https://www.dropbox.com/s/b98d7h9opwla5bj/create_THz.m?dl=0 "create_THz.m"
 [3]: https://www.dropbox.com/s/6ttjy97rfrt34vq/create_xyz.m?dl=0 "create_xyz.m"
 [4]: https://www.dropbox.com/s/6ttjy97rfrt34vq/create_xyz.m?dl=0 "create_xyAr.m"
 [5]: https://www.dropbox.com/s/093pgbx4qx7nwe6/create_THxz.m?dl=0 "create_THxz.m"