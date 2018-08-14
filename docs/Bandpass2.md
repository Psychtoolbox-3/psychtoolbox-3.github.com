# [Bandpass2](Bandpass2)
##### >[Psychtoolbox](Psychtoolbox)>[PsychSignal](PsychSignal)

w=Bandpass2(size,fLow,fHigh) returns a "window", i.e. a matrix meant to be  
used as a band-pass filter. The matrix size is mxn if "size" is [m,n],  
and nxn if "size" is n. The matrix elements represent gain at each freq,  
uniformly spaced from about -1 to 1 of Nyquist frequency (see  
FREQSPACE). fLow and fHigh are the radial cut-off frequencies on this  
scale. The filter has gain 1 in the frequency interval [fLow,fHigh], and  
gain 0 outside it. Add EPS to create complementary filters that add to  
1, e.g.  
    Bandpass2(n,0,f)+Bandpass2(n,f+eps,1)==Bandpass2(n,0,1)  
For circular symmetry make fHigh<=1. Setting fLow=0 and fHigh=Inf will  
produce an all-pass filter. Here's a typical use, to produce bandpass  
noise:  
    noise=randn(n,n);  
    filter=Bandpass2(n,fLow/fNyquist,fHigh/fNyquist);         
    if any(any(filter~=1)) % skip all-pass filter  
        ft=filter.\*fftshift(fft2(noise));  
        noise=real(ifft2(ifftshift(ft)));  
    end  
Also see [OrientationBandpass](OrientationBandpass), [Bandpass](Bandpass), FREQSPACE.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychSignal/Bandpass2.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychSignal/Bandpass2.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychSignal/Bandpass2.m</code>
</div>

