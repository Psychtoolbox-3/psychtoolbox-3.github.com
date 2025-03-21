# [PsychOpenXR](PsychOpenXR)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[PsychVRToolbox](PsychVRToolbox)

[PsychOpenXR](PsychOpenXR) - A high level driver for [OpenXR](OpenXR) supported XR hardware.  
  
Copyright (c) 2022-2025 Mario Kleiner. Licensed to you under the MIT license.  
Our underlying [PsychOpenXRCore](PsychOpenXRCore) mex driver builds against the Khronos [OpenXR](OpenXR) SDK public  
headers, and links against the [OpenXR](OpenXR) open-source dynamic loader, to implement the  
interface to a system-installed [OpenXR](OpenXR) runtime. These components are dual-licensed by  
Khronos under Apache 2.0 and MIT license: SPDX license identifier "Apache-2.0 OR MIT"  
  
Note: If you want to write code that is portable across XR devices of  
different vendors, then use the [PsychVRHMD](PsychVRHMD)() driver instead of this  
driver. The [PsychVRHMD](PsychVRHMD) driver will use this driver as appropriate when  
connecting to a [OpenXR](OpenXR) supported XR device, but it will also  
automatically work with other head mounted displays. This driver does  
however expose a few functions specific to [OpenXR](OpenXR) hardware, so you can  
mix calls to this driver with calls to [PsychVRHMD](PsychVRHMD) to do some mix & match.  
  
For setup instructions for [OpenXR](OpenXR), see "help [OpenXR](OpenXR)".  
  
  
### Usage:  
  
oldverbosity = [PsychOpenXR](PsychOpenXR)('Verbosity' [, newverbosity]);  
- Get/Set level of verbosity for driver status messages, warning messages,  
error messages etc. 'newverbosity' is the optional new verbosity level,  
'oldverbosity' is the currently set verbosity level - ie. before changing  
it.  Valid settings are: 0 = Silent, 1 = Errors only, 2 = Warnings, 3 = Info,  
4 = Debug.  
  
  
hmd = [PsychOpenXR](PsychOpenXR)('AutoSetupHMD' [, basicTask='Tracked3DVR'][, basicRequirements][, basicQuality=0][, deviceIndex]);  
- Open a [OpenXR](OpenXR) device, set it up with good default rendering and  
display parameters and generate a [PsychImaging](PsychImaging)('AddTask', ...)  
line to setup the Psychtoolbox imaging pipeline for proper display  
on the device. This will also cause the device connection to get  
auto-closed as soon as the onscreen window which displays on  
the device is closed. Returns the 'hmd' handle of the device on success.  
  
By default, the first detected devide will be used and if no device  
is connected, it will return an empty [] hmd handle. You can override  
this default choice of device by specifying the optional 'deviceIndex'  
parameter to choose a specific device. However, only one device per machine is  
supported, so the 'deviceIndex' will probably be only useful in the future.  
  
More optional parameters: 'basicTask' what kind of task should be implemented.  
The default is 'Tracked3DVR', which means to setup for stereoscopic 3D  
rendering, driven by head motion tracking, for a fully immersive experience  
in some kind of 3D virtual world. This is the default if omitted. The task  
'Stereoscopic' sets up for display of stereoscopic stimuli, but without  
head tracking. 'Monoscopic' sets up for display of monocular stimuli, ie.  
the device is just used as a special kind of standard display monitor. In 'Monoscopic'  
and 'Stereoscopic' mode, both eyes will be presented with an identical field of view,  
to make sure pure 2D drawing works, without the need for setup of special per-eye  
projection transformations. In 'Tracked3DVR' mode, each eye will have a different  
field of view, optimized to maximize the viewable area while still avoiding occlusion  
artifacts due to the nose of the wearer of the device.  
  
In monoscopic or stereoscopic mode, you can change the imaging parameters, ie.,  
apparent size and location of the 2D views used with the following command to  
optimize visual display:  
  
[oldPosition, oldSize, oldOrientation] = [PsychOpenXR](PsychOpenXR)('View2DParameters', hmd, eye [, position][, size][, orientation]);  
  
  
'basicRequirements' defines basic requirements for the task. Currently  
defined are the following strings which can be combined into a single  
'basicRequirements' string:  
  
'ForceSize=widthxheight' = Enforce a specific fixed size of the stimulus  
image buffer in pixels, overriding the recommmended value by the runtime,  
e.g., 'ForceSize=2200x1200' for a 2200 pixels wide and 1200 pixels high  
image buffer. By default the driver will choose values that provide good  
quality for the given XR display device, which can be scaled up or down  
with the optional 'pixelsPerDisplay' parameter for a different quality vs.  
performance tradeoff in the function [PsychOpenXR](PsychOpenXR)('SetupRenderingParameters');  
The specified values are clamped against the maximum values supported by  
the given hardware + driver combination.  
  
'Float16Display' = Request rendering, compositing and display in 16 bpc float  
format. This will ask Psychtoolbox to render and post-process stimuli in 16 bpc  
linear floating point format, and allocate 16 bpc half-float textures as final  
renderbuffers to be sent to the VR compositor. If the VR compositor takes advantage  
of the high source image precision is at the discretion of the compositor and device.  
By default, if this request is omitted, processing and display in sRGB format is  
requested from Psychtoolbox and the compositor, ie., a roughly gamma 2.2 8 bpc  
format is used.  
  
'ForbidMultiThreading' = Forbid any use of multi-threading for visual  
presentation by the driver for any means or purposes! This is meant to  
get your setup going in case of severe bugs in proprietary [OpenXR](OpenXR)  
runtimes that can cause instability, hangs, crashes or other malfunctions  
when multi-threading is used. Or if one wants to squeeze out every last  
bit of performance, no matter the consequences ("Fast and furious mode").  
On many proprietary [OpenXR](OpenXR) runtimes, this will prevent any reliable,  
trustworthy, robust or accurate presentation timing or timestamping, and  
may cause severe visual glitches under some modes of operation. See the  
following keywords below for descriptions of various more nuanced  
approaches to multi-threading vs. single-threading to choose fine-tuned  
tradeoffs between performance, stability and correctness for your  
specific experimental needs.  
  
