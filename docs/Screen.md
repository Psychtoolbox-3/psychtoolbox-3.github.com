# [Screen](Screen)
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen)

Usage:  
  
% Activate compatibility mode: Try to behave like the old MacOS-9 Psychtoolbox:  
oldEnableFlag=Screen('[Preference](Screen-Preference)', 'EmulateOldPTB', [enableFlag]);  
  
% Open or close a window or texture:  
[windowPtr,rect]=Screen('[OpenWindow](Screen-OpenWindow)',windowPtrOrScreenNumber [,color] [,rect] [,pixelSize] [,numberOfBuffers] [,stereomode] [,multisample][,imagingmode][,specialFlags][,clientRect][,fbOverrideRect][,vrrParams=[]]);  
[windowPtr,rect]=Screen('[OpenOffscreenWindow](Screen-OpenOffscreenWindow)',windowPtrOrScreenNumber [,color] [,rect] [,pixelSize] [,specialFlags] [,multiSample]);  
textureIndex=Screen('[MakeTexture](Screen-MakeTexture)', WindowIndex, imageMatrix [, optimizeForDrawAngle=0] [, specialFlags=0] [, floatprecision] [, textureOrientation=0] [, textureShader=0]);  
oldParams = Screen('[PanelFitter](Screen-PanelFitter)', windowPtr [, newParams]);  
Screen('[Close](Screen-Close)', [windowOrTextureIndex or list of textureIndices/offscreenWindowIndices]);  
Screen('[CloseAll](Screen-CloseAll)');  
  
%  Draw lines and solids like QuickDraw and DirectX (OS 9 and Windows):  
currentbuffer = Screen('[SelectStereoDrawBuffer](Screen-SelectStereoDrawBuffer)', windowPtr [, bufferid] [, param1]);  
Screen('[DrawLine](Screen-DrawLine)', windowPtr [,color], fromH, fromV, toH, toV [,penWidth]);  
Screen('[DrawArc](Screen-DrawArc)',windowPtr,[color],[rect],startAngle,arcAngle)  
Screen('[FrameArc](Screen-FrameArc)',windowPtr,[color],[rect],startAngle,arcAngle[,penWidth] [,penHeight] [,penMode])  
Screen('[FillArc](Screen-FillArc)',windowPtr,[color],[rect],startAngle,arcAngle)  
Screen('[FillRect](Screen-FillRect)', windowPtr [,color] [,rect] );  
Screen('[FrameRect](Screen-FrameRect)', windowPtr [,color] [,rect] [,penWidth]);  
Screen('[FillOval](Screen-FillOval)', windowPtr [,color] [,rect] [,perfectUpToMaxDiameter]);  
Screen('[FrameOval](Screen-FrameOval)', windowPtr [,color] [,rect] [,penWidth] [,penHeight] [,penMode]);  
Screen('[FramePoly](Screen-FramePoly)', windowPtr [,color], pointList [,penWidth]);  
Screen('[FillPoly](Screen-FillPoly)', windowPtr [,color], pointList [, isConvex]);  
  
% New OpenGL functions for OS X:  
Screen('[glPoint](Screen-glPoint)', windowPtr, color, x, y [,size]);  
Screen('[gluDisk](Screen-gluDisk)', windowPtr, color, x, y [,size]);  
[minSmoothPointSize, maxSmoothPointSize, minAliasedPointSize, maxAliasedPointSize] = Screen('[DrawDots](Screen-DrawDots)', windowPtr, xy [,size] [,color] [,center] [,dot_type] [,lenient]);  
[minSmoothLineWidth, maxSmoothLineWidth, minAliasedLineWidth, maxAliasedLineWidth] = Screen('[DrawLines](Screen-DrawLines)', windowPtr, xy [,width] [,colors] [,center] [,smooth] [,lenient]);  
[sourceFactorOld, destinationFactorOld, colorMaskOld]=Screen('[BlendFunction](Screen-BlendFunction)', windowIndex, [sourceFactorNew], [destinationFactorNew], [colorMaskNew]);  
  
