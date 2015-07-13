---
title: Neutral Density code
author: Eleanor Frajka-Williams
layout: post
header: no
permalink: /neutral-density-code/
category_sticky_post:
  - 48
categories:
  - Analysis
  - Neutral density
tags:
  - downloads
  - Installing
  - Mac
---
*Compilation tips for CSIRO Neutral Density code (Fortran/Matlab) on Mac OSX*

Many thanks to Sally Close and Steve Alderson for their help in installing the code on my machine. I&#8217;m listing the steps we used which are provided without warranty or guarantee. Most particularly, they may or may not work for you, but hopefully can get you going in the right direction. (*Original installation was completed Feb 2011 on a Mac OS X version 10.6.6.*) New installation was completed July 2013 on a Mac OS X version 10.8.4, Matlab 2012a.

> If the code or instructions below are helpful to you, I&#8217;d love to hear it. Always nice to know whether it&#8217;s worthwhile to put these kinds of instructions online. (Send me an e-mail at the address above.) Even better, if you encounter and fix a relevant data-access issue that isn&#8217;t in the &#8220;troubleshooting&#8221; below, let me know so I can add it to the page.

The CSIRO neutral density code and package can be found here: [CSIRO Neutral Density home page][1].

The instructions below use `gfortran-mp-4.5` as the compiler and [Macports][2] for package managing. For separate instructions using `f77` and [fink][3] as the package manager, see this instruction sheet by Sally: [CSIRO\_neutral\_density][4]. Please note: you don&#8217;t want to switch between the fink and Macports instructions! The `gamma.a` library and matlab-interface should be compiled with the same fortran compiler, and if you have fink AND Macports, your computer may get confused about where to look for compilers and packages. So, if you already use fink, use the [CSIRO\_neutral\_density][4] instructions. If you don&#8217;t, or already use Macports, follow the instructions below.

  1. [Download the CSIRO package][5]
  2. [Installation of gfortran and netcdf libraries][6]
  3. [Compiling the gamma.a library][7]
  4. [Compiling the matlab-interface][8]
  5. [Running the example][9]

**If you still have problems, you may find the [Troubleshooting][10] tips are helpful, where other users with later versions of Mac OSX had to make alterations to the procedure in order for it to work.**

* * *

### <a name="codeinstall"></a>Install Xcode, Macports, fortran compilers and netcdf libraries

You need a Macports to install fortran and netcdf libraries. Follow the instructions [on this page][11] for installing Xcode, Macports, and then the **gfortran** and **netcdf** ports. If you&#8217;re just getting starting, this may take a couple hours waiting for large downloads.

### <a name="download"></a>Download the CSIRO package

  1. Download the Fortran/Matlab package from here: [gamma.tar.Z (from csiro webpage)][12]. Make sure you get the one to be compiled, rather than the code-compiled versions Windows or Linux.
  2. Move it to an appropriate location on your machine. Mine is in /Users/eleanor/matlab/. 
  3. You&#8217;ll need to unzip/tar it, using the command  
    `% tar -xvzf gamma.tar.Z`  
    This will create the directory `gamma/` in place of the `gamma.tar.Z` with files in there, as well as a sub-directory `matlab-interface/`.

<a name="gamma"></a>  