'Use2DViewsWhen3DStopped' = [Ask](Ask) the driver to switch to use of the same 2D views  
and geometry during the '3DVR' or 'Tracked3DVR' basicTask as would be used  
for pure 2D display in basicTask 'Stereoscopic' whenever the user script  
signals it does not execute a tight tracking and animation loop, ie.  
whenever the script calls [PsychVRHMD](PsychVRHMD)('Stop', hmd). Switch back to regular  
3D projected geometry and views after a consecutive [PsychVRHMD](PsychVRHMD)('Start', hmd).  
This is useful if have phases in your experiment session when you want to  
display non-tracked content, e.g., instructions or feedback to the  
subject between trials, fixation crosses, etc., or pause script execution  
for more than a few milliseconds, but still want the visual display to  
stay stable. If this keyword is omitted, depending on the specific [OpenXR](OpenXR)  
runtime in use, the driver will stabilize the regular 3D projected  
display by use of multi-threaded operation when calling [PsychVRHMD](PsychVRHMD)('Stop', hmd),  
and resume single-threaded operation after [PsychVRHMD](PsychVRHMD)('Start', hmd). This  
higher overhead mode of operation via multi-threading will possibly have  
degraded performance, and not only between the 'Stop' and 'Start' calls,  
but throughout the whole session! This is why it can be advisable to  
evaulate if use of the 'Use2DViewsWhen3DStopped' keyword is a better  
solution for your specific experiment paradigm. The switching between 3D  
projected view and standard 2D stereoscopic view will change the image  
though, which may disorient the subject for a moment while the subjects  
eyes need to adapt their accomodation, vergence and focus point. You can  
change the imaging parameters, ie., apparent size and location of the 2D  
views used in this mode with the following command to minimize visual  
disorientation:  
  
[oldPosition, oldSize, oldOrientation] = [PsychOpenXR](PsychOpenXR)('View2DParameters', hmd, eye [, position][, size][, orientation]);  
  
For such 2D views you can also specify the distance of the virtual  
viewscreen in meters in front of the eyes of the subject. By default the  
distance is 1 meter and the size and position is set up to fill out the  
field of view in a meaningful way, essentially covering the whole  
available field of view. By overriding the distance to a smaller or  
bigger distance than 1 meter, you can "zoom in" to the image, or make  
sure that also the corners and edges of the image are visible. E.g., the  
following keyword would place the virtual screen at 2.1 meters distance:  
  
'2DViewDistMeters=2.1'  
  
'DontCareAboutVisualGlitchesWhenStopped' = Tell the driver that you don't  
care about potential significant visual presentation glitches happening if  
your script does not run a continuous animation with high framerate, e.g.,  
after calling [PsychVRHMD](PsychVRHMD)('Stop', hmd), pausing, etc. This makes sense if  
you don't care, or if your script does not ever pause or slow down during  
a session or at least an ongoing trial. This will avoid multi-threading  
for glitch prevention in such cases, possibly allowing to side-step  
certain bugs in proprietary [OpenXR](OpenXR) runtimes, or to squeeze out higher  
steady-state performance.  
  
'NoTimingSupport' = Signal no need at all for high precision and reliability  
timing for presentation. If you don't need any timing precision or  
reliability in your script, specifying this keyword may allow the driver  
to optimize for higher performance. See 'TimingSupport' explanation right  
below:  
  
'TimingSupport' = Use high precision and reliability timing for presentation.  
  
The current [OpenXR](OpenXR) specification, as of [OpenXR](OpenXR) version v1.0.26 from January 2023,  
does not provide any means of reliable, trustworthy, accurate timestamping of  
presentation, and all so far tested proprietary [OpenXR](OpenXR) runtime implementations  
have severely broken and defective timing support. Only the open-source  
Monado [OpenXR](OpenXR) runtime on Linux provides a reliable and accurate timing  
implementation. Therefore this driver has to use a workaround on non-Monado  
[OpenXR](OpenXR) runtimes to achieve at least ok'ish timing if you require it, and  
that workaround involves multi-threaded operation. This multi-threading  
in turn can severely degrade performance, possibly reducing achievable  
presentation framerates to (less than) half of the maximum video refresh  
rate of your device! For this reason you should only request 'TimingSupport'  
on non-Monado if you really need it and be willing to pay the performance  
price.  
  
If you omit this keyword, the driver will try to guess if you need  
precise presentation timing for your session or not. As long as you only  
call [Screen](Screen)('[Flip](Flip)', window) or [Screen](Screen)('[Flip](Flip)', window, [], ...), ie. don't  
specify a requested stimulus onset time, the driver assumes you don't  
need precise timing, just presenting as soon as possible after a  
[Screen](Screen)('[Flip](Flip)'), and also that you don't care about accurate or trustworthy  
or correct presentation timestamps to be returned by [Screen](Screen)('[Flip](Flip)'). Once  
you specify a target onset time tWhen, ie. via calling '[Flip](Flip)' as  
[Screen](Screen)('[Flip](Flip)', window, tWhen [, ...]), the driver assumes from then on  
and for the rest of the session that you want reasonably accurate  
presentation timing. It will then switch to multi-threaded operation with  
better timing, but potentially drastically reduced performance.  
  
'TimestampingSupport' = Use high precision and reliability timestamping for presentation.  
  
'NoTimestampingSupport' = Do not need high precision and reliability timestamping for presentation.  
Those keywords let you specify if you definitely need or don't need  
trustworthy, reliable, robust, precise presentation timestamps, ie. the  
'timestamp' return values of timestamp = [Screen](Screen)('[Flip](Flip)') should be high  
quality, or if you don't care. If you omit both keywords, the driver will  
try to guess what you wanted. On most current [OpenXR](OpenXR) runtimes, use of  
timestamping will imply multi-threaded operation with the performance  
impacts and problems mentioned above in the section about 'TimingSupport',  
that is why it is advisable to explicitely state your needs, to allow the  
driver to optimize for the best precision/reliability/performance  
tradeoff on all the runtimes where such a tradeoff is required.  
  
As mentioned here, in "help [PsychVRHMD](PsychVRHMD)" and our "help [OpenXR](OpenXR)" overview  
and setup instructions, currently no standard [OpenXR](OpenXR) implementation with  
reliable and trustworthy timestamping exists. Proper enhancements to  
[OpenXR](OpenXR) will need to be done in the future. Right now, as of Psychtoolbox  
3.0.19.2, we have a hacky solution for a subset of Linux users, called  
"Monado metrics timestamping hack". It goes as follows:  
  
