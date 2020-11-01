# [HDRViewer](HDRViewer)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[HDRViewer](HDRViewer)([imfilepattern][, highprecision=0][, windowed=0][, scalefactor=autoselect][, gpudebug=0])  
Load and show high dynamic range images on a compatible HDR display setup.  
  
See "help [PsychHDR](PsychHDR)" for system requirements and setup instructions for HDR  
display. See "help [HDRRead](HDRRead)" for supported HDR image file formats, ie. the  
formats that [HDRRead](HDRRead)() can load, and possible caveats.  
  
The viewer allows to cycle through a sequence of images in the given  
folder, matching the given filename pattern. It allows to adjust the  
intensity online, as well as to zoom into regions of the image. A simple  
"color picker" displays the RGB color values in units of nits under the  
cursor position.  
  
### Input arguments, all optional:  
  
'imfilepattern' - Filename search pattern of the HDR images to load,  
e.g., 'myimages\*.hdr' would load all images in the current folder that  
are starting with 'myimages' and ending with extension '.hdr'.  
  
If 'imfilepattern' is omitted or empty then image files bundled with  
Psychtoolbox and Matlab are loaded. Additionally the viewer will offer to  
download some freely useable sample files from the MPI for Informatics in  
Saarbruecken, Germany. Another bunch of [OpenEXR](OpenEXR) sample images can be found  
on the [OpenEXR](OpenEXR) website under:  
  
https://www.openexr.com/downloads.html  
  
'highprecision' If set to 1, request floating point 16 fp16 display  
output, instead of the default 10 bpc fixed point output of HDR-10.  
  
'windowed' If set to 1 and running on MS-Windows, create a non-fullscreen  
window to test windowed HDR mode. This is not yet supported on Linux, and  
sometimes buggy and/or underwhelming on Windows-10, so may not work at  
all or not correctly due to Windows-10 or gpu display driver limitations.  
  
'scalefactor' If set, use this factor to scale color intensity values of  
images during drawing into the framebuffer. Otherwise use a heuristic  
which sometimes gives not so great results.  
  
'gpudebug' If set to 1 will collect additional low-level info useful for  
debugging of Vulkan driver bugs, and print it to the console window. This  
will have performance impact!  
  
  
### Caveats:  
  
The viewers formula for converting pixel color values from the units in the  
image file to the required linear unit in Nits are as good as they get atm.  
  
There seems to be not much agreement about what the units in the image  
files are supposed to reflect. In case of Radiance files (.hdr) we  
multiply by some fixed number 179, motivated by some comments in the  
Radiance file format spec, when we should actually convert from units of  
Radiance to units of Luminance, but that's the best one can do in the  
general case. Similar, we use encoded color gamut if available, but  
mostly that seems not to be the case, so we apply some hard-coded "BT-709  
alike" gamut as recommended by the spec.  
  
For the [OpenEXR](OpenEXR) format and others, we use the sampleToNits and [ColorGamut](ColorGamut)  
information if provided by the image file. This should give correct  
results, but at least as my image sample sets and the wisdom of the  
internet go, many (most?) freely available images actually lack  
definition of color gamut and conversion factor, so we simply have to  
assume BT-709 gamut and a unit conversion factor. This seems to be the  
case for some, but not all, sample images.  
  
In the end you are responsible for encoding the proper gamut and unit  
conversion meta info into the image files you are about to use for  
serious research, no way around that.  
  
### Control keys:  
  
You can cycle through all images by pressing the space-bar. You can  
change image intensity scaling by pressing the cursor up- and down-keys.  
You can exit the viewer by pressing [ESCape](ESCape). By pressing the 'q' key, you  
can toggle between float precision HDR and 256 level 8 bit quantized  
images (not that useful).  
  
### Zoom mode:  
  
Pressing the left mouse button will enable zoom mode. Dragging the mouse  
while the button is depressed allows to change the region which should be  
zoomed. Releasing the mouse button will show the selected region zoomed  
up to fullscreen. A single mouse click will reset to the full image.  
  
  
This is an extension of [SimpleHDRDemo](SimpleHDRDemo).m, see that file for more basic  
usage of HDR displays with Psychtoolbox.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/HDRViewer.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/HDRViewer.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/HDRViewer.m</code>
</div>

