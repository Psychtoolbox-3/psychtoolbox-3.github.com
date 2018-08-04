# [VideoDVCamCaptureDemo](VideoDVCamCaptureDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

Demonstrate simple use of built-in video capture engine with DV consumer cameras.  
  
[VideoDVCamCaptureDemo](VideoDVCamCaptureDemo)([fullscreen=0][, fullsize=0][, roi][, depth][,deviceId=0][, moviename])  
  
NOTE: As of October 2014, DV video camera capture has not been tested at  
all on MS-Windows, as [[GStreamer](GStreamer)][(GStreamer)]((GStreamer))-1 currently doesn't ship with video  
capture plugins for MS-Windows. On Apple OSX 10.9.5 Mavericks with our  
new [[GStreamer](GStreamer)][(GStreamer)]((GStreamer))-1 video capture engine, video capture from DV did not work,  
neither with Psychtoolbox, nor with [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) command line tools or other  
independent open source video capture applications. Only Apples Facetime  
app managed to get a marginally useable video stream from the DV camera.  
Testing on Linux with this specific demo showed mixed results. However on  
Linux there is a slightly hacky way that makes it work somewhat reliably  
with the new backend by exposing the camera as a regular video source, so  
all regular video capture/recording/processing demos can be used for DV  
capture, without any need for special treatment like in this demo. Read  
the section below for further instructions for a reliable DV setup on  
Linux.  
  
[VideoDVCamCaptureDemo](VideoDVCamCaptureDemo) initializes the first attached and supported DV  
firewire consumer camera, then shows its video image in a Psychtoolbox  
window. A press of the [ESCape](ESCape) key ends the demo.  
  
### Optional parameters:  
  
'fullscreen' If set to non-zero value, the image is displayed in a  
fullscreen window, as usual, otherwise a normal GUI window is used.  
  
'fullsize' If set to 1, the cameras image is scaled up to full screen  
resolution, ie. so it fills the maximum amount of display area, but  
preserving the original aspect ratio.  
  
'roi' Set to [0 0 720 576] for a PAL-DV camera and [0 0 720 480] for a  
NTSC-DV camera. Default is PAL if omitted.  
  
'deviceId' Device index of video capture device. Defaults to system  
default. You can also specify a gst-launch style string to define a  
videosource here. Or you can set the special string deviceId = 'X' so  
builtin spec strings suitable for each operating system will be used.  
  
'moviename' Name string for selection of filename of a target movie file  
to which video should be recorded. Defaults to none,ie., no video  
recording.  
  
[VideoDVCamCaptureDemo](VideoDVCamCaptureDemo) also allows you to test out video capture from  
special video sources other than Consumer-DV cameras, ie. sources which  
require use of a custom built [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) video source bin. You test such  
setups by specifying the bin spec-string and other parameters as parameters  
for the demo. As an example, the following call would try to capture a video  
stream that is encoded as H264 video and that is transmitted over the network  
via TCP-IP protocol, ie., a H264 video stream encapsulated in TCP:  
  
[VideoDVCamCaptureDemo](VideoDVCamCaptureDemo)([], [], [0 0 320 240], 6, 'tcpclientsrc port=8554 host=localhost ! h264parse ! avdec\_h264 name=ptbdvsource');  
  
This would receive the TCP stream from port 8554 on the machine with  
the name 'localhost' (the local machine). The stream would decode from  
H264 to color format 6 - YUV-I420 - with video frames of 320 x 240 pixels  
size. For testing purpose you could enter the following [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) command  
line into a terminal window to generate a test video stream and send it from  
the local machine 'localhost' on port 8554, as H264 encoded TCP-IP stream,  
then receive it via [VideoDVCamCaptureDemo](VideoDVCamCaptureDemo) as shown above:  
  
gst-launch-1.0 videotestsrc horizontal-speed=5 ! x264enc tune="zerolatency" threads=1 ! video/x-h264,stream-format=byte-stream ! tcpserversink port=8554  
  
One application of such a custom setup can be seen in the discussion thread  
containing message \#18807 on the Psychtoolbox forum. There the video source  
is an IP camera attached to a robot, streaming H264 video over the network for  
consumption by a machine running Psychtoolbox.  
  
  
  
  
### Loopback setup on Linux for use with new [[GStreamer](GStreamer)][(GStreamer)]((GStreamer))-1 video backend:  
  
This specific configuration was shown to work at least on Ubuntu 14.04  
LTS with a Sony PAL-DV firewire camera. After following the setup steps,  
demos like our standard [VideoCaptureDemo](VideoCaptureDemo), [VideoRecordingDemo](VideoRecordingDemo), ... worked  
without any special configuration or treatment of DV cameras.  
  
Here you need to install a [Video4Linux2](Video4Linux2) loopback kernel module. It will  
allow to create virtual video sources, from which Psychtoolbox can  
read/capture/process record live video. Then some external application  
can feed video into those virtual sources. You then attach an external  
command line DV capture session as video source.  
  
1. Install the package "v4l2loopback-dkms" to get the kernel module installed and  
   loaded. A "sudo apt-get install v4l2loopback-dkms" on Ubuntu 14.04-LTS  
   and later distributions should do the trick. The package is probably  
   also available on Debian, other Debian/Ubuntu derived distros etc. Or  
   you get the most recent version to compile and install from source  
   code from the homepage of the project:  
   https://github.com/umlaeute/v4l2loopback  
  
2. You may or may not need to "sudo modprobe v4l2loopback" on first use.  
  
3. Then you use a [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) video capture pipeline launched from a terminal  
   window to connect to your DV camera, capture live video and feed it  
   into the virtual video loopback device. An example launch line can  
   look like this:  
  
   gst-launch dv1394src ! dvdemux ! dvdec ! v4l2sink device=/dev/video0  
  
   This would make live video from the first connected DV camera  
   available on /dev/video0. See  
   https://github.com/umlaeute/v4l2loopback/wiki for more detailed  
   instructions.  
  
   If this doesn't work for you with [[GStreamer](GStreamer)][(GStreamer)]((GStreamer))-1 you may need to install  
   good old [[GStreamer](GStreamer)][(GStreamer)]((GStreamer))-0.10 in addition to the already installed  
   [[GStreamer](GStreamer)][(GStreamer)]((GStreamer))-1 and instead use the gst-launch-0.10 command instead of the  
   gst-launch command to select for the old implementation.  
  
4. Psychtoolbox video capture functions should now report and be able to  
   use a new virtual video capture device with a name like "Dummy video  
   device 0000" or some name defined by you. Psychtoolbox should be able  
   to video capture or record video from that device aka your DV video  
   camera.  
  
   The Wiki of v4l2loopback describes more elaborate setups, e.g., for  
   capturing from multiple video DV cameras.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/VideoDVCamCaptureDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/VideoDVCamCaptureDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/VideoDVCamCaptureDemo.m</code>
</div>

