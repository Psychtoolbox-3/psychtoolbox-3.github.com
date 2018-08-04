# [NetStation_old](NetStation_old)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)

  
 [NetStation](NetStation) - Basic control of the EGI/[NetStation](NetStation) EEG recording system via  
 TCP/IP network connection. (See http://www.egi.com)  
  
 This function was developed and contributed to Psychtoolbox by Gergely Csibra, 2006-2008.  
 Code is based on Rick Gilmore's routines, 2005. Thanks!  
 Code adapted to [PCs](PCs) (and Macs with Intel architecture) by Zhao Fan, 2008.  
  
  
 General syntax  
  
   [status, error] = [NetStation](NetStation)('command', ...)  
  
   if status == 0, the command has been succesfully executed  
   otherwise see string "error" for error message  
  
 Commands  
  
   [NetStation](NetStation)('Connect', host [, port])  
  
           Establishes TCP/IP connection to the [NetStation](NetStation) host computer.  
           "host" is the hostname as a string (e.g., 'anything.com' or '187.14.176.12')  
           "port" is the ethernet port to be used. Default is 55513.  
  
   [NetStation](NetStation)('Disconnect')  
  
           Disconnects from [NetStation](NetStation) host.  
  
   [NetStation](NetStation)('Synchronize' [, [SynchLimit](SynchLimit)])  
  
           Synchronize to the connected host. "[SynchLimit](SynchLimit)" could specify the maximum allowed difference  
           IN MILLISECONDS. Default is 2.5 ms.  
  
   [NetStation](NetStation)('StartRecording')  
  
           Instructs [NetStation](NetStation) to start recording.  
  
   [NetStation](NetStation)('StopRecording')  
  
           Instructs [NetStation](NetStation) to stop recording.  
  
   [NetStation](NetStation)('Event' [,code] [,starttime] [,duration] [,keycode1] [,keyvalue1] [...])  
   [NetStation](NetStation)('EventNoAck' [,code] [,starttime] [,duration] [,keycode1] [,keyvalue1] [...])  
  
           Send an event to the [NetStation](NetStation) host. The 'EventNoAck' variant doesn't  
           wait for acknowledgement of reception of the event, whereas the 'Event'  
           version does. Note that the 'EventNoAck' command is included for  
           completeness. It is not a good practice to skip waiting for  
           acknowledgements. If time is an important factor, Event commands can be sent  
           at a later opportunity within a session (e.g., in blocks at the end  
           of experiments).  
  
           "code"      The 4-char event code (e.g., 'STIM')  
                       Default: 'EVEN'  
           "starttime" The time IN SECONDS when the event started. The VBL time  
                       returned by [Screen](Screen)('[Flip](Flip)') can be passed here as a parameter.  
                       Default: current time.  
           "duration"  The duration of the event IN SECONDS.  
                       Default: 0.001.  
           "keycode"   The 4-char code of a key (e.g., 'tria').  
           "keyvalue"  The value of the key (any number or string)  
                       The keycode-keyvalue pairs can be repeated arbitrary times.  
  
   [NetStation](NetStation)('FlushReadbuffer');  
  
            Flushes the read buffer.  
  
   Uses a modified version of the TCP/UDP/IP Toolbox 2.0.5, a third party GPL'ed  
   open source toolbox, which is included in Psychtoolbox,  
   but also available from the Mathworks website:  
   http://www.mathworks.com/matlabcentral/fileexchange/loadFile.do?objectId=345  
  
   The toolbox has been modified for lower communication latency.  
  
   Created by Gergely Csibra, 2006-2008  
   Based on Rick Gilmore's routines, 2005  
   Adapted to PC by Zhao Fan, 2008  
   This function was modified by Matt Mollison to accommodate sending more than just int16s to Net Station  
   Improved by Justin Ales 2014.  
   Consolidated by Gergely Csibra, 2015  
%  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/NetStation_old.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/NetStation_old.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/NetStation_old.m</code>
</div>

