---
layout: page 
title: "Watermarking videos"
subheadline: "In Quicktime"
show_meta: false
teaser: "Watermarking videos (i.e. adding a graphic to all slides) can be useful if you’d like your slides to look more official, and/or want to prevent other people from borrowing them without attributing the source. Or, if it’s a requirement of your university/institution."
permalink: "/resources/watermarking-videos-in-quicktime/"
header: no
---
<!--...and learn at the same time.-->


I use Quicktime 7, primarily because I bought it way back when, and also because I have trouble viewing movies I’ve made in Matlab with the more recent versions of Quicktime for Macs.

I followed the steps from here: geniusdv.com: Including watermarks which can be summarized as:

1. Prepare the watermark/graphic.
    - Open the graphic you’d like to add in Quicktime 7.
    - Save it as a movie (so it’s in the same format as your other movie).
    - Select the graphic using “Edit>>Select All” then “Edit>>Copy”.

2. Add the watermark to your big movie
    - Open the big movie
    - Add the selection using “Edit>>Add to Selection & Scale”. This uses whatever was most recently copied and dumps it in.
    - Adjust the watermark settings using “Window>>Show Movie Properties”.
    - Make sure the watermark is on top: The watermark will most likely be “Video Track 2″, so select this, then verify that the value in the box after “Layer” for video track 2 is smaller than the value in the box after Layer in “Video track 1″. This ensures it’s on top.
    - Scale it. Chances are the watermark isn’t the size you’d like. Selecting “Video Track 2″, adjust the box after “Scaled size” until you get something that looks nice.
    - Offset it. To reposition the watermark, change the values in the X and Y boxes after “Offset” until you get it where you want it
    - Save new movie. Save your move with a new name (just in case something didn’t work, don’t overwrite the original) and then verify that the watermark looks right.

