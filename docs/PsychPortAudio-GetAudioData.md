# [PsychPortAudio('GetAudioData')](PsychPortAudio-GetAudioData) 
##### [Psychtoolbox](Psychtoolbox)>[PsychPortAudio](PsychPortAudio).{mex*} subfunction

[audiodata absrecposition overflow cstarttime] = PsychPortAudio('GetAudioData', pahandle [, amountToAllocateSecs][, minimumAmountToReturnSecs][, maximumAmountToReturnSecs][, singleType=0]);

Retrieve captured audio data from a audio device. 'pahandle' is the handle of  
the device whose data is to be retrieved.  
'audiodata' is a matrix with audio data in floating point format. Each row of  
the matrix returns one sound channel, each column one sample for each channel.  
Returned samples are in range -1.0 to +1.0, with 0.0 for silence. This is  
intentionally a very restricted interface. For lowest latency and best timing we  
want you to accept audio data exactly at the optimal format and sample rate, so  
the driver can save computation time and latency for expensive sample rate  
conversion, sample format conversion, and bounds checking/clipping.  
You must call this function once before start of capture operations to allocate  
an internal buffer that stores captured audio data inbetween your periodic  
calls. Provide 'amountToAllocateSecs' as requested buffersize in seconds. After  
start of capture you must call this function periodically at least every  
'amountToAllocateSecs' seconds to drain the internal buffer into your matrix  
'audiodata'. If you fail to call the function frequently enough, sound data will  
get lost!  
'minimumAmountToReturnSecs' optional minimum amount of recorded data to return  
at each call. The driver will only return control to your script when it was  
able to collect at least that amount of seconds of sound data - or if the  
capture engine was stopped. If you don't set this parameter, the driver will  
return immediately, giving you whatever amount of sound data was available -  
including an empty matrix if nothing was available.  
'maximumAmountToReturnSecs' allows you to optionally restrict the amount of  
returned sound data to a specific duration in seconds. By default, you'll get  
whatever is available.  
If you provide both, 'minimumAmountToReturnSecs' and 'maximumAmountToReturnSecs'  
and set them to equal values (but significantly lower than the  
'amountToAllocateSecs' buffersize!!) then you'll always get an 'audiodata'  
matrix back that is of a fixed size. This may be convenient for postprocessing  
in the scripting language. It may also reduce or avoid memory fragmentation...  
'singleType' if set to 1 will return a sound data matrix of single() type  
instead of double() type. By default, double() type is returned. single() type  
matrices only consume half as much memory as double() type matrices, without  
loss of audio precision for up to 24-Bit ADC hardware.  
  
  
### Optional return arguments other than 'audiodata':  
  
'absrecposition' is the absolute position (in samples) of the first column in  
the returned data matrix, assuming that sample zero was the very first recorded  
sample in this session. The count is reset each time you start a new capture  
session via call to [PsychPortAudio](PsychPortAudio)('Start').  
Each call to this function will return a new chunk of recorded sound data. The  
'absrecposition' provides you with absolute matrix column indices to stitch  
together the results of all calls into one seamless recording if you want.  
'overflow' if this flag is zero then everything went fine. If it is one then you  
didn't manage to call this function frequent enough, the capacity of the  
internal recording buffer was exceeded and therefore you lost captured sound  
data, i.e., there is a gap in your recording. When initially allocating the  
internal buffer, make sure to allocate it big enough so it is able to easily  
store all recorded data inbetween your calls to 'GetAudioData'. Example: You  
expect to call this routine once every second in your trial loop, then allocate  
a sound buffer of at least 2 seconds for some security headroom. If you know  
that the recording time of each recording has an upper bound then you can  
allocate an internal buffer of sufficient size and fetch the buffer all at once  
at the end of a recording.  
'cstarttime' this is an estimate of the system time (in seconds) when the very  
first sample of this recording was captured by the sound input of your hardware.  
This is only to be trusted down to the millisecond level after former careful  
calibration of your setup!  
  


###See also:
Open [GetDeviceSettings](PsychPortAudio-GetDeviceSettings) 
