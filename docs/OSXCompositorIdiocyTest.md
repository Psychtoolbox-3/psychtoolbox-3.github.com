# [OSXCompositorIdiocyTest](OSXCompositorIdiocyTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[OSXCompositorIdiocyTest](OSXCompositorIdiocyTest) - Test for potential OSX compositor brokeness.  
  
### Usage:  
  
[OSXCompositorIdiocyTest](OSXCompositorIdiocyTest)([testScreen=max][, distractorScreen]);  
  
This test tests if the OSX desktop compositor is potentially  
interfering with [Screen](Screen)('[Flip](Flip)') on a fullscreen window on a  
display, especially in dual-display, dual-window configurations.  
  
The test performs 300 black-white flips on 'testScreen'.  
Then it optionally opens a fullscreen window on 'distractorScreen',  
and repeats the 300 black-white flips on 'testScreen'. The 2nd  
window does nothing.  
  
What you should observe is black-white flicker in both "PASS I"  
and "PASS II". If you observe flicker, that's a good sign, although  
not a guarantee that everything is fine, timing-wise, on your system.  
  
If you observe no flicker in "PASS I" then your systems flip  
implementation is totally broken and not recommended for any  
timing-sensitive visual stimulation.  
  
If you observe flicker in "PASS I", but not in "PASS II" - when  
the distractor window is open on 'distractorScreen', then your  
system is possibly fine for single-display stimulation, but  
broken for dual-display (e.g., binocular, stereoscopic, stereoMode 10)  
stimulation wrt. presentation timing and timestamping.  
  
What this test does is it alternates between the two buffers  
of the doublebuffered window. One buffer is filled black, the  
other white.  
- If [Screen](Screen)('[Flip](Flip)') is executed by your operating system  
and graphics hardware via so called page-flipping, then you should  
observe flicker and the timing and timestamping of visual stimuli  
should be research grade.  
  
- However, there is still some chance of observing flicker even  
if page-flipping isn't used, but the desktop compositor is active  
in a triple-buffer configuration. Therefore a successfull run of  
this test is not 100% proof that you are safe from timing woes.  
  
If you don't observe flickering then this means a desktop compositor  
or copy-swapping is active and the presentation timing and timestamps  
are not to be trusted!  
  
So far we know that at least OSX 10.8.5 with AMD graphics hardware  
works properly for single-window / single-display visual stimulation,  
but \*not\* in dual-window stimulation!  
There is some indication that this dual-display stimulation OSX bug  
can be possibly resolved or worked around via the applying the  
[Screen](Screen)('[Preference](Preference)','ConserveVRAM', x); setting with x = 16384 or  
x = 8192. Results look promising but are not 100% certain.  
  
So far we also know that at least OSX 10.9 - 10.10 with [NVidia](NVidia)  
graphics hardware do not work properly at all in any configuration!  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/OSXCompositorIdiocyTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/OSXCompositorIdiocyTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/OSXCompositorIdiocyTest.m</code>
</div>

