# [VignetCalibration](VignetCalibration)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

 s = [VignetCalibration](VignetCalibration)([filename] [, screenId])  
  
 Vignetted Luminance calibration procedure for undistortion of distorted  
 display luminance.  
  
 This code was created by Jorrit S. Montijn of the Laboratoire Psychologie  
 de la Perception at Universite Paris Descartes.  
  
 This function allows the user to create a calibration for a vignetted  
 luminance distortion. It enables the user to choose from either a  
 Gaussian or Exponential approximation of the luminance vignetting. Users  
 can change the position and steepness of the luminance fall-off in  
 horizontal and vertical direction independently. It is also possible to  
 adjust the minimal luminance.  
  
 Once the calibration procedure is finished, the gain matrix (and other  
 possibly useful parameters and variables) are saved to disk for use by a  
 vignetting compensation program (see 'VignettingCorrectionDemo' for an  
 example of how to do this).  
  
###  How to use:  
  
###  Start the script, providing a filename and screennumber:  
  
 'filename' is the name of the file to which calibration results will be   
 saved. If none is provided, a default name will be used. The default file  
 will be stored in the directory returned by [PsychtoolboxConfigDir](PsychtoolboxConfigDir)('ShadingCalibration').  
  
 'screenId' is the optional index of the screen that you want to  
 calibrate. If only one screen is present, it is not necessary to include  
 this parameter.  
  
 When started, the program will show either a gaussian or exponential  
 approximation of the required gain function. You can adjust the  
 parameters so that the screen will look approximately isoluminant. It is  
 recommended to use a photometer, since human eyes are far from perfect when  
 doing this.  
  
###  You can use the following keys to issue commands:  
  
 Escape -   use this key to save and exit  
 Tab        -   show/hide help text  
 Space      -   change the parameter you wish to adjust  
 '<' and '\>'    -   use these keys to change the increment size of the  
                    parameter adjustments  
 Arrow Keys -   adjust parameters (depending on selected parameter)  
                1. Luminance/Function type  
                2. Width/Steepness of function  
                3. Position of centre  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/VignetCalibration.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/VignetCalibration.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/VignetCalibration.m</code>
</div>

