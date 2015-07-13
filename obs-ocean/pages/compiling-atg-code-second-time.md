---
title: Compiling ATG code, second time
author: Eleanor Frajka-Williams
layout: page
header: no
---
This is what I got when I compiled the software to load [Along track gridded altimetry data][1] the second time (after making changes to use `swap_byte.c`).

There were a lot fewer warnings!

`$ make<br />
cc    -c -o decode_ssha_data.o decode_ssha_data.c<br />
decode_ssha_data.c:9:4: warning: implicitly declaring library function 'memmove' with type 'void *(void *, const void *, unsigned long)'<br />
   memmove(&#038;ssha_data.days, &#038;buf[off], sizeof(ssha_data.days));<br />
   ^<br />
decode_ssha_data.c:9:4: note: please include the header <string.h> or explicitly provide a declaration for 'memmove'<br />
decode_ssha_data.c:48:4: warning: implicit declaration of function 'swap_bytes' is invalid in C99 [-Wimplicit-function-declaration]<br />
   swap_bytes(&#038;ssha_data.days, 0, 2);<br />
   ^<br />
2 warnings generated.<br />
cc -o sshadmp_v2 sshadmp.o print_ssha_header.o decode_ssha_data.o print_ssha_data.o swap_bytes.o<br />
`

 [1]: http://frajka-williams.com/data-sources/along-track-gridded-altimetry-to-matlab/ "SSH along tracks – Altimetry"