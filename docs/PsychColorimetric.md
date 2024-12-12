# [PsychColorimetric](PsychColorimetric)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)

Psychtoolbox:[PsychColorimetric](PsychColorimetric).  
  
Colorimetric and spectral calculations.  See also Psychtoolbox:[PsychColorimetricData](PsychColorimetricData).  
And also see the closely related Psychtoolbox:[PsychRadiometric](PsychRadiometric).  Sometimes it is  
not entirely clear whether a routine should be classified as colorimetric or  
radiometric. Apologies if our intuitions don't match yours  
  
  
  [AbsorbanceToAbsorbtance](AbsorbanceToAbsorbtance) - Obsolete.  Use [AbsorbanceToAbsorptance](AbsorbanceToAbsorptance) (spelling fixed).  
  [AbsorbanceToAbsorptance](AbsorbanceToAbsorptance) - Convert absorbance to absorptance spectrum.  
  [AbsorbtanceToAbsorbance](AbsorbtanceToAbsorbance) - Obsolete.  Use [AbsorptanceToAbsorbance](AbsorptanceToAbsorbance) (spelling fixed).  
  [AbsorptanceToAbsorbance](AbsorptanceToAbsorbance) - Convert absorptance to absorbance spectrum.  
  [CheckWls](CheckWls)            - Check consistency of two wavelength descriptions.  
  [ComputeDE](ComputeDE)           - Compute vector length between matrix columns.  
  [ComputeDE2000](ComputeDE2000)\_Lab   - Compute deltaE values (CIEDE200) for color pairs given in L\*a\*b\* coordinates.  
  [ComputeDKL](ComputeDKL)\_M        - Compute transformation matrix for DKL color space.  
  [ComputeAxialDensity](ComputeAxialDensity) - Compute axial optical density from specific density and path length.  
  [ComputePhotopigmentBleaching](ComputePhotopigmentBleaching) - Compute fraction of photopigment bleached.  
  [ConeIncToDKL](ConeIncToDKL)        - Convert from cone increments to DKL.  
  [ContrastToExcitation](ContrastToExcitation) - Convert contrast to excitation coordinate.  
  [ContrastToIncrement](ContrastToIncrement) - Convert contrast to incremental coordinates.  
  [ConvertRGBSourceToRGBTargetColorSpace](ConvertRGBSourceToRGBTargetColorSpace) - Convert an image from a RGB source colorspace to a RGB target colorspace.  
  [DKLToConeInc](DKLToConeInc)        - Convert from DKL to cone increments.  
  [DrawChromaticity](DrawChromaticity) -    Plot chromaticity diagram w spectrum locus (provided by Danny Garside).  
  [EffectiveTrolandsFromLum](EffectiveTrolandsFromLum) - Compute effective trolands from luminance.  
  [EnergyToCones](EnergyToCones)       - Convert monochromatic energy to cone excitations.  
  [ExcitationToContrast](ExcitationToContrast) - Convert excitation coordinates to contrast.  
  [FindCmfPeaks](FindCmfPeaks)        - Find the peak wavelength and values of a set of color matching functions.  
  [FindCovLinMod](FindCovLinMod)       - Find linear model from covariance matrix.  
  [FindLinMod](FindLinMod)          - Find linear model for an ensemble of vectors.  
  [FindModelWeights](FindModelWeights)    - Find the weights with respect to a linear model.  
  [FToRatio](FToRatio)            - Subroutine for Lab/Luv conversions.  
  [GenerateBlackBody](GenerateBlackBody)   - Generate spectra for black body radiators.  
  [GenerateCIEDay](GenerateCIEDay)      - Generate CIE daylights.  
  [IncrementToContrast](IncrementToContrast) - Convert incremental coordinates to contrast.  
  [IsomerizationsFromAbsorbptions](IsomerizationsFromAbsorbptions) - Compute isomerization rate from absorption rate.  
  [LabToXYZ](LabToXYZ)            - Convert from Lab to XYZ.  
  [LjgToXYZ](LjgToXYZ)            - Convert from OSA UCS Ljg to XYZ (10 degree).  
  [LumToRadiance](LumToRadiance)       - Get spectral radiance from luminance and relative spectrum of source.  
  [LumToTrolands](LumToTrolands)       - Convert luminance (cd/m2) to trolands.  
  [LuvToXYZ](LuvToXYZ)            - Convert from Luv to XYZ.  
  [LMSToMacBoyn](LMSToMacBoyn)        - Convert from cones to [MacLeod](MacLeod)-Boynton chromaticity.  
  [MakeFourierBasis](MakeFourierBasis)    - Make a set of Fourier component basis functions.  
  [MakeGaussBasis](MakeGaussBasis)      - Make a set of Gaussian basis functions.  
  [MakeItS](MakeItS)             - Force wavelength sampling spec. to S format.  
  [MakeItStruct](MakeItStruct)        - Force wavelength sampling spec. to struct foramt.  
  [MakeItWls](MakeItWls)           - Force wavelength sampling spec. to wls format.  
  [MakeMonoPrimary](MakeMonoPrimary)     - Make the spd of a monochromatic primary.  
  [MakeOrtho](MakeOrtho)           - Make a set of basis functions orthonormal.  
  [MakeUnitLength](MakeUnitLength)      - Make the columns of a matrix have unit length.  
  [MonoImageToSRGB](MonoImageToSRGB)     - Convert a monochrome image to an sRGB color image at passed chromaticity.  
  M\_PToP              - Conversion matrix from source/dest. primaries.  
  M\_PToT              - Conversion matrix from source primaries and dest. cmfs.  
  M\_TToP              - Conversion matrix from source cmfs and dest. primaries.  
  M\_TToT              - Conversion matrix from source/dest. cmfs.  
  [PhotonAbsorptionRate](PhotonAbsorptionRate) - Compute photon absoroption rate.  
  [PupilDiameterFromLum](PupilDiameterFromLum) - Estimate pupil diameter from luminance.  
  [PsychMunsell](PsychMunsell)        - Munsell renotation to xyY conversion.  
  [RetIrradianceToIsoRecSec](RetIrradianceToIsoRecSec) - Convert retinal irradiance (power units) to iso. per receptor per second.  
  [RGBToXYZMatrix](RGBToXYZMatrix)      - Build a 3x3 CSC matrix for converting some RGB color space to XYZ space.  
  [SampleCircle](SampleCircle)        - [Sample](Sample) points on a circle.  
  [SampleSphere](SampleSphere)        - [Sample](Sample) points on a sphere.  
  [ShiftSpectra](ShiftSpectra)        - Shift a spectral function along the wavelength axis.  
  [SPDToCCT](SPDToCCT)            - Find correlated color temperature of a spectrum.  
  [SPDToLinSPD](SPDToLinSPD)         - Find approximation within specified linear model.  
  [SPDToMetSPD](SPDToMetSPD)         - Find a metameric spd.  
  [SplineCmf](SplineCmf)           - Spline color matching functions to new wavelength sampling.  
  [SplineRaw](SplineRaw)           - Subroutine for other spline functions.  
  [SplineSpd](SplineSpd)           - Spline a spectral power distribution to new wavelength sampling.  
  [SplineSrf](SplineSrf)           - Spline a surface reflectance function to new wavelength sampling.  
  [SRGBPrimaryToXYZ](SRGBPrimaryToXYZ)    - Convert between sRGB primary coordinates and XYZ.  
  [SRGBGammaCorrect](SRGBGammaCorrect)    - Convert between sRGB primary coordinates and 8-bit RGB values.  
  [SRGBGammaUncorrect](SRGBGammaUncorrect)   - Convert between sRGB 8-bit RGB values and primary coordinates.  
  [SToWls](SToWls)              - Convert S wavelength sampling spec to wls format.  
  [TriToMetSPD](TriToMetSPD)         - Compute metamer from tristimulus coordinates.  
  [WattsToRetIrradiance](WattsToRetIrradiance) - Get absolute retinal irradiance (power units) from rel. spectrum and watts/area.  
  [uvTols](uvTols)              - Convert between CIE u'v' and a cone based (ls) chromaticity.  
  [uvToxy](uvToxy)              - Convert between CIE u'v' and CIE xy chromaticity.  
  [uvYToXYZ](uvYToXYZ)            - Convert between u'v'Y and XYZ.  
  [WlsToS](WlsToS)              - Convert wls wavelength sampling spec to S format.   
  [WlsToT](WlsToT)              - Compute identity color matching matrix from wavelength sampling.  
  [xyTouv](xyTouv)              - Convert CIE xy chromaticity to CIE u'v' chromaticity.  
  [xyYToXYZ](xyYToXYZ)            - Convert between xyY and XYZ.  
  [XYZToF](XYZToF)              - Subroutine for Lab/Luv calculations.  
  [XYZToLab](XYZToLab)            - Convert between XYZ and Lab.  
  [XYZToLjg](XYZToLjg)            - Convert between XYZ (10 degree) and OSA UCS Ljg.  
  [XYZToLuv](XYZToLuv)            - Convert between XYZ and Luv.  
  [XYZToRGBMatrix](XYZToRGBMatrix)      - Build a 3x3 CSC matrix for converting XYZ space to some RGB color space.  
  [XYZToSRGBPrimary](XYZToSRGBPrimary)    - Convert between XYZ and sRGB primary coordinates.  
  [[XYZTouv](XYZTouv)][(XYZTouv)]((XYZTouv))             - Compute uv chromaticities from XYZ.  
  [XYZTouvY](XYZTouvY)            - Convert between XYZ and u'v'Y.  
  [XYZToxyY](XYZToxyY)            - Convert between XYZ and xyY.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/Contents.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/Contents.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/Contents.m</code>
</div>

{{category}}