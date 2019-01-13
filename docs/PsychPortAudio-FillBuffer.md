# [PsychPortAudio('FillBuffer')](PsychPortAudio-FillBuffer) 
##### [Psychtoolbox](Psychtoolbox)>[PsychPortAudio](PsychPortAudio).{mex*} subfunction


Fill audio data playback buffer of a [PortAudio](PortAudio) audio device. 'pahandle' is the  
handle of the device whose buffer is to be filled.  
'bufferdata' is usually a matrix with audio data in double() or single() format.  
Each row of the matrix specifies one sound channel, each column one sample for  
each channel. Only floating point values are supported. Samples need to be in  
range -1.0 to +1.0, with 0.0 for silence. This is intentionally a very  
restricted interface. For lowest latency and best timing we want you to provide  
audio data exactly at the optimal format and sample rate, so the driver can save  
computation time and latency for expensive sample rate conversion, sample format  
conversion, and bounds checking/clipping.  
Instead of a matrix, you can also pass in the bufferhandle of an audio buffer as  
'bufferdata'. This buffer must have been created beforehand via  
[PsychPortAudio](PsychPortAudio)('CreateBuffer', ...). Its content must satisfy the same  
constraints as in case of passing a matrix. The content will be copied from the  
given buffer to the standard audio buffer, so it is safe to delete that source  
buffer if you want.  
'streamingrefill' optional: If set to 1, ask the driver to refill the buffer  
immediately while playback is active. You can think of this as appending the  
audio data to the audio data already present in the buffer. This is useful for  
streaming playback or for creating live audio feedback loops. However, the  
current implementation doesn't really append the audio data. Instead it replaces  
already played audio data with your new data. This means that if you try to  
refill more than what has been actually played, this function will wait until  
enough storage space is available. A 'streamingrefill' flag of 2 will always  
refill immediately, ie., without waiting for sufficient buffer space to become  
available, even if this causes audible artifacts or some sound data to be  
overwritten. This is useful for a few very special audio feedback tricks, only  
use if you really know what you're doing!  
It will also fail if you try to refill more than the total buffer capacity.  
Default is to not do streaming refills, i.e., the buffer is filled in one batch  
while playback is stopped. Such a refill will also reset any playloop setting  
done via the 'SetLoop' subfunction to the full size of the refilled buffer.  
If the 'streamingrefill' flag is non-zero and the optional 'startIndex' argument  
is provided, then the refilling of the buffer will happen at the provided linear  
sample index 'startIndex'. If the argument is omitted, new data will be appended  
at the end of the current soundbuffers content. The 'startIndex' argument is  
ignored if no streaming refill is requested.  
  
Optionally the function returns the following values:  
'underflow' A flag: If 1 then the audio buffer underflowed because you didn't  
refill it in time, ie., some audible glitches were present in playback and your  
further playback timing is screwed.  
'nextSampleStartIndex' This is the absolute index in samples since start of  
playback of the sample that would follow after the last sample you added during  
this 'FillBuffer' call, ie., the first sample during a successive 'FillBuffer'  
call.  
'nextSampleETASecs' This value is undefined [(NaN)]((NaN)) if playback isn't running.  
During a streaming refill, it contains the predicted audio onset time in seconds  
of the sample with index 'nextSampleStartIndex'. Please note that this  
prediction can accumulate a prediction error if your buffer is so large that it  
contains samples that will only playback far in the future.  
  


###See also:
Open [GetDeviceSettings](PsychPortAudio-GetDeviceSettings) 
