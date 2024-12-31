<h1>An interop between Vulkan and CUDA</h1>
I love GPU programming, and Vulkan and CUDA are two of my favorite GPU interfaces to work with.
<h3>Vulkan</h3>
Vulkan does graphics. It's extremely fast in everything related to displaying something on a screen.
Vulkan is difficult to work with because of how verbose it is. The developer has to specify every tiny
thing that they want, even to the point of redundancy sometimes. However, this makes Vulkan incredibly fast.
<h3>CUDA</h3>
CUDA is made for computation. Designed specifically for Nvidia cards, it's fantastic at crunching out numbers
for computations that can be parallelized (linear algebra is a great example)
<h2>The interop</h2>
Getting Vulkan and CUDA to work together is quite difficult. There aren't many resources about it online,
and Vulkan requires a lot of prep work.
Here's an abbreviated to-do list:<br>
  1. Create a VkImage <br>
  2. Pass the image handle to CUDA <br>
  3. Create a CUDA surface object tied to the VkImage<br>
  5. Create two VkSemaphores<br>
  6. Create CUDA semaphores that has the same handle as the VkSemaphores<br>
  7. Start the VkRenderPass and do all of the frame setup<br>
  8. Signal one of the semaphores to tell CUDA to go ahead<br>
  9. Raytrace the scene and write the results to the surface tied to the VkImage<br>
  10. Signal the second semaphore to tell Vulkan that the VkImage is ready for presentation<br>
  11. goto 7<br>
<h2>Sources</h2>
https://github.com/NVIDIA/cuda-samples/blob/master/Samples/5_Domain_Specific/vulkanImageCUDA/vulkanImageCUDA.cu
https://forums.developer.nvidia.com/t/cuda-vulkan-vkimage-interop/278691
https://stackoverflow.com/questions/55424875/use-vulkan-vkimage-as-a-cuda-cuarray
  
