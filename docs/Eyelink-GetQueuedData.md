# [Eyelink('GetQueuedData')](Eyelink-GetQueuedData) 
##### [Psychtoolbox](Psychtoolbox)>[Eyelink](Eyelink).{mex*} subfunction

[samples, events, drained] = Eyelink('GetQueuedData' [, eye])

dequeues all samples and events from the link.  
returns double matrices where columns are items and rows are fields from eyelink  
sample structs.  
return flag 'drained' indicates whether queue was emptied or if this function  
needs to be called again.  
if you include the eye argument (as LEFT\_EYE or RIGHT\_EYE as returned by  
[EyelinkInitDefaults)](EyelinkInitDefaults)), samples will include raw fields for that eye.  
if you don't remove items from the queue often enough, the oldest items will be  
replaced by a LOSTDATAEVENT, which will appear in the sample records at the  
location where items were dropped (fields other than type will be set to  
MISSING\_DATA).  
  
sample rows are as follows:   
     1: time of sample (when camera imaged eye, in milliseconds since tracker was  
activated)  
     2: type (always SAMPLE\_TYPE or LOSTDATAEVENT as returned by  
[EyelinkInitDefaults)](EyelinkInitDefaults))  
     3: flags (bits indicating what types of data are present, and for which eye(s)  
- see eye\_data.h)  
     4: left pupil center x (camera coordinates)  
     5: right pupil center x (camera coordinates)  
     6: left pupil center y (camera coordinates)  
     7: right pupil center y (camera coordinates)  
     8: left HEADREF x (angular gaze coordinates)  
     9: right HEADREF x (angular gaze coordinates)  
     10: left HEADREF y (angular gaze coordinates)  
     11: right HEADREF y (angular gaze coordinates)  
     12: left pupil size (arbitrary units, area or diameter as selected by  
pupil\_size\_diameter command)  
     13: right pupil size (arbitrary units, area or diameter as selected by  
pupil\_size\_diameter command)  
     14: left gaze position x (in pixel coordinates set by screen\_pixel\_coords  
command)  
     15: right gaze position x (in pixel coordinates set by screen\_pixel\_coords  
command)  
     16: left gaze position y (in pixel coordinates set by screen\_pixel\_coords  
command)  
     17: right gaze position y (in pixel coordinates set by screen\_pixel\_coords  
command)  
     18: angular resolution x (at gaze position in screen pixels per visual degree)  
     19: angular resolution y (at gaze position in screen pixels per visual degree)  
     20: status (error and status flags (only useful for [EyeLink](EyeLink) II and  
[EyeLink1000](EyeLink1000), report CR status and tracking error). see eye\_data.h.)  
     21: input (data from input port(s))  
     22: button input data: high 8 bits indicate changes from last sample, low 8  
bits indicate current state of buttons 8 (MSB) to 1 (LSB)  
     23: head-tracker data type (0=none)  
     24: head-tracker data (not prescaled) 1  
     25: head-tracker data (not prescaled) 2  
     26: head-tracker data (not prescaled) 3  
     27: head-tracker data (not prescaled) 4  
     28: head-tracker data (not prescaled) 5  
     29: head-tracker data (not prescaled) 6  
     30: head-tracker data (not prescaled) 7  
     31: head-tracker data (not prescaled) 8  
  
if you request the raw sample fields, they will appear in the following  
additional rows:  
     32: raw x sensor position of the pupil  
     33: raw y sensor position of the pupil  
     34: raw x sensor position of the corneal reflection  
     35: raw y sensor position of the corneal reflection  
     36: raw pupil area  
     37: raw corneal reflection area  
     38: raw width of pupil  
     39: raw height of pupil  
     40: raw width of corneal reflection  
     41: raw height of corneal reflection  
     42: raw x position of tracking window on sensor  
     43: raw y position of tracking window on sensor  
     44: (raw pupil x) - (raw corneal reflection x)  
     45: (raw pupil y) - (raw corneal reflection y)  
     46: raw area of 2nd corneal reflection candidate  
     47: raw x sensor position of the 2nd corneal reflection candidate  
     48: raw y sensor position of the 2nd corneal reflection candidate  
  
About raw fields:  
Normal samples do not contain the corneal reflection data, but some  
(non-saccade-based) calibration methods require this information.  
The Eyelink 1000 can be configured to send this information as part of 'raw'  
samples, and this is required before use of this function.  
Sol Simpson at SR-Research emphasizes that this is not officially supported or  
guaranteed.  
1. You need to install Eyelink.dll from the latest software developer kit at  
https://www.sr-support.com/forums/showthread.php?t=6 (windows) or  
https://www.sr-support.com/forums/showthread.php?t=15 (osx)  
       and the latest tracker host software at  
https://www.sr-support.com/forums/showthread.php?t=179  
2. Issue the commands:  
       Eyelink('command','link\_sample\_data =  
LEFT,RIGHT,GAZE,AREA,GAZERES,HREF,PUPIL,STATUS,INPUT,HMARKER');  
       Eyelink('command','inputword\_is\_window = ON');  
More info:  
       HMARKER (originally for Eyelink2's infrared head tracking markers) and INPUT  
(originally for the TTL lines) are jury-rigged to hold the extra data.  
       You can also set file\_sample\_data to collect raw samples in the .edf file.  
CAUTION: It may or may not work on your setup with your tracker.  
  
 event rows are as follows:   
     1: effective time of event  
     2: event type  
     3: read (bits indicating which data fields contain valid data - see  
eye\_data.h.)  
     4: eye  
     5: start time  
     6: end time  
     7: HEADREF gaze position starting point x  
     8: HEADREF gaze position starting point y  
     9: display gaze position starting point x (in pixel coordinates set by  
screen\_pixel\_coords command)  
     10: display gaze position starting point y (in pixel coordinates set by  
screen\_pixel\_coords command)  
     11: starting pupil size (arbitrary units, area or diameter as selected by  
pupil\_size\_diameter command)  
     12: HEADREF gaze position ending point x  
     13: HEADREF gaze position ending point y  
     14: display gaze position ending point x (in pixel coordinates set by  
screen\_pixel\_coords command)  
     15: display gaze position ending point y (in pixel coordinates set by  
screen\_pixel\_coords command)  
     16: ending pupil size (arbitrary units, area or diameter as selected by  
pupil\_size\_diameter command)  
     17: HEADREF gaze position average x  
     18: HEADREF gaze position average y  
     19: display gaze position average x (in pixel coordinates set by  
screen\_pixel\_coords command)  
     20: display gaze position average y (in pixel coordinates set by  
screen\_pixel\_coords command)  
     21: average pupil size (arbitrary units, area or diameter as selected by  
pupil\_size\_diameter command)  
     22: average gaze velocity magnitude (absolute value) in visual degrees per  
second  
     23: peak gaze velocity magnitude (absolute value) in visual degrees per second  
     24: starting gaze velocity in visual degrees per second  
     25: ending gaze velocity in visual degrees per second  
     26: starting angular resolution x in screen pixels per visual degree  
     27: ending angular resolution x in screen pixels per visual degree  
     28: starting angular resolution y in screen pixels per visual degree  
     29: ending angular resolution y in screen pixels per visual degree  
     30: status (collected error and status flags from all samples in the event  
(only useful for [EyeLink](EyeLink) II and [EyeLink1000](EyeLink1000), report CR status and tracking  
error). see eye\_data.h.)  
  
  


###See also:

