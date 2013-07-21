---
layout: page
title: Graphics hardware requirements and recommendations
category: getting-started
---

#### Contents

-  TOC be here
{:toc #toc}
{::options auto_ids="true" toc_levels="1..3"/}

### General recommendations

The summary here is just for your reference, so you can get a feeling on
what to expect with specific hardware. If you buy new systems, go for
the latest generation hardware of NVidia or ATI. Currently, stuff that
claims to support `Direct3D-10`, `OpenGL-3` or `ShaderModel 4`, does
support all functionality of Psychtoolbox in the most optimal way. All
cards of the NVidia GeForce 8 series and later (e.g., 8600, 8800, 9600,
9800, GTX 280 etc.), as well as all cards of the ATI Radeon HD series
and later (HD 2400, 2600, 3000 series, 4000 series etc.) and their
corresponding counterparts from the NVidia Quadro series and ATI FireGL
/ FirePro line of cards are technically state of the art and
Psychtoolbox can take full advantage of their useful new features.
Expensive high-end models differ from cheap low-end models almost only
in raw performace, i.e., drawing speed, not in functionality, unless
stated otherwise below.

Mobile graphics chips (in Laptops) are almost always slower than
discrete graphics cards in desktop computers. This is a design tradeoff
to accomodate the stricter requirements for cooling, space and power
consumption in portable computers.

So called "integrated graphics chips" (aka "onboard graphics chips" or
"chipset graphics" or IGPs) are usually cheaper and consume less power
and space in a computer, which is why they are often found in Laptop
computers and cheap desktops. Their disadvantage is usually much lower
performance. The latest onboard parts from NVidia and ATI provide the
same or almost the same features as dedicated graphics cards, so there
isn't a limitation in functionality per se. The raw processing power is
lower though, because these chips often don't have dedicated fast VRAM
memory, but share slow RAM system memory with all other parts of your
computer. They usually also have less processing units (so called shader
processors or stream processors). All in all they may be sufficient for
many not too demanding tasks. Very compute intense, image processing
intense or memory intense tasks may not be feasible in practice because
although they are doable in principle with the given feature set, the
raw performance is just pathetically insufficient for research grade
realtime behaviour. They are usually perfectly sufficient for designing
and debugging your experiment scripts, where absolute realtime
performance doesn't matter.

### Tested graphics hardware + operating system configurations

The following combinations of graphics hardware and operating systems
are used by the developers for development of PTB-3's Screen function
and therefore tested and known to work well within their respective
feature set. This doesn't exclude other similar or more advanced system
configurations which likely will work equally well or maybe even better.
It just happens to be the equipment that is accessible to us for
development and testing. As a rule of thumb, a specific feature of a
specific piece of graphics hardware that works well on MS-Windows will
likely work equally well on GNU/Linux and vice versa due to the unified
drivers used for these operating systems (drivers for Windows and Linux
by ATI and NVidia are derived from the same code base). This is not
necessarily true for Win/Linux vs. Mac OS X, because the OpenGL drivers
for OS X are developed by different development teams from a different
code base - Apple imposes a much stricter control over their
implementation of OpenGL, with different priorities wrt. feature set.
This means that the same gfx hardware may expose different
functionality, performance, limitations and bugs on OS X vs. Win/Linux
due to fundamental driver differences.

#### The following setups are used for development and testing of PTB, so they get tested for compatibility at least once for each beta release

-   ATI Radeon X1600 mobile chip in a Apple Intel MacBook-Pro, currently
    running OS X 10.4.11. Dual display support tested. This is the
    current main development system for PTB, so it gets tested on a
    daily basis and for each beta release. The same system gets tested
    for each beta release under Linux Ubuntu 7.1.
-   NVidia GeForce 8800 Ultra in a Apple Intel Mac Pro, currently
    running OS X 10.5.6. This is one of the main testing and productive
    systems.
-   NVidia GeforceFX-5200 desktop graphics in a single processor
    PowerMac-G5, under OS X 10.4.11. This is one of the main testing
    systems.
-   NVidia GeForce 7800 Ultra in a Dell PC running Windows XP SP-2/3.
    This is one of the main testing systems.
-   NVidia Geforce2Go/GeforceMX mobile graphics chip: Regularly tested
    under Windows 2000 and GNU/Linux in a Dell Inspiron 8000 laptop.
    Dual display support tested under Windows.

#### These cards get tested infrequently, i.e., if significant changes inside Screen() indicate need for testing and if the systems are available for testing:

-   NVidia GeForce 8800 Ultra under Windows XP.
-   Quadro FX 4500 under Windows XP. Dual display support tested.
-   NVidia QuadroFX-5800 under Ubuntu Linux 8.1.
-   Radeon HD 2400 under OS X 10.4.11 in a Intel Mac.
-   Intel GMA 950 of Apple MacBook. Tested once under OS X 10.4.
-   Nvidia Geforce 6800 mobile chip in a high end Dell Laptop under
    Windows XP and GNU/Linux tested once. Dual display support tested.
-   Intel GMA 945 onboard GPU: Tested exactly once in single-display
    mode on a Dell PC under Windows XP, also tested once under
    GNU/Linux. A similar class would be the ATI Rage 128 / Pro in very
    old Apple Macintosh computers.
-   NVidia Geforce4 desktop graphics chip tested once under GNU/Linux.
    Geforce3 series hardware should behave the same. Also tested once in
    a standard Intel PC under GNU/Linux and Windows XP. Dual display
    support also tested.
-   ATI Radeon 9600 under Intel laptop with Windows-XP, tested once.

### Rough lineup of different generations of graphics hardware with their respective features

#### Basic OpenGL 1.2 compliant hardware

These provide the minimum amount of functionality for use with
Psychtoolbox:

-   Frame accurate stimulus onset timing, animation timing and high
    precision stimulus onset timestamping generally works well, as long
    as you don't try to overtax the hardware.
-   Some of these cards do provide full dual-display output support,
    e.g., for binocular stimulation.
-   All basic 2D and 3D drawing functions work with useable performance
    for simple tasks.
-   Limitations: Drawing of image textures works, but drawing speed may
    be rather low and use of texture memory inefficient (so you can use
    less textures or offscreen windows simultaneously). Drawing to and
    handling of offscreen windows is rather slow and inefficient.
    Precision for scrolling of textures (e.g., for drifting gratings)
    may be rather low. Image anti-aliasing is functionally limited to
    points and lines, slow and of low quality.
-   Psychtoolbox imaging pipeline and support for procedural textures
    completely unsupported.

The limitations are due to lack of programmable shader support, lack of
support for framebuffer objects and lack of support for rectangle
textures. Typical examples of such hardware are: All ATI Rage 128 (Pro)
and older, all Intel chips older than the GMA-950, all NVidia chips
before GeForce-2.

#### Hardware with additional support for rectangle textures

-   Improvements: These support efficient storage and fast drawing of
    textures and offscreen windows, incremental speed and quality
    improvements in anti-aliasing and general performance.
-   Remaining limitations: No support for imaging pipeline, no support
    for procedural textures, rather slow drawing into offscreen windows.
    Only point and line anti-aliasing.

Typical examples are all NVidia GeForce hardware from GeForce-2 series
upto GeForce-4 series, all ATI Radeon hardware upto Radeon 9200.

#### Hardware with support for framebuffer objects and programmable shaders (Shader model 2.0)

Improvements:

-   Fast, efficient support for offscreen windows: Efficient use of
    memory, fast drawing of and into offscreen windows and textures.
-   Basic support for the imaging pipeline, e.g., geometric display
    undistortion, and almost all stereo display modes (dual display,
    very flexible and high quality anaglyph stereo, interlaced stereo).
-   Support for simple procedural texture stimuli via GLSL shaders.
-   CLUT palette animation and image data conversion via simple
    mathematical functions or lookup tables. Basic GLSL Vertex and Pixel
    shader support (Shader model 2.0).
-   High quality multisample anti-aliasing on all non-Intel graphics
    chips. Frame-Sequential stereo under OS X on all graphics cards
    except Intel chips.

Typical examples are all NVidia GeForceFX cards (5200, 5800 etc.) and
all Radeon 9600, 9700, 9800, X400, X600, X800 cards. Intel GMA 950 and
X3000 series.

#### Hardware with support for Shader model 3.0 shaders and limited support for floating point textures and framebuffer objects

-   Improved support for imaging pipeline and procedural textures due to
    higher precision and more complex shader programs.
-   Provide additional support for complex image processing operations,
    e.g., 2D convolution, local and neighborhood operations on images,
    thresholding and classification. (Shader model 3.0).
-   Advanced support for Vertex and Pixel shaders for 3D stimuli.
-   Support for floating point framebuffers and floating point blending
    operations, e.g., high dynamic range rendering and processing,
    precise execution of iterative image processing algorithms, computer
    vision and scientific stream computing algorithms.
-   This is what you minimally want if you need high bit precision color
    or luminance displays, e.g. in conjunction with devices like video
    attenuators, or Bits++ and similar high precision display devices.
-   Simple and fast creation of complex stimuli like procedural gabor
    patches, sine gratings, complex composited stimuli via alpha
    blending.
-   Remaining limitations: Stimuli are limited in precision to 16 bit
    floating point (effective 10-11 bits of linear precision) if you
    want to employ alpha-blending for stimulus creation. Drawing of high
    precision 32 bit floating point (effective 23 bits of linear
    precision) textures and offscreen windows is possible, but limited
    in speed.

Typical examples are all Radeon X1000 series GPUs (e.g., X1400, X1600,
X1950) and all NVidia GeForce 6 and 7 series GPUs (e.g., GeForce 6800,
GeForce 7800 etc.).

The Intel X3100 series chips and later (e.g., some Apple MacBooks) and
its siblings are special in the sense that feature-wise they are
Direct3D 10 cards with support for Shader model version 4 - they can do
most of what the most recent state of the art cards of NVidia and ATI
can do. However, they lack any support for frame-sequential stereo,
anti-aliasing and high precision HDR framebuffers and due to lack of
dedicated fast VRAM memory, they only have a low computational
performance. So although theoretically "state of the art" cards, they
are too restricted and weak for the typical applications of such state
of the art cards.

#### State of the art hardware with support for Direct3D 10, ShaderModel 4.0 and fast full precision floating point textures and framebuffers

These cards remove the remaining limitations of the previous generation
hardware mentioned above. They can store and handle stimuli (and any
kind of drawing or image processing operations on that stimuli) at full
speed without any restrictions at full 32 bit floating point precision,
that is with at least 23 bits of effective linear precision. Shading
operations, e.g., for post processing, or procedural drawing of complex
stimuli can be even more complex.

This is the hardware you want for simple, efficient and fast generation
of high precision contrast or color stimuli, complex compositing and
post-processing of stimuli and for display on high precision devices
like 10 bit framebuffers, 12/13 bit video attenuators or 14-16 bit
devices like Bits++, or high dynamic range displays.

These graphics cards are also fully equipped for future GPU stream
computing applications - They are capable of supporting some planned
exciting future PTB features which wouldn't be possible with previous
generation GPUs.

Typical examples are all NVidia GPUs of type GeForce 8000 and later
(e.g., 8200, 8400, 8600, 8800, 9200, 9600, 9800, GTX-2xx series and
later) and all Radeon HD GPUs (HD 2000 / 3000 / 4000 series and later).

### Choice of operating system and graphics card vendor

For most visual stimulation applications, choice of GPU vendor and
operating system won't be crucial. The different systems do however have
some specific strength and weaknesses that may be important for some
selected applications. This section summarizes a few of these
considerations for different applications:

#### Relative strengths and weaknesses of Apple hardware + OS X

-   Choice of graphics hardware options for Apple hardware is rather
    limited and Apple exerts rather strong control over both hardware
    components and selection of features for the OS X OpenGL graphics
    system implementation. This allows Apple for good integration and
    performance tuning, as well as testing of the limited set of
    available graphics hardware with the available implementations of
    OS X. Our past experience is that this leads to rather high quality
    drivers with relatively few bugs and surprises (although they still
    have their fair share of bugs and we may have just been lucky so
    far) and a generally consistent feature set across different models
    of Apple hardware. Reliability of OS X graphics is high (compared to
    MS-Windows) and timing precision for visual stimulation with full
    screen displays (as typical for cognitive science experiments) is so
    far excellent.
-   Apple provides excellent graphics driver support for its mobile
    computers (MacBook, MacBook Pro), an area where users of Laptops
    under MS-Windows are accustomed to miserable vendor support and lots
    of pain.
-   One downside is higher costs for graphics hardware compared to plain
    PC hardware, as well as limited choice.
-   Apple most of the time doesn't provide the most high-end GPUs as
    options, so if you'd need the last bit of performance you'd likely
    find better options for Windows or Linux on standard PC's.
-   In some specialized areas, OS X graphics system lags behind the
    corresponding systems on Windows and Linux, sometimes by up to 1 or
    2 years. In very few other areas it leads. Weak points of current
    OS X:

    -   Dual display support is implemented in a much more inefficient
        way than on Windows or Linux. Therefore Psychtoolbox needs to
        work much harder "behind the scenes" to provide dual display
        stereo functionality, likely at a significant performance
        penalty when fast stimulus redraw and animation is needed for
        dual display stereo. For reasons beyond our understanding,
        displays on a dual display setup are not synchronized on OS X
        wrt. their video refresh cycles. This can cause severe flicker
        and tearing artifacts or limited synchrony in stimulus onset
        timing for dual display stereo stimulation, at least when NVidia
        GPUs are used. For selected ATI GPUs we provide a special
        workaround to solve this problem (type
        `help PsychtoolboxKernelDriver` in your local PTB installation
        for more information), but it would be much more admirable and
        pain free if Apple would take care of this problem. MS-Windows
        users can take well working and efficient dual display stereo
        stimulation for granted. *In addition, OS X 10.5.3 to 10.5.6
        have serious bugs in the drivers for NVidia GeForce 8000
        hardware, which makes these setups unuseable for dual display
        fullscreen stereo!*
    -   In extension, OS X provides no support for genlock or framelock
        hardware, making reliable synchronization of more than two
        displays almost impossible. On Windows and Linux, a wide range
        of technical options exists for such special demands.
    -   When drawing high precision stimuli (by use of floating point
        framebuffers), OS X has some low level technical limitations
        compared to MS-Windows and Linux: Again, Psychtoolbox implements
        some special workarounds to eliminate the problem for you, but
        again at a performance penalty in drawing.
    -   Stimulus timing in windowed mode is unreliable to the point of
        being unuseable on OS X. This however is not a major limitation
        as experiment stimuli are usually not displayed in windowed
        mode.

-   A strong point of OS X is frame-sequential stereo presentation: This
    is supported on all ATI and NVidia GPUs under OS X out of the box.
    If you want similar functionality on Windows or Linux, you'll need
    to buy expensive professional graphics cards like NVidia Quadro, or
    ATI FireGL / FirePro for the same functionality. *The exception is
    OS X 10.5.6, which has serious bugs in the drivers for NVidia
    GeForce 8000 hardware, which makes these setups unuseable for
    frame-sequential stereo!*

#### Relative strength and weakness of standard PC hardware under GNU/Linux and MS-Windows

In terms of graphics capabilities and support, Linux and Windows are
usually on par with each other, due to the fact that the Windows and
Linux graphics drivers are usually written by the same companies and
therefore often share large amounts of internal code across these
operating systems. Choice of graphics hardware is the same for Linux and
Windows as well, as these operating systems run on the same set of PC
hardware (including Apple Macintosh hardware). Therefore actual support
for graphics features and graphics performance is no discriminating
factor when choosing between Windows or Linux on PC hardware. There are
other non-graphics related reasons to choose one OS over the other
though.

Both systems provide generally feature rich, high performance, mostly
reliable graphics drivers and GPUs. Both systems are strong in dual
display support and for dual display stereo stimulation (compared to
OS X shortcomings) and expensive for frame-sequential stereo stimulation
(requiring high priced pro hardware, as opposed to OS X out of the box
support on cheap hardware). Boths systems provide more advanced, faster
support for high precision framebuffers than OS X. Both systems provide
more options for special purpose hardware, e.g., genlocking /
framelocking of many displays and support the latest GPU features ahead
of OS X. This comes at the price of less consistency across different PC
hardware configurations and more work/trouble for users in setting up
and maintaining their graphics drivers. Driver support for Laptop GPUs
under Linux often requires tinkering, but is plenty and good, once one
gets used to it. Driver support for Laptop GPUs under Windows varies
from vendor to vendor but is quite often a complete disaster.

Technically, in our experience, Linux is much more advanced, feature
rich, robust and reliable in its operation than MS-Windows. It provides
much more robust and precise timing behaviour, higher overall
performance and it is much more flexible and customizable for
applications with special needs. Unfortunately, most of our userbase
consists of Windows users and the Linux userbase is very small.
Therefore we can't spend as many ressources on supporting and developing
the Linux Psychtoolbox as we spend on maintaining the Windows
Psychtoolbox for a larger userbase. This leads to the unfortunate
situation that the Linux PTB lacks a few useful features wrt. the
Windows Psychtoolbox, e.g., movie playback support, and that getting
started with the Linux PTB likely involves a much steeper learning curve
in the beginning. Therefore, we can not unconditionally recommend the
current Linux Psychtoolbox over the Windows Psychtoolbox to beginners,
but only to advanced power users, although this means that the majority
of users will be locked to a technically far inferior operating system
with many shortcomings.

Choice of ATI hardware vs. NVidia hardware
------------------------------------------

...to be written...

**You could stop reading here and be reasonably well informed, but if you are
really curious, feel free to continue reading about the nitty gritty technical
details ;-)**