% Draw Text in windows  
textModes = Screen('[TextModes](Screen-TextModes)');  
oldCopyMode=Screen('[TextMode](Screen-TextMode)', windowPtr [,textMode]);  
oldTextSize=Screen('[TextSize](Screen-TextSize)', windowPtr [,textSize]);  
oldStyle=Screen('[TextStyle](Screen-TextStyle)', windowPtr [,style]);  
[oldFontName,oldFontNumber,oldTextStyle]=Screen('[TextFont](Screen-TextFont)', windowPtr [,fontNameOrNumber][,textStyle]);  
[normBoundsRect, offsetBoundsRect, textHeight, xAdvance] = Screen('[TextBounds](Screen-TextBounds)', windowPtr, text [,x] [,y] [,yPositionIsBaseline] [,swapTextDirection]);  
[newX, newY, textHeight]=Screen('[DrawText](Screen-DrawText)', windowPtr, text [,x] [,y] [,color] [,backgroundColor] [,yPositionIsBaseline] [,swapTextDirection]);  
oldTextColor=Screen('[TextColor](Screen-TextColor)', windowPtr [,colorVector]);  
oldTextBackgroundColor=Screen('[TextBackgroundColor](Screen-TextBackgroundColor)', windowPtr [,colorVector]);  
oldMatrix = Screen('[TextTransform](Screen-TextTransform)', windowPtr [, newMatrix]);  
  
% Copy an image, very quickly, between textures, offscreen windows and onscreen windows.  
[resident [texidresident]] = Screen('[PreloadTextures](Screen-PreloadTextures)', windowPtr [, texids]);  
Screen('[DrawTexture](Screen-DrawTexture)', windowPointer, texturePointer [,sourceRect] [,destinationRect] [,rotationAngle] [, filterMode] [, globalAlpha] [, modulateColor] [, textureShader] [, specialFlags] [, auxParameters]);  
Screen('[DrawTextures](Screen-DrawTextures)', windowPointer, texturePointer(s) [, sourceRect(s)] [, destinationRect(s)] [, rotationAngle(s)] [, filterMode(s)] [, globalAlpha(s)] [, modulateColor(s)] [, textureShader] [, specialFlags] [, auxParameters]);  
Screen('[CopyWindow](Screen-CopyWindow)', srcWindowPtr, dstWindowPtr, [srcRect], [dstRect], [copyMode])  
  
% Copy an image, slowly, between matrices and windows :  
imageArray=Screen('[GetImage](Screen-GetImage)', windowPtr [,rect] [,bufferName] [,floatprecision=0] [,nrchannels=3])  
Screen('[PutImage](Screen-PutImage)', windowPtr, imageArray [,rect]);  
  
% Synchronize with the window's screen (on-screen only):  
[VBLTimestamp StimulusOnsetTime FlipTimestamp Missed Beampos] = Screen('[Flip](Screen-Flip)', windowPtr [, when] [, dontclear] [, dontsync] [, multiflip]);  
[VBLTimestamp StimulusOnsetTime FlipTimestamp Missed Beampos] = Screen('[AsyncFlipBegin](Screen-AsyncFlipBegin)', windowPtr [, when] [, dontclear] [, dontsync] [, multiflip]);  
[VBLTimestamp StimulusOnsetTime FlipTimestamp Missed Beampos] = Screen('[AsyncFlipEnd](Screen-AsyncFlipEnd)', windowPtr);  
[VBLTimestamp StimulusOnsetTime FlipTimestamp Missed Beampos] = Screen('[AsyncFlipCheckEnd](Screen-AsyncFlipCheckEnd)', windowPtr);  
[VBLTimestamp StimulusOnsetTime swapCertainTime] = Screen('[WaitUntilAsyncFlipCertain](Screen-WaitUntilAsyncFlipCertain)', windowPtr);  
[info] = Screen('[GetFlipInfo](Screen-GetFlipInfo)', windowPtr [, infoType=0] [, auxArg1]);  
[telapsed] = Screen('[DrawingFinished](Screen-DrawingFinished)', windowPtr [, dontclear] [, sync]);  
framesSinceLastWait = Screen('[WaitBlanking](Screen-WaitBlanking)', windowPtr [, waitFrames]);  
  
% Load color lookup table of the window's screen (on-screen only):  
[gammatable, dacbits, reallutsize] = Screen('[ReadNormalizedGammaTable](Screen-ReadNormalizedGammaTable)', windowPtrOrScreenNumber [, physicalDisplay]);  
[oldtable, success] = Screen('[LoadNormalizedGammaTable](Screen-LoadNormalizedGammaTable)', windowPtrOrScreenNumber, table [, loadOnNextFlip][, physicalDisplay][, ignoreErrors]);  
oldclut = Screen('[LoadCLUT](Screen-LoadCLUT)', windowPtrOrScreenNumber [, clut] [, startEntry=0] [, bits=8]);  
  
