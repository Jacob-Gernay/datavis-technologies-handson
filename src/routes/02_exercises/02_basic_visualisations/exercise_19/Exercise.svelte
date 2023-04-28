<script>
    // Import statement
    import { scaleLinear, scaleOrdinal } from 'd3-scale';
    import { schemeDark2 } from 'd3-scale-chromatic';
import { text } from 'svelte/internal';

    // Dimensions
    const width = 800;
    const height = 100;
    const margin = { top: 20, right: 5, bottom: 5, left: 5 };
    const innerWidth = width - margin.left - margin.right;
    const innerHeight = height - margin.top - margin.bottom;
  
    // Array
    const values = [
      { x: 2, y: 1, category: "cat1" },
      { x: 4, y: 2, category: "cat3" },
      { x: 6, y: 1, category: "cat2" },
      { x: 7, y: 3, category: "cat3" },
      { x: 9, y: 1, category: "cat2" }
    ];
  
    // Scale
    const xValues = values.map(d => d.x);
    const yValues = values.map(d => d.y);

    const xScale = scaleLinear()
      .domain([Math.min(...xValues)-1, Math.max(...xValues)+1])
      .range([0, innerWidth]);

    const yScale = scaleLinear()
      .domain([Math.min(...yValues)-1, Math.max(...yValues)+1])
      .range([innerHeight, 0]);


    // Colors
    const uniques = [...new Set(values.map(v => v.category))]
    const colorScale = scaleOrdinal()
      .domain(uniques)
      .range(schemeDark2)
  </script>
  
  <svg viewBox="0 0 {width} {height}">
    <g transform="translate({margin.left},{margin.top})">
      {#each values as value}
      <line x1={xScale(value.x)} y1={yScale(value.y)}
      x2={xScale(value.x)} y2={height}
      stroke = "black"/>
      <circle cx = {xScale(value.x)}
              cy = {yScale(value.y)}
              r = "8"
              fill = {colorScale(value.category)} />
      <text x = {xScale(value.x)}
            y = {yScale(value.y)-10}
            class = "valueLabel">
              {value.y} </text>
      {/each}
    </g>
  </svg>
  
  <style>
    text {
      text-anchor: middle;
      font-size: small;
    }
  </style>
  