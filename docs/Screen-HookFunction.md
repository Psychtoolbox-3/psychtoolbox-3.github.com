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
  
### General notes:  
  
\* Hook chains are per onscreen window, so each window can have a different  
configuration and enable state.  
\* Read all available documentation on the Psychtoolbox imaging pipeline in 'help  
PsychGLImageprocessing', the [PsychDocumentation](PsychDocumentation) folder and on the Wiki before  
you make use of this function. Its way to complex to use it by guessing ;)  
  


###See also:

