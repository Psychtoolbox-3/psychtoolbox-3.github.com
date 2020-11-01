# [UpdatePsychtoolbox](UpdatePsychtoolbox)
##### >[Psychtoolbox](Psychtoolbox)

[UpdatePsychtoolbox](UpdatePsychtoolbox)(targetdirectory, targetRevision)  
  
Update your working copy of the Psychtoolbox with the latest bug fixes,  
enhancements, and features from our Git server.  
  
If you are using a Psychtoolbox provided by [NeuroDebian](NeuroDebian), then this is not  
needed. You will be automatically notified of updates to Psychtoolbox by  
your operating systems update manager as soon as they become available.  
  
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
  
[UpdatePsychtoolbox](UpdatePsychtoolbox) cannot change the beta-vs-stable flavor of your  
Psychtoolbox. To change the flavor, run [DownloadPsychtoolbox](DownloadPsychtoolbox) again.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/UpdatePsychtoolbox.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/UpdatePsychtoolbox.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/UpdatePsychtoolbox.m</code>
</div>

