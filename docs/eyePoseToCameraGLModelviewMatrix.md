# [eyePoseToCameraGLModelviewMatrix](eyePoseToCameraGLModelviewMatrix)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOpenGL](PsychOpenGL)

eyePoseToCameraGLModelviewMatrix() - Convert eyePose directly to [OpenGL](OpenGL) modelview matrix.  
  
### Usage:  
  
modelview = eyePoseToCameraGLModelviewMatrix(eyePose [, eyeLocalTranslate])  
  
### Input arguments:  
  
'eyePose' is a [tx, ty, tz, rx, ry, rz, rw] vector, with the first 3 components  
defining eye translation, and the last 4 components defining a rotation Quaternion  
that defines eye orientation.  
  
'eyeLocalTranslate' is an optional 3 component translation vector that gets applied  
to 'eyePose' position, but within the eyes own rotated local coordinate system.  
This is useful if 'eyePose' is not actually describing an eye pose, but the tracked  
global head pose or global HMD pose. Applying suitable 'eyeLocalTranslate' translation  
vectors allows to derive the eyes position from the head/HMD position.  
  
### Return arguments:  
  
'modelview' is a 4x4 matrix that can be directly loaded into [OpenGL](OpenGL) as GL\_MODELVIEW  
matrix, e.g., glLoadMatrixd(modelview); to define camera position and orientation  
for rendering accordign to eyePose. Iow. modelview is already the inverse matrix of  
eyePose.  
  
'eyePoseT' is the original input 'eyePose', but optionally transformed by 'eyeLocalTranslate'.  
It is not the inverse of 'eyePos', like 'modelview'!  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOpenGL/eyePoseToCameraGLModelviewMatrix.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOpenGL/eyePoseToCameraGLModelviewMatrix.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOpenGL/eyePoseToCameraGLModelviewMatrix.m</code>
</div>

