# [PsychOculusVR](PsychOculusVR)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[PsychVRToolbox](PsychVRToolbox)

[PsychOculusVR](PsychOculusVR) - A high level driver for Oculus VR hardware.  
  
Oculus VR's trademarks, e.g., Oculus, Oculus Rift, etc. are registered trademarks  
owned by Oculus VR, LLC.  
  
Note: If you want to write VR code that is portable across  
VR headsets of different vendors, then use the [PsychVRHMD](PsychVRHMD)()  
driver instead of this driver. The [PsychVRHMD](PsychVRHMD) driver will use  
this driver as appropriate when connecting to a Oculus Rift  
or similar Oculus device, but it will also automaticaly work  
with other head mounted displays. This driver does however  
expose a few functions specific to Oculus hardware, so you can  
mix calls to this driver with calls to [PsychVRHMD](PsychVRHMD) to do some  
mix & match.  
  
For setup instructions for Oculus [HMDs](HMDs) see "help [OculusVR](OculusVR)".  
  
  
### Usage:  
  
oldverbosity = [PsychOculusVR](PsychOculusVR)('Verbosity' [, newverbosity]);  
- Get/Set level of verbosity for driver status messages, warning messages,  
error messages etc. 'newverbosity' is the optional new verbosity level,  
'oldverbosity' is the currently set verbosity level - ie. before changing  
it.  Valid settings are: 0 = Silent, 1 = Errors only, 2 = Warnings, 3 = Info,  
4 = Debug.  
  
  
hmd = [PsychOculusVR](PsychOculusVR)('AutoSetupHMD' [, basicTask='Tracked3DVR'][, basicRequirements][, basicQuality=0][, deviceIndex]);  
- Open a Oculus HMD, set it up with good default rendering and  
display parameters and generate a [PsychImaging](PsychImaging)('AddTask', ...)  
line to setup the Psychtoolbox imaging pipeline for proper display  
on the HMD. This will also cause the device connection to get  
auto-closed as soon as the onscreen window which displays on  
the HMD is closed. Returns the 'hmd' handle of the HMD on success.  
  
By default, the first detected HMD will be used and if no VR HMD  
is connected, it will open an emulated/simulated one for basic  
testing and debugging. You can override this default choice of  
HMD by specifying the optional 'deviceIndex' parameter to choose  
a specific HMD.  
  
More optional parameters: 'basicTask' what kind of task should be implemented.  
The default is 'Tracked3DVR', which means to setup for stereoscopic 3D  
rendering, driven by head motion tracking, for a fully immersive experience  
in some kind of 3D virtual world. This is the default if omitted. The task  
'Stereoscopic' sets up for display of stereoscopic stimuli, but without  
head tracking. 'Monoscopic' sets up for display of monocular stimuli, ie.  
the HMD is just used as a special kind of standard display monitor.  
  
'basicRequirements' defines basic requirements for the task. Currently  
defined are the following strings which can be combined into a single  
'basicRequirements' string: 'LowPersistence' = Try to keep exposure  
time of visual images on the retina low if possible, ie., try to approximate  
a pulse-type display instead of a hold-type display if possible. This has  
no effect on the Rift DK1. On the Rift DK2 it will enable low persistence  
scanning of the OLED display panel, to light up each pixel only a fraction  
of a video refresh cycle duration.  
  
'PerEyeFOV' = Request use of per eye individual and asymmetric fields of view even  
when the 'basicTask' was selected to be 'Monoscopic' or 'Stereoscopic'. This allows  
for wider field of view in these tasks, but requires the usercode to adapt to these  
different and asymmetric fields of view for each eye, e.g., by selecting proper 3D  
projection matrices for each eye.  
  
'FastResponse' = Try to switch images with minimal delay and fast  
pixel switching time. This will enable OLED panel overdrive processing  
on the Oculus Rift DK1 and DK2. OLED panel overdrive processing is a  
relatively expensive post processing step.  
  
