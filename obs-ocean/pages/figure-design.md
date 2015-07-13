---
title: Figure design
author: Eleanor Frajka-Williams
layout: page
permalink: "/figure-design/"
header: no
---
An important part of doing scientific research is graphically displaying data and results. While creating scientific figures is usually considered a form of communication, it is also an integral part of doing the research.

I use the Generic Mapping Toolbox to create scientific figures. While it has a steeper learning curve than some methods of generating figures, it is tailored to geographically referenced images (maps) and allows a lot of control over individual figure elements. Because it is only a tool for creating figures, I do my analysis separately (in Matlab) and then export data to be used for the figures.

## GMT

To find out more about GMT, see [Figures with GMT][1] which has several sub-pages:

  * [Gallery of GMT figures][2] for oceanographic applications
  * [Installation instructions][3] for GMT on a Mac
  * [Matlab-to-GMT functions to export data][4]. This is a small collection of m-files to create GMT-readable ASCII files. If you&#8217;re a Matlab-user, you&#8217;ll probably want to export your Matlab data into a format that is readable by GMT. *Note, GMT can read <font face="courier">netcdf</font> files, and can handily access subsets of data within a full <font face="courier">netcdf</font> file.* However, I&#8217;ve found that when processing data in Matlab, it&#8217;s simplest to export data into ASCII format (though not necessarily quickest nor most compact/compressed).
  * [Matlab-to-GMT translation table][5]: Rough equivalents between Matlab plotting functions and GMT commands
  * [Flexible GMT workflow][6]&#8211; Once you&#8217;ve installed GMT, and looked through the tutorial on the GMT website (see link at bottom of this page), you may want to have a look at the way I use GMT. Note: this is a somewhat more involved setup, and not necessary in order to use GMT.

## Generic Figure design ideas

For a more generic discussion of Figure design, I highly recommend Sally Warner&#8217;s blog, [figuredesign.blogspot.co.uk][7].

There are also some great blog entries on data visualization from Nature in [Data Visualization &#8211; Points of View][8].

For resources to pick colour schemes for figures, check out [Color for data visualization][9]

*&#8211;updated May 2015&#8211;*

 [1]: /figures-in-gmt-generic-mapping-toolbox/
 [2]: /figure-design/gmt-figure-examples/
 [3]: /figure-design/installing-gmt-on-a-mac/
 [4]: /figure-design/matlab-to-gmt-functions-to-export-data/
 [5]: /figure-design/matlab-to-gmt-translation-table/
 [6]: /figure-design/flexible-gmt-workflow/
 [7]: http://figuredesign.blogspot.co.uk
 [8]: http://blogs.nature.com/methagora/2013/07/data-visualization-points-of-view.html
 [9]: /color-for-data-visualization/