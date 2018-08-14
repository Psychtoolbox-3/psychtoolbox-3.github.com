# [Screen('OpenWindow')](Screen-OpenWindow) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Open an onscreen window. Specify a screen by a windowPtr or a screenNumber (0 is  
the main screen, with menu bar). "color" is the clut index (scalar or [r g b]  
triplet) that you want to poke into each pixel; default is white. If supplied,  
"rect" must contain at least one pixel. If a windowPtr is supplied then "rect"  
is in the window's coordinates (origin at upper left), and defaults to the whole  
window. If a screenNumber is supplied then "rect" is in screen coordinates  
(origin at upper left), and defaults to the whole screen. (In all cases,  
subsequent references to this new window will use its coordinates: origin at its  
upper left.). Please note that while providing a "rect" parameter to open a  
normal window instead of a fullscreen window is convenient for debugging, but  
drawing performance, stimulus onset timing and onset timestamping may be  
impaired, so be careful.  
"pixelSize" sets the depth (in bits) of each pixel; default is to leave depth  
unchanged. "numberOfBuffers" is the number of buffers to use. Setting anything  
else than 2 will be useful for development/debugging of PTB itself but will mess  
up any real experiment. "stereomode" Type of stereo display algorithm to use: 0  
(default) means: Monoscopic viewing. 1 means: Stereo output via [OpenGL](OpenGL) on any  
stereo hardware that is supported by [MacOS](MacOS)-X, e.g., the shutter glasses from  
[CrystalView](CrystalView). 2 means: Left view compressed into top half, right view into bottom  
half. 3 means left view compressed into bottom half, right view compressed into  
top half. 4 and 5 allow split screen display where left view is shown in left  
half, right view is shown in right half or the display. A value of 5 does the  
opposite (cross-fusion). Values of 6,7,8 and 9 enable Anaglyph stereo rendering  
of types left=Red, right=Green, vice versa and left=Red, right=Blue and vice  
versa. A value of 10 enables multi-window stereo: Open one window for left eye  
view, one for right eye view, treat both of them as one single stereo window. A  
value of 11 enables our own frame-sequential stereo mode. See [StereoDemo](StereoDemo).m for  
examples of usage of the different stereo modes. See [ImagingStereoDemo](ImagingStereoDemo).m for  
more advanced usage on modern hardware.  
"multisample" This parameter, if provided and set to a value greater than zero,  
enables automatic hardware anti-aliasing of the display: For each pixel,  
'multisample' color samples are computed and combined into a single output pixel  
color. Higher numbers provide better quality but consume more video memory and  
lead to a reduction in framerate due to the higher computational demand. The  
maximum number of samples is hardware dependent. Psychtoolbox will silently  
clamp the number to the maximum supported by your hardware if you ask for too  
much. On very old hardware, the value will be ignored. Read 'help AntiAliasing'  
for more in-depth information about multi-sampling. "imagingmode" This optional  
parameter enables PTB's internal image processing pipeline. The pipeline is off  
by default. Read 'help PsychImaging' for information about typical use and  
benefits of this feature.  
"specialFlags" This optional parameter enables some special window behaviours if  
the sum of certain flags is passed. A currently supported flag is the symbolic  
constant kPsychGUIWindow. It enables windows to behave more like regular GUI  
windows on your system. See 'help kPsychGUIWindow' for more info.  
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
  
Opening or closing a window takes about one to three seconds, depending on type  
of connected display. COMPATIBILITY TO OS-9 PTB: If you absolutely need to run  
old code for the old [MacOS](MacOS)-9 or Windows Psychtoolbox, you can switch into a  
compatibility mode by adding the command [Screen](Screen)('[Preference](Preference)', 'EmulateOldPTB',  
1) at the very top of your script. This will restore Offscreen windows and  
[WaitBlanking](WaitBlanking) functionality, but at the same time disable most of the new  
features of the [OpenGL](OpenGL) Psychtoolbox. Please do not write new experiment code in  
the old style! Emulation mode is pretty new and may contain significant bugs, so  
use with great caution!  


###See also:
[OpenOffscreenWindow](Screen-OpenOffscreenWindow), [SelectStereoDrawBuffer](Screen-SelectStereoDrawBuffer), [PanelFitter](Screen-PanelFitter), Close, [CloseAll](Screen-CloseAll)
