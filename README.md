<!DOCTYPE html>
<html>
<head>
	<!-- Load plotly.js into the DOM -->
	<script src='https://cdn.plot.ly/plotly-2.14.0.min.js'></script>
	<script src='https://cdnjs.cloudflare.com/ajax/libs/d3/3.5.17/d3.min.js'></script>
</head>

<body>
	<div id='myDiv'><!-- Plotly chart will be drawn inside this DIV --></div>
  <script>
    d3.csv('https://raw.githubusercontent.com/erinmichno/FridayDirectX/master/testData.csv', function(err, rows){
function unpack(rows, key) {
	return rows.map(function(row)
	{ return row[key]; });}
var xData =unpack(rows, 'x2')
var yData = unpack(rows, 'y2')
var zData = unpack(rows, 'z2')
var trace1 = {
	x:xData, y: yData, z: zData,
	mode: 'markers',
	marker: {
    color: xData,
    colorscale: 'Jet',
		size: 12,
		line: {
		color: zData,
		width: 0.25},
		opacity: 0.9},
	type: 'scatter3d'
};


var data = [trace1];
var layout = {margin: {
	l: 0,
	r: 0,
	b: 0,
	t: 0
  },
             };
Plotly.newPlot('myDiv', data, layout);

});
  </script>
</body>
</html>
