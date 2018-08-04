# [ResponsePixx](ResponsePixx)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[DatapixxToolbox](DatapixxToolbox)>[DatapixxBasic](DatapixxBasic)

[ResponsePixx](ResponsePixx) - Control and use the [ResponsePixx](ResponsePixx) response button box.  
  
This allows to record button events from the [ResponsePixx](ResponsePixx) response box  
device. Start and stop of logging of button responses and control of the  
button lights (on/off and intensity) can be done immediately or  
synchronized to the operation of the [Screen](Screen)('[Flip](Flip)') command, ie.,  
synchronized to visual stimulus onset.  
  
By default, [ResponsePixx](ResponsePixx) response boxes with 5 buttons are supported.  
Specify the 'nrButtons' parameter in the 'Open' subfunction if you need a  
different button count.  
  
The code can scan the first 16 digital input pins of the Datapixx, i.e.,  
nrButtons can be up to 16, e.g., to control self-made response boxes. The  
last 8 input pins are not useable for timestamped button queries and are  
instead used to drive the button illumination of the [ResponsePixx](ResponsePixx)  
devices.  
  
Caution: Avoid intermixing 'StartNow'/'StopNow' commands with  
'StartAtFlip'/'StopAtFlip' commands. While this may work, there is some  
potential for using it the wrong way and producing very "funny" bugs.  
  
For reaction time measurements wrt. visual stimuli, see the timestamp  
logging functions of the [PsychDataPixx](PsychDataPixx) driver to get timestamps in  
Datapixx clock time. You can also calculate RT's in [GetSecs](GetSecs) time wrt. the  
host clock by using the usual [Screen](Screen)('[Flip](Flip)') or [PsychPortAudio](PsychPortAudio) stimulus  
onset timestamps, which may be even more convenient. However, if you do  
so, make sure that you read and understand the comments about achieving  
good precision by correcting for clock drift, both in the help of the  
[ResponsePixx](ResponsePixx) subfunctions and in the help of [PsychDataPixx](PsychDataPixx). Specifically  
look at [PsychDataPixx](PsychDataPixx)('GetPreciseTime') and  
[PsychDataPixx](PsychDataPixx)('BoxsecsToGetsecs').  
  
  
# Button mapping on the [ResponsePixx](ResponsePixx) handheld device  
  
Buttonvector element [1,2,3,4,5] == [Red, Yellow, Green, Blue, White].  
  
  
# Subfunctions and their meaning  
  
[ResponsePixx](ResponsePixx)('Open' [, numSamples=1000][, bufferBaseAddress=12e6][, nrButtons=5]);  
- Open [ResponsePixx](ResponsePixx) for button response collection. Configures the 24 bit  
digital input port of the [DataPixx](DataPixx) to receive button responses from a  
[ResponsePixx](ResponsePixx) response button box and to drive the button illumination  
lights of that box. Enabled button debouncing on the digital inputs.  
  
Optional argument 'numSamples' defines the maximum number of button  
transitions to log. Defaults to 1000 if omitted. 'bufferBasAddress' if  
provided is the memory start address of the logging buffer inside the  
Datapixx. Defaults to 12e6 if omitted.  
  
Optional argument 'nrButtons' defines the number of buttons to query. Can  
be up to 16 buttons for the first 16 TTL inputs of the [DataPixx](DataPixx), but  
defaults to 5 buttons - the maximum number supported by the current  
[ResponsePixx](ResponsePixx) devices.  
  
This function doesn't start logging of responses. Call the 'StartNow' or  
'StartAtFlip' subfunction for start of response collection. Call  
'StopNow' or 'StopAtFlip' to stop response collection.  
  
  
[ResponsePixx](ResponsePixx)('[Close](Close)');  
- [Close](Close) [ResponsePixx](ResponsePixx) after stopping any running logging operations.  
Disable the button lights and reset the digital input port of the  
Datapixx.  
  
  
[startTimeBox, startTimeGetSecs] = [ResponsePixx](ResponsePixx)('StartNow' [, clearLog=0][, buttonLightState][, buttonLightIntensity]);  
- Start button response collection immediately (ie., with minimum  
possible delay on your system). Set the optional 'clearLog' flag to 1 if  
all currently stored button responses should be discarded prior to  
logging of new responses, e.g., at start of a new trial.  
  
The optional vector 'buttonLightState' allows to define the on/off state  
of the button illumination, e.g., buttonLightState = [0,1,0,0,1] would  
turn on the light inside button 2 and 5 and turn off the lights in  
buttons 1, 3 and 4. By default, the state of the button lights is not  
changed. The optional value 'buttonLightIntensity' in the range 0.0 to  
1.0 controls the intensity of the button illumination.  
  
Returns a 'startTimeBox' timestamp in Datapixx clock time of when  
acquisition actually started. You can also use the 2nd optional return  
argument 'startTimeGetSecs' to get the same timestamp mapped to  
Psychtoolbox [GetSecs](GetSecs)() time. For a more precise post-hoc mapping to  
[GetSecs](GetSecs) time, you can convert the 'startTimeBox' timestamp into  
Psychtoolbox [GetSecs](GetSecs)() time with the proper mapping functions of  
[PsychDataPixx](PsychDataPixx) (see "help [PsychDataPixx](PsychDataPixx)").  
  
