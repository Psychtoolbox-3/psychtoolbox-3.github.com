# [DatapixxToolbox](DatapixxToolbox)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[DatapixxToolbox](DatapixxToolbox)

[DatapixxToolbox](DatapixxToolbox)  
Version 0.9, Aug 2009  
  
The [DatapixxToolbox](DatapixxToolbox) is a set of MATLAB/Octave functions interfacing to  
the [DATAPixx](DATAPixx) hardware toolbox from [VPixx](VPixx) Technologies.  
  
See http://www.vpixx.com/datasheets/ds\_datapixx.pdf for more info.  
  
### [DATAPixx](DATAPixx) features:  
  
    \* Data acquisition and graphics system for the vision sciences  
    \* Receives DVI input from laptop or PC   
    \* Transmits dual synchronized VGA outputs with 16-bit video [DACs](DACs)  
    \* 16 channels of 16-bit analog inputs simultaneously sampled at up to  
      200 kHz per channel.  
    \* 4 channels of 16-bit analog outputs simultaneously updated at up to  
      1 [MHz](MHz) per channel.  
    \* Stereo audio inputs/outputs, sampled at up to 96 kHz.  
    \* 24 TTL inputs with timetagged transitions.  
    \* 24 TTL outputs  
    \* All digital/analog/audio output transitions can be initiated  
      with microsecond-precision to video refresh  
    \* All digital/analog/audio input acquisition can be correlated  
      with microsecond-precision to video refresh  
  
The [DatapixxToolbox](DatapixxToolbox) implements basic functionality in a single Mex file,  
and includes a set of demo M-Files in the [DatapixxDemos](DatapixxDemos) folder.  
  
For a complete list of available functions type "Datapixx" in the matlab  
command window.  
  
For an explanation of any particular Datapixx sub-function just add a  
question mark after a command, eg: Datapixx [SetDacSchedule](SetDacSchedule)?  
  
LINUX: If you want to use these functions without the need to run  
Matlab or Octave as root user (i.e., without need for root login or the  
sudo command), please copy the file ...  
Psychtoolbox/[PsychHardware](PsychHardware)/[DatapixxToolbox](DatapixxToolbox)/60-vpixx-permissions.rules  
... into the folder /etc/udev/rules.d/ on your system. This one time copy will  
require administrator privileges, but after that, any user should be able  
to use the Datapixx devices or other [VPixx](VPixx) devices without special permissions.  
  
Peter April  
email: papril@vpixx.com  
  
Copyright (c) 2009, [VPixx](VPixx) Technologies.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/DatapixxToolbox/Contents.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/DatapixxToolbox/Contents.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/DatapixxToolbox/Contents.m</code>
</div>

{{category}}