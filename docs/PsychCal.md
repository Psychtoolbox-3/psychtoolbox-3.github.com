# [PsychCal](PsychCal)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

Psychtoolbox:[PsychCal](PsychCal).  
  
Calibration routines for monitors, e.g., gamma correction.  
For a very simple gamma calibration of a standard monitor with a manually  
controlled photometer, use [CalibrateMonitorPhotometer](CalibrateMonitorPhotometer).  
  
For advanced calibration, with manual or automatic photometers, with  
standard monitors or high precision displays like Bits+,  
[DataPixx](DataPixx)/[ViewPixx](ViewPixx) etc. use [CalibrateMonSpd](CalibrateMonSpd).  
  
  
  
  [BasicToneMapCalFormat](BasicToneMapCalFormat) - Apply simple (truncation) tone mapping to XYZ data in cal format.  
  [CalDataFolder](CalDataFolder)       - Path to the calibration data folder "[PsychCalData](PsychCalData)".  
  [CalFormatToImage](CalFormatToImage)    - Put a stretched out image back into an image image.  
  [CalibrateAmbDrvr](CalibrateAmbDrvr)    - Common code called by monitor calibration programs.  Script.  
  [CalibrateFitGamma](CalibrateFitGamma)   - Fit the gamma function to the calibration measurements.  
  [CalibrateFitLinMod](CalibrateFitLinMod)  - Fit the linear model to spectral calibration data.  
  [CalibrateFitYoked](CalibrateFitYoked)   - Fit a very special kind of yoked calibration data.  
  [CalibrateManualDrvr](CalibrateManualDrvr) - Driver for manual monitor calibration, called by [CalibrateMonSpd](CalibrateMonSpd).  
  [CalibrateMonDrvr](CalibrateMonDrvr)    - Common code called by monitor calibration programs.  Script.  
  [CalibrateMonitorPhotometer](CalibrateMonitorPhotometer) - Simple calibration procedure for use with manually controlled photometers.  
  [CalibrateMonSpd](CalibrateMonSpd)     - Run standard monitor spectral calibration.  Script.  
  [CalibratePlotGamma](CalibratePlotGamma)  - Plot the gamma functions in a calibration structure.  
  [CalibratePlotSpectra](CalibratePlotSpectra) - Plot the device spectra in a calibration structure.  
  [CalToggleBitsPlusPlus](CalToggleBitsPlusPlus) - Determine whether to calibrate with or without Bits++.  
  [CompareMonCal](CompareMonCal)       - Compare two calibration structures to see if they match.  
  [CompareMonCalOverTime](CompareMonCalOverTime) - Compare two calibrations of same monitor and see differences.  Script.  
  [ContrastMatch](ContrastMatch)       - Match contrast of two gratings.  
  [Cross2D](Cross2D)             - Create 2D vectors that cross combinations of passed vectors.  
  [Cross3D](Cross3D)             - Create 3D vectors that cross combinations of passed vectors.  
  [CVIAdjustCalData](CVIAdjustCalData)    - Adjust of PR650 measurements with CVI measurements.  Not of general interest.  
  [CylToSensor](CylToSensor)         - Convert from cylindrical to sensor coordinates.  
  [DescribeMonCal](DescribeMonCal)      - Print a description of calibration structure.  
  [DumpMonCalSpd](DumpMonCalSpd)       - Dump contents of standard spectral calibration file.  Script.  
  [ExpandSettings](ExpandSettings)      - Subroutine for "Acc" conversion routines.  
  [FindSpectralPeaks](FindSpectralPeaks)   - Find the peaks in a spectral function.  
  [FlushCalFile](FlushCalFile)        - Remove old entries from calibration file.  
  [GamutToSettings](GamutToSettings)     - Convert from within gamut device coordinates to settings.  
  [GamutToSettingsSch](GamutToSettingsSch)  - Subroutine for [GamutToSettings](GamutToSettings).  
  [GamutToSettingsTbl](GamutToSettingsTbl)  - Subroutine for [GamutToSettings](GamutToSettings).  
  [GratingNull](GratingNull)         - Match two luminances.  
  [IccProfile](IccProfile).mex      - NOT IMPLEMENTED YET: Read ICC profiles for monitor calibration.  
  [ImageToCalFormat](ImageToCalFormat)    - Stretch out an image to pass to calibration conversion routines.  
  [InvertGammaTable](InvertGammaTable)    - Subroutine for [GamutToSettings](GamutToSettings).  
  [LoadCalFile](LoadCalFile)         - Load calibration data.  
  [MaximizeGamutContrast](MaximizeGamutContrast)- Maximize contrast within gamut.  
  [MeasMonSpd](MeasMonSpd)          - Set monitor and measure spd.  
  [MeasMonXYZ](MeasMonXYZ)          - Set monitor and measure XYZ.  
  [MeasureDpi](MeasureDpi)          - Measure monitor dpi.  
  [PolarToSensor](PolarToSensor)       - Convert from polar to linear coordinates.  
  [PrimaryToGamut](PrimaryToGamut)      - Force primary coordinates into gamut.  
  [PrimaryToSensor](PrimaryToSensor)     - Convert from primary to sensor coordinates.  
  [PrimaryToSettings](PrimaryToSettings)   - Convert from primary coordinates to device settings.  
  [RefitCalGamma](RefitCalGamma)       - Refit the gamma data in a monitor calibration file.  Script.  
  [RefitCalLinMod](RefitCalLinMod)      - Refit primary spectral linear model in calibration file.  Script.  
  [RefitCalYoked](RefitCalYoked)       - Refit linear model to match yoked [a,a,a] measurements. Script.  
  [SaveCalFile](SaveCalFile)         - Save calibration data.  
  [SearchGammaTable](SearchGammaTable)     - Subroutine for [GamutToSettings](GamutToSettings).  
  [SensorToCyl](SensorToCyl)         - Convert from sensor to cylindrical coordinates.  
  [SensorToPolar](SensorToPolar)       - Convert from sensor to polar coordinates.  
  [SensorToPrimary](SensorToPrimary)     - Convert from sensor to primary coordinates.  
  [SensorToSettings](SensorToSettings)    - Convert from sensor coordinates to device settings.  
  [SensorToSettingsAcc](SensorToSettingsAcc) - Convert from sensor coordinates to settings, handle spectral shifts.  
  [SetGammaMethod](SetGammaMethod)      - Set gamma correction method for conversions.  
  [SetSensorColorSpace](SetSensorColorSpace) - Set working sensor color space for conversions.  
  [SettingsToPrimary](SettingsToPrimary)   - Convert from settings to primary coordinates.  
  [SettingsToSensor](SettingsToSensor)    - Convert from settings to sensor coordinates.  
  [SettingsToSensorAcc](SettingsToSensorAcc) - Convert from settings to sensor, handle spectral shifts.  
  [UpdateAmbient](UpdateAmbient)       - Update the ambient used for conversions, in meas. units.  
  [UpdateAmbientSensor](UpdateAmbientSensor) - Update the ambient used for conversions, in sensor units.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/Contents.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/Contents.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/Contents.m</code>
</div>

{{category}}