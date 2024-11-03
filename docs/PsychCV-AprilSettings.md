# [PsychCV('AprilSettings')](PsychCV-AprilSettings) 
##### [Psychtoolbox](Psychtoolbox)>[PsychCV](PsychCV).{mex*} subfunction

[nrThreads, imageDecimation, quadSigma, refineEdges, decodeSharpening, criticalRadAngle, deglitch, maxLineFitMse, minWhiteBlackDiff, minClusterPixels, maxNMaxima] = PsychCV('AprilSettings' [, nrThreads][, imageDecimation][, quadSigma][, refineEdges][, decodeSharpening][, criticalRadAngle][, deglitch][, maxLineFitMse][, minWhiteBlackDiff][, minClusterPixels][, maxNMaxima]);

Return current tracker parameters, optionally change tracker parameters.  
These settings are set to reasonable defaults at startup, but can be changed  
anytime with this subfunction. Most of these settings define tradeoffs between  
computation time aka tracking speed and quality/robustness of tracking.  
Following settings are available:  
'nrThreads' Number of processing threads to use for speeding up operation.  
Default is 1 for single-threaded operation.  
'imageDecimation' 1 = Process full image. \> 1 = Only work on resolution  
decimated image for higher speed at lower precision. Default is 2.  
'quadSigma' How much blurring (values \> 0) or sharpening (values < 0) to apply  
to input images to reduce noise. Default is 0 for none.  
'refineEdges' 1 = Perform edge refinement on detected edges (cheap, and the  
default), 0 = Use simpler strategy.  
'decodeSharpening' How much sharpening should be done to decoded images? Can  
help small tags. Default is 0.25.  
'criticalRadAngle' How close pairs of edges can be to straight before rejection.  
0 = Don't reject. Default is 10 degrees.  
'deglitch' Should the thresholded image be deglitched (1) or not (0)? Only  
useful for very noisy images. Default is 0 for false.  
'maxLineFitMse' When fitting lines to contours, what is the maximum mean squared  
error allowed? For rejecting contours far from quad shape. Default is 10.0.  
'minWhiteBlackDiff' How much brighter (in pixel values 0 - 255) must white  
pixels be than black pixels? Default is 5.  
'minClusterPixels' Reject quads containing less than this number of pixels.  
Default is 5.  
'maxNMaxima' How many corner candidates to consider when segmenting a group of  
pixels into a quad. Default is 10.  
  


###See also:
[AprilDetectMarkers](PsychCV-AprilDetectMarkers)
