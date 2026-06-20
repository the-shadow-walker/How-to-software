Choreo marker commands are the commands that run when they are activated through Choreo markers. Just a heads up, I recommend that you go through the training resources on the basics of java here: [[Java Learning Resources]] before reading this as we talk about classes, objects and methods.

This will also be digging down into the code and showing the structure of how all of these commands work.
### Code break down
What a bind does:
```java
autoFactory.bind("EventName", aCommand);

// Our example:
autoFactory.bind("Intake", collector.intakeCommand());
```
This maps a string to a command. In the case of intake it maps "Intake" to the command:
```java
collector.intakeCommand()
```
Then inside of the Collector class we use a method with the return type command that in turn calls more void methods:
```java
public Command intakeCommand() {
return run(
() -> {
deploy();
intake();
});
}
```
### The Deploy method:
```java
private void deploy() {
setPivotAngle(Rotations.of(deployPosition.get()));
}
```
This method is a private method with the void return type (it means that nothing will be returned when the method is used). This uses the setPivotAngle method and its argument is Rotations.of, which is another method and the argument of that is the method deployPosition.get. Lets break down each of those methods.

**setPivotAngle**
```java
private void setPivotAngle(Angle angle) {
collectorIo.runPivotPosition(angle, Amps.of(0));
}
```
This is another private method with a void return type. Its arguments are actually parameters. We are taking a field and turning it into a variable, and then when the method is used, like in our deploy method, it will then set the angle to be equal to whatever these methods solve for:(Rotations.of(deployPosition.get())
So lets say that we run the method deployPosition.get(), that will use a field and then put it into the method get() and that will return the value of deployPosition, that is now the argument of Rotations.of(), so it looks something like Rotations.of(.8) and Rotations is imported from WPIlib commands to allow for smoother handling of the mesurment of an angle.