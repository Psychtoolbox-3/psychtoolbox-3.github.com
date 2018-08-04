# [PosterBatchAnalyzeTimestamps](PosterBatchAnalyzeTimestamps)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[PosterBatchAnalyzeTimestamps](PosterBatchAnalyzeTimestamps)  
  
Iterate over all timingtest result files ('Res\_flipconfig\_xxxx') which  
contain valid high precision flip timestamps, either based on  
'p'hotodiode measurements or 'd'atapixx measurements.  
  
measMethod must be 'p' or 'd' for photo-diode measurement via [RTBox](RTBox), or  
Datapixx measurement.  
  
The recursive search for matching result files starts at /includes the  
current working directory.  
  
The script iterates over each matching file and adds all collected raw  
and high precision timestamps to a large array of timestamps. At the end  
of iteration, the pooled dataset is analyzed for mean, max and min  
deviation between [Flip](Flip) onset timestamps and measured timestamps. The  
total range of deviation and the standard deviation from the mean (==  
timestamp variability) is computed as well. This is done on the raw  
timestamps and high precision timestamps. End results are printed and  
scatterplots of all individual samples are shown.  
  
This script was used to compute the values of the "Stimulus timestamp  
precision" result table of Mario Kleiner's ECVP-2010 poster "Visual  
stimulus timing precision in Psychtoolbox-3: Tests, pitfalls &  
solutions". The same data is used in the corresponding table of his [PhD](PhD)  
Dissertation.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/PosterBatchAnalyzeTimestamps.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/PosterBatchAnalyzeTimestamps.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/PosterBatchAnalyzeTimestamps.m</code>
</div>

