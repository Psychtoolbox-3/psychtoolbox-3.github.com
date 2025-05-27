# [PsychVulkanCore('GetInteropHandle')](PsychVulkanCore-GetInteropHandle) 
##### [Psychtoolbox](Psychtoolbox)>[PsychVulkanCore](PsychVulkanCore).{mex*} subfunction

[interopObjectHandle, allocationSize, formatSpec, tilingMode, memoryOffset, width, height, interopSemaphoreHandle] = PsychVulkanCore('GetInteropHandle', vulkanWindowHandle [, wantSemaphore=0][, eye=0]);

Retrieve all info needed to import the Vulkan interop image as [OpenGL](OpenGL) renderable  
texture.  
Returned values allow to construct an [OpenGL](OpenGL) GL\_TEXTURE2D object which uses the  
driver internal VkImage's backing memory as backing memory for the [OpenGL](OpenGL)  
texture. Iow. [OpenGL](OpenGL) and Vulkan can share an image buffer into which [OpenGL](OpenGL)  
renders and which is later displayed by [PsychVulkanCore](PsychVulkanCore)() via Vulkan WSI.  
'vulkanWindowHandle' is a handle to the Vulkan window to use for stimulus  
display.  
'wantSemaphore' Optional: If a semaphore interop handle should also be returned  
as 8th return argument. Defaults to 0 = No. 1 = Yes will export the handle, and  
each 'Present' operation on the 'vulkanWindowHandle' will block until the  
returned semaphore is signalled.  
'eye' Optional Eye for which interop data should be returned in a stereo display  
setup:  
0 = Left eye view or monoscopic view, 1 = Right eye view. Defaults to 0.  
Return arguments:  
'interopObjectHandle' Operating system specific handle to the interop image  
backing memory. The caller is responsible for releasing the handle once it is no  
longer needed.  
'allocationSize' Number of bytes of backing memory for the 'interopObjectHandle'  
to import.  
'formatSpec' Type of texture to create: 0 = GL\_RGBA8, 1 = GL\_RGB10A2, 2 =  
GL\_RGBA16F, 3 = GL\_RGBA16.  
'tilingMode' Type of tiling to use/assume for rendering: 0 = Linear (non-tiled),  
1 = Tiled.  
'memoryOffset' Memory offset in bytes into the imported memory object to use.  
'width' Width of texture in pixels.  
'height' Height of texture in pixels.  
'interopSemaphoreHandle' Operating system specific handle to the interop  
semaphore, if one was requested by setting 'wantSemaphore' to 1. The caller is  
responsible for releasing the handle once it is no longer needed.  
  


###See also:

