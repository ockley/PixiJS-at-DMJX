# Up and running with PixiJS

In order to get anything going with PixiJS, you have to set up an environment to work in, familiarize yourself with the basic template in HTML and hook the page up with the PixiJS library. That will be a great target for this first chapter and hopefully we will end up with something on the screen.

## Setting up the viewport

Every time you are to use PixiJS on a web page you set up a so called [PIXI Application](http://pixijs.download/release/docs/PIXI.Application.html). This application will provide you with the basic functionality to start drawing an animation. The code that sets it all up can be as simple as this:

```javascript
const app = new PIXI.Application();
```

This sets up a constant called _app_. A constant is simply said, a variable that can't be changed.  The constant now refer to an object that contains several sub elements.

* A **renderer** that draws elements in the HTML canvas \(via _app.view_\)
* A **ticker** that enables animation and timedependent operations
* A **root container** that you can add images and graphic elements into.

To get anything up on the screen you need to add the renderers view to the HTML document. Having a completely blank HTML template, only referencing the PIXI library, it is a matter of using the HTML [_appendChild_](https://www.w3schools.com/jsref/met_node_appendchild.asp) function and pass in the view object like this:

```javascript
const app = new PIXI.Application();
document.body.appendChild(app.view);
```

## Adding a few parameters

Creating a PIXI Application right off the bat without any optional parameters creates a black canvas element that is 800 pixels wide and 600 pixels high. While that is great for initial testing, you might need to change both colors and size, so let's take a look at the options available.

If you look at the documentation for PIXI Application at [http://pixijs.download/release/docs/PIXI.Application.html](http://pixijs.download/release/docs/PIXI.Application.html) you see a list of parameters that you can include in the construction of the app object. We will focus on the basic parameters here and show how they are passed into the object during creation. As you can see there following properties are available as parameters:

* **width **defines the with of the render view
* **height **defines the height os the render view
* **transparent **sets the view to transparent with a true and false
* **backgroundColor** sets the background color of the view in hex format, like 0xFFFFFF for white
* antialias smoothes the edges but is not supported in all browsers

Before showing how to set the parameters, you may have to familiarize yourself with how you pass in an object. Se the box below for an explanation.

> ##### How to pass parameters as objects
>
> A normal used way to give a range of arguments to a function is to pass them as an object. That you don't have to do it in a specific order and can more freely chose how many arguments to pass in. an argument is given as a _key _\(property name\) and a value separated by a colon. If you want to set the _width \_to 300 pixels, you can do it by entering _`width:200`_. If you both want to set \_width \_and \_height_, the values are to be separated by a come, like `width:200, height:300`. The last thing you need to do is to pack all of the key/value pairs in a set of _curly braces_ in order to package it as an object, like this `{width:200, height:200}`. This is the string you finally place inside the functions parenthesis.

With that said, you can make a 600px wide and 400px high, white and antialiased canvas by entering.

```javascript
const app = new PIXI.Application({width:600, height:400, backgroundColor:0xFFFFFF, antialias:true});
document.body.appendChild(app.view);
```

If you run this you can't see anything, because it is a white canvas on a white background. Luckily, you can reach the canvas element from inside of PIXI and change it via CSS. Try, adding a thin grey border round the canvas by entering this line below

```javascript
app.renderer.view.style.border = "1px solid #eeeeee";
```

## Throw something up on the screen

Before we move on, it might be somewhat satisfying to see something up on the screen ... just something. This could also be a good entry to the next section, where we go through the drawing functions in PIXI.

Enter the following code in the end and open the document in the browser.

```javascript
let circle = new PIXI.Graphics(); // Make a Graphics object called circle
circle.beginFill(0xFF0000);       // Set the fill color to white
circle.drawCircle(100, 100, 40);  // Draw a circle at 100, 100 with a radius of 40px
circle.endFill();                 // Close the fill
app.stage.addChild(circle);       // Add the circle object as a child on the stage of the app
```

In the browser, you should see a red circle in the upper left corner. The code is actually quite self explanatory, but I have made some comments to the right.

In the next section, you will investigate this further, but I encourage you to take a moment and fiddle around with the parameters entered in [beginFill\(\)](http://pixijs.download/release/docs/PIXI.Graphics.html#beginFill) and [drawCircle\(\)](http://pixijs.download/release/docs/PIXI.Graphics.html#drawCircle). Change the size and color of the circle. If that is easy, you could see if you could:

1. Make another circle, so there is two of them on stage.
2. Look in the documentation under [drawCircle\(\)](http://pixijs.download/release/docs/PIXI.Graphics.html#drawCircle) and see if you can make it an ellipsis with different width and height.
3. Look at [beginFill\(\)](http://pixijs.download/release/docs/PIXI.Graphics.html#beginFill) and see if you can make it semi-transparent

If that is a bit to much, no worries. This is partly what the next section is about.



