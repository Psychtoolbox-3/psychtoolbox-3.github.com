# [PsychCamSettings](PsychCamSettings)
##### >[Psychtoolbox](Psychtoolbox)>[PsychVideoCapture](PsychVideoCapture)

rc = [PsychCamSettings](PsychCamSettings)(cmd, grabber [, arg0, arg1, ...])  
  
Setup tool for video sources for use with Psychtoolbox  
video capture functions. This function can mostly only operate  
on IIDC/DCAM machine vision standard compliant camera connected  
via IEEE1394-Firewire bus or USB bus + IIDC protocol. In other  
words, it only operates on cameras controlled via the libdc1394  
firewire video capture engine on Linux and OSX, not on standard  
consumer/prosumer class cameras controlled by the [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) engine,  
e.g., webcams, DV cameras etc.  
  
[PsychCamSettings](PsychCamSettings) is used to query or change settings of such  
a video source that is supported by the [Screen](Screen)() subfunctions  
for video capture. The first parameter, a 'cmd' command string  
specifies the subfunction to execute. The second parameter  
'grabber' is the device handle returned by [Screen](Screen)('OpenVideoCapture').  
All following parameters are dependent on the selected subfunction.  
  
Subfunctions of form 'XXX' change the setting of a parameter XXX.  
Subfunctions of form 'XXX' query the current setting of a parameter XXX.  
Subfunctions of form 'AutoXXX' try to switch parameter XXX into automatic  
control, if supported by the camera or video source.  
  
The type of parameters supported is highly dependent on the specific video  
source. Unsupported parameters are usually "no operations" - silently ignored.  
  
For known camera models, the tool will try to map physically meaningful  
values into camera settings and return camera settings as meaningful properties.  
E.g., exposure time is expected and returned in milliseconds, if the mapping  
for the specific camera is known. Otherwise it is set and returned in arbitrary  
units.  
  
Currently known cameras: Basler A602f grayscale firewire camera. Unibrain Fire-i  
firewire camera. Basler A312fc, AVT Marlin F033.  
  
### Parameters and their meaning:  
  
curval = [PsychCamSettings](PsychCamSettings)('ExposureTime', grabber, val)  
-- Set and/or return current exposure time in milliseconds for supported cams, and  
in raw camera specific system units for unknown cameras.  
  
curval = [PsychCamSettings](PsychCamSettings)('Brightness', grabber, val)  
-- Set/Return brightness setting in arbitrary units. Brightness is the DC offset  
added to the CCD sensor signal before amplification and A/D conversion.  
  
curval = [PsychCamSettings](PsychCamSettings)('Gain', grabber, val)  
-- Set/Return gain setting in arbitrary units. Gain is the multiplier  
applied to the CCD sensor signal during amplification and before A/D conversion.  
  
curval = [PsychCamSettings](PsychCamSettings)('Gamma', grabber, val)  
-- Set/Return gamma setting. Gamma is used to influence or set gamma correction.  
  
curval = [PsychCamSettings](PsychCamSettings)('Sharpness', grabber, val)  
-- Set/Return sharpness setting in arbitrary units. Manipulates digital post-  
processing of images in the camera.  
  
curval = [PsychCamSettings](PsychCamSettings)('WhiteBalance', grabber, val)  
-- Set/Return white-balance setting in arbitrary units. Only meaningful on color cams.  
  
curval = [PsychCamSettings](PsychCamSettings)('Saturation', grabber, val)  
-- Set/Return color saturation setting in arbitrary units. Only meaningful on color cams.  
  
Similar to above are queries and (auto-)settings for: Hue, [WhiteShading](WhiteShading), Iris, Focus, Pan, Tilt,  
Zoom, [CaptureQuality](CaptureQuality), [CaptureSize](CaptureSize), Temperature, [FrameRate](FrameRate), [OpticalFilter](OpticalFilter) and [TriggerDelay](TriggerDelay).  
  
curval = [PsychCamSettings](PsychCamSettings)('BacklightCompensation', grabber, val)  
-- Set/Return setting for backlight compensation mode. Backlight compensation is active  
if control of exposure time, gain and brightness are switched to automatic. It defines  
the algorithm to use for computing the overall image brightness. This is currently  
only supported on the Unibrain Fire-i camera and has the following meaning:  
  
0 = Off. Just average across image.  
1 = Use a disc in the center of the image.  
2 = Use some weighted mix of a disc in the image center and the area outside the disc.  
3 = Use some portrait mode for optimal exposure of a person sitting in front of the cam.  
4 = Use upper third of image.  
5 = Use middle third of image.  
6 = Use lower third of image.  
  
### Special commands and their meaning:  
  
vendor = [PsychCamSettings](PsychCamSettings)('GetVendor', grabber)   
-- Return camera vendor name string.  
  
model = [PsychCamSettings](PsychCamSettings)('GetModel', grabber)   
-- Return camera model name string.  
  
known = [PsychCamSettings](PsychCamSettings)('IsKnownCamera', grabber)  
-- Return 1, if this camera is known to [PsychCamSettings](PsychCamSettings),  
so it can accept and return meaningful physical properties,  
instead of unknown device units.  
  
settings = [PsychCamSettings](PsychCamSettings)('AutomateAllSettings', grabber)  
-- Switch all settings into automatic control mode, where possible,  
and return the current settings in a struct.  
  
settings = [PsychCamSettings](PsychCamSettings)('GetAllSettings', grabber)  
-- Return all known settings in a struct.  
  
oldsettings = [PsychCamSettings](PsychCamSettings)('SetAllSettings', grabber, settings)  
-- Set all settings from a struct 'settings'.  
  
latency = [PsychCamSettings](PsychCamSettings)('EstimateLatency', grabber [, fps])  
-- This command analyses the current camera settings and, based on  
the specification of the camera, tries to estimate the latency (in  
seconds) between start of exposure of a video frame and arrival of  
the video frame in the computers video buffer.  
  
If you subtract this 'latency' value from the 'capturetimestamp'  
returned by the [Screen](Screen)('GetCapturedImage') function, you should  
get an estimate of when (in system time) the image was  
actually acquired that corresponds to the captured image.  
  
Please note: In theory Basler firewire cameras with "SFF cycle timer support"  
should be able to report the start time of image exposure directly via  
the returned capture timestamps if the command ...  
[Screen](Screen)('SetVideoCaptureParameter', grabber, 'BaslerFrameTimestampEnable');  
... was executed before start of capture, therefore making this 'EstimateLatency'  
dance redundant. In practice though, the two tested Basler cameras which should  
support this feature didn't work properly, ie., they returned completely bogus  
capture timestamps when 'BaslerFrameTimestampEnable' was called. Your mileage  
may therefore vary, but it is at least worth a try if you possess a Basler camera.  
  
### Latency is defined as:  
  
Duration of sensor-exposure + sensor readout delay + transmission  
onset delay + time needed for data transfer over Firewire bus or  
other device.  
  
The latency values computed here are based on the official camera  
specs. If the spec is wrong or inaccurate, then this value will  
be wrong or inaccurate as well, so use with caution!  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychVideoCapture/PsychCamSettings.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychVideoCapture/PsychCamSettings.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychVideoCapture/PsychCamSettings.m</code>
</div>

