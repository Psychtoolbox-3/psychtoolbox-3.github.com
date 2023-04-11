# [PsychOculusVR1](PsychOculusVR1)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[PsychVRToolbox](PsychVRToolbox)

[PsychOculusVR1](PsychOculusVR1) - A high level driver for Oculus VR hardware using the Version 1.16+ runtime.  
  
Copyright (c) 2018-2023 Mario Kleiner. Licensed under the MIT license.  
The underlying [PsychOculusVRCore1](PsychOculusVRCore1) mex driver uses the Oculus SDK, which is  
“Copyright © Facebook Technologies, LLC and its affiliates. All rights reserved.”  
A copy of the Oculus SDK license, its terms of use and thereby redistribution  
terms for the [PsychOculusVRCore1](PsychOculusVRCore1) mex file can be found in the [PsychtoolboxRoot](PsychtoolboxRoot)()  
folder under:  
Psychtoolbox/[PsychHardware](PsychHardware)/[PsychVRToolbox](PsychVRToolbox)/LICENSE\_OculusSDK1.txt  
  
Oculus VR's trademarks, e.g., Oculus, Oculus Rift, etc. are registered trademarks  
owned by Oculus VR, LLC.  
  
Note: If you want to write VR code that is portable across  
VR headsets of different vendors, then use the [PsychVRHMD](PsychVRHMD)()  
driver instead of this driver. The [PsychVRHMD](PsychVRHMD) driver will use  
this driver as appropriate when connecting to a Oculus Rift  
or similar Oculus device, but it will also automatically work  
with other head mounted displays. This driver does however  
expose a few functions specific to Oculus hardware, so you can  
mix calls to this driver with calls to [PsychVRHMD](PsychVRHMD) to do some  
mix & match.  
  
For setup instructions for Oculus [HMDs](HMDs) see "help [OculusVR](OculusVR)".  
  
  
### Usage:  
  
oldverbosity = [PsychOculusVR1](PsychOculusVR1)('Verbosity' [, newverbosity]);  
- Get/Set level of verbosity for driver status messages, warning messages,  
error messages etc. 'newverbosity' is the optional new verbosity level,  
'oldverbosity' is the currently set verbosity level - ie. before changing  
it.  Valid settings are: 0 = Silent, 1 = Errors only, 2 = Warnings, 3 = Info,  
4 = Debug.  
  
  
hmd = [PsychOculusVR1](PsychOculusVR1)('AutoSetupHMD' [, basicTask='Tracked3DVR'][, basicRequirements][, basicQuality=0][, deviceIndex]);  
- Open a Oculus HMD, set it up with good default rendering and  
display parameters and generate a [PsychImaging](PsychImaging)('AddTask', ...)  
line to setup the Psychtoolbox imaging pipeline for proper display  
on the HMD. This will also cause the device connection to get  
auto-closed as soon as the onscreen window which displays on  
the HMD is closed. Returns the 'hmd' handle of the HMD on success.  
  
By default, the first detected HMD will be used and if no VR HMD  
is connected, it will return an empty [] hmd handle. You can override  
this default choice of HMD by specifying the optional 'deviceIndex'  
parameter to choose a specific HMD. However, only one HMD per machine is  
supported, so the 'deviceIndex' will probably be only useful in the future.  
  
More optional parameters: 'basicTask' what kind of task should be implemented.  
The default is 'Tracked3DVR', which means to setup for stereoscopic 3D  
rendering, driven by head motion tracking, for a fully immersive experience  
in some kind of 3D virtual world. This is the default if omitted. The task  
'Stereoscopic' sets up for display of stereoscopic stimuli, but without  
head tracking. 'Monoscopic' sets up for display of monocular stimuli, ie.  
the HMD is just used as a special kind of standard display monitor. In 'Monoscopic'  
and 'Stereoscopic' mode, both eyes will be presented with an identical field of view,  
to make sure pure 2D drawing works, without the need for setup of special per-eye  
projection transformations. In 'Tracked3DVR' mode, each eye will have a different  
field of view, optimized to maximize the viewable area while still avoiding occlusion  
artifacts due to the nose of the wearer of the HMD.  
  
'basicRequirements' defines basic requirements for the task. Currently  
defined are the following strings which can be combined into a single  
'basicRequirements' string:  
  
'DebugDisplay' = Show the output which is displayed on the HMD inside the  
Psychtoolbox onscreen window as well. This will have a negative impact on  
performance, latency and timing of the HMD visual presentation, so should only  
be used for debugging, as it may cause a seriously degraded VR experience.  
By default, no such debug output is produced and the Psychtoolbox onscreen  
window is not actually displayed on the desktop.  
  