% Get (and set) information about a window or screen:  
screenNumbers=Screen('[Screens](Screen-Screens)' [, physicalDisplays]);  
windowPtrs=Screen('[Windows](Screen-Windows)');  
kind=Screen(windowPtr, 'WindowKind');  
isOffscreen=Screen(windowPtr,'IsOffscreen');  
hz=Screen('[FrameRate](Screen-FrameRate)', windowPtrOrScreenNumber [, mode] [, reqFrameRate]);  
hz=Screen('[NominalFrameRate](Screen-NominalFrameRate)', windowPtrOrScreenNumber [, mode] [, reqFrameRate]);  
[ monitorFlipInterval nrValidSamples stddev ]=Screen('[GetFlipInterval](Screen-GetFlipInterval)', windowPtr [, nrSamples] [, stddev] [, timeout]);  
screenNumber=Screen('[WindowScreenNumber](Screen-WindowScreenNumber)', windowPtr);  
rect=Screen('[Rect](Screen-Rect)', windowPtrOrScreenNumber [, realFBSize=0]);  
pixelSize=Screen('[PixelSize](Screen-PixelSize)', windowPtrOrScreenNumber);  
pixelSizes=Screen('[PixelSizes](Screen-PixelSizes)', windowPtrOrScreenNumber);  
[width, height]=Screen('[WindowSize](Screen-WindowSize)', windowPointerOrScreenNumber [, realFBSize=0]);  
[width, height]=Screen('[DisplaySize](Screen-DisplaySize)', ScreenNumber);  
[oldmaximumvalue, oldclampcolors, oldapplyToDoubleInputMakeTexture] = Screen('[ColorRange](Screen-ColorRange)', windowPtr [, maximumvalue][, clampcolors][, applyToDoubleInputMakeTexture]);  
info = Screen('[GetWindowInfo](Screen-GetWindowInfo)', windowPtr [, infoType=0] [, auxArg1]);  
resolutions=Screen('[Resolutions](Screen-Resolutions)', screenNumber);  
oldResolution=Screen('[Resolution](Screen-Resolution)', screenNumber [, newwidth] [, newheight] [, newHz] [, newPixelSize] [, specialMode]);  
oldSettings = Screen('[ConfigureDisplay](Screen-ConfigureDisplay)', setting, screenNumber, outputId [, newwidth][, newheight][, newHz][, newX][, newY]);  
Screen('[ConstrainCursor](Screen-ConstrainCursor)', windowIndex, addConstraint [, rect]);  
  
% Get/set details of environment, computer, and video card (i.e. screen):  
struct=Screen('[Version](Screen-Version)');  
comp=Screen('[Computer](Screen-Computer)');  
oldBool=Screen('[Preference](Screen-Preference)', 'IgnoreCase' [,bool]);  
tick0Secs=Screen('[Preference](Screen-Preference)', 'Tick0Secs', tick0Secs);  
psychTableVersion=Screen('[Preference](Screen-Preference)', 'PsychTableVersion');  
mexFunctionName=Screen('[Preference](Screen-Preference)', 'PsychTableCreator');  
proc=Screen('[Preference](Screen-Preference)', 'Process');  
Screen('[Preference](Screen-Preference)','SkipSyncTests', skipTest);  
Screen('[Preference](Screen-Preference)','VisualDebugLevel', level (valid values between 0 and 5));  
Screen('[Preference](Screen-Preference)', 'ConserveVRAM', mode (valid values between 0 and 3));  
Screen('[Preference](Screen-Preference)', 'Enable3DGraphics', [enableFlag]);  
  
% Helper functions.  Don't call these directly, use eponymous wrappers:  
[x, y, buttonVector, hasKbFocus, valuators]= Screen('[GetMouseHelper](Screen-GetMouseHelper)', numButtons [, screenNumber][, mouseIndex]);  
Screen('[HideCursorHelper](Screen-HideCursorHelper)', windowPntr [, mouseIndex]);  
Screen('[ShowCursorHelper](Screen-ShowCursorHelper)', windowPntr [, cursorshapeid][, mouseIndex]);  
Screen('[SetMouseHelper](Screen-SetMouseHelper)', windowPntrOrScreenNumber, x, y [, mouseIndex][, detachFromMouse]);  
Screen('[SetMouseHelper](Screen-SetMouseHelper)', windowPntrOrScreenNumber, x, y [, mouseIndex][, detachFromMouse]);  
  
