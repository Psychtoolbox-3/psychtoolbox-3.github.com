# [XYZToLjg](XYZToLjg)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)

Ljg = [XYZToLjg](XYZToLjg)(XYZ)  
  
Convert XYZ (10 degree) to OSA Ljg coordinates.  Formulae  
derived from [MacAdam](MacAdam) (1974, JOSA, 64, pp. 1691-1702).  Note that  
MacAdam's formulae are in error for the case Y0 less than 30.  The  
correct formulae may be deduced by examing Semelroth's (JOSA, 1970, 16,  
1685-1689) Eqn. 3, from which MacAdam's incomplete Eqn. 1 is derived.  
  
Note that the above problem is propogated into the formulae  
reported in Wyszecki and Stiles, 2cd edition.  In addition, W+S  
reverse the formulae for G and J and leave out the final  
transformation from scriptL to L.  
  
Finally the formualae published in Brainard (2003, Color appearance and  
color difference specification. In The Science of Color, 2cd edition,  
S. K. Shevell (ed.), Optical Society of America, Washington D.C., 191-216),  
which correct for the above errors, introduce a new mistake: The coefficient  
on B^1/3 for the j coordinate in Eq. 5-2 should be -9.7, rather than the  
the +9.7 that is published.  
  
The output of this routine was verified against the tabulated  
values in W+S, Table I(6.6.4).  These are republished from  
[MacAdam](MacAdam) (1978, JOSA, 68, 121-130).  See [[OSAUCSTest](OSAUCSTest)][(OSAUCSTest)]((OSAUCSTest)).  
  
3/27/01  dhb  Wrote it.  
7/14/10  dhb  Added comment that the formulae in my chapter have a typo.  
              The code here is and was correct.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/XYZToLjg.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/XYZToLjg.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/XYZToLjg.m</code>
</div>

