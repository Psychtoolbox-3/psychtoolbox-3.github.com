# [CylinderAnnulusOpenGLDemo](CylinderAnnulusOpenGLDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)>[OpenGL4MatlabDemos](OpenGL4MatlabDemos)

[CylinderAnnulusOpenGLDemo](CylinderAnnulusOpenGLDemo)([patternType=0][, multiSample=0])  
  
This demo demonstrates use of [OpenGL](OpenGL) commands in a Matlab script to  
map a 2D image onto a 3D cylindrical surface.  
  
It loads a JPEG image of the earths surface from the filesystem, using  
Matlabs imread() function, then converts the image into a Psychtoolbox  
texture using [Screen](Screen)('MakeTexture'), then provides this texture as a  
standard [OpenGL](OpenGL) compatible texture using [Screen](Screen)('GetOpenGLTexture').  
This standard texture is applied to a cylinder using standard [OpenGL](OpenGL) commands  
and finally the cylinder is drawn as a rotating object in a simple animation  
loop. --\> You'll see a rotating cylinder.  
  
Stop the demo by pressing any key and it will finish.  
  
The optional parameter 'multiSample' allows to enable anti-aliased  
drawing with 'multiSample' samples per pixel on hardware that supports  
this.  
  
The optional parameter 'patternType' allows (if set to non-zero  
value) to apply a specific pattern to the spinning cylinder, instead of  
a "earth surface texture image". This demonstrates algorithmic texture  
generation and the use of trilinear mipmap filtering to improve image  
quality for high frequency edges and such...  
  
0 = Jpeg image of earth surface.  
1 = Checkerboard pattern.  
2 = Simple vertical annulus.  
  
The [OpenGL](OpenGL) Red Book is a great introduction and reference for [OpenGL](OpenGL)  
programming. Release 1.0 is available online, later releases can be  
purchased in any good book store:  
  
http://www.opengl.org/documentation/red\_book\_1.0/  
  
### For more infos, code samples, tutorials, online documentation, go to:  
  
http://www.opengl.org  
  
The earth surface JPEG-image is taken from the Linux/KDE application  
kdeworldclock. kdeworldclock and its components are licensed under  
GPL.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/OpenGL4MatlabDemos/CylinderAnnulusOpenGLDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/OpenGL4MatlabDemos/CylinderAnnulusOpenGLDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/OpenGL4MatlabDemos/CylinderAnnulusOpenGLDemo.m</code>
</div>

