---
  layout: post
  title: "Learning the Canvas: Part 2"
  tags:
    - javascript
    - canvas
  categories:
---

This is part of an ongoing series of posts about learning how to use the HTML canvas element. If you haven't already seen part 1, I recommend you check out [Learning the Canvas: Part 1]({{ page.previous.url }}).

Last time we only used one function to draw rectangles: `fillRect()`. But in fact, there are two other functions that can be used to draw rectanges as well: `strokeRect()` and `clearRect()`. All three methods take the same parameters: `x`, `y`, `width`, and `height`. For the x and y position, remember that the "starting" coordinates are the top-left corner of the rectangle.

Combining these three functions to form a single drawing can produce some pretty interesting results.

<div>
  <canvas id="canvas" width="200" height="200" style="border: 1px solid black">
  </canvas>
</div>

<script>
  var canvas = document.getElementById("canvas");
  var context = canvas.getContext("2d");
  context.fillRect(0, 0, 200, 200);
  context.clearRect(50, 50, 100, 100);
  context.strokeRect(60, 60, 80, 80);
  context.strokeRect(70, 70, 60, 60);
  context.strokeRect(80, 80, 40, 40);
  context.strokeRect(90, 90, 20, 20);
  context.fillRect(95, 95, 10, 10);
</script>

<br/>

When you look at the above image, what do you see?

Some see a bird's eye view of a tall pryamid, while others see a first-person view down long hallway.

The code for this example is a combination of the three methods mentioned above. 

{% highlight html %}
<div>
  <canvas id="canvas" width="200" height="200" style="border: 1px solid black">
  </canvas>
</div>
{% endhighlight %}

{% highlight html %}
<script>
  var canvas = document.getElementById("canvas");
  var context = canvas.getContext("2d");
  context.fillRect(0, 0, 200, 200);
  context.clearRect(50, 50, 100, 100);
  context.strokeRect(60, 60, 80, 80);
  context.strokeRect(70, 70, 60, 60);
  context.strokeRect(80, 80, 40, 40);
  context.strokeRect(90, 90, 20, 20);
  context.fillRect(95, 95, 10, 10);
</script>
{% endhighlight %}

<br/>

You can see how these functions give us more flexibility on what we can draw, and how we can draw it.

<div>
  <canvas id="canvas-2" width="600" height="200" style="border: 1px solid black">
  </canvas>
</div>

<script>
  var canvas = document.getElementById("canvas-2");
  var context = canvas.getContext("2d");
  context.fillRect(0, 0, 600, 200);
  context.clearRect(10, 10, 580, 180);

  var initialX = 20;
  for (var index = 0; index <= 55; index += 1) {
    context.strokeRect(initialX+index*10, 20, 5, 160);
  }
</script>

<br/>

We can leverage loop structures to draw on bigger canvases without much additional code.

{% highlight html %}
<script>
  var canvas = document.getElementById("canvas-2");
  var context = canvas.getContext("2d");
  context.fillRect(0, 0, 600, 200);
  context.clearRect(10, 10, 580, 180);

  var initialX = 20;
  for (var index = 0; index <= 55; index += 1) {
    context.strokeRect(initialX+index*10, 20, 5, 160);
  }
</script>
{% endhighlight %}

<br/>

Building upon that example, we can imagine all sorts of rectangular-based drawings using a combination of these three functions.

<div>
  <canvas id="canvas-3" width="400" height="400" style="border: 1px solid black">
  </canvas>
</div>

<script>
  var canvas = document.getElementById("canvas-3");
  var context = canvas.getContext("2d");
  context.fillRect(0, 0, 400, 400);

  var initialX = 10;
  var initialY = 10;
  var maxX = 390;
  var maxY = 390;

  context.clearRect(initialX, initialY, maxX-initialX, maxY-initialY);

  for (var y = 0; initialY + 10 * y < maxY; y += 1) {
    context.strokeRect(initialX, initialY*y, maxX-initialX, maxY-initialY);
  }
  for (var x = 0; initialX + 10 * x < maxX; x += 1) {
    context.strokeRect(initialX*x, initialY, maxX-initialX, maxY-initialY);
  }
</script>

<br/>

Even though it appears as a board with many squares, in the code we see it's actually long rectangles rendered on top of each other to achieve the appearance of squares.

{% highlight html %}
<script>
  var canvas = document.getElementById("canvas-3");
  var context = canvas.getContext("2d");
  context.fillRect(0, 0, 400, 400);

  var initialX = 10;
  var initialY = 10;
  var maxX = 390;
  var maxY = 390;

  context.clearRect(initialX, initialY, maxX-initialX, maxY-initialY);

  for (var y = 0; initialY + 10 * y < maxY; y += 1) {
    context.strokeRect(initialX, initialY*y, maxX-initialX, maxY-initialY);
  }
  for (var x = 0; initialX + 10 * x < maxX; x += 1) {
    context.strokeRect(initialX*x, initialY, maxX-initialX, maxY-initialY);
  }
</script>
{% endhighlight %}

This is only the beginning of what you can do with the HTML canvas. In the next post, we'll cover paths, which are an extremely powerful set of tools for drawing almost any shape you can think of.