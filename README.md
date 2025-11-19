# System Programming Lab 11 Multiprocessing

## Overview
For this Lab, I decided to just modify the provided mandelbrot program, adding two command line arguments
- -n which controls the number of frames to generate
- -p which controls the number of processes to use during generation

I used a simple for loop to create the number of processes up to the value defined by the -n argument then ran the image generation code in each loop.

``` C
  for(int i = 0; i < num; i++){
    if(active_proc >= max_proc){
      wait(NULL);
      active_proc--;
    }

    int pid = fork();
    if (pid == 0){


		//modifies the x scale for each child process
    double child_xscale = xscale / pow(1.1, i);
...
```
## Processes vs. Runtime

![Runtime Graph](graph.png)

The runtime follows an inverse exponential, where the first increases have very large time losses associated with them, but the difference decreases as the number of processes increases