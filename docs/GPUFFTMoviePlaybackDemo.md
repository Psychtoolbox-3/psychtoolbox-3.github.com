# [GPUFFTMoviePlaybackDemo](GPUFFTMoviePlaybackDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)>[GPGPUDemos](GPGPUDemos)

[GPUFFTMoviePlaybackDemo](GPUFFTMoviePlaybackDemo) - Demonstrate use of GPGPU computing for live filtering via 2D-FFT.  
  
This demo makes use of the FOSS [GPUmat](GPUmat) toolbox to perform a GPU  
accelerated 2D FFT + filtering in frequency space + 2D inverse FFT on a  
movie video file. [GPUmat](GPUmat) allows to use NVidia's CUDA gpu computing  
framework on supported [NVidia](NVidia) gpu's [(GeForce]((GeForce)-8000 series and later, aka  
[Direct3D](Direct3D)-10 or [OpenGL](OpenGL)-3 capable).  
  
It shows how a Psychtoolbox floating point texture (with movie content  
inside) can be efficiently passed to [GPUmat](GPUmat) as a matrix of [GPUsingle](GPUsingle) data  
type, which is stored and processed on the GPU. Then it uses GPUmat's fft  
routines for forward/inverse fft's and matrix manipulation. Then it  
returns the final image to Psychtoolbox as a new floating point texture  
for display. The same steps are carried out with Matlab/Octave's regular  
fft routines on the cpu for reference.  
  
Requires the freely downloadable [NVidia](NVidia) CUDA-5.0 SDK/Runtime and the free  
and open-source [GPUmat](GPUmat) toolbox as well as a compute capable [NVidia](NVidia)  
graphics card.  
  
### Usage:  
  
[GPUFFTMoviePlaybackDemo](GPUFFTMoviePlaybackDemo)([usegpu=1][, showfft=0][, fwidth=11][, roi][, depth=1][, moviename])  
  
### Parameters:  
  
'usegpu' = 0 to use regular Matlab/Octave fft on CPU, 1 = to use [GPUmat](GPUmat) on GPU.  
  
'showfft' = 1 to show amplitude spectrum of movie in usegpu=1 mode.  
  
'fwidth' = Width of low-pass filter kernel in frequency space units.  
  
'roi' = Region of interest to show, e.g., [0,0,640,480].  
  
'depth' = 1 for Mono, 3 for color processing.  
  
'moviename' Name string for selection of movie file.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/GPGPUDemos/GPUFFTMoviePlaybackDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/GPGPUDemos/GPUFFTMoviePlaybackDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/GPGPUDemos/GPUFFTMoviePlaybackDemo.m</code>
</div>

