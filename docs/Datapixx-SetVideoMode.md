# [Datapixx('SetVideoMode')](Datapixx-SetVideoMode) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Set Datapixx video processing mode.  
The Datapixx inputs digital DVI data, and outputs analog video. The video "mode"  
determines how the digital data is converted to analog RGB. mode can take on one  
of the following values:  
   0: C24, Straight passthrough from DVI 8-bit RGB to VGA RGB.  
   1: L48, DVI RED[7:0] is used as an index into a 256-entry 16-bit RGB  
      color lookup table.  
   2: M16, DVI RED[7:0] & GREEN[7:0] concatenate into a VGA 16-bit value sent to  
      all three RGB components. This mode also contains a 256-entry color lookup  
      table overlay indexed by the blue component. Set the blue component to 0  
      to allow the 16-bit monochrome data to show through.  
   3: C48, Even/Odd pixel RED/GREEN/BLUE[7:0] concatenate to generate 16-bit RGB  
      components at half the horizontal resolution.  
   5: L48D, DVI RED[7:4] & GREEN[7:4] concatenate to form an 8-bit index into a  
      256-entry 16-bit RGB color lookup table.  
   6: M16D, DVI RED[7:3] & GREEN[7:3] & BLUE[7:2] concatenate into a VGA 16-bit  
      value sent to all three RGB components.  
   7: C36D, Even/Odd pixel RED/GREEN/BLUE[7:2] concatenate to generate 12-bit  
      RGB components at half the horizontal resolution.  
   8: RB24, DVI RED[7:0] & GREEN[7:4] concatenate to form 12-bit RED value,  
      DVI BLUE[7:0] & GREEN[3:0] concatenate to form 12-bit BLUE value,  
      GREEN is forced to 0  
  


###See also:
[SetVideoHorizontalSplit](Datapixx-SetVideoHorizontalSplit), [SetVideoVerticalStereo](Datapixx-SetVideoVerticalStereo), [SetVideoClut](Datapixx-SetVideoClut)
