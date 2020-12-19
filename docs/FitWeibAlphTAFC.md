# [FitWeibAlphTAFC](FitWeibAlphTAFC)
##### >[Psychtoolbox](Psychtoolbox)>[Psychometric](Psychometric)

[alpha,beta,thresh92] = [FitWeibAlphTAFC](FitWeibAlphTAFC)(inputs,nCorrect,nError,alpha0,beta0)  
  
Maximum likelihood fit of a Weibull function to psychometric data,  
search only on alpha with fixed beta as passed.  
  
Requires the optimization toolbox.  
  
### INPUTS:  
  inputs:     contains the input levels  
  nCorrect:   contains the number of yes responses at   
              the corresponding input inputs  
  nError:     contains the number of no responses at   
              the corresponding input inputs  
  alpha0:     Initial guess for alpha, empty for default [1].  
  beta0:      Value for beta  
  
### OUTPUTS:  
  alpha       Weibull alpha parameter  
  beta        Weibull beta parameter  
  thresh92    92% percent correct threshold  
  
See also: [FitWeibTAFC](FitWeibTAFC), [FitFitWeibYN](FitFitWeibYN), [FitCumNormYN](FitCumNormYN), [FitLogitYN](FitLogitYN)  
  
8/25/94   dhb, ccc    Cleaned comments, return 92% correct threshold.  
2/8/97    dhb         Added check for optimization toolbox.  
4/26/97   dhb         Change threshold to thresh92.  
4/18/02   dhb         Fix reference to undefined variable 'levels'.  
          dhb         Suppress warnings in calls to optimization toolbox.  
3/5/05    dhb         Update for optimization toolbox version 2.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/Psychometric/FitWeibAlphTAFC.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/Psychometric/FitWeibAlphTAFC.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/Psychometric/FitWeibAlphTAFC.m</code>
</div>

