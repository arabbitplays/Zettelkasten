## Image Memory Barrier

- used to transition image layouts and transferring queue family ownership

```c++
VkImageMemoryBarrier barrier{};

// configure barrier

vkCmdPipelineBarrier( 
	commandBuffer, 
	srcStage, dstStage, 
	0, // per-region condition
	0, nullptr, // memory barriers
	0, nullptr, // buffer barriers
	1, &barrier ); // image barriers
```

- configuring the barrier
	- new and old layout
	- the image and the subresource range
	- `srcAccessMask` - which types of operations should finish before the barrier
	- `dstAccessMask` - which types of operations should wait at the barrier
- `srcStage` - in which stage happen the operations that should finish before the barrier
- `dstStage` - in which stage happen the operations that should wait for the barrier
- see possible combinations [https://docs.vulkan.org/spec/latest/chapters/synchronization.html#synchronization-access-types-supported | here]  

```c++
// examples for the parameters in a rasterization pipeline
if (oldLayout == VK_IMAGE_LAYOUT_UNDEFINED && newLayout == VK_IMAGE_LAYOUT_TRANSFER_DST_OPTIMAL) { 

	barrier.srcAccessMask = 0; 
	barrier.dstAccessMask = VK_ACCESS_TRANSFER_WRITE_BIT; 
	sourceStage = VK_PIPELINE_STAGE_TOP_OF_PIPE_BIT; 
	destinationStage = VK_PIPELINE_STAGE_TRANSFER_BIT; 
	
} else if (oldLayout == VK_IMAGE_LAYOUT_TRANSFER_DST_OPTIMAL && newLayout == VK_IMAGE_LAYOUT_SHADER_READ_ONLY_OPTIMAL) { 

	barrier.srcAccessMask = VK_ACCESS_TRANSFER_WRITE_BIT; 
	barrier.dstAccessMask = VK_ACCESS_SHADER_READ_BIT; 
	sourceStage = VK_PIPELINE_STAGE_TRANSFER_BIT; 
	destinationStage = VK_PIPELINE_STAGE_FRAGMENT_SHADER_BIT; 
}
```