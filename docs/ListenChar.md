# [ListenChar](ListenChar)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

function [ListenChar](ListenChar)([listenFlag])  
  
Tell the Psychtoolbox function "[GetChar](GetChar)" to start or stop listening for  
keyboard input. By default [ListenChar](ListenChar) enables listening when no argument is  
supplied. Passing 0 will turn off character listening and reset the  
buffer which holds the captured characters. Passing a value of 1 or not  
passing any value will enable listening. Passing a value of 2 will enable  
listening, additionally any output of keypresses to Matlabs or Octaves  
windows is suppressed. Use this with care, if your script aborts with an  
error, Matlab or Octave may be left with a dead keyboard until the user  
presses CTRL+C to reenable keyboard input. 'listenFlag' 2 is silently  
ignored on Matlab in -nojvm mode under MS-Windows.  
  
Passing the listenFlag -1 will only suppress keypresses into Matlabs or  
Octaves command window, but not collect characters for use with [CharAvail](CharAvail)  
or [GetChar](GetChar). This allows concurrent use of [ListenChar](ListenChar) for character suppression  
while at the same time using keyboard queues for character and key input.  
Reenabling keypresses into Matlab and Octave is only possible via a call  
with listenFlag 0 if suppression was enabled with listenFlag -1. Use of  
listenFlag -1 does not block keyboard queues, so if you want to get keyboard  
input, the better way might be to use keyboard queues (see [KbEventAvail](KbEventAvail),  
[KbEventGet](KbEventGet) and [KbEventFlush)](KbEventFlush)) for input and [ListenChar](ListenChar)(-1) and [ListenChar](ListenChar)(0)  
to suppress characters into the Matlab/Octave command window or console.  
  
This function isn't entirely necessary to turn on listening as calling  
[GetChar](GetChar), [CharAvail](CharAvail), or [FlushEvents](FlushEvents) will trigger listening on. However,  
it is the only method by which to disable listening or switch between  
suppression of keyboard input to Matlab and unsuppressed mode.  
  
Please note that the commands [ListenChar](ListenChar), [CharAvail](CharAvail) and [GetChar](GetChar) are  
subject to various constraints and limitations, depending on the  
operating system you use, if you use Matlab in Java or -nojvm mode, if  
you use Octave, if you have [Screen](Screen)() onscreen windows open or not, or if  
you use [KbQueueXXX](KbQueueXXX) functions in parallel or not. Therefore use of these  
functions can be troublesome for any but the most simple usages. Use of  
[KbCheck](KbCheck), [KbWait](KbWait), [KbStroke](KbStroke)/Press/[ReleaseWait](ReleaseWait) is often simpler if you are  
just after keyboard input. Use of [KbQueue](KbQueue) functions, e.g., [KbQueueCheck](KbQueueCheck),  
[KbQueueWait](KbQueueWait), [KbTriggerWait](KbTriggerWait) is better suited for background keystroke  
collection. Use of [KbEventAvail](KbEventAvail) and [KbEventGet](KbEventGet) is often more convenient,  
more flexible and subject to less restrictions and gotchas than use of  
[GetChar](GetChar) et al.  
  
### Some of the restrictions and caveats:  
  
1. Works very well with Matlab and its Java based GUI enabled on Linux  
and [MacOSX](MacOSX), as well as on [WindowsXP](WindowsXP) and earlier versions of Windows.  
  
2. When used on Windows Vista or later (Vista, Windows-7, Windows-8, ...)  
with Matlab's Java GUI, you cannot use any [KbQueue](KbQueue) functions at the same  
time, ie., [KbQueueCreate](KbQueueCreate)/Start/Stop/Check/Wait as well as [KbWaitTrigger](KbWaitTrigger),  
[KbEventFlush](KbEventFlush), [KbEventAvail](KbEventAvail), and [KbEventGet](KbEventGet) are off limits after any call  
to [ListenChar](ListenChar), [ListenChar](ListenChar)(1), [ListenChar](ListenChar)(2), [FlushEvents](FlushEvents), [CharAvail](CharAvail) or  
[GetChar](GetChar). You would need to call [ListenChar](ListenChar)(0) before you could call  
[KbQueueCreate](KbQueueCreate) and then use those functions. Vice versa, after a call to  
[KbQueueCreate](KbQueueCreate), [CharAvail](CharAvail), [FlushEvents](FlushEvents), and [GetChar](GetChar) are dysfunctional and  
[ListenChar](ListenChar) may be limited. You need to call [KbQueueRelease](KbQueueRelease) before you can  
use them again. Use of other devices, e.g., mouse or joystick, is not  
prohibited during use of [GetChar](GetChar) et al.  
  
3. If you use Matlab in "matlab -nojvm" mode without its GUI, or if you  
use GNU/Octave instead of Matlab, the same restrictions as in 2. apply -  
no parallel use of the default keyboards [KbQueue](KbQueue). [KbQueues](KbQueues) can be used  
for other input devices and on Linux and OSX for keyboards other than the  
default keyboard.  
  
The only feature that works in parallel with [KbQueues](KbQueues) on the default keyboard  
is the suppression of spilling of keystroke characters into the Matlab or  
Octave window during [ListenChar](ListenChar)(2) - at least on Linux and OSX. On  
Windows this can't be prevented at all in "matlab -nojvm" mode. However,  
if you switch to [ListenChar](ListenChar)(2) mode, you cannot break out of it by  
pressing CTRL+C on Linux if the keyboard queue that is in parallel use  
didn't get [KbQueueStart](KbQueueStart) called, ie. if it is stopped. On OSX with a  
stopped Keyboard queue, neither CTRL+C nor stopping a runaway script  
works.  
  
4. On Linux, as a exception, some [GetChar](GetChar), [CharAvail](CharAvail) functionality may  
still work in case 3. under certain conditions, e.g., if you don't use  
[ListenChar](ListenChar)(2) and your Matlab/Octave is not in interactive mode.  
  
Also, [GetChar](GetChar) can only collect keystrokes from multiple connected  
keyboards in case 1. In all other cases, it can only collect keystrokes,  
or respond to press of CTRL+C, for the default keyboard device. It will  
ignore other connected keyboards.  
  
Basically: Mixing [GetChar](GetChar) et al. and modern [KbQueue](KbQueue) functions is usually  
not advisable, or if needed, great care must be taken to sidestep all the  
mentioned limitations. Also the [KbQueue](KbQueue) functions usually have better  
timing precision and allow to flexibly address multiple keyboards  
separately at least on Linux and OSX.  
  
  
For further explanation see help for "[GetChar](GetChar)".    
  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
See also: [GetChar](GetChar)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/ListenChar.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/ListenChar.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/ListenChar.m</code>
</div>

