# [DropCalBits](DropCalBits)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

cal = [DropCalBits](DropCalBits)(cal,whichScreen,[forceBit])  
  
Drops the bitdepth of a calibration file if  
necessary.  Useful for running programs  
transparently on 8 and 10 bit hardware.  
  
If arg forceBits is passed, it is used as  
the current hardware depth.  Otherwise the  
reported [DACBits](DACBits) of whichScreen is used.  
  
This code assumes calibration was done at  
equally spaced levels in RGB settings, as is  
the case with our calibration routines.  May  
not generalize, and I haven't worried about  
the roundoff errors.  Certainly OK for basic  
use.  
  
2/13/05     dhb     Wrote it.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/DropCalBits.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/DropCalBits.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/DropCalBits.m</code>
</div>

