# [Screen('HookFunction')](Screen-HookFunction) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


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
'hookName' Currently ignored, placeholder for future extensions.  
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
height] = [Screen](Screen)('HookFunction', windowPtr, 'GetDisplayBufferTextures');  
Get the [OpenGL](OpenGL) handles of the backing textures and their parameters for the  
final output color buffers of the imaging pipeline.  
For the meaning of return values see 'SetDisplayBufferTextures' above.  
This only works if imagingMode flag kPsychNeedFinalizedFBOSinks is set or  
stereoMode 12 is active, which implicitely sets that flag.  
This query function works both with internally generated and maintained backing  
textures and externally injected/maintained ones.  
For internally generated textures (without flag kPsychUseExternalSinkTextures),  
the handles should be considered read-only: Binding the textures for  
sampling/reading from them is appropriate, modifying them in any way is  
forbidden.  
  
  
[Screen](Screen)('HookFunction', windowPtr, 'SetOneshotFlipFlags' [, hookname],  
flipFlags);  
Assign special flags to be applied one-time during the next execution of  
[Screen](Screen)('[Flip](Flip)') or [Screen](Screen)('AsyncFlipBegin').  
'hookname' is accepted, but currently ignored. Pass '' or [] for now.  
These 'flipFlags' will be applied during the next window flip operation, and  
each applied flag will then auto-reset after application. This is mostly meant  
to be called from within imaging pipeline processing chains during preflip  
operations or the active presentation sequence to modify behaviour of that  
sequence. The following 'flipFlags' are currently implemented:  
kPsychSkipVsyncForFlipOnce, kPsychSkipTimestampingForFlipOnce,  
kPsychSkipSwapForFlipOnce, kPsychSkipWaitForFlipOnce.  
  
  
[Screen](Screen)('HookFunction', windowPtr, 'SetOneshotFlipResults' [, hookname],  
[VBLTimestamp](VBLTimestamp) [, [StimulusOnsetTime](StimulusOnsetTime)=[VBLTimestamp](VBLTimestamp)][, Missed=0]);  
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
  
  
### General notes:  
  
\* Hook chains are per onscreen window, so each window can have a different  
configuration and enable state.  
\* Read all available documentation on the Psychtoolbox imaging pipeline in 'help  
PsychGLImageprocessing', the [PsychDocumentation](PsychDocumentation) folder and on the Wiki before  
you make use of this function. Its way to complex to use it by guessing ;)  
  


###See also:

