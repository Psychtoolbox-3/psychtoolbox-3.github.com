# [DriftTexturePrecisionTest](DriftTexturePrecisionTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[DriftTexturePrecisionTest](DriftTexturePrecisionTest)([highprecision=0][, verbose=0][, filterMode=1])  
  
This test finds the minimum useful subtexel stepsize of the graphics hardwares  
texture coordinate interpolators. The minimum stepsize is the finest  
subpixel stepwidth that the gfx-hardware can resolve into an image in a  
meaningful way, e.g., for slow subpixel scrolling, drifting gratings and  
such.  
  
It draws an alternating black-white pattern, reads it back, then draws  
the pattern shifted by some small horizontal amount, reads it back and  
compares the two drawn images. If they are different then the hardware  
could resolve the subpixel increment into two different, properly shifted  
images via bilinear texture interpolation. If they are the same then the  
increment was too small to resolve for this hardware. The smallest  
stepsize is found in multiple iterations that reduce the stepsize until  
no difference is found anymore.  
  
The minimum resolvable stepsize for an ATI Mobility Radeon X1600 (e.g.,  
[MacBook](MacBook) Pro) is 1/64 th of a pixel, which corresponds to 6 bits subpixel  
accuracy.  
  
If the optional flag 'highprecision' is set to 1 or 2, then floating  
point textures are used, instead of integer textures with 8 bit  
resolution. 1 selects 16bpc float textures, 2 selects 32bpc float  
textures. A setting of 3 or 4 selects also 16bpc or 32bpc float textures,  
but additionally a special PTB GLSL interpolation shader is used instead  
of the hard-wired interpolator of your gfx chip. This is computationally  
more demanding and therefore slower, but it should provide higher  
precision and better resolution.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/DriftTexturePrecisionTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/DriftTexturePrecisionTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/DriftTexturePrecisionTest.m</code>
</div>

