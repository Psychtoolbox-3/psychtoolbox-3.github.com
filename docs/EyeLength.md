# [EyeLength](EyeLength)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetricData](PsychColorimetricData)

 eyeLengthMM = [EyeLength](EyeLength)(species,source)  
  
 Return the length of the eye in mm.  Length is taken as distance  
 between nodal point and fovea.  For foveal stimuli, this length  
 may be used to convert between degrees of visual angle and mm/um  
 of retina.  Since the nodal point isn't at the center of eye,  
 the same conversion doesn't work for extrafoveal stimuli.  
  
 Supported species:  
        Human (Default), Rhesus, Dog  
  
 Supported sources:  
   [LeGrand](LeGrand) (Human, 16.6832 mm, Default)  
   Rodieck (Human, 16.1 mm)  
   Gulstrand (Human, 17 mm)  
   [PerryCowey](PerryCowey) (Rhesus)  
   Packer (Rhesus)  
   [PennDog](PennDog) (Dog)  
   None  
  
 Passing a numeric value as source returns that value as the  
 estimate, independent of species.  This is a hack that allows  
 some debugging.  
  
 Passing a string that is a number (that is, something that str2num  
 will turn into a number) as the source will cause that number to  
 be returned as the eye length.  This is a bit redundant with the  
 numeric option above.  
  
 Passing None is appropriate as an error check -- if a calculation  
 uses the eye length when none is passed, NaN's will show up in  
 the answer.  
  
 Finally, if you pass a decimal number as a string, this value  
 will be returned.  Useful for passing arbitrary numbers through  
 routines that rely on this function.  
  
 7/15/03  dhb  Wrote it.  
 2/27/13  dhb  Added 17 mm option  
 3/1/13   dhb  Changed '17' to 'Gulstrand'  
          dhb  Added option of passing a number as a string.  
 4/12/13  dhb  Fix bug introduced in previous update, which may have  
               been Matlab version dependent.  
 8/9/13   dhb  A few more comments.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetricData/EyeLength.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetricData/EyeLength.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetricData/EyeLength.m</code>
</div>

