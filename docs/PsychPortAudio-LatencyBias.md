# [PsychPortAudio('LatencyBias')](PsychPortAudio-LatencyBias) 
##### [Psychtoolbox](Psychtoolbox)>[PsychPortAudio](PsychPortAudio).{mex*} subfunction

oldbias = PsychPortAudio('LatencyBias', pahandle [,biasSecs]);

Set audio output latency bias in seconds to 'biasSecs' and/or return old bias  
for a device 'pahandle'. The device must be open for this setting to take  
effect. It is reset to zero at each reopening of the device. [PsychPortAudio](PsychPortAudio)  
computes a latency value for the expected latency of an audio output device to  
get its timing right. If this latency value is slightly off for some reason, you  
can provide a bias value with this function to correct the computed value.  
  
Please note that this 'biasSecs' setting is applied to either audio playback or  
audio capture if your device is configured in simplex mode, either for playback  
\*or\* capture. If your device is opened in full-duplex mode for simultaneous  
capture and playback, then the bias value is only applied to the playback timing  
and timestamps, but not to the capture timing and timestamps!  
  
See the online help for [PsychPortAudio](PsychPortAudio) for more in depth explanation of  
latencies.   


###See also:
Open [GetDeviceSettings](PsychPortAudio-GetDeviceSettings) 
