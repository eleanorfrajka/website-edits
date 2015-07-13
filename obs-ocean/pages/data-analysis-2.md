---
title: Data analysis
author: Eleanor Frajka-Williams
layout: page
header: no
---
There are a range of tools to analyze oceanographic data. Since datasets tend to be large, Microsoft Excel doesn&#8217;t cut it. 

I use Matlab for data analysis. Besides being a relatively easy-to-learn programming language, it is widely used in the oceanographic community which means that code packages have been written with ocean-specific tools. 

If you&#8217;re interested in learning Matlab, I have created a short self-paced Matlab tutorial. It was designed for undergraduates with some knowledge of oceanography and no prior programming experience, and consists of 4 practical exercises and a series of micro-lectures.

### Other resources

I use a Mac, with Matlab as my primary tool for data processing. A few other tools I&#8217;ve needed include the Neutral density code from CSIRO. Since it was difficult to get it running on my computer, I&#8217;ve compiled some notes below about installing it on a Mac. A lot of other tools (Python, Neutral Density, GMT) also install more easily with some sort of package manager, so there are instructions for using MacPorts for ocean-specific applications.

#### Neutral density

  * [Neutral density code][1]. Neutral density is a (relatively) new way to represent conservative density in the ocean. Installing the code to calculate it is somewhat tricky, and I&#8217;ve finally managed to compile the CSIRO neutral density code on my Mac. Since it was an extended process, I&#8217;ve documented how I&#8217;ve done it, in case it can be helpful to others. Many thanks to Sally Close and Steve Alderson for their help.

#### Macports

  * Macports isn&#8217;t really a tool for oceanography, but it&#8217;s an important step to installing either GMT5 or the CSIRO neutral density code on a Mac.  
    See the general instructions [here][2]. 

*&#8211;updated May 2015&#8211;*

 [1]: http://frajka-williams.com/resources/neutral-density/
 [2]: http://frajka-williams.com/resources/using-macports-for-oceanography/