# [PsychCamIntrinsicsToGLProjectionMatrix](PsychCamIntrinsicsToGLProjectionMatrix)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOpenGL](PsychOpenGL)

M = [PsychCamIntrinsicsToGLProjectionMatrix](PsychCamIntrinsicsToGLProjectionMatrix)(cx, cy, fx, fy, zNear, zFar)  
  
Given camera intrinsic parameters from some camera calibration software, and  
the desired zNear and zFar clipping planes of the view frustum, compute and  
return a projection matrix for use as GL\_PROJECTION\_MATRIX for [OpenGL](OpenGL) rendering  
with a virtual pinhole camera that approximates the properties of the real camera.  
  
### Parameters:  
  
cx = Optical sensor center in pixels.  
cy = Optical sensor center in pixels.  
fx = Focal length in units of pixels in x direction.  
fy = Focal length in units of pixels in y direction.  
zNear = Near clipping plane.  
zFar = Far clipping plane.  
  
Returns the 4-by-4 GL\_PROJECTION\_MATRIX.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOpenGL/PsychCamIntrinsicsToGLProjectionMatrix.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOpenGL/PsychCamIntrinsicsToGLProjectionMatrix.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOpenGL/PsychCamIntrinsicsToGLProjectionMatrix.m</code>
</div>

