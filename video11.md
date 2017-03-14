# Output SVG Elements with D3 v4
[Video](https://egghead.io/lessons/d3-output-svg-elements-with-d3-v4)

```js
const scores = [
  { name: 'Alice', score 96 },
  { name: 'Billy', score 83 },
  { name: 'Cindy', score 91 },
  { name: 'David', score 96 },
  { name: 'Emily', score 88 },
]

d3.select('.chart')
  .append('svg') // create svg container
    .attr('height', 255) // set the dimentions of our container
    .attr('width', 300)
  .selectAll('rect') // select all rect svg elements
  .data(scores)
  .enter()
    .append('rect') // add new rect elements
    .attr('y', (d, i) => i * 33) // position each rect, using index to set the y attribute
    .style('width', d => d.score)
    .text(d => d.name)
    .attr('class', 'bar')
```

```HTML
<div class='chart'>
</div>
```
