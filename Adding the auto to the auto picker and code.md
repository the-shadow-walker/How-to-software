This section will also rely on the fact that you have set up and configured your document and the save location
So, you've created your auto and built it, but you still cant run it! In this section I will show you how you can make it so that your auto appears in your auto picker in network tables.

### In the code
1. First you will need to open the actual robot code. In WPIlib/InteliJ it is just going to the top and clicking file > open folder > navigate to the spot where you have the code > src > open
2. Go to main > java > com > ck4911 > autos > then open ChoreoAutoCommandHandler.java
3. When in there, scroll down to the addAutos() method, it should look something like this:
   ```java
   private void addAutos() {
autoChooser.addRoutine("AUTISM", this::testAuto);
autoChooser.addRoutine("Red_fifty_left", this::fiftyRedLeft);
autoChooser.addRoutine("Red_fifty_right", this::fiftyRedRight);
SmartDashboard.putData("Autos", autoChooser);
} 
   ```
4. On the next available line inside of that method, add something like this (change according to the name of your auto of course):
   ```java
   autoChooser.addRoutine("GrantAutos", this::GrantAutos);
   ```

5. Then if you scroll down a bit further, you will see more methods:
   ```java
   private AutoRoutine fiftyRedLeft() {
AutoRoutine routine = autoFactory.newRoutine("Red_fifty_left");
AutoTrajectory traj = routine.trajectory("Red_fifty_left");
routine.active().onTrue(Commands.sequence(traj.resetOdometry(), traj.cmd()));
return routine;
}

private AutoRoutine fiftyRedRight() {
AutoRoutine routine = autoFactory.newRoutine("Red_fifty_right");
AutoTrajectory traj = routine.trajectory("Red_fifty_right");
routine.active().onTrue(Commands.sequence(traj.resetOdometry(), traj.cmd()));
return routine;

}
   ```
6. Add your own like this:
   ```java
   private AutoRoutine GrantAutos() {
AutoRoutine routine = autoFactory.newRoutine("GrantAutos");
AutoTrajectory traj = routine.trajectory("GrantAutos");
routine.active().onTrue(Commands.sequence(traj.resetOdometry(), traj.cmd()));
return routine;
}
   ```
   
Let's break down the code so you understand what you just added, this will be for someone who is new to java or coding in general. 

First, the line you put in `addAutos()`:

```java
autoChooser.addRoutine("GrantAutos", this::GrantAutos);
```

This registers your auto with the chooser (the dropdown that shows up in NetworkTables). `"GrantAutos"` is the label you'll see and pick in the auto picker. `this::GrantAutos` hands over your `GrantAutos` method so the chooser can call it *only if* someone selects that option. Note the two names don't have to match each other, but the part after `this::` **must** exactly match your method's name below, or it won't compile.

Now the method itself:

```java
private AutoRoutine GrantAutos() {
```
Declares a method called `GrantAutos`. `private` means only this class can use it. `AutoRoutine` is the type of thing it gives back when it finishes. The empty `()` means it needs no information passed in.

```java
    AutoRoutine routine = autoFactory.newRoutine("GrantAutos");
```
Creates a new routine and stores it in a variable named `routine`. It asks `autoFactory` (a helper that builds routines) to make a fresh one. `"GrantAutos"` is a name/label for it.

```java
    AutoTrajectory traj = routine.trajectory("GrantAutos");
```
Gets a trajectory (your pre-planned driving path) and stores it in `traj`. It looks up the path named `"GrantAutos"` — the one you drew in Choreo. This name **must** match your Choreo path file exactly, or the auto will fail when you select it.

```java
    routine.active().onTrue(Commands.sequence(traj.resetOdometry(), traj.cmd()));
```
This says when and what to do. Reading it inside-out: `routine.active()` is true while this routine is running; `.onTrue(...)` means "when that's true, run this"; `Commands.sequence(...)` runs commands one after another; `traj.resetOdometry()` tells the robot its starting position is the path's start; `traj.cmd()` actually drives the path. In plain English: *when this starts, reset the robot's position, then drive the path.*

```java
    return routine;
```
Hands the finished routine back so the chooser can use it.

```java
  }
```
Marks the end of the method.
