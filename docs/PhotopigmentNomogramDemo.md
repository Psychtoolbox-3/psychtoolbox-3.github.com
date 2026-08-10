# [PhotopigmentNomogramDemo](PhotopigmentNomogramDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[PhotopigmentNomogramDemo](PhotopigmentNomogramDemo)  
  
Compares photopigment nomograms against the CIE/Stockman-Sharpe tabulated  
photopigment absorbance spectra (T\_log10coneabsorbance\_ss), which serve as  
the fixed reference baseline.  Each nomogram gets its own figure: thick black  
lines show the CIE tabulated absorbance; the nomogram is overlaid in color.  
Rows are L, M, S cones; left column is linear absorbance, right column is  
log absorbance.  
  
### Lambda max values and nomogram comparison notes:  
  
Each nomogram uses its own canonical lambda max values. Because the  
nomograms have different shapes, they require different lambda max  
parameters to approximate the same underlying spectrum.  
  
For the L cone, the CIE absorbance peaks at ~551.9 nm (per the Fourier  
polynomial fit of Stockman & Rider 2023, Table 1). The [StockmanRider](StockmanRider) nomogram  
reproduces this accurately at lambda max = 551.9 (zero shift). The  
[StockmanSharpe](StockmanSharpe) nomogram, which uses a polynomial approximation, requires  
lambda max = 558.9 to best match the same CIE L-cone absorbance — a ~7 nm  
discrepancy. This does not mean the two nomograms represent different spectra;  
both target the same CIE L-cone, but [StockmanSharpe](StockmanSharpe) is less accurate on a  
linear scale (see note in [StockmanSharpeNomogram](StockmanSharpeNomogram).m). The visual difference  
between the two curves reflects that accuracy difference.  
  
For the S cone the discrepancy between nomograms is larger because  
[StockmanSharpe](StockmanSharpe) uses a single polynomial shape for all three cone types (just  
shifted in log wavelength), while [StockmanRider](StockmanRider) uses separately fitted Fourier  
polynomials for L, M, and S. The CIE S-cone absorbance has a different shape  
from L and M on a log-wavelength scale, so [StockmanSharpe](StockmanSharpe) fits it less well.  
  
The [CarrollNeitz](CarrollNeitz) nomogram has a different history and was not developed  
to match the CIE cone fundamentals. It provides a worse approximation to  
to these, at least for the lambda max values we clocked in, which come  
from a Netiz and Neitz review as referenced in the [CarrollNeitzNomogram](CarrollNeitzNomogram)  
function.  
  
History:  
  2026-04-10  dhb  Wrote it.  
  2026-04-10  dhb  Restructured: CIE tabulated data as fixed black reference,  
                   one figure per nomogram.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/PhotopigmentNomogramDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/PhotopigmentNomogramDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/PhotopigmentNomogramDemo.m</code>
</div>

