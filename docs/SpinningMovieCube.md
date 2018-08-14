# [SpinningMovieCube](SpinningMovieCube)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)>[OpenGL4MatlabDemos](OpenGL4MatlabDemos)

[SpinningMovieCubeDemo](SpinningMovieCubeDemo) - Demonstrate use of MATLAB-[OpenGL](OpenGL) toolbox  
  
This demo demonstrates use of [OpenGL](OpenGL) commands in a Matlab script together  
with the movie playback functions of PTB. It shows a randomly  
spinning, three dimensional textured cube. The six sides of the cube  
show a quicktime video, loaded and played from a quicktime movie file.  
  
Stop the demo any time by pressing any key.  
  
### Notable implementation details:  
  
The implementation is nearly identical as [SpinningCubeDemo](SpinningCubeDemo), so make sure  
you understand that file first.  
  
This demo uses the [Screen](Screen)('GetOpenGLTexture') function to make a  
Psychtoolbox texture  (loaded from the movie) available to  
[OpenGL](OpenGL) for 3D texture mapping.  
  
It opens a movie file and then - in a loop - fetches video images frame  
by frame. The images which are stored as Psychtoolbox textures are then  
made available as standard [OpenGL](OpenGL) textures for drawing onto the sides of  
the spinning cube.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/OpenGL4MatlabDemos/SpinningMovieCube.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/OpenGL4MatlabDemos/SpinningMovieCube.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/OpenGL4MatlabDemos/SpinningMovieCube.m</code>
</div>

