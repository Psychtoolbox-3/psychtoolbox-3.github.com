# [Datapixx('SetMicrophoneSchedule')](Datapixx-SetMicrophoneSchedule) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

Datapixx('SetMicrophoneSchedule', scheduleOnset, scheduleRate, maxScheduleFrames [, lrMode=mono] [, bufferBaseAddress=20e6] [, numBufferFrames=maxScheduleFrames]);

Configure a schedule for audio input acquisition.  
-"scheduleOnset" is the desired delay (in double precision seconds) between  
schedule initiation, and the first audio sample acquisition.  
-"scheduleRate" is the rate at which successive audio samples are acquired. The  
value is given in samples/second, and must be in the range 8000-96000.  
Note that the audio input and audio output systems share timing resources, and  
must be configured to the same rate if running simultaneously. Specifically,  
[SetMicrophoneSchedule](SetMicrophoneSchedule) has a side effect of overwriting the audio output rate, to  
have the same value as that which is passed here.  
-"maxScheduleFrames" has two modes, depending on whether the acquisition dataset  
has a fixed known length. If the dataset length is known (eg: 100000 samples),  
then just pass 100000 to maxScheduleFrames. In this mode, once the audio  
acquisition schedule is started with [StartMicrophoneSchedule](StartMicrophoneSchedule), the schedule will  
terminate automatically when maxScheduleFrames has been acquired. If the dataset  
length is not known in advance, then pass 0 to maxScheduleFrames. In this mode,  
the acquisition will continue until the schedule is manually stopped using  
[StopMicrophoneSchedule](StopMicrophoneSchedule).  
-"lrMode" specifies how microphone Left/Right channels are stored to the  
acquisition schedule buffer. The following values are used:  
   0: MONO,   Average of Left/Right data is written to buffer  
   1: LEFT,   Only left data is written to buffer  
   2: RIGHT,  Only right data is written to buffer  
   3: STEREO, Left and Right data are both written to buffer  
If STEREO is selected, then 2 rows of data will be returned in  
[ReadMicrophoneBuffer](ReadMicrophoneBuffer).  
-"bufferBaseAddress" specifies the start of the RAM buffer which should hold the  
acquired data inside the Datapixx. Use [ReadMicrophoneBuffer](ReadMicrophoneBuffer) to upload the  
acquired data from this address after calling [StartMicrophoneSchedule](StartMicrophoneSchedule).  
-"numBufferFrames" specifies the desired size of the acquisition buffer in the  
Datapixx RAM. For many applications, the Datapixx has enough RAM to acquire a  
complete dataset without streaming. In these cases, numBufferFrames could be  
left at its default value of maxScheduleFrames. The Datapixx typically has 128  
MB of internal RAM which is shared between all I/O subsystems (DAC/ADC/AUDIO,  
etc). Datapixx('GetRamSize') can be used to query the quantity of RAM in your  
system. If maxScheduleFrames is larger than numBufferFrames (or 0), then each  
time the acquisition frame counter reaches a multiple of numBufferFrames, the  
acquisition buffer address automatically wraps back to bufferBaseAddress. This  
circular buffer effect can be used for acquiring arbitrarily long audio  
datasets. Simply monitor newBufferFrames returned by [GetMicrophoneStatus](GetMicrophoneStatus), and  
use [ReadMicrophoneBuffer](ReadMicrophoneBuffer) in streaming mode to upload newly acquired data from  
the Datapixx RAM to the host.  
Note that every call to [StartMicrophoneSchedule](StartMicrophoneSchedule) must be preceeded by a call to  
[SetMicrophoneSchedule](SetMicrophoneSchedule) (ie: multiple calls to [StartMicrophoneSchedule](StartMicrophoneSchedule) each  
require their own call to [SetMicrophoneSchedule)](SetMicrophoneSchedule)).  
See [DatapixxMicrophone](DatapixxMicrophone)\*Demo and [DatapixxAudioFeedbackDemo](DatapixxAudioFeedbackDemo) files for examples.  
  


###See also:
[InitAudio](Datapixx-InitAudio), [SetMicrophoneSource](Datapixx-SetMicrophoneSource), [GetMicrophoneGroupDelay](Datapixx-GetMicrophoneGroupDelay), [StartMicrophoneSchedule](Datapixx-StartMicrophoneSchedule), [StopMicrophoneSchedule](Datapixx-StopMicrophoneSchedule), [GetMicrophoneStatus](Datapixx-GetMicrophoneStatus), [ReadMicrophoneBuffer](Datapixx-ReadMicrophoneBuffer)
