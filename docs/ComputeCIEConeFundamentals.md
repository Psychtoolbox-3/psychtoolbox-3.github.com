# [ComputeCIEConeFundamentals](ComputeCIEConeFundamentals)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetricData](PsychColorimetricData)

[T\_quantalAbsorptionsNormalized,T\_quantalAbsorptions,T\_quantalIsomerizations,adjIndDiffParams,params,staticParams] = ...  
  [ComputeCIEConeFundamentals](ComputeCIEConeFundamentals)(S,fieldSizeDegrees,ageInYears,pupilDiameterMM,[lambdaMax],[whichNomogram],[[LserWeight](LserWeight)], ...  
  [DORODS],[rodAxialDensity],[fractionPigmentBleached],[indDiffParams])  
  
Function to compute normalized cone quantal sensitivities  
from underlying pieces, as specified in CIE 170-1:2006.  
  
IMPORTANT: This routine returns quantal sensitivities.  You  
may want energy sensitivities.  In that case, use [EnergyToQuanta](EnergyToQuanta) to convert  
  T\_energy = [EnergyToQuanta](EnergyToQuanta)(S,T\_quantal')'  
and then renormalize.  (You call [EnergyToQuanta](EnergyToQuanta) because you're converting  
sensitivities, which go the opposite direction from spectra.)  
The routine also returns two quantal sensitivity functions. The first gives  
the probability that a photon will be absorbed.  The second is the probability  
that the photon will cause a photopigment isomerization.  It is the latter  
that is what you want to compute isomerization rates from retinal illuminance.  
See note at the end of function [FillInPhotoreceptors](FillInPhotoreceptors) for some information about  
convention.  In particular, this routine takes pre-retinal absorption into  
account in its computation of probability of absorptions and isomerizations,  
so that the relevant retinal illuminant is one computed without accounting for  
those factors.  This routine does not account for light attenuation due to  
the pupil, however.  The only use of pupil size here is becuase of its  
slight effect on lens density as accounted for in the CIE standard.  
  
This standard allows customizing the fundamentals for  
field size, observer age, and pupil size in mm.  
  
To get the Stockman-Sharpe/CIE 2-deg fundamentals, use  
  fieldSizeDegrees = 2;  
  ageInYears = 32;  
  pupilDiameterMM = 3;  
and don't pass the rest of the arguments.  
  
To get the Stockman-Sharpe/CIE 10-deg fundamentals, use  
  fieldSizeDegrees = 10;  
  ageInYears = 32;  
  pupilDiameterMM = 3;  
and don't pass the rest of the arguments.  
  
Although this routine will compute something over any wavelength  
range, I'd (DHB) recommend not going lower than 390 or above about 780 without  
thinking hard about how various pieces were extrapolated out of the range  
that they are specified in the standard.  Indeed, the lens optical  
density measurements only go down to 400 nm and these are extropolated  
to go below 400.  
  
This routine will compute from tabulated absorbance or absorbance based on a nomogram, where  
whichNomogram can be any source understood by the routine [PhotopigmentNomogram](PhotopigmentNomogram).  To obtain  
the nomogram behavior, pass a lambdaMax vector. You can then also optionally pass a nomogram  
source (default: [StockmanSharpe)](StockmanSharpe)).  This option (using shifted nomograms) is not part of the  
CIE standard. See NOTE below for another way to handle individual differences   
  
The nominal values of lambdaMax to fit the CIE 2-degree fundamentals with the  
Stockman-Sharpe nomogram are 558.9, 530.3, and 420.7 nm for the LMS cones respectively.  
These in fact do a reasonable job of reconstructing the CIE 2-degree fundamentals, although  
there are small deviations from what you get if you simply read in the tabulated cone  
absorbances.  Thus starting with these as nominal values and shifting is one way to  
produce fundamentals tailored to observers with different known photopigments.  
  
If you pass lambaMax and its length is 4, then first two values are treated as  
the peak wavelengths of the ser/ala variants of the L cone pigment, and these  
are then weighted according to [LserWeight](LserWeight) and (1-[LserWeight)](LserWeight)).  The default  
for [LserWeight](LserWeight) is 0.56.  After travelling it for a distance to try to get better  
agreement between the nomogram based fundamentals and the tabulated fundamentals  
I (DHB) gave up and decided that using a single lambdaMax is as good as anything  
else I could come up with. If you are interested, see [FitConeFundamentalsTest](FitConeFundamentalsTest).  
  
NOTE 1: When we first implemented the CIE standard, adding this shifting feature  
seemed like a good idea to allow exploration of individual differences in photopigments.  
But, with 0 shift, none of the nomograms exactly reproduce the tabulated photopigment absorbance  
spectral sensitivities, and this is not so good.  We are phasing out our  
use of this feature in favor of simply shifting the tabulated  
photopigment absorbances, and indeed in favor of adopting the method  
published by Asano, Fairchild, & Blonde (2016), PLOS One, doi: 10.1371/journal.pone.0145671  
to tailor the CIE fundamentals to individual observers.  This is done by  
passing the argument indDiffParams, which is a structure as follows.  
  indDiffParams.dlens - deviation in % from CIE computed peak lens density  
  indDiffParams.dmac -  deviation in % from CIE peak macular pigment density  
  indDiffParams.dphotopigment - vector of deviations in % from CIE photopigment peak density.  
  indDiffParams.lambdaMaxShift - vector of values (in nm) to shift lambda max of each photopigment absorbance by.    
  indDiffParams.shiftType - 'linear' (default) or 'log'. 'linear' gets the Asano et al. behavior  
  
