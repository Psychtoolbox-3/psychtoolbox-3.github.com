# [CalibrateFitGamma](CalibrateFitGamma)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

cal = [CalibrateFitGamma](CalibrateFitGamma)(cal,[nInputLevels])  
  
Fit the gamma function to the calibration measurements.  Options for field  
cal.describe.gamma.fitType are:  
   simplePower  
   crtLinear  
   crtPolyLinear  
   crtGamma  
   crtSumPow  
   betacdf  
   sigmoid  
   weibull  
  
Underlying fit routine is [FitGamma](FitGamma) for functional forms originally supported,  
and these rely on the optimization toolbox.  
  
Newer functions (e.g, crtSumPow, betacdf) use the curvefit toolbox and that's just  
done locally in this routine.  Much less cumbersome.  
  
NOTE (5/27/10, dhb): crtSumPow does not currently appear to normalize the  
measurements to unity, while the older methods do (in [FitDeviceGamma)](FitDeviceGamma)).  
This may be a bug, but since we're not currently using crtSumPow I'm not  
going to look into it in detail right now.  
  
See also [PsychGamma](PsychGamma).  
  
3/26/02  dhb  Pulled out of [CalibrateMonDrvr](CalibrateMonDrvr).  
11/14/06 dhb  Define nInputLevels and pass to underlying fit routine.  
07/22/07 dhb  Add simplePower fitType.  
08/02/07 dhb  Optional pass of nInputLevels.  
         dhb  Don't allow a long string of zeros at the start.  
         dhb  Reduce redundant code for higher order terms by pulling out of switch  
08/03/07 dhb  Debug.  Add call to [MakeMonotonic](MakeMonotonic) for first three components.  
11/19/09 dhb  Added crtSumPow option, coded to [0-1] world and using curve fit toolbox.  
3/07/10  dhb  Cosmetic to make m-lint happier, including some "|" -\> "||"  
3/07/10  dhb  Added crtLinear option.  
         dhb  contrasthThresh and fitBreakThresh values only set if not already in struct.  
         dhb  Call [MakeGammaMonotonic](MakeGammaMonotonic) rather than [MakeMonotonic](MakeMonotonic) where appropriate.  
         dhb  Use linear interpolation for higher order linear model weights, rather than  
              a polynomial.  I now think that ringing is worse than not smoothing enough.  
3/08/10  dhb  Update list of options in comment above.  
5/26/10  dhb  Allow gamma input values to be either a single column or a matrix with same number of columns as devices.  
6/5/10   dhb  Extend fix above to higher order terms in the gamma fit.  
         dhb  Fix or supress MATLAB lint warnings.  
         dhb  Add betacdf fit option, which seems to provide a flexible sigmoidally shaped fit.  
6/8/10   dhb, ar Make sure to set cal.gammaInput in options that use curvefit toolbox method.  
              Add a call to [MakeGammaMonotonic](MakeGammaMonotonic) around input values for higher order linmod fit.  
6/1010   dhb  Fix higher order fit in case where there are multiple gamma input columns.  Blew this the other day.  
6/11/10  dhb  Allow passing of weighting parameter as part of cal.describe.gamma structure.  Change functional form of betacdf  
              to include wrapped power functions.  
4/12/11  dhb  For simplePower option, return vector of exponents in cal.describe.exponents.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/CalibrateFitGamma.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/CalibrateFitGamma.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/CalibrateFitGamma.m</code>
</div>

