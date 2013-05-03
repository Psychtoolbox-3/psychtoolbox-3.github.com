---
layout: page
title: Download, Installation, and Update
category: getting-started
---

In order to install and use the Psychtoolbox, *you must already have
Matlab or Octave installed on your computer*. If you already have
Matlab or Octave installed, start it up and read on.

##### Contents {#contents}

* Will be replaced with the ToC
{:toc #toc}
{::options auto_ids="false" toc_levels="1..4"/}

Preliminaries
-------------

First, you should make sure you don’t already have Psychtoolbox-3. Type
the following in the Matlab command window:

    >> PsychtoolboxVersion

The first number in the output is the version number. If it is **3.0.8
or greater**, then you have Psychtoolbox-3. Pick one:

1.  If you have an older version of Psychtoolbox, remove it by following
    the instructions in the next section, [Removing Old
    Versions](#removing)
2.  If you don’t have Psychtoolbox-3 at all, read the [Installation
    Instructions](#installation) below.
3.  If you do have it, skip down to the [Staying
    Up-to-Date](#upgrading) section below.

Removing Old Versions of Psychtoolbox {#removing}
-------------------------------------------------

If you have an old version of Psychtoolbox installed, the installer will
prompt you if it should automatically delete those version from your
file system and do so if you agree. If you want to delete the folder
manually, apply the following procedure.

To find the Psychtoolbox installation directory, type the following in
the Matlab command window:

    >> PsychtoolboxRoot

Find that folder and drag it to the Trash or Recycling Bin. Then type
`pathtool` in the Matlab command window. This will bring up a dialog box
with a list of folders that Matlab searches to find commands. Select all
the folders that have “Psychtoolbox” in the name and click the “Remove”
button.

Installation Instructions {#installation}
-----------------------------------------

These are simple instructions to get you up and running with the
Psychophysics Toolbox on a computer. It is assumed that you already have
Matlab or Octave installed on your computer. See the [System
Requirements][requirements].

#### Mac {#Mac}

1.  **Mac OS X < 10.5 Leopard only:** Download Subversion installer

    -  [Subversion][svnmac] (Look for “Binaries for Mac OS X”).

    Skip this step on OS X 10.5 Leopard or later iff you have Apple's XCode
    development tools installed, as Subversion (`svn`) is then already
    installed on your system by default.

2.  Download the **[Psychtoolbox installer][installer] to your desktop**. 

3.  Open Matlab and type the following in the command window:

        >> cd ~/Desktop
        >> DownloadPsychtoolbox

The second command will take a long time and generate a lot of output.
Please be patient.

If the download fails, read below on [Download Problems](#download-problems). If you
want to know more, see [DownloadPsychtoolbox][docs-download] (or
`help DownloadPsychtoolbox` in the Matlab command window.)

#### Linux {#Linux}

##### Packages

Psychtoolbox for Linux has been packaged and is available in the
following repositories:

-   [NeuroDebian][neurodebian] (packages [`octave-psychtoolbox-3`][nd-octave] or [`matlab-psychtoolbox-3-nonfree`][nd-matlab])
-   [Debian archive][debianrepo] (package `octave-psychtoolbox-3`)
-   [Ubuntu archive][ubunturepo] (package [`octave-psychtoolbox-3`](apt:octave-psychtoolbox-3))

NeuroDebian provides installation instructions on its website. 

_The packages in the main Debian and Ubuntu archives still only ship with GNU
Octave support, hence the package to install is_ **`octave-psychtoolbox-3`**.
Use the script `DownloadAdditionsForNeuroDebian` after the package installation
to post-install the Matlab versions of the binary MEX routines as well.

The advantage of the above repositories is that third-party dependencies
are automatically installed by the package manager.

##### Subversion-based installation
 
Alternatively, you can perform the regular installation via our
[`DownloadPsychtoolbox.m`][installer] script. The following will install
Psychtoolbox by checking out the Subversion repo to the specified local
directory.

  1.  Get the `subversion` package from your Linux distribution’s archive
      (i.e. `apt-get install subversion`, or `yum install subversion`, et al.).
  2.  Start Octave or Matlab, `cd` into the folder that you saved the
      [`DownloadPsychtoolbox.m`][installer] script in, and run

          >> DownloadPsychtoolbox('/home/foo/toolbox')

Additional tips for installing and using Psychtoolbox on Linux can
be found under [UsingPsychtoolboxOnLinux][using-on-linux].

#### Windows {#Windows}

1.  Download Subversion installer

    -   **Windows:** [Subversion 1.7.x command-line client][svnwin]

2.  Download the **[Psychtoolbox installer][installer] to your desktop**. 

3.  Open the **My Computer** icon (it is either on the desktop or in the Start
    Menu).
4.  Double-click on the **C: drive** icon.
5.  Create a new folder called `toolbox`. This assumes you want to install into
    the `toolbox` folder.
6.  Move the Psychtoolbox installer (`DownloadPsychtoolbox`) from the Desktop
    to the new `toolbox` folder.
7.  If you intend to use the 64-Bit Psychtoolbox for 64-Bit Matlab, you must
    install the 64-Bit GStreamer SDK from [gstreamer.com][gstreamer-sdk],
    otherwise Psychtoolbox will not work and the installation will abort.
8.  You also need to install the Microsoft Runtime Libraries for MSVC 2010. You
    can find installers for these at Microsoft’s site beforehand. Otherwise
    when our installer aborted half-ways, follow the instructions it prints to
    the console.
9.  Open Matlab as administrative user (for Windows 7, right-click Matlab
    shortcut and Run As Administrator) and type the following in the command
    window:

        >> cd C:\toolbox
        >> DownloadPsychtoolbox('C:\toolbox')

    The second command will take a long time (~10 min in some cases)
    and generate a lot of output. Please be patient (and make sure your
    computer is not going to go onto standby while installing). You may
    get the command line reappear before the installation is finished -
    so don’t assume the command line reappearing means that installation
    has hung. The installer will tell you when it is finished.

    If the download fails, read below on [Download
    Problems](#download-problems).

If you want to know more about the downloader, see [DownloadPsychtoolbox][docs-download]
(or `help DownloadPsychtoolbox` in the Matlab command window.)

You should now have a complete Psychtoolbox installation. Occasionally
type the command `UpdatePsychtoolbox` in the Matlab command window: this
will ensure that you have the latest version of Psychtoolbox. To start
learning about the Psychtoolbox, use the `help` command. For example,

`>> help Psychtoolbox` will list the categories of functions in the
toolbox, and

`>> help PsychDemos` will list all the demos available.

A PDF file with the presentation slides of an introduction into
Psychtoolbox-3 and the differences to Psychtoolbox-2: [Talk slides of
Psychtoolbox presentation, given at ECVP 2007 Arezzo][arezzo]

Installation without Download
-----------------------------

If you already have downloaded a copy of the Psychtoolbox folder onto a
local computer and want to replicate that installation onto other
computers you don’t need to download the toolbox again. Instead, simply
copy the Psychtoolbox folder to the other target machines. Next, startup
Matlab or Octave on that machines, change Matlab’s or Octave’s working
directory to the copied Psychtoolbox folder (`cd` command) and then type
`SetupPsychtoolbox` (see [SetupPsychtoolbox][docs-setup] or type
`help SetupPsychtoolbox`). The `SetupPsychtoolbox` script will setup
your copied local Psychtoolbox folder for use with Matlab or Octave,
just as our installers would do. This procedure can save some download
time.

Staying Up-to-Date {#upgrading}
-------------------------------

Psychtoolbox-3 can be updated to the latest version by typing the
following Matlab command:

    >> UpdatePsychtoolbox

For more information, see [UpdatePsychtoolbox][docs-update] or type
`help UpdatePsychtoolbox` inside Matlab.

More Information {#more}
------------------------

### Download problems {#download-problems}

If the installer complains about being not able to find the Subversion
client “svn” because it is installed in an unusual location, you can try
to locate the client yourself on your filesystem by use of your
operating systems search functions and then add the path to the folder
which contains the “svn” executable to your Matlab or Octave path. E.g.,
if the svn client is found under `/opt/local/bin/svn`, do a
`addpath('/opt/local/bin')` in Matlab or Octave, save the path via
`savepath` and then retry.

Sometimes the downloader fails with a message like
“`Command CHECKOUT failed with error code xxx`” with `xxx` being some
number, followed by a description of the error condition. You may see
any of these, or similar messages referring to the network or
connections …

    svn: Can't connect to host 'svn.berlios.de': A socket operation was attempted to an unreachable network.
    svn: PROPFIND of '/svnroot/repos/osxptb/unsupported/Psychtoolbox': could not connect to server (http://svn.berlios.de)
    svn: Connection timed out ...
    svn: Connection refused ...

This can mean two things:

<dl>
  <dt> Subversion server is down </dt>
  <dd>
    … our Source code repository server on BerliOS.de or part of your
    internet connection is experiencing temporary problems. Don’t panic,
    just wait a couple of minutes (sometimes a couple of hours) and retry.
  </dd>
  <dt> Subversion server cannot be reached due to a network `proxy` or `firewall` </dt>
  <dd>
    Your institution might route all web traffic trough a local proxy
    server, which can interfere with the operation of Subversion because it
    also uses HTTP to check-out the Psychtoolbox from the repository.
    See FaqDownloadFails to learn how to teach svn to use your institution’s
    proxy.
  </dd>
</dl>


If the updater fails with a message like ...

    svn: E155036: Please see the 'svn upgrade' command 
    svn: E155036: Working copy '/opt/MATLAB/R2011b/toolbox/Psychtoolbox' is too old (format 10, created by Subversion 1.6) 

... then open a terminal window, `cd` into the Psychtoolbox folder and then run
the command `svn upgrade`. Then rerun the `UpdatePsychtoolbox` command.

Alternatively, if you haven't made any modifications to your Psychtoolbox
folder, simply rerun `DownloadPsychtoolbox` to install a fresh copy of
Psychtoolbox.

*If everything else fails, contact the Psychtoolbox [forum][forum] with a
description of what you tried.*

### Subversion {#subversion}

Installing Psychtoolbox-3 requires Subversion because the toolbox is now
kept in a Subversion database, which is stored on a publicly accessible
server. The database both stores the latest version of the code and
tracks all of the changes that have been made to it. This simplifies
maintenance and development of the toolbox. The Psychtoolbox functions
`DownloadPsychtoolbox` and `UpdatePsychtoolbox` automate interactions
with the database, so you never have to use Subversion directly. To
learn more about Subversion, you can visit the website:
<http://subversion.tigris.org/>.

### Downgrading {#downgrading}

If you find something broken after an update, then you might want to
revert to an earlier version. The `UpdatePsychtoolbox` script allows you
to downgrade to an earlier version of Psychtoolbox. To downgrade to the
previous version, type in the Matlab command window:

    >> UpdatePsychtoolbox(PsychtoolboxRoot, 'PREV')

You can repeat this step to incrementally downgrade to earlier versions.

### Access to Archived Versions of PTB-3 {#archived}

You can also choose to install specific old versions of PTB-3 by
providing their name instead of ‘current’ or ‘unsupported’. E.g., to
download Psychtoolbox-3.0.6 you would run
`DownloadLegacyPsychtoolbox([], [], [], 'Psychtoolbox-3.0.6')`. A list
of older versions can be found at the bottom of the page found
[here][versions]. Version 3.0.10 and later use the `DownloadPsychtoolbox`
function instead of `DownloadLegacyPsychtoolbox`.

  [requirements]: {{ site.url }}/requirements
  [forum]: {{ site.url }}/forum
  [versions]: {{ site.url }}/versions
  [using-on-linux]: UsingPsychtoolboxOnLinux

  [svnwin]: http://www.sliksvn.com/en/download
  [svnmac]: http://www.collab.net/downloads/subversion
  [installer]: https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/master/Psychtoolbox/DownloadPsychtoolbox.m
  [gstreamer-sdk]: http://docs.gstreamer.com/display/GstSDK/Installing+on+Windows

  [neurodebian]: http://neuro.debian.net/
  [nd-octave]: http://neuro.debian.net/pkgs/octave-psychtoolbox-3.html
  [nd-matlab]: http://neuro.debian.net/pkgs/matlab-psychtoolbox-3-nonfree.html
  [debianrepo]: http://packages.debian.org/search?keywords=Psychtoolbox
  [ubunturepo]: http://packages.ubuntu.com/search?keywords=Psychtoolbox

  [arezzo]: https://github.com/Psychtoolbox-3/Psychtoolbox-3/raw/master/Psychtoolbox/PsychDocumentation/Psychtoolbox3-Slides.pdf

  [docs-download]: http://docs.psychtoolbox.org/DownloadPsychtoolbox
  [docs-setup]: http://docs.psychtoolbox.org/SetupPsychtoolbox
  [docs-update]: http://docs.psychtoolbox.org/UpdatePsychtoolbox
  [c++ runtime]: http://www.microsoft.com/downloads/details.aspx?familyid=766A6AF7-EC73-40FF-B072-9112BAB119C2&displaylang=en#filelist
