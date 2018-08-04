# [ProceduralNoiseDemo](ProceduralNoiseDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[ProceduralNoiseDemo](ProceduralNoiseDemo)([benchmark=0])  
  
This demo demonstrates fast drawing of noise patches via use of  
procedural texture mapping. It only works on hardware with support for  
the GLSL shading language, vertex- and fragment-shaders.  
  
Patches are not encoded into a texture, but instead a little algorithm -  
a procedural texture shader - is executed on the graphics processor  
(GPU). This is very fast and efficient! All parameters of the patch can  
be set individually.  
  
This demo is both, a speed benchmark, and a correctness test. If executed  
with the optional benchmark flag set to 2, it will execute a loop where  
it repeatedly draws a patch on the GPU and then reads back the noise  
patch and computes a histogram over all pixels, so you can verify if the  
noise distribution is what you expect.  
  
In benchmark mode (flag set to 1), the patch is drawn as fast as  
possible, testing the maximum rate at which your system can draw patchs.  
  
At a default setting of benchmark==0, it just shows nicely drawn patch.  
  
Please note that results in performance and accuracy \*will\* vary,  
depending on the model of your graphics card, gfx-driver version and  
possibly operating system. For consistent results, always check before  
you measure on different setups! However, the more recent the graphics  
card, the faster and more accurate -- the latest generation of cards is  
supposed to be "just perfect" for vision research...  
  
If you want to draw many patches per frame, you wouldn't do it like in  
this script, but use the batch-drawing version of [Screen](Screen)('DrawTextures',  
...) instead, as demonstrated, e.g., in [DrawingSpeedTest](DrawingSpeedTest).m. That way you  
could submit the specs (parameters) of all patches in one single matrix  
via one single [Screen](Screen)('DrawTextures'); call - this is more efficient and  
therefore extra fast!  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/ProceduralNoiseDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/ProceduralNoiseDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/ProceduralNoiseDemo.m</code>
</div>

