Markers are the last part of Choreo we will go over. At some point you may have wondered how the other parts of the robot will be used aside from just driving, and that is a great question. Markers are the answer.

1. Inside of Choreo, find a point where you may want a subsystem to do something. In my auto, I'm going to be using the collector right when I'm outside of the trench, which will be waypoint 2
2. Once you have the waypoint that you want to the robot to activate its subsystem, go to Choreoautocommandhandler.java, and then scroll down to the bindGlobalCommands method and find the autoFactory.bind part and then read the names for 
   ```java
autoFactory.bind("Intake", collector.intakeCommand());
autoFactory.bind("Stow", collector.stowCommand());
autoFactory.bind("Index", indexer.indexcommand());
autoFactory.bind("StopIndex", indexer.stopindexcommand());
autoFactory.bind("StopShooter", shooter.stopShooter());
autoFactory.bind("Down", Commands.runOnce(() ->
 shooter.setAngle(Rotations.of(0.0)), shooter));
autoFactory.bind("Collector_down", collector.intakeCommand());
autoFactory.bind("Collector_stow", collector.stowCommand());
autoFactory.bind("Shoot", Commands.parallel(shooter.shootCommand()));

autoFactory.bind(

"PrepShot",

Commands.parallel(shooter.aimHoodCommand(dynamicDistanceSupplier), indexer.indexcommand()));
   ```
3. You can read that there are names like "Intake", "Stow", etc...  Note that each is case sensitive. If you are curious about what each command does, you can command/windows + click on the command. (in the Intake bind, I'd click the intakeCommand() and it will take you to where you need to see what the method does.)
4. Here I'm going to click on the marker, then click on the waypoint, then set the string to be "Intake" and you can leave the 3rd field set to none
   ![[ScreenRecording2026-06-16at3.49.59PM-ezgif.com-video-to-gif-converter.gif]]
5. Make sure to rebuild it for the marker to take effect, now when the robot drives, that command is ran. Here is a tutorial on how to create your own command and also a quick explainer on what is actually happening inside of the code.
   
   ### Resources:
   [[Choreo Marker Commands]]