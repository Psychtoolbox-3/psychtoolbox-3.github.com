# [psychwavread](psychwavread)
##### >[Psychtoolbox](Psychtoolbox)>[PsychSound](PsychSound)

psychwavread - Replacement for wavread().  
  
Replaces the Matlab wavread() function, which was removed  
in Matlab R2015b, by the audioread() function, which was  
introduced in R2012b, to provide basic sanity to the mess  
that is Matlab's way of (not) dealing with "backwards  
compatibility".  
  
This is a least common denominator implementation of  
what both wavread() and audioread() support in a  
compatible fashion. See the help of either one for  
details.  
  
### Usage:  
  
[y, Fs] = psychwavread(filename [, samples][, dataType]);  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychSound/psychwavread.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychSound/psychwavread.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychSound/psychwavread.m</code>
</div>

