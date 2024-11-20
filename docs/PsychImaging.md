# [PsychImaging](PsychImaging)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

rc = [PsychImaging](PsychImaging)(subcommand [,arg1][,arg2][....,argn]) - Control common  
functions of the Psychtoolbox GPU image processing pipeline.  
  
This function allows you to setup and control various aspects and common  
functions of the Psychtoolbox image processing pipeline in a simple way.  
Various standard scenarious can be conveniently set up with this routine,  
e.g., geometric transformations of your stimulus image, various types of  
display correction, ...  
  
If you want to perform less common, unusual or simply not yet supported tasks  
with the pipeline, use the low-level [Screen](Screen)('HookFunction', ...)  
interface instead and have a peek in the M-File code for the  
[PsychImaging](PsychImaging).m file to learn about the low-level interface.  
See "help [PsychGLImageprocessing](PsychGLImageprocessing)" for more info.  
  
  
### Subcommands and their meaning:  
  
[PsychImaging](PsychImaging)('PrepareConfiguration');  
- Prepare setup of imaging pipeline for onscreen window.  
This is the first step in the sequence of configuration steps.  
  
  
[PsychImaging](PsychImaging)('AddTask', whichChannel, whichTask [,param1]...);  
- Add a specific task or processing requirement to the list of actions  
to be performed by the pipeline for the currently selected onscreen  
window. 'whichChannel' is a string with the name of the channel to  
configure:  
  
'LeftView' applies the action to the processing channel  
for the left-eye view of a stereo configuration. 'RightView' applies the  
action to the right-eye view of a stereo configuration. 'AllViews' applies  
the action to both, left- and right eye view channels of a stereo  
configuration or to the single monoscopic channel of a mono display  
configuration. Other options are 'Compositor', 'FinalFormatting' and  
'Finalizer' for special purpose channels. Set this to 'General' if the  
command doesn't apply to a specific view, but is a general requirement.  
  
'whichTask' contains the name string of one of the supported  
actions:  
  
\* 'UseGPGPUCompute' Enable use of [GeneralPurposeGPU](GeneralPurposeGPU) computing support.  
  This prepares use of Psychtoolbox functions which are meant to  
  interface with, or take advantage of, the general purpose computation  
  capabilities of modern graphics processing units and other massively  
  parallel compute acceleration hardware, e.g., DSP's, or multi-core  
  processors. Interfacing with such hardware is done via common standard  
  compute API's like NVidia's CUDA or the cross-platform [OpenCL](OpenCL) API.  
  
  Use of this function often requires specific modern GPU hardware and  
  the installation of additional driver software, e.g., NVidia's freely  
  available CUDA SDK and runtime, or the free and open-source [GPUmat](GPUmat)  
  toolbox. Read 'help PsychGPGPU' for further info.  
  
  This function just detects and selects supported GPU compute API's for  
  use with Psychtoolbox and initializes them and some Psychtoolbox  
  function to take advantage if appropriate. While you could use those  
  API's by themselves without calling this init function, Psychtoolbox  
  builtin processing functions would not be able to take advantage of the  
  API's or perform efficient and fast data exchange with them.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'UseGPGPUCompute', apitype [, flags]);  
  
  'apitype' Allows selection of the compute API to use. The value 'Auto'  
  leaves the choice to Psychtoolbox. The value 'GPUmat' selects the  
  high-level, free and open-source [GPUmat](GPUmat) compute toolkit for Matlab.  
  Currently no other choices are supported, but this is expected to  
  change in the future.  
  
  'flags' An optional string of keyword flags to determine behaviour.  
  There aren't any flags defined yet.  
  
  
\* 'SideBySideCompressedStereo' [Ask](Ask) for stereo display in a horizontally  
  compressed side-by-side format. Left and Right eye images are drawn at  
  full framebuffer resolution by usercode. [Screen](Screen)('[Flip](Flip)', ...) draws them  
  horizontally compressed side-by-side to each other. They are scanned  
  out to the display device this way and then the display device itself  
  uncompresses them back to full resolution and displays them  
  stereoscopically, typically via built-in alternating frame-sequential  
  stereo with stereo goggles, but other methods are conceivable. This is  
  one popular stereo frame packing format for stereo on HDMI display  
  devices. Once you've set up a stereo display mode via [PsychImaging](PsychImaging), you  
  can tweak its specific parameters by calling the function  
  [SetCompressedStereoSideBySideParameters](SetCompressedStereoSideBySideParameters)().  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'SideBySideCompressedStereo');  
  
  
\* 'InterleavedColumnStereo' [Ask](Ask) for stereo display in interleaved mode.  
  The output image is composed from the lefteye and righteye stereo  
  buffers by interleaving their content: Even columns are filled with  
  content from the left buffer, odd columns are filled with content from  
  the right buffer, i.e., Col 0 = Left col 0, Col 1 = Right Col 0, Col 2  
  = Left col 1, Col 3 = Right col 1, ....  
  
  This mode is useful for driving some auto-stereoscopic displays. These  
  use either some vertical parallax barriers or vertical lenticular  
  lense sheets. These direct light from even columns to one eye, light  
  from odd columns to the other eye.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'InterleavedColumnStereo', startright);  
  
  If 'startright' is zero, then even columns are taken from left buffer. If  
  'startright' is one, then even columns are taken from the right buffer.  
  
  You can use the [RemapMouse](RemapMouse)() function to correct [GetMouse](GetMouse)() positions  
  for potential geometric distortions introduced by this function.  
  
  
\* 'InterleavedLineStereo' [Ask](Ask) for stereo display in interleaved mode.  
  The output image is composed from the lefteye and righteye stereo  
  buffers by interleaving their content: Even lines are filled with  
  content from the left buffer, odd lines are filled with content from  
  the right buffer, i.e., Row 0 = Left row 0, Row 1 = Right row 0, Row 2  
  = Left row 1, Row 3 = Right row 1, ....  
  
  This mode is useful for driving some types of stereo devices and  
  goggles, e.g., the iGlasses 3D Video goggles in interleaved stereo  
  mode.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'InterleavedLineStereo', startright);  
  
  If 'startright' is zero, then even lines are taken from left buffer. If  
  'startright' is one, then even lines are taken from the right buffer.  
  
  You can use the [RemapMouse](RemapMouse)() function to correct [GetMouse](GetMouse)() positions  
  for potential geometric distortions introduced by this function.%  
  
  
\* 'DualWindowStereo' [Ask](Ask) for stereo display in dual-window mode (stereomode 10)  
  
  Only use this function under [MacOSX](MacOSX). If possible on your setup and OS,  
  rather use a single window, spanning both stereo display outputs, and use  
  stereomode 4 or 5 to display dual-display stereo. That is much more  
  efficient in terms of speed, computational load and memory consumption,  
  also potentially more robust with respect to visual stimulation timing.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'DualWindowStereo', rightEyeScreen [, rightEyeWindowRect]);  
  
  The left-eye image will be displayed on the screen and at a location  
  specified as usual via [PsychImaging](PsychImaging)('Openwindow', screenid, ..., rect);  
  The right eye image will be displayed on screen 'rightEyeScreen'. If  
  the optional 'rightEyeWindowRect' is specified, then the right eye image  
  is not displayed in a fullscreen window, but in a window with the bounding  
  rectangle 'rightEyeWindowRect'.  
  
  
\* 'UseVirtualFramebuffer' [Ask](Ask) for support of virtual framebuffer, even if  
  it isn't strictly needed, given the remaining set of requirements. Most  
  of the tasks require such a framebuffer - it gets enabled anyway. In a  
  few cases, e.g., to simplify your code (no need for special cases), it  
  may be useful to activate such a framebuffer even if it isn't strictly  
  needed. This option activates a minimal buffer with 8 bits per color  
  cmponent fixed point precision.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'UseVirtualFramebuffer');  
  
  
\* 'UseFineGrainedTiming' [Ask](Ask) for use of fine-grained stimulus onset timing.  
  [Ask](Ask) [Screen](Screen)('[Flip](Flip)', window, when) to try to show the new visual stimulus  
  close to (= ideally exactly at) target time 'when', instead of showing the  
  stimulus at the next video refresh frame boundary with time t \>= 'when', ie.  
  try to schedule stimuli with better timing granularity than what is given by  
  the multiples of a video refresh cycle duration of the connected display.  
  
  This uses a technique known as "Variable Refresh Rate" or shorthand "VRR" if  
  your operating system and display driver and graphics card and cable and  
  display device supports it at the current system configuration. Otherwise,  
  [PsychImaging](PsychImaging)('OpenWindow', ...) will fail if this task can't be achieved.  
  
  For a list of requirements with respect to graphics cards, display devices,  
  operating systems, drivers and general system configuration to make this work,  
  read "help [VRRSupport](VRRSupport)". This will also tell you about limitations and caveats  
  wrt. this task.  
  
  There may be different methods of implementing such fine-grained timing.  
  The optional 'method' parameter allows you to select a specific method.  
  Using the keyword 'Auto' or omitting the 'method' parameter ([]) will leave  
  the choice of optimal method to [Screen](Screen)(). Currently the methods 'Simple' and  
  'OwnScheduled' are implemented: 'Simple' follows the most naive approach of VRR,  
  simply requesting immediate flip, or in case a 'when' time is specified, waiting  
  until 'when', then requesting a flip. 'OwnScheduled' selects a more sophisticated  
  scheduling method that tries to take other constraints like minimum and maximum  
  refresh rate of the display, display system state, and a specified 'styleHint'  
  for the given visual stimulation paradigm into account, and also tries to  
  compensate for some of the system timing jitter. This may provide higher  
  precision or stability in some stimulation scenarios, but may also cause  
  higher overhead or added latency in other scenarios.  
  
  The optional parameter 'styleHint' allows to give some general high level clue  
  into the nature of the visual stimulation paradigm, as far as presentation  
  timing is concerned. This allows to tune the scheduling method for VRR for  
  maximum precision and reliability for a stimulation paradigm of the specified  
  nature. Omitting the parameter, or setting it to 'None', will ask the algorithm  
  to make almost no assumptions about the nature of the stimulation, but to choose  
  some "one size fits all ok'ish" setup, or try to auto-detect how to tune itself for  
  the running paradigm. The currently supported 'styleHint' settings are:  
  
  - 'None' = Make no assumptions, try some "One size fits all hopefully ok'ish" setup.  
  
  The optional parameter 'vrrMinRefreshHz' allows to specify the lowest video  
  refresh rate that your display can reliably run at. If the parameter is  
  omitted, [Screen](Screen)() will try to auto-detect this display property, or failing  
  that, it will use a reasonable default.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'UseFineGrainedTiming' [, method='Auto'][, styleHint='None'][, vrrMinRefreshHz]);  
  
  
\* 'UseSubpixelDrive' [Ask](Ask) to take advantage of the so-called "Subpixel Drive"  
  mode of certain monochromatic medical imaging displays like, e.g., the  
  "Eizo [RadiForce](RadiForce) GS-521". This monitor essentially has a RGB panel with  
  horizontal RGB subpixels, but with the color filters removed, so each  
  pixel is horizontally split up into 3 luminance subpixels and these can  
  be individually addressed by packing 3 horizontally adjacent 8 bit stimulus  
  luminance pixels into the "RGB" color channels of an output pixel. Use  
  of this task will create a virtual framebuffer three times the width of  
  the output framebuffer and then pack triplets of three horizontal luminance  
  pixels into one output pixel, to triple the effective horizontal resolution.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'UseSubpixelDrive');  
  
  
