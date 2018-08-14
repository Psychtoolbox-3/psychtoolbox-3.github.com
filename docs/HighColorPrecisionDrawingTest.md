# [HighColorPrecisionDrawingTest](HighColorPrecisionDrawingTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[HighColorPrecisionDrawingTest](HighColorPrecisionDrawingTest)([testconfig][, maxdepth][, testblocks][, plotit=0])  
  
Test for numeric drawing precision of your graphics card (GPU). Exercises  
a number of tests, where some 2D drawing primitive(s) is drawn in some  
well defined color, then the content of the framebuffer is read back and  
compared against expected results computed via Matlab code in double  
precision. The Matlab code emulates the expected behaviour of an ideal  
GPU that works at a precision higher than that of any real GPU.  
Difference between exptected and actual results is calculated for each  
tested pixel location and the maximum error is stored. Each test case  
plots that maximum error to the Matlab window. From the maximum error  
value, we also derive the maximum bitdepths of an output device for which  
the error would be negligible, ie., the difference would not show up in  
any measurable way because the deviation is too small to have any effect  
on the display device.  
  
The actual results of the tests depends on a number of conditions like  
tested precision range, selected precision of the framebuffer,  
alpha-blending mode (if any), texture filtering mode (if textures are  
used as drawing primitive), mode of operation of PTB, operating system  
etc. For that reason you can specify the exact test conditions via a  
number of arguments to this function -- Displayed test results will only  
be valid for that exact configuration, so if you want to evaluate  
suitability of your hardware+OS combo for a given type of visual  
stimulus, make sure you choose a test configuration to closely matches  
the one used in your stimulus presentation script.  
  
The test itself is currently in a BETA stage! While many of the test  
cases seem to work reliably on a variety of tested hardware, there may be  
(untested) hardware+OS combos for which the tests display effective  
precision numbers that are lower than the ones really achieved by your  
hardware -- the test is too pessimistic. So USE WITH CARE, DON'T TRUST  
THE TEST BLINDLY and APPLY COMMON SENSE when looking at the results.  
  
### Optional parameters and their meaning:  
  
'testconfig' is a vector that defines the framebuffer and PTB  
configuration to use. All elements have defaults:  
  
Colorclamping (aka high-precision vertex colors vs. standard vertex colors)  
-1 / 0 / 1 = Unclamped high-res via shader / Unclamped high-res / Clamped.  
             Default is 0 == Let PTB auto-select opmode with highest  
             precision. A setting of -1 overrides PTB's choice to always  
             use an internal implementation -- If auto-detection works  
             perfectly this should not give better results than mode 0,  
             but no automatic is perfect, so it doesn't hurt to test that  
             mode. 1 is "low-precision, clamped" mode: It shouldn't ever  
             give better results than -1 or 0 and is normally only used  
             for standard 8 bit precision output of standard stimuli  
             where bit-accurate output doesnt' matter too much.  
  
Framebuffer: (aka bit-depth and format of framebuffer)  
0 / 1 / 2 / 3/ 4 = 8 bpc fixed, 16bpc float, 32bpc float, 32bpc float  
             if possible while alpha-blending enabled 16bpc otherwise,  
             16bpc fixed point (on ATI hardware only).  
  
             Precision with which the framebuffer operates: 8 bpc fixed  
             is a standard 8 bits per precision 256 levels framebuffer.  
             16bpc float allows for an effective 10-11 bit precision,  
             32bpc float allows for an effective 23 bit precision, 16 bpc  
             fixed is only supported on ATI hardware and allows for an  
             effective 16 bit precision, but without alpha-blending  
             support.  
  
             Selected precision is a accuracy vs. speed & functionality  
             tradeoff. Higher resolution means higher output precision  
             and higher precision for calculation of intermediate  
             results. However it means also more memory usage, slower  
             processing and drawing speed and - on some hardware - it  
             means that alpha-blending and anti-aliasing doesn't work or  
             works only very slowly. Therefore you need to select a mode  
             that is good enough for your purpose. [Direct3D](Direct3D) 10 compliant  
             hardware from [NVidia](NVidia) and ATI (Geforce 8000 and later, Radeon  
             HD 2000 and later) is supposed to have no relevant  
             limitations wrt. to functionality or precision anymore -- It  
             can carry out all operations including alpha-blending etc.  
             at highest precision (32 bpc float). If you happen to have  
             such hardware then the only reason to choose less than  
             maximum precision is speed -- Lower precision is still  
             processed faster.  
  
             Please also note that the attainable precision of all the  
             test cases in this script is of course limited by the  
             precision of the framebuffer. E.g., if you chose a 16bpc  
             float framebuffer, none of the tests will be able to attain  
             more than about 10-11 bits of precision.  
  
  
