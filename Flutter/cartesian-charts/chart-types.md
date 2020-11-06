---
layout: post
title: Syncfusion Cartesian Chart types
description: Learn what are the different types of Cartesian Charts available in the Syncfusion Flutter Chart widget.
platform: flutter
control: Chart
documentation: ug
---

# Chart types in Cartesian charts

## Line chart

To render a line chart, create an instance of [`LineSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LineSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The following properties are used to customize the appearance:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the line.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - Controls the transparency of the chart series.
* [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) – Changes the stroke width of the line.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        final List<SalesData> chartData = [
            SalesData(2010, 35),
            SalesData(2011, 28),
            SalesData(2012, 34),
            SalesData(2013, 32),
            SalesData(2014, 40)
        ];

        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders line chart
                            LineSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

    class SalesData {
        SalesData(this.year, this.sales);
            final double year;
            final double sales;
    }

{% endhighlight %}

![Line chart](images/cartesian-chart-types/line.jpg)

### Dashed line

The [`dashArray`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/dashArray.html) property of [`LineSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LineSeries-class.html) is used to render line series with dashes. Odd value is considered as rendering size and even value is considered as gap.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            LineSeries<SalesData, String>(
                                dataSource: chartData,
                                // Dash values for line
                                dashArray: <double>[5,5],
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Dashed line chart](images/cartesian-chart-types/dashed_line.jpg)

### Multi-colored line

To render a multi-colored line series, map the individual colors to the data using the [`pointColorMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/pointColorMapper.html) property.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(),
                        series: <ChartSeries>[
                            LineSeries<SalesData, String>(
                                dataSource: [
                                    SalesData('Jan', 35, Colors.red),
                                    SalesData('Feb', 28, Colors.green),
                                    SalesData('Mar', 34, Colors.blue),
                                    SalesData('Apr', 32, Colors.pink),
                                    SalesData('May', 40, Colors.black)
                                ],
                                // Bind the color for all the data points from the data source
                                pointColorMapper:(SalesData sales, _) => sales.segmentColor,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

    class SalesData {
        SalesData(this.year, this.sales, this.segmentColor);
        final double year;
        final double sales;
        final Color segmentColor;
    }

{% endhighlight %}

![Multi-colored line](images/cartesian-chart-types/multiColored_line.jpg)

Also refer, [color palette](./series-customization#color-palette), [color mapping](./series-customization#color-mapping-for-data-points), [animation](./series-customization#animation), [gradient](./series-customization#gradient-fill) and [empty points](./series-customization#empty-points) for customizing the line series further.

## Fast line chart

[`FastLineSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FastLineSeries-class.html) is a line chart, but it loads faster than [`LineSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LineSeries-class.html). You can use this when there are large number of points to be loaded in a chart. To render a fast line chart, create an instance of [`FastLineSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FastLineSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html). The following properties are used to customize the appearance of fast line segment:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the line.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - Controls the transparency of the chart series.
* [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) – Changes the stroke width of the line.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders fast line chart
                            FastLineSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }


{% endhighlight %}

![Fast line chart](images/cartesian-chart-types/fastline.jpg)

