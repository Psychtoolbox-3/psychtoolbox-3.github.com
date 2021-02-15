# [HDRMinimalisticOpenGLDemo](HDRMinimalisticOpenGLDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[HDRMinimalisticOpenGLDemo](HDRMinimalisticOpenGLDemo) - Demonstrate use of MATLAB-[OpenGL](OpenGL) toolbox with  
HDR High Dynamic Range Displays.  
  
It differs from the normal [MinimalisticOpenGLDemo](MinimalisticOpenGLDemo) only by the [PsychImaging](PsychImaging)  
call that requests HDR support, and the setup of lightsource intensities to  
make better use of the large dynamic range of the HDR display.  
  
This demo demonstrates use of [OpenGL](OpenGL) commands in a Matlab script to  
perform some very boring 3D rendering in Psychtoolbox.  
  
It shows a single static ball, lit with default lighting and exactly one  
light source. This is meant to demonstrate the minimum amount of code to  
draw anything visible with perspective projection. It also draws a static  
teapot and some little box with a cone as roof.  
  
Then it waits for a keyboard press.  
  
After that it demonstrates how to do basic texture mapping and animation:  
It loads a JPEG image of the earths surface from the filesystem, using  
Matlabs imread() function, then converts the image into a Psychtoolbox  
texture using [Screen](Screen)('MakeTexture'), then provides this texture as a  
standard [OpenGL](OpenGL) compatible texture using [Screen](Screen)('GetOpenGLTexture').  
This standard texture is applied to a sphere using standard [OpenGL](OpenGL) commands  
and finally the sphere is drawn as a rotating object in a simple animation  
loop. --\> You'll see a rotating earth.  
  
Stop the demo by pressing any key and it will finish.  
  
### Notable implementation details regarding use of [OpenGL](OpenGL):  
  
The call [InitializeMatlabOpenGL](InitializeMatlabOpenGL) at the top of the script initializes the  
Matlab-[OpenGL](OpenGL) toolbox and enables the 3D gfx support in Psychtoolbox to  
allow proper interfacing between the [OpenGL](OpenGL) toolbox and Psychtoolbox.  
  
After this call, all [OpenGL](OpenGL) functions are made available to Matlab with  
the same - or a very similar - calling syntax as in the C programming  
language. [OpenGL](OpenGL) constants are made available in a format that is optimized  
for Matlab, where the first underscore is replaced by a dot, e.g.,  
GL.DEPTH\_TEST, instead of the C-style GL\_DEPTH\_TEST.  
  
In order to execute [OpenGL](OpenGL) 3D drawing commands to draw 3D stims into a  
Psychtoolbox Onscreen- or offscreen window, one needs to call  
[Screen](Screen)('BeginOpenGL', windowPtr). After [OpenGL](OpenGL) drawing and before  
execution of standard [Screen](Screen)() commands, one needs to call  
[Screen](Screen)('EndOpenGL', windowPtr) to tell Psychtoolbox that 3D drawing is  
finished.  
  
Some [OpenGL](OpenGL) functions that return complex parameters to Matlab are not  
yet implemented - this is work in progress. The performance will be also  
lower than when coding in a compiled language like C++ or C -- that's the  
Matlab tax you'll have to pay ;-)  
  
The toolbox checks after execution of each single [OpenGL](OpenGL) command if it  
caused some error. It aborts your script with an error message, if so. If  
you are happy with your code and want to disable these error checks in  
order to squeeze out a bit more speed, you can call  
[InitializeMatlabOpenGL](InitializeMatlabOpenGL)(0,0) instead of [InitializeMatlabOpenGL](InitializeMatlabOpenGL) at the top  
of your script. This will disable automatic error-checking. You can then  
use the commands gluErrorString or glGetError to perform manual error-checks  
in your code if you want.  
  
Apart from that, use of [OpenGL](OpenGL) for Matlab is the same as [OpenGL](OpenGL) for the C  
programming language. If you are used to [OpenGL](OpenGL) coding in C, it should be  
a zero effort transition to code in Matlab+PTB. If you don't know [OpenGL](OpenGL)  
then get yourself one of the many good books or visit one of the many  
[OpenGL](OpenGL) tutorials on the internet.  
  
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
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/HDRMinimalisticOpenGLDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/HDRMinimalisticOpenGLDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/HDRMinimalisticOpenGLDemo.m</code>
</div>

