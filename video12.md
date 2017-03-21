# SVG Graphics Containers and Text Elements in D3 v4
[Video](https://egghead.io/lessons/d3-svg-graphics-containers-and-text-elements-in-d3-v4)

```js
const scores = [
  { name: 'Alice', score 96 },
  { name: 'Billy', score 83 },
  { name: 'Cindy', score 91 },
  { name: 'David', score 96 },
  { name: 'Emily', score 88 },
]

const bar = d3.select('.chart')
  .append('svg')
    .attr('height', 255)
    .attr('width', 300)
  .selectAll('g')
  .data(scores)
  .enter()
    .append('g') // add graphics containers
    .attr('transform', (d, i) => `translate(0,${i * 33})`) // containers don't have a y property

// add rect to each graphic
bar.append('rect')
  .style('width', d => d.score)
  .attr('class', 'bar')

// add text to each graphic
bar.append('text')
  .attr('y', 20)
  .text(d => d.name)
```

```HTML
<div class='chart'>
</div>
```