### Gamma

  1. In the base directory where you untarred gamma (in my case, `/Users/eleanor/gamma/`), start with the Mfile-lib-SG:  
    `cp Mfile-lib-SG Makefile_gamma`
  2. Edit Makefile_gamma: 
      1. Remove the first line `#!/usr/bin/pmake`
      2. Add the line  
        `FC = gfortran-mp-4.5`  
        to make sure you&#8217;re accessing the right fortran compiler.
      3. Edit the flags to read  
        `FFLAGS = -O -ffixed-line-length-none`
      4. On the gamma.a instruction line, delete MAKELIB command
      5. Under the `read-nc.o: read-nc.F` line, change the command to be  
        ``gfortran-mp-4.5 $(FFLAGS) -DPWD="'`pwd`'" -c read-nc.F``
    
    The `Makefile_gamma` I used looks like [this][13].</li> 
    
      * You can now compile the `gamma.a` library using the command: `make -f Makefile_gamma`. This is what it should look like: [output to screen from making gamma][14].</ol> 
    
    ### <a name="interface"></a>Compile the matlab-fortran interface
    
    Now, compile the matlab fortran routines. Note that `gamma.a` must be compiled first.
    
      1. Change to the matlab-interface directory:  
        `$ cd matlab-interface`
      2. Copy a makefile to customize for your machine:  
        `$ cp Mfile-SG Makefile_interface`
      3. Edit `Makefile_interface`: 
          1. When I ran it, I left the line as `FC=gfortran`, so apparently my machine knew to link `gfortran` with the actual `gfortran-mp-4.5`. Graeme found that he needed to replace that line with `FC=gfortran-mp-4.5`.
          2. Edit the line starting with `FFLAGS` to read  
            `FFLAGS = -O2 -ffixed-line-length-none`
          3. Edit the line starting with `LIBS` to read  
            `LIBS = ../gamma.a -L/opt/local/lib -lnetcdff`
          4. Edit the line starting with `all` to read  
            `all: glabel_matlab nsfces_matlab`
          5. Copy the two lines starting with `$(PROGRAM)` where the first one is specifically for `glabel_matlab` to be  
            `glabel_matlab: glabel_matlab.o`  
            `        $(FC) $(FFLAGS) $(LIBS) -o glabel_matlab glabel_matlab.o`  
            where you retain the tab that is currently preceding the `$(FC)`.
        `nsfces_matlab: nsfces_matlab.o`  
        `        $(FC) $(FFLAGS) $(LIBS) -o nsfces_matlab nsfces_matlab.o`</li> </ol> 
        
        The `Makefile_interface` I used looks like [this][15].</li> 
        
        *Note: there is a problem with the tabs in copying code from this page, so if you do copy it, be sure that you have a tab before the `$(FC)` on L16 and L19, as well as before the `rm` on L22.*
        
        This makefile assumes that your netcdf library was installed using Macports and is in the `/opt/local/lib/`directory.</li> 
        
          * Make the makefile:  
            `$ make -f Makefile_interface` where the -f is specifying which Makefile to use. (Otherwise it will look for a file called &#8220;Makefile&#8221; or &#8220;makefile&#8221;.) 
          * You should end up with two executables: `glabel_matlab` and `nsfces_matlab`, which will interface with the matlab scripts of the same name.</ol> 
        
        ### Update paths in Matlab functions
        
          1. Open `gamma_n.m` and `neutral_surfaces.m`. Modify the lines where the code calls the external binaries to include their full path. In my case, `/Users/eleanor/matlab/gamma/matlab_interface`.
          2. Add the location of the two m-files files to your path in Matlab. This isn&#8217;t strictly necessary (as an alternative, you could execute the code with Matlab sitting in the `/Users/eleanor/matlab/gamma/matlab_interface` folder). But by setting it up in your Matlab path, you are telling Matlab where to search for files. This can be done by creating a `startup.m` file in the directory from which you call Matlab. To add the path, the startup file should include the line `path('/Users/eleanor/matlab/gamma/matlab_interface/',path)`.
          3. Start Matlab in your usual directory OR in the directory `matlab-interface/`. Run the script `example.m`. 
              1. You may get the error:  
                `>> example<br />
Error using load<br />
Unable to read file glabel_matlab.out: No such file or directory.</p>
<p>Error in gamma_n (line 93)<br />
load glabel_matlab.out;</p>
<p>Error in example (line 3)<br />
[g,dgl,dgh] = gamma_n(s,t,p,long,lat);`</p> 
                This error means that &#8216;.&#8217; is not in your bash (or other shell) path. You can fix this by editing the line  
                `command = ['!glabel_matlab >& /dev/null'];`  
                in `gamma_n.m` to read  
                `command = ['!./glabel_matlab >& /dev/null'];`  
                Repeat the change of this line in `neutral_surfaces.m`.</li> 
                
                  * It also appears to be necessary to tell Matlab where to look, so add the line  
                    `setenv('DYLD_LIBRARY_PATH', '/opt/local/lib')`  
                    somewhere near the top of both `gamma_n.m` and `neutral_surfaces.m` files (perhaps after the first `end`).</p> 
                      * If it ran successfully, you should have casts and surfaces output to the screen which look like <a href="http://observationaloceanography.com/neutral-density-output-from-running-example/" title="Neutral density: Output from running >> example&#8221;>this</a>.</ol> </ol> 
                
                <a id="troubleshooting"></a>  
                
                
                ### Troubleshooting:
                
                Based on feedback from a couple folks, you may need to update your installation methodology:
                
                From [Uriel Zajaczkovski][16], 16 Oct 2012:
                
                  1. Installation was done on Mountain Lion + Matlab 2012a. Compilation went ok, except that when I tried to run gamma_n.m I got: 
                      1. dyld: Library not loaded: /opt/local/lib/libnetcdf.7.dylib  
                        Referenced from: /opt/local/lib/libnetcdff.5.dylib  
                        Reason: Incompatible library version: libnetcdff.5.dylib requires version 10.0.0 or later, but libnetcdf.7.dylib provides version 9.0.0  
                        ./glabel_matlab: Trace/breakpoint trap
                      2. This can be fixed by setting the path (from inside Matlab) to:  
                        `setenv('DYLD_LIBRARY_PATH', '/opt/local/lib')` 
                
                From **Danny Kaufman**, 18 Oct 2012:
                
                Mountain Lion with MATLAB version 2012a
                
                  1. I added the full path to each line in both gamma\_n.m and neutral\_surfaces.m &#8230; including the `command = ['!/Users/Danny/Documents/.../glabel_matlab ... `
                  2. before the ` command = ['!/Users ... `, I added `setenv('DYLD_LIBRARY_PATH', '/opt/local/bin')`, which was necessary to access the correct netcdf library files
                  3. I also added the fullpath to each filename in both `glabel_matlab.f` and `nsfces_matlab.f` before compiling the `Makefile_interface`
                
                **Run into any other issues not described here? Leave a note in the comments below.**
                
                *&#8211;updated Feb 2014&#8211;*

 [1]: http://www.marine.csiro.au/%7Ejackett/NeutralDensity/
 [2]: http://www.macports.org/
 [3]: fink.sf.net/‎
 [4]: http://observationaloceanography.com/wp-content/uploads/2014/04/CSIRO_neutral_density.pdf
 [5]: http://observationaloceanography.com/neutral-density-code/#download
 [6]: http://observationaloceanography.com/neutral-density-code/#codeinstall
 [7]: http://observationaloceanography.com/neutral-density-code/#gamma
 [8]: http://observationaloceanography.com/neutral-density-code/#interface
 [9]: http://observationaloceanography.com/neutral-density-code/#example
 [10]: #troubleshooting
 [11]: http://observationaloceanography.com/macports-for-oceanography/ "MacPorts for oceanography"
 [12]: ftp://ftp.marine.csiro.au/software/jackett/gamma.tar.Z
 [13]: http://observationaloceanography.com/makefile_gamma/ "Makefile_gamma"
 [14]: http://observationaloceanography.com/neutral-density-making-gamma-a-output-to-screen/ "Neutral density: Making gamma.a output to screen"
 [15]: http://observationaloceanography.com/makefile_interface/ "Makefile_interface"
 [16]: mailto:uzajaczk@ucsd.edu