If you need reliable timestamping, the only solution right now is to use  
Linux + the latest Monado upstream version + a modified version of Mesa + an  
AMD or Intel gpu of sufficient performance + a VR HMD supported by Monado  
on Linux. Contact our paid support "help [PsychPaidSupportAndServices](PsychPaidSupportAndServices)" for  
help in setting up this feature and getting suitable modified Monado and  
Mesa drivers. Once everything is installed on the hardware and software  
side, the following steps need to be taken at the start of each  
experiment session to enable the special Monado metrics timestamping hack  
for trustworthy timestamping at the price of lowered performance:  
  
    1. Create a Linux fifo pipe file, e.g., in a terminal type  
       "sudo mkfifo /usr/local/framequeue.protobuf"  
       You can choose any file path and name instead of  
       /usr/local/framequeue.protobuf but it makes sense to choose a  
       directory which is under your users control, not a temporary  
       directory, unless you want to repeat step 1 after each system  
       reboot. In steps 2 and 3 you must path the same path/filename to  
       both monado-service and Octave/Matlab via the XRT\_METRICS\_FILE  
       environment variable.  
  
    2. Start monado-service and use the created fifo file as output file  
       for the metrics log, e.g., in a terminal window via  
  
       "XRT\_METRICS\_FILE=/usr/local/framequeue.protobuf XRT\_METRICS\_EARLY\_FLUSH=true monado-service"  
  
       This will launch the monado-service [OpenXR](OpenXR) compositor, enable its  
       metrics logging with low latency into the fifo, and block its  
       startup until the Psychtoolbox XR work session is started.  
  
    3. Start a PTB session, also with XRT\_METRICS\_FILE environment variable  
       specified to the same fifo file location during launch of Octave or  
       Matlab, e.g., in a terminal start Octave or Matlab via:  
  
       "XRT\_METRICS\_FILE=/usr/local/framequeue.protobuf octave --gui" or  
       "XRT\_METRICS\_FILE=/usr/local/framequeue.protobuf matlab"  
  
       Once the [PsychOpenXR](PsychOpenXR) driver has detected that a Monado XR server is  
       running, and that the fifo file exists and is accessible, it opens  
       that fifo for read access, which will let monado-service fully start  
       up and get ready to serve [OpenXR](OpenXR) clients. Your Psychtoolbox session  
       should then work with trustworthy timestamps, but at potentially  
       significantly reduced performance, e.g., a framerate of only half  
       or a third of the refresh rate of your VR HMD display.  
  
  
'Eyetracking' = Request eye gaze tracking via a supported HMD builtin eye tracker.  
This keyword asks the driver to enable eye gaze tracking. A given combo  
of VR/AR/MR device (and its builtin eye tracker), operating system, [OpenXR](OpenXR)  
runtime and additional optionally installed eye tracking software, may  
support multiple different gaze tracking api's and runtimes. By default,  
the driver will try to use the most capable gaze tracking api, ie. the  
one which provides the most detailed and exhaustive information about the  
users gaze, at the highest sampling rate, with the most flexibility. It  
will fall back to less capable or efficient tracking api's if more  
capable ones are not supported or available. For this reason, the amount  
of information can differ widely between the most capable api's and the  
most basic api's. User scripts which strive to be usable on different  
operating systems, software setups or eyetracking hardware and [HMDs](HMDs) must  
therefore be written in a defensive and adaptive way to be able to work  
with only the minimal subset of information guaranteed to be available on  
all implementations. The info struct returned by info = [PsychVRHMD](PsychVRHMD)('GetInfo');  
contains info about basic gaze tracking capabilities as a bitmask in  
info.eyeTrackingSupported: A value of +1 means at least one gaze vector  
is reported. A value of +2 means reporting of binocular eye tracking data  
is supported. A value of +1024 means that HTC's proprietary [SRAnipal](SRAnipal)  
eyetracking is used for more extensive gaze data reporting.  
  
If eye tracking is requested via the keyword and supported, then the user  
script can request return of the most recent eye gaze tracking sample  
data by calling the state = [PsychVRHMD](PsychVRHMD)('PrepareRender', ..., reqmask, ...)  
function with reqmask flag +4. This will cause the returned 'state' struct  
to contain additional fields with information about the most recent gaze.  
See help text for the 'PrepareRender' function for more detailed info.  
  
### The current driver supports the following gazetracking implementations:  
  
- With HTC VR [HMDs](HMDs) with eyetracking support, under Microsoft Windows, in  
combination with the optional HTC [SRAnipal](SRAnipal) runtime DLL's installed, and  
using Matlab, an optional [SRAnipal](SRAnipal) mex driver can be used to provide both  
binocular per-eye gaze tracking data, separate for the subjects left and  
right eye, and a virtual 3rd "cyclops eye" which is synthesized info from  
both hardware eye trackers, sometimes of higher quality due to sensor  
fusion of the two gaze tracker data streams. For each of both eyes, in  
addition to eye gaze position and direction, estimated pupil size in  
millimeters and a measure of eye openess is reported, e.g., for eye  
blink detection or estimation of gaze data reliability. Reported times  
are hardware timestamps of when a gaze sample was measured. On the tested  
"HTC Vive Pro Eye" HMD sampling rates of up to 120 Hz were possible.  
  
- On other device + operating system + [OpenXR](OpenXR) runtime combos with [OpenXR](OpenXR)  
gazetracking support, information from the XR\_EXT\_eye\_gaze\_interaction  
gaze tracking extension is returned. This extension is supported on a wider  
range of XR devices, but the returned information is more limited: A  
single eye gaze vector and position, but without any information about the  
subjects eye openess, pupil size or of the systems confidence in the quality  
of the measured gaze. The gaze vector is of unspecified origin. It could  
be measured gaze from a monocular eye tracker, ie. either left or right eye  
gaze, or it could be a "cyclops eye" synthesized gaze computed via sensor  
fusion of gaze data from a binocular gaze tracker. The gaze data may be  
measured data from a time in the past, or interpolated or extrapolated  
gaze data from one or more past measured eye gaze samples. The returned  
gaze sample timestamp may be a hardware timestamp of when the gaze sample  
was measured, but could also be the time for which gaze was predicted via  
interpolation or extrapolation of past hardware measured gaze samples.  
Temporal resolution of the gaze data is also unspecified. On the tested  
HTC Vive Pro Eye, the reported gaze seems to correspond to the sensor  
fusion of gaze samples from the binocular eye tracker, and the temporal  
resolution is reduced to at best 16.6 msecs for at most 60 gaze samples  
per second.  
  
  
'Handtracking' = Request articulated hand and finger tracking via a supported  
hand tracker. This keyword asks the driver to enable articulated hand tracking.  
Typical methods are markerless vision based hand and finger tracking, e.g.,  
from external cameras or HMD builtin cameras, or marker based optical tracking,  
or sensor equipped hand gloves, or other technologies, depending on your [OpenXR](OpenXR)  
runtime. The info struct returned by info = [PsychVRHMD](PsychVRHMD)('GetInfo'); contains info  
about hand tracking capabilities as a bitmask in info.articulatedHandTrackingSupported:  
A value of +1 means that basic [OpenXR](OpenXR) hand tracking of finger and hand joint poses,  
typically for both hands of a user, is supported. A value of zero means lack of  
any support.  
  
