# [PsychHIDTest](PsychHIDTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[PsychHIDTest](PsychHIDTest)([doStupidTests=0])  
  
NOTE: This test is mostly useless on current operating systems, a relic of the  
past days of OSX on [PowerPC](PowerPC). Running it will almost always confuse you without  
providing any meaningful information. Don't bother reporting any bugs or problems  
with this script to the Psychtoolbox forum.  
  
  
[PsychHIDTest](PsychHIDTest) exercises the [PsychHID](PsychHID) mex file. We list all the HID  
devices on all systems. Please note that the type of devices that  
can be listed depends on operating system type. Security mechanisms  
in many OS'es prevent listing of certain HID devices, or of details  
of certain devices, e.g., keyboards and mice. This is especially true  
on MS-Windows, and to a lesser degree on Linux.  
  
  
On OSX, if you set the optional flag 'doStupidTests' to 1, we try to  
read from the keyboard and mouse. We try to flicker the keyboard  
[LEDs](LEDs). Both due to the brokeness of Apples recent operating systems and  
due to limitations of this test, this may not work on many recent  
keyboards, so a failure of this test may not indicate real trouble.  
That is why the test is disabled by default, to not cause extra confusion.  
  
On non OSX we only list the HID devices, as mouse and keyboard are  
not really accessible for [PsychHID](PsychHID) on MS-Windows, and dangerous to access on Linux.  
  
NOT RESPONDING? If [PsychHID](PsychHID) is not responding, e.g. after unplugging and  
re-plugging the USB connector, try quitting and restarting MATLAB. We  
find that this reliably restores normal communication.   
  
web http://psychtoolbox.org/usb.html -browser;  
See also [DaqTest](DaqTest), [PsychHID](PsychHID), [PsychHardware](PsychHardware).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/PsychHIDTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/PsychHIDTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/PsychHIDTest.m</code>
</div>

