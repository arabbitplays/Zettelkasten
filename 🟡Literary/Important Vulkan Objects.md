# Important Vulkan Objects

- glfw Window
	- the real window implementation
- physical device
	- may need specific extensions and other features to support functionality
	- supports different kind of [[Queues]] families for different kinds of operations
- logical device
- window surface
	- platform agnostic version of a window
	- is backed by the actual window implementation
- swap chain
	- queue of images to render to and to present
	- owns the buffers that are rendered to
	- defines the size of the images (and thus the frame buffers)
- image view
	- wrapper to interact with an image
	- defines the type of image (2D depth texture for example), if mipmapping is used etc.
- pipeline
	- shader modules
		- wrapper for shader code, is put in into the programmable stage infos
	- fixed stages
		- viewport and scissors
		- rasterizer
		- multisampling
		- color blending
		- pipeline layout
	- render pass
		- defines the buffers (attachments) to use while rendering
		- these indices are directly referenced in the shader code
- framebuffers
	- they wrap around the image views (one for each image)
	- the eright one has to be bound when recording the command buffer
- command buffers
	- have to be allocated from a command pool


---

Origin: https://vulkan-tutorial.com/Introduction
References: [[Vulkan Index]]
Tags: 
Created: 27.09.2024

