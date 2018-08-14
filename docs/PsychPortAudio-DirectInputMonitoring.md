# [PsychPortAudio('DirectInputMonitoring')](PsychPortAudio-DirectInputMonitoring) 
##### [Psychtoolbox](Psychtoolbox)>[PsychPortAudio](PsychPortAudio).{mex*} subfunction


Change the current settings for the "direct input monitoring" feature on device  
'pahandle'.  
The device must be open for this setting to take effect. Changed settings may or  
may not persist across closing and opening the device, this is hardware  
dependent and not to be relied on.  
So-called "Zero latency direct input monitoring" is a hardware feature of some  
modern (and usually higher end) soundcards. It allows to directly feed audio  
signals that are received at the audio input connectors of the soundcard back to  
the output connectors, without any extended intermediate processing of the audio  
signals by either the sound hardware or the host computer and its software. Due  
to this direct signal path, which only applies selectable amplification and some  
stereo panning and rerouting, the feedback latency from input to output (e.g,  
microphone to speakers) is as minimal as technically possible. On many high-end  
cards it is instantaneous!  
  
The 'enable' flag is mandatory: If set to zero, monitoring will be disabled for  
the given 'inputChannel'. A setting of one will enable input live-monitoring of  
the given 'inputChannel' to the given 'outputChannel' with the selected other  
settings.  
All following settings are optional and have reasonable defaults. Depending on  
your hardware, some or all of them may be silently ignored by your sound  
hardware.  
The optional 'inputChannel' argument specifies which input audio channels  
monitoring settings should be modified. If omitted or set to -1, all input  
channels settings will be modified, or at least tried to be modified.  
The optional 'outputChannel' specifies the index of the base-channel of a  
channel stereo-pair to which the 'inputChannel' should be routed. It must be an  
even number like 0, 2, 4, .... If omitted, channel 0, i.e., the first output  
channel stereo pair will be used. This at least on ASIO soundcards under  
MS-Windows.  
The optional 'gainLevel' defines the desired amplifier gain for the routed  
signal. The value should be negative for signal attenuation (i.e., negative  
gain) and positive for amplification (i.e., positive gain). As specification of  
gains is not standardized across operating systems, the numbers you'll have to  
pass in for a desired effect will vary across operating systems and audio  
hardware. However, the default setting of zero tries to set a neutral gain of  
zero decibel - the signal is passed through without change in intensity. On  
MS-Windows with ASIO soundcards, values between 0.0 and 1.0 will select gains  
between 0 and 12 dB. Values between 0.0 and -1.0 will select negative gains  
between 0 and -infinity dB, ie., full attenuation. The setting may get  
completely ignored or only approximately implemented by given hardware.  
Double-check your results!  
The optional 'stereoPan' parameter allows to select panning between the two  
output channels of a selected stereo output channel pair if the hardware allows  
that. Range 0.0 - 1.0 selects between left-channel and right channel, with the  
default of 0.5 selecting a centered output with equal distribution to both  
channels.  
  
In the optional return argument 'result' the function returns a status code to  
report if the requested change could be carried out successfully. A value of  
zero means success. A value of 1 means some error, e.g., invalid parameters  
specified. A value of 2 means that your combinatin of operating system, sound  
system, soundcard device driver and soundcard hardware does not support direct  
input monitoring, at least not for the given configuration. A setting of 3 means  
that your [PortAudio](PortAudio) driver plugin does not support the feature - You may need to  
update your plugin from the Psychtoolbox Wiki.  
  
The current [PsychPortAudio](PsychPortAudio) driver supports direct input monitoring on [MacOS](MacOS)/X  
with certain sound hardware (but not the builtin sound) and on Microsoft Windows  
systems with ASIO-2.0 capable sound hardware, and only if the latest  
portaudio\_x86.dll ASIO plugin is installed from our Wiki. Even then, only a  
subset of ASIO-2 hardware may support this feature and only a subset of these  
may support all parameters. According to vendor documentation, some soundcards  
from Creative Labs and many of RME's cards do support this feature.  
  
  


###See also:
Open [GetDeviceSettings](PsychPortAudio-GetDeviceSettings) 
