# [CedrusResponseBox](CedrusResponseBox)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)

[CedrusResponseBox](CedrusResponseBox) - Interface to Cedrus Response Boxes.  
  
This function provides an interface to response button boxes from Cedrus,  
specifically model RB 530,...,830 and compatible models supporting the  
XID protocol (see http://www.cedrus.com).  
  
These response boxes connect via a serial line link interface, or a USB  
interface which emulates a serial link interface. They support the XID  
protocol for communication. See http://www.cedrus.com/xid for details.  
  
This function allows to establish a connection to the box, control a few  
of its parameters and most importantly query its button state and  
associated button press timestamps.  
  
It supports multiple subcommands, which accept and return different  
arguments, as listed below.  
  
# Limitations  
  
Functionality is currently limited mostly to button queries (and RJ-45  
connector state queries), including timestamps, as well as control of  
built-in timers of the box. We also support basic configuration of TTL  
ports, but not yet all settings of the box like e.g., button debounce  
time. Adding such calls is straightforward and simple.  
  
We found communication with the Cedrus boxes to be unreliable quite  
often. It is an open question if this is a flaw in the design of the  
Cedrus devices and their firmware or protocols, or if the programming  
documentation for them is incomplete and therefore our implementation of  
the driver. However, the problems were reproduced under different  
operating systems, serial port drivers, toolboxes by different  
implementations written by different people, so it doesn't seem to be a  
simple glitch in one implementation. In general, the boxes work, but  
don't be surprised if you need to restart your script multiple times  
before you can establish communication, or if the more advanced  
fucntions, e.g., for configuration of the TTL RJ-45 connector, work  
unreliably for no apparent reason. Cedrus has been contacted, but so far  
no resolution or response from them.  
  
In short: If you are looking for a reliable response box that is painfree  
to use, don't buy Cedrus devices!  
  
  
# Subfunctions and their meaning  
  
Functions for device init and shutdown: Call once at beginning/end of  
your script. These are slow!  
  
handle = [CedrusResponseBox](CedrusResponseBox)('Open', port [, lowbaudrate]);  
- Open a compatible response box which is connected to the given named  
serial 'port'. 'port'names differ accross operating systems. A typical  
port name for Windows would be 'COM2', whereas a typical port name on OS/X  
or Linux would be the name of a serial port device file, e.g.,  
'/dev/cu.usbserial-FTDI125ZX9' on OS/X, or '/dev/ttyS0' on Linux.  
  
All names on OS/X are like '/dev/cu.XXXXX', where the XXXXX part depends  
on your serial port device, typically '/dev/cu.usbserial-XXXXX' for  
serial over USB devices with product name XXXXX.  
  
On Linux, all names are of pattern '/dev/ttySxx' for standard serial  
ports, e.g., '/dev/ttyS0' for the first serial port in the system, and of  
type '/dev/ttyUSBxx' for serial over USB devices, e.g., '/dev/ttyUSB0'  
for the first serial line emulated over the USB protocol.  
  
  
After the connection is established and some testing and initialization is,  
done, the function returns a device 'handle', a unique identifier to use  
for all other subfunctions.  
  
By default the commlink is opened at a baud transmission rate of 115200  
Baud (All DIP switches on the box need to be in 'down' position!). If you  
specify the optional flag 'lowbaudrate' as 1, then the speed will be  
lowered to 56 kBaud at device open time -- in case your system works  
unreliably at the higher rate.  
  
By default, the script uses Psychtoolbox's own [IOPort](IOPort)() serial link  
driver for communication (ptb\_cedrus\_drivertype = 2). If you want to use  
a different driver for testing, change the 'ptb\_cedrus\_drivertype'  
parameter inside the code with the id of a supported driver (Matlab  
serial()). This option may go away in the future and is for debugging  
only!  
  
  
[CedrusResponseBox](CedrusResponseBox)('[Close](Close)', handle);  
- [Close](Close) connection to response box. The 'handle' becomes invalid after  
that command.  
  
  
[CedrusResponseBox](CedrusResponseBox)('CloseAll');  
- [Close](Close) all connections to all response boxes. This is a convenience  
function for quick shutdown.  
  
  
dev = [CedrusResponseBox](CedrusResponseBox)('GetDeviceInfo', handle);  
- Return queried information about the device in a struct 'dev'. 'dev'  
contains (amongst other) the following fields:  
  
General information:  
 dev.Name = Device name string.  
 dev.[VersionMajor](VersionMajor) and dev.[VersionMinor](VersionMinor) = Major and Minor firmware revision.  
 dev.productId = Type of device, e.g., 'Lumina', 'VoiceKey' or 'RB response pad'.  
 dev.modelId   = Submodel of the device if the device is a RB response pad,  
                 e.g., 'RB-530', 'RB-730', 'RB-830' or 'RB-834'.  
  
 dev.port      = Portname of serial port, as passed to the open function.  
  
Diagnostic information for timing: Values of -1 or 0 usually mean "info  
not available".  
  
 dev.roundtriptime   = Median of estimated roundtrip latency for  
                       communication with the box - in seconds.  
  
 dev.roundtripstddev = Standard deviation from mean of roundtrip latency  
 measurements in seconds. Large numbers mean that your operating system  
 has bad scheduling and that reported event timestamps may be uncertain by  
 that amount.  
  
 dev.rttresetdelay   = Duration (in seconds) of a reaction time timer reset sequence  
 Values of more than 3 msecs indicate some problems with the box itself or  
 the communication link -- Measured event times or reaction times may not  
 be trustworthy!  
  
  
### Functions for use within script. These are as fast as possible:  
  
[CedrusResponseBox](CedrusResponseBox)('ClearQueues', handle);  
- Clear all queues, discard all pending data.  
  
[status = ] [CedrusResponseBox](CedrusResponseBox)('FlushEvents', handle);  
- Empty/clear/flush the queue of pending events. Use this to get rid of  
any stale button press or release events before start of response  
collection in a trial. E.g., Assume you wait for a subjects keypress and  
finally receive that keypress via 'GetButtons' or 'WaitButtons'. You  
collected your response, the trial is done, but when the subject releases  
the button again, that will generate another event - a release event, in  
which you're not interested. Maybe the subject will accidentally hit the  
button as well. --\> Good to clean the queue before a new trial.  
  
This function has a second use as well. It has an optional output  
argument, 'status', which will return the current status of all buttons  
(i.e. whether they are currently being pressed or not).  
Status is a 3 row by 8 column matrix: Row 1 describes the status of the  
up to eight pushbuttons of the box. Row 2 describes the status of the TTL  
lines of the RJ-45 accessory connector. Row 3 describes the status of the  
[VoiceKey](VoiceKey) if any. Columns 1 to 8 of each row correspond to buttons 1-8,  
TTL lines 1-8 or inputs 1-8 of the [VoiceKey](VoiceKey).  
  
### The mapping for the CB-530 for row 1 of 'status' status(1,:) is as follows:  
  
[top ??? left middle right bottom] -- the 2nd entry has no associated  
button, but it may be the scanner trigger input. The mapping on other boxes  
may be different.  
  
This is useful if you just want to know whether the subject is currently  
pressing any buttons before you proceed, but are not fussed about timing.  
  
E.g. I often find myself doing the following:  
  buttons = 1;  
  while any(buttons(1,:))  
    buttons = [CedrusResponseBox](CedrusResponseBox)('FlushEvents', mybox);  
  end  
  
...to wait for the subject to release any buttons which might currently be down.  
  
evt = [CedrusResponseBox](CedrusResponseBox)('GetButtons', handle);  
- Return next queued button-press or button-release event from the box.  
Each time a button on the box is pressed or released, and each time the  
state of the accessory connector changes, an "event" data packet is sent  
from the box to the computer. The packet is timestamped with the time of  
the triggering event, as measured by the boxes reaction time timer.  
  
This function checks if such an event is available and returns its  
description in a 'evt' struct, if so. If no event is pending, it returns an  
empty 'evt', ie. isempty(evt) is true.  
  
### 'evt' for a real fetched event is a struct with the following fields:  
  
evt.raw     = "raw" byte that describes the event. Only for debugging.  
  
evt.port    = Number of the device port on which the event occured. Push  
              buttons and scanner triggers are on port 0, the RJ-45 TTL  
              connector is on port 1, port 2 is the voice-key (if any).  
  
evt.action  = Action that triggered the event:  
              1 = Button press, 0 = Button release for pushbuttons.  
              1 = TTL line high, 0 = TTL line low for RJ-45 I/O lines.  
              1 = Voice onse, 0 = Voice offset/silence for Voicekey.  
  
evt.button  = Number of the button that was pressed or released (1 to 8)  
              or the TTL line that was going high/low. Numbers vary by  
              response box.  
  
evt.buttonID= Descriptive name string for pressed button, e.g., 'top' or  
              'left'. Please note that this mapping is only meaningful  
              for the RB-530 response box.  
  
evt.rawtime = Time of the event in secs since last reset of the reaction  
              time timer, measured in msecs resolution. This value is  
              always valid, but not directly comparable to any other  
              timestamps or time measurements within Psychtoolbox.  
  
  
evt = [CedrusResponseBox](CedrusResponseBox)('WaitButtons', handle);  
- Queries and returns the same info as 'GetButtons', but waits for  
events. If there isn't any event available, will wait until one becomes  
available.  
  
evt = [CedrusResponseBox](CedrusResponseBox)('WaitButtonPress', handle);  
- Like [WaitButtons](WaitButtons), but will wait until the subject /presses/ a key -- the  
signal that a key has been released is not acceptable -- Button release  
events are simply discarded.  
  
  
evt = [CedrusResponseBox](CedrusResponseBox)('GetBaseTimer', handle [, nSamples=1]);  
- Query current time of base timer of the box. Returned values are in  
seconds, resolution is milliseconds. evt.basetimer is the timers time,  
maybe corrected for serial link receive latency. evt.ptbreceivetime is a  
timestamp taken via PTB's [GetSecs](GetSecs)() at time of receive of the data.  
evt.ptbtime is the basetimers time mapped into PTB [GetSecs](GetSecs) time if such a  
mapping is possible, otherwise this field doesn't exist:  
evt.ptbreceivetime and evt.ptbtime shouldn't be significantly different  
if everything is good. Large differences indicate some timing problems  
with the connection to the box, or a timer problem - either with your  
computers timer or the hardware timer of the tox, or significant  
clock-drift between the computers timer and the boxes timer. In any case,  
reaction timer measurements and such will be problematic.  
  
Note that this automatically discards all pending events in the queue before  
performing the timer query!  
  
The optional argument 'nSamples' allows to specify if multiple samples of  
PTB timer vs. the response boxes timer should be measured. If 'nSamples'  
is set to a value greater than one, a cell array with nSamples elements  
will be returned, each corresponding to one measurement. This allows,  
e.g., to check if [PTBs](PTBs) timer and the boxes timer drift against each  
other.  
  
  
resetTime = [CedrusResponseBox](CedrusResponseBox)('ResetRTTimer', handle);  
- Reset reaction time timer of box to zero. This should not be neccessary  
if you use the evt.ptbtime timestamps for time measurements or reaction  
time measurements. If you however use uncalibrated mode and the  
evt.rawtime values directly, this function may be useful to establish a  
zero baseline for reaction time measurements. However, as the communication  
delay for sending the reset command can't be reliably measured, using  
such a software triggered timer reset may not be the most reliable way of  
resetting the timer. The function returns 'resetTime' PTB's best guess of  
when the reset was carried out -- essentially a [GetSecs](GetSecs)() timestamp of  
when the reset command was sent.  
  
Note that this automatically discards all pending  
events in the queue before performing the query!  
  
  
slope = [CedrusResponseBox](CedrusResponseBox)('GetBoxTimerSlope', handle);  
- Compute slope (drift) between computer clock and device clock. 'slope'  
tells how many seconds of time "elapse" on the computer in [GetSecs](GetSecs) time  
for each "elapsed" second of box time. At device open time, the driver  
takes a timestamp from the device basetimer. This function also takes a  
timestamp and then computes the ratio of differences. The longer you'll  
wait after [CedrusResponseBox](CedrusResponseBox)('Open') before calling this function, the  
more accurate the clock-drift estimate will be.  
  
  
roundtrip = [CedrusResponseBox](CedrusResponseBox)('RoundTripTest', handle);  
- Initiate 100 trials of the roundtrip test of the box. Data is echoed  
forth and back 100 times between PTB and the box, and the latency is  
measured (in seconds, with msecs resolution). The vector of all samples  
is returned in 'roundtrip' for evaluation and debugging. The measured  
latency is also used for delay correction for the 'GetBaseTimer'  
subfunction. However, a roundtrip test is performed automatically when  
opening the response box connection, so this is rarely needed.  
  
Note that this automatically discards all pending  
events in the queue before performing the query!  
  
  
[currentMode] = [CedrusResponseBox](CedrusResponseBox)('SetConnectorMode', handle [, mode]);  
- Set or get mode of operation of external accessory connector: 'mode' can be  
any of the following text strings:  
  
'GeneralPurpose': Input/Output assignment of pins can be freely  
programmed via the 'DefineInputLinesAndLevels' subcommand (see below),  
and the output lines only change if the 'SetOutputLineLevels' command  
(see below) is used. The connector doesn't change state by itself.  
  
'ReflectiveContinuous': Line levels reflect button state: Line is active  
if button is pressed and goes inactive when the button is released again.  
  
'ReflectiveSinglePulse': A single pulse is sent to an output line if a  
button is pressed on the box. Nothing is sent on release.  
  
'ReflectiveDoublePulse': A single pulse is sent to an output line if a  
button is pressed on the box. Another pulse is sent on button release.  
  
If 'mode' is left out, the function queries and returns the current mode  
as return argument 'currentMode'. If mode is given, nothing is returned.  
  
  
[CedrusResponseBox](CedrusResponseBox)('SetOutputLineLevels', handle, outlevels);  
- Set accessory connector output lines to state specified in 'outlevels'.  
outlevels is an 8 element vector of zeros and ones. Each element  
corresponds to an output pin, and its values sets the output level of  
that pin. Example: outlevel = [1,1,1,1,0,0,0,0] would set the 4 lines  
with the lowest numbers (lines 0,1,2,3) to '1' aka active and the 4 lines  
with the highest numbers (lines 4,5,6,7) to '0' aka inactive.  
This corresponds to [XiD](XiD) command 'ah'.  
  
The command is only effective if connector is set to 'GeneralPurpose'.  
  
  
[CedrusResponseBox](CedrusResponseBox)('DefineInputLinesAndLevels', handle, inputlines, logiclevel, debouncetime);  
- Define which lines on the connector are inputs: 'inputlines' is a  
vector with the line numbers of the input lines. All other lines are  
designated as output lines, e.g., inputlines = [0, 2, 4] would set lines  
0, 2 and 4 as inputs, remaining lines 1,3,5,6,7 as outputs. 'logiclevel'  
tells if the default TTL level of the input lines is low (logiclevel=1)  
or high (logiclevel=0). Example: logiclevel = 1 means that the lines are  
pulled low by default, so they will detect an active high state -- if  
their level is raised to TTL high state. The argument 'debouncetime' must  
be the debounce time for the input lines in milliseconds. After an event  
on a input line, the box will ignore all further events on than input  
line for 'debouncetime' milliseconds.  
  
This corresponds to [XiD](XiD) commands 'a4', 'a50' and 'a51', as well as 'a6'.  
  
The command is only effective if connector is set to 'GeneralPurpose'.  
  
  
inputLines = [CedrusResponseBox](CedrusResponseBox)('ReadInputLines', handle);  
- Read current state of the connectors input lines: Returns an 8 element  
vector where each element corresponds to one input line and a 1 means  
active, 0 means inactive. This corresponds to [XiD](XiD) command 'ar'.  
  
Note that this automatically discards all pending  
events in the queue before performing the query!  
  
The command is only effective if connector is set to 'GeneralPurpose'.  
  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/CedrusResponseBox.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/CedrusResponseBox.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/CedrusResponseBox.m</code>
</div>

