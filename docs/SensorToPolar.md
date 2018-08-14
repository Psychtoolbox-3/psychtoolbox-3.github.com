# [SensorToPolar](SensorToPolar)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

 [pol] = [SensorToPolar](SensorToPolar)(sensor)  
  
 Converts from sensor rectangular coordinates to polar  
 coordinates.  
  
 Polar coordinates are defined as radius, azimuth, and elevation.  
  
 See also [PolarToSensor](PolarToSensor), [SensorToCyl](SensorToCyl), [CylToSensor](CylToSensor).  
  
 9/9/93 jms It didn't work for matrix inputs, because a   
                matrix '^' needed to be a by-element '.^'  
 9/26/93 dhb   Added calData argument.  
 2/6/94  jms   Changed 'polar' to 'pol'  
 2/20/94 jms   Added single argument case to avoid cData  
 4/6/96  dhb    Fixed bug noted by ccc.  Need to use four quadrant  
                arctangent atan2().  
 5/20/98 dhb   Fix little bug, make sure index is not empty.  
 4/5/02  dhb, ly  New calling interface.  
 11/6/06 dhb   Only allow one input argument.  
 2/10/07 dhb   Finish above fix.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/SensorToPolar.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/SensorToPolar.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/SensorToPolar.m</code>
</div>

