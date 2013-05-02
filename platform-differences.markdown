---
layout: page
title: Differences between PTB-3 versions for OS X, Windows and Linux
category: getting-started
---

The implementations of Psychtoolbox-3 for Microsoft Windows and GNU/Linux are
derived from the Mac OS X implementation. As of October 2012, all versions are
mostly compatible to each other and equally capable in core functionality. The
different operating systems differ in their capabilities and limitations. You
will have to take this into account if you want to write portable scripts. The
following information should allow you to write scripts that are as portable as
possible and to assess if PTB on a specific operating system is suitable for
you.

*The information on this page is periodically updated (i.e., at any point in
time slightly outdated). It always refers to the state of the current beta
flavor of PTB.*

##### Contents

* Will be replaced with the ToC
{:toc}
{::options toc_levels="3..4"/}

## Status of different core features and how to handle differences

### Matlab M-File functions

All functions that are implemented as Matlab M-Files should work without
any differences between system platforms, as long as they don't depend
on system dependent MEX files. M-Files are tested with the Matlab 7.x
series and the GNU/Octave 3.2.x series.

If you need to write scripts that have to behave differently on the
different platforms, the following functions may be helpful:

-   `IsOS X` returns `1` when the script is executed under Mac OS X, `0`
    otherwise.
-   `IsWin` returns `1` when the script is executed under Microsoft Windows,
    `0` otherwise.
-   `IsLinux` returns `1` when the script is executed under GNU/Linux, `0`
    otherwise.
-   `IsLinux(1)` returns `1` when the script is executed under GNU/Linux with a
    64 bit version of Matlab or Octave, `0` otherwise. 
-   `Is64Bit` returns `1` when the script is executed in a 64-Bit version of
    Matlab or Octave, `0` otherwise.
-   `IsOctave` returns `1` when the script is executed in GNU/Octave, `0` if
    the script is executed in Matlab.
-   `OSName` returns the name of the operating system platform.
-   `AssertOpenGL` aborts execution of your script if someone tries to execute
    it in PTB-2 instead of PTB-3.
-   `AssertOS X` aborts execution of your script if someone tries to execute it
    on a operating system other than Mac OS X.
-   `AssertGLSL` aborts execution of your script if it is executed on graphics
    hardware that does not support the OpenGL Shading language GLSL.

### Serial port access

Our `IOPort` driver provides high quality, flexible serial port support
(also for USB serial ports) with high timing precision on all operating
systems, so use of `IOPort` is strongly recommended over less optimal
solutions like Matlabs serial command.

### Joystick support

The OS X and Linux versions support joysticks via the new `GamePad`
function. We provide some simple joystick support for Windows via
`WinJoystickMex`.

### Eyelink toolbox

A functional implementation of the Eyelink toolbox is included in the
`PsychHardware` folder of PTB for all operating systems. It is reported to
work well, although it's not polished yet, e.g., the documentation and
some of the demos are not yet updated and cleaned in all parts. You must
install the runtime libraries from SR - Research on your system for this
to work. They come bundled with your Eyelink and are also downloadable
from their website. As of October 2012, there seems to be no support for
Eyelink on 64-Bit Windows systems, i.e., Eyelink will not work with
64-Bit Matlab. This limitation is imposed on us by SR-Research's lack of
support.

### `Snd` command for sound output

Sound output via the old and deprecated `Snd` command is currently
implemented as a wrapper around the `PsychPortAudio` driver for decent
cross-platform compatibility. However use of `Snd` is deprecated for all
but the most simple use cases, e.g., providing simple auditory feedback
to a subject. For research grade auditory stimulation, use
`PsychPortAudio` directly, or you will be doomed! 

<http://PsychPortAudio-link>

### OpenGL for Matlab/Octave support MOGL

Support for OpenGL low level commands is identical for all systems.
Well, almost: Support for specific functions depends on the capabilities
of your graphics hardware and OpenGL implementation, so some of the
most recent features of OpenGL may not be supported on old graphics
hardware. The solution to this problem is simple: Upgrade your graphics
drivers or your hardware. We currently support the OpenGL 2.1 API and
earlier versions, including various extensions.

