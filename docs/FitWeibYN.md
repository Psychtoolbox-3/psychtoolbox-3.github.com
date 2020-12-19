# [FitWeibYN](FitWeibYN)
##### >[Psychtoolbox](Psychtoolbox)>[Psychometric](Psychometric)

[alpha,beta,thresh50]=[FitWeibYN](FitWeibYN)(inputs,nYes,nNo,[alpha0],[beta0],[numFunCalls])  
  
Fits a Weibull function to the passed yes-no data.  
  
Requires the optimization toolbox. Doesn't work with Octave yet.  
  
### INPUTS:  
  inputs    Input levels  
  nYes      Number of yes responses at   
            the corresponding input inputs  
  nNo       Number of no responses at   
            the corresponding input inputs  
  alpha0    Initial guess for alpha (optional)  
  beta0     Initial guess for beta (optional)  
OUTPUTS:  
  alpha  
  beta  
  thresh50  50% threshold  
  
See also: [FitWeibTAFC](FitWeibTAFC), [FitFitWeibAlphTAFC](FitFitWeibAlphTAFC), [FitCumNormYN](FitCumNormYN), [FitLogitYN](FitLogitYN)  
  
9/15/93   jms  Added a pre-fit to get a better initial.  
          jms  Made 'options' a parameter so that printing could  
               be disabled higher up.  
9/23/93   jms  Test the slope of the linear pre-fit to set the upper  
               and lower bounds on the fit.  
2/5/97    dhb  Rewrote to parallel TAFC version but kept slope test.  
          dhb  Check for optimization toolbox.  
4/18/00   mpr  Added an option to set the number of allowed function calls  
10/13/00  dhb  Improve initial guess for alpha.  Thanks to Duje Tadin  
               for identifying the need for this.  
3/5/05    dhb  Update for optimization toolbox version 2.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/Psychometric/FitWeibYN.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/Psychometric/FitWeibYN.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/Psychometric/FitWeibYN.m</code>
</div>

