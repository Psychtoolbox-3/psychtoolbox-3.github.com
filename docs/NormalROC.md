# [NormalROC](NormalROC)
##### >[Psychtoolbox](Psychtoolbox)>[Psychometric](Psychometric)

ROC = [NormalROC](NormalROC)(logbetas,us,vars,un,varn)  
  
Compute ROC curve given the parameters.  Done  
analytically for speed.  
  
The trick here is to solve for the values of x  
such that log(l(x)) \> logbetas.  When the variances  
are unequal, there can be two distinct regions.  
I basically handle this by brute force, since there  
are not too many distinct cases.  
  
This routine is not carefully tested and may  
contain errors.  
  
xx/xx/xx  dhb  Wrote it.  
10/4/00   dhb  Added caveat about bug possibilities, based  
               in part on disagreement between this routine  
               and some Monte Carlo simulations.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/Psychometric/NormalROC.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/Psychometric/NormalROC.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/Psychometric/NormalROC.m</code>
</div>

