# [KbWait](KbWait)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

[secs, keyCode, deltaSecs] = [KbWait](KbWait)([deviceNumber][, forWhat=0][, untilTime=inf])  
  
Waits until any key is down and optionally returns the time in seconds  
and the keyCode vector of keyboard states, just as [KbCheck](KbCheck) would do. Also  
allows to wait for release of all keys or for single keystrokes, see  
below.  
  
If the optional parameter 'untilTime' is provided, [KbWait](KbWait) will only wait  
until that time and then return regardless if anything happened on the  
keyboard or not.  
  
CAUTION: [KbWait](KbWait) periodically checks the keyboard. After each failed check  
(ie. no change in keyboard state) it will wait for 5 msecs before the  
next check. This is done to reduce the load on your system, and it is  
important to do so. However if you want to measure reaction times this is  
clearly not what you want, as it adds up to 5 msecs extra uncertainty to  
all measurements!  
  
If you have trouble with [KbWait](KbWait) always returning immediately, this could  
be due to "stuck keys". See "help [DisableKeysForKbCheck](DisableKeysForKbCheck)" on how to work  
around this problem. See also "help [RestrictKeysForKbCheck](RestrictKeysForKbCheck)".  
  
[GetChar](GetChar) and [CharAvail](CharAvail) are character oriented (and slow), whereas [KbCheck](KbCheck)  
and [KbWait](KbWait) are keypress oriented (and fast).  
  
Using [KbWait](KbWait) from the MATLAB command line: When you type "[KbWait](KbWait)" at the  
prompt and hit the enter/return key to execute that command, then [KbWait](KbWait)  
will detect the enter/return key press and return immediatly.  If you  
want to test [KbWait](KbWait) from the command line, then try this:  
  
 [WaitSecs](WaitSecs)(0.2);[KbWait](KbWait)  
  
[KbWait](KbWait) can also wait for releasing of keys instead of pressing of keys  
if you set the optional 2nd argument 'forWhat' to 1.  
  
If you want to wait for a single keystroke, set the 'forWhat' value to 2.  
[KbWait](KbWait) will then first wait until all keys are released, then for the  
first keypress, then it will return. The above example could be realized  
via:  
  
 [KbWait](KbWait)([], 2);  
  
If you would set 'forWhat' to 3 then it would wait for releasing the key  
after pressing it againg, ie. waitForAllKeysReleased -\> waitForKeypress  
-\> waitForAllKeysReleased -\> Return [secs, keyCode] of the key press.  
  
  
OSX and Linux: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[KbWait](KbWait) uses the [PsychHID](PsychHID) function, a general purpose function for  
reading from the Human Interface Device (HID) class of USB devices.  
  
[KbWait](KbWait) tests the first USB-HID keyboard device by default. Optionally  
you can pass in a 'deviceNumber' to test a different keyboard if multiple  
keyboards are connected to your machine.  If deviceNumber is -1, all  
keyboard devices will be checked.  If deviceNumber is -2, all keypad  
devices (if any) will be checked. If deviceNumber is -3, all keyboard and  
keypad devices will be checked. The device numbers to be checked are  
determined only on the first call to the function.  If these numbers  
change, the function can be reset using "clear [KbWait](KbWait)".  
  
As a little bonus, [KbWait](KbWait) can also query other HID human input devices  
which have keys or buttons as if they were keyboards. If you pass in the  
deviceIndex of a mouse [(GetMouseIndices]((GetMouseIndices) will provide with them), it will  
treat mouse button state as keyboard state. Similar behaviour usually  
works with Joysticks, Gamepads and other input controllers.  
  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
See also: [KbCheck](KbCheck), [KbStrokeWait](KbStrokeWait), [KbPressWait](KbPressWait), [KbReleaseWait](KbReleaseWait), [GetChar](GetChar), [CharAvail](CharAvail), [KbDemo](KbDemo).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/KbWait.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/KbWait.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/KbWait.m</code>
</div>

