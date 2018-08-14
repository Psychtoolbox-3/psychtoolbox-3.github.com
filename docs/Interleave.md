# [Interleave](Interleave)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

[vec] = [Interleave](Interleave)(varargin)  
Interleaves any number of vectors and scalars  
input is taken from consequetive elements of each input variable until a  
variable runs out.  
Output will be a columnvector.  
Output will be cell if any of the inputs is cell.  
Output will be char if none of the input is cell and any of the inputs is  
char  
  
a   = [A A A], b= [B B], c= [C C C C], d=D  
out = [Interleave](Interleave)(a,b,c,d)  
out = [A B C D A B C A C C];  
  
DN 06-11-2007  
DN 23-01-2008 updated to support scalars and conversion to char  
DN 28-04-2008 simplified input checking  
DN 28-05-2008 bugfix mixing numeric and char  
DN 09-06-2011 Now works fine with empty inputs. Few changes for compatibility  
              with Octave, might have more up ahead.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/Interleave.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/Interleave.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/Interleave.m</code>
</div>

