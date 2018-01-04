# Up and running with PixiJS

In order to get anything going with PixiJS, you have to set up an environment to work in, familiarize yourself with the basic template in HTML and hook the page up with the PixiJS library. That will be a great target for this first chapter and hopefully we will end up with something on the screen.

## Draw something on the screen

```js
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Circle on screen</title>
  <script src = "https://cdnjs.cloudflare.com/ajax/libs/pixi.js/4.5.1/pixi.min.js"></script>
</head>
<body>
  <script>
    var app = new PIXI.Application();
    document.body.appendChild(app.view);

    var circle = new PIXI.Graphics();
    circle.beginFill(0xFF0000);
    circle.drawCircle(100, 100, 40);
    circle.endFill();
    app.stage.addChild(circle);
  </script>

</body>
</html>
```



