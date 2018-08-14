# [KbQueueCreate](KbQueueCreate)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

[KbQueueCreate](KbQueueCreate)([deviceNumber][, keyList][, numValuators=0][, numSlots=10000][, flags=0])  
  
The routines [KbQueueCreate](KbQueueCreate), [KbQueueStart](KbQueueStart), [KbQueueStop](KbQueueStop), [KbQueueCheck](KbQueueCheck)  
 [KbQueueWait](KbQueueWait), [KbQueueFlush](KbQueueFlush) and [KbQueueRelease](KbQueueRelease) provide replacements for  
 [KbCheck](KbCheck) and [KbWait](KbWait), providing the following advantages:  
  
    1) Brief key presses that would be missed by [KbCheck](KbCheck) or [KbWait](KbWait)  
       are reliably detected  
    2) The times of key presses are recorded more accurately  
    3) The times of key releases are also recorded  
  
### Limitations:  
  
    1) If a key is pressed multiple times before [KbQueueCheck](KbQueueCheck) is called,  
       only the times of the first and last presses and releases of that  
       key can be recovered (this has no effect on other keys)  
    2) If many keys are pressed very quickly in succession on OSX, it is  
       at least theoretically possible for the queue to fill more quickly  
       than it can be emptied, losing key events temporarily while filled  
       to capacity. The queue holds up to thirty events, and events are  
       constantly being removed from the queue and processed, so this is  
       unlikely to be a problem in actual use.  
  
 The deviceNumber of a HID input device can be specified as 'deviceNumber'.  
 Allowable devices are "keyboard like" devices, e.g., Keyboards, Keypads,  
 Mouse, Joystick, Gamepad, Touchpad, etc. - Stuff that has buttons or keys  
 to press. This way a mouse or joysticks buttons can be used as response  
 devices, ignoring mouse movements etc. If deviceNumber is not specified, the first   
 device is the default (like [KbCheck)](KbCheck)). If [KbQueueCreate](KbQueueCreate) has not been called   
 first, the other routines will generate an error message. Likewise, if   
 [KbQueueRelease](KbQueueRelease) has been called more recently than [KbQueueCreate](KbQueueCreate), the other   
 routines will generate error messages.  
  
It is acceptable to call [KbQueueCreate](KbQueueCreate) at any time (e.g., to switch to a new  
 device or to change the list of queued keys) without calling [KbQueueRelease](KbQueueRelease).  
  
 [KbQueueCreate](KbQueueCreate)([deviceNumber][, keyList][, numValuators=0][, numSlots=10000][, flags=0])  
     Creates the queue for the specified (or default) device number  
     If the device number is less than zero, the default device is used.  
  
     'keyList' is an optional 256-length vector of doubles (not logicals)  
     with each element corresponding to a particular key (use [KbName](KbName)  
     to map between keys and their positions). If the double value  
     corresponding to a particular key is zero, events for that key  
     are not added to the queue and will not be reported.  
  
     'numValuators' is an optional maximum number of additional values to report.  
     It defaults to zero. For values greater than zero, if the selected type  
     of input device supports this, and if the operating system supports this,  
     additional info will be recorded. For pointing devices like mice, the mouse  
     position may be reported, for joysticks the state of their various axis, etc.  
     For mouse/joystick/pointing device position reporting numValuators must be  
     at least 2. On touch devices, a value of 2 treats them like a mouse, a value  
     \>= 4 treats them as touchscreen. However, for touch devices there are separate  
     functions like [TouchQueueCreate](TouchQueueCreate), [TouchEventGet](TouchEventGet) etc. for convenient handling.  
     See "help [KbEventGet](KbEventGet)" for how to retrieve potential additionally recorded  
     information.  
  
     'numSlots' defines how many events the event buffer can store. If a script  
     does not periodically remove events via [KbEventGet](KbEventGet)() or [KbEventFlush](KbEventFlush)(), the  
     buffer will fill up, and once 'numSlots' elements are stored, it will stop  
     recording new events. 10000 elements capacity is the default, which may be  
     too little if you use 'numValuators' \> 0 to store dynamic (motion) data like  
     mouse movements or touchscreen input, which can be generated at rates of  
     multiple hundred events per second of data collection.  
  
     'flags' defines special modes of operation for the queue. These are OS  
     specific, see "[PsychHID](PsychHID) [KbQueueCreate](KbQueueCreate)?" for an up to date list of supported  
     flags. In general, you don't need these.  
  
     No events are delivered to the queue until [KbQueueStart](KbQueueStart) or   
     [KbQueueWait](KbQueueWait) is called.  
     [KbQueueCreate](KbQueueCreate) can be called again at any time. The function can also  
     treat other HID devices with buttons or keys as if they are  
     keyboards. E.g., it can also record button state of a mouse, a  
     joystick or a gamepad.  
  
 [KbQueueStart](KbQueueStart)([deviceNumber])  
     Starts delivering keyboard events from the specified device to the   
     queue.  
  
 [KbQueueStop](KbQueueStop)([deviceNumber])  
     Stops delivery of new keyboard events from the specified device to   
     the queue.  
     Data regarding events already queued is not cleared and can be   
     recovered by [KbQueueCheck](KbQueueCheck)  
  
