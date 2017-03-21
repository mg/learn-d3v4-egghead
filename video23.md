# Animate Transitions in D3 v4
[Video](https://egghead.io/lessons/d3-animate-transitions-in-d3-v4)

```js
d3.select('#block')
  .transition() // animate the next attribute changes
    .duration(500) // transition duration in ms
    .delay(750) // delay in ms
    .ease(d3.easeBounceOut) // easeCubicOut, easeElasticOut
    .style('width', '400px')
  .transition() // sequence the transition, e.g. run height after width
    // .duration(500) -> not needed since it inherits from prev transition
     //.ease(d3.easeBounceOut)
    .style('height', '400px')
    .style('background-color', 'red')
```

```HTML
<style>
  #block {
    background: lightgray;
    border: 1px solid black;
    width: 100px;
    height: 100px;
  }
</style>

<div id='block'>
</div>
```