If hand tracking is requested via the keyword, and supported, then the user  
script can request return of hand tracking sample data by calling the  
state = [PsychVRHMD](PsychVRHMD)('PrepareRender', ..., reqmask, ...) function with reqmask  
flag +8. This will cause the returned 'state' struct to contain additional fields  
with information about recently tracked articulated hand configuration. See the  
help text for the 'PrepareRender' function for details.  
  
  
'basicQuality' defines the basic tradeoff between quality and required  
computational power. A setting of 0 gives lowest quality, but with the  
lowest performance requirements. A setting of 1 gives maximum quality at  
maximum computational load. Values between 0 and 1 change the quality to  
performance tradeoff.  
  
  
hmd = [PsychOpenXR](PsychOpenXR)('Open' [, deviceIndex], ...);  
- Open device with index 'deviceIndex'. See [PsychOpenXRCore](PsychOpenXRCore) Open?  
for help on additional parameters.  
  
  
[PsychOpenXR](PsychOpenXR)('SetAutoClose', hmd, mode);  
- Set autoclose mode for device with handle 'hmd'. 'mode' can be  
0 (this is the default) to not do anything special. 1 will close  
the device 'hmd' when the onscreen window is closed which displays  
on the device. 2 will do the same as 1, but close all open [HMDs](HMDs) and  
shutdown the complete driver and [OpenXR](OpenXR) runtime - a full cleanup.  
  
  
isOpen = [PsychOpenXR](PsychOpenXR)('IsOpen', hmd);  
- Returns 1 if 'hmd' corresponds to an open device, 0 otherwise.  
  
  
[PsychOpenXR](PsychOpenXR)('[Close](Close)' [, hmd]);  
- [Close](Close) provided device 'hmd'. If no 'hmd' handle is provided,  
all [HMDs](HMDs) will be closed and the driver will be shutdown.  
  
  
[PsychOpenXR](PsychOpenXR)('Controllers', hmd);  
- Return a bitmask of all connected controllers: Can be the bitand  
of the OVR.[ControllerType](ControllerType)\_XXX flags described in 'GetInputState'.  
  
  
info = [PsychOpenXR](PsychOpenXR)('GetInfo', hmd);  
- Retrieve a struct 'info' with information about the device 'hmd'.  
The returned info struct contains at least the following standardized  
fields with information:  
  
handle = Driver internal handle for the specific device.  
driver = Function handle to the actual driver for the device, e.g., @[PsychOpenXR](PsychOpenXR).  
type   = Defines the type/vendor of the device, e.g., 'OpenXR'.  
modelName = Name string with the name of the model of the device, e.g., 'Rift DK2'.  
  
separateEyePosesSupported = 1 if use of [PsychOpenXR](PsychOpenXR)('GetEyePose') will improve  
                            the quality of the VR experience, 0 if no improvement  
                            is to be expected, so 'GetEyePose' can be avoided  
                            to save processing time without a loss of quality.  
                            This \*always\* returns 0 on this [PsychOpenXR](PsychOpenXR) driver.  
  
  
[VRControllersSupported](VRControllersSupported) = 1 if use of [PsychVRHMD](PsychVRHMD)('GetInputState') will provide input  
                           from actual dedicated VR controllers. Value is 0 if  
                           controllers are only emulated to some limited degree,  
                           e.g., by abusing a regular keyboard as a button controller,  
                           ie. mapping keyboard keys to OVR.Button\_XXX buttons.  
  
handTrackingSupported = 1 if [PsychVRHMD](PsychVRHMD)('PrepareRender') with reqmask +2 will provide  
                          valid tracked hand controller info, 0 if this is not supported  
                          and will just report fake values. A driver may report 1 here but  
                          still don't provide meaningful info at runtime, e.g., if required  
                          tracking hardware is missing or gets disconnected. The flag  
                          just aids extra performance optimizations in your code.  
  
hapticFeedbackSupported = 1 if basic haptic feedback is supported in principle on some controllers.  
                            0 otherwise. A flag of zero means no haptic feedback support, but  
                            a flag of 1 may still mean no actual feedback, e.g., if suitable  
                            hardware is not configured and present. Flags higher than 1 can  
                            signal presence of more advanced haptic feedback, so you should  
                            test for a setting == 1 to know if [PsychVRHMD](PsychVRHMD)('HapticPulse') works  
                            in principle, which is considered basic feedback ability.  
  
eyeTrackingSupported = Info about eye gaze tracking capabilities. A value of +1 means at least one  
                       gaze vector is reported. A value of +2 means reporting of binocular per-eye  
                       tracking data is supported. A value of +1024 means that HTC's proprietary  
                       [SRAnipal](SRAnipal) eyetracking is available for more extensive gaze data reporting.  
  
articulatedHandTrackingSupported = Info about hand tracking capabilities. A value of +1 means that  
                                   basic articulated hand tracking is supported, usually for both  
                                   hands. Zero means no support for articulated hand tracking. The  
                                   hand tracking methods could be based on cameras and computer vision  
                                   markerless optical tracking, or on marker based tracking, or it  
                                   could be, e.g., with some sensor glove input device, or with any  
                                   other suitable future modality supported by your [OpenXR](OpenXR) runtime.  
  
  
The returned struct may contain more information, but the fields mentioned  
above are the only ones guaranteed to be available over the long run. Other  
fields may disappear or change their format and meaning anytime without  
warning. See 'help PsychVRHMD' for more detailed info about available fields.  
  
  
isSupported = [PsychOpenXR](PsychOpenXR)('Supported');  
- Returns 1 if the [OpenXR](OpenXR) driver is functional, 0 otherwise. The  
driver is functional if the VR runtime library was successfully  
initialized and a connection to the VR server process has been  
established. It would return 0 if the server process would not be  
running, or if the required runtime library would not be correctly  
installed.  
  
  
[isVisible, playAreaBounds, [OuterAreaBounds](OuterAreaBounds)] = [PsychOpenXR](PsychOpenXR)('VRAreaBoundary', hmd [, requestVisible]);  
- Request visualization of the VR play area boundary for 'hmd' and returns its  
current extents.  
  
'requestVisible' 1 = Request showing the boundary area markers, 0 = Don't  
request showing the markers. This parameter is accepted, but ignored for [OpenXR](OpenXR).  
  
Returns in 'isVisible' the current visibility status of the VR area boundaries.  
This driver always returns 0 for false / invisible.  
  
'playAreaBounds' is a 3-by-n matrix defining the play area boundaries. Each  
column represents the [x;y;z] coordinates of one 3D definition point. Connecting  
successive points by line segments defines the boundary, as projected onto the  
floor. Points are listed in clock-wise direction. An empty return argument means  
that the play area is so far undefined. This driver returns empty if the boundaries  
are unknown. Otherwise it returns the bounding rectangle of the area, as current  
unextended [OpenXR](OpenXR) runtimes can only return a rectangle, not more complex boundaries.  
  
'OuterAreaBounds' defines the outer area boundaries in the same way as  
'playAreaBounds'. This driver currently returns the same as 'playAreaBounds', as  
current unextended [OpenXR](OpenXR) only supports that information.  
  
  
input = [PsychOpenXR](PsychOpenXR)('GetInputState', hmd, controllerType);  
- Get input state of controller 'controllerType' associated with device 'hmd'.  
  
