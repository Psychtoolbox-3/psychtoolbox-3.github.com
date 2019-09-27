# [Create2DGaussianBlurShader](Create2DGaussianBlurShader)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOpenGL](PsychOpenGL)>[PsychGLSLShaders](PsychGLSLShaders)

blurshader = [Create2DGaussianBlurShader](Create2DGaussianBlurShader)(stddev, width)  
  
Create a GLSL shader which uses a 2D gaussian filter kernel to  
apply gaussian blur onto a texture. Returns the handle 'blurshader',  
which can be used with [Screen](Screen)('DrawTexture') to apply the shader during  
texture drawing.  
  
stddev = Standard deviation of kernel to use. Defaults to 2.5.  
width  = Width of filter-kernel. Currently only a width of 5 is  
supported, so this argument is optional and defaults to 5.  
  
Currently you will need the Matlab imageprocessing toolbox for this to  
work, or the Octave image package, as we use the toolbox function 'fspecial'  
to compute the filter kernel.  
  
### Example of use:  
  
Somewhere during initialization of your script you call:  
blurshader = [Create2DGaussianBlurShader](Create2DGaussianBlurShader)(2.5);  
  
### When you want to draw an image blurred with a gaussian lowpass, you do:  
  
[Screen](Screen)('DrawTexture', win, mytexture, [], [], [], [], [], [], blurshader);  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOpenGL/PsychGLSLShaders/Create2DGaussianBlurShader.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOpenGL/PsychGLSLShaders/Create2DGaussianBlurShader.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOpenGL/PsychGLSLShaders/Create2DGaussianBlurShader.m</code>
</div>