% Internal testing of Screen  
timeList= Screen('GetTimelist');  
Screen('ClearTimelist');  
Screen('[Preference](Screen-Preference)','DebugMakeTexture', enableDebugging);  
  
% Movie and multimedia playback functions:  
[ moviePtr [duration] [fps] [width] [height] [count] [aspectRatio] [hdrStaticMetaData]]=Screen('[OpenMovie](Screen-OpenMovie)', windowPtr, moviefile [, async=0] [, preloadSecs=1] [, specialFlags1=0][, pixelFormat=4][, maxNumberThreads=-1][, movieOptions]);  
Screen('[CloseMovie](Screen-CloseMovie)' [, moviePtr=all]);  
[ texturePtr [timeindex]]=Screen('[GetMovieImage](Screen-GetMovieImage)', windowPtr, moviePtr, [waitForImage], [fortimeindex], [specialFlags = 0] [, specialFlags2 = 0]);  
[droppedframes] = Screen('[PlayMovie](Screen-PlayMovie)', moviePtr, rate, [loop], [soundvolume]);  
timeindex = Screen('[GetMovieTimeIndex](Screen-GetMovieTimeIndex)', moviePtr);  
[oldtimeindex] = Screen('[SetMovieTimeIndex](Screen-SetMovieTimeIndex)', moviePtr, timeindex [, indexIsFrames=0]);  
moviePtr = Screen('[CreateMovie](Screen-CreateMovie)', windowPtr, movieFile [, width][, height][, frameRate=30][, movieOptions][, numChannels=4][, bitdepth=8]);  
Screen('[FinalizeMovie](Screen-FinalizeMovie)', moviePtr);  
Screen('[AddFrameToMovie](Screen-AddFrameToMovie)', windowPtr [,rect] [,bufferName] [,moviePtr=0] [,frameduration=1]);  
Screen('[AddAudioBufferToMovie](Screen-AddAudioBufferToMovie)', moviePtr, audioBuffer);  
[imageArray, format, errorMsg, auxInfo] = Screen('[ReadHDRImage](Screen-ReadHDRImage)', filename [, errorMode=0]);  
  
% Video capture functions:  
devices = Screen('[VideoCaptureDevices](Screen-VideoCaptureDevices)' [, engineId]);  
videoPtr =Screen('[OpenVideoCapture](Screen-OpenVideoCapture)', windowPtr [, deviceIndex][, roirectangle][, pixeldepth][, numbuffers][, allowfallback][, targetmoviename][, recordingflags][, captureEngineType][, bitdepth=8]);  
Screen('[CloseVideoCapture](Screen-CloseVideoCapture)', capturePtr);  
[fps starttime] = Screen('[StartVideoCapture](Screen-StartVideoCapture)', capturePtr [, captureRateFPS] [, dropframes=0] [, startAt]);  
droppedframes = Screen('[StopVideoCapture](Screen-StopVideoCapture)', capturePtr [, discardFrames=1]);  
[ texturePtr [capturetimestamp] [droppedcount] [average_intensityOrRawImageMatrix]]=Screen('[GetCapturedImage](Screen-GetCapturedImage)', windowPtr, capturePtr [, waitForImage=1] [,oldTexture] [,specialmode] [,targetmemptr]);  
oldvalue = Screen('[SetVideoCaptureParameter](Screen-SetVideoCaptureParameter)', capturePtr, 'parameterName' [, value]);  
  
% Low level direct access to OpenGL-API functions:  
% Online info for each function available by opening a terminal window  
% and typing 'man Functionname' + Enter.  
  
Screen('[glPushMatrix](Screen-glPushMatrix)', windowPtr);  
Screen('[glPopMatrix](Screen-glPopMatrix)', windowPtr);  
Screen('[glLoadIdentity](Screen-glLoadIdentity)', windowPtr);  
Screen('[glTranslate](Screen-glTranslate)', windowPtr, tx, ty [, tz]);  
Screen('[glScale](Screen-glScale)', windowPtr, sx, sy [, sz]);  
Screen('[glRotate](Screen-glRotate)', windowPtr, angle, [rx = 0], [ry = 0] ,[rz = 1]);  
  
