# [BitsPlusPackMonoImage](BitsPlusPackMonoImage)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[BitsPlusToolbox](BitsPlusToolbox)

[theColorImage,reconNewWay,reconOldWay] = [BitsPlusPackMonoImage](BitsPlusPackMonoImage)(theMonoImage)  
  
In Mono++ mode, the Bits++ box uses the red and green  
channels to provide 14-bits per pixel true intensity  
resolution.  The blue channel is set to 0 to let the  
monochromatic image through.   Empirically, we concluded  
that the packing is left adjusted.  That is, the 8 MSB  
of the 14-bit input go into the red channel, and the   
6 LSB get left aligned in the green channel, with  
the remaining two bits set to 0.  
  
This routine packs the bits properly for this function.  
  
11/17/03  dhb, ip   Wrote it.  
8/13/04 dhb     Fix bug, the data were not packed quite right.  
2/26/07   mk      Bugfix for LSB conversion: Added modulo operation.  
3/01/07   mk      Bugfix for MSB conversion: Added floor operation.  
3/04/07   dhb     Modified to return some debugging information and  
                  compare original with recent version.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/BitsPlusToolbox/BitsPlusPackMonoImage.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/BitsPlusToolbox/BitsPlusPackMonoImage.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/BitsPlusToolbox/BitsPlusPackMonoImage.m</code>
</div>

