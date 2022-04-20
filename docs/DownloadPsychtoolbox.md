# [DownloadPsychtoolbox](DownloadPsychtoolbox)
##### >[Psychtoolbox](Psychtoolbox)

[DownloadPsychtoolbox](DownloadPsychtoolbox)([targetdirectory][, flavor][, targetRevision][, downloadmethod][, tryNonInteractiveSetup=0])  
  
This script downloads the latest GNU/Linux, MS-Windows, or Apple macOS  
Psychtoolbox-3, version 3.0.10 or later, from our git-server to your  
disk, creating your working copy, ready to use as a new toolbox in your  
MATLAB/OCTAVE application. Subject to your permission, any old  
installation of the Psychtoolbox is first removed. It's a careful  
program, checking for all required resources and privileges before it  
starts.  
  
Note: If you use a Debian derived Linux distribution, e.g., Debian or  
Ubuntu, consider installing the package octave-psychtoolbox-3 or  
matlab-psychtoolbox-3 instead from http://neuro.debian.net - This is more  
convenient and will provide you with automatic updates.  
  
CAUTION: Psychtoolbox 3.0.14 will not work anymore with OSX versions  
earlier than 10.11 "El Capitan".  
  
CAUTION: Psychtoolbox 3.0.13 will not work anymore with 32-Bit Octave-4  
on MS-Windows, or with OSX versions earlier than 10.10 "Yosemite".  
Psychtoolbox will likely work with versions of Microsoft Windows older  
than Windows-10, but it is not tested on such systems anymore and not  
supported at all on Windows versions earlier than Windows-7. For best  
compatibility you should probably use Windows-10 with all upgrades  
installed.  
  
CAUTION: Psychtoolbox 3.0.12 will not work anymore with 32-Bit Matlab, or  
with OSX versions earlier than 10.8 "Mountain Lion". Psychtoolbox may  
work with versions of Microsoft Windows older than Windows-7, but it is  
not tested or supported on such ancient Windows systems anymore, so use  
at your own risk.  
  
Psychtoolbox 3.0.11 \*will not work\* with GNU/Octave on MS-Windows, or  
with 32-Bit Octave on OSX, as support for these setups has been cancelled  
for the 3.0.10 series. It will also not work with 32-Bit Matlab on OSX,  
or with OSX versions earlier than 10.6.8 "Snow Leopard", unless you  
choose the unsupported legacy flavor "Psychtoolbox-3.0.10" via the  
optional 'flavor' parameter.  
  
If you want to download older versions of Psychtoolbox than 3.0.10, e.g.,  
version 3.0.9, use the [DownloadLegacyPsychtoolbox](DownloadLegacyPsychtoolbox)() function instead of  
this function.  
  
On Mac OSX, all parameters are optional. On MS-Windows and GNU/Linux, the  
first parameter "targetdirectory" with the path to the installation  
target directory is required. The "targetdirectory" name may not contain  
any white space, otherwise download may fail with mysterious error  
messages!  
  
On OSX, your working copy of the Psychtoolbox will be placed in either  
your /Applications or your /Users/Shared folder (depending on permissions  
and your preference), or you may specify a 'targetdirectory', as you  
prefer.  
  
On Microsoft Windows, you must specify the full path, including  
the drive name where Psychtoolbox should be installed, e.g.,  
'C:\[MyToolboxes](MyToolboxes)\'.  
  
The desired flavor of a Psychtoolbox release can be selected via the  
optional "flavor" parameter: By default, 'beta' (aka 'current') will be  
installed if you don't specify otherwise, as this is almost always the  
best possible choice. You may be able to download an old versioned  
release via a namestring like 'Psychtoolbox-x.y.z', e.g.,  
'Psychtoolbox-3.0.14' if you'd want to download version 3.0.14. This is  
only useful if you run a very old operating system or Matlab version that  
isn't supported by the current "beta" anymore, so you'd need to stick  
with an old versioned release.  
  
