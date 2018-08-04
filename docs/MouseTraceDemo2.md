# [MouseTraceDemo2](MouseTraceDemo2)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[MouseTraceDemo2](MouseTraceDemo2)  
  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
Draw a curve with the mouse. Same as [MouseTraceDemo](MouseTraceDemo), but asks  
[Screen](Screen)('[Flip](Flip)') to not clear the framebuffer after flip. This way,  
we don't need to redraw the whole mousetrace in each frame.  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
See also: [PsychDemos](PsychDemos), [MouseTraceDemo](MouseTraceDemo), [GetMouse](GetMouse).  
  
### HISTORY  
  
4/23/05  mk       Derived from [MouseTraceDemoOSX](MouseTraceDemoOSX): Uses new "Don't clear" mode of [Flip](Flip).  
                  to avoid redrawing the whole past mousetrace after each  
                  [Flip](Flip) --\> Faster.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/MouseTraceDemo2.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/MouseTraceDemo2.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/MouseTraceDemo2.m</code>
</div>

