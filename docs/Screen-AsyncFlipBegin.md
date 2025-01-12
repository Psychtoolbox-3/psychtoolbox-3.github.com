# [Screen('AsyncFlipBegin')](Screen-AsyncFlipBegin) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

[VBLTimestamp StimulusOnsetTime FlipTimestamp Missed Beampos] = Screen('AsyncFlipBegin', windowPtr [, when] [, dontclear] [, dontsync] [, multiflip]);

Schedule an asynchronous flip of front and back display surfaces for given  
onscreen window.  
"windowPtr" is the id of the onscreen window whose content should be shown at  
flip time. "when" is the requested stimulus onset time, a value of zero or no  
argument asks for flip at next possible vertical retrace.  
For the meaning and explanation of all other parameters, see the help for  
'[Screen](Screen) [Flip](Flip)?'.  
  
If this command is called while a previously scheduled asynchronous flip is  
still in progress, it will wait for that pending async flip to finish and return  
its results (timestamps etc.). If no such operation is in progress, it will  
return results of the most recently finished async or sync flip. Waiting for  
previous flips to complete and returning their results is a convenience  
function. In most cases, in order to have more control over the execution of  
your script and your flip timing, you will rather want to use one of the  
finalizer commands [Screen](Screen)('AsyncFlipCheckEnd') or [Screen](Screen)('AsyncFlipEnd')  
mentioned below to collect information about the final result and timing of the  
asynchronous flip operation.  
  
The difference between [Screen](Screen)('AsyncFlipBegin',...); and the more commonly used  
[Screen](Screen)('[Flip](Flip)', ...); is that [Screen](Screen)('[Flip](Flip)') operates synchronously: Execution of  
your code is paused until the flip operation has finished, ie. at least until  
the requested onset deadline 'when' has passed.  
  
[Screen](Screen)('AsyncFlipBegin') will prepare everything for a flip at the requested  
time 'when' - or at next vertical retrace if 'when' is omitted - but then  
immediately return control to your code. Your code can continue to execute and  
do other things, e.g., schedule flips for other onscreen windows, perform  
keyboard or mouse queries, etc.  
  
You can check the progress state of asynchronous flips or wait for them to  
finish and collect timing information for the finalized flip by use of the  
commands [Screen](Screen)('AsyncFlipCheckEnd') and [Screen](Screen)('AsyncFlipEnd');  
  
In general you should avoid using asynchronous flips and instead use  
conventional '[Flip](Flip)' unless you have a good reason to do otherwise, because async  
flips come with a couple of strings attached:  
  
- You are restricted in what you can do with [Screen](Screen)() or [OpenGL](OpenGL) while async  
  flips are in progress: You can not do anything with textures or offscreen  
  windows while their parent-onscreen window is in async flip state. You can  
  only access onscreen windows which are not participating in an async flip  
  operation.  
  
- If you enable the Psychtoolbox image processing pipeline, most restrictions  
  on drawing during async flips are relaxed: You can draw into any windows while  
  async flips are pending, even the window for which the flip is pending. Only  
  use of the [Screen](Screen)('GetImage') command is forbidden on async flipping onscreen  
  windows and potentially problematic on offscreen windows while an async flip  
  is in progress. However, this is somewhat theoretical. In practice many  
  operating systems, graphics drivers and graphics cards can't really handle the  
  load of parallel drawing and async flipping, due to system bugs or design  
  constraints. On such systems you may observe inconsistent timing, degraded  
  performance, and on some systems even visual stimulus corruption, malfunctions  
  or hard system crashes [e.g., Apple [MacOS](MacOS)/X 10.4.11 with ATI Radeon X1600]!  
  
- Even the restricted set of allowed reliably working [Screen](Screen)/[OpenGL](OpenGL) commands  
  should be avoided, because some graphics hardware and drivers may not be  
  able to handle such concurrent graphics operations without degraded stimulus  
  onset timing accuracy, ie. you may experience more missed stimulus deadlines  
  and timing glitches -- or inconsistent behaviour accross different computers  
  and graphics cards or operating system releases. In the end it allows you to  
  do non-[Screen](Screen) related things like sound, I/O, keyboard checks...  
  
- Parallel processing of flips puts additional burden onto your CPU,  
  GPU and operating system, so it incurs additional overhead and may degrade  
  absolute drawing performance and cause more timing issues and glitches if  
  your system is not reliably able to handle the concurrent load.  
  
- Code with async flips - as any piece of parallely executing code - is harder  
  to implement correctly and more challenging to debug for you.  
  
- Using a non-zero "multiflip" argument is not allowed.  
  
- Asynchronous updates of gamma tables will likely not work reliably.  
  
- Stereo stimulus display in stereomode 10 (two separate onscreen windows) will  
  likely not work with reliable timing or have possible tearing artifacts.  
  
- Use of the 'UserspaceBufferDrawingPrepare' hook-chain of the imaging  
  pipeline is not allowed.  
  
  
Our general stance is that most code can be written efficiently without need for  
async flips, so this feature is provided for the few demanding special cases  
where this is not the case and the benefits outweight the costs.  


###See also:
[DrawingFinished](Screen-DrawingFinished) [WaitUntilAsyncFlipCertain](Screen-WaitUntilAsyncFlipCertain) [AsyncFlipBegin](Screen-AsyncFlipBegin) [AsyncFlipCheckEnd](Screen-AsyncFlipCheckEnd) [AsyncFlipEnd](Screen-AsyncFlipEnd) Flip
