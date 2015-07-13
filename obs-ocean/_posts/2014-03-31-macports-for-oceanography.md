---
title: MacPorts for oceanography
author: Eleanor Frajka-Williams
layout: post
header: no
permalink: /macports-for-oceanography/
category_sticky_post:
  - 0
categories:
  - Analysis
tags:
  - Installing
  - Mac
---
I&#8217;m finding that I refer to Macports several times across this webpage ([here][1], [here][2] and [here][3]). So it seems that if you&#8217;re an oceanographer and you use a Mac, you may want Macports. Starting from scratch, this is a lengthy (2+ hour) process, but most of the time is waiting for downloads, so it can all run in the background.

The nice thing about a package manager like Macports is that when you install a free bit of software, it&#8217;ll automatically check for any other packages that the software needs but you don&#8217;t have (dependencies). These are then downloaded and installed as well.

<a id="macports"></a>  


### Installing Macports

  1. **Xcode:** Before installing Macports, you must first install Xcode. If you already have Xcode, skip to step 2. 
      1. Download the package. (Be warned, Xcode is a LARGE package, and if you don&#8217;t already have it, it may take a while to download and install, ~1 hour). At time of writing, the latest version is 4.3*. 
      2. Install the command line tools. Note from the Macports instruction website: <http://guide.macports.org/chunked/installing.xcode.html>, you need to do one more thing after installing Xcode:  
        > After installing Xcode 4.3, the Command Line Tools must be installed. This is done from the Downloads section of Xcode&#8217;s preferences.
        
        To do this, for 10.8 and Xcode, then select `File>Preferences` and then in the window that opens, click the tab, `Downloads`. Select the button to install the command line tools. </li> 
        
        [<img src="http://i0.wp.com/observationaloceanography.com/wp-content/uploads/2013/07/Screen-Shot-2013-07-07-at-13.17.17.png?w=864" alt="Xcode preferences"  class="alignnone size-full wp-image-1111" data-recalc-dims="1" />][4]
        
          * For Mavericks (OSX 10.9), use the command line: `xcode-select --install` to install the command line tools for Xcode</ol> </li> 
        
          * If you already have Xcode, update it to the latest version before installing Macports.</li> 
        
          * **Macports:** Once Xcode is installed, command line tools installed, you can continue with your Macports installation, following the instructions [here][5]. For straightforward usage, I suggest using disk image `MacPorts-x.x.x.dmg`. In order to pick the right disk image, you need to know what operating system your Mac is running. 
              1. In order to pick the right disk image, you need to know what operating system your Mac is running. Determine your operating system (is it 10.4, 10.5, 10.6&#8230;?). Select the `Apple` in the upper left corner of your screen and choose `About this Mac`. Just beneath &#8220;OS X&#8221; you should see the version of your operating system.<figure id="attachment_1105" style="width: 245px;" class="wp-caption alignnone">
            [<img src="http://i1.wp.com/69.195.124.112/~frajkawi/_sites/wp-content/uploads/2013/07/Screen-Shot-2013-07-07-at-13.24.20-245x300.png?resize=245%2C300" alt="Figure caption.  Determining what version of OS X your computer is running." class="size-medium wp-image-1105" data-recalc-dims="1" />][6]<figcaption class="wp-caption-text">Figure caption. Determining what version of OS X your computer is running.</figcaption></figure> 
            
              2. From the MacPorts list of packages, select the lastest version for your OS. Download it, and then find it on your computer, double click the `*.pkg` file, and follow the installation menu.</ol> 
        
        ### Some useful ports
        
        If it&#8217;s been a while since you first installed Macports, you may want to update it before adding new ports.  
        `$ sudo port selfupdate`
        
        Note that each of the packages below may take **10-20 minutes to install**. These will be running in a terminal window.
        
        *If you need to find a terminal window, you can navigate to it from the finder to **Applications/Utilities**. In your Launchpad, this may or may not appear in a **Utilities** menu.*<figure id="attachment_1236" style="width: 300px;" class="wp-caption alignnone">
        
        [<img src="http://i0.wp.com/69.195.124.112/~frajkawi/_sites/wp-content/uploads/2013/07/Screen-Shot-2013-07-08-at-17.04.42-300x199.png?resize=300%2C199" alt="Find the terminal window on a Mac in the Applications folder>Utilities, or search in the Finder." class="size-medium wp-image-1236" data-recalc-dims="1" />][7]<figcaption class="wp-caption-text">Find the terminal window on a Mac in the Applications folder>Utilities, or search in the Finder.</figcaption></figure> 
        
          1. **GMT5** for figures. 
              1. Install GMT5 using Macports in a terminal window with the command:  
                `$ sudo port install gmt5`  
                where the the `sudo` activates the super-user privileges (i.e. you must be an administrator on the computer you&#8217;d like to install on), `port` invokes Macports, the port command is `install` and the name of the port you&#8217;d like to install is the `gmt5`. 
              2. After installing GMT5, check the later steps (i.e. updating your path and verifying installation) [here][3].
          2. For downloading ocean color data: port **wget** 
              1. Install wget using  
                `$ sudo port install wget`
              2. See how to use it in downloading ocean color data [here][1].
          3. For Neutral density code: ports **gfortran** and **netcdf with fortran support** 
              1. Install gfortran using  
                `$ sudo port install gcc45 +gfortran`  
                *(Old version: `$ sudo port install gfortran`, but as of Jul 2013, the `gfortran` package no longer appears in Macports.)* 
              2. Install netcdf using  
                `$ sudo port install netcdf`  
                `$ sudo port install netcdf-fortran`  
                *(Note: the old version of this was to do a `$ sudo port install netcdf +gcc45`, where the second argument on the netcdf install adds fortran compatibility. As of Jul 2013, in trying a `$ port cat netcdf` to look at the variants of netcdf available, there is a note that explains &#8220;As of version 4.2 c++ and fortran interfaces are separate ports, netcdf-cxx and netcdf-fortran, respectively.&#8221;)*</p> 
                Together, installing fortran/netcdf may take a while (~10-15 minutes). It may look like it’s not doing anything, but it is. </li> 
                
                  * Check that you now have gfortran. It is probably in the directory /opt/local/bin and called gfortran-mp-4.5. Check that you have the right netcdf library. You should find the file libnetcdff.a (note the second f, indicating fortran) in the directory /opt/local/lib/.
                  * Check the follow-on instructions for Neutral density installation [here][8]. </ol> 
                
                  * <a id="python"></a>For python: ports **scipy** and **numpy** 
                      1. To install the **scipy** stack for Python 2.7 with Macports execute this command in a terminal:  
                        `$ sudo port install py27-numpy py27-scipy py27-matplotlib py27-ipython +notebook py27-pandas py27-sympy py27-nose`  
                        See also <http://www.scipy.org/install.html> or <http://jakevdp.github.io/blog/2013/02/02/setting-up-a-mac-for-python-development/>. 
                      2. To install a python interpreter,  
                        `sudo port install py27-ipython`  
                        and then set this as the default  
                        `sudo port select --set ipython ipython27` </li> </ol> 
                      1. Once you start using MacPorts, you will periodically want to update your ports (at least before installing new ones). 
                          1. `sudo port selfupdate`
                          2. `sudo port upgrade outdated`
                    
                    *&#8211;updated Jul 2013&#8211;*

 [1]: http://frajka-williams.com/resources/data-sources/sea-surface-color-modis-aqua-to-matla/
 [2]: http://frajka-williams.com/resources/neutral-density/
 [3]: http://frajka-williams.com/resources/installing-gmt5-on-a-mac/
 [4]: http://i0.wp.com/observationaloceanography.com/wp-content/uploads/2013/07/Screen-Shot-2013-07-07-at-13.17.17.png
 [5]: http://guide.macports.org/chunked/installing.macports.html
 [6]: http://i2.wp.com/69.195.124.112/~frajkawi/_sites/wp-content/uploads/2013/07/Screen-Shot-2013-07-07-at-13.24.20.png
 [7]: http://i2.wp.com/observationaloceanography.com/wp-content/uploads/2013/07/Screen-Shot-2013-07-08-at-17.04.42.png
 [8]: http://frajka-williams.com/resources/neutral-density/#codeinstall