'Float16Display' = Request rendering, compositing and display in 16 bpc float  
format. This will ask Psychtoolbox to render and post-process stimuli in 16 bpc  
linear floating point format, and allocate 16 bpc half-float textures as final  
renderbuffers to be sent to the VR compositor. If the VR compositor takes advantage  
of the high source image precision is at the discretion of the compositor and HMD.  
By default, if this request is omitted, processing and display in sRGB format is  
requested from Psychtoolbox and the compositor, ie., a roughly gamma 2.2 8 bpc  
format is used, which is optimized for the gamma response curve of at least the Oculus  
Rift CV1 display.  
  
'ForceSize=widthxheight' = Enforce a specific fixed size of the stimulus  
image buffer in pixels, overriding the recommmended value by the runtime,  
e.g., 'ForceSize=2200x1200' for a 2200 pixels wide and 1200 pixels high  
image buffer. By default the driver will choose values that provide good  
quality for the given Oculus display device, which can be scaled up or down  
with the optional 'pixelsPerDisplay' parameter for a different quality vs.  
performance tradeoff in the function [PsychOpenXR](PsychOpenXR)('SetupRenderingParameters');  
The specified values are clamped against the maximum values supported by  
the given hardware + driver combination.  
  
'PerEyeFOV' = Request use of per eye individual and asymmetric fields of view even  
when the 'basicTask' was selected to be 'Monoscopic' or 'Stereoscopic'. This allows  
for wider field of view in these tasks, but requires the usercode to adapt to these  
different and asymmetric fields of view for each eye, e.g., by selecting proper 3D  
projection matrices for each eye.  
  
'TimingSupport' = Use high precision and reliability timing for presentation.  
Useless, as this driver always has presentation timing that has to be considered  
\*not trustworthy\*, unreliable and unprecise!  
  
'basicQuality' defines the basic tradeoff between quality and required  
computational power. A setting of 0 gives lowest quality, but with the  
lowest performance requirements. A setting of 1 gives maximum quality at  
maximum computational load. Values between 0 and 1 change the quality to  
performance tradeoff.  
  
  
hmd = [PsychOculusVR1](PsychOculusVR1)('Open' [, deviceIndex], ...);  
- Open HMD with index 'deviceIndex'. See [PsychOculusVRCore1](PsychOculusVRCore1) Open?  
for help on additional parameters.  
  
  
[PsychOculusVR1](PsychOculusVR1)('SetAutoClose', hmd, mode);  
- Set autoclose mode for HMD with handle 'hmd'. 'mode' can be  
0 (this is the default) to not do anything special. 1 will close  
the HMD 'hmd' when the onscreen window is closed which displays  
on the HMD. 2 will do the same as 1, but close all open [HMDs](HMDs) and  
shutdown the complete driver and Oculus runtime - a full cleanup.  
  
  
isOpen = [PsychOculusVR1](PsychOculusVR1)('IsOpen', hmd);  
- Returns 1 if 'hmd' corresponds to an open HMD, 0 otherwise.  
  
  
[PsychOculusVR1](PsychOculusVR1)('[Close](Close)' [, hmd]);  
- [Close](Close) provided HMD device 'hmd'. If no 'hmd' handle is provided,  
all [HMDs](HMDs) will be closed and the driver will be shutdown.  
  
  
[PsychOculusVR1](PsychOculusVR1)('Controllers', hmd);  
- Return a bitmask of all connected controllers: Can be the bitand  
of the OVR.[ControllerType](ControllerType)\_XXX flags described in 'GetInputState'.  
This does not detect if controllers are hot-plugged or unplugged after  
the HMD was opened. Iow. only probed at 'Open'.  
  
  
info = [PsychOculusVR1](PsychOculusVR1)('GetInfo', hmd);  
- Retrieve a struct 'info' with information about the HMD 'hmd'.  
The returned info struct contains at least the following standardized  
fields with information:  
  
handle = Driver internal handle for the specific HMD.  
driver = Function handle to the actual driver for the HMD, e.g., @[PsychOculusVR1](PsychOculusVR1).  
type   = Defines the type/vendor of the device, e.g., 'Oculus'.  
modelName = Name string with the name of the model of the device, e.g., 'Rift DK2'.  
separateEyePosesSupported = 1 if use of [PsychOculusVR1](PsychOculusVR1)('GetEyePose') will improve  
                            the quality of the VR experience, 0 if no improvement  
                            is to be expected, so 'GetEyePose' can be avoided  
                            to save processing time without a loss of quality.  
                            This always returns 1 for at least the Rift DK1 and DK2,  
                            as use of that function can enhance the quality of the  
                            VR experience with fast head movements.  
  
