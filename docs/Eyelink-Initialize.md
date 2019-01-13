# [Eyelink('Initialize')](Eyelink-Initialize) 
##### [Psychtoolbox](Psychtoolbox)>[Eyelink](Eyelink).{mex*} subfunction

[status =] Eyelink('Initialize' [, displayCallbackFunction])

Initializes Eyelink and Ethernet system.  
Opens tracker connection, reports any problems.  
The optional argument 'displayCallbackFunction' registers the name of an m-file  
on the path that will handle callbacks from eyelink (typically  
'PsychEyelinkDispatchCallback' to display the camera image in PTB). No callbacks  
will be generated if that argument is omitted.  
Returns: 0 if OK, -1 if error  


###See also:

