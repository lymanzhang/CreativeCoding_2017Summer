## Recursion

The programming equivalent of feedback is recursion.

Great fleas have little fleas upon their backs to bite 'em,
And little fleas have lesser fleas, and so ad infinitum.
In code, one way of achieving feedback is by creating recursive functions. A recursive function is just a function that calls itself. For example, this simple function returns the sum of all the numbers up to the number passed as the argument:
```java
int sum(int x) {
    if (x <= 1) 
        return x;
    else
        return x + sum(x - 1);
}
```
So sum(0) returns 0, sum(5) returns 15 (5+4+3+2+1). It’s important to note the test condition that stops sum() getting into infinite recursion: if (x <= 1) return x;.

Recursion is a neat conceptual programming trick, but its actually rarely the most efficient way to write code. For example, we could easily re-write the code above without it:
```java
int sum(int x) {
    int result = x;
    while(--x > 0) {
        result += x;
    }
    return result;
}
```
Here we’ve used an iterative technique, that will compute the answer faster and using less memory because it has less overhead for function calls. For small numbers this difference won’t be noticeable, but try sum(100000) and you’ll see what I mean.

The Processing documentation also contains a graphic example of recursion, which produces the image shown at the top of this page.
```java
void setup() {
  size(640, 360);
  noStroke();
  noLoop();
}

void draw() {
  drawCircle(width/2, 280, 6);
}

void drawCircle(int x, int radius, int level) {                    
  float tt = 126 * level/4.0;
  fill(tt);
  ellipse(x, height/2, radius*2, radius*2);      
  if(level > 1) {
    level = level - 1;
    drawCircle(x - radius/2, radius/2, level);
    drawCircle(x + radius/2, radius/2, level);
  }
}
```
The recursive function is drawCircle() that draws a circle and then draws two circles half the size inside. Each circle is progressively darker, due to the level variable being decremented are each recursive call.

Once level reaches 1 the function stops calling itself and returns.

The w6_01 sketch contains a modified version of the recursive circle drawing function that also uses animation. Open and run the sketch to see this version in action.
