# [StockmanRiderNomogram](StockmanRiderNomogram)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetricData](PsychColorimetricData)>[StockmanRiderNomogram](StockmanRiderNomogram)

T\_absorbance = [StockmanRiderNomogram](StockmanRiderNomogram)(S, lambdaMax)  
  
Compute normalized absorbance using the Stockman-Rider Fourier polynomial  
nomogram, as described in:  
  Stockman, A. & Rider, A. T. (2023). Formulae for generating standard and  
  individual human cone spectral sensitivities. Color Research and Application,  
  48, 818-840.  
  
The appropriate L, M, or S cone Fourier template is selected for each  
lambdaMax value based on which cone type's range it falls in, using split  
points halfway between the nominal template peaks:  
  S template peak: 416.9 nm  
  M template peak: 529.8 nm  
  L template peak: 551.9 nm  
  S/M split:       473.35 nm  (midpoint of 416.9 and 529.8)  
  M/L split:       540.85 nm  (midpoint of 529.8 and 551.9)  
  
If lambdaMax is a 3-element column vector it is assumed to be [L; M; S]  
in that order. An error is thrown if the values do not fall in the  
expected ranges, since that likely indicates a calling error.  
  
The result is in quantal units (absorbance in the sense used by PTB  
nomograms). The output is normalized to a peak of 1 for each row,  
if wavelength spacing is <= 1 nm.  
  
To get sensitivity in energy units, apply [EnergyToQuanta](EnergyToQuanta)().  
  
Various utility routines from Stockman-Rider are include, with sr  
prepended to all of their names to avoid namespace collision with  
PTB routines that do similar things.  
  
Good lambda max values (L, M, S): 551.9, 529.8, 416.9 nm.  
These are the nominal template peaks built into the Stockman-Rider  
nomogram itself and reproduce the standard CIE photopigment absorbances  
well.  
  
See also: [PhotopigmentNomogram](PhotopigmentNomogram), srLconelog, srMconelog, srSconelog,  
          srLMSconelog, srDemo  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetricData/StockmanRiderNomogram/StockmanRiderNomogram.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetricData/StockmanRiderNomogram/StockmanRiderNomogram.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetricData/StockmanRiderNomogram/StockmanRiderNomogram.m</code>
</div>

