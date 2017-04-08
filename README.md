# map.sass

Functions for Sass map.

## Install

```
yarn add map.sass
```

## Usage Example

### Defining a color palettes

By using a map-access function like following `my-color-palettes.scss`.

```scss
@import '~map.sass/map-access.scss';
$color-palettes: (
  error: (
    fg: white,
    bg: red,
  ),
  anchor: (
    base: (
      normal: blue,
      hover: yellow,
    ),
  ),
);
@function my-palette($keys...) {
  @return map-access($palettes, $keys...);
}
```

`map-get(map-get(map-get(...)...)...)` is no longer necessary.

```scss
@import './my-color-palettes';
.warning-message {
  color: my-palette(error, fg);
  background-color: my-palette(error, bg);

  // you can also access to any nested map
  a { color: my-palette(anchor, base, normal); }
  a:hover { color: my-palette(anchor, base, hover); }
}
```
