# [GetClicks](GetClicks)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

[clicks,x,y,whichButton,clickSecs] = [GetClicks](GetClicks)([windowPtrOrScreenNumber][, interclickSecs][, mouseDev][, untilTime=inf])  
  
Wait for the user to click the mouse, and then count the number of clicks  
that occur within a inter-click interval of each other. Return the number  
of 'clicks' and the mouse location 'x', 'y', as well as the indices of the  
pressed buttons in vector 'whichButton', and a vector 'clickSecs' with  
the timestamps of when each click was detected.  
  
The x,y location is the location at the downstroke of the first mouse  
click. The mouse position (x,y) is "local", i.e. relative to the origin of  
the window or screen, if supplied; otherwise it's "global", i.e. relative  
to the origin of the desktop.  
  
The allowed inter-click interval can be adjusted by setting the Matlab  
global variable "ptb\_mouseclick\_timeout" to a value in seconds. E.g.,  
global ptb\_mouseclick\_timeout; ptb\_mouseclick\_timeout = 1; would set the  
inter-click interval to 1 second. By default, the interval is 500 msecs.  
  
You can also specify an override interval in the optional argument  
'interClickSecs' for a given call to [GetClicks](GetClicks). A setting of zero would  
disable multi-click detection, ie., only wait for first mouse-click or  
press, then return immediately.  
  
If the optional parameter 'untilTime' is provided, [GetClicks](GetClicks) will only wait  
for the first click until that time and then return, regardless if the 1st click  
happened or not. On such a timeout, all return arguments will be zero. E.g.,  
[clicks,x,y,whichButton,clickSecs] = [GetClicks](GetClicks)(window, 0.2, [], [GetSecs](GetSecs) + 5);  
would wait up to 5 seconds in total for the first click to happen, and then  
another 0.2 seconds for a 2nd click, then 0.2 seconds for a 3rd click...  
  
The optional 'mouseDev' parameter allows to select a specific mouse or  
pointer device to query if your system has multiple pointer devices.  
Currently Linux only, silently ignored on other operating systems.  
  
See Also: [GetMouse](GetMouse), [SetMouse](SetMouse), [GetMouseIndices](GetMouseIndices)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/GetClicks.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/GetClicks.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/GetClicks.m</code>
</div>

