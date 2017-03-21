# Create Chart Axes with D3 v4
[Video](https://egghead.io/lessons/d3-create-chart-axes-with-d3-v4)

```js
const margin = { top: 10; right: 0, bottom: 30, left: 40 }
const width = 425 - margin.left - margin.right
const height = 625 - margin.top - margin.bottom

const g = d3.select('.chart')
  .append('svg')
    .attr('width', width + margin.left + margin.right)
    .attr('height', height + margin.top + margin.bottom)
  .append('g')
    .attr('transform', `translate(${margin.left}, ${margin.top})`)

g.append('rect')
  .attr('width', width)
  .attr('height', height)
  .attr('fill', 'lightblue')
  .attr('stroke', 'green')

const yScale = d3.linearScale()
  .domain([0, 100]) // d3 uses these values to create the ticks
  .range([height, 0]) // y cords run from bottom to top

const yAxis = d3.axisLeft(yScale) // create the axis
  .ticks(5) // suggest 5 ticks (optional)
  // .ticks(5, '%') + domain([0, 1]) -> creates a percentage axis from 0% to 100%
  // .ticks(5, '.2s') -> render with 2 decimal values
  // .ticks(5, 's') -> for huge domain values (e.g from 0 to million). Render ticks with M suffix etc.
  // .tickValues([8, 19, .43. 77]) -> render axis with these exact ticks

g.call(yAxis) // add the axis to the chart

const xScale = d3.scaleTime()
  .domain([new Date(2016, 0, 1), new Date(2016, 1, 1)])
  .range([0, width])

const xAxis = d3.axisBottom(xScale)
  .ticks(5)
  //.ticks(d3.timeMinute.every(45)) -> tick every 45 minute
  //.ticksSize(20) -> larger ticks
  //.ticksSizeInner(10) -> size of inner ticks
  //.ticksSizeOuter(30) -> size of outer (boundaries) ticks
  //.ticksPadding(15) -> space between tick and text

g.append(g) // add a new container for the x axis so we can move it to bottom
  .attr('transform', `translate(0, ${height})`) // move it bottom
  .call(xAxis)
```

```HTML
<div class='chart'>
</div>
```
