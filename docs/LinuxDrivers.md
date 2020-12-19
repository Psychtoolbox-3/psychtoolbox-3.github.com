# [LinuxDrivers](LinuxDrivers)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[LinuxDrivers](LinuxDrivers)

Psychtoolbox/[PsychHardware](PsychHardware)/[LinuxDrivers](LinuxDrivers)  
  
Customized device drivers for Linux.  
  
The subfolder [NVidiaOptimus](NVidiaOptimus)/ contains a customized  
display modesetting driver and configuration files  
for 64-Bit X-Server 1.19, to use [NVidia](NVidia) Optimus  
Laptops with the proprietary [NVidia](NVidia) graphics driver  
instead of the open-source nouveau driver.  
  
CAUTION: These drivers are only for specific processor  
architectures and versions of the X-Server, and thereby  
only for specific versions of specific Linux distributions.  
  
Installation of these drivers on a mismatched/unsuitable  
distribution will likely make your machines GUI unuseable  
by preventing successfull startup of the X-Server!  
  
You can find out which version of X-Server is used on your  
system by typing...  
  
xdpyinfo | grep 'X.Org version'  
  
... into a terminal window. It should report version 1.19 for a  
[XOrg](XOrg) 1.19 server.  
  
### Currently the following drivers are provided:  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/LinuxDrivers/Contents.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/LinuxDrivers/Contents.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/LinuxDrivers/Contents.m</code>
</div>

{{category}}