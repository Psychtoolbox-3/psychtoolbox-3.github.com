# [BlurredVideoCaptureDemo](BlurredVideoCaptureDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[BlurredVideoCaptureDemo](BlurredVideoCaptureDemo) - Show application of image filters to videocaptured images.  
  
This demo shows how to apply 2D convolution kernels to a live video  
stream captured from an attached default camera. Convolution is not  
performed on the cpu by Matlab/Octave, but executed hardware-accelerated  
on the GPU for potentially much higher speed.  
  
### Usage:  
  
[BlurredVideoCaptureDemo](BlurredVideoCaptureDemo)([filtertype=1][, kwidth=11][, deviceIndex=0])  
  
### 'filtertype' is optional and can be:  
  
0 = None.  
1 = Gaussian blur - This is the default.  
2 = Prewitt operator.  
3 = Unsharp operator.  
4 = Sobel operator.  
5 = Log operator.  
  
The filters are selected via the fspecial() function, and converted into  
proper convolution kernels. You may need the Matlab image processing  
toolobox or equivalent Octave package installed, for fspecial() to be  
available.  
  
'kwidth' = Optional convolution kernel width in pixels. Defaults to 11.  
  
'deviceIndex' = Optional index of the video capture device. Defaults to  
auto-selected default video source.  
  
Press any key to finish the demo.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/BlurredVideoCaptureDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/BlurredVideoCaptureDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/BlurredVideoCaptureDemo.m</code>
</div>