The returned struct may contain more information, but the fields mentioned  
above are the only ones guaranteed to be available over the long run. Other  
fields may disappear or change their format and meaning anytime without  
warning. See 'help PsychVRHMD' for more detailed info about available fields.  
  
  
isSupported = [PsychOculusVR1](PsychOculusVR1)('Supported');  
- Returns 1 if the Oculus driver is functional, 0 otherwise. The  
driver is functional if the VR runtime library was successfully  
initialized and a connection to the VR server process has been  
established. It would return 0 if the server process would not be  
running, or if the required runtime library would not be correctly  
installed.  
  
  
[isVisible, playAreaBounds, [OuterAreaBounds](OuterAreaBounds)] = [PsychOculusVR1](PsychOculusVR1)('VRAreaBoundary', hmd [, requestVisible]);  
- Request visualization of the VR play area boundary for 'hmd' and returns its  
current extents.  
  
'requestVisible' 1 = Request showing the boundary area markers, 0 = Don't  
request showing the markers.  
The driver can not prevent the boundaries to be visualized if some external  
setting asks for their visibility. It can cancel its own request for visibility  
though via 'requestVisible' setting 0.  
  
Returns in 'isVisible' the current visibility status of the VR area boundaries.  
  
'playAreaBounds' is a 3-by-n matrix defining the play area boundaries. Each  
column represents the [x;y;z] coordinates of one 3D definition point. Connecting  
successive points by line segments defines the boundary, as projected onto the  
floor. Points are listed in clock-wise direction. An empty return argument means  
that the play area is so far undefined.  
  
'OuterAreaBounds' defines the outer area boundaries in the same way as  
'playAreaBounds'.  
  
  
[isTriggering, closestDistance, closestPointxyz, surfaceNormal] = [PsychOculusVR1](PsychOculusVR1)('TestVRBoundary', oculusPtr, trackedDeviceType, boundaryType);  
- Return if a tracked device of type 'trackedDeviceType' and associated with 'hmd' is  
colliding with VR area boundaries of 'boundaryType'. This needs the requested devices  
to be online, and the boundaries set up properly, in order to provide meaningful results.  
  
'trackedDeviceType' is a bit-mask (sum) of the following possible constants:  
OVR.[TrackedDevice](TrackedDevice)\_HMD = The HMD headset itself,  
OVR.[TrackedDevice](TrackedDevice)\_LTouch = Left touch controller / left hand.  
OVR.[TrackedDevice](TrackedDevice)\_RTouch = Right touch controller / right hand.  
OVR.[TrackedDevice](TrackedDevice)\_Touch = Any/Both of left and right touch controllers.  
OVR.[TrackedDevice](TrackedDevice)\_Object0 - OVR.[TrackedDevice](TrackedDevice)\_Object3 = Tracked objects 0 - 3.  
OVR.[TrackedDevice](TrackedDevice)\_All = All connected tracked devices.  
  
'boundaryType' 0 = Play area, 1 = Outer boundary.  
  
Return values:  
'isTriggering' 1 if collision is imminent, 0 otherwise.  
'closestDistance' Distance to closest point on boundary.  
'closestPointxyz' [x;y;z] 3D position of closest point on the boundary.  
'surfaceNormal' [nx;ny;nz] 3D surface normal of closest point.  
  
  
[isTriggering, closestDistance, closestPointxyz, surfaceNormal] = [PsychOculusVR1](PsychOculusVR1)('TestVRBoundaryPoint', oculusPtr, pointxyz, boundaryType);  
- Return if a 3D point 'pointxyz' is colliding with VR area boundaries of 'boundaryType'  
on device 'hmd'. This needs the boundaries set up properly, in order to provide meaningful  
results.  
  
'pointxyz' = [x,y,z] 3D point position vector.  
'boundaryType' 0 = Play area, 1 = Outer boundary.  
  
'isTriggering' 1 if 'pointxyz' is colliding / close, 0 otherwise.  
'closestDistance' Distance to closest point on boundary.  
'closestPointxyz' [x;y;z] 3D position of closest point on the boundary.  
'surfaceNormal' [nx;ny;nz] 3D surface normal of closest point.  
  
  
input = [PsychOculusVR1](PsychOculusVR1)('GetInputState', hmd, controllerType);  
- Get input state of controller 'controllerType' associated with HMD 'hmd'.  
  
'controllerType' can be one of OVR.[ControllerType](ControllerType)\_LTouch, OVR.[ControllerType](ControllerType)\_RTouch,  
OVR.[ControllerType](ControllerType)\_Touch, OVR.[ControllerType](ControllerType)\_Remote, OVR.[ControllerType](ControllerType)\_XBox, or  
OVR.[ControllerType](ControllerType)\_Active for selecting whatever controller is currently active.  
  
Return argument 'input' is a struct with fields describing the state of buttons and  
other input elements of the specified 'controllerType'. It has the following fields:  
  
