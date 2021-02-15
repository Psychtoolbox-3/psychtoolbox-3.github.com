# [MakeTextureTimingTest](MakeTextureTimingTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[MakeTextureTimingTest](MakeTextureTimingTest)([screenid=max][,width=1024][,height=1024][,channels=4][,nSamples=100][,preload=1][,specialFlags=0][,precision=0]);  
  
Test creation timing of a texture of specific 'width' x 'height' size with  
'channels' color channels (1=Luminance, 2=Luminance+Alpha, 3=RGB,  
4=RGBA). Also measure texture upload speed if 'preload==1' and drawing  
speed if 'preload==2'. Use 'specialFlags' for texture creation, most  
interestingly a value of 4 to use planar texture storage, which can be  
faster under some circumstances. Create textures of 'precision' - 0 = 8  
bit integer, -1 = 8 bit integer, but created from double() input instead  
of uint8 input, 1 = 16 bpc float or 16 bit signed integer as fallback, 2 =  
32 bpc float. Use 'nSamples' samples to compute mean timing.  
  
All parameters are optional: Defaults are width x height = 1024 x 1024,  
channels = 4 (RGBA), screenid = max id, 100 samples, preload but don't  
draw, standard storage, 8 bit uint input to 8 bit integer precision.  
  
Shows average duration.  
  
Each run creates a new texture via [Screen](Screen)('MakeTexture'), then preloads  
it onto the graphics card to measure that aspect as well, then deletes  
the texture again. This test will give you rather "worst case" or  
upper-bound numbers on texture management time. In many cases, processing  
of textures of similar size will be faster due to all kinds of internal  
optimizations. Your mileage may vary (TM), but it provides a rough  
impression at least.  
  
see also: [PsychTests](PsychTests)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/MakeTextureTimingTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/MakeTextureTimingTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/MakeTextureTimingTest.m</code>
</div>

