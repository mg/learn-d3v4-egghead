# Create DOM Elements with D3 v4
[Video](https://egghead.io/lessons/d3-create-dom-elements-with-d3-v4)

- ``append(markup, ?selector)``: Operates on a **selection** and returns a new **selection**. Appends new markup after the last element in the current selection, or after the element selected by the optional **selector**.

- ``insert(markup, ?selector)``: Same as **append**, except it inserts before the first element in the selection. Optional **selector** works the same by anchoring where the operation occurs.

- ``remove()``: Removes the elements from the DOM.

```js
d3.select('div.title')
  .append('button') // append after Concat anchor
    .html('Inventory <b>SALE</b>')

d3.select('div.title')
  .insert('button', 'a:first-child') // insert before About anchor
    .html('Inventory <b>SALE</b>')

d3.select('a.action')
  .remove() // removes a.action from DOM
```

```HTML
<div class="title">
  <a href='#'>About</a>
  <a href='#'>Products</a>
  <a href='#'>Concat</a>
</div>
<a class="action" href='#'>Buy Now</a>
```