Also refer, [color palette](./series-customization#color-palette), [color mapping](./series-customization#color-mapping-for-data-points), [animation](./series-customization#animation), [gradient](./series-customization#gradient-fill) and [empty points](./series-customization#empty-points) for customizing the fast line series further.

## Area chart

To render an area chart, create an instance of [`AreaSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AreaSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The area chart shows the filled area to represent the data, but when there are more than a series, this may hide the other series. To get rid of this, increase or decrease the transparency of the series. 

The following properties are used to customize the appearance:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - Controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) – Changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) – Changes the stroke color of the series.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders area chart
                            AreaSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Area chart](images/cartesian-chart-types/area.jpg)

###	Border customization

The borders of the area chart can be customized using the [`borderDrawMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AreaSeries/borderDrawMode.html) property. The default value of the [`borderDrawMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AreaSeries/borderDrawMode.html) property is [`top`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BorderDrawMode-class.html). The other values are [`all`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BorderDrawMode-class.html) and [`excludeBottom`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BorderDrawMode-class.html).

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            AreaSeries<SalesData, double>(
                                dataSource: chartData,
                                color: Colors.deepOrange[300],
                                borderMode: AreaBorderMode.excludeBottom,
                                borderColor: Colors.green,
                                borderWidth: 2,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Area border](images/cartesian-chart-types/area_border.jpg)

Also refer, [color palette](./series-customization#color-palette), [color mapping](./series-customization#color-mapping-for-data-points), [animation](./series-customization#animation), [gradient](./series-customization#gradient-fill) and [empty points](./series-customization#empty-points) for customizing the area series further.

### Area with gradients

The [`gradient`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/gradient.html) property is used to define the gradient colors. The colors from this property is used for series.


{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
         final List<Color> color = <Color>[];
        color.add(Colors.blue[50]);
        color.add(Colors.blue[200]);
        color.add(Colors.blue);

        final List<double> stops = <double>[];
        stops.add(0.0);
        stops.add(0.5);
        stops.add(1.0);

        final LinearGradient gradientColors =
            LinearGradient(colors: color, stops: stops);
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders area chart
                            AreaSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales,
                                 gradient: gradientColors
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Area gradients](images/cartesian-chart-types/area_gradient.png)

### Area with empty points

Data points with a null value are considered empty points. Empty data points are ignored and are not plotted in the chart. By using [`emptyPointSettings`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/emptyPointSettings.html) property in series, you can decide the action taken for empty points. Available [`modes`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointMode-class.html) are [`gap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointMode-class.html), [`zero`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointMode-class.html), [`drop`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointMode-class.html) and [`average`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointMode-class.html). Default mode of the empty point is [`gap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointMode-class.html).

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            AreaSeries<SalesData, double>(
                                dataSource: chartData,
                                color: Colors.deepOrange[300],
                                borderMode: AreaBorderMode.excludeBottom,
                                borderColor: Colors.green,
                                borderWidth: 2,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Area with empty points](images/cartesian-chart-types/area_emptypoints.png)



### Vertical area chart

The [`isTransposed`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/isTransposed.html) property of [`CartesianSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries-class.html) is used to transpose the horizontal and vertical axes, to view the data in a different perspective. Using this feature, you can render vertical area chart.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        isTransposed: true,
                        series: <ChartSeries>[
                            AreaSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Vertical area chart](images/cartesian-chart-types/vertical_area.png)

## Spline chart

To render a spline chart, create an instance of [`SplineSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The following properties are used to customize the appearance of spline segment:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - Controls the transparency of the chart series.
* [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) – Changes the stroke width of the series.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders spline chart
                            SplineSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Spline border](images/cartesian-chart-types/spline.jpg)

### Dashed spline

The [`dashArray`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/dashArray.html) property of the [`SplineSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineSeries/SplineSeries.html) is used to render spline series with dashes. Odd value is considered as rendering size and even value is considered as gap.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            SplineSeries<SalesData, String>(
                                dataSource: chartData,
                                // Dash values for spline
                                dashArray: <double>[5, 5],
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Dashed spline chart](images/cartesian-chart-types/dashed_spline.jpg)

###	Spline rendering types

The [`splineType`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineSeries/splineType.html) allows you to change the spline curve in series. The following types are used in [`SplineSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineSeries/SplineSeries.html):

* natural
* monotonic
* cardinal
* clamped

By default, the value of [`splineType`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineSeries/splineType.html) is [`natural`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineType-class.html).

The following code sample demonstrates how to set the [`splineType`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineSeries/splineType.html) value to [`cardinal`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineType-class.html). When you set the cardinal type, you can specify the desired line tension of the [`cardinal`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineType-class.html) spline using the [`cardinalSplineTension`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineSeries/cardinalSplineTension.html) property. The value of this property ranges from 0 to 1.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            SplineSeries<SalesData, double>(
                                dataSource: chartData,
                                // Type of spline
                                splineType: SplineType.cardinal,
                                cardinalSplineTension: 0.9,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Spline type](images/cartesian-chart-types/cardinal_spline.jpg)

Also refer, [color palette](./series-customization#color-palette), [color mapping](./series-customization#color-mapping-for-data-points), [animation](./series-customization#animation), [gradient](./series-customization#gradient-fill) and [empty points](./series-customization#empty-points) for customizing the spline series further.

### Vertical spline chart

The [`isTransposed`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/isTransposed.html) property of [`CartesianSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries-class.html) is used to transpose the horizontal and vertical axes, to view the data in a different perspective. Using this feature, you can render vertical Spline chart.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        isTransposed: true,
                        series: <ChartSeries>[
                            SplineSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Vertical spline chart](images/cartesian-chart-types/inversed-spline.png)

## Column chart

To render a column chart, create an instance of [`ColumnSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/XyDataSeries-class.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The following properties are used to customize the appearance:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - Controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) – Changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) – Changes the stroke color of the series.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders column chart
                            ColumnSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )      
            )
        );
    }

{% endhighlight %}

![Column chart](images/cartesian-chart-types/column.jpg)

### Side-by-side series placement

By default, all the column series that have the same x and y-axes are placed side by side in a chart. If you want to place a series one over the other (overlapped), set the [`enableSideBySideSeriesPlacement`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/enableSideBySideSeriesPlacement.html) property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html) to false and configure the [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) property to differentiate the series. The following code snippet and screenshot illustrate the overlapped placement of column series.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        final List<SalesData> chartData = [
            SalesData(2010, 35, 23),
            SalesData(2011, 38, 49),
            SalesData(2012, 34, 12),
            SalesData(2013, 52, 33),
            SalesData(2014, 40, 30)
        ];
        
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        // Columns will be rendered back to back
                        enableSideBySideSeriesPlacement: false,
                        series: <ChartSeries>[
                            ColumnSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            ),
                            ColumnSeries<SalesData, double>(
                                opacity: 0.9,
                                width: 0.4,
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.loss
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Column side by side placement](images/cartesian-chart-types/sidebySidePlacement.jpg)

### Column width and spacing

The [`spacing`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries/spacing.html) property is used to change the spacing between two segments. The default value of spacing is 0, and the value ranges from 0 to 1. Here, 1 and 0 correspond to 100% and 0% of the available space, respectively.

The [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) property is used to change the width of the rectangle. The default value of the width is 0.7, and the value ranges from 0 to 1. Here, 1 and 0 correspond to 100% and 0% of the available width, respectively.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            ColumnSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales,
                                width: 0.8, // Width of the columns
                                spacing: 0.2 // Spacing between the columns
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Column width and spacing](images/cartesian-chart-types/column_width_spacing.jpg)

### Rounded corners

The [`borderRadius`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries/borderRadius.html) property is used to add the rounded corners to the rectangle.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            ColumnSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales,
                                // Sets the corner radius
                                borderRadius: BorderRadius.all(Radius.circular(15))
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Rounded corners](images/cartesian-chart-types/rounded_column.jpg)

### Track customization

Renders column with track. Track is a rectangular bar rendered from the start to the end of the axis. Column series will be rendered above the track. The [`isTrackVisible`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries/isTrackVisible.html) property is used to enable the track. The following properties are used to customize the appearance:

* [`trackColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries/trackColor.html) – Changes the color of the track.
* [`trackBorderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries/trackBorderWidth.html) – Changes the stroke width of the track.
* [`trackBorderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries/trackBorderColor.html) – Changes the stroke color of the track.
* [`trackPadding`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries/trackPadding.html) - Adds padding to the track.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            ColumnSeries<SalesData, double>(
                                dataSource: chartData,
                                // Renders the track
                                isTrackVisible: true,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Track](images/cartesian-chart-types/track_column.jpg)

Also refer, [color palette](./series-customization#color-palette), [color mapping](./series-customization#color-mapping-for-data-points), [animation](./series-customization#animation), [gradient](./series-customization#gradient-fill) and [empty points](./series-customization#empty-points) for customizing the column series further.

## Bar chart

To render a bar chart, create an instance of [`BarSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BarSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The following properties are used to customize the appearance:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - Controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) – Changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) – Changes the stroke color of the series.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders bar chart
                            BarSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Bar chart](images/cartesian-chart-types/bar.jpg)

### Bar width and spacing

The [`spacing`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BarSeries/spacing.html) property is used to change the spacing between two segments. The default value of spacing is 0, and the value ranges from 0 to 1. Here, 1 and 0 correspond to 100% and 0% of the available space, respectively.

The [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) property is used to change the width of the rectangle. The default value of the width is 0.7, and the value ranges from 0 to 1. Here, 1 and 0 correspond to 100% and 0% of the available width, respectively.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            BarSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales,
                                width: 0.6, // Width of the bars
                                spacing: 0.3 // Spacing between the bars
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Bar width and spacing](images/cartesian-chart-types/bar_width_spacing.jpg)

### Rounded corners

The [`borderRadius`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BarSeries/borderRadius.html) property is used to add the rounded corners to the rectangle.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            BarSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales,
                                borderRadius: BorderRadius.all(Radius.circular(15))
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Bar rounded corners](images/cartesian-chart-types/rounded_bar.jpg)

### Track customization

You can render the bar chart with track. Track is a rectangular bar rendered from the start to the end of the axis. Bar series will be rendered above the track. The [`isTrackVisible`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BarSeries/isTrackVisible.html) property is used to enable the track. The following properties are used to customize the appearance:

* [`trackColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BarSeries/trackColor.html) – Changes the color of the track.
* [`trackBorderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BarSeries/trackBorderWidth.html) – Changes the stroke width of the track.
* [`trackBorderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BarSeries/trackBorderColor.html) – Changes the stroke color of the track.
* [`trackPadding`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BarSeries/trackPadding.html) - Adds padding to the track.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            BarSeries<SalesData, double>(
                                dataSource: chartData,
                                // Renders the track
                                isTrackVisible: true,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Bar track](images/cartesian-chart-types/track_bar.jpg)

Also refer, [color palette](./series-customization#color-palette), [color mapping](./series-customization#color-mapping-for-data-points), [animation](./series-customization#animation), [gradient](./series-customization#gradient-fill) and [empty points](./series-customization#empty-points) for customizing the bar series further.

## Bubble chart

To render a bubble chart, create an instance of [`BubbleSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BubbleSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html).

Bubble chart requires three fields (X, Y, and Size) to plot a point. Here, [`sizeValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/sizeValueMapper.html) is used to map the size of each bubble segment from data source.

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - Controls the transparency of the chart series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) – Changes the stroke width of the series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) – Changes the stroke color of the series.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         final List<ChartData> chartData = [
            ChartData(2010, 35, 0.32),
            ChartData(2011, 38, 0.21),
            ChartData(2012, 34, 0.38),
            ChartData(2013, 52, 0.29),
            ChartData(2014, 40, 0.34)
        ];

        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders bubble chart
                            BubbleSeries<ChartData, double>(
                                dataSource: chartData,
                                sizeValueMapper: (ChartData sales, _) => sales.size,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y
                            )
                        ]
                    )
                )   
            )
        );
    }

    class ChartData {
        ChartData(this.x, this.y, this.size);
            final double x;
            final double y;
            final double size;
    }

{% endhighlight %}

![Bubble chart](images/cartesian-chart-types/bubble.jpg)

### Change the min and max radius of bubble

The [`minimumRadius`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BubbleSeries/minimumRadius.html) property is used to change the minimum size of the series and the [`maximumRadius`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BubbleSeries/maximumRadius.html) property is used to change the maximum size of the series.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            BubbleSeries<ChartData, double>(
                                dataSource: chartData,
                                sizeValueMapper: (ChartData sales, _) => sales.size,
                                minimumRadius:9, // Minimum radius of bubble
                                maximumRadius: 15, // Maximum radius of bubble
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Bubble size](images/cartesian-chart-types/bubble_radius.jpg)

Also refer, [color palette](./series-customization#color-palette), [color mapping](./series-customization#color-mapping-for-data-points), [animation](./series-customization#animation), [gradient](./series-customization#gradient-fill) and [empty points](./series-customization#empty-points) for customizing the bubble series further.

### Bubble with various color

Using the [`pointColorMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/pointColorMapper.html) and [`sizeValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/sizeValueMapper.html) properties in the Cartesian charts, the Bubble series with different colors and sizes can be rendered.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            BubbleSeries<ChartData, double>(
                                dataSource: chartData,
                                sizeValueMapper: (ChartData sales, _) => sales.size,
                                pointColorMapper:(ChartData sales, _) => sales.pointColor,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Bubble various color](images/cartesian-chart-types/bubble_variouscolors.png)

### Bubble with gradients

The [`gradient`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/gradient.html) property is used to define the gradient colors. The colors from this property is used for series.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        final List<Color> color = <Color>[];
        color.add(Colors.blue[50]);
        color.add(Colors.blue[200]);
        color.add(Colors.blue);

        final List<double> stops = <double>[];
        stops.add(0.0);
        stops.add(0.5);
        stops.add(1.0);

        final LinearGradient gradientColors =
            LinearGradient(colors: color, stops: stops);

        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <CartesianSeries>[
                            BubbleSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y,
                                 sizeValueMapper:(ChartData sales, _) => sales.size,
                                // Applies gradient color
                                gradient: gradientColors
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Bubble gradients](images/cartesian-chart-types/bubble_gradients.png)

### Bubble with multiple series

Using the [`datasource`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/dataSource.html) property in the Map charts, multiple series can be rendered in a bubble chart.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            BubbleSeries<ChartData, num>(
                                  dataSource: northAmerica,
                                  xValueMapper: (ChartData sales, _) => sales.xValue,
                                  yValueMapper: (ChartData sales, _) => sales.y,
                                  sizeValueMapper: (ChartData sales, _) => sales.size),
                            BubbleSeries<ChartData, num>(
                                  dataSource: europe,
                                  xValueMapper: (ChartData sales, _) => sales.xValue,
                                  yValueMapper: (ChartData sales, _) => sales.y,
                                  sizeValueMapper:(ChartData sales, _) => sales.size),
                            BubbleSeries<ChartData, num>(
                                  dataSource: asia,
                                  xValueMapper: (ChartData sales, _) => sales.xValue,
                                  yValueMapper: (ChartData sales, _) => sales.y,
                                  sizeValueMapper: (ChartData sales, _) => sales.size),
                            BubbleSeries<ChartData, num>(
                                  dataSource: africa,
                                  xValueMapper: (ChartData sales, _) => sales.xValue,
                                  yValueMapper: (ChartData sales, _) => sales.y,
                                  sizeValueMapper: (ChartData sales, _) => sales.size),
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Bubble nultiple series](images/cartesian-chart-types/bubble_with_multiple.png)

## Scatter chart

