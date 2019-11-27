# [Screen('GetWindowInfo')](Screen-GetWindowInfo) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

info = Screen('GetWindowInfo', windowPtr [, infoType=0] [, auxArg1]);

Returns a struct with miscellaneous info for the specified onscreen window.  
  
"windowPtr" is the handle of the onscreen window for which info should be  
returned.  
  
"infoType" If left out or set to zero, all available information for the  
'windowPtr' is returned.  
  
If set to 1, only the rasterbeam position of the associated display device is  
returned (or -1 if unsupported).  
  
If set to 2, information about the window server is returned (or -1 if  
unsupported).  
  
If set to 3, low-level window server settings are changed according to  
'auxArg1'. Do \*not\* use, unless you really know what you're doing and have read  
the relevant PTB source code!  
  
If set to 4, returns a single value with the current activity status of  
asynchronous flips. 1 if a [Screen](Screen)('AsyncFlipBegin') was called and the flip is  
still active, ie., hasn't been finished with a matching [Screen](Screen)('AsyncFlipEnd')  
or [Screen](Screen)('AsyncFlipCheckEnd');, zero otherwise.You can call this function with  
an infoType of zero only if no async flips are active, or if the imaging  
pipeline is fully enabled. This is why you need to use the special infoType 4 to  
find out if async flips are active.  
  
If set to 5, will start measurement of GPU time for render operations. The clock  
will start on the next drawing command after this call. The clock will by  
default stop at the next call to [Screen](Screen)('[Flip](Flip)'), [Screen](Screen)('AsyncFlipBegin'), or  
[Screen](Screen)('DrawingFinished'). Measured time will include all the time spent by the  
GPU for preparing the final visual stimulus image for the next flip, including  
all post-processing operations performed by the imaging pipeline.  
  
If you want to exclude time spent in image post-processing or just measure the  
time spent for a defined set of drawing commands, you can stop the clock earlier  
by calling this function with infoType set to 6. In that case, only GPU time  
spent between the infoType=5 call and the infoType=6 call will be reported,  
excluding any later drawing commands or imaging pipeline post-processing.  
  
After the measured GPU operations complete, the elapsed rendertime will be  
returned in the 'GPULastFrameRenderTime' field of the struct that you get when  
calling with infoType=0.  
Due to the asynchronous nature of GPU rendering, the measured time may not be  
immediately available after the clock is stopped. In this case,  
'GPULastFrameRenderTime' will be zero and you will need to repeat the infoType=0  
query later.  
Please note that not all GPU's and operating systems support this function. If  
the function is unsupported, a value of zero will be returned in the info struct  
and by any call with 'infoType' of 5 or 6.  
  
An 'infoType' of 7 does return the same information as the default 'infoType' 0,  
but does not set the window 'windowPtr' as drawing target, does not activate its  
[OpenGL](OpenGL) context and only returns information that is safe to return without  
setting the window as drawing target.  
  
An 'infoType' of 8 returns 1 if the X-Screens primary gpu uses the  
modesetting-ddx under Linux.  
  
The info struct contains all kinds of information. Just check its output to see  
what is returned. Most of this info is not interesting for normal users, mostly  
provided for internal use by M-Files belonging to Psychtoolbox itself, e.g.,  
display tests.  
  
# The info struct contains the following fields  
  
