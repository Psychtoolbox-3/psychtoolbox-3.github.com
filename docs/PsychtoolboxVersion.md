# [PsychtoolboxVersion](PsychtoolboxVersion)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

  
[versionString, versionStructure] = [PsychtoolboxVersion](PsychtoolboxVersion)  
  
Return a string identifying this release of the Psychtoolbox.  
The first three numbers identify the base version of Psychtoolbox:  
  
- Leftmost (major version): Increments indicate a disruptive change in  
the feature set, application programming interfaces or core design of the  
software, by abrupt introduction of drastic design changes. This should  
never happen, as this would mean a completely new product, entirely  
incompatible with the old software.  
  
- Middle (minor version): Increments indicate very significant  
enhancements or changes in functionality. This would for example happen  
if there would be backwards incompatible changes to the programming  
interface or functionality which may require code adjustments in user  
code or even choosing different hardware or operating systems to run it.  
This will usually only happen every couple of years at most.  
  
- Rightmost (patch level): A counter to distinguish multiple releases  
having the same leftmost and middle version numbers. It increments if we  
cancel support for platforms (Matlab/Octave versions, operating system  
versions, processor architectures etc.). This happens occasionally.  
  
Numeric values of the three integer fields contained in versionString are  
available in fields of the second return argument, "versionStructure".  
  
If Psychtoolbox was installed using Neurodebian or GIT, this source  
is available in the field 'Flavor'.  
  
### Using SVN, the field 'Flavor' defines the subtype of Psychtoolbox being used:  
  
\* beta: The term 'current' is a synonym for 'beta'. Beta releases are the  
only releases we provide at this point. 'Beta' is a historical name, not  
anything is really much of beta quality about them, they are considered  
the most stable and trustworthy releases.  
  
\* trunk: Development prototypes, for testing and debugging by developers  
and really adventurous users, not for production use!  
  
\* Psychtoolbox-x.y.z: Old, no longer supported Psychtoolbox versions.  
  
\* Debian package: A Psychtoolbox provided by GNU/Debian, Ubuntu or [NeuroDebian](NeuroDebian).  
  
The revision number and the provided URL allows you to visit the developer  
website in the Internet and get direct access to all development logs  
regarding your working copy of Psychtoolbox.  
  
Be aware that execution of the [PsychtoolboxVersion](PsychtoolboxVersion) command can take a lot  
of time (in the order of multiple seconds to 1 minute).  
  
Most Psychtoolbox mex files now provide a built-in 'Version' command  
which returns version for themselves.  The version string for the  
built-in version numbers contains a fourth numeric field named "build".  
The build number is a unique serial number.  Mex files distinguished only  
by build numbers were compiled from identical C source files.  
  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
see also: [Screen](Screen)('Version')  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/PsychtoolboxVersion.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/PsychtoolboxVersion.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/PsychtoolboxVersion.m</code>
</div>

