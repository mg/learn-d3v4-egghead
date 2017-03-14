# Select DOM Elements with D3 v4
[Video](https://egghead.io/lessons/d3-select-dom-elements-with-d3-v4)

**Selections** are, along with **scales**, one of the fundamental concepts in D3.

- ``select(expr)``: select the first element that matches the expression
- ``selectAll(expr)``: select all the elements that match the expression

```js
  const div = d3.select('div')
  console.log(div) // -> output a internal D3 structure that tracks the selection
  console.log(div.nodes()) // -> output the HTML nodes captured by the select

  const links = div.selectAll('a')
  // or
  const links = d3.selectAll('div a')
  const actionLink = d3.select('a.action')

  const allLinks = d3.selectAll(document.links)
  console.log(allLinks.size()) // -> 4
```

```HTML
<div class="title">
  <a href='#'>About</a>
  <a href='#'>Products</a>
  <a href='#'>Concat</a>
</div>
<a class="action" href='#'>Buy Now</a>
```
