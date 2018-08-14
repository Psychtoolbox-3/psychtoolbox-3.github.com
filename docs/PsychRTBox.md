# [PsychRTBox](PsychRTBox)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)

Driver for the USTC reaction time button box [(RTBox)]((RTBox)) by Xiangrui Li et al.  
varargout = [PsychRTBox](PsychRTBox)(cmd, varargin);  
  
This driver allows to control most functions of the USTC [RTBox](RTBox) response  
button box. In theory this driver should support boxes up to Box/Firmware  
version 5. In practice it has only been tested by the Psychtoolbox  
developer up to firmware and box version 1.3, therefore you may encounter  
bugs for later versions. The box itself comes bundled with an alternative  
driver called "[RTBox](RTBox)" which is maintained by the developers of the box  
hardware itself, in case this driver doesn't work with your box or  
firmware.  
  
The [RTBox](RTBox) is a USB device which provides 4 response buttons (pushbuttons)  
for subject responses and can report any button press- or release by the  
subject. Additionally it has an input for reporting of external  
electronic trigger signals and a photo-diode input for reporting of  
visual stimulus onset. The box uses a built-in high-resolution clock to  
timestamp all button- or trigger events, independent of the host  
computers clock in order to make it more reliable for response time  
measurements than most other response devices. It also buffers all events  
internally, so experiment scripts can read back events when it is most  
convenient. Timestamps can be either reported in Psychtoolbox standard  
[GetSecs](GetSecs) timebase for direct comparison with timestamps from [GetSecs](GetSecs),  
[WaitSecs](WaitSecs), [KbCheck](KbCheck) et al., [Screen](Screen)('[Flip](Flip)') and [PsychPortAudio](PsychPortAudio), etc. This  
simplifies reaction time calculations. Timestamps can also be reported in  
the timebase of the boxe, e.g., time of a button press relative to the  
photo-diode light trigger signal or electronic trigger signal, if this is  
more convenient for a given experiment setup.  
  
Current versions of the [RTBox](RTBox) have additional functionality, e.g., more  
digital trigger inputs, some sound trigger, and TTL trigger outputs.  
  
See http://lobes.osu.edu/rt-box.php for up to date product information and  
additional driver software.  
  
Please note that while the device documentation claims that the external  
electronic pulse port is able to receive TTL trigger signals, we couldn't  
verify that this is the case with our test sample of version 1 of the  
[RTbox](RTbox) hardware. While the pulse input port responded to some pulses sent  
by one TTL compatible device, it failed to detect the majority of signals  
from TTL most other test devices.  
  
This indicates that the pulse port may not be fully TTL compliant and  
will need additional tinkering for your setup. However, results with  
later versions of the hardware may be different than our experience with  
our test sample.  
  
  
The following subcommands are currently suppported:  
===================================================  
  
  
handle = [PsychRTBox](PsychRTBox)('Open' [, deviceID] [, skipSync=0]);  
-- Try to open a connected [RTBox](RTBox), return a device handle 'handle' to it  
on success. The handle can be used in all further subcommands to refer to  
the box. By default, all USB ports (or rather USB-Serial ports) are scanned  
for a connected [RTBox](RTBox) and the driver will connect to the first box found.  
Alternatively you can specify which box to use via the optional  
'deviceID' namestring. This can be either the name of a box, or the name  
of the USB-Serial port to which the box is connected. This way you can avoid  
scanning of all ports and disambiguate in case multiple boxes are  
connected to your computer.  
  
Btw., if you only make use of one single [RTBox](RTBox), you don't need to specify  
the 'handle' parameter to all following subfunctions. Instead you can  
specify that parameter as [] or omit it and the driver will use the only  
open box connected.  
  
The optional parameter 'skipSync', if set to 1, will prevent the open  
routine from performing an initial clock synchronization. By default, it  
will perform an initial clock synchronization.  
  
### After opening the box, you may want to invoke this method:  
  
  
clockRatio = [PsychRTBox](PsychRTBox)('ClockRatio' [, handle] [, durationSecs]);  
-- Perform a clock drift calibration between the computers [GetSecs](GetSecs) host  
clock and the internal clock of the box 'handle'. Restrict calibration to  
a maximum of 'durationSecs' (default 60 seconds if omitted). Return the  
computed 'clockRatio' and use it for all further operations.  
  
