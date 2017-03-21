# Basic Interactivity with D3 v4
[Video](https://egghead.io/lessons/d3-basic-interactivity-with-d3-v4)

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
    .append('g')
    .attr('transform', (d, i) => `translate(0,${i * 33})`)

bar.append('rect')
  .style('width', d => d.score)
  .attr('class', 'bar')

  // simulate :hover
  .on('mouseover', function() {
    d3.select(this).classed('barOn', true)
  })
  .on('mouseout', function() {
    d3.select(this).classed('barOn', false)
  })

  // make every item translucent, EXCEPT the element that is hover over, WHEN something is being hovered over
  .on('mouseover', function(d, i, elements) {
    d3.selectAll(elements)
      .filter(':not(:hover)') // returns a NEW selection
      .style('fill-opacity', 0.5)
  })
  .on('mouseout', function(d, i, elements) {
    d3.selectAll(elements)
      .style('fill-opacity', 1)
  })

bar.append('text')
  .attr('y', 20)
  .text(d => d.name)
```

```HTML
<div class='chart'>
</div>
```
