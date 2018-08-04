# [FitCumNormYN](FitCumNormYN)
##### >[Psychtoolbox](Psychtoolbox)>[Psychometric](Psychometric)

[uEst,varEst] = [FitCumNormYN](FitCumNormYN)(inputs,nYes,nNo)  
  
Fits a cumulative normal function to the passed yes-no data.  
Requires the optimization toolbox.  
  
### INPUTS:  
  inputs:   Input levels  
  nYes:     Number of yes responses at the corresponding input level  
  nNo:      Number of no responses at the corresponding input level  
OUTPUTS:  
  uEst  
  varEst  
  
See also: [FitWeibTAFC](FitWeibTAFC), [FitFitWeibYN](FitFitWeibYN), [FitWeibAlphTAFC](FitWeibAlphTAFC), [FitLogitYN](FitLogitYN)  
  
9/22/93   jms   Created from [FitWeibullYN](FitWeibullYN).  
2/8/97    dhb   Cleaned up and added some comments.  
                Check that optimization toolbox is present.  
10/4/00   dhb   Fixed bugs along lines suggested by Keith Schneider.  
                Case of uInitial = 0 wasn't handled properly, and  
                variance search limits were set based on mean.  
3/4/05      dhb   Conditionals for optimization toolbox version.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/Psychometric/FitCumNormYN.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/Psychometric/FitCumNormYN.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/Psychometric/FitCumNormYN.m</code>
</div>

