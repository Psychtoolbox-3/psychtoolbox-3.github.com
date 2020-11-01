# [HDRDebugViewer](HDRDebugViewer)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[HDRDebugViewer](HDRDebugViewer)([imfilepattern][, scalefactor=autoselect][gpudebug=1]) -- Load and show high  
dynamic range images on a compatible HDR display setup.  
  
See "help [PsychHDR](PsychHDR)" for system requirements and setup instructions for HDR  
display. See "help [HDRRead](HDRRead)" for supported HDR image file formats, ie. the  
formats that [HDRRead](HDRRead)() can load.  
  
The viewer allows to cycle through a sequence of images in the given  
folder, matching the given filename pattern. It allows to adjust the  
intensity online, as well as to zoom into regions of the image. A simple  
"color picker" displays the RGB color values in units of nits under the cursor  
position.  
  
'imfilepattern' - Filename search pattern of the HDR images to load,  
e.g., 'myimages\*.hdr' would load all images in the current folder that  
are starting with 'myimages' and ending with extension '.hdr'.  
  
If 'imfilepattern' is omitted or empty then image files bundled with  
Psychtoolbox and Matlab are loaded. Additionally the viewer will offer to  
download some freely useable sample files from the MPI for Informatics in  
Saarbruecken, Germany. Another bunch of [OpenEXR](OpenEXR) sample images can be found  
on the [OpenEXR](OpenEXR) website under:  
  
https://www.openexr.com/downloads.html  
  
  
### Limitations:  
  
The viewers formulas for converting pixel color values from the units in the  
image file to the required linear unit in Nits are not neccessarily correct, as  
there seems to be not much agreement about what the units in the image files are  
supposed to reflect. In case of Radiance files (.hdr) we multiply by some fixed  
number, when we should actually convert from units of Radiance to units of  
Luminance. For the [OpenEXR](OpenEXR) format and others, we just use values as they are,  
assuming they are already in Nits. This seems to be the case for some, but not all,  
sample images.  
  
Similarly the formula for computing frame average light level and max content  
light level may or may not be 100% according to spec. At least they give reasonable  
results...  
  
### Control keys:  
  
You can cycle through all images by pressing the space-bar. You can change  
image intensity scaling by pressing the cursor up- and down-keys. You can  
exit the viewer by pressing [ESCape](ESCape). By pressing the 'q' key, you can  
toggle between float precision HDR and 256 level 8 bit quantized output.  
  
### Zoom mode:  
  
Pressing the left mouse button will enable zoom mode. Dragging the mouse  
while the button is depressed allows to change the region which should be  
zoomed. Releasing the mouse button will show the selected region zoomed  
up to fullscreen. A single mouse click will reset to the full image.  
  
  
This is an extension of [SimpleHDRDemo](SimpleHDRDemo).m, see that file for the most basic usage  
of HDR displays with Psychtoolbox.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/HDRDebugViewer.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/HDRDebugViewer.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/HDRDebugViewer.m</code>
</div>

