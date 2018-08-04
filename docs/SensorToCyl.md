# [SensorToCyl](SensorToCyl)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

cyl = [SensorToCyl](SensorToCyl)(sensor)  
  
Convert from sensor to cylindrical coordinates.  
  
This is designed for use with the CIE Lxx color  
spaces, so it's assumed that the first input  
coordinate is luminance and this is taken directly  
as height.  The next two input coordiantes are  
assumed to be chromaticity coords.  
  
The returned cylindrical system is luminance, radius, angle,  
with radius and angle computed in the passed chromaticity plane.  
  
Note that angle is returned in radians.  
  
We use the conventions of the CIE Lxx color spaces  
for angle.  
  
See also [CylToSensor](CylToSensor), [SensorToPolar](SensorToPolar), [PolarToSensor](PolarToSensor).  
  
10/17/93  dhb   Wrote it by converting CAP C code.  
2/20/94   jms   Added single argument case to avoid cData.  
4/5/02    dhb, ly  New calling interface.  
11/06/06  dhb   No longer allow two passed args.  
1/3/10    dhb   Elaborated comments a little.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/SensorToCyl.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/SensorToCyl.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/SensorToCyl.m</code>
</div>

