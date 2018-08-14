# [VideoCaptureDC1394](VideoCaptureDC1394)
##### >[Psychtoolbox](Psychtoolbox)>[PsychVideoCapture](PsychVideoCapture)

[VideoCaptureDC1394](VideoCaptureDC1394) - Setup instructions for IEEE-1394 firewire video  
capture.  
  
Psychtoolbox on GNU/Linux and [MacOSX](MacOSX) supports a special video capture  
engine for IIDC compliant machine vision cameras connected via IEEE-1394  
firewire bus or via USB bus and Firewire-over-USB protocol.  
  
This engine with engineID 1, as selectable via ...  
[Screen](Screen)('[Preference](Preference)', 'DefaultVideocaptureEngine', 1)  
... provides especially precise low-level control over the cameras, high  
framerates, low-latency and high timing precision.  
  
The engine is based on the open-source library libdc1394. For more info  
about it see 'help VideoCapture' in the section about professional class  
video capture engines.  
  
### INSTALLATION:  
  
On Linux, usually no installation is required if you use the Psychtoolbox  
provided by Debian or Ubuntu via the Debian main package archive or the  
[NeuroDebian](NeuroDebian) project. If you have a different Linux distribution, you'll  
need to install the "libdc1394" package via your distributions software  
manager, e.g., via "sudo apt-get install libdc1394" on a Debian based  
system.  
  
The software manager on Linux will keep your system up to date with the  
latest stable version of the library.  
  
On [MacOS](MacOS)/X for 64-Bit Matlab & Octave: [Screen](Screen)() links dynamically against  
a system-installed .dylib version of the library, if such a version is  
installed on your system. A precompiled library can be found in the  
Psychtoolbox/[PsychVideoCapture](PsychVideoCapture)/ subfolder as libdc1394.22.dylib. Copy it  
into the /usr/local/lib/ folder via executing this function  
'VideoCaptureDC1394' and entering your administrator password on request.  
The corresponding source code of this library can be found in the source  
code distribution of Psychtoolbox (see "help [UseTheSource](UseTheSource)") under:  
[PsychSourceGL](PsychSourceGL)/Cohorts/libDC1394/ as libdc1394-2.2.0.tar at the moment of  
this writing. However, you can download the most recent copies of the  
libraries from libDC's sourceforge website anytime and install it instead  
to get access to the latest features and bugfixes. Another way to get the  
library installed is via Homebrew: "brew install libdc1394".  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychVideoCapture/VideoCaptureDC1394.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychVideoCapture/VideoCaptureDC1394.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychVideoCapture/VideoCaptureDC1394.m</code>
</div>

