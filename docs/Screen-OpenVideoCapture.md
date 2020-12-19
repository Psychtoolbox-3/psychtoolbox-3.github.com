# [Screen('OpenVideoCapture')](Screen-OpenVideoCapture) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

videoPtr = Screen('OpenVideoCapture', windowPtr [, deviceIndex][, roirectangle][, pixeldepth][, numbuffers][, allowfallback][, targetmoviename][, recordingflags][, captureEngineType][, bitdepth=8]);

Try to open the video source 'deviceIndex' for video capture into onscreen  
window 'windowPtr' and return a handle 'videoPtr' on success. If 'deviceIndex'  
is left out, it defaults to zero - use the first capture device attached to your  
machine. You can get a list of all available video capture devices on your  
system via a call to [Screen](Screen)('VideoCaptureDevices'). The positive 'deviceIndex'  
values mentioned there can be used to select a specific video capture device.  
Certain videocapture devices can't get auto-detected and are therefore not  
addressable this way. For such devices you must find out the type and unique  
identifier of the device. Then pass in a negative 'deviceIndex' to tell [Screen](Screen)  
you want to select a hidden device by its name or id, and pass in the name or id  
of that hidden device as string in the argument 'targetmoviename', or via the  
'SetNextCaptureBinSpec=' option in [Screen](Screen)('SetVideoCaptureParameter'). The  
special deviceIndex -9 will create a new [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) videocapture bin out of a  
given gst-launch style 'SetNextCaptureBinSpec=' string and attach that as a  
video source. This allows to create arbitrary [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) video capture pipelines.  
'roirectangle' if specified, defines the requested size for captured images. The  
default is to return the maximum size image provided by the capture device. A  
'roirectangle' setting of [0 0 width height] will not define a region of  
interest, but instead request a video capture resolution of width x height  
pixels, instead of the default maximum resolution. Settings of [left top right  
bottom] will leave video capture at maximum resolution, but crop the images to  
the rectangular subregion as defined by the given left, right, top and bottom  
borders. Such ROI's are only applied to returned video images, not to recorded  
video by default. See the 'recordingflags' settings below on how to adjust this  
behaviour to your needs.  
The real ROI (region of interest) may differ from the requested one, depending  
on the capabilities of your capture device. 'pixeldepth' if provided, asks for  
the number of layers that captured textures should have: 1=Luminance image,  
2=Luminance+Alpha image, 3=RGB image, 4=RGB+Alpha, 5=YCBCR, 6=I420 image.  
Default is to take whatever the capture device provides by default. Different  
devices support different formats so some of these settings may be ignored. Some  
combinations of video capture devices and graphics cards may support a setting  
of 5=YCBCR encoding. If they do, then this is an especially efficient way to  
handle color images, which may result in lower cpu load and higher framerates. A  
format of 6=YUV-I420 should be supported by all modern graphics cards and may  
provide some performance benefits, but your mileage may vary. If you need very  
fast color image capture, try formats 4, 5 and 6 and see which one gives the  
best performance for your setup.  
'numbuffers' if provided, specifies the number of internal video buffers to use.  
It defaults to a value that is optimal for your specific hardware for common  
use. 'allowfallback' if set to 1, will allow Psychtoolbox to use a less  
efficient mode of operation for video capture if your specific hardware or  
operating system setup doesn't allow to use the high-performance mode.  
'allowfallback' defaults to 1 = Allow fallback path.  
'targetmoviename' If you provide a filename for this argument, PTB will record  
the captured video to the specified  movie file on your filesystem. PTB will use  
a default video codec for encoding the video stream. If you want to use a  
specific codec, you can extend the targetmoviename by a string of format  
:[CodecType](CodecType)=xxx , where xxx is the numeric type id or name of the codec.  
Please read 'help VideoRecording' for many more options for tweaking the video  
recording process via the 'targetmoviename' parameter.  
'recordingflags' specify the behaviour of harddisc-recording and some other  
capture operations. Please note that not all flags are supported on all capture  
engines, cameras and operating systems. Unsupported flags will be silently  
ignored. Most flags are only supported with [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) at the moment: 0 (default)  
= Only record video. 2 = Record audio track as well. The value 1 (or 1+2) asks  
PTB to first record into system memory, and only write the movie file after  
capture has been stopped. This allows for higher capture framerates, but is  
limited in recording time by installed memory. Also, this mode currently can  
sometimes cause hangs and crashes of PTB for unknown reasons, so better avoid!  
A setting of 4 will only enable recording, but no return of captured data, i.e.,  
just record to disk. A setting of 8 will avoid some calls that are supposed to  
provide better realtime behaviour, but may cause some problems with some video  
codecs when recording to disk. A setting of 16 will perform most of the heavy  
work on a separate parallel background thread, utilizing multi-core machines  
better.  
A setting of 32 will try to select the highest quality codec for texture  
creation from captured video, instead of the normal quality codec. A setting of  
64 will return capture timestamps in the time base of the video engine (e.g.,  
elapsed time since start of capture, or recording time in movie), instead of the  
default time base, which is regular [GetSecs](GetSecs)() time.  
A setting of 128 will force use of a videorate converter in pure live capture  
mode. By default the videorate converter is only used if video recording is  
active. The converter makes sure that video is recorded (or delivered) at  
exactly the requested capture framerate, even if the system isn't really capable  
of maintaining that framerate: If the video source (camera) delivers frames at a  
too low framerate, the converter will insert duplicated frames to boost up  
effective framerate. If the source delivers more frames than the engine can  
handle (e.g., system overload or video encoding too slow) the converter will  
drop frames to reduce effective framerate. Slight fluctuations are compensated  
by adjusting the capture timestamps. This mechanism guarantees a constant  
framerate in recorded video as well as the best possible audio-video sync and  
smoothness of video, given system constraints. The downside may be that the  
recorded content and returned timestamps don't reflect the true timing of  
capture, but a beautified version. In pure live capture, rate conversion is off  
by default to avoid such potential confounds in the timestamps. Choose this  
options carefully.  
A setting of 256 in combined video live capture and video recording mode will  
restrict video framerate conversion to the recorded videostream, but provide  
mostly untampered true timing to the live capture. By default, framerate  
conversion applies to recording and live feedback if video recording is enabled.  
A setting of 512 requests that ROI's as defined by the 'roirectangle' parameter  
get also applied to recorded video. Without this setting, ROI's only apply to  
live video as returned by [Screen](Screen)('GetCapturedImage',...);  
A setting of 1024 disables application of ROI's to live video as returned by  
[Screen](Screen)('GetCapturedImage',...);  
A setting of 2048 requests immediate conversion of video textures into a format  
suitable as offscreen window, for use with [Screen](Screen)('TransformTexture') or for  
drawing with custom user provided GLSL shaders. Normally this happens  
automatically on first use, asking for it explicitely may have performance or  
convenience benefits.  
A setting of 4096 requests to apply some performance optimizations (the setting  
of filter-caps). This can hurt if a videocapture device refuses to work, with  
some error message about ''check your filtered caps, if any.''. By default, if  
the flag is omitted, some performance loss will be present, but capture will be  
more robust with problematic cameras.  
  
