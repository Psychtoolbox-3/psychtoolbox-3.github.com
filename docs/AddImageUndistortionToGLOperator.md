# [AddImageUndistortionToGLOperator](AddImageUndistortionToGLOperator)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

[AddImageUndistortionToGLOperator](AddImageUndistortionToGLOperator)(gloperator, exampleImage, calibrationStructureOrFile [, showCalibOutput=0][, varargin])  
  
Add a geometric undistortion operation to a given imaging pipeline image  
processing operator 'gloperator'. 'gloperator' is the operator to add to.  
'exampleImage' is a texture- or offscreen window handle to a texture or  
offscreen window which has exactly the color depths and size of the input  
images you want to geometrically undistort (and scale) later on. The  
created operator will be adapted to only work correctly on input images  
of that size! 'calibrationStructureOrFile' Either the file name to a  
geometric calibration file, as created by, e.g.,  
[DisplayUndistortionBezier](DisplayUndistortionBezier).m or [DisplayUndistortionBVL](DisplayUndistortionBVL).m, or a struct with  
the neccessary information as created, e.g., by [CreateDisplayWarp](CreateDisplayWarp)().  
'showCalibOutput' optional flag: If set to non-zero value, the routine  
will plot some debug output to the console or into figure windows.  
'varargin' may contain optional parameters that will be passed to the  
routine [CreateDisplayWarp](CreateDisplayWarp)() as optional arguments (see help  
[CreateDisplayWarp)](CreateDisplayWarp)).  
  
This routine can be used if you have geometrically distorted images from  
some source (movie file, video capture, etc.), given as textures or  
offscreen windows. It allows to define an operator that applies some  
geometric correction to that images and returns corrected versions of  
that images.  
  
### A typical way of using this:  
  
a) Create an "undistortion definition file" by use of the interactive  
display calibration routines, e.g., [DisplayUndistortionBezier](DisplayUndistortionBezier).m or  
[DisplayUndistortionBVL](DisplayUndistortionBVL).m, and save it somewhere.  
  
b) In your script, call this routine, passing the filename of that  
calibration file, and an 'exampleImage' of the size and format of the  
input images to undistort, to create a suitable gloperator.  
  
c) In your code, apply the operator to distorted images by use of the  
[Screen](Screen)('TransformTexture') function, e.g.:  
  
correctedImage = [Screen](Screen)('TransformTexture', distortedImage, gloperator);  
  
An example of this procedure can be seen in the demo  
"[ImageUndistortionDemo](ImageUndistortionDemo)".  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/AddImageUndistortionToGLOperator.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/AddImageUndistortionToGLOperator.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/AddImageUndistortionToGLOperator.m</code>
</div>

