# Create Labels from Numeric Data with Quantize Scales in D3 v4
[Video](https://egghead.io/lessons/d3-create-labels-from-numeric-data-with-quantize-scales-in-d3-v4)

Mapping continuous input to a specific discrete set of output values (e.g. labels). The **quantize scale** breaks the domain range into pieces, mapping each piece to a discrete range value.

```js
const quantizeScale = d3.scaleQuantize()
  .domain([0, 100])
  .range(['red', 'white', 'green']) // 0 - 33: red, 33 - 66: white, 67 - 100: green

console.log(quantizeScale(22), quantizeScale(50), quantizeScale(88), quantizeScale(99)) // -> red, white, green, green
console.log(quantizeScale.invertExtent('white')) // --> [33.333..., 66.666...]
```
