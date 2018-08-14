# [PsychDataPixx](PsychDataPixx)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[DatapixxToolbox](DatapixxToolbox)>[DatapixxBasic](DatapixxBasic)

[PsychDataPixx](PsychDataPixx) - High level control driver for the [VPixx](VPixx) - [DataPixx](DataPixx) device.  
  
This driver provides common high-level functionality for interaction with  
the [VPixx](VPixx) Technologies [DataPixx](DataPixx) device. The driver provides high-level  
functions for basic device operations and for timestamping of visual  
stimulus onset. It also provides functionality needed for the  
[PsychImaging](PsychImaging)() command and the [Screen](Screen)() image processing pipeline to  
properly setup the high-precision video display modes and stereo display  
modes of the [DataPixx](DataPixx).  
  
The driver is dependend on the low-level MEX file Datapixx() driver to be  
present. It will fail if that MEX file is missing or dysfunctional.  
  
Normally you will have a [DataPixx](DataPixx) connected when using this driver, but  
for basic code development and testing you can call  
[PsychDataPixx](PsychDataPixx)('SetDummyMode', 1); and then run without a connected  
[DataPixx](DataPixx) device.  
  
For control of visual stimulus display on the [DataPixx](DataPixx), read the relevant  
sections of the help of [PsychImaging](PsychImaging). That command will take care of most  
of the details of visual setup.  
  
  
# Commands and their syntax  
  
oldmode = [PsychDataPixx](PsychDataPixx)('SetDummyMode' [, mode]);  
- Switch driver into dummy mode if 'mode' is set to 1. In dummy mode, the  
code mostly operates without a [DataPixx](DataPixx) device connected. This is useful  
for basic debugging of code without access to the device. The simulated  
device returns more or less meaningful values, good enough for initial  
code development.  
  
A 'mode' setting of zero enabled normal mode of operation.  
You must call this command before any other command for proper operation!  
  
  
[PsychDataPixx](PsychDataPixx)('Open');  
- Open a connection to the device, with default settings. If the device  
is already open then this will do almost nothing, otherwise the  
connection is opened.  
  
You must call this function before all other remaining commands!  
  
  
[PsychDataPixx](PsychDataPixx)('[Close](Close)');  
- [Close](Close) a connection to the device. Multiple virtual connections can be  
simultaneously open. If this function call closes the last virtual  
connection, then the real physical connection to the device is closed and  
the driver is reset.  
  
If you used [PsychImaging](PsychImaging)() to make use of Datapixx graphics mode, it will  
automatically close that connection once the corresponding onscreen  
window is closed. As a simple rule, you only need to call the '[Close](Close)'  
function if you also called the 'Open' function before.  
  
Call this command as last command in your script! All further  
[PsychDataPixx](PsychDataPixx)() commands will be invalid after a '[Close](Close)' call!  
  
  
status = [PsychDataPixx](PsychDataPixx)('GetStatus' [,newstatus]);  
- Retrieve a struct 'status' with the complete driver internal state.  
Optionally assign new state 'newstatus' to driver. Only assign a new  
state if you \*really\* know what you're doing!  
  
  
oldmode = [PsychDataPixx](PsychDataPixx)('LogOnsetTimestamps', mode);  
- Return current timestamp acquisition mode as optional return argument  
'oldmode'. Set a new mode, according to argument 'mode'. 'mode' can  
be one of:  
  
0 = Disable all timestamp acquisition and logging.  
1 = Log a visual stimulus onset timestamp for the next [Screen](Screen)('[Flip](Flip)') or  
    [Screen](Screen)('AsyncFlipBegin') command after this function call, then stop  
    logging again. This is a one-shot timestamp function.  
2 = Log all [Screen](Screen)('[Flip](Flip)') and [Screen](Screen)('AsyncFlipBegin') visual stimulus  
    onset timestamps until this function is called again with a 'mode'  
    setting of 1 or 0.  
  
Timestamping is disabled by default (mode == 0), as it incurs a bit of  
computational overhead to acquire and log timestamps, typically up to 2-3  
msecs of extra time per '[Flip](Flip)' command.  
  
