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
  
You will need at least version 1.2 of [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) on Linux and version 1.4  
on Windows or OSX, but we recommend to use the latest available stable  
release of the version 1 series.  
  
### Installation instructions:  
  
  
### GNU/Linux:  
  
Any recent 2013 Linux distribution will include support for [[GStreamer](GStreamer)][(GStreamer)]((GStreamer))-1 in its  
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
  
You must install [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) if you want to use multi-media functions!  
You must also install [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) if you want to use the high-quality text  
renderer on Windows with Matlab, which provides consistent text rendering  
with OSX and Linux, instead of the lower quality legacy GDI text renderer.  
  
If you don't intend to use such functionality then installation of  
[[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) is optional. [Screen](Screen) will work normally, but abort with an error  
message if you try to use any multi-media functions. For use with Octave-4 on  
Windows you must install [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) regardless if you want to use multi-media  
functionality or not, as the [Screen](Screen)() mex file won't work at all without [[GStreamer](GStreamer)][(GStreamer)]((GStreamer))  
installed.  
  
NOTE: Many Matlab versions on MS-Windows show instable behavior with [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)),  
e.g., crashing in [SimpleMovieDemo](SimpleMovieDemo) and other demos that use [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)), unless  
they are used without the Graphical user interface and without Java. That means  
you need to start Matlab with the -nojvm command line switch, ie. matlab.exe -nojvm.  
See also: https://github.com/Psychtoolbox-3/Psychtoolbox-3/wiki/FAQ\#how-to-resolve-gstreamer-problems  
  
  
### Download and install the latest 64-Bit ("x86\_64") [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) runtimes from:  
  
<http://gstreamer.freedesktop.org/download/\>  
  
You should check for and install the latest runtime packages available for your  
system for best reliability and performance. However, as a convenience, at time  
of this writing (January 2017) the required downloads would be:  
  
For MS-Windows: 64-Bit Intel runtime v1.10.2 for use with 64-Bit Matlab/Octave.  
  
<http://gstreamer.freedesktop.org/data/pkg/windows/1.10.2/gstreamer-1.0-x86\_64-1.10.2.msi\>  
  
For Apple OSX: Runtime v1.10.2  
  
<http://gstreamer.freedesktop.org/data/pkg/osx/1.10.2/gstreamer-1.0-1.10.2-x86\_64.pkg\>  
  
  
When the installer asks you to select the components it should install,  
select a "Custom installation" (instead of "Full installation" or "Basic  
installation" or such). Then, in the displayed check list of packages to  
install, select \*all\* components manually, if you want support for all  
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

