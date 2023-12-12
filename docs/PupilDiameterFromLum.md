# [PupilDiameterFromLum](PupilDiameterFromLum)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetricData](PsychColorimetricData)

[diam,area,trolands] = [PupilDiameterFromLum](PupilDiameterFromLum)(lum [, source])  
  
Compute pupil diameter and area from photomic luminance.  
Diameter is in mm, area in mm^2.  
Luminance is in cd/m2.  
Also returns photopic trolands.  
  
Source (string):  
  [PokornySmith](PokornySmith): (default)  
      Formula is Eq. 1 from: Pokorny and Smith, "How much light  
      reaches the retina", Colour Vision Deficiences XIII (C.  
      Cavonius, ed.), pp. 491-511.  
  
  [DeGrootGebhard](DeGrootGebhard):  
      Formula is De Groot and Gebhard's from  
      Eq. 2(2.4.5) of Wyszecki and Stiles,  
      2cd edition (page 106).  
  
  [MoonSpencer](MoonSpencer):  
      Formula is Moon and Spencer's from  
      Eq. 1(2.4.5) of Wyszecki and Stiles,  
      2cd edition (page 106).  
  
Notes:  
  a) The calculations of the [DeGroot](DeGroot)/Gebhard formula do not seem to agree with the  
      same calculations as expressed in Figure 2(2.4.5) on the same page of W+S. One would  
      need to go back to the original literature to sort out what is going on.  
  
  b) In terms of the different methods, Joel Pokorny (1999, personal communication) says:  
     The average pupil diameter/luminance functions in the literature vary enormously.  
     This can be seen in the figures in  
  
     Moon, P. and D. E. Spencer (1944). "On the Stiles-Crawford Effect."  
     Journal of the Optical Society of America 34: 319-329.  
  
     and  
  
     de Groot, S. G. and J. W. Gebhard (1952). "Pupil size as determined  
     by adapting luminance." Journal of the Optical Society of America  
     42: 492-495.  
  
     For example, the Reeves (1918, "The visibility of radiation."  
     Transactions of the Illuminating Engineering Society 13: 101-109)  
     pupil diameter function is displaced roughly 1.5 log units higher on  
     the luminance axis than Crawford's (1936, "The dependence of pupil  
     size upon external light stimulus under static and variable conditions."  
     Proceedings of the Royal Society B (London) 121(B): 376-395) average data.  
  
     Both Moon and Spenser & [DeGroot](DeGroot) and Gebhard sought functions which were  
     compromises between existing data sets.  LeGrand's function shows good  
     correspondence with the Reeves' data.  These three functions nominally  
     describe pupil behavior for binocular view of large fields.  In vision  
     science we most frequently use fields of limited extent and often use  
     monocular view.  These stimulus manipulations lead to larger pupils than  
     the binocular large field condition. Thus it made sense to me to use the  
     [LeGrand](LeGrand) function. As is mentioned in "How much light..." pupil size  
     varies for all sorts of reasons and any estimate should be viewed as  
     having a large tolerance.  
  
4/2/99  dhb  Wrote it.  
5/8/99  dhb  Consolidated different methods.  
7/8/03  dhb  Accept strings without dashes.  
12/4/07 dhb  Added dog case, with a place holder number of 8 mm.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetricData/PupilDiameterFromLum.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetricData/PupilDiameterFromLum.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetricData/PupilDiameterFromLum.m</code>
</div>

