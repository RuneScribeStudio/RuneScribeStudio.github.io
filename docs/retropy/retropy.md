---
layout: default
title: retroPy
nav_order: 3
has_children: true
permalink: /docs/retropy
---

## Introduction

retroPy is a game console for retro gaming using the Raspberry Pi Pico and programmed in Python.
Most concepts of the retroPy mimic small game engines such as PyGame Zero, Pyxel and Pico-8.
The main idea of retroPy is to be able to create retro games using a “modern” programming language (e.g. Python).
One of retroPy's great qualities is that it runs on a small gaming console, making it super mobile.
retroPy is definitely a fun way to learn Python and a simple way to get into game programming.

![img-description](/assets/images/console1.png)
![img-description](/assets/images/console2.png)

## Installation

If you have one of the following consoles, there is nothing to install.
However, you will need to install Thonny to code in Python.

## Update

> RetroPy is fresh out of the oven and currently just got of beta. Do keep a look out for updates.
{: .prompt-info }

## Example

Below is an example of using retroPy as a graphic tool.

{% capture code %}
{% highlight ruby linenos %}
from retroPy import rpy

rpy.clear()
rpy.filled_circle(120, 120, 100, 8)
rpy.text("hello!", 95, 115, 7)

rpy.show()
{% endhighlight %}
{% endcapture %}
{% include fix_linenos.html code=code %}
{% assign code = nil %}
Next is an example of using retroPy as a simple game engine.


{% capture code %}
{% highlight ruby linenos %}
from retroPy import rpy, Rect

def update(dt):
    pass

def draw():
    rpy.clear()
    rpy.filled_circle(120, 120, 100, 8)
    rpy.text("hello!", 95, 115, 7)

def on_key_down(key):
    pass
def on_key_up(key):
    pass

rpy.run(update, draw, on_key_down, on_key_up)
{% endhighlight %}
{% endcapture %}
{% include fix_linenos.html code=code %}
{% assign code = nil %}

## Getting Started
### Minimal Code

{% capture code %}
{% highlight ruby linenos %}
from retroPy import rpy

def update(dt):
    pass

def draw():
    pass

def on_key_down(key):
    pass
def on_key_up(key):
    pass

rpy.run(update, draw, on_key_down, on_key_up)
{% endhighlight %}
{% endcapture %}
{% include fix_linenos.html code=code %}
{% assign code = nil %}

### Drawing primitives
{% capture code %}
{% highlight ruby linenos %}
from retroPy import rpy, Rect

def update(dt):
pass

def draw():
    rpy.clear(1)
    rpy.filled_rect(Rect(0, 0, 24, 24), 5)
    rpy.filled_circle(50, 50, 12, 8)
    rpy.text("Hello World", 75, 100, 7)
    pass

def on_key_down(key):
    pass
def on_key_up(key):
    pass

rpy.run(update, draw, on_key_down, on_key_up)
{% endhighlight %}
{% endcapture %}
{% include fix_linenos.html code=code %}
{% assign code = nil %}

### Sprite
Using a sprite
{% capture code %}
{% highlight ruby linenos %}
from retroPy import rpy, Rect, actor, LoadSpriteStr
from Assets import boy

player = actor(LoadSpriteStr(boy.boy_idle), 20, 20, 0, 0, 0)
player.flipDuration(300)
player.speed_x = 80
player.bound_x(0,224)

def update(dt):
    player.update(dt)

def draw():
    rpy.clear()
    player.draw()
def on_key_down(key):
    pass

def on_key_up(key):
    pass

rpy.run(update, draw, on_key_down, on_key_up)
{% endhighlight %}
{% endcapture %}
{% include fix_linenos.html code=code %}
{% assign code = nil %}