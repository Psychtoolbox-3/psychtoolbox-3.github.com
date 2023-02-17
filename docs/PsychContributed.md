# [PsychContributed](PsychContributed)
##### >[Psychtoolbox](Psychtoolbox)>[PsychContributed](PsychContributed)

Psychtoolbox:[PsychContributed](PsychContributed)  
  
Scripts and software contributed by Psychtoolbox users, and  
third-party tools and software that are used in Psychtoolbox. These  
third-party tools are covered by different licenses which allow distribution  
with Psychtoolbox, but are not neccessarily free-software or open-source.  
See the descriptions below or the help files of the functions for  
exact licensing conditions of individual contributions.  
  
NOTE: All the content in the [PsychContributed](PsychContributed) folder is not officially  
supported or even neccessarily tested at all by the Psychtoolbox developers.  
  
It is provided "as is" with no guarantee that it will work on your setup  
at all, or that it will keep working on your setup, e.g., after operating  
system upgrades. If something breaks, you are completely on your own!  
  
Additionally, code in this folder may be removed at any time for any reason  
without previous warning, or changed in its functionality or calling syntax  
in a backwards incompatible way.  
  
Use at your own risk!  
  
  
  
  
linux\_blacklist\_kinectvideo  Blacklist file for Linux, to be copied into the  
                             /etc/modprobe.conf/ directory. Disables the Linux  
                             standard video driver for Microsoft Kinect box. Allows  
                             use of the Kinect with [PsychKinect](PsychKinect)() driver et al.  
                             See 'help InstallKinect'.  
  
[ATIRadeonperf](ATIRadeonperf)                [ATIRadeonperf](ATIRadeonperf)\_Linux and [ATIRadeonperf](ATIRadeonperf)\_Windows.exe are  
                             compiled Linux and Windows executables that are called  
                             as helpers from the function [PsychGPUControl](PsychGPUControl)() via a  
                             system() call, ie., they execute in the system shell as  
                             separate processes.  
  
                             These binaries perform the actual GPU setup work on behalf  
                             of [PsychGPUControl](PsychGPUControl)() using ATI/AMD proprietary low-level  
                             API's. The API's are available to registered developers from  
                             AMD/ATI as "ADL SDK" without royalty fees. While the SDK  
                             license does allow redistribution of executables using the  
                             SDK, it doesn't allow redistribution in source code form.  
                             For that reason, these tools are only made available as  
                             precompiled binaries for your use, not under any open-source  
                             or free-software license. The tools were compiled by Mario  
                             Kleiner, so contact him if you have further questions about  
                             the tools.  
  
[AutoBrightness](AutoBrightness)               Obsolete: Use [MacDisplaySettings](MacDisplaySettings)() instead.  
  
                             Helper function [AutoBrightness](AutoBrightness) allows to control the  
                             setting of the "Automatically adjust brightness" control  
                             on Apple OSX, ie., it allows to control if display brightness  
                             should be automatically adjusted based on ambient light, or not.  
                             This uses [AppleScript](AppleScript) for its job. It may not work reliably on  
                             future OSX versions and will not work on other operating  
                             systems. Tested on OSX 10.10. Contributed by Denis Pelli.  
  
Eduloggers/                  Simple functions for accessing Edulogger devices from https://neulog.com  
  
Kinect-v16-[WindowsDrivers](WindowsDrivers).zip Zip file containing the Microsoft Windows  
                              drivers and installer that are needed to  
                              use the Microsoft XBOX Kinect under  
                              Windows. Type "help [PsychKinect](PsychKinect)" for more  
                              infos. The [PsychSourceGL](PsychSourceGL)/Cohorts/Kinect-v16-withsource.zip  
                              file contains corresponding source code.  
  
[MacDisplaySettings](MacDisplaySettings)           Allows temporary override of any macOS user customization  
                             of the display, to allow calibration and user testing with  
                             stable display settings.  
  
x64/libusb-1.0.dll           This is the 64-Bit Windows version of libusb-1.0  
                             for 64-Bit Matlab/Octave/Python from ...  
                             https://libusb.info  
                             The dll is used by 64-Bit [PsychHID](PsychHID) on MS-Windows.  
                             It is licensed under LGPL v2+. You can get a  
                             more recent version of this dll from the  
                             website mentioned above if you like.  
  
libusb-1.0.dll               libusb-1.0.dll in the [PsychContributed](PsychContributed) folder itself  
                             is a corresponding copy for 32-Bit Octave/Python.  
  
                             The corresponding source code for both 32 Bit and  
                             64-Bit libusb-1.0.dll's for MS-Windows can be found  
                             in the [PsychSourceGL](PsychSourceGL)/Cohorts/libusb1-win32/  
                             subfolder after you have downloaded the full  
                             Psychtoolbox source (help [UseTheSource)](UseTheSource)).  
  
simplepsychtoolboxsetup.sh   Configure OS X priority. DO NOT USE ANYMORE!  
  
ple                          Prints useful debugging output, including a stack trace in case  
                             a script exits via rethrow() or [psychrethrow](psychrethrow)(). See help ple for  
                             copyright info.  
  
read\_rle\_rgbe                Reader routine for RLE encoded RGBE high dynamic range images.  
                             See help read\_rle\_rgbe for copyright & authorship info. This is  
                             a helper routine for [ReadHDR](ReadHDR) - the recommended function for user  
                             scripts.  
  
vcredist\_x64\_2015-2019.exe   Microsoft Visual C++ 2015-2019 runtime 64-Bit  
                             redistributable installer. You must use this  
                             to install the Visual C runtime if you want  
                             to use the Psychtoolbox for 64-Bit Matlab on  
                             Microsoft Windows.  
  
vcredist\_x64\_2010.exe        Microsoft Visual C++ 2010 runtime 64-Bit  
                             redistributable installer. You may need this  
                             to install the Visual C runtime if you want  
                             to use the Psychtoolbox for 64-Bit Matlab on  
                             Microsoft Windows.  
  
[WinJoystickMex](WinJoystickMex)               [WinJoystickMex](WinJoystickMex) is a very simple/rudimentary  
                             joystick driver for basic query of position  
                             and button state of joysticks under  
                             MS-Windows, written by Mario Kleiner. The  
                             code is contributed under [GPLv2](GPLv2).  
  
[WinTab](WinTab)/                      This folder contains the (unsupported!)  
                             [WinTabMex](WinTabMex) MEX file driver (and its C source  
                             code) for controlling touch/digitizer  
                             tablets via the [WinTab](WinTab) API on Microsoft  
                             Windows operating systems. It also contains  
                             some basic usage instructions and two M-File  
                             demos, contributed by Andrew Wilson.  
  
gpuclockctrl                 A version of gpuclockctrl compiled for 64-Bit Linux on Intel.  
                             This should be part of FeralInteractive's gamemode package,  
                             but was missing at least in the v1.3.1 ppa, so we deliver  
                             our own copy as a stop-gap measure until the Ubuntu ppa's  
                             are fixed. Gets auto-installed by [PsychLinuxConfiguration](PsychLinuxConfiguration) if  
                             appropriate. Works at least on Ubuntu 18.04-LTS and 19.04,  
                             with [NVidia](NVidia) and AMD graphics.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychContributed/Contents.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychContributed/Contents.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychContributed/Contents.m</code>
</div>

{{category}}