# [HoritaTitler](HoritaTitler)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)

[HoritaTitler](HoritaTitler)(command [, arg1, arg2, ...])  
  
This function establishes a serial port connection to the HORITA SCT-50 video  
titler and compatible devices, and performs a number of commands. Commands are  
based on the HORITA SCT-50 video titler user manual (https://horita.com/).  
  
  
### Commands:  
  
  [HoritaTitler](HoritaTitler)('Open' [, 'serialPort'][, 'HORITAaddress'])  
  
###       THIS FUNCTION SHOULD BE CALLED FIRST!!  
  
      Initializes and opens the serial port which establishes communication to the HORITA.  
      If serialPort/[HORITAaddress](HORITAaddress) is ommitted or left empty, the defaultPort is 'COM4' on  
      MS-Windows, '/dev/tty.KeySerial1' on Apple macOS, and '/dev/ttyS0' on GNU/Linux.  
      The Psychtoolbox function [FindSerialPort](FindSerialPort)() can be helpful to automatically find a  
      connected serial port device.  
  
      The default [HORITAaddress](HORITAaddress) is '02'.  
  
  [HoritaTitler](HoritaTitler)('[Close](Close)')  
  
      Closes the serial connection with HORITA.  
  
  [HoritaTitler](HoritaTitler)('SetAddress', 'HORITAaddress')  
  
      Set the 'HORITAaddress' for the target HORITA titler device. Followup commands will  
      be sent to the new address. This allows to select between multiple daisy-chained  
      HORITA titler devices. Valid [HORITAADDRESSes](HORITAADDRESSes) are between '00' and '99', with a default  
      address of '02'. The special address '00' broadcasts to / selects all connected HORITA  
      devices, so they all execute the same command simultaneously.  
  
  [HoritaTitler](HoritaTitler)('Write' [, 'text', row, column])  
  
      Writes text at a specified position on the screen. Positions are numbered from 001 (top  
      left) to 180 (bottom right), and there are a total number of 9 rows and 20 columns  
      available. Text is automatically converted to uppercase. If row/colum are omitted or left  
      empty, the default is to write on row/column 1. If text is omitted, a blank space is  
      inserted at the specified position. If the text does not fit on one row, then it is  
      shortened.  
  
  [HoritaTitler](HoritaTitler)('Write' [, number, row, column])  
  
      Writes numbers at a specified position on the screen. Numbers are converted from double  
      class to string class using mat2str(number). If row/column are omitted or left empty, the  
      default is to write on row/column 1. If number is omitted, a blank space is inserted at the  
      specified porition.  
  
  [HoritaTitler](HoritaTitler)('WriteCont' [, 'text'])  
  
      Writes text at the current position of the cursor. If no text is provided, a blank space is  
      inserted at the current position.  
  
  [HoritaTitler](HoritaTitler)('WriteCont' [, number])  
  
      Writes numbers at the current position of the cursor. Numbers are converted from double  
      class to string class using mat2str(number). If no number is provided, a blank space is  
      inserted at the current position.  
  
  [HoritaTitler](HoritaTitler)('Clear')  
  
      Clears the display (requires 100 ms).  
  
  [HoritaTitler](HoritaTitler)('ClearLine'[, row])  
  
      Clears the given row on the display. If the row number is omitted, clears the first line.  
      HORITA display has 9 rows, therefore row <= 9.  
  
  [HoritaTitler](HoritaTitler)('Reset')  
  
      Resets the HORITA titler (requires 300 ms). All variable data in the HORITA SCT-50 are set  
      to default values.  
  
  [HoritaTitler](HoritaTitler)('TimeOn')  
  
      Turns the time display on.  
  
  [HoritaTitler](HoritaTitler)('TimeOff')  
  
      Turns the time display off.  
  
  [HoritaTitler](HoritaTitler)('TimeSet' [, 'hour', 'minute', 'second'])  
  
      Sets the time. Hour/minute/second have to be 2 digits long. If hour/minute/second are  
      omitted or empty, the time is set based on the Matlab clock function.  
  
  [HoritaTitler](HoritaTitler)('TimePosit' [, row, column, 'hour', 'minute', 'second'])  
  
###       SET THE TIME ON BEFORE!  
  
      Sets the time and places it at the specified position. Time display has to be set on prior  
      to the positioning. If row/column are omitted or left empty, the time is placed on row/column 1.  
      Hour/minute/second have to be 2 digits long. If hour/minute/second are omitted or empty, the  
      time is set based on the Matlab clock function.  
  
  [HoritaTitler](HoritaTitler)('TimeFormat' [, 'format'])  
  
      Sets the time display format. There are 36 time display formats. The default time format is  
      'hh:mm:ss AM' (i.e. format '05'). Format '02' will display hh:mm:ss. Format '03' will  
      display hh:mm:ss.ms.  
  
  [HoritaTitler](HoritaTitler)('DateOn')  
  
      Turns the date display on.  
  
  [HoritaTitler](HoritaTitler)('DateOff')  
  
      Turns the date display off.  
  
  [HoritaTitler](HoritaTitler)('DateSet' [, 'day', 'month', 'year'])  
  
      Sets the date. Month/day/year have to be 2 digits long. If month/day/year are omitted or  
      empty, the time is set based on the Matlab clock function.  
  
  [HoritaTitler](HoritaTitler)('DatePosit' [, row, column, 'day', 'month', 'year'])  
  
###       SET THE DATE ON BEFORE!  
  
      Sets the date and places it at the specified position. Date display has to be set on prior  
      to the positioning. If row/column are omitted or left empty, the date is placed on  
      row/column 1. Month/day/year have to be 2 digits long. If month/day/year are omitted or  
      empty, the date is set based on the Matlab clock function.  
  
  [HoritaTitler](HoritaTitler)('DateFormat' [, 'format'])  
  
      Sets the date display format. There are 60 display formats. The default date format is  
      'dd/mo/yy' (i.e. format '10', 23/06/17). Format '11' will display 23/JUN/17. Format '59'  
      will display 23JUN17.  
  
  [HoritaTitler](HoritaTitler)('BackgroundOn')  
  
      Sets on the text background.  
  
  [HoritaTitler](HoritaTitler)('BackgroundOff')  
  
      Sets off the text background.  
  
  [HoritaTitler](HoritaTitler)('TextWhite')  
  
      Sets the text to white.  
  
  [HoritaTitler](HoritaTitler)('TextWhite')  
  
      Sets the text to black.  
  
  [HoritaTitler](HoritaTitler)('DeleteSerial')  
  
      [Close](Close) all serial ports. Good to do this right at the beginning, before  
      initializing HORITA, in case a previous serial connection is still open.  
  
  
===================================================================================  
Created by Natasa Ganea, 2017, Goldsmiths Infantlab (email: natasa.ganea@gmail.com)  
Licensed to you under the MIT open-source license.  
===================================================================================  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/HoritaTitler.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/HoritaTitler.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/HoritaTitler.m</code>
</div>

