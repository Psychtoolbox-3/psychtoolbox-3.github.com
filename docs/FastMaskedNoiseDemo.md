# [FastMaskedNoiseDemo](FastMaskedNoiseDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[FastMaskedNoiseDemo](FastMaskedNoiseDemo)([numRects=1][, rectSize=128][, scale=1])  
  
Demonstrates how to generate and draw noise patches on-the-fly in a fast  
way. The patches are shown through circular apertures by the use of  
alpha-blending.  
  
numRects = Number of random patches to generate and draw per frame.  
  
rectSize = Size of the generated random noise image: rectSize by rectSize  
           pixels. This is also the size of the Psychtoolbox noise  
           texture.  
  
scale = Scalefactor to apply to texture during drawing: E.g. if you'd set  
scale = 2, then each noise pixel would be replicated to draw an image  
that is twice the width and height of the input noise image. In this  
demo, a nearest neighbour filter is applied, i.e., pixels are just  
replicated, not bilinearly filtered -- Important to preserve statistical  
independence of the random pixel values!  
  
If you play around with the parameters and compare performance to the  
[FastNoiseDemo](FastNoiseDemo), you will notice the following:  
  
- Scaling the stimulus to a bigger size is nearly free on modern graphics  
hardware, so you can generate low-resolution noise stimuli that still  
fill a huge fraction of your display area if you want.  
  
- Drawing the aperture is nearly free, i.e., this demo runs nearly as  
fast as the [FastNoiseDemo](FastNoiseDemo) without masking. This is because modern  
gfx-hardware is highly optimized for texture drawing and alpha blending.  
The aperture textures are cached in fast onboard VRAM memory to speed up  
drawing them.  
  
- The drawing speed is mostly limited by how fast Matlab can compute new  
random dot number matrices, not by properties of the stimulus images.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/FastMaskedNoiseDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/FastMaskedNoiseDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/FastMaskedNoiseDemo.m</code>
</div>

