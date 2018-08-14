# [EyelinkGazeContingentDemo](EyelinkGazeContingentDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[EyelinkToolbox](EyelinkToolbox)>[EyelinkDemos](EyelinkDemos)>[GazeContingentDemos](GazeContingentDemos)

  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
Demo implementation of a generic gaze-contingent display.  
We take one input image and create - via image processing - two images  
out of it: An image to show at the screen location were the subject  
fixates (According to the eye-tracker). A second image to show in the  
peripery of the subjects field of view. These two images are blended into  
each other via a gaussian weight mask (an aperture). The mask is centered  
at the center of gaze and allows for a smooth transition between the two  
images.  
  
This illustrates an application of [OpenGL](OpenGL) Alpha blending by compositing  
two images based on a spatial gaussian weight mask. Compositing is done  
by the graphics hardware.  
Mode can have the following values:  
Mode 1:  
  Fovea contains original image data:  
  Periphery contains grayscale-version:  
Mode 2:  
  Fovea contains original image data:  
  Periphery contains blurred-version:  
Mode 3  
  Fovea contains color-inverted image data:  
  Periphery contains original data:  
Mode 4  
  Test-case: One shouldn't see any foveated region on the  
  screen - this is a basic correctness test for blending.  
  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
see also: [EyelinkExample](EyelinkExample), [EyelinkPicture](EyelinkPicture)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkDemos/GazeContingentDemos/EyelinkGazeContingentDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkDemos/GazeContingentDemos/EyelinkGazeContingentDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkDemos/GazeContingentDemos/EyelinkGazeContingentDemo.m</code>
</div>

