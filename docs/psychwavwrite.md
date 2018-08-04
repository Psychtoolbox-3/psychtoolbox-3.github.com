# [psychwavwrite](psychwavwrite)
##### >[Psychtoolbox](Psychtoolbox)>[PsychSound](PsychSound)

psychwavwrite - Replacement for wavwrite().  
  
Replaces the Matlab wavwrite() function, which was removed  
in Matlab R2015b, by the audiowrite() function, which was  
introduced in R2012b, to provide basic sanity to the mess  
that is Matlab's way of (not) dealing with "backwards  
compatibility".  
  
This is a least common denominator implementation of  
what both wavwrite() and audiowrite() support in a  
compatible fashion. See the help of either one for  
details.  
  
### Usage:  
  
 wavwrite(y,filename)  
 wavwrite(y,Fs,filename)  
 wavwrite(y,Fs,N,filename)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychSound/psychwavwrite.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychSound/psychwavwrite.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychSound/psychwavwrite.m</code>
</div>

