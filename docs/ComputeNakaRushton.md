# [ComputeNakaRushton](ComputeNakaRushton)
##### >[Psychtoolbox](Psychtoolbox)>[Psychometric](Psychometric)

[response] =  [ComputeNakaRushton](ComputeNakaRushton)(params,contrast)  
  
Compute the Naka-Rushton function on passed vector of contrasts.  
Several different forms may be computed depending on length of  
passed params vector.  
  
length(params) == 2  
  sigma = params(1)  
  n = params(2)  
  response = contrast^n/[contrast^n + sigma^n]  
  
length(params) == 3  
  Rmax = params(1)  
  sigma = params(2)  
  n = params(3)  
  response = Rmax\*[contrast^n]/[contrast^n + sigma^n]  
  
length(params) == 4  
  Rmax = params(1)  
  sigma = params(2)  
  n = params(3)  
  m = params(4)  
  response = Rmax\*[contrast^n]/[contrast^m + sigma^m]  
  
8/1/05    dhb, pr     Wrote from [FitLightnessOrient](FitLightnessOrient) version  
8/2/07    dhb         Rewrote to allow several different forms depending  
                      on length of params.  
12/5/10   dhb         Expanded comment.  Error check on input length  
9/23/13   dhb         Fix BAD bug.  This wasn't computing what the comments said it was.  
                      Not sure when that crept in.  The contrast in the numerator was  
                      being divided by sigma before being raised to the power n.  No idea why.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/Psychometric/ComputeNakaRushton.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/Psychometric/ComputeNakaRushton.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/Psychometric/ComputeNakaRushton.m</code>
</div>

