---
layout: post
title: Psychtoolbox beta update from 2008-08-15 (SVN Revision 1110)
categories: news
author: kleinerm
---

This update introduces support for synchronizing the displays of ATI
based dual-display setups on OS/X, experimental support for 10 bit
native framebuffers on some graphics hardware, smallish fixes for demos
and subroutines, and a few new demos and tests in `PsychDemos` and
`PsychTests`, as well as improvements to existing demos. The new
`IOPort` has been improved as well.

### `IOPort` Serial port hardware support

The new `IOPort` driver has been refined in a few areas. The driver is
still much work in progress, with a few useful features missing.
However, it should be already a superior replacement for all old serial
port drivers like `PsychSerial`, `SerialComm` and Matlabs `serial`
objects for most purposes.

-   The optional `nonBlocking` flag of the `IOPort('Write')` and
    `IOPort('Read')` subfunctions is replaced by a `blocking` flag
    instead! If you didn’t specify that flag in code using that driver,
    you won’t need to change anything in your code, because the default
    behaviour is the same - and the default is pretty reasonable. If you
    specified that flag in your code, you’ll have to change that flag to
    be the opposite of what it was! If you used a setting of `0`, change
    it to `1` and vice versa. The old flag `nonBlocking` used a
    double-negation - A setting of zero meant *no non blocking
    operation, ie., blocking operation*! Beta testing proved that this
    twisted definition is too hard on the brain, including the brain of
    the person that developed the driver ;-) – The meaning of the new
    `blocking` flag is easy to understand, so the potential of wrong use
    of that flag should be greatly reduced.

-   On GNU/Linux, the `blocking` flag in the `IOPort('Write')`
    subfunction can also be set to a setting of `2`, on other operating
    systems a setting of `2` is treated like a setting of `1` for now. A
    settting of `2` requests use of an especially low-latency mode of
    waiting for write completion. This is useful for code that needs
    especially high timing precision in sending data out of the serial
    port, but it incurs much higher processor load, so it should be used
    judiciously. With some serial port hardware, it can cause a complete
    hang of the application due to low level driver bugs (e.g., the
    current FTDI serial-over-usb driver).

-   At `IOPort('Verbosity',0)` verbosity level zero, the driver won’t
    abort an `[handle, errmsg] = IOPort('OpenSerialPort',...);` call
    anymore if opening the serial port fails. Instead it returns
    `handle` to be a negative number and returns an operating system
    dependent error message in the optional return argument `errmsg`.
    The text string `errmsg` contains some specific (searchable) text
    tokens to signal some frequent error conditions. Specifically, the
    text string `ENOENT` is contained in `errmsg` if one tries to open a
    non-existent serial port device. Accessing a device which is already
    opened by some other process, or with insufficient access
    permissions, or opening a serial port that exists but doesn’t have
    an operational device connected, will return `EBUSY` and/or `EPERM`
    as part of the `errmsg` string. This behaviour and tokens allows
    custom written Matlab code to auto-detect and probe available and
    operational serial ports by trying to open known ports and checking
    the return codes. Useful for automatic device detection.

-   Help texts have been improved as well.

### Hardware support

-   The `CedrusResponseBox` driver has been improved to take advantage
    of the improved `IOPort` driver for higher robustness in error
    handling. The overall robustness of Cedrus response box support
    hasn’t increased though, but we are quite certain that this is
    mostly due to design flaws in the response boxes. Still no response
    from Cedrus developer support, 4 month after an inquiry… See also
    Docs:CedrusResponseBox

### Improvements to Screen – The Visuals

Most improvements are related to the image processing pipeline. While
the detailed documentation is contained in the files referenced below,
most functions are accessed and controlled by the `PsychImaging`
function and the basic help for how to use them can be found there.
Demos mentioned below demonstrate this stuff in “real world” scripts.

-   Support for native 10 bits per color component (10 bpc) framebuffers
    on some graphics hardware + operating system combinations:
