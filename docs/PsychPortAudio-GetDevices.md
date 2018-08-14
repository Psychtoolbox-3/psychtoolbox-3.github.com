# [PsychPortAudio('GetDevices')](PsychPortAudio-GetDevices) 
##### [Psychtoolbox](Psychtoolbox)>[PsychPortAudio](PsychPortAudio).{mex*} subfunction


Returns 'devices', an array of structs, one struct for each available [PortAudio](PortAudio)  
device.  
  
If the optional parameter 'deviceIndex' is provided and the optional parameter  
'devicetype' is set to [], then only returns a single struct with information  
about the device with index 'deviceIndex'.  
  
Each struct contains information about its associated [PortAudio](PortAudio) device. The  
optional parameter 'devicetype' can be used to enumerate only devices of a  
specific class:   
1=Windows/[DirectSound](DirectSound), 2=Windows/MME, 3=Windows/ASIO, 11=Windows/WDMKS,  
13=Windows/WASAPI, 8=Linux/ALSA, 7=Linux/OSS, 12=Linux/JACK, 5=[MacOSX](MacOSX)/[CoreAudio](CoreAudio).  
  
On OS/X you'll usually only see devices for the [CoreAudio](CoreAudio) API, a first-class  
audio subsystem. On Linux you may have the choice between ALSA, JACK and OSS.  
ALSA or JACK provide very low latencies and very good timing, OSS is an older  
system which is less capable but not very widespread in use anymore. On  
MS-Windows you'll have the ''choice'' between up to 5 different audio  
subsystems: If you buy an expensive sound card with ASIO drivers, pick that API  
for low latency, it should give you comparable performance to OS/X or Linux. 2nd  
best choice would be WASAPI (on Windows-Vista) or WDMKS (on Windows-2000/XP) for  
ok latency on good days. [DirectSound](DirectSound) is the next worst choice if you have  
hardware with [DirectSound](DirectSound) support. If everything else fails, you'll be left with  
MME, a premium example of system misdesign successfully sold to paying  
customers.  


###See also:
Open [GetDeviceSettings](PsychPortAudio-GetDeviceSettings) 
