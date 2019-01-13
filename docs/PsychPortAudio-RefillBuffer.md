# [PsychPortAudio('RefillBuffer')](PsychPortAudio-RefillBuffer) 
##### [Psychtoolbox](Psychtoolbox)>[PsychPortAudio](PsychPortAudio).{mex*} subfunction


Refill part of an audio data playback buffer of a [PortAudio](PortAudio) audio device.  
'pahandle' is the handle of the device whose buffer is to be filled.  
'bufferhandle' is the handle of the buffer: Use a handle of zero for the  
standard buffer created and accessed via 'FillBuffer'.  
'bufferdata' is a matrix with audio data in double() or single() format. Each  
row of the matrix specifies one sound channel, each column one sample for each  
channel. Only floating point values are supported. Samples need to be in range  
-1.0 to +1.0, with 0.0 for silence. This is intentionally a very restricted  
interface. For lowest latency and best timing we want you to provide audio data  
exactly at the optimal format and sample rate, so the driver can save  
computation time and latency for expensive sample rate conversion, sample format  
conversion, and bounds checking/clipping.  
Instead of a matrix, you can also pass in the bufferhandle of an audio buffer as  
'bufferdata'. This buffer must have been created beforehand via  
[PsychPortAudio](PsychPortAudio)('CreateBuffer', ...). Its content must satisfy the same  
constraints as in case of passing a matrix. The content will be copied from the  
given buffer to the standard audio buffer, so it is safe to delete that source  
buffer if you want.  
'startIndex' optional: Defines the first sample frame within the buffer where  
refill should start. By default, refilling starts at the beginning of the buffer  
- at sample frame 0. 'startIndex' allows to start refilling at some offset.  
Please note that 'RefillBuffer' can't resize an existing buffer - you can't fill  
in more data than the current buffer capacity permits. If you want to add more  
sound, you'll need to use 'FillBuffer' or create a new buffer of proper  
capacity.  
'RefillBuffer' can be used any time on a buffer, even if the buffer is currently  
playing, allowing for on-the-fly replacement of content. However be careful to  
avoid the currently played section, or you'll hear audio artifacts. For  
streaming out audio content in a glitch-free way, you may want to use the  
'streamingrefill' option of the 'FillBuffer' subfunction instead.  
  


###See also:
Open [FillBuffer](PsychPortAudio-FillBuffer) [GetStatus](PsychPortAudio-GetStatus) 
