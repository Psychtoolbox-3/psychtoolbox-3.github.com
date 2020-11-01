# [HDRRead](HDRRead)
##### >[Psychtoolbox](Psychtoolbox)>[PsychFiles](PsychFiles)

[img, info, errmsg] = [HDRRead](HDRRead)(imgfilename [, continueOnError=0][, flipit=0])  
Read a high dynamic range image file and return it as double() matrix,  
suitable for use with [Screen](Screen)('MakeTexture') and friends.  
  
### Input arguments:  
  
'imgfilename' - Filename of the HDR image file to load.  
  
'continueOnError' Optional flag. If set to 1, [HDRRead](HDRRead) won't abort on  
error, but simply return an empty 'img' matrix and 'info' and a error  
message in 'errmsg'. Useful for probing if a specific file type is  
supported. If set to 0 or omitted, then [HDRRead](HDRRead) will abort with an error  
on any problem or unsupported image file types.  
  
'flipit' Optional flag: If set to 1, the loaded image is flipped upside  
down.  
  
### Return arguments:  
  
Returns 'img' - A double precision matrix of size h x w x c where h is  
the height of the input image, w is the width and c is the number of  
color channels: 1 for luminance images, 2 for luminance images with alpha  
channel, 3 for true-color RGB images, 4 for RGB images with alpha  
channel. If 'imgfilename' is not a supported file type or some error happens,  
then 'img' will be returned as empty [] matrix.  
  
Returns 'info' - A struct with info about the image. On error, 'info'  
will be returned as empty [] matrix. On success, 'info' has at least the  
following fields, which may be computed from information in the image file,  
or may be "made up" from internal hard-coded defaults, if the specific image  
file or the general image file format do not provide the information:  
  
info.format - A string describing the format of the image file, e.g.,  
'rgbe' or 'openexr'. See below for supported formats and their id's.  
  
info.dataWindow = Data window [xmin, ymin, xmax, ymax] as defined by [OpenEXR](OpenEXR).  
  
info.displayWindow = Display window [xmin, ymin, xmax, ymax] as defined by [OpenEXR](OpenEXR).  
  
info.pixelAspectRatio = Pixel aspect ratio as defined by [OpenEXR](OpenEXR).  
  
info.screenWindowWidth = Window width as defined by [OpenEXR](OpenEXR).  
  
info.screenWindowCenter = [cx, cy] as defined by [OpenEXR](OpenEXR).  
  
info.lineOrder = Line order (0) = downwards/increasing (1) = upwards/decreasing  
                 as defined by [OpenEXR](OpenEXR).  
  
info.compression = Compression type id, as defined by [OpenEXR](OpenEXR): 0 = None,  
                   1 = RLE, 2 = ZIPS, 3 = ZIP, 4 = PIZ, 5 = PXR24, 6 = B44,  
                   7 = B44A, 128 = ZFP.  
  
info.[GamutFromFile](GamutFromFile) = 0 if the file did not provide color gamut information,  
                   = 1 if the file did provide color gamut information,  
                   = -1 if the file may or may not contain gamut information,  
                        but [HDRRead](HDRRead)() can not read it.  
  
info.[ColorGamut](ColorGamut) = 2-by-4 matrix with the CIE 1931 2D chromaticity  
                  coordinates of the red, green, and blue primaries  
                  (column 1 - 3) and of the white-point (4th column),  
                  iow. the definition of the color gamut of the color  
                  space in which the image is represented.  
  
                  If info.[GamutFromFile](GamutFromFile) is 1, then this matrix is parsed  
                  from the image file. Otherwise, the file did not  
                  provide the info and a hard-coded default is returned,  
                  which is defined in the spec for the file format, e.g.,  
                  Rec-709 color space for [OpenEXR](OpenEXR) images, and something  
                  similar for .hdr Radiance images.  
  
info.sampleToNits = Either a conversion factor from sample units to nits,  
                    ie. the value by which each color component needs to  
                    be multiplied to convert it into nits. Or the value  
                    zero, to mark the conversion factor as "unknown" if  
                    the file does not provide the conversion factor.  
  
Depending on the file format and the specific file, there may be more  
optional info.subfields available, with file format specific meaning. Not  
all image attributes can be parsed by [HDRRead](HDRRead)().  
  
Returns 'errmsg' - An empty string on success, but on failure may contain  
a useful error message for the user.  
  
  
[HDRRead](HDRRead) is a dispatcher for a collection of reading routines for  
different HDR image file formats. Currently supported are:  
  
\* Radiance run length encoded RGBE format, read via read\_rle\_rgbe().  
  File extension is ".hdr" or ".pic". Returns a RGB image.  
  
  info.format is 'rgbe', color values are supposed to be in units of  
  radiance. The Radiance file format is specified here:  
  
  https://floyd.lbl.gov/radiance/refer/filefmts.pdf  
  
  The specification suggests that a pixel (r,g,b) color value of (1,1,1)  
  corresponds to a total energy of 1 watt/steradian/sq.meter over the  
  visible spectrum. It proposes the following formula for conversion to  
  luminance for the standard Radiance RGB primaries:  
  
  luminance = 179 \* (0.265\*R + 0.670\*G + 0.065\*B)  
  
  So (r,g,b) = (1,1,1) corresponds to white light of 179 nits luminance.  
  The value of 179 lumens/watt is the standard luminous efficacy of  
  equal-energy white light that is defined and used by Radiance  
  specifically for this conversion.  
  
\* [OpenEXR](OpenEXR) files, file extension is ".exr". info.format is 'openexr'.  
  By default, [Screen](Screen)()'s builtin [Screen](Screen)('ReadHDRImage') function is used,  
  which uses the builtin tinyexr open-source library from:  
  
  https://github.com/syoyo/tinyexr  
  
  This method is fast and can handle the most common [OpenEXR](OpenEXR) format  
  encoding, single-part RGB(A) images, but will not be able to cope with  
  some more unusual encodings, e.g., YUV images, multipart images or deep  
  images, or additional integer channels for pixel ids. See the feature  
  table at tinyexr's [GitHub](GitHub) page for features and limitations. Some of  
  these limitations apply due to [Screen](Screen)()'s current use of tinyexr, e.g.,  
  tinyexr can handle multi-part images and some deep images, but [Screen](Screen)  
  currently does not implement the needed interfaces.  
  
###   A technical high level spec for [OpenEXR](OpenEXR) files can be found at:  
  
  https://www.openexr.com/documentation/[TechnicalIntroduction](TechnicalIntroduction).pdf  
  
  In case of YUV images, [HDRRead](HDRRead)() will try to use the MIT licensed  
  exrread() command from the following 3rd package/webpage, if the  
  openexr-matlab package has been installed by the user:  
  
  https://github.com/skycaptain/openexr-matlab  
  
  That package uses the [OpenEXR](OpenEXR) libraries for image reading, so those  
  libraries must be installed on your system as well by yourself. At  
  least GNU/Linux usually comes with libopenexr preinstalled or  
  installable from the distribution package archives.  
  
  The downside of using exrread() is that it won't provide color gamut  
  meta information, but always return fixed gamut info for a Rec-709  
  color space. For properly color-managed image reading you might  
  therefore be better off using a 3rd party [OpenEXR](OpenEXR) converter application  
  to convert YUV images to RGB images, so [Screen](Screen)()'s internal .exr  
  reading function can be used.  
  
The reader routines are contributed code or open source / free software /  
public domain code downloaded from various locations under different, but  
MIT compatible licenses. See the help for the respective loaders for  
copyright and author information.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychFiles/HDRRead.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychFiles/HDRRead.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychFiles/HDRRead.m</code>
</div>

