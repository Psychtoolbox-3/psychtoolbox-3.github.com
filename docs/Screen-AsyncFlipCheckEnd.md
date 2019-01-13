# [Screen('AsyncFlipCheckEnd')](Screen-AsyncFlipCheckEnd) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

[VBLTimestamp StimulusOnsetTime FlipTimestamp Missed Beampos] = Screen('AsyncFlipCheckEnd', windowPtr);

Check if a previously scheduled asynchronous flip operation has completed (see  
[Screen](Screen) [AsyncFlipBegin](AsyncFlipBegin)? for help).  
This command will check for completion on onscreen window "windowPtr", then  
return the result of the operation, ie. all the stimulus onset timestamps and  
other diagnostic information. See help for [Screen](Screen) [Flip](Flip)? for explanation of the  
returned info. If the operation hasn't completed yet, it will return a  
'VBLTimestamp' of zero and you'll have to retry later. If you call this function  
without having called 'AsyncFlipBegin' before, it will return the results of the  
last completed flip, regardless if it was a synchronous [Screen](Screen)('[Flip](Flip)') or an  
asynchronous flip long finished ago.  
[Screen](Screen)('AsyncFlipEnd') provides a blocking version of this command -- one that  
pauses until the operation completes if the referenced operation hasn't  
completed yet.  


###See also:
[DrawingFinished](Screen-DrawingFinished) [WaitUntilAsyncFlipCertain](Screen-WaitUntilAsyncFlipCertain) [AsyncFlipBegin](Screen-AsyncFlipBegin) [AsyncFlipCheckEnd](Screen-AsyncFlipCheckEnd) [AsyncFlipEnd](Screen-AsyncFlipEnd) Flip
