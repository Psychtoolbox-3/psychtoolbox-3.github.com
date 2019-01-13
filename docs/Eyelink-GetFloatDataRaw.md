# [Eyelink('GetFloatDataRaw')](Eyelink-GetFloatDataRaw) 
##### [Psychtoolbox](Psychtoolbox)>[Eyelink](Eyelink).{mex*} subfunction


Same as Eyelink('GetFloatData') but additionally returns raw sample data.  
If type is not SAMPLE\_TYPE, identical to [GetFloatData](GetFloatData) (raw will be returned as  
0).  
Specify the eye for which raw values are desired as LEFT\_EYE or RIGHT\_EYE as  
returned by [EyelinkInitDefaults](EyelinkInitDefaults).  Omission of this argument is deprecated.  
Normal samples do not contain the corneal reflection data, but some  
(non-saccade-based) calibration methods require this information.  
The Eyelink 1000 can be configured to send this information as part of 'raw'  
samples.  
Sol Simpson at SR-Research emphasizes that this is not officially supported or  
guaranteed.  
1. You may need to install Eyelink.dll from the latest software developer kit at  
https://www.sr-support.com/forums/showthread.php?t=6 (windows) or  
https://www.sr-support.com/forums/showthread.php?t=15 (osx)  
2. Issue the commands:  
       Eyelink('command','link\_sample\_data =  
LEFT,RIGHT,GAZE,AREA,GAZERES,HREF,PUPIL,STATUS,INPUT,HMARKER');  
       Eyelink('command','inputword\_is\_window = ON');  
More info:  
       HMARKER (originally for Eyelink2's infrared head tracking markers) and INPUT  
(originally for the TTL lines) are jury-rigged to hold the extra data.  
       You can also set file\_sample\_data to collect raw samples in the .edf file.  
Raw structure fields:  
       raw\_pupil           raw x, y sensor position of the pupil  
       raw\_cr              raw x, y sensor position of the corneal reflection  
       pupil\_area          raw pupil area  
       cr\_area             raw cornela reflection area  
       pupil\_dimension     width, height of raw pupil  
       cr\_dimension        width, height of raw cr  
       window\_position     x, y position of tracking window on sensor  
       pupil\_cr            calculated pupil-cr from the raw\_pupil and raw\_cr fields  
       cr\_area2            raw area of 2nd corneal reflection candidate  
       raw\_cr2             raw x, y sensor position of 2nd corneal reflection  
candidate  
CAUTION: It may or may not work on your setup with your tracker.  
  
  


###See also:

