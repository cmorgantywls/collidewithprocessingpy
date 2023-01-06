# Collide2D for Processing.py
A very basic version of [Ben Moren's Collide2D](https://github.com/bmoren/p5.collide2D) for Processing.Py created for [CS4All](https://sites.google.com/schools.nyc.gov/cs4allnyc/home) NYC's [ICM version 2.0 in Python](https://bit.ly/cs4allicm2py).

Creation would not have been possible without [Jeffrey Thompson's Collision Detection site](http://www.jeffreythompson.org/collision-detection/table_of_contents.php) which is truly an amazing and valuable resource.

## Table of Contents
* [collidePointPoint](#pointpoint)
* [collidePointCircle](#pointcirc)
* [collideCircleCircle](#circcirc)
* [collidePointRect](#pointrect)
* [collideRectRect](#rectrect)
* [collideCircRect](#circrect)
* [collideLinePoint](#linepoint)
* [collideLineCircle](#linecirc)
* [collideLineLine](#lineline)
* [collideLineRect](#linerect)
* [Dealing With Other Shapes](#other)

### <a name="pointpoint"></a>Point Point
`collidePointPoint(x1, y1, x2, y2)`

Takes in the x,y coordinates of two points as inputs. Returns true if the points are touching.

Example:
```
from processing import *
from collide2d import *

def setup():
    size(400,400)

def draw():
    background(220)
    text(str(mouseX) + ", " + str(mouseY), 20, 20)
    
    point(200, 200)
    if collidePointPoint(200, 200, mouseX, mouseY):
      background(0)

    

draw = draw
run()
```

### <a name="pointcirc"></a>Point Circle
`collidePointCircle(pointX, pointY, circX, circY, diameter)`
*Important: Will not work as planned with elliptical/oval shapes!*

Takes x,y input from a point and the x, y, and diameter of a circle. Returns true if they are touching.

Example:
```
from processing import *
from collide2d import *

def setup():
    size(400,400)

def draw():
    background(220)
    text(str(mouseX) + ", " + str(mouseY), 20, 20)
    
    ellipse(200, 200, 100, 100)
    if collidePointPoint(mouseX, mouseY, 200, 200, 100):
      background(0)

    
draw = draw
run()
```

### <a name="circcirc"></a>Circle Circle
`collideCircleCircle(circ1x, circ1y, circ1d, circ2x, circ2y, circ2d)`

Takes in the x, y, diameter for two circles and returns true if they are touching.

Example:
```
from processing import *
from collide2d import *

def setup():
    size(400,400)

def draw():
    background(220)
    text(str(mouseX) + ", " + str(mouseY), 20, 20)
    
    ellipse(mouseX, mouseY, 10, 10)
    ellipse(200, 200, 100, 100)
    if collideCircleCircle(mouseX, mouseY, 10, 200, 200, 100):
      background(0)

    
draw = draw
run()
```

### <a name="pointrect"></a>Point Rectangle
`collidePointRect(pX, pY, rX, rY, rW, rH)`

Input x,y coordinates of point and x,y,w,h of rectangle. Returns true if the point and rectangle are touching.

Example:
```
from processing import *
from collide2d import *

def setup():
    size(400,400)

def draw():
    background(220)
    text(str(mouseX) + ", " + str(mouseY), 20, 20)
    
    rect(200, 200, 100, 100)
    if collidePointRect(mouseX, mouseY, 200, 200, 100, 100):
      background(0)

    
draw = draw
run()
```

### <a name="rectrect"></a>Rectangle Rectangle
`collideRectRect(r1x, r1y, r1w, r1h, r2x, r2y, r2w, r2h)`

Input the x,y,w,h for rect 1 and x,y,w,h for rect2. Returns true if the rectangles are touching.

Example:
```
from processing import *
from collide2d import *

def setup():
    size(400,400)

def draw():
    background(220)
    text(str(mouseX) + ", " + str(mouseY), 20, 20)
    
    rect(mouseX, mouseY, 10, 10)
    rect(200, 200, 100, 100)
    if collideRectRect(mouseX, mouseY, 10, 10, 200, 200, 100, 100):
      background(0)

    
draw = draw
run()
```

### <a name="circrect"></a>Circle Rectangle
`collideCircRect(cX, cY, cD, rX, rY, rW, rH)`
*Important: Will not work as intended with elliptical/oval shapes!*

Input x,y, diameter of the circle and x, y, width, height of the rectangle. Returns true if the circle and rectangle are touching.

Example:
```
from processing import *
from collide2d import *

def setup():
    size(400,400)

def draw():
    background(220)
    text(str(mouseX) + ", " + str(mouseY), 20, 20)
    
    ellipse(mouseX, mouseY, 10, 10)
    rect(200, 200, 100, 100)
    if collideCircRect(mouseX, mouseY, 10, 200, 200, 100, 100):
      background(0)

    
draw = draw
run()
```

### <a name="linepoint"></a>Line Point
`collideLinePoint(x1, y1, x2, y2, px, py, buffer=0.1)`

Input x1,y1,x2,y2 values for the line and x,y coordinates for the point. There is an optional 7th value called 'buffer' that has a default of 0.1 - if you do not enter a value, it will use 0.1. You can increase this number to make the collision detection less sensistive, with the caveat that it will also be less accurate about touching the line.

Example:
```
from processing import *
from collide2d import *

def setup():
    size(400,400)

def draw():
    background(220)
    text(str(mouseX) + ", " + str(mouseY), 20, 20)
    
    line(100, 200, 150, 200)
    if collideLinePoint(100, 200, 150, 200, mouseX, mouseY, 0.3): #0.3 is the optional buffer value
      background(0)

    
draw = draw
run()
```

### <a name="linecirc"></a> Line Circle
`collideLineCircle(x1, y1, x2, y2, cX, cY, cD)`
*Important: Will not work as intended with elliptical/oval shapes!*

Input the x1,y1,x2,y2 o fthe line and the x,y, diameter of the circle. Returns true if the line and circle are touching.

Example:
```
from processing import *
from collide2d import *

def setup():
    size(400,400)

def draw():
    background(220)
    text(str(mouseX) + ", " + str(mouseY), 20, 20)
    
    line(100, 200, 150, 200)
    ellipse(mouseX, mouseY, 10, 10)
    if collideLineCirc(100, 200, 150, 200, mouseX, mouseY, 10):
      background(0)

    
draw = draw
run()
```

### <a name="lineline"></a>Line Line
`collideLineLine(x1,y1,x2,y2,x3,y3,x4,y4)`

Input x1,y1,x2,y2 of the first line and x3,y3,x4,y4 of the second line. Returns true if lines are touching.

Example:
```
from processing import *
from collide2d import *

def setup():
    size(400,400)

def draw():
    background(220)
    text(str(mouseX) + ", " + str(mouseY), 20, 20)
    
    line(100, 200, 150, 200)
    line(10, 10, mouseX, mouseY)
    if collideLineLine(100, 200, 150, 200, 10, 10, mouseX, mouseY):
      background(0)

    
draw = draw
run()
```

### <a name="linerect"></a>Line Rectangle
`collideLineRect(x1,y1,x2,y2,rX,rY,rW,rH)`

Input x1,y1,x2,y2 of line and x,y,width,height of rect. Returns true if they are touching.

Example:
```
from processing import *
from collide2d import *

def setup():
    size(400,400)

def draw():
    background(220)
    text(str(mouseX) + ", " + str(mouseY), 20, 20)
    
    rect(100, 200, 150, 200)
    line(10, 10, mouseX, mouseY)
    if collideLineRect(10, 10, mouseX, mouseY, 100, 200, 150, 200):
      background(0)

    
draw = draw
run()
```

### <a name="other"></a>Dealing With Other Shapes
For most other shapes, such as triangles and other polygons, consider using functions that deal with circle collision. Imagine your shape inscribed in a circle, and use that circle for your code. It won't be perfect, but it will work!

Additionally, [Jeffrey Thompson's Collision Detection site](http://www.jeffreythompson.org/collision-detection/table_of_contents.php) has examples for collision with polygons and triangles. His examples are written in Java, but they could help you work out a Python function to use in your code!
