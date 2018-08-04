# [PsychPortAudio('SetLoop')](PsychPortAudio-SetLoop) 
##### [Psychtoolbox](Psychtoolbox)>[PsychPortAudio](PsychPortAudio).{mex*} subfunction


Restrict audio playback to a subrange of sound samples in the current audio  
playback buffer for audio device 'pahandle'. The device must be open and a  
soundbuffer created via 'FillBuffer' for this setting to take effect. The  
setting is reset at each non-streaming 'FillBuffer' call.  
'startSample' defines the first sample to be played, it defaults to zero, ie.  
the very first in the buffer. 'endSample' the last sample to be played, it  
defaults to the end of the buffer.  
Calling this function without any parameter except 'pahandle' will therefore  
reset the playloop to the full buffer size. It is possible but not advisable to  
change the loop range while sound playback is active, as this may cause audible  
glitches or artifacts in the playback.  
By default, 'startSample' and 'endSample' are specified in units of samples, but  
if the optional flag 'UnitIsSeconds' is set to a non-zero value, then the given  
range is interpreted in units of seconds.   


###See also:
[FillBuffer](PsychPortAudio-FillBuffer) Start Stop [RescheduleStart](PsychPortAudio-RescheduleStart) 
