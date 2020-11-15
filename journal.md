# Interactive 3D Graphics - First assignment

## Before getting started

We've been tight for time since the beginning, this course is an elective for both of us and we struggled a lot to find some time to realise the whole project. We decided, by the way, to take time during a weekend and try to realise something simple, intereseting and good.

We have a lot of ideas, but none of them seemed to convince us both. We experimented for a few hours with lights, cubes and buildings and then we found an interesting idea to base our project on.

<img src="lunes.jpg" style="float: right; width: 30%;">

## The main idea
The main ispiration comes from a funny short cartoon we used to watch when we were kids, distributed by Ferrero, which was called "I Lunes e la Sfera di Lasifer". In this little movie, a group of strange characters lives in a pyramid that opens itself like a draw when they have to get out. 

We decided we could build a pyramid made of cubes with a little "phraoh grave" inside that opens itself in an interesting way, making the whole sarcophagus visible.


## Building

We are working together for most of the time, but we're trying to parallelize our work as much as we can.
We realized the whole grave and the pyramid separately and then put everything together in a single script. 
We applied a lot of interesting textures to out block in order to make them look fancy. 


## Lights and dome

After completing the building, we are focusing on light in order to make everything look as realistic as possible. We are using a Directional and an Emissive light in order to simulate the sunlight, while we are using a Point light to build the pyramid's inner lightning. 

We based on a three.js example that is linked in our project references. We also applied a shader to realize our dome in order to make it look as similar to the sky as possible.


## Animation 

After the whole lightning is completed, we are now focusing on programming an interesting animation to open the pyramid. We don't want it to look like the scene of the cartoon mentioned above. 

After messing with pivots a bit, with found a cool way to open the pyramid and we decided that this is the kind of animation we wanted to implement.


## Assigning animation to dat.gui 

We decided to assign the animation to a button and we read on the initial "readme.txt" that the library dat.gui is what we need to do that. 
Aftering checking the library documentation and a few three.js examples, we figured out how to implement dat.gui functionalities. 

We assigned the control of the animation to a fancy button that allows the user to both open and close the pyramid even if the opening or closing is not yet completed.


## Optimization

We are now observing that the whole scene is quite heavy and FPS dropped, so we might need to optimize a few things.
On an **nVidia RTX 2060** with a 140Hz update frequency FULL HD monitor, the whole scene (on Chrome, with all the accelerations enabled) wasn't running that smooth. 

We observed the same result by running the scene on a MacBook Pro 16" 2019 (with a 60Hz update frequency 2K monitor on Chrome with all the accelerations enabled). Particularly, the MacBook Pro wasn't really smooth when running on its AMD Radeon Pro 5500M 4 GB and was completely laggy when running on the intergated intel graphics card.

We read an interesting [article about optimization](https://codeburst.io/improve-your-threejs-performances-with-buffergeometryutils-8f97c072c14b) on [Codeburst](https://codeburst.io/) and we decided to implement the usage of **mergeBufferGeometries** from **BufferGeometryUtils**. This allows to send all the geometry merged to the GPU only once insted of heaving to send every geometry separatly which causes a computational overload. 

However, applying this modification is not as easy as we expected to. We have to build the static truncated pyramid first, and then we have to build the rest of the pyramid (which is the part that will be object of the animation) separately. While doing that, we have to store all the geometries in an array insted of adding them to the Object3D scene. We will later marge all of them and add everything to scene only once as a single geometry. 

After applying this modification, we observed a great improvement in performances which now are as smooth as we wanted to since the beginning. 

