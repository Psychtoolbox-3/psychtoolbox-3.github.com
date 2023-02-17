# [PsychPowerMate](PsychPowerMate)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)

[PsychPowerMate](PsychPowerMate) - A driver for the Griffin Technology [PowerMate](PowerMate) USB knob.  
  
### Note:  
  
This driver is currently only for the [PowerMate](PowerMate) USB edition, not for the  
bluetooth product. It best supports modern Linux systems, e.g.,  
Ubuntu 14.04.2 LTS or later, Debian-8 or later, or other similar modern  
systems with version 2.9.0 or later of the "evdev" X11 input driver.  
  
Support on Apple OSX and Microsoft Windows is much more limited. Expect  
worse reliability, higher cpu load, higher latencies, less accurate  
timing. While on Linux, the current driver can internally record up to  
104 full knob rotations by default, or an unlimited number with suitable  
options set, without losing information, the Windows variant can at most  
record 5 rotations, and the OSX driver will probably not even manage to  
record one full rotation. To avoid loss of position data, you will need  
to call [PsychPowerMate](PsychPowerMate)('Get') frequently on OSX and Windows, even if you  
do not need the information at that moment.  
  
On Windows, setting LED brightness does not work.  
  
Linux setup:  
============  
  
You must install a specific xorg input configuration file for the [PowerMate](PowerMate)  
to be recognized. In a terminal window do:  
  
1. cd into the Psychtoolbox working directory (output of [PsychtoolboxRoot)](PsychtoolboxRoot))  
2. sudo cp [PsychHardware](PsychHardware)/50-evdev-powermate.conf /usr/share/X11/xorg.conf.d/  
3. Logout and login again.  
  
Interesting technical background info:  
======================================  
  
Technical background info, copied from the Linux powermate.c device driver,  
written by William R Sowerbutts, the author of the Linux driver:  
  
"Testing with the knob I have has shown that it measures approximately 94 "clicks"  
for one full rotation. Testing with my High Speed Rotation Actuator (ok, it was  
a variable speed cordless electric drill) has shown that the device can measure  
speeds of up to 7 clicks either clockwise or anticlockwise between pollings from  
the host. If it counts more than 7 clicks before it is polled, it will wrap back  
to zero and start counting again. This was at quite high speed, however, almost  
certainly faster than the human hand could turn it. Griffin say that it loses a  
pulse or two on a direction change; the granularity is so fine that I never  
noticed this in practice."  
  
- The rotary resolution is therefore about 3.8298 degrees per "click" or unit.  
  
- The [PowerMate](PowerMate) can lose a click or two on a direction change, therefore can  
  accumulate rotational error on each turn direction change.  
  
- The [PowerMate](PowerMate) wants to be sampled at 10 msec intervals according to its  
  USB HID descriptor. Low-speed USB interrupt endpoint sampling interval  
  duration must be a power of two, so it will actually get sampled at  
  8 msec intervals, for a maximum update rate of 125 Hz.  
  
  
### Commands:  
  
deviceIds = [PsychPowerMate](PsychPowerMate)('List');  
-- Return a list of all 'deviceIds' of all connected [PowerMates](PowerMates). Items from  
this list can be passed as 'deviceId' parameter to the 'Open' function to  
select a specific [PowerMate](PowerMate). Please note that the [PowerMates](PowerMates) themselves do  
not provide any identifying information, like a serial number, so the computer  
can't distinguish them. The 'deviceIds' you get back from this function are  
therefore only guaranteed to be valid during a given session. Unplugging and  
replugging [PowerMates](PowerMates) may change the ids assigned to them, based on operating  
system specific criteria. On MS-Windows the deviceIds don't change even  
if you plug the [PowerMate](PowerMate) into a different USB port, so this function may  
be useless for device selection and you may have to figure out something  
specific to your computer hardware setup. On Linux you can assign fixed  
ids to fixed USB ports. See the Technical note at the end of this help  
text for how to do it. On OSX the deviceIds seem to be associated with  
fixed USB ports, with numbers at least persistent during a session.  
  
  
handle = [PsychPowerMate](PsychPowerMate)('Open' [, deviceId][, historySize=10000])  
-- Open a connected Griffin [PowerMate](PowerMate), return a handle to it.  
  
The optional 'deviceId' selects which of multiple connected [PowerMates](PowerMates) should  
be used. [PsychPowerMate](PsychPowerMate)('List') returns a list of all possible 'deviceId's.  
If 'deviceId' is omitted then the first found [PowerMate](PowerMate) is opened.  
  