The driver will log all timestamps in a buffer, which can be read out via  
the following timestamp related commands.  
  
  
[boxTime, getsecsTime, flipCount, currentFlipcount] = [PsychDataPixx](PsychDataPixx)('GetLastOnsetTimestamp');  
- Retrieve visual stimulus onset timestamps related to last logged  
"[Flip](Flip)". This call will only return valid values after a [Flip](Flip) command is  
finished, ie., after a successfull call to [Screen](Screen)('[Flip](Flip)') or  
[Screen](Screen)('AsyncFlipCheckEnd') or [Screen](Screen)('AsyncFlipEnd'), and only if  
logging of timestamps was enabled by setting the 'LogOnsetTimestamps'  
mode (see above) to a non-zero value. It always returns the most recently  
acquired timestamp.  
  
'boxTime' is the time in seconds of stimulus onset as measured by the  
[DataPixx](DataPixx) internal clock.  
'getsecsTime' is the time in seconds of stimulus onset as measured by the  
Psychtoolbox [GetSecs](GetSecs)() clock.  
'flipCount' is the "serial number" of the [Screen](Screen) flip command to which  
the returned timestamps refer.  
'currentFlipcount' is the "serial number" of the most recent [Screen](Screen) flip  
command.  
  
Computation of 'getsecsTime' will become inaccurate if you don't  
frequently call [PsychDataPixx](PsychDataPixx)('GetPreciseTime') to resynchronize the  
clocks! A more accurate approach to retrieve [GetSecs](GetSecs)() style timestamps  
is to use the [PsychDataPixx](PsychDataPixx)('GetTimestampLog', 1) function to retrieve  
all logged timestamps at the end of a session and apply some  
high-precision remapping of timestamps.  
  
  
[getsecs, boxsecs, confidence] = [PsychDataPixx](PsychDataPixx)('GetPreciseTime');  
- Query both the [DataPixx](DataPixx) clock and [GetSecs](GetSecs) clock and compute which [GetSecs](GetSecs)  
time 'getsecs' corresponds to which Datapixx time 'boxsecs' and how  
reliable this correspondence is in 'confidence'. 'confidence' is the  
margin of error between both timestamps.  
This function implicitely synchronizes both clocks to get more precise  
values for 'getsecstime' from calls to [PsychDataPixx](PsychDataPixx)('GetLastOnsetTimestamp');  
The function is automatically called once at device open time.  
  
  
log = [PsychDataPixx](PsychDataPixx)('GetTimestampLog' [, remapPrecise = 0]);  
- Fetch the full log of all acquired visual stimulus onset timestamps  
into the variable 'log'. 'log' is a 3-by-n matrix for the n timestamps,  
one column encodes one stimulus onset, aka one logged invocation of  
[Screen](Screen)('[Flip](Flip)') et al.  
  
log(1,i) = i'th timestamp as measured via the Datapixx internal clock.  
log(2,i) = i'th timestamp as measured via the Psychtoolbox [GetSecs](GetSecs) clock.  
log(3,i) = [Flip](Flip) serial number of i'th sample.  
  
If the optional parameter 'remapPrecise' is set to 1, then an expensive  
calibration procedure is used to compute very precise [GetSecs](GetSecs)()  
timestamps for row 2 of the returned matrix, otherwise a cheap but  
inaccurate remapping is performed. The expensive procedure can take up to  
1 second, but is highly recommended for precise timestamps. See  
explanation of 'BoxsecsToGetsecs' function below for more details. You'll  
typically call this function only at the end of an experiment session.  
  
  
[PsychDataPixx](PsychDataPixx)('ClearTimestampLog');  
- Clear the log with all currently acquired timestamps.  
  
  
tgetsecs = [PsychDataPixx](PsychDataPixx)('FastBoxsecsToGetsecs', t);  
- Map given timestamp 't' in Datapixx clock time to Psychtoolbox [GetSecs](GetSecs)  
time and return it in 'tgetsecs'. This mapping is only precise if you  
call [PsychDataPixx](PsychDataPixx)('GetPreciseTime'); frequently. For a more accurate  
remapping use the following [PsychDataPixx](PsychDataPixx)('BoxsecsToGetsecs', t);  
instead, which is more time consuming to execute though.  
  
  
[tgetsecs, sd, ratio] = [PsychDataPixx](PsychDataPixx)('BoxsecsToGetsecs', t);  
- Perform remapping of a vector of Datapixx timestamps 't', ie.,  
timestamps expressed in Datapixx clock time, into Psychtoolbox [GetSecs](GetSecs)  
timestamps 'tgetsecs'. Return measures of accuracy of remapping.  
  
