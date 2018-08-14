# [CMUBox](CMUBox)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)

[CMUBox](CMUBox) - Access CMU response button box or PST serial response button box as well as fORP and Bitwhacker devices.  
  
This allows to query button response boxes of type CMU (Carnegie Mellon  
University box) and PST (E-Prime response box). It also allows to use a  
UBW32/Bitwhacker device to be used as a response box if the device is  
loaded with the [StickOS](StickOS) firmware from http://cpustick.com. It also allows  
to use the Curdes fORP devices if connected via serial port. And it offers  
a simple way to access the [RTBox](RTBox) in E-Prime mode.  
  
Note to MS-Windows users: You may need to setup the COM port of your machine  
properly and then reboot once to get correct timing. In the device manager  
for the COM ports, there is some "Advanced settings" tab or button somewhere.  
If you find a section called "FIFO size" or similar, set the FIFO size to  
a setting of 1 Byte, or disable FIFO's completely. Otherwise you may get  
inaccurate timestamps or many timestamp warnings from [CMUBox](CMUBox)('GetEvent').  
As far as USB-serial converters go, only converters from FTDI have been tested  
to be well behaved.  
  
  
# Commands and their syntax  
  
handle = [CMUBox](CMUBox)('Open', boxtype [, portName] [, options] [, debounceSecs=0.030] [, isInverted]);  
- Open response box connected to serial port 'portName', or the first  
serial port found, if 'portName' is omitted. Initialize it, return a  
'handle' to it. You'll have to pass 'handle' to all following functions  
to access the box.  
  
If your system has multiple devices connected to multiple serial ports  
then you should explicitely specify the 'portName', otherwise the driver  
may connect to the wrong port and choke!  
  
The optional string parameter 'options' allows to tweak the behaviour of  
the driver for certain configurations. It supports the following options:  
  
'ftdi' - Tells the driver that it is connecting to a Serial-over-USB port  
and that the converter/driver is from FTDI Inc., or a compatible device.  
Allows for certain optimizations in timing accuracy.  
  
'norelease' - Tells the driver it shouldn't report button release / TTL  
transition to low events, but only button presses and TTL onsets.  
  
  
The optional parameter 'debounceSecs' sets the debounce interval for  
button debouncing if the Bitwhacker is used as response box. After a  
button press, the device will wait for all the buttons to be released for  
at least 'debounceSecs' seconds. Only then will it accept new button  
presses. The default setting is 30 msecs if this option is omitted.  
  
  
The optional parameter vector 'isInverted' defines whether a TTL input  
signal level of logic low (0) corresponds to a button press or a button  
release. By default, a level of logic low is detected as button press.The  
vector has nine elements, one for each corresponding input line. If an  
element is 1, then a logic level of low is registered as a button press.  
A value of 0 means that a logic level of high is registered as a button  
press. E.g., isInverted = [ 0 0 0 0 1 1 1 1 1 ] would register a logic  
level of low as a button press on the first four inputs, whereas a level  
of high is required to detect a button press on the last five inputs.   
  
  
The mandatory parameter 'boxtype' is a name string defining the  
type/model of box to connnect to. Supported settings are:  
  
'bitwhacker' - Connect to UBW32/Bitwhacker with [StickOS](StickOS) Firmware,  
reconfigure it to impersonate a response box.  
  
'cmu' - Connect to CMU serial port response button box, assuming 19.2  
[KBaud](KBaud) datarate, 8 databits, 1 stop bit, odd parity.  
  
'pst' - Connect to PST serial port response button box in E-Prime  
configuration with 800 streaming samples per second at 19200 Baud, 8  
databits, 1 stopbit, no parity. Please note this is our expectation: If  
the box is configured for something else than 19200 Baud, we will fail or  
hang. If 1600 samples/sec are configured instead of 800 sampes/sec, we  
won't care, but timing might be less accurate due to the too high USB load,  
unless we're running on a real serial port which shouldn't have a  
problem with 1600 samples/sec. Serial-over-USB however will likely choke!  
Verify that the DIP switches or jumpers inside the box are properly set  
up.  
  
