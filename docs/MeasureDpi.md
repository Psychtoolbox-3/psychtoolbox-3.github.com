# [MeasureDpi](MeasureDpi)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

[dpi, SP] = [MeasureDpi](MeasureDpi)([theScreen=max][, useCreditCard=0]);  
  
Helps the user to accurately measure the screen's dots per inch by use of a  
reference object of known size.  
  
### INPUT:  
  
'theScreen' [Screen](Screen) parameter, if the screen is not provided, the  
screen with maximum index (typically an external display) will be used.  
  
'useCreditCard' Credit Card parameter, it allows you to use a credit card as  
an object of known size if set to 1. Otherwise it is recommended to have a  
ruler or some other object of known size at hand, and the script will ask for  
the size of that object.  
  
### OUTPUT:  
  
'dpi' Measured dots per inch.  
'SP'  [Screen](Screen) properties reported by the display driver (e.g., based on EDID).  
It will provide you with a structure containing the physical size of the  
screen (width and height) in mm, the screen resolution in pixels, the  
dot pitch and dpi automatically.   
  
Note: 'SP' relies on information from [Screen](Screen)('DisplaySize'). Read the notes  
in '[Screen](Screen) [DisplaySize](DisplaySize)?' on potential limitations in reliability or accuracy  
of this driver reported info.  
  
Denis Pelli  
  
History  
  
5/28/96 dgp Updated to use new [GetMouse](GetMouse).  
3/20/97 dgp Updated.  
4/2/97  dgp [FlushEvents](FlushEvents).  
4/26/97 dhb Got rid of call to disp(7), which was writing '7' to the  
            command window and not producing a beep.  
8/16/97 dgp Changed "text" to "theText" to avoid conflict with TEXT function.  
4/06/02 awi Check all elements of the new multi-element button vector  
            returned by [GetMouse](GetMouse) on Windows.  
            Replaced Chicago font with Arial because it's available on  
            both Mac and Windows  
11/6/06 dgp Updated from PTB-2 to PTB-3.  
01/31/16 mk Fix some wrong assumptions for PTB-3. Get rid of [GetChar](GetChar).  
8/13/19 mgg Modify to use it with a credit card (common object of a  
            known size).  
9/10/19 mgg Optional output: Withdraw the presets from the screen  
            inc. the screen size, resolution, dot pitch and distance independent dpi.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/MeasureDpi.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/MeasureDpi.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/MeasureDpi.m</code>
</div>

