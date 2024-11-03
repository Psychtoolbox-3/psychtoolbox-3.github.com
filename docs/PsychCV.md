# [PsychCV](PsychCV)
##### [Psychtoolbox](Psychtoolbox)>[PsychCV](PsychCV)

PsychCV - Helper module for miscellaneous functionality related to image processing and/or computer vision:  
  
Copyright 2008 - 2024 Mario Kleiner. Licensed under MIT license. For potential statically included libraries,  
see licenses below. This module employs various different 3rd party software, so here are the credits for those parts:  
  
The 'Aprilxxx' subfunctions for April tag tracking are implemented by use of the apriltag library from:  
https://april.eecs.umich.edu/software/apriltag and https://github.com/AprilRobotics/apriltag .  
The apriltag library is licensed under BSD-2 clause license. See Psychtoolbox main License.txt file for details.  
  
  
General information and settings:  
  
version = PsychCV('[Version](PsychCV-Version)');  
oldlevel = PsychCV('[Verbosity](PsychCV-Verbosity)' [,level]);  
  
Helper functions for memory buffer copies:  
  
PsychCV('[CopyMatrixToMemBuffer](PsychCV-CopyMatrixToMemBuffer)', matrix, memBufferPtr);  
  
Support for the apriltag 2D/3D april tag marker tracking library:  
  
[inputImageMemBuffer] = PsychCV('[AprilInitialize](PsychCV-AprilInitialize)', tagFamilyName, imgWidth, imgHeight, imgChannels [, imgFormat][, maxNrTags]);  
[detectedMarkers] = PsychCV('[AprilDetectMarkers](PsychCV-AprilDetectMarkers)'[, markerSubset=all][, infoType=all]);  
PsychCV('[AprilShutdown](PsychCV-AprilShutdown)');  
[nrThreads, imageDecimation, quadSigma, refineEdges, decodeSharpening, criticalRadAngle, deglitch, maxLineFitMse, minWhiteBlackDiff, minClusterPixels, maxNMaxima] = PsychCV('[AprilSettings](PsychCV-AprilSettings)' [, nrThreads][, imageDecimation][, quadSigma][, refineEdges][, decodeSharpening][, criticalRadAngle][, deglitch][, maxLineFitMse][, minWhiteBlackDiff][, minClusterPixels][, maxNMaxima]);  
[glProjectionMatrix, camCalib, tagSize, minD, maxD] = PsychCV('[April3DSettings](PsychCV-April3DSettings)' [, camCalib][, tagSize][, minD][, maxD]);  
  

 PsychCV is a MEX file for computer-vision applications. PsychCV has  
 many functions; type "PsychCV" for a list:  
    PsychCV  
  
 Please note that PsychCV is only supported on recent platforms, e.g.,  
 Matlab versions 7.4 (R2007a) and later or Octave-3 on Windows, and only  
 on Intel based Macintosh computers under OS/X but not on PowerPC  
 machines.  
  
  


