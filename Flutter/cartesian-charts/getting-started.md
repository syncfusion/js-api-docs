---
layout: post
title: Getting started for Syncfusion Cartesian Charts (SfCartesianChart)
description:  Learn how to create the syncfusion Flutter charts, add series, legend ,markers and other features in Chart.
platform: flutter
control: Chart
documentation: ug
---

# Getting Started with Flutter Cartesian Charts (SfCartesianChart)

This section explains the steps required to populate the chart with data, title, data labels, legend, and tooltips. This section covers only the minimal features needed to know to get started with the chart.

To get start quickly with our Flutter chart widget, you can check on this video.

<style>#flutterChartVideoTutorial{width : 90% !important; height: 300px !important }</style>
<iframe id='flutterChartVideoTutorial' src='https://www.youtube.com/embed/t3Dczqj8-10'></iframe>

## Add Flutter Charts to an application

Create a simple project using the instructions given in the [Getting Started with your first Flutter app](https://flutter.dev/docs/get-started/test-drive?tab=vscode#create-app) documentation.

**Add dependency**

Add the Syncfusion Flutter Chart dependency to your pub spec file.

{% highlight dart %} 

    dependencies:

    syncfusion_flutter_charts: ^xx.x.xx

{% endhighlight %}

N> Here **xx.x.xx** denotes the current version of [`Syncfusion Flutter Charts`](https://pub.dev/packages/syncfusion_flutter_charts/versions) package.

**Get packages**

Run the following command to get the required packages.

{% highlight dart %} 

    $ flutter pub get

{% endhighlight %}

**Import package**

Import the following package in your Dart code.

{% highlight dart %} 

    import 'package:syncfusion_flutter_charts/charts.dart';

{% endhighlight %}

## Initialize chart

Once the package has been imported, initialize the chart as a child of any widget. There are two kinds of chart widgets - SfCartesianChart and SfCircularChart. SfCartesianChart is used to render all kinds of charts which need to be plotted in Cartesian coordinates. SfCircularChart can be used to render pie, doughnut and radial bar charts. Here, as we are plotting line chart, initialize SfCartesianChart widget as a child of Container widget.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    //Initialize chart
                    child: SfCartesianChart()
                )
            )
        );
    }

{% endhighlight %}

![Initialize chart](images/getting-started/default.jpg)

## Bind data source

Based on your data, initialize the appropriate axis type and series type. In the series, you need to map the data source and the fields for x and y data points. Here, line series is rendered with category axis that is demonstrated in the following code snippet.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        // Initialize category axis
                        primaryXAxis: CategoryAxis(),
                        series: <ChartSeries>[
                            // Initialize line series
                            LineSeries<SalesData, String>(
                                dataSource: [
                                    // Bind data source
                                    SalesData('Jan', 35),
                                    SalesData('Feb', 28),
                                    SalesData('Mar', 34),
                                    SalesData('Apr', 32),
                                    SalesData('May', 40)
                                ],
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )
            )
        );
    }

    class SalesData{
        SalesData(this.year, this.sales);
        final String year;
        final double sales;
    }

{% endhighlight %}

![Bind data source](images/getting-started/data_source.jpg)

## Add title

You can add a [`title`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/title.html) to the chart to provide quick information to users about the data plotted in the chart. The title to chart can be set as demonstrated in the following code snippet.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        // Chart title text
                        title: ChartTitle(text: 'Half yearly sales analysis'),
                        // Initialize category axis
                        primaryXAxis: CategoryAxis(),
                        series: <ChartSeries>[
                            // Initialize line series
                            LineSeries<SalesData, String>(
                            dataSource: [
                                // Bind data source
                                SalesData('Jan', 35),
                                SalesData('Feb', 28),
                                SalesData('Mar', 34),
                                SalesData('Apr', 32),
                                SalesData('May', 40)
                            ],
                            xValueMapper: (SalesData sales, _) => sales.year,
                            yValueMapper: (SalesData sales, _) => sales.sales)
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Title to chart](images/getting-started/title_chart.jpg)

## Enable data labels

You can add data labels to improve the readability of the chart using the [`dataLabelSettings`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/dataLabelSettings.html) property.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        title: ChartTitle(text: 'Half yearly sales analysis'),
                        // Initialize category axis
                        primaryXAxis: CategoryAxis(),
                        series: <ChartSeries>[
                            // Initialize line series
                            LineSeries<SalesData, String>(
                                dataSource: [
                                    // Bind data source
                                    SalesData('Jan', 35),
                                    SalesData('Feb', 28),
                                    SalesData('Mar', 34),
                                    SalesData('Apr', 32),
                                    SalesData('May', 40)
                                ],
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales,
                                // Render the data label
                                dataLabelSettings:DataLabelSettings(isVisible : true)
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![DataLabel to chart](images/getting-started/datalabel.jpg)

## Enable legend

The legend provides information about the series rendered in the chart.

You can use legend in chart by setting the [`isVisible`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/Legend/isVisible.html) property to true in [`legend`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/Legend-class.html).

Additionally, you need to set label for each series using the [`series.name`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartSeries/name.html) property. The labels will be displayed in corresponding legends.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        // Enables the legend
                        legend: Legend(isVisible: true), 
                        // Initialize category axis
                        primaryXAxis: CategoryAxis(),
                        series: <ChartSeries>[
                            // Initialize line series
                            LineSeries<SalesData, String>(
                                dataSource: [
                                    // Bind data source
                                    SalesData('Jan', 35),
                                    SalesData('Feb', 28),
                                    SalesData('Mar', 34),
                                    SalesData('Apr', 32),
                                    SalesData('May', 40)
                                ],
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales,
                                name: 'Sales'
                            )
                        ]
                    )
                )      
            )
        );
    }

{% endhighlight %}

![Legend in chart](images/getting-started/legend.png)

## Enable tooltip

The tooltip is used when you cannot display information using the data labels due to space constraints.

The [`tooltipBehavior`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/tooltipBehavior.html) property in chart is used to enable and customize the tooltip for all the series whereas the [`enableTooltip`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartSeries/enableTooltip.html) property in series is used to toggle the tooltip visibility of each series. The tooltip is enabled as demonstrated in the following code snippet.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            appBar: AppBar(
                title: Text(widget.title),
            ),
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        // Enables the tooltip for all the series in chart
                        tooltipBehavior: TooltipBehavior(enable: true),
                        // Initialize category axis
                        primaryXAxis: CategoryAxis(),
                        series: <ChartSeries>[
                            // Initialize line series
                            LineSeries<SalesData, String>(
                                // Enables the tooltip for individual series
                                enableTooltip: true, 
                                dataSource: [
                                    // Bind data source
                                    SalesData('Jan', 35),
                                    SalesData('Feb', 28),
                                    SalesData('Mar', 34),
                                    SalesData('Apr', 32),
                                    SalesData('May', 40)
                                ],
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

![Tooltip in chart](images/getting-started/tooltip.png)

You can find the complete getting started example from this [`link`](https://www.syncfusion.com/downloads/support/directtrac/general/ze/chart_example2131351808).

## See Also

* [Integrate Syncfusion Flutter charts in Flutter web Application](https://www.syncfusion.com/kb/11551/how-to-integrate-syncfusion-charts-in-flutter-web-application-sfcartesianchart).