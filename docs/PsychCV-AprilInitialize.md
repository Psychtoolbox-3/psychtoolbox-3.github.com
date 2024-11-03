# [PsychCV('AprilInitialize')](PsychCV-AprilInitialize) 
##### [Psychtoolbox](Psychtoolbox)>[PsychCV](PsychCV).{mex*} subfunction

[inputImageMemBuffer] = PsychCV('AprilInitialize', tagFamilyName, imgWidth, imgHeight, imgChannels [, imgFormat][, maxNrTags]);

Initialize apriltag prior to first use.  
  
Apriltag markers are loaded for the given apriltag family 'tagFamilyName'.  
The following tag families are currently supported:  
    tag36h11  
    tag25h9  
    tag16h5  
    tagCircle21h7  
    tagCircle49h12    - Use maxNrTags to restrict size!  
    tagCustom48h12    - Use maxNrTags to restrict size!  
    tagStandard41h12  
    tagStandard52h13  - Use maxNrTags to restrict size!  
   
Internal video image memory buffers are set up for input images of size  
'imgWidth' x 'imgHeight' pixels, with 'imgChannels' mono or color channels (1  
MONO, 3 RGB, or 4 RGBA are valid settings, but 1 for MONO is the most efficient  
choice for minimal computation time). For 3 or 4 channels, the input color  
format 'imgFormat' (or a default setting if 'imgFormat' is omitted) defines  
color channel ordering for the input pixel bytes. 'imgFormat' can be one of:  
RGB = 1, BGR = 2, BGRA = 4 (default for 4 channels), ARGB = 7, MONO = 6. Other  
pixel formats are not supported for input images, but these are the ones  
provided by Psychtoolbox's various video capture engines for different video  
sources and settings. For 1 channel mono/grayscale or 3 channel RGB color  
content, you don't need to specify 'imgFormat' as the chosen default will always  
work, but for 4 channel content with alpha channel, you may have to specify  
'imgFormat' if your machine does not return BGRA ordered pixels, but ARGB  
ordered pixels, or marker detection on 4 channel content may fail or perform  
poorly.  
When using a tag family with many potential tags, you can limit the number of  
tags to use to the first 'maxNrTags' tags if you specify 'maxNrTags'. This is  
important for certain large tag families, as using the tag family at its full  
capacity may consume a lot of memory and take a very long time to initialize!  
Then apriltags is initialized, and a memory buffer handle 'inputImageMemBuffer'  
to the internal video memory input buffer is returned.  
  
You should pass this handle to Psychtoolbox functions for videocapture to  
acquire video images from the scene containing the tags, and to store that input  
image inside PsychCV's video buffer.  
  
After this step, you can commence the actual tracking operations by calls to  
[Screen](Screen)()'s video capture engine and the [PsychCV](PsychCV)('AprilDetectMarkers', ...);  
subfunction.  
  


###See also:
[AprilShutdown](PsychCV-AprilShutdown) [AprilDetectMarkers](PsychCV-AprilDetectMarkers) [AprilSettings](PsychCV-AprilSettings) [April3DSettings](PsychCV-April3DSettings)
