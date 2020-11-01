# [PsychGLImageProcessing](PsychGLImageProcessing)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

Psychtoolbox:[PsychGLImageProcessing](PsychGLImageProcessing)  -- [OpenGL](OpenGL) image processing functions.  
  
This subfolder contains subroutines, tests and demos on how to use  
the PTB built-in image processing pipeline.  
  
The built in pipeline provides the infrastructure to define image processing  
or stimulus image postprocessing operations on stimuli drawn by PTB's [Screen](Screen)  
2D drawing commands or MOGL 3D [OpenGL](OpenGL) drawing commands.  
  
The pipeline provides the data flow and API to define type and parameterization  
of the image processing operations. Operations are usually implemented via  
[OpenGL](OpenGL) GLSL shader plugins, vertex & fragment shader programs written in the  
high level [OpenGL](OpenGL) Shading langugage GLSL and executed directly inside the  
graphics processing unit GPU. While this is the most efficient way, operations  
may also be defined in standard [OpenGL](OpenGL) code, Matlab M-Functions or C callable  
functions.  
  
### Typical applications, realized via plugins are:  
  
\* Stereo display algorithms.  
\* High dynamic range display output drivers.  
\* Standard operations like 2D convolution, noise, linear superposition.  
\* Geometric undistortion of displays.  
\* Per pixel output corrections like gamma, color, gain, display PDF.  
  
This part of PTB is under heavy construction. This intro will get extended  
soon with more useful infos...  
  
  
### Files:  
  
[Add2DConvolutionToGLOperator](Add2DConvolutionToGLOperator)  - Create and add a shader for 2D image convolution to a [GLOperator](GLOperator).  
[Add2DSeparableConvolutionToGLOperator](Add2DSeparableConvolutionToGLOperator)  - Create and add a shader for 2D separable image convolution to a [GLOperator](GLOperator).  
[AddImageUndistortionToGLOperator](AddImageUndistortionToGLOperator) - Add geometric image correction to a [GLOperator](GLOperator).  
[AddToGLOperator](AddToGLOperator)               - Add a shader with options to a [GLOperator](GLOperator).  
[BitsPlusPlus](BitsPlusPlus)                  - Setup function for imaging pipelines built-in Bits++ support.  
[CountSlotsInGLOperator](CountSlotsInGLOperator)        - Count number of processing slots in a given [GLOperator](GLOperator).  
[CreateDisplayWarp](CreateDisplayWarp)             - Internal helper function for setup of geometric display undistortion.  
[CreateGLOperator](CreateGLOperator)              - Create a new [GLOperator](GLOperator) as container for imaging operations.  
[CreateProceduralColorGrating](CreateProceduralColorGrating)  - Create a procedural texture for fast drawing of either sinusoidal or square gratings varying between two colors.  
[CreateProceduralGabor](CreateProceduralGabor)         - Create a procedural texture for fast drawing of Gabor patches.  
[CreateProceduralNoise](CreateProceduralNoise)         - Create a procedural texture for fast drawing of random noise patches.  
[CreateProceduralSineGrating](CreateProceduralSineGrating)   - Create a procedural texture for fast drawing of sine grating patches.  
[CreateProceduralSmoothedApertureSineGrating](CreateProceduralSmoothedApertureSineGrating) - Create a procedural texture for fast drawing of smoothed aperture sine grating patches.  
[CreateProceduralSmoothedDisc](CreateProceduralSmoothedDisc)  - Create a procedural texture for fast drawing of smoothed edge discs.  
[CreateProceduralSquareWaveGrating](CreateProceduralSquareWaveGrating) - Create a procedural texture for fast drawing of squarewave grating patches.  
[CreatePseudoGrayLUT](CreatePseudoGrayLUT)           - Create a lookup table for pseudogray conversion - Internal helper function.  
[CreateResolutionPyramid](CreateResolutionPyramid)       - Build a mip-map image resolution pyramid for given texture.  
[CreateSinglePassImageProcessingShader](CreateSinglePassImageProcessingShader) - Create a single pass image processing shader for simple but common operations.  
[DisplayUndistortionBezier](DisplayUndistortionBezier)     - Interactive geometric display calibration for simple needs.  
[DisplayUndistortionBVL](DisplayUndistortionBVL)        - Interactive geometric display calibration. Recommended!  
[DisplayUndistortionCSV](DisplayUndistortionCSV)        - Import ASCII data file with geometric display calibration for [NVidia](NVidia) "Warp API".  
[DisplayUndistortionHalfCylinder](DisplayUndistortionHalfCylinder) - Interactive geometric display calibration for half-cylinder or spherical projections.  
[DisplayUndistortionLabRiggerMouseStim](DisplayUndistortionLabRiggerMouseStim) - Create display undistortion based on method from [LabRigger](LabRigger) for mouse visual stims.  
[DisplayUndistortionSphere](DisplayUndistortionSphere)     - Interactive geometric display calibration for spherical projections.  
[ImagingStereoDemo](ImagingStereoDemo)             - Counterpart to [StereoDemo](StereoDemo), but using imaging pipeline  
                                for increased fidelity, flexibility, ease of use.  
