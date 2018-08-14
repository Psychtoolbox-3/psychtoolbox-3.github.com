# [OptiCAL](OptiCAL)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)

[OptiCAL](OptiCAL) - Psychtoolbox [IOPort](IOPort) interface to the CRS [OptiCAL](OptiCAL) luminance  
          meter device  
  
Usage:  
  \>\> handle = [OptiCAL](OptiCAL)('Open', port)  
  \>\> lum = [OptiCAL](OptiCAL)('Read', handle)  
  \>\> [OptiCAL](OptiCAL)('[Close](Close)', handle)  
  \>\> [OptiCAL](OptiCAL)('CloseAll')  
  
Inputs:  
  command   - string 'Open', 'Read', '[Close](Close)', or 'CloseAll'  
  port      - string device (e.g. '/dev/ttyS0')  
  handle    - double handle  
  
Outputs:  
  handle    - double handle  
  lum       - luminance in cd/m^2  
  
Note:  
  Requires read and write access to the serial port (Ubuntu: add user to  
  the dialout group). Not yet tested with USB-to-serial adapters.  
  
References:  
  [1] Haenel, V. (2010). Pure python interface to CRS [OptiCAL](OptiCAL). Retrieved  
      October 18, 2012 from https://github.com/esc/pyoptical.  
  [2] Cambridge Research Systems. (1995). [OptiCAL](OptiCAL) user's guide v4.02.  
      Retrieved October 18, 2012 from  
    http://support.crsltd.com/ics/support/[DLRedirect](DLRedirect).asp?fileID=63194  
  [3] Cambridge Research Systems. (2009). [OptiCAL](OptiCAL) user's guide v4.02  
      errata. Retrieved October 18, 2012 from  
    http://support.crsltd.com/ics/support/[DLRedirect](DLRedirect).asp?fileID=63194  
  
Author: Andreas Widmann, University of Leipzig, 2012  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/OptiCAL.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/OptiCAL.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/OptiCAL.m</code>
</div>

