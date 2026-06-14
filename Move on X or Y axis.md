In this section we will go over the Pose waypoint, Translation waypoint and the Empty way point. We will go over their uses and their constraintss that can be applied.

### Setting initial position and moving forward
In the top left point on the field section of Choreo, you will see a rectangle with a dot in the middle and a triangle on the outside, click on that.
![[Pasted image 20260613184414.png]]

Now with that clicked, go down to the field and click on the blue alliances start line, the initial robot position will appear.
![[Pasted image 20260613184532.png]]

Now click again a bit further in the blue territory, this will place down a second Pose waypoint.
![[Pasted image 20260613184746.png]]
A few things to note in the diagram above, inside of the red circle there is a option that says "waypoints", currently there are 2 waypoints, any of the three waypoint options in the top (Pose waypoint, Translation waypoint and Empty waypoint), those waypoints will appear under the "WAYPOINTS" menu. The other thing to note is that now that I have more then one way point, a new button in the bottom right corner of the screen has appeared. I have circled it in green. When you click on it, it will build the trajectory, and if you have already built it, will update the one inside of the code, you will have to rebuild and redeploy the code for the changes to take effect.

After clicking it, a "play button" will appear that allows you to see what the built auto will do. This is a good time to watch for all 4 corners of the robot to ensure that clipping wont happen. So, congratulations, you've made your first auto! We could deploy this now and run it and the robot would move, though this auto isn't to helpful yet, so lets  learn some concepts real quick!
### Waypoint ordering:
So, lets take my auto "GrantsAutos" and add a third Pose waypoint, and rebuild it.
![[ScreenRecording2026-06-13at10.00.29PM-ezgif.com-video-to-gif-converter.gif]]

As we can see it goes to 1, then 2 and finally 3, but if i rearrange them, it goes in that order, this is a more exaggerated example here:
![[ScreenRecording2026-06-13at10.08.16PM-ezgif.com-video-to-gif-converter.gif]] 
So, you can rearrange the order in which pose waypoints are to change the order the robot will drive to each, try that out now with a 3 waypoint auto.

### Pose waypoints and Max Angular velocity constraints
Pose waypoints are going to be one of the most used tools in Choreo, and they are very simple to use.
Pose waypoints track both rotation and location. Here is a good exercise to try and learn the concept of it, make sure to delete the 3 waypoints you already placed down.
1. Place the Translation pose down on the starting line
2. Rotate it 180 degrees (if it says rads, just delete the rads part and replace it with "deg")
   ![[Pasted image 20260613222132.png|448]]
3. Next right in front of it, place down another Translation waypoint, don't rotate it this time
4. Finally add another one on the other side of the field, this can be a random rotation, whatever you want.
5. build it and watch the robot spin around (usually not over 180 degrees so it wont be a helicopter.)

**Using Max angular velocity constraint**
The max angular velocity constraints determines how fast the robot can rotate. You will pick 2 or more waypoints where you want this constraint to take place. You will get an error if constraints conflict with a Translation waypoint (ex: you set a max angular velocity between point 1 and 2 to be 0 deg/s but there is a 180 degree difference between 1 and 2, it is impossible to not rotate and have a rotation requirement at the same time!) so it is best practice to have the 2 Pose waypoints to either A) have the same rotation or B) have it be a Pose -> Translation -> Pose and then have an angular constraint between Translation -> pose. Here are the 2 examples and then I'll tell you how to apply a max angular constraint:

**Option one:** Don't rotate it (sometimes can be hard especially when moving quickly)
![[ScreenRecording2026-06-13at10.48.01PM-ezgif.com-video-to-gif-converter.gif]]

**Option 2:** use max angular velocity constraint
![[ScreenRecording2026-06-13at10.52.58PM-ezgif.com-video-to-gif-converter.gif]]
Notice how it is a Pose -> translation (Which has not rotation value) and then Pose again, with my final rotation included. With the Max angular velocity constraint, the robot does not start rotating while still under the trench (the little gap that the robot drove through), which would lead to clipping, and in real life, a collision.

How to apply 
