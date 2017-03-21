# Build an Area Chart with D3 v4
[Video](https://egghead.io/lessons/d3-build-an-area-chart-with-d3-v4)

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

const parseTime = d3.timeParse('%Y/%m/%d') // parse the date string

// fix data, parse date and number
data.forEach(company => {
  company.values.forEach(d => {
    d.date = parseTime(d.date)
    d.close = +d.close
  })
})

const xScale = d3.scaleTime()
  .domain([
    d3.min(data, co => d3.min(co.values, d = d.date)), // get min date, two levels down
    d3.max(data, co => d3.max(co.values, d = d.date)), // get max date, two levels down
  ])
  .range([0, width])

g.append(g)
  .attr('transform', `translate(0, ${height})`)
  .call(d3.axisBottom(xScale))

const yScale = d3.linearScale()
    .domain([
      d3.min(data, co => d3.min(co.values, d = d.close)), // get min close, two levels down
      d3.max(data, co => d3.max(co.values, d = d.close)), // get max close, two levels down      
    ])
    .range([height, 0])
    .nice()

g.append(g)
  .call(d3.axisLeft(yScale))

// area generator
const area = d3.area()
  .x(d => xScale(d.date))
  .y0(yScale(yScale.domain()[0])) // draw area from min value of yScale
  .y1(d => yScale(d.close)) // draw area to close value

g.selectAll('.area')
  .data(data)
  .enter()
    .append('path')
    .attr('class', 'area')
    .attr('d', d => area(d.values))
    .style('stroke', (d, i) => ['#ff9900', '#3369e8'][i])
    .style('stroke-width', 2)
    .style('fill', (d, i) => ['#ff9900', '#3369e8'][i])
    .style('fill-opacity', 0.5)
```

##### Data
```json
[
  {
    "ticker": "AMZN",
    "values": [
      {
        "date": "2016/09/30",
        "close": 837.31
      },
      {
        "date": "2016/09/29",
        "close": 829.05
      },
      {
        "date": "2016/09/28",
        "close": 828.72
      },
      {
        "date": "2016/09/27",
        "close": 816.11
      }
    ]
  },
  {
    "ticker": "GOOG",
    "values": [
      {
        "date": "2016/09/30",
        "close": 777.29
      },
      {
        "date": "2016/09/29",
        "close": 775.01
      },
      {
        "date": "2016/09/28",
        "close": 781.56
      },
      {
        "date": "2016/09/27",
        "close": 783.01
      }
    ]
  }
]
```

```HTML
<div class='chart'>
</div>
```