[pressed, firstPress, firstRelease, lastPress, lastRelease]=  
  [KbQueueCheck](KbQueueCheck)([deviceNumber])  
     Obtains data about keypresses on the specified device since the   
     most recent call to this routine, [KbQueueStart](KbQueueStart), [KbQueueWait](KbQueueWait)  
     Clears all scored events, but unscored events that are still being  
     processsed may remain in the queue  
  
     pressed: a boolean indicating whether a key has been pressed  
  
     firstPress: an array indicating the time that each key was first  
       pressed since the most recent call to [KbQueueCheck](KbQueueCheck) or [KbQueueStart](KbQueueStart)  
  
     firstRelease: an array indicating the time that each key was first  
       released since the most recent call to [KbQueueCheck](KbQueueCheck) or [KbQueueStart](KbQueueStart)  
  
     lastPress: an array indicating the most recent time that each key was  
       pressed since the most recent call to [KbQueueCheck](KbQueueCheck) or [KbQueueStart](KbQueueStart)  
  
     lastRelease: an array indicating the most recent time that each key  
        was released since the most recent call to [KbQueueCheck](KbQueueCheck) or   
        [KbQueueStart](KbQueueStart)  
  
    For firstPress, firstRelease, lastPress and lastRelease, a time value  
      of zero indicates that no event for the corresponding key was  
      detected since the most recent call to [KbQueueCheck](KbQueueCheck) or [KbQueueStart](KbQueueStart)  
  
    To identify specific keys, use [KbName](KbName) (e.g., [KbName](KbName)(firstPress)) to  
      generate a list of the keys for which the events occurred  
  
    For compatibility with [KbCheck](KbCheck), any key codes stored in  
    ptb\_kbcheck\_disabledKeys (see "help [DisableKeysForKbCheck](DisableKeysForKbCheck)"), will  
    not cause pressed to return as true and will be zeroed out in the  
    returned arrays. However, a better alternative is to specify a  
    keyList arguement to [KbQueueCreate](KbQueueCreate).   
  
secs=[KbQueueWait](KbQueueWait)([deviceNumber])  
     Waits for any key to be pressed and returns the time of the press.  
  
     [KbQueueFlush](KbQueueFlush) should be called immediately prior to this function  
     (unless the queue has just been created and started) to clear any   
     prior events.  
  
     Note that this command will not respond to any keys that were   
     inactivated by using the keyList argument to [KbQueueCreate](KbQueueCreate).  
  
     Since [KbQueueWait](KbQueueWait) is implemented as a looping call to  
     [KbQueueCheck](KbQueueCheck), it will not respond to any key codes stored in  
     the global variable ptb\_kbcheck\_disabledKeys  
     (see "help [DisableKeysForKbCheck](DisableKeysForKbCheck)")  
  
[KbQueueFlush](KbQueueFlush)([deviceNumber])  
     Removes all unprocessed events from the queue and zeros out any  
     already scored events.  
  
[KbQueueRelease](KbQueueRelease)([deviceNumber])  
     Releases queue-associated resources; once called, [KbQueueCreate](KbQueueCreate)  
     must be invoked before using any of the other routines  
  
     This routine is called automatically at clean-up (e.g., when   
     'clear mex' is invoked and can be omitted expense of keeping   
     memory allocated and an additional thread running unnecesarily  
  
Note that any keyboard typing used to invoke [KbQueue](KbQueue) commands will be  
recorded. This would include the release of the carriage return used  
to execute [KbQueueStart](KbQueueStart) and the keys pressed and released to invoke   
[KbQueueCheck](KbQueueCheck)  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
See also: [KbQueueCreate](KbQueueCreate), [KbQueueStart](KbQueueStart), [KbQueueStop](KbQueueStop), [KbQueueCheck](KbQueueCheck),  
          [KbQueueWait](KbQueueWait), [KbQueueFlush](KbQueueFlush), [KbQueueRelease](KbQueueRelease)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/KbQueueCreate.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/KbQueueCreate.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/KbQueueCreate.m</code>
</div>

