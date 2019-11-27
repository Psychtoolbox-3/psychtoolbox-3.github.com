# [PsychtoolboxKernelDriver](PsychtoolboxKernelDriver)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDocumentation](PsychDocumentation)

[PsychtoolboxKernelDriver](PsychtoolboxKernelDriver) - A low level support driver for Apple OS-X  
  
The [PsychtoolboxKernelDriver](PsychtoolboxKernelDriver) (PKD) is a [MacOS](MacOS)-X kernel extension (a  
kext). It currently should somewhat work with AMD/ATI Radeon graphics cards  
of the X1000 series, as well as the HD2000 series up to the AMD RX 400 "Polaris"  
graphics cards. Some recent Polaris gpu's and all Vega gpu's and later models  
are unsupported at the moment.  
  
On [NVidia](NVidia) cards, only beamposition queries for high precision timestamping  
are supported. Intel graphics chips are mostly not supported.  
  
The driver needs to be manually installed by a user with administrator  
privileges and provides a few special services to PTB-3, ie., PTB's  
functionality is extended/enhanced if it detects such a driver at startup  
time:  
  
\* Beamposition queries (See help [BeampositionQueries)](BeampositionQueries)) allow for  
especially robust and accurate stimulus onset timestamping. They are  
no longer supported by OS-X 10.9 and later and were not supported at all  
on Intel based Macintosh computers with AMD/ATI or Intel graphics.  
The driver restores this functionality for [NVidia](NVidia) and AMD/ATI gpu's.  
Support for Intel gpu's is disabled by default, as it can lead to system  
crashes due to some unfixable incompatibility of Intel graphics hardware  
which is completely out of our control.  
  
\* Multihead display sync: The driver allows to synchronize the display  
refresh cycles of the displays connected to a multihead graphics card  
to allow for high quality tear-free binocular and stereo stimulation of  
subjects. This is only supported on AMD/ATI graphics cards.  
  
\* Use of 10 bit per color component framebuffers: The driver enabled two  
extra bits of color output precision per color channel on your card,  
allowing for 1 billion shades of different colors instead of the 16.8  
million colors available without the driver. This was only supported on  
AMD/ATI graphics cards and is no longer supported since Psychtoolbox 3.0.14,  
as Apple sabotaged our ability to provide this functionality on OSX 10.11  
and later.  
  
\* The driver implements workarounds to fix some problems caused by  
graphics driver and operating system bugs when the graphics card is used  
with high color/luminance precision display devices like the CRS Bits+ or  
Bits\# boxes, or the [VPixx](VPixx) Inc. [DataPixx](DataPixx) and [ViewPixx](ViewPixx) devices, and similar  
equipment. This is only supported on AMD/ATI graphics hardware and may not  
work anymore on latest AMD gpu's or macOS versions -- unknown.  
  
The driver only works with one single graphics card at a time. On a  
single-gpu system it will just work. On a [MacBookPro](MacBookPro) hybrid-graphics  
system with an integrated intel gpu and a discrete [NVidia](NVidia) or AMD gpu, it  
will automatically switch to use the proper gpu. On a multi-gpu system  
with multiple discrete gpu's, e.g., [MacPro](MacPro) with multiple graphics cards  
installed, it will use the default gpu zero by default. You can ask it use a  
different gpu by calling the command [PsychTweak](PsychTweak)('UseGPUIndex', gpuidx);  
to select gpu 'gpuidx' - numbering starts at zero. Then call clear  
[Screen](Screen), so [Screen](Screen)() actually picks up the new setting. Simultaneous use  
of multiple gpu's is not supported at this time.  
  
As this driver accesses the hardware at a very low level, bypassing the  
whole operating system, its graphics subsystem and drivers, there is  
some potential for things to go wrong. Although our testing over 10 years  
didn't show any such problems, it could happen on some future OSX systems.  
That is why this driver is considered a permanently experimental feature.  
  
# How to install (one time setup) - on OSX 10.11 "El Capitan" and later only  
  
Install the [PsychtoolboxKernelDriver64Bit](PsychtoolboxKernelDriver64Bit).kext.zip, as exemplified here.  
  
