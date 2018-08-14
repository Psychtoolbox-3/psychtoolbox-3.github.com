# [Bandpass](Bandpass)
##### >[Psychtoolbox](Psychtoolbox)>[PsychSignal](PsychSignal)

w=[Bandpass](Bandpass)(n,fLow,fHigh) returns a 1xn window, a band-pass filter. The  
elements represent gain at each freq, uniformly spaced from -1 to 1 of  
Nyquist frequency. fLow and fHigh are the positive cut-off frequencies  
on this scale. We pass frequencies in the interval [fLow,fHigh). The  
asymmetric use of bounds guarantees that complementary filters will add  
to 1: [Bandpass](Bandpass)(n,0,f)+[Bandpass](Bandpass)(n,f,Inf)==ones(1,n). If fHigh is omitted  
it's assumed to be Inf. Also see Bandpass2.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychSignal/Bandpass.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychSignal/Bandpass.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychSignal/Bandpass.m</code>
</div>

