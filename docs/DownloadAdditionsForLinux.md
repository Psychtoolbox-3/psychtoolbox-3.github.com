# [DownloadAdditionsForLinux](DownloadAdditionsForLinux)
##### >[Psychtoolbox](Psychtoolbox)

[DownloadAdditionsForLinux](DownloadAdditionsForLinux)(targetdirectory [, flavor]);  
  
THIS FUNCTION DOES NO LONGER WORK, AS GITHUB HAS REMOVED THEIR  
SUBVERSION FRONTEND, WHICH IT CRITICALLY REQUIRES, FROM THEIR SERVICES  
PERMANENTLY AT 8TH JANUARY 2024.  
  
Due to the lack of financial support for Psychtoolbox by the vast  
majority of our non-paying users, we did not and currently do not have  
the funding to work on a good alternative solution for this.  
  
Try to manually download and install the Datapixx or Eyelink mex files,  
which this function would normally install for you. Other than that,  
see http://psychtoolbox.org/download.html\#alternate-download for a  
workable, although way less convenient and advanced, download and  
installation method, via zip file download and execution of  
[SetupPsychtoolbox](SetupPsychtoolbox)(). Good luck!  
  
=========================================================================  
  
Install missing Matlab or Octave mex files for versions of the Psychtoolbox  
which are directly provided by some Linux distributions, e.g., Ubuntu 20.04  
and later.  
  
You \*DO NOT NEED\* this function if you downloaded Psychtoolbox from its  
home-site via [DownloadPsychtoolbox](DownloadPsychtoolbox)(), or if you install Psychtoolbox from  
the [NeuroDebian](NeuroDebian) repository. If you installed from [NeuroDebian](NeuroDebian), then for  
Matlab nothing extra needs to be done. For Octave, to add the Datapixx  
or Eyelink functions execute this in a terminal:  
  
sudo apt install octave-psychtoolbox-3-nonfree  
  
If you would call this function from within Octave, it will download only  
a few additional addon files for the Octave Psychtoolbox. Currently the  
only added files are the Eyelink mex files for SR-Research Eyelink  
Gazetrackers, and the Datapixx mex file for [VPixx](VPixx) Inc. products.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/DownloadAdditionsForLinux.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/DownloadAdditionsForLinux.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/DownloadAdditionsForLinux.m</code>
</div>

