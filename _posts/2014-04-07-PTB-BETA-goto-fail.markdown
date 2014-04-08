---
layout: post
title: PTB BETA "goto fail" 
categories: news
author: kleinerm
---

"goto fail" is an hommage to Apple's fine software engineering skills and well
known insane attention to detail and perfection.

"goto fail" is the final release of the 3.0.11 series. The next release will
start the 3.0.12 series. It contains the following more notable improvements:

-   Our experimental 10 bit framebuffer support for Linux and OSX for AMD
    Radeon graphics cards is now also available (but untested so far) for
    Radeon HD-5000 and later graphics cards. In the past this was restricted to
    X1000 - HD-3000, now it should covers all currently shipping cards since
    X1000. Along this line goes more fine-grained control of dithering on
    digital display outputs via new parameters to `PsychImaging`'s
    `EnableNative10BitFramebuffer` functions and a new
    `Screen('ConfigureDisplay', 'Dithering')` subfunction; It is important to
    stress here that while 10 bpc output is known to work reasonably well for
    analog VGA connected CRT monitors, 10 bpc output to digital display devices
    will not work on OSX at all, and is unlikely to work over DVI or HDMI on
    Linux. We are currently looking into ways to enable \> 8 bpc support on
    Linux. What you will get if you enable a 10 bpc framebuffer on such a
    display setup is a 10 bpc framebuffer which gets reduced to 8 bpc via
    dithering on the digital video output. Iow., you get simulated 10 bit
    precision via dithering, which may work reasonably well for some stimuli,
    or go horribly wrong for other stimuli.

-   `Screen('Textfont')` now allows atomic setting of font family and and font
    style with a single `Screen('TextFont', window, fontName, fontStyle);` call.
    This to resolve some problems encountered when on tries to use exotic
    fonts.

-   Eyelink bug fixes and improvements contributed by Li Jie of SR-Research and
    me. `Eyelink('ImageTransfer')` should work now, Drawing of targets in
    `PsychEyelinkCallback` should work on less capable graphics hardware, Various
    octave compatibility fixes to SR-Research demos. `Eyelink('Command')`
    robustness improvements against some input.

-   Fix Octave + `PsychDataPixx` long standing compatibility bug for
    timestamping, remove workaround from and cleanup` VBLSyncTest`.

-   Workarounds for nouveau-kms bugs in Linux 3.13/3.14 for the upcoming Ubuntu
    14.04 LTS release. These bugs shouldn't have made it into a release but
    did, because i wasted way too much time fixing Apple's latest screw-ups,
    using up most of the testing time i planned to allocate for Linux + Ubuntu
    14.04 testing. Anyway, this means that the open-source nouveau graphics
    driver for NVidia gpu's will probably be of limited use for vision science
    until we get the required bug fixes into a post-release update. The
    proprietary NVidia driver should work just fine though. I will try to not
    let this happen again. Fixing any problems caused by Apple will have the
    lowest priority from now on.

-   Workarounds for OSX 10.8 dual-display stereo graphics driver bugs and
    various 10.8/10.9 graphics bugs. As it turned out during trying to resolve
    other OSX bugs, at least OSX 10.8 has a hilarious bug when used with two or
    more open fullscreen onscreen windows, e.g., for dual-display stereoscopic
    stimulation in stereomode 10. As soon as a 2nd onscreen window opens on a
    screen, the first previously opened onscreen window will be switched from
    page flipping for stimulus updated (good for timing and performance) to
    desktop composition. This is really bad for performance, visual stimulus
    onset timing and various other things, e.g., 10 bpc framebuffer support. It
    is also almost completely undetectable by software tests, so will have a
    good chance of silently corrupted presentation timing in such scenarios.
    The current PTB will enable a workaround for OSX 10.8 and later which fixed
    the problem at least on the one tested setup with AMD graphics. It is
    unclear if this would introduce any new subtle bugs. According to Apple
    docs it shouldn't, but of course this is Apple talking about its own
    products and we know how well that goes in practice. I also realized when
    testing on my MacBookPro with 10.9.2 and NVidia graphics that 10.9's swap
    scheduling on NVidia gpu's seems to be utterly broken as well. PTB has a
    new visual test script `OSXCompositorIdiocyTest()` which you should run on
    your setups and dual display setups. If that test doesn't show expected
    results then you can consider your setup being mostly unuseable for frame
    accurate visual presentation timing. There are no known workarounds for
    these issues. I don't consider "modern" OSX systems trustworthy for
    frame-accurate visual presentation anymore.

    Bugs not fixed on OSX 10.9: Sometimes you will be left with a blank screen at
    the end of a session after PTB closed its windows. A mouse click, keyboard
    press gives you your GUI back. This bug brought to you by Apple. The only known
    workaround is to use `Screen('Preference','ConserveVRAM', 16384);` which will
    likely reduce performance and visual timing accuracy - or possibly make visual
    timing untrustworthy. I can't test this because my only remaining Mac test
    machine has a NVidia graphics card with broken graphics drivers, so timing on
    my only test machine is always untrustworthy.

    Keyboard queues apparently don't work at all on recent MacBookAir's on at least
    10.9, because Apple completely broke backwards compatibility in the relevant
    bits of the OSX HID subsystem.

-   Ability to disable crashy CVDisplayLink timestamping on OSX:
    `PsychTweak('DisableCVDisplayLink');` now allows to disable CoreVideo
    timestamping as a workaround for timing. If you care about timing you
    should always install the `PsychtoolboxKernelDriver` on OSX. CoreVideo
    timestamping was used as a workaround for setups where this couldn't be
    used, e.g., on all Intel graphics cards. The method has proven unreliable
    due to Apple CoreVideo bugs not fixed since years, but additionally its use
    causes random crashes at the end of experiment sessions on some setups for
    some users.

-   `PsychImaging` - add convenience setup function for dual-display stereo mode 10.
    See `ImagingStereoDemo` for the simplified setup for stereomode 10.

-   `PsychImaging` - Improve 10 bpc framebuffer setup: Do not disable dithering
    on digital output by default, but leave decision to OS, with option to
    override.

-   `Screen('ConfigureDisplay', 'Dithering')` allow low-level control of AMD
    dither control registers.

-   Various help text updates.

-   Various updates to color calibration/color handling routines by David
    Brainard.

-   Misc other fixes.

-   `PsychtoolboxKernelDriver` updates. Different drivers for legacy 10.7 and
    earlier vs. 10.8+. Apple removed the necessary sdk's from its latest XCode
    to build the `PsychtoolboxKernelDriver` for OSX versions earlier than 10.8.
    Therefore we now have a `PsychtoolboxKernelDriver64Bit.kext.zip` for OSX 10.8
    and 10.9, which contains bug fixes and improvements. Then a legacy set of
    64-Bit and 32-Bit kernel drivers for OSX 10.7 and earlier. These legacy
    drivers are no longer maintained and contain known bugs and limitation.

-   The OSX Psychtoolbox now requires Octave 3.8.0 or later. It will not work
    with Octave 3.6 and earlier anymore. It could be made working by manually
    setting a symbolic link in the file system if somebody wants to stick to
    3.6. But upgrading to 3.8 is a good thing, as it now provides a useable GUI
    and other improvements relevant for PTB.