### Linux only:  
  
The optional 'historySize' parameter allows to select how many events the  
knob press and motion history functions 'StartHistory' and 'GetHistory' can  
collect in the background. It defaults to 10000 events if omitted, ie. up to  
5000 knob presses + releases, or alternatively about 104 full knob rotations  
can be recorded in the background before you either need to get the recorded  
data via the 'GetHistory' subfunction to empty the internal storage, or the  
internal storage will be full and stop collecting new data.  
  
If you need to record more than 10000 such events in total, just specify a  
larger 'historySize': Each button press or release creates 2 events (1 press +  
1 release). Each turn of the knob by 1 unit (about 3.8 degrees) creates one  
event.  
  
  
[PsychPowerMate](PsychPowerMate)('[Close](Close)', handle);  
-- [Close](Close) previously opened [PowerMate](PowerMate) specified by 'handle'.  
  
  
[PsychPowerMate](PsychPowerMate)('SetBrightness', handle, level);  
-- Change brightness of the LED of the [PowerMate](PowerMate) specified by 'handle'  
to 'level'. Level can be between 0 and 255. 'handle' is currently ignored  
on Linux.  
  
  
[button, dialPos] = [PsychPowerMate](PsychPowerMate)('Get', handle);  
-- Poll the [PowerMate](PowerMate) specified by 'handle', return the status  
of its 'button' 1 = Pressed, 0 = Released. Also return the current  
'dialPos' dial position of its dial - its turning knob. Please note  
that the knob does not have a defined zero position. You can turn it  
endlessly in one direction. Turning in one direction will simply  
increment the 'dialPos' position, turning into the other direction  
will decrement it. See above comments on the accuracy and resolution  
of position reporting.  
  
  
secs = [PsychPowerMate](PsychPowerMate)('WaitButton', handle [, waitforbuttonpress=1][, untilTime=inf]);  
-- Wait for button press or release on the [PowerMate](PowerMate) specified by 'handle',  
return the [GetSecs](GetSecs)() time of press in 'secs'.  
  
If the optional 'waitforbuttonpress' flag is set to 0 then the function  
waits for a button release, otherwise it waits for a button press.  
  
If the optional 'untilTime' parameter is given, the function times out  
at time 'untilTime', otherwise it waits forever if nobody presses or releases  
the button.  
  
secs = [PsychPowerMate](PsychPowerMate)('WaitRotate', handle [, untilTime=inf]);  
-- Wait for knob rotation on the [PowerMate](PowerMate) specified by 'handle',  
return the [GetSecs](GetSecs)() time of rotation in 'secs'.  
  
If the optional 'untilTime' parameter is given, the function times out  
at time 'untilTime', otherwise it waits forever if nobody moves the knob.  
  
  
# The following functions are only supported on Linux  
  
[PsychPowerMate](PsychPowerMate)('StartHistory', handle [, clearHistory=0]);  
-- Start recording of a knob press and knob motion history in the background.  
If the optional 'clearHistory' flag is set to 1 then the current history is  
cleared/discarded before start of recording of a new one.  
  
  
[PsychPowerMate](PsychPowerMate)('StopHistory', handle);  
-- Stop recording of knob press and knob motion history.  
You can resume recording via 'StartHistory' or start recording a new one,  
discarding old data via 'StartHistory' with the flag clearHistory=1 set.  
  
  
history = [PsychPowerMate](PsychPowerMate)('GetHistory', handle);  
-- Retrieve currently recorded knob press and knob motion history.  
history is a 4-by-n matrix with n columns for n recorded events.  
Row 1 contains knob position. Row 2 contains knob button state: 0 = Released,  
1 = Pressed. Row 3 contains a [GetSecs](GetSecs) timestamp of the element. Row 4 tells  
if the given column records a knob press/release (0) or a knob movement (1).  
  
  
numItems = [PsychPowerMate](PsychPowerMate)('GetHistorySize', handle);  
-- Return number of items currently recorded in history.  
  
  
  
Technical note: How to map physical USB bus location to a /dev/input/powermateXX  
symlink via a udev rule, then how to map that device file to a xinput device  
name for enumeration/selection by our driver. Follow the approach outlined  
at the bottom of this thread for dual-touchscreen setups with identical touchscreen:  
  
http://arstechnica.com/civis/viewtopic.php?f=16&t=1146846  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/PsychPowerMate.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/PsychPowerMate.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/PsychPowerMate.m</code>
</div>

