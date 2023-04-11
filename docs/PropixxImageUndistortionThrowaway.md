# [PropixxImageUndistortionThrowaway](PropixxImageUndistortionThrowaway)
##### >[Psychtoolbox](Psychtoolbox)>[PsychAlpha](PsychAlpha)

[PropixxImageUndistortionThrowaway](PropixxImageUndistortionThrowaway)(calibfilename [, flipmethod=0][, corrmethod=0][, imagefilename])  
  
A preliminary throwaway demo of how to use [PropPixx](PropPixx) in fast 4x or 12x  
display mode. This demo is EXPERIMENTAL and subject to change  
without warning, potentially even removal, in future Psychtoolbox  
releases. Make a private copy of it and the [PsychProPixx](PsychProPixx).m file  
if you want to keep it as is for production use!  
  
You will need a powerful, fast graphics card and a well configured  
operating system and machine for this to work reliably at 12x mode.  
  
The demo can be stopped via the ESCAPE key.  
  
### Parameters and their meaning:  
  
'calibfilename' mandatory name of a display geometry calibration file  
created via [DisplayUndistortionBVL](DisplayUndistortionBVL)() iff corrmethod is \>= 0.  
  
flipmethod = 0 -\> Sync flips. [ Slow but easy ]  
flipmethod = 1 -\> Async flips for some sort of triplebuffering. [ Potentially faster but more difficult ]  
flipmethod = 2 -\> Fastest method, but only available on Linux with open-source graphics drivers.  
  
corrmethod = -1 -\> No correction.  
corrmethod = 0  -\> Global correction for whole image. [Fastest and default]  
corrmethod = 1  -\> Separate correction for each quadrant.  
  
'imagefilename' optional name of image file to display - see code.  
  
### Performance/Stability tips:  
  
On Linux with the open-source graphics drivers, flipmethod 2 will  
increase stability due to the ability to do non-blocking but still  
vsynced flips without the overhead of [AsyncFlipBegin](AsyncFlipBegin) et al.  
  
On Linux with the proprietary [NVidia](NVidia) graphics driver, or on macOS or Windows,  
where you can't use flipmethod 2, flipmethod 1 for use of 'AsyncFlipBegin'  
flips should get you a bit of extra stability if you are lucky, although not  
as good as flipmethod 2 with Linux + FOSS drivers.  
  
On Linux with proprietary [NVidia](NVidia) driver, or on Windows, you may be able to  
get a bit more stability if your graphics driver supports triplebuffering.  
However, time stamping and other correctness tests wouldn't work anymore,  
so you'd need some other means to verify timing.  
  
Another method to get reliability and proper timestamping on any  
operating system without much tweaking or configuration is of course  
to simply buy the fastest graphics card money can buy and then make  
your stimuli simple enough so it can cope with them.  
  
In general, your graphics card must be able to do all processing within  
much less than 8.33 msecs for Propixx fast modes to work, so reasonable  
stimulus design and a fast graphics card is important. Above special  
flipmethod's or the use of properly setup Linux can buy you a few msecs  
of extra safety margin to compensate for occassional timing glitches, ie.,  
if the graphics card occassionally overshoots its 8.3 msecs budget, but is  
capable of meeting it on average - in such cases those tricks help.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychAlpha/PropixxImageUndistortionThrowaway.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychAlpha/PropixxImageUndistortionThrowaway.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychAlpha/PropixxImageUndistortionThrowaway.m</code>
</div>