'controllerType' can be one of OVR.[ControllerType](ControllerType)\_LTouch, OVR.[ControllerType](ControllerType)\_RTouch,  
OVR.[ControllerType](ControllerType)\_Touch, OVR.[ControllerType](ControllerType)\_Remote, OVR.[ControllerType](ControllerType)\_XBox, or  
OVR.[ControllerType](ControllerType)\_Active for selecting whatever controller is currently active.  
  
Return argument 'input' is a struct with fields describing the state of buttons and  
other input elements of the specified 'controllerType'. It has the following fields:  
  
'Valid' = 1 if 'input' contains valid results, 0 if input status is invalid/unavailable.  
'Time' Time of last input state change of controller.  
'ActiveInputs' = Bitmask defining which of the following struct elements do contain  
meaningful input from actual physical input source devices. This is a more fine-grained  
reporting of what 'Valid' conveys, split up into categories. The following flags will be  
logical or'ed together if the corresponding input category is valid, ie. provided with  
actual input data from some physical input source element, controller etc.:  
  
+1  = 'Buttons' gets input from some real buttons or switches.  
+2  = 'Touches' gets input from some real touch/proximity sensors or gesture recognizers.  
+4  = 'Trigger' gets input from some real analog trigger sensor or gesture recognizer.  
+8  = 'Grip' gets input from some real analog grip sensor or gesture recognizer.  
+16 = 'Thumbstick' gets input from some real thumbstick, joystick or trackpad or similar 2D sensor.  
+32 = 'Thumbstick2' gets input from some real secondary thumbstick, joystick or trackpad or similar 2D sensor.  
  
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
  
'Thumbstick2' = Like 'Thumbstick', but for devices with a 2nd 2D input device for each hand, e.g.,  
a 2nd thumbstick or a trackpad.  
  
  
pulseEndTime = [PsychOpenXR](PsychOpenXR)('HapticPulse', hmd, controllerType [, duration=2.5][, freq=1.0][, amplitude=1.0]);  
- Trigger a haptic feedback pulse, some controller vibration, on the  
specified 'controllerType' associated with the specified 'hmd'.  
  
### Currently supported values for 'controllerType' are:  
  
OVR.[ControllerType](ControllerType)\_XBox   - The Microsoft [XBox](XBox) controller or compatible gamepad.  
OVR.[ControllerType](ControllerType)\_Remote - Connected remote control or similar, e.g., control buttons on device.  
OVR.[ControllerType](ControllerType)\_LTouch - Haptic enabled left hand controller.  
OVR.[ControllerType](ControllerType)\_RTouch - Haptic enabled right hand controller.  
OVR.[ControllerType](ControllerType)\_Touch  - All haptics enabled hand controllers.  
OVR.[ControllerType](ControllerType)\_Active - All active haptics enabled controllers.  
  
'duration' is requested pulse duration in seconds. By default a pulse of  
2.5 seconds duration is executed, as this is the maximum pulse duration  
supported by Oculus Rift CV1 touch controllers. Other controllers or  
[OpenXR](OpenXR) runtimes may have different limits on pulse duration, or no limit  
at all. A duration of 0 maps to the minimum duration supported by the  
active [OpenXR](OpenXR) runtime and device. 'freq' may be a normalized frequency in  
range 0.0 - 1.0, or a higher frequency in Hz. A value of 0 will disable  
an ongoing pulse. The range up to 1.0 gets mapped to the interval 0 - 320  
Hz for backwards compatibility with older Oculus VR drivers. Values  
greater than 1 are interpreted as desired frequency in Hz. [OpenXR](OpenXR)  
runtimes and hardware may clamp the requested frequency to implementation  
dependent minimum or maximum values, or quantize to only a few discrete  
frequencies. E.g., Oculus touch controllers only support 160 Hz and 320  
Hz, no other frequencies. 'amplitude' is the amplitude of the vibration  
in normalized 0.0 - 1.0 range.  
  
'pulseEndTime' returns the expected stop time of vibration in seconds,  
given the parameters. This may be inaccurate, depending on [OpenXR](OpenXR) runtime  
and hardware.  
  
In general, unfortunately, testing so far shows that [OpenXR](OpenXR) runtimes vary  
considerably in how well they follow the requested haptic pulse duration,  
frequency, and timing, so some caution is advised wrt. haptic pulse  
feedback. Never trust a given software + hardware combo blindly, always  
verify your specific setup!  
  
  
state = [PsychOpenXR](PsychOpenXR)('PrepareRender', hmd [, userTransformMatrix][, reqmask=1][, targetTime]);  
- Mark the start of the rendering cycle for a new 3D rendered stereoframe.  
Return a struct 'state' which contains various useful bits of information  
for 3D stereoscopic rendering of a scene, based on head tracking data.  
  
'hmd' is the handle of the device which delivers tracking data and receives the  
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
flag means the device is actually strapped onto the subjects head and displaying  
our visual content. Lack of this flag means the device is off and thereby blanked  
and dark, or we lost access to it to another application.  
  
state also always contains a field state.[SessionState](SessionState), whose bits signal general  
VR session status:  
+1  = Our rendering goes to the device, ie. we have control over it. Lack of this could  
      mean the Health and Safety warning is displaying at the moment and waiting for  
      acknowledgement, or the [OpenXR](OpenXR) GUI application is in control.  
+2  = Device is present and active.  
+4  = Device is strapped onto users head. A Rift CV1 would switch off/blank if not on the head.  
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
     contained in state.cameraView{1} and state.cameraView{2}.  
  
     Additionally tracked/predicted head pose is returned in state.localHeadPoseMatrix  
     and the global head pose after application of the 'userTransformMatrix' is  
     returned in state.globalHeadPoseMatrix - this is the basis for computing  
     the camera transformation matrices.  
  
+2 = Return matrices for tracked left and right hands of user, ie. of tracked positions  
     and orientations of left and right XR input controllers, if any.  
  
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
  
