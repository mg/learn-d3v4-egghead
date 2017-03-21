# Margin Convention with D3 v4
[Video](https://egghead.io/lessons/d3-margin-convention-with-d3-v4)

Common D3 pattern

```js
// the margin convention
const margin = { top: 0; right: 0, bottom: 25, left: 25 }
const width = 425 - margin.left - margin.right
const height = 625 - margin.top - margin.bottom

const g = d3.select('.chart')
  .append('svg')
    .attr('width', width + margin.left + margin.right) // add margins back to dimensions
    .attr('height', height + margin.top + margin.bottom)
  .append('g')
    .attr('transform', `translate(${margin.left}, ${margin.top})`) // displace any child elements according to left and top margin

// we can now ignore margins for child dimensions
g.append('rect')
  .attr('width', width / 2)
  .attr('height', height)
  .attr('fill', 'lightblue')
  .attr('stroke', 'green')

g.append('rect')
  .attr('x', width / 2)
  .attr('width', width / 2)
  .attr('height', height)
  .attr('fill', 'lightblue')
  .attr('stroke', 'green')
```

```HTML
<div class='chart'>
</div>
```
