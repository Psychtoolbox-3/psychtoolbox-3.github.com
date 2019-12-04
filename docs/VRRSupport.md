# [VRRSupport](VRRSupport)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDocumentation](PsychDocumentation)

[VRRSupport](VRRSupport) - How to set up and use variable refresh rate (VRR) displays.  
  
This text describes how you can take advantage of variable refresh rate  
displays (also known as VRR displays, [DisplayPort](DisplayPort) Adaptive Sync displays,  
HDMI VRR displays, [FreeSync](FreeSync) displays, or G-Sync displays) to improve the  
timing granularity of visual stimulus presentation to smaller time-scales  
than what the video refresh rate of your display allows, e.g., for a 60  
Hz display with a refresh duration of 1/60 second or 16.666 msecs.  
  
Regular fixed rate refresh displays only allow to start presentation of  
a new stimulus image at frame boundaries between video refresh cycles,  
e.g., for a 60 Hz display only at integral multiples of 16.666 msecs. If  
you specify a requested stimulus onset time 'when' in  
[Screen](Screen)('[Flip](Flip)', window, when); then your stimulus image won't show up  
until the start time 't' of the first video refresh cycle after 'when' ie.  
only at time 't' \>= 'when' with t being a multiple of 16.666 msecs. This  
means that interstimulus intervals or stimulus presentation durations are  
limited to multiple of 16.666 msecs. Dynamic animations correspondingly  
can only run at framerates (fps) which are integral divisors of the video  
refresh rate, e.g., for a 60 Hz display at 60 fps, 30 fps, 20 fps, 15 fps,  
12.5 fps, 10 fps, ...  
  
### For some high level overview:  
  
https://en.wikipedia.org/wiki/Variable\_refresh\_rate  
https://en.wikipedia.org/wiki/[FreeSync](FreeSync)  
https://en.wikipedia.org/wiki/Nvidia\_G-Sync  
  
If you have an operating system, a graphics card, video cables and a  
display device which are VRR capable, you can enable a PTB function to  
enable a continuous setting of inter-stimulus-interval (ISI) and the system  
will try its best to conform to your specification. There is still a  
minimum stimulus presentation duration / ISI which is the duration of a  
video refresh cycle of your display, ie. for a 60 Hz display, that would  
be 16.666 msecs. However above 16.666 msecs you can specify ISI or  
stimulus duration with sub-millisecond precision and the system will try  
to obey, ie. almost perfectly match the onset of a requested 'when' time.  
  
This allows for variable ISI's / stimulus durations over a larger range  
of values, and it allows for changing any framerate fps for animations  
that is <= 60 Hz and not locked to the 30, 20, 15, 12.5 ... fps sequence,  
e.g., choose 38.4 fps, 42.2 fps, etc.  
  
So far the theory. In practice things are not always that beautiful.  
  
### But first things first:  
  
On a properly setup hardware + software system, you can request this new  
fine-grained timing mode via a new [PsychImaging](PsychImaging) task, before opening a  
opaque, non-transparent, unoccluded, toplevel, decorationless, fullscreen  
onscreen window:  
  
[PsychImaging](PsychImaging)('PrepareConfiguration');  
[PsychImaging](PsychImaging)('AddTask', 'General', 'UseFineGrainedTiming');  
win = [PsychImaging](PsychImaging)('OpenWindow', screenNumber, ...);  
  
If the hardware and software supports fine-grained timing mode (referred  
to from now on as VRR), the opened fullscreen window will be presented  
with VRR mode and vbl = [Screen](Screen)('[Flip](Flip)', win, when); will try to obey 'when' as  
closely as possible, as long as 'when' for flip is more than one video  
refresh duration away from the time of previous [Flip](Flip), ie. when \>= vbl +  
videorefreshduration. If you request a when smaller than 1 video refresh  
duration away, the system will behave as in the past, it will flip after  
one video refresh duration. How well this mechanism works is highly  
dependent on your operating system, graphics card, display driver and  
display device. Current support for this is pretty basic, only working  
reliably under certain conditions, but support in Psychtoolbox is  
supposed to considerably improve in the future.  
  
  
### Operating system requirements:  
  
Currently only Linux is supported. This has been tested with Ubuntu  
19.10, and should also work with Ubuntu 18.04.3 LTS after some additional  
setup (see below).  
  
### Hardware requirements:  
  