Normally your download should just work(TM). Very infrequently, the  
download servers may be overloaded or down for maintenance, resulting in  
download failure. In that case, please retry a few hours later.  
  
  
The "targetRevision" argument is optional and should be normally omitted.  
Normal behaviour is to download the latest revision of Psychtoolbox. If  
you provide a specific targetRevision, e.g., 1234 for revision 1234, then  
this script will install a copy of Psychtoolbox according to the  
specified revision.  
  
This is only useful if you experience problems and want to revert to an  
earlier known-to-be-good release.  
  
Revisions can be specified by a revision number or by the special flag  
'PREV' which will choose the revision before the most current one.  
  
  
'downloadmethod' Optional: The method to use or prefer for download. By  
default method 0 is used, which means to perform a Subversion checkout of  
a fully versioned working copy, including all revision information, which  
allows to go backward in time or update efficiently via the  
[UpdatePsychtoolbox](UpdatePsychtoolbox)() command, query the current version and revision of  
Psychtoolbox via [PsychtoolboxVersion](PsychtoolboxVersion)() command, and access the  
development history via svn command-line tools etc. A setting of 1  
requests an export without versioning information, essentialy a dumb  
download. This will cut download size and disc space usage in less than  
half, but you won't be able to use [UpdatePsychtoolbox](UpdatePsychtoolbox)() or  
[PsychtoolboxVersion](PsychtoolboxVersion)() or other svn features anymore.  
  
By default, the most efficient and convenient method of Subversion  
download is used, e.g., using Matlabs integrated [SVNKit](SVNKit) for Matlab R2014b  
or later, instead of a svn command-line client. You can always enforce  
use of an installed svn command-line client via setting downloadmethod to  
-1. This is the old way of doing things, in case the improved method via  
[SVNKit](SVNKit) should not work for some reason.  
  
  
The optional parameter 'tryNonInteractiveSetup' if provided as 1 (true), will  
try a setup without user interaction, not asking users for input in certain  
situations, but assuming an answer that keeps the setup progressing. Note that  
this is not guaranteed to work in all cases, and may end in data loss, e.g.,  
overwriting an old and potentially user-modified Psychtoolbox installation.  
This non-interactice setup mode is highly experimental, not well tested, not  
supported in case of any trouble!  
  
  
INSTALLATION INSTRUCTIONS: The Wiki contains much more up to date  
instructions. If in doubt, follow instructions on the Wiki!  
  
0. If you are using Matlab R2014b or later, skip to step 2.  
  
  
1. On older Matlab versions, or on Octave, if you don't already have it,  
you must install a Subversion client.  
  
  
On Linux, use the OS package manager, e.g., on Debian/Ubuntu based  
systems:  
  
sudo apt install subversion  
  
  
On Windows, download the Windows Subversion client from the internet, e.g.,  
from one of these:  
  
