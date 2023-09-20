---
title: Flip Sprite
layout: default
parent: Tutorials
grand_parent: retroPy
---

## Introduction

In this tutorial, we will cover on how to change the orientation of our sprites using *Flip*.

| We can flip images horizontally, vertically or both |
| - |
| 0 – no flip |
| 1 – flip horizontally |
| 2 – flip vertically |
| 3 – flip both horizontally and vertically |


Example 
{% capture code %}
{% highlight python linenos %}
from retroPy import rpy, actor, LoadSpriteStr
from Assets import heart

p_heart = LoadSpriteStr(heart.heart)

heart1 = actor(p_heart, 120, 120, 100, 0, 0) # flip = 0
heart2 = actor(p_heart, 140, 120, 100, 0, 0) 
heart2.flip(1) #flip horizontally

heart3 = actor(p_heart, 120, 140, 100, 0, 0) 
heart3.flip(2) #flip vertically
heart4 = actor(p_heart, 140, 140, 100, 0, 0) 
heart4.flip(3) #flip vertically

heart1.draw()
heart2.draw()
heart3.draw()
heart4.draw()

rpy.show()
{% endhighlight %}
{% endcapture %}
{% include fix_linenos.html code=code %}
{% assign code = nil %}

![img-description](/assets/images/flip-hearts-2.png)
_Image of the heart in different orientations using flip_

In the next example we are using a sing sprite of boy moving in the right direction. When we need boy to walk in the left direction, we will flip the image horizontally.

`player.flip(1)`

Using the flip allows us to change the direction of the sprite without the need for extra sprites, thus allowing us to save more memory.

{% capture code %}
{% highlight python linenos %}
from retroPy import rpy, Rect, actor, LoadSpriteStr
import Assets.boy

player = actor(LoadSpriteStr(Assets.boy.boy_walk_r), 120, 120, 300, 80, 0, 0, 224, 0, 224)
player.speed_x = 80

def update(dt):
    if player.pos_x > 170:
        player.speed_x = -80  
        player.flip(1)    
    if player.pos_x < 70:
        player.speed_x = 80  
        player.flip(0)    
    
    player.update(dt)

def draw():
    rpy.clear()
    player.draw()

#=========================================================================
rpy.run(update, draw)  
{% endhighlight %}
{% endcapture %}
{% include fix_linenos.html code=code %}
{% assign code = nil %}

Our player should now face the direction he is walking towards without needing to create more sprites. 

| ![img-description](/assets/images/boy_walk_r.png) | ![img-description](/assets/images/boy_walk_l.png) |