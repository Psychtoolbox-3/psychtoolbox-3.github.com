# [PsychVulkanCore('OpenWindow')](PsychVulkanCore-OpenWindow) 
##### [Psychtoolbox](Psychtoolbox)>[PsychVulkanCore](PsychVulkanCore).{mex*} subfunction

vulkanWindow = PsychVulkanCore('OpenWindow', gpuIndex, targetUUID, isFullscreen, screenId, rect, outputHandle, hdrMode, colorPrecision, refreshHz, colorSpace, colorFormat, flags);

Open a display window on a Vulkan device.  
  
'gpuIndex' is the index of the Vulkan gpu that should be used for displaying the  
window. Devices are numbered 1 to [PsychVulkanCore](PsychVulkanCore)('GetCount'). A value of zero  
means to auto-detect the proper gpu + driver combo, given all other passed in  
parameters.  
'targetUUID' A 16 byte uint8() vector with the unique device id UUID which  
identifies the gpu hardware. This is needed for [OpenGL](OpenGL) + Vulkan interoperation,  
so [Screen](Screen)() can pass images for presentation to this driver. The UUID of the  
[OpenGL](OpenGL) gpu used by [Screen](Screen)() for rendering and the Vulkan gpu used for  
presentation must match for this to work, hence [Screen](Screen)() needs to provide the  
proper 'targetUUID' to use here. The proper 'targetUUID' can be set as  
winfo.[GLDeviceUUID](GLDeviceUUID) with winfo queried as winfo = [Screen](Screen)('GetWindowInfo', window)  
for a given [Screen](Screen) onscreen 'window'. The special targetUUID = zeros(1, 16,  
'uint8'); can be used to match any gpu.  
'isFullscreen' Open a fullscreen exclusive window if set to 1, a windowed window  
if set to 0. Proper presentation timing and timestamping, HDR display and  
similar is often only possible with fullscreen exclusive mode.  
'screenId' The 'screenId' of the presentation monitor or screen, as used in  
[Screen](Screen)('Openwindow', screenId) ...  
'rect' The [left, top, right, bottom] bounding rectangle of the presentation  
windows client area. Should match the rectangle covered of the desktop or screen  
of a display monitor for fullscreen exclusive mode. Defines the window location  
in windowed mode.  
'outputHandle' Handle defining the video output surface to use, in an operating  
system dependent manner: On MS-Windows the parameter is currently ignored. On  
Linux X11 in windowed mode, it must be the X11 window handle of the window to  
which we want to display (cfe. [Screen](Screen)('GetWindowInfo', ...);. On Linux in X11  
fullscreen mode, it must be the [RandR](RandR) output XID for the video output to which  
we want to display in fullscreen mode.  
'hdrMode' Which HDR display mode, if any, to set up for: 0 = No HDR mode, SDR  
display. 1 = HDR-10. This will also determine presets for 'colorPrecision',  
'colorSpace' and 'colorFormat' depending on selected mode, if those arguments  
are set to auto-select. E.g., hdrMode == 1 for HDR-10 enforces at least  
'colorPrecision' 1 for at least 10 bpc output, and selects a HDR10 color space  
with BT2020 color gamut and SMPTE ST-2084 PQ eotf encoding.  
'colorPrecision' Required output framebuffer (swapchain) precision. For HDR  
display modes, will be forced to at least 1 for at least 10 bpc precision:  
0 = 8 bpc fixed point linear RGBA8, unorm  
1 = 10 bpc fixed point linear RGB10A2, unorm  
2 = fp16 RGBA16F half-float  
3 = 16 bpc fixed point linear RGBA16, unorm  
4 = Try all deep-color unorm precisions from highest to lowest: RGBA16 -\>  
RGB10A2  
  
5 = Try all deep-color precisions (unorm and fp16) from highest to lowest:  
RGBA16 -\> RGBA16F -\> RGB10A2  
6 = Try fp16, then 10 bpc unorm: RGBA16F -\> RGB10A2  
Values 0 - 3 request the exact precision, and fail window creation if the system  
does not support them.  
Values 4 - 6 request the highest precision, then fall back to lower precisions  
if the system does not support them, and fail if the lowest precision in the  
sequence is not supported either. E.g., A value of 6 would aim for fp16, for  
more than 10 bpc effective output precision, but fall back to 10 bpc if fp16 is  
not supported. It would abort though if 10 bpc would not be supported either.  
This is a good choice for HDR display modes with the highest possible precision  
that a given operating system + Vulkan driver + gpu + display cable + display  
combination supports.  
'refreshHz' The desired video refresh rate for fullscreen windows. May have no  
effect in windowed mode.  
'colorSpace' The output color space to assume / select as [VkColorSpace](VkColorSpace) id. If  
zero, then will be set automatically according to 'hdrMode', e.g.,  
VK\_COLOR\_SPACE\_SRGB\_NONLINEAR\_KHR in hdrMode 0, VK\_COLOR\_SPACE\_HDR10\_ST2084\_EXT  
in hdrMode 1 (=HDR10).  
'colorFormat' NOT USED YET! The pixel output color format to use as [VkFormat](VkFormat)  
color format id. If empty, then will be set automatically according to  
'colorPrecision' and/or 'hdrMode'.  
'flags' Special mode selection flags or'ed together: +1 = Diagnostic display  
only, no [Screen](Screen)() [OpenGL](OpenGL) interop, just show an alternating black-white test  
image. Useful for most basic Vulkan testing and driver bringup if the given gpu  
does not have graphics drivers with [OpenGL](OpenGL)+Vulkan interop capabilities yet.  
+2 = Do not switch to fullscreen-exclusive mode on MS-Windows, even for  
fullscreen windows. This is useful as workaround for some buggy Vulkan drivers.  
  
  
Returns: The 'vulkanWindow' handle of the Vulkan presentation window.  
  


###See also:
[CloseWindow](PsychVulkanCore-CloseWindow)
