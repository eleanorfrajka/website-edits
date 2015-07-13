---
title: Code snippets
author: Eleanor Frajka-Williams
layout: page
header: no
---
Here is a listing of the code-snippets available on this website (currently growing, as I transfer files to GitHub). Please note, all code is provided without warrantee or guarantee.

#### Handy functions

These are a few functions which are called by some of the code below.

  * **findbetw.m** &#8211; Finds indices of a vector that are within a specified range.   
    View the file: [findbetw.m][1] or as a [[text-file][2]]

#### Argo float profiles

  * **Load an Argo float profiles** in an arbitrary geographic region and time range. Requires data downloaded from a particular ocean basin (as defined by the Argo community, either Indian, Atlantic or Pacific). Also uses file *load\_argo\_1month.m*.   
    View m-file [load\_argo\_select.m][3] or as a [[text file][4]].
  * **Load 1 month of Argo float profiles**: Requires data downloaded from a particular ocean basin, then untarred. Is called by *load\_argo\_select.m*.   
    View the m-file: [load\_argo\_1month.m][5] or as a [[text-file][6]]

#### Oceancolor data (MODIS/SeaWiFS)

  * View the file: [load\_color\_1file.m][7] or as a [[text-file][8]]

*&#8211;updated May 2015&#8211;*

 [1]: http://observationaloceanography.com/data-analysis-2/code-snippets/findbetw-m/
 [2]: https://gist.githubusercontent.com/frajkawilliams/6898ec354d40c0ce2ff1/raw/793c1267fcf0cd51d48d195cf0580defbc423a6e/findbetw.m
 [3]: http://observationaloceanography.com/in-situ-data/argo-floats-for-hydrographic-data/load_argo_select-m/
 [4]: https://gist.githubusercontent.com/frajkawilliams/a8b906cd0f12b4a071eb/raw/ed17fd05f862d1177a646de5795d1980971eea84/load_argo_select.m
 [5]: http://observationaloceanography.com/in-situ-data/argo-floats-for-hydrographic-data/load_argo_1month-m/
 [6]: https://gist.githubusercontent.com/frajkawilliams/033c23f969e35393b5d0/raw/load_argo_1month.m
 [7]: http://observationaloceanography.com/satellite-data/ocean-color-modis-aqua/load_color_1file-m/
 [8]: https://gist.githubusercontent.com/frajkawilliams/414afd5a8f0ad333d42a/raw/load_color_1file.m