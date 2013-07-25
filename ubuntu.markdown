---
layout: page
title: Using Psychophysics Toolbox on Ubuntu
categories: getting-started
nachricht: Hallo Ingmar
---

The most recent beta release (since V3.0.9 revision 2191) contains
support for 64bit Matlab / Octave, but one cannot mix running 64bit
Matlab on a 32bit Ubuntu and visa versa. Please see below for some
potential problems with correctly installing dependencies.

##### Choice of Kernel

See this page for more info:

<https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel>

Comment by Mario

> The `lowlatency` kernel is simple to install, as you explained, and probably
> good enough for all but the most challenging applications.  For example some
> tables benchmark results with respect to the minimal audio latency that can
> be reliably achieved: <https://wiki.ubuntu.com/RealTime> To put this into
> perspective, a typical os/x system won't be able to achieve less than about
> 6-8 msecs, at least I haven't seen anything better in my testing from
> Macbook Pro to 8 core mac-pro. The values they achieve (3-4 msecs) are close
> to the theoretical optimum. Even the default kernel is already at least as
> good as what the other operating systems have to offer.  Compiling a hard
> realtime kernel yourself is not that simple for beginners, but if you'd
> really need it you can also download and install a realtime kernel from an
> older distribution, e.g., 10.04. It would be a tradeoff between gaining hard
> realtime caps and losing some functionality which was added in later kernels.

##### Choice of Desktop environment

The recommendation is to use Classic mode; comment from Mario:

> Yep. "Ubuntu Classic (no effects)" may be even better. If you use the
> new Unity UI, that's the most shiny and untested one -- I don't quite
> hate it as much as many other people, but so far I don't see it adding
> much to the user experience. It's the usual "let's add a smartphone or
> tablet GUI to a desktop/laptop computer, because it looks fancy."
>
> Both "Ubuntu Classic" and "Unity" use a desktop compositor to create
> the shiny 3d'ish desktop. This is nice for ergonomy and eye-candy but
> it can reduce performance and really impair exact presentation timing
> and timestamping. Same problem as on Windows Vista/7 and OS/X with
> their desktop compositors.
>
> The Linux guys are working on a solution to make the timing and
> timestamping as precise with a compositor as without it -- I'm
> involved in that effort. It is a pretty difficult technical problem
> and progress is slow, but we'll get there at some point. No similar
> efforts exist at all on OS/X or Windows afaik -- At least none that
> aren't known to be extremely broken to the point of being not only
> useless but harmful.
>
> Psychtoolbox disables the desktop compositor when a fullscreen
> onscreen window is presented on OS/X, Windows and Linux to achieve
> correct stimulus onset timing and timestamping and to reduce the
> performance impact of a compositor.
>
> However, if you are running a machine for real data collection you may
> want to manually shut down the compositor completely, because a) it is
> the most reliable way to know it really doesn't interfere, and b) it
> frees up additional graphics and system resources, which are usually
> used even if the compositor is in standby mode.
>
> On Linux 10.10 and earlier this was achieved via Menubar -> System
> settings -> Appearance -> Desktop effects -> "Off" or something
> like that.
>
> On 11.04 I think you select the "Ubuntu classic (no effects)"
> environment.
>
> This will run in a old unsexy, non 3d'ish, "flicker during Windows
> movements and redraws like WindowsXP" environment, however with
> drastically reduced GPU resource consumption and no interference at
> all.
>
> I usually do complex timing tests with the compositor shut down, but
> normal testing with the compositor on and just switching to standby
> when fullscreen windows are used.
>
> One catch: On Linux, PTB doesn't actively switch the compositor to
> standby. Instead it uses the `PsychGPUControl()` command as part of the
> Psychtoolbox installer/updater to configure the compositor to switch
> itself to standby if it detects a fullscreen window on a display. If
> you do something like install PTB while Unity is running, then switch
> to the "Classic" environment, this configuration setting may not
> transfer. It doesn't hurt to add the `PsychGPUControl` command to the
> top of your script for extra paranoia. Or manually disable it via the
> GUI.
>
> I'll probably add some call to `PsychGPUControl()` to Screen's
> `OpenWindow` function in the future, so this is more fool-proof.

##### Choice of Graphics Driver

Use the proprietary driver for NVidia. For Intel and probably ATI, the
open-source drivers should be sufficient, except for 30 bit support.

Mario again:

> But nouveau in its current incarnation isn't yet suitable for research grade
> stimulus presentation timing. It's pretty good performance- and
> functionality-wise, but the display onset timing has bugs. I'm working with
> the nouveau-devs to get it properly implemented for a future nouveau release,
> but it probably won't be part of the 2011 Linux distros, at least not as a
> standard install. PTB outputs warnings if you try to run on a too old
> nouveau- ie. on any nouveau at the moment.
>
> The free software Intel (for half-way recent GPU's) and ATI (for almost all
> GPU's) drivers are in a very good shape in the recent distros. Both should have
> the most precise and robust timestamping you could find anywhere. Also the
> only timestamping that works in all display configurations with all display
> types and settings. Functionality and performance are catching up to the
> binary drivers in all areas that are relevant to us. I'd expect them to be
> perfectly usable for the majority of vision science experiments, and for
> some of them even more than the binary drivers.

##### Installing Issues

The newer PTB has several dependencies that need to be installed first before
PTB will work correctly. Please **read** the information given by the PTB
installer which gives the following instructions:

The Psychtoolbox on GNU/Linux needs the following 3rd party libraries in order
to function correctly. If you get "Invalid MEX file errors", or similar fatal
error messages, check if these are installed on your system and if they are
missing, install them via your system specific software management tools:

### For `Screen()` and OpenGL support

-   The OpenGL utility toolkit GLUT: glut, glut-3 or freeglut are
    typical provider packages in most Linux distributions.
-   GStreamer multimedia framework: At least version 0.10.24 of the core
    runtime and the gstreamer-base plugins.

For optimal performance use the latest available versions.

A simple way to get GStreamer at least on Ubuntu Linux is to install the "rhythmbox" or
"totem" multimedia-players. You may need to install additional packages to play back all
common audio- and video file formats. See `help GStreamer`.

-   libusb-1.0 USB low-level access library.
-   libdc1394 Firewire video capture library.
-   libraw1394 Firewire low-level access library.

### For `PsychKinect()` (See `help InstallKinect`)

-   libusb-1.0 USB low-level access library.
-   libfreenect: Kinect driver library.

### For `Eyelink()`

-   The `Eyelink` core libraries from the SR-Research download website.

If you receive an installation failure soon, then please read the output
of `help GStreamer` first and follow the installation instructions for
GStreamer on Linux. Psychtoolbox's `Screen()` command will not work
without GStreamer!

Also, at least one user had to physically move `libdc1394.so.22` from the
Matlab. For more information see

<http://tech.groups.yahoo.com/group/psychtoolbox/message/12408> 

##### Install Instructions on 64-bit Linux

<small>`cum grano salis`</small>

General setup for PTB and Matlab on Ubuntu 11.04 64-bit:

-   install low-latency kernel (some info found here -
    <https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel>)

    ~~~ bash
    sudo add-apt-repository ppa:abogani/ppa
    sudo apt-get update
    sudo apt-get install linux-lowlatency
    ~~~

-   Install subversion:

    ~~~ bash
    sudo apt-get install subversion
    ~~~

-   Install Matlab 64-bit (2010b was used for these instructions)

-   Install PTB using [these instructions](download)

-   Need to fix a few things in matlab for PTB to work

    ~~~ bash
    cd $MATLABROOT/sys/os/glnxa64/
    sudo mv libstdc++.so.6.0.10 old_libstdc++.so.6.0.10
    sudo mv libstdc++.so.6 old_libstdc++.so.6
    cd $MATLABROOT/bin/glnxa64/
    sudo mv libdc1394.so.22 old_libdc1394.so.22
    sudo mv libdc1394.so.22.1.0 old_libdc1394.so.22.1.0
    sudo apt-get install libdc1394-22
    ~~~

-   Finally, solve a Matlab issue specific to Ubuntu 11.04:

    ~~~ bash
    sudo ln -s /lib64/x86_64-linux-gnu/libc-2.13.so /lib64/libc.so.6
    ~~~

-   Alternatively, you could use NeuroDebian install of
    octave-psychtoolbox-3 (http://neuro.debian.net), but you may still
    need some of the above steps

Refresh rate setup
------------------

This is an example based on setting this up on my `rig2display` machine.

-   Use `gtf` to generate a modeline:

    ~~~ bash
    gtf 1024 768 100
    ~~~

    This is the output of that command on an example machine:

    ~~~ bash
      # 1024x768 @ 100.00 Hz (GTF) hsync: 81.40 kHz; pclk: 113.31 MHz
      Modeline "1024x768_100.00"  113.31  1024 1096 1208 1392  768 769 772 814  -HSync +Vsync
    ~~~

    `cvt` is another program that works basically the same way

-   Be sure the modeline is valid for the monitor. Look up the
    horizontal and vertical sync in the specs

-   Use `xrandr -q` to see the modes available and what your graphics
    system is called (mine is CRT1)

-   Copy that modeline to make 3 commands:

    ~~~ bash
    xrandr --newmode "1024x768_100.00"  113.31  1024 1096 1208 1392  768 769 772 814  -HSync +Vsync
    xrandr --addmode CRT1 "1024x768_100.00"
    xrandr --output CRT1 --mode "1024x768_100.00"
    ~~~

-   Paste these into the file `/etc/gmd/Init/Defaults` just above the
    `/sbin/initctl` command. So mine looks like:

    ~~~ bash
    xrandr --newmode "1024x768_100.00"  113.31  1024 1096 1208 1392  768 769 772 814  -HSync +Vsync
    xrandr --addmode CRT1 "1024x768_100.00"
    xrandr --output CRT1 --mode "1024x768_100.00"
    /sbin/initctl -q emit login-session-start DISPLAY_MANAGER=gdm
    ~~~

-   Could also do this by modifying xorg.conf but that looks like a
    headache, and this works

-   `lspci` will tell you the name of the graphics card and other system
    info if you need it

