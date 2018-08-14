# [TrolandsToRetIrradiance](TrolandsToRetIrradiance)
##### >[Psychtoolbox](Psychtoolbox)>[PsychRadiometric](PsychRadiometric)

[radianceWattsPerM2Sr, irradianceS] =...  
    [TrolandsToRetIrradiance](TrolandsToRetIrradiance)(relativeSpectrum, relativeSpectrumS, trolands, [photopic], [species], [source])  
  
The assumption underlying this routine is that the relative spectrum of a light  
is available, as well as the retinal illuminance in trolands.  
  
The routine computes the irradiance (watts/um^2-wlinterval) from the relative spectrum  
(relative power, not relative quanta) and the number of trolands.  
  
See Wyszecki and Stiles, 1982, p. 103 for the conversions.  
  
Input variables: relativeSpectrum - the relative power as a function of wavelength.  
                 relativeSpectrumS - the wavelength sampling information for the relativeSpectrum.  
                 trolands - the number of trolands.  
                 photopic - what kind of trolands: 'Photopic' (Default), 'JuddVos', 'Scotopic'.   
                 species - what species determins eye length: 'Human' (Default), 'Monkey'.  
                 source - source for eye length estimate, passed directly to [EyeLength](EyeLength) and inherits its default.  
  
07/18/03  dhb         Wrote it.  
1/26/04   ly, dhb     Fix [JuddVos](JuddVos) path through switch.  
7/16/13   dhb         Comment and code cleaning, minor.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychRadiometric/TrolandsToRetIrradiance.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychRadiometric/TrolandsToRetIrradiance.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychRadiometric/TrolandsToRetIrradiance.m</code>
</div>