This must be called while the device is still open! It performs the same  
calibration procedure as [PsychDataPixx](PsychDataPixx)('GetTimestampLog', 1); and can  
easily take up to 1 second of time.  
  
The remapping is performed by fitting a mapping function to the set of  
acquired timestamp samples from both the Psychtoolbox [GetSecs](GetSecs) clock and  
the [DataPixx](DataPixx) clock. The best fit function is used for mapping [DataPixx](DataPixx)  
timestamps in 't' to PTB timestamps in 'tgetsecs'. 'sd' is the standard  
deviation of the best-fit function wrt. to fitting error. 'ratio' is an  
estimate of the clock speed difference between the host clock and the  
Datapixx clock.  
  
  
[PsychDataPixx](PsychDataPixx)('RequestPsyncedUpdate');  
- Request an update of the [DataPixx](DataPixx) register block in sync with the next  
visual stimulus onset as triggered by [Screen](Screen)('[Flip](Flip)') or  
[Screen](Screen)('AsyncFlipBegin'). This will emit the neccessary PSYNC pixel  
sequence at next flip and tell the device to apply all pending settings  
on reception of that PSYNC token.  
  
  
count = [PsychDataPixx](PsychDataPixx)('FlipCount');  
- Return "serial number" of the last executed visual stimulus update via  
one of the [Screen](Screen) "[Flip](Flip)" commands.  
  
  
[PsychDataPixx](PsychDataPixx)('ExecuteAtFlipCount', targetFlipCount, commandString);  
- Request execution of 'commandString' via eval() function in sync with  
the [Screen](Screen)('[Flip](Flip)') or [Screen](Screen)('AsyncFlipBegin') command which will  
cause the stimulus onset with "serial number" 'targetFlipCount'. You can  
ask for the current "serial number" by calling current = [PsychDataPixx](PsychDataPixx)('FlipCount');  
Providing an empty 'targetFlipCount' means to execute at next flip.  
  
Datapixx related commands in 'commandString' will be scheduled for  
execution on the device at next visual stimulus onset by use of the psync  
mechanism.  
  
Not all commands are allowed inside 'commandString'! Any call to [Screen](Screen)()  
or any [OpenGL](OpenGL) command is forbidden. Datapixx commands which could block  
execution to wait for the Datapixx , e.g., Datapixx('RegWrRd') are  
problematic, and the calls Datapixx('RegWrPixelSync') and  
Datapixx('RegWrRdPixelSync') are strictly forbidden!  
  
