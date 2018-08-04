# [kPsychNeedFastBackingStore](kPsychNeedFastBackingStore)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

rval = kPsychNeedFastBackingStore  
  
Return a flag that you can pass to the 'imagingmode' parameter of  
[Screen](Screen)('OpenWindow') in order to request use of fast image buffers.  
  
If requested, Psychtoolbox will use an especially fast buffering scheme  
to implement Offscreen windows and to implement the dontclear=1 mode of  
[Screen](Screen)('[Flip](Flip)'). This can significantly speed up drawing if you use  
[Screen](Screen)('[Flip](Flip)') with dontclear=1 or if you make heavy use of Offscreen  
windows.  
  
It is part of the Psychtoolbox imaging pipeline and only works on modern  
graphics hardware, e.g., ATI Radeon 9600 and later, [NVidia](NVidia) [GeforceFX](GeforceFX) 5000  
and later. Check the www.psychtoolbox.org Wiki for graphics hardware  
recommendations and for a description of PTB's image processing  
capabilities. If you need to use older hardware, Offscreen windows will  
still work, but at a significantly lower speed.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/kPsychNeedFastBackingStore.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/kPsychNeedFastBackingStore.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/kPsychNeedFastBackingStore.m</code>
</div>

