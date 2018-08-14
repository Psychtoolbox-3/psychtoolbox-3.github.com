# [GetSVNInfo](GetSVNInfo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

 svnInfo = [GetSVNInfo](GetSVNInfo)(directoryOrFile)  
  
 Description:  
 Retrieves the svn information on a specified directory or file.  This is  
 essentially a wrapper around the shell command "svn info".  
  
 Input:  
 directoryOrFile (string) - Directory or file name of interest.  
  
 Output:  
 svnInfo (struct) - Structure containing the following information:  
   Path  
    URL  
    [RepositoryRoot](RepositoryRoot)  
    [RepositoryUUID](RepositoryUUID)  
    Revision  
    [NodeKind](NodeKind)  
    Schedule  
    [LastChangedAuthor](LastChangedAuthor)  
    [LastChangedRev](LastChangedRev)  
    [LastChangedDate](LastChangedDate)  
  
    'svnInfo' will be empty if there is no svn info for 'directoryOrFile'.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/GetSVNInfo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/GetSVNInfo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/GetSVNInfo.m</code>
</div>

