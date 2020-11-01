# [BrightSideDisplay](BrightSideDisplay)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[BrightSideDisplay](BrightSideDisplay)

Psychtoolbox:[PsychHardware](PsychHardware):[BrightSideDisplay](BrightSideDisplay)  
  
Support files for interfacing Psychtoolbox-3 with the  
High Dynamic Range display device DR37-P or compatible  
devices from [BrightSide](BrightSide) Technologies.  
  
See http://www.brightsidetech.com  
  
NOTE: Deprecated and scheduled for removal. The company [BrightSide](BrightSide)  
      is dead since before the year 2010, and so are most likely  
      all DR37-P displays ever made. Therefore the code here is  
      almost certainly obsolete. Also, the driver mex file is no  
      longer bundled since many years, given it was only built  
      for 32-Bit Intel cpu's under [WindowsXP](WindowsXP) for 32-Bit Matlab.  
  
The driver consists of a high-level M-File "[BrightSideHDR](BrightSideHDR).m"  
which implements the user callable PTB interface and a low-  
level Matlab MEX file "[BrightSideCore](BrightSideCore).dll" that does the  
low level interfacing to [BrightSides](BrightSides) libraries.  
  
The runtime libraries and config files for your display  
need to be stored in the [BSRuntimeLibs](BSRuntimeLibs) subfolder. They  
are not included in Psychtoolbox, so you need to manually  
copy them from your [BrightSide](BrightSide) installation CD to that folder.  
  
Have a look at [SimpleHDRDemo](SimpleHDRDemo).m to see how simple it is to use the  
display with PTB, thanks to the new PTB built-in imaging pipeline.  
  
### Files:  
  
[BrightSideBasicDemo](BrightSideBasicDemo)   -- Basic demo to demonstrate use of the [BrightSide](BrightSide) display.  
  
[BrightSideHDR](BrightSideHDR).m       -- Psychtoolbox interface to the display.  
[BrightSideCore](BrightSideCore).m      -- Technical documentation for [BrightSideCore](BrightSideCore).mexw32.  
[BrightSideCore](BrightSideCore).cpp    -- C++ source code for [BrightSideCore](BrightSideCore).mexw32  
  
[BSRuntimeLibs](BSRuntimeLibs)/        -- Subfolder for runtime libraries and config.  
                         Empty by default. Needs to be filled with files that  
                         are bundled with the software for your display device.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/BrightSideDisplay/Contents.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/BrightSideDisplay/Contents.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/BrightSideDisplay/Contents.m</code>
</div>

{{category}}