# [kPsychSkipSwapForFlipOnce](kPsychSkipSwapForFlipOnce)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

rval = kPsychSkipSwapForFlipOnce  
  
Return a flag that you can pass as part of the flipFlags for a call to  
[Screen](Screen)('Hookfunction', windowPtr, 'SetOneshotFlipFlags', flipFlags);  
  
This flag will disable the actual visual stimulus presentation to  
the onscreen window via [OpenGL](OpenGL) double-buffer swap during execution  
of the next [Screen](Screen)('[Flip](Flip)') operation, ergo also any timestamping and  
wait for swap completion. It will go through all the moves, post-  
processing the stimulus, computing the final image, and most post-flip  
operations, but the results of this work will not be shown as a visual  
update to the onscreen window.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/kPsychSkipSwapForFlipOnce.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/kPsychSkipSwapForFlipOnce.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/kPsychSkipSwapForFlipOnce.m</code>
</div>

