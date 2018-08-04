# [AddToMatlabPathDynamically](AddToMatlabPathDynamically)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

[AddToMatlabPathDynamically](AddToMatlabPathDynamically)(directory)  
  
Add the directory and its subdirectories to Matlab's path, dynamically,  
with strippint out of .svn and .git directories.  
  
Use for putting routines onto path that are specifict to a particular  
project, without them staying around and clogging up the name space.  
  
Typical usages:  
a) When getting version info  
  exp.mFileName = mfilename;  
  [exp.versionInfo,exp.codeDir] = [GetAllVersionInfo](GetAllVersionInfo)(exp.mFileName);  
  [AddToMatlabPathDynamically](AddToMatlabPathDynamically)(exp.codeDir);  
  
b) Direct call  
  [AddToMatlabPathDynamically](AddToMatlabPathDynamically)( fileparts(which(mfilename)));   
  
7/12/13  dhb  Wrote it.  
7/25/14  dhb  Make independent of [BrainardLab](BrainardLab) idiosyncracies.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/AddToMatlabPathDynamically.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/AddToMatlabPathDynamically.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/AddToMatlabPathDynamically.m</code>
</div>

