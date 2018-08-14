# [RenderDemo](RenderDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

 [RenderDemo](RenderDemo)  
  
 Illustrates calibration interface for simple task of producing a uniform  
 color patch of desired CIE xyY coordinates.  
  
 The calculation is done with respect to the current PTB demonstration  
 calibration file.  
  
 The demo shows multiple different ways to implement this, starting with a  
 purely Matlab based method, progressing to more advanced methods. The  
 final demonstration shows how to do it automatically and graphics  
 hardware accelerated.  
  
###  Demo 1:  
  
 The RGB values are gamma corrected and live in the range [0,1].  If they  
 contain 0 or 1, the xyY coordinates requested may have been out of gamut.  
  
 A uniform color patch is displayed in the MATLAB figure window. This is  
 not a well-controlled display method, but does give a sense of the patch  
 color if the calibration file is a reasonable description of the display.  
  
 Immediately afterwards, the same color patch is shown in a PTB onscreen  
 window, with the same gamma table loaded which was used during  
 calibration measurements. This should render an accurate stimulus.  
  
 Demo 2: As demo 1, but displaying in a onscreen window and performing the  
 gamma correction via proper inverse gamma lookup tables loaded into the  
 graphics card, thereby presenting on a linearized display, instead of  
 using the [SensorToSettings](SensorToSettings)() routine to adapt the stimulus to a  
 non-linearized display.  
  
 The last two demos Demo 3 and Demo 4 require a recent graphics card and  
 perform all color space conversions and calibrated display automatically  
 and hardware accelerated on the graphics card. Any [NVidia](NVidia) [GeForce](GeForce)-8000 or  
 later, AMD Radeon X-1000 or later, or Intel HD graphics card should be  
 able to support these demos.  
  
 Demo 3: The stimulus is defined in XYZ tristimulus color space and  
 converted automatically by [Screen](Screen)() into RGB output format, taking the  
 calibration data in 'cal' into account.  
  
 Demo 4: The stimulus is directly defined in xyY chromacity + luminance  
 format and all conversions and calibrations are done automatically by  
 [Screen](Screen)().  
  
 4/26/97  dhb  Wrote it.  
 7/25/97  dhb  Better initialization.  
 3/12/98  dgp  Use [Ask](Ask).  
 3/14/02  dhb  Update for [OpenWindow](OpenWindow).  
 4/03/02  awi  Merged in Windows changes.  On Windows we do not copy the result to the clipboard.   
 4/13/02  awi   Changed "[SetColorSpace](SetColorSpace)" to new name "[SetSensorColorSpace](SetSensorColorSpace)".  
                Changed "[LinearToSettings](LinearToSettings)" to new name "[SensorToSettings](SensorToSettings)".  
 12/21/02 dhb  Remove reliance on now obsolete [OpenWindow](OpenWindow)/[CloseWindow](CloseWindow).  
 11/16/06 dhb  Start getting this to work with PTB-3.  
 11/22/06 dhb  Fixed except that [Ask](Ask)() needs to be fixed.  
 6/16/11  dhb  The PTB display section was out of date and didn't work.  I removed it.  
 1/26/13  mk   Add standard PTB display, but also imaging pipeline based methods.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/RenderDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/RenderDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/RenderDemo.m</code>
</div>

