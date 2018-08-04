# [DirList](DirList)
##### >[Psychtoolbox](Psychtoolbox)>[PsychFiles](PsychFiles)

str = [DirList](DirList)(dirnm,qdispfiles,lim,pref, folderFilter, fileFilter, qRelPath)  
recursively lists directories en returns the whole shit  
as a string  
all inputs except the first are optional  
QDISPFILES is a boolean indicating whether files should also be listed  
(true, default)  
LIM is the maximum number of levels that will be listed (default unlimited (inf))  
PREF is a prefix for each node in the directorylist  
FOLDERFILTER is to filter out unwanted folders (regexp). If a match  
occurs, the directory \_IS NOT\_ output and not recursed into  
FILEFILTER is to filter out unwanted files (regexp). If a match  
occurs, the files \_ARE\_ output. Use e.g. '\.m$' to only display files with  
.m extensions, '\.mat$|\.m$' to include all files with .mat or .m files.  
default: '.', shows all files.  
QRELPATH if true, a listing of existing paths relative to DIRNM. Default  
false  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychFiles/DirList.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychFiles/DirList.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychFiles/DirList.m</code>
</div>

