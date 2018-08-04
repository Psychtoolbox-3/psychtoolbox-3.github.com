# [GetGitPath](GetGitPath)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

gitpath = [GetGitPath](GetGitPath) -- Return auto-detected installation path  
for git client, if any. Return empty string if auto-detection not  
possible. Typical usage is like this:  
  
mygitcommand = [[GetGitPath](GetGitPath) 'git describe']; system(mygitcommand);  
  
[GetGitPath](GetGitPath) will return the path to be prefixed in front of the git  
executable. If none can be found, the git executable will be executed  
without path spec. If it is installed in the system executable search  
path, it will then still work.  
  
The function simply checks if the git executable is in the Matlab path  
and returns a proper path-spec. If it isn't found in the Matlab path, it  
tries default path locations for OS-X and Windows. If that doesn't work,  
it returns an empty string.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/GetGitPath.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/GetGitPath.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/GetGitPath.m</code>
</div>

