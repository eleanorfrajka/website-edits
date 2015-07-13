---
title: Installing GMT on a Mac
author: Eleanor Frajka-Williams
layout: page
category_sticky_post:
  - 0
header: no
permalink: "/figure-design/installing-gmt-on-a-mac/"
---
*[Mar 2014] Note, this page may no longer be up-to-date. It looks like the latest version of GMT has a downloadable *.dmg file.*

The GMT website says that for a Mac (OS X operating system) that you can follow their instructions for Unix/Linux ([Instructions on GMT website][1]). As an after thought, they also say that it&#8217;s available with fink (a package manager). It appears as though gmt5 may not yet be available through fink. However, it is available via [Macports][2], another package manager. Since I couldn&#8217;t get the CSIRO neutral density code running using fink, I&#8217;ve now switched to Macports.

  1. See the instructions [here to install Macports][3], which also requires Xcode.
  2. **GMT5:** Once you have Macports and the command tools installed for Xcode, you can then install GMT5.0.0b (current version as of 31 May 2013). To install it, use the command:  
    `$ sudo port install gmt5`
  3. **Update path?** It&#8217;s not clear to me whether this is a step that Macports does for you automatically, but in my <font face="courier">.profile</font> file (in the home directory on my Mac), I found the following 3 lines:  
    > `# MacPorts Installer addition on 2012-09-14_at_11:04:29: adding an appropriate PATH variable for use with MacPorts.<br />
export PATH=/opt/local/bin:/opt/local/sbin:/opt/local/lib/gmt5/bin/:$PATH<br />
# Finished adapting your PATH environment variable for use with MacPorts.`
    
    In particular, the third addition to the `PATH` variable was <font face="courier">/opt/local/lib/gmt5/bin/</font>, which is where my gmt5 files are located. If GMT isn&#8217;t working for you, check that your <font face="courier">.profile</font> file has this directory in its search path.</li> 
    
      * After modifying `.profile`, you need to reload it with a `$ source .profile`
      * **Check that GMT is installed.** At the command line (i.e. in a Terminal window), from any directory, execute the command:  
        `$ gmt<br />
gmt - The Generic Mapping Tools, Version 5.0.0b [64-bit]<br />
Copyright 1991-2012 Paul Wessel, Walter H. F. Smith, R. Scharroo, and J. Luis</p>
<p>This program comes with NO WARRANTY, to the extent permitted by law.<br />
You may redistribute copies of this program under the terms of the<br />
GNU General Public License.<br />
For more information about these matters, see the file named LICENSE.TXT.<br />
For a brief description of GMT programs, type gmt --help<br />
`</ol> 
    
    And you&#8217;re ready to go!  
      
    *&#8211;updated Jul 2013&#8211;*

 [1]: http://www.soest.hawaii.edu/gmt5/gmt/gmt_download.html
 [2]: http://www.macports.org
 [3]: http://observationaloceanography.com/macports-for-oceanography/ "MacPorts for oceanography"