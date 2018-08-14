# [DatarecordingFromSerialPortDemo](DatarecordingFromSerialPortDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

Template for asynchronous data collection and timestamping from serial port.  
  
[DatarecordingFromSerialPortDemo](DatarecordingFromSerialPortDemo)([maxReadQuantum=15][, lineTerminator=10][, sampleFreq=120][, baudRate=115200][, portSpec=auto-detect][, specialSettings=None])  
  
This demo shows how to perform efficient data recording of data from an  
external device which is connected to the serial port or a USB-Serial  
converter. The device is assumed to stream data in packets of at most  
'maxReadQuantum' bytes, each packet ending with a special ASCII or byte  
code 'lineTerminator', the packets streaming at a rate of 'sampleFreq'  
Hz. Typical candidates would be serial port data acquisition devices or  
eyetrackers.  
  
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
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/DatarecordingFromSerialPortDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/DatarecordingFromSerialPortDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/DatarecordingFromSerialPortDemo.m</code>
</div>

