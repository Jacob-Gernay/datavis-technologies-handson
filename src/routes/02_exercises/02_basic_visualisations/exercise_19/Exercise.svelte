<script>
    // Import statement
    import { scaleLinear } from 'd3-scale';

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
    const xScale = scaleLinear()
    .domain([Math.min(values.x), Math.max(values.x)])
    .range([0, innerWidth]);

    const yScale = scaleLinear()
    .domain([Math.min(values.y), Math.max(values.y)])
    .range([0, innerHeight]);
  </script>
  
  <svg viewBox="0 0 {width} {height}">
    <g transform="translate({margin.left},{margin.top})">
      <!--  -->
    </g>
  </svg>
  
  <style>
    text {
      text-anchor: middle;
      font-size: small;
    }
  </style>
  