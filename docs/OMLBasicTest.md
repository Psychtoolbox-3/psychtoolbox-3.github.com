# [OMLBasicTest](OMLBasicTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[OMLBasicTest](OMLBasicTest)([screenid=max][, querystresstest = 0]) - Test basic correctness of [OpenML](OpenML) timestamping.  
  
Performs a sequence of 300 flips, acquires timestamps of  
[Flip](Flip) completion according to OML\_sync\_control timestamping,  
as well as a post-swap [GetSecs](GetSecs) timestamp and a timestamp of  
the last vblank. If [OpenML](OpenML) timestamping works correctly, then  
all three timestamps should be almost identical, ie., the vblank  
and flip timestamps should be identical, the [GetSecs](GetSecs) timestamp  
only minimally later than the flip timestamp, depending on  
system scheduling noise and load.  
  
If the timestamps (minus a few outliers) disagree, then  
something is likely broken in [OpenML](OpenML) flip timestamping.  
  
if the optional parameter 'querystresstest' is set to a  
value \> 0 then a stress test of vblank count and timestamp  
queries is run for 'querystresstest' seconds and potential  
trouble is reported.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/OMLBasicTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/OMLBasicTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/OMLBasicTest.m</code>
</div>