\* 'UseRetinaResolution' [Ask](Ask) to prefer a framebuffer with the full native  
  resolution of attached [HiDPI](HiDPI) "Retina" displays on OSX, instead of a scaled  
  down lower resolution framebuffer with typically half the horizontal  
  and vertical resolution of the Retina display. This setting will be  
  ignored if the onscreen window is not displayed on a [HiDPI](HiDPI) "Retina"  
  display in a scaled display mode, or if the panel fitter is in use by  
  specifying the 'UsePanelFitter' task. By default, [Screen](Screen)() would use a  
  downscaled framebuffer on a Retina display under OSX and scale that low  
  resolution buffer up to full display panel resolution, just as Apples  
  OSX operating system does it by default. This in order to reduce  
  computational load, improve graphics performance, and avoid problems  
  with backward compatibility of old code. If you want to make full use  
  of the resolution of your [HiDPI](HiDPI) display, specify this task to tell  
  [Screen](Screen)() to use the full display panel resolution on OSX, even if this may  
  introduce some compatibility issues into your code and causes a decrease  
  in graphics performance due to the higher graphics rendering load.  
  
  If 'UseRetinaResolution' is used with a non-fullscreen window, ie.  
  the 'rect' parameter in [PsychImaging](PsychImaging)('OpenWindow', ...) is provided  
  to specify the screen position and size of the window, note that  
  the size of the window rect returned by [Screen](Screen)('GlobalRect') and  
  [Screen](Screen)('Rect'), as well as of the returned rect of [PsychImaging](PsychImaging)('OpenWindow')  
  will differ from the size of the 'rect' passed to 'OpenWindow'. 'rect's  
  passed into [OpenWindow](OpenWindow) for positioning and sizing the window, as well  
  as the global position rect returned by [Screen](Screen)('GlobalRect') for the  
  current size and position of the onscreen window are expressed in global  
  desktop coordinates, in somewhat arbitrary units of virtual "points".  
  How such a point translates into display pixels depends on the operating  
  system, possibly the desktop GUI in use (on other systems than OSX), the  
  set of connected displays and their Retina or non-Retina resolutions.  
  The aim is that the coordinate system is somewhat consistent and meaningful  
  across all connected displays, for varying definitions of "consistent" and  
  "meaningful" on different operating systems, but the mapping of points to  
  physical screen pixels can be different on each connected display, at the  
  discretion of the operating system. You may get especially "interesting"  
  results if you try to move an onscreen window between screens, or let it  
  span multiple displays of different type and resolution.  
  The rect returned by [PsychImaging](PsychImaging)('Openwindow') and [Screen](Screen)('Rect'), as  
  well as sizes returned by [Screen](Screen)('WindowSize') define the net useable  
  size of the window in display pixels. It is affected by all kind of  
  [PsychImaging](PsychImaging) operations, e.g., selection of stereo modes, high bit depth  
  modes etc., but also by scaling on Retina displays in high res mode.  
  If 'UseRetinaResolution' is used on a Retina/[HiDPI](HiDPI) display, one typical  
  result will be that the size of the window in pixels reported by these  
  functions will be higher than the size in points, as one virtual point will  
  get represented by more than 1 pixel on a Retina display. Observing twice  
  the window size in pixels than in points is quite typical, but other  
  scaling factors are possible. The take home message for you is to specify  
  location and size of your stimuli based on the sizes and rects returned  
  by [Screen](Screen)('Rect'), [PsychImaging](PsychImaging)('Openwindow') and [Screen](Screen)('Windowsize'), as  
  these are in units of display pixels, and \*not\* based on the virtual points  
  returned by [Screen](Screen)('GlobalRect'). The 2nd take home message is that you  
  should mostly use fullscreen windows for visual stimulation to avoid such  
  and other pitfalls.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'UseRetinaResolution');  
  
  
\* 'UseDisplayRotation' [Ask](Ask) to use builtin panel fitter exclusively for  
  rotating the framebuffer. This is useful if you want to turn your  
  display device from landscape (= normal upright) orientation into  
  portrait orientation (= rotated by 90 degrees clockwise or  
  counterclockwise). In such a case you will want to rotate the  
  framebuffer by 90 degrees as well, but you should \*not\* use the "rotate  
  monitor" function of your operating system for this purpose, as this  
  will very likely interfere with visual stimulus presentation timing and  
  timestamping! Use this task instead. It will perform rotation in a  
  similar way, but without severe interference to timing. However, there  
  is one limitation to this method: Multisample anti-aliasing currently  
  does not work if you use our framebuffer rotation.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'UseDisplayRotation', angle);  
  
  'angle' is the desired rotation angle. The only values which will give  
  well defined and useful results are multiples of 90 degrees, useful  
  values are essentially 0, +90, -90 and 180 degrees for no rotation,  
  clockwise rotation, counterclockwise rotation and upside down rotation.  
  
  This function is mutually exclusive with 'UsePanelFitter', but if you  
  need to use both, you can omit 'UseDisplayRotation' and pass the  
  'angle' parameter to 'UsePanelFitter' instead, which also accepts an  
  'angle' parameter with the same meaning.  
  
  This function is not very mature yet: If you want to use the  
  panelfitter for anything beyond simple framebuffer rotation by 90  
  degree increments, you will likely hit bugs or limitations which will  
  require significant tinkering by you.  
  
  
\* 'UsePanelFitter' [Ask](Ask) to use builtin panel fitter. This allows you to  
  define a virtual size for your onscreen window. The window will behave  
  as if it had that virtual size wrt. all size queries and drawing  
  operations. However, at [Screen](Screen)('[Flip](Flip)') time, the visual content of the  
  window will be resized by a fast scaling operation to the real size of  
  the windows framebuffer, ie., its real onscreen size. Scaling uses  
  bilinear interpolation or better for high quality results. After  
  rescaling to the real size, post-processing and display of your  
  stimulus image will proceed at full resolution. This function is useful  
  if you want to display a stimulus designed for a specific display  
  resolution on a display device of different higher or lower resolution.  
  Given that size and shape of the virtual framebuffer and real display  
  window may not match, the function provides you with multiple possible  
  choices on how to rescale your stimulus image, e.g., to maximize  
  display area, or to preserve the aspect ratio of the original image,  
  trading off displayed area etc.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'UsePanelFitter', size, strategy [, srcRect, dstRect][, angle]);  
  
  'size' is a [width, height] vector defining the width x height of the  
  virtual window in pixels.  
  
###   'strategy' a text string selecting the scaling method. Following settings are possible:  
  
  'Full' - [Scale](Scale) to full window size. Aspect ratio is not preserved,  
           unless the virtual window and the real onscreen windows 'rect'  
           already have the same aspect ratio, in which case this will be  
           a simple scaling operation.  
  
  'Aspect' - [Scale](Scale) to maximum size possible while preserving aspect  
             ratio. This will center the stimulus and add black  
             horizontal or vertical borders as neccessary.  
  
  'AspectWidth' - [Scale](Scale) aspect ratio preserving to cover full display  
                  width. Cut off top and bottom content if neccessary.  
  
  'AspectHeight' - [Scale](Scale) aspect ratio preserving to cover full display  
                   height. Cut off left and right content if neccessary.  
  
  'Centered' - Center stimulus without any scaling, add black borders  
               around stimulus or cut away border regions to get a  
               one-to-one mapping.  
  
  'Custom' - This works like the 'srcRect' and 'dstRect' parameters of  
             [Screen](Screen)('DrawTexture'): Cut out a 'srcRect' region from the  
             virtual framebuffer and display it in the 'dstRect' region.  
             'srcRect' and 'dstRect' are given in typical [left, top, right, bottom]  
             format.  
  
  'angle' is an optional rotation angle. If provided and non-zero, the  
  panelfitter will also rotate the output framebuffer by the given  
  rotation angle. Note: This doesn't work very well yet with most  
  framebuffer sizes and scaling strategies. What does work is if the  
  specified 'size' is identical to the onscreen windows size, or is its  
  transposed size (ie., if window is width x height pixels, then height x  
  width pixels will work as 'size' parameter) and the rotation angle is a  
  multiple of 90 degrees. This is mostly useful for display rotation from  
  landscape orientation into portrait orientation. Your mileage with  
  other configurations or rotation angles will vary.  
  
  Example: Suppose your real window covers a 1920 x 1080 display.  
  
  [PsychImaging](PsychImaging)('AddTask', 'General', 'UsePanelFitter', [800 600], 'Aspect');  
  -\> This would give you a virtual window of 800 x 600 pixels to draw  
  into and would rescale the 800 x 600 stimulus image to 1440 x 1080  
  pixels and display it centered on the 1920 x 1080 pixels display.  
  Aspect ratio would be correct and the image would cover the full height  
  1080 pixels of the display, but only 1440 out of 1920 pixels of its  
  width, thereby leaving black borders on the left and right side of your  
  stimulus.  
  
  [PsychImaging](PsychImaging)('AddTask', 'General', 'UsePanelFitter', [800 600], 'AspectHeight');  
  -\> Would do the same as above.  
  
  [PsychImaging](PsychImaging)('AddTask', 'General', 'UsePanelFitter', [800 600], 'AspectWidth');  
  -\> Would create a final image of 1920 pixels width, as you asked to  
  cover the full display width, aspect ratio would be correct, but the  
  top and bottom 75 pixels of your original stimulus would get cut away,  
  because they wouldn't fit after scaling without distorting the image.  
  
  
\* 'UseFastOffscreenWindows' [Ask](Ask) for support of fast Offscreen windows.  
  These use a more efficient storage, backed by [OpenGL](OpenGL) framebuffer  
  objects (FBO's). Drawing into them isn't faster, but \*switching\*  
  between drawing into onscreen- and offscreen windows, or switching  
  between drawing into different offscreen windows is faster. They also  
  support a couple of other advanced features and performance  
  improvements in conjunction with the imaging pipeline.  
  If you only specify this task, then you'll get the benefit of fast  
  windows, without the cost of other features of the pipeline you might  
  not need.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'UseFastOffscreenWindows');  
  
  
\* 'EnableCLUTMapping' Enable support for old-fashioned clut animation /  
  clut mapping. The drawn framebuffer image is transformed by applying a  
  color lookup table (clut). This is not done via the hardware gamma  
  tables as in the good ol' days, but by application of the clut via  
  image processing. Hardware gamma tables don't provide well defined  
  timing on modern hardware, therefore they aren't suitable anymore.  
  
  You can update the clut to be applied at the next [Screen](Screen)('[Flip](Flip)');  
  via the command [Screen](Screen)('LoadNormalizedGammatable', windowPtr, clut, 2);  
  
  'clut' needs to be a clutSize-by-3 matrix, with 'clutSize' slots and  
  one column for each of the red, green and blue color channels.  
  
###   Setup command:  
  
  By default, a clut of 256 slots with (R,G,B) values is used, but you  
  can provide the optional 'clutSize' parameter to use clut's with more  
  slots. The maximum number depends on your GPU, but 2048 are typically  
  supported even on very low-end cards.  
  
  If you set 'highprecision' to 1, the clut will resolve values at more  
  than 8 bit per color channel on modern hardware. This usually only  
  makes sense if you also use a more than 8 bpc framebuffer with more  
  than 256 slots as clutSize.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', whichView, 'EnableCLUTMapping' [, clutSize=256][, highprecision=0]);  
  Example: [PsychImaging](PsychImaging)('AddTask', 'AllViews', 'EnableCLUTMapping');  
  
  
\* 'FloatingPoint16Bit' [Ask](Ask) for a 16 bit floating point precision  
  framebuffer. This allows more than 8 bit precision for complex drawing,  
  compositing and image processing operations. It also allows  
  alpha-blending with signed color values and intermediate results that  
  are outside the displayable range, e.g., negative. Precision is about 3  
  digits behind the decimal point or 1024 discriminable displayable  
  levels. If you need higher precision, choose 'FloatingPoint32Bit'.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'FloatingPoint16Bit');  
  
  
