# [ComputeGammaSig](ComputeGammaSig)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGamma](PsychGamma)

output = [ComputeGammaSig](ComputeGammaSig)(x,input)  
  
Compute the gamma table using sigmoidal function.  
  
sinput = (input/x(3)).^x(4);  
output = x(2).\*sinput./(sinput + x(1));  
  
10/3/93  dhb,jms  Normalize output to max of 1.  
                  Better be sure that last value is max setting.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGamma/ComputeGammaSig.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGamma/ComputeGammaSig.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGamma/ComputeGammaSig.m</code>
</div>

