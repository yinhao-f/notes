# Computer graphics

- Rendering
- Animation

## Rendering

### OpenGL (Open Graphics Library) is an API to graphics hardware

- Cross language
- Cross platform

### OpenGL ES (Embedded Systems)

For mobile and embedded systems

### Web GL

Web based, control code written in JavaScript, shader code written in OpenGL ES

[Fun demo](https://madebyevan.com/webgl-water/)

### Single 3D object

How to describe a piece of geometry?

- point clouds
- polygons
- grid

#### Triangle meshes

Triangle: 3 vertices  
Mesh: vertices, triangles

#### Frame buffer

RAM on GPU, what we see

#### Screen

Displays what's in the frame buffer

Pixel: basic element on device  
Resolution: number of rows and columns in device

### Summary

#### Input

3D objects, usually triangles

#### Output

2D image, a grid of (r,g,b) pixels

### Scene

- Coordinate frame
- 3D objects
- Materials
- Lights
- Camera(s)

### Interpolation

### Bounding box

Compute the max and min of x and y coordinates, therefore creating a "bounding box". Then check the pixels inside the box. 

### Rasterization

### Ray tracing


