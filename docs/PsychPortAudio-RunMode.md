# [PsychPortAudio('RunMode')](PsychPortAudio-RunMode) 
##### [Psychtoolbox](Psychtoolbox)>[PsychPortAudio](PsychPortAudio).{mex*} subfunction

oldRunMode = PsychPortAudio('RunMode', pahandle [,runMode]);

Set general run mode to 'runMode' and/or return old runMode for a device  
'pahandle'.  
The device must be open for this setting to take effect and playback must be  
stopped if one wants to change the setting. If playback isn't stopped, it will  
be forcefully stopped. Change of runMode is not supported on slave devices. The  
current/old runMode is returned in the optional return value 'oldRunMode'.  
'runMode' is the optional new runmode: At device open time, the runMode defaults  
to one. In mode zero, the audio hardware and all internal processing are  
completely stopped at end of audio playback. This reduces system ressource usage  
(both hardware and computation time), but may cause slightly longer latencies  
when re'Start'ing the device for playback of a different sound, e.g., a sequence  
of sounds. In 'runMode' 1, the audio hardware and processing don't shut down at  
the end of audio playback. Instead, everything remains active in a ''hot  
standby'' state. This allows to very quickly (with low latency) restart sound  
playback via the 'RescheduleStart' function. The downside is a permanent use of  
system ressources even if no sound is playing. Future runMode settings may  
provide more interesting options, stay tuned...  
  


###See also:
Start Stop [RescheduleStart](PsychPortAudio-RescheduleStart) 
