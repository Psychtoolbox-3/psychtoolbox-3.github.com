# [PsychPortAudio('GetDevices')](PsychPortAudio-GetDevices) 
##### [Psychtoolbox](Psychtoolbox)>[PsychPortAudio](PsychPortAudio).{mex*} subfunction

devices = PsychPortAudio('GetDevices' [, devicetype] [, deviceIndex]);

Returns 'devices', an array of structs, one struct for each available [PortAudio](PortAudio)  
device.  
  
If the optional parameter 'deviceIndex' is provided and the optional parameter  
'devicetype' is set to [], then only returns a single struct with information  
about the device with index 'deviceIndex'.  
  
Each struct contains information about its associated [PortAudio](PortAudio) device. The  
optional parameter 'devicetype' can be used to enumerate only devices of a  
specific class:   
1=Windows/[DirectSound](DirectSound), 2=Windows/MME, 11=Windows/WDMKS, 13=Windows/WASAPI,  
8=Linux/ALSA, 7=Linux/OSS, 12=Linux/JACK, probably 16=Linux/[PulseAudio](PulseAudio),  
5=[MacOSX](MacOSX)/[CoreAudio](CoreAudio).  
  
On macOS you'll usually only see devices for the [CoreAudio](CoreAudio) API, a first-class  
audio subsystem. On Linux you may have the choice between ALSA, JACK, [PulseAudio](PulseAudio)  
and OSS. ALSA or JACK provide very low latencies and very good timing, OSS is an  
older system which is less capable and not in widespread in use anymore. On  
MS-Windows you'll have the choice between multiple different audio subsystems:  
WASAPI (on Windows-Vista and later), or WDMKS (on Windows-2000/XP) should  
provide ok latency.  
[DirectSound](DirectSound) is the next worst choice if you have hardware with [DirectSound](DirectSound)  
support.  
If everything else fails, you'll be left with MME, a completely unusable API for  
precise or low latency timing. Current [PsychPortAudio](PsychPortAudio) only provides reasonably  
precise timing with WASAPI.  
  
  


###See also:
Open [GetDeviceSettings](PsychPortAudio-GetDeviceSettings) 