+4 = Return the most recent eye gaze information on devices with built-in eye tracking hardware.  
     Returned information may represent the latest available measured eye  
     gaze data, or it may be predicted eye gaze information for the  
     specified 'targetTime', computed via interpolation or extrapolation  
     from actual previously measured eye gaze. This is dependent on the  
     specific gaze tracker implementation of your system. If the reported  
     gaze sample timestamps are identical to the provided 'targetTime'  
     then that is one possible indication that reported gaze may be  
     predicted gaze instead of a direct hardware measured gaze sample.  
  
     The following fields are mandatory as part of the state struct, if gaze  
     tracking is supported and enabled and requested:  
  
     state.gazeRaw = If no new gaze tracking data is available, returns an  
     empty [] variable. Otherwise a variable in a format that is  
     dependent on the actually used gaze tracking api and implementation.  
     It could be a vector, a struct, an array of structs... The format  
     may change without prior notice, without any regard for backward  
     compatibility, so it is mostly useful for debugging by the PTB  
     developers or other Psychtoolbox internal special use cases, not to  
     be relied on by regular user experiment scripts!  
  
     The following variables are arrays, whose length depends on the  
     used gaze tracking method. Each array element represents properties  
     of one tracked eye gaze. At a minimum, the arrays have one element  
     for the most basic gaze tracking, e.g., if the [OpenXR](OpenXR) extension  
     XR\_EXT\_eye\_gaze\_interaction is used for gaze tracking, it will only  
     report one gaze vector in index 1: A monocular gaze sample from either  
     the left or right eye, or a synthetic "cyclops eye" gaze sample, computed  
     via sensor fusion of data from a binocular gazetracker. The arrays could  
     also have 2 elements for a purely binocular eye tracker, with index 1 for  
     the left eye, and index 2 for the right eye data. On a binocular tracker,  
     it is also possible for a three element array to be returned, in  
     which case index 1 is left eye date, 2 is right eye date, and 3 is  
     synthesized "cyclops eye" data.  
  
     Please write your scripts so they can handle any number of 1, 2 or  
     three array elements meaningfully:  
  
     state.gazeStatus(i) = A flag telling if i'th gaze is unavailable  
                           (=0), available (+1) or available and somewhat  
                           trustworthy (+2). Values other than 3 (=1+2)  
                           should not really be trusted. A value of only  
                           1 could, e.g., mean that data was reported,  
                           but it is not based on an actual measured eye  
                           gaze sample, but purely extrapolated or  
                           predicted from past valid data. A value of 3  
                           is not a guarantee of high quality data, just  
                           that the data is actually measured eye gaze  
                           data and passed the minimum quality treshold.  
  
  
     state.gazeTime(i) = A timestamp of the time for which the given  
     gaze information is valid, or the value [NaN](NaN) if no valid timestamp is  
     available from the gaze tracker. Depending on gaze tracking method in  
     use, this could be a time in the past, referring to the hardware  
     timestamp of when the gaze tracker hardware acquired that sample, or  
     it could be the time in the past or near future for which the gaze  
     data was computed via prediction / extrapolation of gaze movement or  
     interpolation from past gaze tracking data history. [OpenXR](OpenXR) built in  
     gaze tracking extensions often may not report the most recent  
     measured eye gaze sample from a past tracking cycle. Instead they  
     take the user provided 'targetTime' (or predicted stimulus onset  
     time for the next to-be-presented VR/AR/MR/XR stimulus image, if  
     'targetTime' was omitted) and try to predict where the subject will  
     be looking (for a 'targetTime' in the near future) or has looked  
     (for a 'targetTime' in the near past). In case of such prediction,  
     the reported state.gazeTime(i) corresponds to the time for which  
     gaze was actually predicted. It is a bit of a hazard for scientific  
     research purposes that there is some uncertainty if timestamps refer  
     to time of real measured gaze, or to some predicted time, or that  
     prediction / interpolation / extrapolation may be used instead of  
     reporting measured data, or that the prediction method - if any - is  
     not specified or standardized across different devices, gaze  
     trackers and gaze tracking runtimes and api's. This is unfortunately  
     unavoidable, as most commercial off the shelf gaze trackers for XR  
     applications are not targeted at scientific research use cases, but  
     as human computer interaction method for operating and navigating in  
     VR and AR, e.g., for gaming and entertainment purposes. Not much we  
     could do about this, so you will have to deal with this in your  
     research paradigm or carefully select hardware with known suitable  
     properties for your specific use case.  
  
     Actual gaze information is provided in two formats, a 2D format, in  
     onscreen window pixel coordinates, ie. where in the image has the  
     subject looked, and a 3D format, as 3D gaze rays, ie. where in a  
     rendered 3D scene has the subject looked:  
  
###      2D - Onscreen window referenced:  
  
     state.gazePos{i} = A two-element [x,y] vector of the estimated 2D user  
     gaze position in Psychtoolbox onscreen window coordinates. Iow. the  
     x,y coordinates of where the user looked. In mono display mode this  
     is done by mapping the users gaze vector to the 2D space of the  
     common image that is displayed in the left and right eye display of  
     a VR/AR/MR HMD. In stereoscopic 2D display mode or full 3D perspective  
     correct rendering mode with potential head tracking, where a different  
     image is rendered and displayed to the subjects left and right eye, the  
     mapping of indices is as follows: state.gazePos{1} is expressed wrt.  
     to the left eye image buffer, ie. the one selected via  
     [Screen](Screen)('SelectStereoDrawBuffer', win, 0);. state.gazePos{2} refers  
     to the right eye image buffer ([Screen](Screen)('SelectStereoDrawBuffer', win, 0);).  
     state.gazePos{3} for a potential synthetic "cyclops eye" gaze will  
     reference the left eye image buffer again.  
  
###      3D - 3D scene geometry referenced:  
  
     state.gazeRayLocal{i} = encodes the subjects gaze direction / line  
     of sight within a HMD fixed reference frame:  
  
     state.gazeRayLocal{i}.gazeC = a [x,y,z] 3D vector denoting the  
     estimated position of the optical center of the subjects eye balls,  
     relative to the origin of the head-fixed reference frame.  
  
     state.gazeRayLocal{i}.gazeD = a [dx,dy,dz] 3D vector denoting the  
     gaze direction in the head-fixed x, y and z axis.  
  
     The values in gazeRayLocal therefore define a 3D line equation  
     denoting the users line of sight, a "gaze ray" so to speak:  
  
     For all scalar values t from zero to infinity, p(t) with  
     p(t) = state.gazeRayLocal{i}.gazeC + t \* state.gazeRayLocal{i}.gazeD  
     defines 3D points along the looking direction / gaze vector / gaze  
     ray of the subject, in a head-fixed reference frame.  
  
     Mathematical intersection of such a defined line equation p(t) with 3D  
     scene geometry in 3D rendering mode that is fixed wrt. to the users head  
     allows you to figure out where the user is looking in 3D space.  
  
     For a typical 3D head tracked VR / AR / MR rendering scenario, where  
     you would also set the the 'reqmask' flag +1 to retrieve head  
     tracking information and state.modelView matrices for 3D rendering,  
     the function also provides state.gazeRayGlobal{i} of the same  
     format. In this case the HMD head tracking information is used to  
     locate the subjects head position and orientation in a 3D rendered  
     scene and the gaze ray is transformed accordingly, so mathematical  
     intersection of rendered 3D geometry with the 3D line equation ...  
     p(t) = state.gazeRayGlobal{i}.gazeC + t \* state.gazeRayGlobal{i}.gazeD  
     ... allows to find the point of fixation in a 3D world even if the  
     subject is moving their head or walking around.  
  
  
     Some of the supported eye tracking implementations may provide the  
     following additional optional information for each gaze index i. If  
     the information is not available for a given implementation, either  
     an empty vector [] or the scalar value [NaN](NaN) is returned:  
  
     state.gazeConfidence(i) = A scalar value of confidence, ie. how  
     certain is the gaze tracker that reported data is trustworthy and  
     accurate. Currently unsupported on all trackers, returns [NaN](NaN).  
  
     state.gazeEyeOpening(i) = A scalar value of how far the subjects  
     eyes are open, in a normalized range 0 for closed to 1 for fully  
     open. This can be used, e.g., as another confidence measure, or for  
     eye blink detection. Supported for i=1,2 with HTC [SRAnipal](SRAnipal) gaze  
     tracking on suitable HTC [HMDs](HMDs) like the HTC Vive Pro Eye.  
  
     state.gazeEyePupilDiameter(i) = The estimated diameter of the  
     subjects pupil, presumably in millimeters. Supported for i=1,2 with  
     HTC [SRAnipal](SRAnipal) gaze tracking on suitable HTC [HMDs](HMDs) like the HTC Vive Pro Eye.  
  
     state.gazeEyeConvergenceDistance = For binocular gaze tracking, this  
     may be a scalar estimate of eye convergence distance, ie. the  
     distance of the fixation point from the eyes. May be supported on  
     some HTC [HMDs](HMDs) under [SRAnipal](SRAnipal), but has not been confirmed to work in  
     practice on the tested HTC Vive Pro Eye.  
  
