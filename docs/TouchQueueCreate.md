# [TouchQueueCreate](TouchQueueCreate)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

[TouchQueueCreate](TouchQueueCreate)(windowHandle, deviceNumber [, numSlots=100000][, numValuators=auto][, keyList=all])  
  
Create a touch queue for receiving touch input from touch input devices  
like touchscreens, tablets, touch surfaces, or touchpads.  
  
'windowHandle' Handle for a [Screen](Screen)() onscreen window for which touch  
should be received.  
  
'deviceNumber' Handle for the touch input device. [GetTouchDeviceIndices](GetTouchDeviceIndices)()  
allows to enumerate touch devices.  
  
'numSlots' Number of input slots for storing touch events. You must empty  
the queue frequently enough, so no more than 'numSlots' events collect in  
the queue, or the queue will stop storing new events and drop information.  
  
'numValuators' Number of optional touch device properties to store per  
event. Defaults to what the device can provide.  
  
'keyList' If the touch queue is also used to receive button input from  
physical buttons (or maybe virtual buttons?) from the device, this provides  
the list of buttons to accept. See [KbQeueCreate](KbQeueCreate) for explanation. By default  
all buttons are accepted.  
  
Once a queue is created its touch data collection can be started via  
[TouchQueueStart](TouchQueueStart)(), stopped via [TouchQueueStop](TouchQueueStop)(), cleared via [TouchQueueFlush](TouchQueueFlush)(),  
asked for current number of pending events via [TouchEventAvail](TouchEventAvail)() and events  
can be fetched via [TouchEventGet](TouchEventGet)().  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/TouchQueueCreate.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/TouchQueueCreate.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/TouchQueueCreate.m</code>
</div>