\* 'FixedPoint16Bit' [Ask](Ask) for a 16 bit integer precision framebuffer.  
  On graphics hardware that supports this, a 16 bit signed integer  
  framebuffer will be created. Such a framebuffer can store intermediate  
  color values in the normalized range [-1.0 ; +1.0] with a precision of  
  15 bits per component. Only positive values between 0.0 and 1.0 are  
  displayable in the end though. If the graphics hardware does not support this,  
  a 16 bit unsigned integer framebuffer is tried instead. Such a framebuffer  
  allows for 16 bits of precision per color component. However, many graphics  
  cards do not support alpha-blending on such a framebuffer, and  
  intermediate out-of-range values (smaller than zero or bigger than one) aren't  
  supported either. Such values will be clamped to the representable [0.0 ; 1.0]  
  range instead. Additionally this mode is only supported on some graphics  
  hardware. It is a special purpose intermediate solution - more accurate  
  than 16 bit floating point, but less capable and less accurate than 32  
  bit floating point. If you need higher precision, choose 'FloatingPoint32Bit'.  
  
  The main sad reason this switch exists is because some graphics hardware or  
  graphics drivers do not support floating point precision textures and  
  framebuffers due to some ridiculous patent restrictions, but they do  
  support a 16 bit signed or unsigned integer precision format. The switch  
  is basically a workaround for the broken patent systems of many countries.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'FixedPoint16Bit');  
  
  
\* 'FloatingPoint32Bit' [Ask](Ask) for a 32 bit floating point precision  
  framebuffer. This allows more than 8 bit precision for complex drawing,  
  compositing and image processing operations. It also allows  
  alpha-blending with signed color values and intermediate results that  
  are outside the displayable range, e.g., negative. Precision is about  
  6.5 digits behind the dezimal point or 8 million discriminable displayable  
  levels. Be aware that only the most recent hardware [(NVidia]((NVidia) Geforce  
  8000 series, ATI Radeon HD 2000 series) is able to perform  
  alpha-blending at full speed in this mode. Enabling alpha-blending on  
  older hardware may cause a significant decrease in drawing performance,  
  or alpha blending may not work at all at this precision! If you'd like  
  to have both, the highest precision and support for alpha-blending,  
  specify 'FloatingPoint32BitIfPossible' instead. PTB will then try to  
  use 32 bit precision if this is possible in combination with alpha  
  blending. Otherwise, it will choose 16 bit precision for drawing &  
  blending, but 32 bit precision at least for the post-processing.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'FloatingPoint32Bit');  
  
  
\* 'FloatingPoint32BitIfPossible' [Ask](Ask) PTB to choose the highest precision  
  that is possible on your hardware without sacrificing functionality like,  
  e.g., alpha-blending. PTB will choose the best compromise possible for  
  your hardware setup.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'FloatingPoint32BitIfPossible');  
  
  
\* 'NormalizedHighresColorRange' [Ask](Ask) PTB to use a normalized range of  
  color and luminance intensity levels in the interval [0; 1], ie. values  
  between zero and one for minimum and maximum intensity. Also ask for  
  unclamped colors -- intermediate results are allowed to take on  
  arbitrary values, e.g., also negative values. All [Screen](Screen)() 2D drawing  
  commands should operate at maximum color/luminance precision.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'NormalizedHighresColorRange' [, applyAlsoToMakeTexture]);  
  
  The command [PsychImaging](PsychImaging)('AddTask', 'General', 'NormalizedHighresColorRange', 1);  
  is automatically executed if you used [PsychDefaultSetup](PsychDefaultSetup)(featureLevel)  
  with a featureLevel of \>= 2 at the top of your experiment script,  
  \*except\* that clamping is \*not\* disabled by default in this case! To  
  disable clamping you'd still need to add this task explicitely, as  
  unclamping may have unintended side effects on old graphics hardware.  
  
  The optional flag 'applyAlsoToMakeTexture' defaults to zero. If set to 1,  
  then a unit color range of expected input values in the [0; 1] range is  
  also applied to standard 8-Bit precision textures in [Screen](Screen)('MakeTexture')  
  if the provided Matlab imageMatrix is of double precision type instead of  
  uint8 type. This allows to specify standard textures in the same consistent  
  value range 0-1 as other drawing colors, for cleaner code. Such textures  
  will still be limited to 0-1 range and only resolved into 256 intensity  
  levels, unless you also set the optional 'floatprecision' flag in [Screen](Screen)('MakeTexture')  
  to a value of 1 or 2. We still apply this limitation, as high precision textures consume  
  more memory and other resources and are incompatible with very old graphics  
  hardware.  
  
  This is just a convenience shortcut for [Screen](Screen)('ColorRange', win, 1, 0, applyAlsoToMakeTexture);  
  with the added benefit of allowing to specify the background clear  
  color in normalized 0-1 range as well. This command is implied by use  
  of any of the high precision display device drivers (for attenuators,  
  Bits+ box etc.). It is only needed if you want to create the same  
  visual results on a 8 bit standard framebuffer without needing to  
  change your code, or if you want to set the 'applyAlsoToMakeTexture' flag to a  
  setting of non-zero, so unit colorrange also applies to [Screen](Screen)('MakeTexture').  
  
  
\* 'StereoCrosstalkReduction' If a stereoMode is active or requested,  
  apply a shader first in the processing chain that for each eye aims to  
  reduce crosstalk from the other eye.  
  
###   Usage:  
  
    [PsychImaging](PsychImaging)('AddTask', 'LeftView', 'StereoCrosstalkReduction', method, crossTalkGain);  
    [PsychImaging](PsychImaging)('AddTask', 'RightView', 'StereoCrosstalkReduction', method, crossTalkGain);  
  
  The 'method' parameter selects the method to use for crosstalk  
  reduction.  
  
###   Currently only a method named 'SubtractOther' is implemented, which works as follows:  
  
  To reduce crosstalk, the contrast in the image of each eye, i.e., the  
  difference in color from the background level provided as background  
  clear color of the window is subtracted from the image of the other eye,  
  after scaling the contrast by 'crossTalkGain'. 'crossTalkGain' can be a  
  scalar, or a separate gain for each RGB channel. The background color  
  can be a scalar in the range 0-1, or a 3-element array to set the  
  backgroundlevel for each RGB channel separately. The background  
  color level should not be zero, as contrast then can't be inverted  
  around the background level. In general, the background level  
  should be high enough to allow unclamped inversion of the highest  
  contrast features of your stimulus at your 'crossTalkGain', or  
  artifacts will occur.  
  
  
\* 'DisplayColorCorrection' Select a method for color correction to apply to  
  stimuli before output conversion and display. You have to specify a  
  color correction method 'methodname' to apply as parameter, see "help  
  [PsychColorCorrection](PsychColorCorrection)" for an overview of supported color correction  
  methods and their adjustable parameters. The imaging pipeline will be  
  set up to support the chosen color correction method. After you've  
  opened the onscreen window, you can use the different subcommands of  
  [PsychColorCorrection](PsychColorCorrection)() to change parameters of the color correction  
  algorithm at runtime.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', whichView, 'DisplayColorCorrection', methodname);  
  
  Example: [PsychImaging](PsychImaging)('AddTask', 'FinalFormatting', 'DisplayColorCorrection', 'SimpleGamma');  
  This would apply a simple power-law gamma correction to all view  
  channels of a stereo setup, or the single view of a monoscopic setup.  
  Later on you could use the methods of [PsychColorCorrection](PsychColorCorrection)() to  
  actually set the wanted gamma correction factors.  
  
  Please note that we use the channel 'FinalFormatting' instead of  
  'AllViews' as we'd usually do. Both specs will work, but a selection  
  of 'FinalFormatting' will lead to faster processing in many cases, so  
  this is preferred here if you want to apply the same setting to all  
  view channels - or to a single monoscopic display. Should you find  
  that things don't work as expected, you might try 'AllViews' instead  
  of 'FinalFormatting' - There are subtle differences in how they  
  process your instructions, which may matter in some corner cases.  
  
  
\* 'EnablePseudoGrayOutput' Enable the high-performance driver for the  
  rendering of up to 1786 different levels of gray on a standard - but  
  well calibrated - color monitor and 8 bit graphics card. This is done  
  by applying an algorithn known as "Pseudo-Gray" or "Bit stealing".  
  Selecting this mode implies use of 32 bit floating point  
  framebuffers, unless you specify use of a 16 bit floating point  
  framebuffer via 'FloatingPoint16Bit' explicitely. The expected range  
  of input luminance values is between 0 and 1. See "help [CreatePseudoGrayLUT](CreatePseudoGrayLUT)"  
  for further explanation.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'EnablePseudoGrayOutput');  
  
  
\* 'EnableGenericHighPrecisionLuminanceOutput'  
  Setup Psychtoolbox for conversion of high precision luminance images  
  into a format suitable for special high precision luminance display  
  devices. This is a generic support routine that uses LUT based  
  conversion.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'EnableGenericHighPrecisionLuminanceOutput', lut);  
  
  
\* 'EnableVideoSwitcherSimpleLuminanceOutput'  
  Setup Psychtoolbox for conversion of high precision luminance images  
  into a format suitable for driving the "[VideoSwitcher](VideoSwitcher)" high precision  
  luminance display device which was developed by Xiangrui Li et al.  
  
  This implements the simple converter, which only needs the  
  Blue-To-Red-Ratio of the device as input parameter and performs  
  conversion via a closed-form formula without any need for lookup  
  tables. This is supposed to be fast.  
  
  See "help [VideoSwitcher](VideoSwitcher)" for more info about the device and its  
  options.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'EnableVideoSwitcherSimpleLuminanceOutput' [, btrr] [, trigger]);  
  
  - The optional 'btrr' parameter is the Blue-To-Red-Ratio to use. If the  
  parameter is left out, the btrr value will be read from a global  
  configuration file.  
  
  - The optional 'trigger' parameter can be zero for "No trigger", or 1  
  for "Use trigger as configured". By default, trigger is off (==0).  
  Enabled, one can use the [VideoSwitcher](VideoSwitcher)('SetTrigger', ...); function to  
  configure when and how a trigger signal should be emitted. Trigger  
  signals are simply specific pixel patterns in the green output channel.  
  That channel is recognized by the [VideoSwitcher](VideoSwitcher) as a trigger signal  
  control channel.  
  
  
\* 'EnableVideoSwitcherCalibratedLuminanceOutput'  
  Setup Psychtoolbox for conversion of high precision luminance images  
  into a format suitable for driving the "[VideoSwitcher](VideoSwitcher)" high precision  
  luminance display device which was developed by Xiangrui Li et al.  
  
  This implements the simple converter, which only needs the  
  Blue-To-Red-Ratio of the device as input parameter and performs  
  conversion via a closed-form formula without any need for lookup  
  tables. This is supposed to be fast.  
  
  See "help [VideoSwitcher](VideoSwitcher)" for more info about the device and its  
  options.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'EnableVideoSwitcherCalibratedLuminanceOutput' [, btrr] [, lut] [, trigger]);  
  
  - The optional 'btrr' parameter is the Blue-To-Red-Ratio to use. If the  
  parameter is left out, the btrr value will be read from a global  
  configuration file.  
  
  - The optional 'lut' paramter is a 257 elements vector of luminance  
  values, which maps blue channel drive indices to luminance values. This  
  lut needs to be acquired via a calibration procedure by use of a  
  photometer. If 'lut' is left out, the table will be read from a global  
  configuration file.  
  
  - The optional 'trigger' parameter can be zero for "No trigger", or 1  
  for "Use trigger as configured". By default, trigger is off (==0).  
  Enabled, one can use the [VideoSwitcher](VideoSwitcher)('SetTrigger', ...); function to  
  configure when and how a trigger signal should be emitted. Trigger  
  signals are simply specific pixel patterns in the green output channel.  
  That channel is recognized by the [VideoSwitcher](VideoSwitcher) as a trigger signal  
  control channel.  
  
  
