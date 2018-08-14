# [FitWeibTAFC](FitWeibTAFC)
##### >[Psychtoolbox](Psychtoolbox)>[Psychometric](Psychometric)

 [alpha,beta,thresh92] = [FitWeibTAFC](FitWeibTAFC)(inputs,nCorrect,nError,...  
      [alpha0],[beta0])  
  
 Maximum likelihood fit of a Weibull function to TAFC psychometric data.  
  
 Requires the optimization toolbox. Doesn't work with Octave yet.  
  
###  INPUTS:  
   inputs:   Contains the input levels  
   nCorrect: Contains the number of yes responses at   
             the corresponding input level  
   nError:   Contains the number of no responses at   
             the corresponding input level  
  alpha0:    Initial guess for alpha (optional)  
  beta0:     Initial guess for beta (optional)  
 OUTPUTS:  
  alpha      Weibull alpha parameter  
  beta       Weibull beta parameter  
  thresh92   92% percent correct threshold  
  
 See also: [FitWeibAlphTAFC](FitWeibAlphTAFC), [FitWeibYN](FitWeibYN), [FitCumNormYN](FitCumNormYN), [FitLogitYN](FitLogitYN)  
  
 8/25/94   dhb, ccc    Cleaned comments, return 92% correct threshold  
 2/5/97    dhb         Check if fminu is not available.  
                       Add slope test.  
 4/26/97   dhb         Fix bug in threshold assignment  
 10/13/00  dhb         Improve initial guess for alpha.  Thanks to Duje Tadin  
                       for identifying the need for this.  
 4/18/02   dhb         Suppress warnings in calls to optimization toolbox.  
 3/5/05    dhb         Update for optimization toolbox version 2.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/Psychometric/FitWeibTAFC.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/Psychometric/FitWeibTAFC.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/Psychometric/FitWeibTAFC.m</code>
</div>