### You must type this into the terminal:  
  
cd /Library/Extensions/  
sudo unzip /[PathToPsychtoolbox](PathToPsychtoolbox)/Psychtoolbox/[PsychHardware](PsychHardware)/[PsychtoolboxKernelDriver64Bit](PsychtoolboxKernelDriver64Bit).kext.zip  
  
"[PathToPsychtoolbox](PathToPsychtoolbox)" must be replaced with the path to the Psychtoolbox folder, e.g., if your  
Psychtoolbox is installed under /Users/kleinerm/Psychtoolbox, then the above command would  
look like this:  
  
sudo unzip /Users/kleinerm/Psychtoolbox/[PsychHardware](PsychHardware)/[PsychtoolboxKernelDriver64Bit](PsychtoolboxKernelDriver64Bit).kext.zip  
  
  
This will automatically load the driver after a few seconds, and also after  
each system restart.  
  
If the driver fails to load, then please report it to the Psychtoolbox forum.  
If it fails to load due to invalid cryptographic signatures you can disable  
"System integrity protection" (SIP) as a temporary measure. The Internet will  
tell you how to do that. This would make the kernel driver load, but reduce  
resistance of your system against potential hacker/virus/trojan horses attacks  
and other security threats.  
  
If you are a user of OSX 10.13 "High Sierra" or later, the iToys company put up  
some additional obstacles on top of all the awfulness of macOS. Read these  
instructions if you get the error message "System policy prevents loading the kernel extension."  
from "kextload", or it fails for some other reason:  
  
https://developer.apple.com/library/content/technotes/tn2459/\_index.html  
  
If you are using macOS 10.14 "Mojave", the driver may not load at all unless  
you disable SIP. Apple put additional obstacles in our way, because Apple!  
  
If you use some of the latest and most overprized Apple computers with some  
models of "AMD Radeon Pro" 500 series RX gpu's and Psychtoolbox doesn't recognize  
your graphics card, you may need to install this updated driver instead:  
  
/[PathToPsychtoolbox](PathToPsychtoolbox)/Psychtoolbox/[PsychHardware](PsychHardware)/[PsychtoolboxKernelDriverUpTodDate](PsychtoolboxKernelDriverUpTodDate)\_Unsigned.kext.zip  
  
This driver is not yet cryptographically signed or attestated by us, so macOS may  
throw extra obstacles into your way, e.g., not loading the driver automatically at  
system boot, requiring you to do it manually with a kextload or kexttool command  
from a terminal window. Disable SIP and other than that, good luck!  
  
Another limitation on Apples latest "masterpieces" is that auto-detection of screen  
to video output mappings may not work reliably on multi-display setups. Read how  
to work around this in "help [DisplayOutputMappings](DisplayOutputMappings)".  
  
# How to upgrade with a more recent version, bundled with a new version of Psychtoolbox  
  
### You can unload and delete the driver before a driver upgrade via:  
  
sudo kextunload /Library/Extensions/[PsychtoolboxKernelDriver](PsychtoolboxKernelDriver).kext  
sudo rm -R /Library/Extensions/[PsychtoolboxKernelDriver](PsychtoolboxKernelDriver).kext  
  
On older setups, the driver may reside in /System/Library/Extensions/, so  
delete it from there if above does not work:  
  
sudo kextunload /System/Library/Extensions/[PsychtoolboxKernelDriver](PsychtoolboxKernelDriver).kext  
sudo rm -R /System/Library/Extensions/[PsychtoolboxKernelDriver](PsychtoolboxKernelDriver).kext  
  
Then you can follow the instructions for installation above.  
  
If everything went well, Psychtoolbox will report availability (and its  
use) of the driver the first time the [Screen](Screen)() mex file gets loaded and  
used. If it doesn't happen immediately, type "clear [Screen](Screen)" to force a  
reload of [Screen](Screen).  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDocumentation/PsychtoolboxKernelDriver.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDocumentation/PsychtoolboxKernelDriver.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDocumentation/PsychtoolboxKernelDriver.m</code>
</div>

