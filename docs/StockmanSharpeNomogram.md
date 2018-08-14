# [StockmanSharpeNomogram](StockmanSharpeNomogram)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetricData](PsychColorimetricData)

T\_absorbance = [StockmanSharpeNomogram](StockmanSharpeNomogram)(S,lambdaMax)  
  
Compute normalized absorbance according to the  
nomogram provided by Stockman and Sharpe:  
  See Stockman & Sharpe (2000), p. 1730 or http://www.cvrl.org/.  
  
The lmax values of the fitted templates that best fits   
to the Stockman and Sharpe (2000) S-, M- and L-cone photopigment  
spectra are 420.7, 530.3 and 558.9 nm for the  
S-, M- and L-cones, respectively;  
  
The result is in quantal units, in the sense that to compute  
absorptions you want to incident spectra in quanta.  
To get sensitivity in energy units, apply [EnergyToQuanta](EnergyToQuanta)()  
(not [QuantaToEnergy](QuantaToEnergy), because here you are converting sensitivity  
rather than spectra.)  
  
Argument lambdaMax may be a column vector of wavelengths.  
  
This routine converts the log10 absorbance computed by the nomogram  
formulae into absorbance.  
  
Note from DHB. By eye, this nomogram gives a good fit to the log10 LMS pigment  
absorbance spectra when you plot them on a log scale over 8 log units,  
as in Stockman & Sharpe (2000), Figure 12.  The fit does not look quite so  
good in my hands on a linear scale or an expanded log scale.  
I think the deviations occur in part because the tabulated  
photopigment absorbances for the L are a mixture of the ser/ala   
pigments, and the nomogram was developed in part on the basis of fitting these  
as if they corresponded to a single lambda max value. It may also be that  
the template was built by minimizing the error in log sensitivity, and this  
would more heavily weight the long wavelength limbs of the pigments, where  
the linear sensitivity is essentially zero.  In any case, though, if you  
are working in the land of the CIE 170-1:2006 fundamentals, this is the  
probably the best current nomogram to use.  
  
See [ComputeCIEConeFundamentals](ComputeCIEConeFundamentals), [CIEConeFundamentalsTest](CIEConeFundamentalsTest),  
[FitConeFundamentalsFromNomogram](FitConeFundamentalsFromNomogram), [FitConeFundamentalsTest](FitConeFundamentalsTest)  
  
5/8/99  dhb  Started writing it.  
10/27/99    dhb  Added error return to prevent premature use of this routine.  
7/18/03   dhb  Finished it off.  
8/13/11   dhb  Improved comments.  Double check polynomial coefficients.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetricData/StockmanSharpeNomogram.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetricData/StockmanSharpeNomogram.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetricData/StockmanSharpeNomogram.m</code>
</div>

