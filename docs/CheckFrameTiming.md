# [CheckFrameTiming](CheckFrameTiming)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

 [times, badOut, misses]=[CheckFrameTiming](CheckFrameTiming)([rectSize=128][, scale=1][, dur=30][, thresh=0.05][, runPriority=[MaxPriority](MaxPriority)('KbCheck')][, useWhen=0][,useDrawingFinished=1])  
  
 based on [FastMaskedNoiseDemo](FastMaskedNoiseDemo), [CheckFrameTiming](CheckFrameTiming) collects and displays  
 timing info  
  
 rectSize = Size of the generated random noise image: rectSize by rectSize  
            pixels. This is also the size of the Psychtoolbox noise  
            texture.  
  
 scale = Scalefactor to apply to texture during drawing: E.g. if you'd set  
         scale = 2, then each noise pixel would be replicated to draw an image  
         that is twice the width and height of the input noise image. In this  
         demo, a nearest neighbour filter is applied, i.e., pixels are just  
         replicated, not bilinearly filtered -- Important to preserve statistical  
         independence of the random pixel values!  
  
 dur   = seconds to display  
  
 thresh = percent deviation to report as a miss (specify 5% as 0.05)  
  
 runPriority = the priority at which to run  
  
 useWhen = 0 for no when parameter sent to [Screen](Screen)('[Flip](Flip)') (seems to give  
           better timing.  any other value sends lastVbl + .5\*ifi  
  
 useDrawingFinished = 0 to use [Screen](Screen)('DrawingFinished'). mario's comment  
                      suggets it may slow thigns down, but edf thinks it is supposed to speed  
                      things up and only printing its return value would slow things down.  
  
return vals:  
times is a vector of inter-vbl-times as measured by [Screen](Screen)('[Flip](Flip)')  
badOut is 3 x N, with one column for each frame whose time deviates by more than thresh % from the ifi  
   row 1 is the frame number  
   row 2 is the measured frame time  
   row 3 is the % deviation from ifi  
misses are the frame numbers that [Screen](Screen)('[Flip](Flip)') noticed it missed  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/CheckFrameTiming.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/CheckFrameTiming.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/CheckFrameTiming.m</code>
</div>