You also can shift the absorbances along a wavenumber axis after you have  
obtained them.  To do this, pass argument lambdaMaxShift with the same  
number of entries as the number of absorbances that are used.  
  
The adjIndDiffParams output is a struct which is populated by [ComputeRawConeFundamentals](ComputeRawConeFundamentals).  
It contains the actual parameter values for the parameters adjusted using the indDiffParams   
input. It contains the following fields:  
   adjIndDiffParams.mac - the adjusted macular pigment transmittance as a function of wavelength  
                          as calculated in line 151 of [ComputeRawConeFundamentals](ComputeRawConeFundamentals).  
   adjIndDiffParams.lens - the adjusted lens transmittance as a function of wavelength as calculated  
                           in line 41 of [ComputeRawConeFundamentals](ComputeRawConeFundamentals).  
   adjIndDiffParams.dphotopigment - 3-vector of the adjusted photopigment axial density for  
                                    L, M and S cones (in that order), as calculated in lines  
                                    200-202 of [ComputeRawConeFundamentals](ComputeRawConeFundamentals); or rods, as calculated  
                                    in line 216 of [ComputeRawConeFundamentals](ComputeRawConeFundamentals) if params.DORODS is true.  
   adjIndDiffParams.absorbance - Photopigment absorbance as given in line 188 of [ComputeRawConeFundamentals](ComputeRawConeFundamentals)  
   adjIndDiffParams.absorptance - Photopigment absorptance as given in line 230 of [ComputeRawConeFundamentals](ComputeRawConeFundamentals)  
  
For both adjIndDiffParams.mac and adjIndDiffParams.lens, the wavelength  
spacing is the same as in the S input variable of this function.  
  
The params and staticParams outputs are the argument strucutures that  
were passed to [ComputeRawConeFundamentals](ComputeRawConeFundamentals) by this routine to do the work.  
These can be useful if you'd like, say, to susequently use  
[ComputeRawConeFundamentals](ComputeRawConeFundamentals) to produce estimates for (e.g.) melanopsin or  
the rods, where you keep everything else as consistent as possible to  
what this routine does. Note that this is all a bit klugy for historical  
reasons, as there is redundancy between what you can/might do with  
adjIndDiffParams and with these two return outputs. In particular, these  
two return outputs would let you call [ComputeRawConeFundamentals](ComputeRawConeFundamentals) and get  
adjIndDiffParams directly from there.  
  
This function also has an option to compute rod spectral sensitivities, using  
the pre-retinal values that come from the CIE standard.  Set DORODS to true on  
call.  You then need to explicitly pass a single lambdaMax value.  You can  
also pass an optional rodAxialDensity value.  If you don't pass that, the  
routine uses the 'Alpern' estimate for 'Human'/'Rod' embodied in routine  
[PhotopigmentAxialDensity](PhotopigmentAxialDensity).  The default nomogram for the rod spectral  
absorbance is 'StockmanSharpe', but you can override with any of the  
others available in routine [PhotopigmentNomogram](PhotopigmentNomogram).  Use of this requires  
good choices for lambdaMax, rodAxialDensity, and the nomogram.  We are  
working on identifying those values more precisely.  
  
Finally, you can adjust the returned spectral sensitivities to account for  
the possibility that some of the pigment in the cones is bleached.  Pass  
a column vector with same length as number of spectral sensitivities beingt  
computed.  You need to estimate the fraction elsewhere.  
  
Relevant to individual differences, S & S (2000) estimate the wavelength difference  
between the ser/ala variants to be be 2.7 nm (ser longer).  
  
NOTE 2.  The CIE standard is specified for field sizes between 1 and 10  
degrees.  Our code will extrapolate using the given formulae to larger  
field sizes without complaining.  We think this is reasonable; see  
[CIEConeFundamentalsFieldSizeTest](CIEConeFundamentalsFieldSizeTest) and its header comments, but be aware  
that you have sailed into little charted territory if you do this.  
  
See also: [ComputeRawConeFundamentals](ComputeRawConeFundamentals), [CIEConeFundamentalsTest](CIEConeFundamentalsTest), [CIEConeFundamentalsFieldSizeTest](CIEConeFundamentalsFieldSizeTest),   
[FitConeFundamentalsTest](FitConeFundamentalsTest), [FitConeFundamentalsWithNomogram](FitConeFundamentalsWithNomogram), [StockmanSharpeNomogram](StockmanSharpeNomogram),  
[ComputePhotopigmentBleaching](ComputePhotopigmentBleaching).  
  
8/13/11  dhb  Wrote it.  
8/14/11  dhb  Clean up a little.  
12/16/12 dhb, ms  Add rod option.  
08/10/13 dhb  Test for consistency between what's returned by [FillInPhotoreceptors](FillInPhotoreceptors) and  
              what's returned by [ComputeRawConeFundamentals](ComputeRawConeFundamentals).  
05/24/14 dhb  Add fractionPigmentBleached optional arg.  
05/26/14 dhb  Comment improvements.  
02/08/16 dhb, ms  Add lambdaMaxShift argument.  
         ms   Don't do two way check when lambdaMax is shifted.  
02/24/16 dhb, ms  Started to implement Asano et al. individual difference model  
3/30/17  ms   Added output argument returning adjusted ind differences  
8/1/17   dhb, ms  Added return of params and staticParams.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetricData/ComputeCIEConeFundamentals.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetricData/ComputeCIEConeFundamentals.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetricData/ComputeCIEConeFundamentals.m</code>
</div>

