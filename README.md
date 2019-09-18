# What's this

A demo of how to include sprites in a single SVG and extract pieces.

1. Draw SVGs, add wrappers with id="the-id" in the relevant elements (`G`, `SYMBOL`, plain `PATH`s etc.)

2. Create a SVG with a `USE` tag like this:

```html
<svg>
    <use xlink:href="/drawing.svg#the-id"></use>
</svg>
```

3. Profit.

To automate the process of creating those SVG elements a bit, a lil bit of JavaScript is used:

```js
  // Creates the SVG similar to the piece above within s.element.
  const s = new SvgFragment('drawing.svg', 'the-id');

  // Append!
  document.body.appendChild(s.element);

  // Convenience: move the top/left property of the element.
  s.move(10, 10);
```

## Optimizing the SVG

```sh
$ yarn global add svgo
$ svgo --disable=cleanupIDs drawing.svg
```