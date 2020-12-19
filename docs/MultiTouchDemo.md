# [MultiTouchDemo](MultiTouchDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[MultiTouchDemo](MultiTouchDemo)([dev][, screenId=max][, verbose=0]) - A advanced demo for multi-touch touchscreens.  
  
Run it. Pressing the [ESCape](ESCape) key will stop it.  
  
Touch the screen and watch the nice colorful happy blobs  
sprinkle to life :)  
  
The demo will try to use the first available touchscreen, or if  
there isn't any touchscreen, the first available touchpad. You  
can also select a specific touch device by passing in its 'dev'  
device handle. Use of touchpads usually needs special configuration.  
See "help [TouchInput](TouchInput)" for more info.  
  
You can select a specific screen to display on - usually the screenId  
of the touch screen display surface - with the optional 'screenId' parameter,  
or it will select the default maximum screenId if omitted.  
  
If you set 'verbose' to 1, then all the available info about each  
touch point will be displayed close to the touch point. As drawing  
so much text is very slow, the demo will only update touchpoints  
very slowly!  
  
The demo not only tracks and display touches and their location, as  
well as their timing. It also uses info about the shape of the contact,  
visualizing this as aspect ratio of the drawn rectangle. It tries to  
get info about the contacts orientation and draws accordingly. It tries  
to get (or derive) info about touch pressure and modulates the brightness  
of the rectangle accordingly. One property not used, but available would  
be distance for fingers or tools hovering over a touch surface, if that  
surface provides that info.  
  
This demo currently only works on Linux + X11 display system,  
not on Linux + Wayland, not on other operating systems.  
  
For background info on capabilities and setup see "help [TouchInput](TouchInput)".  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/MultiTouchDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/MultiTouchDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/MultiTouchDemo.m</code>
</div>