'Valid' = 1 if 'input' contains valid results, 0 if input status is invalid/unavailable.  
'ActiveInputs' = Bitmask defining which of the following struct elements do contain  
meaningful input from actual physical input source devices. This is a more fine-grained  
reporting of what 'Valid' conveys, split up into categories. The following flags will be  
logical or'ed together if the corresponding input category is valid, ie. provided with  
actual input data from some physical input source element, controller etc.:  
  
+1  = 'Buttons' gets input from some real buttons or switches, ie. Touch / [XBox](XBox) / Oculus remote controller.  
+2  = 'Touches' gets input from some real touch sensors or gesture recognizers, e.g., Touch controller.  
+4  = 'Trigger' gets input from some real analog trigger sensor, e.g., Touch or [XBox](XBox) controller.  
+8  = 'Grip' gets input from Touch controllers.  
+16 = 'Thumbstick' gets input from some real thumbstick, e.g., from Touch controllers or [XBox](XBox) controller.  
  
'Time' Time of last input state change of controller.  
'Buttons' Vector with button state on the controller, similar to the 'keyCode'  
vector returned by [KbCheck](KbCheck)() for regular keyboards. Each position in the vector  
reports pressed (1) or released (0) state of a specific button. Use the OVR.Button\_XXX  
constants to map buttons to positions.  
  
'Touches' Like 'Buttons' but for touch buttons. Use the OVR.Touch\_XXX constants to map  
touch points to positions.  
  
'Trigger'(1/2) = Left (1) and Right (2) trigger: Value range 0.0 - 1.0, filtered and with dead-zone.  
'TriggerNoDeadzone'(1/2) = Left (1) and Right (2) trigger: Value range 0.0 - 1.0, filtered.  
'TriggerRaw'(1/2) = Left (1) and Right (2) trigger: Value range 0.0 - 1.0, raw values unfiltered.  
'Grip'(1/2) = Left (1) and Right (2) grip button: Value range 0.0 - 1.0, filtered and with dead-zone.  
'GripNoDeadzone'(1/2) = Left (1) and Right (2) grip button: Value range 0.0 - 1.0, filtered.  
'GripRaw'(1/2) = Left (1) and Right (2) grip button: Value range 0.0 - 1.0, raw values unfiltered.  
  
'Thumbstick' = 2x2 matrix: Column 1 contains left thumbsticks [x;y] axis values, column 2 contains  
 right sticks [x;y] axis values. Values are in range -1 to +1, filtered and with deadzone applied.  
'ThumbstickNoDeadzone' = Like 'Thumbstick', filtered, but without a deadzone applied.  
'ThumbstickRaw' = 'Thumbstick' raw date without deadzone or filtering applied.  
  
  
pulseEndTime = [PsychOculusVR1](PsychOculusVR1)('HapticPulse', hmd, controllerType [, duration=2.5][, freq=1.0][, amplitude=1.0]);  
- Trigger a haptic feedback pulse, some controller vibration, on the specified 'controllerType'  
associated with the specified 'hmd'. 'duration' is pulse duration in seconds, by default a maximum  
of 2.5 seconds is executed. 'freq' is normalized frequency in range 0.0 - 1.0. A value of 0 will  
disable an ongoing pulse. As of Oculus runtime version 1.11, only freq values 0.5 and 1.0 are  
reproduced. Other freq values will be clamped/quantized to those values. 'amplitude' is the  
amplitude of the vibration in normalized 0.0 - 1.0 range.  
  
NOTE: As of November 2018, Oculus SDK 1.16, runtime 1.32, this works very unreliably, and  
often not at all at least with the tested [XBox](XBox) controller!  
  
'pulseEndTime' returns the expected stop time of vibration in seconds, given the parameters.  
Currently the function will return immediately for a (default) 'duration' of 2.5 seconds, and the pulse  
will end after 2.5 seconds. Smaller 'duration' values will block the execution of the function  
until the 'duration' has passed on some types of controllers.  
  
  
state = [PsychOculusVR1](PsychOculusVR1)('PrepareRender', hmd [, userTransformMatrix][, reqmask=1][, targetTime]);  
- Mark the start of the rendering cycle for a new 3D rendered stereoframe.  
Return a struct 'state' which contains various useful bits of information  
for 3D stereoscopic rendering of a scene, based on head tracking data.  
  
'hmd' is the handle of the HMD which delivers tracking data and receives the  
rendered content for display.  
  
'reqmask' defines what kind of information is requested to be returned in  
struct 'state'. Only query information you actually need, as computing some  
of this info is expensive! See below for supported values for 'reqmask'.  
  