### PsychHID and the DAQ toolbox

`PsychHID` for control of USB HID devices is implemented on all systems
since the end of 2011. You may encounter differences in the information
provided about connected HID devices when calling `PsychHID('Devices')`
due to differences in the underlying operating systems. If you write
code that uses device enumeration to detect your devices, make sure to
test on different operating systems to take these differences into
account.

### GamePad

The `GamePad` function is only available on Mac OS X and Linux for
now.

### Fonts

The `Fonts` command for flexible query and handling of character fonts
*only exists on Mac OS X* with no plans to ever implement it on
Windows or Linux.

### `ListenChar,` `CharAvail,` `GetChar,` `FlushEvents`

In Matlabs regular GUI mode, functions for character input are
implemented as a Java class via Matlabs built-in Java virtual machine
(JVM). Usage on all platforms is identical, no known principal
differences, except that it doesn't work well on MS Windows Vista and
Windows-7 (see the FAQ section about Vista problems for more info).
Differences, if any, would be due to differences in the implementation
of the JVM in different versions of Matlab. We need JVM version 1.4.2 or
later. If Matlab is run without Java support or GUI (`matlab -nojvm`
mode or `matlab -nodesktop` mode selected at startup), or if you are
using Octave instead of Matlab, a different implementation is used,
which works but is more limited in its capabilities. Read `help
GetChar` and `help ListenChar` for more info. The
`GetKbChar` function is often a viable and more robust replacement for
`GetChar`.

### `KbCheck`, `KbWait`, `KbName`

Usage, behaviour and timing of `KbCheck`, `KbWait` and `KbName`
should be identical / similar on all systems - no known relevant
differences.

The mapping of keyboard scancodes to key names used to be different in
the Psychtoolboxes for OS 9, OS X, Windows and Linux. E.g., the left
arrow cursor control key used to be named `left` on Windows,
`LeftArrow` on Mac OS X and `Left` on Linux. This is annoying if one
wants to write portable scripts. When writing new code, you should add
the command `KbName('UnifyKeyNames');` at the top of your script. This
will make sure that `KbName` accepts and returns identical keynames on all
operating system platforms, allowing you to write portable code without
extra effort. However, mapping of some special or exotic keys may be
incomplete, so you should probably avoid those keys for portable
scripts.

{% highlight matlab %}
% Add this at top of new scripts for maximum portability
% It unifies the names for keyboard keys across systems
KbName('UnifyKeyNames');
{% endhighlight %}

### `SetMouse`, `GetMouse`, `ShowCursor`, `HideCursor`, `GetSecs`

No known relevant differences in behaviour or quality, tell us if you
find some! `GetSecs` timestamps are accurate at sub-millisecond level on
all systems. The mouse and cursor handling functions on Linux allow to
query and control multiple mice or mouse cursors individually. Only one
mouse or mouse cursor is supported on OS X and Windows, multiple
mice are "merged" into one mouse input.

### Priority and `WaitSecs`

The range of values accepted by the `Priority` command differs between
OS X, Windows and Linux. `Priority(0)` disables realtime scheduling on
all operating systems. On Linux, the Priority command can utilize some
special system facilities to make realtime mode more effective and
robust than on the other operating systems. On Linux you can also
optionally install a low-latency or hard-realtime operating system
kernel and various other tweaks to the system configuration if you
require especially precise or robust realtime behaviour. This is
generally not needed for most experimental setups, but if you choose to
do it, it can provide realtime behaviour and timing precision that is
orders of magnitude better than what Windows or OS X can possibly
achieve. See the Linux specific setup pages on the Wiki for more
information.

Use the `MaxPriority` function to query maximum allowable priority
levels for realtime scheduling (`help MaxPriority`) in order to
keep your code portable.

{% highlight matlab %}
% Select maximum allowable realtime priority
% for current operating system
Priority(MaxPriority);
{% endhighlight %}