http://subversion.apache.org/packages.html\#windows  
http://www.wandisco.com/subversion/download\#windows  
  
  
On macOS, if you happen to have [HomeBrew](HomeBrew) (http://brew.sh) installed, a  
  
brew install subversion  
  
should do the trick.  
  
  
After installation of the Subversion client, you will need to exit and  
restart Matlab or Octave, so it can find the new subversion executable.  
  
Btw. you should avoid to install the client into a path that contains  
blanks/spaces/white-space as this can lead to download failures in some  
cases, e.g., 'C:\Program Files\...' may be bad because there is a blank  
between the "Program" and "Files".  
  
Alternatively, if you don't have the neccessary permissions to install  
Subversion into a system folder, you can install Subversion into an  
arbitrary folder on your system (excluding ones with blanks in their  
path) and then add that folder to your Matlab or Octave path. E.g. you  
installed into D:\[MyOwnFolder](MyOwnFolder)\Subversion\ . Then you can do this:  
addpath('D:\[MyOwnFolder](MyOwnFolder)\Subversion\'). Our installer should find the  
client then.  
  
  
2. On macOS, to install the Psychtoolbox in the default location  
(/Applications or, failing that, /Users/Shared). Just type:  
  
[DownloadPsychtoolbox](DownloadPsychtoolbox)  
  
Our standard option is in the Applications folder, but note that, as with  
installation of any software, you'll need administrator privileges. Also  
note that if you put the toolbox in the Applications folder, you'll need  
to reinstall it when MATLAB / OCTAVE is updated on your machine. If you  
must install without access to an administrator, we offer the option of  
installing into the /Users/Shared/ folder instead. If you want to install  
the Psychtoolbox in some other folder, then specify it in the optional  
first argument of your call.  
  
On Windows or Linux, provide a pathname, e.g.:  
[DownloadPsychtoolbox](DownloadPsychtoolbox)('C:\[MyToolboxes](MyToolboxes)\');  
  
That's it. Any pre-existing installation of the Psychtoolbox will be  
removed (if you approve). The program will then download the latest  
Psychtoolbox and update your MATLAB / OCTAVE path and other relevant  
system settings.  
  
Enjoy! If you're new to this, you might start by typing "help  
Psychtoolbox".  
  
P.S. If you get stuck, first check the FAQ section and Download section  
of our Wiki at http://www.psychtoolbox.org. If that doesn't help, post  
your question to the forum:  
  
https://psychtoolbox.discourse.group  
  
Please specify your full name and the version of your operating system,  
MATLAB / OCTAVE, and psychtoolbox.  
  
### UPGRADE INSTRUCTIONS:  
  
To upgrade your copy of Psychtoolbox, at any time, to incorporate the  
latest bug fixes, enhancements, and new features, just type:  
[UpdatePsychtoolbox](UpdatePsychtoolbox)  
  
[UpdatePsychtoolbox](UpdatePsychtoolbox) cannot change the flavor of your Psychtoolbox. To  
change the flavor, run [DownloadPsychtoolbox](DownloadPsychtoolbox) to completely discard your  
old installation and get a fresh copy with the requested flavor. If you  
used [DownloadPsychtoolbox](DownloadPsychtoolbox) with the optional 'downloadmethod' set to 1  
then [UpdatePsychtoolbox](UpdatePsychtoolbox)() won't work. That's the price you pay for saving  
disc space.  
  
### PERMISSIONS:  
  
There's a thorny issue with permissions on OS/X. It may not be possible  
to install into /Applications (or whatever the targetdirectory is) with  
the user's existing privileges. The normal situation on Mac OSX is that a  
few users have "administrator" privileges, and many don't. By default,  
writing to the /Applications folder requires administrator privileges.  
  
[DownloadPsychtoolbox](DownloadPsychtoolbox) creates the Psychtoolbox folder with permissions set  
to allow writing by everyone. Our hope is that this will allow updating  
(by [UpdatePsychtoolbox)](UpdatePsychtoolbox)) without need for administrator privileges.  
  
Some labs that may want to be able to install without access to an  
administrator. For them we offer the fall back of installing Psychtoolbox  
in /Users/Shared/, instead of /Applications/, because, by default,  
/Users/Shared/ is writeable by all users.  
  
### SAVEPATH  
  
Normally all users of MATLAB / OCTAVE use the same path. This path is  
normally saved in MATLABROOT/toolbox/local/pathdef.m, where "MATLABROOT"  
stands for the result returned by running that function in MATLAB, e.g.  
'/Applications/MATLAB.app/Contents/Matlab14.1'. Since pathdef.m is inside  
the MATLAB package, which is normally in the Applications folder,  
ordinary users (not administrators) cannot write to pathdef.m. They'll  
get an error message whenever they try to save the path, e.g. by typing  
"savepath". Most users will find this an unacceptable limitation. The  
solution is very simple, ask an administrator to use File Get Info to set  
the pathdef.m file permissions to allow write by everyone. This needs to  
be done only once, after installing MATLAB.  
  
web http://www.mathworks.com/access/helpdesk/help/techdoc/matlab\_env/ws\_pat18.html  
  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/DownloadPsychtoolbox.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/DownloadPsychtoolbox.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/DownloadPsychtoolbox.m</code>
</div>

