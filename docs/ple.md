# [ple](ple)
##### >[Psychtoolbox](Psychtoolbox)>[PsychContributed](PsychContributed)

PLE "Print Last Error"  
  
ple prints the last error message issued by Matlab, including a complete  
backtrace of the call-sequence of functions that led to the error  
condition. Each line in the backtrace includes M-Filename and line number  
and allows you to open that file on the specified line by simply clicking  
on it with the mouse.  
  
ple is only supported on Matlab version 7 (Release 14 service pack 3) and later.  
  
Usage:  
ple     - Print last error, as contained in error structure '[psychlasterror](psychlasterror)'.  
ple(s)  - Print error and backtrace contained in error structure 's'.  
  
Copyright: This implementation of 'ple' is a slightly modified derivate of  
the original public domain implementation of ple.m by Malcolm Wood (the [MathWorks)](MathWorks)).  
  
The original file can be downloaded from Matlab Central at:  
http://www.mathworks.com/matlabcentral/fileexchange/loadFile.do?objectId=  
9525&objectType=file  
  
Thanks to David Fencsik for pointing us to this useful file and Malcolm  
Wood for writing it.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychContributed/ple.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychContributed/ple.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychContributed/ple.m</code>
</div>