`WaitSecs` accepts values with microsecond precision. The robustness and
accuracy of the *real waiting time* compared to the *requested
waiting time* depends on the scheduling accuracy and timing jitter of
the underlying operating system. My experience is that scheduling on a
well configured Linux system or Mac OS X Tiger / Leopard system is very
accurate and robust, whereas Microsoft Windows systems are
*significantly worse* on many tasks. For best possible precision, use
a Linux system with low-latency or realtime kernel installed.

### `Screen`

The implementation of `Screen` is mostly identical on all systems,
providing the same capabilities and performance on all operating
systems. The following differences are known to exist. These differences
are mostly unavoidable and therefore unfixable due to different designs
and limitations in the underlying operating systems.

-   Multi display support: On single display setups, Screen behaves
    identically. On multi display setups, enumeration of displays is
    handled slightly different:
    -   **Mac OS X**: `Screen('Screens')` will return a vector with
        one numerical screen id for each connected display device, e.g.,
        `[0 1]` for a dual-display system. Display `0` corresponds to the
        main display (the one with the Dock), Display `1` corresponds to
        the secondary display.
    -   **Linux**: Each X-Windows system x-screen will be enumerated
        as a separate Psychtoolbox screen. A x-screen can cover multiple
        connected physical display devices, depending on how you
        configured your setup in the `xorg.conf` file. On a single display
        setup you only have one x-screen, which maps to Psychtoolbox
        screenid 0. On a multi-display setup you would group physical
        displays together into one or multiple x-screens. Each x-screen
        maps to a Psychtoolbox screenid and is either covered and
        displayed to by a separate fullscreen Psychtoolbox onscreen
        window for stimulus presentation, or not used by Psychtoolbox,
        e.g., for operator control displays. The individual physical
        display devices (aka outputs) attached to a Psychtoolbox screen
        can be individually controlled via the
        `Screen('ConfigureDisplay')` command and the optional
        `physicalDisplay` parameter of various `Screen` subcommands,
        e.g., the `LoadNormalizedGammaTable` command for setting
        individual gamma tables per display.
    -   **Windows**: If your system is switched to multi-monitor mode,
        `Screen('Screens')` will report `n+1` displays for a setup
        with `n` displays. The display with index zero is special: It
        corresponds to the display area of *all* connected displays.
        If you open an onscreen window on display zero, it will occupy
        all connected display devices. This is useful for presentation
        of stereo stimuli or other binocular stimuli. The screens with
        indices `1, 2, ..., n` correspond to the display areas of
        display devices `1, 2, ..., n`, so specifying these screen ids
        allows you to open onscreen windows on individual displays or to
        query and set properties of individual displays, e.g., refresh
        rate, resolution, color depth, size or the hardware color lookup
        tables. If you have an unusual display arrangement, you can also
        explicitely specify a `rect` argument to the
        `Screen('OpenWindow', screenid, color, rect)` command to create
        a window that occupies the specified `rect` on the desktop,
        partially covering multiple monitors.

-   Window placement and size:
    -   **Mac OS X**: `Screen('OpenWindow', screenid, color, rect)`
        correctly handles the `rect` argument - You can open windows
        that don't cover the full display area for debugging purpose.
        However, timing precision and stimulus onset timing is strongly
        impaired in windowed mode due to limitations of MacOS X. By
        default, an onscreen window always covers the full area of a
        specific display device.
    -   **Windows**: Onscreen windows cover the full display area as
        on OS X by default. If you provide a `rect` argument,
        Psychtoolbox will open a onscreen window that only covers the
        area specified by the `rect` parameter. E.g.,
        `Screen('OpenWindow', 0, [], [0 0 800 600])` would open an
        onscreen window on display device zero, with its top-left corner
        at `(0,0)` and its bottom-right corner at `(800,600)`. The window
        will have the usual decorations, title bar and buttons, so it
        can be closed, minimized/maximized, resized and dragged around
        on the screen. This is useful for debugging. You can also open
        multiple windows on the same display device.
    -   **Linux**: ditto.

