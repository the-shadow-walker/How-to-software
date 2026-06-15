Constraints are critical to making a good auto and are a core part of Choreo (Like waypoints and markers) and you will need a strong understanding of them as without constraints, the robot just flies around.



TODO: make a video for this one (if you are reading this, it means i havent made the video yet)

### Brief overview of each:
* **Stop point:** A point where the robot comes to a complete halt before immediately starting up again. There's no delay - it just momentarily stops.
* **Max velocity:** The maximum speed the robot can move, measured in meters per second (m/s).
* **Max acceleration:** Not to be confused with max velocity. This is how quickly the robot can change its speed, measured in meters per second squared (m/s²).
* **Max angular velocity:** This is the maximum the robot will spin around (measured in rad/s)
* **Point at:** We will skip this for now as you will rarely use it and it is a rather finicky feature.
* **Keep in circle:** This is a constraint that requires all parts of a robot to stay in a circle, if that is not possible (ex: the circle is too far away from a waypoint, the circle is too far, some other random reason) it will throw an error, and you will have to change stuff around till it works.
* **Keep in rectangle:** The same as the circle, but its a rectangle (Hence the name, keep in **rectangle**)
* **Keep in lane:** The Keep in lane constraint creates an actual lane that the robot must stay inside of, so when you create a path an Choreo optimizes and accounts for momentum, it creates lines that may go a bit outside of the actual line, so the keep in lane makes sure that the robot follows the line you made, to a certain tolerance.
* **Keep out circle:** This works as the name implies, it is a circle that the robot must keep out of, again, if the keep out is too close (as in for the robot to go to the point, it also must go into the circle, that can't work.) it will throw an error

### How to apply constraints
Applying the constraints can be a bit confusing at first, but once you understand its very simple too use. After this, we will go into how to use each constraint and also some use cases (the examples won't always be perfect/over simplified where there are better solutions, but it is for learning/education.)

1. Make a simple path, remember the rules: The first waypoint has to be a Pose waypoint, Pose waypoints affect Translation (where it is on the X and Y) and translation only affects the Translation. Have the path be more then 3 waypoints, then build it. this will be mine (note that I used translation waypoints as not to interfere with any explicit rotation):
   ![[Pasted image 20260614214534.png|376]]
2. I will use the Max velocity constraint for this first example (note that Stop point constraint is slightly different from the others, which I will cover in the Stop point section of this document)
3. Click the Max velocity button at the top:
   ![[Pasted image 20260614222938.png|472]]
4. Next click the waypoints you want affected by this constraint. Lets say I want waypoint 2-3 to have a max velocity of 1.8 m/s with the max velocity constraint selected in my tool bar, I'd click waypoint 2, then 3. You should see a dotted yellow line appear between them. If one does not appear, make sure that the tool is selected and highlighted in yellow.
   ![[Screen Recording 2026-06-14 at 10.40.31 PM.gif]]
5. As you can see, the robot slows down while under the max velocity constraint, again, this application will apply for all constraints except for the Stop point constraint

### Stop points
The Stop point constraint will bring the linear velocity to 0. 