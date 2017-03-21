# Debug D3 v4 with Dev Tools
[Video](https://egghead.io/lessons/d3-debug-d3-v4-with-dev-tools)

- ``$0``: The currently selected DOM element in Chrome Inspector
- ``$0.__data__``: The D3 data used to create the element. Read-only.
- ``d3.select($0).attr('myAttr', value)``: Change the data in console
- ``d3.selectAll('circle').filter(d => d.x < 30).nodes()``: Spit out a subset of elements