-   Color depth setting `pixelsize`: This parameter is mostly there
    for backwards compatibility. It should be left at its default
    setting in almost all cases.
    -   **Mac OS X**: Screen tries to switch a display device to the
        requested color depth before opening an onscreen window on it.
        Psychtoolbox may work at a setting of 24 bpp or 16 bpp with
        reduced functionality, i.e., some alpha blending modes are not
        supported at a depth of 24 bpp and color resolution is
        drastically reduced at 16 bpp. Color index mode with 8 bpp is
        not supported on OS X.
    -   **Windows**: The color depth setting is ignored. You'd need to
        change the settings in the display properties control panel of
        your system. However, any setting except the default of 32 bpp
        will cause abortion of your script with an error message.
    -   **Linux**: Works with 24 bpp or 32 bpp, depending on graphics
        card. Simply leave out this parameter so PTB can choose the
        correct default.

    In any case, you have to run your displays at a color depth of 32
    bits per pixel - which is the default setting - to take full advantage
    of Psychtoolbox alpha blending functions.

-   Stereo presentation modes `stereomode`:
    -   **Mac OS X**: All modes are supported with high performance.
        For dual-display stereo you need to use a different setup code
        than on Windows. On Windows you'd use stereo mode `4`, whereas on
        Mac OS you'd use stereo mode 10 and a slightly different setup
        code. Look at `ImagingStereoDemo` on how to do this.
        *Caution:* The different displays on a Mac OS X system are
        not synchronized wrt. their display refresh cycles! This can
        cause tearing artifacts on one of the two displays if you use
        dual-display mode for binocular stimulation and show stereo
        movie animations.
    -   **Windows**: Mode `1` `frame sequential stereo` for driving
        shutter glasses is emulated in software by PTB on consumer
        hardware, so actual quality of frame-sequential stereo will
        highly depend on your system. The professional line of gfx-cards
        (ATI FireGL and NVidia Quadro series) should support
        this mode at high quality. All other modes (Anaglyph stereo,
        dual display stereo, free fusion) should work on all hardware
        with high performance.
    -   **Linux**: Mode `1` `frame sequential stereo` for driving
        shutter glasses is emulated in software by PTB on consumer
        hardware, so actual quality of frame-sequential stereo will
        highly depend on your system. The professional line of
        gfx-cards (ATI FireGL and NVidia Quadro series) should
        support this mode at high quality. All other modes (Anaglyph
        stereo, dual display stereo, free fusion) should work on all
        hardware with high performance.

    In general, it is beneficial to use the stereo modes with the PTB
    imaging pipeline enabled. See `ImagingStereoDemo` for an example of
    use. On OS X this is crucial for dual display stereo. On all operating
    systems if you use Anaglyph stereo presentation, it will allow for very
    flexible control over gains and other parameters via
    `SetAnaglyphStereoParameter()`.

-   `Quicktime/GStreamer` support for audio- and movie playback:
    -   **Mac OS X**: Movie playback is fully supported via GStreamer,
        but on 32-Bit Matlab, Quicktime is used by default.
    -   **Windows**: Movie playback is fully supported via GStreamer.
    -   **Linux**: Movie playback is fully supported via GStreamer at
        a performance that generally exceeds the performance of either
        Windows or Mac OS X.

-   `Drawtext` and `TextBounds` functions for drawing text: No difference in
    functionality or quality, only in speed.
    -   **Mac OS X**: Apples ATSU text renderer is used. Provides very
        flexible, very high quality text rendering at a comparably low
        speed. Unicode character strings are supported. Text bounding
        boxes are highly accurate.
    -   **Windows**: By default, a text renderer based on the Windows
        GDI is used: It provides accurate text bounding boxes,
        anti-aliased text (although not at the superb quality level of
        OS X, but still good), and Unicode support, just as on OS X with
        moderate speed. An older text renderer can be optionally
        selected, which is based on OpenGL display lists: Less flexible,
        significantly lower text quality (no text Anti-Aliasing), only
        the standard ASCII character set, but *very fast*. Limitations
        of the fast optional renderer: Computation of text bounding
        boxes doesn't take descenders of letters into account, due to
        some Microsoft implementation brain-damage. The text size
        setting is not correctly handled due to some unresolved bug.
        Text shows up at a size approximately 2/3rd of what was
        requested.
    -   **Linux**: Fast text rendering of high quality, anti-aliased,
        unicode text with true type text fonts is fully supported. The
        speed of the Linux text renderer is usually significantly higher
        than the speed of the Windows or OS X renderer, while
        retaining their quality, functionality and flexibility.

