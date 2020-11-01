# [PsychOneliners](PsychOneliners)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

Psychtoolbox:[PsychOneliners](PsychOneliners).  
  
  
  [AddStructs](AddStructs)              - Merges input structs into one struct.  
  [AddToMatlabPathDynamically](AddToMatlabPathDynamically) - Add a directory tree to the Matlab path at runtime  
  [AltSize](AltSize)                 - ALTSIZE is an extension of SIZE, it supports querying the size of multiple dimensions of a variable in one call.  
  [AreStructsEqualOnFields](AreStructsEqualOnFields) - Are two structures the same on the passed list of fields?  
  [Ask](Ask)                     - Display message, get user's response.  
  [AssertGLSL](AssertGLSL)              - Require the [OpenGL](OpenGL) shading language is supported.  
  [AssertMex](AssertMex)               - Detect missing mex file and exit with error.  
  [AssertOpenGL](AssertOpenGL)            - Require that Psychtoolbox be based on [OpenGL](OpenGL).  
  [AssertOSX](AssertOSX)               - Require that Psychtoolbox be based on OS X.  
  [BackupCluts](BackupCluts)             - Make internal backup of (given) Cluts, for later restoration via [RestoreCluts](RestoreCluts).  
  [BlackIndex](BlackIndex)              - Returns number that will produce the color black.  
  [CatStr](CatStr)                  - Concatenate array or cell array of strings.  
  [CenterMatOnPoint](CenterMatOnPoint)        - Returns indices to center a matrix on a point.  
  [Circle](Circle)                  - Returns a boolean mask in the shape of a [Circle](Circle).  
  [CleanStruct](CleanStruct)             - Deletes all empty structs and fields from a struct array, optionally recursively.  
  [ComputeHDRStaticMetadataType1ContentLightLevels](ComputeHDRStaticMetadataType1ContentLightLevels) - Compute CTA-861-G static content light levels for an image or a cell array of images.  
  [CreateUniformDotsIn3DFrustum](CreateUniformDotsIn3DFrustum) - [Sample](Sample) dots in 3D frustum uniformly.  
  [CropBlackEdges](CropBlackEdges)          - Detects if there are any black edges around an image and returns indices that can be used to cut away these edges.  
  [DeEmptify](DeEmptify)               - Deletes empty cells or rows from cellarray.  
  [DegToMrad](DegToMrad)               - Convert angle in degrees to milliradians (mrad).  
  [DescribeComputer](DescribeComputer)        - Print a description of the environment.  
  [DotOffset](DotOffset)               - Calculate offsets for a 3D movement. Various per-dot options.  
  [Ellipse](Ellipse)                 - Returns a boolean mask in the shape of a (super-) [Ellipse](Ellipse).  
  [EnforcePos](EnforcePos)              - Truncate negative values of a vector to 0.  
  [Explode](Explode)                 - Splits a numeric or character array by a delimiter or delimiter-pattern.  
  [FillEmptyFields](FillEmptyFields)         - Fill all empty fields of a struct(array) or all empty elements of a cellarray with specified value.  
  [FindInd](FindInd)                 - Returns indices in all dimensions to non-zero elements in matrix.  
  [FindRepeatAlongDims](FindRepeatAlongDims)     - Find repeated rows or columns in a matrix.  
  [FunctionFolder](FunctionFolder)          - Get full path to folder containing passed function.  
  [GetEchoNumber](GetEchoNumber)           - Get a number typed on-screen.  
  [GetEchoString](GetEchoString)           - Get a string typed on-screen.  
  [GetKbChar](GetKbChar)               - Simple, limited replacement for [GetChar](GetChar)(), using [KbCheck](KbCheck) for character input.  
  [GetMyCaller](GetMyCaller)             - Returns the name of the calling function.  
  [GetNumber](GetNumber)               - Get a number typed at the keyboard.  
  [GetOctlibDir](GetOctlibDir)            - Get path to Octave runtime libraries.  
  [GetString](GetString)               - Get a string typed at the keyboard.  
  [GetSubversionPath](GetSubversionPath)       - Return path required to invoke snv.  
  [GetSVNInfo](GetSVNInfo)              - Find info on SVN version number of directory or file.  
  [GetWithDefault](GetWithDefault)          - Get string or number with prompt and default value.  
  [GrayIndex](GrayIndex)               - Any graylevel from black (0) to white (1).  
  [GroupStructArrayByFields](GroupStructArrayByFields) - An aid to sorting data kept in structure arrays.  
  [hexstr](hexstr)                  - Hex string of lowest 32 bits of any number.  
  [ImageToVec](ImageToVec)              - Convert a grayscale image to vector format.  
  [Ind2Str](Ind2Str)                 - Converts numbers to characters (decimal to base 26 conversion). Useful for character indices.  
  [Interleave](Interleave)              - Interleaves any number of arrays. Can handle different data types.  
  [IsACell](IsACell)                 - Tests (recursively--cells in cells) if a cell satisfies a user-supplied condition.  
  [IsARM](IsARM)                   - Return if running on a processor with ARM architecture, typically a mobile or embedded system.  
  [IsGLES](IsGLES)                  - Return if the current rendering api in use is [OpenGL](OpenGL)-ES, the "[OpenGL](OpenGL) Embedded Subset".  
  [IsGLES1](IsGLES1)                 - Return if the current rendering api in use is [OpenGL](OpenGL)-ES 1.x.  
  [IsGUI](IsGUI)                   - Is the Matlab or Octave GUI enabled in this session?  
  [IsLinux](IsLinux)                 - Shorthand for testing whether running under Linux.  
  [IsMinimumOSXVersion](IsMinimumOSXVersion)     - Query if this is a specific OS/X version or higher.  
  [IsOctave](IsOctave)                - Shortand for testing whether running under Octave.  
  [IsOSX](IsOSX)                   - Return if running on a Apple OSX operating system.  
  [IsWin](IsWin)                   - Return if running on a MS-Windows operating system.  
  [Is64Bit](Is64Bit)                 - Return if script is running on a 64-Bit Octave or Matlab.  
  [KbMapKey](KbMapKey)                - Checks if any of specified keys is depressed in a vector returned by [KbCheck](KbCheck), [KbWait](KbWait) etc.  
  kPsychGUIWindow         - Flag to ask [Screen](Screen)() to create onscreen windows with behaviour similar to normal GUI windows.  
  kPsychGUIWindowWMPositioned - Flag to ask [Screen](Screen)() to leave onscreen GUI window placement to the window manager.  
  [LoadIdentityClut](LoadIdentityClut)        - Loads the identity CLUT on a specified monitor.  
  [log10nw](log10nw)                 - Compute log base 10 without annoying warnings.  
  [MacModelName](MacModelName)            - Mac model name, e.g. 'PowerBook G4 15"'.  
  [Magnify2DMatrix](Magnify2DMatrix)         - [Expand](Expand) the size of a two-dimensional matrix via entry replication.  
  [MakeBeep](MakeBeep)                - Compute a beep of specified frequency and duration, for [Snd](Snd).  
  [MakeCosImage](MakeCosImage)            - Make a cosinusoidal image.  
  [MakeGrid](MakeGrid)                - Makes raster of elements centered on screen / in image (leftover space is divided equally over the edges).  
  [MakeSincImage](MakeSincImage)           - Make a sinc image.  
  [MakeSineImage](MakeSineImage)           - Make a sinusoidal image.  
  [MapIndexColorThroughClut](MapIndexColorThroughClut) - Convert an index color image and clut to a true color image.  
  [MergeCell](MergeCell)               - Concatenates contents of input cells element-wise.  
  [MradToDeg](MradToDeg)               - Convert angle in milliradians (mrad) to degrees.  
  [NameBytes](NameBytes)               - Nicely format memory size for human readers.  
  [NameFrequency](NameFrequency)           - Nicely format clock rate for human readers.  
  [NearestResolution](NearestResolution)       - Find a screen resolution that most closely matches a requested resolution.  
  [[OSName](OSName)][(OSName)]((OSName))                  - Convential English-language name of your operating system.  
  overrideBuiltInFunction - Temporarily run a different version of some function other than what is on the path.  
  [PackColorImage](PackColorImage)          - Pack three color planes into one m by n by three matrix.  
  [ProgressBar](ProgressBar)             - Displays a progress bar in MATLAB's command window.  
  [PsychDebugWindowConfiguration](PsychDebugWindowConfiguration) - Enable special debug window configuration to aid single display debugging.  
  [PsychDefaultSetup](PsychDefaultSetup)       - Setup various defaults for Psychtoolbox session.  
  [PsychGPUControl](PsychGPUControl)         - Control low-level operating parameters of certain supported GPU's.  
  [PsychNumel](PsychNumel)              - Drop-in replacement for numel() on old Matlab versions that don't support it.  
  [PsychtoolboxRoot](PsychtoolboxRoot)        - Robust way to get path to Psychtoolbox folder, even if renamed.  
  [RemoveMatchingPaths](RemoveMatchingPaths)     - Removes folders that contain a given string from the path.  
  [RemoveSVNPaths](RemoveSVNPaths)          - Removes ".svn" folders from the path.  
  [Replace](Replace)                 - Perform exact [Replace](Replace) on strings or numeric arrays.  
  [Resolute](Resolute)                - Cuts from and adds to a matrix to make it the specified dimensions.  
  [RestoreCluts](RestoreCluts)            - Restore original CLUT's for all monitors from backups made during [LoadIdentityClut](LoadIdentityClut)().  
  Rot3d                   - Rotates a matrix in 3D space (around the x, y or z axis) in 90 degrees steps.  
  [SaveIdentityClut](SaveIdentityClut)        - Store current or given CLUT as identity LUT for use with [LoadIdentityClut](LoadIdentityClut).  
  [SaveMovieFrames](SaveMovieFrames)         - Displays a GUI in which a movie can be played and from which screenshots can be saved.  
  [sca](sca)                     - Shorthand for [Screen](Screen)('CloseAll').  Using this is a good way to make your code obscure.  
  [ScreenDacBits](ScreenDacBits)           - What is precision of the graphics boardDACs. Currently returns 8 always.  
  [SetResolution](SetResolution)           - Change display resolution, refresh rate and color depths to requested values.  
  [ShrinkMatrix](ShrinkMatrix)            - Shrinks a 2-D or 3-D matrix (an image) by a factor.  
  [SmartVec](SmartVec)                - Creates a vector/sequence that satisfies certain conditions.  
  [SortCell](SortCell)                - Sorts cell matrices containing different data types in different columns.  
  Speek                   - Use speech synthesis output to speak a given text. Mac OS/X only.  
  [Stopwatch](Stopwatch)               - Time intervals.  
  streq                   - strcmp.  
  [StrPad](StrPad)                  - Makes a string a specified length, either by pre-padding it with a specified character or cutting from its beginning.  
  [Struct2Vect](Struct2Vect)             - Returns (cell-) array with all values in a specified field of a structure array.  
  [TextBounds](TextBounds)              - Draw string, return enclosing rect.  
  [TextCenteredBounds](TextCenteredBounds)      - Draw string, centered, return enclosing rect.  
  [UnpackColorImage](UnpackColorImage)        - Extract three color planes from an m by n by 3 color image.  
  [VecToImage](VecToImage)              - Convert a grayscale image from vector to image format.  
  [WhiteIndex](WhiteIndex)              - Returns number that will produce the color white.  
  [WinDesk](WinDesk)                 - Sends command to windows shell to minimize all Windows, equal to Windows+M.  
  [WrapString](WrapString)              - Word wrap (break into lines).  
  
  