% Support for 3D graphics rendering and for interfacing with external OpenGL code:  
Screen('[Preference](Screen-Preference)', 'Enable3DGraphics', [enableFlag]);  % Enable 3D gfx support.  
Screen('[BeginOpenGL](Screen-BeginOpenGL)', windowPtr [, sharecontext]);  % Prepare window for external OpenGL drawing.  
Screen('[EndOpenGL](Screen-EndOpenGL)', windowPtr);  % Finish external OpenGL drawing.  
[targetwindow, IsOpenGLRendering] = Screen('[GetOpenGLDrawMode](Screen-GetOpenGLDrawMode)');  
[textureHandle rect] = Screen('[SetOpenGLTextureFromMemPointer](Screen-SetOpenGLTextureFromMemPointer)', windowPtr, textureHandle, imagePtr, width, height, depth [, upsidedown][, target][, glinternalformat][, gltype][, extdataformat][, specialFlags]);  
[textureHandle rect] = Screen('[SetOpenGLTexture](Screen-SetOpenGLTexture)', windowPtr, textureHandle, glTexid, target [, glWidth][, glHeight][, glDepth][, textureShader][, specialFlags]);  
[ gltexid gltextarget texcoord_u texcoord_v ] =Screen('[GetOpenGLTexture](Screen-GetOpenGLTexture)', windowPtr, textureHandle [, x][, y]);  
  
% Support for plugins and for builtin high performance image processing pipeline:  
[ret1, ret2, ...] = Screen('[HookFunction](Screen-HookFunction)', windowPtr, 'Subcommand', 'HookName', arg1, arg2, ...);  
proxyPtr = Screen('[OpenProxy](Screen-OpenProxy)', windowPtr [, imagingmode]);  
transtexid = Screen('[TransformTexture](Screen-TransformTexture)', sourceTexture, transformProxyPtr [, sourceTexture2][, targetTexture][, specialFlags]);  
  

 Screen is a MEX file for precise control of the video display. Screen has  
 many functions; type "Screen" for a list:  
  
 Screen  
  
 For explanation of any particular screen function, just add a question  
 mark "?". E.g. for 'OpenWindow', try either of these equivalent forms:  
   Screen('OpenWindow?')  
   Screen OpenWindow?  
  
 All the Screen Preference settings are documented together:  
   Screen Preference?  
  
 General Screen ARGUMENTS, common to most subfunctions of Screen:  
   
 "windowPtr" argument: Screen 'OpenWindow' and 'OpenOffscreenWindow' both  
 return a windowPtr, a number that designates the window you just  
 created. You can create many windows. To use a window, you pass its  
 windowPtr to the Screen function you want to apply to that window.  
  
 "rect" argument: "rect" is a 1x4 matrix containing the coordinates of an  
 imaginary box containing all the pixels. All screen and window  
 coordinates follow Apple Macintosh conventions. (In Apples the pixels  
 occupy the space between the coordinates. Thus a rect [0 0 1 1] contains  
 just one pixel.) Coordinates can be local to the window (i.e. 0,0 origin  
 is at upper left of window), or local to the screen (origin at upper left  
 of screen), or "global", which follows Apple's convention of treating the  
 entire desktop (all your screens) as one big screen, with the origin at   
 upper left of the main screen, which has the menu bar. Historically we've  
 had two different orderings of the elements of rect, so, for general  
 compatibility, all of the Psychophysics Toolbox refers to the elements  
 symbolically, through RectLeft, RectTop, etc. Since 2/97, we use Apple's  
 standard ordering: RectLeft=1, RectTop=2, RectRight=3, RectBottom=4.  
  
 [optional arguments]: Brackets in the function list, e.g. [color],  
 indicate optional arguments, not matrices. Optional arguments must be in  
 order, without omitting earlier ones, but you can use the empty matrix  
 [] as a place holder, with the same effect as omitting it.  
  
