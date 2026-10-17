**HK Temperature Heatmap: CSCE-679 Data Visualization Assignment 1**

Live notebook: \[Open in Google Colab\]([https\://colab.research.google.com/drive/1SWedRTMzQjWBMFXsXUj3ZdnQELB9Pz\_B?usp=sharing](https://colab.research.google.com/drive/1SWedRTMzQjWBMFXsXUj3ZdnQELB9Pz_B?usp=sharing) )

Overview

This assignment presents two interactive visualizations of Hong Kong temperature data. The project was developed in Google Colab using Python for data preparation and HTML, CSS, JavaScript, SVG, and D3.js v7 for interactive charts.

Screenshots

Level 1: Maximum Temperature



Level 1: Minimum Temperature with Tooltip



Level 2: Daily Temperature Lines — Maximum Background



Level 2: Daily Temperature Lines — Minimum Background



Files

HK_Temperature_Heatmap.ipynb: Google Colab/Jupyter notebook containing data preparation and both visualizations.

temperature_daily.csv: Source dataset required to run the notebook.

README.md: Project documentation.

SCREENSHOTS/: Screenshots of the visualization outputs.

Tools and How They Are Used

Google Colab: Development and execution environment for the notebook.

Python: Loads, cleans, aggregates, and prepares the temperature data.

pandas: Reads the CSV, parses dates and numeric columns, removes invalid records, and computes monthly summaries.

JSON: Passes prepared Python data into the JavaScript visualization code.

HTML and CSS: Define chart headings, controls, layout, and tooltip styling.

JavaScript: Builds the interactive visualizations and handles user interactions.

D3.js v7: Creates the heatmap, temperature lines, scales, color mapping, and tooltips. It is loaded from https://d3js.org/d3.v7.min.js.

SVG: Draws heatmap cells, axes, labels, legends, and daily temperature lines.

Input Data and Preparation

The CSV contains the columns date, max_temperature, and min_temperature. Python parses the dates and numeric values and removes rows with invalid required values.

The data is grouped by year and month to calculate:

Monthly maximum: The highest daily maximum temperature recorded in that month.

Monthly minimum: The lowest daily minimum temperature recorded in that month.

Python serializes the prepared records to JSON for use by the D3.js visualizations.

Level 1: Year/Month Heatmap

Covers 1997–2017.

Years are arranged in columns, and January through December are arranged in rows.

Each cell represents one year/month combination.

A dropdown switches the background colors between monthly maximum and monthly minimum temperatures.

Hovering over a cell displays the year, month, and temperature information.

Missing year/month combinations remain blank rather than being treated as zero.

D3.js scales position the cells, while SVG elements draw the axes, tick marks, and labels.

Level 2: Daily Temperature Heatmap

Focuses on 2008–2017.

Each cell represents one month in a particular year.

Daily maximum temperatures are displayed as a green line, and daily minimum temperatures as a cyan line.

Day of the month determines the horizontal position, while temperature determines the vertical position within each monthly cell.

A Maximum Temperature / Minimum Temperature toggle changes the monthly background colors.

In maximum mode, each monthly background represents that month's highest daily maximum temperature.

In minimum mode, each monthly background represents that month's lowest daily minimum temperature.

Both daily temperature lines remain visible in either mode.

Hovering over daily points displays the date, temperature type, and value. Hovering over a monthly background displays the corresponding monthly temperature summary.

A vertical temperature index bar appears on the right side of the visualization.

Color Mapping and Legend

Both levels use the same reversed D3 Spectral palette:

d3.schemeSpectral[11].slice().reverse()

The temperature thresholds are:

4, 8, 12, 15, 18, 22, 25, 29, 33, 36

Using the same palette and thresholds keeps the temperature color interpretation consistent between both visualizations. The legend uses discrete color bands, with temperature labels ranging from 0°C at the bottom to 40°C at the top of the vertical index bar.

Run in Google Colab

Open the notebook using the Google Colab link, or upload HK_Temperature_Heatmap.ipynb to Colab.

Upload temperature_daily.csv to the Colab session if it is not already available.

Restart the session and run the notebook cells in order.

Confirm that both visualizations render successfully.

Test the Level 1 maximum/minimum dropdown and the Level 2 maximum/minimum toggle.

Hover over cells and daily points to verify the tooltips.

Check that the axes, labels, color legends, and chart boundaries are visible.

The notebook loads D3.js from a public CDN, so an internet connection is required. The dataset ends on October 28, 2017; November and December 2017 have no observations.

Implementation Note

The visualizations are embedded in notebook cells rather than maintained as separate JavaScript files. Python handles data preparation and passes JSON records to the HTML templates, while D3.js renders the interactive charts in the browser. Some visualization logic, including legend and axis drawing, is implemented separately for each level.
**Implementation note**

The visualizations are embedded in notebook cells rather than separated into standalone JavaScript files. Python handles data processing and passes JSON into the HTML templates, and D3.js executes in the browser to render the interactive visualizations. The legend/axis drawing and other chart logic remain defined in each level's JavaScript, so some logic is repeated between levels.  