'TimingSupport' = Support some hardware specific means of timestamping  
or latency measurements. On the Rift DK1 this does nothing. On the DK2  
it enables dynamic prediction and timing measurements with the Rifts internal  
latency tester.  
  
'TimeWarp' = Enable per eye image 2D timewarping via prediction of eye  
poses at scanout time. This mostly only makes sense for head-tracked 3D  
rendering. Depending on 'basicQuality' a more cheap or more expensive  
procedure is used.  
  
'basicQuality' defines the basic tradeoff between quality and required  
computational power. A setting of 0 gives lowest quality, but with the  
lowest performance requirements. A setting of 1 gives maximum quality at  
maximum computational load. Values between 0 and 1 change the quality to  
performance tradeoff.  
  
  
hmd = [PsychOculusVR](PsychOculusVR)('Open' [, deviceIndex], ...);  
- Open HMD with index 'deviceIndex'. See [PsychOculusVRCore](PsychOculusVRCore) Open?  
for help on additional parameters.  
  
  
[PsychOculusVR](PsychOculusVR)('SetAutoClose', hmd, mode);  
- Set autoclose mode for HMD with handle 'hmd'. 'mode' can be  
0 (this is the default) to not do anything special. 1 will close  
the HMD 'hmd' when the onscreen window is closed which displays  
on the HMD. 2 will do the same as 1, but close all open [HMDs](HMDs) and  
shutdown the complete driver and Oculus runtime - a full cleanup.  
  
  
isOpen = [PsychOculusVR](PsychOculusVR)('IsOpen', hmd);  
- Returns 1 if 'hmd' corresponds to an open HMD, 0 otherwise.  
  
  
[PsychOculusVR](PsychOculusVR)('[Close](Close)' [, hmd])  
- [Close](Close) provided HMD device 'hmd'. If no 'hmd' handle is provided,  
all [HMDs](HMDs) will be closed and the driver will be shutdown.  
  
  
[PsychOculusVR](PsychOculusVR)('Controllers', hmd);  
- Return a bitmask of all connected controllers: Can be the bitand  
of the OVR.[ControllerType](ControllerType)\_XXX flags described in 'GetInputState'.  
This does not detect if controllers are hot-plugged or unplugged after  
the HMD was opened. Iow. only probed at 'Open'.  
As the classic Oculus driver does not support dedicated controllers at the  
moment, this always returns 0.  
  
  
info = [PsychOculusVR](PsychOculusVR)('GetInfo', hmd);  
- Retrieve a struct 'info' with information about the HMD 'hmd'.  
The returned info struct contains at least the following standardized  
fields with information:  
handle = Driver internal handle for the specific HMD.  
driver = Function handle to the actual driver for the HMD, e.g., @[PsychOculusVR](PsychOculusVR).  
type   = Defines the type/vendor of the device, e.g., 'Oculus'.  
modelName = Name string with the name of the model of the device, e.g., 'Rift DK2'.  
separateEyePosesSupported = 1 if use of [PsychOculusVR](PsychOculusVR)('GetEyePose') will improve  
                            the quality of the VR experience, 0 if no improvement  
                            is to be expected, so 'GetEyePose' can be avoided  
                            to save processing time without a loss of quality.  
                            This always returns 1 for at least the Rift DK1 and DK2,  
                            as use of that function can enhance the quality of the  
                            VR experience with fast head movements.  
  
The returned struct may contain more information, but the fields mentioned  
above are the only ones guaranteed to be available over the long run. Other  
fields may disappear or change their format and meaning anytime without  
warning.  
  
  
isSupported = [PsychOculusVRCore](PsychOculusVRCore)('Supported');  
- Returns 1 if the Oculus driver is functional, 0 otherwise. The  
driver is functional if the VR runtime library was successfully  
initialized and a connection to the VR server process has been  
established. It would return 0 if the server process would not be  
running, or if the required runtime library would not be correctly  
installed.  
  
  
[isVisible, playAreaBounds, [OuterAreaBounds](OuterAreaBounds)] = [PsychOculusVRCore](PsychOculusVRCore)('VRAreaBoundary', hmd [, requestVisible]);  
- Request visualization of the VR play area boundary for 'hmd' and returns its  
current extents.  
  
