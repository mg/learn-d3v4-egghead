# Build a Column Chart with D3 v4
[Video](https://egghead.io/lessons/d3-build-a-column-chart-with-d3-v4)

```js
const margin = { top: 10; right: 20, bottom: 30, left: 30 }
const width = 400 - margin.left - margin.right
const height = 565 - margin.top - margin.bottom

const g = d3.select('.chart')
  .append('svg')
    .attr('width', width + margin.left + margin.right)
    .attr('height', height + margin.top + margin.bottom)
  .append('g')
    .attr('transform', `translate(${margin.left}, ${margin.top})`)

const yScale = d3.linearScale()
    .domain([0, 100])
    .range([height, 0])

const yAxis = d3.axisLeft(yScale)
g.call(yAxis)

const data = [
   score: 63, subject: 'Mathematics' },
   score: 82, subject: 'Geography' },
   score: 74, subject: 'Spelling' },
   score: 97, subject: 'Reading' },
   score: 52, subject: 'Science' },
]

const xScale = d3.scaleBand()
  .padding(0.2) // relative padding, 1 is no padding. This is part of the bandScale
  //.paddingInner(0.2) -> padding between bars
  //.paddingOuter(0.5) -> padding before first and after last bars
  //.align() -> 0 = left align, 1 = right align
  .domain(data.map(d => d.subject)) // 1 bar for each subject
  .range([0, width])
const xAxis = d3.axisBottom(xScale)

g.append(g)
  .attr('transform', `translate(0, ${height})`)
  .call(xAxis)
  // create more room for text labels
  .selectAll('text')
    .style('text-anchor', 'end')
    .attr('transform', 'rotate(-45)')

svg.selectAll('rect')
  .data(data)
  .enter()
    .append('rect')
    .attr('x', d => xScale(d.subject)) // band scale controls positioning
    .attr('y', d => yScale(d.score))
    .attr('width', xScale.bandwidth()) // let the band scale determine bar width
    .attr('height', d => height - yScale(d.score)) // invert y coords
    .attr('fill', 'steelblue')
```

```HTML
<div class='chart'>
</div>
```
