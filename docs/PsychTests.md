# [PsychTests](PsychTests)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

Psychtoolbox/[PsychTests](PsychTests)/Contents.m  
  
  
  [AlphaAdditionTest](AlphaAdditionTest)               - Combine planes by [OpenGL](OpenGL) alpha addition and verify the result.  
  [AlphaBlendingTest](AlphaBlendingTest)               - Multiple tests of [OpenGL](OpenGL) alpha blending.  
  [AlphaBlendSettingTest](AlphaBlendSettingTest)           - Set and readback alpha blending settings by screen; verify match.  
  [AlphaMultiplicationTest](AlphaMultiplicationTest)         - Test alpha multiplication by 0 and 1 for perfect precision.  
  [AlphaMultiplicationAccuracyTest](AlphaMultiplicationAccuracyTest) - Test precision of alpha multiplication for values between 0 and 1.  
  [AnalyzeTiming](AnalyzeTiming)                   - Analyze timing logs from [FlipTimingWithRTBoxPhotoDiodeTest](FlipTimingWithRTBoxPhotoDiodeTest).  
  [AsyncFlipTest](AsyncFlipTest)                   - Test robustness and performance of [Screen](Screen)('AsyncFlipBegin') et al.  
  [BatchAnalyzeTiming](BatchAnalyzeTiming)              - Batch version of [AnalyzeTiming](AnalyzeTiming).  
  [BeampositionTest](BeampositionTest)                - Test GPU scanout position ("beamposition") queries.  
  [CIEConeFundamentalsTest](CIEConeFundamentalsTest)         - Test/demonstrate routines for producing cone fundamentals according to CIE 170-1:2006  
  [CIEConeFundamentalsFieldSizeTest](CIEConeFundamentalsFieldSizeTest) - Test behavior of underying formulae as field size exceeds the 10-deg limit of the standard.  
  [CIEXYZPhysTest](CIEXYZPhysTest)                  - Test properties of CIE physiological XYZ color matching function.  
  [CLUTMappingBugTest](CLUTMappingBugTest)              - Test proper function of [PsychImaging](PsychImaging) 'EnableCLUTMapping' task.  
  [Color3DLUTTest](Color3DLUTTest)                  - Test [PsychColorCorrection](PsychColorCorrection)() method for 3D-CLUT color correction.  
  [ConvolutionKernelTest](ConvolutionKernelTest)           - Test routine for correctness, accuracy and speed of PTB imaging convolution shaders.  
  [DatapixxGPUDitherpatternTest](DatapixxGPUDitherpatternTest)    - Low level diagnostic of GPU dithering bugs via Datapixx et al.  
  [DeinterlacerTest](DeinterlacerTest)                - Simple correctness test for GLSL video image deinterlacer. INCOMPLETE.  
  [DrawingIntoTexturesTest](DrawingIntoTexturesTest)         - Tests if using a texture as an offscreen window, i.e., for drawing, works.  
  [DrawTextFontSwitchSpeedTest](DrawTextFontSwitchSpeedTest) - Test speed of text drawing when switching between different font type/style/size settings.  
  [DriftTexturePrecisionTest](DriftTexturePrecisionTest)       - Test subpixel accuracy of texture interpolators: What is the smallest  
                                    fraction of a pixel that one can scroll, using built-in bilinear interpolation?  
  eGalaxTrace-\*.evemu             - Linux evdev traces with recorded single/multi-touch input from an eGalax touchscreen.  
  [FitCumNormYNTest](FitCumNormYNTest)                - Fit a cumulative normal to yes-no data.  
  [FlipTestConfigurations](FlipTestConfigurations).zip      - Input configuration files for [FlipTimingWithRTBoxPhotoDiodeTest](FlipTimingWithRTBoxPhotoDiodeTest).m  
  [FlipTimingWithRTBoxPhotoDiodeTest](FlipTimingWithRTBoxPhotoDiodeTest) - Benchmark of visual stimulus onset timing and timestamping. See ECVP 2010 poster in [PsychDocumentation](PsychDocumentation)/  
  [CopyWindowTest](CopyWindowTest)                  - Test [CopyWindow](CopyWindow) functionality.  
  [DaqTest](DaqTest)                         - Test [PsychHID](PsychHID) and routines to control the  USB-1208FS digital acquistion device.  
  [DrawingStuffTest](DrawingStuffTest)                - [FrameRect](FrameRect), [DrawLine](DrawLine), [FillPoly](FillPoly), [FramePoly](FramePoly).  
  [FillPolyTest](FillPolyTest)                    - Test drawing concave polygons.  
  [FitConeFundamentalsTest](FitConeFundamentalsTest)         - Test/explore fitting CIE cone fundamentals with absorbance obtained from nomograms.  
  [FitWeibullTAFCTest](FitWeibullTAFCTest)              - Fit a Weibull to 2AFC data.  
  [FitWeibullYNTest](FitWeibullYNTest)                - Fit a Weibull to yes-no data.  
  [FloatTexturePrecisionTest](FloatTexturePrecisionTest)       - Test effective precision of floating point 16bpc textures.  
  [FrameSequentialStereoTest](FrameSequentialStereoTest)       - Test routine for timing and stimulus onset on quad-buffered frame-sequential stereo hardware.  
  [GetCharTest](GetCharTest)                     - Tests of [GetChar](GetChar).  
  [GetSecsTest](GetSecsTest)                     - Timing test of clock used by Psychtoolbox, e.g., [GetSecs](GetSecs), [WaitSecs](WaitSecs), [Screen](Screen)...  
  [GraphicsDisplaySyncAcrossDualHeadsTest](GraphicsDisplaySyncAcrossDualHeadsTest) - Test synchronization of refresh cycles of different display heads.  
  [GraphicsDisplaySyncAcrossDualHeadsTestLinux](GraphicsDisplaySyncAcrossDualHeadsTestLinux) - Linux version of the test.  
  [HDRTest](HDRTest)                         - Perform some basic correctness tests and evaluation for HDR display operation, using a Colorimeter.  
  [HIDIntervalTest](HIDIntervalTest)                 - [Sample](Sample) HID keyboard and mouse, plot distribution of detected event times.  
  [HighColorPrecisionDrawingTest](HighColorPrecisionDrawingTest)   - Test drawing precision of a variety of [Screen](Screen)() functions, esp. wrt. high precision framebuffers.  
  [HighPrecisionLuminanceOutputDriversImagingPipelineTest](HighPrecisionLuminanceOutputDriversImagingPipelineTest) - Test precision of a variety of high precision luminance device output drivers.  
  [JavaClockTest](JavaClockTest)                   - Timing test of clock used by Java functions (e.g. [GetChar)](GetChar))  
  [KeyboardLatencyTest](KeyboardLatencyTest)             - Get a feeling for keyboard and mouse latency via some sound-based measurement procedure.  
  [LabLuvTest](LabLuvTest)                      - Test routines that convert to CIELAB and CIELUV.  
  [LoadGenerator](LoadGenerator)                   - Create cpu load by spinning in an infinite loop. Used in conjunction with [FlipTimingWithRTBoxPhotoDiodeTest](FlipTimingWithRTBoxPhotoDiodeTest).  
  [LosslessMovieWritingTest](LosslessMovieWritingTest)        - Test lossless encoding and decoding of video in movie files.  
  [MakeTextureTimingTest](MakeTextureTimingTest)           - Time texture creation -\> upload -\> destruction for given texture by [MakeTexture](MakeTexture) et al.  
  [MelanopsinFundamentalTest](MelanopsinFundamentalTest)       - Test the PTB routines generate a good melanopsin fundamental.  
  [MonoImageToSRGBTest](MonoImageToSRGBTest)             - Test/demo for routine [PsychColorimetric](PsychColorimetric)/[MonoImageToSRGB](MonoImageToSRGB).  
  [MultiWindowLockStepTest](MultiWindowLockStepTest)         - Exercise asynchronous flip scheduling and timestamping on multiple onscreen windows in parallel.  
  [MultiWindowVulkanTest](MultiWindowVulkanTest)           - Test multi-window / multi-display exclusive operation under Vulkan.  
  [[OSAUCSTest](OSAUCSTest)][(OSAUCSTest)]((OSAUCSTest))                      - Test OSA UCS <-\> XYZ conversion routines.  
  [OSXCompositorIdiocyTest](OSXCompositorIdiocyTest)         - Test for potential OSX compositor brokeness.  
  [OMLBasicTest](OMLBasicTest)                    - Very basic correctness test for [OpenML](OpenML) flip timestamping.  
  [OSSchedulingAccuracyTest](OSSchedulingAccuracyTest)        - Test timing accuracy of operating system scheduler for timed waits.  
  [PBTAndIsetbioColorimetryTest](PBTAndIsetbioColorimetryTest)    - Compare PTB and VSET colorimetric calculations.  
  [PosterBatchAnalyzeTimestamps](PosterBatchAnalyzeTimestamps)    - Batch analysis of timestamp logs generated by [FlipTimingWithRTBoxPhotoDiodeTest](FlipTimingWithRTBoxPhotoDiodeTest) for ECVP 2010 poster.  
  [PupilDiameterTest](PupilDiameterTest)               - Test functions that compute pupil diameter from luminance.  
  [PutImageTest](PutImageTest)                    - Test [Screen](Screen)('PutImage') when used with 'NormalizedHighresColorRange'.  
  [PsychPortAudioDataPixxTimingTest](PsychPortAudioDataPixxTimingTest) - Test PsychPortAudio's timing with a [DataPixx](DataPixx) device and a audio line cable.  
  [PsychPortAudioTimingTest](PsychPortAudioTimingTest)        - Testsignal generator for test of [PsychPortAudios](PsychPortAudios) timing with external measurement equipment.  
  [QuestTest](QuestTest)                       - Some [Quest](Quest) simulations, more elaborate than [QuestDemo](QuestDemo).  
  [ResolutionTest](ResolutionTest)                  - Use [Screen](Screen) Resolutions to print table of display resolutions.  
  [RodFundamentalTest](RodFundamentalTest)              - Test the PTB routines generate a good rod fundamental.  
  [StructsFileTest](StructsFileTest)                 - Test routines for reading and writing struct arrays to text files.  
  [SyncedCLUTUpdateTest](SyncedCLUTUpdateTest)            - Visual test of clut write synching to vertical retrace.  
  [TextBoundsTest](TextBoundsTest)                  - Test [Screen](Screen)('TestBounds')  
  [TextBugTest](TextBugTest)                     - Look for interference between  
  [TextInitBugTest](TextInitBugTest)                 - Test for failure of 'DrawText' default font.  
  [TextInOffscreenWindowTest](TextInOffscreenWindowTest)       - Compare text rendered into onscreen and offscreen windows.  
  [TextOffByOneBugTest](TextOffByOneBugTest)             - Tests for fix off an off-by-one bug in [Screen](Screen)('Drawtext').  
  [TextToStuffColorMismatchTest](TextToStuffColorMismatchTest)    - Test if text is drawn in the color it was requested to be drawn.  
  [TextureChannelsTest](TextureChannelsTest)             - Test assignment of matrix layers to RGBA texture channels.  
  [TextureSharingTest](TextureSharingTest)              - Test [OpenGL](OpenGL) context resource sharing.  
  [TrolandTest](TrolandTest)                     - Test colorimetric conversions.  
  [VBLSyncTest](VBLSyncTest)                     - Tests visual stimulus onset timing and timestamping.  
  [VREyetrackingTest](VREyetrackingTest)               - Test eye gaze tracking in VR/AR [HMDs](HMDs) and other XR devices.  
  [VRRFixedRateSwitchingTest](VRRFixedRateSwitchingTest)       - Test support for fast refresh rate switching on AMD+Linux via VRR mechanisms.  
  [VRRTest](VRRTest)                         - Test support of your setup for Variable refresh rate mode.  
  [WavelengthSamplingTest](WavelengthSamplingTest)          - Test conversion between representations of wavelength sampling information.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/Contents.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/Contents.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/Contents.m</code>
</div>

{{category}}