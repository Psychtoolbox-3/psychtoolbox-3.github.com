# [FileFromFolder](FileFromFolder)
##### >[Psychtoolbox](Psychtoolbox)>[PsychFiles](PsychFiles)

[file,nfile] = [FileFromFolder](FileFromFolder)(folder,mode,ext)  
  
Returns struct with all files in directory FOLDER.  
MODE specifies whether an error is displayed when no directories are  
found (default). If MODE is 'silent', only a message will will be  
displayed in the command window, if 'ssilent', no notification will be  
produced at all. If left empty, default is implied.  
Ext is an optional filter on file extension. If specified, only files  
with the specified extension will be found. It can be a cell vector of  
strings for filtering on multiple extensions  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychFiles/FileFromFolder.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychFiles/FileFromFolder.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychFiles/FileFromFolder.m</code>
</div>

