# [ComputePhotopigmentBleaching](ComputePhotopigmentBleaching)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)

[fractionBleached] = [ComputePhtopigmentBleaching](ComputePhtopigmentBleaching)(irradiance,[receptorType],[units],[source],[initialFraction],[timeUnits])  
  
Compute fraction of photopigment bleached, given irradiance of light  
reaching the eye.  
  
There are two distinct uses, controlled by the value of initialFraction.  
  
Usage 1 - If initialFraction is not passed or is empty, the steady state  
fraction of pigment bleached is returned for each irradiance in the  
passed input irradiance.  
  
Usage 2 - If initialFraction is passed as a scalar, this is taken as the  
time zero fraction bleached, and inputirradiance is taken to be the time  
variying irradiance, with fractionBleached the time varying fraction  
bleached.  
  
When time varying signals are handled, the unit of time is as specified  
by the timeunits argument (default, msec).  
  
As far as I can tell, the fundemantal measurements of the half-bleach  
constant for human cones were made by Rushton and Henry (1968, Vision Research,  
8, 617-631). This fact I learned from CVRL  
(http://www.cvrl.org/database/text/intros/introbleaches.htm).  
  
I am pretty sure that the Rushton and Henry measurements were made for  
560 nm light, and they give (see their Figure 2) a half-bleach constant  
of 4.3 log10 trolands (20,000 td). This number is also given in Boynton  
and Kaiser, Human Color Vision, 2nd edition, pp 211 and following.  This  
is the number you get here if you specify 'Boynton' as the source for the  
cone bleaching data.  
  
Elsewhere in the same paper, Rushton and Henry use another method and  
come up with 29167 td) as the half-bleach constant.  You can get this  
number by specifying 'RushtonHenryAlt' as the source for the cone  
constants.  If you use isomemerizations here, the constant is scaled up  
from the one derived above by the ratio (29167/(10^4.3)).  
  
It's probably fine to compute bleaching for L and M cones given retinal  
illuminance in trolands, given that these are effects that matter over  
log10 units.  But trolands are not going to help much for the S-cones.  
According to CVRL there aren't good measurements for the half-bleaching  
constant for S cones because putting enough short-wavelength light onto  
the retina to bleach the S cones is not good for the eyes.  
  
None-the-less, it seems nice to have this routine written so that it will  
return a number if you give it irradiance either in trolands or in  
isomerizations/cone-sec.  For 560 nm light and the CIE 10 deg  
fundamentals, I compute that 1 td is 137 isomerizations/cone-sec for L  
cones and 110 isomerizations/cone-sec for M cones.  Take the weighted  
average value of (2\*L + 1\*M)/3 = 128 and multiply by (10.^4.3) to get a  
half-bleach constant in isomerizations/cone-sec of  2.55e+06 (6.4 log10  
isomerizations/cone-sec). [Computations done 6/2/14 using  
[IsomerizationsInEyeDemo](IsomerizationsInEyeDemo) and setting the fundamentals to 'CIE10deg' and  
wavelength to 560 nm by hand in the code.  These are for the 'Boynton'  
source.]  
  
[ASIDE: I used 10 deg fundamentals to compute the bleaching constant  
expressed in terms of isomerizations, because I figure that Rushton's  
measurements are based on a fairly large field.  Because the macular  
pigment absorbs a fair amount of light, this matters.  If I compute  
instead with 2-deg fundamentals, I get that 1 td is 23.7 L cone  
isomerizations/cone-sec and 19.5 M cone isomerizations/cone-sec.   These  
two numbers are ballpark consistent with Rodiek page 475 who gives 18.3  
and 15.9 for a monochromatic 540 [THz](THz) light (555 nm)].  
  
This paper  
  Burkhardt, D. A. "Light adaptation and photopigment  
  bleaching in cone photoreceptors in situ in the retina  
  of the turtle." Journal of Neuroscience 14.3 (1994):  
  1091-1105.  
provides a half bleach constant for turtle cones of 5.57 expressed  
in log10 R\*/um2/sec, which could with some work be converted to  
isomerizations/cone/sec for turtle cones. But it's not  
clear you want to use that number unless you are studying turtle.  
  
This routine will do the computation either on the basis of input in  
trolands or input in isomerization/cone-sec, using the appropirate  
constant as above.  Note that the computation of isomerizations takes  
into account lens and macular pigment, while the troland value is the  
straight troland value.  A second advantage of using units of  
isomerizations/cone-sec is that you can compute this for other regions of  
the visual field and presumably the numbers will be about right.  You can  
also compute for S-cones on the assumption that the half-bleach constant  
is the same for S-cones as for L- and M- cones.  
  
As far as I can tell, the computations and analysis of bleaching do not  
take into account changes in isomerization rate that occur because of  
change in spectral sensitivity of cones with bleaching.  That is, the  
measurements are simply of steady state pigment density and are modeled  
with a formula that assumes monochromatic light (see treatment in  
Boynton).  
  
irradiance    -- retinal irradiance specified as determined by units. If  
                 initialFraction is empty, this is a single number and  
                 steady state bleaching fraction is returned.  If  
                 initialFraction is a number, then this is a time series  
                 of irradiance versus time, and fraction bleached for the  
                 same times is returned.  
  
receptortype  
  'cones'     -- computations for cones. [Default]  
  'rods'      -- computations for rods.  
  
units         -- units of irradiance  
  'trolands'     input irradiance trolands.  Note that the computation  
                 only makes sense for L and M cones if this is the input.  
                 This is photopic trolands if receptor type is 'cones'.  
                 [Default].  It is scotopic trolands if receptor type is  
                 rods.  
  'isomerizations'  nominal isomerization rate in  
                 isomerizations/cone-sec, comptued taking into account  
                 pre-retinal absorption as well as nominal cone axial  
                 density.  But not taking into account any pigment  
                 bleaching.  
  
source        -- source of underlying data  
  'Boynton'      Boynton and Kaiser, Human Color Vision, 2nd edition,  
                 pp. 211 and following. See intro text above. [Default]  
  'RushtonHenryAlt' - Rushton and Henry's other half-bleach constant.  
                 Only available for 'cones'.  
  'WyszeckiStiles' - Wyszecki and Stiles (1982) give parameters on page  
  
initialFraction -- fraction of input bleached at time zero. If  
                empty, steady state fraction bleached is  
                returned. Default is empty.  
  
timeUnits     -- units for time step on input and output  
  'sec'          seconds  
  'tenth'        tenths of seconds  
  'hundredth'    hundredths of seconds  
  'msec'         millseconds [Default]  
  'tenthmsec'     tenths of milliseconds  
  
05/23/14 dhb  Wrote it.  
05/26/14 dhb  Clean up.  
06/02/14 dhb  Take isomerizations number based on 2:1 L:M assumed ratio.  
12/18/18 dhb  Modify header comments for possibility of passing time  
              varying signal.  This breaks old usage that allowed  
              computing steady state bleaching for a set of vector  
              inputs, but I think that is OK.  
08/19/19 dhb  Added some information about Burkhardt (1994) to header  
              comment, and inserted a stub to use that information if  
              someone does the work to put the number from it into the  
              right units.  
         dhb  Reorganized some code relative to source switch statement. Because  
              there was only one case this didn't matter, but now I think it  
              is right if more cases.  
01/09/21 dhb  Finish off adding kinetics.  
01/12/21 dhb  Add in the alternate Rushton & Henry half-bleach constant  
              for cones.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/ComputePhotopigmentBleaching.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/ComputePhotopigmentBleaching.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/ComputePhotopigmentBleaching.m</code>
</div>

