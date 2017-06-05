## IF and SWITCH

Sometimes when using this statement you’ll find yourself ‘chaining’ if ... else if ... else if ... statements to perform an action based on the value of a particular variable.

For example, we’ve already looked at Processing’s built-in key variable, which contains the value of the last keyboard key that was pressed. You’ll often use different key commands, such as in the first ‘draw your name’ sketch that used the ‘r’ and ‘s’ keys to clear the screen and save, respectively. We could add an additional key command to quit the program (‘q’):

```java
if (keyPressed == true && key == 's') {
    saveFrame("yourName.jpg");
} else if (keyPressed == true && key == 'r') {
    background(255);
} else if (keyPressed == true && key == 'q') {
    exit();
} 
```

This becomes a bit tedious, and the more additional key commands we add the longer the chain of if ... else if ... statements becomes. Fortunately there’s an alternative: switch. This statement is useful when you have situations like the one above. It allows you to take actions based on different values of the same variable. Here’s the code above rewritten using switch:

```java
if (keyPressed == true) {
    switch( key ) {
      case 's':
        saveFrame("yourName.jpg");
        break;
      case 'r':
        background(255);
        break;
      case 'q':
        exit();
        break;
      default:
        println("Unknown key command: ", key);
    } // end switch
}
```

Note the use of the break; statement – this tells the computer to break out of the switch and not try to process any other cases. The default: at the end matches anything, so it’s a good idea to always include it at then end, unless you provide a specific case for every possible value.
