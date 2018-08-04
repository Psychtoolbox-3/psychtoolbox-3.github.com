# [BrightSideCore](BrightSideCore)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[BrightSideDisplay](BrightSideDisplay)

[BrightSideCore](BrightSideCore) -- Matlab MEX file for low-level interfacing with  
[BrightSide](BrightSide) technologies HDR display controller library.  
  
Don't call this file directly, but use the user friendly [BrightSideHDR](BrightSideHDR)()  
command instead!!  
  
### Low-Level command codes:  
  
[BrightSideCore](BrightSideCore)(0, configpath, configfile);  
- Initialize core, read config file 'configfile' located in path  
'configpath'.  
  
[BrightSideCore](BrightSideCore)(1);  
- Shut down brightside system, release all ressources.  
  
[BrightSideCore](BrightSideCore)(2);  
- Convert HDR image content of input texture to an image suitable for  
driving the HDR display, blit it into the real LDR framebuffer.  
  
[BrightSideCore](BrightSideCore)(3, texid, fboid);  
- Change source texture to 'texid' and target framebuffer to 'fboid' for conversion.  
  
[BrightSideCore](BrightSideCore)(4, ledintensity);  
- Change output multiplication factor for intensity of the LED array.  
  
[BrightSideCore](BrightSideCore)(5, clampingenabled);  
- Enable or disable clamping of colors in the [OpenGL](OpenGL) pipeline, depending  
if 'clampingenabled' is 1 or 0. 0 == Disable clamping is what one usually  
wants for drawing of HDR content.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/BrightSideDisplay/BrightSideCore.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/BrightSideDisplay/BrightSideCore.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/BrightSideDisplay/BrightSideCore.m</code>
</div>

