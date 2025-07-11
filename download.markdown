---
layout: page
title: Download, Installation, and Update
categories: getting-started
---

Make sure to familiarize yourself with the [System requirements][requirements],
so your system is set up with suitable hardware and additional required
software before installing Psychtoolbox itself.

In order to install and use the Psychtoolbox, *you must already have
Matlab or Octave installed on your computer, unless you install for
Octave on Linux via the NeuroDebian repositories.* If you already have
Matlab or Octave installed, start it up and read on. On Windows you
must have installed GStreamer 1.22.5 MSVC edition or later versions.

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
installed on your computer, or you are installing for Octave on Linux via the
NeuroDebian repositories. See the [System Requirements][requirements].

#### Linux {#Linux}

##### Packages

**Recommended:** Psychtoolbox for Linux has been packaged by the NeuroDebian team and is
available in the following repositories:

Usually reasonably up to date, tracks most recent official PTB beta releases -
recommended for most "bread and butter" use cases:

- [NeuroDebian Psychtoolbox for GNU/Octave][nd-octave]
- [NeuroDebian Psychtoolbox for Matlab][nd-matlab]

[NeuroDebian][neurodebian] provides installation instructions on its website when you
click on the links for Octave or Matlab above.

If you installed Matlab *before* installing Psychtoolbox for Matlab from NeuroDebian,
the installation will ask you for the location of your Matlab installation, and if
you want it to rename some Matlab libraries to fix compatibility issues caused by
Matlab. **Answer YES to these questions, this is crucial!** Otherwise hardware
accelerated graphics will likely not work with Matlab later on.

If you installed Matlab *after* installing Psychtoolbox, *or after you have upgraded
Matlab to a more recent version* **you must rerun this Matlab compatibility fixing
script via:** ``sudo dpkg-reconfigure matlab-support``.

As opposed to Octave, the Psychtoolbox for Matlab won't get permanently added to your
Matlab path by default. You can execute the following command from a terminal to run
a Matlab session with the standard system-wide Psychtoolbox installation added to the
path for the duration of that session (this path is not customizable easily):

    ptb3-matlab

You could then execute Matlabs `savepath` command to add it permanently if you wanted,
or after customizing it for your special needs, or in the typical case simply call
`ptb3-matlab` whenever you need to run a standard Psychtoolbox work session.

At the end of a successfull NeuroDebian installation, after first launch of your Octave
or Matlab with the new Psychtoolbox, run the script `PsychLinuxConfiguration` from within
Matlab or Octave, and follow the interactive instructions and questions to optimize your
Linux system for data collection.

**Only for basic testing and very simple use cases:**
Debian and Ubuntu and potentially other Debian/Ubuntu based Linux distributions also
provide Psychtoolbox directly from their repositories, but these Psychtoolbox packages
are usually **very outdated, often years behind** versions, and they support GNU Octave
only, no Matlab, and not certain functions like Eyelink or Datapixx:

-   [Debian archive][debianrepo] (package `octave-psychtoolbox-3`)
-   [Ubuntu archive][ubunturepo] (package [`octave-psychtoolbox-3`](apt:octave-psychtoolbox-3))


_The packages in the main Debian and Ubuntu archives only ship with GNU Octave
support, hence the package to install is_ **`octave-psychtoolbox-3`**.

*In general using the NeuroDebian repo above is more convenient and provides more
up to date packages for Octave and Matlab*, but the distribution packages will do
for a quick test drive, e.g., from within a Live Linux system, booted from a USB
flash drive, for quick compatibility testing.

If you choose installation from the distribution directly, bypassing NeuroDebian,
after package installation, run the script `PsychLinuxConfiguration` from within
Octave once, and follow the interactive instructions and questions to optimize your
Linux system for data collection. You may be able to do without this step for a
quick basic test drive or maybe for pure student training without need for high
timing precision or precise low-level control of your hardware and special equipment.

The advantage of all the above methods is that third-party dependencies
are automatically installed by the package manager.

##### Manual download

