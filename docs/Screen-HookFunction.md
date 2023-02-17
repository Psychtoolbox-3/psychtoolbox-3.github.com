# [Screen('HookFunction')](Screen-HookFunction) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

[ret1, ret2, ...] = Screen('HookFunction', windowPtr, 'Subcommand', 'HookName', arg1, arg2, ...);

Manage [Screen](Screen) processing hook chains. Hook chains are a way to extend [PTBs](PTBs)  
behaviour with plugins for generic processing or fast image processing. They  
should allow to interface PTB seamlessly with 3rd party special response  
collection devices or stimulus display devices. They also allow to perform high  
performance image processing, utilizing modern graphics hardwares huge  
computational bandwidth. Read 'help PsychGLImageProcessing' for more infos.  
  
  
### Subsubcommands and their syntax:   
  
[Screen](Screen)('HookFunction', [windowPtr], 'ListAll');   
Print out a listing of all supported 'HookName' hook points, including a short  
synopsis on what they do, to the Matlab console in a human readable format -  
Useful as a reference for coding. The 'windowPtr' argument is optional. If left  
out (replaced by empty [] brackets) it prints all implemented chains.  
  
[slot idstring blittercfg voidptr glslid luttexid insertString] =  
[Screen](Screen)('HookFunction', windowPtr, 'Query', hookname, slotnameOrIndex);  
Query information about a specific command slot in a specific hook processing  
chain: 'hookname' is the name of the chain to query, e.g.,  
'StereoCompositingBlit' for the stereo processing chain. Use the subcommand  
'ListAll' for a printout of all available processing hooks and a short help on  
them. 'slotnameOrIndex', either the symbolic name of the requested slot or the  
index in the hook-chain: Indices start with 0. Names can be assigned to slots  
when you add a processing slot with the 'Append' or 'Prepend' command, or they  
are system assigned names like , e.g., 'StereoCompositingShader' for builtin  
shaders that are needed for stereo processing.  
  
Return arguments, all optional: 'slot' is the index of the named slot in the  
chain to which the queried subfunction is assigned, or -1 if no such slot exists  
in the chain. 'glslid' numeric GLSL handle of the [OpenGL](OpenGL) GLSL shader object if  
the slot contains a GLSL shader for image processing on the GPU, 0 otherwise.  
'luttexid' [OpenGL](OpenGL) texture handle of the first assigned lookup texture, 0 if none  
assigned. 'voidptr' Memory pointer (encoded as double) to a C callback function,  
if one is assigned to this slot, 0 otherwise. 'blittercfg' either a parameter  
string with a meaning dependent of slot type, or the string 'NONE' if none  
assigned. 'idstring' The symbolic name of this slot if any assigned, 'NONE'  
otherwise. 'insertString' the subcommand to use for reinserting this slot at the  
place it was after a deletion.  
  
[Screen](Screen)('HookFunction', windowPtr, 'AppendShader', hookname, idString, glslid [,  
blittercfg] [luttexid1]);   
Append a new instruction slot to the end of hook processing chain 'hookname',  
assign the symbolic name 'idString' for later query by the 'Query' command.  
'glslid' must be the name of a valid GLSL program object which defines the  
algorithm to apply on the GPU. 'blittercfg' optional string with configuration  
commands for the shader. 'luttexid' Optional handle to an [OpenGL](OpenGL) texture which  
is used to encode lookup tables for the shader.  
  
[Screen](Screen)('HookFunction', windowPtr, 'PrependShader', hookname idString, glslid [,  
blittercfg] [luttexid1]);   
Same as 'AppendShader' but add shader slot to beginning of the hook chain. It's  
recommended that you prepend slots instead of appending them, because PTB itself  
may add special slots at the end of a chain.  
  
[Screen](Screen)('HookFunction', windowPtr, 'AppendCFunction', hookname, idString,  
voidfunctionptr);   
[Screen](Screen)('HookFunction', windowPtr, 'PrependCFunction', hookname, idString,  
voidfunctionptr);   
Attach a C callable function to the chain. voidfunctionptr is a double value  
which encodes a memory pointer to the function in memory. Encoding of the  
pointer and requirements to the function are non-trivial, so this is for expert  
developers only!  
  
