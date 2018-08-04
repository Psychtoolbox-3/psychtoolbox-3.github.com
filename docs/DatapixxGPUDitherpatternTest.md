# [DatapixxGPUDitherpatternTest](DatapixxGPUDitherpatternTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[DatapixxGPUDitherpatternTest](DatapixxGPUDitherpatternTest)([fullscreen=1])  
  
Low level diagnostic for GPU dithering via a [VPixx](VPixx)  
devices like Datapixx/[ViewPixx](ViewPixx)/Propixx, or a CRS  
device like the Bits\# - but \*not\* the original Bits+.  
  
Steps through all 256 grayscale levels and uses  
Datapixx et al. scanline readback to check what  
the GPU actually outputs. Plots it and prints  
the first 10 pixels of the topmost output scanline.  
  
This is meant to facilitate low-level diagnosis  
of GPU dithering bugs if our regular test script  
[BitsPlusIdentityClutTest](BitsPlusIdentityClutTest).m reports dithering trouble  
and can't fix the problem automatically.  
  
'fullscreen' Defaults to 1 for fullscreen windows.  
0 = Use a windowed window at top of screen for  
display to also diagnose possible compositor  
interference.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/DatapixxGPUDitherpatternTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/DatapixxGPUDitherpatternTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/DatapixxGPUDitherpatternTest.m</code>
</div>