### Graphics hardware requirements for specific PTB features

OpenGL graphics hardware exposes its functionality via so called OpenGL
extensions. Each extension defines a specific subset of functionality
supported by the hardware. Specific advanced features of PTB-3 require
your graphics hardware to support specific sets of OpenGL extensions. If
you try to use an advanced PTB feature, PTB will probe your hardware for
support of the required extension. If the extension is unsupported, PTB
will either refuse use of an advanced feature or it will enable internal
fallback implementations that do what you want, but at a much lower
performance or precision and much higher resource requirements than if
your hardware would support the extension. A list of all existing OpenGL
extensions, including their full in-depth technical specification, can
be found at [the official OpenGL extension
registry](http://www.opengl.org/registry).

Different models of a specific generation of graphics hardware usually
share support for a common set of extensions, but they differ in the
precision, performance or efficiency with which features are supported
as well as in the set of constraints that need to be fullfilled in order
for the hardware efficiently to support a feature. The following
websites list the specific set of extensions that are supported for
specific models of graphics hardware for specific driver versions or
operating system releases. They also list many interesting properties
and limitations of these graphics cards. You will notice that there are
separate websites for Windows/Linux and OS X and that if you compare the
resource limits, capabilities and feature sets of the same models of
graphics hardware between Win/Lin and OS X you'll sometimes find
significant differences. Given that the hardware is the same, these
differences are imposed by the different design and implementation of
the graphics drivers and OpenGL subsystems of Windows/Linux versus OS X.

-   [Delphi3D - Support on Microsoft Windows, sorted by vendor, model
    and driver release](http://www.delphi3d.net/hardware/index.php)
-   [GLInfo - Support on MacOS X, sorted by OS release, PowerPC vs.
    IntelMac and
    model](http://homepage.mac.com/arekkusu/bugs/GLInfo.html)
-   [Wikipedia has nicely written overview articles about different
    graphics cards and how they differ](http://www.wikipedia.org)
-   [Tom's hardware has some overview about the best graphics cards for
    a given range of money you'd like to spend. (Caution: Check how
    recent the article is, could become
    outdated.)](http://www.tomshardware.com/reviews/graphics-cards,1942.html)
-   [And an interface for quick comparison of prices. (Caution: Could be
    biased, use common
    sense!)](http://stores.tomshardware.com/search_attrib.php/page_id=5)

If you want to buy a graphics card which is an optimal tradeoff between
required features for your project and cost, you'll have to match the
listed requirements of PTB against the features in those databases.
PTB's Screen command outputs a list of all OpenGL extensions supported
by your hardware + operating system + driver at startup ("OpenGL
extensions are: ...") unless you suppress it. The websites above also
provide a tool called GLInfo which probes your hardware and outputs a
full listing of all tested properties if you need reliable information
about your hardware.

Standard `Screen` subfunctions and their requirements
-----------------------------------------------------

-   Support for fast, efficient textures and moderately fast Offscreen
    windows: `GL_ARB_texture_rectangle` or `GL_EXT_texture_rectangle` or
    `GL_NV_texture_rectangle`.

    -   Everything on IntelMacs, everything on PowerMacs except ATI Rage,
        Rage 128 or Rage Pro. NVidia Geforce2 and later on Windows/Linux.
        Intel GMA 945.

-   Support for fast drawing of 3D geometry in MOGL:
    `GL_EXT_draw_range_elements`.

    -   All OS X hardware. Most PC hardware.

-   Support for `Screen('Flip', ..., clearmode)` command with
    `clearmode=1` (don't clear after Flip): At least one AUX buffer for
    mono displays, two AUX buffers for stereo displays.

-   Well supported on OS X on PowerPC, faulty on OS
    X IntelMac, unsupported on most Windows and Linux systems, especially with ATI hardware. Alternatively if your hardware support the PTB imaging pipeline, you'll get this feature very efficiently for free.



-   Support for different stereo display methods (`stereomode` flag in
    `Screen('OpenWindow', ...)`:

    -   Frame sequential stereo for shutter glasses: Blue line syncing method
        supported on all OS X hardware except ATI Rage and Intel chips. On
        Windows, only expensive professional line hardware is supported (ATI
        FireGL series and NVidia Quadro series). Linux can be extended in
        various ways to support commodity hardware in addition to the
        professional line hardware, and to support very special setups, e.g.,
        high performance render clusters.

    -   Vertical split screen stereo (modes 2 and 3): Supported on OS X PowerPC
        on all hardware. All other platforms need support for the PTB imaging
        pipeline for this to work.

    -   Dualview stereo for free fusion, cross fusion, haploscopes and dual
        display systems: Works on all hardware and OS, either via cheap display
        splitter hardware [like the Matrox
        DualHead2Go](http://www.matrox.com/graphics) or via dual display (dual
        head) graphics cards.

    -   Anaglyph stereo: Basic support (without automatic gain correction,
        desaturation or color to luminance conversion) works on all systems.
        Advanced anaglyph stereo with automatic color to luminance conversion,
        desaturation and gain correction is only supported on hardware that
        supports the PTB imaging pipeline.

-   Other algorithms: Need basic support for PTB imaging pipeline.

-   Support for full scene anti-aliasing (`multisample` parameter of
    `Screen('OpenWindow', ...)`): Needs `GL_ARB_multisample` with at
    least 1 multisample buffer (See constants `Max Sample Buffers` and
    `Max Samples`, bigger is better.

    -   Supported on most ATI and NVidia hardware, not supported on Intel
        onboard graphics, e.g., GMA 950 of MacMini, IntelMac or MacBook.

-   Support for fast Offscreen windows: Needs support for basic imaging
    pipeline.
-   Support for fast geometric display distortion correction, display
    hotspotting correction, color correction, clut animation: Needs
    support for basic imaging pipeline.

Psychtoolbox imaging pipeline:
------------------------------

The Psychtoolbox imaging pipeline is a built-in framework for fast image
processing on the graphics hardware, currently in beta stage. It allows
to perform common image processing operations on image stimuli
(represented as Psychtoolbox textures), to customize and extend the
behavior of specific `Screen` drawing commands and to provide a set of
fully automatic post processing operations on your final visual stimuli
which may be useful for some more advanced applications. The
infrastructure is integrated into PTB, but the specific operations are
implemented as shader plugins, written in the OpenGL shading language
(GLSL) and executed on the graphics processor itself. The imaging
pipeline requires recent hardware for basic operation and mid-level to
high-end hardware for the more advanced features.

Basic imaging pipeline support
------------------------------

Provides the following features:

-   Fast efficient support for Offscreen windows.
-   Fast support for "don't clear after Flip" mode (`dontclear=1`) for
    the `Screen('Flip')` command, allows for incremental drawing of
    stimuli.
-   Automatic drawing of blue sync lines for frame sequential stereo on
    consumer hardware.
-   Fast support for vertical split screen stereo modes (`stereomode` `2` and `3`).
-   Flexible high quality Anaglyph stereo modes with automatic
    conversion of color stimuli into grayscale images, online color gain
    correction, desaturation and alternate anaglyph implementations.
-   New stereo modes, e.g., interlaced stereo and vertically interlaced
    stereo for free viewing setups with lenticular lens systems.
-   Fast remapping of pixel values via lookup tables, e.g., for palette
    animation.
-   Geometric undistortion and alignment for non-rectilinear displays.
-   Correction of inhomogenities in display intensity via application of
    per pixel gain values. (On your request)

Minimum requirement for 2D drawing is the support for the following
`OpenGL` extensions: `GL_EXT_framebuffer_object`, `GL_ARB_multitexture`,
`GL_ARB_shading_language_100`, `GL_ARB_shader_objects`,
`GL_ARB_vertex_shader`, `GL_ARB_fragment_shader`. The following cards
and later models are known to fully support these extensions: ATI Radeon
9600, NVidia GeforceFX-5200, Intel GMA-950 onboard chip of Intel based
MacMinis and MacBooks under OS X.

For 3D graphics via MOGL or OpenGL one needs these additional
extensions: `GL_ARB_depth_texture` for depth buffer support and
`GL_EXT_packed_depth_stencil` for stencil buffer support on some
systems. Stencil buffers are unsupported on all `PowerPC` hardware (an
OS limitation not a hardware limitation), unless you use OS X 10.5
"Leopard" and later.

High dynamic range support
--------------------------

This allows for drawing, processing and representation of images with
floating point precision. Color values can exceed the normal 0-255
integer range of standard 8bpc framebuffers and one can handle images
and colors with negative color components. This is useful for efficient
creation of specific stimuli, e.g., fields of overlapping gabor patches
and special blending operations. The final stimulus image can get
automatically converted into a format suitable for special high
precision display hardware, e.g., CRS Bits++, video attenuators, high
dynamic range display devices.

Required extensions: A subset of `GL_ARB_float_pixels`,
`GL_APPLE_float_pixels`, `GL_ATI_float_pixels`, `GL_NV_float_pixels`,
`GL_ATI_texture_float`, `GL_ARB_texture_float`, `GL_NV_texture_float`.

At least the following graphics cards should support this according to
their specification: NVidia Geforce-6000 series and ATI Radeon X800
series. The following cards have been successfully tested for support:
ATI X1600 and NVidia Geforce 7800. All later cards will support this as
well. The NVidia GeforceFX 5200 should support it, but malfunctioned on
OS X PowerPC during tests. This may be different on OS X 10.5 Leopard,
but is untested so far. The Intel chips do not support these functions.

Advanced support for imaging pipeline
-------------------------------------

This allows for more complex shaders and therefore for additional
functionality, especially in the area of general purpose image
processing:

-   Support for display devices with complex output processing
    requirements: e.g., BrightSide Technology High Dynamic Range
    display.
-   Support for 2D convolution, 2D FFT and other standard image
    processing operations.
-   Support for iterative algorithms and machine vision algorithms.

The graphics hardware needs to be Shader model 3.0 (aka DirectX 9.0c,
aka Windows Vista Premium ready) compliant.

Known cards that should work well: (Follow the links for detailed infos
about the different models)

-   [NVidia Geforce 6000 and 7000 series (e.g., Geforce
    6800)](http://en.wikipedia.org/wiki/GeForce_6000), NVidia Geforce
    8000 series and later recommended, Quadro FX 4500. PTB is tested on
    Geforce 7800 GTX.
-   [ATI Radeon X1300 and
    later](http://en.wikipedia.org/wiki/Radeon_R520). PTB is tested on
    the Mobility Radeon X1600 of the Apple MacBook-Pro.

Good luck in choosing a suitable card.
