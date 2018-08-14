# [DaqCalls](DaqCalls)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[Daq](Daq)

Examples for each function in the Daq Toolbox.  
\* Analog input/output commands    
[data,params]=[DaqAIn](DaqAIn)[(DeviceIndex]((DeviceIndex),options);                   % Read analog in (works)  
[data,params]=[DaqAInScan](DaqAInScan)[(DeviceIndex]((DeviceIndex),options);               % Scan analog channels (works)  
          err=[DaqAInStop](DaqAInStop)[(DeviceIndex)]((DeviceIndex));                       % Stop input scan (works)  
       params=[DaqAInScanBegin](DaqAInScanBegin)[(DeviceIndex]((DeviceIndex),options);          % Begin sampling. (works)  
       params=[DaqAInScanContinue](DaqAInScanContinue)[(DeviceIndex]((DeviceIndex),options);       % Continue sampling: transfer data from Mac OS to [PsychHID](PsychHID). (works)  
[data,params]=[DaqAInScanEnd](DaqAInScanEnd)[(DeviceIndex]((DeviceIndex),options);            % End sampling: data are returned. (works)  
          err=[DaqALoadQueue](DaqALoadQueue)[(DeviceIndex]((DeviceIndex),channel,gain);       % Set channel gains (works)  
          err=[DaqAOut](DaqAOut)[(DeviceIndex]((DeviceIndex),channel,v);                % Write analog out (does not work with 1608FS -- no analog output)  
       params=[DaqAOutScan](DaqAOutScan)[(DeviceIndex]((DeviceIndex),v,options);            % Clocked analog out (does not work with 1608FS -- no analog output)  
          err=[DaqAOutStop](DaqAOutStop)[(DeviceIndex)]((DeviceIndex));                      % Stop output scan (does not work with 1608FS -- no analog output)  
  
\* Digital input/output commands   
          err=[DaqDConfigPort](DaqDConfigPort)[(DeviceIndex]((DeviceIndex),port,direction);    % Configure digital port (works)  
         data=[DaqDIn](DaqDIn)[(DeviceIndex)]((DeviceIndex));                           % Read digital ports (works)  
          err=[DaqDOut](DaqDOut)[(DeviceIndex]((DeviceIndex),port,data);                % Write digital port (works)  
          err=[DaqDConfigPortBit](DaqDConfigPortBit)[(DeviceIndex]((DeviceIndex),[BitNo](BitNo),direction);% Configure individual port bits (works on 1608FS only; also beware: physical input overrides config)  
     [BitValue](BitValue)=[DaqDReadBit](DaqDReadBit)[(DeviceIndex]((DeviceIndex),[BitNo)](BitNo));                % Read single bit from digital port (works on 1608FS only)  
          err=[DaqDWriteBit](DaqDWriteBit)[(DeviceIndex]((DeviceIndex),[BitNo)](BitNo));               % Write single bit to digital port (works on 1608FS only)  
  
\* Miscellaneous commands      
          daq=[DaqDeviceIndex](DaqDeviceIndex);                                % Get reference(s) to our device(s); (works)  
          daq=[DaqFind](DaqFind);                                       % Return [DeviceIndex](DeviceIndex) iff one device is connected (works)  
          err=[DaqBlinkLED](DaqBlinkLED)[(DeviceIndex)]((DeviceIndex));                      % Cause LED to blink (works)  
          err=[DaqCInit](DaqCInit)[(DeviceIndex)]((DeviceIndex));                         % Initialize counter (works)  
        count=[DaqCIn](DaqCIn)[(DeviceIndex)]((DeviceIndex));                           % Read counter (works)  
         data=[DaqGetAll](DaqGetAll)[(DeviceIndex)]((DeviceIndex));                        % Retrieve all analog and digital input values (does not work on 1608FS)  
       status=[DaqGetStatus](DaqGetStatus)[(DeviceIndex)]((DeviceIndex));                     % Retrieve device status (works)  
          err=[DaqReset](DaqReset)[(DeviceIndex)]((DeviceIndex));                         % Reset the device (sort of works)  
          err=[DaqSetCal](DaqSetCal)[(DeviceIndex]((DeviceIndex),on);                     % Set CAL output (works)  
              [DaqCalibrateAIn](DaqCalibrateAIn)[(DeviceIndex]((DeviceIndex),channel);          % Compare input/output and write calibration data to file (1608FS only)  
          err=[DaqSetSync](DaqSetSync)[(DeviceIndex]((DeviceIndex),type);                  % Configure sync (works)  
          err=[DaqSetTrigger](DaqSetTrigger)[(DeviceIndex]((DeviceIndex),rising);             % Configure ext. trigger (works)  
  
\* Memory commands     
         data=[DaqMemRead](DaqMemRead)[(DeviceIndex]((DeviceIndex),address,bytes);         % Read memory (works)  
          err=[DaqMemWrite](DaqMemWrite)[(DeviceIndex]((DeviceIndex),address,data);         % Write memory (works)  
         data=[DaqReadCode](DaqReadCode)[(DeviceIndex]((DeviceIndex),address,bytes);        % Read program memory (works)  
          err=[DaqPrepareDownload](DaqPrepareDownload)[(DeviceIndex)]((DeviceIndex));               % Prepare for program memory download (works)  
          err=[DaqWriteCode](DaqWriteCode)[(DeviceIndex]((DeviceIndex),address,data);        % Write program memory (not adequately tested)  
For 1608 [DaqWriteCode](DaqWriteCode) probably cannot work except in conjunction with a [DaqUpdateCode](DaqUpdateCode) function no one has written  
          err=[DaqWriteSerialNumber](DaqWriteSerialNumber)[(DeviceIndex]((DeviceIndex),serialstring);% Write a new serial number to device (not adequately tested)  
  
See also Daq, [DaqFunctions](DaqFunctions), [DaqCodes](DaqCodes), [DaqPins](DaqPins), and [DaqHelp](DaqHelp).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/Daq/DaqCalls.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/Daq/DaqCalls.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/Daq/DaqCalls.m</code>
</div>

