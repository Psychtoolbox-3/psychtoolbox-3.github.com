---
layout: post
title: Psychtoolbox beta updates up to and including the update from 2009-02-18 (SVN Revision 1245)
category: news
author: kleinerm
---

These updates introduce support for the USTC RTBox button response box,
the PR-655 colorimeter, and various bug fixes and enhancements.
Especially the `IOPort` and `PsychPortAudio` drivers have been improved
again.

### Online documenation updated

Our tireless “master of online documentation” Tobias Wolf has updated
the online documentation of all PTB functions on the Wiki, so it
corresponds to the state of PTB - Beta as of 21st february 2009.

### New `PsychRTBox` driver for `RTBox` USB Response button box by Xiangrui Li et al.

This new driver (see `PsychRTBoxDemo` for demonstration of most basic
functions) allows to interface with the [“USTC RTBox Reaction Time
Box”](http://lobes.usc.edu/RTbox), a response button box for button
response collection from subjects with exact button press- or release
timestamping. In addition to four response buttons, the box also
provides a photo-diode input (including a photo-diode) and a single BNC
trigger input for reception and timestamping of external trigger signals
and visual stimulus onset. The driver allows to control all features of
the box and to retrieve exact timestamps in the regular Psychtoolbox
`GetSecs` time format, so the timestamps are directly comparable to
timestamps returned by
`Screen('Flip'), PsychPortAudio, KbCheck, KbWait, GetSecs, WaitSecs, IOPort`
etc., which greatly simplifies calculation of reaction times and other
time related events. Most aspects of the driver and especially its
timing precision have been extensively tested under a variety of
Macintosh computers and PC’s under Microsoft Windows XP, Linux and
`MacOS/X` 10.4.x and 10.5.x., so far with good results.

### `PsychPortAudio` sound driver

-   Important bugfix for playback of short sounds (less than about 50
    milliseconds) on MS-Windows and GNU/Linux. Due to a flaw in the
    underlying `PortAudio` library, trying to call
    `PsychPortAudio('Stop')` after playback of such short sounds could
    cause Matlab to hang until it got forcefully terminated. This is
    fixed. However, this bug was only present in betas released in
    January 2009. Older versions of the driver didn’t expose this flaw.

-   `PsychPortAudio methods 'Start', 'Stop', and 'RescheduleStart'` now
    also allow you to define a `sound offset time` (called ‘stop’ time)
    in addition to the previous ‘when’ sound onset time: This allows to
    schedule a sound playback which lasts until an exactly specified
    point in time, nearly sample accurate, ie., with sub-millisecond
    precision. The ‘Stop’ subfunction allows you to (re-)specify a stop
    time while playback is already active, for on-the-fly rescheduling
    of your sound timing. This is done by setting the new optional
    `'stopTime'` parameter.

-   These routines also allow you to specifiy and respecify (while
    playback is already active) the repetition count ‘repetitions’ for a
    defined number of sound repetitions, and the repetition count can be
    fractional now, e.g., 1.5 for one and a half repetitions of a sound.

-   The `PsychPortAudio('Stop')` function can now request stop of sound
    playback (as mentioned above via `'stopTime'` or ‘repetitions’ or
    immediately) without waiting for the stop to actually happen. This
    can avoid blocking execution of your Matlab code in the ‘Stop’
    routine for a few milliseconds, should your experiments require such
    a non-blocking behaviour. This is achieved by setting the new
    optional `'blockUntilStopped'` parameter to a zero value. Otherwise,
    the ‘Stop’ method will block until sound is really stopped as in
    previous driver versions.

-   `PsychPortAudio('RefillBuffer', pahandle [, bufferhandle=0], bufferdata [, startIndex=0]);`
    allows to refill portions of the sound playback buffer while
    playback is active, for dynamic updating of sound content in
    situations where the streaming refill via the
    `PsychPortAudio('FillBuffer')` command is not applicable. This is
    interesting when used in conjunction with the new
    `PsychPortAudio('SetLoop')` command to restrict sound playback to a
    subsection of the playback buffer.

-   The new subfunctions `PsychPortAudio('UseSchedule')` and
    `PsychPortAudio('AddToSchedule')` allow to predefine a whole
    sequence of precisely timed of sounds to be played according to a
    given playback schedule. This is similar to the playlists you can
    set in your favorite media player. The schedule can be extended on
    the fly during sound playback to allow very flexible sound playback
    which can concatenate different sounds with well defined gaps
    inbetween or completely gap-free. Unfortunately we don’t have any
    interesting demos for this new function yet.

-   For people with very low latency requirements, the driver can be
    switched into a new mode of operation, called “runmode 1” via the
    `PsychPortAudio('RunMode')` function. By default, runmode 0 is used.
    In runmode 1, the audio hardware, once started, keeps running all
    the time. This consumes more system memory and processing ressources
    on your computer during the runtime of your script, as processing is
    active even if no sound is played at all, but it allows for a faster
    stop and restart of playback operations, ie., it can avoid multiple
    milliseconds of delay, especially on Linux, but also to some lesser
    extent on the other operating systems. You can compare this to a
    strategy where you keep the engine of your car running during stops
    at red traffic lights or in traffic jams, as opposed to our default
    strategy of stopping the engine at each halt and restarting after
    the break.

### Colorimeter Support

-   We now support the Photo Research PR-655 colorimeter via the new
    `PR655Toolbox` in the folder
    `Psychtoolbox/Psychhardware/PR655Toolbox`. This code has been
    contributed by Thad Czuba. You can either use the routines in that
    subfolder directly, or use the higher level functions like
    `CMCheckInit, CMClose, MeasXYZ and MeasSpd` by selecting the
    ‘metertype’ argument to be 4.

-   Both, the new `PR-655` toolbox and the old `PR-650` toolbox now use
    the new `IOPort` driver instead of the old operating system
    dependent `SerialComm` driver. Due to this change, both toolboxes
    should now work on all operating systems, not only on OS/X.

### `IOPort` Serial port hardware support

The new `IOPort` driver has been refined in a few areas. The driver is
still much work in progress, with a few useful features missing.
However, it should be already a far superior replacement for all old
serial port drivers like `PsychSerial`, `SerialComm` and Matlabs
`serial` objects for most purposes.

-   `FindSerialPort` function: Now can also automatically find serial
    port devices for the `IOPort` serialport driver on all operating
    systems.

-   New optional parameter `'HardwareBufferSizes=in,out'` for
    `IOPort('OpenSerialPort',..);` and
    `IOPort('ConfigureSerialPort', ...);` configstring parameter. This
    is not set by default, and only supported on MS-Windows, ignored on
    other platforms. It triggers the Windows `SetupComm()` function to
    set the hardware input and output buffer sizes to the requested
    in,out values. Hardware drivers are free to ignore the request, and
    it will only work if invoked after opening the device but before
    doing any I/O. Rationale: The operating system is supposed to choose
    reasonable settings for these buffersizes if not provided (according
    to Microsoft documentation), but the old Windows `PsychSerial`
    driver set these sizes explicitely, so we give usercode the option
    to do so as well, in case some buggy windows drivers misbehave if
    this isn’t set.

-   `IOPort('OpenSerialPort')`: Bugfix in configuration option parser
    code for all operating systems. Providing settings/options in the
    optional `'ConfigString'` parameter which conflicted with the
    builtin defaults may cause wrong setup, ie. either the defaults take
    precedence or the users settings, but in a unpredictable way. This
    is fixed now. Didn’t show up in any real applications so far,
    because 100% of all tested devices (and probably 95% of all devices
    out there) are happy with our builtin defaults.

-   Help texts have been improved as well.

### Improvements and bug fixes to Screen and other drawing functions – The Visuals

-   New `Screen('Preference','ConserveVRAM', ...)` setting 16384 on OS/X
    allows to force use of AGL and Carbon in non-fullscreen windowed
    mode, even if a fullscreen window is requested. This as another
    attempt to work around the broken NVidia drivers for dual-display
    operations on Leopard 10.5.6 with Geforce 8000 hardware, as that bug
    persists on OS/X 10.5.6, and Apple engineering remains silent about
    this major defect. This workaround provides dual-display fullscreen
    display on such machines, but at a horrible performance, zero timing
    accuracy and defunct timestamping. It may be good enough for mostly
    static stimulus displays though.

-   `Screen('Computer')` on Mac OS should not crash anymore if machine
    has an empty machine name or empty username.

-   `Screen('GlobalRect', win)` now correctly returns the global
    bounding box (wrt. to origin of desktop coordinate system) of a
    given onscreen window handle ‘win’ even if the window is a real
    window, not a fullscreen window.

-   `Screen('FrameRect')`: When providing an empty (=default) rectangle,
    it didn’t draw anything due to some bug in the batchdrawing
    processing routine. This is now fixed.

-   `Screen('Resolution')` now only checks for open onscreen windows
    when deciding to be cooperative or not, not for any window.
    Previously a resolution switch was also prevented when textures or
    offscreen windows where open, which is not neccessary.

-   Bugfix for Screen on Mac OS: When onscreen window wasn’t a
    fullscreen window, but a windowed AGL+Carbon window, and the imaging
    pipeline was off, userspace rendering via MOGL didn’t work due to a
    bug in the way we set up our userspace OpenGL context in the AGL
    setup path. This is now fixed.

-   `Screen('FillOval')`: Added missing documentation of
    `'perfectUpToMacDiameter'` parameter.

-   Screen subfunctions `FillOval`, `FrameOval` and `FillArc`,
    `FrameArc`, et al. will now work with subpixel accurate precision
    instead of rounding given locations to full pixels at various
    occassions. The precision of positioning and sizing such drawing
    primitives is now only limited the the graphics hardware at use, no
    longer by Screen itself.

-   `Screen('DrawText')` on Linux: Didn’t assign proper textcolors or
    render text correctly if a floating point precision HDR framebuffer
    was enabled, and a HDR draw shader was active to work-around GPU’s
    without `glClampColorARB()` support, e.g., on Linux with current ATI
    driver for Radeon X1600. This is now fixed. Also made more robust
    against very long fontnames of more than 256 characters.

-   Bugfixes to some `PsychRects` functions: They didn’t handle the case
    of passing 2, 3 or 4 rects properly. Only the single rect and \> 4
    rects cases were handled correctly. This is now fixed, although the
    current beta still contains a glitch for the exactly 4 rects case.
    Bugfixes by Thad Czuba and MK.

-   `BitsPlusPlus` error handling improved: Restores display gamma
    tables on error abort.

-   `DrawFormattedText`: New optional ‘vspace’ parameter allows to set
    line spacing between consecutive lines of text. Contributed by Alex
    Leykin. The function also now optionally allows to draw text that is
    mirrored/flipped left-right and/or upside down.

-   New function `AddNormalsToOBJ`: Takes an obj 3D object definition,
    as provided by, e.g., `LoadOBJFile()`, and adds per-vertex surface
    normal vectors to it. Useful if an OBJ file doesn’t have surface
    normals defined. Uses cross-product computation on defining
    triangles to calculate normals.

-   Minor other fixes and updates to help texts.

**There are still a few unresolvable serious bugs in OS/X 10.5.6,
especially prominent with NVidia 8000 series hardware for which no
workaround exists. E.g., multi-display operation (stereo setups) seems
to be highly unreliable and dysfunctional. Frame sequential stereo on
NVidia 8000 series hardware seems to be seriously broken in 10.5.5 (and
maybe 10.5.6, untested). Only Apple engineering will be able to fix
this.**

### New or enhanced demos

-   `FDFDemo` and `moglFDF` received some further improvements: The
    `maxFGDots` and `maxBGDots` parameters are auto-adapted to meet
    requirements, instead of aborting with error. The new subfunction
    `ReinitContext` allows to change context stimulus parameters without
    need to destroy and recreate the fdf context, this is about 4 times
    faster when switching between conditions with high or low dot
    densities, short or long dot lifetimes and other parameters. The new
    optional `instantOn` flag to the `Update` function allows to buildup
    the whole dot distribution in one single ‘Update’ call at start of a
    trial. Minor other fixes and improvements. Now one can regulate the
    signal to noise ratio within the silhouette of the animated object
    between 0.0 and 1.0, allowing to introduce some background noise in
    the silhouette area. The `FDFDemo` now allows to control a couple of
    stimulus parameters during runtime by use of the cursor keys.

-   `VideoCaptureDemo` Now allows video image to cover full window, by
    proper, aspect preserving, rescaling.

-   `MinimalisticOpenGLDemo` now has an optional ‘checkerboard’ mode:
    Setting that optional flag will texture the spinning sphere with a
    Matlab generated checkerboard pattern instead of an earth surface
    image, just to show how this is done, as well as how to apply
    trilinear mipmap filtering to avoid any aliasing artifacts with such
    high-frequency patterns.

-   `SimpleMovieDemo` is the new most simple demo on how to playback
    Quicktime movies. Not fancy, but down to the absolute basics.

-   `PsychRTBoxDemo` demonstrates basic use of the new `PsychRTBox`
    driver for control of the USTC `RTBox` button response box.

### Test scripts in `PsychTests`

-   Minor improvements to dualhead display sync tests in
    `GraphicsDisplaySyncAcrossDualHeadsTest` and
    `PerceptualVBLSyncTest`.

-   `KeyboardLatencyTest` now allows some assessment of the timing
    accuracy of response boxes, the response box from Cedrus, and the
    reaction time box from Xiangrui Li et al.

### Misc other stuff

-   Merged large parts of the “Bitstuff Toolbox”: This is a collection
    of generally useful new M-File routines in the categories
    `PsychSignal`, `PsychOneliners` and `PsychProbability`. The toolbox
    was written and contributed under GPL license by Diederick C.
    Niehorster.

-   `RestrictKeysForKbCheck` is a new function that allows to restrict
    the keys to check in `KbCheck, KbWait, et al.` to a subset of keys
    on the keyboard. This is convenient on all systems to restrict
    subject responses to valid response keys. On Mac OS it can also
    provide a significant speedup in the operation of `KbCheck`,
    reducing its execution time from 1 millisecond to a few dozen
    microseconds.

-   `KbName` now queries all connected keyboards if called via `KbName`
    from the commandline, not only the primary keyboard.

-   Improvements to geometric display calibration routines: Optionally
    one can load an image file as a “backdrop image” to the calibration
    grids in `DisplayUndistortionBezier/BVL`, and one can set window
    size to the size of those images. This allows to (mis-)use those
    display calibration routines for creation of generic
    transformations, e.g., for generic image undistortion of images or
    videos. The still unfinished `ImageUndistortionDemo` allows to apply
    such calibrations to loaded images from disk for the purpose of
    image unwarping.

-   New routines for color conversions in Munsell color space in
    subfolder `PsychColorimetric/PsychMunsell`, contributed by David
    Brainard.

-   Add function `GetEchostring`: Ported from PTB-2, contributed by
    yaosiang.

-   Also add functions `GetNumber and GetEchoNumber` from PTB-2.

-   `Ask` function:Strips `ENTER` keycode and `BACKSPACE` keycodes from
    returned replies.

-   `WaitSecs('YieldSecs', seconds)` is a new subfunction of `WaitSecs`
    which allows to sleep for a specified time interval `seconds`, but
    imprecisely. That is, the sleep is allowed to take a few
    milliseconds longer than specified. This allows to use a different
    waiting strategy which is not precise, but reduces the load on the
    computers processor. It is meant for code that wants to be nice by
    not taxing the cpu too much, e.g., in a polling loop where not every
    millisecond counts.

-   `Snd`: Always returns some ‘err’ status, even if it is only a zero,
    as this return argument is mostly meaningless in current
    implementation. This for backwards compatibility to old Mac OS-9
    code.

-   Enhancements to `GetClicks` and `GetMouse`, as suggested by
    Diederick Niehorster.

-   Modified `PsychtoolboxRegistration` routine for online registration
    to use the `pnet()` file on Matlab runtimes to implement
    communication for online registration. No need to use netcat
    anymore, except for Octave runtimes. As netcat aka nc.exe aka
    nc111nt.zip is no longer needed on the MS-Windows platform it has
    been remove from the distribution. No problems for poor Windoze
    users due to idiotic virus scanners anymore.

-   The new `PsychHomeDir` function retrieves path to users home
    directory on each system, and optionally to subdirectories as well.

### New download location for Portaudio driver with ASIO support

The special patched `portaudio_x86.dll` audio low-level driver with
compiled-in support for Steinberg’s ASIO sound interface for use on
Microsoft Windows systems with our `PsychPortAudio` driver has a new
home on our Wiki. You no longer need to request the driver from Mario
Kleiner via e-mail. [Instead, simply download the zip file with the
driver from the PsychPortAudio section of the
Wiki](http://psychtoolbox.org/wikka.php?wakka=PsychPortAudio). The zip
file contains the DLL, a readme file with installation, setup and usage
instructions, and the special license for use of this driver, which
deviates from our normal GPL license.