'targetTime' is the expected time at which the rendered frame will display.  
This could potentially be used by the driver to make better predictions of  
camera/eye/head pose for the image. Omitting the value will use a target time  
that is implementation specific, but known to give generally good results,  
e.g., the midpoint of scanout of the next video frame.  
  
'userTransformMatrix' is an optional 4x4 right hand side (RHS) transformation  
matrix. It gets applied to the tracked head pose as a global transformation  
before computing results based on head pose like, e.g., camera transformations.  
You can use this to translate the "virtual head" and thereby the virtual eyes/  
cameras in the 3D scene, so observer motion is not restricted to the real world  
tracking volume of your headset. A typical 'userTransformMatrix' would be a  
combined translation and rotation matrix to position the observer at some  
3D location in space, then define his/her global looking direction, aka as  
heading angle, yaw orientation, or rotation around the y-axis in 3D space.  
Head pose tracking results would then operate relative to this global transform.  
If 'userTransformMatrix' is left out, it will default to an identity transform,  
in other words, it will do nothing.  
  
  
state always contains a field state.tracked, whose bits signal the status  
of head tracking for this frame. A +1 flag means that head orientation is  
tracked. A +2 flag means that head position is tracked via some absolute  
position tracker like, e.g., the Oculus Rift DK2 or Rift CV1 camera. A +128  
flag means the HMD is actually strapped onto the subjects head and displaying  
our visual content. Lack of this flag means the HMD is off and thereby blanked  
and dark, or we lost access to it to another application.  
  
state also always contains a field state.[SessionState](SessionState), whose bits signal general  
VR session status:  
+1  = Our rendering goes to the HMD, ie. we have control over it. Lack of this could  
      mean the Health and Safety warning is displaying at the moment and waiting for  
      acknowledgement, or the Oculus GUI application is in control.  
+2  = HMD is present and active.  
+4  = HMD is strapped onto users head. A Rift CV1 would switch off/blank if not on the head.  
+8  = [DisplayLost](DisplayLost) condition! Some hardware/software malfunction, need to completely quit this  
      Psychtoolbox session to recover from this.  
+16 = [ShouldQuit](ShouldQuit) The user interface / user asks us to voluntarily terminate this session.  
+32 = [ShouldRecenter](ShouldRecenter) = The user interface asks us to recenter/recalibrate our tracking origin.  
  
### 'reqmask' defaults to 1 and can have the following values added together:  
  
+1 = Return matrices for left and right "eye cameras" which can be directly  
     used as [OpenGL](OpenGL) GL\_MODELVIEW matrices for rendering the scene. 4x4 matrices  
     for left- and right eye are contained in state.modelView{1} and {2}.  
  
     Return position and orientation 4x4 camera view matrices which describe  
     position and orientation of the "eye cameras" relative to the world  
     reference frame. They are the inverses of state.modelView{}. These  
     matrices can be directly used to define cameras for rendering of complex  
     3D scenes with the [Horde3D](Horde3D) 3D engine. Left- and right eye matrices are  
     contained in state.cameraView{1} and {2}.  
  
     Additionally tracked/predicted head pose is returned in state.localHeadPoseMatrix  
     and the global head pose after application of the 'userTransformMatrix' is  
     returned in state.globalHeadPoseMatrix - this is the basis for computing  
     the camera transformation matrices.  
  
+2 = Return matrices for tracked left and right hands of user, ie. of tracked positions  
     and orientations of left and right Oculus touch controllers, if any.  
  
     state.handStatus(1) = Tracking status of left hand: 0 = Untracked, 1 = Orientation  
                           tracked, 2 = Position tracked, 3 = Orientation and position  
                           tracked. If handStatus is == 0 then all the following information  
                           is invalid and can not be used in any meaningful way.  
     state.handStatus(2) = Tracking status of right hand.  
  
     state.localHandPoseMatrix{1} = 4x4 [OpenGL](OpenGL) right handed reference frame matrix with  
                                    hand position and orientation encoded to define a  
                                    proper GL\_MODELVIEW transform for rendering stuff  
                                    "into"/"relative to" the oriented left hand.  
     state.localHandPoseMatrix{2} = Ditto for the right hand.  
  
     state.globalHandPoseMatrix{1} = userTransformMatrix \* state.localHandPoseMatrix{1};  
                                     Left hand pose transformed by passed in userTransformMatrix.  
     state.globalHandPoseMatrix{2} = Ditto for the right hand.  
  
     state.globalHandPoseInverseMatrix{1} = Inverse of globalHandPoseMatrix{1} for collision  
                                            testing/grasping of virtual objects relative to  
                                            hand pose of left hand.  
     state.globalHandPoseInverseMatrix{2} = Ditto for right hand.  
  