See section [Alternate Download below for how to download zip files instead.](#alternate-download)

##### After basic Linux installation - further tweaks:

Another recommendation is to install a low-latency Linux kernel for optimized
timing, e.g., on Ubuntu flavors and maybe also Debian flavors:

    sudo apt install linux-lowlatency

Optimization of the display server settings for good visual timing is
achieved by following the Linux instructions in ">> help SyncTrouble"
and by running the helper scripts `XOrgConfCreator` and `XOrgConfSelector`
to automatically create and install optimized xorg.conf configuration files
for the X-Server. This is especially useful for hybrid graphics laptops and
multi-display setups.

If you have older AMD graphics cards with DCE display engines, ie. AMD Polaris,
AMD Vega, or earlier, and want to use Psychtoolbox low-level features for extra
reliability and peace of mind for visual stimulation, or if you are using a
NVidia graphics card with proprietary driver and want precise visual onset
timestamping, Psychtoolbox needs low-level gpu access. This is generally only
possible on modern Linux distributions with EFI secure boot disabled in your
firmware settings, as EFI secure boot will trigger an additional security
mechanism in Linux, called "kernel lockdown", which will prevent these low
level features from working. Disabling secure boot may be also needed if
you want to access some types of serial or parallel ports.

[Additional tips][using-on-linux] for installing and using Psychtoolbox on
Linux.

#### Windows {#Windows}

Execute steps 1 and 2 below and then [skip to Alternate Download below for how to download zip files instead.](#alternate-download)
We strongly recommend use of Psychtoolbox 3.0.21 or later, not version 3.0.20.

Filesystem locations given here are examples. You could choose other disc drives or
folders of your liking instead:

1.  You **must** install the 64-Bit GStreamer-1.22.5 **MSVC** (or later versions) runtime 
    from [gstreamer.freedesktop.org][gstreamer-win] even if you do not need multi-media
    support! Do **not** install the MINGW variant, it will not work, but likely crash!
    Make absolutely sure that you install all offered packages. [Read `help GStreamer`
    carefully for this purpose, *before downloading and installing GStreamer*.][docs-gstreamer]

    If you intend to use Octave, you will need to delete the following DLL files from the
    C:\Program Files\GNU Octave\Octave-7.3.0\mingw64\bin\ folder:
    opengl32.dll -- Otherwise hardware accelerated visual stimulation will not work.

2.  [You may also need to install the Microsoft Runtime Libraries for MSVC 2015-2019 if
    you use Matlab instead of Octave, and those have not been installed already by other
    software on your system. For a few use cases you may even need those if you use Octave.
    You can find installers for these at Microsoft’s site beforehand. Otherwise, if our
    installer aborted half-ways, follow the instructions it prints to the console. Or simply
    click this link to get a copy bundled with Psychtoolbox][c++ runtime]

3.  Psychtoolbox 3.0.20 and later will require a paid license key to function, except for
    a time-limited 14 days free trial period. The version will require consent to enabling
    of the software network license manager, and then is freely usable until 14 days after 
    first use on a machine, or until 14th of April 2025 in case of machines first used
    before start of April 2025, whatever end date comes later.

#### Mac {#Mac}

Execute step 1 and then [skip to Alternate Download below for how to download zip files instead.](#alternate-download)
We strongly recommend use of Psychtoolbox 3.0.21 or later, not version 3.0.20.

1.  If you intend to use multi-media functions, or if you want fast, high-quality,
    cross-platform, consistent text rendering with Matlab, you must install the 64-Bit
    GStreamer-1.18.5 or later runtime from [gstreamer.freedesktop.org][gstreamer-osx] on
    Intel based Macintosh computers, or GStreamer 1.22.0 or later on ARM based Macs.
    Make absolutely sure that you install all offered packages. [Read `help GStreamer`
    carefully for this purpose, *before downloading and installing GStreamer*.][docs-gstreamer]

2.  Psychtoolbox 3.0.20 and later will require a paid license key to function, except for
    a time-limited 14 days free trial period. The version will require consent to enabling
    of the software network license manager, and then is freely usable until 14 days after
    first use on a machine, or until 14th of April 2025 in case of machines first used
    before start of April 2025, whatever end date comes later.

Download of Psychtoolbox as a zip file {#alternate-download}
------------------------------------------------------------

If you don't want to download manually via GitHub (expert approach), or via
convenient Linux package respositories, the typical approach is download of a
zip file. **You generally do not want to install via the Matlab Add-On package
manager! The Add-On package manager has serious limitations and can cause
problems!**

**Usually you'll want to download the zip file whose name is the version number,
and with a little box symbol to its left, for only the Psychtoolbox standard
folder** (ie. without source code), e.g., for Psychtoolbox version 3.0.22.1, it
would be named like `3.0.22.1.zip`. See the following screenshot for the location
of the correct download link for the correct zip file for most users:

![Screenshot of proper zip file download link](/images/ZipFileDownloadLink.png)

[For the latest release zip file, click this link.](https://github.com/Psychtoolbox-3/Psychtoolbox-3/releases/latest/download/3.0.22.1.zip)


The "Assets" section of each Psychtoolbox GitHub release contains these download links,
as shown in the picture.

[Click this link to go to the downloads page for all official releases.][PTBReleases]

Then read on how to set up your manually downloaded copy of Psychtoolbox in the
following section. This also applies to a manually git cloned Psychtoolbox.

<small>We also provide "Source Code" zip or tar.gz files, which contain a given
Psychtoolbox release, including the full source code. These are large, due
to inclusion of the source code. This is usually not what you want, it is
only useful for a developers that want to dig deep!</small>


Installation without Download or after zip file or GitHub git download {#without-download}
----------------------------------------------------------------------

**Note: You still need to execute operating-system dependent or Matlab/
Octave dependent setup steps like installing GStreamer, or other packages
and configuration steps mentioned above. Essentially, do everything operating
system dependent mentioned in the previous sections before proceeding here.**

Tip: If you already have downloaded a copy of the Psychtoolbox folder onto a
local computer and want to replicate that installation onto other computers,
then you don’t need to download the toolbox again. Instead, simply copy the
Psychtoolbox folder to the other target machines.

Next, startup Matlab or Octave on the machine, change Matlab’s or Octave’s
working directory to the Psychtoolbox folder (`cd` command) and then type
`SetupPsychtoolbox`.

(see [SetupPsychtoolbox][docs-setup] or type `help SetupPsychtoolbox`). The
`SetupPsychtoolbox` script will setup your local Psychtoolbox folder for use
with Matlab or Octave. It will also allow for first time license manager setup
on a users computer account on macOS and Windows.

Note that as of Psychtoolbox 3.0.20 or later, you will need to purchase a
license key for Psychtoolbox on Apple macOS and Microsoft Windows, once
your 14 days free trial ends for a given machine.

Staying Up-to-Date {#upgrading}
-------------------------------

If you installed Psychtoolbox-3 for Linux from NeuroDebian, Debian or
Ubuntu, your operating system will automatically notify you of new
Psychtoolbox releases. After your approval, it will automatically
upgrade the toolbox to the new version.

A manually Git cloned Psychtoolbox can be upgraded via `git pull`, and then 
rerunning `SetupPsychtoolbox` as mentioned in the previous section.

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


More Information {#more}
------------------------

### Download problems {#download-problems}

[If you need timely expert support in resolving download or installation
issues, we also offer paid support under this link.][paid-support]
*If everything else fails, contact the Psychtoolbox [forum][forum] with a
description of what you tried.*

### Access to Archived Versions of PTB-3 {#archived}

You can also choose to install specific old versions of Psychtoolbox-3 by
cloning or downloading the correspondingly named Git branches on our
[GitHub repository](https://github.com/Psychtoolbox-3/Psychtoolbox-3)

E.g., to download Psychtoolbox-3.0.12 you would checkout or download the
branch named 'Psychtoolbox-3.0.12'. A list of older versions can be found
at the bottom of the page found [here][versions]. This only works for
versions since 3.0.10.

  [requirements]: /requirements
  [forum]: /forum
  [paid-support]: https://www.psychtoolbox.net/license-key
  [versions]: /versions
  [using-on-linux]: /linux
  [installer]: https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/master/Psychtoolbox/DownloadPsychtoolbox.m.zip
  [gstreamer-win]: https://gstreamer.freedesktop.org/data/pkg/windows/1.22.12/msvc/gstreamer-1.0-msvc-x86_64-1.22.12.msi
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
