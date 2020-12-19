# [VideoRecordingDemo](VideoRecordingDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[VideoRecordingDemo](VideoRecordingDemo)(moviename [, codec=0] [, withsound=1] [, showit=1] [, windowed=1])  
  
Demonstrates simple video capture and recording to a movie file.  
  
Supports [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) on all systems, and DC1394 engine on Linux and OSX.  
  
Please look at the source code of the demo carefully! Both [MacOSX](MacOSX) and  
MS-Windows often need special treatment in terms of codec and parameter  
selection to work reliably (or to be honest: To work at all).  
  
The demo starts the videocapture engine, recording video from the default  
video source and (optionally) sound from the default audio source. It  
encodes the video+audio data with the selected 'codec' and writes it to the  
'moviename' movie file. Optionally it previews the recorded  
video onscreen (often at a much lower framerate to keep system load low  
enough for reliable recording). Recording ends if any key is pressed on  
the keyboard.  
  
### Arguments and their meaning:  
  
'moviename' name of output movie file. The file must not exist at start  
of recording, otherwise it is overwritten.  
  
'codec' Indicate the type of video codec you want to use.  
Defaults to "whatever the system default is". Some codecs are very fast,  
i.e., high framerates and low system load, others provide high compression  
rates, i.e., small video files at good quality. Usually there's a tradeoff  
between encoding speed, quality and compression ratio, so you'll have to try  
out different ones to find one suitable for your purpose. Some codecs only  
work at specific framerates or for specific image sizes.  
  
The supported codecs and settings with [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) can be found in the code  
and are explained in 'help VideoRecording'.  
  
Empirically, the MPEG-4 or H264 codecs seem to provide a good tradeoff  
between quality, compression, speed and cpu load. They allow to reliably  
record drop-free sound and video with a resolution of 640x480 pixels at  
30 frames per second.  
  
H.264 has better quality and higher compression, but is able to nearly  
saturate a [MacBookPro](MacBookPro), so reliable recording at 30 fps may be difficult  
to achieve or needs more powerful machines.  
  
Some of the other codecs may provide the highest image quality and lowest  
cpu load, but they also produce huge files, e.g., all the [DVxxx](DVxxx) codecs  
for PAL and NTSC video capture, as well as the component video codecs.  
  
'withsound' If set to non-zero, sound will be recorded as well. This is  
the default.  
  
'showit' If non-zero, video will be shown onscreen during recording  
(default: Show it). Not showing the video during recording will  
significantly reduce system load, so this may help to sustain a skip free  
recording on lower end machines.  
  
'windowed' If set to non-zero, show captured video in a window located at  
the top-left corner of the screen, instead of fullscreen. Windowed  
display is the default.  
  
  
Tip on Linux: If you have an exotic camera which only delivers video in non-standard  
video formats, and Psychtoolbox does not handle this automatically, but aborts with  
some [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) errors, e.g., "source crop failed", or "negotiation error", you may  
be able to work around the problem (after a "clear all" or fresh start), by adding  
this command: setenv('GST\_V4L2\_USE\_LIBV4L2','1');  
This will use of a helper library that can convert some video formats which  
[[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) or Psychtoolbox can not handle automatically yet. In any case, please  
report your problem to the Psychtoolbox user forum, so proper automatic handling  
of your camera model can be added to a future Psychtoolbox version.  
  
Tip for the Microsoft Surface Pro 6 tablet and similar: The builtin cameras only  
work if you explicitely specify the 'pixeldepth' parameter in [Screen](Screen)('OpenVideoCapture')  
as value 6 for YUV-I420 encoding. This seems to be a quirk of the builtin cameras, as  
of Windows-10 (20H2) from December 2020.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/VideoRecordingDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/VideoRecordingDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/VideoRecordingDemo.m</code>
</div>

