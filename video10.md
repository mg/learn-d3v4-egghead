# Start Visualizing Data Driven Documents with D3 v4
[Video](https://egghead.io/lessons/d3-start-visualizing-data-driven-documents-with-d3-v4)

#### The data join
- **Enter**: We have data but our element selection is empty.

- **Update**: We have both data and a matching element selection.

- **Exit**: We have a element selection, but no data.

- ``data(data, mergeFn)``: Merge data to markup, using the **mergeFn** to control how we merge. Returns the **update** selection.

- ``enter()``: Select the **enter** selection from the **update** selection.

- ``exit()``: Select the **exit** selection from the **update** selection.

- ``merge()``: Merge **enter** and **update** selections for common transformations.

```js
const scores = [
  { name: 'Alice', score 96 },
  { name: 'Billy', score 83 },
  { name: 'Cindy', score 91 },
  { name: 'David', score 96 },
  { name: 'Emily', score 88 },
]

const update = d3.select('.chart')
  .selectAll('div') // empty element selection
  .data(scores, function(d) {
    return d ? d.name : this.innerText
  }) // creates a join between the data and the div's
  .style('color', 'blue') // styling the elements in the update selection

const enter = update.enter() // enter the enter selection
  .append('div')
    .text(d => d.name)
    .style('color', 'green')

update.exit()
  .remove() // removes Walter

// work with both update and enter selections
update.merge(enter)
  .style('width', d => `${d.score}px`)
  .style('height', '50px')
  .style('background', 'lightgreen')
  .style('border', '1px solid black')
```

```HTML
<div class='chart'>
  <div>Billy</div>
  <div>Cindy</div>
  <div>Walter</div>
</div>
```
