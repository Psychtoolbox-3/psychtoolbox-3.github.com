# [ComputeWeibYN](ComputeWeibYN)
##### >[Psychtoolbox](Psychtoolbox)>[Psychometric](Psychometric)

pyes = [ComputeWeibYN](ComputeWeibYN)(x,alpha,beta)  
  
Compute the value of a yes-no weibull psychometric function.  
If 'x' is a matrix and the parameters are scalars, the same   
psychometric function is applied to the whole matrix.  
If 'x' is a matrix and the parameters are vectors, the  
parameters are taken as applying to separate columns.  
  
   pyes = ( 1.0 - exp( - (x./alpha).^beta ) )  
  
9/15/93  jms  Added some special casing to deal with matrix inputs  
              with/without vectors of parameters  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/Psychometric/ComputeWeibYN.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/Psychometric/ComputeWeibYN.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/Psychometric/ComputeWeibYN.m</code>
</div>

