# Animate Chart Axis Transitions in D3 v4
[Video](https://egghead.io/lessons/d3-animate-chart-axis-transitions-in-d3-v4)

```js
const data = [
  { name: 'Alice', math: 37, science: 62, language: 54 },
  { name: 'Billy', math: null, science: 34, language: 85 },
  { name: 'Cindy', math: 86, science: 48, language: null },
  { name: 'David', math: 144, science: null, language: 65 },
  { name: 'Emily', math: 59, science: 55, language: 29 },
]

const margin = { top: 10; right: 20, bottom: 30, left: 30 }
const width = 400 - margin.left - margin.right
const height = 535 - margin.top - margin.bottom

const g = d3.select('.chart')
  .append('svg')
    .attr('width', width + margin.left + margin.right)
    .attr('height', height + margin.top + margin.bottom)
  .append('g')
    .attr('transform', `translate(${margin.left}, ${margin.top})`)

const xScale = d3.scaleBand()
  .domain(data.map(d => d.name))
  .range([0, width])
  .padding(0.2)

g.append(g)
  .attr('transform', `translate(0, ${height})`)
  .call(d3.axisBottom(xScale))

const yScale = d3.linearScale()
    .domain([0, 100])
    .range([height, 0])

const yAxis = g.append(g) // get a reference to the y axis
  .call(d3.axisLeft(yAxis))

function render(subject) {
  const t = d3.transition().duration(1000)

  const update = g.selectAll('rect')
    .data(data.filter(d => d[subject]), d => d.name)

  update.exit()
    .transition(t)
    .attr('y', height)
    .attr('height', 0)
    .remove()

  // rescale y domain, animate scaleBand
  yScale.domain([0, d3.max(data, d => d[subject])])
  yAxis
    .transition(t)
    .delay(1000)
    .call(d3.axisLeft(yAxis))

  update
    .transition(t)
    .delay(1000)
    .attr('y', d => yScale(d[subject]))
    .attr('height', d => height - yScale(d[subject]))

  update.enter()
    .append('rect')
    .attr('y', height)
    .attr('height', 0)
    .attr('x', d => xScale(d.name))
    .attr('width', xScale.bandwidth)
    .transition(t)
    .delay(update.exit().size() ? 2000 : 0)
    .attr('y', d => yScale(d[subject]))
    .attr('height', d => height - yScale(d[subject]))
}

render('math')
```

```HTML
<style>
  .chart {
    background: lightgray;
    border: 1px solid black;
  }

  rect {
    fill: steelblue;
  }
</style>

<div class='chart'></div>
```
