# [VRHMDDemo](VRHMDDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

  
[VRHMDDemo](VRHMDDemo)([stereoscopic=1][, checkerboard=0][, withGazeTracking=0][, deviceindex=0])  
  
A very basic demo for the most basic setup of VR [HMDs](HMDs), e.g., the Oculus  
VR Rift DK2. It shows the absolute minimum of steps needed - one line of  
code - to use the first connected HMD as mono or stereo display.  
  
'stereoscopic' if set to 1 (which is the default), configures the  
HMD as a stereoscopic display. A setting of 0 configures it as a  
monoscopic display.  
  
'checkerboard' if set to 1 draws a checkboard pattern instead of the  
regular test image.  
  
The optional parameter 'withGazeTracking', if provided and non-zero, will  
enable some basic test of eye gaze tracking with VR HMD's which support  
eye tracking. Please note that this functionality is not available in  
official Psychtoolbox releases yet, at least not as of v3.0.19.1, and the  
api used in this demo is highly experimental and subject to backwards  
incompatible changes!  
  
'deviceindex' if provided, selects the HMD with given index. Otherwise  
the first HMD (deviceindex 0) is chosen.  
  
The demo just renders one static simple 2D image, or image pair in  
stereoscopic mode, then displays it in a loop until a key is pressed.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/VRHMDDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/VRHMDDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/VRHMDDemo.m</code>
</div>

