# [PhotoreceptorDimensions](PhotoreceptorDimensions)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetricData](PsychColorimetricData)

 dimensions = [PhotoreceptorDimensions](PhotoreceptorDimensions)(receptorTypes,whichDimension,species,source)  
  
 Return estimates of photoreceptor dimensions.  
  
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
 That is to say, for the same source, species, and type, you should get  
 a consistent triplet of numbers.  
  
 Argument whichDimension may take on values:  
    [OSdiam](OSdiam), [ISdiam](ISdiam), [OSlength](OSlength).  
  
 Supported species:  
        Human (Default), [GuineaPig](GuineaPig), Dog  
  
 Supported sources:  
   Rodeick (Default).  
    CVRL (Human Cone OS length)  
   Webvision (Human Cone IS diameter)  
   Hendrickson (Human Rod OS length)  
    [SterlingLab](SterlingLab) [(GuineaPig]((GuineaPig) dimensions).  
   Generic  
   [PennDog](PennDog) (Dog dimensions).  
   None (returns empty for the corresponding value)  
  
 The Generic type returns a single number for all species/type.  
  
 7/11/03  dhb  Wrote it.  
 12/04/07 dhb  Added dog but with placeholder numbers.  
 8/9/13   dhb  Comment clean up, allow 'None' to return empty as the value.  
 8/10/13  dhb  Added Webvision source for IS diameter.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetricData/PhotoreceptorDimensions.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetricData/PhotoreceptorDimensions.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetricData/PhotoreceptorDimensions.m</code>
</div>

