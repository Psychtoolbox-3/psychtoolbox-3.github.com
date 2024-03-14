# [Gamepad](Gamepad)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[PsychGamepad](PsychGamepad)

result = Gamepad(command [,arg1] [,arg2])  
  
Gamepad reads the state of any USB game controller. Gamepad was  
previously named "[JoyStick](JoyStick)", the name has been changed to agree with the  
USB Human Interface Device (HID) terminology.  
  
Gamepad provides built-in help.  For usage, enter "Gamepad" alone on the  
command line.  
  
### Performance tips:  
  
As initialization of Gamepad takes significant time, you should call it  
once at the beginning of your script before entering the trial loop.  
After plugging/unplugging or replugging of any USB devices you \*must\*  
call Gamepad('Unplug') or clear all, so Gamepad can recognize the changed  
hardware configuration at next invocation. Actually, a clear all is  
recommended, as Gamepad('Unplug') doesn't work reliably on non-OSX systems.  
  
The subfunctions for state queries of axis, button and hat state are  
optimized for low execution time -- suitable for time critical parts of  
your trial loop. All other functions, e.g., for query of the number of  
buttons etc. are not optimized, so they shouldn't be called in time  
critical parts of your loop.  
  
If you need ultra-fast queries, check the help for 'GetButtonRawMapping',  
'GetAxisRawMapping' and 'GetHatRawMapping' for a slightly inconvenient,  
but superfast way to query device state.  
  
  
LINUX: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
On Linux/X11, Gamepad() uses the [Screen](Screen)() mex file and its mouse query functions.  
  
On Linux, gamepads and joysticks are treated as a special type of mouse/pointing  
device with multiple extra axes and buttons. You should install the optional  
joystick driver, although the evdev driver may also work with suitable configuration.  
  
### On Ubuntu 20.04 LTS or later, the following command should work:  
  
"sudo apt install xserver-xorg-input-joystick"  
  
You should also install a custom joystick configuration file to customize the  
mapping and behaviour of buttons and axis, and if the Joystick also operates  
as a mouse or not.  
  
An example configuration file with installation instructions is  available in  
the Psychtoolbox/[PsychContributed](PsychContributed) folder under the name "52-[MyLinuxJoystick](MyLinuxJoystick).conf".  
  
OSX: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[GamePad](GamePad) uses the [PsychHID](PsychHID) function, which provides a universal interface to  
USB HID devices, including keyboards.  
  
WIN: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
Gamepad is not yet supported on Windows. [WinJoystickMex](WinJoystickMex)() in the  
Psychtoolbox/[PsychContributed](PsychContributed) subfolder may serve as a temporary  
replacement of more limited functionality.  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
See also: [PsychGamepad](PsychGamepad), [PsychHID](PsychHID)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/PsychGamepad/Gamepad.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/PsychGamepad/Gamepad.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/PsychGamepad/Gamepad.m</code>
</div>

