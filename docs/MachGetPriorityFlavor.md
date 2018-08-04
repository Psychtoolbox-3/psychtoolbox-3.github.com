# [MachGetPriorityFlavor](MachGetPriorityFlavor)
##### >[Psychtoolbox](Psychtoolbox)>[PsychPriority](PsychPriority)

OS X: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[MachGetPriorityFlavor](MachGetPriorityFlavor) returns the priority flavor mode of the main   
MATLAB thread, either 'THREAD\_TIME\_CONSTRAINT\_POLICY' or   
'THREAD\_STANDARD\_POLICY'.    
  
The second return argument, priorityStruct, is the  priority struct for  
the active priority flavor mode.  
  
The priority flavor 'THREAD\_PRECEDENCE\_POLICY' is never returned  
because its status is implied  by either 'THREAD\_TIME\_CONSTRAINT\_POLICY'  
or  'THREAD\_STANDARD\_POLICY':  
  
  -If flavorNameString is 'THREAD\_TIME\_CONSTRAINT\_POLICY', then then  
  'THREAD\_PRECEDENCE\_POLICY'and its 'importance' parameter  are ignored  
  by the Mach task scheduler.  
  
  -If flavorNameString is 'THREAD\_STANDARD\_POLICY' then the 'importance'  
  parameter associated with 'THREAD\_PRECEDENCE\_POLICY' governs the   
  relative allocation of CPU time between the main MATLAB thread and all  
  other threads of the MATLAB process.    
  
[MachGetPriorityFlavor](MachGetPriorityFlavor) probes priority using [MachGetPriorityMex](MachGetPriorityMex).  
  
OS 9: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[MachGetPriorityFlavor](MachGetPriorityFlavor) does not exist in OS 9.   
  
WINDOWS: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[MachGetPriorityFlavor](MachGetPriorityFlavor) does not exist in Windows.  
  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
see also: [Priority](Priority), [Rush](Rush), [MachGetPriorityMex](MachGetPriorityMex), [MachSetPriorityMex](MachSetPriorityMex),   




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychPriority/MachGetPriorityFlavor.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychPriority/MachGetPriorityFlavor.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychPriority/MachGetPriorityFlavor.m</code>
</div>