+8 = Request return of articulated hand tracking information on suitable [OpenXR](OpenXR)  
     systems.  
  
     Returned information may represent the latest available measured hand and  
     finger configuration data, or it may be predicted configuration information  
     for the specified 'targetTime', computed via interpolation or extrapolation  
     from actual previously tracked configurations. This is dependent on the  
     specific hand tracker implementation of your XR system.  
  
     The following fields are mandatory as part of the returned state struct,  
     if hand tracking is supported and enabled and requested:  
  
###      TODO  
  
     The following constants allow to index the returned set of 26 hand joints  
     by symbolic names for the different parts of the fingers and hand, or you  
     can use the numbers behind each symbolic name:  
  
       OVR.XR\_HAND\_JOINT\_PALM = 0 + 1;  
       OVR.XR\_HAND\_JOINT\_WRIST = 1 + 1;  
       OVR.XR\_HAND\_JOINT\_THUMB\_METACARPAL = 2 + 1;  
       OVR.XR\_HAND\_JOINT\_THUMB\_PROXIMAL = 3 + 1;  
       OVR.XR\_HAND\_JOINT\_THUMB\_DISTAL = 4 + 1;  
       OVR.XR\_HAND\_JOINT\_THUMB\_TIP = 5 + 1;  
       OVR.XR\_HAND\_JOINT\_INDEX\_METACARPAL = 6 + 1;  
       OVR.XR\_HAND\_JOINT\_INDEX\_PROXIMAL = 7 + 1;  
       OVR.XR\_HAND\_JOINT\_INDEX\_INTERMEDIATE = 8 + 1;  
       OVR.XR\_HAND\_JOINT\_INDEX\_DISTAL = 9 + 1;  
       OVR.XR\_HAND\_JOINT\_INDEX\_TIP = 10 + 1;  
       OVR.XR\_HAND\_JOINT\_MIDDLE\_METACARPAL = 11 + 1;  
       OVR.XR\_HAND\_JOINT\_MIDDLE\_PROXIMAL = 12 + 1;  
       OVR.XR\_HAND\_JOINT\_MIDDLE\_INTERMEDIATE = 13 + 1;  
       OVR.XR\_HAND\_JOINT\_MIDDLE\_DISTAL = 14 + 1;  
       OVR.XR\_HAND\_JOINT\_MIDDLE\_TIP = 15 + 1;  
       OVR.XR\_HAND\_JOINT\_RING\_METACARPAL = 16 + 1;  
       OVR.XR\_HAND\_JOINT\_RING\_PROXIMAL = 17 + 1;  
       OVR.XR\_HAND\_JOINT\_RING\_INTERMEDIATE = 18 + 1;  
       OVR.XR\_HAND\_JOINT\_RING\_DISTAL = 19 + 1;  
       OVR.XR\_HAND\_JOINT\_RING\_TIP = 20 + 1;  
       OVR.XR\_HAND\_JOINT\_LITTLE\_METACARPAL = 21 + 1;  
       OVR.XR\_HAND\_JOINT\_LITTLE\_PROXIMAL = 22 + 1;  
       OVR.XR\_HAND\_JOINT\_LITTLE\_INTERMEDIATE = 23 + 1;  
       OVR.XR\_HAND\_JOINT\_LITTLE\_DISTAL = 24 + 1;  
       OVR.XR\_HAND\_JOINT\_LITTLE\_TIP = 25 + 1;  
  
     TODO, IMPLEMENTATION OF FEATURE NOT YET FINISHED.  
  
  
More flags to follow...  
  
  
eyePose = [PsychOpenXR](PsychOpenXR)('GetEyePose', hmd, renderPass [, userTransformMatrix][, targetTime]);  
- Return a struct 'eyePose' which contains various useful bits of information  
for 3D stereoscopic rendering of the stereo view of one eye, based on head or  
eye tracking data. This function provides essentially the same information as  
the 'PrepareRender' function, but only for one eye. Therefore you will need  
to call this function twice, once for each of the two renderpasses, at the  
beginning of each renderpass. NOTE: The function only exists for backwards  
compatibility with existing older VR/AR/XR scripts. It does \*not\* provide any  
benefit on [OpenXR](OpenXR) VR/AR/XR devices, but instead may cause a performance decrease  
when used! It is recommended to not use it in new scripts.  
  
'hmd' is the handle of the device which delivers tracking data and receives the  
rendered content for display.  
  
'renderPass' defines if information should be returned for the 1st renderpass  
(renderPass == 0) or for the 2nd renderpass (renderPass == 1). The driver will  
decide for you if the 1st renderpass should render the left eye and the 2nd  
pass the right eye, or if the 1st renderpass should render the right eye and  
then the 2nd renderpass the left eye. The ordering depends on the properties  
of the video display of your device, specifically on the video scanout order:  
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
           You can pass 'eyeIndex' into [Screen](Screen)('SelectStereoDrawBuffer', win, eyeIndex)  
           to select the proper eye target render buffer.  
  
'modelView' is a 4x4 RHS [OpenGL](OpenGL) matrix which can be directly used as [OpenGL](OpenGL)  
            GL\_MODELVIEW matrix for rendering the scene.  
  
'cameraView' contains a 4x4 RHS camera matrix which describes position and  
             orientation of the "eye camera" relative to the world reference  
             frame. It is the inverse of eyePose.modelView. This matrix can  
             be directly used to define the camera for rendering of complex  
             3D scenes with the [Horde3D](Horde3D) 3D engine or other engines which want  
             absolute camera pose instead of the inverse matrix.  
  
  
