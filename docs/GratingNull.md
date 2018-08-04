# [GratingNull](GratingNull)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

foreWeight=[GratingNull](GratingNull)(device,message,forePart,blendPeriodPix,[foreColor],[backColor],[viewingDistanceM],[dpi])  
[GratingNull](GratingNull) obtains visual matches that allow calibration of a video monitor's gamma.  
Finds the "matchColor" (dac triplet) that produces a visual match to a two-color optical mixture  
of foreColor and backColor of which the proportion forePart is the   
"foreground" color. The matchColor is a weighted average, with the weight adjusted by the viewer,  
of foreColor and backColor.   
matchColor=foreWeight\*foreColor+(1-foreWeight)\*backColor;  
The program returns foreWeight.  
The blend grating is very fine (normally 60 c/deg).  
The spatial periodicity of the grating for the visual match is  
optimal (i.e. 3 c/deg) at the specified viewing distance.  
If dpi is omitted it is assumed to be 66.  
If viewing distance is omitted it is assumed to be the distance at which  
the mixture spatial frequency is 60 c/deg.  
  
Denis Pelli 6/1/97  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/GratingNull.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/GratingNull.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/GratingNull.m</code>
</div>

