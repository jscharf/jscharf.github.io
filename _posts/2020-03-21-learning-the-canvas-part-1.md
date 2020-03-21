---
  layout: post
  title: "Learning the Canvas: Part 1"
  tags:
    - javascript
    - canvas
  categories:
---

First we start by creating the canvas element, with an ID, width and height
attributes, and a border so it's easier to see.

{% highlight html %}
<div>
  <canvas id="canvas" width="200" height="200" style="border: 1px solid black">
  </canvas>
</div>
{% endhighlight %}

Then we add the JavaScript code to draw a simple shape onto the canvas. We'll
choose (0,0) as the starting point and stretch it out half the width and half
the height of the canvas.

{% highlight html %}
<script>
  var canvas = document.getElementById("canvas");
  var context = canvas.getContext("2d");
  context.fillStyle = "rgb(0, 0, 125)";
  context.fillRect(0, 0, 100, 100);
</script>
{% endhighlight %}

The result is a square that occupies one quarter of the total area of the
canvas.

<div>
  <canvas id="canvas" width="200" height="200" style="border: 1px solid black">
  </canvas>
</div>

<script>
  var canvas = document.getElementById("canvas");
  var context = canvas.getContext("2d");
  context.fillStyle = "rgb(0, 0, 125)";
  context.fillRect(0, 0, 100, 100);
</script>

<br/>

Next we can extend the same idea by drawing more shapes onto the canvas to form
a pattern.

{% highlight html %}
<script>
  var canvas = document.getElementById("canvas");
  var context = canvas.getContext("2d");
  context.fillStyle = "rgb(0, 0, 125)";
  context.fillRect(0, 0, 100, 100);
  context.fillStyle = "rgb(125, 0, 0)";
  context.fillRect(0, 100, 100, 200);
  context.fillStyle = "rgb(125, 0, 0)";
  context.fillRect(100, 0, 200, 100);
  context.fillStyle = "rgb(0, 0, 125)";
  context.fillRect(100, 100, 200, 200);
</script>
{% endhighlight %}

<div>
  <canvas id="canvas-2" width="200" height="200" style="border: 1px solid black">
  </canvas>
</div>

<script>
  var canvas = document.getElementById("canvas-2");
  var context = canvas.getContext("2d");
  context.fillStyle = "rgb(0, 0, 125)";
  context.fillRect(0, 0, 100, 100);
  context.fillStyle = "rgb(125, 0, 0)";
  context.fillRect(0, 100, 100, 200);
  context.fillStyle = "rgb(125, 0, 0)";
  context.fillRect(100, 0, 200, 100);
  context.fillStyle = "rgb(0, 0, 125)";
  context.fillRect(100, 100, 200, 200);
</script>

<br/>

Now this is great, but it's a lot of repetition. It would be great if we could
leverage a bit of JavaScript's dynamic nature to make this easier.

{% highlight html %}
<script>
  var canvas = document.getElementById("canvas-3");
  var context = canvas.getContext("2d");
  for (var index = 0; index < 8; index += 1) {
    if (index % 2 == 0) {
      context.fillStyle = "rgb(255, 255, 255)";
    } else {
      context.fillStyle = "rgb(0, 0, 0)";
    }
    context.fillRect(0+100*index, 0, 100+100*index, 100);
  }
</script>
{% endhighlight %}

<div>
  <canvas id="canvas-3" width="800" height="100" style="border: 1px solid black">
  </canvas>
</div>

<script>
  var canvas = document.getElementById("canvas-3");
  var context = canvas.getContext("2d");
  for (var index = 0; index < 8; index += 1) {
    if (index % 2 == 0) {
      context.fillStyle = "rgb(255, 255, 255)";
    } else {
      context.fillStyle = "rgb(0, 0, 0)";
    }
    context.fillRect(0+100*index, 0, 100+100*index, 100);
  }
</script>

<br/>

You can see how powerful this is and how it's starting to resemble a game board
that might look familiar.
