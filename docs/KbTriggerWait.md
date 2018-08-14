# [KbTriggerWait](KbTriggerWait)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

secs = [KbTriggerWait](KbTriggerWait)(keyCode, [deviceNumber])  
  
Waits until one or more trigger keys have been pressed and returns the  
time of the first key press in seconds. The keyCode argument can be a  
vector of key indices. For example, to check for the 't' key as the  
trigger use [KbTriggerWait](KbTriggerWait)[(KbName]((KbName)('t')), to check for 't' and the escape  
key, use [KbTriggerWait](KbTriggerWait)([[KbName](KbName)('t'), [KbName](KbName)('ESCAPE')]).  
  
You cannot use [KbTriggerWait](KbTriggerWait) while a queue created by [KbQueueCreate](KbQueueCreate)  
exists. To shut down such a queue, use [KbQueueRelease](KbQueueRelease).  
  
On Matlab versions older than R2007a on MS-Windows, this function simply  
serves as a convenient substitute for using [KbCheck](KbCheck) to detect the  
trigger of interest.  
  
This function should allow triggers to be reliably detected from devices  
that only briefly report that the key is down. [KbCheck](KbCheck) is not reliable  
with such devices because it may not poll often enough to detect the  
key down state.  
  
[KbTriggerWait](KbTriggerWait) uses the [PsychHID](PsychHID) function, a general purpose function for  
reading from the Human Interface Device (HID) class of USB devices.  
Unlike [KbCheck](KbCheck), it starts a queue that receives keyboard events  
regarding the trigger key (and no other keys) and then polls this queue  
(rather than the current key status) periodically. In theory, this  
should also provide more accurate reporting of the time of the  
triggering keypress. However, if multiple trigger events have occurred  
since last polled, it is possible that the timestamp of the earliest  
of these will have already rotated out of the limited capacity (eight  
events) queue. In this case, the time of the earliest event remaining  
in the queue is reported. Since the polling frequency is the same as  
[KbCheck](KbCheck), it should be more accurate on average with regard to timing,  
even when the timestamps of the earliest events have been lost due to  
queue overflow.  
  
[KbTriggerWait](KbTriggerWait) tests the first USB-HID keyboard device by default.  
Optionally, you can pass in a 'deviceNumber' to test a different keyboard  
if multiple keyboards are connected to your machine. The function also  
allows to wait for button presses on keypads, mice or other HID devices  
with buttons or keys.  
  
Passing a deviceNumber of -1 will NOT cause all keyboards to be detected  
  
One disadvantage of this function is that it renders Matlab relatively  
unresponsive to Ctrl-C interrupts. [KbQueueWait](KbQueueWait) is a better option in  
this regard, but more complicated to use.  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
See also: [KbQueueWait](KbQueueWait) [KbCheck](KbCheck), [KbWait](KbWait), [GetChar](GetChar), [CharAvail](CharAvail), [KbDemo](KbDemo).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/KbTriggerWait.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/KbTriggerWait.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/KbTriggerWait.m</code>
</div>

