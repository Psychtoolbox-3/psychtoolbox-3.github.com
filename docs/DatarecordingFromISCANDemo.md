# [DatarecordingFromISCANDemo](DatarecordingFromISCANDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

Template for asynchronous data collection and timestamping from serial port.  
  
[DatarecordingFromSerialPortDemo](DatarecordingFromSerialPortDemo)([portSpec=auto-detect][, sampleFreq=240][maxComponents=2][, baudRate=115200][, specialSettings=None])  
  
This demo shows how to perform efficient data recording of data from an  
ISCAN eyetracker which is connected to the serial port or a USB-Serial  
converter. The device is assumed to stream data in packets of at most  
'maxComponents' gaze sample components in ASCII streaming mode.  
  
The demo connects to the first found serial port, or optionally the port  
given by the 'portSpec' parameter, e.g., 'COM5'. It connects at a  
baudrate of 'baudRate' Baud, by default without flow-control, with 8  
databits, 1 stopbit and no parity, but you can set arbitrary settings via  
the optional 'specialSettings' string (see [IOPort](IOPort) [OpenSerialPort](OpenSerialPort)?  
online-help for possible parameters).  
  
Then it allocates receivebufferspace for up to 1 hour of uninterrupted  
recording, then starts background recording of data.  
  
Datapackets can be read out in realtime, as demonstrated in the main  
while loop here, or offline at end of a session. Each packet is padded to  
be 'maxReadQuantum' bytes in size (zeros are added for shorter packets).  
Each packet comes with a [GetSecs](GetSecs)() timestamp of when the first byte of a  
packet was received.  
  
Of course you'll need to understand the code of this demo and then  
customize it for your needs. We don't know what kind of weird stuff  
you're going to connect, but the default parameter settings may work on  
some simple devices like eyetrackers.  
  
For accurate timestamping and data reception with low latency, make sure  
that you've configured your serial ports properly. Search the  
Psychtoolbox forum for posts on that topic, e.g., message 9873.  
  
The following setup has to be performed in the ISCAN DQW software,  
citing ISCAN software documentation:  
  
To enable the serial output capability in DQW: In the DQW "System  
Configuration" dialog, select the "Serial I/O" tab. Of the available COM  
channels, specify the COM port to be used as "Data I/O", the baud rate to  
match the receiving system, and select "Output" as active. Click on "OK"  
to register changes to the system configuration. Click on the "Options"  
button until the "Auxiliary Output Controls" panel appears as the lower  
left DQW screen. Then click on the "Serial" tab if this is not already in  
the foreground. Choose "Raw Binary" or "Raw ASCII" as the output type  
depending on your preference. Two parameter banks with six parameters  
each, for a total of up to 12 parameters may be output with each data  
sample. To begin, select "Param Bank" 1 and fill the channels (01 -\> 06)  
with the desired parameters by selecting from the pop up list activated  
by clicking on the "..." button to the right of each channel. Fill the  
channels in order and be sure that unused channels have parameter  
"................" selected to minimize data transmission time. If more  
than 6 parameters are desired, select "Param Bank" 2 and proceed as above  
to fill in channels 07 -\> 12. With the above steps completed, whenever  
"Track Active" is enabled a data packet will be output via the specified  
COM port for each system data sample. The data packet will consist of  
each of the non-blank channel data values for the parameters specified in  
channel order (01 -\> 12).  
  
To enable the serial input capability in DQW: In the DQW "System  
Configuration" dialog, select the "Serial I/O" tab. Of the available COM  
channels, specify the COM port to be used as "Data I/O", the baud rate to  
match the remote data sending system, and select "Input" as active. Click  
on "OK" to register changes to the system configuration. With the above  
steps completed, the DQW system is ready to receive serial commands from  
a remote source. All DQW remote serial commands are single bytes between  
128 and 255 (80 -\> FF Hex). Whenever "Track Active" is enabled, the DQW  
system can receive and record any single serial byte between 0 and 127  
(00 and 7F Hex) as a synchronizing data marker. These bytes are  
represented as parameter "[SerIn0](SerIn0)" wherever parameter selections are made  
for display or recording in the DQW program. To trigger data recording  
via the serial port, in the DQW "System Configuration" dialog, select the  
?Recording? tab and set the recording ?Trigger? to ?Serial.?   
  
Thanks to Sebastian Moeller for finding this out.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/DatarecordingFromISCANDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/DatarecordingFromISCANDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/DatarecordingFromISCANDemo.m</code>
</div>

