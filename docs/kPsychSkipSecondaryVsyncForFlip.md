# [kPsychSkipSecondaryVsyncForFlip](kPsychSkipSecondaryVsyncForFlip)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

rval = kPsychSkipSecondaryVsyncForFlip  
  
This flag can be passed to the optional 'specialFlags' parameter of  
[Screen](Screen)('OpenWindow', ...) or [PsychImaging](PsychImaging)('OpenWindow', ...).  
  
This flag will disable synchronization of [OpenGL](OpenGL) bufferswaps of a potential  
secondary / slave window to vertical blank ("VBLANK" / "VSYNC"). Such windows  
are used for the right-eye view in stereomode 10 (dual window stereo), special  
dual-window display modes, and for display mirroring/cloning with the [PsychImaging](PsychImaging)  
task 'MirrorDisplayTo2ndOutputHead', which provides a copy of the visual stimulus  
image presented to the subject also to a secondary window / display for the  
experimenter.  
  
Especially for this latter use case of display mirroring to an experimenter  
control monitor, one usually wants to skip vsync and accept degraded image  
quality / tearing, because tearing doesn't matter much for a simple control  
display, but disabling vsync prevents throttling of the main subject stimulus  
display to the potentially lower video refresh rate of a cheaper/lower-end  
experimenter display.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/kPsychSkipSecondaryVsyncForFlip.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/kPsychSkipSecondaryVsyncForFlip.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/kPsychSkipSecondaryVsyncForFlip.m</code>
</div>

