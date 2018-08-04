# [MergeCell](MergeCell)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

Merges contents of multiple cell arrays into one big cell array  
  
c = [MergeCell](MergeCell)(varargin)  
  
[MergeCell](MergeCell) takes any number of cell vectors (contain the same datatype)  
and concatenates their contents into one big cellvector  
Any signleton inputs are expanded as needed, these inputs can be 1x1  
cells or the contained datatype itself  
  
Example: To add some information about fit to plot legend, we'd wan't to  
append information about the fit to the line labels:  
  
linelbls = {'line a','line b','line c'};  
chi2\_r   = [.9 1 4.2];  
chi2\_rtxt= arrayfun(@(x) sprintf('slope: %.3f',x),chi2\_r,'UniformOutput',false);  
  
leglbls  = [MergeCell](MergeCell)(linelbls,', chi^2\_r: ',chi2\_rtxt);  
% leglbls  = [MergeCell](MergeCell)(linelbls,{', chi^2\_r: '},chi2\_rtxt); would be equivalent  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/MergeCell.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/MergeCell.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/MergeCell.m</code>
</div>

