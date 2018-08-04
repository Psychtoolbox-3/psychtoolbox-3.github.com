# [ComputeWeibTAFC](ComputeWeibTAFC)
##### >[Psychtoolbox](Psychtoolbox)>[Psychometric](Psychometric)

pCorrect = [ComputeWeibTAFC](ComputeWeibTAFC)(x,alpha,beta)  
  
Compute the value of a TAFC weibull psychometric function.  
If 'x' is a matrix and the parameters are scalars, the same   
psychometric function is applied to the whole matrix.  
If 'x' is a matrix and the parameters are vectors, the  
parameters are taken as applying to separate columns.  
  
   pCorrect = ( 1.0 - 0.5\*exp( - (x./alpha).^beta ) )  
  
9/15/93  jms         Added some special casing to deal with matrix inputs  
                     with/without vectors of parameters  
8/26/94  dhb, ccc      Handle weird values of alpha, beta  
10/13/00 dhb         Improve initial guess for alpha.  Thanks to Duje Tadin  
                     for identifying the need for this.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/Psychometric/ComputeWeibTAFC.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/Psychometric/ComputeWeibTAFC.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/Psychometric/ComputeWeibTAFC.m</code>
</div>

