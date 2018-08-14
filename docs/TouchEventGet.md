# [TouchEventGet](TouchEventGet)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

[event, nremaining] = [TouchEventGet](TouchEventGet)(deviceIndex, windowHandle [, maxWaitTimeSecs=0])  
  
Return oldest pending event, if any, in return argument 'event', and the  
remaining number of recorded events in the event buffer of a touch  
queue in the return argument 'nremaining'.  
  
[TouchEventGet](TouchEventGet)() will wait up to 'maxWaitTimeSecs' seconds for at least one  
event to show up before it gives up. By default, if 'maxWaitTimeSecs' is 0  
or empty or omitted, it doesn't wait but just gives up if there aren't any  
events queued at time of invocation. In that case it returns an empty 'event'.  
  
'event' is either empty if there aren't any events available, or it is a  
struct with various information about the touch event. The returned event  
struct currently contains at least the following useful fields:  
  
'Type' = 0 for button presses or releases if the touch device also has  
         physical or logical buttons. 'Pressed' will tell if this is a  
         button press (1) or release (0) event.  
  
       = 1 single touch point move: Only happens on some mousepads if mouse  
         emulation kicks in. 'X', 'mappedX' and 'Y' / 'mappedY' will tell the  
         touch point / emulated mouse cursor position.  
  
       = 2 New touch: 'X/[NormX](NormX)/mappedX' and 'Y/[NormY](NormY)/mappedY' tell start location.  
           Happens, e.g., when a finger touches the touch surface. The 'Keycode'  
           contains a numeric id which uniquely identifies this touch point while  
           it is active, e.g., while the finger stays on the surface.  
  
       = 3 Touch moved: 'X/[NormX](NormX)/mappedX' and 'Y/[NormY](NormY)/mappedY' tell new location.  
           E.g., when a finger moves over the touch surface. 'Keycode' allows you  
           to know which of possible multiple fingers or tools is moving.  
  
       = 4 Touch finished: 'X/[NormX](NormX)/mappedX' and 'Y/[NormY](NormY)/mappedY' tell final location.  
           Happens when the finger or tool is lifted from the touch surface. The  
           'Keycode' tells you which finger or tool was lifted from the surface.  
  
       = 5 Touch data lost: Some other application or the GUI took over our  
           touch input, and cut us off from it, so the recorded touch data  
           sequence is incomplete. You should wait a second, then call  
           [TouchEventFlush](TouchEventFlush)() to discard all remaining events in the queue,  
           then mark your trial invalid and take some corrective action,  
           maybe asking the experimenter to disable other running touch  
           applications or GUI services, e.g., touch gesture recognition of  
           the system user interface, so they can no longer interfere with  
           experiment data collection.  
  
'X'    = x-position in units of screen pixels, with fractional (sub-pixel) resolution.  
'Y'    = y-position in units of screen pixels, with fractional (sub-pixel) resolution.  
  
The origin (0,0) for 'X' and 'Y' coordinates is the top-left corner of the screen  
on MS-Windows and on Linux with classic X11 X-Window display system. On Linux with  
the next-generation Wayland display system, (0,0) refers to the top-left corner of  
the associated onscreen window for the touch event. Use 'mappedX' and 'mappedY'  
below if you always want onscreen window relative coordinates, transformed to the  
top-left corner of the provided 'windowHandle'.  
  
'NormX' = Normalized x-position in range 0 - 1. Constant 0 if unavailable.  
'NormY' = Normalized y-position in range 0 - 1. Constant 0 if unavailable.  
  
'MappedX' = x-position relative to provided onscreen window with 'windowHandle'.  
'MappedY' = y-position relative to provided onscreen window with 'windowHandle'.  
  
'Time' = The [GetSecs](GetSecs) time when the event was received.  
  
'Keycode' = The unique numeric id key of this touch point. A specific physical  
            touch, e.g., one specific finger touching a touchscreen, will get  
            a unique number assigned, which will persist while the finger rests  
            or moves on the touch surface, until it is lifted off the surface,  
            ie. the unique number is assigned in a Type=2 event, kept throughout  
            Type=3 events, and last used in Type=4 events, before it goes the  
            way of all mortal things. If you'd put the same finger down onto the  
            touch surface again, it would get a new unique number assigned, as  
            the touch hardware doesn't know it is the same finger.  
  
'Pressed' = 1 while a touch point is active (finger touches screen), 0 when the  
            touch point is removed, e.g., finger lifted from screen.  
  
'Motion'  = 1 while a touch point (=finger) is moving over the surface, 0 while  
            it is resting.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/TouchEventGet.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/TouchEventGet.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/TouchEventGet.m</code>
</div>

