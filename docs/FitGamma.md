# [FitGamma](FitGamma)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGamma](PsychGamma)

[fit\_out,x,fitComment] = ...  
  [FitGamma](FitGamma)(values\_in,measurements,values\_out,[fitType])  
  
Fit a gamma function.  This essentially a driver function.  
It has two main purposes.  
  
First it tries several different  
underlying parametric forms for the fit and chooses the best  
for a particular data set.  
  
Second, it does the bookkeeping for fitting each column of  
input measurements.  (Each of the underlying fit functions expects  
only vector input.)  
  
To a large extent, the interface to the underlying fit functions  
(e.g. [FitGammaPow](FitGammaPow), [FitGammaSig](FitGammaSig), ...) is uniform.  However, this routine  
does have to know a little bit about initial value dimension and choice.  
We have tried to localize this information in the initialization routines  
(e.g. [InitialXPow](InitialXPow), [InitialXSig](InitialXSig), ...) as much as possible, but some  
caution is advised.  
  
Optional argument fitType allows you to force the return of a particular  
parametric form.  Currently:  
  fitType == 1:  Power function  
  fitType == 2:  Extended power function  
  fitType == 3:  Sigmoid  
  fitType == 4:  Weibull  
  fitType == 5:  Modified polynomial  
  fitType == 6:  Linear interpolation  
  fitType == 7:  Cubic spline  
  
All fit types are in a form such that the fit is forced through the  
origin for 0 input.  This is because our convention is that gamma  
correction happens after subtraction of the ambient light.  
  
NOTE: [FitGammaPow](FitGammaPow) (and perhaps other subroutines) uses CONSTR, which is part of the   
Mathworks Optimization Toolbox.  
  
Also see [FitGammaDemo](FitGammaDemo).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGamma/FitGamma.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGamma/FitGamma.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGamma/FitGamma.m</code>
</div>

