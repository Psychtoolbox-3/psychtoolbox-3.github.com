# [Add2DSeparableConvolutionToGLOperator](Add2DSeparableConvolutionToGLOperator)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

[Add2DSeparableConvolutionToGLOperator](Add2DSeparableConvolutionToGLOperator)(gloperator, kernel1, kernel2 [, opname] [, nrinputchannels] [, nroutchannels] [, debug] [, shadertype])  
  
Add a separable 2D pair of convolution kernels to GL operator 'gloperator'.  
  
'kernel1' and 'kernel2' are a simple 1-by-n or m-by-1 matrices of floating  
point numbers with m and n being odd numbers, e.g., 1, 3, 5, 7, 9, ...  
Each entry in the kernel matrices is used as a weight factor for the  
convolution. First kernel1 is applied   
  
The simplest way to get a kernel is to use the function  
kernel = fspecial(...); fspecial is part of the Matlab image  
processing toolbox, see "help fspecial" for more information.  
  
'opname' is the optional name of the convolution operation, meant as  
debugging aid.  
  
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




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/Add2DSeparableConvolutionToGLOperator.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/Add2DSeparableConvolutionToGLOperator.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/Add2DSeparableConvolutionToGLOperator.m</code>
</div>

