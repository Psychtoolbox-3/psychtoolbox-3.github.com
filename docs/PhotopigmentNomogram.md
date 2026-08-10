# [PhotopigmentNomogram](PhotopigmentNomogram)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetricData](PsychColorimetricData)

T\_absorbance = [PhotopigmentNomogram](PhotopigmentNomogram)(S,lambdaMax,[source])  
  
Compute normalized absorbance according to various  
nomograms.  This is basically a wrapper routine.  
  Baylor  
  Dawis  
  Govardovskii (Default)  
  Lamb  
  [StockmanSharpe](StockmanSharpe)  
  [StockmanRider](StockmanRider)  
  
7/11/03  dhb  Wrote it.  
7/16/03  dhb  Add [StockmanSharpe](StockmanSharpe).  
4/10/26  Add  Add [StockmanRider](StockmanRider).  
         Systematially edit all the individual functions so that if wl  
         spacing is <= 1, they normalize the return to peak of 1.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetricData/PhotopigmentNomogram.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetricData/PhotopigmentNomogram.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetricData/PhotopigmentNomogram.m</code>
</div>