As VR area boundaries are not actually supported by this Oculus classic driver,  
this function returns no-op results, compatible with what the new Oculus driver  
would return if the Oculus guardian system would not be set up, e.g., because the  
hardware setup does not include Oculus touch controllers.  
  
The input flag 'requestVisible' is silently ignored:  
'requestVisible' 1 = Request showing the boundary area markers, 0 = Don't  
request showing the markers.  
  
Returns in 'isVisible' the current visibility status of the VR area boundaries.  
This is always 0 for "invisible".  
  
'playAreaBounds' is an empty matrix defining the play area boundaries. The empty  
return argument means that the play area is so far undefined on this driver.  
  
'OuterAreaBounds' defines the outer area boundaries in the same way as  
'playAreaBounds'. In other words, it always returns an empty matrix.  
  
  
input = [PsychOculusVRCore](PsychOculusVRCore)('GetInputState', hmd, controllerType);  
- Get input state of controller 'controllerType' associated with HMD 'hmd'.  
  
As this driver does not actually support special VR controllers, only a minimally  
useful 'input' state is returned for compatibility with other drivers, which is  
based on emulating or faking input from real controllers, so this function will be  
of limited use. Specifically, only the input.Valid, input.Time and input.Buttons fields are  
returned, all other fields are missing. input.Buttons maps defined OVR.Button\_XXX  
fields to similar or corresponding buttons on the regular keyboard.  
  
'controllerType' can be one of OVR.[ControllerType](ControllerType)\_LTouch, OVR.[ControllerType](ControllerType)\_RTouch,  
OVR.[ControllerType](ControllerType)\_Touch, OVR.[ControllerType](ControllerType)\_Remote, OVR.[ControllerType](ControllerType)\_XBox, or  
OVR.[ControllerType](ControllerType)\_Active for selecting whatever controller is currently active.  
  
Return argument 'input' is a struct with fields describing the state of buttons and  
other input elements of the specified 'controllerType'. It has the following fields:  
  
'Valid' = 1 if 'input' contains valid results, 0 if input status is invalid/unavailable.  
'Time' Time of last input state change of controller.  
'Buttons' Vector with button state on the controller, similar to the 'keyCode'  
vector returned by [KbCheck](KbCheck)() for regular keyboards. Each position in the vector  
reports pressed (1) or released (0) state of a specific button. Use the OVR.Button\_XXX  
constants to map buttons to positions.  
  
  
pulseEndTime = [PsychOculusVR](PsychOculusVR)('HapticPulse', hmd, controllerType [, duration=2.5][, freq=1.0][, amplitude=1.0]);  
- Fake triggering a haptic feedback pulse. This does nothing, but return a made up  
but consistent 'pulseEndTime', as this classic Oculus driver does not support haptic  
feedback.  
  
  
state = [PsychOculusVRCore](PsychOculusVRCore)('PrepareRender', hmd [, userTransformMatrix][, reqmask=1][, targetTime]);  
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
position tracker like, e.g., the Oculus Rift DK2 camera.  
  
state always contains a field state.tracked, whose bits signal the status  
of head tracking for this frame. A +1 flag means that head orientation is  
tracked. A +2 flag means that head position is tracked via some absolute  
position tracker like, e.g., the Oculus Rift DK2 camera. We also return a +128  
flag which means the HMD is actually strapped onto the subjects head and displaying  
our visual content. We can't detect actual HMD display state, but do this for  
compatibility to other drivers.  
  
state also always contains a field state.[SessionState](SessionState), whose bits signal general  
VR session status. In our case we always return +7 on this classic Oculus driver,  
as we can't detect [ShouldQuit](ShouldQuit), [ShouldRecenter](ShouldRecenter) or [DisplayLost](DisplayLost) conditions, neither  
if the HMD is strapped to the users head.  
  
