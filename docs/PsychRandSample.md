# [PsychRandSample](PsychRandSample)
##### >[Psychtoolbox](Psychtoolbox)>[PsychProbability](PsychProbability)

x=[PsychRandSample](PsychRandSample)(list,[dims])  
  
Returns a random sample from a list. The optional second argument may be  
used to request an array (of size dims) of independent samples. E.g.  
[PsychRandSample](PsychRandSample)(-1:1,[10,10]) returns a 10x10 array of samples from the list  
-1:1.  [PsychRandSample](PsychRandSample) is a quick way to generate samples (e.g. visual noise)  
from a bounded Gaussian distribution. Also see RAND, RANDN, [Randi](Randi),  
[Sample](Sample), and [Shuffle](Shuffle).  
  
"list" can be a double, char, cell, or struct array, but it must be a   
vector (1xn or nx1). In the future, we may accept matrices (mxn) and treat  
columns separately, as other Matlab functions do.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychProbability/PsychRandSample.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychProbability/PsychRandSample.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychProbability/PsychRandSample.m</code>
</div>

