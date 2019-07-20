# [KbEventGet](KbEventGet)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

[event, nremaining] = [KbEventGet](KbEventGet)([deviceIndex][, maxWaitTimeSecs=0])  
  
Return oldest pending event, if any, in return argument 'event', and the  
remaining number of recorded events in the event buffer of a keyboard  
queue in the return argument 'nremaining'.  
  
By default, the event buffer of the default keyboard queue is checked,  
but you can specify 'deviceIndex' to check the buffer of the queue  
associated with 'deviceIndex'.  
  
[KbEventGet](KbEventGet)() will wait up to 'maxWaitTimeSecs' seconds for at least one  
event to show up before it gives up. By default, it doesn't wait but just  
gives up if there aren't any events queued at time of invocation.  
  
'event' is either empty if there aren't any events available, or it is a  
struct with information about the keyboard event. The returned event  
struct currently contains the following fields:  
  
'Keycode' = The [KbCheck](KbCheck) / [KbName](KbName) style keycode of the key or button that  
            triggered this event.  
  
'Time' = The [GetSecs](GetSecs) time of when the event was received.  
  
'Pressed' = 1 for a key press event, 0 for a key release event.  
  
'CookedKey' = Keycode translated into a [GetChar](GetChar)() style Unicode character code.  
Or zero if key does not have a corresponding character. Or -1 if mapping  
is unsupported for given event.  
  
A note on international keyboards: Non US keyboards with a different layout,  
e.g., german keyboards, may have keys that do not exist on US keyboards, e.g.,  
german umlauts like ö, ä, ü, ß. How such non-ASCII characters are translated  
into proper 'CookedKey' key codes is dependent on the language locale setup of  
your operating system for the keyboard. There is some potential for confusion  
there and it could happen that if Psychtoolbox misdetects the chosen keyboard  
layout, it will return such keys with the wrong character code. E.g., the ö key  
of a german keyboard may map to a ; key if german layout is misdetected as US  
layout. If this happens, try to select the proper keyboard layout in the GUI  
setup tools of your operating system, "clear all" and then retry. On Linux/X11  
it has been observed that this settings selected via GUI tools is not always  
respected, e.g., on the KDE and GNOME desktop environment. In this case, use  
of the terminal command line tool "setxkbmap" managed to enforce use of the  
correct keyboard layout for key -\> char translation. E.g., "setxkbmap -layout de"  
to select a german keyboard layout. Obviously you could call  
system('setxkbmap -layout de'); from within your script to achieve this effect.  
  
Psychtoolbox will return mapped keys in 'CookedKey' as double() values, encoding  
Unicode character codes in the UTF-16 (on MS-Windows) or UTF-32 (Linux, macOS)  
encoding and code range. This currently works splendidly with Matlab, but current  
versions of GNU/Octave (as of version 5.1) are not really unicode capable and can  
only deal with UTF-8 encoded strings in a limited fashion. This means that if you  
use Octave, you can receive proper 'CookedKey' UTF-32 unicode characters from  
international keyboards, you can manipulate the double() values in your script,  
but Octave's string processing functions, or even printing such characters to  
the Octave command window via disp() or fprintf() will likely give wrong behaviour.  
This is a design limitation of current Octave, so you will have to work around it.  
  
Keyboard event buffers are a different way to access the information  
collected by keyboard queues. Before you can use an event buffer you  
always must create its "parent keyboard queue" via [KbQueueCreate](KbQueueCreate)() and  
call [KbQueueStart](KbQueueStart)() to enable key event recording. See "help  
[KbQueueCreate](KbQueueCreate)" etc. on how to do this.  
  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
See also: [KbQueueCreate](KbQueueCreate), [KbQueueStart](KbQueueStart), [KbQueueStop](KbQueueStop), [KbQueueCheck](KbQueueCheck),  
           [KbQueueWait](KbQueueWait), [KbQueueFlush](KbQueueFlush), [KbQueueRelease](KbQueueRelease)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/KbEventGet.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/KbEventGet.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/KbEventGet.m</code>
</div>

