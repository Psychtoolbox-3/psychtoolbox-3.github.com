# [CalDataFolder](CalDataFolder)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

directory=[CalDataFolder](CalDataFolder)([forceDemo],[calFileName],[calDir],[noWarning])  
  
Get the path to the [CalData](CalData) folder.  
  
If "forceDemo" is true (false by default), then force use of  
[PsychCalDemoData](PsychCalDemoData).  Otherwise return location of [PsychCalLocalData](PsychCalLocalData)  
if it exists, and [PsychCalDemoData](PsychCalDemoData) if it [PsychCalLocalData](PsychCalLocalData) does  
not exist.  
  
If calFileName is passed, it checks if the specified file exists  
in the top level of the directory it located.  If so, it returns  
that directory.  If not, it searches the first level subdirectories  
of the top level directories and if the specfied file is in one of  
them, returns that.  Skips subdirs called 'xOld', 'Plots', and those  
that begin with '.'.  
  
calFileName can either have .mat postpended or not.  
  
If calDir is passed as a string, that is used as the directory, with  
the subdir searching as above.  
  
See also [LoadCalFile](LoadCalFile), [SaveCalFile](SaveCalFile).  
  
Denis Pelli 7/25/96  
Denis Pelli 2/28/98 change "[CalDat](CalDat)" to "[PsychCalData](PsychCalData)"  
8/14/00  dhb  Add alternate name, change names.  
4/1/07   dhb  Fix subtle bug in error message when there are duplicate cal  
              folders on path.  
3/7/08   mpr  changed documentation to make it consistent (apparently  
              "forceDemo" used to be "alt"  
4/2/13   dhb  Add calFileName and associated behavior.  
6/2/13   dhb  Make this properly return subfolder containing calibration file  
              if .mat is not postpended.  
6/10/13  dhb  Fix buglet introduced 6/2/13 -- need to handle empty calFileName (thanks to MS for  
              identifying the problem and the fix.  
3/29/16  dhb  Allow multiple [PsychCalDemo](PsychCalDemo) data on path, but issue a warning printout.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/CalDataFolder.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/CalDataFolder.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/CalDataFolder.m</code>
</div>

