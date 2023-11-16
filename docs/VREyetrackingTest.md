# [VREyetrackingTest](VREyetrackingTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[VREyetrackingTest](VREyetrackingTest)([stereoscopic=0][, render3D=0][, testEye=0][, modulateBackgroundBrightness=0][, text])  
  
A test for eye gaze tracking in VR HMD's via [PsychVRHMD](PsychVRHMD) supported methods.  
Tested with HTC Vive Pro Eye binocular eyetracker.  
  
### Parameters:  
  
'stereoscopic' if set to 1, configures the HMD as a stereoscopic display.  
A default setting of 0 configures it as a monoscopic display with both eyes  
seeing the same stimulus.  
  
'render3D' if set to 1, use [OpenGL](OpenGL) 3D rendering of target with use of  
perspective projection, using the driver provided MODELVIEW and  
PROJECTION matrices.  
  
'testEye' which eye gaze source to test and plot further. Defaults to 0.  
Choose 1 for left-eye in binocular setup, or mono-eye in monocular setup.  
Choose 2 for right eye in binocular setup, 3 for cyclops eye in binocular setup.  
  
'modulateBackgroundBrightness' if set greater than zero, change brightness  
of background over time, to see if that affects gaze tracking, and for  
suitable gaze trackers if it correlates with measured/reported pupil diameter.  
  
'text' An optional text string that can be displayed on the screen.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/VREyetrackingTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/VREyetrackingTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/VREyetrackingTest.m</code>
</div>

