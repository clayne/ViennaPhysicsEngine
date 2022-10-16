# The Vienna Physics Engine (VPE)
The Vienna Physics Engine (VPE) is a simple, single file physics engine for educational purposes.
Rendering is done by the Vienna Vulkan Engine.

The VPE is developed as basis for game based courses at the Faculty of Computer Science of the University of Vienna, held by Prof. Helmut Hlavacs:

- https://ufind.univie.ac.at/de/course.html?lv=052214&semester=2019W
- https://ufind.univie.ac.at/de/course.html?lv=052212&semester=2019W
- https://ufind.univie.ac.at/de/course.html?lv=052211&semester=2019S

VPE's main contributor is Prof. Helmut Hlavacs (http://entertain.univie.ac.at/~hlavacs/). However, VPE will be heavily involved in the aforementioned courses, and other courses as well.

VPE features are:
- C++20
- Polytopes only
- Sequential impulse based
- Implements two solvers to choose from
- Friction
- Contact set reduction
- Warm starting, stable stacking

# Set up for Windows 10

The whole engine is contained in VPE.hpp. Clone the project, open the .sln file, compile, run.
For Windows 11, all non-Vulkan dependencies are in the external directory. The Vulkan SDK is supposed to be pointed at by the VULKAN_SDK environment variable.

The project will be updated regularly, so it makes sense to download the source files once in a while, or clone the whole project. Make sure to keep your main.cpp or other files that you created.

# Using VPE

The main class is called VPEWorld. This class manages bodies, which themselves must be polytopes, i.e., convex mesh like objects, consisting of faces, edges and vertexes. There can be arbitrary numbers of VPEWOrld instances at any time. You can create bodies, erase bodies, attach forces to bodies by calling the respective member functions addBody(), eraseBody(), attachForce().

When created, you can specify a plethora of parameters, like polytope type, mass, velocity, rotation, friction etc. See the constructor of the class Body for more details.
You can also specify two callbacks. One is called when the body moves, so the render engine can update its position and orientation. The other is called if the body is erased by calling eraseBody() or clear(). This way, its pendent in the render engine can be automatically removed as well. This pendent is called the owner of the body, and pointer to it is stored as void pointer with the body. The pointer VPEWorld::m_body always points the latest body creates, or a body that was picked with the debug panel option "pick body".

The simulation is advanced by dt seconds calling tick(dt). See how the debug panel works for more options.

# The Debug Panel

Main.cpp contains code that uses Nuklear to create a debug panel. This panel lets to monitor and change many values of the simulation. This is done simply by changing the respective member variables of the VPEWorld instance.

In debug mode, the simulation pauses and can be stepped through manually. This can be mixed with debugging and setting breakpoints, and outputting values.

# Screenshots

![](screenshot1.png "")
Random objects falling from above.

![](screenshot2.png "Pyramid.")
Pyramid.

![](screenshot3.png "")
Destroying the pyramid.

![](screenshot4.png "")
Arbitrarily high stack.


## Links
-	https://github.com/hlavacs/ViennaVulkanEngine
