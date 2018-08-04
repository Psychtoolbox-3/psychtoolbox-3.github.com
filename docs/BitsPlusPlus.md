# [BitsPlusPlus](BitsPlusPlus)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

[BitsPlusPlus](BitsPlusPlus)(cmd [, arg1][, arg2, ...]) -- Psychtoolbox interface to  
Cambridge Research Systems Bits++ and Bits\# boxes for high precision  
stimulus output to analog displays via 14 bit video converters.  
  
This function is used to set up and interface with the Bits++ / Bits\# box of  
CRS. It is a Matlab wrapper around lower level GLSL Psychtoolbox  
functions. This function depends on graphics hardware that supports the  
Psychtoolbox imaging pipeline and framebuffers with more than 14 bit  
precision, i.e., 16 bpc fixed point framebuffers or floating point  
framebuffers. Have a look at the Psychtoolbox Wiki where you can find a  
list of graphics cards with the neccessary features.  
  
This function supersedes the old Matlab based Bits++ Toolbox, which  
essentially provides the same functionality on any graphics card, but is  
harder to use, much slower and not fully integrated into PTB, ie, you  
can't take full advantage of PTB's advanced drawing and image processing  
functions when using the old Bits++ toolbox.  
  
See the help section about Bits\# for advanced Bits\# commands and how to  
establish communication and convenient control for the Bits\# via USB  
connection.  
  
cmd - The command that [BitsPlusPlus](BitsPlusPlus) should execute. cmd can be any of  
the following:  
  
  
Load a linear identity mapping CLUT into Bits++ while running in Bits++  
mode:  
  
[BitsPlusPlus](BitsPlusPlus)('LoadIdentityClut', window);  
  
Will schedule update to an identity clut. Next invocation of  
[Screen](Screen)('[Flip](Flip)', window); will actually upload the identity clut into  
Bits++.  
  
  
[BitsPlusPlus](BitsPlusPlus)('UseFE1StereoGoggles', window, enable [, shutterState=0]);  
If 'enable' is 1, enable use of the CRS FE1 stereo goggles connected  
to the Bits display device. If 'enable' is 0 then disable use of the  
goggles again and put them in a resting state with either both shutters  
open ('shutterState = 0') or closed ('shutterState = 1').  
  
  
### Schedule a Bits++ DIO command for execution on next [Screen](Screen)('[Flip](Flip)'):  
  
[BitsPlusPlus](BitsPlusPlus)('DIOCommand', window, repetitions, mask, data, command [, xpos, ypos]);  
  
This will draw the proper T-Lock control codes at positions (xpos, ypos)  
for execution of the Bits++ DIO commands (mask, data, command).  
  
You can specify multiple codes at once: If mask, data, command, xpos and  
ypos are matrices or vectors with 'num' rows, then each of the 'num' rows  
defines one T-Lock code. If mask, command, xpos and ypos are scalars and  
data is a one row vector, then only the corresponding T-Lock line is  
drawn.  
  
For each DIO command:  
'mask' must be a 8 bit integer value, 'command' must be a 8 bit integer  
value, whereas 'data' must be a a 248 element row vector of bytes.   
  
Consult your Bits++ manual for explanation of the meaning of the values.  
  
xpos and ypos are optional: By default, the T-Lock code is drawn into the  
3rd pixel row of the output image, so it can't collide with a potential  
T-Lock code for CLUT updates.  
  
The DIO command will become effective during the next flip command. The  
T-Lock code is drawn during 'repetitions' successive invocations of  
[Screen](Screen)('[Flip](Flip)'). If you set 'repetitions' to -1, then the code will be  
drawn until you stop it via a call to [BitsPlusPlus](BitsPlusPlus)('DIOCommandReset', window);  
  
  
### Disable use of the DIO T-Lock code blitting:  
  
[BitsPlusPlus](BitsPlusPlus)('DIOCommandReset', window);  
Stops blitting of T-Lock command codes immediately. If you want to use  
them again, you have to respecify codes via the [BitsPlusPlus](BitsPlusPlus)('DIOCommand',...);  
  
  
### Manage treatment of one or two connected CRS devices:  
  
