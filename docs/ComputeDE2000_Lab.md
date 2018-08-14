# [ComputeDE2000_Lab](ComputeDE2000_Lab)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)

Computes the deltaE values (CIEDE2000) for color pairs given in CIELAB coordinates (L\*a\*b\*).  
  
      dE2000 = [ComputeDE2000](ComputeDE2000)\_Lab(Lab1,Lab2[,kLCH]);  
  
The inputs 'Lab1' and 'Lab2' are N\*3 matrices each with one color per row [L\*,a\*,b\*].   
The output is a column vector with N elements, containing the according   
dE2000 values.  
'kLCH' is optional and contains one or three elements for the weighting   
factors kL, kC, kH (either one value for all, or three values for each).   
The weighting factors are set to 1, if 'kLCH' is not specified.  
  
This implementation might not be the most efficient but it follows the formulas  
given in https://en.wikipedia.org/wiki/Color\_difference\#CIEDE2000 as closely  
as possible for better traceability.   




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/ComputeDE2000_Lab.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/ComputeDE2000_Lab.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/ComputeDE2000_Lab.m</code>
</div>

