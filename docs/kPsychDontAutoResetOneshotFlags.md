# [kPsychDontAutoResetOneshotFlags](kPsychDontAutoResetOneshotFlags)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

rval = kPsychDontAutoResetOneshotFlags  
  
Return a flag that you can pass as part of the flipFlags for a call to  
[Screen](Screen)('Hookfunction', windowPtr, 'SetOneshotFlipFlags', flipFlags);  
  
This flag will prevent the one-shot flip flags from being automatically cleared  
after execution of the next [Screen](Screen)('[Flip](Flip)') operation. E.g., flags that won't  
get cleared after [Flip](Flip) are kPsychSkipWaitForFlipOnce, kPsychSkipSwapForFlipOnce,  
kPsychSkipTimestampingForFlipOnce, kPsychSkipVsyncForFlipOnce.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/kPsychDontAutoResetOneshotFlags.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/kPsychDontAutoResetOneshotFlags.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/kPsychDontAutoResetOneshotFlags.m</code>
</div>

