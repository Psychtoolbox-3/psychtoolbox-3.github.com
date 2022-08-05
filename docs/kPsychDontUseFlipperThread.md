# [kPsychDontUseFlipperThread](kPsychDontUseFlipperThread)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

rval = kPsychDontUseFlipperThread  
  
This flag can be passed to the optional 'specialFlags' parameter of  
[Screen](Screen)('OpenWindow', ...) or [PsychImaging](PsychImaging)('OpenWindow', ...), and is  
used internally by [PsychImaging](PsychImaging) for some use-cases.  
  
It prevents conventional use of [Screen](Screen)'s internal background flipper thread  
and thereby disables all use-cases and functionality that requires the thread,  
e.g., some modes of fine-grained visual stimulus presentation timing via VRR,  
our own homegrown frame-sequential stereo modes (stereoMode 11), and the async  
flip function [Screen](Screen)('AsyncFlipBegin/Check/End').  
  
The flag will be often used for interoperation with external presentation  
backends, e.g., Virtual Reality / Augmented Reality / Mixed Reality runtimes  
like [OpenXR](OpenXR) for stimulus presentation by a VR compositor. Other applications  
are conceivable, but [OpenXR](OpenXR) is the initial target application of this flag.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/kPsychDontUseFlipperThread.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/kPsychDontUseFlipperThread.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/kPsychDontUseFlipperThread.m</code>
</div>

