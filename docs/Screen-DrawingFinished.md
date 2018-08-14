# [Screen('DrawingFinished')](Screen-DrawingFinished) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Tell Psychtoolbox that no further drawing commands will be issued to 'windowPtr'  
before the next [Screen](Screen)('[Flip](Flip)') or [Screen](Screen)('AsyncFlipBegin') command.  
  
This is a hint that allows to optimize drawing performance on some occasions.  
Don't issue this command multiple times between a [Flip](Flip), it will degrade  
performance or even cause undefined stimulus display!  
  
You must provide the same value for 'dontclear' flag that you're going to pass  
to the following [Flip](Flip) command, if you pass such an optional flag to the [Flip](Flip)  
command.  
  
You can time the execution of all drawing commands between the most recent [Flip](Flip)  
and this command by setting the optional flag sync=1. In that case, telapsed is  
the elapsed time at drawing completion. Don't set the sync - Flag for real  
experiments, it will degrade performance!  
  
Some recent graphics cards provide a more fine-grained way to measure the time  
spent drawing and processing your stimulus. See the help of '[Screen](Screen)  
[GetWindowInfo](GetWindowInfo)?' about 'infoType' settings 5 and 6 on how to use that mechanism.  
That method also has the advantage of measuring precise without degrading  
overall performance.  


###See also:
Flip [AsyncFlipBegin](Screen-AsyncFlipBegin)