\* 'EnableNative10BitFramebuffer' Enable support for output of stimuli  
  with 10 bit precision per color channel (10 bpc / 30 bpp / "Deep color")  
  on graphics hardware that supports native 10 bpc framebuffers.  
  
  Under Linux, AMD graphics cards since at least the year 2007, [NVidia](NVidia) graphics  
  cards since 2008, and Intel graphics chips since at least 2010 do support native  
  10 bit framebuffers. Intel graphics chips must use the legacy X11 "intel" video driver  
  to output their 10 bit framebuffers with actual 10 bit precision on Ubuntu  
  20.04 LTS or earlier, as old "modesetting" video drivers do not support output  
  with more than 8 bit. On Ubuntu 22.04-LTS and later, the modern modesetting driver  
  can deal with 10 bpc output on all Intel graphics, so at least Ubuntu 22.04-LTS is  
  recommended. [XOrgConfCreator](XOrgConfCreator) will take care of these Intel quirks when creating a  
  custom xorg.config for such 10 bpc setups under Intel.  
  
  Under MS-Windows, many graphics cards of the professional class AMD/ATI Fire/Pro  
  series (2008 models and later), and all current models of the professional class  
  [NVidia](NVidia) Quadro series (2008 models and later), do support 10 bpc framebuffers  
  under some circumstances. 10 bpc display on classic CRT monitors which are connected  
  via analog VGA outputs is supported. Support for digital display devices like  
  LCD/OLED panels or video projectors depends on the specific type of display output  
  connector used, the specific panels, and their video settings. Consult manufacturer  
  documentation for details. In general, 10 bpc output is usually supported on graphics  
  cards and displays via [DisplayPort](DisplayPort) or HDMI video outputs, but to our knowledge not  
  via DVI-D outputs.  
  
  If such a combination of graphics card and display is present on your system  
  on Linux or Microsoft Windows, then Psychtoolbox will request native support  
  from the standard graphics drivers, ie., it won't need to use our own  
  homegrown experimental box of tricks to enable this. You do need to enable/  
  unlock 10 bpc mode somewhere in the display driver settings though. On Linux you  
  can do this for supported cards and drivers via [XOrgConfCreator](XOrgConfCreator) + [XOrgConfSelector](XOrgConfSelector),  
  on Windows the method is vendor specific.  
  
  Apple OSX, since version 10.11.2 "El Capitan", does support native 10 bpc video  
  output on some small subset of Apple hardware, as of May 2017 these are the [MacPro](MacPro)  
  2013 "with some suitable displays" (Apple quotation), and the 27 inch iMac models  
  late 2014 and late 2015 with Retina 5k displays. We've confirmed this to be working  
  on the iMac 5k Retina 27 inch late 2014 model via photometer measurements. On OSX,  
  the OS will actually provide a 16 bit half-float framebuffer for our onscreen windows.  
  This buffer provides ~11 bpc effective linear precision in the displayable color  
  intensity range 0.0-1.0. The OS outputs this 11 bpc framebuffer as a native 10 bpc  
  video signal on suitable displays and uses some Apple proprietary software spatial  
  dithering algorithm to add 1 extra bit of simulated precision, so a photometer would  
  measure up to 11 bpc perceived/measured precision. On some other Mac models, which are  
  not in Apples list of 10 bit capable Macs, Apple uses a proprietary spatial dithering  
  algorithm implemented in software to fake a precision of 11 bpc on standard 8 bpc  
  framebuffers and displays, at least convincing enough for a photometer. The downside  
  of this proprietary dithering scheme is that visual stimulus onset timing precision  
  and timestamping precision is impaired, so Macs in "10 bit" framebuffer mode are not  
  suitable if trustworthy frame accurate visual timing is needed. Nothing we could do  
  about this. To summarize: [EnableNative10BitFramebuffer](EnableNative10BitFramebuffer) mode on OSX will actually give  
  you a simulated 11 bpc framebuffer on some Mac hardware, plus severe visual timing  
  problems.  
  
###   Psychtoolbox experimental 10 bpc framebuffer support:  
  
  Additionally, we support ATI/AMD Radeon hardware of the X1000, HD2000 - HD8000,  
  series and later models (everything since at least the year 2006) up to the AMD  
  Polaris gpu family under Linux via our own low-level setup mechanisms. AMD gpu's  
  of type Vega or more recent are not supported by our own hacks, but by the builtin  
  native driver support mentioned in the paragraphs above. These graphics cards support  
  a native ARGB2101010 framebuffer, ie., a system framebuffer with 2 bits for the alpha  
  channel, and 10 bits per color channel.  
  
  As this is supported by the hardware, but not always by the standard AMD  
  graphics drivers, we follow a hybrid approach: We use special low-level  
  hardware access to reconfigure the hardware for 10 bpc framebuffer support.  
  Then we use a special imaging pipeline formatting plugin to convert 16 bpc or  
  32 bpc stimuli into the special data format required by this framebuffer  
  configuration.  
  
  On Linux you must have run [PsychLinuxConfiguration](PsychLinuxConfiguration) at least once on your  
  system at some point. You'll need to have one of the supported AMD Radeon  
  gfx-cards (see above) for this to work. If you use Linux with the free and  
  open-source AMD graphics drivers, 10 bpc framebuffer support should work  
  reliably, so use of the open-source drivers on Linux is recommended for  
  reliable results.  
  
  Getting a 10 bpc framebuffer working is only the first half of what you need for  
  high color precision output. Your graphics card must also be able to transmit the  
  video signal at high precision to the display device and the display must be able  
  to faithfully reproduce the high precision image. 10 bpc output has been verified  
  to work for analog VGA connected CRT monitors and displays on both AMD and [NVidia](NVidia)  
  graphics cards which do support 10 bpc framebuffers, so with a analog VGA CRT you  
  should be safe. Note that this only applies to native VGA output via VGA connectors  
  or passive DVI-I to VGA adapters connected to a DVI-I connector. Active [DisplayPort](DisplayPort)  
  to VGA adapters or active HDMI to VGA adapters may be limited to maximum 8 bpc output.  
  The status of 10 bpc output to digital display devices differs a lot across devices  
  and OS'es. Output of 10 bpc framebuffers to standard 8 bpc digital laptop panels or  
  DVI/HDMI/[DisplayPort](DisplayPort) panels via digital dithering is known to work, but that is not  
  the real thing, only a simulation of 10 bpc via dithering to 8 bpc. This may or may  
  not be good enough for your specific visual stimulation paradigm. On a DVI-D connected  
  standard digital display, this dithered output is the best you will ever get.  
  
  [DisplayPort](DisplayPort): Recent AMD/Intel/[NVidia](NVidia) graphics cards can output to some suitable [DisplayPort](DisplayPort)  
  displays with 10 bpc or higher precision on Linux, and maybe also on MS-Windows, but you  
  have to verify this carefully for your specific display.  
  
  HDMI: Recent Intel graphics cards can output up to 12 bpc precision to HDMI deep color  
  capable displays on Linux if the X11 intel-ddx video driver is used. All AMD graphics  
  cards of model Radeon HD-5000 or later (and equivalent Fire-Series models) can output to  
  HDMI deep color capable displays with 10 bpc real precision at least if you use a Linux  
  kernel of version 3.16 or later with the open-source AMD graphics drivers. Execute  
  [PsychLinuxConfiguration](PsychLinuxConfiguration) to enable this \>= 10 bpc deep color output mode, then reboot your  
  machine once to enable it.  
  
  The status with the proprietary AMD drivers on MS-Windows is unknown.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'EnableNative10BitFramebuffer' [, disableDithering=0]);  
  
  This function will setup a 32 bpc floating point resolution framebuffer by  
  default for Psychtoolbox drawing and stimulus processing. Output will happen  
  into a 10 bpc framebuffer. The function will also disable the graphics cards  
  gamma tables, so you'll need to use [PsychImaging](PsychImaging)(...'DisplayColorCorrection'...)  
  for gamma and color correction if you need this.  
  
  The function will \*not\* disable dithering on digital displays by default,  
  but leave that decision to the operating system and graphics drivers of  
  your machine. A well working OS would disable dithering on a 10 bpc or  
  higher color depth display, if the display reports its capability to the  
  OS via its EDID info. It would enable dithering on < 10 bpc displays, so  
  you'd get a "pseudo 10 bpc" display where 10 bpc color depths is simulated  
  on a 6 bpc or 8 bpc display via the dithering.  
  
  You can disable dithering manually on some graphics cards by providing the  
  optional 'disableDithering' flag as 1. Currently mostly AMD cards allow this  
  control. [NVidia](NVidia) or Intel cards require manual setup to force dithering off.  
  
  
\* 'EnableNative11BitFramebuffer' Enable support for output of stimuli with (almost)  
  11 bit precision per color channel (11 bpc / 32 bpp / "Deep color") on graphics  
  hardware that supports native 11 bpc framebuffers. This will request an ~ 11 bpc  
  framebuffer from the operating system. If it can't get such a framebuffer on Linux  
  with AMD graphics hardware, it will use our own homegrown setup code to provide  
  such a framebuffer anyway on Radeon X1000, HD-2000 and later graphics cards and  
  equivalent Fire-Series graphics cards. On OSX 10.11.2 it will request and get a  
  ~11 bpc framebuffer on some Mac models. See the explanations above for 10 bpc on  
  OSX.  
  
  Read all the explanations in the section above for 'EnableNative10BitFramebuffer'  
  for capabilities, limitations and possible caveats on different systems.  
  
  Please note that on Linux this "11 Bit framebuffer" is not quite 11 bpc precision,  
  but only about ~ 10.6666 bpc precision. Specifically, the framebuffer can only  
  store at most 32 bits of color information per pixel, so it will store 11 bit  
  precision for the red channel (2048 distinct red intensity levels), 11 bit  
  (2048 levels) for the green channel, but only 10 bit (1024 levels) for the blue  
  channel, for a total number of 11 + 11 + 10 bits = 32 bits of color information  
  per pixel, or 4 billion different possible colors. A true 11 bpc framebuffer would  
  need 33 bits per pixel, and current graphics hardware can't handle that.  
  
  How many bits of precision of these ~ 11 bpc actually reach your display device?  
  
  - Analog VGA only provides for maximum 10 bpc output precision on all shipping  
    [NVidia](NVidia) and AMD graphics cards at best. Intel graphics cards only allow for 8 bpc.  
  
  - [DisplayPort](DisplayPort) or HDMI might allow for transfer of 11 bpc precision, in general they  
    support up to 12 bpc. However additional hardware restrictions for your graphics  
    card may limit precision to as low as 10 bpc. To our knowledge, only AMD graphics  
    cards support ~ 11 bpc framebuffers at all. Radeon HD-7000 and earlier can only  
    truly process up to 10 bpc, so 'EnableNative11BitFramebuffer' may not gain you any  
    precision over 'EnableNative10BitFramebuffer' in practice on these cards. AMD cards  
    of the "Sea Islands" family or later, mostly models from the year \>= 2014, are  
    able to process and output up to 12 bpc over HDMI or [DisplayPort](DisplayPort), so they can  
    output true ~11 bpc images.  
  
  So obviously: Measure very carefully on your setup what kind of precision you really  
  get and make sure not to be fooled by dithering if you need precise low-level control  
  of spatial stimulus properties, or per-pixel high precision, instead of just averaged  
  over larger clusters of pixels.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'EnableNative11BitFramebuffer' [, disableDithering=0]);  
  
  