To render a scatter chart, create an instance of [`ScatterSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ScatterSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html). The following properties are used to customize the scatter segment appearance.

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - Controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) – Changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) – Changes the stroke color of the series.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders scatter chart
                            ScatterSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Scatter chart](images/cartesian-chart-types/scatter.jpg)

###	Change shape and size of the scatter

The [`shape`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerSettings/shape.html) property is used to change the rendering shape of scatter series. The available shapes are [`circle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataMarkerType-class.html), [`rectangle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataMarkerType-class.html), [`pentagon`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataMarkerType-class.html), [`verticalLine`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataMarkerType-class.html), [`horizontalLine`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataMarkerType-class.html), [`diamond`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataMarkerType-class.html), [`triangle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataMarkerType-class.html), [`image`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataMarkerType-class.html), and [`invertedTriangle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataMarkerType-class.html). If [`image`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerSettings/image.html) shape is specified, then you can assign the image using the [`image`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerSettings/image.html) property.

The [`height`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerSettings/height.html) and [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerSettings/width.html) properties of [`markerSettings`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/markerSettings.html) are used to change the height and width of the scatter series, respectively.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            ScatterSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y,
                                markerSettings: MarkerSettings(
                                    height: 15,
                                    width: 15,
                                    // Scatter will render in diamond shape
                                    shape: DataMarkerType.diamond
                                )
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Scatter shape](images/cartesian-chart-types/scatter_shape.jpg)

Also refer, [color palette](./series-customization#color-palette), [color mapping](./series-customization#color-mapping-for-data-points), [animation](./series-customization#animation), [gradient](./series-customization#gradient-fill) and [empty points](./series-customization#empty-points) for customizing the scatter series further.

## Step line chart

To render a step line chart, create an instance of [`StepLineSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StepLineSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html). The following properties are used to customize the appearance of spline segment:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the line.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - Controls the transparency of the chart series.
* [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) – Changes the stroke width of the line.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders step line chart
                            StepLineSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Step line chart](images/cartesian-chart-types/stepline.jpg)

### Dashed step line

The [`dashArray`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/dashArray.html) property of the [`StepLineSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StepLineSeries-class.html) is used to render step line series with dashes. Odd value is considered as rendering size and even value is considered as gap.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StepLineSeries<ChartData, double>(
                                dataSource: chartData,
                                // Dashes for step line
                                dashArray: <double>[5, 5],
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Step line chart](images/cartesian-chart-types/dashed_stepline.jpg)

Also refer, [color palette](./series-customization#color-palette), [color mapping](./series-customization#color-mapping-for-data-points), [animation](./series-customization#animation), [gradient](./series-customization#gradient-fill) and [empty points](./series-customization#empty-points) for customizing the step line series further.

## Range column chart

To render a range column chart, create an instance of [`RangeColumnSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/RangeColumnSeries-class.html) and add to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html). 

Since the [`RangeColumnSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/RangeColumnSeries-class.html) requires two Y values for a point, your data should contain high and low values. High and low value specifies the maximum and minimum range of the point. 

* [`highValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/highValueMapper.html) - Field in the data source, which is considered as high value for the data points.
* [`lowValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/lowValueMapper.html) - Field in the data source, which is considered as low value for the data points. 

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(),
                        series: <ChartSeries>[
                            RangeColumnSeries<ChartData, double>(
                                dataSource: <ChartData>[
                                    ChartData('Jan', 3, 9),
                                    ChartData('Feb', 4, 11),
                                    ChartData('Mar', 6, 13),
                                    ChartData('Apr', 9, 17),
                                    ChartData('May', 12, 20),
                                ],
                                xValueMapper: (ChartData sales, _) => sales.x,
                                lowValueMapper: (ChartData sales, _) => sales.low,
                                highValueMapper: (ChartData sales, _) => sales.high,
                            )
                        ]
                    )
                )   
            )
        );
    }

    class ChartData {
        ChartData(this.x, this.high, this.low);
            final String x;
            final double high;
            final double low;
    }

{% endhighlight %}

![Range column chart](images/cartesian-chart-types/range_column.jpg)

### Data label

In the range column chart when data label is enabled, by default there will be two values displayed namely, high and low, but in the other types of charts, only y value will be displayed.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(),
                        series: <ChartSeries>[
                            RangeColumnSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                lowValueMapper: (ChartData sales, _) => sales.low,
                                highValueMapper: (ChartData sales, _) => sales.high,
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true, 
                                    position: CartesianLabelPosition.top
                                ),
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Range column datalabel](images/cartesian-chart-types/range_column_datalabel.jpg)

### Transposed range column

The [`isTransposed`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/isTransposed.html) property of [`CartesianSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries-class.html) is used to transpose the horizontal and vertical axes, to view the data in a different perspective. Using this feature, you can render range column chart.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        isTransposed: true,
                        primaryXAxis: CategoryAxis(),
                        series: <ChartSeries>[
                            RangeColumnSeries<ChartData, double>(
                                dataSource: <ChartData>[
                                    ChartData('Jan', 3, 9),
                                    ChartData('Feb', 4, 11),
                                    ChartData('Mar', 6, 13),
                                    ChartData('Apr', 9, 17),
                                    ChartData('May', 12, 20),
                                ],
                                xValueMapper: (ChartData sales, _) => sales.x,
                                lowValueMapper: (ChartData sales, _) => sales.low,
                                highValueMapper: (ChartData sales, _) => sales.high,
                            )
                        ]
                    )
                )   
            )
        );
    }

    class ChartData {
        ChartData(this.x, this.high, this.low);
            final String x;
            final double high;
            final double low;
    }

{% endhighlight %}


## Range area chart

To render a range area chart, create an instance of `RangeAreaSeries` and add to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html). 

Since the `RangeAreaSeries` requires two Y values for a point, your data should contain high and low values. High and low value specifies the maximum and minimum range of the point. 

* [`highValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/highValueMapper.html) - Field in the data source, which is considered as high value for the data points.
* [`lowValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/lowValueMapper.html) - Field in the data source, which is considered as low value for the data points. 

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            RangeAreaSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                lowValueMapper: (ChartData sales, _) => sales.low,
                                highValueMapper: (ChartData sales, _) => sales.high,
                            )
                        ]
                    )
                )   
            )
        );
    }

    class ChartData {
        ChartData(this.x, this.high, this.low);
            final double x;
            final double high;
            final double low;
    }

{% endhighlight %}

![Range area chart](images/cartesian-chart-types/range_area.png)

###	Border customization

The borders of the range area chart can be customized using the `borderDrawMode` property. The default value of the `borderMode` property is `all` and the other value is `excludeSides`.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            RangeAreaSeries<SalesData, double>(
                                dataSource: chartData,
                                color: Colors.deepOrange[300],
                                borderDrawMode: RangeAreaBorderMode.excludeSides,
                                borderColor: Colors.green,
                                borderWidth: 2,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Range area border](images/cartesian-chart-types/range_area_border.png)

