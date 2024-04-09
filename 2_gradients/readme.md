# Gradient grid experiments

### Links:

[Codepen](https://codepen.io/minollisantiago/pen/KKYRqqw)

**Inspired by these two pens:**
[Hyperplexed pen](https://codepen.io/Hyperplexed/pen/zYWvXMM)
[jhey pen](https://codepen.io/jh3y/pen/GRLQjXE)

### Hyperplexed video:
[![Video](https://img.youtube.com/vi/bAwEj_mSzOs/maxresdefault.jpg)](https://www.youtube.com/watch?v=bAwEj_mSzOs&list=PL4UMjyVQYX-GeRcIIT5gui7c3LmydEYZS&index=14)

### Source: 

The starting code is based on [jhey's](https://twitter.com/jh3yy) background gradient:
```css
body {
  margin: 0;
  height: 100vh;
  background-color: #1e2326;
  display: grid;
  justify-items: center;
  align-items: center;
}

body::before {
  --size: 60px;
  --line: hsl(216 3% 75% / 0.15);
  content: '';
  height: 100vh;
  width: 100vw;
  position: fixed;
  background: linear-gradient(90deg,
      var(--line) 1px,
      transparent 1px var(--size)) 50% 50% / var(--size) var(--size),
    linear-gradient(var(--line) 1px, transparent 1px var(--size)) 50% 50% / var(--size) var(--size);
  mask: linear-gradient(-15deg, transparent 30%, white);
  top: 0;
  transform-style: flat;
  pointer-events: none;
  z-index: -1;
}
```

### GPTs transcript

This CSS code snippet creates a visually intriguing background pattern using CSS gradients and applies it to a pseudo-element (`::before`) of the `body` tag. Let's break down each part of this code to understand its function:

### Pseudo-Element and Size
- `body::before`: Targets a pseudo-element that is the first child of the `body`. This is used to create content before any other content inside the body.
- `--size: 60px;`: A CSS custom property (variable) defining the size of the grid cells in the pattern.
- `--line: hsl(216 3% 75% / 0.15);`: Another custom property specifying the color and transparency of the grid lines. It uses HSLA color format (Hue, Saturation, Lightness, and Alpha/opacity).
- `content: '';`: Required for the `::before` pseudo-element to be generated, even though it's empty.
- `height: 100vh; width: 100vw;`: Makes the pseudo-element cover the entire viewport with 100% viewport height and width.
- `position: fixed;`: Fixes the position of the pseudo-element relative to the viewport, so it doesn't move with scrolling.
- `top: 0;`: Aligns the pseudo-element at the top of the viewport.

### Background
The `background` property is a bit complex as it layers two linear gradients to create a grid pattern, and uses the custom properties for dimensions and color:

- `linear-gradient(90deg, var(--line) 1px, transparent 1px var(--size)) 50% 50% / var(--size) var(--size),`: This creates vertical grid lines. `90deg` sets the direction of the gradient; `var(--line) 1px` creates a line 1px thick with the color defined in `--line`, followed by transparency until the end of `--size`. The background position and size (`50% 50% / var(--size) var(--size)`) center the pattern and scale it based on `--size`.
- `linear-gradient(var(--line) 1px, transparent 1px var(--size)) 50% 50% / var(--size) var(--size);`: Similar to the first, but for horizontal lines, creating a grid. By default, linear gradients go from top to bottom, so there's no need to specify a degree for horizontal lines.

### Mask
- `mask: linear-gradient(-15deg, transparent 30%, white);`: Applies a masking effect where the gradient starts transparent and becomes opaque. This creates an interesting fade effect on the grid pattern, with the gradient angle at -15 degrees creating a diagonal transition.

### Miscellaneous
- `transform-style: flat;`: Specifies that children of the pseudo-element (though there are none in this case) do not exist in a 3D space.
- `pointer-events: none;`: Ensures that the pseudo-element does not interfere with mouse events, allowing clicks to pass through to elements below.
- `z-index: -1;`: Places the pseudo-element underneath the content of the body.

In summary, this CSS snippet creates a subtle, fixed-position, grid-patterned background for a webpage, with a diagonal fade effect from one corner to the other, enhancing the page's aesthetic without interfering with its usability.