+1  = Our rendering goes to the HMD, ie. we have control over it. Lack of this could  
      mean the Health and Safety warning is displaying at the moment and waiting for  
      acknowledgement, or the Oculus GUI application is in control.  
+2  = HMD is present and active.  
+4  = HMD is strapped onto users head. E.g., a Oculus Rift CV1 would switch off/blank  
      if not on the head.  
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
     and orientations of left and right hand tracking controllers, if any. As the old  
     driver does not support hand tracking, this reports hard-coded neutral results and  
     reports a state.handStatus of 0 = "Not tracked/Invalid data".  
  
     state.handStatus(1) = Tracking status of left hand: 0 = Untracked, signalling that  
                           all the following information is invalid and can not be used  
                           in any meaningful way.  
  
     state.handStatus(2) = Tracking status of right hand. 0 = Untracked.  
  
     state.localHandPoseMatrix{1} = 4x4 [OpenGL](OpenGL) right handed reference frame matrix with  
                                    hand position and orientation encoded to define a  
                                    proper GL\_MODELVIEW transform for rendering stuff  
                                    "into"/"relative to" the oriented left hand. Always  
                                    a 4x4 unit identity matrix for hand resting in origin.  
  
     state.localHandPoseMatrix{2} = Ditto for the right hand.  
  
     state.globalHandPoseMatrix{1} = userTransformMatrix \* state.localHandPoseMatrix{1};  
                                     Left hand pose transformed by passed in userTransformMatrix.  
  
     state.globalHandPoseMatrix{2} = Ditto for the right hand.  
  
     state.globalHandPoseInverseMatrix{1} = Inverse of globalHandPoseMatrix{1} for collision  
                                            testing/grasping of virtual objects relative to  
                                            hand pose of left hand.  
  
     state.globalHandPoseInverseMatrix{2} = Ditto for right hand.  
  
More flags to follow...  
  
  
eyePose = [PsychOculusVR](PsychOculusVR)('GetEyePose', hmd, renderPass [, userTransformMatrix][, targetTime]);  
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
  
Additionally tracked/predicted head pose is returned in eyePose.localHeadPoseMatrix  
and the global head pose after application of the 'userTransformMatrix' is  
returned in eyePose.globalHeadPoseMatrix - this is the basis for computing  
the camera transformation matrix.  
  
  
[PsychOculusVR](PsychOculusVR)('SetupRenderingParameters', hmd [, basicTask='Tracked3DVR'][, basicRequirements][, basicQuality=0][, fov=[[HMDRecommended](HMDRecommended)]][, pixelsPerDisplay=1])  
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
  
  
[PsychOculusVR](PsychOculusVR)('SetBasicQuality', hmd, basicQuality);  
- Set basic level of quality vs. required GPU performance.  
  
  
oldSetting = [PsychOculusVR](PsychOculusVR)('SetFastResponse', hmd [, enable]);  
- Return old setting for 'FastResponse' mode in 'oldSetting',  
optionally disable or enable the mode via specifying the 'enable'  
parameter as 0 or greater than zero. Please note that if you want to  
use 'FastResponse', you must request and thereby enable it at the  
beginning of a session, as the driver must do some neccessary setup  
prep work at startup of the HMD. Once it was initially enabled, you  
can switch the setting at runtime with this function.  
  
Currently implemented are an algorithmic overdrive mode if 'enable'  
is set to 1, and two lookup table (LUT) based modes for 'enable'  
settings of 2 or 3, each selecting a slightly different lookup table.  
  
  
oldSetting = [PsychOculusVR](PsychOculusVR)('SetTimeWarp', hmd [, enable]);  
- Return old setting for 'TimeWarp' mode in 'oldSetting',  
optionally enable or disable the mode via specifying the 'enable'  
parameter as 1 or 0. Please note that if you want to use 'TimeWarp',  
you must request and thereby enable it at the beginning of a session, as  
the driver must do some neccessary setup prep work at startup of the HMD.  
Once it was initially enabled, you can switch the setting at runtime with  
this function.  
  
  
oldSetting = [PsychOculusVR](PsychOculusVR)('SetLowPersistence', hmd [, enable]);  
- Return old setting for 'LowPersistence' mode in 'oldSetting',  
optionally enable or disable the mode via specifying the 'enable'  
parameter as 1 or 0.  
  
  
oldSettings = [PsychOculusVR](PsychOculusVR)('PanelOverdriveParameters', hmd [, newparams]);  
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
  
  
[PsychOculusVR](PsychOculusVR)('SetHSWDisplayDismiss', hmd [, dismissTypes=1+2+4]);  
- Set how the user can dismiss the "Health and safety warning display".  
'dismissTypes' can be -1 to disable the HSWD, or a value \>= 0 to show  
the HSWD until a timeout and or until the user dismisses the HSWD.  
The following flags can be added to define type of dismissal:  
  
