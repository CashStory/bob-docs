---
title: Plot Lib
description: 
published: true
date: 2020-07-01T13:25:17.555Z
tags: 
editor: markdown
---

# Plot Lib 

Plot lib contains functions to generate plotly graphs.

### Functions

``` python
def updateChartCss(self, chart_filename, css_filename)
```
Update css file of a plotly chart.

| Parameter       | Type   | Description                        |
| --------------- | ------ | ---------------------------------- |
| chart_filename* | string | Name of the html file of the chart |
| css_filename*   | string | Name of the css file               |


```python
def financial_candlestick(self, stock_companies, start=(dt.datetime.today() - dt.timedelta(days=365)), end=dt.datetime.today(), interval='1d', filter=True, filter_title='Stock')
```
Return a candlestick chart made with plotly with yahoo finance csv data. 

| Parameter        | Type    | Description                                                  |
| ---------------- | ------- | ------------------------------------------------------------ |
| stock_companies* | string  | Name of the company (ex: 'AAPL' for Apple)                   |
| start            | string  | Start date of data                                           |
| end              | string  | End date of data (default is today)                          |
| interval         | string  | Interval between data values                                 |
| filter           | boolean | Show filter button to show candlestick for multiples company names |
| filter_title     | string  | Name of the filter button                                    |

``` python
def tablechart(self, header_values, cells_values, header_color = 'rgb(136,233,175)')
```
Return a table chart made with plotly from an excel or csv file. 

| Parameter      | Type   | Description                                                  |
| -------------- | ------ | ------------------------------------------------------------ |
| header_values* | string | Values of the columns ('df.columns' for all)                 |
| cells_values*  | string | Values in each columns (ex: [df.Rank, df.State, df.Postal, df.Population]) |
| header_color   | string | Color of the top line of the table (use rgb color)           |