[BitsPlusPlus](BitsPlusPlus)('SetDualDevices', mode);  
If 'mode' is set to 0, which is the default, assume one CRS device is connected.  
  
If 'mode' is set to 1, then assume two CRS devices, e.g., 2 Display++ or  
Bits\# devices are connected for dual-display stereo/binocular stimulation and  
adapt accordingly. Apply the same CLUT in Bits++ and Mono++ display mode  
to both connected display devices in stereomodes 4, 5 and 10.  
  
  
  
  
Open a full-screen window on the Bits++ display as with  
[Screen](Screen)('OpenWindow', ...), perform all initialization:  
  
The following commands will execute [Screen](Screen)('OpenWindow') with all proper  
parameters, followed by Bits++ init routines. They are completely sufficient  
drop in replacements for [Screen](Screen)('OpenWindow'), accepting and returning  
exactly the same arguments that [Screen](Screen)() would do, adjusting all  
parameters to the constraints of the Bits++, if necessary.  
  
### Activate Bits++ mode:  
  
[win, winRect] = [BitsPlusPlus](BitsPlusPlus)('OpenWindowBits++', screenid, ...);  
  
This will open an onscreen window on Bits++ screen 'screenid' with a  
standard 8 bits per color channel framebuffer. The gamma table of your  
graphics hardware will be loaded with an identity gamma table, so the  
T-Lock system of Bits++ works and Bits++ can accept commmands embedded  
into the stimulus images. Psychtoolbox will automatically embed a T-Lock  
control line into the top line of the display screen, which encodes the  
256 entry, 14 bit per color channel CLUT to use for Bits++ display mode.  
You can change the Bits++ CLUT at any time via the standard PTB  
[Screen](Screen)('LoadNormalizedGammaTable', win, newclut, 2); command. The  
'newclut' will get uploaded to the Bits++ at the next invocation of  
[Screen](Screen)('[Flip](Flip)') to allow updates of the CLUT synchronous to stimulus  
updates. 'newclut' has to be a 256 rows by 3 columns matrix with values  
in range 0.0 - 1.0: 0.0 is mapped to clut color value 0, 1.0 is mapped to  
the highest Bits++ output color value 16383.  
  
This mode works on any [OpenGL](OpenGL) graphics hardware.  
  
  
### Activate Mono++ mode:  
  
[win, winRect] = [BitsPlusPlus](BitsPlusPlus)('OpenWindowMono++', screenid, ...);  
  
This will open an onscreen window on Bits++ screen 'screenid' for display  
of pure luminance (grayscale) images. The framebuffer has a resolution of  
32 bit floating point precision by default: This means that pixel luminance  
values have to be specified as floating point numbers between 0.0 and  
1.0. 0.0 maps to black (Output intensity 0 on Bits++ device). 1.0 maps to  
white (Maximum output intensity 16383 on Bits++ device). The intensity  
range between 0.0 and 1.0 is internally represented and processed by  
Psychtoolbox with a resolution 23 bits, i.e. over 8 million levels of  
luminance. The Bits++ can resolve this range to 14 bits, ie. 16384 levels  
of luminance during display. This mode is not compatible with the use of  
any gamma- or clut- tables. Both the graphics hardwares gamma table and  
the Bits++ internal clut are set to an identity mapping while this mode  
is active. Please read the notes below the Color++ section for graphics  
hardware requirements and other useful tips for use of Bits++.  
  
If you call this subfunction as 'OpenWindowMono++WithOverlay', the  
overlay plane of Bits++ gets enabled and an additional overlay window is  
created for drawing the image for that overlay plane.  
  
