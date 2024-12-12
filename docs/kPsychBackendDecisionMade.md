# [kPsychBackendDecisionMade](kPsychBackendDecisionMade)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

rval = kPsychBackendDecisionMade  
  
This flag can be passed to the optional 'specialFlags' parameter of  
[Screen](Screen)('OpenWindow', ...) or [PsychImaging](PsychImaging)('OpenWindow', ...).  
  
This flag tells [Screen](Screen)('OpenWindow', ...) that a higher level calling  
function of [Screen](Screen)('OpenWindow', ...), e.g., [PsychImaging](PsychImaging)('OpenWindow', ...),  
has made an appropriate, explicit, and intentional choice of the display  
backend that [Screen](Screen)() should use for visual stimulus presentation for the  
given onscreen window, and performed / performs all needed setup, so  
[Screen](Screen)() should not take any initiative on its own, but simply obey  
whatever the calling code has decided for it. Absence of the flag is an  
indicator that [Screen](Screen)('OpenWindow', ...) is called by user written  
experiment scripts directly, which are unaware of specific display  
backend requirements on a given setup, so [Screen](Screen)() may have to make  
backend selection decisions on its own.  
  
In practice, as of November 2024, this flag matters for [Screen](Screen)() running  
on top of macOS on a Apple Silicon Mac with Apples own proprietary gpu  
and display engine on top of Apples proprietary [OpenGL](OpenGL) implementation,  
which requires use of the Vulkan display backend in most cases for proper  
visual stimulus presentation timing and timestamping. If [Screen](Screen)() detects  
it is running on macOS for Apple Silicon and the flag is present, then it  
knows that high-level code like [PsychImaging](PsychImaging)('OpenWindow', ...) has taken  
care of proper setup. Absence of the flag signals that [Screen](Screen) was likely  
called directly by a users legacy experiment script that was unaware of  
the special requirements of the macOS + Apple Silicon platform. In this  
case, [Screen](Screen)('Openwindow') will recursively call [PsychImaging](PsychImaging)('OpenWindow')  
so [PsychImaging](PsychImaging) can then do the needed appropriate backend decisions and  
itself call back into [Screen](Screen)() with the flag set, to perform actual  
proper configuration. It is essentially a backwards compatibility measure  
to make old legacy scripts work transparently on this special snowflake  
platform.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/kPsychBackendDecisionMade.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/kPsychBackendDecisionMade.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/kPsychBackendDecisionMade.m</code>
</div>

