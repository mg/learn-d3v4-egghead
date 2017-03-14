# Load and Inspect Data with D3 v4
[Video](https://egghead.io/lessons/d3-load-and-inspect-data-with-d3-v4)

```js
d3.json('data/data.json'), data => {
  d3.min(data, d => d.age) // -> 13
  d3.max(data, d => d.age) // -> 38
  const extent = d3.extent(data, d => d.age) // -> [13, 38]

  // mapping age to a scale
  const scale = d3.linearScale()
    .domain(extend)
    range([0, 600])

  const ages = d3.set(data, d => d.age) // a set of all unique values -> {$23: '23', $38: '38', $13: '13', $37: '37'}
  console.log(ages.values()) // -> ['23', '38', '13', 37']
})

d3.csv('data/data.csv'), data => {
})

d3.tsv('data/data.tsv'), data => {
})

```

###### Data set
```json
[
  { "age": 21, "name": "Welch" },
  { "age": 38, "name": "Villarreal" },
  { "age": 13, "name": "Sheryl" },
  { "age": 37, "name": "Marshall" },
  { "age": 37, "name": "Aimee" },
]
```
