# [ProceduralGaborDemo](ProceduralGaborDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[ProceduralGaborDemo](ProceduralGaborDemo)([benchmark=0][, nonsymmetric=0])  
  
This demo demonstrates fast drawing of Gabor patches via use procedural  
texture mapping. It only works on hardware with support for the GLSL  
shading language, vertex- and fragment-shaders.  
  
Gabors are not encoded into a texture, but instead a little algorithm - a  
procedural texture shader - is executed on the graphics processor (GPU).  
This is very fast and efficient! All parameters of the gabor patch can be  
set individually.  
  
By default - if the optional 'nonsymmetric' flag is not provided or set  
to zero - only symmetric circular gabors are drawn. If the flag is set to  
1 then gabors with an aspect ratio ~= 1, ie., elliptical gabors, are  
drawn as well. Restricting drawing to symmetric gabors allows for an  
additional speedup in drawing (about 15% on a [MacBookPro](MacBookPro) 2nd generation),  
so this may be interesting if you are in "need for speed(TM)".  
  
This demo is both, a speed benchmark, and a correctness test. If executed  
with the optional benchmark flag set to 2, it will execute a loop  
where it repeatedly draws a gabor patch both on the GPU (new style) and  
with Matlab code, then reads back and verifies the images, evaluating the  
maximum error between the old Matlab method and the new GPU method. The  
maximum error value and plotted error map are a means to assess if  
procedural shading works correctly on your setup and if the accuracy is  
sufficient for your purpose. In benchmark mode (flag set to 1), the gabor  
is drawn as fast as possible, testing the maximum rate at which your  
system can draw gabors.  
  
At a default setting of benchmark==0, it just shows nicely drawn gabor.  
  
Typical results on a [MacBookPro](MacBookPro) with Radeon X1600 under OS/X 10.4.11 are:  
Accuracy: Error wrt. Matlab reference code is 0.0005536900, i.e., about  
1 part in 2000, equivalent to a perfect display on a gfx-system with 11 bit   
DAC resolution. Note that errors scale with spatial frequency and  
absolute magnitude, so real-world errors are usually smaller for typical  
stimuli. This is just the error, given the settings hardcoded in this script.  
Typical speed is 2800 frames per second.  
  
The error on a Radeon HD 2400 XT is 0.0000842185, i.e., about 1 part in  
11000, equivalent to perfect display on a 13 bit DAC resolution gfx  
system.  
  
The error on a Radeon HD 5870 on OS/X 10.6 is 0.0000274425 units, about 15  
bits effective resolution, with a framerate of 8175 fps.  
  
Typical result on Intel Pentium IV, running on [WindowsXP](WindowsXP) with a [NVidia](NVidia)  
Geforce7800 and up-to-date drivers: Error is 0.0000146741 units, ie. one  
part in 68000, therefore display would be perfect even on a display device  
with 15 bit DAC's. The framerate is about 2344 frames per second.  
  
A Geforce 8800 on OS/X achieves about max error 0.0000207 units and  
a max fps of 3029 frames per second.  
  
Please note that results in performance and accuracy \*will\* vary,  
depending on the model of your graphics card, gfx-driver version and  
possibly operating system. For consistent results, always check before you  
measure on different setups! However, the more recent the graphics card,  
the faster and more accurate -- the latest generation of cards is  
supposed to be "just perfect" for vision research...  
  
If you want to draw many gabors per frame, you wouldn't do it like in this script,  
but use the batch-drawing version of [Screen](Screen)('DrawTextures', ...) instead,  
as demonstrated, e.g., in [DrawingSpeedTest](DrawingSpeedTest).m. That way you could submit  
the specs (parameters) of all gabors in one single matrix via one single  
[Screen](Screen)('DrawTextures'); call - this is more efficient and therefore extra  
fast!  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/ProceduralGaborDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/ProceduralGaborDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/ProceduralGaborDemo.m</code>
</div>

