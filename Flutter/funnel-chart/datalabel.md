---
layout: post
title: Data labels in Syncfusion Funnel Charts
description: Learn how to add the Data point labels to the series available in the Syncfusion Flutter Funnel Chart widget.
platform: flutter
control: Chart
documentation: ug
---

# Data label in Funnel chart

Data label can be added to a chart series by enabling the [`isVisible`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/isVisible.html) option in the [`dataLabelSettings`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/FunnelSeries/dataLabelSettings.html). You can use the following properties to customize the appearance.

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/color.html) – used to change the background color of the data label shape.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/borderWidth.html) – used to change the stroke width of the data label shape.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/borderColor.html) – used to change the stroke color of the data label shape.
* [`alignment`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/alignment.html) - aligns the data label text to [`near`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAlignment-class.html), [`center`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAlignment-class.html) and [`far`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAlignment-class.html).
* [`textStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/textStyle.html) – used to change the data label text color, size, font family, font style, and font weight.
* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/color.html) – used to change the color of the data label.
* [`fontFamily`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTextStyle/fontFamily.html) - used to change the font family for the data label.
* [`fontStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTextStyle/fontStyle.html) - used to change the font style for the data label.
* [`fontWeight`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTextStyle/fontWeight.html) - used to change the font weight for the data label.
* [`fontSize`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTextStyle/fontSize.html) - used to change the font size for the data label.
* [`margin`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/margin.html) - used to change the margin size for data labels.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/opacity.html) - used to control the transparency of the data label.
* [`labelAlignment`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/labelAlignment.html) - used to align the Funnel data label positions. The available options to customize the positions are [`outer`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelAlignment-class.html), [`auto`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelAlignment-class.html), [`top`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelAlignment-class.html), [`bottom`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelAlignment-class.html) and [`middle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelAlignment-class.html).
* [`borderRadius`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/borderRadius.html) - used to add the rounded corners to the data label shape.
* [`angle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/angle.html)  - used to rotate the labels.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfFunnelChart(
                        series: FunnelSeries<SalesData, String>(
                                dataSource: chartData,
                                pointColorMapper: (SalesData data, _) => data.color,
                                xValueMapper: (SalesData data, _) => data.x,
                                yValueMapper: (SalesData data, _) => data.y,
                                dataLabelSettings: DataLabelSettings(
                                    // Renders the data label
                                    isVisible: true
                                )
                            )
                    )
                )
            )
        );
    }

{% endhighlight %}

![DataLabel](images/datalabel/default_datalabel.png)

### Label position

The [`labelAlignment`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelAlignment-class.html) property is used to position the Funnel chart type data labels at [`top`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelAlignment-class.html), [`bottom`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelAlignment-class.html), [`auto`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelAlignment-class.html), [`outer`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelAlignment-class.html) and [`middle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelAlignment-class.html) position of the actual data point position. By default, labels are [`auto`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelAlignment-class.html) positioned. You can move the labels horizontally and vertically using OffsetX and OffsetY properties respectively.

The [`labelPosition`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/labelPosition.html) property is used to place the Funnel series data labels either [`inside`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelPosition-class.html) or [`outside`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelPosition-class.html). By default the label of Funnel chart is placed [`inside`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelPosition-class.html) the series.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfFunnelChart(
                        series: FunnelSeries<SalesData, String>(
                                dataSource: chartData,
                                xValueMapper: (SalesData data, _) => data.x,
                                yValueMapper: (SalesData data, _) => data.y,
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    // Positioning the data label
                                    labelPosition: ChartDataLabelPosition.outside
                                )
                            )
                    )
                )
            )
        );
    }

{% endhighlight %}

![Data label position](images/datalabel/datalabel_position.png)

N> The [`labelAlignment`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/labelAlignment.html) property is used to position the Funnel chart labels whereas [`labelPosition`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/labelPosition.html) property is used to position the Funnel chart labels.

### Apply series color

The [`useSeriesColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/useSeriesColor.html) property is used to apply the series color to background color of the data labels. The default value of this property is *false*.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfFunnelChart(
                        series: FunnelSeries<SalesData, String>(
                                dataSource: chartData,
                                xValueMapper: (SalesData data, _) => data.x,
                                yValueMapper: (SalesData data, _) => data.y,
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    // Positioning the data label
                                    labelPosition: ChartDataLabelPosition.outside,
                                    // Renders background rectangle and fills it with series color
                                    useSeriesColor: true
                                )
                            )
                    )
                )
            )
        );
    }

{% endhighlight %}

![Series color](images/datalabel/use_series_color.png)

### Hide data label for 0 value

Data label and its connector line in the Funnel charts for the point value 0 can be hidden using the [`showZeroValue`]() property. This defaults to *true*.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                    child:SfFunnelChart(
                        series: FunnelSeries<SalesData, num>(
                            dataSource: [
                                SalesData(11, 35),
                                SalesData(12, 28),
                                SalesData(13, 0),
                                SalesData(14, 32),
                                SalesData(15, 40)
                            ],
                            xValueMapper: (SalesData sales, _) => sales.xValue,
                            yValueMapper: (SalesData sales, _) => sales.yValue,
                            dataLabelSettings: DataLabelSettings(
                                showZeroValue: false,
                                isVisible: true
                            ),
                        )
                    )
            )
        );
    }
{% endhighlight %}

![hide_0_value](images/datalabel/dataLabel_0_value.png)

