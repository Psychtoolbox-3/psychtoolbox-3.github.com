# [SaveCalFile](SaveCalFile)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

[SaveCalFile](SaveCalFile)(cal, [filespec], [dir])  
  
Saves calibration data in the structure "cal" to a  
calibration file in the [CalData](CalData) folder.  
  
If filespec is not passed, then it saves to default.mat  
in the [CalData](CalData) folder.  If filespec is an integer, saves  
to screenN.mat.  If filespec is a string, saves to string.mat.  
You can also pass the name with the training .mat already there.  
  
Saves to existing file if it is found, otherwise creates a  
new calibration file.  
  
See also [LoadCalFile](LoadCalFile), [CalDataFolder](CalDataFolder).  
  
5/28/96  dgp  Wrote it.  
6/6/96   dgp  Use [CalibrationsFolder](CalibrationsFolder).  
7/25/96  dgp  Use [CalDataFolder](CalDataFolder).  
8/4/96   dhb  More flexible filename interface.  
8/21/97  dhb  Rewrite for cell array convention.  
8/25/97  dhb, pbe  Fix bug in cell array handling.  
8/26/97  dhb  Make saving code parallel [LoadCalFile](LoadCalFile).  
5/18/99  dhb  Add optional directory arg.  
8/10/00  dhb  Fix loading code for default.mat  
7/9/02   dhb  Incorporate filespec/filename fix as suggested by Eiji Kimura.  
3/27/12  dhb  Pass dir to [LoadCalFile](LoadCalFile) call, so that it does the right thing  
              in cases where cal file location is expilcitly passed.  
4/2/13   dhb  Updated for subdir searching logic.  
4/12/13  dhb  Make this save to cal file folder when file doesn't yet exist.  
6/2/13   dhb  More robust about whether passed filespec contains the trailing '.mat'.  
11/30/14 dhb  Handle case where .mat isn't in passed filename, and name is less then 5 chars long.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/SaveCalFile.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/SaveCalFile.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/SaveCalFile.m</code>
</div>