oldType = [PsychOpenXR](PsychOpenXR)('TrackingOriginType', hmd [, newType]);  
- Specify the type of tracking origin for [OpenXR](OpenXR) device 'hmd'.  
This returns the current type of tracking origin in 'oldType'.  
Optionally you can specify a new tracking origin type as 'newType'.  
Type must be either:  
0 = Origin is at eye height (device height).  
1 = Origin is at floor height.  
The eye height or floor height gets defined by the system during  
sensor calibration, possibly guided by some [OpenXR](OpenXR) GUI control application.  
  
  
[PsychOpenXR](PsychOpenXR)('SetupRenderingParameters', hmd [, basicTask='Tracked3DVR'][, basicRequirements][, basicQuality=0][, fov=[[HMDRecommended](HMDRecommended)]][, pixelsPerDisplay=1])  
- Query the device 'hmd' for its properties and setup internal rendering  
parameters in preparation for opening an onscreen window with [PsychImaging](PsychImaging)  
to display properly on the device. See section about 'AutoSetupHMD' above for  
the meaning of the optional parameters 'basicTask', 'basicRequirements'  
and 'basicQuality'.  
  
'fov' Optional field of view in degrees, from line of sight: [leftdeg, rightdeg,  
updeg, downdeg]. If 'fov' is omitted, the device runtime will be asked for a  
good default field of view and that will be used. The field of view may be  
dependent on the settings in the device user profile of the currently selected  
user. Note: This parameter is ignored with the current driver in 3D mode, ie.  
basicTask '3DVR' or 'Tracked3DVR' on any standard [OpenXR](OpenXR) 1.0 backend, as the  
driver auto-selects optimal field of view for 3D perspective correct rendering.  
In the 2D modes 'Monoscopic' or 'Stereoscopic', or in 3D mode with stopped loop,  
the specified field of view will be used for calculating position and size of the  
2D views in use. If omitted the driver will try to auto-detect a meaningful field  
of view. If that is impossible, it will use the hard-coded values of an Oculus  
Rift CV-1 HMD as fallback. In all these cases, the 'PerEyeFOV' keyword will alter  
the method of default view setup from one that only takes the minimal vertical  
field of view min(updeg, downdeg) into account and calculates horizontal size to  
preserve stimulus image aspect ratio, to one that takes all field of view parameters  
into account, even if it causes distortions of shapes.  
  
'pixelsPerDisplay' Ratio of the number of render target pixels to display pixels  
at the center of distortion. Defaults to 1.0 if omitted. Lower values can  
improve performance, at lower quality.  
  
  
[PsychOpenXR](PsychOpenXR)('SetBasicQuality', hmd, basicQuality);  
- Set basic level of quality vs. required GPU performance.  
  
  
oldSetting = [PsychOpenXR](PsychOpenXR)('SetFastResponse', hmd [, enable]);  
- Return old setting for 'FastResponse' mode in 'oldSetting',  
optionally disable or enable the mode via specifying the 'enable'  
parameter as 0 or greater than zero.  
  
Deprecated: This function does nothing. It just exists for (backwards)  
compatibility with [PsychVRHMD](PsychVRHMD).  
  
  
oldSetting = [PsychOpenXR](PsychOpenXR)('SetTimeWarp', hmd [, enable]);  
- Return old setting for 'TimeWarp' mode in 'oldSetting',  
optionally enable or disable the mode via specifying the 'enable'  
parameter as 1 or 0.  
  
Deprecated: This function does nothing. It just exists for (backwards)  
compatibility with [PsychVRHMD](PsychVRHMD).  
  
  
oldSetting = [PsychOpenXR](PsychOpenXR)('SetLowPersistence', hmd [, enable]);  
- Return old setting for 'LowPersistence' mode in 'oldSetting',  
optionally enable or disable the mode via specifying the 'enable'  
parameter as 1 or 0.  
  
Deprecated: This function does nothing. It just exists for (backwards)  
compatibility with [PsychVRHMD](PsychVRHMD).  
  
  
oldSettings = [PsychOpenXR](PsychOpenXR)('PanelOverdriveParameters', hmd [, newparams]);  
Deprecated: This function does nothing. It just exists for (backwards)  
compatibility with [PsychVRHMD](PsychVRHMD).  
  
  
[PsychOpenXR](PsychOpenXR)('SetHSWDisplayDismiss', hmd [, dismissTypes=1+2+4]);  
- Set how the user can dismiss the "Health and safety warning display".  
Deprecated: This function does nothing. It just exists for (backwards)  
compatibility with [PsychVRHMD](PsychVRHMD).  
  
  
[bufferSize, imagingFlags, stereoMode] = [PsychOpenXR](PsychOpenXR)('GetClientRenderingParameters', hmd);  
- Retrieve recommended size in pixels 'bufferSize' = [width, height] of the client  
renderbuffer for each eye for rendering to the device. Returns parameters  
previously computed by [PsychOpenXR](PsychOpenXR)('SetupRenderingParameters', hmd).  
  
Also returns 'imagingFlags', the required imaging mode flags for setup of  
the [Screen](Screen) imaging pipeline. Also returns the needed 'stereoMode' for the  
pipeline.  
  
  
needPanelFitter = [PsychOpenXR](PsychOpenXR)('GetPanelFitterParameters', hmd);  
- 'needPanelFitter' is 1 if a custom panel fitter task is needed, and the 'bufferSize'  
from the [PsychVRHMD](PsychVRHMD)('GetClientRenderingParameters', hmd); defines the size of the  
clientRect for the onscreen window. 'needPanelFitter' is 0 if no panel fitter is  
needed.  
  
  
[winRect, ovrfbOverrideRect, ovrSpecialFlags, ovrMultiSample, screenid] = [PsychOpenXR](PsychOpenXR)('OpenWindowSetup', hmd, screenid, winRect, ovrfbOverrideRect, ovrSpecialFlags, ovrMultiSample);  
- Compute special override parameters for given input/output arguments, as needed  
for a specific device. Take other preparatory steps as needed, immediately before the  
[Screen](Screen)('OpenWindow') command executes. This is called as part of [PsychImaging](PsychImaging)('OpenWindow'),  
with the user provided hmd, screenid, winRect etc.  
  
  
isOutput = [PsychOpenXR](PsychOpenXR)('IsHMDOutput', hmd, scanout);  
- Returns 1 (true) if 'scanout' describes the video output to which the  
device 'hmd' is connected. 'scanout' is a struct returned by the [Screen](Screen)  
function [Screen](Screen)('ConfigureDisplay', 'Scanout', screenid, outputid);  
This allows probing video outputs to find the one which feeds the device.  
Deprecated: This function does nothing. It just exists for (backwards)  
compatibility with [PsychVRHMD](PsychVRHMD).  
  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/PsychVRToolbox/PsychOpenXR.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/PsychVRToolbox/PsychOpenXR.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/PsychVRToolbox/PsychOpenXR.m</code>
</div>

