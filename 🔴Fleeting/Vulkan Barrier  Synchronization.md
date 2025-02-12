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

- `srcStage` - in which stage happen the operations that should finish before the barrier
- `dst`