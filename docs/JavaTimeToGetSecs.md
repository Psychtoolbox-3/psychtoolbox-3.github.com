# [JavaTimeToGetSecs](JavaTimeToGetSecs)
##### >[Psychtoolbox](Psychtoolbox)>[PsychJava](PsychJava)

timeSecs=[JavaTimeToGetSecs](JavaTimeToGetSecs)(javaTime, [updateInterval])  
  
Convert time as reported by "java.lang.System.currentTimeMillis()" to  
[GetSecs](GetSecs) units.    
  
The Java timebase and [JavaTimeToGetSecs](JavaTimeToGetSecs) are used internally by [GetChar](GetChar)  
because Java calls underlying [GetChar](GetChar) timestamp keyboard events in those  
units.  
  
updateInterval is the number of seconds before this function updates its  
internal timing cache measuring the difference between [GetSecs](GetSecs) and  
java.lang.System.currentTimeMillis().  If set to -1, the cache is only  
made the first time this function funs.  When ommitted, it defaults to 0,  
i.e., it recaches at every call.  
  
  
see also:  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychJava/JavaTimeToGetSecs.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychJava/JavaTimeToGetSecs.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychJava/JavaTimeToGetSecs.m</code>
</div>

