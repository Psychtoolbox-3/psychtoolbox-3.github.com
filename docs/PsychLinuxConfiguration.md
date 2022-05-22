# [PsychLinuxConfiguration](PsychLinuxConfiguration)
##### >[Psychtoolbox](Psychtoolbox)

[PsychLinuxConfiguration](PsychLinuxConfiguration)([answers]) -- Optimize setup of Linux system.  
  
This script modifies system settings and configuration files  
to optimize a Linux system for use with Psychtoolbox.  
  
Currently it modifies files to allow to run Octave or Matlab  
as regular non-root user, ie. without need for root login or  
the "sudo" command. It does so by changing file permissions  
and resource usage limits to allow a regular user application  
to switch to realtime scheduling, lock its memory, and to  
access special purpose hardware like [GPUs](GPUs), Bits+, Datapixx and  
other research equipment.  
  
Realtime optimizations are achieved by extending the  
/etc/security/limits.conf file with entries that allow  
members of the Unix user group "psychtoolbox" to lock  
application memory into physical RAM, eliminating/minimizing  
interference from the VM subsystem, and to run with realtime  
priorities up to level 50. The group "psychtoolbox" is created  
if it does not already exist.  
  
If the target system has a /etc/security/limits.d/ directory,  
then a separate rule file is stored to that directory to  
achieve the change without messing around with the limits.conf  
file.  
  
root-less hardware access is achieved by copying a special  
psychtoolbox.rules file into the /etc/udev/rules.d/ directory.  
This udev rules file contains rules to auto-detect certain  
hardware at bootup or when the hw is hot-plugged and to  
reconfigure this hw or access permission for root-less access  
by Psychtoolbox, and for optimal performance for the kind  
of typical PTB use cases.  
  
The script also creates a /etc/X11/xorg.conf.d/ directory for  
xorg.conf configuration files which are writable by members  
of the 'psychtoolbox' group to allow easy reconfiguration of  
the X11 display system for running experiment sessions.  
  
Additionally it configures the gpu's to allow for display color  
depths of more than 8 bpc. Furthermore, it configures a potentially  
installed gamemoded daemon to further optimize cpu and graphics  
performance for use with Psychtoolbox.  
  
The script calls into the shell via "sudo" to achieve this  
setup task, which itself needs admin privileges to modify  
system files etc. "sudo" will prompt the user for his admin  
password to complete the tasks.  
  
The script also checks if any special configuration is required  
to work around Linux specific [OpenGL](OpenGL) quirks of Matlab R2014b or  
later.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychLinuxConfiguration.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychLinuxConfiguration.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychLinuxConfiguration.m</code>
</div>

