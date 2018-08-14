# [HIDIntervalTest](HIDIntervalTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[HIDIntervalTest](HIDIntervalTest) -- Illustrate human interface device sampling interval.  
  
The routine queries first the keyboard, later on the mouse buttons for  
changes in key press state or mouse button press state, recording the  
timestamp of any change. This is done first for 10 seconds on the  
keyboard, then for 10 seconds on the mouse.  
  
Time difference between consecutive "state-change" samples is computed  
and plotted as a histogram.  
  
At least on USB-HID devices - keyboards and mice connected via USB - you  
should see some characteristic distribution in the histograms. You'll see  
that clusters of samples are spaced in even time intervals, typically  
separated by multiples of 8-10 msecs. This indicates that operating  
systems only update mouse and keyboard state at a sampling frequency of  
about 100 - 125 Hz and therefore measured mouse or keyboard response  
times will be quantized with at least that granularity.  
  
There are more complex interactions, especially inside keyboards, that  
will increase latency and uncertainty about the timing of key presses  
beyond the 8 msecs granularity of the USB-HID scan cycle.  
  
Be very cautious when using normal keyboards for reaction time  
measurements, or better use a dedicated response box.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/HIDIntervalTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/HIDIntervalTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/HIDIntervalTest.m</code>
</div>

