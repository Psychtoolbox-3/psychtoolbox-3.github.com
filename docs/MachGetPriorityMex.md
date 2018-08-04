# [MachGetPriorityMex](MachGetPriorityMex)
##### >[Psychtoolbox](Psychtoolbox)>[PsychPriority](PsychPriority)

priorityStruct = [MachGetPriorityMex](MachGetPriorityMex)(policyFlavorString, defaultFlag)  
  
OSX: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
Retrieve current or default parameters for the main MATLAB thread for any  
of the  three priority flavors: 'THREAD\_STANDARD\_POLICY',  
'THREAD\_TIME\_CONSTRAINT\_POLICY'  and 'THREAD\_PRECEDENCE\_POLICY'  
  
### The returned struct contains these fields:  
  
  priorityStruct.threadID          
      a number identifying the current thread.   
  
  priorityStruct.flavor            
      one of: 'THREAD\_STANDARD\_POLICY', 'THREAD\_TIME\_CONSTRAINT\_POLICY',  
      'THREAD\_PRECEDENCE\_POLICY'  
  
  priorityStruct.policy             
      see policy struct variants below  
  
  priorityStruct.policySize        
      The amount of memory allocated for the policy struct passed to the  
      Mach function thread\_policy\_get() by [MachGetPriorityMex](MachGetPriorityMex).  
  
  priorityStruct.policyFillSize    
      amount of memory filled into the  policy struct by  
      Mach function thread\_policy\_get().  
  
  priorityStruct.getDefault        
      value of the defaultFlag argument passed into [MachGetPriorityMex](MachGetPriorityMex).   
  
  priorityStruct.isDefault         
      If the flag value passed to [MachGetPriorityMex](MachGetPriorityMex) is 0, requesting  
      current parameter values and not default parameter values and yet  
      [MachGetPriorityMex](MachGetPriorityMex) returns default parameters and defaultFlag value  
      1, then the priority flavor which was specified in the first  
      argument to priorityFlavorString is not in effect.    
  
The form of the embedded struct "policy" depends on the value of  
priorityFlavorString argument.  
  
'THREAD\_STANDARD\_POLICY':  
    priorityStruct.flavorPolicy.no\_data    % a place holder only  
  
'THREAD\_TIME\_CONSTRAINT\_POLICY'     % see help [MachSetTimeConstraintPriority](MachSetTimeConstraintPriority)  
    priorityStruct.flavorPolicy.period  
    priorityStruct.flavorPolicy.computation  
    priorityStruct.flavorPolicy.constraint  
    priorityStruct.flavorPolicy.preemptible  
  
'THREAD\_PRECEDENCE\_POLICY'          % see help [MachSetTimeConstraintPriority](MachSetTimeConstraintPriority)  
    priorityStruct.flavorPolicy.importance  
  
There are three policy flavors but a thread may have only one of two   
policy modes: THREAD\_STANDARD\_POLICY or THREAD\_TIME\_CONSTRAINT\_POLICY.  
These are mutually-exclusive modes; setting a thread to either one will   
unset the other mode.  The "importance" parameter associated with   
THREAD\_PRECEDENCE\_POLICY is preserved after either THREAD\_STANDARD\_POLICY  
or THREAD\_TIME\_CONSTRAINT\_POLICY is set, however the  
THREAD\_PRECEDENCE\_POLICY "importance" setting is ignored by the Mach task  
scheduler while a thread is in  THREAD\_TIME\_CONSTRAINT\_POLICY mode.  A  
thread is governed by the "importance" parameter only when in  
THREAD\_STANDARD\_POLICY mode.   
  
[MachGetPriorityMex](MachGetPriorityMex) uses the OS X Darwin function thread\_policy\_get().  
For more information on thread\_policy\_get() see:  
Psychtoolbox3/Source/Common/[MachPriorityMex](MachPriorityMex)/[MachGetPriorityMex](MachGetPriorityMex).c  
http://developer.apple.com/documentation/Darwin/Conceptual/[KernelProgramming](KernelProgramming)/scheduler/chapter\_8\_section\_4.html  
/usr/include/mach/thread\_policy.h  
  
OS9: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[MachGetPriorityMex](MachGetPriorityMex) does not exist in OS 9.   
  
WIN: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[MachGetPriorityMex](MachGetPriorityMex) does not exist in Windows.  
  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
see also: [Priority](Priority), [Rush](Rush), [MachGetPriorityFlavor](MachGetPriorityFlavor), [MachSetPriorityMex](MachSetPriorityMex),   




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychPriority/MachGetPriorityMex.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychPriority/MachGetPriorityMex.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychPriority/MachGetPriorityMex.m</code>
</div>

