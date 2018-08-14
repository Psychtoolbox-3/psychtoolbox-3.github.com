# [DescribeMonCal](DescribeMonCal)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

same = [DescribeMonCal](DescribeMonCal)(cal,[file],[whichScreen])  
  
Print descriptive information about a calibration   
to the command window or file.  
  
Argument file is a standard Matlab file descriptor,  
see fopen.  If file arg is omitted or empty, printout  
goes to command window.  
  
If argument whichScreen is passed, a description of  
the current hardware is also printed.  In this case,  
returned boolean same indicates whether the calibration  
is consistent with the current hardware.  Boolean  
same is empty if whichScreen is not provided.  
  
8/25/97  dhb, pbe  Wrote it.  
7/3/98   dhb, pbe  Updated for cal.describe.  
12/3/99  dhb, mpr  Fix check for calibration desription field.  
8/1800   dhb       Add whichScreen arg, same return.  
6/29/02  dgp       Use new version of [Screen](Screen) [VideoCard](VideoCard).  
9/23/02  dhb, jms  Fix small bug in way driver is compared, presumably introduced 6/29/02.  
9/29/08  dhb, tyl, ijk Update for OS/X, current computer stuff.  
                   Comparison of computer name skipped, because it seems to vary with login.   
6/24/11  dhb       Dump out gamma fit type and exponents if gamma function was fit with a simple power function.  
5/28/13  dhb       Change output printed format to make it easier to paste into Doku wiki.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/DescribeMonCal.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/DescribeMonCal.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/DescribeMonCal.m</code>
</div>