\* 'EnableNative16BitFramebuffer' Enable 16 bpc, 64 bpp framebuffer on some supported setups.  
  
  This asks to enable a framebuffer with a color depth of 16 bpc for up to 65535 levels of intensity  
  per red, green and blue channel, ie. 48 bits = 2^48 different colors. Currently, as of November 2024,  
  this mode of operation is only supported on Linux/X11 when using the open-source amdgpu-kms driver  
  on modern AMD GCN 1.1+ graphics cards [3]. On suitable setups, this will establish a 16 bpc framebuffer  
  which packs 3 \* 16 bpc = 48 bit color info into 64 bpp pixels and the gpu's display engine will scan  
  out that framebuffer at 16 bpc. However, effective output precision is further limited to < 16 bpc by  
  your display, video cable and specific model of graphics card. As of November 2024, the maximum effective  
  output precision is limited to at most 12 bpc (= 4096 levels of red, green and blue) by the graphics card,  
  and this precision is only attainable on AMD graphics cards of the so called "Sea Islands" (cik) family  
  (aka [GraphicsCore](GraphicsCore) Next GCN 1.1 or later), or any later models when used with the amdgpu-kms display driver.  
  
  Older AMD cards of type GCN 1.0 "Southern Islands" or earlier won't work, as they only support at most 10  
  bpc overall output precision.  
  
  Please note that actual 12 bpc output precision can only be attained on certain display devices and  
  software configurations. As of November 2024, the following hardware + software combos have been  
  verified with a CRS [ColorCal2](ColorCal2) colorimeter to provide 12 bpc per color channel precision:  
  
  - The Apple [MacBookPro](MacBookPro) 2017 15 inch with its built-in 10 bit Retina display, running under Ubuntu Linux  
    20.04 with Linux 5.14 or later kernels, as well as with a HDR-10 monitor via [DisplayPort](DisplayPort) and also via  
    HDMI. As those displays are 10 bit only, the 12 bit precision was attained via spatial dithering by the gpu.  
  
  - AMD Ryzen 5 2400G with AMD [RavenRidge](RavenRidge) integrated graphics chip with a HDR-10 monitor via [DisplayPort](DisplayPort) and  
    also via HDMI. As that display is 10 bit only, the 12 bit precision was attained via spatial dithering  
    by the gpu.  
  
  High bit depth 12 bpc output should work with native 12 bit displays connected via HDMI or [DisplayPort](DisplayPort).  
  Modern AMD gpus, e.g., AMD Polaris, are also able to emulate 12 bpc precision via spatial dithering on  
  8 and 10 bit display panels. Measure your results carefully with a photometer or colorimeter, this is the  
  only way to verify your specific setup really achieves 12 bpc! See the sections about 11 bpc and 10 bpc  
  native framebuffers above for further details.  
  
###   Required manual one-time setup:  
  
###   1. You will need to install the AMD developed and maintained AMDVLK open-source vulkan driver from:  
  
     https://github.com/[GPUOpen](GPUOpen)-Drivers/AMDVLK/releases  
  
     Driver release v-2021.Q4.1 or later from November 2021 is required to support this feature.  
     Note that release 2023-Q3.3 from September 2023 was the last release to support pre-Navi  
     gpu's like Polaris and Vega. Later versions only support AMD Navi and later with RDNA  
     graphics architecture.  
  
  2. You will need at least Linux kernel 5.14 or later versions. A way to manually install it on  
     Ubuntu 20.04-LTS is described on the following web page via the "mainline" helper software:  
  
     https://ubuntuhandbook.org/index.php/2020/08/mainline-install-latest-kernel-ubuntu-linux-mint  
  
     Ubuntu 22.04-LTS and later versions already have a suitable Linux 5.15 or later kernel by default  
     since April 2022.  
  
  3. If you are using an AMD Polaris gpu (aka Radeon 400 series) or later, then you are done.  
     Polaris was introduced in summer 2016.   
  
     If you are using an old "Sea Islands" / "[GraphicsCore](GraphicsCore) Next 1.1" / "GCN 1.1" gpu, you must reboot  
     your machine with Linux kernel boot settings that select the new amdgpu kms driver and AMD [DisplayCore](DisplayCore),  
     instead of the old radeon kms driver that would be used by default. This requires adding the following  
     parameters to the kernel boot command line: "radeon.cik\_support=0 amdgpu.cik\_support=1 amdgpu.dc=1"  
  
     Additionally you would need a custom AMDVLK driver, as AMD's current official AMDVLK driver does  
     no longer support pre-Polaris gpu's. We won't provide this driver for free at the moment, so please  
     enquire for potential paid support options on the Psychtoolbox user forum.  
  
  On AMD you can verify actual output bit depth for an output XXX by typing this command into a terminal  
  window, assuming your AMD graphics card is the first or only gpu in the system, ie. has index 0. If your  
  card has a different index, then replace the 0 below with that index:  
  
  sudo cat /sys/kernel/debug/dri/0/XXX/output\_bpc  
  
###   E.g., for the internal laptop eDP flat panel of the [MacBookPro](MacBookPro) 2017:  
  
  sudo cat /sys/kernel/debug/dri/0/eDP-1/output\_bpc  
  
  Note also that currently Psychtoolbox by itself will usually limit video output precision to 10 bpc,  
  even if a display is connected that claims to support 12 bpc or more, so 12 bpc content is actually  
  displayed by the graphics card using spatial dithering down to 10 bpc. Why? Because at least all 10  
  bpc capable HDMI displays are required by the HDMI standard to also "support" 12 bpc output precision.  
  However, most displays do not actually support 12 bpc, but just fake 12 bpc support. By forcing actual  
  output precision down to 10 bpc on such "pretend 12 bpc" displays, we can still achieve a good approximation  
  of 12 bpc output via gpu hardware dithering. If by chance you are the lucky owner of a true 12 bpc capable  
  display device, you can override Psychtoolbox 10 bpc choice by executing the xrandr command in a terminal,  
  or via a system('xrandr ...'); call from Octave/Matlab. E.g., the following xrandr command would enable  
  true 12 bpc output without dithering on HDMI output 0: xrandr --output HDMI-0 --set 'max bpc' 12  
  
  Once the above one-time setup is done, adding the following command to your script will enable the  
  16 bpc framebuffer with up to 12 bpc effective output precision:  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'EnableNative16BitFramebuffer');  
  
  
\* 'EnableNative16BitFloatingPointFramebuffer' Enable support for output of  
  stimuli with up to 16 bit floating point precision per color channel on  
  graphics hardware and displays that support native 16 bpc floating point  
  framebuffers. Please note that the effective linear output precision of a  
  16 bit non-linear floating point framebuffer in the normalized range 0.0 - 1.0  
  (the "typical" output range for SDR standard dynamic range displays) is only  
  about 11 bits ~ 2048 levels of red, green, blue intensity. Specifically, for  
  normalized color values above 0.5 (ie. 50% max intensity) only 11 bpc can be  
  attained at most, whereas values smaller or equal 0.5 may be able to attain  
  12 bpc output precision on some recent gpu's. This is due to the precision of  
  floating point 16, which decreases with increasing magnitude of values and  
  maxes out at 14 bits for very small magnitude values - however current hardware  
  can not output at more than 12 bpc precision anyway, even for very small color  
  values.  
  
  Linux supports this mode on AMD gpu's of the "Sea Islands" gpu family or later  
  if you install the AMDVLK AMD open-source Vulkan driver and use the imaging  
  pipeline tasks 'UseVulkanDisplay' or 'EnableHDR'. See AMDVLK instructions  
  above for 'EnableNative16BitFramebuffer'. You need Linux 5.8 for AMD Polaris  
  and later (e.g. contained in Ubuntu 20.10 or 20.04.2-LTS), or Linux 5.12  
  (e.g., from Ubuntu 21.10 or 20.04.4-LTS) for also supporting the earlier AMD  
  "Sea Islands" and later gpu's.  
  
  macOS [OpenGL](OpenGL) does support this mode with what seems to be mostly software  
  rendering on most machines, ie. with very low performance and even worse timing.  
  Your mileage may vary.  
  
  Windows usually only supports this mode on some gpu's with Vulkan when HDR  
  mode is used via 'EnableHDR', but not in SDR standard dynamic range mode.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'EnableNative16BitFloatingPointFramebuffer');  
  
  
\* 'UseDataPixx' Tell Psychtoolbox that additional functionality for  
  displaying the onscreen window on a [VPixx](VPixx) Technologies [DataPixx](DataPixx) device  
  should be enabled.  
  
  This command is implied by enabling a [DataPixx](DataPixx) video mode by one of the  
  commands for the [DataPixx](DataPixx) in the following sections.  
  
  'UseDataPixx' mostly prepares use of a variety of subfunctions in the  
  [DataPixxToolbox](DataPixxToolbox) ("help [DataPixxToolbox](DataPixxToolbox)") and in the [PsychDataPixx](PsychDataPixx)()  
  high-level driver ("help [PsychDataPixx](PsychDataPixx)").  
  
  
\* 'EnableDataPixxL48Output' Setup Psychtoolbox for L48 mode of the [VPixx](VPixx)  
  Technologies [DataPixx](DataPixx) device. This loads the graphics hardwares gamma  
  table with an identity mapping so it can't interfere with [DPixx](DPixx) video  
  processing. It also sets up automatic generation of control signals to  
  support the features of [DPixx](DPixx) that are available via the functions in  
  [PsychDataPixx](PsychDataPixx)(). You will be able to upload new CLUT's into the [DPixx](DPixx)  
  by use of the [Screen](Screen)('LoadNormalizedGammaTable', window, clut, 2);  
  command. CLUT updates will be synchronized with [Screen](Screen)('[Flip](Flip)') commands.  
  Please note that while L48 CLUT mode works even with very old  
  graphics hardware, this is a pretty cumbersome way of driving the  
  [DPixx](DPixx). On recent hardware, you will want to use M16 or C48 mode  
  (see below). That allows to draw arbitrarily complex stimuli with as  
  many colors as you want and PTB will take care of conversion into the  
  M16 or C48 format for [DataPixx](DataPixx).  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'EnableDataPixxL48Output');  
  
  
\* 'EnableDataPixxM16Output' Enable the high-performance driver for M16  
  mode of the [VPixx](VPixx) Technologies [DataPixx](DataPixx) device. This is the fastest and  
  most elegant way of driving the [DPixx](DPixx) box with 16 bit luminance output  
  precision. See "help [DataPixx](DataPixx)" for more information. Selecting this  
  mode implies use of 32 bit floating point framebuffers, unless you  
  specify use of a 16 bit floating point framebuffer via  
  'FloatingPoint16Bit' explicitely. If you do that, you will not be able  
  to use the full 16 bit output precision, but only approximately 10 bits.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'EnableDataPixxM16Output');  
  
  If you want to make use of the color overlay plane in M16 mode, then  
  call the function like this:  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'EnableDataPixxM16OutputWithOverlay');  
  See the explanation of color overlays in the section  
  'EnableBits++Mono++OutputWithOverlay' - behaviour of color overlays is  
  identical for the CRS Bits++ and the [VPixx](VPixx) [DataPixx](DataPixx).  
  
  
\* 'EnableDataPixxC48Output' Enable the high-performance driver for the  
  C48 mode of [VPixx](VPixx) technologies [DataPixx](DataPixx) box. This is the fastest and  
  most elegant way of driving the [DataPixx](DataPixx) box with 16 bit per color  
  channel output precision. See "help [DataPixx](DataPixx)" for more information.  
  Selecting this mode implies use of 32 bit floating point framebuffers,  
  unless you specify use of a 16 bit floating point framebuffer via  
  'FloatingPoint16Bit' explicitely. If you do that, you will not be able  
  to use the full 16 bit output precision, but only approximately 10 bits.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'EnableDataPixxC48Output', mode);  
  
  See the section below about 'EnableBits++Color++Output' for the meaning  
  of the mandatory "mode" parameter.  
  
  You can use the [RemapMouse](RemapMouse)() function to correct [GetMouse](GetMouse)() positions  
  for potential geometric distortions introduced by this function for  
  "mode" zero.  
  
  
