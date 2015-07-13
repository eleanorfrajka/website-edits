---
title: Figure design in GMT (Generic Mapping Toolbox)
author: Eleanor Frajka-Williams
layout: page
category_sticky_post:
  - 45
header: no
---
or, the weird and wonderful world of [GMT5 (Generic Mapping Toolbox v5)][1]. The collection of pages here is about the technical aspects of creating nice figures. If you don&#8217;t want to use GMT, however, you might want to check out [figuredesign.blogspot.co.uk][2], a blog started by Sally Warner on making good figures in Matlab.

GMT is a collection of tools for producing crisp and beautiful scientific figures. The tools are accessed at the command line (in a terminal window on a Mac) and can be collected into shell-scripts. GMT is not my top choice tool for data analysis. The software is free to use and very flexible, but with that flexibility and control comes a lot of opportunities for programming errors. It is particularly powerful for mapping (hence it&#8217;s relatively widespread use in Earth and Ocean Sciences), but can handle all manner of scientific figures.

  * Browse a few sample images to see if they&#8217;re something you&#8217;d like to be able to make. One example embedded here (click the image for fullsize), or see a few more examples of [oceanographic GMT figures (redirects to another page)][3].  
    [<img align="center" src="http://i1.wp.com/69.195.124.112/~frajkawi/_sites/wp-content/uploads/2013/05/fig1_mapts2.png" data-recalc-dims="1" />][4]</p> 
    * * *
    
    ## What can GMT do that Matlab can&#8217;t?
    
      * Is it worth learning to use GMT when I can make figures in Matlab?  
        *GMT is a flexible plotting tool which comes with a wide range of projections, good control over axis elements (tick length, width, frame line width, which frame edges to plot) and some very nice contouring tools. However, while GMT is powerful, it can be cumbersome to learn. If you&#8217;re satisfied with how Matlab makes figures, or you post-process figures in Adobe Illustrator or GIMP, then maybe you don&#8217;t need GMT.*
      * Self-quiz: ask yourself the following questions. If you answer yes to several, you may find it worthwhile to learn GMT:
      1. Need two different y-axes and don&#8217;t like what <font face="courier">plotyy</font> gives you?
      2. Want double x-axes (like time and distance for a section)?
      3. Want more than one colormap in the same figure or even the same panel?
      4. Need a few more choices of map projections to show your data to best advantage? (polar, equal-area, other more esoteric)?
      5. Want lines and fonts to be crisp and clear?
      6. Want to use Greek or other symbols in your figure labels and annotations without strange typesetting artefacts?
      7. Need five or more easily distinguishable grayscale lines for a black and white figure?
      8. Want more control over contour plots (some smoothing/skipping contours with fewer than x-points/specifying the position and orientation of contour labels)?</li> 
    
    * * *
    
    ### Quicklist of local pages for more about GMT:
    
      * [Gallery of GMT figures][5] for oceanographic applications
      * [Installation instructions][6] for GMT on a Mac
      * [Matlab-to-GMT functions to export data][7]. This is a small collection of m-files to create GMT-readable ASCII files. If you&#8217;re a Matlab-user, you&#8217;ll probably want to export your Matlab data into a format that is readable by GMT. *Note, GMT can read <font face="courier">netcdf</font> files, and can handily access subsets of data within a full <font face="courier">netcdf</font> file.* However, I&#8217;ve found that when processing data in Matlab, it&#8217;s simplest to export data into ASCII format (though not necessarily quickest nor most compact/compressed).
      * [Matlab-to-GMT translation table][8]: Rough equivalents between Matlab plotting functions and GMT commands
      * [Flexible GMT workflow][9]&#8211; Once you&#8217;ve installed GMT, and looked through the tutorial on the GMT website (see link at bottom of this page), you may want to have a look at the way I use GMT. Note: this is a somewhat more involved setup, and not necessary in order to use GMT.
    * * *
    
    ## How to learn GMT?
    
    Fortunately, the good folks who created GMT have put together a handy tutorial. It is not thrilling, but it is a good, solid introduction. After [installing GMT][10], get the tutorial document, linked here as a pdf file: [GMT_tutorial.pdf (redirects to new page)][11].
    
    *&#8211;updated May 2015&#8211;*

 [1]: http://www.soest.hawaii.edu/gmt5/ "GMT5 (Generic Mapping Toolbox v5)"
 [2]: http://figuredesign.blogspot.co.uk
 [3]: http://observationaloceanography.com/gmt-figure-examples/ "GMT Figure examples"
 [4]: http://i1.wp.com/69.195.124.112/~frajkawi/_sites/wp-content/uploads/2013/05/fig1_mapts2.png
 [5]: http://observationaloceanography.com/figure-design/gmt-figure-examples/
 [6]: http://observationaloceanography.com/figure-design/installing-gmt-on-a-mac/
 [7]: http://observationaloceanography.com/figure-design/matlab-to-gmt-functions-to-export-data/
 [8]: http://observationaloceanography.com/figure-design/matlab-to-gmt-translation-table/
 [9]: http://observationaloceanography.com/figure-design/flexible-gmt-workflow/
 [10]: http://frajka-williams.com/resources/installing-gmt5-on-a-mac/
 [11]: http://www.soest.hawaii.edu/gmt5/gmt/pdf/GMT_Tutorial.pdf