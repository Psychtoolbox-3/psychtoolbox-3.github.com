# [Datapixx('SetVideoHorizontalSplit')](Datapixx-SetVideoHorizontalSplit) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


The Datapixx has two independant analog video outputs, VGA1 and VGA2. There are  
two ways in which these dual video outputs can be driven. In "mirror" mode, the  
two outputs receive the same image. This could allow a tester to have his own  
stimulus console during testing. In "split" mode, the left half of the image is  
presented on VGA1, and the right half of the image is presented on VGA2. This  
would create perfectly synchronized dual displays, ideal for applications like  
haploscopes. The [SetVideoHorizontalSplit](SetVideoHorizontalSplit) "mode" can take on one of the following  
values:  
   0: MIRROR, VGA1 and VGA2 get identical images  
   1: SPLIT, VGA1/2 get left/right halves of image  
   2: AUTO (default value), Datapixx automatically switches to SPLIT when the  
horizontal resolution is at least twice the vertical resolution.  
  


###See also:
[SetVideoMode](Datapixx-SetVideoMode), [GetVideoStatus](Datapixx-GetVideoStatus)
