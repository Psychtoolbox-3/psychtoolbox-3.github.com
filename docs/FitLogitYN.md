# [FitLogitYN](FitLogitYN)
##### >[Psychtoolbox](Psychtoolbox)>[Psychometric](Psychometric)

[a,b,thresh50] = [FitLogistic](FitLogistic)(inputs,nYes,nNo)  
  
Fit a logistic function to YN psychometric data.  
Returns logistic parameters and 50% threshold.   
  
The form of the logistic equation is pYes = 1/(1+10^-(a\*inputs+b))  
  
The logistic is not a good function to use for serious work,  
but you can do a quick and dirty fit analytically and  
you can explain it to students more easily than some  
other candidate models for psychometric functions.  
  
See also: [FitLogistic](FitLogistic), [FitWeibYN](FitWeibYN), [FitCumNormYN](FitCumNormYN),   
 [InvertLogistic](InvertLogistic), [ComputeLogistic](ComputeLogistic).  
  
2/8/97      dhb     Wrote it.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/Psychometric/FitLogitYN.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/Psychometric/FitLogitYN.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/Psychometric/FitLogitYN.m</code>
</div>

