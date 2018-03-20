# SASS Triangle Maker

Triangles are so pain. At least before it was. Sass Triangle makes it so easy.

## Usage

First include the sass-triangle

```
@import "sass-toolset/sass-triangle";
```

Then use the mixin

```
// Basic usage: equal triangle
// @include triangle(direction, size, color);

// Two size usage: width and height can be different
// @include triangle(direction, width height, color);

// Free usage: custom triangle
// @include triangle(direction, width/height left/top right/bottom, color);
```

If direction is "custom top" or "custom bottom", sizes paramteres will be sort by "height left right", if it is "custom left" or "custom right" then alignment will be "width top bottom"

There is more. You can have internet explorer 6 support (optional)

```
@include triangle(top, 50px, red, ie6);

// or

@include triangle(top, 50px, red, true);
```

### Parameter Options

| Parameter | Value Types                                                                                                                                            |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Direction | "top", "bottom", "left", "right", "top left", "top right", "bottom left", "bottom right", "custom top", "custom bottom", "custom left", "custom right" |
| Size      | Number with or without units (50, 50px, 50em, 50rem)                                                                                                   |
| Color     | All color types (rgb, rgba, hex, hsl, hsla, color names)                                                                                               |
| IE 6      | boolean or "ie6"                                                                                                                                       |

## Bonus Utilities

| class                         | purpose                                      |
| ----------------------------- | -------------------------------------------- |
| \_firefox-gray-border-problem | If firefox renders a strange gray border     |
| \_webkit-better-antialiasing  | For a better anti-aliasing in webkit browser |
