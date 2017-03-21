# Make D3 v4 Charts Responsive with the viewBox attribute
[Video](https://egghead.io/lessons/d3-make-d3-v4-charts-responsive-with-the-viewbox-attribute)

The ``viewBox`` attribute of SVG takes advantage of the vector nature of SVG and scales accordingly.

More info: https://sarasoueidan.com/blog/svg-coordinate-systems/

```js
const margin = { top: 10; right: 20, bottom: 30, left: 30 }
const width = 400 - margin.left - margin.right // control inital width & height & set aspect ratio
const height = 600 - margin.top - margin.bottom
//const fullWidth = width + margin.left + margin.right
//const fullHeight = height + margin.top + margin.bottom

const g = d3.select('.chart')
  .append('svg')
    .attr('width', width + margin.left + margin.right) // creating the dimensions of the viewport
    .attr('height', height + margin.top + margin.bottom)
    //.attr('viewBox', `0 0 ${fullWidth} ${fullHeight}`)
    //.attr('viewBox', `0 0 ${fullWidth / 2} ${fullHeight / 2}`) -> zoom in
    //.attr('viewBox', `0 0 ${fullWidth * 2} ${fullHeight * 2}`) -> zoom out
    .call(responsify) // make container responsive
  .append('g')
    .attr('transform', `translate(${margin.left}, ${margin.top})`)

function responsify(svg) {
  // get container and aspect ratio
  const container = d3.select(svg.node().parentNode),
    width = parseInt(svg.style('width')),
    height = parseInt(svg.style('height')),
    aspect = width / height

  // add viewBox and perform initial resize
  svg.attr('viewBox', `0 0 ${width} ${height}`)
    .attr('preserveRation', 'xMinYMid')
    .call(resize)

  // register listener, resize.NAMESPACE allows for multiple listener for resize event
  d3.select(window).on(`resize.${container.attr('id')}`, resize)

  // resize svg to fit container
  const resize = () => {
    const targetWidth = parseInt(container.style('width'))
    svg.attr('width', targetWidth).attr('height', Math.round(targetWidth / aspect))
  }
}
```

```HTML
<div class='chart'>
</div>
```