[Screen](Screen)('HookFunction', windowPtr, 'AppendMFunction', hookname, idString,  
fevalstring);   
[Screen](Screen)('HookFunction', windowPtr, 'PrependMFunction', hookname, idString,  
fevalstring);   
Add a Matlab callable function to the chain. 'fevalstring' is the function call  
string: It will be passed to and evaluated by Matlabs or Octaves feval()  
function, so it has to work with that function. It is not allowed to return any  
return arguments. Some special names in the string will be replaced by PTB with  
internal settings, think of it as a macro replacement. Caution: The called  
function is not allowed to call any [Screen](Screen)() commands or you'll likely get  
undefined behaviour or a crash -- [Screen](Screen) is not reentrant!  
  
[Screen](Screen)('HookFunction', windowPtr, 'AppendBuiltin', hookname, idString,  
builtincmd);   
[Screen](Screen)('HookFunction', windowPtr, 'PrependBuiltin', hookname, idString,  
builtincmd);   
Add a call to a PTB built-in function 'builtincmd'.  
  
You can also insert a hook function somewhere at a specific slot index via:  
[Screen](Screen)('HookFunction', windowPtr, 'InsertAtXXXYYY', ...);  
where XXX is a numeric slot id and YYY is the type specifier. Example: Insert a  
Builtin function  
at index 4 in hook 'UserDefinedBlit':  
[Screen](Screen)('HookFunction', windowPtr, 'InsertAt4Builtin', 'UserDefinedBlit', ...);  
  
  
[Screen](Screen)('Hookfunction', windowPtr, 'Remove', hookname, slotindex);  
Remove slot at index 'slotindex' in hookchain 'hookname'. The slot after this  
slot will move up by one.  
  
  
[Screen](Screen)('HookFunction', windowPtr, 'Enable', hookname);   
[Screen](Screen)('HookFunction', windowPtr, 'Disable', hookname);   
Enable or disable a specific hook chain. Chains are disabled until you enable  
them, with the exception of a few internal chains that get initialized and  
enabled by PTB itself, e.g., stereo algorithm chain. Disabled chains are not  
processed.  
  
[Screen](Screen)('HookFunction', windowPtr, 'Reset', hookname);   
Reset a processing hook chain: All slots are deleted, resetting the chain to its  
startup state. Seldomly needed.   
  
[Screen](Screen)('HookFunction', windowPtr, 'Dump', hookname);   
Print out the full chain for hook 'hookname' to the Matlab console in a human  
readable format - Useful for debugging.  
  
[Screen](Screen)('HookFunction', windowPtr, 'DumpAll');   
Print out all chains for the given onscreen window 'windowPtr' to the Matlab  
console in a human readable format - Useful for debugging.  
  
oldImagingMode = [Screen](Screen)('HookFunction', proxyPtr, 'ImagingMode' [,  
imagingMode]);   
Change or query imagingMode flags of provided proxy window 'proxyPtr' to  
'imagingMode'. Proxy windows are used to define image processing operations,  
mostly for [Screen](Screen)('TransformTexture'). Returns old imaging mode.  
  
