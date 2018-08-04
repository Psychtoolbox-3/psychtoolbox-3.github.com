# [HighPrecisionLuminanceOutputDriversImagingPipelineTest](HighPrecisionLuminanceOutputDriversImagingPipelineTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[HighPrecisionLuminanceOutputDriversImagingPipelineTest](HighPrecisionLuminanceOutputDriversImagingPipelineTest)(whichDriver, [whichScreen][,plotdiffs=0][, forcesuccess=0])  
  
Tests correct function of a variety of high precision luminance output  
device drivers (so called "output formatters") with imaging pipeline.  
  
This test script needs to be run once after each graphics card or  
graphics driver or Psychtoolbox upgrade, or after any other major change  
in system configuration and display settings.  
  
This test verifies that the Psychtoolbox image processing pipeline is  
capable to correctly convert a high dynamic range / high bit precision  
luminance image into a output format suitable for driving one of the  
supported high precision luminance output devices, e.g., different Pelli,  
Zhang, Watson style video attenuators, Xiangru Li et al. [VideoSwitchers](VideoSwitchers),  
Pseudo-Gray output formatters, etc.  
  
It does so by generating a test stimulus, converting it into a properly  
formatted image via the "known good" Matlab reference implementation of  
an output driver, then again via the  use of the imaging pipeline. Then  
it reads back and compares the conversion results of both to verify that  
the imaging pipeline produces exactly the same results as the Matlab  
routines.  
  
If the results are the same, it will write some info file to the  
filesystem to confirm this test was successfully run, otherwise it will  
fail with a description of the discrepancy. In case of failure, fast  
stimulus conversion will not work via the imaging pipeline.  
  
The required parameter 'whichDriver' defines the type of output driver to  
test. It can be any of the following:  
  
\* 'GenericLUT': Test the generic lookup-table based driver that can handle  
arbitrary devices, albeit not with maximum speed. 'whichDriver' must be a  
struct with the following fields:  
  
whichDriver.name = 'GenericLUT'  
  
### Then either one of these for testing of a generic LUT:  
  
whichDriver.bpc = Bitdepths of LUT to test - Anything between 1 and 16.  
whichDriver.nslots = Size of LUT in slots - Anything between 2 and 65536.  
  
Alternatively you can test with an existing self-created LUT:  
whichDriver.lut = A 3 rows by nslots column uint8 matrix which encodes  
the LUT: Rows 1,2 and 3 encode Red, Green and Blue channel, each of the  
'nslots' columns encodes a LUT slot. The driver will map luminance values  
between 0.0 and 1.0 to the corresponding LUT slots in range 1 to nslots,  
then readout the stored column vector with the output RGBA8 pixels to  
poke into the framebuffer.  
  
\* 'VideoSwitcherSimple': Test the "simple" driver for the [VideoSwitcher](VideoSwitcher)  
video attenuator. The simple driver implements a closed-form solution, a  
formula, to map luminance values between 0.0 - 1.0 to output values for  
the Red and Blue channel, just using the 'BTRR' ratio as parameter. This  
is the fast driver, as it doesn't need any lookup tables.  
  
You should provide the whichDriver.btrr BTRR ratio when testing this  
driver. If you omit it, it will be loaded from the configuration file in  
the Psychtoolbox configuration directory.  
  
\* 'VideoSwitcherCalibrated': Test the LUT based driver for the [VideoSwitcher](VideoSwitcher)  
video attenuator. This driver computes the Blue channel value by  
searching for the given luminance value in a 256 entry lookup table, then  
uses a closed-form formula to compute the Red channel drive value from  
the luminance and the looked-up blue channel value. This is slower due to table  
lookups and requires more involved calibration procedures to build a  
lookup table, but it is also potentially more accurate.  
  
You should provide the whichDriver.btrr BTRR ratio when testing this  
driver, as well as the 257 slot whichDriver.lut lookup table for blue  
channel to measured luminance mapping. See help [PsychVideoSwitcher](PsychVideoSwitcher) for  
more info. If you omit these parameters, a default BTRR and LUT will be  
loaded from the Psychtoolbox configuration subdirectory.  
  
### Optional parameters:  
  
whichScreen  = [Screen](Screen) id of display to test on. Will be the secondardy  
               display if none provided.  
  
plotdiffs    = If set to one, plot diagnostic difference images, if any  
               differences are detected. By default no such images are  
               plotted. No images will be plotted if no differences  
               exist.  
  
forcesuccess = Set this to one if you want to force the test to succeed,  
               despite detected errors, ie., if you want the GPU  
               conversion to be used. Only use this if you really know  
               what you are doing!  
  
Please note that this test script can only test if the correct output to  
your systems framebuffer is generated by Psychtoolbox. It can't detect if  
the electronic high precision converter device itself is working  
correctly with this data. Only visual inspection and a  
photometer/colorimeter test can really tell you if the whole system is  
working correctly!  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/HighPrecisionLuminanceOutputDriversImagingPipelineTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/HighPrecisionLuminanceOutputDriversImagingPipelineTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/HighPrecisionLuminanceOutputDriversImagingPipelineTest.m</code>
</div>

