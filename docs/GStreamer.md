# [GStreamer](GStreamer)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDocumentation](PsychDocumentation)

[[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) - Installation instructions for the [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) media framework.  
  
Psychtoolbox uses the [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) multi-media framework for all multi-media  
related operations. On Windows with Matlab, [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) is also needed for  
high quality text rendering via [Screen](Screen)('DrawText').  
  
All movie playback, movie creation, video capture and video recording  
operations are based on [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)). These functions won't work without a  
working [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) installation on your system (with the exception of video  
capture from firewire DCAM/IIDC machine vision cameras on Linux and OSX).  
  
You will need at least version 1.4 of [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) on Linux and OSX and version  
1.16 on Windows, but we recommend to use the latest available stable  
release of the version 1 series.  
  
### Installation instructions:  
  
  
### GNU/Linux:  
  
Any decent Linux distribution will include support for [[GStreamer](GStreamer)][(GStreamer)]((GStreamer))-1 in its  
package management system, so you can easily install it via the software  
management tools of your system. If you install PTB via [NeuroDebian](NeuroDebian), then most  
[[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) packages will get automatically installed, with the possible exception  
of some optional packages with potential license or patent restrictions, so read on.  
  
You may need to install those extra plugin packages to play back all  
common audio and video file formats like MP3 and MP4. Video or movie  
recording with high quality [(DivX]((DivX), H.264) may also require recent  
versions of additional plugin packages which contain support for these  
formats. These may not installed by default due to licensing and patent  
clauses in place for some territories on this planet. You may want to  
specifically add them to your system depending on your format needs.  
  
An easy test is to run [SimpleMovieDemo](SimpleMovieDemo). If it fails or only plays sound,  
but not video, then some of the plugins are missing, e.g., the important  
"gst-libav" plugins.  
  
  
### MS-Windows and Apple OSX:  
  
macOS: You must install [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) if you want to use multi-media functions or  
if you want to use the high-quality text renderer with Matlab, which provides  
consistent, fast, high-quality text rendering, instead of the lower quality  
legacy Apple [CoreText](CoreText) text renderer.  
  
If you don't intend to use such functionality then installation of  
[[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) is optional on macOS. [Screen](Screen) will work normally, but abort with an  
error message if you try to use any multi-media functions.  
  
Windows: You must install [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) regardless if you want to use multi-media  
functionality or not, as the [Screen](Screen)() mex file won't work at all without  
[[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) installed! You must install at least version 1.16.0 of the MSVC build  
variant of [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)).  
  
### Here is a FAQ entry on resolving [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) problems:  
  
<https://github.com/Psychtoolbox-3/Psychtoolbox-3/wiki/FAQ\#how-to-resolve-gstreamer-problems\>  
  
NOTE: If [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) complains about not being able to find some plugins,  
e.g., the video playback doesn't work because there is a [[GStreamer](GStreamer)][(GStreamer)]((GStreamer))  
configuration problem, then it can help to delete the [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) plugin  
registry to force a rebuild of that database. E.g., under Windows-10, if your  
login user name would be Bob, you would probably have to delete the file:  
  
'C:\Users\Bob\[AppData](AppData)\Local\Microsoft\Windows\[INetCache](INetCache)\gstreamer-1.0\registry.x86\_64.bin'  
  
  
### Download and install the latest 64-Bit ("x86\_64") [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) runtimes from:  
  
<http://gstreamer.freedesktop.org/download/\>  
  
The following [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) runtime packages have been tested for good compatibility  
with Psychtoolbox 3.0.16 as of August 2019:  
  
For MS-Windows: 64-Bit Intel MSVC runtime v1.16.0 for use with 64-Bit Matlab/Octave.  
  
<https://gstreamer.freedesktop.org/data/pkg/windows/1.16.0/gstreamer-1.0-msvc-x86\_64-1.16.0.msi\>  
  
You \*must\* install the MSVC variants of [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)), not the [MinGW64](MinGW64) variants!  
  
  
For Apple OSX: Runtime v1.16.0  
  
<https://gstreamer.freedesktop.org/data/pkg/osx/1.16.0/gstreamer-1.0-1.16.0-x86\_64.pkg\>  
  
  
When the installer asks you to select the components it should install,  
select a "Custom installation" (instead of a "Basic installation" or such).  
Then, if you chose a "Custom installation" in the displayed check list of packages  
to install, select \*all\* components manually, if you want support for all  
video formats and all functionality. Without this, many popular video  
formats like H264 video will not play at all, or video recording / video  
capture and similar functions may not work. In fact, even our own demos,  
e.g., [SimpleMovieDemo](SimpleMovieDemo) \*will fail\* if you don't have all codecs installed!  
-\> If [SimpleMovieDemo](SimpleMovieDemo) doesn't work, then the most likely cause is that  
you didn't select all [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) packages for installation, so restart the  
installer and repeat installation with the full set of packages.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDocumentation/GStreamer.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDocumentation/GStreamer.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDocumentation/GStreamer.m</code>
</div>

