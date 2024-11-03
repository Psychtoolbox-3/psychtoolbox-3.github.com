# [PsychCV('AprilShutdown')](PsychCV-AprilShutdown) 
##### [Psychtoolbox](Psychtoolbox)>[PsychCV](PsychCV).{mex*} subfunction

PsychCV('AprilShutdown');

Shut down apriltag after use, release all resources.  
The memory buffer handle 'inputImageMemBuffer' returned by a prior call to  
inputImageMemBuffer = [PsychCV](PsychCV)('AprilInitialize', ...); will be invalid after  
this shutdown call and must not be used anymore, or Psychtoolbox will crash!  
  


###See also:
[AprilInitialize](PsychCV-AprilInitialize)
