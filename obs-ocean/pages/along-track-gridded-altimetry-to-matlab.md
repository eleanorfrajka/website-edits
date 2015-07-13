---
title: 'SSH along tracks - Altimetry'
author: Eleanor Frajka-Williams
layout: page
subheadline: ""
show_meta: false
teaser: ""
permalink: "/data/along-track-gridded-altimetry-to-matlab/"
header: no
---
### <a name="altimetry"></a>Along track gridded &#8211; Altimetry track data

How to download and parse into Matlab the along-track gridded altimetry product from the PODAAC website. The along-track **gridded** product is one step processed from the &#8220;along track&#8221; product in that it&#8217;s regularly gridded to approximately 6 km spacing along the track.

URL:<http://podaac-ftp.jpl.nasa.gov/DATA_CATALOG/topGravity.html>

  1. Get the software to read the files
  * **Download the software** to read this dataset from <ftp://podaac-ftp.jpl.nasa.gov/allData/topex/L2/tp_atg/software/c> I.e., open the above address in your browser, right click each filename, and choose &#8220;save target as..&#8221;. Select a dedicated directory on your computer. I use /Users/eddifying/Data/atg\_altimetry/sw\_c/
  * You should have retrieved the files: Makefile, decode\_ssha\_data.c, print\_ssha\_header.c, ssha\_data.h, ssha\_header.h, sshadmp\_v2, SSHA\_V2\_DUMP\_README, print\_ssha\_data.c, read\_sshafile.c, ssha\_defines.h, sshadmp.c, swap_bytes.c

  * Compile the code  
    *% make *

  2. Download all the track files
  * *Using wget instead of ftp:* Previously, I suggested getting the data via command-line `ftp`. But with the directory structure on the podaac-ftp space, it would be tiresome to change directory into each subdirectory to download the data. `wget` can be used to recursively get data out of the filestructure.
  * **Download data for the test case first.** At the command line, in the directory where you want the downloaded files to live, start with a  
    `$ wget -r --no-clobber  --user user --password password ftp://podaac-ftp.jpl.nasa.gov/allData/topex/L2/tp_ssha/c392/*001`  
    This should download the file `tpsshag2b392.001` which is needed to test the software. Then continue to get all the data in the next step. 
  * **Download all the cycles.** At the command line, use  
    `$ wget -r --no-clobber  --user user --password password ftp://podaac-ftp.jpl.nasa.gov/allData/topex/L2/tp_ssha/`  
    where you replace the second `user` with your username and the second `password` with your password. The option `-r` makes it recursive (i.e. the command will look into sub-directories and copy those as well), and the option `--no-clobber` checks whether or not a file is already on your local machine before downloading it (very handy if the download gets interrupted and you don&#8217;t want to start at the beginning). 
  * **Slight issue with directory structures**: When this downloads the directory structure, it gets *everything* and replicates that filestructure on your own machine. So in this case, from the location where I started the `wget` command, I gained a new subdirectory called `podaac-ftp.jpl.nasa.gov` with the further sub-directories `allData/topex/L2/tp_ssha/`, within which the data are now located. *I&#8217;m sure there&#8217;s a way to put things where you want them, but haven&#8217;t found it yet.* 
  * *Duration of download:* I started this around 10:40am on 13 Aug, and only 9/481 cycles were downloaded as of 11:18am. </ul> 
      * Test the software
      * Note: the test requires TPSSHA cycle 392 pass file `tpsshag2b392.001`, so you may want to interrupt your `wget` command above to ensure you have this one.
      * Run the file as `<br />
$ ./sshadmp_v2 c392/tpsshag2b392.001`  
        When prompted, enter &#8220;1&#8221; for the start and &#8220;1&#8221; for the end. On first running, I got this: [output from testing atg code][1]. (Note, formatting got messed up on input to the website.) Looking at the line for `days = [     45376] 0000b140`, according to the readme file `SSHA_V2_DUMP_README`, this should read `days         = [     16561] 000040b1`.
    There is a comment in the readme which says:
    
    > If you are using a VAX or other system that uses reverse order bytes  
    > for 2 and 4 byte integers than Unix, then the bytes need to be swapped  
    > in program decode\_ssha\_data.c. The calls to swap_bytes are there but  
    > commented out. Simply uncomment these calls and compile.
    
    so I uncommented these by removing the `/*` before and `*/` after, and recompiled (ran `$ make` again). See the output from running make the second time [here][2]. Running it on the 392-nd cycle, pass 1, the days now match! However, the `ssha` value does not. I got the [output shown here][3].</li> 
    
      * **Where is the problem coming from?** see this page on Unix byte order and incompatibility for binary files: <http://unixpapa.com/incnote/byteorder.html>. </ul> </ol> 
    
    * * *
    
    * * *
    
    ### Old instructions (prior to Aug 2013 update)
    
    *Note: these instructions were initially written for the data which are now available at [podaac-ftp.jpl.nasa.gov/allData/topex/retired/L2/tp_atg][4] rather than the new ftp-directories listed below. I have not verified that the code continues to work for the updated files. If you do, and it works (or doesn&#8217;t), I&#8217;d love to hear it! &#8211;Aug 2013*
    
      1. Get the software to read the files 
          * Download the software to read this dataset from [ ftp://podaac-ftp.jpl.nasa.gov/allData/topex/L2/tp_atg/sw/c][5] I.e., open the above address in your browser, right click each filename, and choose &#8220;save target as..&#8221;. Select a dedicated directory on your computer. I use /home/eleanor/Data/ssh/
          * Edit the paths for supporting files (reftrk.ascending, reftrk.descending, eqxl\_tp\_then\_j1.dat and eqxl\_new\_tp.dat) in atgdmp\_v2.c to be nothing, or /home/eleanor/Data/ssh/ (the dedicated directory you chose above). These lines are approximate (L146, 164, 183, 187, 189) or you can search for &#8220;pgsa&#8221;.
          * Compile the code  
            *% make *
      2. Download data files to test the software. 
          * Location: <ftp://podaac-ftp.jpl.nasa.gov/allData/topex/L2/tp_ssha/> Find file tpatgssha22.369 and do a right-click and save-target-as. Save it to the same directory as your software. This particular cycle is used in the test file example.
          * The filename structure is tpatgssha22.XXX, where tp=topex poseidon, atg=along track gridded, ssha=sea surface height anomaly and XXX is the cycle number, ranging from 11-481. Each file contains 254 passes (each orbit is 2 passes). More information can be found at [ftp://podaac.jpl.nasa.gov/allData/topex/L2/tp_atg/docs][6] or the URL above.
          * Later you&#8217;ll download the files you actually want for your work. If you don&#8217;t know which cycles and passes you want, I will include some matlab files later that will help you pick them using latitude and longitude boxes.
      3. Run the test files as shown in SAMPLE_DUMP.PRT 
          * The software is invoked as:  
            % ./atgdmp_v2 *filename* *mission* *cycle* *pass* *begin_rec* *end_rec*  
            where filename is the filename, mission is either tp for TOPEX/Poseidon or j1 for Jason-1, cycle is the cycle number (11-481 for T/P), pass is the pass number (1-254) and begin\_rec and end\_rec are the starting and ending records of the file.
          * Run the first sample:  
            *% ./atgdmp_v2 tpatgssha22.369 tp 369 1 1000 1100*
          * Compare the output with that in SAMPLE_DUMP.PRT. The line of code in the above step will print to screen. If you want to dump the data to a file, do instead  
            *% ./atgdmp_v2 tpatgssha22.369 tp 369 1 1000 1100 > firstexample.txt*
          * **Troubleshooting**: 
              1. When you compare your results to the SAMPLE\_DUMP.PRT, if the second printing of &#8220;deltat is not 1.0786&#8243; then you probably are missing a few libraries from your c-code. Edit atgdmp\_v2.c where you see &#8220;#include <stdio.h>&#8221; and below it add the lines &#8220;#include <stdlib.h>&#8221; and &#8220;#include <string.h>&#8221;.
              2. Recompile the code as before  
                *% make*
              3. Run the code on the first sample again. Compare the files. If it matches, then repeat for the next sample.
              4. If your SSHA is off by a factor of 256.. mine was, I don&#8217;t know why, then you can fix this by changing line 250 or 252 in the code, where you see &#8220;ssh[i-1]);&#8221;.
              5. To divide by 256, change that snippet to &#8220;ssh[i-1]>>8);&#8221; which does a bit shift, effectively dividing by 2^8 or 256.
              6. Recompile, rerun and test. Hopefully the output matches.  
                **Note (10/30/08):** The software for jason is slightly different&#8211;notably, there is another c file called &#8220;swapbyte.c&#8221;. You need this one, if you find you&#8217;re getting errors for sea surface height anomalies higher than 128.
      4. Your code works! You can now get the files you want for your research, run them and output these text files of the SSHA
    
    *&#8211;updated Aug 2013&#8211;*

 [1]: http://frajka-williams.com/data-sources/along-track-gridded-altimetry-to-matlab/output-from-testing-atg-code/ "Output from testing atg code"
 [2]: http://frajka-williams.com/data-sources/along-track-gridded-altimetry-to-matlab/compiling-atg-code-second-time/ "Compiling ATG code, second time"
 [3]: http://frajka-williams.com/data-sources/along-track-gridded-altimetry-to-matlab/output-from-testing-atg-code-second-time/ "Output from testing atg code, second time"
 [4]: ftp://podaac-ftp.jpl.nasa.gov/allData/topex/retired/L2/tp_atg
 [5]: ftp://podaac-ftp.jpl.nasa.gov/allData/topex/L2/tp_atg/sw/c
 [6]: ftp://podaac-ftp.jpl.nasa.gov/allData/topex/L2/tp_atg/docs