-   Stimulus onset timestamps reported by `Screen('Flip')`:
    -   **Mac OS X**: On many Intel Macs, the timestamps are
        guaranteed to be sub-millisecond accurate, regardless of system
        load or scheduling jitter. Synchronization of stimulus onset to
        the vertical retrace is guaranteed to be microsecond accurate on
        properly working hardware. However, on some recent versions of
        the operating system with ATI/AMD or Intel graphics cards,
        installation of the `PsychtoolboxKernelDriver` is required for
        reliable timestamping to compensate for various operating system
        bugs. Without this driver installed, a different set of
        workarounds so far provided at least millisecond accurate
        timestamping, but this workarounds are ineffective due to new
        additional bugs introduced in OS X 10.7 "Lion", so on 10.7
        and later, we cannot guarantee timestamp precision or
        correctness if you don't use the kernel driver.
    -   **Windows**: Accuracy of returned timestamps is the same as on
        OS X on NVidia and ATI hardware, but not on older Intel onboard
        graphics hardware. There it will be millisecond accurate in most
        cases, but no guarantees can be made due to technical
        limitations of the Windows + Intel graphics combo. Stimulus
        onset is microsecond accurate wrt. vertical retrace, as on Mac
        OS X.
    -   **Linux**: Stimulus onset is microsecond accurate wrt.
        vertical retrace, as on Mac OS X. Currently you need to run the
        `PsychLinuxConfiguration` script once and then reboot once, if
        you use the proprietary graphics drivers from NVidia or ATI/AMD
        to get the same timestamping precision as on a well working
        OS X or Windows systems. However, this function is
        automatically executed after each installation or update of your
        Psychtoolbox, so it rarely needs to be called manually by you.
        If you choose to use the free graphics drivers for Intel,
        ATI/AMD or NVidia graphics cards instead of the proprietary
        drivers, timestamp precision and visual stimulus onset precision
        will be even better and more robust than on any other operating
        system or graphics hardware without any need for additional
        setup steps or use of root mode.

-   Color lookup tables, gamma tables, CLUT animation:
    -   **Mac OS X**: OS X supports up to 16 bit DAC precision on
        graphics hardware that supports this. CLUT animation works, but
        updates to the CLUTS can't be synchronized to `Screen('Flip')`.
    -   **Linux**: Has the same capabilities as Mac OS X, the
        status of CLUT synchronization is hardware dependent.
    -   **Windows**: Windows supports up to 16 bit DAC precision on
        graphics hardware that supports this. CLUT animation is mostly
        impossible due to extreme brain-damage in the Windows CLUT
        implementation. Synchronization of CLUT updates to the execution
        of `Screen('Flip')` is possible.
    -   *Most older graphics cards are restricted to 8 bits DAC precision and
        even the latest models from ATI or NVidia have at most 10 bits of DAC
        precision, so the 16 bit limit imposed by the operating systems is a
        theoretical limit, not a practical one!*

    On recent graphics hardware, the
    `PsychImaging('AddTask','General','EnableCLUTMapping')` function allows to
    restore clut animation in a portable and reliable way on all operating
    systems.  This needs hardware with fragment shader support.  This method of
    clut animation also allows for perfectly frame-accurate animation.

    However, we consider clut animation mostly an obsolete, ancient feature -
    There are almost always better ways to create animated stimuli with all the
    new PTB drawing functions.

-   `Screen('Computer')` command:
    -   **Mac OS X**: The command returns lots of information about
        the host system, many of which seems to be pretty uninteresting
        for any practical purpose.
    -   **Windows**: Reports only bare minimum.
    -   **Linux**: Reports only bare minimum.

