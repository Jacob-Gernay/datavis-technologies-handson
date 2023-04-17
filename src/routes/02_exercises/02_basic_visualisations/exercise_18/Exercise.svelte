<script>
  // Import statements
  import { scaleLog } from 'd3-scale';
  import { axisBottom } from 'd3-axis';
  import { select } from 'd3-selection';

  // Dimensions
  const width = 800;
  const height = 100;
  const margin = { top: 5, right: 5, bottom: 5, left: 5 };
  const innerWidth = width - margin.left - margin.right;
  const innerHeight = height - margin.top - margin.bottom;
  
  // Array
  const values = [2, 4, 6, 7, 9];
  
  // Scaler
  const scale = scaleLog()
    .domain([1, Math.max(...values)])
    .range([0, innerWidth]);
  
  // x-Axis
  const xAxis = axisBottom(scale) 
  function AxisGenerator(handle){
    xAxis(select(handle))
  }
</script>
  

<svg viewBox="0 0 {width} {height}">
  <g class = "logcircles" transform="translate({margin.left},{margin.top})">
    {#each values as value}
    <circle cx = {scale(value)} cy = 50% r=10 />
    {/each}
   </g>

   <g use:AxisGenerator transform="translate({margin.left},{height-25})"> 
  </g>
  <g class="tick" opacity="1" transform="translate({margin.left+ 400},{height - 20})">
    <text fill="currentColor" y="9" dy="0.71em">X-axis</text>
  </g>
</svg>

<style>
  circle {
    fill: teal;
  }
  text {
    font:10px sans-serif
  }
</style>