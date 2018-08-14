# [InitializeMatlabOpenAL](InitializeMatlabOpenAL)
##### >[Psychtoolbox](Psychtoolbox)>[PsychSound](PsychSound)>[MOAL](MOAL)>[core](core)

[InitializeMatlabOpenAL](InitializeMatlabOpenAL)([debuglevel] [,snddevicename] [, openal\_c\_style])  
  
[InitializeMatlabOpenAL](InitializeMatlabOpenAL) -- Initialize the [OpenAL](OpenAL) for Matlab wrapper 'moal'.  
  
Call this function at the beginning of your experiment script if you intend  
to use low-level [OpenAL](OpenAL) sound commands in your script as provided by our  
moalcore extension.  
  
This will check if moal is properly installed and upload all required  
[OpenAL](OpenAL) constants into your Matlab workspace. It will also set up  
Psychtoolbox for interfacing with external [OpenAL](OpenAL) code.  
  
[MacOS](MacOS)/X users do not need to take any measures, [OpenAL](OpenAL) comes installed on  
Tiger (10.4) by default. The same is true for modern GNU/Linux distributions.  
  
Users of Microsoft Windows need to download and install the freely available  
[OpenAL](OpenAL) runtime for Windows. Follow the links to the runtime for Windows in  
the 'Downloads' section of the [OpenAL](OpenAL) homepage:  
  
http://www.openal.org  
  
Options: All options are optional.  
  
debuglevel = 0 to 3: Setting debuglevel == 0 will disable debug-output.  
A level of 1 will cause MOAL to output error messages and abort your  
scripts execution if it detects any [OpenAL](OpenAL) error. A level of 2 provides  
additional information that may help you to optimize your code. level 3  
means to be very verbose  
  
snddevicename: Optional. Request a specific sound output device by  
its name. If left out, or if an invalid name is given, [OpenAL](OpenAL) will  
select a default output device - the most capable and most efficient  
device in your system.  
  
openal\_c\_style = 0 / 1: Optional. If left out or set to zero, all   
constants will be loaded in structs in order to avoid cluttering the  
Matlab workspace too much. You'll have to replace all AL\_xxx calls by  
AL.xxx calls, e.g., AL\_TRUE becomes AL.TRUE .  
If set to one, then all constants will additionally be provided in standard  
C-Style syntax, aka AL\_TRUE, but this only works in the main function, not  
in subroutines.  
  
The 'OpenAL for Matlab' low level wrapper moal was implemented by Mario  
Kleiner, trivially derived from our MOGL Matlab for [OpenGL](OpenGL) wrapper, which  
was developed and contributed to Psychtoolbox under GPL license by  
Prof. Richard F. Murray, University of York, Canada and Mario Kleiner.  
  
MOAL is now licensed under the more permissive MIT license since 2011.  
Relicensing with permission of Richard Murray.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychSound/MOAL/core/InitializeMatlabOpenAL.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychSound/MOAL/core/InitializeMatlabOpenAL.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychSound/MOAL/core/InitializeMatlabOpenAL.m</code>
</div>