###  WHEN YOU GET A MATLAB ERROR  
   
 If your computer only has one screen (the typical scenario) and your  
 program produces a Matlab error while your full-screen window is open,  
 you'll hear the beep, but you won't be able to see the Matlab Command  
 Window. Follow the instructions below for bringing forward the command  
 window, then type clear screen to flush just the Screen MEX file, or   
 "clear mex" to flush all the MEX files. When flushed, as part of its   
 exit sequence, Screen closes all its windows, restores the screen's normal   
 color table, and shows the cursor. Or you can get just those effects,   
 without flushing, by calling Screen('CloseAll') or sca - which is an   
 abbreviation for Screen('CloseAll').  
  
 You can use Matlab's EVAL command to do this for you automatically. E.g.  
 if your program is called "foo.m", run your program by calling EVAL:  
   eval('foo','clear screen;error(''error in foo'')')  
  
 If an error occurs in FOO, Matlab, instead of halting, will execute the  
 second argument to EVAL, which restores your screen and reports the  
 error.  
  
 OpenGL: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
 Instead of offscreen windows, the OpenGL Psychtoolbox uses fast rendering  
 and OpenGL textures for animation. With the exception of matrices, all  
 drawing may be done during the animation loop directly to the  onscreen  
 window, rather than being rendered to offscreen windows before the start  
 of the movie.  Matrices are converted to Textures before the start of the  
 animation and, like offscreen windows in OS 9, may be quickly copied to  
 an onscreen window during movie play. Offscreen windows are still supported  
 if you need to draw very complex stimuli. You can draw the stimulus into  
 an offscreen window and then quickly copy the window into the onscreen  
 window. For most purposes however, it is possible to draw directly into  
 the backbuffer of your offscreen window and make the backbuffer visible  
 on next vertical blank by a call to Screen('Flip', windowPtr).    
  
 See MovieDemoOSX and DriftDemoOSX for examples of how to create and show  
 movies this way.  
  
 Off-screen windows are invisible, but useful as an intermediate place to  
 create and store images for later display. Copying from window to window  
 is very fast. It's easy to precompute a series of off-screen windows  
 and then show them as a movie, in real time, one per video frame:  
  
  % make movie  
  window=Screen('OpenWindow', 0, 0);  
  rect=[0 0 200 200];  
  white = WhiteIndex(window);  
  for i=1:100  
    movie(i)=Screen('OpenOffscreenWindow', window, 0, rect);  
    Screen('FillOval', movie(i), white, [0 0 2 2]\*(i-1));  
  end;  
  
  % show movie  
  for i=[1:100 100:-1:1] % forwards and backwards  
    Screen('CopyWindow',movie(i),window,rect,rect);  
    Screen('Flip', window);  
  end;  
  Screen('CloseAll');  
  
  
###  Stopping programs:  
  
 Ctrl-C halts any program.  (Type a "c" while holding down the "Ctrl"  
 key). Sometimes, Ctrl-C fails to halt programs executing in a Matlab process  
 run with the "-nojvm" option. To halt a runaway Psychtoolbox script in  
 Psychtoolbox you might resort to the Windows Task Manager to kill  
 the Matlab process.  (Use Ctrl-Alt-Delete to open a window from which  
 you can start the Task Manager.)  
  
###  Windows:  
  
 Ctrl-Alt-Delete allows you to launch the Windows task manager, which  
 reduces the Psychtoolbox onscreen windows when it opens. (Simultaneously  
 press the "Ctrl", "Alt", and "Delete" keys.)  There are also simpler ways of  
 reducing the Psychtoolbox window which are specific to particular  
 versions of Windows.  
 Windows 2000: Alt-Tab will bring another application to the foreground,  
 minimizing the Matlab Psychtoolbox window.  
   
 OS-X:  
  
 Apple-Command-Escape executes "Force Quit" on Matlab, closing Matlab and all  
 of its windows.  
  
###  Linux:  
  
 Ctrl-Alt-Escape, followed by a mouse click kills the onscreen windows and your  
 Matlab session.  
  
  
 See "help PsychDemos" for many demos which demonstrate Screen's capabilities.  
  
 Differences in Screens capabilities between different operating systems  
 are discussed in the online help for the different subfunctions, our  
 "PsychDemos" if differences apply, and on the Psychtoolbox Wiki under  
 "Platform Differences and writing portable code".  
  
###  Initial reports appear first at the forum:  
  
 https://psychtoolbox.discourse.group  
  
 If you find a bug, please report it to the forum or our issue tracker at  
 psychtoolbox.org  
  
 It will help greatly if you can supply a  minimal-length program that exhibits   
 the bug. And please include as much information about your hardware and software  
 setup to document the context in which you're running, e.g., Computer type, graphics  
 card type and model, operating system, Matlab version, Psychtoolbox version and flavor  
 and the output of PTB to the Matlab window.  
  


