# [AppleVersion](AppleVersion)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

versionString=[AppleVersion](AppleVersion)(gestaltString)  
  
WARNING: This function is deprecated and will likely cease to work  
in a future Psychtoolbox release. This is due to Apple deprecating  
their [Gestalt](Gestalt)() function from their operating system. While [Gestalt](Gestalt),  
and thereby this function, still works on OSX 10.10, no guarantees  
can be made about future OSX versions.  
  
Adapt your code accordingly to do without this function.  
  
OS 9 and OS X: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[AppleVersion](AppleVersion)('qtim') % [QuickTime](QuickTime)  
[AppleVersion](AppleVersion)('atkv') % [AppleTalk](AppleTalk)  
Uses [Gestalt](Gestalt) to retrieve Apple version information and returns a string.  
Apple has a "standard" format for versions, e.g. 3.0f7 or 8.0.1, that  
they use for some of their software components. APPLEVERSION uses GESTALT  
to retrieve the information. However, this is only useful for the few  
[Gestalt](Gestalt) selectors that return information in this "standard" format.  
If the selector is undefined (possibly because that software is  
not present) APPLEVERSION returns an empty string.  
  
WINDOWS: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[AppleVersion](AppleVersion) does not exist in Windows.  
  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
see also: [Gestalt](Gestalt), [Screen](Screen)('Computer?'), [MacModelName](MacModelName)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/AppleVersion.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/AppleVersion.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/AppleVersion.m</code>
</div>

