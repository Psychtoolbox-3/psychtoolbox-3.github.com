# [AltSize](AltSize)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

varargout = [AltSize](AltSize)(in,arg)  
  
extends size()'s functionality to support querying the size of multiple  
dimensions of a variable in one call.  
requested dimensions can be repeated and may (of course) be singleton  
number of output arguments must match number of requested dimension sizes  
or be one, in which case a vector is returned  
  
example:  
    in = ones(1,2,3,4,5);  
    [d e f g h i] = [AltSize](AltSize)(in,[1 3 2 8 4 2])  
    d =  
         1  
    e =  
         3  
    f =  
         2  
    g =  
         1  
    h =  
         4  
    i =  
         2  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/AltSize.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/AltSize.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/AltSize.m</code>
</div>