This function is mostly used by other higher-level [DataPixxToolbox](DataPixxToolbox)  
functions, e.g., for I/O (sound, digital or analog), in order to  
synchronize their operation and schedules to visual stimulus updates.  
  
  
[PsychDataPixx](PsychDataPixx)('LoadIdentityClut', win);  
- Load an identity CLUT into the device at next stimulus onset, ie., next  
'[Flip](Flip)' command for window 'win'. This is a pure convenience function for  
that common case. Normally you'd use [Screen](Screen)('LoadNormalizedGammaTable', win, clut, 2);  
to upload a new 'clut' table at next '[Flip](Flip)' command execution.  
  
  
oldverbosity = [PsychDataPixx](PsychDataPixx)('Verbosity' [,verbosity]);  
- Retrieve and optionally set a new level of 'verbosity' for driver debug  
output. verbosity can be 0 for no output, 1 for only errors, 2 for  
additionally warnings, 3 for additional info, 4 for very verbose output.  
  
  
oldtimeout = [PsychDataPixx](PsychDataPixx)('PsyncTimeoutFrames' [, timeoutFrames]);  
-- Query and/or set timeout (in video refresh cycles) for recognition of  
PSYNC codes by the device. By default, the timeout is set to the  
equivalent of 5 minutes, which means: If the device is instructed to wait  
for a PSYNC marker token in the video stream, but doesn't receive the  
expected token within 5 minutes, it will continue processing as if the  
token was received. This is used to prevent device-hangs on programming  
errors or other malfunctions. The default setting of 5 minutes is very  
generous. You can override this default and set an arbitrary timeout  
between 1 and 65535 video refresh cycles with this function.  
  
  
  
  
Normally you won't call the following functions yourself, as Psychtoolbox  
automatically performs neccessary setup during calls to [PsychImaging](PsychImaging)()  
that are related to the [DataPixx](DataPixx) device ("help [PsychImaging](PsychImaging)" for  
details).  
  
  
[PsychDataPixx](PsychDataPixx)('SetVideoMode', mode);  
-- Switch [DPixx](DPixx) device immediately into video processing mode 'mode'.  
Type "Datapixx [SetVideoMode](SetVideoMode)?" for a list of available 'mode' settings and  
explanation of their purpose and behaviour.  
  
  
[PsychDataPixx](PsychDataPixx)('SetVideoHorizontalSplit', mode);  
-- Switch [DPixx](DPixx) device immediately into video split mode 'mode'.  
Type "Datapixx [SetVideoHorizontalSplit](SetVideoHorizontalSplit)?" for a list of available 'mode'  
settings and explanation of their purpose and behaviour.  
  
  
[PsychDataPixx](PsychDataPixx)('SetVideoVerticalStereo', mode);  
-- Switch [DPixx](DPixx) device immediately into vertical stereo video mode 'mode'.  
Type "Datapixx [SetVideoVerticalStereo](SetVideoVerticalStereo)?" for a list of available 'mode'  
settings and explanation of their purpose and behaviour.  
  
  
[PsychDataPixx](PsychDataPixx)('EnableVideoScanningBacklight');  
-- Enable [ViewPixx](ViewPixx) panels scanning backlight.  
  
  
[PsychDataPixx](PsychDataPixx)('DisableVideoScanningBacklight');  
-- Disable [ViewPixx](ViewPixx) panels scanning backlight.  
  
  
[PsychDataPixx](PsychDataPixx)('EnableVideoStereoBlueline');  
-- Enable detection and handling of blue-line stereo sync lines by the  
[DataPixx](DataPixx).  
  
  
[PsychDataPixx](PsychDataPixx)('DisableVideoStereoBlueline');  
-- Disable detection and handling of blue-line stereo sync lines by the  
[DataPixx](DataPixx).  
  
  
Internal commands: NOT FOR USE BY PURE MORTALS!  
  
[PsychDataPixx](PsychDataPixx)('PerformPostWindowOpenSetup');  
-- Called by [PsychImaging](PsychImaging)('OpenWindow') after opening a window on the  
device. Performs all low-level setup for use of [DataPixx](DataPixx).  
  
  
rc = [PsychDataPixx](PsychDataPixx)('CheckGPUSanity', window, xoffset);  
-- Perform online-test of GPU identity gamma tables and DVI-D display  
encoders. Try to correct problems with wrong identity gamma tables and at  
least detect problems with (spatio-)temporal display dithering. Returns  
rc == 0 on full success, rc \> 0 on failure.  
  
  
[PsychDataPixx](PsychDataPixx)(-1);  
-- PTB callback: Request immediate emission of a PSYNC'ed [RegWrRd](RegWrRd) command  
to driver if a PSYNC is pending. Otherwise noop.  
  
  
[PsychDataPixx](PsychDataPixx)(0);  
-- PTB callback at '[Flip](Flip)' time: Do whatever [DPixx](DPixx) related work is  
pending for next '[Flip](Flip)', e.g., [DPixx](DPixx) clut updates, writing of PSYNC pixel  
sequences, preparation of logging of timestamps etc.  
  
  
[PsychDataPixx](PsychDataPixx)(1, clut);  
-- Callback for PTB imaging pipeline: Ultrafast upload of given 'clut'  
into the device at next bufferswap.  
  
  
[PsychDataPixx](PsychDataPixx)(2);  
-- Callback for PTB imaging pipeline after successfull finish of a  
bufferswap. Do whatever needs to be done, e.g., incrementing the  
swapcounter and logging of timestamps.  
  
  
[PsychDataPixx](PsychDataPixx)(3);  
-- Callback at time of closing the [DataPixx](DataPixx) onscreen window: Perform  
whatever actions are needed at shutdown, e.g., restoring identity clut on  
device, restoring default video mode and settings, closing device  
connection, cleanup of data structures etc.  
  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/DatapixxToolbox/DatapixxBasic/PsychDataPixx.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/DatapixxToolbox/DatapixxBasic/PsychDataPixx.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/DatapixxToolbox/DatapixxBasic/PsychDataPixx.m</code>
</div>

