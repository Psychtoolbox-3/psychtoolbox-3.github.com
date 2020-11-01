# [Screen('ReadHDRImage')](Screen-ReadHDRImage) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

[imageArray, format, errorMsg, auxInfo] = Screen('ReadHDRImage', filename [, errorMode=0]);

Read a high dynamic range (HDR) image file from the filesystem and return its  
content.  
  
This function allows to read some HDR file formats and return the image data as  
a double matrix.  
'filename' is the name of the image file.  
'errorMode' is the optional flag to define how failures to read the file should  
be handled: 0 = Fail silently: Return empty 'imageArray', 1 = Like 0, but print  
warning or error message to console, 2 = Like 1, but also abort script with  
error message.  
In any case, 'errorMsg' is either empty on success, 'unknown-format' if the file  
was not recognized as a supported HDR format, or a loader specific error message  
if the file could not be loaded for some reason.  
'imageArray' is a height-by-width-by-channels double matrix containing the pixel  
data in usual Matlab format, e.g., 4 channels RGBA planes. 'imageArray' can be  
directly passed into [Screen](Screen)('MakeTexture', win, imageArray); to turn it into a  
displayable image texture.  
'format' is a name string that identifies the format of the image file read.  
'auxInfo' is a struct with additional properties and information about an image  
if the image file supports such additional meta information. If an image file  
format does not support useful additional information then 'auxInfo' will be an  
empty [] matrix. The fields of the struct are dependent on the file format and  
specific image file, so don't assume a fixed set of fields and fieldNames for a  
returned 'auxInfo' struct.  
  
The following HDR file formats are currently supported:  
\* [OpenEXR](OpenEXR) file format (file suffix ".exr", 'format' = "openexr"), via use of the  
included open-source [TinyEXR](TinyEXR) library (https://github.com/syoyo/tinyexr). Only  
single-part RGB(A) images are supported at the moment, no multi-part images or  
deep images. Only color channels are supported, no integer id channels.  
The 'auxInfo' struct for [OpenEXR](OpenEXR) images contains the following struct fields:  
'ColorGamut' a 2-by-4 matrix defining the CIE 1931 2D chromaticity coordinates  
of the red, green and blue primaries and white-point of the gamut / color-space  
in which the image content is represented. 'GamutFromFile' is 1 if the  
'ColorGamut' was actually read from the 'chromaticities' [OpenEXR](OpenEXR) optional image  
attribute, in which case the 'chromaticities' field will contain exactly the  
same information. 'GamutFromFile' is 0 if the image file does not contain a  
'chromaticities' attribute, in which case the spec requires to assume the gamut  
to be that of BT-709-3, and the 'ColorGamut' matrix will contain the gamut info  
for BT-709.  
'sampleToNits' is always present and describes the conversion factor from sample  
values to absolute units of nits. The 'sampToNits' attribute/field is either  
provided by the exr file, or it will default to zero, to mark the info  
unavailable.  
Additionally, many of the mandatory [OpenEXR](OpenEXR) attributes are part of 'auxInfo',  
e.g., 'dataWindow', 'displayWindow', 'pixelAspectRatio'. Additional optional  
custom attributes may be present. The current implementation can handle  
attributes of type 'string', 'float', and 'chromaticities'. Other attributes  
will be listed, but returned as empty [] struct fields.  
You can find technical background info about the [OpenEXR](OpenEXR) file format under this  
link:  
https://www.openexr.com/documentation/[TechnicalIntroduction](TechnicalIntroduction).pdf  
  
  


###See also:
[MakeTexture](Screen-MakeTexture)
