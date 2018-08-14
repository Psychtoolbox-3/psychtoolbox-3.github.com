# [ConvolutionKernelTest](ConvolutionKernelTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[passed difference speedup] = [ConvolutionKernelTest](ConvolutionKernelTest)(win, nrinchannels, nroutchannels, kernel1, kernel2, imgsize, shadertype, debug)  
  
Test Psychtoolbox imaging pipeline's 2D convolution shaders for  
correctness and accuracy, perform speed benchmark, return fastest setup,  
when using a specific (pair) of kernel(s) and parameters.  
  
This routine builds and tests a set of convolution shaders from the given  
convolution kernel (or pair of kernels for separable dual-pass  
convolution). Each shader is compared against the results of  
Matlabs/Octaves conv2 function, applied to a random noise luminance image  
matrix. The shader is tagged as working correctly if the conv2 result and  
PTB's result do not disagree by more than 1 unit at any location in the  
convolved output images. Accuracy (maximum difference) is reported. All  
correctly working shaders are then benchmarked for speed during a test  
period of 10 seconds and the speedup of the GPU vs. Matlab (CPU) is  
determined and reported. At the end, the best configuration (wrt.  
correctness, accuracy and speed) is reported/recommended for use with the  
given kernel.  
  
The routine takes at least 10 seconds per tested shader, so a full test  
run will take at least 4\*10 = 40 seconds, probably a bit more for setup  
and shutdown. Status messages will tell you about progress of the  
operation. You shouldn't use your machine and don't run any other  
applications during benchmarking, otherwise the measured speedup numbers  
may be wrong due to GPU or CPU overload.  
  
### Optional parameters and their defaults:  
  
'win' Window handle of the onscreen window to test on. If none provided,  
will open a suitable one by itself on screen 0.  
  
'nrinchannels' number of image color channels in test image: Default is 1  
for pure luminance convolution. This script always only tests the first  
channel (red/luminance) for correctness/accuracy, even on multi-channel  
images, but choice of channels will affect overall correctness and speed.  
  
'nroutchannels' number of image output channels from convolution: By  
default 1 == convolve, replicate result to RGB channels, pass alpha  
through. 3 == Convolve RGB separately, pass through alpha. 4 == Convolve  
RGBA separately.  
  
'kernel1' == 2D kernel or first 1D kernel in separable mode.  
'kernel2' == 1D kernel for 2nd pass in separable convolution test.  
  
'imgsize' == Either size of the random noise test image (default =  
512x512), or a Matlab image matrix to test on.  
  
'shadertype' == Vector of mode ids: Tests all modes in the vector. By  
default all shadertypes are tested ie shadertype = [0 1 2 3]. PTB  
provides different implementations of convolution (0,1,2,3) which may  
have different accuracy and performance for a given hardware and kernel.  
The shaders provided in this vector will be tested against each other.  
  
'debug'Defaults to zero (no output): Amount of debug output to write to  
Matlab window.  
  
THIS SCRIPT IS NOT COMPLETELY FINISHED YET.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/ConvolutionKernelTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/ConvolutionKernelTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/ConvolutionKernelTest.m</code>
</div>

