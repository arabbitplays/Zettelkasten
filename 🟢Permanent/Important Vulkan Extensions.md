
# Important Vulkan Extensions

```c++
std::vector<const char*> getRequiredExtensions() {  
    uint32_t glfwExtensionCount = 0;  
    const char** glfwExtensions;  
    glfwExtensions = glfwGetRequiredInstanceExtensions(&glfwExtensionCount);  
  
    std::vector<const char*> extensions(glfwExtensions, glfwExtensions + glfwExtensionCount);  
  
    if (enableValidationLayers) {  
        extensions.push_back(VK_EXT_DEBUG_UTILS_EXTENSION_NAME);  
    }  
    //Add other instance extensions here
  
    return extensions;  
}
```

- `VK_KHR_surface`
	- Gives an abstract surface to render images to, backed up by a real window like from glfw
	- Already in `glfwGetRequiredInstanceExtensions()`
- `VK_KHR_swapchain` (`VK_KHR_SWAPCHAIN_EXTENSION_NAME`)
	- Device Extension
	- For swap chain support

---

Origin: https://vulkan-tutorial.com/Introduction
References: [[Vulkan Index]]
Tags: 
Created: 27.09.2024

