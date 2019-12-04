# [Screen('OpenWindow')](Screen-OpenWindow) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

[windowPtr,rect]=Screen('OpenWindow',windowPtrOrScreenNumber [,color] [,rect][,pixelSize][,numberOfBuffers][,stereomode][,multisample][,imagingmode][,specialFlags][,clientRect][,fbOverrideRect][,vrrParams=[]]);

Open an onscreen window. Specify a screen by a windowPtr or a screenNumber (0 is  
the main screen, with menu bar). "color" is the clut index (scalar or [r g b]  
triplet or [r g b a] quadruple) that you want to poke into each pixel; default  
color is white.  
  
If supplied, "rect" must contain at least one pixel. "rect" is in screen  
coordinates (origin at upper left), and defaults to the whole screen. (In all  
cases, subsequent references to this new window will use its coordinates: origin  
at its upper left.). Please note that while providing a "rect" parameter to open  
a normal window instead of a fullscreen window is convenient for debugging,  
drawing performance, stimulus onset timing and onset timestamping may be  
impaired, so be careful.  
  
"pixelSize" sets the depth (in bits) of each pixel; default is to leave depth  
unchanged. You should usually not specify such a bit depth, the system knows  
what it is doing.  
  
"numberOfBuffers" is the number of buffers to use. Setting anything else than 2  
will be only useful for development/debugging of PTB itself but will mess up any  
real experiment.  
  
"stereomode" Type of stereo display algorithm to use: 0 (default) means:  
Monoscopic viewing:  
1 means: Stereo output via [OpenGL](OpenGL) native quad-buffered stereo on any stereo  
hardware supports this.  
2 means: Left view compressed into top half, right view into bottom half of  
window for frame-doubling stereo.  
3 means left view compressed into bottom half, right view compressed into top  
half for frame-doubling stereo.  
4 and 5 allow split screen stereo display where the left view is shown in left  
half, the right view is shown in the right half of the display, e.g., for  
mirrorscope/haploscope setups, or dual-display stereo devices.  
A value of 5 does the opposite (cross-fusion), exchanges left and right eye  
view.  
Values of 6,7,8 and 9 enable Anaglyph stereo rendering of types left=Red,  
right=Green, vice versa and left=Red, right=Blue and vice versa.  
A value of 10 enables multi-window stereo: Open one window for left eye view,  
one for right eye view, treat both of them as one single stereo window.  
A value of 11 enables our own frame-sequential stereo mode for driving shutter  
glasses and similar devices on display hardware and operating systems which do  
not support frame-sequential stereo natively (like mode 1).  
A value of 12 enables stereo processing within separate streams of the imaging  
pipeline, followed by some custom display method for the end results of that  
separate stream processing. This is usually used for stereo output to special  
display devices like Virtual reality head sets, instead of output to a normal  
onscreen window or display monitor.  
See [StereoDemo](StereoDemo).m for examples of usage of the different stereo modes. See  
[ImagingStereoDemo](ImagingStereoDemo).m for more advanced usage on modern hardware.  
  
"multisample" This parameter, if provided and set to a value greater than zero,  
enables automatic hardware anti-aliasing of the display: For each pixel,  
'multisample' color samples are computed and combined into a single output pixel  
color. Higher numbers provide better quality but consume more video memory and  
lead to a reduction in framerate due to the higher computational demand. The  
maximum number of samples is hardware dependent. Psychtoolbox will silently  
clamp the number to the maximum supported by your hardware if you ask for too  
much. On very old hardware, the value will be ignored. Read 'help AntiAliasing'  
for more in-depth information about multi-sampling.  
  
"imagingmode" This optional parameter enables PTB's internal image processing  
pipeline. The pipeline is off by default. Read 'help PsychImaging' for  
information about typical use and benefits of this feature.  
  
"specialFlags" This optional parameter enables some special window behaviours if  
the sum of certain flags is passed. A currently supported flag is the symbolic  
constant kPsychGUIWindow. It enables windows to behave more like regular GUI  
windows on your system. See 'help kPsychGUIWindow' for more info. The flag  
kPsychGUIWindowWMPositioned additionally leaves initial positioning of the GUI  
window to the window manager.  
  
