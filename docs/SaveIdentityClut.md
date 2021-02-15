# [SaveIdentityClut](SaveIdentityClut)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

savedClut = [SaveIdentityClut](SaveIdentityClut)(windowPtr [, LUT])  
  
This routine defines a LUT or LUT-type for use as identity gamma lookup  
table for applications that need such a table, e.g., Bits+ box,  
[VideoSwitcher](VideoSwitcher), Video attenuators, etc.  
  
It writes the LUT into a config file. The function [LoadIdentityClut](LoadIdentityClut)()  
will use the written LUT from that config file, if such a file exists.  
  
You can either pass a full blown LUT in the optional argument 'LUT', or  
you can pass a LUT id code (see codes and corresponding LUT's in the  
source code of [LoadIdentityClut](LoadIdentityClut).m). If you omit the argument, then the  
function will readout and store the current CLUT of the given display -  
in the hope that the current LUT is actually an identity CLUT.  
  
windowPtr is optional: It can be omitted, in which case the LUT of the  
screen with screenid = max([Screen](Screen)('Screens')) is used. It can be a  
screenid for the screen to read out, or it can be the window handle of an  
existing open onscreen window, in which case the screen corresponding to  
that window is used.  
  
In any case the type of operating system, graphics card vendor and model,  
as well as [OpenGL](OpenGL) version and [OpenGL](OpenGL) driver version and screenid is used  
to specify the configuration to which the LUT applies. This to  
disambiguate in case multiple different operating systems, os versions,  
GPU's or display types are used.  
  
The routine returns the stored clut in the optional return argument 'oldClut'.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/SaveIdentityClut.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/SaveIdentityClut.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/SaveIdentityClut.m</code>
</div>