## Spline area chart

To render a spline area chart, create an instance of `SplineAreaSeries`, and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The following properties are used to customize the appearance of spline area chart:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - Controls the transparency of the chart series.
* [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) – Changes the stroke width of the series.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            SplineAreaSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Spline area chart](images/cartesian-chart-types/spline_area.png)

### Dashed spline area

The [`dashArray`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/dashArray.html) property of the [`SplineAreaSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineAreaSeries-class.html) is used to render spline area series with dashes. Odd value is considered as rendering size and even value is considered as gap.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            SplineAreaSeries<SalesData, double>(
                                dataSource: chartData,
                                dashArray: <double>[5, 5],
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Dashed spline area chart](images/cartesian-chart-types/spline_area_dashed.png)

###	Spline area rendering types

The `splineType` allows you to change the spline area curve in series. The following types are used in `SplineAreaSeries`:

* natural
* monotonic
* cardinal
* clamped

By default, the value of `splineType` is `natural`.

The following code sample demonstrates how to set the `splineType` value to `cardinal`. When you set the cardinal type, you can specify the desired line tension of the `cardinal` spline using the `cardinalSplineTension` property. The value of this property ranges from 0 to 1.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            SplineAreaSeries<SalesData, double>(
                                dataSource: chartData,
                                splineType: SplineType.cardinal,
                                cardinalSplineTension: 0.9,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Spline area type](images/cartesian-chart-types/spline_area_types.png)

## Spline range area chart

To render a spline range area chart, create an instance of the [`SplineRangeAreaSeries`](), and add to the series collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html).


 `SplineRangeAreaSeries` requires two Y values for a point, data should contain high and low values. The high and low values specify the maximum and minimum ranges of a point.

* [`highValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/highValueMapper.html) - Field in the data source, which is considered as high value for the data points.
* [`lowValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/lowValueMapper.html) - Field in the data source, which is considered as low value for the data points.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <CartesianSeries<SalesData, num>>[
                        SplineRangeAreaSeries<SalesData, num>(
                          dataSource: chartData,
                          xValueMapper: (SalesData sales, _) => sales.xValue,
                          lowValueMapper: (SalesData sales, _) =>
                              sales.lowValue,
                          highValueMapper: (SalesData sales, _) =>
                              sales.highValue,),
                    ]
                )
             )
          )
       );
    }

{% endhighlight %}

![splinerangearea](images/cartesian-chart-types/splinerangearea.png)

###	Spline rendering types

The [`splineType`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineSeries/splineType.html) allows you to change the spline curve in series. The following types are used in [`SplineRangeAreaSeries`]().

* natural
* monotonic
* cardinal
* clamped

By default, the value of [`splineType`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineSeries/splineType.html) is [`natural`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineType-class.html).

The following code sample demonstrates how to set the [`splineType`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineSeries/splineType.html) value to [`cardinal`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineType-class.html). When you set the cardinal type, you can specify the desired line tension of the [`cardinal`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineType-class.html) spline using the [`cardinalSplineTension`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SplineSeries/cardinalSplineTension.html) property. The value of this property ranges from 0 to 1.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <CartesianSeries<SalesData, num>>[
                            SplineRangeAreaSeries<SalesData, num>(
                                dataSource: chartData,
                                splineType: SplineType.cardinal,
                                cardinalSplineTension: 0.8,
                                xValueMapper: (SalesData sales, _) => sales.xValue,
                                lowValueMapper: (SalesData sales, _) => sales.lowValue,
                                highValueMapper: (SalesData sales, _) => sales.highValue
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![splinerangearea](images/cartesian-chart-types/splinerangeareatype.png)

### Border customization

The borders of the spline range area chart can be customized using the [`borderDrawMode`]() property. The default value of the [`borderDrawMode`]() property is `all` and the other value is `excludeSides`.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <CartesianSeries<SalesData, num>>[
                            SplineRangeAreaSeries<SalesData, num>(
                                borderDrawMode: RangeAreaBorderMode.all,
                                borderWidth:2,
                                borderColor: Colors.red
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![splinerangearea_bordermode](images/cartesian-chart-types/splinerangearea_bordermode.png)

## Step area chart

To render a spline area chart, create an instance of `StepAreaSeries`, and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The following properties are used to customize the appearance of spline area chart.

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - Controls the transparency of the chart series.
* [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) – Changes the stroke width of the series.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StepAreaSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Step area chart](images/cartesian-chart-types/step_area.png)

### Dashed step area

The [`dashArray`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/dashArray.html) property of the [`StepAreaSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StepAreaSeries-class.html) is used to render spline area series with dashes. Odd value is considered as rendering size and even value is considered as gap.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StepAreaSeries<SalesData, double>(
                                dataSource: chartData,
                                dashArray: <double>[5, 5],
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Dashed step area chart](images/cartesian-chart-types/step_area_dashed.png)

## Histogram chart

Histogram chart is a graphical representation that organizes a group of data points into user-specified ranges. It is similar in appearance to a bar chart. The histogram condenses a data series into an easily interpreted visual by taking many data points and grouping them into logical ranges.

To render a histogram chart, create an instance of [`HistogramSeries`]() and add to the series collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html).

You can customize intervals using the [`binInterval`]() property. Interval value by which the data points are grouped and rendered as bars, in histogram series.

For example, if the [`binInterval`]() is set to 20, the x-axis will split with 20 as the interval. The first bar in the histogram represents the count of values lying between 0 to 20 in the provided data and the second bar will represent 20 to 40.

If no value is specified for this property, then the interval will be calculated automatically based on the data points count and value.

You can collapse the normal distribution curve using the [`showNormalDistributionCurve`]() property. You can use the following properties to customize the appearance.

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - Controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) – Changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) – Changes the stroke color of the series.
* [`curveColor`]() - Changes the color of the normal distribution curve.
* [`curveWidth`]() - Changes the width of the normal distribution curve.
* [`curveDashArray`]() -  Renders the normal distribution curve  with dashes.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            HistogramSeries<SalesDaa, num>(
                                dataSource: chartData,
                                yValueMapper: (SalesData sales, _) => sales.yValue,
                                binInterval: 20,
                                showNormalDistributionCurve: true,
                                curveColor: const Color.fromRGBO(192, 108, 132, 1),
                                borderWidth: 3
                            ),
                        ]
                    )
                )
             )
        );
    }

