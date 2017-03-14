# Modify DOM Elements with D3 v4
[Video](https://egghead.io/lessons/d3-modify-dom-elements-with-d3-v4)

```js
const secondLink = d3.selectAll('a:nth-child(2)')
secondLink.attr('href', 'http://google.com') // set href
console.log(secondLink.attr('href')) // get href

// idomatic D3
d3.selectAll('a:nth-child(2)')
  .attr('href', 'http://google.com')
  .style('color', 'red')
  .classed('red', true)
  .text('Inventory')
  .html('<strong>SALE</strong>')
```

```HTML
<div class="title">
  <a href='#'>About</a>
  <a href='#'>Products</a>
  <a href='#'>Concat</a>
</div>
<a class="action" href='#'>Buy Now</a>
```
