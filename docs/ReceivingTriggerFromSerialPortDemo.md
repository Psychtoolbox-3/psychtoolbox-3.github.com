# [ReceivingTriggerFromSerialPortDemo](ReceivingTriggerFromSerialPortDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

Template for asynchronous trigger collection and timestamping from serial port.  
  
[ReceivingTriggerFromSerialPortDemo](ReceivingTriggerFromSerialPortDemo)([sampleFreq=120][, baudRate=115200][, portSpec=auto-detect][, specialSettings=None])  
  
This demo shows how to perform efficient trigger recording from an  
external trigger device which is connected to the serial port or a USB-Serial  
converter. The device is assumed to send trigger bytes at a rate of at most  
'sampleFreq' Hz. Typical devices would be fMRI / TMS / MEG / EEG systems  
or other research equipment.  
  
The demo connects to the first found serial port, or optionally the port  
given by the 'portSpec' parameter, e.g., 'COM5'. It connects at a  
baudrate of 'baudRate' Baud, by default without flow-control, with 8  
databits, 1 stopbit and no parity, but you can set arbitrary settings via  
the optional 'specialSettings' string (see [IOPort](IOPort) [OpenSerialPort](OpenSerialPort)?  
online-help for possible parameters).  
  
Then it allocates receivebufferspace for up to 1 hour of uninterrupted  
recording, then starts background recording of data.  
  
Triggers can be read out in realtime, as demonstrated in the main  
while loop here, or offline at end of a session.  
Each trigger gets a [GetSecs](GetSecs)() timestamp of when it was received.  
  
Of course you'll need to understand the code of this demo and then  
customize it for your needs.  
  
For accurate timestamping and data reception with low latency, make sure  
that you've configured your serial ports properly. Search the  
Psychtoolbox forum for posts on that topic, e.g., message 9873.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/ReceivingTriggerFromSerialPortDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/ReceivingTriggerFromSerialPortDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/ReceivingTriggerFromSerialPortDemo.m</code>
</div>