\* 'UseBits\#' Tell Psychtoolbox that additional functionality for  
  displaying the onscreen window on a Cambridge Research Systems Bits\#  
  device should be enabled.  
  
  This command is implied by enabling a Bits+ or Bits\# video mode by one  
  of the commands for the Bits+/Bits\# in the following sections, if the  
  driver can auto-detect a connected Bits\# device. If it cannot auto-detect  
  a connected Bits\# device and this command is omitted, Psychtoolbox will  
  instead assume that an older Bits+ is in use and only allow functionality  
  common to Bits\# and Bits+, without automatic video mode switching.  
  
  If you provide this command, you can optionally specify the name of the  
  serial port to which your Bits\# is connected, instead of leaving it to  
  the system to find this out (either via configuration file or via a  
  guess-o-matic).  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'UseBits\#' [, [BitsSharpSerialPort](BitsSharpSerialPort)]);  
  
  'BitsSharpSerialPort' is optional and can be set to the name of a serial  
  port for your specific operating system and computer, to which the Bits\#  
  is connected. If omitted, Psychtoolbox will look for the name in the first  
  line of text of a text file stored under the filesystem path and filename  
  [[PsychtoolboxConfigDir](PsychtoolboxConfigDir) 'BitsSharpConfig.txt']. If that file is empty, the  
  serial port is auto-detected (Good luck!).  
  
  'UseBits\#' mostly prepares use of a variety of new Bits\# subfunctions  
  in the [BitsPlusPlus](BitsPlusPlus)() high-level driver ("help [BitsPlusPlus](BitsPlusPlus)").  
  
  
\* 'EnableBits++Bits++Output' Setup Psychtoolbox for Bits++ mode of the  
  Cambridge Research Systems Bits++ box. This loads the graphics  
  hardwares gamma table with an identity mapping so it can't interfere  
  with Bits++ T-Lock system. It also sets up automatic generation of  
  Bits++ T-Lock codes: You will be able to upload new CLUT's into the  
  Bits++ by use of the [Screen](Screen)('LoadNormalizedGammaTable', window, clut, 2);  
  command. CLUT updates will be synchronized with [Screen](Screen)('[Flip](Flip)')  
  commands, because PTB will generate and draw the proper T-Lock code  
  into the top line of your onscreen window. Please note that while  
  Bits++ CLUT mode works even with very old graphics hardware, this is a  
  pretty cumbersome way of driving the Bits++. On recent hardware, you  
  will want to use Mono++ or Color++ mode (see below). That allows to  
  draw arbitrarily complex stimuli with as many colors as you want and  
  PTB will take care of conversion into the Color++ or Mono++ format for  
  Bits++.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'EnableBits++Bits++Output');  
  
  
\* 'EnableBits++Mono++Output' Enable the high-performance driver for the  
  Mono++ mode of Cambridge Research Systems Bits++ box. This is the  
  fastest and most elegant way of driving the Bits++ box with 14 bit  
  luminance output precision. See "help [BitsPlusPlus](BitsPlusPlus)" for more  
  information. Selecting this mode implies use of 32 bit floating point  
  framebuffers, unless you specify use of a 16 bit floating point  
  framebuffer via 'FloatingPoint16Bit' explicitely. If you do that, you  
  will not be able to use the full 14 bit output precision of Bits++, but  
  only approximately 10 bits.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'EnableBits++Mono++Output');  
  
  If you want to make use of the color overlay plane in Mono++ mode, then  
  call the function like this:  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'EnableBits++Mono++OutputWithOverlay');  
  
###   Then you can query the window handle of the overlay window via:  
  
  overlayWin = [PsychImaging](PsychImaging)('GetOverlayWindow', window);  
  
  'overlayWin' is the handle to the overlay window associated with the  
  overlay of onscreen window 'window'. The overlay window is a standard  
  offscreen window, so you can do anything with it that you would want to  
  do with offscreen windows. The only difference is that the window is a  
  pure index window: It only has one "color channel", which can be written  
  with color values between 0 and 255. Values 1 to 255 get mapped to the  
  corresponding color indices of the Bits++ overlay plane: A zero value is  
  transparent -- Content of the onscreen window is visible. Positive  
  non-zero color values map to the 255 indices available in overlay mode,  
  these get mapped by the Bits++ CLUT to colors. You can define the  
  mapping of indices to CLUT colors via the  
  [Screen](Screen)('LoadNormalizedGammaTable', window, clut, 2); command.  
  
  Updates of the overlay image are synchronized to [Screen](Screen)('[Flip](Flip)')  
  updates. If you draw into the overlay window, the changed overlay image  
  will become visible at [Screen](Screen)('[Flip](Flip)') time -- in sync with the changed  
  onscreen window content. The overlay plane is not automatically cleared  
  to background (or transparent) color after a flip, but its content  
  persists across flips. You need to clear it out manually via a  
  [Screen](Screen)('FillRect') command.  
  
  
\* 'EnableBits++Color++Output' Enable the high-performance driver for the  
  Color++ mode of Cambridge Research Systems Bits++ box. This is the  
  fastest and most elegant way of driving the Bits++ box with 14 bit  
  per color channel output precision. See "help [BitsPlusPlus](BitsPlusPlus)" for more  
  information. Selecting this mode implies use of 32 bit floating point  
  framebuffers, unless you specify use of a 16 bit floating point  
  framebuffer via 'FloatingPoint16Bit' explicitely. If you do that, you  
  will not be able to use the full 14 bit output precision of Bits++, but  
  only approximately 10 bits.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'EnableBits++Color++Output', mode);  
  
  "mode" is a mandatory numeric parameter which must be 0, 1 or 2. In  
  Color++ mode, the effective horizontal display resolution is only half  
  the normal horizontal resolution. To cope with this, multiple different  
  methods are implemented to squeeze your stimulus image horizontally by  
  a factor of two. The following options exist:  
  
  0 = This is the "classic" mode which was used in all Psychtoolbox  
  versions prior to 22nd September 2010. If you want to keep old code  
  working as is, select 0. In this mode, your script will only see a  
  framebuffer that is half the true horizontal resolution of your  
  connected display screen. Each drawn pixel will be stretched to cover  
  two pixels on the output display device horizontally. While this  
  preserves the content of your stimulus image exactly, it means that the  
  aspect ratio of all displayed text and stimuli will be 2:1. Text will  
  be twice as wide as its height. Circles or squares will turn into  
  horizontal ellipses or rectangles etc. You'll need to do extra work in  
  your code if you want to preserve aspect ratio properly.  
  
  You can use the [RemapMouse](RemapMouse)() function to correct [GetMouse](GetMouse)() positions  
  for potential geometric distortions introduced by this function for  
  "mode" zero.  
  
  Example: A fine vertical grid with alternating vertical white and black  
  lines would display as expected, but each white or black stripe would be  
  two pixels wide on the display instead of one pixel wide.  
  
  1 = Subsample: Your framebuffer will appear at the same resolution as  
  your display device. Aspect ratio of drawn stimuli/text etc. will be  
  correct and as expected. However, every 2nd column of pixels in your  
  stimulus (ie., all odd-numbered x-coordinates 1,3,5,7,...) will be  
  completely ignored, only even columns are used!  
  
  Example: A fine vertical grid with alternating vertical white and black  
  lines would display as a purely white image, as only the white pixels  
  in the even columns would be used, whereas the black pixels in the odd  
  columns would be ignored.  
  
  2 = Average: Your framebuffer will appear at the same resolution as  
  your display device. Aspect ratio of drawn stimuli/text etc. will be  
  correct and as expected. However, each pair of adjacent even/odd pixel  
  columns will be averaged before output. Stimulus pixels 0 and 1 will  
  contribute the mean color for display pixel 0. Pixels 2 and 3 will be  
  averaged into display pixel 1 and so on. Visually this gives the most  
  pleasing and smooth results, but if adjacent even/odd pixels don't have  
  the same color value, you'll obviously get an output color that is  
  neither the color of the even pixel nor the odd pixel, but the average  
  of both.  
  
  Example: A fine vertical grid with alternating vertical white and black  
  lines would display as a 50% gray image, as the alternating white and  
  black columns would be averaged into the average of white and black,  
  which is 50% gray.  
  
  
\* 'EnableDualPipeHDROutput' Enable EXPERIMENTAL high-performance driver  
  for HDR display devices which are composites of two separate displays.  
  
  EXPERIMENTAL proof-of-concept code with no real function yet!  
  
  This is meant for high-precision luminance or color output. It implies  
  use of 32 bpc floating point framebuffers unless otherwise specified by  
  other calls to [PsychImaging](PsychImaging)().  
  
  The pair of specially encoded output images that are derived from  
  content of the onscreen window shall be output to both, the display  
  associated with the screen given to [PsychImaging](PsychImaging)('OpenWindow',...); and  
  on the screen with the index 'pipe1Screen', using appropriate encoding  
  to drive the HDR device or similar composite device.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'EnableDualPipeHDROutput', pipe1Screen [, pipe1Rectangle]);  
  
  Optionally you can pass a 'pipe1Rectangle' if the window with the  
  pipe1 image shall not fill the whole 'pipe1Screen', but only a  
  subregion 'pipe1Rectangle'.  
  
  
\* 'AddOffsetToImage' Add a constant color- or intensity offset to the  
  drawn image, possibly also multiply with a gain, prior to all following  
  image processing and post-processing operations:  
  
  Outimage(x,y) = (Inimage(x,y) + preOffset) \* gain + Offset.  
  
  If the framebuffer is in a color display mode, the same offset will be added  
  to all three color channels.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', whichView, 'AddOffsetToImage', Offset [, gain=1][, preOffset=0]);  
  'gain' and 'preOffset' are optional, 'Offset' is required.  
  
  Example: [PsychImaging](PsychImaging)('AddTask', 'AllViews', 'AddOffsetToImage', 0.5);  
  
  
