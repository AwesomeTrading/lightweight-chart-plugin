<!-- markdownlint-disable no-inline-html first-line-h1 -->

<div align="center">
  <a href="https://github.com/safaritrader/lightweight-chart-plugin" target="_blank">
    <img width="1000" src="https://github.com/safaritrader/lightweight-chart-plugin/blob/main/src/lightweight-chart-plugin.jpg">
  </a>
  <h1>TradingView Lightweight Charts™ Plugin (LCP)</h1>
</div>

[![ License](https://img.shields.io/badge/Tradingview_LightWeight_Chart-4.2.0-blue&?color=red)](https://github.com/tradingview/lightweight-charts)
[![MIT License](https://img.shields.io/badge/LCP-1.0.0-blue&?color=red)](https://choosealicense.com/licenses/mit/)

Elevate your financial charts with custom overlays, interactive tooltips, and dynamic volume profiles. The Lightweight Chart Plugin extends the [Lightweight Charts library](https://github.com/tradingview/lightweight-charts/), offering powerful features for advanced data visualization and user interaction.


## 🎉 Features

- **✨ Custom Overlays**: Draw rectangles, circles, and vertical session markers directly on your charts.
- **💬 Interactive Tooltips**: Display rich, informative tooltips upon user interaction.
- **📈 Volume Profiles**: Visualize volume distribution across different price levels with ease.
- **🔧 Flexible Configuration**: Tailor every aspect of the plugin to fit your specific needs.

## 🚀 Getting Started
**Installation**
CDN

You can use [unpkg](https://unpkg.com):

[https://unpkg.com/lightweight-chart-plugin@1.0.0/dist/lightweight-chart-plugin.js](https://unpkg.com/lightweight-chart-plugin@1.0.0/dist/lightweight-chart-plugin.js)

or include it directly in your HTML:
```html
<script src="https://unpkg.com/lightweight-charts@4.2.0/dist/lightweight-charts.standalone.production.js"></script>
<div id="chartContainer">
    <div id="chart" style=""></div>
    <!-- Plugin Canvas --->
    <canvas id="overlayCanvas" style="position: absolute; top: 0; left: 0; pointer-events: none;"></canvas>
    <!-- Plugin Canvas --->
    <canvas id="overlayCanvasVP" style="position: absolute; top: 0; left: 0; pointer-events: none;"></canvas>
</div>
<!-- Load Plugin --->
<script src="path/to/lightweight-chart-plugin.js"></script>
<script>
    <!-- Create Chart --->
    <!-- Plugin Implementation --->
</script>
</body>
</html>
```
**Quick Example**

```js
const chart = LightweightCharts.createChart(document.getElementById('chart'), {});
const series = chart.addCandlestickSeries({});
const lcp = new LighweightChartPlugin({
    //Pass The Chart
    chart: chart,
    //Pass CandleStick Series
    series: series});
//Add Rectangle
lcp.addRectangle(
    time1='2023-04-13 10:02' , price1=103,
    time2='2023-04-13 14:32', price2=105,
    color='rgba(255,1,73,0.70)', useGradient= true,
    tooltipText = 'Sell Label Not Triggered', triggered = false);
//Add Circle
lcp.addCircle(
    time = '2023-04-13 10:03', price = 1,
    color= 'rgba(255,2,2,0.5)', useGradient= true,
    tooltipText ='Circle Sell location_ High', location_ ='high');
//Add Session 
lcp.addSession(
    time='2023-04-13 10:25',
    color= 'rgba(8,255,178,0.27)');

let volume_data = [
        { time: '2023-04-13 10:00', price: 100, volume:5 },
        { time: '2023-04-13 10:01', price: 101, volume:5 },]
volume_data.forEach(vol =>{
        //Add Volume Profile
        lcp.addVolume(vol.time,vol.price,vol.volume)
    })
```


## 📚 Documentation
### Initialization

Create a new instance of LightweightChartPlugin:
```js
const lcp = new LightweightChartPlugin(userSettings);
```
### Parameters:
- userSettings (Object): Configuration options.
Configuration Options
Plugin Defaults

    chartContainerId (string): The ID of the chart container element.
    chartDivId (string): The ID of the chart div element.
    overlayCanvasId (string): The ID of the overlay canvas element.
    series (Series): The series object from Lightweight Charts.
    chart (Chart): The chart object from Lightweight Charts.

Tooltip Defaults

Customize the tooltip appearance:

|enabled (boolean)|position (string)|padding (string)|backgroundColor (string)|color (string)|borderRadius (string)|textAlign (string)|
|-----------------|------------------|---------------|------------------------|--------------|---------------------|------------------|
| Enable or disable tooltips | CSS position property | Padding around the tooltip content | Background color | Text color | Border radius | Text alignment |

Volume Profile Defaults

## Customize the volume profile: 
| enabled (boolean) | volumeProfileId (string) | bins (number) | width_percentage_vp (number) | textColor (string) | color (string) |
|-------------------|--------------------------|---------------|------------------------------|--------------------|----------------|
| Enable or disable volume profiles | The ID of the volume profile canvas element | Number of bins for the volume profile | Width percentage of the volume profile canvas | Color of the volume text | Color of the volume bars |

---

## Methods

### *addRectangle*

**Add a ❏Rectangle overlay to the chart.**

| Parameter       | Type     | Description                                                                 |
|-----------------|----------|-----------------------------------------------------------------------------|
| time1           | string   | Start time (yyyy-mm-dd HH:MM)                                                |
| price1          | number   | Lower price                                                                  |
| time2           | string   | End time (yyyy-mm-dd HH:MM)                                                  |
| price2          | number   | Upper price                                                                  |
| color           | string   | Color of the rectangle                                                       |
| useGradient     | boolean  | Use gradient fill                                                            |
| tooltipText     | string   | Text to display in the tooltip                                               |
| triggered       | boolean  | Whether the rectangle is triggered; if `false`, the rectangle ends in view.  |

---

### *addCircle*

**Add a © Circle overlay to the chart.**

| Parameter       | Type            | Description                                        |
|-----------------|-----------------|----------------------------------------------------|
| time            | string          | Time (yyyy-mm-dd HH:MM)                            |
| price           | number          | Radius of the circle (price difference)            |
| color           | string          | Color of the circle                                |
| useGradient     | boolean         | Use gradient fill                                  |
| tooltipText     | string          | Text to display in the tooltip                     |
| location        | string \| number| Location on the chart ('high', 'low', or a specific price) |

---

### *addSession*

**Add a vertical rectangle (session marker) to the chart.**

| Parameter       | Type     | Description                                 |
|-----------------|----------|---------------------------------------------|
| time            | string   | Time (yyyy-mm-dd HH:MM)                     |
| color           | string   | Color of the session marker                 |
| label           | string   | Label for the session                       |

---

### *addVolume*

**Add ☰ Volume data for volume profile visualization.**

| Parameter       | Type     | Description                       |
|-----------------|----------|-----------------------------------|
| time            | string   | Time (yyyy-mm-dd HH:MM)           |
| price           | number   | Price                             |
| volume          | number   | Volume                            |

---

## 🎨 Customization

```js
const plugin = new LightweightChartPlugin({
  background: {
        opacity : '1',
        backgroundColor : '#131723',
    },
    tooltip:{
        padding : '5px',
        backgroundColor : 'rgb(19,23,35)',
        color : '#fff',
        borderRadius : '4px',
        transform : 'translate(-50%, -100%)',
        zIndex : 9999999,
        textAlign : 'center',
    },
    volumeprofile:{
        enabled : true,
        bins:40,
        width_percentage_vp:10,
        textColor:'white',
        color:'rgba(231,156,250,0.1)',
    }
  // Other settings...
});
```
## 🛠️ Development
**Project Structure**

    dist/lightweight-chart-plugin.js: The main plugin class.
    example/index.html: An example HTML file demonstrating the plugin usage.

**Running the Example**

To run the example locally:

1. Clone the repository:

```bash
git clone https://github.com/safaritrader/lightweight-chart-plugin.git
```

Open example/index.html in your web browser.

---

## 🤝 Contributing

Contributions are what make the open-source community such an amazing place to learn, inspire, and create. Any contributions you make are greatly appreciated.

1. Fork the Project

2. Create your Feature Branch

```bash
git checkout -b feature/AmazingFeature
```
3. Commit your Changes

```bash
git commit -m 'Add AmazingFeature'
```

4. Push to the Branch

```bash
git push origin feature/AmazingFeature
```
5. Open a Pull Request

---

## 📰 Feautres To Add
- Custom Price Line (deletable , hover's)
- Price Alert (Settings : Cross , Timer)
- Custom Trend Line (with Alert)
---

## 📝 License

Distributed under the MIT License. See LICENSE for more information.

---

## 📞 Contact

[Hassan Safari] - @global-fxs - info@global-fxs.com

Project Link: https://github.com/yourusername/lightweight-chart-plugin