[overlaywin, overlaywinRect] = [BitsPlusPlus](BitsPlusPlus)('GetOverlayWindow', win);  
- Will return the handle to the 'overlaywin'dow associated with the  
onscreen luminance window:  
  
  'overlayWin' is the handle to the overlay window associated with the  
  overlay of onscreen window 'win'. The overlay window is a standard  
  offscreen window, so you can do anything with it that you would want to  
  do with offscreen windows. The only difference is that the window is a  
  pure index window: It only has one "color channel", which can be written  
  with color values between 0 and 255. Values 1 to 255 get mapped to the  
  corresponding color indices of the Bits++ overlay plane: A zero value is  
  transparent -- Content of the onscreen window is visible. Positive  
  non-zero color values map to the 255 indices available in overlay mode,  
  these get mapped by the Bits++ CLUT to colors. You can define the  
  mapping of indices to CLUT colors via the  
  [Screen](Screen)('LoadNormalizedGammaTable', win, clut, 2); command.  
  
  Updates of the overlay image are synchronized to [Screen](Screen)('[Flip](Flip)')  
  updates. If you draw into the overlay window, the changed overlay image  
  will become visible at [Screen](Screen)('[Flip](Flip)') time -- in sync with the changed  
  onscreen window content. The overlay plane is not automatically cleared  
  to background (or transparent) color after a flip, but its content  
  persists across flips. You need to clear it out manually via a  
  [Screen](Screen)('FillRect') command.  
  
  
### Activate Color++ mode:  
  
[win, winRect] = [BitsPlusPlus](BitsPlusPlus)('OpenWindowColor++', screenid, ...);  
  
This will open an onscreen window on Bits++ screen 'screenid' for display  
of 14 bit per color component 42bpp color images. The framebuffer has  
a resolution of 32 bit floating point precision for each color component  
by default: This means that (Red, Green, Blue) color pixel component  
values have to be specified as floating point numbers between 0.0 and  
1.0. 0.0 maps to minimum output intensity on Bits++ device for a channel.  
1.0 maps to maximum output intensity 16383 on Bits++ device for a channel.  
The color intensity range between 0.0 and 1.0 is internally represented and  
processed by Psychtoolbox with an effective resolution of about 23 bits,  
i.e. over 8 million levels of color per color channel. The Bits++ can resolve  
this range to 14 bits, ie. 16384 levels of color during display. This mode  
is not compatible with the use of any gamma- or clut- tables. Both the graphics  
hardwares gamma table and the Bits++ internal clut are set to an identity  
mapping while this mode is active. Please read the notes below for graphics  
hardware requirements and other useful tips for use of Bits++.  
  
  
If you use Color++ mode, you must call  
[BitsPlusPlus](BitsPlusPlus)('SetColorConversionMode', mode); first to select the mode  
for sampling the framebuffer and converting into output color values. See  
the respective section of "help [PsychImaging](PsychImaging)" for 'Color++' or  
'EnableDataPixxC48Output' mode for the Bits+ or Datapixx device for an  
explanation of this mandatory parameter. The setting before 22nd  
September 2010 for all PTB-3 versions was 0 (==zero).  
  
You can query the mode for an onscreen window 'win' by a call to:  
mode = [BitsPlusPlus](BitsPlusPlus)('GetColorConversionMode', win);  
  
  
### Notes for both Mono++ and Color++ mode:  
  
In Mono++ and Color++ mode, PTB expects color values in the range 0.0 to  
1.0 instead of the (otherwise usual) range 0 to 255. The range 0.0-1.0  
is a more natural fit for high dynamic range/precision output devices than  
the 0-255 range with its strong ties to 8 bpc output devices. 0-1 is also  
the "natural" native color range of [OpenGL](OpenGL), so colors in this range can  
be handled by the graphics hardware at a higher speed. You can change the  
mapping of input colors to output intensities by use of the command  
[Screen](Screen)('ColorRange') (see its online help for usage), but in the interest  
of uniform code and to avoid possible side effects with some graphics  
hardware, we strongly recommend using the default 0.0-1.0 color range.  
  
You can still pass standard 8bpc (256 color/intensity levels) color/luminance  
textures to PTB via standard use of [Screen](Screen)('MakeTexture') - the hardware  
will convert such 8bpc images to OpenGL's native color range, as well as  
any images delivered by the Quicktime movie playback engine or the video  
capture engine. If you want to provide high dynamic range, high color  
depths images, please specify them as Matlab double matrices to  
[Screen](Screen)('MakeTexture') and set the optional flag 'floatprecision' to 1 or  
2, i.e., hdrtex = [Screen](Screen)('MakeTexture', win, myHDRImage, [], [], 2);  
  
