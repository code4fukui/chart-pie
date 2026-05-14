# chart-pie

> 日本語のREADMEはこちらです: [README.ja.md](README.ja.md)

A lightweight Web Component for creating responsive pie charts from CSV or JavaScript data.

## Demo

[Live demo](https://code4fukui.github.io/chart-pie/)


![A pie chart showing resource counts by group from data.go.jp, with labels for name, count, and percentage on each slice, and the total count in the center.](https://github.com/code4fukui/chart-pie)


## Features

-   **Simple & Declarative:** Use as a standard HTML custom element (`<chart-pie>`).
-   **Flexible Data Sources:** Provide data as inline CSV, an external CSV file, or a JavaScript object.
-   **Responsive:** Automatically resizes to fit its container.
-   **Informative Labels:** Displays the name, value, and percentage for each slice.
-   **Total Value Display:** Shows the sum of all values in the center of the chart.

## Usage

### 1. In HTML

Include the `chart-pie.js` module in your HTML file. You can then use the `<chart-pie>` element directly.

```html
<script type="module" src="https://code4fukui.github.io/chart-pie/chart-pie.js"></script>

<!-- Example 1: Data as inline CSV -->
<chart-pie style="width: 600px; height: 400px;">
name,count
A,30
B,20
C,70
</chart-pie>

<!-- Example 2: Data from an external CSV file -->
<chart-pie src="./data.csv" style="width: 100vw; height: 30vh;"></chart-pie>
```

### 2. Programmatically with JavaScript

You can also import the `ChartPie` class and create an instance programmatically.

```html
<div id="chart-container"></div>

<script type="module">
  import { ChartPie } from "https://code4fukui.github.io/chart-pie/chart-pie.js";

  // Data as an array of objects
  const dataArray = [
    { name: "A", count: 30 },
    { name: "B", count: 20 },
    { name: "C", count: 70 },
  ];

  // Or data as a simple key-value object
  const dataObject = {
    "A": 30,
    "B": 20,
    "C": 70,
  };

  const chart = new ChartPie(dataArray);
  chart.style.width = "300px";
  chart.style.height = "300px";
  
  document.getElementById("chart-container").appendChild(chart);
</script>
```

## API & Data Format

### Element Attributes

-   `src`: A URL to a CSV file. The component will fetch and parse this file to generate the chart.

### Data Structure

The component accepts data in several formats:

1.  **CSV**: The CSV data, whether inline or from a `src` file, must have a header row. It requires two columns: one for the label (e.g., `name`) and one for the numerical value (`count` or `value`).

    ```csv
    name,count
    Agriculture,96777
    Finance,47496
    Education,28012
    ```

2.  **JavaScript Array**: An array of objects, where each object has a `name` property and a `count` or `value` property.

    ```javascript
    [
      { name: "A", value: 30 },
      { name: "B", value: 20 },
      { name: "C", value: 70 }
    ]
    ```

3.  **JavaScript Object**: A simple key-value object, where keys are the labels and values are the numerical data.

    ```javascript
    {
      "A": 30,
      "B": 20,
      "C": 70
    }
    ```

## License

MIT License — see [LICENSE](LICENSE).