{% endhighlight %}

![histogram chart](images/cartesian-chart-types/Histogram.png)

## Stacked line chart

To render a stacked line chart, create an instance of [`StackedLineSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedLineSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html). The following properties are used to customize the appearance of stacked line series:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the line.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) – Controls the transparency of the chart series.
* [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) – Changes the stroke width of the line.


{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedLineSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedLineSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                             StackedLineSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                            StackedLineSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y4
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked line chart](images/cartesian-chart-types/stacked_line.jpg)

### Grouping series

You can group and stack the similar stacked series types using the [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedLineSeries/groupName.html) property of stacked series. The stacked series that contains the same [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedLineSeries/groupName.html) will be stacked in a single group.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedLineSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedLineSeries<ChartData, double>(
                                groupName: 'Group B',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                            StackedLineSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked line grouping](images/cartesian-chart-types/stacked_line_grouping.jpg)

### Display cumulative values

You can show the cumulative data label values using the [`showCumulativeValues`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/showCumulativeValues.html) property. If the series are grouped using [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedLineSeries/groupName.html), then cumulative values will be shown based on grouping.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedLineSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    showCumulativeValues: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedLineSeries<ChartData, double>(
                                groupName: 'Group B',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    showCumulativeValues: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                            StackedLineSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    showCumulativeValues: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked line cumulative](images/cartesian-chart-types/stacked_line_cumulative.jpg)

## Stacked area chart

To render a stacked area chart, create an instance of [`StackedAreaSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedAreaSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html). The following properties are used to customize the appearance of stacked line series:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the line.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) – Controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) – Changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) – Changes the stroke color of the series.


{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedAreaSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedAreaSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                            StackedAreaSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked area](images/cartesian-chart-types/stacked_area.jpg)

### Grouping series

You can group and stack the similar stacked series types using the [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedAreaSeries/groupName.html) property of stacked series. The stacked series that contains the same [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedAreaSeries/groupName.html) will be stacked in a single group.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedAreaSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedAreaSeries<ChartData, double>(
                                groupName: 'Group B',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                            StackedAreaSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked area grouping](images/cartesian-chart-types/stacked_area_grouping.jpg)

### Display cumulative values

You can show the cumulative data label values using the [`showCumulativeValues`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/showCumulativeValues.html) property. If the series are grouped using [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedAreaSeries/groupName.html), then cumulative values will be shown based on grouping.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedAreaSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    showCumulativeValues: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedAreaSeries<ChartData, double>(
                                groupName: 'Group B',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    showCumulativeValues: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                            StackedAreaSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    showCumulativeValues: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked area cumulative](images/cartesian-chart-types/stacked_area_cumulative.jpg)

## Stacked column chart

To render a stacked column chart, create an instance of [`StackedColumnSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedColumnSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html). The following properties are used to customize the appearance of stacked line series:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the line.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) – Controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) – Changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) – Changes the stroke color of the series.


{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedColumnSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedColumnSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                             StackedColumnSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                            StackedColumnSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y4
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked column](images/cartesian-chart-types/stacked_column.jpg)

### Grouping series

You can group and stack the similar stacked series types using the [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedColumnSeries/groupName.html) property of stacked series. The stacked series that contains the same [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedColumnSeries/groupName.html) will be stacked in a single group.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedColumnSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedColumnSeries<ChartData, double>(
                                groupName: 'Group B',
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                            StackedColumnSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                            StackedColumnSeries<ChartData, double>(
                                groupName: 'Group B',
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y4
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked column grouping](images/cartesian-chart-types/stacked_column_grouping.jpg)

### Display cumulative values

You can show the cumulative data label values using the [`showCumulativeValues`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/showCumulativeValues.html) property. If the series are grouped using [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedColumnSeries/groupName.html), then cumulative values will be shown based on grouping.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedColumnSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(isVisible:true, showCumulativeValues: true),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedColumnSeries<ChartData, double>(
                                groupName: 'Group B',
                                dataLabelSettings: DataLabelSettings(isVisible:true, showCumulativeValues: true),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                            StackedColumnSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(isVisible:true, showCumulativeValues: true),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                            StackedColumnSeries<ChartData, double>(
                                groupName: 'Group B',
                                dataLabelSettings: DataLabelSettings(isVisible:true, showCumulativeValues: true),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y4
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked column cumulative](images/cartesian-chart-types/stacked_column_cumulative.jpg)

## Stacked bar chart

To render a stacked bar chart, create an instance of [`StackedBarSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedBarSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html). The following properties are used to customize the appearance of stacked line series:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the line.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) – Controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) – Changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) – Changes the stroke color of the series.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedBarSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedBarSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                             StackedBarSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                            StackedBarSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y4
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked bar](images/cartesian-chart-types/stacked_bar.jpg)

### Grouping series

You can group and stack the similar stacked series types using the [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedBarSeries/groupName.html) property of stacked series. The stacked series that contains the same [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedBarSeries/groupName.html) will be stacked in a single group.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedBarSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedBarSeries<ChartData, double>(
                                groupName: 'Group B',
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                            StackedBarSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                            StackedBarSeries<ChartData, double>(
                                groupName: 'Group B',
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y4
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked bar grouping](images/cartesian-chart-types/stacked_bar_grouping.jpg)

### Display cumulative values

You can show the cumulative data label values using the [`showCumulativeValues`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/showCumulativeValues.html) property. If the series are grouped using [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedBarSeries/groupName.html), then cumulative values will be shown based on grouping.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedBarSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(isVisible:true, showCumulativeValues: true),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedBarSeries<ChartData, double>(
                                groupName: 'Group B',
                                dataLabelSettings: DataLabelSettings(isVisible:true, showCumulativeValues: true),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                            StackedBarSeries<ChartData, double>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(isVisible:true, showCumulativeValues: true),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                            StackedBarSeries<ChartData, double>(
                                groupName: 'Group B',
                                dataLabelSettings: DataLabelSettings(isVisible:true, showCumulativeValues: true),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y4
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked bar cumulative](images/cartesian-chart-types/stacked_bar_cumulative.jpg)

## 100% Stacked Area Chart

To render a 100% stacked area chart, create an instance of `StackingArea100Series` and add to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html). You can use the following properties to customize the 100% stacked area appearance.

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - Controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) – Changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) – Changes the stroke color of the series.
* `borderDrawMode` - Specifies the type of the border mode and it defaults to *top*.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedArea100Series<ChartData, DateTime>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.year,
                                yValueMapper: (ChartData sales, _) => sales.sales1
                            ),
                            StackedArea100Series<ChartData, DateTime>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.year,
                                yValueMapper: (ChartData sales, _) => sales.sales2
                            ),
                            StackedArea100Series<ChartData, DateTime>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.year,
                                yValueMapper: (ChartData sales, _) => sales.sales3
                            ),
                            StackedArea100Series<ChartData, DateTime>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.year,
                                yValueMapper: (ChartData sales, _) => sales.sales4
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Stacked 100Area chart](images/cartesian-chart-types/stacked_area_100.png)

