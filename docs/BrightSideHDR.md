# [BrightSideHDR](BrightSideHDR)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[BrightSideDisplay](BrightSideDisplay)

[BrightSideHDR](BrightSideHDR)(cmd [, arg1][, arg2]) -- Psychtoolbox interface to  
[BrightSide](BrightSide) Technologies High Dynamic Range display device.  
  
This function is used to set up and interface with the High Dynamic Range  
display of [BrightSide](BrightSide) Technologies. It is a Matlab wrapper around lower  
level GLSL Psychtoolbox functions and the low-level [BrightSideCore](BrightSideCore).dll  
MEX-File. You need to have Brightsides DLL's (and the display device)  
installed on your machine for this to work. Without the DLL's this will  
simply crash. See "help [BSRuntimeLibs](BSRuntimeLibs)" for information about  
dependencies.  
  
cmd - The command that [BrightSideHDR](BrightSideHDR) should execute. cmd can be any of  
the following:  
  
Open a window on the HDR display as with [Screen](Screen)('OpenWindow', ...),  
perform all HDR initialization:  
  
[win, winRect] = [BrightSideHDR](BrightSideHDR)('OpenWindow', screenid, ...);  
  
This will execute [Screen](Screen)('OpenWindow') with all proper parameters,  
followed by [BrightSide](BrightSide) HDR init routines. It is a completely sufficient  
drop in replacement for [Screen](Screen)('OpenWindow'), accepting and returning  
exactly the same arguments that [Screen](Screen)() would do, adjusting all  
parameters to the constraints of the [BrightSideHDR](BrightSideHDR), if necessary.  
  
[win, winRect] = [BrightSideHDR](BrightSideHDR)('DummyOpenWindow', screenid, ...);  
Same as [OpenWindow](OpenWindow), but just init a dummy mode that operates on standard  
displays without the Brightside-Libraries - useful for off-site testing.  
  
  
[win, winRect] = [BrightSideHDR](BrightSideHDR)('RawOpenWindow', screenid, ...);  
Same as [DummyOpenWindow](DummyOpenWindow), but just init a bare-minimum window on the HDR  
display suitable for playback of previously computed raw framebuffer  
images (see raw capture and replay support below). This will essentially  
open a fullscreen window on the HDR display, with proper window settings  
and identity gamma tables to make sure framebuffer content is passed  
unaltered 1-to-1 to the display. The imaging pipeline is disabled, this  
is a pure "fast replay" mode of content created in a previous session.  
  
  
In most applications you won't ever need to use any of the commands  
below, as PTB does all this stuff automatically behind the scenes...  
Ignore them unless you know what you're doing.  
  
[BrightSideHDR](BrightSideHDR)('Initialize', win [, dummy]); -- Initialize the [BrightSide](BrightSide) libraries  
for HDR output into onscreen window 'win'. Onscreen window 'win' must have been  
opened before on a screen which corresponds to the attached High Dynamic Range  
display device. If you set 'dummy' to 1, then we are in emulation mode,  
i.e., we work without invocation of the mex file and without a real HDR  
display. This call will also attach all callback functions to the proper  
hooks for the given onscreen window 'win' inside the [Screen](Screen)() command.  
  
[BrightSideHDR](BrightSideHDR)('Debuglevel', level); -- Set level of verbosity for  
debugging. The default is zero which means to be silent. A level of 1  
produces some debug output.  
  
  
### SUPPORT FOR RAW HDR IMAGE CAPTURE AND REPLAY:  
  
[sourceWin, destWin] = [BrightSideHDR](BrightSideHDR)('CreateSnapshotBufferPair');  
- Create a pair of offscreen windows useable for "offline" HDR-\>[BrightSide](BrightSide)  
conversion. Will create 'sourceWin' as a offscreen window with 32bpc  
float RGBA format, 'destWin' as a offscreenwindow with 8 bpc RGBA format.  
Both windows will have the size of the HDR displays framebuffer.  
  
You can draw into the 'sourceWin' just as you'd do to an onscreen window.  
Then you can call [BrightSideHDR](BrightSideHDR)('ConvertImageToSnapshotBuffer', destWin,  
sourceWin); to convert the HDR image into a [BrightSide](BrightSide) formatted image in  
'destWin'. You can use 'destWin' or its content in the  
[BrightSideHDR](BrightSideHDR)('BlitRawFramebufferSnapshot') call for quick "replay" of  
HDR content.  
  
  
[rawImg] = [BrightSideHDR](BrightSideHDR)('ConvertImageToSnapshotBuffer', destWin, sourceWin);  
- Convert HDR image in offscreen window 'sourceWin' into a HDR  
useable raw image in offscreen window 'destWin'. Optionally return a  
Matlab uint8 RGB image matrix with the raw data as 1st return argument  
rawImg.  
  
You could save 'rawImg' to disk and later load it and "replay" it on the  
HDR display via calls to [BrightSideHDR](BrightSideHDR)('BlitRawFramebufferSnapshot',  
sourceWin);  
  
  
rawSnapshotMatrix = [BrightSideHDR](BrightSideHDR)('GetRawFramebufferSnapshot');  
-Call immediately after [Screen](Screen)('[Flip](Flip)'). This will create a "screenshot" of the  
framebuffer for the currently displaying HDR image and return a Matlab  
matrix with proper raw framebuffer data, formatted for the HDR display.  
Can be used to [Screen](Screen)('MakeTexture') a texture that you can blit into the  
framebuffer via [BrightSideHDR](BrightSideHDR)('BlitRawFramebufferSnapshot') without need  
for expensive conversion at runtime.  
  
  
[BrightSideHDR](BrightSideHDR)('BlitRawFramebufferSnapshot', sourceWin); Blit the given  
RGB8 or RGBA8 texture or offscreen window into the framebuffer of HDR  
display, so it gets displayed at the next invocation of [Screen](Screen)('[Flip](Flip)').  
The 'sourceWin' must be a texture or offscreen window whose image content  
was previously created by one of the raw snapshotting functions above,  
ie., it must be already encoded in the special data format for [BrightSide](BrightSide)  
displays.  
  
  
Callbacks: Usually called automatically by [Screen](Screen)(), no need to use them  
in your script directly! Some of them may disappear in the future,  
getting subsumed by [Screen](Screen)()'s internal imaging pipeline.  
  
[BrightSideHDR](BrightSideHDR)('BrightSideExecuteBlit', win); -- This will convert  
the HDR image content in the HDR backbuffer into the special data  
format needed by the HDR display hardware. This is called by PTB  
automatically, don't call it yourself!  
  
[BrightSideHDR](BrightSideHDR)('Shutdown'); -- Shut down the HDR device and core library,  
switch PTB back to standard LDR output. This is called by PTB  
automatically, don't call it yourself!  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/BrightSideDisplay/BrightSideHDR.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/BrightSideDisplay/BrightSideHDR.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/BrightSideDisplay/BrightSideHDR.m</code>
</div>

