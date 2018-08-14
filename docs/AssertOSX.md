# [AssertOSX](AssertOSX)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

[AssertOSX](AssertOSX)  
  
OS X: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
Call [AssertOSX](AssertOSX) at the head of scripts which use functions unique to the  
OS X Psychtoolbox.  [AssertOSX](AssertOSX) will exit with an error if called from  
MATLAB running on any OS other than OS X, providing an explanation to  
users for why the script failed.  [AssertOSX](AssertOSX) also serves to document your  
code clearly as being specific to OS X.      
  
Use of OSX-specific Psychtoolbox functions is discouraged, though  
sometimes necessary.    
  
Note that Psychtoolbox functions which are unique to [OpenGL](OpenGL) are a  
different category than those unique to OS X.  Please use [AssertOpenGL](AssertOpenGL) in  
place of [AssertOSX](AssertOSX) if your script calls functions specific to [OpenGL](OpenGL) but  
none specific to OS X. [OpenGL](OpenGL)-specific Psychtoolbox functions are any  
of the following:  
      [Screen](Screen)('MakeTexture');   
      [Screen](Screen)('DrawTexture');  
      [Screen](Screen)('[Flip](Flip)');  
  
Some Psychtoolbox functions are unique to OS X because they exploit  
features in OS X not present in other operating systems, for example,  
the [MachPriority](MachPriority)\* functions underlying [Priority](Priority) in OS X. Generally, as  
with [Priority](Priority), there is a platform-neutral function overlalying the  
platform-specific functions.  Where available, you can use these to write  
platform-neutral scripts, unless for your purposes you must take  
advantage of features specific to the OS.  [PsychHID](PsychHID) is another such  
example.  It exists only for OS X but is overlayed by [KbCheck](KbCheck) and Gamepad  
(a.k.a. Joystick) which also exist on OS 9.  If you have an unusual USB  
HID device, you can read from it in OSX using [PsychHID](PsychHID), though compromising  
platform independence.    
  
Overview- New functions for OS X fall into one of these categories:  
 \* [OpenGL](OpenGL)-specific functions which are a permanent departure from earlier  
  Psychtoolboxes.  Call [IsOpenGL](IsOpenGL) or [AssertOpenGL](AssertOpenGL) if you use only these.   
 \* Functions which take advantage of features unique to a specific  
 operating system.  When possible, avoid these by using platform-neutral  
  overlay functions.   
 \* Remaining differences are a temporary failure to keep the OS 9,  
 Windows, and OS X Psychtoolboxes synchronized during the course of  
 development. The [AssertOSX](AssertOSX) script is itself an example of this; it has  
 not been ported back to OS 9 and Windows Psychtoolboxes yet.  
 Psychtoolbox help displays clear divisions denoting  
 platform-specificity.  In the case of not-yet-backported functions, these  
 divisions denote the actual currrent state of the Psychtoolbox, not its  
 intended design.    
  
 You can make your scripts and functions platform-neutral by testing the  
 OS version using MATLAB's "computer" command and conditionally executing  
 platform-specific calls.   
  
OS9: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[AssertOSX](AssertOSX) does not yet exist in OS 9.   
  
WIN: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[AssertOSX](AssertOSX) does not yet exist in Windows.  
  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
see also: [AssertOpenGL](AssertOpenGL), [IsOSX](IsOSX), computer  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/AssertOSX.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/AssertOSX.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/AssertOSX.m</code>
</div>

