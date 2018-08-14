# [OrientationBandpass](OrientationBandpass)
##### >[Psychtoolbox](Psychtoolbox)>[PsychSignal](PsychSignal)

w=orientationBandpass(size,oLow,oHigh) returns a "window", i.e. a matrix  
meant to be used as a band-pass filter. The matrix size is mxn if "size"  
is [m,n], and nxn if "size" is n. The matrix elements represent gain at  
each freq, uniformly spaced from about -1 to 1 of Nyquist frequency (see  
FREQSPACE). oLow and oHigh are the cut-off orientations in degrees (e.g.  
0 to 360). The interval will include all angles from oLow up to but not  
including orientation oHigh. oHigh must be in the range [oLow,oLow+180].  
Setting oHigh=oLow+180 will produce an all-pass filter. The filter has  
gain 1 in the orientation intervals [oLow,oHigh) and  
[oLow+180,oHigh+180), and gain 0 outside those intervals. Note the  
asymmetry: oLow is included and oHigh is excluded. Frequency zero, which  
has no orientation, is always passed with gain 1. The logical OR  
of filters for several contiguous bands, e.g. 0 to 20 and 20 to 40 will  
equal the filter for the composite band, 0 to 40. oLow can be any finite  
value, but only the range 0 to 180 is unique. o+180 is equivalent to o.  
Here's a typical use, to produce orientation-bandpass noise:  
    noise=randn(n,n);  
    filter=[OrientationBandpass](OrientationBandpass)(n,oLow,oHigh);         
    if any(any(filter~=1)) % skip all-pass filter  
        ft=filter.\*fftshift(fft2(noise));  
        noise=real(ifft2(ifftshift(ft)));  
    end  
Also see Bandpass2, [Bandpass](Bandpass), FREQSPACE.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychSignal/OrientationBandpass.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychSignal/OrientationBandpass.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychSignal/OrientationBandpass.m</code>
</div>

