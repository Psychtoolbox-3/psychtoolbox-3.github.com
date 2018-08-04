# [LosslessMovieWritingTest](LosslessMovieWritingTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[LosslessMovieWritingTest](LosslessMovieWritingTest) - Test lossless encoding and decoding of video in movie files.  
  
[LosslessMovieWritingTest](LosslessMovieWritingTest)([codec=huffyuv][, nrchannels=3][, bpc=8])  
  
This test is meant to exercise [Screen](Screen)'s movie writing function with  
different [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) video codecs and to test if specific codecs are  
capable of encoding video without loss of information into a movie file.  
  
The test creates a test image, encodes/writes it into a movie file, then  
reads it back from the movie file and then compares the original test  
image against the image read back from the movie. If lossless encoding  
worked, both images should be identical.  
  
### Optional parameters:  
  
'codec' name of video codec to use. Defaults to huffyuv, for use of the  
lossless [FFMpeg](FFMpeg) Huffman encoder. ffenc\_ljpeg would be another option for  
a lossless codec, however ffenc\_ljpeg can't be decoded by Psychtoolbox's  
[[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) movie playback functions. Another lossless codec is  
'ffenc\_sgi', which allows for lossless encoding and relatively high  
compression rates, but its movie files can only be read by Psychtoolbox,  
not by other tools.  
  
'nrchannels' How many color channels to test: 1, 3, or 4 are possible  
values for grayscale, RGB or RGBA encoding with 8 bpc. For 16 bpc  
encoding, only 1 or 3 channels are possible. Note that most codecs can't  
really encode the alpha channel and discard it instead, so nrchannels=4  
does not actually verify integrity of the alpha channel.  
  
'bpc' Bitdepth for color encoding: 8 is the default, which should work.  
16 is the other allowed option for 16 bpc testing. Most codecs can't  
encode 16 bpc though and will reduce precision to <= 8 bpc. Check the  
code of this script to see how a Psychtoolbox proprietary 16 bpc encoding  
can be used to handle lossless 16 bpc, and how this can be decoded. Only  
Psychtoolbox can handle movies in this proprietary encoding, no other 3rd  
party tools! Other constraints for 16 bpc mode: 1 layer grayscale images  
must have a height for which height \* 2/3 is an integral value. 3 layer  
RGB images must not be wider than 2048 pixels for use with most codecs.  
  
This test script will write the - potentially huge - temporary test file  
into the current working directory and leave it there after the test!  
  
Requires a GPU which can handle at least 4096 x 4096 pixel textures,  
otherwise test failure will occur. The GPU must also support floating  
point textures for \> 8 bpc tests.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/LosslessMovieWritingTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/LosslessMovieWritingTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/LosslessMovieWritingTest.m</code>
</div>