'captureEngineType' This optional parameter allows selection of the video  
capture engine to use for this video source. Allowable values are currently 1  
and 3. A value of 1 selects Firewire video capture via the free software library  
libdc1394-V2. That engine only supports high performance IIDC machine vision  
cameras that are compliant with the IIDC-1.x standard and are connected via a  
Firewire (IEEE-1394) bus system or via USB-3 [USBVision](USBVision) standard. Use of the  
engine with such cams allows for much higher flexibility and performance than  
use of video capture via [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)), however one restriction is that sound  
recording isn't yet supported with this capture engine. This IIDC capture engine  
is supported on Linux and to a lesser degree on [MacOSX](MacOSX), but not on MS-Windows.  
  
A value of 3 selects the [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) video capture engine. This engine is  
supported on all operating systems and allows for video and sound recording of  
captured video and audio streams. Type 'help [[GStreamer](GStreamer)][(GStreamer]((GStreamer))' for installation and  
setup instructions for the required [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) runtime libraries.  
  
If you don't specify 'captureEngineType', the global setting from  
[Screen](Screen)('[Preference](Preference)', 'DefaultVideoCaptureEngine') will be used. If you don't  
specify that either then engine selection will default to [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)).  
  
To summarize:   
[[GStreamer](GStreamer)][(GStreamer)]((GStreamer)): Is the engine of choice for all operating systems and with most  
standard applications.  
Firewire engine: Supports only Firewire machine vision cameras, but allows free  
selection among all connected cameras, simultaneous operation of many cameras,  
low latency, high framerates and reliability, precise timestamping and low level  
access to many special features of such cameras, e.g., gain-, shutter-,  
exposure-, trigger controls etc.  
  
'bitdepth' Optional parameter to ask for video capture in a certain color or  
luminance resolution, a certain number of bits per color or luminance component,  
also known as bpc. Defaults to 8 bpc if omitted, ie., 8 bits or 1 Byte  
resolution per luminance or color channel for classic 256 levels of intensity.  
Lower values are unsupported and will get rounded up to 8 bpc. Higher values may  
be supported by some higher end professional class cameras. If you ask for an  
unsupported value, the engine will try to get the lowest supported value that  
matches or exceeds what you want. Currently the libdc1394 engine for pro-class  
IIDC compliant firewire or USB machine vision cameras supports bitdepth \> 8 bpc  
on capable cameras. The [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) engine always supports 8 bpc and it may  
support 16 bpc on capable cameras. Please note that requesting \> 8 bpc will  
cause a substantial increase in both video bus bandwidth and memory consumption:  
Twice the bus bandwidth and two to four times the amount of memory per video  
frame, so tread carefully.  
  


###See also:
[CloseVideoCapture](Screen-CloseVideoCapture) [StartVideoCapture](Screen-StartVideoCapture) [StopVideoCapture](Screen-StopVideoCapture) [GetCapturedImage](Screen-GetCapturedImage)
