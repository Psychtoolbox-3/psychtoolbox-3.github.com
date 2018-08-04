# [PsychPortAudio('RescheduleStart')](PsychPortAudio-RescheduleStart) 
##### [Psychtoolbox](Psychtoolbox)>[PsychPortAudio](PsychPortAudio).{mex*} subfunction


Modify requested start time 'when' of an already started [PortAudio](PortAudio) audio device.  
After you've started an audio device via the 'Start' subfunction, but \*before\*  
the device has really started playback (because the 'when' time provided to the  
'Start' method is still far in the future), you can use this function to  
reschedule the start for a different 'when' time - including a value of zero for  
immediate start.  
  
The 'pahandle' is the handle of the device to start. Starting a device means:  
Start playback of output devices, start recording on capture device, do both on  
full duplex devices. 'waitForStart' if set to 1 will wait until device has  
really started, default is to continue immediately, ie. only schedule start of  
device. 'when' Requested time, when device should start. Defaults to zero, i.e.  
start immediately. If set to a non-zero system time, PTB will do its best to  
start the device at the requested time, but the accuracy of start depends on the  
operating system, audio hardware and system load. If 'waitForStart' is set to  
non-zero value, ie if PTB should wait for sound onset, then the optional return  
argument 'startTime' will contain an estimate of when the first audio sample hit  
the speakers, i.e., the real start time.  
Please note that the 'when' value always refers to playback, so it defines the  
starttime of playback. The start time of capture is related to the start time of  
playback in duplex mode, but it isn't the same. In pure capture mode (without  
playback), 'when' will be ignored and capture always starts immediately. See the  
help for subfunction 'GetStatus' for more info on the meaning of the different  
timestamps.  
The 'repetitions' parameter will change the number of playback repetitions if  
provided. The value for 'repetitions' from the [PsychPortAudio](PsychPortAudio)('Start') function  
will be used if the parameter is omitted. See explanation in the 'Start'  
function for its meaning.  
'stopTime' is an optional override for the 'stopTime' parameter from the 'Start'  
function, see explanations there.  
  


###See also:
Open