[leftglHandle, rightglHandle, glTextureTarget, format, multiSample, width,  
height] = [Screen](Screen)('HookFunction', windowPtr, 'SetDisplayBufferTextures' [,  
hookname][, leftglHandle][, rightglHandle][, glTextureTarget][, format][,  
multiSample][, width][, height]);  
Changes the external backing textures and their parameters for the final output  
color buffers of the imaging pipeline.  
Optionally returns the previously used backing textures and their old  
parameters. All new parameters are optional, the old values are left as they  
were if a parameter is not provided.  
This only works if imagingMode flags kPsychNeedFinalizedFBOSinks and  
kPsychUseExternalSinkTextures are set, otherwise external changes are rejected.  
It is not allowed to set a configuration which would cause the underlying  
framebuffers to become framebuffer incomplete. Trying to do so will fail and try  
to revert to the old framebuffer configuration. It is not allowed to switch from  
multisample backing textures to single-sample textures or vice versa, as that  
would cause various processing failures in the image post-processing for a  
stimulus. Setting the kPsychSinkIsMSAACapable imagingMode flag signals that the  
external sink is capable of providing multisample backing textures and desires  
such textures, otherwise only external single-sample textures are desired. The  
implementation will decide if it honors the request for multisample textures,  
depending on general imaging pipeline setup. It may decide to allow MSAA for  
rendering but perform the multiSample resolve step internally. In any case the  
presence of kPsychSinkIsMSAACapable in the final imagingMode for the window  
signals if the caller of this function should provide multisample or single  
sample non-power-of-two textures (GL\_TEXTURE\_2D\_MULTISAMPLE vs. GL\_TEXTURE\_2D).  
The current implementation does not allow for a change in multiSample setting,  
ie., the effective number of samples per pixel for a backing texture. This  
limitation may get relaxed in future versions of the software if possible and  
sensible.  
Parameters and their meaning:  
'hookname' Currently ignored, placeholder for future extensions.  
'leftglHandle' [OpenGL](OpenGL) texture object handle of the left-eye texture in  
stereoMode 12, or of the mono-texture in mono mode.  
'rightglHandle' [OpenGL](OpenGL) texture object handle of the right-eye texture in  
stereoMode 12, or ignored in mono mode.  
'glTextureTarget' [OpenGL](OpenGL) texture target: GL\_TEXTURE\_2D or  
GL\_TEXTURE\_2D\_MULTISAMPLE, depending on multisample configuration.  
'format' [OpenGL](OpenGL) internal texture format, e.g., GL\_RGBA. Must be a framebuffer  
renderable format to prevent framebuffer incompleteness.  
'multiSample' The number of samples per texel. Must be 0 for single-sampled  
GL\_TEXTURE\_2D textures, \> 0 for GL\_TEXTURE\_2D\_MULTISAMPLE textures.  
'width' and 'height' Width and height of the output framebuffer (=texture) in  
pixels or texels.  
  
  
[leftglHandle, rightglHandle, glTextureTarget, format, multiSample, width,  
height, leftFboId, rightFboId] = [Screen](Screen)('HookFunction', windowPtr,  
'GetDisplayBufferTextures');  
Get the [OpenGL](OpenGL) handles of the backing textures and their parameters for the  
final output color buffers of the imaging pipeline.  
'leftFboId' and 'rightFboId' return the ids of the associated [OpenGL](OpenGL) framebuffer  
objects containing the 'leftglHandle' and 'rightglHandle' output textures.  
For the meaning of other return values see 'SetDisplayBufferTextures' above.  
This only works if the imaging pipeline is active.  
This query function works both with internally generated and maintained backing  
textures and externally injected/maintained ones.  
For internally generated textures (without flag kPsychUseExternalSinkTextures),  
the handles should be considered read-only: Binding the textures for  
sampling/reading from them is appropriate, modifying them in any way is  
forbidden.  
  
  
[Screen](Screen)('HookFunction', windowPtr, 'ImportDisplayBufferInteropMemory' [,  
hookname][, viewId=0][, interopMemObjectHandle][, allocationSize][,  
formatSpec][, tilingMode][, memoryOffset][, width][, height][,  
interopSemaphoreHandle]);  
CAUTION: EXPERIMENTAL, UNSTABLE API - Subject to backwards incompatible breaking  
changes without notice!  
[Replace](Replace) the current image backing memory for the final output color buffers of  
the imaging pipeline by externally imported memory.  
This only works if imagingMode flag kPsychNeedFinalizedFBOSinks is set or  
stereoMode 12 is active, which implicitely sets that flag.  
This uses the external memory objects [OpenGL](OpenGL) extension to import external  
backing memory, e.g., from a Vulkan gpu + driver, and assign it as new backing  
memory oject to the textures which are used to implement the final output color  
buffers of the pipeline. Iow. it allows to render into image buffers of an  
external agent, e.g., a Vulkan device instance.  
Parameters and their meaning:  
'hookname' Currently ignored, placeholder for future extensions.  
'viewId' Selects the left-eye/mono framebuffer if 0, and the right-eye  
framebuffer if 1 in a stereoMode 12 configuration.  
'interopMemObjectHandle' Operating system specific handle to the interop image  
backing memory.  
'allocationSize' Number of bytes of backing memory for the  
'interopMemObjectHandle' to import.  
'formatSpec' Type of texture to create: 0 = GL\_RGBA8, 1 = GL\_RGB10A2, 2 =  
GL\_RGBA16F, 3 = GL\_RGBA16.  
'tilingMode' Type of tiling to use/assume for rendering: 0 = Linear (non-tiled),  
1 = Tiled.  
'memoryOffset' Memory offset in bytes into the imported memory object to use.  
'width' Width of texture in pixels.  
'height' Height of texture in pixels.  
'interopSemaphoreHandle' Operating system specific handle to an external  
interop-image-rendering-complete semaphore. If this handle is provided, then  
[Screen](Screen)() will signal the associated [OpenGL](OpenGL) semaphore each time [OpenGL](OpenGL) rendering  
into the imported interop image is finished.  
  
  
[Screen](Screen)('HookFunction', windowPtr, 'SetOneshotFlipFlags' [, hookname],  
flipFlags);  
Assign special flags to be applied one-time during the next execution of  
[Screen](Screen)('[Flip](Flip)') or [Screen](Screen)('AsyncFlipBegin').  
'hookname' is accepted, but currently ignored. Pass '' or [] for now.  
These 'flipFlags' will be applied during the next window flip operation, and  
each applied flag will then auto-reset after application, unless you also pass  
in the kPsychDontAutoResetOneshotFlags to prevent "[OneShot](OneShot)" auto-reset.  
This is mostly meant to be called from within imaging pipeline processing chains  
during preflip operations or the active presentation sequence to modify  
behaviour of that sequence. The following 'flipFlags' are currently implemented:  
kPsychSkipVsyncForFlipOnce, kPsychSkipTimestampingForFlipOnce,  
kPsychSkipSwapForFlipOnce, kPsychSkipWaitForFlipOnce,  
kPsychDontAutoResetOneshotFlags.  
  
  
[Screen](Screen)('HookFunction', windowPtr, 'SetOneshotFlipResults' [, hookname],  
[VBLTimestamp](VBLTimestamp) [, [StimulusOnsetTime](StimulusOnsetTime)=[VBLTimestamp](VBLTimestamp)][, Missed=0][, Beampos=-1]);  
Assign override timestamp values to return from [Screen](Screen)('[Flip](Flip)') or  
[Screen](Screen)('AsyncFlipBegin').  
'hookname' is accepted, but currently ignored. Pass '' or [] for now.  
The provided timestamps will be applied during return from the next window flip  
operation and returned as the corresponding [Screen](Screen)('[Flip](Flip)') return values. You  
must have called the 'SetOneshotFlipFlags' [HookFunction](HookFunction) beforehand with at least  
the kPsychSkipTimestampingForFlipOnce flag to suppress internal timestamping.  
This is mostly meant to be called from within imaging pipeline processing  
chains, notably the 'PreSwapbuffersOperations' hook chain, to inject stimulus  
onset timestamps provided by some external display client or external  
timestamping mechanism. The following values can be injected:  
'VBLTimestamp' The vbl timestamp of [Flip](Flip) completion, or something semantically  
equivalent, useful for [Flip](Flip) scheduling.  
'StimulusOnsetTime' Optional true stimulus onset time. Will be set to  
[VBLTimestamp](VBLTimestamp) if omitted. Must be [StimulusOnsetTime](StimulusOnsetTime) \>= [VBLTimestamp](VBLTimestamp).  
'Missed' The presentation deadline miss estimate aka 'Missed' flag of  
[Screen](Screen)('[Flip](Flip)'). Defaults to 0 if omitted.  
'Beampos' The beamposition at flip completion, as returned in the 'Beampos'  
return argument of [Flip](Flip). Defaults to -1 if omitted.  
  
  
[Screen](Screen)('HookFunction', windowPtr, 'SetWindowBackendOverrides' [, hookname][,  
pixelSize][, refreshInterval][, proj]);  
Assign override values for various window properties, as provided by the backend  
client instead of the windowing system.  
'hookname' is accepted, but currently ignored. Pass '' or [] for now.  
'pixelSize' The net color depth of the display, as returned by  
[Screen](Screen)('PixelSize', windowPtr);  
'refreshInterval' The video refresh interval duration in seconds, as reported by  
the display backend, and after proper translation returned by  
[Screen](Screen)('NominalFramerate', windowPtr), [Screen](Screen)('Framerate', windowPtr), and  
[Screen](Screen)('GetFlipInterval', windowPtr).  
'proj' Override projection matrix/matrices for 2D drawing: proj = [] == don't  
change, proj = 1 == Disable overrides, proj = 4x4 matrix for mono-mode drawing,  
proj = 4x4x2 matrices for separate matrices in stereo modes (:,:,1) left eye,  
(:,:,2) right eye.  
  
  
[maxSDRToHDRScaleFactor, normalizedToHDRScaleFactor] = [Screen](Screen)('HookFunction',  
windowPtr, 'SetHDRScalingFactors' [, hookname][, maxSDRToHDRScaleFactor][,  
normalizedToHDRScaleFactor]);  
Get or assign scaling factors to map SDR color values or HDR color values into  
the linear HDR color range and units of the window.  
'maxSDRToHDRScaleFactor' defines to which color value the maximum input color  
value of SDR content is mapped. This is used by [Screen](Screen)('MakeTexture') for  
converting the color/luminance channels of SDR uint8 image matrices into the  
value range needed for making the texture compatible with the HDR framebuffer.  
It is also used for mapping SDR movie video content to HDR framebuffer. Example:  
A factor of 80 would mean to map the maximum uint8 texture value 255 in  
[MakeTexture](MakeTexture), or the maximum possible component value of the video frame from a  
SDR movie to an output value of 80 units - Typical if the framebuffer operates  
in units of Nits, so maximum SDR content intensity would map to 80 Nits,  
standardized as typical maximum of SDR content.  
'normalizedToHDRScaleFactor' defines to which color value the maximum possible  
input color value of HDR content is mapped. This is used by movie playback to  
map the normalized linear 0.0 - 1.0 intensity range of HDR movies to the linear  
range 0.0 - maximum HDR intensity. A typical value would be 10000 to map the 1.0  
normalized maximum to the maximum intensity of 10000 nits of the current HDR  
display standards HDR10, HDR10+, [DolbyVision](DolbyVision) etc., if the framebuffer uses units  
of Nits. A factor of 125 would be typical if the framebuffer is set up to  
operate in units of multiples of 80 Nits, another common standard, where a value  
of 125 corresponds to 10000 Nits. This scaling factor is also used for  
displaying HDR movie frames into a SDR window, in this scale to upscale some  
fraction of the lower range of HDR values to the 0.0 - 1.0 intensity range of a  
SDR window, as a dumb people's tone-mapping operator. E.g., the startup default  
is to map 0 - 500 nits input to the 0 - 1 range, to get something reasonable  
displayed even without application of some proper tone-mapping operator.  
  
