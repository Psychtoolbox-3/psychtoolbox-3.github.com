# [PsychComputeSHA](PsychComputeSHA)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

hash = [PsychComputeSHA](PsychComputeSHA)(msg [, shaId='256']) -- Return the SHA hash of a string.  
  
This uses either GNU/Octave's builtin hash() function, or if that doesn't exist,  
e.g., on Matlab or old Octave versions, falls back to Java's [MessageDigest](MessageDigest)  
hashing classes to do the same in a slightly less efficient way.  
  
'msg' should be a string of which the hash should be computed and returned.  
  
'shaId' optional string with numbers, selecting one of the supported SHA  
functions. This defaults to SHA-256, ie. shaId == '256', if omitted.  
  
Currently the following shaId's are supported by both Octave and Matlab:  
'1', '224', '256', '384', '512'  
  
Returns 'hash' as the string with the returned SHA hash.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/PsychComputeSHA.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/PsychComputeSHA.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/PsychComputeSHA.m</code>
</div>

