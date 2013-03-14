---
layout: post
title: Psychtoolbox beta update from 2008-07-12 (SVN Revision 1090)
category: news
author: kleinerm
---

This update, apart from work-arounds for for broken graphics card
drivers mainly introduces support for anti-aliasing of visual stimuli
while the image processing pipeline is used. So far, use of the imaging
pipeline and of multisampled anti-aliasing where mutually exclusive.
Simultaneous use of both is available on graphics hardware and operating
systems that support the required OpenGL extensions
EXT\_framebuffer\_blit and EXT\_framebuffer\_multisample.

### Hardware support

-   Serial port support: Small improvements to “IOPort”, a new
    cross-platform driver for control of Input/Output ports and esp.
    serial ports. At verbosity level zero, the driver shut now really
    shut up. If opening a port fails at verbosity level zero, no abort
    due to error is done, instead an invalid handle -1 is returned. This
    allows code to probe serial ports via trial and error without
    cluttering the console window of Matlab/Octave. Timing behaviour of
    blocking writes to serial port improved: Should now really block on
    Windows until data has been written out the port. On Linux a new
    polling-for-completion mode allows to poll for write completion
    instead of blocking. This is useful to get lower latencies on short
    writes, e.g., for clock calibration routines that are used to sync
    PTB’s clock with external hardware clocks.

-   `KbCheck(-1)` now allows to treat all connected keyboards on OS/X as
    one single keyboard, instead of querying each keyboard in isolation
    (when a keyboard index of a specific keyboard is passed) or of the
    primary keyboard alone. Contributed by Andrew Leber.

-   `CharAvail` Christopher Broussard implemented some speed
    optimizations for that command.

### Improvements to Screen – The Visuals

Most improvements are related to the image processing pipeline. While
the detailed documentation is contained in the files referenced below,
most functions are accessed and controlled by the `PsychImaging`
function and the basic help for how to use them can be found there.
Demos mentioned below demonstrate this stuff in “real world” scripts.

-   Support for multisample anti-aliasing when using the imaging
    pipeline: If the optional ‘multisample’ parameter in
    `Screen('OpenWindow')` or `PsychImaging('OpenWindow')` is set to a
    non-zero value, then multisample anti-aliasing will be used in the
    same way as when the imaging pipeline is disabled. This wasn’t
    supported up to now, because it requires a totally different
    internal implementation. Additionally,
    `Screen('OpenOffscreenWindow')` with imaging pipeline enabled,
    honors a new optional ‘multisample’ parameter, so one can enable or
    disable multisample anti-aliasing for offscreen windows on a
    per-offscreen windows basis. Please note though that anti-aliased
    offscreen windows can’t be directly drawn or copied around via
    `Screen('DrawTexture') or Screen('CopyWindow')`, neither can’t there
    images be read-back directly via `Screen('GetImage')`. Instead one
    needs to create a “normal” offscreen window of matching size and use
    `Screen('CopyWindow')` to create a copy of a multisampled offscreen
    window into such a normal offscreen window. The copy will be
    anti-aliased and drawable. This is due to the way the underlying
    hardware works – The use of `Screen('CopyWindow')` triggers an
    explicit multisample resolve and anti-aliasing operation for more
    control.

-   On MS-Windows and GNU/Linux, most recent NVidia and ATI GPU’s do
    support anti-aliasing with the imaging pipeline on. On OS/X, only
    some ATI GPU’s do support this feature when used on “Leopard”
    version 10.5.3 or later, but support for NVidia GPU’s on “Leopard”
    is expected to arrive in a future OS/X release.

-   `Screen('CopyWindow')` will use a new internal implementation on
    systems that support EXT\_framebuffer\_blit extension for more
    flexibility and speed. Should this pretty new code expose any bugs,
    you can use `Screen('Preference', 'ConserveVRAM', 2048);` setting to
    switch back to the old implementation, but don’t forget to report
    such issues to the forum, should there be any.

-   The subfunction `Screen('Blendfunction')` optionally allows to set a
    “color write mask”: You can selectively enable or disable drawing
    into specific color channels, in case this is of any use. E.g., you
    could only enable the red channel for drawing ops, so any following
    drawing commands only change colors in the red channel, but leave
    the green, blue or alpha components of the framebuffer untouched.

