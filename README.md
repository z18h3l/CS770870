java c
CS770/870 Assignment 7 
•  Due: Tuesday, November 5th.
Overview 
In this assignment, you will write a ray caster. This is a ray tracer that uses only primary rays (no reflected, refracted or shadow rays). You should be able to render spheres, triangles, and cylinders.
Pseudocode 
The ray caster implements this pseudocode:for each pixel in image {set_a_ray(s=pixel, v = (pixel - eye))pixel = ray_color (ray, scene)}ray_color (ray, scene) {hit = first_hit (ray, scene)return hit.color or background_color}first_hit (ray, scene) {list = (empty)for each shape in scene {if (ray intersects shape at location) {hit = new hitpoint(location, shape)list.append(hit)}}return list.get_minimum()}
The Scene 
Your picture should render a scene that contains several spheres, several triangles, and a cylinder.The starting code defines a scene with three spheres, two triangles, and a cylinder. It gives the camera an initial position, which you can change. The left image shows the initial view and resolution, and the right image shows a higher resolution view a什er moving the camera:
C++ Classes 
You will need the following classes to represent aspects of the problem:•  Shape : a geometric shape in the scene. The most elegant way to proceed is to make this an abstract class, with
subclasses Triangle, Sphere, and Cylinder. This class defines an abstract intersect( ray ) method, which sets a Hit object if the ray intersects the shape.
• Triangle : (a subclass of Shape) a polygon which contains:
– three vertices
– surface normal
– color
•  Sphere : (a subclass of Shape) a sphere which contains:
– center location
– radius
– color
•  Cylinder : (a subclass of Shape) a cylinder aligned with they axis which contains:
– center location
– radius
– height
•  Hit : describes the intersection of a ray and a shape, and contains the following data members:
– location of intersection
– color of shape that was hit
– surface normal at the intersection point (not used in this assignment)
Controls 
The following keyboard controls are implemented in the Caster_Controller class (which you don’t have to change):
•  UP  /  DOWN  arrow: move eye up/down, keeping look-at point fixed
•  LEFT   /   RIGHT  arrow : move eye le什/right, keeping look-at point fixed
• Shift+UP  /  Shift+DOWN  arrow: move eye forward/backward.
•  R  /  Shift+R : decrease/increase the resolution
•  C : output the current camera position.
Tasks 
1.  Implement the Triangle ::intersects() method. This returns true/false if the ray does/doesn’代 写CS770/870 Assignment 7C/C++
代做程序编程语言thit the triangle. If it does, also call hit .set () to store information about the hit point.
2.  Implement the Sphere ::intersects() method. This returns true/false if the ray does/doesn’thit the sphere. If it does, also call hit .set () to store information about the hit point.
3.  Implement the Cylinder ::intersects() method. This returns true/false if the ray does/doesn’thit the cylinder. If it does, also call hit .set () to store information about the hit point.
4.  Implement the following methods in the Caster class:•  set_ray () : initialize the start point and direction vector for a ray originating at the given DCS pixel position.
•  update_camera () : update information that depends on the camera’s eye, look-at, and up parameters.
• get_ﬁrst_hit () : find the closest shape intersected by the given ray. If it hits nothing, return false. If it hits something, set the hit variable accordingly and return true. The function init_scene () fills a vector
of Shape pointers, which you should use to identify the closest shape.
•  ray_color () : return the color of the ray originating at the given DCS pixel position.
Speed 
If your program runs very slowly, reduce the resolution (press R). If you want more detail, increase it (press Shift-R). Also, in your local .mak file, define
CXX = g++  -std=c++11 -O3 
to optimize the compiled code for speed. Define
CXX = g++ -std=c++11 -g 
to make the code work with a debugger (it will run more slowly).
Debugging 
If you insert cout   << everywhere, you’ll drown in output. If you set a breakpoint in your IDE or debugger, you’ll probably stop at the bottom-le什 pixel first, which isn’t very interesting or useful.Instead, click the mouse on a pixel, and trace the progress of the ray_color () function on that one particular pixel. In the Caster_Controller::mouse_button_callback () function, there is code that turns up the Log :: LEVEL to 1, and calls ray_color () once. In your code, insert debugging output as follows:if (Log::LEVEL > 0) {Log::os() << " some debugging information ";...}
This debugging output will be triggered by the mouse click. By default, Log ::os () is cout. If you want to send output to a diferent stream, call Log ::set_output ().
Turning in your Work 
When you are done, go to mycourses.unh .edu, find the course, Assignments, and find the assignment. Then upload these files:
•  caster .cpp
• triangle.cpp
• sphere.cpp
•  cylinder.cpp
If you modified any other files, upload them too.







         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
