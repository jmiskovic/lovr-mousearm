# mousearm

When running on desktop, [LÖVR](https://github.com/bjornbytes/lovr) has an implementation of virtual headset. It includes the virtual hand controlled with a mouse.

This little project aims to improve the mouse control over the VR hand. Most noteably, it maps the screen coordinates to world space and allows the hand to be extended using the mouse wheel.

The controller buttons are simulated through function keys F1 to F10. For example, TRIGGER is F1 and GRIP is F2. Keys can easily be remapped.

There's also a handy `getRay()` function that can be used for raycasting into the 3D space.

To use, put the script alongside with [lovr-mouse](https://github.com/bjornbytes/lovr-mouse) into your project and just require it at the top of your `main.lua`. The `lovr.headset.getPose()` and similar functions will be replaced.