Psychtoolbox will represent such images with an internal precision of 10  
bits + 1 bit sign if you choose the 'floatprecision' flag to be 1. If you  
choose a 'floatprecision' flag of 2, PTB will represent the images with  
an internal precision of 23 bits + 1 bit sign. You can provide negative  
color values as well, e.g., -0.5. If you wonder what the use of this  
might be, have a careful look at the tutorial script...  
'AdditiveBlendingForLinearSuperpositionTutorial.m'  
... for an example of extremely fast drawing of luminance gratings with  
controllable size, orientation and contrast and correct linear superposition:  
  
By default, PTB will use a 32-bit floating point framebuffer for your  
drawings, ie. the precision is way higher than needed for any high  
dynamic range/resolution display device in existence. The downside of this  
super-precision is that alpha-blending is not supported in this mode, unless  
you employ an [NVidia](NVidia) Geforce 8000 series (and later) graphics card, or a  
ATI Radeon HD2000/3000 series graphics card (and later). If you need  
alpha-blending on older/other hardware then specify the optional flag  
'kPsychNeed16BPCFloat' for the 'imagingmode' argument. This will reduce  
effective accuracy of the framebuffer to 10 bit precision, but allow for  
fast alpha-blending. 10 Bit precision are 4 bits less than the 14 bits  
that Bits++ can provide, but it will be possible to use the extra 14-10 =  
4 bits for gamma correction of the display by employing a gamma  
correction shader.  
  
### Gamma- and color correction:  
  
In Mono++ and Color++ mode, the hardware gamma tables of your graphics  
card and the Bits+ box can't be used for gamma- or color correction.  
However, PTB provides a much more powerful and flexible color correction  
system for this purpose. See "help [PsychColorCorrection](PsychColorCorrection)" for further  
explanation and usage examples for standard gamma correction.  
  
Graphics hardware requirements: Mono++ and Color++ mode require use of the  
Psychtoolbox imaging pipeline and floating point framebuffers. The  
minimum requirements are ATI Radeon X1000 series or [NVidia](NVidia) Geforce-6800  
series and later graphics hardware. We currently recommend [NVidia](NVidia)  
Geforce-8000 series or ATI Radeon HD-2000/3000 hardware for best results.  
However, this functions have been successfully tested on ATI Radeon X1600  
and [NVidia](NVidia) Geforce-7800 hardware as well.  
  
All Bits++ modes supported by this function should work Plug & Play,  
requiring no changes to your stimulus code other than mentioned here to  
take full advantage of all functionality of Psychtoolbox just as with standard  
8 bpc displays at the higher 14 bpc quality of Bits++. If you find this  
not to be the case then it's either an omission in our documentation  
or a bug - Please report it.  
  
  
### BITS\# specific functions:  
  
A Bits\# device which is connected via USB will show up as an additional  
serial port on the system. This driver will communicate with the Bits\#  
by establishing a serial port connection to the device via that serial  
port. Presence of a Bits\# can be signalled by either calling the [BitsPlusPlus](BitsPlusPlus)('OpenBits\#')  
function and passing a serial port device spec 'portSpec', or just by calling  
[BitsPlusPlus](BitsPlusPlus)('OpenBits\#') without any parameters. In the latter case, the  
driver will check for the existence of a configuration file named...  
[[PsychtoolboxConfigDir](PsychtoolboxConfigDir) 'BitsSharpConfig.txt']. Presence of the file means  
to use a Bits\# device, absence means to treat any device as a Bits+ device.  
Presence of a serial port device file name in the first line of that text  
configuration file will use the serial port device with that name for  
communication, otherwise the driver will try to auto-detect the proper  
serial port for communication. If you have multiple such devices, you can add  
multiple lines with serial port names to the configuration file, and then select  
a given device by specifying a index into the file as 'portSpec'. portSpec=1  
would use line 1 of the file for finding the device, portSpec=2 would use line 2  
etc.  
  
  
[handle, portHandle] = [BitsPlusPlus](BitsPlusPlus)('OpenBits\#' [, portSpec]);  
-- Open a serial port control connection to a connected Bits\# device, return  
a non-zero 'handle' to it on success, or the value zero if no such device exists  
or could not be opened. On successfull open, a low-level 'portHandle' is returned  
as well, which allows access to the serial port control connection via [IOPort](IOPort) for  
people who really know what they are doing.  
  