Ideally a modern "[FreeSync](FreeSync) capable" AMD graphics card (GPU). GPU's of the  
Sea Islands gpu family (Graphics Core Next 2nd Generation, cfe.  
https://en.wikipedia.org/wiki/Graphics\_Core\_Next\#second) should work  
after some manual extra setup, GPU's of the Volcanic Islands or Polaris  
series (Graphics Core Next 3rd Generation, cfe.  
https://en.wikipedia.org/wiki/Graphics\_Core\_Next\#third) should work plug  
and play. GPU's of the AMD Vega series or later (Graphics Core Next 5th  
Generation, cfe. https://en.wikipedia.org/wiki/Graphics\_Core\_Next\#fifth)  
should provide improved stability and precision for VRR mode in many cases  
and are therefore recommended if you intend to make heavy use of this new  
feature.  
  
Such "[FreeSync](FreeSync)" gpu's from AMD need to be currently combined with a  
"[FreeSync](FreeSync)" or "[FreeSync](FreeSync)-2" or "[FreeSync](FreeSync)-2 HDR" certified display that is  
connected via [DisplayPort](DisplayPort) cable. [FreeSync](FreeSync)-2 certified displays are  
preferable for better quality and displays which are both "AMD [FreeSync](FreeSync)-2"  
certified and certified as "[NVidia](NVidia) G-Sync compatible" should provide best  
quality. A display with a large refresh rate range (VRR range) of 30 Hz -  
120 Hz (or higher) is recommended. One problem of VRR displays is that  
they may flicker if ISI's are changed too rapidly over a too large range.  
Higher quality displays (probably correlated to purchase prize) are  
supposed to flicker less. Both AMD and [NVidia](NVidia) have testing labs to test  
and certify displays if they meet certain criteria (like little flicker),  
with [FreeSync2](FreeSync2) / [FreeSync2](FreeSync2) HDR having to conform to stricter criteria  
than [FreeSync](FreeSync), and a display that is both [FreeSync2](FreeSync2) certified and G-Sync  
compatible having passed the strictest tests at both AMD and [NVidia](NVidia).  
  
Some interesting technical talk from AMD at XDC 2019 about VRR / [FreeSync](FreeSync)  
under Linux:  
  
https://www.youtube.com/watch?v=ajBf\_b4Aw98  
  
Blurbusters has a list of [FreeSync](FreeSync) monitors here:  
https://www.blurbusters.com/freesync/list-of-freesync-monitors  
  
Another option that may work, but is not expected to work as well, would  
be a [NVidia](NVidia) G-Sync capable graphics card, ie. the Kepler GPU family or  
later cards [(GeForce]((GeForce) GTX 650 Ti Boost GPU or higher) in combination with  
a [NVidia](NVidia) G-Sync capable monitor, or a Pascal GPU family card [(GeForce]((GeForce)  
GTX 1000 series) or later with "G-Sync compatible" monitor, e.g.,  
certain models of [FreeSync2](FreeSync2) monitors.  
  
Blurbusters has a list of G-Sync monitors here:  
https://www.blurbusters.com/gsync/list-of-gsync-monitors  
  
Please note that currently properly "[FreeSync](FreeSync) and G-Sync compatible" monitors  
should work with both AMD and [NVidia](NVidia) GPU's, but G-Sync monitors will only  
work with [NVidia](NVidia) GPU's. Therefore a "[FreeSync2](FreeSync2) and G-Sync compatible"  
monitor would be a better long-term choice which doesn't restrict the  
freedom of choice of graphics card.  
  
  
As operating system, Ubuntu Linux 18.04.3 LTS or later or compatible  
flavors are currently recommended.  
  
For a recommended AMD GPU, you will need a Linux 5.2 kernel or later (the  
later the better!), with xorg-video-amdgpu 19.0 video driver or later.  
  
Ubuntu 19.10 ships suitable components by default (Linux 5.3), and for  
Ubuntu 18.04.3 LTS you can easily upgrade to these components by  
installing the most recent Hardware Enablement Stack (HWE 18.04) plus the  
absolutely latest edge Linux kernel 5.3. In a terminal type:  
  
sudo apt install --install-recommends linux-lowlatency-hwe-18.04-edge xserver-xorg-hwe-18.04  
Then reboot.  
  
After rebooting, run our [XOrgConfCreator](XOrgConfCreator) script, answer the question for  
"advanced features" with (y)es, answer the question about VRR support  
with (y)es, and the other questions to your liking, finish the script to  
save the new config file, then run [XOrgConfSelector](XOrgConfSelector) to select that file as  
new configuration for the following work sessions accordingly, followed by  
a logout and login (or a reboot if you want) to activate the new  
configuration.  
  
For [NVidia](NVidia) GPU's (Not recommended! May or may not work ok) you must  
install a recent enough [NVidia](NVidia) proprietary graphics and display driver,  
use a X-[Screen](Screen) with exactly one G-Sync monitor, and use the  
nvidia-settings GUI app to enable "G-Sync" mode whenever you need it, and  
disable "G-Sync" mode whenever you want to use conventional fixed refresh  
rate presentation again. Psychtoolbox was recently lightly tested with a  
[NVidia](NVidia) [GeForce](GeForce) GTX 1070 + "435 series" drivers at the time of this writing  
(December 2019).  
  
Once you have set up your hardware and OS accordingly, you can add the  
above mentioned 'UseFineGrainedTiming' [PsychImaging](PsychImaging) command to script  
which want to utilize VRR for fine grained timing or controllable  
framerate. With AMD hardware, Psychtoolbox [Screen](Screen)() command will help you  
to diagnose and fix any problems that might prevent VRR from working -  
pointing out missing but required setup steps. With [NVidia](NVidia) hardware,  
[Screen](Screen)() will just mostly assume that it works and is properly setup and  
enabled, simply failing or malfunctioning in interesting ways if  
something is not set up correctly.  
  
An example script for testing and exercising VRR mode can be found as  
[VRRTest](VRRTest).m  
  
As of 4th December 2019, Psychtoolbox 3.0.16 only ships very basic  
support for VRR. It may work reasonably well as long as you choose  
animation framerates that are within the supported VRR range of your  
display, e.g., 30 - 144 Hz or 48 - 144 Hz or such, or  
inter-stimulus-intervals that are within a range corresponding to those  
framerates, e.g., for a 30 - 144 Hz display, from 6.9444 msecs to 33.333  
msecs. For framerates lower than the displays minimum, e.g., below 30  
fps, or ISI's above 33.333 msecs on a 30 Hz display, timing may become  
very unstable and unpredictable! Smooth changes in framerate or small  
incremental changes in ISI may provide more stable results than quick  
changes. These are hardware limitations at the moment. Future versions of  
Psychtoolbox or the Linux operating system are expected to provide vastly  
improved support and stability, but only time will tell... Stay tuned...  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDocumentation/VRRSupport.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDocumentation/VRRSupport.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDocumentation/VRRSupport.m</code>
</div>

