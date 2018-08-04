# [BrightSideDisplay](BrightSideDisplay)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[BrightSideDisplay](BrightSideDisplay)

Psychtoolbox:[PsychHardware](PsychHardware):[BrightSideDisplay](BrightSideDisplay)  
  
Support files for interfacing Psychtoolbox-3 with the  
High Dynamic Range display device DR37-P or compatible  
devices from [BrightSide](BrightSide) Technologies.  
  
See http://www.brightsidetech.com  
  
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
  
[SimpleHDRDemo](SimpleHDRDemo).m       -- Simple demo to demonstrate use of [BrightSide](BrightSide)-HDR with  
                         Psychtoolbox.  
  
[ShowHDRDemo](ShowHDRDemo).m         -- Less simple demo to demonstrate use of these functions.  
  
[HDRViewer](HDRViewer).m           -- An interactive viewer for HDR images, including  
                         zoom function.  
  
[BrightSideHDR](BrightSideHDR).m       -- Psychtoolbox interface to the display.  
[BrightSideCore](BrightSideCore).dll    -- Matlab MEX interface, used by [BrightSideHDR](BrightSideHDR).  
[BrightSideCore](BrightSideCore).m      -- Technical documentation for [BrightSideCore](BrightSideCore).dll.  
[BrightSideCore](BrightSideCore).cpp    -- C++ source code for [BrightSideCore](BrightSideCore).dll.  
  
[BSRuntimeLibs](BSRuntimeLibs)/        -- Subfolder for runtime libraries and config.  
                         Empty by default. Needs to be filled with files that  
                         are bundled with the software for your display device.  
  
[HDRRead](HDRRead).m             -- Generic HDR image reader. Dispatches into helper  
                         routines for different file formats.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/BrightSideDisplay/Contents.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/BrightSideDisplay/Contents.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/BrightSideDisplay/Contents.m</code>
</div>

{{category}}