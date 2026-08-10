# [srLMSconelog](srLMSconelog)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetricData](PsychColorimetricData)>[StockmanRiderNomogram](StockmanRiderNomogram)>[srFunctions](srFunctions)

[LMSout](LMSout) = srLMSconelog(nm, Lshift, Mshift, Sshift, loglin)  
  
This returns the fits to the Stockman-Sharp LMS absorbances.  Paper  
Figure 1 and Table 1.  
  
Pass 'lin' as last argument to get linear absorbance, otherwise returns log10  
absorbance.  
  
Return is matrix with four columns, first is wavelength in nm, then L, M, and S  
absorbances (or log10 absorbances) in that order.  
  
Adopted by Claude AI and DHB from Stockman-Rider paper and Python code.  See  
[StockmanRiderDemo](StockmanRiderDemo) for more info.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetricData/StockmanRiderNomogram/srFunctions/srLMSconelog.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetricData/StockmanRiderNomogram/srFunctions/srLMSconelog.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetricData/StockmanRiderNomogram/srFunctions/srLMSconelog.m</code>
</div>

