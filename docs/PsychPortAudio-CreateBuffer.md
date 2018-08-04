# [PsychPortAudio('CreateBuffer')](PsychPortAudio-CreateBuffer) 
##### [Psychtoolbox](Psychtoolbox)>[PsychPortAudio](PsychPortAudio).{mex*} subfunction


Create a new dynamic audio data playback buffer for a [PortAudio](PortAudio) audio device and  
fill it with initial data.  
Return a 'bufferhandle' to the new buffer. 'pahandle' is the optional handle of  
the device whose buffer is to be filled. 'bufferdata' is a matrix with audio  
data in double() or single() format. Each row of the matrix specifies one sound  
channel, each column one sample for each channel. Only floating point values are  
supported. Samples need to be in range -1.0 to +1.0, with 0.0 for silence. This  
is intentionally a very restricted interface. For lowest latency and best timing  
we want you to provide audio data exactly at the optimal format and sample rate,  
so the driver can safe computation time and latency for expensive sample rate  
conversion, sample format conversion, and bounds checking/clipping.  
  
You can refill the buffer anytime via the [PsychPortAudio](PsychPortAudio)('RefillBuffer') call.  
You can delete the buffer via the [PsychPortAudio](PsychPortAudio)('DeleteBuffer') call, once it  
is not used anymore.   
You can attach the buffer to an audio playback schedule for actual audio  
playback via the [PsychPortAudio](PsychPortAudio)('AddToSchedule') call.  
The same buffer can be attached to and used by multiple audio devices  
simultaneously, or multiple times within one or more playback schedules.   


###See also:
Open [FillBuffer](PsychPortAudio-FillBuffer) [GetStatus](PsychPortAudio-GetStatus) 
