# Reuse Transitions in D3 v4
[Video](https://egghead.io/lessons/d3-reuse-transitions-in-d3-v4)

Transitions run the moment they are defined (e.g. the next RAF) so it must be used when it is defined. Another option is to use the ``call()`` method to create the transition.

```js
function go() {
  // cannot be defined outside of go(), since then it would have already run before go() is called
  const t = d3.transition()
    .delay(1000)
    .duration(1000)

  d3.selectAll('.block')
    .transition(t)
    .style('width', '400px')

  d3.selectAll('.a')
    .transition(t)
    .style('background-color', 'orange')

  d3.selectAll('.b')
    .transition(t)
    .style('background-color', 'blue')
}

// second method to achieve delayed transition
function configure(t, delay, duration) {
  return t.delay(delay).duration(duration)
}

function goNow() {
  d3.selectAll('.block')
    .transition()
    .call(configure, 1000, 1000)
    .style('height', '300px')    
}
```

```HTML
<style>
  .block {
    background: lightgray;
    border: 1px solid black;
    width: 50px;
    height: 50px;
  }
</style>

<div class='block a'></div>
<div class='block b'></div>

<button onclick="go()">Go</button>
<button onclick="go2()">Go 2</button>
```
