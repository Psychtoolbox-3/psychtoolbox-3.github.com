# [AssertOpenGL](AssertOpenGL)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

[AssertOpenGL](AssertOpenGL)  
  
Break and issue an error message if the installed Psychtoolbox is not  
based on [OpenGL](OpenGL) or [Screen](Screen)() is not working properly.  
To date there are four versions of the Psychtoolbox, each based on a  
different graphics library:  
  
 OS9: Psychtoolbox-2, based on Apple's [QuickDraw](QuickDraw).  
 Win: Psychtoolbox-2, based on Direct X and GDI.  
 Win: [OpenGL](OpenGL) for the ported OSX-Psychtoolbox, aka Psychtoolbox-3.  
 OSX: [OpenGL](OpenGL) for Psychtoolbox-3.  
 Linux: [OpenGL](OpenGL) for Psychtoolbox-3.  
  
 The Psychtoolboxes based on [OpenGL](OpenGL) are partially incompatible (see below)  
 with previous Psychtoolboxes.  A script which relies on the [OpenGL](OpenGL)  
 Psychtoolbox should call [AssertOpenGL](AssertOpenGL) so that it will issue the  
 appropriate warning if a user tries to run it on a computer with a  
 non-[OpenGL](OpenGL) based Psychtoolbox installed.  
  
 [OpenGL](OpenGL)-based Psychtoolboxes are distinguised by the availability of these  
 functions:  
  
  [Screen](Screen)('[Flip](Flip)',...);  
  [Screen](Screen)('MakeTexture');  
  [Screen](Screen)('DrawTexture');  
  
  
 If you know you're using Psychtoolbox-3, then the most likely cause for  
 this error message is a problem in the configuration of your  
 Matlab/Octave + System setup, or in the Psychtoolbox installation.  
  
 Typically either the [Screen](Screen) MEX file can't be found or accessed, due to  
 some wrong Matlab/Octave path (Proper [Screen](Screen) file not in path), or due  
 to some permission issue (insufficient security access permissions -  
 typically found on MS-Windows systems), or the [Screen](Screen) MEX file can't be  
 loaded and initialized due to some missing or wrong system library on  
 your machine, e.g., the C runtime library is of an incompatible type.  
 Simply type the command "[Screen](Screen)" at the prompt to see if this may be an  
 issue.  
  
 In both cases, indicated by some "file not found" or "file could not by  
 accesses" or "invalid MEX file" error message, you may want to run the  
 [SetupPsychtoolbox](SetupPsychtoolbox) command again. This will either fix the problem for  
 you by reconfiguring Psychtoolbox, or it will provide more diagnostic  
 error and troubleshooting messages. Make also sure that you read the  
 troubleshooting tips in the "Download" and "Frequently asked questions"  
 sections of our Psychtoolbox Wiki at http://www.psychtoolbox.org  
  
See also: [IsOSX](IsOSX), [IsWin](IsWin), [IsLinux](IsLinux).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/AssertOpenGL.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/AssertOpenGL.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/AssertOpenGL.m</code>
</div>

