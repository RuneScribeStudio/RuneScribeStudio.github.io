---
layout: default
title: APIs
parent: retroPy
---



## API References

### rpy

`quitRun()`
- quit the retroPy game
{: .fs-3 }
{: .lh-0 }

`pauseRun()`
- pause the retroPy game
{: .fs-3 }
{: .lh-0 }

`resumeRun()`
- resume the retroPy game
{: .fs-3 }
{: .lh-0 }

`pauseTimer()`
- pause dt
{: .fs-3 }
{: .lh-0 }

`resumeTimer()`
- resume dt
{: .fs-3 }
{: .lh-0 }

`clear(color)`
- clear the screen black
{: .fs-3 }
{: .lh-0 }
- color: use specific color to clear screen with
{: .fs-3 }
{: .lh-0 }

`draw()`
- draw the actor in the draw
{: .fs-3 }
{: .lh-0 }

`color_p(color)`

`color_palette(val)`

`color_reset()`

### Rect Setup

`Rect(x,  y,  width,  length)`
- A built in class.
{: .fs-3 }
{: .lh-0 }

### Graphics (Primitives)
`pixel(x, y, color)`
- set the pixel at x, y with color
{: .fs-3 }
{: .lh-0 }

`line(x1, y1, x2, y2, color)`
- draw a line starting at x1, y1 and ending at x2, y2
{: .fs-3 }
{: .lh-0 }

`hline(x, y, length, color)`
- draw a horizontal line at x, y with length and color
{: .fs-3 }
{: .lh-0 }

`vline(x, y, height, color)`
- draw a verticle line at x, y with length and color
{: .fs-3 }
{: .lh-0 }

`circle(x, y, radius, color)`
- draw a circle center x, y with radius and color
{: .fs-3 }
{: .lh-0 }

`filled_circle(x, y, radius, color)`
- draw a filled circle center x, y with radius and color
{: .fs-3 }
{: .lh-0 }

`rect(Rect, color)`
- draw a rectangle at Rect with color
{: .fs-3 }
{: .lh-0 }

`filled_rect(Rect, color)`
- draw a filled rectangle at Rect with color
{: .fs-3 }
{: .lh-0 }

`text(string, x, y, color)`
- write a string at x, y with color
{: .fs-3 }
{: .lh-0 }


### Game Object

`gameObj(ptr2spriteTable, x, y, flipDuration, speed_x, speed_y, mode)`
- create an game object with spriteTable at x, y with flipDuration and speed_x and speed_y
{: .fs-3 }
{: .lh-0 }
- speed is in pixel per second (float)
{: .fs-3 }
{: .lh-0 }

#### Game Object Members

`speed(speed_x, speed_y)`
- gameObj speed x direction and y direction
{: .fs-3 }
{: .lh-0 }

`speed_x(speed)`
- get gameObj speed in the x direction
{: .fs-3 }
{: .lh-0 }

`speed_x`
- get gameObj speed x direction
{: .fs-3 }
{: .lh-0 }

`speed_y(speed)`
- set gameObj speed in the y direction
{: .fs-3 }
{: .lh-0 }
 
`speed_y`

- get gameObj speed y direction
{: .fs-3 }
{: .lh-0 }

`pos(pos_x, pos_y)`
- set gameObj position
{: .fs-3 }
{: .lh-0 }

`pos_x(position)`
- set gameObj x position
{: .fs-3 }
{: .lh-0 }

`pos_x`
- get gameObj x position
{: .fs-3 }
{: .lh-0 }

`pos_y(position)`
- set gameObj y position
{: .fs-3 }
{: .lh-0 }

`pos_y`
- get gameObj y position
{: .fs-3 }
{: .lh-0 }

`mid_x`
- get gameObj x mid position
{: .fs-3 }
{: .lh-0 }

`mid_y`
- get gameObj y mid position
{: .fs-3 }
{: .lh-0 }

`bot_x`
- get gameObj x bot right position
{: .fs-3 }
{: .lh-0 }

`bot_y`
- get gameObj y bot right position
{: .fs-3 }
{: .lh-0 }

`pos_cx`
- get camera x position
{: .fs-3 }
{: .lh-0 }

`pos_cy`
- get camera y position
{: .fs-3 }
{: .lh-0 }

`bot_cx`

`bot_cy`

### Colliders

`drawCollider(color)`
- draw a rectangle to represent the collider
{: .fs-3 }
{: .lh-0 }

`collider(gameObj)`
- check if gameObj collides with another
{: .fs-3 }
{: .lh-0 }

`colliderEx(gameObj)`
- similar to collider with extra info
{: .fs-3 }
{: .lh-0 }

`colliderPt(x, y)`
- check if a point is inside the gameObj collider
{: .fs-3 }
{: .lh-0 }

`resizeCollider(x, y, w, h)`
- resize the gameObj collider
{: .fs-3 }
{: .lh-0 }

`collider_xy(gameObj, x, y)`
- check if gameObj collides with another position x, y
{: .fs-3 }
{: .lh-0 }

### Sprite

`sprite()`
- change the spriteTable
{: .fs-3 }
{: .lh-0 }

`currNdx(ndx)`
- get the current sprite index
{: .fs-3 }
{: .lh-0 }

`flip(val)`
- val (0: default, 1: 90 degrees, 2: 180 degrees, 3: 270 degrees)
{: .fs-3 }
{: .lh-0 }

`mode(val)`

`flipDuration(msec)`

### Calculations

`dist(gameObj)`
- get distance between 2 actors
{: .fs-3 }
{: .lh-0 }

`moveTowards(x, y, speed, dt)`
- make gameObj move towads a specific point
{: .fs-3 }
{: .lh-0 }

`id(val)`
`type(val)`
`val(val)`
- give id to gameObj
{: .fs-3 }
{: .lh-0 }

## retroPy Color Palette

retroPy uses a 16 color palette system.
_(retroPy uses the same color palette system as Pico-8)._

![img-description](/assets/images/color_pallet.png)

Color values:

> 0x0000, 0x194A, 0x792A, 0x042A, 0xAA86, 0x5AA9, 0xC618, 0xFF9D,

> 0xF809, 0xFD00, 0xFF64, 0x0726, 0x2D7F, 0x83B3, 0xFBB5, 0xFE75