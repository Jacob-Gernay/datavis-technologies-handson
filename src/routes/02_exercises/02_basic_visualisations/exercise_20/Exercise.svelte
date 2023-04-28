<script>
    // Import statement
    import { scaleLinear, scaleBand } from 'd3-scale';
    import { axisLeft, axisBottom } from 'd3-axis';
    import { select } from 'd3-selection';

    // Dimensions
    const width = 600;
    const height = 300;
    const margin = { top: 10, right: 10, bottom: 30, left: 60 };
    const innerWidth = width - margin.left - margin.right;
    const innerHeight = height - margin.top - margin.bottom;
  
    // Array
    const data = [
      { service: "Netflix", viewers: 2.9 },
      { service: "Amazon Prime Video", viewers: 1.3 },
      { service: "Disney+", viewers: 2.1 },
      { service: "Hulu", viewers: 0.9 },
      { service: "Apple TV", viewers: 1.1 },
      { service: "Rakuten", viewers: 0.4 }
    ];

    // Scale
    const yValues = data.map(d => d.viewers);
    const uniques = [...new Set(data.map(v => v.service))]

    const yScale = scaleLinear()
      .domain([0, Math.max(...yValues)+1])
      .range([innerHeight, 0]);

    const xScale = scaleBand()
      .domain(uniques)
      .range([0, innerWidth])
      .paddingInner(0.1)
      .paddingOuter(0.1);

    // y-Axis
    const yAxis = axisLeft(yScale) 
    function yAxisGenerator(handle){
    yAxis(select(handle))
    }

    // x-Axis
    const xAxis = axisBottom(xScale) 
    function xAxisGenerator(handle){
    xAxis(select(handle))
    }


  </script>
  
  <!-- setting a viewBox and max-width allows the SVG to shrink but not grow! -->
  <svg viewBox="0 0 {width} {height}" style="max-width: {width}px">
    <g transform={`translate(${margin.left},${margin.top})`}>
      {#each data as value}
      <rect x={xScale(value.service)} y={yScale(value.viewers)} width={xScale.bandwidth()} height={innerHeight - yScale(value.viewers)}/>
      {/each}
    </g>
    <g use:yAxisGenerator transform="translate({margin.left},{margin.top})"> 
    </g>
    <g transform={`translate(${margin.left-50},${height/2}) rotate(-90)`}>
      <text>Viewers</text>
    </g>
    <g use:xAxisGenerator transform="translate({margin.left},{height - margin.bottom})"> 
    </g>
  </svg>