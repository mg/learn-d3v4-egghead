# Better Code Organization with selection.call() with D3 v4
[Video](https://egghead.io/lessons/d3-better-code-organization-with-selection-call-with-d3-v4)

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

const scaleBar = (selection, scale) => selection.style('transform', `scaleX(${scale})`)  
const fade = (selection, opacity) => selection..style('fill-opacity', opacity)
const setFill = (selection, color) => selection.style('fill', color)

bar.append('rect')
  .style('width', d => d.score)
  .attr('class', 'bar')

  .on('mouseover', function(d, i, elements) {
    d3.select(this)
      .call(scaleBar, 1.5)
      .call(setFill, 'orange') // call returns the selection and is chain-able

    d3.selectAll(elements)
      .filter(':not(:hover)') // returns a NEW selection
      .call(fade, 0.5)
  })
  .on('mouseout', function(d, i, elements) {
    d3.select(this).call(scaleBar, 1)
    d3.selectAll(elements)
      .call(fade, 1)
      .call(setFill, 'lightgreen')
  })

bar.append('text')
  .attr('y', 20)
  .text(d => d.name)
```

```HTML
<div class='chart'>
</div>
```