More flags to follow...  
  
  
eyePose = [PsychOculusVR1](PsychOculusVR1)('GetEyePose', hmd, renderPass [, userTransformMatrix][, targetTime]);  
- Return a struct 'eyePose' which contains various useful bits of information  
for 3D stereoscopic rendering of the stereo view of one eye, based on head  
tracking data. This function provides essentially the same information as  
the 'PrepareRender' function, but only for one eye. Therefore you will need  
to call this function twice, once for each of the two renderpasses, at the  
beginning of each renderpass.  
  
'hmd' is the handle of the HMD which delivers tracking data and receives the  
rendered content for display.  
  
'renderPass' defines if information should be returned for the 1st renderpass  
(renderPass == 0) or for the 2nd renderpass (renderPass == 1). The driver will  
decide for you if the 1st renderpass should render the left eye and the 2nd  
pass the right eye, or if the 1st renderpass should render the right eye and  
then the 2nd renderpass the left eye. The ordering depends on the properties  
of the video display of your HMD, specifically on the video scanout order:  
Is it right to left, left to right, or top to bottom? For each scanout order  
there is an optimal order for the renderpasses to minimize perceived lag.  
  
'targetTime' is the expected time at which the rendered frame will display.  
This could potentially be used by the driver to make better predictions of  
camera/eye/head pose for the image. Omitting the value will use a target time  
that is implementation specific, but known to give generally good results.  
  
'userTransformMatrix' is an optional 4x4 right hand side (RHS) transformation  
matrix. It gets applied to the tracked head pose as a global transformation  
before computing results based on head pose like, e.g., camera transformations.  
You can use this to translate the "virtual head" and thereby the virtual eyes/  
cameras in the 3D scene, so observer motion is not restricted to the real world  
tracking volume of your headset. A typical 'userTransformMatrix' would be a  
combined translation and rotation matrix to position the observer at some  
3D location in space, then define his/her global looking direction, aka as  
heading angle, yaw orientation, or rotation around the y-axis in 3D space.  
Head pose tracking results would then operate relative to this global transform.  
If 'userTransformMatrix' is left out, it will default to an identity transform,  
in other words, it will do nothing.  
  
### Return values in struct 'eyePose':  
  
'eyeIndex' The eye for which this information applies. 0 = Left eye, 1 = Right eye.  
           You can pass 'eyeIndex' into the [Screen](Screen)('SelectStereoDrawBuffer', win, eyeIndex)  
           to select the proper eye target render buffer.  
  
'modelView' is a 4x4 RHS [OpenGL](OpenGL) matrix which can be directly used as [OpenGL](OpenGL)  
            GL\_MODELVIEW matrix for rendering the scene.  
  
'cameraView' contains a 4x4 RHS camera matrix which describes position and  
             orientation of the "eye camera" relative to the world reference  
             frame. It is the inverse of eyePose.modelView. This matrix can  
             be directly used to define the camera for rendering of complex  
             3D scenes with the [Horde3D](Horde3D) 3D engine or other engines which want  
             absolute camera pose instead of the inverse matrix.  
  
  
trackers = [PsychOculusVR1](PsychOculusVR1)('GetTrackersState', hmd);  
- Return a struct array with infos about all connected tracking cameras/sensors  
for 'hmd'.  
  
  
success = [PsychOculusVR1](PsychOculusVR1)('RecenterTrackingOrigin', hmd);  
- Recenter the tracking origin for the 'hmd', based on its current position and  
orientation. Returns 'success' = 1 on success, 0 on failure to recenter. One  
reason for failure could be that the HMD wasn't roughly level, but instead was  
facing upward or downward, which is not allowed. This function also gets automatically  
triggered if the Oculus GUI or other user input requests a recenter. Recenter would then  
be auto-triggered during a call to 'PrepareRender'.  
  
  
oldType = [PsychOculusVR1](PsychOculusVR1)('TrackingOriginType', hmd [, newType]);  
- Specify the type of tracking origin for Oculus device 'oculusPtr'.  
This returns the current type of tracking origin in 'oldType'.  
Optionally you can specify a new tracking origin type as 'newType'.  
Type must be either:  
0 = Origin is at eye height (HMD height).  
1 = Origin is at floor height.  
The eye height or floor height gets defined by the system during  
calls to 'RecenterTrackingOrigin' and during sensor calibration in  
the Oculus GUI application.  
  
  
[adaptiveGpuPerformanceScale, frameStats, anyFrameStatsDropped, aswIsAvailable] = [PsychOculusVR1](PsychOculusVR1)('GetPerformanceStats', hmd);  
- Return global and per-frame performance statistics for the given 'hmd'.  
  
  
[PsychOculusVR1](PsychOculusVR1)('SetupRenderingParameters', hmd [, basicTask='Tracked3DVR'][, basicRequirements][, basicQuality=0][, fov=[[HMDRecommended](HMDRecommended)]][, pixelsPerDisplay=1])  
- Query the HMD 'hmd' for its properties and setup internal rendering  
parameters in preparation for opening an onscreen window with [PsychImaging](PsychImaging)  
to display properly on the HMD. See section about 'AutoSetupHMD' above for  
the meaning of the optional parameters 'basicTask', 'basicRequirements'  
and 'basicQuality'.  
  
