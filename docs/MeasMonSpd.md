# [MeasMonSpd](MeasMonSpd)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

 [spd,S] = [MeasMonSpd](MeasMonSpd)(window, settings, [S], [syncMode], [whichMeterType], [bitsppClut])  
  
 Measure the Spd of a series of monitor settings.  
  
 This routine is specific to go with [CalibrateMon](CalibrateMon),  
 as it depends on the action of [SetMon](SetMon).   
  
 If whichMeterType is passed and set to 0, then the routine  
 returns random spectra.  This is useful for testing when  
 you don't have a meter.  
  
 Other valid types:  
  1 - Use PR650 (default)  
  2 - Use CVI  
  
 10/26/93  dhb    Wrote it based on ccc code.  
 11/12/93  dhb    Modified to use [SetColor](SetColor).  
 8/11/94    dhb   Sync mode.  
 8/15/94   dhb    Sync mode as argument, allow S to be [] for default.  
 4/12/97   dhb   New toolbox compatibility, take window and bits args.  
 8/26/97   dhb   pbe Add noMeterAvail arg.  
 4/7/99    dhb   Add argument for radius board. Compact default arg code.  
 8/14/00   dhb   Call to CMETER('SetParams') conditional on OS9.  
 8/20/00   dhb   Remove bits arg to [SetColor](SetColor).  
 8/21/00   dhb   Remove dependence on RADIUS flag.  This is now handled inside of [SetColor](SetColor).  
            dhb   Change calling conventions to remove unused args.  
 9/14/00   dhb   Sync mode is not actually used.  Arg still passed for backwards compat.  
 2/27/02   dhb   Change noMeterAvail to whichMeterType.  
 8/19/12   mk    Rewrite g\_usebitspp path to use PTB imaging pipeline for higher robustness   
                 and to support more display devices.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/MeasMonSpd.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/MeasMonSpd.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/MeasMonSpd.m</code>
</div>

