# mousearm

When running on desktop, [LÖVR](https://github.com/bjornbytes/lovr) has an implementation of virtual headset and a left hand controlled by a mouse.

This little module changes how the mouse controls the VR hand. The cursor position on the screen is directly mapped into the 3D world space, acting as a 3D pointer. This makes UI interactions and other precise mouse operations easy and intuitive. The distance of the pointer from the near camera plane can be controlled with the mouse wheel. The trigger button is mapped to the right mouse button, and the grip button is mapped to middle mouse button.

Note that this module dynamically replaces some of `lovr.headset` functions. This is not a particularly good practice to use in shipped code. The library is intended as helpful utility for desktop development and quick testing between desktop and VR. For any desktop-only LOVR projects I would recommend to take the 2D-to-3D mouse calculation from this library and re-implement it properly instead of reusing the VR headset API.

### Usage:

Just like the built-in virtual headset, the mouse-controlled 3D pointer is exposed as if it was the tracked left hand device. The same API is used for getting pose, position, orientation and velocity.

There's also a handy `getRay()` exposed function that can be used for raycasting into the 3D space.

```lua
require('mousearm') -- place this at the top of your `main.lua` file

function lovr.draw(pass)
  -- draw a pointer
  pass:setColor(0xfcf57e)
  pass:sphere(vec3(lovr.headset.getPosition('left')), .05)
end


-- cast a ray against the shapes added to the physics world instance
local ray = mousearm.getRay() -- by default the ray is 1000m long
world:raycast(ray.origin, ray.target, callback_fn)
```

Older versions of LOVR don't have the built-in mouse support and need additional library [lovr-mouse](https://github.com/bjornbytes/lovr-mouse).
