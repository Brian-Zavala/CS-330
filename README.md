# CS-330 Computational Graphics and Visualization

My final project for CS-330. It's a 3D scene built in OpenGL that recreates a small
desk workspace from a 2D photo: an open laptop on a dark wood desk, a white coffee
mug behind it, and a phone off to the right, with a drywall wall behind everything.

The full Visual Studio project is in `3D_Scene.zip`, and my write-up on the modeling
and design choices is in `Zavala_Brian_Design_Decisions.docx`.

## What's in the scene

- Laptop built from two box meshes (base + a screen leaned back ~15 degrees)
- Mug made from a cylinder body and a torus handle
- Plane desk, plane back wall, and a box phone
- Image textures on the desk, wall, and laptop screen; flat colors on the rest
- Two point lights (warm key, cool blue fill) with full Phong shading
- Camera you can fly around with, and an orthographic/perspective toggle

## Controls

- W/A/S/D move forward, left, back, right
- Q up, E down
- Mouse looks around (pitch/yaw)
- Scroll wheel changes movement speed
- P perspective, O orthographic

## Building it

Open `7-1_FinalProjectMilestones.sln` in Visual Studio 2022 and build in x64. The
GLEW, GLFW, and GLM libraries are included under `Libraries/`, and the include/lib
paths are already set in the project. The exe loads its shaders and textures with
relative paths, so run it from the project directory.

## Reflection

**How do I approach designing software?**

This project pushed me to plan before writing code. I started from a real photo and
broke it down into shapes I could actually build, a desk that's just a plane, a
laptop that's two boxes, a mug that's a cylinder plus a torus. Committing to one
reference image up front kept me from drifting. The design skill I got better at was
thinking in primitives and transforms instead of trying to model something
complicated all at once. My process was pick the reference, list the objects, decide
which primitives each needs, then add textures and lighting last. I can reuse that
same approach later: get the structure roughly right first, then worry about how it
looks.

**How do I approach developing programs?**

The milestone setup made me build the scene in stages, and that was the real lesson.
I didn't write it all at once. I'd place one object, run it, fix the position by eye,
then move on. Iteration was constant, especially with lighting and the camera where
the only way to know if a value was right was to run it and look. I also split the
setup into smaller helper functions (loading textures, defining materials, setting up
lights) so the main render code stayed short and I could change one piece without
breaking the rest. My approach changed a lot across the milestones. Early on I was
hardcoding things and copying blocks of code, and by the end I was writing functions
I could reuse and thinking about how to make the next object easy to drop in.

**How can computer science help me in reaching my goals?**

This course gave me a real feel for how a GPU turns data into a picture: vertices,
transforms, shaders, textures, lighting. For school it makes the more advanced
graphics and game courses less intimidating since I already know the pipeline.
Professionally the same ideas show up in web graphics with WebGL, in data
visualization, and in simulation work, so I can apply it even if I'm not building a
game. More than the specific OpenGL calls, the habit of breaking a hard visual
problem into small buildable pieces and iterating on it is something I'll carry into
whatever I work on next.
