# [PhotonAbsorptionRate](PhotonAbsorptionRate)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)

 [photonAbsorptionRate] =...  
        [PhotonAbsorptionRate](PhotonAbsorptionRate) (irradianceInQuanta, irradianceS, absorptanceSpectra, absorptanceSpectraS, collectingDiameter)  
  
 Compute photons being absorbed per photoreceptor per sec, given the spectrum incident on the  
 photoreceptor array.  We typically take the collecting area of a photoreceptor to be the inner segement  
 diameter.  
  
 Spatial units for this routine are um, which are convenient for photoreceptor calculations.  Be sure  
 to convert your incident spectrum to these units.  The retinal irradiance is passed in quantal units.  Note  
 that routines [EnergyToQuanta](EnergyToQuanta) and [QuantaToEnergy](QuantaToEnergy) are available for your converting pleasure.  
  
 Can handle multiple photoreceptor types.  Put each absopbtance spectrum in a row of matrix  
 absorptanceSpectra, put corresponding collecting diameters in column vector collectingDiameter.  
  
 Units:   
   photonAbsorptionRate: quanta/sec/photorecptor  
   irradianceInQuanta: quanta/um^2-sec-wlinterval  
   absorptanceSpectra: probability an incident quantum will be absorbed.  
   collectingDiameter (um^2)  
  
 05/06/03   lyin Wrote it  
 06/12/03   lyin Change the way variable being passed.  
 06/26/03  dhb  Change computation of area to pi\*r^2 rather than pi\*d^2!  
 06/26/03  dhb  Change to expect absorptanceSpectra and collectingDiameter in rows.  
 7/08/03   dhb  Cosmetic.  
 7/09/03   dhb  Take input in quantal units.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/PhotonAbsorptionRate.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/PhotonAbsorptionRate.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/PhotonAbsorptionRate.m</code>
</div>