Due to manufacturing imperfections and environmental factors, no two  
clocks ever run at exactly the same speed. Therefore the computer clock  
and box clock will slowly "drift out of sync" under normal conditions,  
rendering retrieved event timestamps inaccurate over the course of a long  
experiment session. This calibration routine will exercise the clocks and  
compute the clock drift due to this speed difference, then use the  
computed drift (= clockRatio) to correct all reported timestamps for this  
drift, thereby providing the accuracy needed for reaction time studies.  
  
The clockRatio value tells, how many seconds of [GetSecs](GetSecs) time elapse when  
the box clock measures 1 second elapsed time. Ideally this value would be  
1, ie. both clocks run at the same speed. A more realistic value would be,  
e.g., 1.000009 -- The computer clock goes 9 microseconds faster than the  
box clock, so the drift will accumulate an error of 9 microseconds for  
each elapsed second of your study.  
  
As every calibration, this routine involves some measurement/calibration  
error and is therefore not perfect, so even after a successfull  
'ClockRatio' calibration, timestamps reported during your experiment will  
accumulate some error during the course of long experiment sessions.  
  
### There are multiple ways to handle this:  
  
a) Use a long calibration time in this function for accurate results, and  
a reasonably short experiment duration.  
  
b) Repeat this procedure after every large block of trials, ie., every  
couple of minutes, e.g., while the subject is allowed to take a break in  
a long experiment session.  
  
c) Use the [PsychRTBox](PsychRTBox)('SyncClocks') function after each short block of  
trials, or even after each trial, for the highest accuracy.  
  
d) Don't care for clock drift throughout the experiment session, just  
collect the event timestamps in box clock format (see the 3rd return  
argument of [PsychRTBox](PsychRTBox)('GetSecs') or the returned timing array of  
[PsychRTBox](PsychRTBox)('BoxSecs');) and store them in some array. Remap all timestamps  
into the computers [GetSecs](GetSecs) time at the end of your session via  
[PsychRTBox](PsychRTBox)('BoxsecsToGetsecs'). This requires a bit more  
discipline from you in programming and organizing your data, but it  
provides the most accurate timestamps.  
  
  
[syncResult, clockRatio] = [PsychRTBox](PsychRTBox)('SyncClocks' [, handle]);  
-- Synchronize or resynchronize the clocks of the host computer and the  
box. Return result in 'syncResult' and the current clockRatio in  
'clockRatio'. This routine is automatically carried out during invocation  
of [PsychRTBox](PsychRTBox)('ClockRatio'); but you can repeat the sync procedure  
anytime between trials via this subfunction for extra accuracy at the  
expense of about 0.5 - 1 second additional time for each invocation. You  
would typically execute this function at the start of each large block of  
trials, or before start of each trial if you are really picky about  
super-exact timing. The syncResult contains three values:  
  
