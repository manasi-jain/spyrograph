---
title: "Scaling trochoid's and cycloid's input parameters with the spyrograph `scale` method"
date: 2023-04-01 01:18:00 -0500
categories: Python, tutorial
header:
  overlay_image: /images/rgb.gif
---

## Scaling trochoid's and cycloid's input parameters with the spyrograph `scale` method

In this blog post, we will explore the `scale` method in the `spyrograph` package which enables users to easily scale their trochoids and cycloids

## Creating a `Hypocycloid`
First, let's create a `Hypocycloid` with 10 cusps to work with:

{% highlight python %}
import numpy as np
from spyrograph import Hypocycloid

hypocycloid = Hypocycloid.n_cusps(
    R=300,
    n=10,
    thetas=np.arange(0, 2*np.pi, .1)
)
{% endhighlight %}

<p align="center">
  <img src="{{ site.url }}{{ site.baseurl }}/images/cusps_shape_for_scale.gif" alt="A circular shape with 20 cusps is drawn by a circle rolling around the interior of another fixed circle">
</p>

## Scaling the `Hypocycloid` with the `scale` method
Now that we have a `Hypocycloid`, we can easily scale it using the `scale` method:

{% highlight python %}
scaled_hypocycloid = hypocycloid.scale(factor=.5)
{% endhighlight %}

<p align="center">
  <img src="{{ site.url }}{{ site.baseurl }}/images/web_shape_scale.PNG" alt="A circular shape with 20 cusps is drawn by a circle rolling around the interior of another fixed circle and then an identical shape that is half the size is drawn right in the center">
</p>

The `scaled_hypocycloid` will now have its input parameters (`R`, `r`, and `d`) multiplied by the scaling factor

For example the radius of the big circle `R=300` will now be `R*.5=150`

## Using `scale` to `trace` a beautiful pattern
Let's jump into a concrete example of using the `scale` method in action to `trace` a gradually smaller set of curves

{% highlight python %}
from spyrograph import Hypocycloid
import numpy as np
import time

screen = None
hypocycloid = Hypocycloid.n_cusps(
    R=200,
    n=20,
    theta_start=0,
    theta_stop=2*3.1415,
    theta_step=.01
)
for i in range(1,40):
    screen = hypocycloid.trace(screen=screen)
    hypocycloid = hypocycloid.scale(factor=((40/(i+40))))
    time.sleep(.1)
turtle.exitonclick()
{% endhighlight %}

<p align="center">
  <img src="{{ site.url }}{{ site.baseurl }}/images/scale_web.gif" alt="A circular shape with 20 cusps is drawn and then a slightly smaller one is drawn within that and then this continues down until a shape that resembles a spiderweb is drawn">
</p>

## Conclusion
The `scale` method in spyrograph provides a convenient way to resize trochoids and cycloids while preserving their shape

With just a single method call and a scaling factor, users can quickly create new shapes with different sizes, making the package even more versatile for artists, educators, and developers alike

Don't forget to experiment with different scaling factors and shapes to create stunning patterns and visuals!