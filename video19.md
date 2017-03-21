# Build a Scatter Plot with D3 v4
[Video](https://egghead.io/lessons/d3-build-a-scatter-plot-with-d3-v4)

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

const data = ...

const yScale = d3.linearScale()
    .domain(d3.extent(data, d => d.expectancy))
    .range([height, 0])
    .nice() // make axis end on round numbers

const yAxis = d3.axisLeft(yScale)
g.call(yAxis)


const xScale = d3.scaleLinear()
  .domain(d3.extent(data, d => d.cost))
  .range([0, width])
  .nice()

const xAxis = d3.axisBottom(xScale)

g.append(g)
  .attr('transform', `translate(0, ${height})`)
  .call(xAxis)

// scale for circle radius
const rScale = d3.scaleSqrt() // scales better with bigger numbers
  .domain([0, d3.max(data, d => d.population)])
  .range([0, 40])

const circles = svg.selectAll('g.ball')
  .data(data)
  .enter()
    .append('g')
    .attr('class', 'ball')
    .attr('transform', d => `translate(${xScale(d.cost)}), ${xScale(d.expectancy)}`) // move graphics element to correct x, y position

  circles.append('circle')
    .attr('cx', 0)
    .attr('cy', 0)
    .attr('r', d => rScale(d.population))
    .style('fill-opacity', 0.5)
    .style('fill', 'steelblue')

  circles.append('text')
    .style('text-anchor', 'middle')
    .style('fill', 'black')
    .attr('y', 4)
    .text(d => d.code)
```

##### Data
```json
[
  {
    "country": "United States",
    "population": 3230500000,
    "expectancy": 78.94,
    "cost": 9024.21,
    "code": "US"
  },
  {
    "country": "Switzerland",
    "population": 8306200,
    "expectancy": 82.85,
    "cost": 6786.47,
    "code": "CH"
  },
  {
    "country": "Norway",
    "population": 5213985,
    "expectancy": 81.75,
    "cost": 6081,
    "code": "NO"
  },
]
```

```HTML
<div class='chart'>
</div>
```
