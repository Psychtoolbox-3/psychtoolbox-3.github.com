# [kPsychNeedRetinaResolution](kPsychNeedRetinaResolution)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

rval = kPsychNeedRetinaResolution  
  
Return a flag that you can pass to the 'imagingmode' parameter of  
[Screen](Screen)('OpenWindow') in order to allow driving a [HiDPI](HiDPI) display, aka  
Retina-Display at its full native resolution.  
  
Without this flag, [Screen](Screen)() will automatically enable its builtin  
panelfitter if it detects the onscreen window being displayed on a Retina  
style display, ie., with a scaled [HiDPI](HiDPI) display mode. The panelfitter  
will expose only a smaller, lower resolution framebuffer to the user and  
upscale user drawn stimuli to full panel resolution at [Screen](Screen)('[Flip](Flip)').  
This is the same behaviour as what OSX normally exposes on a Retina  
panel, because it doesn't cause headaches with various coordinate  
transforms, e.g., mouse or touch input coordinates to display coordinates  
and vice versa and it puts less load on the GPU, therefore performance  
impact is minimized. The downside of this default behaviour is that one  
can't take full advantage of the displays high resolution, apart from  
anti-aliasing.  
  
By default [Screen](Screen)() will use the low-level compatibility mode via panel  
fitting. If usercode explicitely requests use of the panelfitter via  
[PsychImaging](PsychImaging)() tasks, then those requests override [Screen](Screen)'s default  
behaviour.  
  
If usercode doesn't want panelfitting or low-res modes, but the full  
native Retina resolution, it can pass this flag to express its wish.  
Normally the flag is passed by [PsychImaging](PsychImaging) as part of a more convenient  
setup procedure.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/kPsychNeedRetinaResolution.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/kPsychNeedRetinaResolution.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/kPsychNeedRetinaResolution.m</code>
</div>