-   On GNU/Linux and OS/X with ATI Radeon GPU’s of the consumer level
    Radeon X1000 series and the Radeon HD2000 / 3000 / 4000 series and
    later, we provide *experimental* support for 10 bit framebuffers
    with our own homegrown solution. On Linux you need to start Octave
    or Matlab as system administrator or via the `sudo` command so it
    has the neccessary permissions to do so. On OS/X you need to load
    our special `PsychtoolboxKernelDriver`, see
    `help PsychtoolboxKernelDriver` for how to do that. Support is
    experimental in the sense that we can’t guarantee that this feature
    will work reliable (or at all) on a given system configuration,
    because we use tricks that are not officially supported or
    recommended by ATI or Apple, so this feature may or may not work due
    to factors out of our control. If it works, it may break with future
    operating system upgrades, so if you need it, better make a backup
    of your operating system in case you’d need to downgrade!
-   That said, it works pretty well on the tested machines with Tiger
    10.4.11, and it actually worked like that since multiple
    Psychtoolbox beta releases. The news is that we finally verified it
    really gives 10 bits resolution on consumer Radeon cards via some
    perceptual visual test - A nice greyscale gradient test image which
    shows clearly perceptible intensity steps at the expected locations
    in 8 bit framebuffer mode, but a smooth gradient in experimental 10
    bit framebuffer mode.

-   On Microsoft Windows and GNU/Linux, the first graphics cards with
    native, officially vendor supported 10 bit framebuffers start to hit
    the market. If you happen to have such a card, Psychtoolbox will
    support it as well, without the need for special experimental
    tricks. These cards should support 10 bit reliably - assuming the
    vendors implementation is correct. As of now, vendors have announced
    some level of 10 bit support for the following cards:

-   ATI/AMD `FirePro` / `FireGL` GPU of the latest 2008 generation is
    advertised as supporting 10 bit on special 10 bit digital displays
    (e.g., high precision flat panels with `DisplayPort`), it may soon
    support 10 bit over the analog output as well (ie., VGA driven CRT
    monitors etc.).

-   The latest generation NVidia Quadro GPU’s on Linux (and probably
    Windows?) will support 10 bit output, according to [this excerpt
    from the release notes of the latest NVidia display drivers for
    Linux](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.12/README/chapter-28.html).

