# [UpdatePsychtoolbox](UpdatePsychtoolbox)
##### >[Psychtoolbox](Psychtoolbox)

[UpdatePsychtoolbox](UpdatePsychtoolbox)([targetdirectory][, targetRevision][, tryNonInteractiveSetup=0])  
  
THIS UPDATER DOES NO LONGER WORK, AS GITHUB HAS REMOVED THEIR  
SUBVERSION FRONTEND, WHICH IT CRITICALLY REQUIRES, FROM THEIR SERVICES  
PERMANENTLY AT 8TH JANUARY 2024.  
  
Due to the lack of financial support for Psychtoolbox by the vast  
majority of our non-paying users, we did not and currently do not have  
the funding to work on a good alternative solution for this. Therefore  
this convenient installation and update method will be unavailable for an  
unknown period of time.  
  
See http://psychtoolbox.org/download.html\#alternate-download for a  
workable, although way less convenient and advanced, download and  
installation method, via zip file download and execution of  
[SetupPsychtoolbox](SetupPsychtoolbox)(). Good luck!  
  
=========================================================================  
  
Update your working copy of the Psychtoolbox with the latest bug fixes,  
enhancements, and features from our Git server.  
  
If you are using a Psychtoolbox provided by [NeuroDebian](NeuroDebian), then this is not  
needed. You will be automatically notified of updates to Psychtoolbox by  
your operating systems update manager, as soon as they become available.  
  
The "targetdirectory" argument is optional. If present, it specifies the path  
of the Psychtoolbox folder to update. If omitted, [UpdatePsychtoolbox](UpdatePsychtoolbox) will  
update the Psychtoolbox folder reported by [PsychtoolboxRoot](PsychtoolboxRoot)(). Examples:  
  
[UpdatePsychtoolbox](UpdatePsychtoolbox)  
[UpdatePsychtoolbox](UpdatePsychtoolbox)('~/Applications/Psychtoobox')  
  
The "targetRevision" argument is optional and should be normally omitted.  
Normal behaviour is to upgrade your working copy to the latest revision.  
If you provide a specific targetRevision, then this script will  
\*downgrade\* your copy of Psychtoolbox to the specified revision. This is  
only useful if you experience problems after an update and want to revert  
to an earlier known-to-be-good release. Revisions can be specified by a  
revision number or by the special flag 'PREV' which should downgrade to  
the revision before the most current one. By executing this script  
multiple times with the 'PREV' specifier, you could incrementally  
downgrade until stuff works for you.  
  
[UpdatePsychtoolbox](UpdatePsychtoolbox) cannot change the flavor of your Psychtoolbox. To  
change the flavor, run [DownloadPsychtoolbox](DownloadPsychtoolbox) again.  
  
The optional parameter 'tryNonInteractiveSetup' if provided as 1 (true), will  
try a setup without user interaction, not asking users for input in certain  
situations, but assuming an answer that keeps the setup progressing. Note that  
this is not guaranteed to work in all cases, and may end in data loss, e.g.,  
overwriting an old and potentially user-modified Psychtoolbox installation.  
This non-interactice setup mode is highly experimental, not well tested, not  
supported in case of any trouble!  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/UpdatePsychtoolbox.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/UpdatePsychtoolbox.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/UpdatePsychtoolbox.m</code>
</div>

