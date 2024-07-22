# Advanced and Robot Programming: Second Assignment

## Overview

The second assignment for the 'Advanced and Robot Programming' class involves creating an interactive simulator for a simplified vision system that tracks an object in a 2-D plane.

### Contributors

- Miriam Anna Ruggero (4881702)
- Alessio Mura (4861320)
- Ivan Terrile (4851947)

# Simulator Behavior

## Overview

The simulator comprises two processes designed to model a camera system and feature extraction:

### Process A: Camera Simulation

- **Function**: Simulates a moving camera with an 80x30 ncurses window.
- **Controls**: Use arrow keys to move a spot in the window, representing the camera's view.
- **Video Memory**: Simulates a 1600x600 pixel RGB image (3 bytes per pixel) with a 20x magnification factor compared to the ncurses window.
- **Debug Feature**: Clicking in the window with the mouse saves a snapshot of the video memory as a .bmp file.

### Process B: Feature Extraction

- **Function**: Extracts features from the image stored in video memory.
- **Output**: Displays the trajectory of the image's center in a second 80x30 ncurses window.

This setup provides an interactive simulation of image capture and feature tracking, complete with real-time controls and debugging capabilities.

### Repository Structure

- **`src/`**: Contains the source code for all processes.
- **`include/`**: Contains data structures and methods used with the ncurses framework to build the two graphical user interfaces (GUIs).

### Additional Directories

After compiling the program, the following directories will be created:

- **`bin/`**: Contains executable files.
- **`out/`**: Stores .bmp images captured by Process A.

### Compilation and Execution

To compile the program, run:

```bash
$ bash ./compile.sh
```
After compilation, start the program with:
```bash
$ bash ./run.sh
```

## Library installation and usage guide 
To execute the program you need to install the *libbitmap* library. This library is used to read and write bitmap images. It is a shared library, which means that it is not linked to the executable at compile time, but rather at runtime. This allows the library to be updated without having to recompile the programs which use it.

To work with the bitmap library, you need to follow these steps:
1. Download the source code from [this GitHub repo](https://github.com/draekko/libbitmap.git) in your file system.
2. Navigate to the root directory of the downloaded repo and run the configuration through command ```./configure```. Configuration might take a while.  While running, it prints some messages telling which features it is checking for.
3. Type ```make``` to compile the package.
4. Run ```make install``` to install the programs and any data files and documentation.
5. Upon completing the installation, check that the files have been properly installed by navigating to ```/usr/local/lib```, where you should find the ```libbmp.so``` shared library ready for use.
6. In order to properly compile programs which use the *libbitmap* library, you first need to notify the **linker** about the location of the shared library. To do that, you can simply add the following line at the end of your ```.bashrc``` file:      
```export LD_LIBRARY_PATH="/usr/local/lib:$LD_LIBRARY_PATH"```

### Use of the *libbitmap* library in our programs
To use it in our programs:
1. include the library in your programs via ```#include <bmpfile.h>```. If you want to check the content of ```bmpfile.h``` to glimpse the functionalities of the library, navigate to ```/usr/local/include```, where the header file should be located.
2. compile programs which use the *libbitmap* library by linking the shared library with the ```-lbmp``` command.     
