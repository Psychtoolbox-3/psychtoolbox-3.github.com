# [CalibrateMonitorPhotometer](CalibrateMonitorPhotometer)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

[gammaTable1, gammaTable2, displayBaseline, displayRange. displayGamma, maxLevel ] = [CalibrateMonitorPhotometer](CalibrateMonitorPhotometer)([numMeasures=9][, screenid=max])  
  
A simple calibration script for analog photometers.  
  
Use [CalibrateMonSpd](CalibrateMonSpd)() if you want to do more fancy calibration with  
different types of photometers or special devices like Bits+ or [DataPixx](DataPixx),  
assuming you know how to operate [CalibrateMonSpd](CalibrateMonSpd)() that is...  
  
numMeasures (default: 9) readings are taken manually, and the readings  
are fit with a gamma function and piecewise cubic splines. numMeasures -  
1 should be a power of 2, ideally (9, 17, 33, etc.). The corresponding  
linearized gamma tables (1 -\> gamma, 2 -\> splines) are returned, as well  
as the display baseline, display range in cd/m^2 and display gamma. Plots  
of the two fits are created as well. Requires fit tools.  
  
If the normalized gamma table is not loaded, then the cd/m^2 value of a  
screen value can be figured out by the formula: cdm2 =  
displayRange\*(screenval/maxLevel).^(1/displayGamma) + displayBaseline.  
  
Generally, you will want to load the normalized gamma tables and use them  
in [Screen](Screen)('LoadNormalizedGammaTable'). For example:  
  
[gammaTable1, gammaTable2] = [CalibrateMonitorPhotometer](CalibrateMonitorPhotometer);  
%Look at the outputted graphs to see which one gives a better fit  
%Then save the corresponding gamma table for later use  
gammaTable = gammaTable1;  
save [MyGammaTable](MyGammaTable) gammaTable  
  
%Then when you're ready to use the gamma table:  
load [MyGammaTable](MyGammaTable)  
[Screen](Screen)('LoadNormalizedGammaTable', win, gammaTable\*[1 1 1]);  
  
  
History:  
Version 1.0: Patrick Mineault (patrick.mineault@gmail.com)  
22.10.2010 mk Switch numeric input from use of input() to use of  
              [GetNumber](GetNumber)(). Restore gamma table after measurement. Make  
              more robust.  
19.08.2012 mk Some cleanup.  
 4.09.2012 mk Use [Screen](Screen)('ColorRange') to adapt number/max of intensity  
              level to given range of framebuffer.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/CalibrateMonitorPhotometer.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/CalibrateMonitorPhotometer.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/CalibrateMonitorPhotometer.m</code>
</div>