## 100% Stacked Column Chart

To render a 100% stacked column chart, create an instance of [`StackedColumn100Series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedColumnSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/XyDataSeries-class.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The following properties are used to customize the appearance:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - Controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) – Changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) – Changes the stroke color of the series.
* [`borderRadius`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedColumnSeries/borderRadius.html) -  used to add the rounded corners to the rectangle.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedColumn100Series<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            ),
                            StackedColumn100Series<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales2
                            ),
                            StackedColumn100Series<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales3
                            ),
                            StackedColumn100Series<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales4
                            )
                        ]
                    )
                )      
            )
        );
    }

{% endhighlight %}

![Stacked 100 column chart](images/cartesian-chart-types/stacked_column_100.png)

### Column width and spacing

The `spacing` property is used to change the spacing between two segments. The default value of spacing is 0, and the value ranges from 0 to 1. Here, 1 and 0 correspond to 100% and 0% of the available space, respectively.

The `width` property is used to change the width of the rectangle. The default value of the width is 0.7, and the value ranges from 0 to 1. Here, 1 and 0 correspond to 100% and 0% of the available width, respectively.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedColumn100Series<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales,
                                width: 0.8, // Width of the columns
                                spacing: 0.2 // Spacing between the columns
                            ),
                            StackedColumn100Series<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales2,
                                width: 0.8, // Width of the columns
                                spacing: 0.2 // Spacing between the columns
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked 100 column width and spacing](images/cartesian-chart-types/stacked_column_100_size.png)

## 100% Stacked Bar Chart

To render a 100% stacked bar chart, create an instance of [`StackedBar100Series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedBar100Series-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The following properties are used to customize the appearance:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - Controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) – Changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) – Changes the stroke color of the series.
* [`borderRadius`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedBar100Series/borderRadius.html) -  used to add the rounded corners to the rectangle.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedBar100Series<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            ),
                            StackedBar100Series<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales2
                            ),
                            StackedBar100Series<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales3
                            ),
                            StackedBar100Series<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales4
                            )
                        ]
                    )
                )      
            )
        );
    }

{% endhighlight %}

![Stacked 100 bar chart](images/cartesian-chart-types/stacked100_bar.png)

### Bar width and spacing

The [`spacing`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedBar100Series/spacing.html) property is used to change the spacing between two segments. The default value of spacing is 0, and the value ranges from 0 to 1. Here, 1 and 0 correspond to 100% and 0% of the available space, respectively.

The [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) property is used to change the width of the rectangle. The default value of the width is 0.7, and the value ranges from 0 to 1. Here, 1 and 0 correspond to 100% and 0% of the available width, respectively.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedBar100Series<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales,
                                width: 0.8, 
                                spacing: 0.2 
                            ),
                            StackedBar100Series<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales2,
                                width: 0.8, 
                                spacing: 0.2 
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked 100 bar width and spacing](images/cartesian-chart-types/stacked_bar_100_sizing.png)

## 100% Stacked Line Chart

To render a 100% stacked line chart, create an instance of `StackedLine100Series`, and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The following properties are used to customize the appearance:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the line.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - Controls the transparency of the chart series.
* [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) – Changes the stroke width of the line.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedLine100Series<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            ),
                            StackedLine100Series<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales2
                            ),
                            StackedLine100Series<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales3
                            ),
                            StackedLine100Series<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales4
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Stacked 100 line chart](images/cartesian-chart-types/stacked_line_100.png)

### Dashed line

The `dashArray` property of `StackedLine100Series` is used to render line series with dashes. Odd value is considered as rendering size and even value is considered as gap.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            StackedLine100Series<SalesData, String>(
                                dataSource: chartData,
                                dashArray: <double>[5,5],
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            ),
                            StackedLine100Series<SalesData, String>(
                                dataSource: chartData,
                                dashArray: <double>[5,5],
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales2
                            ),
                            StackedLine100Series<SalesData, String>(
                                dataSource: chartData,
                                dashArray: <double>[5,5],
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales3
                            ),
                            StackedLine100Series<SalesData, String>(
                                dataSource: chartData,
                                dashArray: <double>[5,5],
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales4
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Dashed line chart](images/cartesian-chart-types/stacked_line_100_dashes.png)

## HiLo chart
HiLo Series illustrates the price movements in stock using the high and low values.

To render a HiLo chart, create an instance of [`HiloSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/HiloSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The following properties are used to customize the appearance:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - Controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) – Changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) – Changes the stroke color of the series.
* [`lowValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/lowValueMapper.html) - used to get the low values from the series.
* [`highValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/highValueMapper.html) - used to get the high values from the series.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders bar chart
                            HiloSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                  lowValueMapper: (Sample sales, _) => sales.low,
              highValueMapper: (Sample sales, _) => sales.high
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![hiLo chart](images/cartesian-chart-types/hilo_chart.png)

## Open High Low Close (OHLC)

 OpenHighLowClose series is used to represent the low, high, open and closing values over time.

To render a OpenHighLowClose chart, create an instance of [` hiloOpenCloseSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/HiloOpenCloseSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The following properties are used to customize the appearance:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - Controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) – Changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) – Changes the stroke color of the series.
* [`lowValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/lowValueMapper.html) - used to get the low values from the series.
* [`highValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/highValueMapper.html) - used to get the high values from the series.
* [`openValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/HiloOpenCloseSeries/openValueMapper.html) - used to get the open values from the series.
* [`closeValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/HiloOpenCloseSeries/closeValueMapper.html) - used to get the close values from the series.
* [`bearFillColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/HiloOpenCloseSeries/bearColor.html) - bearFillColor will be applied when the opening value is less than the closing value.
* [`bullFillColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/HiloOpenCloseSeries/bullColor.html) - bullFillColor will be applied when the opening value is greater than closing value.