[BeamPosition](BeamPosition): Current rasterbeam position of the video scanout cycle.  
[LastVBLTimeOfFlip](LastVBLTimeOfFlip): VBL timestamp of last finished [Screen](Screen)('[Flip](Flip)') operation.  
[TimeAtSwapRequest](TimeAtSwapRequest): Timestamp taken prior to submission of the low-level swap  
command. Useful for micro-benchmarking.  
[TimePostSwapRequest](TimePostSwapRequest): Timestamp taken after submission of the low-level swap  
command. Useful for micro-benchmarking.  
[VBLTimePostFlip](VBLTimePostFlip): Optional flip completion timestamp from VBLANK timestamping.  
Useful for micro-benchmarking.  
[OSSwapTimestamp](OSSwapTimestamp): Optional flip completion timestamp from OS-Builtin  
timestamping. Useful for micro-benchmarking.  
[GPULastFrameRenderTime](GPULastFrameRenderTime): Duration of all rendering operations, as measured by  
GPU, if infoType=5 was used.  
[RawSwapTimeOfFlip](RawSwapTimeOfFlip): Raw (uncorrected by high-precision timestamping) timestamp of  
last finished [Screen](Screen)('[Flip](Flip)') operation.  
[LastVBLTime](LastVBLTime): System time when last vertical blank happened, or the same as  
[LastVBLTimeOfFlip](LastVBLTimeOfFlip) if the system doesn't support queries of this property  
(currently only OS/X does.)  
[VBLCount](VBLCount): Running count of vertical blank intervals since (graphics)system  
startup. Or zero if notsupported by system. Currently only OS/X and Linux do  
support this with some GPU's.  
[VideoRefreshFromBeamposition](VideoRefreshFromBeamposition): Estimate of video refresh cycle from beamposition  
measurement method.  
[GLVendor](GLVendor), [GLRenderer](GLRenderer), [GLVersion](GLVersion): Vendor name, renderer name and version of the  
[OpenGL](OpenGL) implementation.  
[StereoMode](StereoMode): Currently selected stereomode, as requested in call to  
[Screen](Screen)('OpenWindow', ...);  
[StereoDrawBuffer](StereoDrawBuffer): Current drawbuffer for stereo display (0 = left eye, 1 = right  
eye, 2 = None in mono mode).  
[ImagingMode](ImagingMode): Currently selected imging pipeline mode, as requested in call to  
[Screen](Screen)('OpenWindow', ...);  
[MultiSampling](MultiSampling): Currently selected multisample anti-aliasing mode, as requested  
in call to [Screen](Screen)('OpenWindow', ...);  
[MissedDeadlines](MissedDeadlines): Number of missed [Screen](Screen)('[Flip](Flip)') stimulus onset deadlines,  
according to internal skip detector.  
[FlipCount](FlipCount): Total number of flip command executions, ie., of stimulus updates.  
[GuesstimatedMemoryUsageMB](GuesstimatedMemoryUsageMB): Estimated memory usage of window or texture in  
Megabytes. Can be very inaccurate or unavailable!  
[VBLStartLine](VBLStartLine), [VBLEndline](VBLEndline): Start/Endline of vertical blanking interval. The  
[VBLEndline](VBLEndline) value is not available/valid on all GPU's.  
[SwapGroup](SwapGroup): Swap group id of the swap group to which this window is assigned.  
Zero for none.  
[SwapBarrier](SwapBarrier): Swap barrier id of the swap barrier to which this windows swap  
group is assigned. Zero for none.  
[SysWindowHandle](SysWindowHandle): Low-level windowing system specific window handle of the  
onscreen window. Currently Linux/X11 only: The X-Window handle.  
[ExternalMouseMultFactor](ExternalMouseMultFactor): Scaling factor to apply for remapping input coordinates  
on some systems, e.g., by [RemapMouse](RemapMouse).m.  
  
The following settings are derived from a builtin detection heuristic, which  
works on most common GPU's:  
  
[GPUCoreId](GPUCoreId): Symbolic name string that roughly describes the name of the GPU core  
of the graphics card. This string is arbitrarily  
chosen to roughly group the cores by common capabilities (and quirks). Currently  
defined are:  
R100 = Very old ATI [GPUs](GPUs), R300 = GPU's roughly starting at Radeon 9000, R500 =  
Radeon X1000 or later, R600 = Radeon HD2000 or later.  
NV10 = Very old [NVidia](NVidia) [GPUs](GPUs), NV30 = NV30 or later, NV40 = Geforce6000/7000 or  
later, G80 = Geforce8000 or later.  
An empty [GPUCoreId](GPUCoreId) string means a different, unspecified core.  
  
[DisplayCoreId](DisplayCoreId): Vendor of the display engine / display gpu, [NVidia](NVidia), AMD, Intel,  
or same as 'GPUCoreId'. May differ from 'GPUCoreId' in hybrid graphics laptops.  
[BitsPerColorComponent](BitsPerColorComponent): Effective color depths of window/framebuffer in bits per  
color channel component (bpc).  
[GLSupportsFBOUpToBpc](GLSupportsFBOUpToBpc): 0 = No support for framebuffer objects. Otherwise maximum  
supported bpc (8, 16, 32).  
[GLSupportsBlendingUpToBpc](GLSupportsBlendingUpToBpc): Maximum supported bpc for hardware accelerated  
framebuffer blending (alpha blending).  
[GLSupportsTexturesUpToBpc](GLSupportsTexturesUpToBpc): Maximum supported bpc for textures (8, 16, 32).  
[GLSupportsFilteringUpToBpc](GLSupportsFilteringUpToBpc): Maximum supported bpc for hardware accelerated  
linear filtering of textures (8, 16, 32).  
[GLSupportsPrecisionColors](GLSupportsPrecisionColors): 1 = Hardware can be fully trusted to rasterize  
perfect 32 bpc colors in floating point color mode without special support of  
PTB. 0 = Needs special (slower) support from PTB to work.  
[GLSupportsFP32Shading](GLSupportsFP32Shading): 1 = All internal calculations of the GPU are done with  
IEEE single precision 32 bit floating point, i.e., very accurate.  
[GPUMinorType](GPUMinorType): Numeric vendor specific gpu id. Chip family on [NVidia](NVidia), display  
engine revision on AMD atm. -1 if unknown. Subject to change without notice!  
  
  


###See also:
[OpenWindow](Screen-OpenWindow), Flip, [NominalFrameRate](Screen-NominalFrameRate)