"clientRect" This optional parameter allows to define a size of the onscreen  
windows drawing area that is different from the actual size of the windows  
framebuffer. If set, then the imaging pipeline is started and a virtual  
framebuffer of the size of "clientRect" is created. Your code will draw into  
that framebuffer. At display time, the content of this virtual framebuffer will  
get scaled to the size of the true onscreen window, a process known as  
panel-scaling or panel-fitting. This allows to decouple the size of a stimulus  
as drawn by your code from the actual resolution of the display device. The  
feature is mostly useful if you need to run the same presentation code on  
different setups with different native resolutions. See the 'help PsychImaging'  
section about 'UsePanelFitter' for more info.  
  
"fbOverrideRect" This optional parameter allows to override the true size of the  
onscreen windows framebuffer for the purpose of image processing operations with  
the imaging pipeline. While the true size of the windows framebuffer is defined  
by the standard "rect" parameter, internal processing will instead use the given  
override size. This usually only makes sense in combination with special output  
devices that live outside the regular windowing system of your computer, e.g.,  
special Virtual reality displays.  
  
"vrrParams" This optional parameter allows to control the method for scheduling  
visual stimulus onset. By default, if the parameter is omitted, or set to 0,  
standard presentation with fixed refresh rate is used. Visual stimuli will  
present at the start of a new video refresh cycle of fixed duration, ie. timing  
is quantized to multiples of refresh duration.  
Non-zero values ask to use a more fine-grained technique to schedule stimulus  
onset, than the classic fixed refresh interval scheduling. This may allow to  
more often achieve a visual stimulus onset exactly at the 'when' onset time  
asked for in [Screen](Screen)('[Flip](Flip)'), instead of only at the closest frame boundary of a  
fixed duration frame. This needs a suitable operating-system, display driver and  
graphics hardware, as well as a suitable display device that can run at a  
non-fixed refresh rate. On unsuitable system hardware+software configurations  
selecting a mode other than zero will abort 'OpenWindow'. Fine-grained stimulus  
onset scheduling aka non-zero mode is currently only supported on Linux with  
some hardware.  
Settings other than 0 / default may require passing a vector with parameters  
instead of just a mode selection scalar. E.g., instead of vrrParams = mode, it  
could be vrrParams = [mode, minDuration, maxDuration] with minDuration and  
maxDuration defining the minimum and maximum duration of a video refresh cycle  
that the given display is capable off in VRR mode, e.g., in situations where  
this can't be auto-detected reliably by [Screen](Screen)().  
If set to 1, Psychtoolbox will auto-select the strategy based on the given setup  
to provide more fine-grained visual stimulus onset timing. See 'help VRRSupport'  
for hardware and software requirements and setup instructions for VRR on your  
system.  
If set to 2, Psychtoolbox will use VRR technology in the straightforward naive  
way, efficient, but of limited timing precision and stability: If a 'when'  
target time is given in [Screen](Screen)('[Flip](Flip)', ...), [Screen](Screen) will simply wait until that  
time and then submit the flip request to hardware. Immediate flips will be  
submitted to hardware immediately. Special constraints of the specific operating  
system, display driver, graphics card or display model are not taken into  
account, jitter in hardware or software is not compensated for.  
Future versions of [Screen](Screen)() may bring additional fine-grained presentation  
timing modes of higher sophistication or with different performance vs precision  
vs reliability tradeoffs.  
  
  
Opening or closing a window takes about one to three seconds, depending on the  
type of connected display. If your system has noisy timing or flaky graphics  
drivers it might take up to 15 seconds to open a window.  
COMPATIBILITY TO OS-9 PTB: If you absolutely need to run old code for the old  
[MacOS](MacOS)-9 or Windows Psychtoolbox-2, you can switch into a compatibility mode by  
adding the command [Screen](Screen)('[Preference](Preference)', 'EmulateOldPTB', 1) at the very top of  
your script. This will restore Offscreen windows and [WaitBlanking](WaitBlanking) functionality,  
but at the same time disable most of the new features of the [OpenGL](OpenGL)  
Psychtoolbox. Please do not write new experiment code in the old style!  
Emulation mode may contain significant bugs, as it gets virtually no testing, so  
use with great caution!  


###See also:
[OpenOffscreenWindow](Screen-OpenOffscreenWindow), [SelectStereoDrawBuffer](Screen-SelectStereoDrawBuffer), [PanelFitter](Screen-PanelFitter), Close, [CloseAll](Screen-CloseAll)
