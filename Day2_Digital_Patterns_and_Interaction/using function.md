## USing Function

Functions are an important programming mechanism to organise your code.

Open and run the w2_04 sketch. This sketch creates a grid of animated ‘clocks’. It builds on the conditional and looping constructs we’ve discussed in the previous examples.

Let’s look at some specific sections of the code:

```java
for (int i=0; i<num; i++) { // column in y
  for (int j=0; j<num; j++) { // row in x
    ++circleNumber;

    float tx = margin + cellsize/2  + (cellsize + gutter) * j;
    float ty = margin + cellsize/2  + (cellsize + gutter) * i;

    movingCircle(tx, ty, cellsize, circleNumber * TWO_PI * millis() / 60000.0);
  }
}
```

The code to draw the grid of shapes inside the nested for loops has been replaced with a function call to movingCircle. The variables tx and ty store the computed position of each circle in the grid. cellsize is the diameter of each circle. The expression circleNumber * TWO_PI * millis() / 60000.0 calculates the number of minutes that have elapsed since the sketch started running (millis() / 60000.0), multiplied by 2π2π and the circleNumber, which is indexed from 1 up to num2num2 (the total number of circles as there are num rows and num columns).

Now let’s look at movingCircle:

```java
void movingCircle(float x, float y, float size, float angle) {
    // calculate endpoint of the line
    float endpointX = x + (size / 2) * cos(angle);
    float endpointY = y + (size / 2) * sin(angle);

    stroke(0);
    strokeWeight(1);
    fill(140, 180);
    ellipse(x, y, size, size); // circle

    stroke(255, 0, 0);
    line(x, y, endpointX, endpointY); // red line
}
```

This function takes the circle position (x and y), diameter (size) and the angle of the clock ‘hand’ (angle), calculates the position of the endpoint of the hand and draws the circle and the red hand.

It is using the cos() and sin() functions to calculate the (x,y) endpoint of each hand.

Using the cos() and sin() functions the hand position is calculated and added to the centre point for each circle.

While we could have put the code in this function directly inside the nested for loops in draw(), using a function has several advantages:

- Functions encapsulate a specific task, often parameterised by the functions arguments, making them more flexible and reusable;
- Functions break more complex tasks down into easier steps. Functions can call other functions (even themselves – known as recursive functions);
- A function’s variables have only local scope (meaning they only exist inside the function), leading to fewer problems with finding unique variable names in more complex sketches.

Duplicate the movingCircle function in the code (call it movingCircle2) and modify this function so that it draws a square clock face, with the hand moving in the opposite direction. Test your function by replacing the function call in draw() from movingCircle to movingCircle2 (the arguments should be the same).

Next, modify the code inside the nested for loops to call movingCircle if circleNumber is odd, movingCircle2 otherwise. 