-   The latest generation of NVidia Geforce GPU’s is rumored to support
    10 bit natively under some circumstances as well: [See this
    link](http://blogs.zdnet.com/hardware/?p=2079&page=4) and [this
    link](http://www.tgdaily.com/content/view/38649/135/).

-   Support for 10 bpc framebuffers can be enabled via the
    `PsychImaging('AddTask', 'General', 'EnableNative10BitFramebuffer');`
    subcommand, as demonstrated in the
    `AdditiveBlendingForLinearSuperpositionTutorial` demo.

-   The `PsychtoolboxKernelDriver` for OS/X has been refined. We’ve
    verified that it is able to synchronize (or resynchronize, after
    some change of display settings or display configuration) the video
    refresh cycles of two identical displays connected to the two output
    connectors of a dual-head graphics card. This works only on ATI
    Radeon graphics cards of the X1000 series (and likely later models
    of the HD series) and only for one single dual-head card. It has
    only been tested on the Radeon Mobility X1600 so far. You need to
    choose identical monitors and identical display settings for
    resolution, color depths and refresh rate if you want the monitors
    to stay in sync after a synchronization, otherwise they’ll quickly
    drift out of sync due to different timing. You need to load the
    kernel driver as described in `help PsychtoolboxKernelDriver`. Then
    you can issue the
    `residual = Screen('Preference', 'SynchronizeDisplays', 1);` command
    to trigger a resync. The optional return argument `residual` will
    contain a remaining offset in scanlines between the two displays.
    The driver will try up to four times to resync. We always managed to
    get perfect sync this way. The scripts
    `PerceptualVBLSyncTest([0,1])` and
    `GraphicsDisplaySyncAcrossDualHeadsTest` allow you to test the sync.
    The first script allows for a perceptual test, the latter script for
    some numeric assessment.

-   The `PsychtoolboxKernelDriver` for OS/X also provides support for
    beamposition timestamping on ATI graphics cards – a feature lacking
    on current OS/X. This support is nothing new, just worth mentioning
    again.

-   We no longer unconditionally disable beamposition queries on
    MS-Windows with Intel GPU’s. Some modern Intel GPU’s will probably
    work correctly and our tests have improved so much that we should be
    able to detect problematic chips automatically. So some Intel GPU’s
    will provide more accurate stimulus timestamping.

-   Capabilities of the ATI FireGL / FirePro GPU should be now detected
    correctly on Windows and Linux.

-   A new image processing function `AddImageUndistortionToGLOperator()`
    plus demo `ImageUndistortionDemo.m` how to use it: It allows
    application of geometric “unwarp” transformation as created by
    `DisplayUndistortionBVL/Bezier` to textures and offscreen windows by
    use of `Screen('TransformTexture')` instead of as part of preflip
    operations. This allows for geometric undistortion of input images,
    instead of whole display devices. The demo is kind of sketchy,
    that’s why it is added to the `PsychAlpha/` subfolder to label it as
    workable but immature. This method is useful if you don’t want to
    correct for geometric distortions of your display device (for that,
    see `help DisplayUndistortionBVL`), but if you have some optically
    distorted input video footage or images (e.g., from some camera)
    that you want to undistort, or if you want to actually apply a
    geometric distortion to your visual stimulus image.

-   Minor other fixes and updates to help texts.

### New built-in workarounds in Screen for broken graphics drivers and operating systems

These workarounds get automatically enabled if the corresponding problem
is detected on your system. Some will print out some warning messages to
inform you about the problem and possible caveats related to the
workaround. Remember: It’s always better to fix the system than to rely
on some workaround which can only fix 90% of the problem and isn’t
totally for free. Therefore stay informed about graphics driver and
operating system updates if your system has problems.

-   MS-Windows with many ATI cards and recent NVidia cards/drivers:
    Beamposition queries fail and therefore get disabled. Certain types
    of failure can be auto-detected and a workaround is enabled. This
    workaround should reenable high-precison timestamping on such
    systems, at the expense of slightly increased processor load in
    certain cases. The warning message of Screen will tell you about
    more details and refer you to some help text that explains further
    caveats of this approach.
-   In this release we’ve increased the sensitivity of the test which is
    supposed to detect such broken beamposition mechanism on startup, so
    it is less likely to miss some broken configs. In case it still
    misses some bugs, you can add the new setting `4096` to a call
    `Screen('Preference', 'ConserveVRAM', ...);`, see
    `help ConserveVRAMSettings` for more info. This will unconditionally
    enable the special workarounds, even if our test doesn’t detect any
    problems.

**There are still a few unresolvable serious bugs in OS/X 10.5.3 and
10.5.4, especially prominent with NVidia 8000 series hardware for which
no workaround exists. E.g., multi-display operation (stereo setups)
seems to be highly unreliable and dysfunctional. Certain
`Screen('CopyWindow')` commands can caus a hard graphics system lockup
for no conceivable reason. Many posts on public internet forums and the
Apple mailing lists suggest many more similar serious problems. Only
Apple engineering will be able to fix this. Currently we recommend to
not upgrade to 10.5.3 or 10.5.4 on machines that are crucial for your
productive work!**

### New or enhanced demos

-   `AdditiveBlendingForLinearSuperpositionTutorial` shows two things:
    -   How to take advantage of high precision floating point textures,
        framebuffers and additive alpha-blending to efficiently draw
        mathematically correct superimposed stimuli, e.g., overlapping
        gratings with controllable contrast. This demonstrates a very
        efficient way of doing such things.
    -   How to enable support for a variety of supported high precision
        display devices and methods. The demo shows correct setup of nearly
        all currently supported devices. Type
        `help AdditiveBlendingForLinearSuperpositionTutorial` for an
        overview. The previous demo, which was specific to the CRS `Bits++`
        box, has been merged into this demo.

-   `SimpleVoiceTriggerDemo` demonstrates two different methods of
    implementing voice triggers via the `PsychPortAudio` driver. The
    `BasicSoundInputDemo` and a few other scripts demonstrate this as
    well, but this demo is cut down to show only the essentials of voice
    trigger support. Please note that this is just a simple
    threshold-based trigger, nothing fancy. One could implement more
    clever filtering to make it more robust, but the basic structure
    would be the same.

-   `DrawMirroredTextDemo` now also shows how to mirror (flip) text
    upside down instead of only left vs. right.

-   `MovingLineDemo` just shows a pair of vertical lines which move
    horizontally over the screen from left to right. The speed of travel
    can be set. Why? Because it nicely illustrates the kind of display
    artifacts and strong motion blur you can get for moving stimuli if
    you use a flat panel instead of a CRT monitor.

### New test scripts in `PsychTests`

Two tests illustrate the accuracy, or rather inaccuracy, of keypress and
mousebuttonpress timestamps. Try them yourself! There are good reasons
why special response boxes are still sold and bought for precise
reaction time measurements.

-   `KeyboardLatencyTest`: This test scripts implements a method to
    measure absolute keyboard or mouse latency, ie., how close the
    measured keypress time, e.g., via `KbCheck` or `GetMouse` is to the
    real keypress time on your standard keyboard, trackpad our mouse.
    The script relies on a properly configured `PsychPortAudio` driver
    and a sensitive microphone attached to or close to your keyboard or
    mouse. I’ve tested it with the built-in microphone of a MacBookPro.
    The measurement procedure consists of you repeatedly hitting keys on
    the keyboard or buttons on you mouse / trackpad. The noise made by
    hitting the buttons or keys gets captured by the microphone and
    timestamped by our audio driver + threshold based “voice trigger”
    implementation. Keypress / Mouse button press time is also measured
    via a tight `KbCheck`, `KbTriggerWait` or `GetMouse` loop. The
    script then compares the timestamps of both methods to compute
    average keypress latency and variability in timing, assuming/knowing
    that the audio measurements are usually more accurate and low
    latency on well working audio hardware. The method is of course not
    perfect, needs careful tuning of sound thresholds and a well working
    sound card, and you should obviously not trust the measurements down
    to the millisecond - or at least first verify correct working of the
    sound trigger method with measurement equipment before trusting it .
    Still it provides some quite nice illustration of how *large* and
    *noisy* latencies from standard keyboards and mice can be. Also with
    identical hardware, latencies can vary significantly depending on
    operating system and model of keyboard or mouse. Example: On a
    MacBookPro under OS/X average latencies of 16 msecs for external
    mouse queries and 30 msecs for internal keyboard queries have been
    observed. The same machine under Ubuntu Linux 7.1 showed also 30
    msecs average latency for the keyboard, but 60 msecs latency for the
    mouse. Variability of mouse timestamps was lower than that of
    keyboard timestamps.

-   `HIDIntervalTest`: This scripts measures the sampling interval of
    human interface devices (HID), specifically mice and keyboards.
    During a measurement loop of 10 seconds duration, it asks you to
    randomly and furiously hit keys on the keyboard, press mouse buttons
    and move the mouse. Then it plots histograms with the distribution
    of timestamps collected from mouse button up/down, mouse movement
    and keypress/release events. The histograms illustrate the sampling
    – and therefore – quantization of HID devices. Here a few results:
    On the MacBookPro under OS/X 10.4.11, the internal keyboard as well
    as buttons on trackpad and mouse are sampled at roughly 8 msec
    intervals. The sampling frequency of mouse movements however is
    directly related to the display refresh interval: At 60 Hz refresh,
    1000 / 60 = 16.6 msecs. At 75 Hz refresh, 1000 / 75 = 13.333 msecs
    etc. The same machine under Linux has a constant sampling interval
    of 8 msecs for mouse, trackpad and keyboard. Some other machine
    tested under WindowsXP showed a sampling interval of 16 msecs for
    mouse and keyboard.

### Misc other stuff

-   Diederick C. Niehorster contributed a new function `ShrinkMatrix`
    and a speed improvement to the existing function `Magnify2DMatrix`.
    Both functions are used for shrinking or expanding Matlab matrices.

-   The file extensions of all MEX files for Matlab 7.4 (`R2007a`) and
    later on Microsoft Windows have been changed from `.dll` to
    `.mexw32` - the preferred name extension in new Matlab releases.
    This to prevent unneccessary warning messages by the upcoming Matlab
    `R2008b` about deprecated file extensions.
