# [GetTouchValuators](GetTouchValuators)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)

event = [GetTouchValuators](GetTouchValuators)(event, deviceInfo)  
  
Return 'event', an augmented version of the input 'event', ie. event extended  
with info about additional semantic meaning of the specified touch input event,  
using device specific semantic mapping info provided in 'deviceInfo'.  
  
### Typical use:  
  
1. Get 'deviceInfo' at script startup:  
   deviceInfo = [GetTouchDeviceInfo](GetTouchDeviceInfo)(deviceIndex);  
  
2. For each retrieved touch event evt = [TouchEventGet](TouchEventGet)(...):  
   evt = [GetTouchValuators](GetTouchValuators)(evt, deviceInfo)  
  
Which information is available on a given operating system/display system and  
device combo is variable, but the returned event struct potentially has the  
following additional fields:  
  
.[RawX](RawX) = Raw device x position of touch.  
  
.[RawY](RawY) = Raw device y position of touch.  
  
.[ToolX](ToolX) = Raw device x position of approaching tool, if detectable.  
  
.[ToolY](ToolY) = Raw device y position of approaching tool, if detectable.  
  
.[ToolType](ToolType) = Type of tool used on the surface. There are numbers for finger,  
            palm, and different type of styluses.  
  
.Pressure = Pressure which the touch applies to the touch device surface,  
            normalized to 0.0 - 1.0 range.  
  
.Distance = Distance from the touch surface, normalized to 0.0 - 1.0 range,  
            with 0.0 = contact, 1.0 = Maximally far away while still being  
            detectable, iow. hovering over the surface.  
  
.[TouchMajor](TouchMajor) = Length of major axis of an ellipse which approximates the shape  
              of the touch area, in device units.  
  
.[TouchMinor](TouchMinor) = Length of minor axis of an ellipse which approximates the shape  
              of the touch area, in device units.  
  
.[WidthMajor](WidthMajor) and .[WidthMinor](WidthMinor) are major/minor width of an ellipse approximating  
 the complete object approaching the screen. The ratio [TouchMajor](TouchMajor) / [WidthMajor](WidthMajor)  
 and [TouchMinor](TouchMinor) / [WidthMinor](WidthMinor) can be used to approximate how close/strong a touch  
 is, in the absence of .Pressure or .Distance information.  
  
.Orientation = If the touch contact area isn't circular and the hardware can  
               detect the orientation of a touch area, then this stores orientation  
               in degrees. 0 degrees = Upward pointing - aligned with positive  
               y-axis of the touch surface. \> 0 degress = clock-wise turn, < 0  
               degrees = counter clock-wise turn. Many devices can not find out  
               orientation at all, or only if a contact is more vertical (0 deg.)  
               rather more horizontal (90 deg.).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/GetTouchValuators.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/GetTouchValuators.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/GetTouchValuators.m</code>
</div>

