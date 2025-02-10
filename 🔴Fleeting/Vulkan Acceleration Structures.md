# Vulkan Acceleration Structures

- Implementierung von [[Bounding Volume Hierarchie (BVH)]]
- Unterteilung in <mark style="background: #FFB86CA6;">Bottom Level Acceleration Structures (BLAS)</mark> und <mark style="background: #FFB86CA6;">Top Level Acceleration Structure (TLAS)</mark>

## Extensions and Features

- Device Extensions:
```c++
const std::vector<const char*> deviceExtensions = {
    VK_KHR_ACCELERATION_STRUCTURE_EXTENSION_NAME,
    VK_KHR_RAY_TRACING_PIPELINE_EXTENSION_NAME,
    VK_KHR_BUFFER_DEVICE_ADDRESS_EXTENSION_NAME,
};

// add to the pNext pointer of VkDeviceCreateInfo
VkPhysicalDeviceAccelerationStructureFeaturesKHR accelerationStructureFeatures{};
    accelerationStructureFeatures.sType = VK_STRUCTURE_TYPE_PHYSICAL_DEVICE_ACCELERATION_STRUCTURE_FEATURES_KHR;
    accelerationStructureFeatures.accelerationStructure = VK_TRUE;

    VkPhysicalDeviceRayTracingPipelineFeaturesKHR rayTracingPipelineFeatures{};
    rayTracingPipelineFeatures.sType = VK_STRUCTURE_TYPE_PHYSICAL_DEVICE_RAY_TRACING_PIPELINE_FEATURES_KHR;
    rayTracingPipelineFeatures.rayTracingPipeline = VK_TRUE;
    rayTracingPipelineFeatures.pNext = &accelerationStructureFeatures;

    VkPhysicalDeviceBufferDeviceAddressFeatures deviceAddressFeatures{};
    deviceAddressFeatures.sType = VK_STRUCTURE_TYPE_PHYSICAL_DEVICE_BUFFER_DEVICE_ADDRESS_FEATURES;
    deviceAddressFeatures.bufferDeviceAddress = VK_TRUE;
    deviceAddressFeatures.pNext = &rayTracingPipelineFeatures;
```
- Features:

---

Origin: 
References: [[Vulkan Index]]
Tags: 
Created: 13.12.2024