\* 'MirrorDisplayTo2ndOutputHead' Mirror the content of the onscreen  
  window to the given 2nd screen, ie., to a 2nd video output (head) of a  
  multi-display setup. This should give roughly the same result as if one  
  switches the graphics card into "Mirror mode" or "Clone mode" via the  
  display settings panel of your operating system, but with different  
  tradeoffs. The disadvantage compared to use of an operating system provided  
  mirror mode is that it requires more gpu processing, adding one millisecond to  
  potentially multiple milliseconds of processing time to each [Screen](Screen)('[Flip](Flip)').  
  
  The advantage is that it allows for proper visual stimulation timing and for  
  higher animation framerates in various configurations in which the operating  
  system provided mechanisms would cause impaired timing and drastically reduced  
  or erratic framerates, especially when the subject visual stimulation display  
  and the experimenter feedback mirror display do not have perfectly synchronized  
  video refesh cycles, e.g., because the two displays are not the same model and  
  vendor, or can't be set to the same video resolution and refresh rate, or  
  can't be connected both to the same type of video link (e.g. not both via  
  [DisplayPort)](DisplayPort)), or operating system limitations prevent synchronized scanout.  
  Non-synchronized video refresh can cause broken timing, strong judder of  
  animations or severely reduced framerate, e.g., if a 60 Hz experimenter  
  display throttles all animations down to 60 fps, even though the subjects  
  stimulus display is configured for 120 Hz operation. This mode will run the  
  main window for stimulus presentation with proper timing and vsync, whereas  
  it runs the experimenter feedback "mirror" display without vsync, allowing  
  for tearing artifacts to happen, in exchange for optimal timing and performance  
  on the main display.  
  
  Another advantage is that this allows to display an overlay window on top of  
  the visual stimulus mirror image, to supply some additional debug information  
  to the experimenter. Operating system provided mirror modes don't allow for  
  such overlays.  
  
  This function only works for monoscopic displays and single-window stereo  
  modes (steremode 2 - 9 and some [PsychImaging](PsychImaging) modes), it can not be used with  
  frame-sequential or dual-window / dual-stream stereo display modes, as it  
  internally uses the machinery for stereomode 10 with a few modifications to  
  get its job done, so obviously neither dual-window mode 10 nor any similar  
  mode can be used without interference.  
  
  This function is typically used for mirroring onto a secondary display of a  
  multi-display setup on Apple macOS, or if you need to mirror on Microsoft  
  Windows and can't use "desktop spanning" mode on Windows to achieve dual  
  display output. On Linux/X11, this can be useful in combination with the  
  Vulkan display backend, ie. the 'UseVulkanDisplay' task. On Linux or Windows  
  with a properly synchronized dual-display setup, rather use the task  
  'MirrorDisplayToSingleSplitWindow' (see below). That task should work  
  well on in synchronized mode, and is more efficient. It would also work well  
  in conjunction with a hardware display splitter attached to a single  
  head on any operating system. It has the advantage of consuming less  
  memory and compute ressources, so it is potentially faster or provides  
  a more reliable overall timing. On modern Linux distributions with X-Server  
  version 21 or later, e.g., Ubuntu 22.04-LTS or later, that more efficient  
  mode can also be made to work, after special setup with [XOrgConfCreator](XOrgConfCreator), on  
  unsynchronized displays.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'MirrorDisplayTo2ndOutputHead', mirrorScreen [, mirrorRectangle=[]][, specialFlags=0][, useOverlay=0]);  
  
  The content of the onscreen window shall be shown not only on the  
  display associated with the screen given to [PsychImaging](PsychImaging)('OpenWindow',  
  ...); but also (as a copy) on the screen with the index 'mirrorScreen'.  
  
  Optionally you can pass a 'mirrorRectangle' if the window with the  
  mirror image shall not fill the whole 'mirrorScreen', but only a  
  subregion 'mirrorRectangle'.  
  
  'specialFlags' are optional flags to customize the mirror window, similar to  
  the specialFlags parameter of [PsychImaging](PsychImaging)('OpenWindow', ...., specialFlags).  
  Cfe. flags like kPsychGUIWindow and kPsychGUIWindowWMPositioned to turn the  
  experimenter feedback mirror window into a regular desktop GUI window that  
  can be moved and resized.  
  
  Optionally you can set the 'useOverlay' flag to 1, to request use of an  
  overlay window on top of the mirror window. The function ...  
  overlaywin = [PsychImaging](PsychImaging)('GetMirrorOverlayWindow', win);  
  ... will return a window handle overlaywin for a given onscreen window win,  
  and you can then use overlaywin for drawing content into that overlay.  
  
\* 'MirrorDisplayToSingleSplitWindow' Mirror the content of the onscreen  
  window to the right half of the desktop (if desktop spanning on a  
  dual-display setup is enabled) or the right-half of the virtual screen  
  if a display splitter (e.g., Matrox [Dualhead2Go](Dualhead2Go) (TM)) is attached to a  
  single head of a graphics card. This should give the same result as if one  
  switches the graphics card into "Mirror mode" or "Clone mode" via the  
  display settings panel of your operating system. It offers the same tradeoffs  
  and advantages as explained above for 'MirrorDisplayTo2ndOutputHead' mode.  
  The 'MirrorDisplayToSingleSplitWindow' task may be a bit more efficient than  
  'MirrorDisplayTo2ndOutputHead', but it requires either use of a modern Linux  
  distribution like Ubuntu 22.04-LTS with X-Server 21, and some configuration  
  with [XOrgConfCreator](XOrgConfCreator), or the use of two display devices of identical  
  model from the same vendor, set to exactly the same video mode  
  (resolution and refresh rate), and identical video connections, so the  
  video refresh cycles of both the stimulus presentation display, and the  
  experimenter feedback mirror display are perfectly synchronized with  
  each other. Otherwise timing and performance will be less than optimal!  
  If you can't meet these conditions then the 'MirrorDisplayTo2ndOutputHead'  
  task is the better choice, at expense of higher gpu load.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', 'General', 'MirrorDisplayToSingleSplitWindow' [, useOverlay=0][, mirrorDestination]);  
  
  Optionally you can set the 'useOverlay' flag to 1, to request use of an  
  overlay window on top of the mirrored stimulus. The function ...  
  overlaywin = [PsychImaging](PsychImaging)('GetMirrorOverlayWindow', win);  
  ... will return a window handle overlaywin for a given onscreen window win,  
  and you can then use overlaywin for drawing content into that overlay.  
  
  Optionally you can provide the 'mirrorDestination' parameter to specify  
  where the mirror image should go within the onscreen window, and which  
  size it has. By default, the mirror image will fill out the right half  
  of the onscreen window, an appropriate choice if your mirror display  
  monitor has the same resolution as the stimulus display monitor and  
  both are arranged side-by-side in a dual-display setup. For different  
  monitor arrangements, e.g., triple-display setups or similar, of for  
  different selected mirror monitor resolutions, a future Psychtoolbox  
  release may also select a proper location and size for the mirror  
  image. But for now, if your mirror monitor has a different resolution  
  than the stimulus monitor, you need to manually specify the mirror  
  monitors resolution, ie. width x height in pixels as mirrorDestination  
  parameter, a two-component row vector of form [width, height]., so the  
  mirror image can get appropriately scaled to the resolution of the  
  mirror monitor. On Linux you will also need to use the [SetResolution](SetResolution)()  
  function to set a horizontal resolution that is twice the horizontal  
  resolution of your stimulus monitor(s). E.g., if your stimulus monitor  
  is 2560x1440 resolution and your mirror monitor is 1280x1024 pixels,  
  and both are attached to Psychtoolbox screen 1 (aka X-[Screen](Screen) 1), you'd  
  have to call [SetResolution](SetResolution)(1, 2\*2560, 1440); before 'OpenWindow', and  
  specify 'mirrorDestination' as [1280, 1024]. A setup with three  
  monitors, two stimulus monitors next to each other at 2560x1440 pixels  
  each, plus one mirror monitor of 1280x1024 right to the both stimulus  
  monitors would instead require a call to  
  [SetResolution](SetResolution)(1, 2 \* (2560 + 2560), 1440). Note that setups which  
  require specification of 'mirrorDestination' may not work at all at the  
  moment on systems other than Linux.  
  
  Optionally, if you don't need the imaging pipeline and don't need the overlay  
  for experimenter feedback, ie. you let 'useOverlay' = 0, you can add ...  
  [PsychImaging](PsychImaging)('AddTask', 'General', 'DontUsePipelineIfPossible');  
  ... if you don't intend to use the imaging pipeline for anything else  
  than display mirroring. This will allow further optimizations.  
  
  
\* 'RestrictProcessing' Restrict stimulus processing to a specific subarea  
  of the screen. If your visual stimulus only covers a subarea of the  
  display screen you can restrict PTB's output processing to that  
  subarea. This may save some computation time to allow for higher  
  display redraw rates.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', whichChannel, 'RestrictProcessing', ROI);  
  
  ROI is a rectangle defining the area to process ROI = [left top right bottom];  
  E.g., ROI = [400 400 800 800] would only create output pixels in the  
  screen area with top-left corner (400,400) and bottom-right corner  
  (800, 800).  
  
  
\* 'FlipHorizontal' and 'FlipVertical' flip your output images  
  horizontally (left- and right interchanged) or vertically (upside down).  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', whichChannel, 'FlipHorizontal');  
  Usage: [PsychImaging](PsychImaging)('AddTask', whichChannel, 'FlipVertical');  
  
  You can use the [RemapMouse](RemapMouse)() function to correct [GetMouse](GetMouse)() positions  
  for potential geometric distortions introduced by this function.  
  
  
\* 'GeometryCorrection' Apply some geometric warping operation during  
  rendering of the final stimulus image to correct for geometric  
  distortion of your physical display device. You need to measure the  
  geometric distortion of your display with a suitable calibration  
  procedure, then compute an inverse warp transformation to undo this  
  distortion, then provide that transformation to this function.  
  
  Usage: [PsychImaging](PsychImaging)('AddTask', whichChannel, 'GeometryCorrection', calibfilename [, debugoutput] [, arg1], [arg2], ...);  
  
  'calibfilename' is the filename of a calibration file which specified  
  the type of undistortion to apply. Calibration files can be created by  
  interactive calibration procedures. See 'help CreateDisplayWarp' for a  
  list of calibration methods. One of the supported procedures is, e.g.,  
  "[DisplayUndistortionBezier](DisplayUndistortionBezier)", read "help [DisplayUndistortionBezier](DisplayUndistortionBezier)". The  
  recommended method for most cases is 'DisplayUndistortionBVL', read  
  "help [DisplayUndistortionBVL](DisplayUndistortionBVL)" for help.  
  
  The optional flag 'debugoutput' if set to non-zero value will trigger  
  some debug output about the calibration with some calibration methods.  
  
  The optional 'arg1', 'arg2', ..., are optional parameters whose  
  meaning depends on the calibration method in use.  
  
  Use of geometry correction will break the 1:1 correspondence between  
  framebuffer pixel locations (x,y) and the mouse cursor position, ie. a  
  mouse cursor positioned at display position (x,y) will be no longer  
  pointing to framebuffer pixel (x,y). If you want to know which  
  pixel in your original stimulus image corresponds to a specific  
  physical display pixel (or mouse cursor position), use the function  
  [RemapMouse](RemapMouse)() to perform the neccessary coordinate transformation.  
  
  
\* 'UseVRHMD' Display this onscreen window on a "Virtual Reality" head mounted  
  display (HMD), e.g., the Oculus Rift DK1 or Rift DK2. This enables display of  
  stereoscopic visual stimuli on supported virtual reality headsets.  
  You need to have the neccessary vendor supplied VR runtimes installed for  
  this to work.  
  