[MakeTextureDrawShader](MakeTextureDrawShader)         - Create GLSL shader for use with [Screen](Screen)('DrawTexture') and [Screen](Screen)('MakeTexture')  
                                to apply on-the-fly texture filtering operations during texture draw.  
  
[PsychHDR](PsychHDR)                      - Support and control stimulus display to HDR "High dynamic range" displays.  
  
[PsychImaging](PsychImaging)                  - Generic setup routine for the imaging pipeline. Allows to setup  
                                and initialize the pipeline for many common tasks.  
  
[PsychVideoSwitcher](PsychVideoSwitcher)            - Setup routine for the Xiangru Li et al. "[VideoSwitcher](VideoSwitcher)" video attenuator device.  
  
[PsychVulkan](PsychVulkan)                   - Interface with the Vulkan graphics and compute api for special purpose tasks.  
  
[SetAnaglyphStereoParameters](SetAnaglyphStereoParameters)       - Function for runtime tuning of Anaglyph stereo parameters,  
                                    see [ImagingStereoDemo](ImagingStereoDemo) for example of use.  
[SetStereoBlueLineSyncParameters](SetStereoBlueLineSyncParameters)   - Change settings for drawing of stereo sync lines in frame-sequential stereo mode.  
[SetStereoSideBySideParameters](SetStereoSideBySideParameters)     - Change parameters for side-by-side stereo display modes (4 and 5).  
[SetCompressedStereoSideBySideParameters](SetCompressedStereoSideBySideParameters) - Change parameters for compressed side-by-side stereo display modes.  
  
[VignetCalibration](VignetCalibration)                 - Vignetted luminance calibration procedure for undistortion of distorted display luminance.  
  
  
Constants for use as 'flipFlags' with the imaging pipeline function  
[Screen](Screen)('HookFunction', windowPtr, 'SetOneshotFlipFlags' ..., flipFlags):  
  
kPsychDontAutoResetOneshotFlags   - Prevent "one-shot" flip flags from being automatically cleared after execution of the next [Screen](Screen)('[Flip](Flip)') operation.  
kPsychSkipSwapForFlipOnce         - Skip [OpenGL](OpenGL) double-buffer swap during execution of next [Screen](Screen)('[Flip](Flip)').  
kPsychSkipTimestampingForFlipOnce - Skip timestamping of [OpenGL](OpenGL) double-buffer swap stimulus onset after execution of next [Screen](Screen)('[Flip](Flip)').  
kPsychSkipVsyncForFlipOnce        - Do not synchronize next [OpenGL](OpenGL) buffer swap to vertical retrace during execution of next [Screen](Screen)('[Flip](Flip)').  
kPsychSkipWaitForFlipOnce         - Do not schedule [OpenGL](OpenGL) buffer swap for specific target time, leave it to some external method.  
  
  
Constants for imagingmode flag of [Screen](Screen)('OpenWindow', ...., imagingmode);  
One can 'or' them together, e.g., imagingmode = mor(kPsychNeed16BPCFixed, kPsychNeedFastBackingStore);  
  
kPsychNeed16BPCFixed          - Request 16 bit per color component, fixed point framebuffer.  
kPsychNeed16BPCFloat          - Request 16 bit per color component, floating point framebuffer.  
kPsychNeed32BPCFloat          - Request 32 bit per color component, floating point framebuffer.  
kPsychNeedDualPass            - Indicate that some of the used image processing plugins will need  
                                at two render passes for processing.  
kPsychNeedFastBackingStore    - Enable minimal imaging pipeline. This flag is implied when using any  
                                of the other flags.  
kPsychNeedFastOffscreenWindows - Only enable support for fast Offscreen windows, nothing else.  
kPsychNeedHalfWidthWindow     - Tell imaging pipe to create internal buffers half the real window width. Internal flag, not useful for end-user code.  
kPsychNeedHalfHeightWindow    - Tell imaging pipe to create internal buffers half the real window height. Internal flag, not useful for end-user code.  
kPsychNeedImageProcessing     - Request explicit support for image processing.  
kPsychNeedMultiPass           - Indicate that some of the used plugins will need more than two passes.  
kPsychNeedOutputConversion    - Indicate that display output is going to some special output device that  
                                needs special output formatting, e.g., Bits++ or Brightside HDR.  
kPsychNeedTwiceWidthWindow    - Tell imaging pipe to create internal buffers twice the real window width. Internal flag, not useful for end-user code.  
kPsychNeedTripleWidthWindow   - Tell imaging pipe to create internal buffers triple the real window width. Internal flag, not useful for end-user code.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/Contents.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/Contents.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/Contents.m</code>
</div>

{{category}}