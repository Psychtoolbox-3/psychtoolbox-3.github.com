# [DeinterlacerTest](DeinterlacerTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[DeinterlacerTest](DeinterlacerTest)([sf][,imgname][,method])  
  
Tests (and thereby demonstrates) the Psychtoolbox builtin GLSL realtime  
deinterlaceshader, an [OpenGL](OpenGL) GLSL Fragmentshader for on-the-fly  
deinterlacing of video images which are given as PTB textures and drawn  
via [Screen](Screen)('MakeTexture').  
  
Parameters: 'imgname' is optional. If provided, the routine loads an  
imagefile of that name as test input, otherwise it creates a synthetic  
test pattern in Matlab.  
  
sf - Optional scalefactor, by which the image is scaled in size.  
  
### method - Select deinterlace method:  
  
0 = None. 1 = Replacement of lines, 2 = Averaging of lines.  
  
See the shader sources under Psychtoolbox/[PsychOpenGL](PsychOpenGL)/[PsychGLSLShaders](PsychGLSLShaders)  
for proper definition of the operations.  
  
### What you should see (assuming you did not provide an input image file):  
  
First an image with alternating red- and green color gradients. This is  
the interlaced test pattern where even rows contain only red, odd rows  
contain only green gradients.  
  
Press a key.  
  
Then, by pressing and releasing a key, the image should alternate between  
an all red image (only red gradients of twice the thickness), and an all  
green image: This is the alternating deinterlaced even, odd, even, odd  
... half-fields of the interlaced image.  
  
End the demo by pressing [ESCape](ESCape) key twice.  
  
If you see something else, or just a black screen, or it aborts with  
error, then your hardware is probably not capable of running the  
deinterlace-shader and you're out of luck.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/DeinterlacerTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/DeinterlacerTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/DeinterlacerTest.m</code>
</div>

