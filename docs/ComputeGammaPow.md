# [ComputeGammaPow](ComputeGammaPow)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGamma](PsychGamma)

output = [ComputeGammaPow](ComputeGammaPow)(x,input)  
  
Compute the gamma table using simple gamma function.  
  
Largest value in input must be the maximum device  
setting.  This is wise during measurements in   
any case.  
  
output = ((input/maxInput).^x(1));  
  
10/3/93  dhb,jms  Normalize output to max of 1, remove old x(1).  
                  Better be sure that last value is max setting.  
8/7/00   dhb      Modify convention with gamma to be consistent  
                  with extended gamma function.  
                  Get rid of explicity normalization.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGamma/ComputeGammaPow.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGamma/ComputeGammaPow.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGamma/ComputeGammaPow.m</code>
</div>

