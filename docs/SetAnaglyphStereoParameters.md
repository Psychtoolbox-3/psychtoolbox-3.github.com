# [SetAnaglyphStereoParameters](SetAnaglyphStereoParameters)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

retval = [SetAnaglyphStereoParameters](SetAnaglyphStereoParameters)(subcommand, windowPtr, [red green blue]);  
  
Change parameters of built-in anaglyph stereo display function at  
runtime. Allows to change all relevant settings of the algorithm at any  
time in your script. You need to open your onscreen window with the  
'stereomode' parameter set to one of the anaglyph modes (i.e. one of  
6=Red-Green anaglyph, 7=Green-Red, 8=Red-Blue, 9=Blue-Red, where  
Red-Green means "Left eye displayed in red channel, right eye displayed  
in green channel").  
  
Anaglyph stereo also works in stereo modes 2, 3, 4, 5 and 10 if you used  
the ...  
[PsychImaging](PsychImaging)('AddTask', 'LeftView', 'DisplayColorCorrection', 'AnaglyphStereo')  
... and ...  
[PsychImaging](PsychImaging)('AddTask', 'RightView', 'DisplayColorCorrection', 'AnaglyphStereo')  
... setup sequence to add an anaglyph shader to the end of each view  
channel. However, in those "non-pure" exotic anaglyph modes only a subset  
of the commands mentioned here work, specifically the ones for advanced  
anaglyph display, ie., subfunctions 'ColorAnaglyphMode' and friends. Inverted mode  
or simple mode or changing NTSC weights or simple gains does not work in  
this configuration.  
  
Additionally you also need to enable the Psychtoolbox image processing  
pipeline by using the [PsychImaging](PsychImaging)() command for configuring and opening  
onscreen windows.  
  
Example:  
[PsychImaging](PsychImaging)('PrepareConfiguration');  
stereomode = 6;  
windowPtr = [PsychImaging](PsychImaging)('OpenWindow', screenid, bgcolor, [], [], [], stereomode);  
  
See 'help PsychImaging' and 'help PsychGLImageProcessing' for an overview  
of the imaging pipeline.  
  
# Parameters and their meaning  
  
'windowPtr' is the handle to a anaglyph stereo onscreen window.  
  
### 'subcommand' can be one of:  
  
'LeftGains' - Provide (in optional vector [red green blue]) per-channel  
color gains for computation of the left-eye channel. This allows to  
adjust the output colors to optimally match the color emission / filter  
profile of your anaglyph glasses and monitor - Reduce ghosting / visual  
crosstalk. E.g.  
  
[SetAnaglyphStereoParameters](SetAnaglyphStereoParameters)('LeftGains', win, [1.0 0.0 0.0]); sets the  
red-gain for the left eye image to 1.0 and disables output of the left  
eye image into the green or blue channels. This is the default setting  
for Red-Green or Red-Blue anaglyph, left eye view only goes into red  
channel.  
  
The command always returns the old gains as a 3 component vector.  
  
'RightGains' - See left gains, but this time for right image:  
[SetAnaglyphStereoParameters](SetAnaglyphStereoParameters)('RightGains', win, [0.0 0.7 0.0]);  
would set the green channel to 70% output intensity and disable the red-  
and blue channels. This is a typical setting for Red-Green anaglyph  
stereo: Right eye only written to green color channel, but with reduced  
output intensity to compensate for the stronger green-sensitivity of the  
human eye.  
  
'ColorToLuminanceWeights' - Set the color to luminance conversion  
weights: PTB converts all color images into pure luminance (greyscale)  
images before distributing them into the color channels via the formula:  
Luminance = redvalue \* redweight + bluevalue \* blueweight + greenvalue \*  
greenweight.  
  
The default red- green- and blue-weights are (0.3, 0.59, 0.11), so:  
L = 0.3\*red + 0.59\*green + 0.11\*blue. This is according to NTSC standard  
(if i remember correctly!). You can change the weights via:  
  
[SetAnaglyphStereoParameters](SetAnaglyphStereoParameters)('ColorToLuminanceWeights', win, [redweight greenweight blueweight]);  
  
The command always returns the old weights as a 3 component vector.  
  
'BackgroundColorBias' - Set the "background color" for inverted anaglyph  
mode. This color value is added to each pixel. It defaults to zero - bias  
free display. For inverted mode, one usually sets it to maximum output  
intensity, so that the default background is a bright output.  
  
'InvertedMode' - Switch to inverted display mode, i.e., set the  
'BackgroundColorBias' and color gains properly. The image is displayed in  
an inverted fashion, like a photo-negative. This allows for less ghosting  
artifacts if your stimulus is sparse, e.g., dots and lines. This trick  
was proposed by Massimiliano di Luca.  
  
'NormalMode' - Switch from inverted mode to normal anaglyph mode.  
Background color bias is set to zero, gains a positive.  
  
### Color reproduction in color images with Anaglyphs:  
  
[SetAnaglyphStereoParameters](SetAnaglyphStereoParameters)('ColorAnaglyphMode', win [,[LeftMatrix](LeftMatrix)] [,[RightMatrix](RightMatrix)] [, Gamma]);  
  
This switches to a more flexible anaglyph implementation, where the  
output color is calculated as:  
  
[redout, greenout, blueout]' = [LeftMatrix](LeftMatrix) \* [leftred, leftgreen, leftblue]' + [RightMatrix](RightMatrix) \* [rightred, rightgreen, rightblue]'  
  
where [redout, greenout, blueout] == Final anaglyph color pixel.  
      [leftred, leftgreen, leftblue] == Input left eye pixel color.  
      [rightred, rightgreen, rightblue] == Input right eye pixel color.  
  
and   [LeftMatrix](LeftMatrix) and [RightMatrix](RightMatrix) are 3 by 3 color weight matrices.  
  
If 'Gamma' is provided, then the 'redout' color is gamma corrected with  
the given 'Gamma' value, ie. redout = redout ^ Gamma.  
  
Multiple sets of possible matrices and gamma weights are already defined  
and selectable with the following names:  
  
[SetAnaglyphStereoParameters](SetAnaglyphStereoParameters)('OptimizedColorAnaglyphMode', win);  
[SetAnaglyphStereoParameters](SetAnaglyphStereoParameters)('FullColorAnaglyphMode', win);  
[SetAnaglyphStereoParameters](SetAnaglyphStereoParameters)('HalfColorAnaglyphMode', win);  
[SetAnaglyphStereoParameters](SetAnaglyphStereoParameters)('GrayAnaglyphMode', win);  
  
The idea and matrices/gammas for these four selectable presets are taken  
from the following website:  
  
http://mitglied.lycos.de/stereo3d/anaglyphcomparison.htm  
  
  
### Overlay support:  
  
If you want to have an additional monoscopic overlay window, e.g., for  
text instructions to the subject, fixation dots etc., you can get one via  
a call to:  
  
overlaywindow = [SetAnaglyphStereoParameters](SetAnaglyphStereoParameters)('CreateMonoOverlay', win);  
  
This will create a fullscreen 'overlaywindow'. You can draw to that  
window like to any other window. It's content will be overlaid to the  
final anaglyph image, but without applying anaglyph conversion to it.  
Wherever this overlay has an alpha color value of zero, the stimulus will  
be shown. Wherever its alpha value is greater than zero, the overlays  
image will be shown.  
  
overlaywindow = [SetAnaglyphStereoParameters](SetAnaglyphStereoParameters)('CreateGreenOverlay', win);  
... and ...  
overlaywindow = [SetAnaglyphStereoParameters](SetAnaglyphStereoParameters)('CreateBlueOverlay', win);  
... will allow to only place the overlay info into the green color channel  
or blue color channel, ie., the channel not used by Red-Blue or Red-Green  
color anaglyph stereo.  
  
'GetHandle' - Return GLSL handle to anaglyph shader. Allows to modify the  
shader itself, e.g., replace it by your own customized shader. Only for  
[OpenGL](OpenGL) experts!  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/SetAnaglyphStereoParameters.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/SetAnaglyphStereoParameters.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/SetAnaglyphStereoParameters.m</code>
</div>