colorGamut = [Screen](Screen)('HookFunction', windowPtr, 'WindowColorGamut' [, hookname][,  
colorGamut]);  
Return the current color gamut settings for the onscreen window 'windowPtr'.  
Optionally assign new settings.  
'hookname' is accepted, but currently ignored. Pass '' or [] for now.  
'colorGamut' as return argument is a 2x4 matrix specifying the currently  
assigned color gamut for the window. You can specify an optional 'colorGamut'  
matrix parameter to set a new color gamut.  
By default, 'colorGamut' is an all-zeros matrix, which means that no color gamut  
is assigned, and [Screen](Screen)() should use reasonable defaults (which may be context  
dependent) if it does some gamut dependent processing. If you do set a matrix,  
then it must be a 2-by-4 matrix, encoding the CIE-1931 2D chromaticity  
coordinates of the red, green, and blue color primaries in columns 1, 2, and 3,  
and the location of the white-point in column 4. This defines the color space  
and gamut in which the visual content of the onscreen window is supposed to  
live. Currently, this color gamut is only used for movie playback with  
pixelFormat 11, e.g., HDR playback. When decoding and returning video frames  
from a movie, [Screen](Screen)() will perform a color space transformation to remap the  
image pixels from the source color gamut of the movie to the color gamut  
specified for the window. If no 'WindowColorGamut' call was made prior to start  
of movie playback, then color gamut will be selected as BT-2020 for HDR windows,  
and BT-709 for standard dynamic range windows.  
  
  
### General notes:  
  
\* Hook chains are per onscreen window, so each window can have a different  
configuration and enable state.  
\* Read all available documentation on the Psychtoolbox imaging pipeline in 'help  
PsychGLImageprocessing', the [PsychDocumentation](PsychDocumentation) folder and on the Wiki before  
you make use of this function. Its way to complex to use it by guessing ;)  
  


###See also:

