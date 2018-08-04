# [DotOffset](DotOffset)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

[dx,dy,dz,a,e] = [DotOffset](DotOffset)(r,d,ndots)  
computes DX, DY and DZ offsets to move a point in a direction specified  
by R. Output for NDOTS offsets are computed independently. Only azimuthal  
direction can be specified or both azimuth and elevation, in which case a  
number of different randomizations are possible (see third form of R  
below). D is the distance by with dots are to be offset and should be  
either scalar or have length NDOTS.  
  
all angles are in degrees  
  
Outputs A and E are the azimuth and elevation angles used by [DotOffset](DotOffset)  
for each offset. If only one output is requested, a 3xNDOTS output matrix  
with the x, y and z offset on the respective rows is returned.  
  
R can take four forms:  
- scalar: direction (in degrees) of offset in azimuth (0 is translation  
  in z direction, 90 in x direction towards 3 o'clock), used for all  
  outputted offsets  
- vector with length NDOTS: direction (in degrees) of offset in azimuth  
  specified in input for each outputted offset  
- a matrix of size [NDOTSx2](NDOTSx2): direction (in degrees) of offset in azimuth  
  (first column) and elevation (second column) specified in input for  
  each outputted offset  
- 2x2 cellmatrix: the first row specifies azimuth direction, the second  
  the elevation angle. A number of different inputs for the azimuth and  
  the elevation row are possible and lead to the following outputs:  
  - first column is a vector with length NDOTS: direction (in degrees) of  
    offset specified for each outputted offset. Second column is ignored.  
  - first column is a vector with length other than NDOTS: for each  
    outputted offset, offset direction is randomly selected from the  
    values in the vector (see 'help RandSel'). Second column is ignored.  
  - scalar in the first column and [NaN](NaN) in the second column (e.g.  
    {45,[NaN](NaN);67,[NaN](NaN)} or {45,90;67,[NaN](NaN)}). Direction specified in the first  
    column is used for all outputted offsets.  
  - scalar in the first and second column (both non-[NaN)](NaN)) (e.g.  
    {45,90;67,[NaN](NaN)} or {45,90;0,360}). For each offset, a random direction  
    is chosen within the specified limits. Angles are randomly chosen  
    between lower (1st column) and upper (2nd column) boundaries (see  
    'help RandLim').  
  
Function can also be used to compute points laying on (part of) a [Circle](Circle)  
or sphere with radius D:  
[X,~,Z] = [DotOffset](DotOffset)(linspace(0,360),D,100);  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/DotOffset.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/DotOffset.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/DotOffset.m</code>
</div>