The function can be called multiple times, while logging is already  
started, if you just want to clear the log of stored responses or change  
the state of the button lights.  
  
  
[ResponsePixx](ResponsePixx)('StartAtFlip' [, flipCount=next][, clearLog=0][, buttonLightState][, buttonLightIntensity]);  
- Schedule start of response collection synchronized to the visual stimulus  
onset of a future [Screen](Screen)('[Flip](Flip)') or [Screen](Screen)('AsyncFlipBegin') command.  
  
All parameters are identical to the ones for [ResponsePixx](ResponsePixx)('StartNow',...),  
except for the first optional parameter 'flipCount'. 'flipCount' defines  
at which [Screen](Screen)('[Flip](Flip)') acquisition should be started. If omitted or  
set to zero or [], acquisition will be started by the next flip command.  
Otherwise it will be started by the flip command with the given  
'flipCount'. You can query the current flipCount via [PsychDatapixx](PsychDatapixx)('FlipCount').  
  
Example: Setting flipCount = [PsychDatapixx](PsychDatapixx)('FlipCount') + 10; would start  
acquisition at the 10'th invocation of a flip command from now.  
  
This function doesn't return a start timestamp as acquisition will  
only happen in the future, so the timestamp is only available in the  
future.  
  
  
[stopTimeBox, stopTimeGetSecs] = [ResponsePixx](ResponsePixx)('StopNow' [, clearLog=0][, buttonLightState][, buttonLightIntensity]);  
- Stop button response collection immediately (ie., with minimum  
possible delay on your system). See 'StartNow' for meaning of optional  
arguments.  
  
The function can be called multiple times, while logging is already  
stopped, if you just want to clear the log of stored responses or change  
the state of the button lights.  
  
  
[ResponsePixx](ResponsePixx)('StopAtFlip' [, flipCount=next][, clearLog=0][, buttonLightState][, buttonLightIntensity]);  
- Schedule stop of response collection synchronized to the visual stimulus  
onset of a future [Screen](Screen)('[Flip](Flip)') or [Screen](Screen)('AsyncFlipBegin') command.  
See 'StartAtFlip' for meaning of parameters.  
  
  
[buttonStates, transitionTimesSecs, underflows] = [ResponsePixx](ResponsePixx)('GetLoggedResponses' [, numberResponses=current][, blocking=1][, timeout=inf]);  
- Try to fetch logged button responses from a running logging  
operation. Only call this function after logging has been  
started via [ResponsePixx](ResponsePixx)('StartNow') or scheduled for start at a  
certain flipCount via [ResponsePixx](ResponsePixx)('StartAtFlip') and the flip is  
imminent, i.e., after the flip command for that flip has been called  
already. The function will error-out if you call it too early!  
  
The optional 'numberResponses' asks the driver to return exactly  
'numberResponses' button transitions. By default it will return whatever  
is available at time of call. If 'numberResponses' is specified, but the  
requested amount is not yet available, the optional 'blocking' flag will  
define behaviour: If set to 1 (default), the driver will wait until the  
specified amount becomes available. If set to 0, the driver will return  
with empty [] return arguments so you can retry later. If 'blocking' is  
set, then the driver will wait for at most 'timeout' seconds for a  
response, then return anyway. By default the timeout is infinite.  
  
'buttonStates' is a n-by-5 matrix: The n'th row encodes the button state  
after the n'th transition of button state. Each column encodes up/down  
state of a button, ie., the j'th column encodes state of the j'th button.  
0 = Button released, 1 = Button pressed. A button press followed by a  
release would create two rows of button transition, one for the  
buttonState after pressing a button, a second one for the state after  
releasing the button. The [ResponsePixx](ResponsePixx) uses a debouncing algorithm to  
filter out multiple transitions within a 30 msecs time window.  
  
'transitionTimesSecs' is the vector of timestamps in Datapixx clock time  
of when the corresponding button state has changed. The i'th element  
corresponds to the time when the i'th element in the 'buttonStates'  
vector was logged due to a change in button state at that time. See  
"help [PsychDataPixx](PsychDataPixx)" on how to map these box timestamps to [GetSecs](GetSecs)()  
timestamps if you wish.  
  
'underflows' is the number of times the logging buffer underflowed. This  
indicated lost or corrupted button events. It should only happen if your  
subject pressed more buttons within two calls to 'GetLoggedResponses'  
than the event buffer can hold. The size of the buffer can be selected at  
'Open' time with the 'numSamples' parameter, but it defaults to a  
generous 1000 button events.  
  
  
[buttonStates, boxTimeSecs, getsecsTimeSecs] = [ResponsePixx](ResponsePixx)('GetButtons');  
- Perform immediate query of response box button states. Return current  
state in 'buttonStates' and corresponding box time and [GetSecs](GetSecs) time  
timestamps of time of query in 'boxTimeSecs' and 'getsecsTimeSecs'.  
  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/DatapixxToolbox/DatapixxBasic/ResponsePixx.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/DatapixxToolbox/DatapixxBasic/ResponsePixx.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/DatapixxToolbox/DatapixxBasic/ResponsePixx.m</code>
</div>

