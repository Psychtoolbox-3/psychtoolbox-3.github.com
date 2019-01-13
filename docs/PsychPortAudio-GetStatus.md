# [PsychPortAudio('GetStatus')](PsychPortAudio-GetStatus) 
##### [Psychtoolbox](Psychtoolbox)>[PsychPortAudio](PsychPortAudio).{mex*} subfunction

status = PsychPortAudio('GetStatus', pahandle);

Returns 'status', a struct with status information about the current state of  
device 'pahandle'.  
The struct contains the following fields:  
Active: Can be 1 if playback or recording is active, or 0 if playback/recording  
is stopped or not yet started.  
[RequestedStartTime](RequestedStartTime): Is the requested start time of the audio stream after start  
of playback/recording. [StartTime](StartTime): Is the real start time of the audio stream  
after start of playback/recording. If both, playback and recording are active  
(full-duplex mode), it is the start time of sound playback, ie an estimate of  
when the first sample hit the speakers. Same goes for pure playback.   
[CaptureStartTime](CaptureStartTime): Start time of audio capture (if any is active) - an estimate  
of when the first sound sample was captured. In pure capture mode, this is  
nearly identical to [StartTime](StartTime), but whenever playback is active, [StartTime](StartTime) and  
[CaptureStartTime](CaptureStartTime) will differ. [CaptureStartTime](CaptureStartTime) doesn't take the user provided  
'LatencyBias' into account.  
[RequestedStopTime](RequestedStopTime): The requested stop / sound offset time for playback of  
sounds, as selected via the 'stopTime' paramter in the 'Start',  
'RescheduleStart' or 'Stop' function. This will show a very large (~ infinite)  
value if no stop time has been sprecified.  
[EstimatedStopTime](EstimatedStopTime): Estimated time when sound playback has stopped. This is an  
estimate of when exactly the last audio sample will leave the speaker. The value  
is zero as long as the estimate isn't available. Due to the latency involved in  
sound playback, the value may become available a few msecs before or after  
actual sound offset.  
[CurrentStreamTime](CurrentStreamTime): Estimate of when the most recently submitted sample will hit  
the speaker. This corresponds roughly to 'PositionSecs' below, but in absolute  
realtime.  
[ElapsedOutSamples](ElapsedOutSamples): Total number of samples played out since start of playback.  
This count increments monotonically from start of playback to stop of playback.  
This denotes the absolute sample position that will hit the speaker at time  
'CurrentStreamTime'.   
[PositionSecs](PositionSecs) is an estimate of the current stream playback position in seconds  
within the current playback loop of the current buffer. it's not totally  
accurate, because it measures how much sound has been submitted to the sound  
system, not how much sound has left the speakers, i.e., it doesn't take driver  
and hardware latency into account.  
[SchedulePosition](SchedulePosition): Current position in a running schedule, if any.  
[XRuns](XRuns): Number of dropouts due to buffer overrun or underrun conditions. This is  
not perfectly reliable, as the algorithm can miss some dropouts. Iow.: A  
non-zero or increasing value means that audio glitches during playback or  
capture happened, but a zero or constant value doesn't mean everything was  
glitch-free, because some glitches can't get reliably detected on some operating  
systems or audio hardware.  
[TotalCalls](TotalCalls), [TimeFailed](TimeFailed) and [BufferSize](BufferSize) are only for debugging of [PsychPortAudio](PsychPortAudio)  
itself.  
[CPULoad](CPULoad): How much load does the playback engine impose on the CPU? Values can  
range from 0.0 = 0% to 1.0 for 100%. Values close to 1.0 indicate that your  
system can't handle the load and timing glitches or sound glitches are likely.  
In such a case, try to reduce the load on your system.  
[PredictedLatency](PredictedLatency): Is the latency in seconds of your driver+hardware combo. It  
tells you, how far ahead of time a sound device must be started ahead of the  
requested onset time via [PsychPortAudio](PsychPortAudio)('Start'...) to make sure it actually  
starts playing in time. High quality systems like Linux or [MacOS](MacOS)/X may allow  
values as low as 5 msecs or less on standard hardware. Other operating systems  
may require dozens or hundreds of milliseconds of headstart. Caution: In  
full-duplex mode, this value only refers to the latency on the sound output, not  
in the sound input! Also, this is just an estimate, not 100% reliable.  
[LatencyBias](LatencyBias): Is an additional bias setting you can impose via  
[PsychPortAudio](PsychPortAudio)('LatencyBias', pahandle, bias); in case our drivers estimate is a  
bit off. Allows fine-tuning.  
[SampleRate](SampleRate): Is the sampling rate for playback/recording in samples per second  
(Hz).  
[OutDeviceIndex](OutDeviceIndex): Is the deviceindex of the playback device, or -1 if not opened  
for playback. You can pass [OutDeviceIndex](OutDeviceIndex) to [PsychPortAudio](PsychPortAudio)('GetDevices', [],  
[OutDeviceIndex)](OutDeviceIndex)); to query information about the device.  
[InDeviceIndex](InDeviceIndex): Is the deviceindex of the capture device, or -1 if not opened for  
capture.  
[RecordedSecs](RecordedSecs): Is the total amount of recorded sound data (in seconds) since  
start of capture.  
[ReadSecs](ReadSecs): Is the total amount of sound data (in seconds) that has been fetched  
from the internal buffer. The difference between [RecordedSecs](RecordedSecs) and [ReadSecs](ReadSecs) is  
the amount of recorded sound data pending for retrieval.   


###See also:
Open [GetDeviceSettings](PsychPortAudio-GetDeviceSettings) 