###   Simple usage:  
  
  The most simple way to setup a HMD for use is to add a call to  
  hmd = [PsychVRHMD](PsychVRHMD)('AutoSetupHMD') instead of a call to  
  [PsychImaging](PsychImaging)('AddTask', 'General', UseVRHMD', ...). The 'AutoSetupHMD'  
  call would detect the first supported HMD device on your computer, connect to  
  it, then set it up with reasonable default operating parameters. Then it would  
  call this [PsychImaging](PsychImaging) task to perform all required setup steps.  
  
###   Advanced usage:  
  
    1. Open a connection to a HMD and get a handle for the device:  
       For example, if you wanted to use a Oculus Rift DK1 or DK2, you could  
       do:  
  
       hmd = [PsychOculusVR](PsychOculusVR)('Open' ...);  
  
    2. Perform basic configuration of the HMD via the HMD specific driver.  
  
    3. Add a [PsychImaging](PsychImaging) task for the HMD and pass in its device handle 'hmd':  
       [PsychImaging](PsychImaging)('AddTask', 'General', 'UseVRHMD', hmd);  
  
  This sequence will perform the necessary setup of panel fitter, stereo display  
  mode and image post-processing for geometry correction, color aberration  
  correction and vignette correction for a fullscreen window on the HMD.  
  
  
\* 'UseVulkanDisplay' Display this onscreen window using a Vulkan-based display  
  backend. This only works on graphics card + operating system combinations  
  which support both the [OpenGL](OpenGL) and Vulkan rendering api's and [OpenGL](OpenGL)-Vulkan  
  interop. As of March 2023 this would be modern AMD, Intel, and [NVidia](NVidia) graphics  
  cards under modern GNU/Linux (Ubuntu 22.04-LTS and later) and under Microsoft  
  Windows-10 and later. Very experimental support for the curious is also possible  
  on the [RaspberryPi](RaspberryPi) 4/400 and later with Mesa 23.1 or later, but this support  
  does not have any advantages over standard mode, quite the contrary! See  
  'help RaspberryPiSetup' if you wanted to try it anyway.  
  
  Apple macOS 10.15.4 Catalina and later is also supported if you install the  
  3rd party Khronos open-source [MoltenVK](MoltenVK) "Vulkan on Metal" driver. However, this  
  support is very unreliable wrt. stimulus timing at least on macOS 10/11/12, due  
  to severe bugs in Apple's macOS 10/11 Metal graphics api, which only Apple could  
  fix. Performance is also miserable, achieving at most a framerate that is half  
  the video refresh rate of the display monitor. The status on macOS 13 is unknown  
  as of March 2023. Do not ask us for help in using this on macOS, don't trust it!  
  
  At the moment 'UseVulkanDisplay' does not provide any advantages for standard  
  visual stimulus display tasks. It can be of some benefit if one employs display  
  mirroring on Linux/X11 via the 'MirrorDisplayTo2ndOutputHead' task, or wants to  
  flexibly operate multi-display setups under Linux/X11. It also provides very high  
  precision framebuffers under Linux with AMD graphics cards and the AMDVLK Vulkan  
  driver via the 'EnableNative16BitFramebuffer' task. For other more standard tasks,  
  it is of no benefit right now and may reduce performance instead.  
  
###   Usage:  
  
  [PsychImaging](PsychImaging)('AddTask', 'General', 'UseVulkanDisplay');  
  
  Psychtoolbox will try to display the onscreen window by using a Vulkan driver  
  with Vulkan/WSI backend, instead of the usual [OpenGL](OpenGL) windowing system backend.  
  This may fail if the given system setup does not support this.  
  
  
\* 'EnableHDR' Display this onscreen window on a "High dynamic range" (HDR) display.  
  This requires a combination of operating-system, display drivers, graphics card,  
  video cables and display devices which are at least HDR-10 capable.  
  
  For hardware and system requirements, setup instructions, and further explanations  
  read "help [PsychHDR](PsychHDR)".  
  
###   Usage:  
  
  [PsychImaging](PsychImaging)('AddTask', 'General', 'EnableHDR' [, unit='Nits'][, hdrMode='Auto'][, extraRequirements]);  
  
###   Optional parameters:  
  
  'unit'  The unit in which color values are specified by the users drawing code.  
          Default value is 'Nits', ie. 1 unit = 1 Nit = 1 candela per square-meter.  
          '80Nits', ie. 1 unit = 80 Nits = 80 cd/sqm = Supposedly the SDR range.  
  
  'hdrMode' General mode of operation for HDR display:  
            Default is 'Auto' for auto-selection of optimal mode for given system  
            configuration, selected out of the following available op-modes:  
  
            'HDR10' Standard HDR-10, with 10 bpc color precision, ITU Rec 2020 input  
            color space (aka BT-2020), SMPTE ST-2084 PQ "Perceptual Quantizer" OETF  
            transfer function.  
  
            -\> Currently 'Auto' will select 'HDR-10' as the only supported op-mode.  
  
  'extraRequirements' String with various keywords to specify special requirements.  
                      Default is empty, ie. no extra requirements. Currently supported  
                      keywords are:  
  
                      'Dummy' - Only simulate HDR on a SDR standard dynamic range display.  
                                This only performs setup steps and processing possible on  
                                a SDR display, to allow for basic script development and  
                                testing. Visual results will be obviously wrong!  
  
  
\* 'UseStaticHDRHack' Use a Linux + X11 only HDR display setup hack to allow multi-display  
  HDR presentation, e.g., for dual-HDR-monitors setups with two identical HDR monitors  
  or display devices for binocular or stereoscopic HDR visual stimulation.  
  
  Currently our Vulkan-based HDR display backend does not yet support proper dual-display/  
  multi-display stereo presentation in a proper way. As a stop-gap solution until we have  
  proper support implemented, this task requests use of a Linux + X11 specific hack to make  
  HDR stereo presentation work ok. The hack is a hack, not guaranteed to work on your setup,  
  or even if it works it is not guaranteed to work permanently, e.g. across operating system  
  updates. Use of this highly experimental hack is at your own risk, you have been warned!  
  Also note that using this [PsychImaging](PsychImaging) tasks will make your script non-portable to other  
  operating systems than Linux or other display systems than X11 (e.g., Wayland) for the time  
  being. Another limitation is that this only works with 10 bpc HDR-10 precision framebuffers,  
  not with the higher precision 16 bit floating point framebuffers offered by standard HDR  
  mode. This hack will be limited permanently to HDR-10 with static HDR metadata and 10 bit  
  precision. It will eventually be superseded by a proper multi-display/stereo HDR implementation,  
  if and when we get funding to work on this.  
  
###   To setup HDR-10 display with this hack:  
  
  0. You \*must\* install GNU/Octave and setup Psychtoolbox for use with GNU/Octave! Even if  
     you prefer to run your scripts in Matlab, Octave is needed as a background helper! In  
     general we recommend using Octave for this special hack, as Matlab's GUI is currently  
     incompatible with 10 bit display mode as of R2020b. It will misrender, crash or simply  
     hang! The only way to use Matlab here is without GUI in the terminal window by launching  
     Matlab via "matlab -nodesktop". In this case, using Octave in the first place may be  
     more convenient, as Octave's GUI works just fine!  
  
  1. Connect identical models of HDR monitors to your X-[Screen](Screen) 0, or at your leisure,  
     create a separate X-[Screen](Screen) for stimulation by use of [XOrgConfCreator](XOrgConfCreator). It is important  
     that the X-[Screen](Screen) used for visual HDR stimulation only has HDR monitors connected, no  
     other monitors, iow. the same configuration as if you'd do multi-display stereo stimulation  
     for standard dynamic range stimuli under Linux.  
  
  2. Use [XOrgConfCreator](XOrgConfCreator) to create a separate X-[Screen](Screen) - or setup your one and only X-[Screen](Screen) 0  
     to use 10 bpc, color depth 30 bit mode. If the [XOrgConfCreator](XOrgConfCreator) asks you if you want to  
     setup advanced settings, answer "y"es, and then when it asks for 10 bpc / 30 bit deep  
     color support, answer "y"es and select all X-Screens which will be used for HDR stimulation.  
  
  3. Select this HDR-10 10 bit configuration via [XOrgConfSelector](XOrgConfSelector), logout and login again to  
     get your single or multi-X-[Screen](Screen) setup with the X-[Screen](Screen) to which the HDR displays are  
     connected running in 10 bpc color depth.  
  
  4. Now you can use a regular HDR script, but add the [PsychImaging](PsychImaging)('AddTask', 'General', 'UseStaticHDRHack')  
     task before opening the onscreen window. Also select a stereoMode of 4 for dual-display stereo  
     stimulation in [PsychImaging](PsychImaging)('OpenWindow', ..., stereoMode);  
  
  5. All connected HDR monitors should switch to HDR mode and the onscreen window should be setup  
     for stereo stimulus display across HDR monitors, as usual.  
  
  If these steps don't work for you, too bad. If they work, great.  
  
  This mode will only allow slow switching of different HDR metadata settings via [PsychHDR](PsychHDR)('HDRMetadata'),  
  and each switch of settings will be slow and accompanied by flicker. For this reason you can  
  also assign the meta-data as part of the 'UseStaticHDRHack' setup as optional hdrStaticMetadata  
  struct. The same HDR metadata will be applied to all connected HDR monitors for a window / X-[Screen](Screen).  
  Other limitations may apply, and this functionality is so far only tested on one HDR setup.  
  
###   Usage:  
  
  [PsychImaging](PsychImaging)('AddTask', 'General', 'UseStaticHDRHack' [, hdrStaticMetadata]);  
  
  
\* More actions will be supported in the future. If you can think of an  
  action of common interest not yet supported by this framework, please  
  file a feature request on our Wiki (Mainpage -\> Feature Requests).  
  
  
After adding all wanted task specifications and other requirements,  
call...  
  
[windowPtr, windowRect] = [PsychImaging](PsychImaging)('OpenWindow', screenid, [backgroundcolor], ....);  
  
- Finishes the setup phase for imaging pipeline, creates a suitable onscreen  
window and performs all remaining configuration steps. After this  
command, your onscreen window will be ready for drawing and display of  
stimuli. All specified imaging operations will get automatically applied  
to your stimulus before stimulus onset.  
  
  
After the window has been opened you can call the following commands any  
time at runtime:  
  
[PsychImaging](PsychImaging)('RestrictProcessingToROI', window, whichChannel, ROI);  
- Restrict the processing area of viewChannel 'whichChannel' of onscreen  
window 'window' to the rectangular subarea defined by 'ROI'. See the  
explanation above for subtask 'RestrictProcessing'. This does exactly the  
same but allows a dynamic change of the restricted area at any point  
during your experiment script.  
  
  
[PsychImaging](PsychImaging)('UnrestrictProcessing', window, whichChannel);  
- Remove a restriction of the processing area of viewChannel  
'whichChannel' of onscreen window 'window' to a previously defined  
subarea. Can be called anytime during your scripts execution.  
  
  
[overlaywin, overlaywinRect] = [PsychImaging](PsychImaging)('GetOverlayWindow', win);  
- Will return the handle to the 'overlaywin'dow associated with the  
given 'win'dow, if any. Will abort with an error message if the 'win'dow  
doesn't have an associated overylay window.  
Currently, only the CRS Bits+ box in Mono++ mode and the [VPixx](VPixx) [DataPixx](DataPixx)  
box in M16 mode does support overlays. Other output drivers don't support  
such a feature. See "help [BitsPlusPlus](BitsPlusPlus)" for subfunction  
'GetOverlayWindow' for more explanations of the purpose and properties of  
overlay windows. The explanations apply to the [DPixx](DPixx) device as well if it  
is opened in videomode 'M16WithOverlay'.  
  
  
overlaywin = [PsychImaging](PsychImaging)('GetMirrorOverlayWindow', win);  
- Will return the handle to the mirror 'overlaywin'dow associated with the  
given 'win'dow, if any. Will abort with an error message if the 'win'dow  
doesn't have an associated mirror overylay, because the 'win'dow was not  
configured for mirror mode, or for use of an overlay on its mirror window.  
Cfe. the [PsychImaging](PsychImaging) stimulus mirroring tasks 'MirrorDisplayTo2ndOutputHead'  
and 'MirrorDisplayToSingleSplitWindow' for use cases.  
  
  
  
### The following commands are only for specialists:  
  
[imagingMode, needStereomode] = [PsychImaging](PsychImaging)('FinalizeConfiguration');  
- Finish the configuration phase for this window. This will compute an  
optimal configuration for all stages of the pipeline, but won't apply it  
yet. You'll have to call [Screen](Screen)('OpenWindow', windowPtr, ......,  
imagingMode, ...); with the returned 'imagingMode' + any other options  
you'd like to have for your window. After that, you'll have to call  
[PsychImaging](PsychImaging)('PostConfiguration') to really apply and setup all your  
configuration settings. If you don't have unusual needs, you can simplify  
these steps by simply calling [PsychImaging](PsychImaging)('OpenWindow', ....);  
with the same parameters that you'd pass to [Screen](Screen)('OpenWindow', ....);  
[PsychImaging](PsychImaging) will perform all necessary steps to upon return, you'll have  
your window properly configured.  
  
  
[PsychImaging](PsychImaging)('PostConfiguration', windowPtr [, clearcolor]);  
- To be called after opening the onscreen window 'windowPtr'.  
Performs all the setup work to be done after the window was created.  
  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/PsychImaging.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/PsychImaging.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/PsychImaging.m</code>
</div>

