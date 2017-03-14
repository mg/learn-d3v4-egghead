# Create Labels from Non-numeric Data with Ordinal Scales in D3 v4
[Video](https://egghead.io/lessons/d3-create-labels-from-non-numeric-data-with-ordinal-scales-in-d3-v4)

Mapping discrete set of input values to a discrete set of output values.

```js
const ordinalScale = d3.scaleOrdinal()
  .domain(['poor', 'good', 'great'])
  .range(['red', 'white', 'green'])

console.log(ordinalScale('good'), ordinalScale('great'), ordinalScale('poor')) // -> white, green, red
```
