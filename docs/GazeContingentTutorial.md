# [GazeContingentTutorial](GazeContingentTutorial)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)>[PsychTutorials](PsychTutorials)

  
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
  
See also: [PsychDemos](PsychDemos), [MovieDemo](MovieDemo), [DriftDemo](DriftDemo)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/PsychTutorials/GazeContingentTutorial.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/PsychTutorials/GazeContingentTutorial.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/PsychTutorials/GazeContingentTutorial.m</code>
</div>

