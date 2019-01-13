# [Eyelink('WaitForModeReady')](Eyelink-WaitForModeReady) 
##### [Psychtoolbox](Psychtoolbox)>[Eyelink](Eyelink).{mex*} subfunction


After a mode-change command is given to the [EyeLink](EyeLink) tracker,  
an additional 5 to 30 milliseconds may be needed to complete mode setup.  
Call this function after mode change functions to wait until they are finished  
setting up.  
maxwait is in milliseconds -- max duration to wait for the mode to change.  
Returns 0 if mode switching is done, else still waiting (assume a tracker error  
has occurred).  
  


###See also:

