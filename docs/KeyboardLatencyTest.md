# [KeyboardLatencyTest](KeyboardLatencyTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[KeyboardLatencyTest](KeyboardLatencyTest)([triggerlevel=0.01][,modality=0][,submode][,portString])  
  
Uses sound capture with high timing precision via  
[PsychPortAudio](PsychPortAudio)() for measuring latency, timing accuracy and variability  
of various response input devices, e.g., keyboard, keypad, mouse, other  
HID devices like Joysticks etc., various response button boxes, and some  
exotic response devices.  
  
Whenever the script tells you, hit a key on the tested input device  
hard and loud enough so the noise of hitting the button or key can be  
recorded by the attached microphone. This noise will be timestamped by  
the code as the "true" button press time. Timestamps acquired  
by standard input device queries are compared against that reference  
and the difference is computed as device latency.  
  
Sound is captured from the default recording device, waiting  
until the amplitude exceeds some 'triggerlevel'.  
  
The 'modality' flag chooses between keyboard (==0 - the default), and  
mouse (==1). 'portString' allows to select which keyboard to test on some  
systems (OS/X and Linux). It also allows to select which mouse to test on  
Linux, but not on other systems.  
  
A 'modality' of 2 queries the keyboard, a keypad, a mouse, or other HID  
devices by use of the [KbTriggerWait](KbTriggerWait)() function. 'submode' specifies the  
[KbName](KbName)() keyCode of the key to test on a keyboard. By default the SPACE  
key is used. For other devices you \*must\* specify a key or button number in  
'submode'. Specifiying numbers of non-existent keys or buttons will cause  
an infinite hang of Matlab or Octave, as there is no way to interrupt the  
function or press a non-existent key or button. The optional 'portString'  
specifies the deviceIndex of the device to test. If omitted, the primary  
keyboard is tested.  
  
A 'modality' of 3 will test the [PsychRTBox](PsychRTBox)() driver for the USTCRTBOX reaction  
time button box, if such a box is attached. A setting 4 will also test  
that box, but without opening a connection to it, ie., it is assumed that  
the box is already open from a previous call of this function with  
modality setting '3'. This allows to repeat the test many times without  
recalibrating the box. The optional 'submode' flag selects different ways  
of testing the box: A setting of zero will perform a 'ClockRatio'  
calibration to provide exact live timestamps and to test drift  
correction. A setting of 1 will skip this, so live timestamps will  
exhibit clock-drift and only the post-hoc timestamps will be somewhat  
exact. A setting of 2 will skip collection of post-hoc timestamps.  
  
A 'modality' of 5 will exercise the RB-x30 response pads from Cedrus.  
  
A 'modality' of 6 will exercise the PST serial response button box.  
Setting 'submode' to 1 will optimize for use with FTDI serial-USB  
converters.  
  
A 'modality' of 7 will exercise the CMU serial response button box.  
Setting 'submode' to 1 will optimize for use with FTDI serial-USB  
converters.  
  
A 'modality' of 8 will exercise the Bitwhacker emulated response button box.  
Setting 'submode' to 1 will optimize for use with FTDI serial-USB  
converters.  
  
A 'modality' of 9 will exercise the fORP serial response button box in  
program mode 0.  
Setting 'submode' to 1 will optimize for use with FTDI serial-USB  
converters.  
  
A 'modality' of 10 will measure timing of touch input devices like  
touchscreens or touchpads. 'portString' allows to select a specific  
touch input device as enumerated via [GetTouchDeviceIndices](GetTouchDeviceIndices)(). By default  
the first detected touchscreen or touchpad is used. Note that on some  
operating systems you must hit the touchscreen or touchpad inside the  
displayed onscreen window, as those systems will not register touches  
outside the onscreen window.  
  
  
The optional 'portString' argument can be set to define the serial port  
to connect to for response devices that are connected via serial port.  
By default, the proper serial port is auto-detected, but you can override  
a wrong detection this way.  
  
  
Obviously this method of measuring carries quite a bit of uncertainty  
in exact timing, but with a high quality microphone, proper tuning and  
good sound hardware, it shouldn't be off too much. At least you get a  
rough feeling for the lags inherent to keyboards and mice.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/KeyboardLatencyTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/KeyboardLatencyTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/KeyboardLatencyTest.m</code>
</div>

