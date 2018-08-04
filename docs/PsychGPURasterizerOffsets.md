# [PsychGPURasterizerOffsets](PsychGPURasterizerOffsets)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)

[PsychGPURasterizerOffsets](PsychGPURasterizerOffsets) - Test GPU drivers for spatial misplacement of content.  
  
The function tests if the GPU places content where it is told  
to place it. It warns if this isn't the case and returns corrective  
offsets to compensate for the problem.  
  
Different postioning methods are tested and potentially different  
offsets are reported for the different methods.  
  
Input args:  
'win' Window handle to open onscreen window.  
'drivername' driver name string to prefix to output messages.  
  
Returns args: (x,y) offsets created by driver inaccuracy. You will need  
to apply the negation of these to correct for driver misplacement!  
  
(rpfx, rpfy) Corrective offsets for glRasterPos2f()  
(rpix, rpiy) Corrective offsets for glRasterPos2i()  
(vix, viy) Corrective offsets for glVertex2i()  
(vfx, vfy) Corrective offsets for glVertex2f()  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/PsychGPURasterizerOffsets.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/PsychGPURasterizerOffsets.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/PsychGPURasterizerOffsets.m</code>
</div>

