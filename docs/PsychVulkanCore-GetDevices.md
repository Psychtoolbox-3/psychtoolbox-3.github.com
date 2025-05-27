# [PsychVulkanCore('GetDevices')](PsychVulkanCore-GetDevices) 
##### [Psychtoolbox](Psychtoolbox)>[PsychVulkanCore](PsychVulkanCore).{mex*} subfunction

devices = PsychVulkanCore('GetDevices');

Returns an array of structs enumerating all currently available Vulkan driver +  
GPU combos.  
Each struct in the array describes one combination of Vulkan driver and device,  
with the following fields:  
  
'DeviceIndex' = Index of the device. Can be used in 'OpenWindow' as 'gpuIndex'.  
'GpuName' = Name of the Vulkan device / graphics card.  
'GpuDriver' = Name of the Vulkan driver associated with the device.  
'DriverInfo' = Additional info associated with the driver, vendor specific.  
'DriverVersion' = Major.minor.point version string with the driver version.  
'DriverVersionRaw' = Raw scalar Vulkan driver version.  
'DriverId' = Id of the type of Vulkan driver: 1 = AMD proprietary, 2 = AMD open  
             source amdvlk, 3 = AMD OSS Mesa radv, 4 = [NVidia](NVidia) proprietary,  
             5 = Intel proprietary Windows, 6 = Intel OSS Mesa anvil,  
             13 = Mesa OSS llvmpipe.  
'VendorID' = Vulkan device vendor id. Typically the PCI vendor id.  
'DeviceID' = Vulkan device id. Typically the PCI device id.  
'VulkanVersion' = Major.minor.point version of supported Vulkan api.  
'GpuType' = Type of device: 0 = Unknown/Other, 1 = Integrated gpu,  
            2 = Discrete gpu, 3 = Virtual gpu, 4 = cpu, ie. software renderer.  
  
'SupportsHDR' = Does the gpu support driving HDR displays in principle?  
                0 = No, 1 = Basic HDR-10.  
'SupportsTiming' = Does the gpu support high precision/reliability timing  
                   extensions. 0 = No, 1 = Yes. If the driver does not support  
                   timing extensions, the driver will fall back to hacks.  
'SupportsWait' = Does the gpu support waiting for present completion: 0 = No, 1  
= Yes.  
  
  


###See also:
[GetCount](PsychVulkanCore-GetCount)
