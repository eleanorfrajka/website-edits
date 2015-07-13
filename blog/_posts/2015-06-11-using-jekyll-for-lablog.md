---
layout: post
title: "Using Jekyll for a Lab notebook"
category: workflow
permalink: /:year/:month-:day-:title.html
date: "2015-06-10"
tags:
 - workflow
---


I came across **Jekyll** for an online lab notebook through some GitHub browsing.  I found two that were interesting, the [MadsenLabNotebook](http://notebook.madsenlab.org/labnotebook.html) and [LabLog](http://fdschneider.github.io/blog/2014/labnotebook_release/) by Schneider.  I prefer the Madsen because I liked the style and flexibility to organise by project and experiment, but in the end went with LabLog because it was easier to install and start out for a complete newbie.

The great thing is that the organisation by post and semi-automatic creating of entries was very similar to a latex research notebook I'd started using a couple years ago.  

The benefit of the Jekyll versions include:
    - using Markdown, which is easier to read in the raw format
    - Markdown is also simpler to track changes with git
    - It _could_ be web-public if desired, but also runs locally
    - It tracks both original post creating and updates, so is more dynamic
    - Tags to allow multiple groupings of individual entries
    - Organisation by date.

And it still retains numerous benefits from my latex version:
    - Using Latex math formating through **mathjax**
    - Individual files for individual entries
    
## Starting to use Jekyll  ##
In the process, I've learned quite a few things
    - **Installing Jekyll** is easy, but I needed to get rvm if I didn't want to run the gem install jekyll with sudo
    - **Cloning the LabLog** was simple.  I just started using GitHub to host gists, but followed the instructions on the GitHub pages website for creating my own website (then ditched it because I'm not sure I want this public yet) and then cloned the LabLog to my local computer and copied the contents into a new directory to play with.  
    - **Local serving** I love being able to work on this jekyll thing and view it on my own computer with no internet, and then (not yet tested) serve it to GitHub or elsewhere as a live website. Wow.  I could really be converted from WordPress.

I also came across this beautiful tool for editing _everything_, markdown, scripts, latex, matlab code...
    - **Sublime Text**, a text editor for doing all this markup stuff, is pretty.  It reminds me of using unix and emacs, back in the day. 