'forpserial-1' - Connect to a fORP interface unit type FIU-005 on the  
serial port, configured with a program switch setting of 1. This is  
exactly the same as a PST box running with 800 Samples/Sec streaming  
rate.  
  
'forpserial-0', 'forpserial-2', 'forpserial-4', 'forpserial-6'  
Connect to a fORP interface unit type FIU-005 on the serial port,  
configured with a program switch setting of 0, 2, 4 or 6. In this mode,  
similar to the Bitwhacker, the device will only send a single byte if the  
status of the buttons or triggers changes. This is more efficient than  
mode 'forpserial-1', so one of these settings is recommended.  
  
Modes 0, 4 and 6 will only report button presses or trigger reception,  
but not button releases, whereas mode 2 will report any status change,  
ie., it will also report and timestamp button releases. The mapping of  
the returned status value to corresponding button / trigger states is  
dependent on the selected mode. Modes 0, 4 and 6 report ASCII codes that  
identify the pressed button, whereas mode 2 returns a status byte where  
each bit encodes the current (updated) status of a single button, similar  
to the PST and CMU response boxes. For the specifics, see the fORP manual  
at http://www.curdes.com/[ForpUserGuide](ForpUserGuide).html  
  
'rtbox' - Connect to a [RTBox](RTBox) in "simple mode", the mode it uses after  
powerup. The Box will send a byte of data for each event, each bit encoding  
the new status of one button or other input.  
  
'lumina' - Connect to a Cedrus Lumina response box.  
  
  
[CMUBox](CMUBox)('[Close](Close)', handle);  
- [Close](Close) connection to response box 'handle'. The 'handle' is invalid  
thereafter.  
  
  
evt = [CMUBox](CMUBox)('GetEvent', handle [, waitForEvent=0]);  
- Retrieve next queued event received from the box in the struct 'evt'.  
If no new events are available and the optional 'waitForEvent' is set to  
1, then the function will wait until at least one valid event becomes  
available and return that event. Otherwise it will return an empty struct,  
ie., evt = [] to signal that no new events are available.  
  
### The following subfields are available in 'evt' if 'evt' is non-empty:  
  
evt.state = 1 Byte value which encodes the new status of the response  
buttons and input lines of the box. A 1-bit means button pressed/signal  
active. A 0-bit means button released/signal inactive. See the  
documentation of your box for meaning of the single bits. If you use the  
Bitwhacker then evt.state does directly encode the button number of a  
pressed button: 0 == All buttons released and all TTL inputs low.  
Values 1-7 correspond to a low-\>high transition of TTL input pins A1 - A7.  
Values 8 and 9 correspond to a button press of onboard buttons "USER" or  
"PRG". Bitwhacker can only report one active button or TTL line at a time.  
  
The fORP device will encode evt.state differently depending on selected  
mode, either like a Bitwhacker device or like a CMU/PST response box.  
  
evt.time  = Psychtoolbox [GetSecs](GetSecs)() timestamp of the time when the event  
was received from the box. The accuracy depends on the properties of your  
serial port device and system load. For a native serial port and a  
normally loaded system, you can expect about 1-2 msec delay. For a  
Serial-over-USB port, it depends on the converter type and driver  
settings but can be 2-3 msecs at best.  
  
evt.trouble = If zero, then evt is probably valid and good. If non-zero,  
then the timestamp is likely screwed and useless, as are probably all  
following timestamps, at least for CMU/PST boxes and fORP's in mode 1!  
For the Bitwhacker or fORP's in modes 0,2,4 or 6, only the current 'evt'  
will be invalid, but later events will recover and thereby be unaffected.  
  
  
status = [CMUBox](CMUBox)('Status', handle);  
- Retrieve internal status of response box 'handle' as a struct.  
  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/CMUBox.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/CMUBox.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/CMUBox.m</code>
</div>

