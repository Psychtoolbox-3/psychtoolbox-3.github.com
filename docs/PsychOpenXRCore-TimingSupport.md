# [PsychOpenXRCore('TimingSupport')](PsychOpenXRCore-TimingSupport) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenXRCore](PsychOpenXRCore).{mex*} subfunction

timingSupport = PsychOpenXRCore('TimingSupport' [, openxrPtr]);

Return available level of precise timing and timestamping support for [OpenXR](OpenXR)  
device 'openxrPtr'. If 'openxrPtr' is omitted, a more basic, general assessment  
of the [OpenXR](OpenXR) runtimes capabilities is returned.  
Standard unextended [OpenXR](OpenXR)-1 runtimes, as of March 2025, do not support reliable  
visual onset timestamping, and most tested runtimes don't support reliable onset  
timing either. These runtimes will return zero, hinting at the need for  
multi-threading tricks for bearable precision.  
The open-source Monado runtime does support precise onset timing, and may  
support some better onset timestamping for special customized Linux+Monado  
versions, or future Monado versions. This would be reported by a combination of  
one or more non-zero flags, as described below.  
The returned 'timingSupport' can be the logical OR of one of these flags:  
0 = None. Only use of multi-threading will allow for basic timing and  
    timestamping, but still of limited trustworthiness!  
1 = Some more reliable/trustworthy/accurate timing and timestamping precision  
    available, however, likely with drawbacks like significantly reduced  
    performance.  
  
  


###See also:
[PresentFrame](PsychOpenXRCore-PresentFrame) [PresenterThreadEnable](PsychOpenXRCore-PresenterThreadEnable)
