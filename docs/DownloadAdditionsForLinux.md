# [DownloadAdditionsForLinux](DownloadAdditionsForLinux)
##### >[Psychtoolbox](Psychtoolbox)

[DownloadAdditionsForLinux](DownloadAdditionsForLinux)(targetdirectory [, flavor]);  
  
Install missing Matlab or Octave mex files for older versions of the  
Psychtoolbox, as provided by some Linux distributions, e.g., Ubuntu 12.10  
or (as of April 2013) 13.04.  
  
It needs Subversion to be installed on your machine (sudo apt-get install  
subversion).  
  
You \*do not need\* this function if you downloaded Psychtoolbox from its  
home-site via [DownloadPsychtoolbox](DownloadPsychtoolbox)(), or if you install Psychtoolbox from  
the [NeuroDebian](NeuroDebian) repository. If you install from [NeuroDebian](NeuroDebian), simply  
install these packages:  
  
### For Matlab:  
  
Basic Mex files:      sudo apt-get install matlab-psychtoolbox-3  
Datapixx and Eyelink: sudo apt-get install matlab-psychtoolbox-3-nonfree  
  
For Octave, if you want to use the Datapixx or Eyelink functions:  
sudo apt-get install octave-psychtoolbox-3-nonfree  
  
However, some Linux distributinos bundle Psychtoolbox as part of their  
standard package repository, e.g., Ubuntu 12.10 and 13.04, and they  
provide outdated packages (as of April 2013) which require you to run  
this script manually after each installation or update in order to  
retrieve mex files for Matlab, or the Datapixx and Eyelink mex files for  
octave.  
  
You can call this function from within Matlab, providing the full path to  
a directory. The function will create a new folder [PsychtoolboxAddOns](PsychtoolboxAddOns)  
inside that directory and add it to your path. The add on files will be  
downloaded from the Psychtoolbox main repository and stored there.  
  
After this function successfully completes, your Psychtoolbox should work  
with Matlab on Linux as well.  
  
If you call this function from within Octave, it will download only a few  
additional addon files for the Octave Psychtoolbox. Currently the only  
added files are the Eyelink mex files for SR-Research Eyelink  
Gazetrackers, and the Datapixx mex file for [VPixx](VPixx) Inc. products.  
  
This function should eventually become obsolete when the regular mainstream  
Linux distributions update their packaged versions of Psychtoolbox.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/DownloadAdditionsForLinux.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/DownloadAdditionsForLinux.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/DownloadAdditionsForLinux.m</code>
</div>