+0 = Display until timeout, if any. Will wait forever if there isn't any timeout!  
+1 = Dismiss via keyboard keypress.  
+2 = Dismiss via mouse click or mousepad tap.  
+4 = Dismiss via a tap to the HMD (detected via accelerometer).  
  
  
[bufferSize, imagingFlags, stereoMode] = [PsychOculusVR](PsychOculusVR)('GetClientRenderingParameters', hmd);  
- Retrieve recommended size in pixels 'bufferSize' = [width, height] of the client  
renderbuffer for each eye for rendering to the HMD. Returns parameters  
previously computed by [PsychOculusVR](PsychOculusVR)('SetupRenderingParameters', hmd).  
  
Also returns 'imagingFlags', the required imaging mode flags for setup of  
the [Screen](Screen) imaging pipeline. Also returns the needed 'stereoMode' for the  
pipeline.  
  
  
needPanelFitter = [PsychOculusVR](PsychOculusVR)('GetPanelFitterParameters', hmd);  
- 'needPanelFitter' is 1 if a custom panel fitter tasks is needed, and 'bufferSize'  
from the [PsychVRHMD](PsychVRHMD)('GetClientRenderingParameters', hmd); defines the size of the  
clientRect for the onscreen window. 'needPanelFitter' is 0 if no panel fitter is  
needed.  
  
  
[winRect, ovrfbOverrideRect, ovrSpecialFlags] = [PsychOculusVR](PsychOculusVR)('OpenWindowSetup', hmd, screenid, winRect, ovrfbOverrideRect, ovrSpecialFlags);  
- Compute special override parameters for given input/output arguments, as needed  
for a specific HMD. Take other preparatory steps as needed, immediately before the  
[Screen](Screen)('OpenWindow') command executes. This is called as part of [PsychImaging](PsychImaging)('OpenWindow'),  
with the user provided hmd, screenid, winRect etc.  
  
  
isOutput = [PsychOculusVR](PsychOculusVR)('IsHMDOutput', hmd, scanout);  
- Returns 1 (true) if 'scanout' describes the video output to which the  
HMD 'hmd' is connected. 'scanout' is a struct returned by the [Screen](Screen)  
function [Screen](Screen)('ConfigureDisplay', 'Scanout', screenid, outputid);  
This allows probing video outputs to find the one which feeds the HMD.  
  
  
[headToEyeShiftv, headToEyeShiftMatrix] = [PsychOculusVR](PsychOculusVR)('GetEyeShiftVector', hmd, eye);  
- Retrieve 3D translation vector [tx, ty, tz] that defines the 3D position of the given  
eye 'eye' for the given HMD 'hmd', relative to the origin of the local head/HMD  
reference frame. This is needed to translate a global head pose into a eye  
pose, e.g., to translate the output of [PsychOculusVR](PsychOculusVR)('GetEyePose') into actual  
tracked/predicted eye locations for stereo rendering.  
  
In addition to the 'headToEyeShiftv' vector, a corresponding 4x4 translation  
matrix is also returned in 'headToEyeShiftMatrix' for convenience.  
  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/PsychVRToolbox/PsychOculusVR.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/PsychVRToolbox/PsychOculusVR.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/PsychVRToolbox/PsychOculusVR.m</code>
</div>

