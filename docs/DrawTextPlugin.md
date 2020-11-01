# [DrawTextPlugin](DrawTextPlugin)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDocumentation](PsychDocumentation)

[DrawTextPlugin](DrawTextPlugin) -- The plugin-based [Screen](Screen)('DrawText') text renderer.  
  
You may have arrived here because [Screen](Screen)() instructed you to go here  
after [Screen](Screen) failed to load the external text renderer plugin.  
  
On all operating systems the functions [Screen](Screen)('DrawText') and  
[Screen](Screen)('TextBounds') try to use an external text rendering plugin for  
drawing and handling of high quality text. This allows for advanced text  
layout and formatting, high-quality anti-aliased rendering of text at  
arbitrary text sizes, support for modern fonts like [TrueType](TrueType), and support  
for drawing of the full international Unicode character set. Its use across  
all operating systems also allows for (more) consistent text appearance on  
different systems. Differences between installed fonts on different operating  
systems can still cause slight differences in text appearance if you don't  
manage this though.  
  
Which text renderer should be used can be set via  
[Screen](Screen)('[Preference](Preference)','TextRenderer', type), and after a first call to  
[Screen](Screen)('DrawText', ...), type = [Screen](Screen)('[Preference](Preference)','TextRenderer') will  
report which 'type' of text renderer is actually used. A 'type' of 1 means  
that the plugin based renderer is used, a 'type' of 0 or -1 would mean the  
use of a less high quality fallback renderer, e.g., because loading the  
text rendering plugin failed.  
  
If use of the drawtext plugin renderer fails then that likely means that  
some required 3rd party library is not installed, or of incompatible version.  
The plugin requires a working installation of the [FreeType](FreeType)-2 and  
[FontConfig](FontConfig) libraries on your operating system, ie., somewhere stored in  
a folder on the system library search path.  
  
How to get those required 3rd party libraries:  
==============================================  
  
# Linux  
  
Nothing to do. On Linux these libraries are part of the default installation  
of any decent GNU/Linux distribution, so there usually isn't any need for  
manual setup work on your part.  
  
# OSX  
  
On OSX with GNU/Octave, these are part of Octave, so you don't need  
to do anything. If you use macOS with Matlab then we recommend installing  
[[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) (help [[GStreamer](GStreamer)][(GStreamer)]((GStreamer))) which also provides multi-media support, as  
[[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) provides the required libraries. Other sources than [[GStreamer](GStreamer)][(GStreamer)]((GStreamer))  
are [HomeBrew](HomeBrew), or [XQuartz](XQuartz) (X11 for macOS). Other sources of this libraries  
may also work, as long as they are findable by the macOS linker, but this  
is only tested with [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) and [HomeBrew](HomeBrew).  
  
Some recent Matlab versions, e.g., R2015a and R2015b will contain an  
outdated and incompatible version of libfreetype.6.dylib which may  
cause problems. If you experience such problems, malfunctions or crashes,  
then delete (or rename) that file, or move it out of the way.  
E.g., for R2015b you'd have to delete or rename this file:  
  
/Applications/MATLAB\_R2015b.app/bin/maci64/libfreetype.6.dylib  
  
# Windows  
  
On MS-Windows with GNU/Octave the libraries are bundled with Octave,  
no need for you to do anything.  
  
On MS-Windows with Matlab you will need to install the [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) multi-  
media framework - see "help [[GStreamer](GStreamer)][(GStreamer)]((GStreamer))" for installation instructions -  
otherwise Psychtoolbox will use the old lower quality GDI text renderer  
instead.  
  
If your version of Matlab bundles an outdated libfreetype.dll, as may be  
the case with at least R2015a and later, you may need to get rid of that as  
well, just as on OSX (see above). The file to delete or rename would likely  
be found in (e.g., for R2015b):  
C:\Program Files\MATLAB\R2015b\bin\win64\ under a name like libfreetype.dll,  
or a similar name containing "freetype".  
  
The first time a script calls a text drawing function after an operating system  
update, or the installation of new text fonts, a long pause of many seconds or  
even minutes may occur, while the so called fontconfig cache gets rebuilt.  
Patience is the key. If this pause happens not only once, but at each invocation  
of text drawing, your system may developed a glitch, as described in [GitHub](GitHub)  
issue \#429 on our issue tracker:  
https://github.com/Psychtoolbox-3/Psychtoolbox-3/issues/429  
  
The solution is to manually delete the fontconfig cache, e.g., if your user  
name would be "paul", you'd likely need to delete the following file:  
"C:\Users\paul\[AppData](AppData)\Local\fontconfig\cache"  
  
Some users find that the location of the cache file could be also in a different  
place, e.g., following the above example for user "paul" it could be under:  
"C:\Users\paul\.cache\fontconfig\" so files in that folder would need to be  
deleted.  
  
More background info about Psychtoolbox's standard text renderer:  
=================================================================  
  
On OSX one can still select Apple's [CoreText](CoreText) text renderer via the command  
[Screen](Screen)('[Preference](Preference)','TextRenderer', 0); although Apples text renderer is  
inferior in essentially any aspect. Apples [CoreText](CoreText) renderer would also  
get automatically selected if the plugin renderer would not work for some  
reason. On MS-Windows one can still select the legacy MS-Windows GDI text  
renderer via [Screen](Screen)('[Preference](Preference)','TextRenderer', 0). This renderer provides  
lower quality anti-aliasing, less accurate computation of text bounding boxes  
via [Screen](Screen)('TextBounds'), and less accurate text positioning, as well as a  
lower text drawing speed. Additionally this legacy GDI text renderer has  
problems on [HiDPI](HiDPI) "Retina" displays and can misrender text in both size and  
appearance.  
  
The text renderer plugin implements a high-speed renderer based on a  
combination of multiple free software libraries for text rendering and  
text handling:  
  
\* OGLFT (http://oglft.sourceforge.net/) the [OpenGL](OpenGL)-[FreeType](FreeType) library.  
\* The [FreeType](FreeType)-2 (http://freetype.sourceforge.net/) library.  
\* The [FontConfig](FontConfig) (http://www.fontconfig.org) library.  
  
The [FontConfig](FontConfig) library is used to find the optimal font and font  
settings, given a specific font specification by your user code, a process  
known as "font matching". [FontConfig](FontConfig) internally uses the [FreeType](FreeType)-2  
library to handle the font files on your system and to gather all needed  
information for the matching process.  
  
After a font and settings have been selected, [FreeType](FreeType)-2 is used to load  
the font and convert it into high-quality character glyphs, then the  
OGLFT library is used to convert these glyphs into a format optimized for  
fast drawing with [OpenGL](OpenGL). OGLFT also performs caching of glyphs, text  
layout, measurement of text dimensions and bounding boxes and the actual  
drawing of the text.  
  
Our actual plugin coordinates all these operations and communicates with  
[Screen](Screen)().  
  
The source code of the plugin can be found in the Psychtoolbox source  
tree under [PsychSourceGL](PsychSourceGL)/Cohorts/[FTGLTextRenderer](FTGLTextRenderer)/  
  
The plugins themselves are stored in the  
Psychtoolbox/[PsychBasic](PsychBasic)/[PsychPlugins](PsychPlugins) folder of your Psychtoolbox  
installation. This is where [Screen](Screen)() expects to find the plugins for  
dynamic loading.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDocumentation/DrawTextPlugin.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDocumentation/DrawTextPlugin.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDocumentation/DrawTextPlugin.m</code>
</div>

