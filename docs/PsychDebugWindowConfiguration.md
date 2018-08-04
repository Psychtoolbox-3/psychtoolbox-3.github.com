# [PsychDebugWindowConfiguration](PsychDebugWindowConfiguration)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

Switch PTB's onscreen window into a display mode suitable for easy debugging on single-screen setups.  
  
This function allows to setup [Screen](Screen) onscreen windows to be  
partially transparent, so one can simultaneously see the stimulus display and  
the Matlab window and other GUI windows.  
  
Usage: [PsychDebugWindowConfiguration](PsychDebugWindowConfiguration)([opaqueForHID=0][, opacity=0.5])  
  
To enable: Call [PsychDebugWindowConfiguration](PsychDebugWindowConfiguration) before the [Screen](Screen)('OpenWindow',...) call!  
To disable: Type "clear [Screen](Screen)" or "clear all".  
  
The optional parameter 'opaqueForHID' if set to a non-zero value will  
disallow mouse clicks and other mouse actions to "get through" to the  
GUI, ie., it will make the onscreen window opaque to the mouse pointer.  
  
A setting of -1 will disable the transparency again, but \*keep all timing tests  
and timestamping disabled\*.  
  
The optional parameter 'opacity' controls how opaque the onscreen window  
is, in a range of 0.0 to 1.0 for 0% to 100% opacity. By default the  
window is 50% opaque (or 50% transparent if you like).  
  
Stimulus onset timing and timestamping will be inaccurate in this mode  
and graphics performance will be reduced! Don't use for timing tests or  
during real experiment sessions!  
  
This feature will only work reliably - or at all - if your operating  
system is running with a compositing window manager installed and  
enabled. This is the case for Windows Vista, Windows-7/8 and later MS  
operating systems, as well as [MacOS](MacOS)/X, and most GNU/Linux distributions  
which have a compositing desktop installed and enabled, e.g., KDE,  
GNOME-2/3, Compiz, Unity.  
  
Keyboard and mouse input may not work as expected under all conditions,  
i.e., it may by impaired in either Psychtoolbox, or for the other running  
applications. Good luck!  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/PsychDebugWindowConfiguration.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/PsychDebugWindowConfiguration.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/PsychDebugWindowConfiguration.m</code>
</div>