'fov' Optional field of view in degrees, from line of sight: [leftdeg, rightdeg,  
updeg, downdeg]. If 'fov' is omitted, the HMD runtime will be asked for a  
good default field of view and that will be used. The field of view may be  
dependent on the settings in the HMD user profile of the currently selected  
user.  
  
'pixelsPerDisplay' Ratio of the number of render target pixels to display pixels  
at the center of distortion. Defaults to 1.0 if omitted. Lower values can  
improve performance, at lower quality.  
  
  
[PsychOculusVR1](PsychOculusVR1)('SetBasicQuality', hmd, basicQuality);  
- Set basic level of quality vs. required GPU performance.  
  
  
oldValues = [PsychOculusVR1](PsychOculusVR1)('FloatsProperty', hmd, property [, newValues]);  
- Get current values 'oldValues' and optionally set new values 'newValues'  
for a floating point array property with name 'property' on 'hmd'.  
  
'property' name strings are defined under OVR.KEY\_XXX. As of SDK version 1.11,  
the following floats properties exist:  
OVR.KEY\_PLAYER\_HEIGHT = [Height] of subject in meters.  
OVR.KEY\_EYE\_HEIGHT = [Height] of eyes of subject above ground in meters.  
OVR.KEY\_NECK\_TO\_EYE\_DISTANCE = [horizontal, vertical] neck to eye distance in meters.  
OVR.KEY\_EYE\_TO\_NOSE\_DISTANCE = [horizontal, vertical] eye to nose distance in meters.  
  
  
oldString = [PsychOculusVR1](PsychOculusVR1)('StringProperty', hmd, property [, defaultString][, newString]);  
- Get current string 'oldString' and optionally set new string 'newString'  
for a string property with name 'property' on 'hmd'. If the property does not  
exist yet or does not have a string value assigned, optionally return 'defaultString'.  
  
'property' name strings are defined under OVR.KEY\_XXX. As of SDK version 1.11,  
the following string properties exist:  
OVR.KEY\_USER = User name.  
OVR.KEY\_NAME = Name.  
OVR.KEY\_GENDER = Gender 'Male', 'Female', or 'Unknown'.  
OVR.KEY\_DEFAULT\_GENDER = 'Unknown'.  
  
  
oldSetting = [PsychOculusVR1](PsychOculusVR1)('SetFastResponse', hmd [, enable]);  
- Return old setting for 'FastResponse' mode in 'oldSetting',  
optionally disable or enable the mode via specifying the 'enable'  
parameter as 0 or greater than zero.  
  
Deprecated: This function does nothing. It just exists for (backwards)  
compatibility with the old Oculus driver and [PsychVRHMD](PsychVRHMD).  
  
  
oldSetting = [PsychOculusVR1](PsychOculusVR1)('SetTimeWarp', hmd [, enable]);  
- Return old setting for 'TimeWarp' mode in 'oldSetting',  
optionally enable or disable the mode via specifying the 'enable'  
parameter as 1 or 0.  
  
Deprecated: This function does nothing. It just exists for (backwards)  
compatibility with the old Oculus driver and [PsychVRHMD](PsychVRHMD).  
  
  
oldSetting = [PsychOculusVR1](PsychOculusVR1)('SetLowPersistence', hmd [, enable]);  
- Return old setting for 'LowPersistence' mode in 'oldSetting',  
optionally enable or disable the mode via specifying the 'enable'  
parameter as 1 or 0.  
  
Deprecated: This function does nothing. It just exists for (backwards)  
compatibility with the old Oculus driver and [PsychVRHMD](PsychVRHMD).  
  
  
oldSettings = [PsychOculusVR1](PsychOculusVR1)('PanelOverdriveParameters', hmd [, newparams]);  
Deprecated: This function does nothing. It just exists for (backwards)  
compatibility with the old Oculus driver and [PsychVRHMD](PsychVRHMD).  
  