{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders hiloOpenCloseSeries 
                            hiloOpenCloseSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                lowValueMapper: (Sample sales, _) => sales.low,
                                highValueMapper: (Sample sales, _) => sales.high, 
                                openValueMapper: (Sample sales, _) => sales.open,
                          closeValueMapper: (Sample sales, _) => sales.close,

                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![hiLoopenclose chart](images/cartesian-chart-types/hilo_open_close.png)

## Candle

Candle series is similar to HiLo Open Close series, used to represent the low, high, open and closing price over time.

To render a Candle chart, create an instance of [` CandleSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CandleSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The following properties are used to customize the appearance:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) – Changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - Controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) – Changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) – Changes the stroke color of the series.
* [`enableSolidCandles`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CandleSeries/enableSolidCandles.html)- Used to enable/disable the solid candles. By default is set to be false. The fill color of the candle will be defined by its opening and closing values.
* [`lowValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/lowValueMapper.html) - used to get the low values from the series.
* [`highValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/highValueMapper.html) - used to get the high values from the series.
* [`openValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CandleSeries/openValueMapper.html) - used to get the open values from the series.
* [`closeValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CandleSeries/closeValueMapper.html) - used to get the close values from the series.
* [`bearFillColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CandleSeries/bearColor.html) - bearFillColor will be applied when the opening value is less than the closing value.
* [`bullFillColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CandleSeries/bullColor.html) - bullFillColor will be applied when the opening value is greater than closing value.



{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders CandleSeries
                            CandleSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                lowValueMapper: (Sample sales, _) => sales.low,
                                highValueMapper: (Sample sales, _) => sales.high, 
                                openValueMapper: (Sample sales, _) => sales.open,
                          closeValueMapper: (Sample sales, _) => sales.close,

                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![candle chart](images/cartesian-chart-types/candle.png)

## Box and Whisker chart

The Box and Whisker charts are used to visualize a group of numerical data through their quartiles. It is also referred as box plot. Box plots may also have lines extending vertically from the boxes (whiskers) indicating variability outside the upper and lower quartiles.

To render a Box and Whisker chart, create an instance of [`BoxAndWhiskerSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BoxAndWhiskerSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The following properties to customize the appearance.

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) - Changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - Controls the transparency of the chart series.
* [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) – Changes the stroke width of the series.
* [`BoxPlotMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BoxPlotMode-class.html) - used to change the box plot rendering mode. This property is applicable for 
`normal`, `exclusive`, and `inclusive` values.
* [`showMean`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BoxAndWhiskerSeries/showMean.html) - Indication for mean value in box plot. It is set to be true, a cross symbol will be displayed at the mean value, for each data point in box plot. Else, it will not be displayed.
* [`spacing`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BoxAndWhiskerSeries/spacing.html) - Spacing between the box plots.The value ranges from 0 to 1, where 1 represents 100% and 0 represents 0% of the available space.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries<SalesData, double>>[
                           BoxAndWhiskerSeries<SalesData, double>(
                                dataSource: data,
                                boxPlotMode: BoxPlotMode.exclusive,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.number
                            )
                        ]
                    )
                )
            )   
        );
    }

{% endhighlight %}

![box and whisker chart](images/cartesian-chart-types/box_and_whisker.png)

## Waterfall Chart

The waterfall chart explains gradual changes in the quantitative value of an entity that is subject to changes by increments or decrements. Using the waterfall chart, you can quickly illustrate changes in revenues.

To render a waterfall chart, create an instance of [`WaterfallSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/WaterfallSeries-class.html) and add to the[`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html)collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The following properties to customize the appearance.

* [`negativePointsColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/WaterfallSeries/negativePointsColor.html) - Changes the color of the negative data points in the series. If no color is specified, then the negative data points will be rendered with the series default color.
* [`intermediateSumColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/WaterfallSeries/intermediateSumColor.html) - Changes the Color of the intermediate sum points in the series. If no color is specified, then the intermediate sum points will be rendered with the series default color.
* [`totalSumColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/WaterfallSeries/totalSumColor.html) - Changes the color of the total sum points in the series. If no color is specified, then the total sum points will be rendered with the series default color.
* [`connectorLineSettings`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/WaterfallSeries/connectorLineSettings.html) - used to customize the waterfall chart connector line. Data points in waterfall chart are connected using the connector line. Provides the options to change the [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ConnectorLineSettings/width.html), [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ConnectorLineSettings/color.html) and [`dashArray`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/WaterfallConnectorLineSettings/dashArray.html) of the connector line to customize the appearance.
* [`spacing`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/WaterfallSeries/spacing.html) - used to provide spacing between the data points in waterfall chart. The value ranges from 0 to 1, where 1 represents 100% and 0 represents 0% of the available space.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries<SalesData, double>>[
                            WaterfallSeries<SalesData, double>(
                                dataSource: <SalesData>[
                                    SalesData(2, 10, Colors.red),
                                    SalesData(3, -3, Colors.green),
                                    SalesData(4, 5, Colors.red, true),
                                    SalesData(5, 4, Colors.blue),
                                    SalesData(6, -2, Colors.red),
                                    SalesData(7, -5, Colors.red, true),
                                    SalesData(8, -10, Colors.red),
                                    SalesData(9, 8, Colors.red),
                                    SalesData(10, 8, Colors.red),
                                    SalesData(11, 5, Colors.red),
                                    SalesData(12, 8, Colors.red, false),
                                    SalesData(13, -5, Colors.red, false, true),
                                ],
                                negativePointsColor: const Color.fromRGBO(229, 101, 144, 1),
                                intermediateSumColor: const Color.fromRGBO(79, 129, 188, 1),
                                totalSumColor: const Color.fromRGBO(79, 129, 188, 1),
                                xValueMapper: (SalesData sales, _) => sales.x,
                                yValueMapper: (SalesData sales, _) => sales.y,
                                intermediateSumPredicate: (SalesData sales, _) => sales.isIntermediate,
                                totalSumPredicate: (SalesData sales, _) => sales.isTotal,
                                connectorLineSettings: WaterfallConnectorLineSettings(
                                    width: 2.5,
                                    dashArray: <double>[3, 1]
                                )
                            )
                        ]
                    )
                )
            )   
        );
    }

{% endhighlight %}

![waterfall_chart](images/cartesian-chart-types/waterfall_series.png)
