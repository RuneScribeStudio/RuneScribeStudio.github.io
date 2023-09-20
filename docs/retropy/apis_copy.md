---
layout: default
title: APIs Updated
parent: retroPy
---



## API References

### rpy

`quitRun()`

`pauseRun()`

`resumeRun()`

`pauseTimer()`

`resumeTimer()`

`clear(color)`
- clear the screen black
- color: use specific color to clear screen with

`draw()`
- draw the actor in the draw

`color_p(color)`

`color_palette(val)`

`color_reset()`

### Rect Setup

`Rect(x,  y,  width,  length)`
- A built in class.

### Graphics (Primitives)
`pixel(x, y, color)`
- set the pixel at x, y with color

`line(x1, y1, x2, y2, color)`
- draw a line starting at x1, y1 and ending at x2, y2

`hline(x, y, length, color)`
- draw a horizontal line at x, y with length and color

`vline(x, y, height, color)`
- draw a verticle line at x, y with length and color

`circle(x, y, radius, color)`
- draw a circle center x, y with radius and color 

`filled_circle(x, y, radius, color)`
- draw a filled circle center x, y with radius and color 

`rect(Rect, color)`
- draw a rectangle at Rect with color 

`filled_rect(Rect, color)`
- draw a filled rectangle at Rect with color 

`text(string, x, y, color)`
- write a string at x, y with color


### Game Object

`gameObj(ptr2spriteTable, x, y, flipDuration, speed_x, speed_y, mode)`
- create an game object with spriteTable at x, y with flipDuration and speed_x and speed_y
- speed is in pixel per second (float)

#### Game Object Members

[`speed(speed_x, speed_y)`](## "gameObj speed x direction and y direction")

[`speed_x(speed)`](## "get gameObj speed in the x direction")

[`speed_x`](## "get gameObj speed x direction")

[`speed_y(speed)`](## "set gameObj speed in the y direction")
 
[`speed_y`](## "get gameObj speed y direction")

[`pos(pos_x, pos_y)`](## "set gameObj position")

[`pos_x(position)`](## "set gameObj x position")

[`pos_x`](## "get gameObj x position")

[`pos_y(position)`](## "set gameObj y position")

[`pos_y`](## "get gameObj y position")

`mid_x`

`mid_y`

`bot_x`

`bot_y`

`pos_cx`

`pos_cy`

`bot_cx`

`bot_cy`

### Colliders

[`drawCollider(color)`](## "draw a rectangle to represent the collider")

[`collider(gameObj)`](## "check if gameObj collides with another")

[`colliderEx(gameObj)`](## "similar to collider with extra info")

[`colliderPt(x, y)`](## "check if a point is inside the gameObj collider")

[`resizeCollider(x, y, w, h)`](## "resize the gameObj collider")

[`collider_xy(gameObj, x, y)`](## "check if gameObj collides with another position x, y")

### Sprite

`sprite()`
- change the spriteTable

`currNdx(ndx)`
- get the current sprite index

`flip(val)`

`mode(val)`

`flipDuration(msec)`

### Calculations

`dist(gameObj)`
- get distance between 2 actors

`moveTowards(x, y, speed, dt)`

`id(val)`

`type(val)`

`val(val)`

## retroPy Color Palette

retroPy uses a 16 color palette system.
_(retroPy uses the same color palette system as Pico-8)._

![img-description](/assets/images/color_pallet.png)

Color values:

> 0x0000, 0x194A, 0x792A, 0x042A, 0xAA86, 0x5AA9, 0xC618, 0xFF9D,

> 0xF809, 0xFD00, 0xFF64, 0x0726, 0x2D7F, 0x83B3, 0xFBB5, 0xFE75