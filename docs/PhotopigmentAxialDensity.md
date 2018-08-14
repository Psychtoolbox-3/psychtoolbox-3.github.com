# [PhotopigmentAxialDensity](PhotopigmentAxialDensity)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetricData](PsychColorimetricData)

 densities = [PhotopigmentAxialDensity](PhotopigmentAxialDensity)(receptorTypes,[species],[source],[fieldSizeDegrees])  
  
 Return estimates of photopigment axial density, sometimes called peak  
 absorbance.  
  
 Allowable receptor types depend on species and source, but the general  
 list is:  
    [SCone](SCone), [MCone](MCone), [LCone](LCone), [FovealSCone](FovealSCone), [FovealMCone](FovealMCone), [FovealLCone](FovealLCone), Rod.  
  
 The type argument may be a single string or a cell array of strings.  If it  
 is an array, a column vector of values is returned.  
  
 The foveal version of cone types is sensible only for primates.  Not all  
 estimate sources support all receptor types.  
  
 Note that the following three numbers are overdetermined: photopigment  
 specific density (sd), photopigment axial density (ad), and outer segment  
 length osl.  In particular, ad = sd\*osl.  Depending on the measurement  
 method, different sources provide different pairs of these numbers.  
 We have attempted to enforce this consistency in the set of routines  
 [PhotopigmentSpecificDensity](PhotopigmentSpecificDensity), [PhotopigmentAxialDensity](PhotopigmentAxialDensity), and [PhotoreceptorDimensions](PhotoreceptorDimensions).  
 That is to say, for the same source, species, and cone type, you should get  
 a consistent triplet of numbers.  
  
 Supported species:  
        Human (Default).  
  
 Supported sources:  
        Rodieck (Human) (Default).  
        [StockmanSharpe](StockmanSharpe) (Human).  
        CIE (Human).  
        Tsujimura (Human; melanopsin-containing [RGCs)](RGCs))  
  
 The CIE method takes a field size argument.  This  
 overrides the specified foveal or not part of the  
 cone string.  If the field type is not passed and  
 the method is CIE, it is set to 10-degrees for [SCone](SCone), [MCone](MCone),  
 and [LcCne](LcCne), and to 2-degrees for [FovealSCone](FovealSCone), [FovealMCone](FovealMCone), and  
 [FovealLCone](FovealLCone).  
  
 The fieldSizeDegrees argument is ignored for sources other than  
 CIE.  
  
 7/11/03  dhb  Wrote it.  
 8/12/11  dhb  Added CIE source, and allow passing of fieldSizeDegrees.  
 4/20/12  dhb  Add Tsujimura's estimate of melanopsin optical density in human.  
 12/16/12 dhb, ms Add Alpern's rod estimates from CVRL table.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetricData/PhotopigmentAxialDensity.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetricData/PhotopigmentAxialDensity.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetricData/PhotopigmentAxialDensity.m</code>
</div>