-   Minor other fixes or help text updates.

### New built-in workarounds in Screen for broken graphics drivers and operating systems

These workarounds get automatically enabled if the corresponding problem
is detected on your system. Some will print out some warning messages to
inform you about the problem and possible caveats related to the
workaround. Remember: It’s always better to fix the system than to rely
on some workaround which can only fix 90% of the problem and isn’t
totally for free. Therefore stay informed about graphics driver and
operating system updates if your system has problems.

-   MS-Windows with many ATI cards and recent NVidia cards: Crash when
    trying to use 3D mode. Fixed: You no longer need to provide the
    special `Screen('ConserveVRAM')` flags to manually enable
    workarounds. Should just work, without any known limitations.

-   MS-Windows with many ATI cards and recent NVidia cards/drivers:
    Beamposition queries fail and therefore get disabled. Certain types
    of failure can be auto-detected and a workaround is enabled. This
    workaround should reenable high-precison timestamping on such
    systems, at the expense of slightly increased processor load in
    certain cases. The warning message of Screen will tell you about
    more details and refer you to some help text that explains further
    caveats of this approach.

-   OS/X with all graphics cards on both “Tiger” and “Leopard”: Wrong
    conversion of very small values in floating point textures of 16 bit
    float precision. Very small values (around 10e-9) which should be
    rounded down to zero, as they are not representable by that format,
    “wrap around” and result in huge numbers that create severe visual
    artifacts. This is an operating system bug. Our code now performs
    this rounding itself, restoring correct behaviour, at the cost of
    additional computation time in `Screen('MakeTexture')` when using
    such floating point textures. If you use 32 bpc floating point
    textures instead, numerical precision will be much higher, and there
    are no known problems with that format. 16bpc textures are accurate
    to 3 digits behind the decimal point, whereas 32 bpc float textures
    are accurate to around 7-8 digits - sufficient for any conceivable
    use. However such high precision textures take up twice the amount
    of memory and have potentially lower drawing speeds– Life is full of
    trade-offs…

-   Some optimizations to the internal texture creation code to allow
    for faster texture creation on some broken ATI drivers on Windows:
    Speedup can be 10x or more.

-   The timestamping code in Screen has been improved further to try to
    prevent false alerts wrt. broken timestamping on some slightly
    deficient graphics drivers under rare conditions.

-   Workaround in `Screen('DrawDots')` and `Screen('DrawLines')` to
    prevent hard graphics system lockups on some totally broken OS/X
    10.5 systems with NVidia hardware.

-   Workaround in procedural gabor and sine grating shaders for bugs in
    the GLSL shading language implementation for ATI Radeon HD cards on
    OS/X 10.5.3 and 10.5.4. The workaround fully resolves the issue.
    Apple engineering confirms a fix will be available in an upcoming OS
    release.

-   Small fix to `InitializeMatlabOpenGL`, contributed by Mingjing
    Zhang, Vision Research Lab., University of Science and Technology of
    China. Had trouble loading the GL constants file if PTB was
    installed in a path with spaces in its name on MS-Windows.

However, there are still a few unresolvable serious bugs in OS/X 10.5.3
and 10.5.4, especially prominent with NVidia 8000 series hardware for
which no workaround exists. E.g., multi-display operation (stereo
setups) seems to be highly unreliable and dysfunctional. Certain
`Screen('CopyWindow')` commands can caus a hard graphics system lockup
for no conceivable reason. Many posts on public internet forums and the
Apple mailing lists suggest many more similar serious problems. Only
Apple engineering will be able to fix this. Currently we recommend to
not upgrade to 10.5.3 or 10.5.4 on machines that are crucial for your
productive work!

### Misc other stuff

-   `MoviePlaybackDemoOSX` can now optionally the “Buy a Mac” ads from
    Apple’s website instead of the boring colliding discs demo movie on
    “OS/X”. Unfortunately movie playback from the web is only supported
    on “OS/X”, so the main target audience is missed ;-)
-   `MinimalisticOpenGLDemo` allows to set flags to demonstrate
    multisample anti-aliasing with/without imaging pipeline enabled.
-   Other small enhancements to demos, downloaders and installers.
