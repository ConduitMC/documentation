
# Adding your first custom command

Conduit leverages Minecraft's Brigadier system for command management making it very simple to create commands and parse arguments.


### Creating your command

Create a new class called `MyFirstCommand`, have it extend the `BaseCommand` class. Add the following method override to the class you just created:

```java
@Override
public LiteralArgumentBuilder<CommandSourceStack> getCommand() {
    return Commands.literal("myfirstcommand").executes(ctx -> ctx.getSource().sendSuccess("Hello, world!", false));
}
```

This method override will allow you to properly utilize Minecraft's Brigadier system. Your `MyFirstCommand.java` file should now look like the code below:

```java
public class MyFirstCommand extends BaseCommand {

    @Override
    public LiteralArgumentBuilder<CommandSourceStack> getCommand() {
        return Commands.literal("myfirstcommand").executes(ctx -> ctx.getSource().sendSuccess("Hello, world!", false));
    }
}
```

The command context that is provided in the arguments of `executes` contains all the information about both the command arguments, and the command sender.

### Using the command context

TODO

### Accepting arguments on the command

TODO

### Registering the command

To register the command, call the `registerCommand` method with an instance of the command's class in your plugin's `onEnable` method.

```java
registerCommand(new MyFirstCommand())
```

You can enable any number of commands in this function by adding another command object instance to the method as can be seen below:

```java
registerCommand(new CustomCommand1(), new CustomCommand2(), /* ... */ , new CustomCommandX())
```