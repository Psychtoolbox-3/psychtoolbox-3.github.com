# [DaqCodes](DaqCodes)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[Daq](Daq)

Command codes for the USB-1208FS Daq.                                         
0x10    16  [DaqAIn](DaqAIn)                  Read analog in            
0x11    17  [DaqAInScan](DaqAInScan)              Read analog in, clocked                  
0x12    18  [DaqAInStop](DaqAInStop)              Stop input scan                   
0x13    19  [DaqALoadQueue](DaqALoadQueue)           Set channel gains                     
0x14    20  [DaqAOut](DaqAOut)                 Write analog out              
0x15    21  [DaqAOutScan](DaqAOutScan)             Write analog out, clocked                
0x16    22  [DaqAOutStop](DaqAOutStop)             Stop output scan                  
0x01     1  [DaqDConfigPort](DaqDConfigPort)          Configure digital port                    
0x03     3  [DaqDIn](DaqDIn)                  Read digital ports            
0x04     4  [DaqDOut](DaqDOut)                 Write digital port            
0x40    64  [DaqBlinkLED](DaqBlinkLED)             Cause LED to blink                
0x20    32  [DaqCInit](DaqCInit)                Initialize counter                
0x21    33  [DaqCIn](DaqCIn)                  Read counter              
0x46    70  [DaqGetAll](DaqGetAll)               Read all analog and digital input values                  
0x44    68  [DaqGetStatus](DaqGetStatus)            Read device status                    
0x41    65  [DaqReset](DaqReset)                Reset the device                  
0x45    69  [DaqSetCal](DaqSetCal)               Set CAL output                
0x43    67  [DaqSetSync](DaqSetSync)              Configure sync                
0x42    66  [DaqSetTrigger](DaqSetTrigger)           Configure ext. trigger                    
0x30    48  [DaqMemRead](DaqMemRead)              Read memory                   
0x31    49  [DaqMemWrite](DaqMemWrite)             Write memory                  
0x55    85  [DaqReadCode](DaqReadCode)             Read program memory                   
0x50    80  [DaqPrepareDownload](DaqPrepareDownload)      Prepare for program memory download                       
0x51    81  [DaqWriteCode](DaqWriteCode)            Write program memory                      
0x53    83  [DaqWriteSerialNumber](DaqWriteSerialNumber)    Write a new serial number to device                           
See also Daq, [DaqFunctions](DaqFunctions), [DaqPins](DaqPins).  
  
  
  
Command codes for USB-1608FS.  Since all overlapped codes are the same,  
assume that all codes are the same...  well... except that there are no  
analog output ports apparently, so [DaqAOut](DaqAOut), [DaqAOutScan](DaqAOutScan), and [DaqAOutStop](DaqAOutStop)  
should not have associated codes.  No 20, 21, or 22.  
0x01    1   [DaqDConfigPort](DaqDConfigPort)        Configure digital port  
0x02    2   [DaqDConfigPortBit](DaqDConfigPortBit)     Configure individual digital port bits  
0x03    3   [DaqDIn](DaqDIn)                Read digital port  
0x04    4   [DaqDOut](DaqDOut)               Write digital port  
0x05    5   [DaqDReadBit](DaqDReadBit)           Read digital port bit  
0x06    6   [DaqDWriteBit](DaqDWriteBit)          Write digital port bit  
  
0x10   16   [DaqAIn](DaqAIn)                Read analog input channel  
0x11   17   [DaqAInScan](DaqAInScan)            Scan analog channels  
0x12     18   [DaqAInStop](DaqAInStop)            Stop input scan  
0x13     19   [DaqALoadQueue](DaqALoadQueue)         Load the channel/gain queue  
  
0x20     32   [DaqCInit](DaqCInit)              Initialize counter  
0x21     33   [DaqCIn](DaqCIn)                Read Counter  
  
0x30     48   [DaqMemRead](DaqMemRead)            Read Memory  
0x31     49   [DaqMemWrite](DaqMemWrite)           Write Memory  
  
0x40     64   [DaqBlinkLED](DaqBlinkLED)           Causes LED to blink  
0x41     65   [DaqReset](DaqReset)              Reset USB interface  
0x42     66   [DaqSetTrigger](DaqSetTrigger)         Configure external trigger  
0x43     67   [DaqSetSync](DaqSetSync)            Configure sync input/output  
0x44     68   [DaqGetStatus](DaqGetStatus)          Get device status  
0x45     69   [DaqSetCal](DaqSetCal)             Set calibration output  
0x46     70   [DaqGetAll](DaqGetAll)             Get all analog and digital input values  
  
0x50     80   [DaqPrepareDownload](DaqPrepareDownload)    Prepare for program memory download  
0x51     81   [DaqWriteCode](DaqWriteCode)          Write program memory  
0x52     82   (unwritten)           Return program memory checksum  
0x53     83   [DaqWriteSerialNumber](DaqWriteSerialNumber)  Write a new serial number to device  
0x54     84   (unwritten)           Update program memory  
0x55     85   [DaqReadCode](DaqReadCode)           Read program memory  
  
  
  
Command codes for USB-1024LS and similar: Quite different from the 1x08  
series: A speciality is that reportId must be always zero (0) for these  
devices - they use interrupt endpoint 0 transfers. For the same reason,  
output reports must always by 8 bytes in length -- pad them if they're  
shorter! Handling of port C of the device may be a bit quirky, as it is  
treated as two ports, a low port and a high port.  
  
This is based on code and command codes found in usb-1024LS.h and .c,  
subroutine files of the free libhid, a GPL'ed cross platform HID device  
library written by Warren Jasper (<wjasper@tx.ncsu.edu\>). It has not been  
tested by me on any actual device! (MK).  
  
0x0d   13   [DaqDConfigPort](DaqDConfigPort)        Configure digital port (portid == portA = 0x1, portB = 0x4, portClow = 0x8 portCHi = 0x2)  
0x03    3   [DaqDIn](DaqDIn)                Read digital port  
0x01    1   [DaqDOut](DaqDOut)               Write digital port  
0x02    2   [DaqDReadBit](DaqDReadBit)           Read digital port bit    (unwritten)  
0x03    3   [DaqDWriteBit](DaqDWriteBit)          Write digital port bit   (unwritten)  
0x0b     11   [DaqBlinkLED](DaqBlinkLED)           Causes LED to blink  
0x11     17   [DaqReset](DaqReset)              Reset USB interface      (unwritten)  
0x05      5   [DaqCInit](DaqCInit)              Initialize counter  
0x04      4   [DaqCIn](DaqCIn)                Read Counter  
0x0a     10   [DaqWriteCode](DaqWriteCode)          Write program memory     (unwritten)  
0x09      9   [DaqReadCode](DaqReadCode)           Read program memory      (unwritten)  
0x0c     12   [DaqWriteSerialNumber](DaqWriteSerialNumber)  Write a new serial number to device (unwritten)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/Daq/DaqCodes.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/Daq/DaqCodes.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/Daq/DaqCodes.m</code>
</div>

