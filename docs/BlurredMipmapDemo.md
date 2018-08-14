# [BlurredMipmapDemo](BlurredMipmapDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[BlurredMipmapDemo](BlurredMipmapDemo) - Show blurring of live video or movies via adaptive mipmapping.  
  
This demo shows how to selectively blur regions of a live video stream  
captured from an attached camera, or a live playing movie. The method  
employed here uses a GLSL shader to select an individual blur level for  
each output pixel. Pixels close to the mouse cursor (which simulates gaze  
position, e.g., as aquired by an eyetracker) will be drawn sharp, whereas  
pixels at larger radial distance will be drawn increasingly unsharp by  
low-pass filtering them.  
  
The method of blurring here is computationally efficient and fast,  
because it generates and uses a image resolution pyramid to precompute  
different versions of the video image at different resolutions. Then the  
shader just looks up color information for each individual output pixel  
from the proper "level of detail" in the pyramid of low pass filtered  
images. The resolution pyramid is auto-generated in a fast, GPU  
accelerated way for each image by use of [OpenGL](OpenGL) "mip-mapping". This  
method uses a fixed low-pass filter for downsampling, usually a box  
filter, but the exact type of filter used is system dependent and can  
vary across different graphics cards, graphics driver versions or  
operating systems.  
  
The demo requires recent graphics hardware and won't work on old graphics  
cards.  
  
### Usage:  
  
[BlurredMipmapDemo](BlurredMipmapDemo)([deviceIndexOrMoviename=0][, gazeRadius=25][, customMipmap=0])  
  
'gazeRadius' Some falloff radius in pixels. Controls how quickly the  
resolution degrades with increasing distance from the cursorposition.  
Smaller values give a smaller simulated "foveal area".  
  
'deviceIndexOrMoviename' = Optional: Either the index of the video  
capture device, or the full path to a movie file. Defaults to  
auto-selected default video source.  
  
'customMipmap' Optional: If non-zero, use a custom shader for  
downsampling during mipmap building, instead of the relatively simple  
builtin filter of the GPU.  
  
Press any key to finish the demo.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/BlurredMipmapDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/BlurredMipmapDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/BlurredMipmapDemo.m</code>
</div>

