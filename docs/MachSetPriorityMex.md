# [MachSetPriorityMex](MachSetPriorityMex)
##### >[Psychtoolbox](Psychtoolbox)>[PsychPriority](PsychPriority)

priority=[MachSetPriorityMex](MachSetPriorityMex)(policyFlavorString [,arg1] [,arg2] [,arg3] [,arg4])  
  
OS X: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
Set  one of three priority flavors for the main MATLAB thread:  
'THREAD\_STANDARD\_POLICY', 'THREAD\_TIME\_CONSTRAINT\_POLICY',  
'THREAD\_PRECEDENCE\_POLICY'.  
  
Each of the threed flavors has an associated set of parameters   
following the flovor argument string in the first position:  
  
[MachSetPriorityMex](MachSetPriorityMex)('THREAD\_STANDARD\_POLICY');  
 There are no parameters.      
  
[MachSetPriorityMex](MachSetPriorityMex)('THREAD\_TIME\_CONSTRAINT\_POLICY',  
'periodTicks','computationTicks', 'constraint', 'preemptible');  
 See [MachSetTimeConstrainPriority](MachSetTimeConstrainPriority) for an explanation of arguments.  Note  
 that [MachSetPriorityMex](MachSetPriorityMex) arguments "period","computation", and  
 "constraint" are in units of bus tick rate which depends on you  
 particular model of computer, whereas [MachSetTimeConstrainPriority](MachSetTimeConstrainPriority)  
 accepts arguments in units of seconds.  Therefore it is better to use  
 [MachSetTimeConstrainPriority](MachSetTimeConstrainPriority) than [MachSetPriorityMex](MachSetPriorityMex).    
  
[MachSetPriorityMex](MachSetPriorityMex)('THREAD\_PRECEDENCE\_POLICY', 'importance');  
 Set the priority of the main MATLAB thread relative to other threads of  
 the MATLAB process.  This is not useful.    
  
Parameters for any priority flavor may be omitted and the single string  
argument 'default' substituted in their place:    
  [MachSetPriorityMex](MachSetPriorityMex)('THREAD\_STANDARD\_POLICY', 'default');  
  [MachSetPriorityMex](MachSetPriorityMex)('THREAD\_TIME\_CONSTRAINT\_POLICY', 'default');  
  [MachSetPriorityMex](MachSetPriorityMex)('THREAD\_PRECEDENCE\_POLICY', 'default');  
Call [MachGetPriorityMex](MachGetPriorityMex) with the 'default' flag argument set to discover  
default values. The default values are provided by the the underlying  
thread\_policy\_get() function.  
  
There are three policy flavors but a thread may have only one of two   
policy modes: THREAD\_STANDARD\_POLICY or THREAD\_TIME\_CONSTRAINT\_POLICY.  
These are mutually-exclusive modes; setting a thread to either one will   
unset the other mode.  The "importance" parameter associated with   
THREAD\_PRECEDENCE\_POLICY is preserved after either THREAD\_STANDARD\_POLICY  
or THREAD\_TIME\_CONSTRAINT\_POLICY is set, however the  
THREAD\_PRECEDENCE\_POLICY setting is ignored by the Mach task scheduler  
while a thread is in  THREAD\_TIME\_CONSTRAINT\_POLICY mode.  A thread is  
governed by the   THREAD\_PRECEDENCE\_POLICY "importance" parameter only  
when in THREAD\_STANDARD\_POLICY mode.    
  
[MachSetPriorityMex](MachSetPriorityMex) calls the OS X Dawrin function thread\_policy\_set().  
for more information on thread\_policy\_set() see:  
Psychtoolbox3/Source/Common/[MachPriorityMex](MachPriorityMex)/[MachGetPriorityMex](MachGetPriorityMex).c  
Psychtoolbox3/Source/Common/[MachPriorityMex](MachPriorityMex)/[MachSetPriorityMex](MachSetPriorityMex).c  
http://developer.apple.com/documentation/Darwin/Conceptual/[KernelProgramming](KernelProgramming)/scheduler/chapter\_8\_section\_4.html  
/usr/include/mach/thread\_policy.h  
  
OS 9: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[MachSetPriorityMex](MachSetPriorityMex) does not exist in OS 9.   
  
WINDOWS: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[MachSetPriorityMex](MachSetPriorityMex) does not exist in Windows.  
  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
see also: [Priority](Priority), [Rush](Rush), [MachGetPriorityMex](MachGetPriorityMex), [MachSetTimeConstraintPolicy](MachSetTimeConstraintPolicy)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychPriority/MachSetPriorityMex.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychPriority/MachSetPriorityMex.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychPriority/MachSetPriorityMex.m</code>
</div>