Textures: (aka texture precision)  
0 / 1 / 2 = 8 bpc fixed, 16bpc float, 32bpc float.  
  
             Precision with which textures are represented -- and  
             ultimately drawn. Same explanations apply as with  
             'Framebuffer'. However, there is no limitation in  
             functionality associated with high texture precision: Should  
             the hardware have some limitations, PTB will work-around  
             them. Higher precision textures still incur higher storage  
             requirements and lower drawing speeds though, so don't use  
             higher precision than you really need!  
  
Samplers: (aka texture sampling method)  
0 / 1 / 2 = Hardware / PTB-Auto / PTB-Shaders.  
  
             Method employed for texture drawing: PTB-Auto is the  
             preferred choice -- Let PTB auto-select best method for  
             given texture precision and other requirements. However you  
             can manually override to always use PTB-Shaders (built-in  
             workarounds for less capable hardware) or Hardware  
             implementation of your GPU -- usually faster, but maybe less  
             precise.  
  
Filters: (aka texture filtering method)  
0 / 1     = Nearest-Neighbour / Bilinear filtering.  
  
            Method of filtering texture pixels before drawing:  
            Nearest-Neighbour just uses pixels as they are -- blocky or  
            aliased appearance if you draw rotated textures, textures  
            where the 'srcRect' and 'dstRect' parameters in  
            [Screen](Screen)('DrawTexture') don't exactly match in size, and no way  
            of "scrolling" or positioning textures with subpixel  
            accuracy. However, also no loss in precision due to filtering  
            artifacts caused by low precision filtering hardware.  
            'Bilinear filtering' always provides perfectly anti-aliased  
            and smooth looking textures due to use of bilinear filtering,  
            but may introduce a slight loss of precision if your hardware  
            doesn't sample accurately. See [DriftTexturePrecisionTest](DriftTexturePrecisionTest) for  
            an extra test of filter accuracy of your GPU.  
  
  
'maxdepth' parameter: Choose the maximum precision for which the  
test-cases test your hardware. Defaults to 16 bits and is restricted to  
about 18 bits by the current implementation of this test script. 16 bits  
is chosen because there aren't any display devices with more than 14 bit  
output precision available on the market, so 16 bits is "good enough" for  
most purposes. Plese note that even if your GPU is able to provide much  
more than 'maxdepth' bits of precision, the test won't detect that -- it  
will only test up to 'maxdepth' bits of precision!  
  
  
'testblocks' parameter: A vector of tests to carry out. By default all  
tests are carried out and each single test is interruptible by holding  
down the left mouse button for a while. However this may take quite long  
-- dozens of minutes, maybe even over an hour! For that reason you can  
specify your own 'testblocks' vector to only run a subset of all test  
cases and save some time.  
  
### The following test cases are currently implemented:  
  
1  = Test precision of clearing of the framebuffer to selected  
     'clearcolor'. 'clearcolor' is set in [Screen](Screen)('OpenWindow') or  
     [PsychImaging](PsychImaging)('OpenWindow') etc. or via [Screen](Screen)('FillRect', window,  
     clearcolor). Framebuffer clearing is performed after each  
     [Screen](Screen)('[Flip](Flip)') or [Screen](Screen)('FillRect', window, clearcolor) command and  
     this test tests precision of that operation.  
  
2  = Test precision of [Screen](Screen) 2D drawing commands like [FillRect](FillRect),  
     [FrameRect](FrameRect), [FillOval](FillOval), [FrameOval](FrameOval), [DrawLine](DrawLine) etc.  
  
3  = Test precision of [Screen](Screen) 2D batch-drawing commands, ie. commands  
     that allow to draw multiple primitives per command, e.g., [DrawDots](DrawDots),  
     [DrawLines](DrawLines) and the batch versions of [FillRect](FillRect), [FrameRect](FrameRect), [FillOval](FillOval)  
     etc.  
     Also tests precision of the 'DrawTexture' command and of the  
     built-in gamma correction mechanism of PTB when used with the PTB  
     imaging pipeline, e.g., in Mono++ or Color++ mode of a CRS Bits++  
     box.  
  
4  = Test precision of texture drawing commands when the special  
     'globalAlpha' or 'modulateColor' arguments are used to modulate the  
     textures pixel values during drawing -- for example for contrast  
     selection.  
  
5  = Test of precision of alpha-blending: Does use of the alpha-blending  
     function via [Screen](Screen)('BlendFunction') introduce any loss of numeric  
     stimulus precision - and if so, how much?  
  
     This testcase 5 is incomplete and under development!  
  
6  = Test of color precision of text drawing. This only tests to a fixed  
     precision of 8 bits for 256 levels at the moment, as our the text  
     renderer doesn't have a higher precision.  
  
'plotit' parameter: If set to 1, output some error plots after tests where it  
makes sense. No plotting happens by default.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/HighColorPrecisionDrawingTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/HighColorPrecisionDrawingTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/HighColorPrecisionDrawingTest.m</code>
</div>