The following is a list of old one-liners that might some day be updated  
from PTB-2, but haven't been yet.  
  
  [BlankingInterruptRate](BlankingInterruptRate) - Used by [PsychBasic](PsychBasic) [FrameRate](FrameRate).  
  [ClutDefault](ClutDefault)           - Returns standard clut for screen at any pixelSize.  
  [CmdWinToUpperLeft](CmdWinToUpperLeft)     - Bring Command window forward, saving [Screen](Screen) window.  
  [DescribeScreen](DescribeScreen)        - Print a description of the screen's video driver.  
  [DescribeScreenPrefs](DescribeScreenPrefs)   - Print more about the screen's video driver.  
  [GammaIdentity](GammaIdentity)         - Returns an identity gamma table appropriate to the screen's dacSize.  
  [IsDownArrow](IsDownArrow)           - Is char the down arrow?  
  [IsLeftArrow](IsLeftArrow)           - Is char the left arrow?  
  [IsRightArrow](IsRightArrow)          - Is char the right arrow?  
  [IsUpArrow](IsUpArrow)             - Is char the up arrow?  
  [IsInOrder](IsInOrder)             - Are the two strings in alphabetical order?  
  [IsPopCharProInstalled](IsPopCharProInstalled) - Is the Control Panel "[PopChar](PopChar) Pro" installed?  
  [MaxPriorityGetSecs](MaxPriorityGetSecs)    - Figure out the maximum priority compatible with [GetSecs](GetSecs). Slow.  
  [ScreenClutSize](ScreenClutSize)        - How many entries in the graphic card Color Lookup Table?  
  [ScreenUsesHighGammaBits](ScreenUsesHighGammaBits) - Does this card use the high 10 bits of the gamma values?  
  [SCREENWinToFront](SCREENWinToFront)      - Bring [Screen](Screen) window back in front of Command window.  
  [ShowTiff](ShowTiff)              - Show a TIFF file, calibrated.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/Contents.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/Contents.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/Contents.m</code>
</div>

{{category}}