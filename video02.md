# Convert Input Data to Output Values with Linear Scales in D3 v4
[Video](https://egghead.io/lessons/d3-convert-input-data-to-output-values-with-linear-scales-in-d3-v4)

Mapping domain data values (such as test score) to screen values for representation (pixel coordinates, color values, etc.).

- ``d3.scaleLinear()``: Takes a continuous input domain and maps it to a continuous output range and maps it to a continuous output range.
- ``invert(n)``: Map value **n** from output range to domain range.

```js
const linearScale = d3.scaleLinear()
  .domain([0, 100]) // possible domain values (test scores)
  .range([0, 1]) // possible output range
  .clamp(true) // any value outside domain values will be mapped inside range values

console.log(linearScale(0), linearScale(50), linearScale(100), , linearScale(110)) // -> 0, 0.5, 1, 1
console.log(linearScale.invert(0), linearScale.invert(0.5), linearScale.invert(1), , linearScale.invert(1,1)) // -> 0, 50, 100, 100
```
