# [FastFilteredNoiseDemo](FastFilteredNoiseDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[FastFilteredNoiseDemo](FastFilteredNoiseDemo)([validate=1][, filtertype=1][, rectSize=128][, kwidth=5][, scale=1][, syncToVBL=1][, dontclear=0])  
  
Demonstrates how to generate, filter and draw noise patches on-the-fly   
in a fast way by use of GLSL fragment shaders.  
Use it to benchmark your system by varying the load. If you like this demo  
then also have a look at [FastMaskedNoiseDemo](FastMaskedNoiseDemo) that shows how to  
efficiently draw a masked stimulus by use of alpha-blending.  
  
filtertype = Type of filter to apply, see switch statement below for  
supported filters. Zero selects no filtering, 1 is Gaussian blur.  
  
rectSize = Size of the generated random noise image: rectSize by rectSize  
           pixels. This is also the size of the Psychtoolbox noise  
           texture.  
  
kwidth = For filters which support a varying kernel size, the kernel  
size. Will create a kwidth x kwidth convolution kernel.  
  
scale = Scalefactor to apply to texture during drawing: E.g. if you'd set  
scale = 2, then each noise pixel would be replicated to draw an image  
that is twice the width and height of the input noise image. In this  
demo, a nearest neighbour filter is applied, i.e., pixels are just  
replicated, not bilinearly filtered -- Important to preserve statistical  
independence of the random pixel values!  
  
syncToVBL = 1=Synchronize bufferswaps to retrace. 0=Swap immediately when  
drawing is finished. Value zero is useful for benchmarking the whole  
system, because your measured framerate will not be limited by the  
monitor refresh rate -- Gives you a feeling of how much headroom is left  
in your loop.  
  
dontclear = If set to 1 then the backbuffer is not automatically cleared  
to background color after a flip. Can save up to 1 millisecond on old  
graphics hardware.  
  
Example results on a Intel Pentium-4 3.2 Ghz machine with a [NVidia](NVidia)  
[GeForce](GeForce) 7800 GTX graphics card, running under M$-Windows XP SP3:  
  
Two patches, 256 by 256 noise pixels each, scaled by any factor between 1  
and 5 yields a redraw rate of 100 Hz.  
  
One patch, 256 by 256 noise pixels, scaled by any factor between 1  
and 5 yields a redraw rate of 196 Hz.  
  
Two patches, 128 by 128 noise pixels each, scaled by any factor between 1  
and 5 yields a redraw rate of 360 - 380 Hz.  
  
One patch, 128 by 128 noise pixels, scaled by any factor between 1  
and 5 yields a redraw rate of 670 Hz.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/FastFilteredNoiseDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/FastFilteredNoiseDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/FastFilteredNoiseDemo.m</code>
</div>