Note: The current implementation only allows to connect to one device at a time,  
therefore use of the returned 'handle' is not very useful at the moment.  
  
The 'portSpec' parameter is optional and defines the name of the serial  
port(-device file) or index of the CRS device to use for the connection.  
If omitted, the name will be taken from a configuration file, or auto-detected.  
If specified as a string, the string defines the serial port device file. If  
specified as a numeric index, it selects the line within the configuration file  
from which the portname string will be taken, ie. index 1 = 1st line, 2 = 2nd line...  
  
This function must be called before use of any Bits\# specific functions, otherwise  
they'll turn into no-ops or failures. This function can be called multiple times for  
a given device. It will only open the connection on first call. Successive calls will  
do nothing but increment a reference count of clients to the device.  
  
  
rc = [BitsPlusPlus](BitsPlusPlus)('[Close](Close)' [, handle]);  
-- Decrement reference count to a Bits\# device 'handle', close the serial  
connection to it once the count drops to zero, ie., as soon as nobody is using  
the connection anymore. If 'handle' is omitted, the '[Close](Close)' call is executed for  
each currently open device.  
  
  
rc = [BitsPlusPlus](BitsPlusPlus)('ResetOnWindowClose');  
-- Like '[Close](Close)', but switch display back to Bits++ video mode first, as  
that mode is "GUI friendly". Usually automatically called from [Screen](Screen)()  
when the Bits\# stimulation onscreen window gets closed, at least if you  
used [PsychImaging](PsychImaging)() to control the device.  
  
  
rc = [BitsPlusPlus](BitsPlusPlus)('CheckGPUSanity', window, xoffset [, injectFault=0]);  
-- Perform online-test of GPU identity gamma tables and DVI-D display  
encoders. Try to correct problems with wrong identity gamma tables and at  
least detect problems with (spatio-)temporal display dithering. Returns  
rc == 0 on full success, rc \> 0 on failure.  
If the optional 'injectFault' parameter is set to 1, then an intentionally  
perturbed gamma table is loaded into the gpu to test how well the gamma table  
tweaking code is able to recover from wrong tables.  
  
  
pixels = [BitsPlusPlus](BitsPlusPlus)('GetVideoLine', nrPixels, scanline);  
-- Return the first (left-most) 'nrPixels' pixels in video scanline  
'scanline' of the video display driven by a Bits\# device. 'pixels' is  
a uint8 matrix with three rows for red, green and blue pixel color values,  
and 'nrPixels' columns, the three elements of each column encoding the  
r,g,b color values of the pixel corresponding to that column (x-position)  
of the scanline (y-position). Values are read back via the USB-Serial  
connection from the Bits\# and the device sends back the pixel data as  
received over the DVI-D link.  
  
  
[BitsPlusPlus](BitsPlusPlus)('SwitchToBits++');  
-- Switch Bits\# to Bits++ mode.  
  
  
[BitsPlusPlus](BitsPlusPlus)('SwitchToMono++');  
-- Switch Bits\# to Mono++ mode.  
  
  
[BitsPlusPlus](BitsPlusPlus)('SwitchToColor++');  
-- Switch Bits\# to Color++ mode.  
  
  
[BitsPlusPlus](BitsPlusPlus)('SwitchToStatusScreen');  
-- Switch Bits\# to Status screen display.  
  
  
[BitsPlusPlus](BitsPlusPlus)('MassStorageMode');  
-- Switch Bits\# to [MassStorageMode](MassStorageMode). This will forcefully close allow  
client connections to the device, close the USB serial port connection  
and close the driver. The Bits\# will report into USB mass storage mode,  
where it can get accessed like a USB flash drive, e.g., to edit configuration  
files, update firmware or EDID's etc. Only a power-cycle will bring the  
device back into a mode which allows us to connect to it again.  
  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/BitsPlusPlus.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/BitsPlusPlus.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/BitsPlusPlus.m</code>
</div>

