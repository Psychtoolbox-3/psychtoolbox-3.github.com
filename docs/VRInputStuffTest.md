# [VRInputStuffTest](VRInputStuffTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[PsychVRToolbox](PsychVRToolbox)

[VRInputStuffTest](VRInputStuffTest)([withHapticFeedback=0][, withMTStressTest=0][, specialReqs='DebugDisplay'][, refSpace][, withGazeTracking=0]) - Test input functionality related to VR devices.  
  
Tries to enumerate available controllers and other properties related to  
input. After any key press or controller button press, reports live state  
of buttons, sensors, triggers etc. of connected controllers.  
  
If the optional parameter 'withHapticFeedback' is set to 1, then also  
exercises the haptic feedback functionality of any of the left and right  
hand controllers, if the A/B or X/Y buttons are pressed for low/high  
frequency rumble on right or left controller. Haptic feedback is not  
exercised by default, as it empties the controllers batteries relatively  
fast.  
  
The optional parameter 'withMTStressTest' if set to 1 will test  
single-threading to multi-threading switching on the fly. Multi-threaded  
mode is less efficient, more prone to skipped deadlines or lower  
animation rates, but stabilizes visuals in 'Stop'ed 3D mode, and is  
needed on most [OpenXR](OpenXR) runtimes to get even a semblance of correct frame  
presentation timing and timestamping.  
  
The optional parameter 'specialReqs' allows to pass in extra  
basicRequirments into the driver. Meaningful keywords could be:  
  
[ForceSize](ForceSize)=1230x4560 = Enforce a per-eye image size of 1230x4560 pixels.  
[Use2DViewsWhen3DStopped](Use2DViewsWhen3DStopped) = Use different display mode for stopped 3D rendering.  
2DViewDistMeters=2.1 = Enforce 2D views to be 2.1 meters away from the  
viewer, instead of the default of 1 meter. Allows scaling of 2D image  
views.  
[DontCareAboutVisualGlitchesWhenStopped](DontCareAboutVisualGlitchesWhenStopped) = Don't care about glitches when stopped.  
[ForbidMultiThreading](ForbidMultiThreading) = Do not use multi-threaded presentation ever.  
[DebugDisplay](DebugDisplay) = Also show rendered stimuli on the experimenters monitor.  
This is the default.  
  
The optional parameter 'refSpace', if provided and non-zero, allows to  
select a specific [OpenXR](OpenXR) reference space under [OpenXR](OpenXR). It is ignored  
under other drivers. The most interesting values are 1 for head locked, 2  
for a local reference space, and 3 for a stage reference space. 3 often  
enables additional goodies, but support for it is not mandatory for an  
[OpenXR](OpenXR) runtime, so selecting 3 could fail. However, so far 4 out of 4  
tested [OpenXR](OpenXR) runtimes on Linux and Windows did support the stage  
reference space, which provided a more natural coordinate system and also  
visualization of the "play area". The driver default is 2 for local, as  
that is always supported.  
  
The optional parameter 'withGazeTracking', if provided and non-zero, will  
enable some basic tests of eye gaze tracking with VR HMD's which support  
eye tracking. A setting of 1 will visualize the 2D gaze position, a setting of  
2 will visualize a 3D gaze ray in addition.  
  
After a keypress (or Enter/Back button press on the controller),  
visualizes tracked hand position and orientation of hand controllers and  
allows to do some nice visual effects based on trigger / grip button  
presses, thumbsticks movement etc.  
  
Tested with [XBox](XBox) controller, Oculus remote, and the two Oculus touch  
controllers of the Oculus Rift CV-1 on Windows-10 and Linux, with the  
[OculusVR](OculusVR) v1 runtime on Windows, and with various [OpenXR](OpenXR) runtimes like  
Monado, [OculusVR](OculusVR), [SteamVR](SteamVR). Additionally tested with the Vive Wand  
controllers and builtin binocular eye gaze tracker of a HTC Vive Pro Eye.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/PsychVRToolbox/VRInputStuffTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/PsychVRToolbox/VRInputStuffTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/PsychVRToolbox/VRInputStuffTest.m</code>
</div>

