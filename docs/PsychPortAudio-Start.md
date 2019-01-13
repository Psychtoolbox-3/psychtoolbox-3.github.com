# [PsychPortAudio('Start')](PsychPortAudio-Start) 
##### [Psychtoolbox](Psychtoolbox)>[PsychPortAudio](PsychPortAudio).{mex*} subfunction

startTime = PsychPortAudio('Start', pahandle [, repetitions=1] [, when=0] [, waitForStart=0] [, stopTime=inf] [, resume=0]);

Start a [PortAudio](PortAudio) audio device. The 'pahandle' is the handle of the device to  
start. Starting a device means: Start playback of output devices, start  
recording on capture device, do both on full duplex devices. 'waitForStart' if  
set to 1 will wait until device has really started, default is to continue  
immediately, ie. only schedule start of device. 'when' Requested time, when  
device should start. Defaults to zero, i.e. start immediately. If set to a  
non-zero system time, PTB will do its best to start the device at the requested  
time, but the accuracy of start depends on the operating system, audio hardware  
and system load. If 'waitForStart' is set to non-zero value, ie if PTB should  
wait for sound onset, then the optional return argument 'startTime' will contain  
an estimate of when the first audio sample hit the speakers, i.e., the real  
start time.  
Please note that the 'when' value always refers to playback, so it defines the  
starttime of playback. The start time of capture is related to the start time of  
playback in duplex mode, but it isn't the same. In pure capture mode (without  
playback), 'when' will be ignored and capture always starts immediately. See the  
help for subfunction 'GetStatus' for more info on the meaning of the different  
timestamps.  
The 'repetitions' parameter defines how often the playback of the sound data  
should be repeated. A setting of zero will cause infinite repetitions, ie.,  
until manually stopped via the 'Stop' subfunction. A positive setting will cause  
the provided number of repetitions to happen. The default setting is 1, ie.,  
play exactly once, then stop. Fractional values are allowed, e.g, 1.5 for one  
and a half repetition.  
The optional parameter 'stopTime' allows to set a specific system time when  
sound playback should stop by itself at latest, regardless if the requested  
number of 'repetitions' has completed. PTB will do its best to stop sound at  
exactly that time, see comments about the 'when' parameter - The same mechanism  
is used, with the same restrictions.  
The optional parameter 'resume' if set to 1, allows to resume playback at the  
position it was last stopped, instead of starting at the beginning again. By  
default, playback starts at the beginning.  
  


###See also:
Open
