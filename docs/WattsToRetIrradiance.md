# [WattsToRetIrradiance](WattsToRetIrradiance)
##### >[Psychtoolbox](Psychtoolbox)>[PsychRadiometric](PsychRadiometric)

 [irradiance, irradianceS] =...  
        [WattsToRetIrradiance](WattsToRetIrradiance)(relativeSpectrum, relativeSpectrumS, readingInWatts, [radiometer])  
  
 The assumption underlying this routine is that the relative spectrum of a light  
 is available, as well as the total power of the light passing through an aperture  
 of known size.  This is the situation in the apparatus we use in Sterling's lab.  
    The routine computes the irradiance (watts/um^2-wlinterval) from the relative spectrum  
 (relative power, not relative quanta) and a measurement of the total power in watts,  
 given the radiometer properties specified.   
  
 Radiometers do not typically have an ideal flat spectral response, and the actual  
 spectral response is often provided as part of the instrument calibration.  In addition,  
 the instruments are typically calibrated to provide an accurate reading for one  
 particular reference spectrum, which is also specified.  This routine is set up  
 to use this calibration information together with the known relative spectrum to  
 provide a correct result.  The radiometer properties may be passed in the radiometer  
 structure.  A default structure is set up that describes the radiometer used in  
 the Sterling lab.  This structure also describes the collecting area of the measurement  
 configuration.  
  
 This routine could be easily modified to deal with a photometric head.   
  
 Input variables: relativeSpectrum is the relative power as a function of wavelength.  
                  relativeSpectrumS is the wavelength sampling information for the relativeSpectrum.  
                                   readingInWatts is the total power measured.  
                  radiometer is a structure describing the radiometer. (default = Sterling Lab's IL1400A).  
  
 04/29/03   lyin Wrote it with advice from DHB  
 05/06/03   lyin Put wls into variable: lightSource  
 05/06/03   lyin Correction for wavelength sampling interval  
 06/12/03   lyin Change the way, variable being passed  
 6/26/03   dhb  Change some names, also compute power per wavelength interval, not per nm.  
 6/30/03   dhb  Lots more changes.  
 7/08/03   dhb  Monochromatic ref spectrum default, as per manual.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychRadiometric/WattsToRetIrradiance.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychRadiometric/WattsToRetIrradiance.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychRadiometric/WattsToRetIrradiance.m</code>
</div>

