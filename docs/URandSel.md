# [URandSel](URandSel)
##### >[Psychtoolbox](Psychtoolbox)>[PsychProbability](PsychProbability)

sel = [RandSel](RandSel)(in,n)  
  if N is a scalar  
    randomly selects N elements from set IN, each element from IN will  
    be selected up to one time (so sampling without replacing).  
    Output is of size 1xN  
  if N is a vector  
    randomly selects prod(N) elements from set IN, without replacing. N  
    specifies the shape of the output, e.g., if N=[10 10 5], SEL will be  
    a 10x10x5 matrix  
  IN can be of any datatype and can have any number of dimensions and  
  elements  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychProbability/URandSel.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychProbability/URandSel.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychProbability/URandSel.m</code>
</div>

