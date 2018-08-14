# [HDRViewer](HDRViewer)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[BrightSideDisplay](BrightSideDisplay)

[HDRViewer](HDRViewer)([imfilepattern][, dummymode][, scalefactor]) -- Load and show high  
dynamic range images on the [BrightSide](BrightSide) Technologies High Dynamic Range  
display device.  
  
The viewer allows to cycle through a sequence of images in the given  
folder, matching the given filename pattern. It allows to adjust the  
intensity online, as well as to zoom into regions of the image.  
  
'imfilepattern' - Filename search pattern of the HDR images to load,  
e.g., 'myimages\*.hdr' would load all images starting with 'myimages' and  
ending with extension '.hdr'.   
  
'dummymode' - If set to 1 we only run in emulation mode without use of  
the HDR device or [BrightSide](BrightSide) core library.  
  
### Control keys:  
  
You can cycle through all images by pressing the space-bar. You can change  
image intensity scaling by pressing the cursor up- and down-keys. You can  
exit the viewer by pressing [ESCape](ESCape). By pressing the 'q' key, you can  
toggle between float precision HDR and 256 level 8 bit quantized output.  
  
Zoom mode:  
Pressing the left mouse button will enable zoom mode. Dragging the mouse  
while the button is depressed allows to change the region which should be  
zoomed. Releasing the mouse button will show the selected region zoomed  
up to fullscreen. A single mouse click will reset to the full image.  
  
Btw. you can find lot's of nice free HDR images by Googling on the  
internet!  
  
This is an extension of [SimpleHDRDemo](SimpleHDRDemo).m, see that file for basic usage of  
HDR displays with Psychtoolbox.  
  
History:  
Written 2006 by Mario Kleiner - MPI for Biological Cybernetics, Tuebingen, Germany  
and Oguz Ahmet Akyuz - Department of Computer Science, University of Central Florida.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/BrightSideDisplay/HDRViewer.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/BrightSideDisplay/HDRViewer.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/BrightSideDisplay/HDRViewer.m</code>
</div>

