# [PsychPortAudio('Stop')](PsychPortAudio-Stop) 
##### [Psychtoolbox](Psychtoolbox)>[PsychPortAudio](PsychPortAudio).{mex*} subfunction


Stop a [PortAudio](PortAudio) audio device. The 'pahandle' is the handle of the device to  
stop.  
'waitForEndOfPlayback' - If set to 1, this method will wait until playback of  
the audio stream finishes by itself. This only makes sense if you perform  
playback with a defined playback duration. The flag will be ignored when  
infinite repetition is requested (as playback would never stop by itself,  
resulting in a hang) and if no scheduled 'stopTime' has been set, either in this  
call or in the 'Start' function. The setting will be also ignored if this is a  
pure recording session.  
A setting of 0 (which is the default) requests stop of playback without waiting  
for all the sound to be finished playing. Sound may continue to be played back  
for multiple milliseconds after this call, as this is a polite request to the  
hardware to finish up.  
A setting of 2 requests abortion of playback and/or capture as soon as possible  
with your sound hardware, even if this creates audible artifacts etc. Abortion  
may or may not be faster than a normal stop, this depends on your specific  
hardware, but our driver tries as hard as possible to get the hardware to shut  
up. In a worst-case setting, the hardware would continue to playback the sound  
data that is stored in its internal buffers, so the latency for stopping sound  
would be the the same as the latency for starting sound as quickly as possible.  
E.g., a 2nd generation Intel [MacBook](MacBook) Pro seems to have a stop-delay of roughly  
5-6 msecs under optimal conditions (e.g., buffersize = 64, frequency=96000, OS/X  
10.4.10, no other sound apps running).  
A setting of 3 will not try to stop the playback now: You can use this setting  
if you just want to use this function to wait until playback stops by itself,  
e.g. because the set number of 'repetitions' or the set 'stopTime' has been  
reached. You can also use this to just change the 'repetitions' or 'stopTime'  
settings without waiting for anything.  
The optional parameter 'blockUntilStopped' defines if the subfunction should  
wait until sound processing has really stopped (at a setting of 1, which is the  
default), or if the function should return with minimal delay after only  
scheduling a stop at a zero setting. If 'waitForEndOfPlayback' is set to 1, then  
'blockUntilStopped' is meaningless and the function will always block until the  
stop is completed.  
The optional parameter 'stopTime' allows to set a defined system time when  
playback should stop by itself. Similar, the optional 'repetitions' setting  
allows to change the number of repetitions after which playback should stop by  
itself. These settings allow you to override the same settings made during a  
call to the 'Start' or 'RescheduleStart' function.  
The optional return argument 'startTime' returns an estimate of when the stopped  
stream actually started its playback and/or recording. Its the same timestamp as  
the one returned by the start command when executed in waiting mode.  
'endPositionSecs' is the final playback/recording position in seconds. 'xruns'  
is the number of buffer over- or underruns. This should be zero if the playback  
operation was glitch-free, however a zero value doesn't imply glitch free  
operation, as the glitch detection algorithm can miss some types of glitches.  
The optional return argument 'estStopTime' returns an estimate of when playback  
likely stopped.  
The return arguments are undefined if you set the 'blockUntilStopped' flag to  
zero.  
  


###See also:
Open [GetDeviceSettings](PsychPortAudio-GetDeviceSettings) 
