---
layout: page
title: Download, Installation, and Update
categories: getting-started
---

Make sure to familiarize yourself with the [System requirements][requirements],
so your system is set up with suitable hardware and additional required
software before installing Psychtoolbox itself.

In order to install and use the Psychtoolbox, *you must already have
Matlab or Octave installed on your computer*, unless you install for
Octave on Linux via the NeuroDebian repositories. If you already have
Matlab or Octave installed, start it up and read on. On Windows you
must have installed GStreamer 1.18.0 MSVC edition or later versions.

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

1.  If you have an older version of Psychtoolbox than 3.0.8, remove it
    by following the instructions in the next section, [Removing Old
    Versions](#removing)
2.  If you don’t have Psychtoolbox-3 at all, read the [Installation
    Instructions](#installation) below.
3.  If you do have it, skip down to the [Staying Up-to-Date](#upgrading)
    section below.

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
button, followed by the "Save" button to save the changes.

Installation Instructions {#installation}
-----------------------------------------

These are simple instructions to get you up and running with the Psychophysics
Toolbox on a computer. It is assumed that you already have Matlab or Octave
installed on your computer, or are installing for Octave on Linux via the
NeuroDebian repositories. See the [System Requirements][requirements].

#### Linux {#Linux}

##### Packages

Psychtoolbox for Linux has been packaged by the NeuroDebian team and is
available in the following repositories:

Up to date, tracks most recent official PTB beta releases - recommended:

-   [NeuroDebian][neurodebian] ([Octave][nd-octave] or [Matlab][nd-matlab])

NeuroDebian provides installation instructions on its website when you click
on the links for Octave or Matlab above. At the end of NeuroDebian installation,
run the script `PsychLinuxConfiguration` and follow the interactive instructions
and questions.

Usually somewhat outdated versions, GNU Octave only, no Matlab:

-   [Debian archive][debianrepo] (package `octave-psychtoolbox-3`)
-   [Ubuntu archive][ubunturepo] (package [`octave-psychtoolbox-3`](apt:octave-psychtoolbox-3))


_The packages in the main Debian and Ubuntu archives only ship with GNU
Octave support, hence the package to install is_ **`octave-psychtoolbox-3`**.
In general using the NeuroDebian repo above is more convenient and provides up to
date packages for Octave and Matlab, but the distribution packages will do for a
quick test drive, e.g., from within a Live system for quick compatibility testing.

The advantage of the above repositories is that third-party dependencies
are automatically installed by the package manager.

##### Subversion-based installation
 
Alternatively, you can perform the regular installation via our
[`DownloadPsychtoolbox.m`][installer] script. The following will install
Psychtoolbox by checking out the Subversion repo to the specified local
directory.

  1.  Skip this step and go directly to step 2 if you use Matlab R2014b or later.
      Get the `subversion` package from your Linux distribution’s archive
      (i.e. `apt-get install subversion`, or `yum install subversion`, et al.).

  2.  Start Octave or Matlab, `cd` into the folder that you saved the
      [`DownloadPsychtoolbox.m`][installer] script in, and run

          >> DownloadPsychtoolbox('/home/foo/toolbox')

However, Octave mex files from this download will only work out of the box with
Octave 3.8, 4.0 or 4.2 on a fairly recent distribution like Ubuntu 16.04-LTS or better
Ubuntu 18.04-LTS, as well as with Octave 5.2 on Ubuntu 20.04-LTS. All required dependencies
like GStreamer-1.8+, libdc1394, etc. need to be manually installed in this case. It may
work on Debian/Ubuntu based system to execute "sudo apt build-dep psychtoolbox-3" though
to get your distribution to auto install required dependencies. Generally prefer the
NeuroDebian installation instead if you are on Debian or Ubuntu flavors.

[Additional tips][using-on-linux] for installing and using Psychtoolbox on
Linux.

#### Windows {#Windows}

Filesystem locations given here are examples. You could choose other disc drives or
folders of your liking instead:

1.  Skip this step and go directly to step 2 if you use Matlab R2014b or later.

    Download and install the Subversion installer

    -   **Windows:** [Subversion 1.7.x command-line client][svnwin]

2.  Download the **[Psychtoolbox installer][installer] to your desktop**. 

3.  You **must** install the 64-Bit GStreamer-1.18.0 **MSVC** runtime or later versions
    from [gstreamer.freedesktop.org][gstreamer-win] even if you do not need multi-media
    support! Do **not** install the MINGW variant, it will not work, but likely crash!
    Make absolutely sure that you install all offered packages. [Read `help GStreamer`
    carefully for this purpose, *before downloading and installing GStreamer*.][docs-gstreamer]

    If you intend to use Octave, you will need to delete the following DLL files from the
    C:\Octave\Octave-5.2.0\mingw64\bin\ folder:
    opengl32.dll -- Otherwise hardware accelerated visual stimulation will not work.

4.  [You may also need to install the Microsoft Runtime Libraries for MSVC 2015-2019 if
    you use Matlab instead of Octave.
    You can find installers for these at Microsoft’s site beforehand. Otherwise
    when our installer aborted half-ways, follow the instructions it prints to
    the console. Or simply click this link to get a copy bundled with Psychtoolbox][c++ runtime]

5.  Open Matlab as administrative user (for Windows 7 and later, right-click the Matlab
    shortcut and "Run As Administrator") and type the following in the command window,
    assuming you want Psychtoolbox to be installed inside the C:\toolbox folder:

        >> cd('into the folder where you downloaded DownloadPsychtoolbox.m to').
        >> DownloadPsychtoolbox('C:\toolbox')

    The second command will take a bit of time (a few minutes in some cases) and
    may generate a lot of output. Please be patient (and make sure your
    computer is not going to go onto standby while installing). You may
    get the command line reappear before the installation is finished -
    so don’t assume the command line reappearing means that installation
    has hung. The installer will tell you when it is finished.

    If the download fails, read below on [Download Problems](#download-problems).

If you want to know more about the downloader, see [DownloadPsychtoolbox][docs-download]
(or `help DownloadPsychtoolbox` in the Matlab command window.)

#### Mac {#Mac}

1.  Skip this step for current Psychtoolbox 3.0.17 or later with Matlab R2014b
    or later. [Also skip it with GNU/Octave if you already have HomeBrew installed][homebrew]
    Go to step 2 instead.

    Otherwise get and install Subversion from somewhere, e.g., HomeBrew.

2.  Download the **[Psychtoolbox installer][installer] to your desktop**. 

3.  Open Octave or Matlab and type the following in the command window:

        >> cd ~/Desktop
        >> DownloadPsychtoolbox

The second command will take a long time and may generate a lot of output.
Please be patient.

If the download fails, read below on [Download Problems](#download-problems). If you
want to know more, see [DownloadPsychtoolbox][docs-download] (or
`help DownloadPsychtoolbox` in the command window.)

4.  If you intend to use multi-media functions, or you want fast, high-quality,
    cross-platform, consistent text rendering with Matlab, you must install the 64-Bit
    GStreamer-1.18 or later runtime from [gstreamer.freedesktop.org][gstreamer-osx].
    Make absolutely sure that you install all offered packages. [Read `help GStreamer`
    carefully for this purpose, *before downloading and installing GStreamer*.][docs-gstreamer]

After Download and installation
-------------------------------

You should now have a complete Psychtoolbox installation. To start
learning about the Psychtoolbox, use the `help` command. For example,

`>> help Psychtoolbox` will list the categories of functions in the
toolbox, and

`>> help PsychDemos` will list all the demos available.

A PDF file with the presentation slides of an introduction into Psychtoolbox-3:
[Talk slides of Psychtoolbox presentation, given at ECVP 2013 Bremen][bremen]

More detailled information can be found in the Psychtoolbox subfolder
named `PsychDocumentation` of your Psychtoolbox installation.

Alternate download as a zip file {#alternate-download}
------------------------------------------------------

If regular installation via Subversion or package respositories does not
work for some reason, you can also manually download a zip file which
contains a given Psychtoolbox release, including the source code. These
downloads are larger due to inclusion of the source code.

[Click this link to go to the downloads page for all official releases.][PTBReleases]

Then read on in the following section on how to set up your manually
downloaded copy of Psychtoolbox.

Installation without Download {#without-download}
-------------------------------------------------

If you already have downloaded a copy of the Psychtoolbox folder onto a
local computer and want to replicate that installation onto other computers,
then you don’t need to download the toolbox again. Instead, simply copy the
Psychtoolbox folder to the other target machines. Next, startup Matlab or
Octave on that machines, change Matlab’s or Octave’s working directory to the
copied Psychtoolbox folder (`cd` command) and then type
`SetupPsychtoolbox` (see [SetupPsychtoolbox][docs-setup] or type
`help SetupPsychtoolbox`). The `SetupPsychtoolbox` script will setup
your copied local Psychtoolbox folder for use with Matlab or Octave,
just as our installers would do. This procedure can save some download
time.

If you cannot install the Subversion client `svn` for some reason and
can not use Matlab R2014b or later with its integrated svn client, then
you can also download the ZIP file comprising the whole project. Running
`SetupPsychtoolbox` from the `Psychtoolbox` sub-folder from the extracted
ZIP will add PTB to your Matlab or Octave path.

Staying Up-to-Date {#upgrading}
-------------------------------

If you installed Psychtoolbox-3 for Linux from NeuroDebian, Debian or
Ubuntu, your operating system will automatically notify you of new
Psychtoolbox releases. After your approval, it will automatically
upgrade the toolbox to the new version.

After a manual installation on OSX, Windows or Linux via `DownloadPsychtoolbox`,
Psychtoolbox-3 can be updated to the latest version by typing the following command:

    >> UpdatePsychtoolbox

For more information, see [UpdatePsychtoolbox][docs-update] or type
`help UpdatePsychtoolbox` inside Matlab.

More Information {#more}
------------------------

### Download problems {#download-problems}

[You can also download Psychtoolbox as a zip file.](#alternate-download)

If the installer complains about not being able to find the Subversion
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

    svn: Can't connect to host 'github.com': A socket operation was attempted to an unreachable network.
    svn: PROPFIND of '/svnroot/repos/osxptb/unsupported/Psychtoolbox': could not connect to server (https://github.com)
    svn: Connection timed out ...
    svn: Connection refused ...

This can mean two things:

<dl>
  <dt> Subversion server is down </dt>
  <dd>
    … our Source code repository server on GitHub.com or part of your
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

[If you need timely expert support in resolving download or installation
issues, we also offer paid priority support under this link.][priority-support]
*If everything else fails, contact the Psychtoolbox [forum][forum] with a
description of what you tried.*

### Subversion {#subversion}

Installing Psychtoolbox-3 requires Subversion because the toolbox is now
kept in a database, which is stored on a publicly accessible Subversion
server. The database both stores the latest version of the code and
tracks all of the changes that have been made to it. This simplifies
maintenance and development of the toolbox. The Psychtoolbox functions
`DownloadPsychtoolbox` and `UpdatePsychtoolbox` automate interactions
with the database, so you never have to use Subversion directly. To
learn more about Subversion, you can visit the website:
<http://subversion.apache.org>.

Matlab R2014b and later include a builtin Subversion client, whereas if you use
earlier versions of Matlab or you use Octave, you will need to install a 3rd
party Subversion client yourself, as described above in step 1 of the download
instructions.

### Downgrading {#downgrading}

If you find something broken after an update, then you might want to
revert to an earlier version. The `UpdatePsychtoolbox` script allows you
to downgrade to an earlier version of Psychtoolbox. To downgrade to the
previous version, type this into the command window:

    >> UpdatePsychtoolbox(PsychtoolboxRoot, 'PREV')

You can repeat this step to incrementally downgrade to earlier versions.

If you know the revision number of a specific Psychtoolbox release,
because you noted down the output of `PsychtoolboxVersion` to document
the software version you used to conduct some of your studies, then you
can get that version as well, by passing that revision number instead of
'PREV'. E.g., to get software revision 1236, type

    >> UpdatePsychtoolbox(PsychtoolboxRoot, '1236')

### Access to Archived Versions of PTB-3 {#archived}

You can also choose to install specific old versions of Psychtoolbox-3 by
providing their name instead of ‘current’ or ‘unsupported’. E.g., to
download Psychtoolbox-3.0.12 you would run
`DownloadPsychtoolbox([], 'Psychtoolbox-3.0.12')`. A list
of older versions can be found at the bottom of the page found
[here][versions]. This only works for versions since 3.0.10.

  [requirements]: /requirements
  [forum]: /forum
  [priority-support]: /prioritysupport
  [versions]: /versions
  [using-on-linux]: /linux

  [svnwin]: http://www.sliksvn.com/en/download
  [homebrew]: https://brew.sh
  [installer]: https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/master/Psychtoolbox/DownloadPsychtoolbox.m.zip
  [legacy-installer]: https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/master/Psychtoolbox/DownloadLegacyPsychtoolbox.m
  [gstreamer-win]: https://gstreamer.freedesktop.org/data/pkg/windows/1.18.1/msvc/gstreamer-1.0-msvc-x86_64-1.18.1.msi
  [gstreamer-osx]: http://gstreamer.freedesktop.org/data/pkg/osx/
  [PTBReleases]: https://github.com/Psychtoolbox-3/Psychtoolbox-3/releases

  [neurodebian]: http://neuro.debian.net/
  [nd-octave]: http://neuro.debian.net/pkgs/octave-psychtoolbox-3.html
  [nd-matlab]: http://neuro.debian.net/pkgs/matlab-psychtoolbox-3.html
  [debianrepo]: http://packages.debian.org/search?keywords=Psychtoolbox
  [ubunturepo]: http://packages.ubuntu.com/search?keywords=Psychtoolbox

  [arezzo]: https://github.com/Psychtoolbox-3/Psychtoolbox-3/raw/master/Psychtoolbox/PsychDocumentation/Psychtoolbox3-Slides.pdf
  [bremen]: https://github.com/Psychtoolbox-3/Psychtoolbox-3/raw/master/Psychtoolbox/PsychDocumentation/PTBTutorial-ECVP2013.pdf
  [docs-gstreamer]: http://psychtoolbox.org/docs/GStreamer
  [docs-download]: http://psychtoolbox.org/docs/DownloadPsychtoolbox
  [docs-setup]: http://psychtoolbox.org/docs/SetupPsychtoolbox
  [docs-update]: http://psychtoolbox.org/docs/UpdatePsychtoolbox
  [c++ runtime]: https://github.com/Psychtoolbox-3/Psychtoolbox-3/raw/master/Psychtoolbox/PsychContributed/vcredist_x64_2015-2019.exe
