# [VideoIPWebcamCaptureDemo](VideoIPWebcamCaptureDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

Demonstrate use of built-in video capture engine with the Android [IPWebcam](IPWebcam) app,  
or with a local videoloopback source, e.g., a [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) screencast.  
  
[VideoIPWebcamCaptureDemo](VideoIPWebcamCaptureDemo)([videourl='http://192.168.178.22:8080/videofeed'][fullscreen=0][, fullsize=1][, moviename])  
  
if 'videourl' is left out, or a URL then [VideoIPWebcamCaptureDemo](VideoIPWebcamCaptureDemo)  
connects to a IP web video stream streamed from an Android device by  
the Android [IPWebcam](IPWebcam) application, available from the Google Play Store here:  
  
https://play.google.com/store/apps/details?id=com.pas.webcam&hl=en  
  
It then shows its video stream in a Psychtoolbox window.  
A press of the [ESCape](ESCape) key ends the demo.  
  
This demo has been successfully tested on Ubuntu Linux 14.04.5-LTS,  
but should likely work with OSX and Windows as well if the installed  
[[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) framework provides the needed plugins.  
  
If you provide the value 1 as videourl then [VideoIPWebcamCaptureDemo](VideoIPWebcamCaptureDemo) tries  
to source video from a local video source running on port 8554. E.g., on  
Linux you can use the following command in a terminal window to perform  
a screencast from the desktop to port 8554 scaled to 640x480 pixels resolution  
and 30 fps target framerate:  
  
gst-launch-1.0 ximagesrc xname="Psychophysics Toolbox - Yahoo Groups - Mozilla Firefox" use-damage=0 ! video/x-raw,framerate=30/1 ! videoscale method=0 ! video/x-raw,width=640,height=480  ! videoconvert ! x264enc tune="zerolatency" threads=1 ! video/x-h264,stream-format=byte-stream ! tcpserversink port=8554  
  
The specific example would only capture from a Mozilla firefox window with the  
title "Psychophysics Toolbox - Yahoo Groups - Mozilla Firefox"  
  
### The following similar line might achieve screencasting on MS-Windows, but has not been tested:  
  
gst-launch-1.0 gdiscreencapsrc ! video/x-raw,framerate=30/1 ! videoscale method=0 ! video/x-raw,width=640,height=480  ! videoconvert ! x264enc tune="zerolatency" threads=1 ! video/x-h264,stream-format=byte-stream ! tcpserversink port=8554  
  
  
### Optional parameters:  
  
'videourl' If not set, defaults to 'http://192.168.178.22:8080/videofeed'.  
Instead of a URL of a IP Webcam you can also pass in the value 1 to get  
a local videoloopback as shown above, e.g., for a screencast.  
  
'fullscreen' If set to non-zero value, the image is displayed in a  
fullscreen window, as usual, otherwise a normal GUI window is used.  
  
'fullsize' If set to 1, the cameras image is scaled up to full screen  
resolution, ie. so it fills the maximum amount of display area, but  
preserving the original aspect ratio.  
  
'moviename' Name string for selection of filename of a target movie file  
to which video should be recorded. Defaults to none,ie., no video  
recording. 'help VideoRecording' for more info about video recording.  
  
One application of such a custom setup can be seen in the discussion thread  
containing message \#20942 on the Psychtoolbox forum.  
  
  
This section is referring to an alternative way of getting video, which  
can be significantly higher performance and more flexible, but only works  
on Linux. As of this release it has not been tested with [IPWebcam](IPWebcam)!  
  
### See the following [GitHub](GitHub) project for an elegant solution on Linux:  
  
https://github.com/bluezio/ipwebcam-gst  
  
### More background information:  
  
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
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/VideoIPWebcamCaptureDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/VideoIPWebcamCaptureDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/VideoIPWebcamCaptureDemo.m</code>
</div>