- Return old settings for panel overdrive mode in 'oldSettings',  
optionally set new settings in 'newparams'. This changes the operating  
parameters of OLED panel overdrive on the Rift DK-2 if 'FastResponse'  
mode is active. newparams is a vector [upscale, downscale, gamma] with  
the following meaning: gamma = 1 Use gamma/degamma pass to perform  
overdrive boost in gamma 2.2 corrected space. This is the startup default.  
upscale = How much should rising pixel color intensity values be boosted.  
Default is 0.10 for a 10% boost.  
downscale = How much should rising pixel color intensity values be reduced.  
Default is 0.05 for a 5% reduction.  
The Rift DK-2 OLED panel controller is slower on rising intensities than on  
falling intensities, therefore the higher boost on rising than on falling  
direction.  
  
  
[PsychOculusVR1](PsychOculusVR1)('SetHSWDisplayDismiss', hmd [, dismissTypes=1+2+4]);  
- Set how the user can dismiss the "Health and safety warning display".  
Deprecated: This function does nothing. It just exists for (backwards)  
compatibility with the old Oculus driver and [PsychVRHMD](PsychVRHMD). The current [OculusVR](OculusVR)  
runtime 1.0 enforces display of the Health and Safety Warning at the beginning  
of each VR session.  
  
  
[PsychOculusVR1](PsychOculusVR1)('SetHUDState', hmd, mode);  
- Set mode of operation for the builtin head up display (HUD) for performance  
information. The HUD is automatically displayed and updated by the VR compositor  
if enabled, and can be in one of the following selectable 'mode's:  
  
0 = Head up display HUD off ie. invisible.  
1 = HUD shows performance summary.  
2 = HUD shows latency timing.  
3 = HUD shows application render timing.  
4 = HUD shows VR compositor render timing.  
5 = HUD shows Version information of different components.  
6 = HUD shows Asynchronous time warp (ASW) stats.  
Higher numbers may do something useful in the future.  
  
  
[bufferSize, imagingFlags, stereoMode] = [PsychOculusVR1](PsychOculusVR1)('GetClientRenderingParameters', hmd);  
- Retrieve recommended size in pixels 'bufferSize' = [width, height] of the client  
renderbuffer for each eye for rendering to the HMD. Returns parameters  
previously computed by [PsychOculusVR1](PsychOculusVR1)('SetupRenderingParameters', hmd).  
  
Also returns 'imagingFlags', the required imaging mode flags for setup of  
the [Screen](Screen) imaging pipeline. Also returns the needed 'stereoMode' for the  
pipeline.  
  
  
needPanelFitter = [PsychOculusVR1](PsychOculusVR1)('GetPanelFitterParameters', hmd);  
- 'needPanelFitter' is 1 if a custom panel fitter tasks is needed, and 'bufferSize'  
from the [PsychVRHMD](PsychVRHMD)('GetClientRenderingParameters', hmd); defines the size of the  
clientRect for the onscreen window. 'needPanelFitter' is 0 if no panel fitter is  
needed.  
  
  
[winRect, ovrfbOverrideRect, ovrSpecialFlags, ovrMultiSample] = [PsychOculusVR1](PsychOculusVR1)('OpenWindowSetup', hmd, screenid, winRect, ovrfbOverrideRect, ovrSpecialFlags, ovrMultiSample);  
- Compute special override parameters for given input/output arguments, as needed  
for a specific HMD. Take other preparatory steps as needed, immediately before the  
[Screen](Screen)('OpenWindow') command executes. This is called as part of [PsychImaging](PsychImaging)('OpenWindow'),  
with the user provided hmd, screenid, winRect etc.  
  
  
isOutput = [PsychOculusVR1](PsychOculusVR1)('IsHMDOutput', hmd, scanout);  
- Returns 1 (true) if 'scanout' describes the video output to which the  
HMD 'hmd' is connected. 'scanout' is a struct returned by the [Screen](Screen)  
function [Screen](Screen)('ConfigureDisplay', 'Scanout', screenid, outputid);  
This allows probing video outputs to find the one which feeds the HMD.  
Deprecated: This function does nothing. It just exists for (backwards)  
compatibility with the old Oculus driver and [PsychVRHMD](PsychVRHMD).  
  
  
[headToEyeShiftv, headToEyeShiftMatrix] = [PsychOculusVR1](PsychOculusVR1)('GetEyeShiftVector', hmd, eye);  
- Retrieve 3D translation vector [tx, ty, tz] that defines the 3D position of the given  
eye 'eye' for the given HMD 'hmd', relative to the origin of the local head/HMD  
reference frame. This is needed to translate a global head pose into a eye  
pose, e.g., to translate the output of [PsychOculusVR1](PsychOculusVR1)('GetEyePose') into actual  
tracked/predicted eye locations for stereo rendering.  
  
In addition to the 'headToEyeShiftv' vector, a corresponding 4x4 translation  
matrix is also returned in 'headToEyeShiftMatrix' for convenience.  
  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/PsychVRToolbox/PsychOculusVR1.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/PsychVRToolbox/PsychOculusVR1.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/PsychVRToolbox/PsychOculusVR1.m</code>
</div>

