compass-inline-sprites
======================

Just a simple wrapper to make your sprites map a base64 string within your CSS instead of a reference to local files. Feel free to spread around the the various steps within screen.scss if you use a SMACSS-style file structure. Make sure you notice the selector grouping happening in the rendered screen.css. See comments in screen.scss for guidance. Note that this uses the awesome "inline-sprite" feature in the most recent Compass.

So instead of the usual spriting like this:

````
.mysprites-sprite, .random-selector, .another-random-selector {
  background: url('/images/mysprites-s8860754bda.png') no-repeat;
}
````

We now have this:

````
.base64-sprites, .random-selector, .another-random-selector {
  background-image: url('data:image/png;base64,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');
  background-repeat: no-repeat;
}
````