syncResult(1) = Host time [(GetSecs]((GetSecs) time) at time of clock sync.  
  
syncResult(2) = Box time at time of clock sync.  
  
syncResult(3) = Confidence interval for the accuracy of the sync. This  
value (in seconds) provides a reliable upper bound for the possible error  
introduced in all reported timestamps from the box. The real error may be  
significantly smaller, this is just an upper bound that you can check.  
Typical results on a well working system should be in the sub-millisecond  
range, e.g., 0.0003 seconds or 0.3 msecs. Typical results on a rather  
noisy system would be around 0.001 second or 1 msec. Results worse than 2  
msecs indicate some problem with your system setup that should be fixed  
before executing any experiment study which involves reaction time  
measurements. By default, the sync procedure will abort with an error if  
it can't calibrate to an accuracy with a maximum error of 1.3 msecs within  
a duration of 0.5 seconds. You can change these default constraints with  
a call to [PsychRTBox](PsychRTBox)('SyncConstraints').  
  
  
[oldmaxDurationSecs, oldgoodEnoughSecs, oldrequiredSecs, oldsyncMethod] = [PsychRTBox](PsychRTBox)('SyncConstraints'[, maxDurationSecs][, goodEnoughSecs][, requiredSecs][, syncMethod]);  
-- Change the constraints to apply during calls to [PsychRTBox](PsychRTBox)('SyncClocks');  
Optionally return old settings.  
  
'maxDurationSecs' limits any call to 'SyncClocks' to a duration of at  
most the given number of seconds. Calibration aborts after at most that  
time, even if unsuccessfull - in that case with an error message. By  
default, the duration is limited to 0.5 seconds.  
'goodEnoughSecs' Calibration will finish before 'maxDurationSecs' have  
elapsed, if the result is more accurate than an error of at most  
'goodEnoughSecs'. By default, this is set to zero seconds, i.e.,  
calibration will always take 'maxDurationSecs'.  
'requiredSecs' - The calibration will only use samples with an  
uncertainty of at most 'requiredSecs'. If not even a single sample of the  
required precision can be acquired within 'maxDurationSecs', the call  
will fail with an error, indicating that your system setup doesn't  
provide the required timing precision for your demands. By default, the  
minimum required precision is 0.0013 seconds, ie., it will tolerate an  
error of at most 1.3 msecs.  
'syncMethod' - Select the synchronization method to use. Either, method 0  
(prewrite sync), or method 1 (postwrite sync), or method 2 (average). If  
you want to know the difference between the methods, please consult the  
source code of this file and read the code for the subroutine 'function  
syncClocks'. All three methods are robust and accurate within the  
returned confidence window, usually better than 1 msec. So far, method 1  
seems to get the best results on our test setups, so this is the default  
for the current driver release. However, we are still evaluating if  
method 0 would be a tiny bit better and worth switching the default to  
that.  
  
  
oldverbose = [PsychRTBox](PsychRTBox)('Verbosity' [, handle], verbosity);  
-- Set level of verbosity for driver: 0 = Shut up. 1 = Report errors  
only. 2 = Report warnings as well. 3 = Report additional status info. 4 =  
Be very verbose about what is going on. The default setting is 3 --  
Report moderate status output.  
  
  
devinfo = [PsychRTBox](PsychRTBox)('BoxInfo' [, handle] [, newdevinfo]);  
-- Return a struct 'devinfo' with all information about the current  
status and parameter settings for [RTBox](RTBox) 'handle'. Optionally set a new  
struct with updated parameters via 'newdevinfo'. This function is mostly  
useful for debugging and benchmarking the driver itself. Most information  
contained in 'devinfo' will be useless for your purpose.  
  
  
[PsychRTBox](PsychRTBox)('[Close](Close)', handle);  
-- [Close](Close) connection to specific box 'handle'. Release all associated  
ressources.  
  
  
[PsychRTBox](PsychRTBox)('CloseAll');  
-- [Close](Close) connections to all attached [RTBox](RTBox) devices. Reset the [PsychRTBox](PsychRTBox)  
driver completely. You'll usually use this function at the end of your  
experiment script to clean up.  
  
  
oldeventspec = [PsychRTBox](PsychRTBox)('Enable' [,handle][, eventspec]);  
-- Enable specified type of event 'eventspec' on box 'handle'. This  
allows to enable detection and reporting of a specific type of event. By  
default, only reporting of push-button press is enabled, as this is the  
most common use of a response box.  
  
The following names are valid for the name string 'eventspec':  
'press' = Report push-button press. This is the default setting.  
'release' = Report push-button release.  
'pulse' = Report electronic trigger events on external input port.  
'light' = Report reception of light flashes by photo-diode on light port.  
'tr' = Report reception of scanner trigger "TR" (TTL input from pin 7 of DB-9 port).  
'all' = Enable all events.  
  
If called without the 'eventspec' parameter, the function will return the  
names of all currently enabled events.  
  
  
oldeventspec = [PsychRTBox](PsychRTBox)('Disable' [,handle][, eventspec]);  
-- Disable specified type of event 'eventspec' on box 'handle'. This  
allows to disable detection and reporting of a specific type of event. By  
default, only reporting of push-button press is enabled, as this is the  
most common use of a response box.  
  
See 'Enable' call for help on parameters.  
  
  
Once you have setup and calibrated the box and selected the type of  
events to detect and report, you will want to actually retrieve  
information about events. For this you use these commands:  
  
  
[PsychRTBox](PsychRTBox)('Start' [, handle] [, dontwaitforstart=0]);  
-- Start event detection and reporting by the box. The box will start  
detecting button and trigger events from here on and record them in the  
event buffer.  
  
You will usually call this at the beginning of a response period. By  
default, the box has reporting already enabled after 'Open'ing it.  
  
The optional 'dontwaitforstart' parameter, if set to 1, will ask the  
'Start' function to return control as soon as possible, ie., without  
waiting for confirmation of the box that event reporting has actually  
started. By default, the routine waits for an acknowledgement from the  
box, which can take 16 - 30 msecs in some cases.  
  
  
[PsychRTBox](PsychRTBox)('Stop' [, handle]);  
-- Stop event detection and reporting by the box. The box will ignore  
detecting button and trigger events from here on and no longerrecord them  
in the event buffer.  
  
You will usually call this at the end of a response period.  
  
  
[PsychRTBox](PsychRTBox)('Clear' [, handle] [, syncClocks=0] [, dontRestart=0]);  
-- Stop event detection and reporting by the box, clear all recorded  
events so far, then restart reporting if it was active before calling  
this function.  
  
Instead of calling 'Start' and 'Stop' to mark the start and end of a  
response period in a trial you can also simply use this function at the  
beginning of a trial (or its response period) to discard any stale data  
from a previous trial (or non-response interval).  
  
You can prevent an automatic restart of event reporting by setting the  
optional flag 'dontRestart' to a value of 1.  
  
You can ask the box to resynchronize its clock to the host computer clock  
by setting the optional flag 'syncClocks' to a value of 1. This is the  
same as calling [PsychRTBox](PsychRTBox)('SyncClocks').  
  
  
[time, event, boxtime] = [PsychRTBox](PsychRTBox)('GetSecs' [, handle] [, interTimeout=0.1] [, maxTimeout=interTimeout] [, maxItems=inf]);  
-- Retrieve recorded events from the box 'handle'.  
  
By default, as many events are returned as are available within the  
test interval, but you can select a specific number of wanted events  
by setting the optional parameter 'maxItems'. If there aren't any pending  
events from the box, by default the driver waits for up to 0.1 seconds  
for events to arrive. You can change this 'interTimeout' interval via the  
positive (non-zero) 'interTimeout' parameter. The function will return if  
no new events show up within 'interTimeout' seconds. If something shows  
up, the deadline for return is extended by 'interTimeout' seconds. You  
can set an absolute upper limit to the response interval via the  
'maxTimeout' parameter. That defaults to 'interTimeout' if omitted.  
Please note that after an event is detected by the box, up to 16-32 msecs  
can elapse until the event is received by the computer, so you may not  
want to set these timeout values too small!  
  
The function will return an array of timestamps in 'time', and an array  
of corresponding names of the events in 'event'. E.g., event(1) will  
report the identity of the first detected event, e.g., '1' if button 1  
was pressed, whereas time(1) will tell you when the event happened, ie.,  
when button 1 was pressed. 'time' is expressed in host clock time, aka  
[GetSecs](GetSecs)() time. If no events are pending since last invocation of this  
function, empty vectors will be returned.  
  
Additionally, the vector 'boxtime' contains the same timestamp, but  
expressed in box clock time. See below for a use of that.  
  
### By default, the following names are possible for 'event's:  
  
'1' = 1st button pressed, '1up' = 1st button released.  
'2' = 2nd button pressed, '2up' = 2nd button released.  
'3' = 3rd button pressed, '3up' = 3rd button released.  
'4' = 4th button pressed, '4up' = 4th button released.  
'pulse' = electronic pulse received on electronic pulse input port.  
'light' = Light pulse received by photo-diode connected to light input port.  
'tr' = Scanner trigger "TR" (TTL input from pin 7 of DB-9 port) received.  
'serial' = [PsychRTBox](PsychRTBox)('Trigger') Softwaretrigger signal received on USB-Serial port.  
  
Note: 'tr' is only supported on boxes with Firmware version 3.0 or later.  
  
However, you can assign arbitrary names to the buttons and events if you  
don't like this nomenclature via the [PsychRTBox](PsychRTBox)('ButtonNames') command.  
  
The reported timestamps are expressed in host clock time, ie., in the  
same units as the timestamps returned by [GetSecs](GetSecs), [Screen](Screen)('[Flip](Flip)'),  
[PsychPortAudio](PsychPortAudio), [KbCheck](KbCheck), [KbWait](KbWait), etc., so you can directly calculate  
reaction times to auditory stimuli, visual stimuli and other events.  
  
See the help for [PsychRTBox](PsychRTBox)('SyncClocks') and [PsychRTBox](PsychRTBox)('ClockRatio')  
for the accuracy of these timestamps and tips for obtaining optimal  
accuracy.  
  
Additionally the event times are also returned in 'boxtime', but this  
time expressed in box time -- the time of the box internal clock.  
  
  
There are multiple variants of this query command with the same optional  
input arguments, but different return arguments. All of these return  
timestamps in box time without remapping to [GetSecs](GetSecs) time by calling:  
  
[boxtime, event] = [PsychRTBox](PsychRTBox)('BoxSecs' ...);  
-- Timestamps are in raw box clock time, everything else is the same as  
in [PsychRTBox](PsychRTBox)('GetSecs' ...).  
  
If you have the 'boxtime' timestamps from one of the previous functions  
around, you can map them later to [GetSecs](GetSecs) time with very high precision  
at the end of your experiment session via:  
  
[[GetSecs](GetSecs), Stddev] = [PsychRTBox](PsychRTBox)('BoxsecsToGetsecs' [, handle], boxTimes);  
-- Perform a post-hoc mapping of a vector of raw box timestamps  
'boxTimes' into a vector of host clock 'GetSecs' timestamps. Return some  
error measure in 'Stddev' as well, if available.  
  
This method can be used to convert event timestamps expressed in the box  
clocks timebase into timestamps in Psychtoolbox [GetSecs](GetSecs) host clock  
timebase. It has the advantage of providing the highest possible accuracy  
in mapping, because it computes an optimal mapping function for this  
purpose, which is based on all the timing information collected  
throughout a whole experiment session. The disadvantage is that it will  
only provide meaningful results if you call it at the end of your  
experiment session, so you'll need to manage all your collected  
timestamps in a format that is suitable as input to this function.  
  
  
Timestamps can also be returned relative to a specific trigger event: You  
specify which event acts as a trigger. Then all timestamps of all events  
are expressed relative to the time of that trigger event, i.e., as  
deltas. Any event can be the trigger. Format of all arguments is  
as in [PsychRTBox](PsychRTBox)('BoxSecs' ...);  
  
E.g., [PsychRTBox](PsychRTBox)('serial', ...); Returns timestamps relative to the first  
occurence of a electronic input port trigger signal since the last query.  
[PsychRTBox](PsychRTBox)('light', ...); Returns timestamps relative to photo-diode  
light pulse. [PsychRTBox](PsychRTBox)('1'); returns relative to press of 1st button,  
etc. etc.  
  
  
sendTime = [PsychRTBox](PsychRTBox)('SerialTrigger' [, handle]);  
-- Send a software generated trigger to the box via the serial port  
connection. This will register as a event of type 'serial' and you can  
retrieve timestamps relative to the first trigger within a response  
period via the [PsychRTBox](PsychRTBox)('serial', ...); command.  
  
  
sendTime = [PsychRTBox](PsychRTBox)('EngageLightTrigger [, handle]);  
sendTime = [PsychRTBox](PsychRTBox)('EngagePulseTrigger [, handle]);  
sendTime = [PsychRTBox](PsychRTBox)('EngageTRTrigger [, handle]);  
  
-- Engage trigger input on the box for reception of a one-shot trigger  
signal. This function will return immediately after submitting the  
request to the box. It may take up to 5 msecs worst-case until the  
trigger input is really enabled. If you want to wait for the trigger to  
be really enabled, call, e.g., [PsychRTBox](PsychRTBox)('Enable', handle, 'lighton'); instead,  
as that function will wait until the trigger is really active.  
  
Trigger events are special: If a trigger has been received, the  
box auto-disables the trigger input, preventing reception of any  
further trigger events, until the trigger gets reenabled. The trigger gets  
reenabled on many occasions if it has been enabled once via the  
[PsychRTBox](PsychRTBox)('Enable', ...); command, e.g., at each call to  
[PsychRTBox](PsychRTBox)('Start'); or [PsychRTBox](PsychRTBox)('Clear'). If you want to enable the  
trigger on-the-fly, then this function is your friend.  
  
The reason why light trigger auto-disables itself is because a typical  
CRT display monitor would generate such trigger signals at the rate of  
video refresh, once your stimulus is displayed, e.g., at a rate of 100  
Hz. Usually you only want to know one defined timestamp of initial  
stimulus onset, therefore the box prevents reception of all but the  
first light trigger.  
  
Similar reasoning applies to Pulse and TR triggers.  
  
  
oldNames = [PsychRTBox](PsychRTBox)('ButtonNames' [, handle] [, newNames]);  
-- Query or assign labels for the four response box buttons other than  
the default names.  
  
This function allows to assign arbitrary names to the four buttons on the  
box. These names are reported when querying for button presses and  
releases. By default, oldNames = [PychRTBox](PychRTBox)('ButtonNames') would return  
the cell array with the four following names: '1', '2', '3', '4'. These  
are the names reported for button presses. Button releases would report  
the names with an 'up' appended, ie., '1up', '2up', '3up', '4up'. You can  
assign arbitrary new names by passing a cell array with four namestrings,  
e.g., [PsychRTBox](PsychRTBox)('ButtonNames', [], {'7', 'whats', 'hick', 'screw'})  
would assign the names '7', 'whats', 'hick' and 'screw' for button press  
events, and '7up', 'whatsup', 'hickup' and 'screwup' for release events  
of the corresponding buttons.  
  
Please note that the assignment of names to buttons must be unique, ie.  
assigning the same name to multiple buttons is not allowed.  
  
  
oldIntervals = [PsychRTBox](PsychRTBox)('DebounceInterval' [, handle] [, debounceSecs]);  
-- Query current button debounce intervals (in 4-element vector  
'oldIntervals', one value for each button), and optionally set new  
debounce interval in seonds via the optional argument 'debounceSecs'.  
'debounceSecs' can be a scalar, in which case the same setting is applied  
to all buttons, or a 4-element row vector, e.g., [0.1, 0.1, 0.1, 0.1] to  
set an individual interval for each of the four buttons.  
  
The built-in debouncer prevents multiple button responses (button press  
or release actions) from getting recorded/reported within some  
'debounceSecs' debounce interval. After a button has changed state, only  
the type (press or release), identity (which button) and timestamp (when)  
of the first state change is reported. Any other state change within  
'debounceSecs' seconds of time after that first change will be ignored.  
After that time has elapsed, further state changes are reported again. By  
default, this dead "debounce" interval is set to 0.050 seconds, ie., 50  
msecs. Button bouncing happens if a subject presses or releases a button  
very rapidly or vigorously. If such quick multiple events or bounces are  
not ignored, they will create multiple apparent button responses which  
are a hazzle to deal with in experiment scripts and data analysis.  
  
If you find multiple responses generated for only one apparent button  
press during piloting, you may want to set a bigger debounce interval  
with this function.  
  
Please note that debouncing doesn't apply to the [PsychRTBox](PsychRTBox)('ButtonDown')  
function.  
  
Please also note that there is another hardware debouncer with a duration  
of 0.3 msecs on [RTBox](RTBox) versions with firmware versions 1.3 and older, which  
can't be disabled, so even if you'd set a zero interval here, you'd still  
get a minimum 0.3 msecs debounce period from the hardware itself.  
  
Later versions of the firmware support the following  
[PsychRTBox](PsychRTBox)('HardwareDebounce') command to control the hardware debounce  
interval more fine-grained.  
  
  
[oldValue] = [PsychRTBox](PsychRTBox)('HardwareDebounce' [, handle] [, scanNum]);  
-- Set/get hardware debouncer setting. The hardware will treat a button  
event as valid only if the button state stays stable for at least  
'scanNum' scanning iterations of the firmware. The scan interval is about  
67 microseconds. The valid scanNum is from 1 through 255, with a default  
setting of 16 cycles for 1.072 msecs debounce interval.  
  
For software debouncing at the driver level, see [PsychRTBox](PsychRTBox)('DebounceInterval')  
above.   
  
  
buttonState = [PsychRTBox](PsychRTBox)('ButtonDown' [, handle] [, whichButtons]);  
-- This reports the current button state of all response buttons of box  
'handle', or a subset of response buttons if specified by the optional  
'whichButtons' argument, e.g., whichButton = {'1', '4'} to only test  
buttons 1 and 4. 'buttonState' is a vector which contains a 1 for each  
pressed button, and a zero for each released button.  
  
This query is as instantaneous and "live" as possible. The reported state  
is not subject to button debouncing, but the measured "raw state".  
Usually you will want to use the [PsychRTBox](PsychRTBox)('GetSecs' ...) functions ans  
similar functions to query timestamped button state. They are typically  
as fast as this method and they provide timestamps of when the state was  
queried, whereas this function doesn't give you information about how  
"fresh" or recent the query is. However for simple button queries outside  
the response interval, e.g., while the box is [PsychRTBox](PsychRTBox)('Stop')'ped with  
no need for timestamps, this may be an option.  
  
Due to the design of the USB bus, the query may be outdated wrt. to the  
real state by up to 16 - 21 msecs, depending on operating system and  
driver configuration.  
  
  
buttonState = [PsychRTBox](PsychRTBox)('WaitButtonDown' [, handle] [, whichButtons]);  
-- Wait until at least one of the specified buttons in 'whichButtons' is  
pressed down. If 'whichButtons' is omitted, all buttons are tested.  
  
  
[PsychRTBox](PsychRTBox)('WaitButtonUp' [, handle] [, whichButtons]);  
-- Wait until all of the specified buttons in 'whichButtons' are  
released. If 'whichButtons' is omitted, all buttons are tested.  
  
  
[timeSent, confidence] = [PsychRTBox](PsychRTBox)('TTL' [, handle] [, eventCode=1]);  
- Send TTL to DB-25 port (pin 8 is bit 0). The second input is event code  
(default 1 if omitted), 4-bit (0~15) for box versions < 5, and 8-bit  
(0~255) for later versions. It can also be equivalent binary string, such  
as '0011'.  
  
The optional return arguments are the 'timeSent' when the TTL update was  
performed, and an upper bound on the uncertainty 'confidence' of  
'timeSent'.  
  
The width (duration) of the TTL pulse is controlled by the  
[PsychRTBox](PsychRTBox)('TTLWidth') command.  
  
This function is only supported for v3.0 [RTBoxes](RTBoxes) and later, the ones with  
EEG event code support.  
  
  
[oldValue] = [PsychRTBox](PsychRTBox)('TTLWidth' [, handle][, widthSecs]);  
- Set/get TTL pulse width in seconds. The default width is 0.97e-3, ie.  
97 microseconds when the device is opened. The actual width may have some  
small variation. The supported width ranges from 0.14e-3 to 35e-3 secs. A  
infinite width 'inf' is also supported. Infinite width means the TTL will  
stay until it is changed by the next [PsychRTBox](PsychRTBox)('TTL') command, such as  
[PsychRTBox](PsychRTBox)('TTL',0).  
  
This function is only supported for v3.0 [RTBoxes](RTBoxes) and later, the ones with  
EEG event code port support.  
  
In Version <5.0, the TTL width at DB-25 pins 17~24 is controlled by a  
potentiometer inside the box. In Version \>= 5, the width is also  
controlled by 'TTLWidth' command.   
  
  
[oldValue] = [RTBox](RTBox)('TTLResting' [, handle][, newLevel]);  
- Set/get TTL polarity for DB-25 pins 1~8. The default is 0, meaning the  
TTL resting is low. If you set newLevel to nonzero, the resting TTL will  
be high level. If you need different polarity for different pins, let us  
know. This function is only supported with firmware version 3.1 and  
later.  
  
In Version 5.0 and later, newLevel has second value, which is the  
polarity for pins 17~24.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/PsychRTBox.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/PsychRTBox.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/PsychRTBox.m</code>
</div>

