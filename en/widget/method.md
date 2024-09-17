# $widget

$widget provides API to interact with widgets.

# $widget.height

Get or set the height of widget:

```js
// Get
const height = $widget.height;
// Set
$widget.height = 400;
```

# $widget.mode

Get current display mode (show less/show more):

```js
const mode = $widget.mode; // 0: less 1: more
```

# $widget.modeChanged

Observe mode changes:

```js
$widget.modeChanged = mode => {
  
}
```