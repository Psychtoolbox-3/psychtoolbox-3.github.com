# [EXPCreateStatic2DConvolutionShader](EXPCreateStatic2DConvolutionShader)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOpenGL](PsychOpenGL)>[PsychGLSLShaders](PsychGLSLShaders)

[shader configstring] = [EXPCreateStatic2DConvolutionShader](EXPCreateStatic2DConvolutionShader)(kernel [, nrinputchannels=3][, nroutchannels=3][, debug][, shadertype])  
  
Creates a GLSL fragment shader for 2D convolution of textures with  
the 2D or 1D convolution kernel 'kernel' and returns a handle 'shader'  
to it, as well as a blitter config options string as needed by the  
PTB imaging pipeline.  
  
Usually you won't call this routine directly, but use  
[Add2DConvolutionToGLOperator](Add2DConvolutionToGLOperator)() instead. It allows convenient setup of  
convolution operators of arbitrary size and complexity to [GLOperators](GLOperators)  
for use with [Screen](Screen)('TransformTexture'); and for use with the stimulus  
post-processing pipeline. Only if you want to create small convolution  
kernels for single-pass convolution of textures, you'll use this routine  
directly and use the returned 'shader' as argument to [Screen](Screen)('DrawTexture')  
or [Screen](Screen)('MakeTexture') as 'textureShader' argument.  
  
If you call this function directly, the generated shader may only work with  
the onscreen window that is active at the time you call the function. To make  
sure that the shader works with the onscreen window 'win' of your choice, call  
[Screen](Screen)('GetWindowInfo', win); first, to activate the window 'win'.  
  
  
### Parameters:  
  
'kernel' is a simple 2D m-by-n matrix of floating point numbers with m and  
n being odd numbers, e.g., 1x1, 3x3, 5x5, 7x7, 9x9,..., 1x3, 1x9, 7x1 ...  
Each entry in the kernel is used as a weight factor.  
  
The simplest way to get a 2D kernel is to use the function  
kernel = fspecial(...); fspecial is part of the Matlab image  
processing toolbox, see "help fspecial" for more information.  
  
'nrinputchannels' = The number of image channels to use as input for the  
convolution. Possible values are: 3 = Red, Green and Blue color channels are  
provided as part of a true-color image, don't use the alpha channel (if  
any) for convolution but just pass it through unmodified. 1 = The image  
only defines a luminance channel for convolution, an (optional) alpha  
channel is passed through unmodified. 4 = Use all four channels (Red,  
green, blue, alpha) for convolution.  
  
'nroutchannels' = The number of channels to convolve as output: 3 =  
Convolve each of the three color channels red, green and blue separately  
by the same kernel. An (optional) alpha channel is passed through unmodified.  
1 = Output a filtered luminance channel, and an (optional) unmodified  
alpha channel. If input is a 3 channel RGB image, then the RGB image will  
get converted to luminance before convolution. 4 = Filter all four  
channels independently.  
  
### Typical settings:  
  
Filter a RGB(A) image: nrinputchannels = 3, nroutchannels = 3.  
Filter a RGB(A) image into grayscale: nrinputchannels = 3, nroutchannels = 1.  
Filter a luminance(A) image: inputchannels = 1, filteredoutchannels = 1.  
Generic filtering of 4-channel data: nrinputchannels = 4, nroutchannels = 4.  
  
'debug' Optional debug flag: If set to non-zero, will output some debug  
info about the shader.  
  
'shadertype' (Optional) The type of internal implementation to choose for  
the operator. This parameter is best left alone, unless you really know  
what you are doing.  
  
### CAUTION:  
  
This feature is in early alpha stage. It may fail on your system and its  
future implementation may change significantly! Don't trust its results  
without validation against a known good reference implementation!  
  
NOTES: Filtermode 2 and 3 not fully implemented for the general case!  
---\> No separable 1D kernels, no support for all input-\>output mappings  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOpenGL/PsychGLSLShaders/EXPCreateStatic2DConvolutionShader.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOpenGL/PsychGLSLShaders/EXPCreateStatic2DConvolutionShader.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOpenGL/PsychGLSLShaders/EXPCreateStatic2DConvolutionShader.m</code>
</div>

