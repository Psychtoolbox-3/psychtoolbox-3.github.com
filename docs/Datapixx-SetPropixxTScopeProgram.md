# [Datapixx('SetPropixxTScopeProgram')](Datapixx-SetPropixxTScopeProgram) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

Datapixx('SetPropixxTScopeProgram', program);

Sends a microcode program to the [PROPixx](PROPixx) T-Scope system.  
The argument is an array with two columns. Each row of the program contains one  
microcode command. The [PROPixx](PROPixx) supports a maximum of 1024 commandsThe first  
column contains the frame index which should be presented. The second column  
contains the number of times this frame should be presented. If the frame count  
is 0, then the program continues showing this last frame forever.  
  


###See also:
[EnablePropixxTScope](Datapixx-EnablePropixxTScope), [SetPropixxTScopeSchedule](Datapixx-SetPropixxTScopeSchedule), [StartPropixxTScopeSchedule](Datapixx-StartPropixxTScopeSchedule), [SetPropixxTScopeMode](Datapixx-SetPropixxTScopeMode), [SetPropixxTScopeProgramAddress](Datapixx-SetPropixxTScopeProgramAddress)
