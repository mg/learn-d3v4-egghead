# Convert Dates to Numeric Values with Time Scales in D3 v4
[Video](https://egghead.io/lessons/d3-convert-dates-to-numeric-values-with-time-scales-in-d3-v4)

What date falls exactly in the middle between now and January 1st?

```js
const timeScale = d3.scaleTime()
  .domain([new Date(2016, 0, 1), new Date()]) // domain date values
  .range([0, 100])

console.log(timeScale(new Date(2016, 4, 15))) // -> 61.198...
console.log(timeScale.invert(50)) // -> Wd Apr 20 2016
```
