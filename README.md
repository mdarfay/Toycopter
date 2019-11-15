# Toycopter
Computer Graphics project made at INSA Rennes, France, 2019. Small animation of a toy helicopter, using OpenGL.

Authors: [Matthieu DARFAY](https://www.github.com/mdarfay) & [Zoé LEVREL](https://www.github.com/zlevrel)

This project results in a 45 seconds animation, that you can watch here : [Toycopter, the movie](https://youtu.be/u-voBjlJ_RU).

## Code sources

Since this is a **school project**, the structure of the classes and the basis of the code was provided by our teacher at INSA Rennes, [Maud Marchal](https://people.rennes.inria.fr/Maud.Marchal/).

We weren't allowed to make this code public, for educational and research reasons. Moreover, it would have been useless to publish only separate functions or parts of the project that we made.

We will make the code public in a few years.

## Description
The project was made with OpenGL. The main part of the code was done in **C++**. Some parts were coded in **GLSL**, in the shaders used by OpenGL.
**External libraries used:** [GLEW](http://glew.sourceforge.net/), [GLM](https://glm.g-truc.net/0.9.9/index.html), [tinyobjloader](https://github.com/syoyo/tinyobjloader).

First (and main) objective of this project was to get familiar with OpenGL, GLSL and basics in computer graphics (including the whole graphics pipeline for displaying 3D objects).
Second objective was to do a small animation, using all the notions seen during the course.

All the notions seen and used are listed below:
* Shader coding, to display vertices, colors and polygons.
* Objects modeling, using mathematical functions and representations, and importing complex meshes (`.obj`).
* Geometric transformations, using differents coordinates system. Includes translating, scaling and rotating objects.
* Hierarchical modeling: linking objects together. Using local (independant from hierarchy) and hierarchical transformations.
* Procedural animation, using keyframes.
* Physically-based animation (springs, particles, planes, force fields, gravity, ...).
* Lighting and shading (Phong illumination model).
* Textures and materials, image filtering and wrapping, mipmapping and multi-texturing.

## Main features of the project
### Modeling
The main object of the animation, the helicopter, consists in 3 objects:
- the body,
- the top blades,
- the tail blades.

These 3 objects are linked together in a hierarchy: the body is the father of the blades. This property is used in the animation process.

The majority of the scene's decor represents Andy's room, from the movie Toy Story. Most of these objects were imported as meshes, and textured afterwards.

### Animations
The helicopter is moved inside the scene procedurally, using keyframes. 
The notion of hierarchy between objects is used, to help create related and independant animations at the same time. 

*For example: the blades of the helicopter rotate independently, but the objects still follow the body of the helicopter, without impacting its own orientation.*

The camera is animated as well. At some steps, it's programmed to follow the helicopter at a certain distance. Otherwise, it's fixed at key positions in the scene.

### Dynamics and physically-based animations
This project implements a dynamic system, in order to solve physical equations for collisions between moving particles.
Particles in the scene are the glass marbles (scattered on the floor) and the ball "Luxo", falling from the desk.
These particles can collide with each other, and collide with the floor as well (plane-particle collisions).

Another object uses physics: the helicopter. A particle is attached to it, and follows its trajectory, in order to ram the ball on the desk and make it fall.

To simulate the gravity and let the ball fall, we added a force field, applying to all the particles in the scene. Another constant force field is used to simulate air viscosity.

### Lighting and texturing
Phong's illumination model is used in this animation. We implemented simple spot lights, point lights and directional lights.
We also coded a color changing light (nightstand lamp).

Materials are applied to objects. These materials have different properties, which define the way the object is illuminated by light sources.

Textures are as well a key element to give the objects their aspect. Some objects (like the stars behind one of the windows) have different textures, which are swapped in a loop, animating the object and the textures.

## Key words
OpenGL - Keyframes - Physically-based animation - Phong's illumination - Materials - Textures

## 3D models references
All the 3D models used in our scene come from internet. Some of them were modified using Blender. All the models can be found below:

**Helicopter:**
https://www.turbosquid.com/fr/3d-models/dinoco-blend-free/459106

**Room:**
https://sketchfab.com/search?q=andy%27s+room&sort_by=-pertinence&type=models

**Photophore (nightstand lamp):**
https://cults3d.com/en/3d-model/home/photophore-ce0f1d43-b04a-4cbf-b056-d1eb2c8bb4ba
